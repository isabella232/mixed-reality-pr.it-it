---
title: Rendering in DirectX
description: Informazioni su come aggiornare ed eseguire il rendering del contenuto nelle applicazioni DirectX per la realtà mista di Windows.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, rendering, grafica 3D, HolographicFrame, ciclo di rendering, ciclo di aggiornamento, procedura dettagliata, codice di esempio, Direct3D
ms.openlocfilehash: aafead61b45550f499405ae63bda7d7f8e79d224
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006721"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="88773-104">Rendering in DirectX</span><span class="sxs-lookup"><span data-stu-id="88773-104">Rendering in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="88773-105">Questo articolo si riferisce alle API native di WinRT legacy.</span><span class="sxs-lookup"><span data-stu-id="88773-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="88773-106">Per i nuovi progetti di app native, è consigliabile usare l' **[API OpenXR](openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="88773-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="88773-107">La realtà mista di Windows si basa su DirectX per produrre un'esperienza grafica 3D avanzata per gli utenti.</span><span class="sxs-lookup"><span data-stu-id="88773-107">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="88773-108">L'astrazione del rendering si trova appena sopra DirectX, che consente alle app di ragionare sulla posizione e sull'orientamento degli osservatori di scena olografici previsti dal sistema.</span><span class="sxs-lookup"><span data-stu-id="88773-108">The rendering abstraction sits just above DirectX, which lets apps reason about the position and orientation of holographic scene observers predicted by the system.</span></span> <span data-ttu-id="88773-109">Lo sviluppatore può quindi trovare i propri ologrammi in base a ogni fotocamera, consentendo all'app di eseguire il rendering di questi ologrammi in vari sistemi di coordinate spaziali quando l'utente si sposta.</span><span class="sxs-lookup"><span data-stu-id="88773-109">The developer can then locate their holograms based on each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

<span data-ttu-id="88773-110">Nota: in questa procedura dettagliata viene descritto il rendering olografico in Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="88773-110">Note: This walkthrough describes holographic rendering in Direct3D 11.</span></span> <span data-ttu-id="88773-111">Un modello di app per la realtà mista Direct3D 12 Windows viene fornito anche con l'estensione dei modelli di app per realtà mista.</span><span class="sxs-lookup"><span data-stu-id="88773-111">A Direct3D 12 Windows Mixed Reality app template is also supplied with the Mixed Reality app templates extension.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="88773-112">Aggiornamento per il frame corrente</span><span class="sxs-lookup"><span data-stu-id="88773-112">Update for the current frame</span></span>

<span data-ttu-id="88773-113">Per aggiornare lo stato dell'applicazione per gli ologrammi, una volta per ogni fotogramma l'app:</span><span class="sxs-lookup"><span data-stu-id="88773-113">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="88773-114">Ottenere un <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> dal sistema di gestione dello schermo.</span><span class="sxs-lookup"><span data-stu-id="88773-114">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="88773-115">Aggiornare la scena con la stima corrente del punto in cui la visualizzazione della fotocamera sarà quando il rendering viene completato.</span><span class="sxs-lookup"><span data-stu-id="88773-115">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="88773-116">Si noti che la scena olografica può contenere più di una fotocamera.</span><span class="sxs-lookup"><span data-stu-id="88773-116">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="88773-117">Per eseguire il rendering delle visualizzazioni della fotocamera olografica, una volta per ogni fotogramma l'app:</span><span class="sxs-lookup"><span data-stu-id="88773-117">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="88773-118">Per ogni fotocamera, eseguire il rendering della scena per il frame corrente, usando la visualizzazione della fotocamera e le matrici di proiezione dal sistema.</span><span class="sxs-lookup"><span data-stu-id="88773-118">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="88773-119">Creare un nuovo frame olografico e ottenere la relativa stima</span><span class="sxs-lookup"><span data-stu-id="88773-119">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="88773-120">Il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> contiene informazioni necessarie all'app per aggiornare ed eseguire il rendering del frame corrente.</span><span class="sxs-lookup"><span data-stu-id="88773-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs to update and render the current frame.</span></span> <span data-ttu-id="88773-121">L'app avvia ogni nuovo frame chiamando il metodo **CreateNextFrame** .</span><span class="sxs-lookup"><span data-stu-id="88773-121">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="88773-122">Quando viene chiamato questo metodo, le stime vengono effettuate usando i dati dei sensori più recenti disponibili e incapsulati nell'oggetto **CurrentPrediction** .</span><span class="sxs-lookup"><span data-stu-id="88773-122">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="88773-123">Per ogni frame sottoposto a rendering è necessario usare un nuovo oggetto frame perché è valido solo per un istante di tempo.</span><span class="sxs-lookup"><span data-stu-id="88773-123">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="88773-124">La proprietà **CurrentPrediction** contiene informazioni come la posizione della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="88773-124">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="88773-125">Le informazioni vengono estrapolate nel momento esatto in cui il frame dovrebbe essere visibile all'utente.</span><span class="sxs-lookup"><span data-stu-id="88773-125">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="88773-126">Il codice seguente è tratto da **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="88773-126">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="88773-127">Elaborare gli aggiornamenti della fotocamera</span><span class="sxs-lookup"><span data-stu-id="88773-127">Process camera updates</span></span>

