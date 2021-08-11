---
title: Input sguardo fisso in Unreal
description: Informazioni su come configurare e usare l'input dello sguardo fisso con il tracciamento oculare e l'orientamento della testa per HoloLens app in Unreal.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality, ologrammi, HoloLens 2, tracciamento oculare, input dello sguardo fisso, display montato con la testa, motore Unreal, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale
ms.openlocfilehash: e423086e293629e3dfadb49b52a376c0b93f5e465328b93f47c2f1e3e0790b63
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200677"
---
# <a name="gaze-input"></a>Input sguardo fisso

L'input dello sguardo fisso nelle app di realtà mista consente di scoprire cosa guardano gli utenti. Quando le fotocamere di tracciamento oculare del dispositivo corrispondono ai raggi nello spazio mondiale di Unreal, i dati della linea di vista dell'utente diventano disponibili. Lo sguardo fisso può essere usato sia nei progetti che in C++, ed è una funzionalità di base per meccanismi come l'interazione con gli oggetti, la ricerca di modi e i controlli della fotocamera.

## <a name="enabling-eye-tracking"></a>Abilitazione del tracciamento oculare

- In **Project Impostazioni > HoloLens** abilitare la funzionalità **Input sguardo** fisso:

![Screenshot delle funzionalità HoloLens di impostazione del progetto con l'input dello sguardo fisso evidenziato](images/unreal-gaze-img-01.png)

- Creare un nuovo attore e aggiungerlo alla scena

> [!NOTE]
> HoloLens tracciamento oculare in Unreal ha un solo raggio dello sguardo per entrambi gli occhi. Il rilevamento stereoscopico, che richiede due raggi, non è supportato.

## <a name="using-eye-tracking"></a>Uso del tracciamento oculare

Verificare prima di tutto che il dispositivo supporti il tracciamento oculare **con la funzione IsEyeTrackerConnected.**  Se la funzione restituisce true, chiamare **GetGazeData** per trovare il punto in cui gli occhi dell'utente guardano nel frame corrente:

![Progetto della funzione connessa is eye tracking](images/unreal-gaze-img-02.png)

> [!NOTE]
> Il punto di correzione e il valore di confidenza non sono disponibili in HoloLens.

Usare l'origine e la direzione dello sguardo fisso in una traccia di linea per individuare esattamente la posizione di ricerca degli utenti.  Il valore dello sguardo fisso è un vettore, a partire dall'origine dello sguardo fisso e terminando in corrispondenza dell'origine più la direzione dello sguardo fisso moltiplicata per la distanza di traccia della linea:

![Progetto della funzione Get Gaze Data](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>Ottenere l'orientamento della testa

È anche possibile usare la rotazione del display HMD (Head Mounted Display) per rappresentare la direzione della testa dell'utente. È possibile ottenere la direzione della testa degli utenti senza abilitare la funzionalità Input sguardo fisso, ma non si otterrà alcuna informazione sul tracciamento oculare.  Aggiungere un riferimento al progetto come contesto mondiale per ottenere i dati di output corretti:

> [!NOTE]
> Il recupero dei dati HMD è disponibile solo in Unreal 4.26 e in altri.

![Progetto della funzione Get HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>Utilizzo di C++

- Nel file **build.cs del gioco** aggiungere **EyeTracker** all'elenco **PublicDependencyModuleNames:**

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "EyeTracker"
});
```

- In **File/Nuova classe C++** creare un nuovo attore C++ denominato **EyeTracker**
    - Una Visual Studio soluzione aprirà la nuova classe EyeTracker. Compila ed esegui per aprire il gioco Unreal con il nuovo attore EyeTracker.  Cercare "EyeTracker" nella finestra **Place Actors** e trascinare e rilasciare la classe nella finestra del gioco per aggiungerla al progetto:

![Screenshot di un attore con la finestra place actor aperta](images/unreal-gaze-img-06.png)

- In **EyeTracker.cpp** aggiungere include per **EyeTrackerFunctionLibrary** e **DrawDebugHelpers:**

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

Verificare che il dispositivo supporti il tracciamento oculare **con UEyeTrackerFunctionLibrary::IsEyeTrackerConnected** prima di provare a ottenere i dati dello sguardo fisso.  Se il tracciamento oculare è supportato, trovare l'inizio e la fine di un raggio per una traccia di linea da **UEyeTrackerFunctionLibrary::GetGazeData**. Da qui, è possibile costruire un vettore di sguardo fisso e passarne il contenuto **a LineTraceSingleByChannel per** eseguire il debug di qualsiasi risultato di raggi:

```cpp
void AEyeTracker::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    if(UEyeTrackerFunctionLibrary::IsEyeTrackerConnected())
    {
        FEyeTrackerGazeData GazeData;
        if(UEyeTrackerFunctionLibrary::GetGazeData(GazeData))
        {
            FVector Start = GazeData.GazeOrigin;
            FVector End = GazeData.GazeOrigin + GazeData.GazeDirection * 100;

            FHitResult Hit Result;
            if (GWorld->LineTraceSingleByChannel(HitResult, Start, End, ECollisionChannel::ECC_Visiblity))
            {
                DrawDebugCoordinateSystem(GWorld, HitResult.Location, FQuat::Identity.Rotator(), 10);
            }
        }
    }
}
```

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si segue il percorso delineato per lo sviluppo con Unreal, tenere presente che si stanno esplorando i blocchi predefiniti fondamentali di MRTK. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Tracciamento mano](unreal-hand-tracking.md)

In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Fotocamera HoloLens](unreal-hololens-camera.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Calibrazione](/hololens/hololens-calibration)
* [Comodità](../../design/comfort.md)
* [Sguardo e commit](../../design/gaze-and-commit.md)
* [Input vocale](../../out-of-scope/voice-design.md)