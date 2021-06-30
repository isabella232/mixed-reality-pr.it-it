---
title: Controller, puntatori e stato attivo
description: Interazione con controller, puntatori e stato attivo.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, puntatori, controller
ms.openlocfilehash: b3e4438c1318abbc60606bcbca42854edae28167
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121619"
---
# <a name="controllers-pointers-and-focus"></a>Controller, puntatori e stato attivo

Controller, puntatori e stato attivo sono concetti di livello superiore che si basano sulle basi stabilite dal sistema di input principale. Insieme, forniscono una grande parte del meccanismo per l'interazione con gli oggetti nella scena.

## <a name="controllers"></a>Controllers

I controller sono rappresentazioni di un controller fisico (6 gradi di libertà, mano articolata e così via). Vengono creati dai gestori di dispositivi e sono responsabili della comunicazione con il sistema sottostante corrispondente e della traduzione di tali dati in dati ed eventi a forma di MRTK.

Ad esempio, nella piattaforma Windows Mixed Reality, è un controller responsabile dell'interfaccia con le API di rilevamento della mano di Windows sottostanti per ottenere informazioni su giunzioni, pose e altre proprietà della [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) mano. [](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) È responsabile della trasformazione di questi dati in eventi MRTK pertinenti ,ad esempio chiamando RaisePoseInputChanged o RaiseHandJointsUpdated, e aggiornando il proprio stato interno in modo che le query per restituiranno i dati [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) corretti.

In genere, il ciclo di vita di un controller comporta:

1. Un controller viene creato da un gestore di dispositivi al rilevamento di una nuova origine( ad esempio, il gestore dei dispositivi rileva e inizia a rilevare una mano).

2. Nel ciclo Update() del controller chiama il sistema API sottostante.

3. Nello stesso ciclo di aggiornamento, genera modifiche all'evento di input chiamando direttamente nel sistema di input principale stesso,ad esempio generando HandMeshUpdated o HandJointsUpdated.

## <a name="pointers-and-focus"></a>Puntatori e stato attivo

I puntatori vengono usati per interagire con gli oggetti di gioco. Questa sezione descrive come vengono creati i puntatori, come vengono aggiornati e come determinano gli oggetti che sono nello stato attivo. Verranno inoltre descritti i diversi tipi di puntatori esistenti e gli scenari in cui sono attivi.

### <a name="pointer-categories"></a>Categorie di puntatori

I puntatori rientrano in genere in una delle categorie seguenti:

- **Puntatori lontano**

  Questi tipi di puntatori vengono usati per interagire con oggetti che sono lontani dall'utente (lontano è definito semplicemente "non vicino"). Questi tipi di puntatori in genere esereranno il cast di righe che possono andare lontano nel mondo e consentire all'utente di interagire e modificare gli oggetti che non sono immediatamente accanto a essi.

- **Vicino ai puntatori**

  Questi tipi di puntatori vengono usati per interagire con oggetti abbastanza vicini all'utente da afferrare, toccare e manipolare. In genere, questi tipi di puntatori interagiscono con gli oggetti cercando gli oggetti nelle vicinanze (eseguendo il raycasting a piccole distanze, eseguendo il cast sferico alla ricerca di oggetti nelle vicinanze o enumerando elenchi di oggetti considerati afferrabili/toccabili).

- **Puntatori di teletrasporto**

  Questi tipi di puntatori si collegano al sistema di teletrasporto per gestire lo spostamento dell'utente nella posizione di destinazione del puntatore.

## <a name="pointer-mediation"></a>Mediazione dei puntatori

Poiché un singolo controller può avere più puntatori (ad esempio, la mano articolata può avere puntatori di interazione sia vicino che lontano), esiste un componente responsabile della mediazione del puntatore che deve essere attivo.

Ad esempio, quando la mano dell'utente si avvicina a un pulsante pressabile, l'oggetto dovrebbe smettere di essere visualizzato e [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) l'oggetto deve essere attivato.

Viene gestito da , responsabile della determinazione dei puntatori attivi, in base [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) allo stato di tutti i puntatori. Una delle operazioni principali è disabilitare i puntatori lontano quando un puntatore vicino è vicino a un oggetto (vedere [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ).

È possibile fornire un'implementazione alternativa del mediatore puntatore modificando la [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) proprietà nel profilo del puntatore.

### <a name="how-to-disable-pointers"></a>Come disabilitare i puntatori

Poiché il mediatore di puntatori esegue ogni frame, finisce per controllare lo stato attivo/inattivo di tutti i puntatori. Pertanto, se si imposta la proprietà IsInteractionEnabled di un puntatore nel codice, il mediatore del puntatore verrà sovrascritto da ogni frame. È invece possibile specificare per [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) controllare se i puntatori devono essere spenti o spenti manualmente. Si noti che questa operazione funzionerà solo se si usa l'impostazione [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) predefinita e [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK.

#### <a name="example-disable-hand-rays-in-mrtk"></a>Esempio: Disabilitare i raggi della mano in MRTK

Il codice seguente disattiva i raggi della mano in MRTK:

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

Il codice seguente restituirà i raggi della mano al comportamento predefinito in MRTK:

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

Il codice seguente forza l'azione dei raggi della mano, indipendentemente dal fatto che sia vicino a un oggetto afferrabile:

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

Per [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) altri [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) esempi, vedere e .

### <a name="focusprovider"></a>FocusProvider

è il workhorse responsabile dell'esecuzione dell'iter sull'elenco di tutti i puntatori e di descrizione dell'oggetto attivo [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) per ogni puntatore.

In ogni `Update()` chiamata verrà:

1. Aggiornare tutti i puntatori, eseguendo il raycasting e eseguendo il rilevamento degli hit come configurato dal puntatore stesso (ad esempio, il puntatore sphere potrebbe specificare SphereOverlap raycastMode, in modo che FocusProvider eserciti una collisione basata su sfera)

2. Aggiornare l'oggetto attivo in base al puntatore(ad esempio, se un oggetto ottiene lo stato attivo, attiva anche eventi per tali oggetti, se un oggetto perde lo stato attivo, attiva lo stato attivo perso e così via).

### <a name="pointer-configuration-and-lifecycle"></a>Configurazione e ciclo di vita del puntatore

[I puntatori possono essere configurati](../features/input/pointers.md) nella *sezione Puntatori* del profilo di sistema di input.

La durata di un puntatore è in genere la seguente:

1. Un gestore di dispositivi rileverà la presenza di un controller. Questo gestore di dispositivi creerà quindi il set di puntatori associati al controller tramite una chiamata a [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .

2. FocusProvider, nel ciclo Update(), esegue l'iterazione su tutti i puntatori validi ed esegue la logica di rilevamento raycast o hit associata. Viene usato per determinare l'oggetto con lo stato attivo da ogni particolare puntatore.

    - Poiché è possibile avere più origini di input attive contemporaneamente (ad esempio, due mani attive), è anche possibile avere più oggetti che hanno lo stato attivo contemporaneamente.

3. Gestione dispositivi, dopo aver scoperto che un'origine del controller è stata persa, errerà i puntatori associati al controller perso.