<span data-ttu-id="88773-128">I buffer indietro possono variare da frame a frame.</span><span class="sxs-lookup"><span data-stu-id="88773-128">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="88773-129">L'app deve convalidare il buffer nascosto per ogni fotocamera e rilasciare e ricreare le visualizzazioni delle risorse e i buffer di profondità in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="88773-129">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="88773-130">Si noti che il set di pose nella stima è l'elenco autorevole di fotocamere utilizzate nel frame corrente.</span><span class="sxs-lookup"><span data-stu-id="88773-130">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="88773-131">In genere, questo elenco viene usato per eseguire l'iterazione sul set di fotocamere.</span><span class="sxs-lookup"><span data-stu-id="88773-131">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="88773-132">Da **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="88773-132">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="88773-133">Da **DeviceResources:: EnsureCameraResources**:</span><span class="sxs-lookup"><span data-stu-id="88773-133">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="88773-134">Ottenere il sistema di coordinate da utilizzare come base per il rendering</span><span class="sxs-lookup"><span data-stu-id="88773-134">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="88773-135">La realtà mista di Windows consente all'app di creare vari [sistemi di coordinate](coordinate-systems-in-directx.md), ad esempio frame di riferimento allegati e stazionari per i percorsi di rilevamento nel mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="88773-135">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md), like attached and stationary reference frames for tracking locations in the physical world.</span></span> <span data-ttu-id="88773-136">L'app può quindi usare questi sistemi di coordinate per motivare la posizione in cui eseguire il rendering degli ologrammi per ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="88773-136">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="88773-137">Quando si richiedono le coordinate da un'API, si passerà sempre il <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> all'interno del quale si desidera esprimere le coordinate.</span><span class="sxs-lookup"><span data-stu-id="88773-137">When requesting coordinates from an API, you'll always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="88773-138">Da **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="88773-138">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="88773-139">Questi sistemi di coordinate possono quindi essere utilizzati per generare matrici di visualizzazione stereo durante il rendering del contenuto nella scena.</span><span class="sxs-lookup"><span data-stu-id="88773-139">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="88773-140">Da **CameraResources:: UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="88773-140">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="88773-141">Input di sguardi e movimenti del processo</span><span class="sxs-lookup"><span data-stu-id="88773-141">Process gaze and gesture input</span></span>

<span data-ttu-id="88773-142">Gli input [sguardo](gaze-in-directx.md) e [mano](hands-and-motion-controllers-in-directx.md) non sono basati sul tempo e non è necessario aggiornarli nella funzione **StepTimer** .</span><span class="sxs-lookup"><span data-stu-id="88773-142">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input aren't time-based and don't have to update in the **StepTimer** function.</span></span> <span data-ttu-id="88773-143">Tuttavia, questo input è un elemento che l'app deve esaminare per ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="88773-143">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="88773-144">Elaborare gli aggiornamenti basati sul tempo</span><span class="sxs-lookup"><span data-stu-id="88773-144">Process time-based updates</span></span>

<span data-ttu-id="88773-145">Qualsiasi app per il rendering in tempo reale richiede un modo per elaborare gli aggiornamenti basati sul tempo. il modello di app olografico di Windows usa un'implementazione di **StepTimer** , simile a StepTimer fornito nel modello di app DirectX 11 UWP.</span><span class="sxs-lookup"><span data-stu-id="88773-145">Any real-time rendering app will need some way to process time-based updates - the Windows Holographic app template uses a **StepTimer** implementation, similar to the StepTimer provided in the DirectX 11 UWP app template.</span></span> <span data-ttu-id="88773-146">Questa classe helper di esempio StepTimer può fornire aggiornamenti fissi in fase di esecuzione, aggiornamenti variabili del tempo e la modalità predefinita prevede intervalli temporali variabili.</span><span class="sxs-lookup"><span data-stu-id="88773-146">This StepTimer sample helper class can provide fixed time-step updates, variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="88773-147">Per il rendering olografico, è stato scelto di non inserire troppo nella funzione timer perché è possibile configurarla in modo che sia un passaggio di tempo fisso.</span><span class="sxs-lookup"><span data-stu-id="88773-147">For holographic rendering, we've chosen not to put too much into the timer function because you can configure it to be a fixed time step.</span></span> <span data-ttu-id="88773-148">Potrebbe essere chiamato più di una volta per frame, o non per alcuni frame, e gli aggiornamenti dei dati olografici dovrebbero essere eseguiti una sola volta per ogni fotogramma.</span><span class="sxs-lookup"><span data-stu-id="88773-148">It might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="88773-149">Da **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="88773-149">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="88773-150">Posizionare e ruotare gli ologrammi nel sistema di coordinate</span><span class="sxs-lookup"><span data-stu-id="88773-150">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="88773-151">Se si opera in un sistema di coordinate singolo, come nel caso del modello con il **SpatialStationaryReferenceFrame**, questo processo non è diverso da quello che viene usato altrimenti in grafica 3D.</span><span class="sxs-lookup"><span data-stu-id="88773-151">If you're operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="88773-152">Qui viene ruotato il cubo e la matrice del modello viene impostata in base alla posizione nel sistema di coordinate fisse.</span><span class="sxs-lookup"><span data-stu-id="88773-152">Here, we rotate the cube and set the model matrix based on the position in the stationary coordinate system.</span></span>

