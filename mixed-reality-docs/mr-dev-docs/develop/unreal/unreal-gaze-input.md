---
title: Input di sguardi in Unreal
description: Esercitazione sulla configurazione dell'input di sguardi per HoloLens e Unreal Engine
author: hferrone
ms.author: jacksonf
ms.date: 06/10/2020
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, HoloLens 2, rilevamento degli occhi, input di sguardi, visualizzazione montata su schermo, Unreal Engine, auricolare realtà mista, auricolare della realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: d0470c5abbefce797254aa9f2030519d3347aaab
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96578890"
---
# <a name="gaze-input"></a><span data-ttu-id="ce161-104">Input sguardo</span><span class="sxs-lookup"><span data-stu-id="ce161-104">Gaze Input</span></span>

<span data-ttu-id="ce161-105">Lo sguardo viene usato per indicare l'aspetto dell'utente.</span><span class="sxs-lookup"><span data-stu-id="ce161-105">Gaze is used to indicate what the user is looking at.</span></span>  <span data-ttu-id="ce161-106">Questo usa le telecamere di rilevamento degli occhi sul dispositivo per trovare un raggio nello spazio non reale che corrisponde a quello che l'utente sta attualmente cercando.</span><span class="sxs-lookup"><span data-stu-id="ce161-106">This uses the eye tracking cameras on the device to find a ray in Unreal world space matching what the user is currently looking at.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="ce161-107">Abilitazione del rilevamento degli occhi</span><span class="sxs-lookup"><span data-stu-id="ce161-107">Enabling eye tracking</span></span>

