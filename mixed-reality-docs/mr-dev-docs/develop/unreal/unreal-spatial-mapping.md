---
title: Mapping spaziale in Unreal
description: Guida all'uso del mapping spaziale in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, mapping spaziale, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 878eae5f5fd0b7a1630511faa23c1477455ed988
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354379"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="8cf75-104">Mapping spaziale in Unreal</span><span class="sxs-lookup"><span data-stu-id="8cf75-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="8cf75-105">Il mapping spaziale consente di posizionare oggetti sulle superfici reali visualizzando l'ambiente intorno a HoloLens, rendendo gli ologrammi più realistici per l'utente.</span><span class="sxs-lookup"><span data-stu-id="8cf75-105">Spatial mapping makes it possible to place objects on surfaces in the physical world by showing the world around the HoloLens, which makes holograms seem more real to the user.</span></span> <span data-ttu-id="8cf75-106">Il mapping spaziale consente anche di ancorare gli oggetti nel mondo dell'utente sfruttando i segnali di profondità del mondo reale. In questo modo l'utente avrà l'impressione che questi ologrammi si trovino effettivamente nello spazio che lo circonda; gli ologrammi che fluttuano nello spazio o che si muovono insieme all'utente non vengono percepiti come reali.</span><span class="sxs-lookup"><span data-stu-id="8cf75-106">Spatial mapping also anchors objects in the user's world by taking advantage of real world depth cues. This helps convince the user that these holograms are actually in their space; holograms floating in space or moving with the user will not feel as real.</span></span> <span data-ttu-id="8cf75-107">È consigliabile inserire elementi di comfort, quando possibile.</span><span class="sxs-lookup"><span data-stu-id="8cf75-107">You want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="8cf75-108">Per altre informazioni su qualità del mapping spaziale, posizionamento, occlusione, rendering e così via, consulta il documento [Mapping spaziale](../../design/spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="8cf75-108">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](../../design/spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="8cf75-109">Abilitazione del mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="8cf75-109">Enabling Spatial Mapping</span></span>

<span data-ttu-id="8cf75-110">Per abilitare il mapping spaziale in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="8cf75-110">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="8cf75-111">Apri **Edit > Project Settings** (Modifica > Impostazioni progetto) e scorri fino alla sezione **Platforms** (Piattaforme).</span><span class="sxs-lookup"><span data-stu-id="8cf75-111">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="8cf75-112">Seleziona **HoloLens** e **Spatial Perception** (Percezione spaziale).</span><span class="sxs-lookup"><span data-stu-id="8cf75-112">Select **HoloLens** and check **Spatial Perception**.</span></span>