<span data-ttu-id="88773-153">Da **SpinningCubeRenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="88773-153">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

<span data-ttu-id="88773-154">**Nota sugli scenari avanzati:** Il cubo rotante è un semplice esempio di come posizionare un ologramma all'interno di un singolo frame di riferimento.</span><span class="sxs-lookup"><span data-stu-id="88773-154">**Note about advanced scenarios:** The spinning cube is a simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="88773-155">È anche possibile [usare più SpatialCoordinateSystems](coordinate-systems-in-directx.md) nello stesso frame sottoposto a rendering, allo stesso tempo.</span><span class="sxs-lookup"><span data-stu-id="88773-155">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="88773-156">Aggiornare i dati del buffer costante</span><span class="sxs-lookup"><span data-stu-id="88773-156">Update constant buffer data</span></span>

<span data-ttu-id="88773-157">Le trasformazioni del modello per il contenuto vengono aggiornate come di consueto.</span><span class="sxs-lookup"><span data-stu-id="88773-157">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="88773-158">A questo punto sono state calcolate le trasformazioni valide per il sistema di coordinate in cui verrà eseguito il rendering.</span><span class="sxs-lookup"><span data-stu-id="88773-158">By now, you'll have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="88773-159">Da **SpinningCubeRenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="88773-159">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

<span data-ttu-id="88773-160">Informazioni sulle trasformazioni di visualizzazione e proiezione</span><span class="sxs-lookup"><span data-stu-id="88773-160">What about view and projection transforms?</span></span> <span data-ttu-id="88773-161">Per ottenere risultati ottimali, è necessario attendere fino a quando non si è pronti per le chiamate di estrazione.</span><span class="sxs-lookup"><span data-stu-id="88773-161">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="88773-162">Esegue il rendering del frame corrente</span><span class="sxs-lookup"><span data-stu-id="88773-162">Render the current frame</span></span>

<span data-ttu-id="88773-163">Il rendering in realtà mista di Windows non è molto diverso dal rendering in una visualizzazione mono 2D, ma vi sono alcune differenze:</span><span class="sxs-lookup"><span data-stu-id="88773-163">Rendering on Windows Mixed Reality isn't much different from rendering on a 2D mono display, but there are a few differences:</span></span>
* <span data-ttu-id="88773-164">Le stime del frame olografico sono importanti.</span><span class="sxs-lookup"><span data-stu-id="88773-164">Holographic frame predictions are important.</span></span> <span data-ttu-id="88773-165">Più si avvicina la stima a quando viene presentato il frame, migliore sarà l'aspetto degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="88773-165">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="88773-166">La realtà mista di Windows controlla le visualizzazioni della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="88773-166">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="88773-167">Eseguirne il rendering in ognuno di essi poiché il frame olografico li mostrerà in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="88773-167">Render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="88773-168">Si consiglia di eseguire il rendering stereo utilizzando il disegno istanza in una matrice di destinazione di rendering.</span><span class="sxs-lookup"><span data-stu-id="88773-168">We recommend doing stereo rendering using instanced drawing to a render target array.</span></span> <span data-ttu-id="88773-169">Il modello di app olografico usa l'approccio consigliato del disegno di istanza in una matrice di destinazione di rendering, che usa una visualizzazione della destinazione di rendering in un **Texture2DArray**.</span><span class="sxs-lookup"><span data-stu-id="88773-169">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="88773-170">Se si vuole eseguire il rendering senza usare le istanze stereo, è necessario creare due RenderTargetViews non di matrice, uno per ogni occhio.</span><span class="sxs-lookup"><span data-stu-id="88773-170">If you want to render without using stereo instancing, you'll need to create two non-array RenderTargetViews, one for each eye.</span></span> <span data-ttu-id="88773-171">Ogni RenderTargetViews fa riferimento a una delle due sezioni in **Texture2DArray** fornite all'app dal sistema.</span><span class="sxs-lookup"><span data-stu-id="88773-171">Each RenderTargetViews references one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="88773-172">Questa operazione non è consigliata, in quanto è in genere più lenta rispetto all'uso della creazione di istanze.</span><span class="sxs-lookup"><span data-stu-id="88773-172">This isn't recommended, as it's typically slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="88773-173">Ottenere una stima HolographicFrame aggiornata</span><span class="sxs-lookup"><span data-stu-id="88773-173">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="88773-174">L'aggiornamento della stima del frame migliora l'efficacia della stabilizzazione dell'immagine.</span><span class="sxs-lookup"><span data-stu-id="88773-174">Updating the frame prediction enhances the effectiveness of image stabilization.</span></span> <span data-ttu-id="88773-175">Si ottiene un posizionamento più accurato degli ologrammi a causa del tempo più breve tra la stima e quando il frame è visibile all'utente.</span><span class="sxs-lookup"><span data-stu-id="88773-175">You get more accurate positioning of holograms because of the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="88773-176">Aggiornare idealmente la stima dei frame immediatamente prima del rendering.</span><span class="sxs-lookup"><span data-stu-id="88773-176">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="88773-177">Rendering in ogni fotocamera</span><span class="sxs-lookup"><span data-stu-id="88773-177">Render to each camera</span></span>