- <span data-ttu-id="ce161-108">In **Impostazioni progetto > HoloLens** abilitare la funzionalità di **input di sguardi** :</span><span class="sxs-lookup"><span data-stu-id="ce161-108">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![Screenshot delle funzionalità di impostazione del progetto HoloLens con l'input dello sguardo evidenziato](images/unreal-gaze-img-01.png)

- <span data-ttu-id="ce161-110">Crea un nuovo attore e aggiungilo alla tua scena</span><span class="sxs-lookup"><span data-stu-id="ce161-110">Create a new actor and add it to your scene</span></span>

> [!NOTE] 
> <span data-ttu-id="ce161-111">HoloLens Eye Tracking in Unreal ha solo un singolo raggio di sguardi per entrambi gli occhi anziché i due raggi necessari per il rilevamento stereoscopico, che non è supportato.</span><span class="sxs-lookup"><span data-stu-id="ce161-111">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="ce161-112">Uso del tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="ce161-112">Using eye tracking</span></span>

<span data-ttu-id="ce161-113">Verificare prima di tutto che il dispositivo supporti la verifica degli occhi con la funzione IsEyeTrackerConnected.</span><span class="sxs-lookup"><span data-stu-id="ce161-113">First check that the device supports eye tracking with the IsEyeTrackerConnected function.</span></span>  <span data-ttu-id="ce161-114">Se restituisce true, chiamare GetGazeData per trovare la posizione in cui si trovano gli occhi dell'utente durante il frame corrente:</span><span class="sxs-lookup"><span data-stu-id="ce161-114">If this returns true, call GetGazeData to find where the user’s eyes are looking at during the current frame:</span></span>

![Progetto della funzione di rilevamento degli occhi connessa](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="ce161-116">Il punto di fissaggio e il valore di confidenza non sono disponibili in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ce161-116">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="ce161-117">Per trovare le informazioni che l'utente sta osservando, usare l'origine e la direzione degli sguardi in una traccia di riga.</span><span class="sxs-lookup"><span data-stu-id="ce161-117">To find what the user is looking at, use the gaze origin and direction in a line trace.</span></span>  <span data-ttu-id="ce161-118">L'inizio di questo vettore è l'origine dello sguardo e la fine è l'origine più la direzione dello sguardo moltiplicata per la distanza desiderata:</span><span class="sxs-lookup"><span data-stu-id="ce161-118">The start of this vector is the gaze origin and the end is the origin plus the gaze direction multiplied by the desired distance:</span></span>

![Progetto della funzione Get sguardi data](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="ce161-120">Recupero dell'orientamento della testa</span><span class="sxs-lookup"><span data-stu-id="ce161-120">Getting head orientation</span></span>

<span data-ttu-id="ce161-121">In alternativa, è possibile usare la rotazione HMD per rappresentare la direzione della testa dell'utente.</span><span class="sxs-lookup"><span data-stu-id="ce161-121">Alternatively, the HMD rotation can be used to represent the direction of the user’s head.</span></span>  <span data-ttu-id="ce161-122">Questa operazione non richiede la funzionalità di input di sguardi, ma non fornisce informazioni di rilevamento degli occhi.</span><span class="sxs-lookup"><span data-stu-id="ce161-122">This does not require the Gaze Input capability but won't give you any eye tracking information.</span></span>  <span data-ttu-id="ce161-123">Per ottenere i dati di output corretti, è necessario aggiungere un riferimento al progetto come contesto globale:</span><span class="sxs-lookup"><span data-stu-id="ce161-123">A reference to the blueprint must be added as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="ce161-124">Il recupero dei dati di HMD è disponibile solo in Unreal 4,26 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce161-124">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Progetto della funzione Get HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="ce161-126">Utilizzo di C++</span><span class="sxs-lookup"><span data-stu-id="ce161-126">Using C++</span></span> 

- <span data-ttu-id="ce161-127">Nel file build.cs del gioco aggiungere "EyeTracker" all'elenco PublicDependencyModuleNames:</span><span class="sxs-lookup"><span data-stu-id="ce161-127">In your game’s build.cs file, add “EyeTracker” to the PublicDependencyModuleNames list:</span></span>

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

- <span data-ttu-id="ce161-128">In "file/nuova classe C++" creare un nuovo attore C++ denominato "EyeTracker"</span><span class="sxs-lookup"><span data-stu-id="ce161-128">In “File/ New C++ Class”, Create a new C++ actor called “EyeTracker”</span></span>
    - <span data-ttu-id="ce161-129">Una soluzione di Visual Studio si aprirà alla nuova classe EyeTracker.</span><span class="sxs-lookup"><span data-stu-id="ce161-129">A Visual Studio solution will open to the new EyeTracker class.</span></span> <span data-ttu-id="ce161-130">Compilare ed eseguire per aprire il gioco Unreal con il nuovo attore EyeTracker.</span><span class="sxs-lookup"><span data-stu-id="ce161-130">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="ce161-131">Cercare "EyeTracker" nella finestra "Place Actors".</span><span class="sxs-lookup"><span data-stu-id="ce161-131">Search for “EyeTracker” in the “Place Actors” window.</span></span>  <span data-ttu-id="ce161-132">Trascinare e rilasciare questa classe nella finestra del gioco per aggiungerla al progetto:</span><span class="sxs-lookup"><span data-stu-id="ce161-132">Drag and drop this class into the game window to add it to the project:</span></span>

![Screenshot di un attore con la finestra posiziona attore aperta](images/unreal-gaze-img-06.png)

- <span data-ttu-id="ce161-134">In EyeTracker. cpp aggiungere inclusioni per EyeTrackerFunctionLibrary e DrawDebugHelpers:</span><span class="sxs-lookup"><span data-stu-id="ce161-134">In EyeTracker.cpp, add includes for EyeTrackerFunctionLibrary, and DrawDebugHelpers:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="ce161-135">In segno di spunta verificare che il dispositivo supporti la verifica degli occhi con UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected.</span><span class="sxs-lookup"><span data-stu-id="ce161-135">In Tick, check that the device supports eye tracking with UEyeTrackerFunctionLibrary::IsEyeTrackerConnected.</span></span>  <span data-ttu-id="ce161-136">Individuare quindi l'inizio e la fine di un raggio per una traccia di linea da UEyeTrackerFunctionLibrary:: GetGazeData:</span><span class="sxs-lookup"><span data-stu-id="ce161-136">Then find the start and end of a ray for a line trace from UEyeTrackerFunctionLibrary::GetGazeData:</span></span>

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

## <a name="next-development-checkpoint"></a><span data-ttu-id="ce161-137">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="ce161-137">Next Development Checkpoint</span></span>

<span data-ttu-id="ce161-138">Se si segue il percorso di checkpoint per lo sviluppo con Unreal che è stato delineato, si stanno esplorando i blocchi predefiniti fondamentali di MRTK.</span><span class="sxs-lookup"><span data-stu-id="ce161-138">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="ce161-139">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="ce161-139">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="ce161-140">Tracciamento mano</span><span class="sxs-lookup"><span data-stu-id="ce161-140">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="ce161-141">In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="ce161-141">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ce161-142">Fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="ce161-142">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="ce161-143">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="ce161-143">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce161-144">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ce161-144">See also</span></span>
* [<span data-ttu-id="ce161-145">Calibrazione</span><span class="sxs-lookup"><span data-stu-id="ce161-145">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="ce161-146">Comodità</span><span class="sxs-lookup"><span data-stu-id="ce161-146">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="ce161-147">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="ce161-147">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="ce161-148">Input vocale</span><span class="sxs-lookup"><span data-stu-id="ce161-148">Voice input</span></span>](../../out-of-scope/voice-design.md)