![Screenshot delle funzionalità delle impostazioni di progetto di HoloLens con l'opzione Spatial Perception evidenziata](images/unreal-spatial-mapping-img-01.png)

<span data-ttu-id="8cf75-114">Per acconsentire esplicitamente al mapping spaziale ed eseguire il debug di **MRMesh** in un gioco HoloLens:</span><span class="sxs-lookup"><span data-stu-id="8cf75-114">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="8cf75-115">Apri **ARSessionConfig** ed espandi la sezione **ARSettings > World Mapping** (ARSettings > Mapping mondo).</span><span class="sxs-lookup"><span data-stu-id="8cf75-115">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="8cf75-116">Seleziona **Generate Mesh Data from Tracked Geometry** (Genera dati mesh da geometria rilevata), che indica al plug-in di HoloLens di avviare l'acquisizione asincrona dei dati di mapping spaziale e presentarli ad Unreal tramite **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="8cf75-116">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="8cf75-117">Seleziona **Render Mesh Data in Wireframe** (Esegui il rendering dei dati mesh in wireframe) per visualizzare un contorno wireframe bianco di ogni triangolo in **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="8cf75-117">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![Archivio di ancoraggi nello spazio pronto](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="8cf75-119">Mapping spaziale in fase di runtime</span><span class="sxs-lookup"><span data-stu-id="8cf75-119">Spatial Mapping at runtime</span></span>
<span data-ttu-id="8cf75-120">Puoi modificare i parametri seguenti per aggiornare il comportamento di runtime del mapping spaziale:</span><span class="sxs-lookup"><span data-stu-id="8cf75-120">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="8cf75-121">Apri **Edit > Project Settings** (Modifica > Impostazioni progetto), scorri verso il basso fino alla sezione **Platforms** (Piattaforme) e seleziona **HoloLens > Spatial Mapping** (HoloLens > Mapping spaziale):</span><span class="sxs-lookup"><span data-stu-id="8cf75-121">Open **Edit > Project Settings**, scroll down to the **Platforms** section and select **HoloLens > Spatial Mapping**:</span></span> 

![Impostazioni del progetto di ancoraggi nello spazio](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="8cf75-123">Il parametro **Max Triangles Per Cubic Meter** (Numero massimo di triangoli per metro cubo) aggiorna la densità dei triangoli nella mesh di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="8cf75-123">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="8cf75-124">Il parametro **Spatial Meshing Volume Size** (Dimensioni del volume della mesh spaziale) indica le dimensioni del cubo intorno al giocatore per il rendering e l'aggiornamento dei dati di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="8cf75-124">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="8cf75-125">Se prevedi che l'ambiente di runtime dell'applicazione sia di grandi dimensioni, è possibile che questo valore debba essere elevato per poter corrispondere allo spazio reale.</span><span class="sxs-lookup"><span data-stu-id="8cf75-125">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span>  <span data-ttu-id="8cf75-126">Viceversa, questo valore può essere più piccolo se l'applicazione deve soltanto posizionare ologrammi sulle superfici immediatamente attorno all'utente.</span><span class="sxs-lookup"><span data-stu-id="8cf75-126">On the other hand, this value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="8cf75-127">Il volume di mapping spaziale si sposterà quindi contestualmente all'utente.</span><span class="sxs-lookup"><span data-stu-id="8cf75-127">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="8cf75-128">Uso di MRMesh</span><span class="sxs-lookup"><span data-stu-id="8cf75-128">Working with MRMesh</span></span>

<span data-ttu-id="8cf75-129">In primo luogo, è necessario avviare il mapping spaziale:</span><span class="sxs-lookup"><span data-stu-id="8cf75-129">First, you need to start Spatial Mapping:</span></span>

![Progetto della funzione ToggleARCapture con il tipo di acquisizione Spatial Mapping evidenziato](images/unreal-spatial-mapping-img-02.png)

<span data-ttu-id="8cf75-131">Una volta acquisito il mapping spaziale per lo spazio, è consigliabile disattivare il mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="8cf75-131">Once spatial mapping has been captured for the space, we recommend toggling spatial mapping off.</span></span>  <span data-ttu-id="8cf75-132">Il mapping spaziale può essere completato dopo un determinato periodo di tempo oppure quando i raycast emessi in ogni direzione restituiscono collisioni con MRMesh.</span><span class="sxs-lookup"><span data-stu-id="8cf75-132">The spatial mapping may be completed either after a certain amount of time, or when raycasts in each direction return collisions against the MRMesh.</span></span>

<span data-ttu-id="8cf75-133">Per ottenere l'accesso a **MRMesh** in fase di runtime:</span><span class="sxs-lookup"><span data-stu-id="8cf75-133">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="8cf75-134">Aggiungi un componente **ARTrackableNotify** a un attore del progetto.</span><span class="sxs-lookup"><span data-stu-id="8cf75-134">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![Ancoraggi nello spazio AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="8cf75-136">Seleziona il componente **ARTrackableNotify** ed spandi la sezione **Events** (Events) nel pannello **Details** (Dettagli).</span><span class="sxs-lookup"><span data-stu-id="8cf75-136">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="8cf75-137">Fai clic sul pulsante **+** sugli eventi da monitorare.</span><span class="sxs-lookup"><span data-stu-id="8cf75-137">Click the **+** button on the events you want to monitor.</span></span> 

![Eventi sugli ancoraggi nello spazio](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="8cf75-139">In questo caso viene monitorato l'evento **On Add Tracked Geometry** (All'aggiunta della geometria rilevata), che cerca mesh reali valide corrispondenti ai dati del mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="8cf75-139">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="8cf75-140">L'elenco completo degli eventi è disponibile nell'API del componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="8cf75-140">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="8cf75-141">Il materiale della mesh può essere modificato nel grafico eventi del progetto o in C++.</span><span class="sxs-lookup"><span data-stu-id="8cf75-141">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="8cf75-142">Nello screenshot seguente è mostrato il percorso del progetto:</span><span class="sxs-lookup"><span data-stu-id="8cf75-142">The screenshot below shows the Blueprint route:</span></span> 

![Esempi di ancoraggi nello spazio](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a><span data-ttu-id="8cf75-144">Mapping spaziale in C++</span><span class="sxs-lookup"><span data-stu-id="8cf75-144">Spatial Mapping in C++</span></span>

<span data-ttu-id="8cf75-145">Nel file build.cs del gioco aggiungere **AugmentedReality** e **MRMesh** all'elenco PublicDependencyModuleNames:</span><span class="sxs-lookup"><span data-stu-id="8cf75-145">In your game's build.cs file, add **AugmentedReality** and **MRMesh** to the PublicDependencyModuleNames list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",    
        "EyeTracker",
        "AugmentedReality",
        "MRMesh"
});
```

<span data-ttu-id="8cf75-146">Per accedere a MRMesh, effettuare la sottoscrizione ai delegati **OnTrackableAdded**:</span><span class="sxs-lookup"><span data-stu-id="8cf75-146">To access the MRMesh, subscribe to the **OnTrackableAdded** delegates:</span></span>

```cpp
#include "ARBlueprintLibrary.h"
#include "MRMeshComponent.h"

void AARTrackableMonitor::BeginPlay()
{
    Super::BeginPlay();

    // Subscribe to Tracked Geometry delegates
    UARBlueprintLibrary::AddOnTrackableAddedDelegate_Handle(
        FOnTrackableAddedDelegate::CreateUObject(this, &AARTrackableMonitor::OnTrackableAdded)
    );
}

void AARTrackableMonitor::OnTrackableAdded(UARTrackedGeometry* Added)
{
    // When tracked geometry is received, check that it's from spatial mapping
    if(Added->GetObjectClassification() == EARObjectClassification::World)
    {
        UMRMeshComponent* MRMesh = Added->GetUnderlyingMesh();
    }
}
```

> [!NOTE]
> <span data-ttu-id="8cf75-147">Sono presenti delegati simili per eventi aggiornati e rimossi, rispettivamente **AddOnTrackableUpdatedDelegate_Handle** e **AddOnTrackableRemovedDelegate_Handle**.</span><span class="sxs-lookup"><span data-stu-id="8cf75-147">There are similar delegates for updated and removed events, **AddOnTrackableUpdatedDelegate_Handle** and **AddOnTrackableRemovedDelegate_Handle** respectively.</span></span>
>
> <span data-ttu-id="8cf75-148">L'elenco completo degli eventi è disponibile nell'API [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).</span><span class="sxs-lookup"><span data-stu-id="8cf75-148">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="8cf75-149">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8cf75-149">See also</span></span>
* [<span data-ttu-id="8cf75-150">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="8cf75-150">Spatial mapping</span></span>](../../design/spatial-mapping.md)