<span data-ttu-id="88773-178">Il ciclo del set di fotocamere si pone nella stima e viene eseguito il rendering in ogni fotocamera in questo set.</span><span class="sxs-lookup"><span data-stu-id="88773-178">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="88773-179">**Configurare la sessione di rendering**</span><span class="sxs-lookup"><span data-stu-id="88773-179">**Set up your rendering pass**</span></span>

<span data-ttu-id="88773-180">La realtà mista di Windows usa il rendering stereoscopico per migliorare l'illusione della profondità e per eseguire il rendering in modo stereoscopico, in modo che sia la visualizzazione a sinistra che quella destra siano attive</span><span class="sxs-lookup"><span data-stu-id="88773-180">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="88773-181">Con il rendering stereoscopico, esiste un offset tra le due visualizzazioni, che il cervello può riconciliare come profondità effettiva.</span><span class="sxs-lookup"><span data-stu-id="88773-181">With stereoscopic rendering, there's an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="88773-182">Questa sezione illustra il rendering stereoscopico usando le istanze, usando il codice del modello di app olografico di Windows.</span><span class="sxs-lookup"><span data-stu-id="88773-182">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="88773-183">Ogni fotocamera ha una propria destinazione di rendering (buffer nascosto) e matrici di visualizzazione e proiezione nello spazio olografico.</span><span class="sxs-lookup"><span data-stu-id="88773-183">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="88773-184">L'app dovrà creare altre risorse basate su fotocamera, ad esempio il buffer di profondità, per ogni singola fotocamera.</span><span class="sxs-lookup"><span data-stu-id="88773-184">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="88773-185">Nel modello di app olografico di Windows, viene fornita una classe helper per raggruppare queste risorse in DX:: CameraResources.</span><span class="sxs-lookup"><span data-stu-id="88773-185">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="88773-186">Per iniziare, configurare le visualizzazioni della destinazione di rendering:</span><span class="sxs-lookup"><span data-stu-id="88773-186">Start by setting up the render target views:</span></span>

<span data-ttu-id="88773-187">Da **AppMain:: Render**:</span><span class="sxs-lookup"><span data-stu-id="88773-187">From **AppMain::Render**:</span></span>

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

<span data-ttu-id="88773-188">**Utilizzare la stima per ottenere le matrici di visualizzazione e proiezione per la fotocamera**</span><span class="sxs-lookup"><span data-stu-id="88773-188">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="88773-189">Le matrici di visualizzazione e proiezione per ogni fotocamera olografica cambieranno con ogni frame.</span><span class="sxs-lookup"><span data-stu-id="88773-189">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="88773-190">Aggiornare i dati nel buffer costante per ogni fotocamera olografica.</span><span class="sxs-lookup"><span data-stu-id="88773-190">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="88773-191">Eseguire questa operazione dopo aver aggiornato la stima e prima di effettuare qualsiasi chiamata di richiamo per la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="88773-191">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="88773-192">Da **AppMain:: Render**:</span><span class="sxs-lookup"><span data-stu-id="88773-192">From **AppMain::Render**:</span></span>

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

<span data-ttu-id="88773-193">Qui viene illustrato come vengono acquisite le matrici dalla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="88773-193">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="88773-194">Durante questo processo, viene anche ottenuto il viewport corrente per la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="88773-194">During this process, we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="88773-195">Si noti il modo in cui viene fornito un sistema di Coordinate: si tratta dello stesso sistema di coordinate usato per comprendere lo sguardo ed è uguale a quello usato per posizionare il cubo rotante.</span><span class="sxs-lookup"><span data-stu-id="88773-195">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="88773-196">Da **CameraResources:: UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="88773-196">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

