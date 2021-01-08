---
title: Tracciamento mano in Unreal
description: Informazioni su come usare l'input per il rilevamento della mano, la posa, le mesh di mano e le animazioni dei collegamenti dinamici in app Real realtà miste.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realtà mista di Windows, Tracking manuale, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, sviluppo di giochi, cuffie per realtà mista, cuffia a realtà mista di Windows, headset di realtà virtuale
ms.openlocfilehash: e482c93233348325736d2c224788e9174c1f3b67
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010161"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="ad11b-104">Tracciamento mano in Unreal</span><span class="sxs-lookup"><span data-stu-id="ad11b-104">Hand tracking in Unreal</span></span>

<span data-ttu-id="ad11b-105">Il sistema di rilevamento manuale usa le palme e le dita di una persona come input.</span><span class="sxs-lookup"><span data-stu-id="ad11b-105">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="ad11b-106">I dati sulla posizione e sulla rotazione di ogni dito, l'intero palmo e i movimenti della mano sono disponibili.</span><span class="sxs-lookup"><span data-stu-id="ad11b-106">Data on position and rotation of every finger, the entire palm, and hand gestures is available.</span></span> <span data-ttu-id="ad11b-107">A partire da Unreal 4,26, il rilevamento manuale è basato sul plug-in HeadMountedDisplay non reale e usa un'API comune in tutti i dispositivi e le piattaforme XR.</span><span class="sxs-lookup"><span data-stu-id="ad11b-107">Starting in Unreal 4.26, hand tracking is based on the Unreal HeadMountedDisplay plugin and uses a common API across all XR platforms and devices.</span></span> <span data-ttu-id="ad11b-108">La funzionalità è la stessa per i sistemi OpenXR e di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="ad11b-108">Functionality is the same for both Windows Mixed Reality and OpenXR systems.</span></span>

## <a name="hand-pose"></a><span data-ttu-id="ad11b-109">Hand Pose</span><span class="sxs-lookup"><span data-stu-id="ad11b-109">Hand pose</span></span>

<span data-ttu-id="ad11b-110">Hand Pose consente di tenere traccia e di usare le mani e le dita degli utenti come input, a cui è possibile accedere sia nei progetti sia in C++.</span><span class="sxs-lookup"><span data-stu-id="ad11b-110">Hand pose lets you track and use the hands and fingers of your users as input, which can be accessed in both Blueprints and C++.</span></span> <span data-ttu-id="ad11b-111">L'API Unreal invia i dati come sistema di coordinate, con segni di selezione sincronizzati con il motore irreale.</span><span class="sxs-lookup"><span data-stu-id="ad11b-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

