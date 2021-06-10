---
title: Mapping spaziale in Unity
description: Informazioni su come usare e gestire il rendering e la collisione con la geometria reale nelle app unity di realtà mista.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, mapping spaziale, renderer, collisore, mesh, scansione, componente, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: fa571a13ce192b29b2a35033b55061f3ffb707da
ms.sourcegitcommit: ec80ef1e496bf0b17a161735535517e87ffdd364
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2021
ms.locfileid: "110351779"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="62ae7-104">Mapping spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="62ae7-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="62ae7-105">[Il mapping](../../design/spatial-mapping.md) spaziale consente di recuperare le mesh a triangolo che rappresentano le superfici del mondo intorno a un dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="62ae7-105">[spatial mapping](../../design/spatial-mapping.md) lets you retrieve triangle meshes that represent the surfaces in the world around a HoloLens device.</span></span> <span data-ttu-id="62ae7-106">È possibile usare i dati di superficie per il posizionamento, l'occlusione e l'analisi della stanza per offrire ai progetti Unity una dose aggiuntiva di immersione.</span><span class="sxs-lookup"><span data-stu-id="62ae7-106">You can use surface data for placement, occlusion, and room analysis to give your Unity projects an extra dose of immersion.</span></span>

<span data-ttu-id="62ae7-107">Unity include il supporto completo per il mapping spaziale, esposto agli sviluppatori nei modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="62ae7-107">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>

1. <span data-ttu-id="62ae7-108">Componenti di mapping spaziale disponibili in MixedRealityToolkit, che forniscono un percorso pratico e rapido per iniziare a usare il mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="62ae7-108">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="62ae7-109">API di mapping spaziale di livello inferiore, che forniscono il controllo completo e consentono una personalizzazione più sofisticata specifica dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="62ae7-109">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application-specific customization</span></span>

<span data-ttu-id="62ae7-110">Per usare il mapping spaziale nell'app, è necessario impostare la funzionalità spatialPerception in AppxManifest.</span><span class="sxs-lookup"><span data-stu-id="62ae7-110">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="device-support"></a><span data-ttu-id="62ae7-111">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="62ae7-111">Device support</span></span>

| <span data-ttu-id="62ae7-112">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="62ae7-112">Feature</span></span> | [<span data-ttu-id="62ae7-113">HoloLens (prima generazione)</span><span class="sxs-lookup"><span data-stu-id="62ae7-113">HoloLens (first gen)</span></span>](/hololens/hololens1-hardware) | [<span data-ttu-id="62ae7-114">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="62ae7-114">HoloLens 2</span></span>](/hololens/hololens2-hardware) | [<span data-ttu-id="62ae7-115">Visori VR immersive</span><span class="sxs-lookup"><span data-stu-id="62ae7-115">Immersive headsets</span></span>](../../discover/immersive-headset-hardware-details.md) |
| ---- | ---- | ---- | ---- |
| <span data-ttu-id="62ae7-116">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="62ae7-116">Spatial mapping</span></span> | <span data-ttu-id="62ae7-117">✔️</span><span class="sxs-lookup"><span data-stu-id="62ae7-117">✔️</span></span> | <span data-ttu-id="62ae7-118">✔️</span><span class="sxs-lookup"><span data-stu-id="62ae7-118">✔️</span></span> | ❌ |

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="62ae7-119">Impostazione della funzionalità SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="62ae7-119">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="62ae7-120">Per consentire a un'app di utilizzare i dati di mapping spaziale, è necessario che sia abilitata la funzionalità SpatialPerception.</span><span class="sxs-lookup"><span data-stu-id="62ae7-120">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="62ae7-121">Come abilitare la funzionalità SpatialPerception:</span><span class="sxs-lookup"><span data-stu-id="62ae7-121">How to enable the SpatialPerception capability:</span></span>

1. <span data-ttu-id="62ae7-122">Nell'editor unity aprire il riquadro **"Impostazioni lettore"** (Modifica impostazioni progetto > progetto > Lettore)</span><span class="sxs-lookup"><span data-stu-id="62ae7-122">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="62ae7-123">Selezionare la scheda **"Windows Store"**</span><span class="sxs-lookup"><span data-stu-id="62ae7-123">Select on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="62ae7-124">Espandere **"Impostazioni di pubblicazione"** e controllare la **funzionalità "SpatialPerception"** nell'elenco **"Funzionalità"**</span><span class="sxs-lookup"><span data-stu-id="62ae7-124">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

> [!NOTE]
> <span data-ttu-id="62ae7-125">Se il progetto Unity è già stato esportato in una soluzione Visual Studio, è necessario eseguire l'esportazione in una nuova cartella o impostare manualmente questa funzionalità [in AppxManifest in Visual Studio](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="62ae7-125">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="62ae7-126">Il mapping spaziale richiede anche un valore MaxVersionTested di almeno 10.0.10586.0:</span><span class="sxs-lookup"><span data-stu-id="62ae7-126">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>

1. <span data-ttu-id="62ae7-127">In Visual Studio fare clic con il pulsante destro del mouse su **Package.appxmanifest** nell'Esplora soluzioni e selezionare **Visualizza codice**</span><span class="sxs-lookup"><span data-stu-id="62ae7-127">In Visual Studio, right-click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="62ae7-128">Trovare la riga che specifica **TargetDeviceFamily** e modificare **MaxVersionTested="10.0.10240.0"** in **MaxVersionTested="10.0.10586.0"**</span><span class="sxs-lookup"><span data-stu-id="62ae7-128">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="62ae7-129">**Salvare** Package.appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="62ae7-129">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="62ae7-130">Introduzione ai componenti di mapping spaziale predefiniti di Unity</span><span class="sxs-lookup"><span data-stu-id="62ae7-130">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="62ae7-131">Unity offre due componenti per aggiungere facilmente il mapping spaziale all'app, **il renderer di mapping** spaziale e il **collisore di mapping spaziale.**</span><span class="sxs-lookup"><span data-stu-id="62ae7-131">Unity offers two components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="62ae7-132">Renderer di mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="62ae7-132">Spatial Mapping Renderer</span></span>