<span data-ttu-id="88773-197">Il viewport deve essere impostato su ogni frame.</span><span class="sxs-lookup"><span data-stu-id="88773-197">The viewport should be set each frame.</span></span> <span data-ttu-id="88773-198">Il vertex shader (almeno) deve in genere accedere ai dati di visualizzazione/proiezione.</span><span class="sxs-lookup"><span data-stu-id="88773-198">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="88773-199">Da **CameraResources:: AttachViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="88773-199">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

<span data-ttu-id="88773-200">**Eseguire il rendering sul buffer nascosto della fotocamera ed eseguire il commit del buffer di profondità**:</span><span class="sxs-lookup"><span data-stu-id="88773-200">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="88773-201">È consigliabile verificare che **TryGetViewTransform** abbia avuto esito positivo prima di provare a usare i dati di visualizzazione/proiezione, perché se il sistema di coordinate non è locatable (ad esempio, il rilevamento è stato interrotto) non è possibile eseguire il rendering dell'app per quel frame.</span><span class="sxs-lookup"><span data-stu-id="88773-201">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system isn't locatable (for example, tracking was interrupted) your app can't render with it for that frame.</span></span> <span data-ttu-id="88773-202">Il modello chiama solo il **rendering** sul cubo rotante se la classe **CameraResources** indica un aggiornamento riuscito.</span><span class="sxs-lookup"><span data-stu-id="88773-202">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="88773-203">La realtà mista di Windows include funzionalità per la [stabilizzazione delle immagini](../platform-capabilities-and-apis/hologram-stability.md) che consentono di posizionare gli ologrammi in cui uno sviluppatore o un utente li inserisce nel mondo.</span><span class="sxs-lookup"><span data-stu-id="88773-203">Windows Mixed Reality includes features for [image stabilization](../platform-capabilities-and-apis/hologram-stability.md) to keep holograms positioned where a developer or user puts them in the world.</span></span> <span data-ttu-id="88773-204">La stabilizzazione delle immagini consente di nascondere la latenza intrinseca in una pipeline di rendering per garantire la migliore esperienza olografica per gli utenti.</span><span class="sxs-lookup"><span data-stu-id="88773-204">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users.</span></span> <span data-ttu-id="88773-205">È possibile specificare un punto di interesse per migliorare ulteriormente la stabilizzazione dell'immagine oppure è possibile fornire un buffer di profondità per calcolare la stabilizzazione delle immagini ottimizzata in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="88773-205">A focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="88773-206">Per ottenere risultati ottimali, l'app deve fornire un buffer di profondità usando l'API <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> .</span><span class="sxs-lookup"><span data-stu-id="88773-206">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="88773-207">La realtà mista di Windows può quindi usare le informazioni di geometria dal buffer di profondità per ottimizzare la stabilizzazione delle immagini in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="88773-207">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="88773-208">Per impostazione predefinita, il modello di app Windows olografico consente di eseguire il commit del buffer di profondità dell'app per ottimizzare la stabilità degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="88773-208">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="88773-209">Da **AppMain:: Render**:</span><span class="sxs-lookup"><span data-stu-id="88773-209">From **AppMain::Render**:</span></span>

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
><span data-ttu-id="88773-210">Windows elaborerà la trama di profondità sulla GPU, quindi è necessario usare il buffer di profondità come risorsa dello shader.</span><span class="sxs-lookup"><span data-stu-id="88773-210">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="88773-211">Il ID3D11Texture2D creato deve avere un formato senza tipo e deve essere associato come visualizzazione delle risorse dello shader.</span><span class="sxs-lookup"><span data-stu-id="88773-211">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="88773-212">Di seguito è riportato un esempio di come creare una trama di profondità di cui è possibile eseguire il commit per la stabilizzazione delle immagini.</span><span class="sxs-lookup"><span data-stu-id="88773-212">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="88773-213">Codice per la **creazione di risorse del buffer di profondità per CommitDirect3D11DepthBuffer**:</span><span class="sxs-lookup"><span data-stu-id="88773-213">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

<span data-ttu-id="88773-214">**Creare contenuto olografico**</span><span class="sxs-lookup"><span data-stu-id="88773-214">**Draw holographic content**</span></span>

<span data-ttu-id="88773-215">Il modello di app olografico di Windows esegue il rendering del contenuto in stereo usando la tecnica consigliata per il disegno di una geometria di istanza in un Texture2DArray di dimensioni 2.</span><span class="sxs-lookup"><span data-stu-id="88773-215">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="88773-216">Esaminiamo la parte relativa alle istanze e il funzionamento della realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="88773-216">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="88773-217">Da **SpinningCubeRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="88773-217">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

