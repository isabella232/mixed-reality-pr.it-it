---
title: Tracciamento mano in Unreal
description: Spiega come usare il rilevamento manuale in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realtà mista di Windows, verifica della mano, Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, sviluppo di giochi
ms.openlocfilehash: 5bc120f802c2160282befd1ce6cb8025be21cbaa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683081"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="892c9-104">Tracciamento mano in Unreal</span><span class="sxs-lookup"><span data-stu-id="892c9-104">Hand tracking in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="892c9-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="892c9-105">Overview</span></span>

<span data-ttu-id="892c9-106">Il sistema di rilevamento manuale usa le palme e le dita di una persona come input.</span><span class="sxs-lookup"><span data-stu-id="892c9-106">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="892c9-107">È possibile ottenere la posizione e la rotazione di ogni dito, l'intero Palm e persino i movimenti di mano da usare nel codice.</span><span class="sxs-lookup"><span data-stu-id="892c9-107">You can get the position and rotation of every finger, the entire palm, and even hand gestures to use in your code.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="892c9-108">Hand Pose</span><span class="sxs-lookup"><span data-stu-id="892c9-108">Hand Pose</span></span>

<span data-ttu-id="892c9-109">Hand Pose consente di tenere traccia delle mani e delle dita dell'utente attivo e di usarla come input, a cui è possibile accedere tramite progetti e C++.</span><span class="sxs-lookup"><span data-stu-id="892c9-109">Hand pose lets you track the hands and fingers of the active user and use it as input, which you can access through Blueprints and C++.</span></span> <span data-ttu-id="892c9-110">È possibile trovare dettagli più tecnici nell'API [Windows. Perception. people. HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) di Unreal.</span><span class="sxs-lookup"><span data-stu-id="892c9-110">You can find more technical details in Unreal's [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) API.</span></span> <span data-ttu-id="892c9-111">L'API Unreal invia i dati come sistema di coordinate, con segni di selezione sincronizzati con il motore irreale.</span><span class="sxs-lookup"><span data-stu-id="892c9-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

### <a name="understanding-the-bone-hierarchy"></a><span data-ttu-id="892c9-112">Informazioni sulla gerarchia ossea</span><span class="sxs-lookup"><span data-stu-id="892c9-112">Understanding the bone hierarchy</span></span>

<span data-ttu-id="892c9-113">L' `EWMRHandKeypoint` enumerazione descrive la gerarchia ossea della mano.</span><span class="sxs-lookup"><span data-stu-id="892c9-113">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="892c9-114">È possibile trovare ogni punto di riferimento della mano elencato nei progetti:</span><span class="sxs-lookup"><span data-stu-id="892c9-114">You can find each hand keypoint listed in your Blueprints:</span></span>

![BP punto di riferimento della mano](images/hand-keypoint-bp.png)

<span data-ttu-id="892c9-116">L'enumerazione C++ completa è elencata di seguito:</span><span class="sxs-lookup"><span data-stu-id="892c9-116">The full C++ enum is listed below:</span></span>
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

<span data-ttu-id="892c9-117">È possibile trovare i valori numerici per ogni case enum nella tabella [Windows. Perception. people. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) .</span><span class="sxs-lookup"><span data-stu-id="892c9-117">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span> <span data-ttu-id="892c9-118">Nell'immagine seguente viene illustrato l'intero layout di creazione della mano con i case enum corrispondenti:</span><span class="sxs-lookup"><span data-stu-id="892c9-118">The entire hand pose layout with matching enum cases is shown in the image below:</span></span>