<span data-ttu-id="62ae7-133">Il renderer di mapping spaziale consente la visualizzazione della mesh di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="62ae7-133">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Renderer di mapping spaziale in Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="62ae7-135">Collisore di mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="62ae7-135">Spatial Mapping Collider</span></span>

<span data-ttu-id="62ae7-136">Il collisore di mapping spaziale consente l'interazione di contenuto olografico (o carattere), ad esempio fisica, con la mesh di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="62ae7-136">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Collisore di mapping spaziale in Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="62ae7-138">Uso dei componenti di mapping spaziale predefiniti</span><span class="sxs-lookup"><span data-stu-id="62ae7-138">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="62ae7-139">È possibile aggiungere entrambi i componenti all'app se si desidera visualizzare e interagire con le superfici fisiche.</span><span class="sxs-lookup"><span data-stu-id="62ae7-139">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="62ae7-140">Per usare questi due componenti nell'app Unity:</span><span class="sxs-lookup"><span data-stu-id="62ae7-140">To use these two components in your Unity app:</span></span>

1. <span data-ttu-id="62ae7-141">Selezionare un GameObject al centro dell'area in cui si desidera rilevare le mesh di superficie spaziale.</span><span class="sxs-lookup"><span data-stu-id="62ae7-141">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="62ae7-142">Nella finestra Inspector **(Controllo) aggiungere Component**  >  **XR** Spatial Mapping Collider  >  **(Collisore** di mapping spaziale XR componente) **o Spatial Mapping Renderer (Renderer di mapping spaziale).**</span><span class="sxs-lookup"><span data-stu-id="62ae7-142">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="62ae7-143">Per altre informazioni su come usare questi componenti, vedere il sito della documentazione <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">di Unity.</a></span><span class="sxs-lookup"><span data-stu-id="62ae7-143">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="62ae7-144">Oltre i componenti di mapping spaziale predefiniti</span><span class="sxs-lookup"><span data-stu-id="62ae7-144">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="62ae7-145">Questi componenti semplificano il trascinamento della selezione per iniziare a usare Mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="62ae7-145">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span>  <span data-ttu-id="62ae7-146">Per andare oltre, è possibile esplorare due percorsi principali:</span><span class="sxs-lookup"><span data-stu-id="62ae7-146">When you want to go further, there are two main paths to explore:</span></span>

* <span data-ttu-id="62ae7-147">Per eseguire la propria elaborazione della mesh di livello inferiore, vedere la sezione seguente sull'API script di mapping spaziale di basso livello.</span><span class="sxs-lookup"><span data-stu-id="62ae7-147">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="62ae7-148">Per eseguire un'analisi della mesh di livello superiore, vedere la sezione seguente relativa alla libreria SpatialUnderstanding in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span><span class="sxs-lookup"><span data-stu-id="62ae7-148">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="62ae7-149">Uso dell'API unity spatial mapping di basso livello</span><span class="sxs-lookup"><span data-stu-id="62ae7-149">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="62ae7-150">Se è necessario un maggiore controllo rispetto all'offerta dei componenti Renderer di mapping spaziale e Collisore di mapping spaziale, usare le API di mapping spaziale di basso livello.</span><span class="sxs-lookup"><span data-stu-id="62ae7-150">If you need more control than the Spatial Mapping Renderer and Spatial Mapping Collider components offer, use the low-level Spatial Mapping APIs.</span></span>

<span data-ttu-id="62ae7-151">**Spazio dei nomi:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="62ae7-151">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="62ae7-152">**Tipi:** *SurfaceObserver,* *SurfaceChange,* *SurfaceData,* *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="62ae7-152">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="62ae7-153">È stato descritto il flusso suggerito per un'applicazione che usa le API di mapping spaziale nelle sezioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="62ae7-153">We've outlined the suggested flow for an application that uses the spatial mapping APIs in the sections below.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="62ae7-154">Configurare surfaceObserver(s)</span><span class="sxs-lookup"><span data-stu-id="62ae7-154">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="62ae7-155">Creare un'istanza di un oggetto SurfaceObserver per ogni area di spazio definita dall'applicazione per cui sono necessari dati di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="62ae7-155">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

private void Start()
{
    surfaceObserver = new SurfaceObserver();
}
```

<span data-ttu-id="62ae7-156">Specificare l'area di spazio per cui ogni oggetto SurfaceObserver fornirà i dati chiamando SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox o SetVolumeAsFrustum.</span><span class="sxs-lookup"><span data-stu-id="62ae7-156">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="62ae7-157">È possibile ridefinire l'area dello spazio in futuro semplicemente chiamando di nuovo uno di questi metodi.</span><span class="sxs-lookup"><span data-stu-id="62ae7-157">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
private void Start()
{
    surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="62ae7-158">Quando si chiama SurfaceObserver.Update(), è necessario fornire un gestore per ogni superficie spaziale nell'area di spazio di SurfaceObserver per cui il sistema di mapping spaziale ha nuove informazioni.</span><span class="sxs-lookup"><span data-stu-id="62ae7-158">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="62ae7-159">Il gestore riceve, per una superficie spaziale:</span><span class="sxs-lookup"><span data-stu-id="62ae7-159">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    // see Handling Surface Changes
}
```

