---
title: ControllersPointersAndFocus
description: Interazione con i controller, i puntatori e lo stato attivo.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, puntatori, controller
ms.openlocfilehash: f37c096e527def716da70b3845c95473c9b8c695
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692868"
---
# <a name="controllers-pointers-and-focus"></a>Controller, puntatori e stato attivo

I controller, i puntatori e lo stato attivo sono concetti di livello più alto che si basano sulle basi stabilite dal sistema di input di base. Insieme, forniscono un'ampia parte del meccanismo per interagire con gli oggetti nella scena.

## <a name="controllers"></a>Controllers

I controller sono rappresentazioni di un controller fisico (6 gradi di libertà, mano articolata e così via). Sono creati da Gestione dispositivi e sono responsabili della comunicazione con il sistema sottostante corrispondente e della conversione dei dati in eventi e dati a forma di MRTK.

Nella piattaforma di realtà mista di Windows, ad esempio, [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) è un controller responsabile dell'interazione con le [API di rilevamento manuale](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) di Windows sottostanti per ottenere informazioni sui giunti, sulla posa e su altre proprietà della mano. È responsabile della trasformazione di questi dati in eventi MRTK rilevanti, ad esempio chiamando RaisePoseInputChanged o RaiseHandJointsUpdated, e aggiornando il proprio stato interno in modo che le query per [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose(TrackedHandJoint,Handedness,MixedRealityPose@)) restituiscano i dati corretti.

In genere, il ciclo di vita di un controller implica:

1. Un controller viene creato da un gestore di dispositivi al rilevamento di una nuova origine (ad esempio, rileva e inizia a tenere traccia di una mano).

2. Nel ciclo Update () del controller viene chiamato il sistema API sottostante.

3. Nello stesso ciclo di aggiornamento, genera modifiche all'evento di input chiamando direttamente nel sistema di input principale stesso (ad esempio, la generazione di HandMeshUpdated o HandJointsUpdated).

## <a name="pointers-and-focus"></a>Puntatori e stato attivo

I puntatori vengono usati per interagire con gli oggetti di gioco. In questa sezione viene descritto il modo in cui vengono creati i puntatori, il modo in cui vengono aggiornati e il modo in cui determinano gli oggetti in stato attivo. Verranno inoltre illustrati i diversi tipi di puntatori esistenti e gli scenari in cui sono attivi.

### <a name="pointer-categories"></a>Categorie di puntatori

I puntatori in genere rientrano in una delle categorie seguenti:

- **Puntatori a distanza**

  Questi tipi di puntatori vengono usati per interagire con gli oggetti lontani dall'utente (l'esterno è definito semplicemente come "non vicino"). Questi tipi di puntatori in genere eseguono il cast delle linee che possono andare lontano nel mondo e consentono all'utente di interagire con gli oggetti che non sono immediatamente accanto a essi.

- **Near puntatori**

  Questi tipi di puntatori vengono usati per interagire con gli oggetti che sono sufficientemente vicini all'utente per acquisire, toccare e modificare. In genere, questi tipi di puntatori interagiscono con gli oggetti cercando oggetti nelle vicinanze vicine (eseguendo Raycasting a distanze ridotte, eseguendo il cast sferico cercando gli oggetti in prossimità o enumerando elenchi di oggetti che sono considerati catturabili/toccabili).

- **Puntatori Teleport**

  Questi tipi di puntatori si collegano al sistema di Teleportation per gestire lo spostamento dell'utente nella posizione di destinazione dell'indicatore di misura.

## <a name="pointer-mediation"></a>Mediazione puntatore

Poiché un singolo controller può avere più puntatori (ad esempio, la mano articolata può avere puntatori di interazione near e lontani), esiste un componente responsabile della mediazione del puntatore attivo.

Ad esempio, quando la mano dell'utente si avvicina a un pulsante stampabile, [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) deve interrompere la visualizzazione e [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) deve essere attivato.

Questo è gestito da [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) , che è responsabile della determinazione dei puntatori attivi, in base allo stato di tutti i puntatori. Uno degli elementi chiave è la disabilitazione di puntatori lontani quando un puntatore vicino è vicino a un oggetto (vedere [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ).

È possibile fornire un'implementazione alternativa del Mediator del puntatore modificando la [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) proprietà sul profilo del puntatore.

### <a name="how-to-disable-pointers"></a>Come disabilitare i puntatori

Poiché il Mediator del puntatore esegue ogni frame, termina il controllo dello stato attivo/inattivo di tutti i puntatori. Se pertanto si imposta la proprietà IsInteractionEnabled di un puntatore nel codice, questa verrà sovrascritta dal Mediatore del puntatore a ogni frame. In alternativa, è possibile specificare [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) per controllare se i puntatori devono essere attivati o disattivati. Si noti che questo funzionerà solo se si usano le impostazioni predefinite [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) e [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK.

#### <a name="example-disable-hand-rays-in-mrtk"></a>Esempio: disabilitare i raggi mano in MRTK

Il codice seguente disattiva i raggi mano in MRTK:

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

Il codice seguente restituirà i raggi di mano al comportamento predefinito in MRTK:

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

Il codice seguente forza l'utilizzo dei raggi di mano, indipendentemente dal fatto che si avvicini a un'acquisizione:

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) Per altri esempi, vedere e.

### <a name="focusprovider"></a>FocusProvider

[`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)È il compito che è responsabile dell'iterazione dell'elenco di tutti i puntatori e di capire quale sia l'oggetto mirato per ogni puntatore.

In ogni `Update()` chiamata verrà:

1. Aggiornare tutti i puntatori, da Raycasting ed eseguire il rilevamento dei riscontri come configurati dal puntatore stesso. ad esempio, il puntatore a sfera potrebbe specificare SphereOverlap raycastMode, quindi FocusProvider eseguirà un conflitto basato su sfera)

2. Aggiornare l'oggetto con lo stato attivo per ogni puntatore (ad esempio, se un oggetto ha ottenuto lo stato attivo, genera anche gli eventi per tali oggetti, se un oggetto ha perso lo stato attivo, potrebbe attivare la perdita dello stato attivo e così via).

### <a name="pointer-configuration-and-lifecycle"></a>Configurazione e ciclo di vita del puntatore

I [puntatori possono essere configurati](../../features/Input/Pointers.md) nella sezione *puntatori* del profilo di sistema di input.

La durata di un puntatore è generalmente la seguente:

1. Una gestione dispositivi rileverà la presenza di un controller. Questo gestore di dispositivi creerà quindi il set di puntatori associati al controller tramite una chiamata a [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .

2. FocusProvider, nel ciclo di aggiornamento (), eseguirà l'iterazione di tutti i puntatori validi ed eseguirà la logica di rilevamento Raycast o hit associato. Viene utilizzato per determinare l'oggetto che è stato concentrato da ogni particolare puntatore.

    - Poiché è possibile avere più origini di input attive allo stesso tempo (ad esempio, due mani attive presenti), è anche possibile avere più oggetti con lo stato attivo nello stesso momento.

3. Gestione dispositivi, quando si scopre che un'origine del controller è stata persa, chiuderà i puntatori associati al controller perso.
