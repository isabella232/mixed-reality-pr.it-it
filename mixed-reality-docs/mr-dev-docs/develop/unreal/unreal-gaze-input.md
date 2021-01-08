---
title: Input di sguardi in Unreal
description: Informazioni su come configurare e usare l'input di sguardi con la traccia degli occhi e l'orientamento della testa per le app HoloLens in Unreal.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, HoloLens 2, rilevamento degli occhi, input di sguardi, visualizzazione montata su schermo, Unreal Engine, auricolare realtà mista, auricolare della realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: e546867fe02acd5e72ee76b4108a369ec25fd32f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010141"
---
# <a name="gaze-input"></a><span data-ttu-id="9a4ca-104">Input sguardo</span><span class="sxs-lookup"><span data-stu-id="9a4ca-104">Gaze Input</span></span>

<span data-ttu-id="9a4ca-105">L'input di sguardi nelle app di realtà mista sta per scoprire cosa si sta osservando gli utenti.</span><span class="sxs-lookup"><span data-stu-id="9a4ca-105">Gaze input in mixed reality apps is all about finding out what your users are looking at.</span></span> <span data-ttu-id="9a4ca-106">Quando le telecamere di rilevamento degli occhi sul dispositivo corrispondono a raggi nello spazio globale non reale, i dati della linea di visione dell'utente diventano disponibili.</span><span class="sxs-lookup"><span data-stu-id="9a4ca-106">When the eye tracking cameras on your device match up with rays in Unreal's world space, your user's line of sight data becomes available.</span></span> <span data-ttu-id="9a4ca-107">Lo sguardo può essere usato sia in progetti sia in C++ ed è una funzionalità di base per i meccanismi come l'interazione tra oggetti, la ricerca e i controlli della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="9a4ca-107">Gaze can be used in both blueprints and C++, and is a core feature for mechanics like object interaction, way finding, and camera controls.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="9a4ca-108">Abilitazione del rilevamento degli occhi</span><span class="sxs-lookup"><span data-stu-id="9a4ca-108">Enabling eye tracking</span></span>