### <a name="handling-surface-changes"></a><span data-ttu-id="62ae7-160">Gestione delle modifiche della superficie</span><span class="sxs-lookup"><span data-stu-id="62ae7-160">Handling Surface Changes</span></span>

<span data-ttu-id="62ae7-161">Esistono diversi casi principali da gestire: aggiunti e aggiornati, che possono usare lo stesso percorso di codice e rimossi.</span><span class="sxs-lookup"><span data-stu-id="62ae7-161">There are several main cases to handle - added and updated, which can use the same code path, and removed.</span></span>

* <span data-ttu-id="62ae7-162">Nei casi aggiunti e aggiornati si aggiunge o si ottiene l'oggetto GameObject che rappresenta questa mesh dal dizionario, si crea uno struct SurfaceData con i componenti necessari, quindi si chiama RequestMeshDataAsync per popolare GameObject con i dati della mesh e la posizione nella scena.</span><span class="sxs-lookup"><span data-stu-id="62ae7-162">In the added and updated cases, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="62ae7-163">Nel caso rimosso, l'oggetto GameObject che rappresenta questa mesh viene rimosso dal dizionario e viene eliminato definitivamente.</span><span class="sxs-lookup"><span data-stu-id="62ae7-163">In the removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects =
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    switch (changeType)
    {
        case SurfaceChange.Added:
        case SurfaceChange.Updated:
            if (!spatialMeshObjects.ContainsKey(surfaceId))
            {
                spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                spatialMeshObjects[surfaceId].transform.parent = this.transform;
                spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
            }
            GameObject target = spatialMeshObjects[surfaceId];
            SurfaceData sd = new SurfaceData(
                // the surface id returned from the system
                surfaceId,
                // the mesh filter that is populated with the spatial mapping data for this mesh
                target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                // the world anchor used to position the spatial mapping mesh in the world
                target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                // the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                // triangles per cubic meter requested for this mesh
                1000,
                // bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                true
            );

            SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
            break;
        case SurfaceChange.Removed:
            var obj = spatialMeshObjects[surfaceId];
            spatialMeshObjects.Remove(surfaceId);
            if (obj != null)
            {
                GameObject.Destroy(obj);
            }
            break;
        default:
            break;
    }
}
```

### <a name="handling-data-ready"></a><span data-ttu-id="62ae7-164">Gestione dei dati pronti</span><span class="sxs-lookup"><span data-stu-id="62ae7-164">Handling Data Ready</span></span>

<span data-ttu-id="62ae7-165">Il gestore OnDataReady riceve un oggetto SurfaceData.</span><span class="sxs-lookup"><span data-stu-id="62ae7-165">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="62ae7-166">Gli oggetti WorldAnchor, MeshFilter e (facoltativamente) MeshCollider che contiene riflettono lo stato più recente della superficie spaziale associata.</span><span class="sxs-lookup"><span data-stu-id="62ae7-166">The WorldAnchor, MeshFilter, and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="62ae7-167">Facoltativamente, analizzare e/o [elaborare](../../design/spatial-mapping.md#mesh-processing) i dati della mesh accedendo al membro Mesh dell'oggetto MeshFilter.</span><span class="sxs-lookup"><span data-stu-id="62ae7-167">Optionally, analyze and/or [process](../../design/spatial-mapping.md#mesh-processing) the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="62ae7-168">Eseguire il rendering della superficie spaziale con la mesh più recente e (facoltativamente) usarla per collisioni fisiche e raggi.</span><span class="sxs-lookup"><span data-stu-id="62ae7-168">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="62ae7-169">È importante verificare che il contenuto di SurfaceData non sia Null.</span><span class="sxs-lookup"><span data-stu-id="62ae7-169">It's important to confirm that the contents of the SurfaceData aren't null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="62ae7-170">Avviare l'elaborazione degli aggiornamenti</span><span class="sxs-lookup"><span data-stu-id="62ae7-170">Start processing on updates</span></span>

<span data-ttu-id="62ae7-171">SurfaceObserver.Update() deve essere chiamato in caso di ritardo, non per ogni frame.</span><span class="sxs-lookup"><span data-stu-id="62ae7-171">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

```cs
void Start ()
{
    StartCoroutine(UpdateLoop());
}

