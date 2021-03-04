---
title: Sguardo fisso
description: Docummentation sui tipi di sguardo in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sguardo,
ms.openlocfilehash: 8f3f7317cd0bc2bb120328453f1fedf8e27025ca
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781962"
---
# <a name="gaze"></a>Sguardo fisso

[Sguardi](https://docs.microsoft.com/windows/mixed-reality/gaze) è un tipo di input che interagisce con il mondo in base alla posizione dell'utente. Lo sguardo esiste in due diverse varianti

## <a name="head-gaze"></a>Puntamento con la testa

Questo tipo di sguardi è basato sulla direzione che la testa/fotocamera sta osservando. Il punto di vista del controllo è attivo nei sistemi che non supportano gli sguardi, oppure nei casi in cui l'hardware può supportare gli sguardi, ma il set di [autorizzazioni e l'installazione](../EyeTracking/EyeTracking_BasicSetup.md#eye-tracking-requirements-checklist) corretti non sono stati eseguiti.

Lo sguardo a capo è in genere associato alle interazioni di stile HoloLens 1 che coinvolgono l'oggetto, inserendolo al centro del frame olografico e quindi eseguendo il movimento del rubinetto d'aria.

## <a name="eye-gaze"></a>Tracciamento oculare

Questo tipo di sguardi è basato sulla posizione in cui si trovano gli occhi dell'utente. Eye sguardi è presente solo nei sistemi che supportano il rilevamento degli occhi. Per informazioni dettagliate su come usare gli occhi, vedere la [documentazione relativa a Eye Tracking](../EyeTracking/EyeTracking_Main.md) .

## <a name="gazeprovider"></a>GazeProvider

La funzionalità di sguardi (sia Head che Eye) viene fornita da [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider). Questo provider può essere configurato nella sezione *puntatore* del profilo di sistema di input:

![EntryPoint configurazione sguardo](../Images/Input/GazeConfigurationEntrypoint.png)

Analogamente ad altre origini di input, il provider di sguardi interagisce con gli oggetti nella scena tramite l'uso di un puntatore [(vedere questo documento per informazioni sui puntatori)](../../architecture/InputSystem/ControllersPointersAndFocus.md).
Nel caso del provider di sguardi, il relativo puntatore viene implementato tramite `InternalGazePointer` e non è configurato tramite un profilo.

È possibile sostituire il GazeProvider di magazzino con un'implementazione alternativa modificando il *tipo di provider di sguardi* per fare riferimento a una classe diversa che implementa [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) e [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).
È in genere consigliabile usare il GazeProvider di magazzino (e i problemi di archiviazione durante la ricerca dei bug) perché la riimplementazione di GazeProvider non è semplice.

### <a name="alternative-platform-provided-gaze-poses"></a>Pose mirate della piattaforma alternative

Per impostazione predefinita, MRTK GazeProvider usa il centro del frame della fotocamera come origine dello sguardo. Alcune piattaforme, ad esempio la realtà mista di Windows in HoloLens 2, forniscono uno sguardo definito in modo alternativo. Questa operazione viene gestita tramite l' `Use Head Gaze Override` impostazione nelle impostazioni di sguardi. Quando è abilitata, verrà usato l'override di sguardi alternativi. Se questa opzione è disabilitata, verrà utilizzata l'origine di frame Center predefinita. In particolare, per HoloLens 2, l'angolo dello sguardo verrà generato da diversi gradi per tenere conto del comfort degli utenti nell'uso della loro testa per la destinazione.

## <a name="usage"></a>Utilizzo

### <a name="how-get-the-current-gaze-target"></a>Come ottenere la destinazione dello sguardo corrente

In questo esempio viene illustrato come ottenere l'oggetto Game corrente di destinazione dello sguardo dell'utente.

```c#
void LogCurrentGazeTarget()
{
    if (CoreServices.InputSystem.GazeProvider.GazeTarget)
    {
        Debug.Log("User gaze is currently over game object: "
            + CoreServices.InputSystem.GazeProvider.GazeTarget)
    }
}
```

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a>Come ottenere la direzione e l'origine dello sguardo corrente

In questo esempio viene illustrato come ottenere l'oggetto Vector3 che rappresenta la direzione dello sguardo dell'utente e l'origine (il punto da cui la direzione sta per essere).

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
