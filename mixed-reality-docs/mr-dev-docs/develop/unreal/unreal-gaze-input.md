---
title: Input di sguardi in Unreal
description: Esercitazione sulla configurazione dell'input di sguardi per HoloLens e Unreal Engine
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, HoloLens 2, rilevamento degli occhi, input di sguardi, visualizzazione montata su schermo, Unreal Engine, auricolare realtà mista, auricolare della realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: a11573d732e739068dca8c42dd8688c0705fc5bb
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925992"
---
# <a name="gaze-input"></a>Input sguardo

L'input di sguardi nelle app di realtà mista sta per scoprire cosa si sta osservando gli utenti. Quando le telecamere di rilevamento degli occhi sul dispositivo corrispondono a raggi nello spazio globale non reale, i dati della linea di visione dell'utente diventano disponibili. Lo sguardo può essere usato sia in progetti sia in C++ ed è una funzionalità di base per i meccanismi come l'interazione tra oggetti, la ricerca e i controlli della fotocamera.

## <a name="enabling-eye-tracking"></a>Abilitazione del rilevamento degli occhi

- In **Impostazioni progetto > HoloLens** abilitare la funzionalità di **input di sguardi** :

![Screenshot delle funzionalità di impostazione del progetto HoloLens con l'input dello sguardo evidenziato](images/unreal-gaze-img-01.png)

- Crea un nuovo attore e aggiungilo alla tua scena

> [!NOTE]
> HoloLens Eye Tracking in Unreal ha un singolo raggio di sguardi per entrambi gli occhi. Il rilevamento stereoscopico, che richiede due raggi, non è supportato.

## <a name="using-eye-tracking"></a>Uso del tracciamento oculare

Verificare prima di tutto che il dispositivo supporti la verifica degli occhi con la funzione **IsEyeTrackerConnected** .  Se la funzione restituisce true, chiamare **GetGazeData** per trovare il punto in cui gli occhi dell'utente stanno esaminando nel frame corrente:

![Progetto della funzione di rilevamento degli occhi connessa](images/unreal-gaze-img-02.png)

> [!NOTE]
> Il punto di fissaggio e il valore di confidenza non sono disponibili in HoloLens.

Usare l'origine e la direzione degli sguardi in una traccia di linea per individuare esattamente il punto in cui gli utenti stanno cercando.  Il valore dello sguardo è un vettore, a partire dall'origine dello sguardo e termina dall'origine più la direzione dello sguardo moltiplicata per la distanza di traccia della riga:

![Progetto della funzione Get sguardi data](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>Recupero dell'orientamento della testa

È anche possibile usare la rotazione della visualizzazione a capo montato (HMD) per rappresentare la direzione della testa dell'utente. È possibile ottenere la direzione degli utenti senza abilitare la funzionalità di input di sguardi, ma non vengono fornite informazioni di rilevamento degli occhi.  Aggiungere un riferimento al progetto come contesto globale per ottenere i dati di output corretti:

> [!NOTE]
> Il recupero dei dati di HMD è disponibile solo in Unreal 4,26 e versioni successive.

![Progetto della funzione Get HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>Utilizzo di C++

- Nel file **Build.cs** del gioco aggiungere **EyeTracker** all'elenco **PublicDependencyModuleNames** :

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

- In **file/nuova classe c++** creare un nuovo attore C++ denominato **EyeTracker**
    - Una soluzione di Visual Studio apre la nuova classe EyeTracker. Compilare ed eseguire per aprire il gioco Unreal con il nuovo attore EyeTracker.  Cercare "EyeTracker" nella finestra **posiziona attori** e trascinare la classe nella finestra del gioco per aggiungerla al progetto:

![Screenshot di un attore con la finestra posiziona attore aperta](images/unreal-gaze-img-06.png)

- In **EyeTracker. cpp** aggiungere inclusioni per **EyeTrackerFunctionLibrary** e **DrawDebugHelpers**:

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

Verificare che il dispositivo supporti la verifica degli occhi con **UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected** prima di provare a ottenere i dati di sguardi.  Se è supportata la verifica degli occhi, trovare l'inizio e la fine di un raggio per una traccia di linea da **UEyeTrackerFunctionLibrary:: GetGazeData**. Da qui è possibile costruire un vettore di sguardi e passare il relativo contenuto a **LineTraceSingleByChannel** per eseguire il debug di tutti i risultati del raggio:

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

Se si sta seguendo il percorso di sviluppo non reale, si sta per esplorare i blocchi predefiniti di MRTK core. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Tracciamento mano](unreal-hand-tracking.md)

In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Fotocamera HoloLens](unreal-hololens-camera.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Calibrazione](../../calibration.md)
* [Comodità](../../design/comfort.md)
* [Sguardo e commit](../../design/gaze-and-commit.md)
* [Input vocale](../../out-of-scope/voice-design.md)
