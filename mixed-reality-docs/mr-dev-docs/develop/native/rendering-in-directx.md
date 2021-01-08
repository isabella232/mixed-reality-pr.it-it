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
# <a name="rendering-in-directx"></a>Rendering in DirectX

> [!NOTE]
> Questo articolo si riferisce alle API native di WinRT legacy.  Per i nuovi progetti di app native, è consigliabile usare l' **[API OpenXR](openxr-getting-started.md)**.

La realtà mista di Windows si basa su DirectX per produrre un'esperienza grafica 3D avanzata per gli utenti. L'astrazione del rendering si trova appena sopra DirectX, che consente alle app di ragionare sulla posizione e sull'orientamento degli osservatori di scena olografici previsti dal sistema. Lo sviluppatore può quindi trovare i propri ologrammi in base a ogni fotocamera, consentendo all'app di eseguire il rendering di questi ologrammi in vari sistemi di coordinate spaziali quando l'utente si sposta.

Nota: in questa procedura dettagliata viene descritto il rendering olografico in Direct3D 11. Un modello di app per la realtà mista Direct3D 12 Windows viene fornito anche con l'estensione dei modelli di app per realtà mista.

## <a name="update-for-the-current-frame"></a>Aggiornamento per il frame corrente

Per aggiornare lo stato dell'applicazione per gli ologrammi, una volta per ogni fotogramma l'app:
* Ottenere un <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> dal sistema di gestione dello schermo.
* Aggiornare la scena con la stima corrente del punto in cui la visualizzazione della fotocamera sarà quando il rendering viene completato. Si noti che la scena olografica può contenere più di una fotocamera.

Per eseguire il rendering delle visualizzazioni della fotocamera olografica, una volta per ogni fotogramma l'app:
* Per ogni fotocamera, eseguire il rendering della scena per il frame corrente, usando la visualizzazione della fotocamera e le matrici di proiezione dal sistema.

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>Creare un nuovo frame olografico e ottenere la relativa stima

Il <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> contiene informazioni necessarie all'app per aggiornare ed eseguire il rendering del frame corrente. L'app avvia ogni nuovo frame chiamando il metodo **CreateNextFrame** . Quando viene chiamato questo metodo, le stime vengono effettuate usando i dati dei sensori più recenti disponibili e incapsulati nell'oggetto **CurrentPrediction** .

Per ogni frame sottoposto a rendering è necessario usare un nuovo oggetto frame perché è valido solo per un istante di tempo. La proprietà **CurrentPrediction** contiene informazioni come la posizione della fotocamera. Le informazioni vengono estrapolate nel momento esatto in cui il frame dovrebbe essere visibile all'utente.

Il codice seguente è tratto da **AppMain:: Update**:

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>Elaborare gli aggiornamenti della fotocamera

I buffer indietro possono variare da frame a frame. L'app deve convalidare il buffer nascosto per ogni fotocamera e rilasciare e ricreare le visualizzazioni delle risorse e i buffer di profondità in base alle esigenze. Si noti che il set di pose nella stima è l'elenco autorevole di fotocamere utilizzate nel frame corrente. In genere, questo elenco viene usato per eseguire l'iterazione sul set di fotocamere.

Da **AppMain:: Update**:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

Da **DeviceResources:: EnsureCameraResources**:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>Ottenere il sistema di coordinate da utilizzare come base per il rendering

La realtà mista di Windows consente all'app di creare vari [sistemi di coordinate](coordinate-systems-in-directx.md), ad esempio frame di riferimento allegati e stazionari per i percorsi di rilevamento nel mondo fisico. L'app può quindi usare questi sistemi di coordinate per motivare la posizione in cui eseguire il rendering degli ologrammi per ogni fotogramma. Quando si richiedono le coordinate da un'API, si passerà sempre il <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> all'interno del quale si desidera esprimere le coordinate.

Da **AppMain:: Update**:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

Questi sistemi di coordinate possono quindi essere utilizzati per generare matrici di visualizzazione stereo durante il rendering del contenuto nella scena.

Da **CameraResources:: UpdateViewProjectionBuffer**:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>Input di sguardi e movimenti del processo

