---
title: Sguardo fisso
description: Docummentation sui tipi di sguardo fisso in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sguardo,
ms.openlocfilehash: 95dad85ca8154d35f73906b53019d3a52ced546f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176911"
---
# <a name="gaze"></a>Sguardo fisso

[Lo](/windows/mixed-reality/gaze) sguardo fisso è una forma di input che interagisce con il mondo in base alla posizione in cui l'utente sta cercando. Lo sguardo è presente in due diverse versioni

## <a name="head-gaze"></a>Puntamento con la testa

Questo tipo di sguardo è basato sulla direzione che la testa/fotocamera sta osservando. Lo sguardo con la testa è attivo nei sistemi che non supportano lo sguardo fisso o nei casi in cui l'hardware può supportare lo sguardo fisso, ma non è stato eseguito il set di autorizzazioni e la configurazione corrette. [](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist)

Lo sguardo della testa è in genere associato HoloLens interazioni di stile 1 che implicano la visualizzazione dell'oggetto posizionarlo al centro del frame olografico e quindi eseguire il movimento del tocco dell'aria.

## <a name="eye-gaze"></a>Tracciamento oculare

Questo tipo di sguardo si basa sul punto in cui gli occhi dell'utente guardano. Lo sguardo fisso è presente solo nei sistemi che supportano il tracciamento oculare. Per altri [dettagli su come](eye-tracking/eye-tracking-main.md) usare lo sguardo fisso, vedere la documentazione relativa al tracciamento oculare.

## <a name="gazeprovider"></a>GazeProvider

La funzionalità dello sguardo (testa e occhio) viene fornita da [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider). Questo provider può essere configurato nella sezione *Puntatore* del profilo di sistema di input:

![Punto di ingresso di configurazione dello sguardo fisso](../images/input/GazeConfigurationEntrypoint.png)

Analogamente ad altre origini di input, il provider dello sguardo fisso interagisce con gli oggetti nella scena tramite l'uso di un puntatore (vedere questo documento per [informazioni sui puntatori).](../../architecture/controllers-pointers-and-focus.md)
Nel caso del provider di sguardo fisso, il relativo puntatore viene implementato tramite `InternalGazePointer` e non viene configurato tramite un profilo.

È possibile sostituire lo stock GazeProvider con un'implementazione alternativa modificando il tipo di *provider gaze* in modo da fare riferimento a una classe diversa che implementa [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) e [IMixedRealityEyeGazeProvider.](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider)
È in genere consigliabile usare lo stock GazeProvider (e i problemi di archiviazione in durante la ricerca di bug) perché la ri-implementazione di GazeProvider non è semplice.

### <a name="alternative-platform-provided-gaze-poses"></a>Posizioni di sguardo alternative fornite dalla piattaforma

Per impostazione predefinita, MRTK GazeProvider usa il centro della cornice della fotocamera come origine dello sguardo. Alcune piattaforme, ad esempio Windows Mixed Reality su HoloLens 2, forniscono una posizione dello sguardo fisso definita in alternativa. Questa operazione viene gestita tramite `Use Head Gaze Override` l'impostazione nelle impostazioni dello sguardo. Se abilitata, verrà usata la sostituzione dello sguardo alternativo. Se disabilitata, verrà usata l'origine predefinita del centro frame. In particolare, per HoloLens 2, l'angolo dello sguardo fisso verrà aumentato di diversi gradi per motivi di comfort dell'utente nell'uso della testa per il targeting.

## <a name="usage"></a>Utilizzo

### <a name="how-get-the-current-gaze-target"></a>Come ottenere la destinazione dello sguardo corrente

Questo esempio illustra come ottenere l'oggetto di gioco corrente destinato dallo sguardo dell'utente.

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

Questo esempio illustra come ottenere Vector3 che rappresenta la direzione dello sguardo dell'utente e l'origine (il punto da cui sta andando la direzione).

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
