---
title: Rendering in DirectX
description: Informazioni su come aggiornare ed eseguire il rendering del contenuto nelle applicazioni DirectX per Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, ologrammi, rendering, grafica 3D, HolographicFrame, ciclo di rendering, ciclo di aggiornamento, procedura dettagliata, codice di esempio, Direct3D
ms.openlocfilehash: 2c3dd32f5782d6096c6560ec6db55ef1cc7bb533dddb0a4b5fe87cd91bb2f81b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209449"
---
# <a name="rendering-in-directx"></a>Rendering in DirectX

> [!NOTE]
> Questo articolo è correlato alle API native WinRT legacy.  Per i nuovi progetti di app native, è consigliabile usare **[l'API OpenXR](openxr-getting-started.md)**.

Windows Mixed Reality è basato su DirectX per produrre esperienze grafiche 3D ricche per gli utenti. L'astrazione del rendering si trova appena sopra DirectX, che consente alle app di giustificare la posizione e l'orientamento degli osservatori di scena olografici stimati dal sistema. Lo sviluppatore può quindi individuare gli ologrammi in base a ogni fotocamera, consentendo all'app di eseguire il rendering di questi ologrammi in vari sistemi di coordinate spaziali mentre l'utente si sposta.

Nota: questa procedura dettagliata descrive il rendering olografico in Direct3D 11. Un modello di app Windows Mixed Reality Direct3D 12 viene fornito anche con l'estensione modelli di app di realtà mista.

## <a name="update-for-the-current-frame"></a>Aggiornamento per il frame corrente

Per aggiornare lo stato dell'applicazione per gli ologrammi, una volta per frame l'app:
* Ottenere un <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">holographicFrame</a> dal sistema di gestione dello schermo.
* Aggiornare la scena con la stima corrente di dove si trova la visualizzazione della fotocamera al termine del rendering. Si noti che può essere presente più di una fotocamera per la scena olografica.

Per eseguire il rendering nelle visualizzazioni della fotocamera olografica, una volta per fotogramma l'app:
* Per ogni fotocamera, eseguire il rendering della scena per il fotogramma corrente usando la visualizzazione della fotocamera e le matrici di proiezione del sistema.

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>Creare un nuovo frame olografico e ottenere la stima

<a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> contiene informazioni che l'app deve aggiornare ed eseguire il rendering del frame corrente. L'app avvia ogni nuovo frame chiamando il **metodo CreateNextFrame.** Quando viene chiamato questo metodo, le stime vengono effettuate usando i dati più recenti del sensore disponibili e incapsulate **nell'oggetto CurrentPrediction.**

È necessario usare un nuovo oggetto frame per ogni frame sottoposto a rendering perché è valido solo per un istante nel tempo. La **proprietà CurrentPrediction** contiene informazioni quali la posizione della fotocamera. Le informazioni vengono estrapolate nel momento esatto in cui si prevede che il frame sia visibile all'utente.

Il codice seguente viene estratto da **AppMain::Update**:

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

I buffer back possono cambiare da frame a frame. L'app deve convalidare il buffer nascosto per ogni fotocamera e rilasciare e ricreare le visualizzazioni delle risorse e i buffer di profondità in base alle esigenze. Si noti che il set di pose nella stima è l'elenco autorevole di fotocamere usate nel frame corrente. In genere, si usa questo elenco per scorrere il set di fotocamere.

Da **AppMain::Update**:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

Da **DeviceResources::EnsureCameraResources**:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>Ottenere il sistema di coordinate da usare come base per il rendering

Windows Mixed Reality consente all'app di creare vari sistemi di [coordinate,](coordinate-systems-in-directx.md)ad esempio fotogrammi di riferimento collegati e stazionari per tenere traccia delle posizioni nel mondo fisico. L'app può quindi usare questi sistemi di coordinate per trovare la posizione in cui eseguire il rendering degli ologrammi di ogni fotogramma. Quando si richiedono coordinate da un'API, si passerà sempre <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">l'oggetto SpatialCoordinateSystem</a> all'interno del quale si vuole esprimere tali coordinate.

Da **AppMain::Update**:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

Questi sistemi di coordinate possono quindi essere usati per generare matrici di visualizzazione stereo durante il rendering del contenuto nella scena.

Da **CameraResources::UpdateViewProjectionBuffer**:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>Elaborare lo sguardo fisso e l'input dei movimenti

[Lo](gaze-in-directx.md) sguardo [fisso](hands-and-motion-controllers-in-directx.md) e l'input manuale non sono basati sul tempo e non devono essere aggiornati nella **funzione StepTimer.** Tuttavia, questo input è qualcosa che l'app deve esaminare ogni frame.

### <a name="process-time-based-updates"></a>Elaborare gli aggiornamenti basati sul tempo

Qualsiasi app per il rendering in tempo reale dovrà elaborare gli aggiornamenti basati sul tempo: il modello di app holographic di Windows usa un'implementazione **StepTimer,** simile a Quella fornita nel modello di app UWP DirectX 11. Questa classe helper di esempio StepTimer può fornire aggiornamenti temporici fissi, aggiornamenti dei passaggi temporici variabili e la modalità predefinita è passaggi temporici variabili.

Per il rendering olografico, è stato scelto di non inserire troppo nella funzione timer perché è possibile configurarla come passaggio fisso. Potrebbe essere chiamato più di una volta per frame, o per alcuni fotogrammi, e gli aggiornamenti dei dati olografici dovrebbero essere emessi una sola volta per ogni frame.


Da **AppMain::Update**:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>Posizionare e ruotare gli ologrammi nel sistema di coordinate

Se si opera in un singolo sistema di coordinate, come nel modello con **SpatialStationaryReferenceFrame,** questo processo non è diverso da quello usato in caso contrario nella grafica 3D. In questo caso, si ruota il cubo e si imposta la matrice del modello in base alla posizione nel sistema di coordinate stazionarie.

Da **SpinningCubeRenderer::Update**:

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

**Nota sugli scenari avanzati:** Il cubo rotante è un semplice esempio di posizionamento di un ologramma all'interno di un singolo frame di riferimento. È anche possibile usare [più SpatialCoordinateSystems](coordinate-systems-in-directx.md) nello stesso frame sottoposto a rendering contemporaneamente.

### <a name="update-constant-buffer-data"></a>Aggiornare i dati del buffer costante

Le trasformazioni del modello per il contenuto vengono aggiornate come di consueto. A questo punto, saranno state calcolate trasformazioni valide per il sistema di coordinate in cui verrà visualizzato il rendering.

Da **SpinningCubeRenderer::Update**:

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

Informazioni sulle trasformazioni di visualizzazione e proiezione Per ottenere risultati ottimali, è necessario attendere fino a quando non si è quasi pronti per le chiamate di disegno prima di ottenere queste.

## <a name="render-the-current-frame"></a>Eseguire il rendering del frame corrente

Il rendering Windows Mixed Reality non è molto diverso dal rendering su uno schermo mono 2D, ma esistono alcune differenze:
* Le stime dei fotogrammi olografici sono importanti. Più la stima è vicina alla presentazione del frame, migliore sarà l'aspetto degli ologrammi.
* Windows Mixed Reality le visualizzazioni della fotocamera. Eseguire il rendering a ognuno perché il frame olografico li presenterà in un secondo momento.
* È consigliabile eseguire il rendering stereo usando il disegno con istanze in una matrice di destinazione di rendering. Il modello di app olografica usa l'approccio consigliato del disegno con istanze a una matrice di destinazione di rendering, che usa una visualizzazione di destinazione di rendering in **un oggetto Texture2DArray.**
* Se si vuole eseguire il rendering senza usare istanze stereo, è necessario creare due oggetti RenderTargetView non di matrice, uno per ogni occhio. Ogni elemento RenderTargetViews fa riferimento a una delle due sezioni di **Texture2DArray** fornite all'app dal sistema. Questa operazione non è consigliata, perché in genere è più lenta rispetto all'uso delle istanze.

### <a name="get-an-updated-holographicframe-prediction"></a>Ottenere una stima aggiornata di HolographicFrame

L'aggiornamento della stima dei fotogrammi migliora l'efficacia della stabilizzazione delle immagini. Si ottiene un posizionamento più accurato degli ologrammi a causa del tempo più breve tra la stima e il momento in cui il frame è visibile all'utente. Aggiornare idealmente la stima dei fotogrammi subito prima del rendering.

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>Eseguire il rendering in ogni fotocamera

Eseguire il ciclo sul set di posizioni della fotocamera nella stima ed eseguire il rendering su ogni fotocamera in questo set.

**Configurare il passaggio di rendering**

Windows Mixed Reality il rendering stereoscopico per migliorare l'illusione della profondità e per eseguire il rendering stereoscopico, in modo che sia lo schermo sinistro che quello destro siano attivi. Con il rendering stereoscopico, c'è un offset tra i due schermi, che il cervello può riconciliare come profondità effettiva. Questa sezione illustra il rendering stereoscopico usando l'instancing, usando il codice Windows modello di app Holographic.

Ogni fotocamera ha una propria destinazione di rendering (buffer nascosto) e matrici di visualizzazione e proiezione nello spazio olografico. L'app dovrà creare qualsiasi altra risorsa basata su fotocamera, ad esempio il buffer di profondità, in base alla fotocamera. Nel modello Windows'app Holographic viene specificata una classe helper per aggregare queste risorse in DX::CameraResources. Per iniziare, configurare le visualizzazioni di destinazione di rendering:

Da **AppMain::Render**:

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

**Usare la stima per ottenere le matrici di visualizzazione e proiezione per la fotocamera**

Le matrici di visualizzazione e proiezione per ogni fotocamera olografica cambieranno con ogni fotogramma. Aggiornare i dati nel buffer costante per ogni fotocamera olografica. Eseguire questa operazione dopo aver aggiornato la stima e prima di effettuare chiamate di disegno per la fotocamera.

Da **AppMain::Render**:

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

Qui viene illustrato come vengono acquisite le matrici dalla posizione della fotocamera. Durante questo processo si ottiene anche il viewport corrente per la fotocamera. Si noti come viene fornito un sistema di coordinate: si tratta dello stesso sistema di coordinate usato per comprendere lo sguardo ed è lo stesso usato per posizionare il cubo rotante.


Da **CameraResources::UpdateViewProjectionBuffer**:

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

Il viewport deve essere impostato per ogni frame. Il vertex shader (almeno) dovrà in genere accedere ai dati di visualizzazione/proiezione.


Da **CameraResources::AttachViewProjectionBuffer**:

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

**Eseguire il rendering nel buffer nascosto della fotocamera ed eseguire il commit del buffer di profondità:**

È buona idea verificare che **TryGetViewTransform** sia riuscito prima di provare a usare i dati di visualizzazione/proiezione, perché se il sistema di coordinate non è localizzato (ad esempio, il rilevamento è stato interrotto) l'app non può eseguirne il rendering per tale frame. Il modello chiama **Render sul** cubo rotante solo se la **classe CameraResources** indica un aggiornamento riuscito.

Windows Mixed Reality include funzionalità per la [stabilizzazione](../platform-capabilities-and-apis/hologram-stability.md) delle immagini per mantenere gli ologrammi posizionati dove uno sviluppatore o un utente li inserisce nel mondo. La stabilizzazione delle immagini consente di nascondere la latenza inerente a una pipeline di rendering per garantire esperienze olografiche ottimali per gli utenti. È possibile che venga specificato un punto di interesse per migliorare ulteriormente la stabilizzazione delle immagini oppure che venga fornito un buffer di profondità per calcolare la stabilizzazione delle immagini ottimizzata in tempo reale.

Per ottenere risultati ottimali, l'app deve fornire un buffer di profondità usando l'API <a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer.</a> Windows Mixed Reality possibile usare le informazioni sulla geometria del buffer di profondità per ottimizzare la stabilizzazione delle immagini in tempo reale. Il Windows di app Holographic esegue il commit del buffer di profondità dell'app per impostazione predefinita, consentendo di ottimizzare la stabilità dell'ologramma.

Da **AppMain::Render**:

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
>Windows la trama di profondità sulla GPU, quindi deve essere possibile usare il buffer di profondità come risorsa shader. L'ID3D11Texture2D creato deve essere in un formato senza tipo e deve essere associato come visualizzazione di risorse shader. Di seguito è riportato un esempio di come creare una trama di profondità di cui è possibile eseguire il commit per la stabilizzazione delle immagini.

Codice per **la creazione della risorsa buffer Depth per CommitDirect3D11DepthBuffer:**

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

**Disegnare contenuto olografico**

Il Windows di app Holographic esegue il rendering del contenuto in stereo usando la tecnica consigliata per disegnare la geometria con istanze in un oggetto Texture2DArray di dimensioni 2. Di seguito viene illustrata la parte di creazione di istanze di questo e il suo funzionamento Windows Mixed Reality.

Da **SpinningCubeRenderer::Render**:

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

Ogni istanza accede a una matrice di visualizzazione/proiezione diversa dal buffer costante. Ecco la struttura costante del buffer, che è solo una matrice di due matrici.

Da **VertexShaderShared.hlsl,** incluso da **VPRTVertexShader.hlsl:**

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

L'indice della matrice di destinazione di rendering deve essere impostato per ogni pixel. Nel frammento di codice seguente viene eseguito il mapping di output.viewId alla **SV_RenderTargetArrayIndex** semantica. Ciò richiede il supporto per una funzionalità Direct3D 11.3 facoltativa, che consente di impostare la semantica dell'indice della matrice di destinazione di rendering da qualsiasi fase dello shader.

Da **VPRTVertexShader.hlsl:**

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

Da **VertexShaderShared.hlsl,** incluso da **VPRTVertexShader.hlsl:**

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

Se si vogliono usare le tecniche di disegno con istanze esistenti con questo metodo di disegno in una matrice di destinazione di rendering stereo, disegnare il doppio del numero di istanze normalmente in uso. Nello shader dividere **input.instId** per 2 per ottenere l'ID istanza originale, che può essere indicizzato in un buffer di dati per oggetto: `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>Nota importante sul rendering di contenuto stereo in HoloLens

Windows Mixed Reality supporta la possibilità di impostare l'indice della matrice di destinazione di rendering da qualsiasi fase dello shader. In genere, si tratta di un'attività che può essere eseguita solo nella fase geometry shader a causa del modo in cui viene definita la semantica per Direct3D 11. Di seguito viene illustrato un esempio completo di come configurare una pipeline di rendering con solo il vertice e pixel shader fasi impostate. Il codice dello shader è come descritto in precedenza.

Da **SpinningCubeRenderer::Render**:

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>Nota importante sul rendering in dispositivi non HoloLens

L'impostazione dell'indice della matrice di destinazione di rendering nel vertex shader richiede che il driver di grafica supporti una funzionalità Direct3D 11.3 facoltativa, che HoloLens supporta. L'app può implementare in modo sicuro solo questa tecnica per il rendering e tutti i requisiti saranno soddisfatti per l'esecuzione nel Microsoft HoloLens.

È possibile che si voglia usare anche l'emulatore HoloLens, che può essere un potente strumento di sviluppo per l'app olografica, e supportare i dispositivi Windows Mixed Reality visori VR immersive collegati ai PC Windows 10. Il supporto per il percorso di rendering non HoloLens, per tutti i Windows Mixed Reality, è integrato anche nel modello di app Windows Holographic. Nel codice del modello è presente il codice per consentire l'esecuzione dell'app olografica nella GPU nel PC di sviluppo. Ecco come la classe **DeviceResources** verifica il supporto di questa funzionalità facoltativa.

Da **DeviceResources::CreateDeviceResources**:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

Per supportare il rendering senza questa funzionalità facoltativa, l'app deve usare un geometry shader per impostare l'indice della matrice di destinazione del rendering. Questo frammento  di codice viene aggiunto dopo  **VSSetConstantBuffers** e prima di **PSSetShader** nell'esempio di codice illustrato nella sezione precedente che illustra come eseguire il rendering stereo in HoloLens.

Da **SpinningCubeRenderer::Render**:

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

**NOTA HLSL:** in questo caso, è necessario caricare anche un vertex shader leggermente modificato che passa l'indice della matrice di destinazione di rendering al geometry shader usando una semantica dello shader sempre consentita, ad esempio TEXCOORD0. Lo shader geometry non deve eseguire alcuna operazione. Il modello geometry shader passa attraverso tutti i dati, ad eccezione dell'indice della matrice di destinazione di rendering, che viene usato per impostare la SV_RenderTargetArrayIndex semantica.

Codice del modello di app **per GeometryShader.hlsl:**

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

Con Windows Mixed Reality, il sistema controlla la catena di scambio. Il sistema gestisce quindi la presentazione di fotogrammi a ogni fotocamera olografica per garantire un'esperienza utente di alta qualità. Fornisce anche un aggiornamento del viewport per ogni fotogramma, per ogni fotocamera, per ottimizzare gli aspetti del sistema, ad esempio la stabilizzazione delle immagini o Acquisizione realtà mista. Pertanto, un'app olografica che usa DirectX non chiama **Present** su una catena di scambio DXGI. Al contrario, si usa la <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">classe HolographicFrame</a> per presentare tutti gli swapchain per un frame dopo aver finito di disegnarlo.

Da **DeviceResources::P resent:**

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

Per impostazione predefinita, questa API attende il completamento del frame prima che venga restituito. Le app olografiche devono attendere il completamento del fotogramma precedente prima di iniziare a lavorare su un nuovo fotogramma, perché ciò riduce la latenza e consente di ottenere risultati migliori dalle stime dei fotogrammi olografici. Non si tratta di una regola rigida e se il rendering dei fotogrammi che richiede più di un aggiornamento dello schermo è possibile disabilitare questa attesa passando il parametro HolographicFramePresentWaitBehavior a <a href="/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction.</a> In questo caso, è probabile che si usi un thread di rendering asincrono per mantenere un carico continuo sulla GPU. La frequenza di aggiornamento HoloLens dispositivo è di 60 hz, dove un fotogramma ha una durata di circa 16 ms. I dispositivi vr immersive possono variare da 60 hz a 90 hz; Quando si aggiorna lo schermo a 90 hz, ogni fotogramma avrà una durata di circa 11 ms.

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>Gestire scenari DeviceLost in collaborazione con HolographicFrame

Le app DirectX 11 in genere vogliono controllare il valore HRESULT restituito dalla funzione **Present** della catena di scambio DXGI per verificare se si è verificato un **errore DeviceLost.** La <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">classe HolographicFrame</a> gestisce automaticamente questa operazione. Esaminare <a href="/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">l'oggetto HolographicFramePresentResult</a> restituito per scoprire se è necessario rilasciare e ricreare il dispositivo Direct3D e le risorse basate sul dispositivo.

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

Se il dispositivo Direct3D è stato perso ed è stato ricreato, è necessario indicare a <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> di iniziare a usare il nuovo dispositivo. La catena di scambio verrà ricreata per questo dispositivo.

Da **DeviceResources::InitializeUsingHolographicSpace**:

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

Dopo aver presentato il frame, è possibile tornare al ciclo del programma principale e consentirlo di continuare con il frame successivo.

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>PC grafici ibridi e applicazioni di realtà mista

Windows 10 Creators Update I PC possono essere configurati **con** GPU discrete e integrate. Con questi tipi di computer, Windows sceglierà l'adattatore a cui è connesso il visore VR. Le applicazioni devono assicurarsi che il dispositivo DirectX creato usi la stessa scheda.

Il codice di esempio Direct3D più generale illustra la creazione di un dispositivo DirectX usando la scheda hardware predefinita, che in un sistema ibrido potrebbe non essere uguale a quella usata per il visore VR.

Per risolvere eventuali problemi, usare <a href="/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterID</a> da <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace.</a> PrimaryAdapterId() o <a href="/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay.</a> AdapterId(). Questo adapterId può quindi essere usato per selezionare il DXGIAdapter giusto usando IDXGIFactory4.EnumAdapterByLuid.

Da **DeviceResources::InitializeUsingHolographicSpace**:

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

Codice per **aggiornare DeviceResources::CreateDeviceResources per l'uso di IDXGIAdapter**

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

L'Media Foundation nei sistemi ibridi può causare problemi in cui il rendering del video non viene eseguito o la trama video è danneggiata perché Media Foundation predefinito è un comportamento del sistema. In alcuni scenari è necessario creare un id3D11Device separato per supportare il multithreading e vengono impostati i flag di creazione corretti.

Quando si inizializza ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT deve essere definito come parte del D3D11_CREATE_DEVICE_FLAG. Dopo aver creato il dispositivo e il contesto, chiamare <a href="/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> per abilitare il multithreading. Per associare il dispositivo a <a href="/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager,</a>usare la <a href="/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">funzione IMFDXGIDeviceManager::ResetDevice.</a>

Codice per **associare id3D11Device a IMFDXGIDeviceManager:**

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

## <a name="see-also"></a>Vedi anche
* [Sistemi di coordinate in DirectX](coordinate-systems-in-directx.md)
* [Uso dell'emulatore HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md)