Gli input [sguardo](gaze-in-directx.md) e [mano](hands-and-motion-controllers-in-directx.md) non sono basati sul tempo e non è necessario aggiornarli nella funzione **StepTimer** . Tuttavia, questo input è un elemento che l'app deve esaminare per ogni fotogramma.

### <a name="process-time-based-updates"></a>Elaborare gli aggiornamenti basati sul tempo

Qualsiasi app per il rendering in tempo reale richiede un modo per elaborare gli aggiornamenti basati sul tempo. il modello di app olografico di Windows usa un'implementazione di **StepTimer** , simile a StepTimer fornito nel modello di app DirectX 11 UWP. Questa classe helper di esempio StepTimer può fornire aggiornamenti fissi in fase di esecuzione, aggiornamenti variabili del tempo e la modalità predefinita prevede intervalli temporali variabili.

Per il rendering olografico, è stato scelto di non inserire troppo nella funzione timer perché è possibile configurarla in modo che sia un passaggio di tempo fisso. Potrebbe essere chiamato più di una volta per frame, o non per alcuni frame, e gli aggiornamenti dei dati olografici dovrebbero essere eseguiti una sola volta per ogni fotogramma.


Da **AppMain:: Update**:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>Posizionare e ruotare gli ologrammi nel sistema di coordinate

Se si opera in un sistema di coordinate singolo, come nel caso del modello con il **SpatialStationaryReferenceFrame**, questo processo non è diverso da quello che viene usato altrimenti in grafica 3D. Qui viene ruotato il cubo e la matrice del modello viene impostata in base alla posizione nel sistema di coordinate fisse.

Da **SpinningCubeRenderer:: Update**:

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

**Nota sugli scenari avanzati:** Il cubo rotante è un semplice esempio di come posizionare un ologramma all'interno di un singolo frame di riferimento. È anche possibile [usare più SpatialCoordinateSystems](coordinate-systems-in-directx.md) nello stesso frame sottoposto a rendering, allo stesso tempo.

### <a name="update-constant-buffer-data"></a>Aggiornare i dati del buffer costante

Le trasformazioni del modello per il contenuto vengono aggiornate come di consueto. A questo punto sono state calcolate le trasformazioni valide per il sistema di coordinate in cui verrà eseguito il rendering.

Da **SpinningCubeRenderer:: Update**:

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

Informazioni sulle trasformazioni di visualizzazione e proiezione Per ottenere risultati ottimali, è necessario attendere fino a quando non si è pronti per le chiamate di estrazione.

## <a name="render-the-current-frame"></a>Esegue il rendering del frame corrente

Il rendering in realtà mista di Windows non è molto diverso dal rendering in una visualizzazione mono 2D, ma vi sono alcune differenze:
* Le stime del frame olografico sono importanti. Più si avvicina la stima a quando viene presentato il frame, migliore sarà l'aspetto degli ologrammi.
* La realtà mista di Windows controlla le visualizzazioni della fotocamera. Eseguirne il rendering in ognuno di essi poiché il frame olografico li mostrerà in un secondo momento.
* Si consiglia di eseguire il rendering stereo utilizzando il disegno istanza in una matrice di destinazione di rendering. Il modello di app olografico usa l'approccio consigliato del disegno di istanza in una matrice di destinazione di rendering, che usa una visualizzazione della destinazione di rendering in un **Texture2DArray**.
* Se si vuole eseguire il rendering senza usare le istanze stereo, è necessario creare due RenderTargetViews non di matrice, uno per ogni occhio. Ogni RenderTargetViews fa riferimento a una delle due sezioni in **Texture2DArray** fornite all'app dal sistema. Questa operazione non è consigliata, in quanto è in genere più lenta rispetto all'uso della creazione di istanze.

### <a name="get-an-updated-holographicframe-prediction"></a>Ottenere una stima HolographicFrame aggiornata

L'aggiornamento della stima del frame migliora l'efficacia della stabilizzazione dell'immagine. Si ottiene un posizionamento più accurato degli ologrammi a causa del tempo più breve tra la stima e quando il frame è visibile all'utente. Aggiornare idealmente la stima dei frame immediatamente prima del rendering.

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>Rendering in ogni fotocamera

Il ciclo del set di fotocamere si pone nella stima e viene eseguito il rendering in ogni fotocamera in questo set.

**Configurare la sessione di rendering**