<span data-ttu-id="88773-218">Ogni istanza accede a una matrice di visualizzazione/proiezione diversa dal buffer costante.</span><span class="sxs-lookup"><span data-stu-id="88773-218">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="88773-219">Di seguito è illustrata la struttura del buffer costante, che è solo una matrice di due matrici.</span><span class="sxs-lookup"><span data-stu-id="88773-219">Here's the constant buffer structure, which is just an array of two matrices.</span></span>

<span data-ttu-id="88773-220">Da **VertexShaderShared. HLSL**, incluso in **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="88773-220">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="88773-221">Per ogni pixel è necessario impostare l'indice della matrice di destinazione di rendering.</span><span class="sxs-lookup"><span data-stu-id="88773-221">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="88773-222">Nel frammento di codice seguente viene eseguito il mapping di output. viewId alla semantica **SV_RenderTargetArrayIndex** .</span><span class="sxs-lookup"><span data-stu-id="88773-222">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="88773-223">È necessario il supporto per una funzionalità facoltativa Direct3D 11,3, che consente di impostare la semantica dell'indice della matrice di destinazione di rendering da qualsiasi fase dello shader.</span><span class="sxs-lookup"><span data-stu-id="88773-223">This requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="88773-224">Da **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="88773-224">From **VPRTVertexShader.hlsl**:</span></span>

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

<span data-ttu-id="88773-225">Da **VertexShaderShared. HLSL**, incluso in **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="88773-225">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

<span data-ttu-id="88773-226">Se si desidera utilizzare le tecniche di disegno con istanze esistenti con questo metodo di disegno in una matrice di destinazione di rendering stereo, disegnare due volte il numero di istanze di cui si dispone normalmente.</span><span class="sxs-lookup"><span data-stu-id="88773-226">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, draw twice the number of instances you normally have.</span></span> <span data-ttu-id="88773-227">Nello shader dividere **input. IDIstanza** per 2 per ottenere l'ID istanza originale, che può essere indicizzato in (ad esempio) un buffer di dati per oggetto: `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="88773-227">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="88773-228">Nota importante sul rendering del contenuto stereo in HoloLens</span><span class="sxs-lookup"><span data-stu-id="88773-228">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="88773-229">La realtà mista di Windows supporta la possibilità di impostare l'indice della matrice di destinazione di rendering da qualsiasi fase dello shader.</span><span class="sxs-lookup"><span data-stu-id="88773-229">Windows Mixed Reality supports the ability to set the render target array index from any shader stage.</span></span> <span data-ttu-id="88773-230">In genere, si tratta di un'attività che può essere eseguita solo nella fase geometry shader a causa del modo in cui la semantica è definita per Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="88773-230">Normally, this is a task that could only be done in the geometry shader stage because of the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="88773-231">Qui viene illustrato un esempio completo di come configurare una pipeline di rendering solo con le fasi Vertex e pixel shader impostate.</span><span class="sxs-lookup"><span data-stu-id="88773-231">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="88773-232">Il codice dello shader è come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="88773-232">The shader code is as described above.</span></span>

<span data-ttu-id="88773-233">Da **SpinningCubeRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="88773-233">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="88773-234">Nota importante sul rendering nei dispositivi non HoloLens</span><span class="sxs-lookup"><span data-stu-id="88773-234">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="88773-235">Per impostare l'indice della matrice di destinazione di rendering nel vertex shader, è necessario che il driver di grafica supporti una funzionalità facoltativa Direct3D 11,3, supportata da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="88773-235">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="88773-236">L'app può implementare in modo sicuro solo questa tecnica per il rendering e tutti i requisiti verranno soddisfatti per l'esecuzione in Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="88773-236">Your app may can safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="88773-237">È possibile che si voglia usare anche l'emulatore di HoloLens, che può essere uno strumento di sviluppo potente per l'app olografica e per supportare i dispositivi con auricolari a realtà mista di Windows, collegati a PC Windows 10.</span><span class="sxs-lookup"><span data-stu-id="88773-237">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="88773-238">Il supporto per il percorso di rendering non HoloLens, per tutte le realtà miste di Windows, è anche incorporato nel modello di app olografico di Windows.</span><span class="sxs-lookup"><span data-stu-id="88773-238">Support for the non-HoloLens rendering path - for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="88773-239">Nel codice del modello è presente codice per abilitare l'esecuzione dell'app olografica sulla GPU nel PC di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="88773-239">In the template code, you'll find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="88773-240">Ecco il modo in cui la classe **DeviceResources** verifica la presenza di questo supporto della funzionalità facoltativa.</span><span class="sxs-lookup"><span data-stu-id="88773-240">Here's how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="88773-241">Da **DeviceResources:: CreateDeviceResources**:</span><span class="sxs-lookup"><span data-stu-id="88773-241">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="88773-242">Per supportare il rendering senza questa funzionalità facoltativa, l'app deve usare un geometry shader per impostare l'indice della matrice di destinazione di rendering.</span><span class="sxs-lookup"><span data-stu-id="88773-242">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="88773-243">Questo frammento di codice verrà aggiunto *dopo* **VSSetConstantBuffers** e *prima* di **PSSetShader** nell'esempio di codice illustrato nella sezione precedente, in cui viene illustrato come eseguire il rendering dello stereo su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="88773-243">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="88773-244">Da **SpinningCubeRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="88773-244">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