![Scheletro mano](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a><span data-ttu-id="892c9-120">Supporto del rilevamento della mano</span><span class="sxs-lookup"><span data-stu-id="892c9-120">Supporting Hand Tracking</span></span>

<span data-ttu-id="892c9-121">È possibile usare il rilevamento manuale nei progetti, aggiungendo supporto per il **rilevamento** manuale **> realtà mista di Windows** :</span><span class="sxs-lookup"><span data-stu-id="892c9-121">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality** :</span></span>

![Verifica della mano BP](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="892c9-123">Questa funzione restituisce `true` se il rilevamento manuale è supportato nel dispositivo e `false` se il rilevamento manuale non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="892c9-123">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking is not available.</span></span>

![Supporta la verifica della mano BP](images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="892c9-125">C++:</span><span class="sxs-lookup"><span data-stu-id="892c9-125">C++:</span></span> 

<span data-ttu-id="892c9-126">Includere `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span><span class="sxs-lookup"><span data-stu-id="892c9-126">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="892c9-127">Recupero del rilevamento della mano</span><span class="sxs-lookup"><span data-stu-id="892c9-127">Getting Hand Tracking</span></span>
<span data-ttu-id="892c9-128">È possibile utilizzare **GetHandJointTransform** per restituire i dati spaziali dalla mano.</span><span class="sxs-lookup"><span data-stu-id="892c9-128">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="892c9-129">I dati vengono aggiornati ogni frame, ma se ci si trova all'interno di un frame i valori restituiti vengono memorizzati nella cache.</span><span class="sxs-lookup"><span data-stu-id="892c9-129">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="892c9-130">Per motivi di prestazioni, non è consigliabile usare una logica intensa in questa funzione.</span><span class="sxs-lookup"><span data-stu-id="892c9-130">It's not recommended to have heavy logic in this function for performance reasons.</span></span> 

![Ottenere la trasformazione congiunta della mano](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="892c9-132">C++:</span><span class="sxs-lookup"><span data-stu-id="892c9-132">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="892c9-133">Suddivisione parametri funzione:</span><span class="sxs-lookup"><span data-stu-id="892c9-133">Function parameter breakdown:</span></span>

* <span data-ttu-id="892c9-134">**Hand** : è il lato sinistro o destro dell'utente</span><span class="sxs-lookup"><span data-stu-id="892c9-134">**Hand** – an be the left or right hand of the user</span></span>
* <span data-ttu-id="892c9-135">**Punto di riferimento** : l'osso della mano.</span><span class="sxs-lookup"><span data-stu-id="892c9-135">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="892c9-136">**Transform** : coordinate e orientamento della base dell'osso.</span><span class="sxs-lookup"><span data-stu-id="892c9-136">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="892c9-137">È possibile richiedere la base dell'osso successivo per ottenere i dati di trasformazione per la fine di un osso.</span><span class="sxs-lookup"><span data-stu-id="892c9-137">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="892c9-138">Un osso Tip speciale fornisce la fine del valore distali.</span><span class="sxs-lookup"><span data-stu-id="892c9-138">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="892c9-139">**RADIUS** : raggio della base dell'osso.</span><span class="sxs-lookup"><span data-stu-id="892c9-139">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="892c9-140">**Valore restituito** : true se l'osso rileva il frame, false se l'osso non viene rilevato.</span><span class="sxs-lookup"><span data-stu-id="892c9-140">**Return Value** — true if the bone is tracked this frame, false if the bone is not tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="892c9-141">Animazione collegamento dinamico</span><span class="sxs-lookup"><span data-stu-id="892c9-141">Hand Live Link Animation</span></span>
<span data-ttu-id="892c9-142">Le pose della mano vengono esposte all'animazione usando il plug-in [Live link](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span><span class="sxs-lookup"><span data-stu-id="892c9-142">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="892c9-143">Se sono abilitati i plug-in della realtà mista di Windows e dei collegamenti dinamici:</span><span class="sxs-lookup"><span data-stu-id="892c9-143">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span> 
1. <span data-ttu-id="892c9-144">Selezionare **finestra > collegamento Live** per aprire la finestra dell'editor di collegamento Live.</span><span class="sxs-lookup"><span data-stu-id="892c9-144">Select **Window > Live Link** to open the Live Link editor window.</span></span> 
2. <span data-ttu-id="892c9-145">Fare clic su **origine** e abilitare l' **origine rilevamento a mano della realtà mista di Windows**</span><span class="sxs-lookup"><span data-stu-id="892c9-145">Click **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![Origine collegamento dinamico](images/unreal/live-link-source.png)
 
<span data-ttu-id="892c9-147">Dopo aver abilitato l'origine e aperto un asset di animazione, espandere la sezione **animazione** nella scheda della **scena anteprima** . vedere anche opzioni aggiuntive (i dettagli sono disponibili nella documentazione del collegamento Live di Unreal, perché il plug-in è in versione beta, il processo potrebbe cambiare in seguito).</span><span class="sxs-lookup"><span data-stu-id="892c9-147">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options (the details are in Unreal’s Live Link documentation - as the plugin is in beta, the process may change later).</span></span>

![Animazione collegamento dinamico](images/unreal/live-link-animation.png)
 
<span data-ttu-id="892c9-149">La gerarchia di animazione della mano è identica a quella di `EWMRHandKeypoint` .</span><span class="sxs-lookup"><span data-stu-id="892c9-149">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="892c9-150">L'animazione può essere ridestinata usando **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** :</span><span class="sxs-lookup"><span data-stu-id="892c9-150">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** :</span></span>

![Animazione collegamento dinamico 2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="892c9-152">Può anche essere sottoclassato nell'Editor:</span><span class="sxs-lookup"><span data-stu-id="892c9-152">It can also be subclassed in the editor:</span></span>

![Modifica del mapping di Live link](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a><span data-ttu-id="892c9-154">Accesso ai dati della rete a mano</span><span class="sxs-lookup"><span data-stu-id="892c9-154">Accessing Hand Mesh Data</span></span>

![Mesh mano](images/unreal/hand-mesh.png)

<span data-ttu-id="892c9-156">Prima di poter accedere ai dati della mesh a mano, è necessario:</span><span class="sxs-lookup"><span data-stu-id="892c9-156">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="892c9-157">Selezionare l'asset **ARSessionConfig** , espandere impostazioni **AR-> Impostazioni mapping del mondo** e selezionare **genera dati mesh da geometria rilevata** .</span><span class="sxs-lookup"><span data-stu-id="892c9-157">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry** .</span></span> 

<span data-ttu-id="892c9-158">Di seguito sono riportati i parametri di mesh predefiniti:</span><span class="sxs-lookup"><span data-stu-id="892c9-158">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="892c9-159">Usare i dati mesh per l'occlusione</span><span class="sxs-lookup"><span data-stu-id="892c9-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="892c9-160">Genera collisione per i dati mesh</span><span class="sxs-lookup"><span data-stu-id="892c9-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="892c9-161">Genera la mesh NAV per i dati mesh</span><span class="sxs-lookup"><span data-stu-id="892c9-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="892c9-162">Eseguire il rendering dei dati mesh nel parametro wireframe-debug che mostra la mesh generata</span><span class="sxs-lookup"><span data-stu-id="892c9-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="892c9-163">Questi valori di parametro vengono usati come il mapping spaziale mesh e le impostazioni predefinite mesh a mano.</span><span class="sxs-lookup"><span data-stu-id="892c9-163">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="892c9-164">È possibile modificarli in qualsiasi momento in progetti o codice per qualsiasi mesh.</span><span class="sxs-lookup"><span data-stu-id="892c9-164">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="892c9-165">Informazioni di riferimento sulle API C++</span><span class="sxs-lookup"><span data-stu-id="892c9-165">C++ API Reference</span></span> 
<span data-ttu-id="892c9-166">Usare `EEARObjectClassification` per trovare i valori della mesh mano in tutti gli oggetti rilevabili.</span><span class="sxs-lookup"><span data-stu-id="892c9-166">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

<span data-ttu-id="892c9-167">I delegati seguenti vengono chiamati quando il sistema rileva qualsiasi oggetto rilevabile, inclusa una mesh mano.</span><span class="sxs-lookup"><span data-stu-id="892c9-167">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 

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

<span data-ttu-id="892c9-168">Assicurarsi che i gestori del delegato seguano la firma della funzione seguente:</span><span class="sxs-lookup"><span data-stu-id="892c9-168">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="892c9-169">È possibile accedere ai dati mesh tramite  `UARTrackedGeometry::GetUnderlyingMesh` :</span><span class="sxs-lookup"><span data-stu-id="892c9-169">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a><span data-ttu-id="892c9-170">Riferimento all'API Blueprint</span><span class="sxs-lookup"><span data-stu-id="892c9-170">Blueprint API Reference</span></span>

<span data-ttu-id="892c9-171">Per lavorare con le mesh mano nei progetti:</span><span class="sxs-lookup"><span data-stu-id="892c9-171">In order to work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="892c9-172">Aggiungere un componente **ARTrackableNotify** a un attore del progetto</span><span class="sxs-lookup"><span data-stu-id="892c9-172">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![Notifica ARTrackable](images/unreal/ar-trackable-notify.png)
 
2. <span data-ttu-id="892c9-174">Passare al pannello dei **Dettagli** ed espandere la sezione **eventi** .</span><span class="sxs-lookup"><span data-stu-id="892c9-174">Go to the **Details** panel and expand the **Events** section.</span></span> 

![Notifica ARTrackable 2](images/unreal/ar-trackable-notify2.png)
 
3. <span data-ttu-id="892c9-176">Sovrascrivi in Aggiungi/Aggiorna/Rimuovi geometria rilevata con i nodi seguenti nel grafico eventi:</span><span class="sxs-lookup"><span data-stu-id="892c9-176">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![In ARTrackable notifica](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="892c9-178">Raggi mano</span><span class="sxs-lookup"><span data-stu-id="892c9-178">Hand Rays</span></span>

<span data-ttu-id="892c9-179">È possibile usare un raggio di mano come un dispositivo di puntamento sia in C++ che nei progetti, che espone l'API [Windows. UI. input. Spatial. SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) .</span><span class="sxs-lookup"><span data-stu-id="892c9-179">You can use a hand ray as a pointing device in both C++ and Blueprints, which exposes the [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API.</span></span>

<span data-ttu-id="892c9-180">È importante ricordare che, poiché i risultati di tutte le funzioni cambiano ogni frame, sono tutti resi richiamabili.</span><span class="sxs-lookup"><span data-stu-id="892c9-180">It’s important to mention that since the results of all the functions change every frame, they're all made callable.</span></span> <span data-ttu-id="892c9-181">Per ulteriori informazioni sulle funzioni pure e non pure o chiamabili, vedere il progetto GUID utente sulle [funzioni](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span><span class="sxs-lookup"><span data-stu-id="892c9-181">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span></span>

<span data-ttu-id="892c9-182">Per utilizzare i raggi mano nei progetti, cercare le azioni in **HMD realtà mista di Windows** :</span><span class="sxs-lookup"><span data-stu-id="892c9-182">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD** :</span></span>

![Raggi mano BP](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="892c9-184">Per accedere ad essi in C++, includere nella `WindowsMixedRealityFunctionLibrary.h` parte superiore del file di codice chiamante.</span><span class="sxs-lookup"><span data-stu-id="892c9-184">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="892c9-185">Enumerazione</span><span class="sxs-lookup"><span data-stu-id="892c9-185">Enum</span></span>
<span data-ttu-id="892c9-186">È anche possibile accedere ai case di input in **EHMDInputControllerButtons** , che possono essere usati nei progetti:</span><span class="sxs-lookup"><span data-stu-id="892c9-186">You also have access to input cases under **EHMDInputControllerButtons** , which can be used in Blueprints:</span></span>

![Pulsanti del controller di input](images/unreal/input-controller-buttons.png)

<span data-ttu-id="892c9-188">Per l'accesso in C++, usare la `EHMDInputControllerButtons` classe enum:</span><span class="sxs-lookup"><span data-stu-id="892c9-188">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="892c9-189">Di seguito è riportata una suddivisione dei due case enum applicabili:</span><span class="sxs-lookup"><span data-stu-id="892c9-189">Below is a breakdown of the two applicable enum cases:</span></span>
* <span data-ttu-id="892c9-190">**Selezionare** l'evento di selezione attivato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="892c9-190">**Select** - User triggered Select event.</span></span> 
    * <span data-ttu-id="892c9-191">L'evento può essere attivato in HoloLens 2 tramite il tocco di aria, lo sguardo e il commit oppure "Select" con l' [input vocale](unreal-voice-input.md) abilitato.</span><span class="sxs-lookup"><span data-stu-id="892c9-191">The event can be triggered in HoloLens 2 by air-tap, gaze and commit, or by saying “Select” with [voice input](unreal-voice-input.md) enabled.</span></span> 
* <span data-ttu-id="892c9-192">L' **evento di comprensione** attivato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="892c9-192">**Grasp** - User triggered Grasp event.</span></span> 
    * <span data-ttu-id="892c9-193">Questo evento può essere attivato in HoloLens 2 chiudendo le dita dell'utente su un ologramma.</span><span class="sxs-lookup"><span data-stu-id="892c9-193">This event can be triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 

<span data-ttu-id="892c9-194">È possibile accedere allo stato di rilevamento della mesh mano in C++ tramite l' `EHMDTrackingStatus` enumerazione illustrata di seguito:</span><span class="sxs-lookup"><span data-stu-id="892c9-194">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="892c9-195">Di seguito è riportata una suddivisione dei due case enum applicabili:</span><span class="sxs-lookup"><span data-stu-id="892c9-195">Below is a breakdown of the two applicable enum cases:</span></span>
* <span data-ttu-id="892c9-196">**NotTracked** : la mano non è visibile</span><span class="sxs-lookup"><span data-stu-id="892c9-196">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="892c9-197">**Rilevato** : la mano viene rilevata completamente</span><span class="sxs-lookup"><span data-stu-id="892c9-197">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="892c9-198">Struct</span><span class="sxs-lookup"><span data-stu-id="892c9-198">Struct</span></span>
<span data-ttu-id="892c9-199">Lo struct PointerPoseInfo può fornire informazioni sui dati della mano seguenti:</span><span class="sxs-lookup"><span data-stu-id="892c9-199">The PointerPoseInfo struct can give you information on the following hand data:</span></span>
* <span data-ttu-id="892c9-200">**Origin** : origine della mano</span><span class="sxs-lookup"><span data-stu-id="892c9-200">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="892c9-201">**Direzione** : direzione della mano</span><span class="sxs-lookup"><span data-stu-id="892c9-201">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="892c9-202">Vettore **attivo** della mano</span><span class="sxs-lookup"><span data-stu-id="892c9-202">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="892c9-203">**Orientamento** -quaternione orientamento</span><span class="sxs-lookup"><span data-stu-id="892c9-203">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="892c9-204">**Stato di rilevamento** -stato di rilevamento corrente</span><span class="sxs-lookup"><span data-stu-id="892c9-204">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="892c9-205">È possibile accedere a questo con i progetti, come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="892c9-205">You can access this through Blueprints, as shown below:</span></span>

![Indicatore di posa indicatore BP](images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="892c9-207">O con C++:</span><span class="sxs-lookup"><span data-stu-id="892c9-207">Or with C++:</span></span>

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a><span data-ttu-id="892c9-208">Funzioni</span><span class="sxs-lookup"><span data-stu-id="892c9-208">Functions</span></span>

<span data-ttu-id="892c9-209">Tutte le funzioni elencate di seguito possono essere chiamate in ogni frame, che consente il monitoraggio continuo.</span><span class="sxs-lookup"><span data-stu-id="892c9-209">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span> 

1. <span data-ttu-id="892c9-210">**Get Pointer post info** restituisce informazioni complete sulla direzione del raggio di mano nel frame corrente.</span><span class="sxs-lookup"><span data-stu-id="892c9-210">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span> 

<span data-ttu-id="892c9-211">Progetto</span><span class="sxs-lookup"><span data-stu-id="892c9-211">Blueprint:</span></span>

![Ottenere le informazioni sulla posa del puntatore](images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="892c9-213">C++:</span><span class="sxs-lookup"><span data-stu-id="892c9-213">C++:</span></span> 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="892c9-214">**Viene** restituito true se la mano viene afferrata nel frame corrente.</span><span class="sxs-lookup"><span data-stu-id="892c9-214">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="892c9-215">Progetto</span><span class="sxs-lookup"><span data-stu-id="892c9-215">Blueprint:</span></span>

![Viene afferrato BP](images/unreal/is-grasped-bp.png)

<span data-ttu-id="892c9-217">C++:</span><span class="sxs-lookup"><span data-stu-id="892c9-217">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. <span data-ttu-id="892c9-218">**Is Select Pressed** restituisce true se l'utente ha attivato SELECT nel frame corrente.</span><span class="sxs-lookup"><span data-stu-id="892c9-218">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="892c9-219">Progetto</span><span class="sxs-lookup"><span data-stu-id="892c9-219">Blueprint:</span></span>

![Seleziona BP premuto](images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="892c9-221">C++:</span><span class="sxs-lookup"><span data-stu-id="892c9-221">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="892c9-222">Il **pulsante è selezionato** restituisce true se l'evento o il pulsante viene attivato nel frame corrente.</span><span class="sxs-lookup"><span data-stu-id="892c9-222">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="892c9-223">Progetto</span><span class="sxs-lookup"><span data-stu-id="892c9-223">Blueprint:</span></span>

![Pulsante è selezionato BP](images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="892c9-225">C++:</span><span class="sxs-lookup"><span data-stu-id="892c9-225">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="892c9-226">**Ottenere** lo stato di rilevamento del controller restituisce lo stato di rilevamento nel frame corrente.</span><span class="sxs-lookup"><span data-stu-id="892c9-226">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="892c9-227">Progetto</span><span class="sxs-lookup"><span data-stu-id="892c9-227">Blueprint:</span></span>

![Ottenere lo stato di rilevamento del controller BP](images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="892c9-229">C++:</span><span class="sxs-lookup"><span data-stu-id="892c9-229">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a><span data-ttu-id="892c9-230">Movimenti</span><span class="sxs-lookup"><span data-stu-id="892c9-230">Gestures</span></span>

<span data-ttu-id="892c9-231">Hololens 2 consente di tenere traccia dei movimenti spaziali, il che significa che è possibile acquisire tali movimenti come input.</span><span class="sxs-lookup"><span data-stu-id="892c9-231">The Hololens 2 can track spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="892c9-232">Per ulteriori informazioni sui movimenti, vedere il documento [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) .</span><span class="sxs-lookup"><span data-stu-id="892c9-232">You can find more details about gestures are the [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) document.</span></span>

<span data-ttu-id="892c9-233">È possibile trovare la funzione Blueprint in **input spaziale di realtà mista di Windows** e la funzione C++ aggiungendo `WindowsMixedRealitySpatialInputFunctionLibrary.h` nel file di codice chiamante.</span><span class="sxs-lookup"><span data-stu-id="892c9-233">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input** , and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![Acquisisci movimenti](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="892c9-235">Enumerazione</span><span class="sxs-lookup"><span data-stu-id="892c9-235">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="892c9-236">Progetto</span><span class="sxs-lookup"><span data-stu-id="892c9-236">Blueprint:</span></span> 

![Tipo di movimento](images/unreal/gesture-type.png)

<span data-ttu-id="892c9-238">C++:</span><span class="sxs-lookup"><span data-stu-id="892c9-238">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="892c9-239">Funzione</span><span class="sxs-lookup"><span data-stu-id="892c9-239">Function</span></span>
<span data-ttu-id="892c9-240">È possibile abilitare e disabilitare l'acquisizione di movimenti con la `CaptureGestures` funzione.</span><span class="sxs-lookup"><span data-stu-id="892c9-240">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="892c9-241">Quando un movimento abilitato genera eventi di input, la funzione restituisce `true` se l'acquisizione del movimento riesce e `false` se si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="892c9-241">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="892c9-242">Progetto</span><span class="sxs-lookup"><span data-stu-id="892c9-242">Blueprint:</span></span>

![Movimenti di acquisizione BP](images/unreal/capture-gestures-bp.png)

<span data-ttu-id="892c9-244">C++:</span><span class="sxs-lookup"><span data-stu-id="892c9-244">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

<span data-ttu-id="892c9-245">Di seguito sono riportati gli eventi chiave che è possibile trovare in progetti e C++: ![ eventi chiave](images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="892c9-245">The following are key events, which you can find in Blueprints and C++: ![Key Events](images/unreal/key-events.png)</span></span>

![Eventi chiave 2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

## <a name="next-development-checkpoint"></a><span data-ttu-id="892c9-247">Checkpoint di sviluppo successivo</span><span class="sxs-lookup"><span data-stu-id="892c9-247">Next Development Checkpoint</span></span>

<span data-ttu-id="892c9-248">Se si segue il percorso di checkpoint dello sviluppo non reale, si sta per esplorare i blocchi predefiniti di MRTK core.</span><span class="sxs-lookup"><span data-stu-id="892c9-248">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="892c9-249">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="892c9-249">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="892c9-250">Ancoraggi nello spazio locali</span><span class="sxs-lookup"><span data-stu-id="892c9-250">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="892c9-251">In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="892c9-251">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="892c9-252">Fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="892c9-252">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="892c9-253">È sempre possibile tornare ai checkpoint di [sviluppo non reali](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="892c9-253">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>