La realtà mista di Windows usa il rendering stereoscopico per migliorare l'illusione della profondità e per eseguire il rendering in modo stereoscopico, in modo che sia la visualizzazione a sinistra che quella destra siano attive Con il rendering stereoscopico, esiste un offset tra le due visualizzazioni, che il cervello può riconciliare come profondità effettiva. Questa sezione illustra il rendering stereoscopico usando le istanze, usando il codice del modello di app olografico di Windows.

Ogni fotocamera ha una propria destinazione di rendering (buffer nascosto) e matrici di visualizzazione e proiezione nello spazio olografico. L'app dovrà creare altre risorse basate su fotocamera, ad esempio il buffer di profondità, per ogni singola fotocamera. Nel modello di app olografico di Windows, viene fornita una classe helper per raggruppare queste risorse in DX:: CameraResources. Per iniziare, configurare le visualizzazioni della destinazione di rendering:

Da **AppMain:: Render**:

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

**Utilizzare la stima per ottenere le matrici di visualizzazione e proiezione per la fotocamera**

Le matrici di visualizzazione e proiezione per ogni fotocamera olografica cambieranno con ogni frame. Aggiornare i dati nel buffer costante per ogni fotocamera olografica. Eseguire questa operazione dopo aver aggiornato la stima e prima di effettuare qualsiasi chiamata di richiamo per la fotocamera.

Da **AppMain:: Render**:

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

Qui viene illustrato come vengono acquisite le matrici dalla fotocamera. Durante questo processo, viene anche ottenuto il viewport corrente per la fotocamera. Si noti il modo in cui viene fornito un sistema di Coordinate: si tratta dello stesso sistema di coordinate usato per comprendere lo sguardo ed è uguale a quello usato per posizionare il cubo rotante.


Da **CameraResources:: UpdateViewProjectionBuffer**:

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

Il viewport deve essere impostato su ogni frame. Il vertex shader (almeno) deve in genere accedere ai dati di visualizzazione/proiezione.


Da **CameraResources:: AttachViewProjectionBuffer**:

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

**Eseguire il rendering sul buffer nascosto della fotocamera ed eseguire il commit del buffer di profondità**:

È consigliabile verificare che **TryGetViewTransform** abbia avuto esito positivo prima di provare a usare i dati di visualizzazione/proiezione, perché se il sistema di coordinate non è locatable (ad esempio, il rilevamento è stato interrotto) non è possibile eseguire il rendering dell'app per quel frame. Il modello chiama solo il **rendering** sul cubo rotante se la classe **CameraResources** indica un aggiornamento riuscito.

La realtà mista di Windows include funzionalità per la [stabilizzazione delle immagini](../platform-capabilities-and-apis/hologram-stability.md) che consentono di posizionare gli ologrammi in cui uno sviluppatore o un utente li inserisce nel mondo. La stabilizzazione delle immagini consente di nascondere la latenza intrinseca in una pipeline di rendering per garantire la migliore esperienza olografica per gli utenti. È possibile specificare un punto di interesse per migliorare ulteriormente la stabilizzazione dell'immagine oppure è possibile fornire un buffer di profondità per calcolare la stabilizzazione delle immagini ottimizzata in tempo reale.

Per ottenere risultati ottimali, l'app deve fornire un buffer di profondità usando l'API <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> . La realtà mista di Windows può quindi usare le informazioni di geometria dal buffer di profondità per ottimizzare la stabilizzazione delle immagini in tempo reale. Per impostazione predefinita, il modello di app Windows olografico consente di eseguire il commit del buffer di profondità dell'app per ottimizzare la stabilità degli ologrammi.

Da **AppMain:: Render**:

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
>Windows elaborerà la trama di profondità sulla GPU, quindi è necessario usare il buffer di profondità come risorsa dello shader. Il ID3D11Texture2D creato deve avere un formato senza tipo e deve essere associato come visualizzazione delle risorse dello shader. Di seguito è riportato un esempio di come creare una trama di profondità di cui è possibile eseguire il commit per la stabilizzazione delle immagini.

Codice per la **creazione di risorse del buffer di profondità per CommitDirect3D11DepthBuffer**:

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

**Creare contenuto olografico**

Il modello di app olografico di Windows esegue il rendering del contenuto in stereo usando la tecnica consigliata per il disegno di una geometria di istanza in un Texture2DArray di dimensioni 2. Esaminiamo la parte relativa alle istanze e il funzionamento della realtà mista di Windows.