<span data-ttu-id="88773-245">**HLSL nota**: in questo caso, è necessario caricare anche un vertex shader leggermente modificato che passa l'indice della matrice di destinazione di rendering a geometry shader usando una semantica shader sempre consentita, ad esempio TEXCOORD0.</span><span class="sxs-lookup"><span data-stu-id="88773-245">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="88773-246">Il geometry shader non deve eseguire alcuna operazione; il modello geometry shader passa attraverso tutti i dati, fatta eccezione per l'indice della matrice di destinazione di rendering, che viene usato per impostare la semantica del SV_RenderTargetArrayIndex.</span><span class="sxs-lookup"><span data-stu-id="88773-246">The geometry shader doesn't have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="88773-247">Codice modello app per **GeometryShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="88773-247">App template code for **GeometryShader.hlsl**:</span></span>

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint instId         : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint rtvId          : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a><span data-ttu-id="88773-248">Presente</span><span class="sxs-lookup"><span data-stu-id="88773-248">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="88773-249">Abilitare il frame olografico per presentare la catena di scambio</span><span class="sxs-lookup"><span data-stu-id="88773-249">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="88773-250">Con la realtà mista di Windows, il sistema controlla la catena di scambio.</span><span class="sxs-lookup"><span data-stu-id="88773-250">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="88773-251">Il sistema gestisce quindi la presentazione dei frame a ogni fotocamera olografica per garantire un'esperienza utente di alta qualità.</span><span class="sxs-lookup"><span data-stu-id="88773-251">The system then manages presenting frames to each holographic camera to ensure a high-quality user experience.</span></span> <span data-ttu-id="88773-252">Fornisce anche un viewport per aggiornare ogni frame, per ogni fotocamera, per ottimizzare gli aspetti del sistema, ad esempio la stabilizzazione dell'immagine o l'acquisizione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="88773-252">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="88773-253">Quindi, un'app olografica che usa DirectX non chiama **presente** in una catena di scambio dxgi.</span><span class="sxs-lookup"><span data-stu-id="88773-253">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="88773-254">Al contrario, si usa la classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> per presentare tutti i le catene per un frame al termine del disegno.</span><span class="sxs-lookup"><span data-stu-id="88773-254">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="88773-255">Da **DeviceResources::P inviato nuovamente**:</span><span class="sxs-lookup"><span data-stu-id="88773-255">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="88773-256">Per impostazione predefinita, questa API attende il completamento del frame prima della restituzione.</span><span class="sxs-lookup"><span data-stu-id="88773-256">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="88773-257">Le app olografiche devono attendere il completamento del frame precedente prima di iniziare a lavorare su un nuovo frame, perché questo riduce la latenza e consente di ottenere risultati migliori dalle stime dei frame olografici.</span><span class="sxs-lookup"><span data-stu-id="88773-257">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="88773-258">Questa regola non è rigida e se sono presenti frame che impostano più di un aggiornamento dello schermo per il rendering, è possibile disabilitare questa attesa passando il parametro HolographicFramePresentWaitBehavior a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span><span class="sxs-lookup"><span data-stu-id="88773-258">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="88773-259">In questo caso, è probabile che si usi un thread di rendering asincrono per mantenere un carico continuo sulla GPU.</span><span class="sxs-lookup"><span data-stu-id="88773-259">In this case, you would likely use an asynchronous rendering thread to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="88773-260">La frequenza di aggiornamento del dispositivo HoloLens è 60 Hz, dove un frame ha una durata di circa 16 ms.</span><span class="sxs-lookup"><span data-stu-id="88773-260">The refresh rate of the HoloLens device is 60 hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="88773-261">I dispositivi per auricolari immersivi possono variare da 60 Hz a 90 Hz; Quando si aggiorna la visualizzazione a 90 Hz, ogni frame avrà una durata pari a circa 11 ms.</span><span class="sxs-lookup"><span data-stu-id="88773-261">Immersive headset devices can range from 60 hz to 90 hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="88773-262">Gestire scenari DeviceLost in collaborazione con HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="88773-262">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="88773-263">Le app DirectX 11 in genere vogliono controllare il valore HRESULT restituito dalla funzione **presente** della catena di scambio DXGI per determinare se si è verificato un errore **DeviceLost** .</span><span class="sxs-lookup"><span data-stu-id="88773-263">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="88773-264">La classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> gestisce questa operazione automaticamente.</span><span class="sxs-lookup"><span data-stu-id="88773-264">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="88773-265">Esaminare i <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> restituiti per verificare se è necessario rilasciare e ricreare il dispositivo Direct3D e le risorse basate su dispositivo.</span><span class="sxs-lookup"><span data-stu-id="88773-265">Inspect the returned <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