IEnumerator UpdateLoop()
{
    var wait = new WaitForSeconds(2.5f);
    while(true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}
```

## <a name="higher-level-mesh-analysis-spatial-understanding"></a><span data-ttu-id="62ae7-172">Analisi della mesh di livello superiore: Comprensione spaziale</span><span class="sxs-lookup"><span data-stu-id="62ae7-172">Higher-level mesh analysis: Spatial Understanding</span></span>

> [!CAUTION]
> <span data-ttu-id="62ae7-173">La comprensione spaziale è stata deprecata a favore di [Scene Understanding.](../../design/scene-understanding.md)</span><span class="sxs-lookup"><span data-stu-id="62ae7-173">Spatial Understanding has been deprecated in favor of [Scene Understanding](../../design/scene-understanding.md).</span></span>

<span data-ttu-id="62ae7-174"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> è una raccolta di codice di utilità per lo sviluppo olografico basato sulle API olografiche di Unity.</span><span class="sxs-lookup"><span data-stu-id="62ae7-174">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of utility code for holographic development built on Unity's holographic APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="62ae7-175">Comprensione spaziale</span><span class="sxs-lookup"><span data-stu-id="62ae7-175">Spatial Understanding</span></span>

<span data-ttu-id="62ae7-176">Quando si posizionano ologrammi nel mondo fisico, è spesso consigliabile andare oltre i piani mesh e di superficie della mappa spaziale.</span><span class="sxs-lookup"><span data-stu-id="62ae7-176">When placing holograms in the physical world, it's often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="62ae7-177">Quando il posizionamento viene eseguito proceduralmente, è consigliabile un livello superiore di comprensione dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="62ae7-177">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="62ae7-178">Questo richiede in genere di prendere decisioni su ciò che è il pavimento, il controsoffitto e le pareti.</span><span class="sxs-lookup"><span data-stu-id="62ae7-178">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="62ae7-179">È anche possibile ottimizzare in base a un set di vincoli di posizionamento per determinare le posizioni fisiche più ottimali per gli oggetti olografici.</span><span class="sxs-lookup"><span data-stu-id="62ae7-179">You also have the ability to optimize against a set of placement constraints to determine the most best physical locations for holographic objects.</span></span>

<span data-ttu-id="62ae7-180">Durante lo sviluppo di Young Conker e Fragments, Asobo Studios ha dovuto affrontare questo problema sviluppando un risolutore di stanza.</span><span class="sxs-lookup"><span data-stu-id="62ae7-180">During development of Young Conker and Fragments, Asobo Studios faced this problem head on by developing a room solver.</span></span> <span data-ttu-id="62ae7-181">Ognuno di questi giochi aveva esigenze specifiche del gioco, ma condividevano la tecnologia di comprensione spaziale di base.</span><span class="sxs-lookup"><span data-stu-id="62ae7-181">Each of these games had game-specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="62ae7-182">La libreria HoloToolkit.SpatialUnderstanding incapsula questa tecnologia, consentendo di trovare rapidamente spazi vuoti sulle pareti, posizionare oggetti sul controsoffitto, identificare la posizione in cui posizionare il carattere e una miriade di altre query di comprensione spaziale.</span><span class="sxs-lookup"><span data-stu-id="62ae7-182">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="62ae7-183">Tutto il codice sorgente è incluso, consentendo di personalizzarlo in base alle proprie esigenze e condividere i miglioramenti con la community.</span><span class="sxs-lookup"><span data-stu-id="62ae7-183">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="62ae7-184">Il codice per il risolutore C++ è stato incapsulato in una dll UWP ed esposto a Unity con un calo nel prefab contenuto in MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="62ae7-184">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="62ae7-185">Informazioni sui moduli</span><span class="sxs-lookup"><span data-stu-id="62ae7-185">Understanding Modules</span></span>

<span data-ttu-id="62ae7-186">Esistono tre interfacce principali esposte dal modulo: topologia per query semplici su superfici e spaziali, forma per il rilevamento degli oggetti e risolutore di posizionamento degli oggetti per il posizionamento basato su vincoli di set di oggetti.</span><span class="sxs-lookup"><span data-stu-id="62ae7-186">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint-based placement of object sets.</span></span> <span data-ttu-id="62ae7-187">Ogni modalità è illustrata di seguito.</span><span class="sxs-lookup"><span data-stu-id="62ae7-187">Each of these is described below.</span></span> <span data-ttu-id="62ae7-188">Oltre alle tre interfacce principali del modulo, è possibile usare un'interfaccia di ray casting per recuperare i tipi di superficie con tag e copiare una mesh dello spazio di gioco a tenuta stagna personalizzata.</span><span class="sxs-lookup"><span data-stu-id="62ae7-188">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="62ae7-189">Ray Casting</span><span class="sxs-lookup"><span data-stu-id="62ae7-189">Ray Casting</span></span>

<span data-ttu-id="62ae7-190">Al termine dell'analisi della stanza, le etichette vengono generate internamente per superfici come il pavimento, il controsoffitto e le pareti.</span><span class="sxs-lookup"><span data-stu-id="62ae7-190">After the room scan is completed, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="62ae7-191">La funzione accetta un raggio e restituisce se il raggio entra in collisione con una superficie nota e, in tal caso, le informazioni su tale superficie sotto `PlayspaceRaycast` forma di `RaycastResult` .</span><span class="sxs-lookup"><span data-stu-id="62ae7-191">The `PlayspaceRaycast` function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a `RaycastResult`.</span></span>

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology,
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface,
                    //  but vertical surface that looks like a
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

<span data-ttu-id="62ae7-192">Internamente, il raycast viene calcolato sulla rappresentazione voxel a cubo di 8 cm calcolata dello spazio di gioco.</span><span class="sxs-lookup"><span data-stu-id="62ae7-192">Internally, the raycast is computed against the computed 8-cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="62ae7-193">Ogni voxel contiene un set di elementi di superficie con i dati della topologia elaborati (alias surfel).</span><span class="sxs-lookup"><span data-stu-id="62ae7-193">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="62ae7-194">Vengono confrontati i surfel contenuti all'interno della cella voxel intersecata e viene usata la corrispondenza migliore usata per cercare le informazioni sulla topologia.</span><span class="sxs-lookup"><span data-stu-id="62ae7-194">The surfels contained within the intersected voxel cell is compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="62ae7-195">Questi dati della topologia contengono l'etichettatura restituita sotto forma di enumerazione "SurfaceTypes", nonché l'area di superficie della superficie intersecata.</span><span class="sxs-lookup"><span data-stu-id="62ae7-195">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="62ae7-196">Nell'esempio Unity il cursore esegue il cast di un raggio per ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="62ae7-196">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="62ae7-197">In primo luogo, contro i collisori di Unity.</span><span class="sxs-lookup"><span data-stu-id="62ae7-197">First, against Unity’s colliders.</span></span> <span data-ttu-id="62ae7-198">In secondo piano, rispetto alla rappresentazione del mondo del modulo di comprensione.</span><span class="sxs-lookup"><span data-stu-id="62ae7-198">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="62ae7-199">Infine, ancora elementi dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="62ae7-199">And finally, again UI elements.</span></span> <span data-ttu-id="62ae7-200">In questa applicazione l'interfaccia utente ottiene la priorità, quindi il risultato di comprensione e infine i collisori di Unity.</span><span class="sxs-lookup"><span data-stu-id="62ae7-200">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="62ae7-201">SurfaceType viene segnalato come testo accanto al cursore.</span><span class="sxs-lookup"><span data-stu-id="62ae7-201">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="62ae7-202">![Il tipo di superficie viene etichettato accanto al cursore](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="62ae7-202">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="62ae7-203">*Il tipo di superficie viene etichettato accanto al cursore*</span><span class="sxs-lookup"><span data-stu-id="62ae7-203">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="62ae7-204">Query sulla topologia</span><span class="sxs-lookup"><span data-stu-id="62ae7-204">Topology Queries</span></span>

<span data-ttu-id="62ae7-205">All'interno della DLL, il gestore della topologia gestisce l'etichettatura dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="62ae7-205">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="62ae7-206">Come accennato in precedenza, gran parte dei dati viene archiviata all'interno di un volume voxel.</span><span class="sxs-lookup"><span data-stu-id="62ae7-206">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="62ae7-207">Inoltre, la struttura "PlaySpaceInfos" viene usata per archiviare le informazioni sullo spazio di gioco, tra cui l'allineamento del mondo (altri dettagli su questo di seguito), il piano e l'altezza del controsoffitto.</span><span class="sxs-lookup"><span data-stu-id="62ae7-207">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="62ae7-208">L'euristica viene usata per determinare il piano, il controsoffitto e le pareti.</span><span class="sxs-lookup"><span data-stu-id="62ae7-208">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="62ae7-209">Ad esempio, la superficie orizzontale più grande e più bassa con una superficie di superficie maggiore di 1 m2 viene considerata il piano.</span><span class="sxs-lookup"><span data-stu-id="62ae7-209">For example, the largest and lowest horizontal surface with greater than 1-m2 surface area is considered the floor.</span></span>

> [!NOTE]
> <span data-ttu-id="62ae7-210">In questo processo viene usato anche il percorso della fotocamera durante il processo di analisi.</span><span class="sxs-lookup"><span data-stu-id="62ae7-210">The camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="62ae7-211">Un subset delle query esposte dal gestore della topologia viene esposto tramite la DLL.</span><span class="sxs-lookup"><span data-stu-id="62ae7-211">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="62ae7-212">Le query sulla topologia esposte sono le seguenti.</span><span class="sxs-lookup"><span data-stu-id="62ae7-212">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="62ae7-213">Ognuna delle query ha un set di parametri, specifico per il tipo di query.</span><span class="sxs-lookup"><span data-stu-id="62ae7-213">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="62ae7-214">Nell'esempio seguente l'utente specifica l'altezza minima & larghezza del volume desiderato, l'altezza di posizionamento minima sopra il piano e la quantità minima di spazio davanti al volume.</span><span class="sxs-lookup"><span data-stu-id="62ae7-214">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="62ae7-215">Tutte le misurazioni sono in metri.</span><span class="sxs-lookup"><span data-stu-id="62ae7-215">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="62ae7-216">Ognuna di queste query accetta una matrice preallocato di strutture "TopologyResult".</span><span class="sxs-lookup"><span data-stu-id="62ae7-216">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="62ae7-217">Il parametro "locationCount" specifica la lunghezza della matrice passata.</span><span class="sxs-lookup"><span data-stu-id="62ae7-217">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="62ae7-218">Il valore restituito indica il numero di posizioni restituite.</span><span class="sxs-lookup"><span data-stu-id="62ae7-218">The return value reports the number of returned locations.</span></span> <span data-ttu-id="62ae7-219">Questo numero non è mai maggiore del parametro "locationCount" passato.</span><span class="sxs-lookup"><span data-stu-id="62ae7-219">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="62ae7-220">"TopologyResult" contiene la posizione centrale del volume restituito, la direzione rivolta (normale) e le dimensioni dello spazio trovato.</span><span class="sxs-lookup"><span data-stu-id="62ae7-220">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult
{
    DirectX::XMFLOAT3 position;
    DirectX::XMFLOAT3 normal;
    float width;
    float length;
};
```

> [!NOTE]
> <span data-ttu-id="62ae7-221">Nell'esempio unity ognuna di queste query è collegata a un pulsante nel pannello dell'interfaccia utente virtuale.</span><span class="sxs-lookup"><span data-stu-id="62ae7-221">In the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="62ae7-222">L'esempio imposta come hard code i parametri per ognuna di queste query in base a valori ragionevoli.</span><span class="sxs-lookup"><span data-stu-id="62ae7-222">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="62ae7-223">Per altri esempi, vedere SpaceVisualizer.cs nel codice di esempio.</span><span class="sxs-lookup"><span data-stu-id="62ae7-223">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="62ae7-224">Query di forma</span><span class="sxs-lookup"><span data-stu-id="62ae7-224">Shape Queries</span></span>

<span data-ttu-id="62ae7-225">Nella DLL, l'analizzatore forme ("ShapeAnalyzer_W") usa l'analizzatore della topologia per la corrispondenza con forme personalizzate definite dall'utente.</span><span class="sxs-lookup"><span data-stu-id="62ae7-225">In the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="62ae7-226">L'esempio Unity definisce un set di forme ed espone i risultati tramite il menu di query in-app, all'interno della scheda della forma. L'obiettivo è che l'utente possa definire le proprie query di forma degli oggetti e usarle, in base alle esigenze dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="62ae7-226">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="62ae7-227">L'analisi delle forme funziona solo su superfici orizzontali.</span><span class="sxs-lookup"><span data-stu-id="62ae7-227">The shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="62ae7-228">Un divano, ad esempio, è definito dalla superficie della sella piana e dalla parte superiore piana del divano.</span><span class="sxs-lookup"><span data-stu-id="62ae7-228">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="62ae7-229">La query di forma cerca due superfici di dimensioni, altezza e intervallo di aspetti specifici, con le due superfici allineate e connesse.</span><span class="sxs-lookup"><span data-stu-id="62ae7-229">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="62ae7-230">Usando la terminologia delle API, il posto sul divano e il back-top sono componenti di forma e i requisiti di allineamento sono vincoli dei componenti della forma.</span><span class="sxs-lookup"><span data-stu-id="62ae7-230">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="62ae7-231">Di seguito è illustrata una query di esempio definita nell'esempio Unity (ShapeDefinition.cs) per gli oggetti "sittable".</span><span class="sxs-lookup"><span data-stu-id="62ae7-231">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="62ae7-232">Ogni query di forma è definita da un set di componenti della forma, ognuno con un set di vincoli di componente e un set di vincoli di forma che elencano le dipendenze tra i componenti.</span><span class="sxs-lookup"><span data-stu-id="62ae7-232">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="62ae7-233">Questo esempio include tre vincoli in una singola definizione di componente e nessun vincolo di forma tra i componenti (poiché è presente un solo componente).</span><span class="sxs-lookup"><span data-stu-id="62ae7-233">This example includes three constraints in a single component definition and no shape constraints between components (as there's only one component).</span></span>