Da **SpinningCubeRenderer:: Render**:

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

Ogni istanza accede a una matrice di visualizzazione/proiezione diversa dal buffer costante. Di seguito è illustrata la struttura del buffer costante, che è solo una matrice di due matrici.

Da **VertexShaderShared. HLSL**, incluso in **VPRTVertexShader. HLSL**:

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

Per ogni pixel è necessario impostare l'indice della matrice di destinazione di rendering. Nel frammento di codice seguente viene eseguito il mapping di output. viewId alla semantica **SV_RenderTargetArrayIndex** . È necessario il supporto per una funzionalità facoltativa Direct3D 11,3, che consente di impostare la semantica dell'indice della matrice di destinazione di rendering da qualsiasi fase dello shader.

Da **VPRTVertexShader. HLSL**:

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

Da **VertexShaderShared. HLSL**, incluso in **VPRTVertexShader. HLSL**:

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

Se si desidera utilizzare le tecniche di disegno con istanze esistenti con questo metodo di disegno in una matrice di destinazione di rendering stereo, disegnare due volte il numero di istanze di cui si dispone normalmente. Nello shader dividere **input. IDIstanza** per 2 per ottenere l'ID istanza originale, che può essere indicizzato in (ad esempio) un buffer di dati per oggetto: `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>Nota importante sul rendering del contenuto stereo in HoloLens

La realtà mista di Windows supporta la possibilità di impostare l'indice della matrice di destinazione di rendering da qualsiasi fase dello shader. In genere, si tratta di un'attività che può essere eseguita solo nella fase geometry shader a causa del modo in cui la semantica è definita per Direct3D 11. Qui viene illustrato un esempio completo di come configurare una pipeline di rendering solo con le fasi Vertex e pixel shader impostate. Il codice dello shader è come descritto in precedenza.

Da **SpinningCubeRenderer:: Render**:

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>Nota importante sul rendering nei dispositivi non HoloLens

Per impostare l'indice della matrice di destinazione di rendering nel vertex shader, è necessario che il driver di grafica supporti una funzionalità facoltativa Direct3D 11,3, supportata da HoloLens. L'app può implementare in modo sicuro solo questa tecnica per il rendering e tutti i requisiti verranno soddisfatti per l'esecuzione in Microsoft HoloLens.

È possibile che si voglia usare anche l'emulatore di HoloLens, che può essere uno strumento di sviluppo potente per l'app olografica e per supportare i dispositivi con auricolari a realtà mista di Windows, collegati a PC Windows 10. Il supporto per il percorso di rendering non HoloLens, per tutte le realtà miste di Windows, è anche incorporato nel modello di app olografico di Windows. Nel codice del modello è presente codice per abilitare l'esecuzione dell'app olografica sulla GPU nel PC di sviluppo. Ecco il modo in cui la classe **DeviceResources** verifica la presenza di questo supporto della funzionalità facoltativa.

Da **DeviceResources:: CreateDeviceResources**:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

Per supportare il rendering senza questa funzionalità facoltativa, l'app deve usare un geometry shader per impostare l'indice della matrice di destinazione di rendering. Questo frammento di codice verrà aggiunto *dopo* **VSSetConstantBuffers** e *prima* di **PSSetShader** nell'esempio di codice illustrato nella sezione precedente, in cui viene illustrato come eseguire il rendering dello stereo su HoloLens.

Da **SpinningCubeRenderer:: Render**:

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

**HLSL nota**: in questo caso, è necessario caricare anche un vertex shader leggermente modificato che passa l'indice della matrice di destinazione di rendering a geometry shader usando una semantica shader sempre consentita, ad esempio TEXCOORD0. Il geometry shader non deve eseguire alcuna operazione; il modello geometry shader passa attraverso tutti i dati, fatta eccezione per l'indice della matrice di destinazione di rendering, che viene usato per impostare la semantica del SV_RenderTargetArrayIndex.

Codice modello app per **GeometryShader. HLSL**:

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

## <a name="present"></a>Presente

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>Abilitare il frame olografico per presentare la catena di scambio