- <span data-ttu-id="9a4ca-109">In **Impostazioni progetto > HoloLens** abilitare la funzionalità di **input di sguardi** :</span><span class="sxs-lookup"><span data-stu-id="9a4ca-109">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![Screenshot delle funzionalità di impostazione del progetto HoloLens con l'input dello sguardo evidenziato](images/unreal-gaze-img-01.png)

- <span data-ttu-id="9a4ca-111">Crea un nuovo attore e aggiungilo alla tua scena</span><span class="sxs-lookup"><span data-stu-id="9a4ca-111">Create a new actor and add it to your scene</span></span>

> [!NOTE]
> <span data-ttu-id="9a4ca-112">HoloLens Eye Tracking in Unreal ha un singolo raggio di sguardi per entrambi gli occhi.</span><span class="sxs-lookup"><span data-stu-id="9a4ca-112">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes.</span></span> <span data-ttu-id="9a4ca-113">Il rilevamento stereoscopico, che richiede due raggi, non è supportato.</span><span class="sxs-lookup"><span data-stu-id="9a4ca-113">Stereoscopic tracking, which requires two rays, isn't supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="9a4ca-114">Uso del tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="9a4ca-114">Using eye tracking</span></span>

<span data-ttu-id="9a4ca-115">Verificare prima di tutto che il dispositivo supporti la verifica degli occhi con la funzione **IsEyeTrackerConnected** .</span><span class="sxs-lookup"><span data-stu-id="9a4ca-115">First, check that your device supports eye tracking with the **IsEyeTrackerConnected** function.</span></span>  <span data-ttu-id="9a4ca-116">Se la funzione restituisce true, chiamare **GetGazeData** per trovare il punto in cui gli occhi dell'utente stanno esaminando nel frame corrente:</span><span class="sxs-lookup"><span data-stu-id="9a4ca-116">If the function returns true, call **GetGazeData** to find where the user’s eyes are looking at in the current frame:</span></span>

![Progetto della funzione di rilevamento degli occhi connessa](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="9a4ca-118">Il punto di fissaggio e il valore di confidenza non sono disponibili in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9a4ca-118">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="9a4ca-119">Usare l'origine e la direzione degli sguardi in una traccia di linea per individuare esattamente il punto in cui gli utenti stanno cercando.</span><span class="sxs-lookup"><span data-stu-id="9a4ca-119">Use the gaze origin and direction in a line trace to find out exactly where your users are looking.</span></span>  <span data-ttu-id="9a4ca-120">Il valore dello sguardo è un vettore, a partire dall'origine dello sguardo e termina dall'origine più la direzione dello sguardo moltiplicata per la distanza di traccia della riga:</span><span class="sxs-lookup"><span data-stu-id="9a4ca-120">The gaze value is a vector, starting at the gaze origin and ending at the origin plus the gaze direction multiplied by the line trace distance:</span></span>

![Progetto della funzione Get sguardi data](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="9a4ca-122">Recupero dell'orientamento della testa</span><span class="sxs-lookup"><span data-stu-id="9a4ca-122">Getting head orientation</span></span>

<span data-ttu-id="9a4ca-123">È anche possibile usare la rotazione della visualizzazione a capo montato (HMD) per rappresentare la direzione della testa dell'utente.</span><span class="sxs-lookup"><span data-stu-id="9a4ca-123">You can also use the rotation of the Head Mounted Display (HMD) to represent the direction of the user’s head.</span></span> <span data-ttu-id="9a4ca-124">È possibile ottenere la direzione degli utenti senza abilitare la funzionalità di input di sguardi, ma non vengono fornite informazioni di rilevamento degli occhi.</span><span class="sxs-lookup"><span data-stu-id="9a4ca-124">You can get the users head direction without enabling the Gaze Input capability, but you won't get you any eye tracking information.</span></span>  <span data-ttu-id="9a4ca-125">Aggiungere un riferimento al progetto come contesto globale per ottenere i dati di output corretti:</span><span class="sxs-lookup"><span data-stu-id="9a4ca-125">Add a reference to the blueprint as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="9a4ca-126">Il recupero dei dati di HMD è disponibile solo in Unreal 4,26 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="9a4ca-126">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Progetto della funzione Get HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="9a4ca-128">Utilizzo di C++</span><span class="sxs-lookup"><span data-stu-id="9a4ca-128">Using C++</span></span>

- <span data-ttu-id="9a4ca-129">Nel file **Build.cs** del gioco aggiungere **EyeTracker** all'elenco **PublicDependencyModuleNames** :</span><span class="sxs-lookup"><span data-stu-id="9a4ca-129">In your game’s **build.cs** file, add **EyeTracker** to the **PublicDependencyModuleNames** list:</span></span>

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

- <span data-ttu-id="9a4ca-130">In **file/nuova classe c++** creare un nuovo attore C++ denominato **EyeTracker**</span><span class="sxs-lookup"><span data-stu-id="9a4ca-130">In **File/ New C++ Class**, create a new C++ actor called **EyeTracker**</span></span>
    - <span data-ttu-id="9a4ca-131">Una soluzione di Visual Studio apre la nuova classe EyeTracker.</span><span class="sxs-lookup"><span data-stu-id="9a4ca-131">A Visual Studio solution will open up the new EyeTracker class.</span></span> <span data-ttu-id="9a4ca-132">Compilare ed eseguire per aprire il gioco Unreal con il nuovo attore EyeTracker.</span><span class="sxs-lookup"><span data-stu-id="9a4ca-132">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="9a4ca-133">Cercare "EyeTracker" nella finestra **posiziona attori** e trascinare la classe nella finestra del gioco per aggiungerla al progetto:</span><span class="sxs-lookup"><span data-stu-id="9a4ca-133">Search for “EyeTracker” in the **Place Actors** window and drag and drop the class into the game window to add it to the project:</span></span>

![Screenshot di un attore con la finestra posiziona attore aperta](images/unreal-gaze-img-06.png)

- <span data-ttu-id="9a4ca-135">In **EyeTracker. cpp** aggiungere inclusioni per **EyeTrackerFunctionLibrary** e **DrawDebugHelpers**:</span><span class="sxs-lookup"><span data-stu-id="9a4ca-135">In **EyeTracker.cpp**, add includes for **EyeTrackerFunctionLibrary**, and **DrawDebugHelpers**:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="9a4ca-136">Verificare che il dispositivo supporti la verifica degli occhi con **UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected** prima di provare a ottenere i dati di sguardi.</span><span class="sxs-lookup"><span data-stu-id="9a4ca-136">Check that your device supports eye tracking with **UEyeTrackerFunctionLibrary::IsEyeTrackerConnected** before trying to get any gaze data.</span></span>  <span data-ttu-id="9a4ca-137">Se è supportata la verifica degli occhi, trovare l'inizio e la fine di un raggio per una traccia di linea da **UEyeTrackerFunctionLibrary:: GetGazeData**.</span><span class="sxs-lookup"><span data-stu-id="9a4ca-137">If eye tracking is supported, find the start and end of a ray for a line trace from **UEyeTrackerFunctionLibrary::GetGazeData**.</span></span> <span data-ttu-id="9a4ca-138">Da qui è possibile costruire un vettore di sguardi e passare il relativo contenuto a **LineTraceSingleByChannel** per eseguire il debug di tutti i risultati del raggio:</span><span class="sxs-lookup"><span data-stu-id="9a4ca-138">From there, you can construct a gaze vector and pass its contents to **LineTraceSingleByChannel** to debug any ray hit results:</span></span>

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

## <a name="next-development-checkpoint"></a><span data-ttu-id="9a4ca-139">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="9a4ca-139">Next Development Checkpoint</span></span>

<span data-ttu-id="9a4ca-140">Se si segue il percorso delineato per lo sviluppo con Unreal, tenere presente che si stanno esplorando i blocchi predefiniti fondamentali di MRTK.</span><span class="sxs-lookup"><span data-stu-id="9a4ca-140">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="9a4ca-141">Da qui, è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="9a4ca-141">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9a4ca-142">Tracciamento mano</span><span class="sxs-lookup"><span data-stu-id="9a4ca-142">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="9a4ca-143">In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="9a4ca-143">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9a4ca-144">Fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="9a4ca-144">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="9a4ca-145">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="9a4ca-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a4ca-146">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9a4ca-146">See also</span></span>
* [<span data-ttu-id="9a4ca-147">Calibrazione</span><span class="sxs-lookup"><span data-stu-id="9a4ca-147">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="9a4ca-148">Comodità</span><span class="sxs-lookup"><span data-stu-id="9a4ca-148">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="9a4ca-149">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="9a4ca-149">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="9a4ca-150">Input vocale</span><span class="sxs-lookup"><span data-stu-id="9a4ca-150">Voice input</span></span>](../../out-of-scope/voice-design.md)