<span data-ttu-id="62ae7-234">Al contrario, la forma del divano ha due componenti di forma e quattro vincoli di forma.</span><span class="sxs-lookup"><span data-stu-id="62ae7-234">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="62ae7-235">I componenti sono identificati dal relativo indice nell'elenco dei componenti dell'utente (0 e 1 in questo esempio).</span><span class="sxs-lookup"><span data-stu-id="62ae7-235">Components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="62ae7-236">Le funzioni wrapper vengono fornite nel modulo Unity per creare facilmente definizioni di forme personalizzate.</span><span class="sxs-lookup"><span data-stu-id="62ae7-236">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="62ae7-237">L'elenco completo dei vincoli di componente e forma è disponibile in "SpatialUnderstandingDll.cs" all'interno delle strutture "ShapeComponentConstraint" e "ShapeConstraint".</span><span class="sxs-lookup"><span data-stu-id="62ae7-237">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="62ae7-238">![La forma rettangolo si trova su questa superficie](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="62ae7-238">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="62ae7-239">*La forma rettangolo si trova su questa superficie*</span><span class="sxs-lookup"><span data-stu-id="62ae7-239">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="62ae7-240">Risolutore di posizionamento degli oggetti</span><span class="sxs-lookup"><span data-stu-id="62ae7-240">Object Placement Solver</span></span>

<span data-ttu-id="62ae7-241">Il risolutore di posizionamento degli oggetti può essere usato per identificare le posizioni ideali nella stanza fisica in cui posizionare gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="62ae7-241">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="62ae7-242">Il risolutore troverà la posizione più adatta in base alle regole e ai vincoli dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="62ae7-242">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="62ae7-243">Inoltre, le query su oggetti vengono mantenute fino a quando l'oggetto non viene rimosso con chiamate "Solver_RemoveObject" o "Solver_RemoveAllObjects", consentendo il posizionamento vincolato di più oggetti.</span><span class="sxs-lookup"><span data-stu-id="62ae7-243">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="62ae7-244">Le query di posizionamento degli oggetti sono costituite da tre parti: tipo di posizionamento con parametri, un elenco di regole e un elenco di vincoli.</span><span class="sxs-lookup"><span data-stu-id="62ae7-244">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="62ae7-245">Per eseguire una query, usare l'API seguente.</span><span class="sxs-lookup"><span data-stu-id="62ae7-245">To run a query, use the following API.</span></span>

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

<span data-ttu-id="62ae7-246">Questa funzione accetta un nome di oggetto, una definizione di posizionamento e un elenco di regole e vincoli.</span><span class="sxs-lookup"><span data-stu-id="62ae7-246">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="62ae7-247">I wrapper C# forniscono funzioni helper di costruzione per semplificare la costruzione di regole e vincoli.</span><span class="sxs-lookup"><span data-stu-id="62ae7-247">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="62ae7-248">La definizione di posizionamento contiene il tipo di query, ad esempio uno dei seguenti.</span><span class="sxs-lookup"><span data-stu-id="62ae7-248">The placement definition contains the query type – that is, one of the following.</span></span>

```cpp
public enum PlacementType
{
    Place_OnFloor,
    Place_OnWall,
    Place_OnCeiling,
    Place_OnShape,
    Place_OnEdge,
    Place_OnFloorAndCeiling,
    Place_RandomInAir,
    Place_InMidAir,
    Place_UnderFurnitureEdge,
};
```

<span data-ttu-id="62ae7-249">Ogni tipo di posizionamento ha un set di parametri univoci per il tipo.</span><span class="sxs-lookup"><span data-stu-id="62ae7-249">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="62ae7-250">La struttura "ObjectPlacementDefinition" contiene un set di funzioni helper statiche per la creazione di queste definizioni.</span><span class="sxs-lookup"><span data-stu-id="62ae7-250">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="62ae7-251">Ad esempio, per trovare una posizione in cui inserire un oggetto sul piano, è possibile usare la funzione seguente.</span><span class="sxs-lookup"><span data-stu-id="62ae7-251">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="62ae7-252">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) Oltre al tipo di posizionamento, è possibile fornire un set di regole e vincoli.</span><span class="sxs-lookup"><span data-stu-id="62ae7-252">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="62ae7-253">Le regole non possono essere violate.</span><span class="sxs-lookup"><span data-stu-id="62ae7-253">Rules cannot be violated.</span></span> <span data-ttu-id="62ae7-254">Le possibili posizioni di posizionamento che soddisfano il tipo e le regole vengono quindi ottimizzate rispetto al set di vincoli per selezionare la posizione ottimale.</span><span class="sxs-lookup"><span data-stu-id="62ae7-254">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="62ae7-255">Ogni regola e vincolo può essere creato dalle funzioni di creazione statiche fornite.</span><span class="sxs-lookup"><span data-stu-id="62ae7-255">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="62ae7-256">Di seguito è riportata una regola di esempio e una funzione di costruzione di vincoli.</span><span class="sxs-lookup"><span data-stu-id="62ae7-256">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="62ae7-257">La query di posizionamento degli oggetti seguente cerca un punto in cui posizionare un cubo di mezzo metro sul bordo di una superficie, lontano da altri oggetti posizionati in precedenza e vicino al centro della stanza.</span><span class="sxs-lookup"><span data-stu-id="62ae7-257">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

