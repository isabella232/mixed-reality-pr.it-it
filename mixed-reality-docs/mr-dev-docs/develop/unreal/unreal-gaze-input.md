---
title: Input di sguardi in Unreal
description: Esercitazione sulla configurazione dell'input di sguardi per HoloLens e Unreal Engine
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, HoloLens 2, rilevamento degli occhi, input di sguardi, visualizzazione montata su schermo, Unreal Engine, auricolare realtà mista, auricolare della realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: f89638cef6b90e004f097c701c3df13edaf74fac
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354334"
---
# <a name="gaze-input"></a>Input sguardo

Lo sguardo viene usato per indicare l'aspetto dell'utente.  Questo usa le telecamere di rilevamento degli occhi sul dispositivo per trovare un raggio nello spazio non reale che corrisponde a quello che l'utente sta attualmente cercando.

## <a name="enabling-eye-tracking"></a>Abilitazione del rilevamento degli occhi

- In **Impostazioni progetto > HoloLens** abilitare la funzionalità di **input di sguardi** :

![Screenshot delle funzionalità di impostazione del progetto HoloLens con l'input dello sguardo evidenziato](images/unreal-gaze-img-01.png)

- Crea un nuovo attore e aggiungilo alla tua scena

> [!NOTE] 
> HoloLens Eye Tracking in Unreal ha solo un singolo raggio di sguardi per entrambi gli occhi anziché i due raggi necessari per il rilevamento stereoscopico, che non è supportato.

## <a name="using-eye-tracking"></a>Uso del tracciamento oculare

Verificare prima di tutto che il dispositivo supporti la verifica degli occhi con la funzione IsEyeTrackerConnected.  Se restituisce true, chiamare GetGazeData per trovare la posizione in cui si trovano gli occhi dell'utente durante il frame corrente:

![Progetto della funzione di rilevamento degli occhi connessa](images/unreal-gaze-img-02.png)

> [!NOTE]
> Il punto di fissaggio e il valore di confidenza non sono disponibili in HoloLens.

Per trovare le informazioni che l'utente sta osservando, usare l'origine e la direzione degli sguardi in una traccia di riga.  L'inizio di questo vettore è l'origine dello sguardo e la fine è l'origine più la direzione dello sguardo moltiplicata per la distanza desiderata:

![Progetto della funzione Get sguardi data](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>Recupero dell'orientamento della testa

In alternativa, è possibile usare la rotazione HMD per rappresentare la direzione della testa dell'utente.  Questa operazione non richiede la funzionalità di input di sguardi, ma non fornisce informazioni di rilevamento degli occhi.  Per ottenere i dati di output corretti, è necessario aggiungere un riferimento al progetto come contesto globale:

> [!NOTE]
> Il recupero dei dati di HMD è disponibile solo in Unreal 4,26 e versioni successive.

![Progetto della funzione Get HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>Utilizzo di C++ 

- Nel file build.cs del gioco aggiungere "EyeTracker" all'elenco PublicDependencyModuleNames:

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

- In "file/nuova classe C++" creare un nuovo attore C++ denominato "EyeTracker"
    - Una soluzione di Visual Studio si aprirà alla nuova classe EyeTracker. Compilare ed eseguire per aprire il gioco Unreal con il nuovo attore EyeTracker.  Cercare "EyeTracker" nella finestra "Place Actors".  Trascinare e rilasciare questa classe nella finestra del gioco per aggiungerla al progetto:

![Screenshot di un attore con la finestra posiziona attore aperta](images/unreal-gaze-img-06.png)

- In EyeTracker. cpp aggiungere inclusioni per EyeTrackerFunctionLibrary e DrawDebugHelpers:

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

In segno di spunta verificare che il dispositivo supporti la verifica degli occhi con UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected.  Individuare quindi l'inizio e la fine di un raggio per una traccia di linea da UEyeTrackerFunctionLibrary:: GetGazeData:

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

Se si segue il percorso di checkpoint per lo sviluppo con Unreal che è stato delineato, si stanno esplorando i blocchi predefiniti fondamentali di MRTK. Da qui è possibile passare al blocco predefinito successivo: 

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