<span data-ttu-id="88773-266">Se il dispositivo Direct3D è stato perso ed è stato ricreato, è necessario indicare all' <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> di iniziare a usare il nuovo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="88773-266">If the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="88773-267">La catena di scambio verrà ricreata per questo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="88773-267">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="88773-268">Da **DeviceResources:: InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="88773-268">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="88773-269">Una volta visualizzato il frame, è possibile tornare al ciclo principale del programma e consentirne la continuazione al frame successivo.</span><span class="sxs-lookup"><span data-stu-id="88773-269">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="88773-270">Computer grafici ibridi e applicazioni di realtà mista</span><span class="sxs-lookup"><span data-stu-id="88773-270">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="88773-271">I PC Windows 10 Creators Update possono essere configurati con GPU **sia** discrete che integrate.</span><span class="sxs-lookup"><span data-stu-id="88773-271">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="88773-272">Con questi tipi di computer, Windows sceglierà la scheda a cui è connessa l'auricolare.</span><span class="sxs-lookup"><span data-stu-id="88773-272">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="88773-273">Le applicazioni devono garantire che il dispositivo DirectX creato usi la stessa scheda.</span><span class="sxs-lookup"><span data-stu-id="88773-273">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="88773-274">La maggior parte del codice di esempio Direct3D generale illustra la creazione di un dispositivo DirectX usando la scheda hardware predefinita, che in un sistema ibrido potrebbe non essere uguale a quella usata per l'auricolare.</span><span class="sxs-lookup"><span data-stu-id="88773-274">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="88773-275">Per risolvere i problemi, usare <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterID</a> da <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId () o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId ().</span><span class="sxs-lookup"><span data-stu-id="88773-275">To work around any issues, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterID</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="88773-276">Questo adapterId può quindi essere usato per selezionare il DXGIAdapter corretto usando IDXGIFactory4. EnumAdapterByLuid.</span><span class="sxs-lookup"><span data-stu-id="88773-276">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="88773-277">Da **DeviceResources:: InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="88773-277">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

<span data-ttu-id="88773-278">Codice per l' **aggiornamento di DeviceResources:: CreateDeviceResources per l'uso di IDXGIAdapter**</span><span class="sxs-lookup"><span data-stu-id="88773-278">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

<span data-ttu-id="88773-279">**Grafica ibrida e Media Foundation**</span><span class="sxs-lookup"><span data-stu-id="88773-279">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="88773-280">L'uso di Media Foundation nei sistemi ibridi può causare problemi in caso di danneggiamento del video o della trama video, in quanto Media Foundation viene utilizzato per impostazione predefinita un comportamento del sistema.</span><span class="sxs-lookup"><span data-stu-id="88773-280">Using Media Foundation on hybrid systems may cause issues where video won't render or video texture are corrupt because Media Foundation is defaulting to a system behavior.</span></span> <span data-ttu-id="88773-281">In alcuni scenari, la creazione di un ID3D11Device separato è necessaria per supportare il multithreading e vengono impostati i flag di creazione corretti.</span><span class="sxs-lookup"><span data-stu-id="88773-281">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="88773-282">Durante l'inizializzazione di ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag deve essere definito come parte del D3D11_CREATE_DEVICE_FLAG.</span><span class="sxs-lookup"><span data-stu-id="88773-282">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="88773-283">Una volta creato il dispositivo e il contesto, chiamare <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> per abilitare il multithreading.</span><span class="sxs-lookup"><span data-stu-id="88773-283">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="88773-284">Per associare il dispositivo a <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, usare la funzione <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager:: ResetDevice</a> .</span><span class="sxs-lookup"><span data-stu-id="88773-284">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="88773-285">Codice per **associare un ID3D11Device a IMFDXGIDeviceManager**:</span><span class="sxs-lookup"><span data-stu-id="88773-285">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a><span data-ttu-id="88773-286">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="88773-286">See also</span></span>
* [<span data-ttu-id="88773-287">Sistemi di coordinate in DirectX</span><span class="sxs-lookup"><span data-stu-id="88773-287">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="88773-288">Uso dell'emulatore HoloLens</span><span class="sxs-lookup"><span data-stu-id="88773-288">Using the HoloLens emulator</span></span>](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