```cs
List<ObjectPlacementRule> rules =
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints =
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f),
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="62ae7-258">In caso di esito positivo, viene restituita una struttura "ObjectPlacementResult" contenente la posizione di posizionamento, le dimensioni e l'orientamento.</span><span class="sxs-lookup"><span data-stu-id="62ae7-258">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions, and orientation is returned.</span></span> <span data-ttu-id="62ae7-259">Inoltre, il posizionamento viene aggiunto all'elenco interno della DLL di oggetti inseriti.</span><span class="sxs-lookup"><span data-stu-id="62ae7-259">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="62ae7-260">Le query di posizionamento successive prenderanno in considerazione questo oggetto.</span><span class="sxs-lookup"><span data-stu-id="62ae7-260">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="62ae7-261">Il file "LevelSolver.cs" nell'esempio Unity contiene altre query di esempio.</span><span class="sxs-lookup"><span data-stu-id="62ae7-261">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="62ae7-262">![Risultati del posizionamento degli oggetti](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="62ae7-262">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="62ae7-263">*Figura 3: Le caselle blu illustrano come viene restituito il risultato da tre query sul piano con le regole di posizione della fotocamera*</span><span class="sxs-lookup"><span data-stu-id="62ae7-263">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="62ae7-264">Durante la risoluzione della posizione di posizionamento di più oggetti necessari per uno scenario di livello o applicazione, risolvere prima di tutto oggetti di grandi dimensioni e disaffezionati per massimizzare la probabilità che sia possibile trovare uno spazio.</span><span class="sxs-lookup"><span data-stu-id="62ae7-264">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="62ae7-265">L'ordine di posizionamento è importante.</span><span class="sxs-lookup"><span data-stu-id="62ae7-265">Placement order is important.</span></span> <span data-ttu-id="62ae7-266">Se non è possibile trovare i posizionamenti degli oggetti, provare le configurazioni meno vincolate.</span><span class="sxs-lookup"><span data-stu-id="62ae7-266">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="62ae7-267">La presenza di un set di configurazioni di fallback è fondamentale per supportare le funzionalità in molte configurazioni di stanza.</span><span class="sxs-lookup"><span data-stu-id="62ae7-267">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="62ae7-268">Processo di analisi delle camere</span><span class="sxs-lookup"><span data-stu-id="62ae7-268">Room Scanning Process</span></span>

<span data-ttu-id="62ae7-269">Anche se la soluzione di mapping spaziale fornita da HoloLens è progettata per essere sufficientemente generica da soddisfare le esigenze dell'intera gamma di spazi problematici, il modulo di comprensione spaziale è stato creato per supportare le esigenze di due giochi specifici.</span><span class="sxs-lookup"><span data-stu-id="62ae7-269">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="62ae7-270">La soluzione è strutturata in base a un processo specifico e a un set di presupposti, riepilogati di seguito.</span><span class="sxs-lookup"><span data-stu-id="62ae7-270">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```txt
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process –
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace.
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="62ae7-271">"disegno" dello spazio di gioco guidato dall'utente: durante la fase di analisi, l'utente si sposta e guarda intorno al ritmo di riproduzione, disegnando in modo efficace le aree, che devono essere incluse.</span><span class="sxs-lookup"><span data-stu-id="62ae7-271">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas, which should be included.</span></span> <span data-ttu-id="62ae7-272">La mesh generata è importante per fornire commenti e suggerimenti durante questa fase.</span><span class="sxs-lookup"><span data-stu-id="62ae7-272">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="62ae7-273">Configurazione dell'ambiente domestico o dell'ufficio: le funzioni di query sono progettate su superfici piatte e pareti ad angolo retto.</span><span class="sxs-lookup"><span data-stu-id="62ae7-273">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="62ae7-274">Si tratta di una limitazione soft.</span><span class="sxs-lookup"><span data-stu-id="62ae7-274">This is a soft limitation.</span></span> <span data-ttu-id="62ae7-275">Tuttavia, durante la fase di analisi, viene completata un'analisi dell'asse principale per ottimizzare la trama mesh lungo l'asse principale e secondario.</span><span class="sxs-lookup"><span data-stu-id="62ae7-275">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="62ae7-276">Il file SpatialUnderstanding.cs incluso gestisce il processo della fase di analisi.</span><span class="sxs-lookup"><span data-stu-id="62ae7-276">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="62ae7-277">Chiama le funzioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="62ae7-277">It calls the following functions.</span></span>