Con la realtà mista di Windows, il sistema controlla la catena di scambio. Il sistema gestisce quindi la presentazione dei frame a ogni fotocamera olografica per garantire un'esperienza utente di alta qualità. Fornisce anche un viewport per aggiornare ogni frame, per ogni fotocamera, per ottimizzare gli aspetti del sistema, ad esempio la stabilizzazione dell'immagine o l'acquisizione di realtà mista. Quindi, un'app olografica che usa DirectX non chiama **presente** in una catena di scambio dxgi. Al contrario, si usa la classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> per presentare tutti i le catene per un frame al termine del disegno.

Da **DeviceResources::P inviato nuovamente**:

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

Per impostazione predefinita, questa API attende il completamento del frame prima della restituzione. Le app olografiche devono attendere il completamento del frame precedente prima di iniziare a lavorare su un nuovo frame, perché questo riduce la latenza e consente di ottenere risultati migliori dalle stime dei frame olografici. Questa regola non è rigida e se sono presenti frame che impostano più di un aggiornamento dello schermo per il rendering, è possibile disabilitare questa attesa passando il parametro HolographicFramePresentWaitBehavior a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>. In questo caso, è probabile che si usi un thread di rendering asincrono per mantenere un carico continuo sulla GPU. La frequenza di aggiornamento del dispositivo HoloLens è 60 Hz, dove un frame ha una durata di circa 16 ms. I dispositivi per auricolari immersivi possono variare da 60 Hz a 90 Hz; Quando si aggiorna la visualizzazione a 90 Hz, ogni frame avrà una durata pari a circa 11 ms.

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>Gestire scenari DeviceLost in collaborazione con HolographicFrame

Le app DirectX 11 in genere vogliono controllare il valore HRESULT restituito dalla funzione **presente** della catena di scambio DXGI per determinare se si è verificato un errore **DeviceLost** . La classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> gestisce questa operazione automaticamente. Esaminare i <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> restituiti per verificare se è necessario rilasciare e ricreare il dispositivo Direct3D e le risorse basate su dispositivo.

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

Se il dispositivo Direct3D è stato perso ed è stato ricreato, è necessario indicare all' <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> di iniziare a usare il nuovo dispositivo. La catena di scambio verrà ricreata per questo dispositivo.

Da **DeviceResources:: InitializeUsingHolographicSpace**:

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

Una volta visualizzato il frame, è possibile tornare al ciclo principale del programma e consentirne la continuazione al frame successivo.

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>Computer grafici ibridi e applicazioni di realtà mista

I PC Windows 10 Creators Update possono essere configurati con GPU **sia** discrete che integrate. Con questi tipi di computer, Windows sceglierà la scheda a cui è connessa l'auricolare. Le applicazioni devono garantire che il dispositivo DirectX creato usi la stessa scheda.

La maggior parte del codice di esempio Direct3D generale illustra la creazione di un dispositivo DirectX usando la scheda hardware predefinita, che in un sistema ibrido potrebbe non essere uguale a quella usata per l'auricolare.

Per risolvere i problemi, usare <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterID</a> da <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId () o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId (). Questo adapterId può quindi essere usato per selezionare il DXGIAdapter corretto usando IDXGIFactory4. EnumAdapterByLuid.

Da **DeviceResources:: InitializeUsingHolographicSpace**:

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

Codice per l' **aggiornamento di DeviceResources:: CreateDeviceResources per l'uso di IDXGIAdapter**

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

**Grafica ibrida e Media Foundation**

L'uso di Media Foundation nei sistemi ibridi può causare problemi in caso di danneggiamento del video o della trama video, in quanto Media Foundation viene utilizzato per impostazione predefinita un comportamento del sistema. In alcuni scenari, la creazione di un ID3D11Device separato è necessaria per supportare il multithreading e vengono impostati i flag di creazione corretti.

Durante l'inizializzazione di ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag deve essere definito come parte del D3D11_CREATE_DEVICE_FLAG. Una volta creato il dispositivo e il contesto, chiamare <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> per abilitare il multithreading. Per associare il dispositivo a <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, usare la funzione <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager:: ResetDevice</a> .

Codice per **associare un ID3D11Device a IMFDXGIDeviceManager**:

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

## <a name="see-also"></a>Vedere anche
* [Sistemi di coordinate in DirectX](coordinate-systems-in-directx.md)
* [Uso dell'emulatore HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
