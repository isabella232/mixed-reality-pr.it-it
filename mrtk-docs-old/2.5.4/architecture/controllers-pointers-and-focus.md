---
title: ControllersPointersAndFocus
description: Interazione con controller, puntatori e stato attivo.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, puntatori, controller
ms.openlocfilehash: cc759c827f864c7c53d4b12b284ad4b89d2db9fdebe9e08a25dd3d62b16b6e4a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187629"
---
# <a name="controllers-pointers-and-focus"></a>Controller, puntatori e stato attivo

Controller, puntatori e messa a fuoco sono concetti di livello superiore che si basano sulle basi stabilite dal sistema di input di base. Insieme, forniscono una parte significativa del meccanismo per l'interazione con gli oggetti nella scena.

## <a name="controllers"></a>Controllers

I controller sono rappresentazioni di un controller fisico (6 gradi di libertà, mano articolata e così via). Vengono creati dai gestori di dispositivi e sono responsabili della comunicazione con il sistema sottostante corrispondente e della conversione dei dati in dati ed eventi a forma di MRTK.

Nella piattaforma Windows Mixed Reality, ad esempio, è un controller responsabile dell'interconnessione con le API di tracciamento della mano Windows sottostanti per ottenere informazioni su giunzioni, posizione e altre proprietà della [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) mano. [](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) È responsabile della trasformazione di questi dati in eventi MRTK pertinenti (ad esempio, chiamando RaisePoseInputChanged o RaiseHandJointsUpdated) e dell'aggiornamento del proprio stato interno in modo che le query per restituiranno i dati [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose(TrackedHandJoint,Handedness,MixedRealityPose@)) corretti.

In genere, il ciclo di vita di un controller comporterà:

1. Un controller viene creato da un gestore di dispositivi al rilevamento di una nuova origine (ad esempio, gestione dispositivi rileva e inizia a tenere traccia di una mano).

2. Nel ciclo Update() del controller chiama nel sistema API sottostante.

3. Nello stesso ciclo di aggiornamento genera modifiche all'evento di input chiamando direttamente nel sistema di input principale stesso(ad esempio, generando HandMeshUpdated o HandJointsUpdated).

## <a name="pointers-and-focus"></a>Puntatori e stato attivo

I puntatori vengono usati per interagire con gli oggetti gioco. Questa sezione descrive come vengono creati i puntatori, come vengono aggiornati e come determinano gli oggetti che sono nello stato attivo. Verranno inoltre descritti i diversi tipi di puntatori esistenti e gli scenari in cui sono attivi.

### <a name="pointer-categories"></a>Categorie di puntatori

I puntatori rientrano in genere in una delle categorie seguenti:

- **Puntatori far**

  Questi tipi di puntatori vengono usati per interagire con oggetti che sono distorsi dall'utente (molto lontano è definito semplicemente "non vicino"). Questi tipi di puntatori in genere eseranno il cast di righe che possono andare lontano nel mondo e consentire all'utente di interagire con gli oggetti che non sono immediatamente accanto a essi e modificarli.

- **Puntatori vicini**

  Questi tipi di puntatori vengono usati per interagire con oggetti abbastanza vicini all'utente da afferrare, toccare e manipolare. In genere, questi tipi di puntatori interagiscono con gli oggetti cercando oggetti nelle vicinanze (eseguendo il raycasting a piccole distanze, eseguendo il cast sferico alla ricerca di oggetti nelle vicinanze o enumerando elenchi di oggetti considerati afferrabili/toccabili).

- **Puntatori di teletrasporto**

  Questi tipi di puntatori si collegano al sistema di teletrasporto per gestire lo spostamento dell'utente nella posizione di destinazione dell'indicatore di misura.

## <a name="pointer-mediation"></a>Puntatore a puntatore

Poiché un singolo controller può avere più puntatori (ad esempio, la mano articolata può avere puntatori di interazione da vicino e da lontano), esiste un componente responsabile della mediazione del puntatore che deve essere attivo.

Ad esempio, quando la mano dell'utente si avvicina a un pulsante a pressione, l'elemento dovrebbe smettere di essere [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) visualizzato e deve essere [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) attivato.

Questa operazione viene gestita da , responsabile della determinazione dei puntatori attivi, in base [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) allo stato di tutti i puntatori. Una delle operazioni principali è disabilitare i puntatori da lontano quando un puntatore vicino è vicino a un oggetto (vedere [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ).

È possibile fornire un'implementazione alternativa del mediatore del puntatore modificando la [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) proprietà nel profilo del puntatore.

### <a name="how-to-disable-pointers"></a>Come disabilitare i puntatori

Poiché il mediatore di puntatori esegue ogni frame, finisce per controllare lo stato attivo/inattivo di tutti i puntatori. Pertanto, se si imposta la proprietà IsInteractionEnabled di un puntatore nel codice, il mediatore del puntatore verrà sovrascritto da ogni fotogramma. È invece possibile specificare per [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) controllare se i puntatori devono essere spenti o spenti manualmente. Si noti che questa operazione funziona solo se si usa l'impostazione [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) predefinita e [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK.

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

è la workhorse responsabile dell'esecuzione dell'iterazione dell'elenco di tutti i puntatori e della ricerca dell'oggetto con lo stato attivo [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) per ogni puntatore.

In ogni `Update()` chiamata:

1. Aggiornare tutti i puntatori, eseguendo il raycasting e il rilevamento degli hit come configurato dal puntatore stesso (ad esempio, il puntatore a sfera potrebbe specificare SphereOverlap raycastMode, in modo che FocusProvider eserciti una collisione basata su sfera)

2. Aggiornare l'oggetto con lo stato attivo in base al puntatore(ad esempio, se un oggetto ottiene lo stato attivo, attiva anche eventi per tali oggetti, se un oggetto perde lo stato attivo, attiva lo stato attivo perso e così via).

### <a name="pointer-configuration-and-lifecycle"></a>Configurazione e ciclo di vita dei puntatori

[I puntatori possono essere configurati](../features/input/pointers.md) nella *sezione Puntatori* del profilo del sistema di input.

La durata di un puntatore è in genere la seguente:

1. Gestione dispositivi rileverà la presenza di un controller. Questo gestore di dispositivi creerà quindi il set di puntatori associati al controller tramite una chiamata a [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .

2. FocusProvider, nel ciclo Update(), esegue l'iterazione su tutti i puntatori validi ed esegue il raycast associato o la logica di rilevamento degli hit. Viene utilizzato per determinare l'oggetto con lo stato attivo da ogni puntatore specifico.

    - Poiché è possibile avere più origini di input attive contemporaneamente (ad esempio, due mani attive), è anche possibile avere più oggetti con lo stato attivo contemporaneamente.

3. Gestione dispositivi, dopo aver scoperto che un'origine del controller è stata persa, i puntatori associati al controller perso verranno disattesi.