```txt
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan –
    Called each frame to update the scanning process. The camera position and
    orientation is passed in and is used for the playspace painting process,
    described above.

GeneratePlayspace_RequestFinish –
    Called to finalize the playspace. This will use the areas “painted” during
    the scan phase to define and lock the playspace. The application can query
    statistics during the scanning phase as well as query the custom mesh for
    providing user feedback.

Import_UnderstandingMesh –
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by
    the module and placed on the understanding prefab will periodically query the
    custom mesh generated by the process. In addition, this is done once more
    after scanning has been finalized.
```

<span data-ttu-id="62ae7-278">Il flusso di analisi, basato sul comportamento "SpatialUnderstanding", chiama InitScan e quindi UpdateScan per ogni frame.</span><span class="sxs-lookup"><span data-stu-id="62ae7-278">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="62ae7-279">Quando la query sulle statistiche segnala una copertura ragionevole, l'utente può chiamare RequestFinish per indicare la fine della fase di analisi.</span><span class="sxs-lookup"><span data-stu-id="62ae7-279">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="62ae7-280">UpdateScan continua a essere chiamato fino a quando il valore restituito non indica che la DLL ha completato l'elaborazione.</span><span class="sxs-lookup"><span data-stu-id="62ae7-280">UpdateScan continues to be called until its return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="62ae7-281">Informazioni su Mesh</span><span class="sxs-lookup"><span data-stu-id="62ae7-281">Understanding Mesh</span></span>