![Scheletro mano](../native/images/hand-skeleton.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a><span data-ttu-id="ad11b-113">Animazione collegamento dinamico</span><span class="sxs-lookup"><span data-stu-id="ad11b-113">Hand Live Link Animation</span></span>

<span data-ttu-id="ad11b-114">Le pose della mano vengono esposte all'animazione usando il plug-in [Live link](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span><span class="sxs-lookup"><span data-stu-id="ad11b-114">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="ad11b-115">Se sono abilitati i plug-in della realtà mista di Windows e dei collegamenti dinamici:</span><span class="sxs-lookup"><span data-stu-id="ad11b-115">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span>
1. <span data-ttu-id="ad11b-116">Selezionare **finestra > collegamento Live** per aprire la finestra dell'editor di collegamento Live.</span><span class="sxs-lookup"><span data-stu-id="ad11b-116">Select **Window > Live Link** to open the Live Link editor window.</span></span>
2. <span data-ttu-id="ad11b-117">Selezionare l' **origine** e abilitare l' **origine del rilevamento a mano della realtà mista di Windows**</span><span class="sxs-lookup"><span data-stu-id="ad11b-117">Select **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![Origine collegamento dinamico](images/unreal/live-link-source.png)

<span data-ttu-id="ad11b-119">Dopo aver abilitato l'origine e aperto un asset di animazione, espandere la sezione **animazione** nella scheda della **scena anteprima** . vedere anche opzioni aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="ad11b-119">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options.</span></span>

![Animazione collegamento dinamico](images/unreal/live-link-animation.png)

<span data-ttu-id="ad11b-121">La gerarchia di animazione della mano è identica a quella di `EWMRHandKeypoint` .</span><span class="sxs-lookup"><span data-stu-id="ad11b-121">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="ad11b-122">L'animazione può essere ridestinata usando **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span><span class="sxs-lookup"><span data-stu-id="ad11b-122">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span></span>

![Animazione collegamento dinamico 2](images/unreal/live-link-animation2.png)

<span data-ttu-id="ad11b-124">Può anche essere sottoclassato nell'Editor:</span><span class="sxs-lookup"><span data-stu-id="ad11b-124">It can also be subclassed in the editor:</span></span>

![Modifica del mapping di Live link](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a><span data-ttu-id="ad11b-126">Mesh mano</span><span class="sxs-lookup"><span data-stu-id="ad11b-126">Hand Mesh</span></span>

### <a name="hand-mesh-as-a-tracked-geometry"></a><span data-ttu-id="ad11b-127">Mesh mano come geometria rilevata</span><span class="sxs-lookup"><span data-stu-id="ad11b-127">Hand Mesh as a Tracked Geometry</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ad11b-128">Per ottenere le mesh della mano come geometria tracciata in OpenXR, è necessario chiamare **set Use Hand mesh** con la **geometria di rilevamento abilitata**.</span><span class="sxs-lookup"><span data-stu-id="ad11b-128">Getting hand meshes as a tracked geometry in OpenXR requires you to call **Set Use Hand Mesh** with **Enabled Tracking Geometry**.</span></span>

<span data-ttu-id="ad11b-129">Per abilitare questa modalità, è necessario chiamare **set Use Hand mesh** con la **geometria di rilevamento abilitata**:</span><span class="sxs-lookup"><span data-stu-id="ad11b-129">To enable that mode you should call **Set Use Hand Mesh** with **Enabled Tracking Geometry**:</span></span>

![Progetto di avvio dell'evento Play connesso per impostare Use Hand mesh Function con la modalità di rilevamento Geometry abilitata](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> <span data-ttu-id="ad11b-131">Non è possibile abilitare entrambe le modalità nello stesso momento.</span><span class="sxs-lookup"><span data-stu-id="ad11b-131">It’s not possible for both modes to be enabled at the same time.</span></span> <span data-ttu-id="ad11b-132">Se ne viene abilitato uno, l'altro viene disabilitato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ad11b-132">If you enable one, the other is automatically disabled.</span></span>

### <a name="accessing-hand-mesh-data"></a><span data-ttu-id="ad11b-133">Accesso ai dati della rete a mano</span><span class="sxs-lookup"><span data-stu-id="ad11b-133">Accessing Hand Mesh Data</span></span>

![Mesh mano](images/unreal/hand-mesh.png)

<span data-ttu-id="ad11b-135">Prima di poter accedere ai dati della mesh a mano, è necessario:</span><span class="sxs-lookup"><span data-stu-id="ad11b-135">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="ad11b-136">Selezionare l'asset **ARSessionConfig** , espandere impostazioni **AR-> Impostazioni mapping del mondo** e selezionare **genera dati mesh da geometria rilevata**.</span><span class="sxs-lookup"><span data-stu-id="ad11b-136">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry**.</span></span>

<span data-ttu-id="ad11b-137">Di seguito sono riportati i parametri di mesh predefiniti:</span><span class="sxs-lookup"><span data-stu-id="ad11b-137">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="ad11b-138">Usare i dati mesh per l'occlusione</span><span class="sxs-lookup"><span data-stu-id="ad11b-138">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="ad11b-139">Genera collisione per i dati mesh</span><span class="sxs-lookup"><span data-stu-id="ad11b-139">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="ad11b-140">Genera la mesh NAV per i dati mesh</span><span class="sxs-lookup"><span data-stu-id="ad11b-140">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="ad11b-141">Eseguire il rendering dei dati mesh nel parametro wireframe-debug che mostra la mesh generata</span><span class="sxs-lookup"><span data-stu-id="ad11b-141">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="ad11b-142">Questi valori di parametro vengono usati come il mapping spaziale mesh e le impostazioni predefinite mesh a mano.</span><span class="sxs-lookup"><span data-stu-id="ad11b-142">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="ad11b-143">È possibile modificarli in qualsiasi momento in progetti o codice per qualsiasi mesh.</span><span class="sxs-lookup"><span data-stu-id="ad11b-143">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="ad11b-144">Informazioni di riferimento sulle API C++</span><span class="sxs-lookup"><span data-stu-id="ad11b-144">C++ API Reference</span></span>
<span data-ttu-id="ad11b-145">Usare `EEARObjectClassification` per trovare i valori della mesh mano in tutti gli oggetti rilevabili.</span><span class="sxs-lookup"><span data-stu-id="ad11b-145">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

<span data-ttu-id="ad11b-146">I delegati seguenti vengono chiamati quando il sistema rileva qualsiasi oggetto rilevabile, inclusa una mesh mano.</span><span class="sxs-lookup"><span data-stu-id="ad11b-146">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span>

```cpp
class FARSupportInterface
{
    public:
    // Other params
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

<span data-ttu-id="ad11b-147">Assicurarsi che i gestori del delegato seguano la firma della funzione seguente:</span><span class="sxs-lookup"><span data-stu-id="ad11b-147">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="ad11b-148">È possibile accedere ai dati mesh tramite  `UARTrackedGeometry::GetUnderlyingMesh` :</span><span class="sxs-lookup"><span data-stu-id="ad11b-148">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a><span data-ttu-id="ad11b-149">Riferimento all'API Blueprint</span><span class="sxs-lookup"><span data-stu-id="ad11b-149">Blueprint API Reference</span></span>

<span data-ttu-id="ad11b-150">Per lavorare con le mesh mano nei progetti:</span><span class="sxs-lookup"><span data-stu-id="ad11b-150">To work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="ad11b-151">Aggiungere un componente **ARTrackableNotify** a un attore del progetto</span><span class="sxs-lookup"><span data-stu-id="ad11b-151">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![Notifica ARTrackable](images/unreal/ar-trackable-notify.png)

2. <span data-ttu-id="ad11b-153">Passare al pannello dei **Dettagli** ed espandere la sezione **eventi** .</span><span class="sxs-lookup"><span data-stu-id="ad11b-153">Go to the **Details** panel and expand the **Events** section.</span></span>

![Notifica ARTrackable 2](images/unreal/ar-trackable-notify2.png)

3. <span data-ttu-id="ad11b-155">Sovrascrivi in Aggiungi/Aggiorna/Rimuovi geometria rilevata con i nodi seguenti nel grafico eventi:</span><span class="sxs-lookup"><span data-stu-id="ad11b-155">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![In ARTrackable notifica](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a><span data-ttu-id="ad11b-157">Visualizzazione Mesh mano in OpenXR</span><span class="sxs-lookup"><span data-stu-id="ad11b-157">Hand Mesh visualization in OpenXR</span></span>

<span data-ttu-id="ad11b-158">Il metodo consigliato per visualizzare la mesh manuale consiste nell'usare il plug-in XRVisualization di Epic insieme al plug-in [Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="ad11b-158">The recommended way to visualize hand mesh is to use Epic’s XRVisualization plugin together with the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span> 

<span data-ttu-id="ad11b-159">Nell'editor del progetto è quindi consigliabile usare la funzione di **configurazione Use Hand mesh** dal [plug-in Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal) con **XRVisualization abilitato** come parametro:</span><span class="sxs-lookup"><span data-stu-id="ad11b-159">Then in the blueprint editor, you should use **Set Use Hand Mesh** function from the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) with **Enabled XRVisualization** as a parameter:</span></span>

![Progetto di avvio dell'evento Play connesso per impostare Use Hand mesh Function con la modalità xrvisualization abilitata](images/unreal-hand-tracking-img-05.png)

<span data-ttu-id="ad11b-161">Per gestire il processo di rendering, è necessario usare il **controller di movimento di rendering** da XRVisualization:</span><span class="sxs-lookup"><span data-stu-id="ad11b-161">To manage the rendering process, you should use **Render Motion Controller** from XRVisualization:</span></span>

![Progetto della funzione Get Motion controller data connessa alla funzione di rendering del controller di movimento](images/unreal-hand-tracking-img-06.png)

<span data-ttu-id="ad11b-163">Ecco il risultato:</span><span class="sxs-lookup"><span data-stu-id="ad11b-163">The result:</span></span>

![Immagine della mano digitale sovrapposta a una mano umana reale](images/unreal-hand-tracking-img-07.png) 

<span data-ttu-id="ad11b-165">Se sono necessarie altre operazioni più complesse, ad esempio il disegno di una mesh mano con uno shader personalizzato, è necessario ottenere le mesh come geometria rilevata.</span><span class="sxs-lookup"><span data-stu-id="ad11b-165">If you need anything more complicated, such as drawing a hand mesh with a custom shader, you need to get the meshes as a tracked geometry.</span></span> 

## <a name="hand-rays"></a><span data-ttu-id="ad11b-166">Raggi mano</span><span class="sxs-lookup"><span data-stu-id="ad11b-166">Hand rays</span></span>

<span data-ttu-id="ad11b-167">Il recupero della disposizione è adatto a interazioni di chiusura, ad esempio l'acquisizione di oggetti o la pressione di pulsanti.</span><span class="sxs-lookup"><span data-stu-id="ad11b-167">Getting hand pose works for close interactions like grabbing objects or pressing buttons.</span></span> <span data-ttu-id="ad11b-168">Tuttavia, a volte è necessario lavorare con ologrammi lontani dagli utenti.</span><span class="sxs-lookup"><span data-stu-id="ad11b-168">However, sometimes you need to work with holograms that are far away from your users.</span></span> <span data-ttu-id="ad11b-169">Questa operazione può essere eseguita con i raggi mano, che possono essere usati come dispositivi di puntamento sia in C++ che nei progetti.</span><span class="sxs-lookup"><span data-stu-id="ad11b-169">This can be accomplished with hand rays, which can be used as pointing devices in both C++ and Blueprints.</span></span> <span data-ttu-id="ad11b-170">È possibile disegnare un raggio da una mano all'altra e, con alcuni aiuti dalla traccia del raggio non reale, selezionare un ologramma che altrimenti non sarà raggiungibile.</span><span class="sxs-lookup"><span data-stu-id="ad11b-170">You can draw a ray from your hand to a far point and, with some help from Unreal ray tracing, select a hologram that would otherwise be out of reach.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="ad11b-171">Poiché tutti i risultati della funzione cambiano ogni frame, sono tutti resi richiamabili.</span><span class="sxs-lookup"><span data-stu-id="ad11b-171">Since all function results change every frame, they're all made callable.</span></span> <span data-ttu-id="ad11b-172">Per ulteriori informazioni sulle funzioni pure e non pure o chiamabili, vedere il GUID utente del progetto nelle [funzioni](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span><span class="sxs-lookup"><span data-stu-id="ad11b-172">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span></span>

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a><span data-ttu-id="ad11b-173">Movimenti</span><span class="sxs-lookup"><span data-stu-id="ad11b-173">Gestures</span></span>

<span data-ttu-id="ad11b-174">HoloLens 2 tiene traccia dei movimenti spaziali, il che significa che è possibile acquisire tali movimenti come input.</span><span class="sxs-lookup"><span data-stu-id="ad11b-174">The HoloLens 2 tracks spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="ad11b-175">Il rilevamento dei movimenti si basa su un modello di sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="ad11b-175">Gesture tracking is based on a subscription model.</span></span> <span data-ttu-id="ad11b-176">Utilizzare la funzione "Configura movimenti" per indicare al dispositivo quali movimenti si desidera rilevare.  Per ulteriori informazioni sui movimenti, vedere il documento [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) .</span><span class="sxs-lookup"><span data-stu-id="ad11b-176">You should use the “Configure Gestures” function to tell the device which gestures you want to track.  You can find more details about gestures are the [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) document.</span></span>

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="ad11b-177">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="ad11b-177">Next Development Checkpoint</span></span>

<span data-ttu-id="ad11b-178">Se si segue il percorso delineato per lo sviluppo con Unreal, tenere presente che si stanno esplorando i blocchi predefiniti fondamentali di MRTK.</span><span class="sxs-lookup"><span data-stu-id="ad11b-178">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="ad11b-179">Da qui, è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="ad11b-179">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ad11b-180">Ancoraggi nello spazio locali</span><span class="sxs-lookup"><span data-stu-id="ad11b-180">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="ad11b-181">In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="ad11b-181">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ad11b-182">Fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="ad11b-182">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="ad11b-183">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="ad11b-183">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>