<span data-ttu-id="62ae7-282">La DLL di comprensione archivia internamente lo spazio di riproduzione come griglia di cubi voxel con dimensioni di 8 cm.</span><span class="sxs-lookup"><span data-stu-id="62ae7-282">The understanding dll internally stores the playspace as a grid of 8 cm sized voxel cubes.</span></span> <span data-ttu-id="62ae7-283">Durante la parte iniziale dell'analisi, viene completata un'analisi dei componenti principali per determinare gli assi della stanza.</span><span class="sxs-lookup"><span data-stu-id="62ae7-283">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="62ae7-284">Internamente, archivia lo spazio voxel allineato a questi assi.</span><span class="sxs-lookup"><span data-stu-id="62ae7-284">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="62ae7-285">Una mesh viene generata circa ogni secondo estraendo l'isosurface dal volume voxel.</span><span class="sxs-lookup"><span data-stu-id="62ae7-285">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

<span data-ttu-id="62ae7-286">![Mesh generata dal volume voxel](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="62ae7-286">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="62ae7-287">*Mesh generata dal volume voxel*</span><span class="sxs-lookup"><span data-stu-id="62ae7-287">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="62ae7-288">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="62ae7-288">Troubleshooting</span></span>

* <span data-ttu-id="62ae7-289">Assicurarsi di aver impostato [la funzionalità SpatialPerception](#setting-the-spatialperception-capability)</span><span class="sxs-lookup"><span data-stu-id="62ae7-289">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="62ae7-290">Quando il rilevamento viene perso, il successivo evento OnSurfaceChanged rimuoverà tutte le mesh.</span><span class="sxs-lookup"><span data-stu-id="62ae7-290">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="62ae7-291">Mapping spaziale in Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="62ae7-291">Spatial Mapping in Mixed Reality Toolkit</span></span>

<span data-ttu-id="62ae7-292">Per altre informazioni sull'uso del mapping spaziale con Mixed Reality Toolkit, vedi la sezione sulla consapevolezza [spaziale](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) della documentazione di MRTK.</span><span class="sxs-lookup"><span data-stu-id="62ae7-292">For more information on using Spatial Mapping with Mixed Reality Toolkit, see the [spatial awareness section](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) of the MRTK docs.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="62ae7-293">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="62ae7-293">Next Development Checkpoint</span></span>

<span data-ttu-id="62ae7-294">Se si sta seguendo il percorso di sviluppo di Unity che è stato strutturato, si stanno esplorando i blocchi predefiniti principali di MRTK.</span><span class="sxs-lookup"><span data-stu-id="62ae7-294">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="62ae7-295">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="62ae7-295">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="62ae7-296">Text</span><span class="sxs-lookup"><span data-stu-id="62ae7-296">Text</span></span>](text-in-unity.md)

<span data-ttu-id="62ae7-297">In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="62ae7-297">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="62ae7-298">Esperienze condivise</span><span class="sxs-lookup"><span data-stu-id="62ae7-298">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="62ae7-299">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="62ae7-299">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="62ae7-300">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="62ae7-300">See also</span></span>

* [<span data-ttu-id="62ae7-301">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="62ae7-301">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* [<span data-ttu-id="62ae7-302">Sistemi di coordinate in Unity</span><span class="sxs-lookup"><span data-stu-id="62ae7-302">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="62ae7-303"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="62ae7-303"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="62ae7-304"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="62ae7-304"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="62ae7-305"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="62ae7-305"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="62ae7-306"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span><span class="sxs-lookup"><span data-stu-id="62ae7-306"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
