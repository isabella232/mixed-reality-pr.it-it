---
title: Mapping spaziale in DirectX
description: Informazioni su come implementare il mapping spaziale nell'app DirectX e su come usare l'applicazione di esempio di mapping spaziale in Universal Windows Platform SDK.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows realtà mista, mapping spaziale, ambiente, interazione, directx, winrt, API, codice di esempio, UWP, SDK, procedura dettagliata
ms.openlocfilehash: e7f0735ea28703d3a9f18198901ffa5f06676f78b7b8962bf20824e05f793061
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198847"
---
# <a name="spatial-mapping-in-directx"></a>Mapping spaziale in DirectX

> [!NOTE]
> Questo articolo è correlato alle API native WinRT legacy.  Per i nuovi progetti di app native, è consigliabile usare **[l'API OpenXR](openxr-getting-started.md)**.

Questo argomento descrive come implementare il [mapping](../../design/spatial-mapping.md) spaziale nell'app DirectX, inclusa una spiegazione dettagliata dell'applicazione di esempio di mapping spaziale inclusa in un pacchetto con Universal Windows Platform SDK.

Questo argomento usa il codice [dell'esempio di codice UWP HolographicSpatialMapping.](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l'uso di C++/CX anziché di C++17 conforme a C++/WinRT usato nel modello di progetto [olografico C++.](creating-a-holographic-directx-project.md)  I concetti sono equivalenti per un progetto C++/WinRT, anche se è necessario tradurre il codice.

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Mapping spaziale</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="directx-development-overview"></a>Panoramica dello sviluppo DirectX

Lo sviluppo di applicazioni native per il mapping spaziale usa le API nel [Windows. Spazio dei nomi Perception.Spatial.](/uwp/api/Windows.Perception.Spatial) Queste API offrono il controllo completo della funzionalità di mapping spaziale, nello stesso modo in cui le API di mapping spaziale vengono esposte da [Unity.](../unity/spatial-mapping-in-unity.md)

### <a name="perception-apis"></a>API per la percezione

I tipi principali forniti per lo sviluppo del mapping spaziale sono i seguenti:
* [SpatialSurfaceObserver](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) fornisce informazioni sulle superfici nelle aree di spazio specificate dall'applicazione vicino all'utente, sotto forma di oggetti SpatialSurfaceInfo.
* [SpatialSurfaceInfo](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo) descrive una singola superficie spaziale esterna, inclusi un ID univoco, il volume di delimitazione e l'ora dell'ultima modifica. Fornirà un spatialSurfaceMesh in modo asincrono su richiesta.
* [SpatialSurfaceMeshOptions contiene i](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMeshOptions) parametri usati per personalizzare gli oggetti SpatialSurfaceMesh richiesti da SpatialSurfaceInfo.
* [SpatialSurfaceMesh rappresenta](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh) i dati della mesh per una singola superficie spaziale. I dati per le posizioni dei vertici, le normali dei vertici e gli indici triangolo sono contenuti negli oggetti spatialSurfaceMeshBuffer del membro.
* [SpatialSurfaceMeshBuffer esegue il](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMeshBuffer) wrapping di un singolo tipo di dati mesh.

Quando si sviluppa un'applicazione usando queste API, il flusso di programma di base sarà simile al seguente (come illustrato nell'applicazione di esempio descritta di seguito):
- **Configurare SpatialSurfaceObserver**
  - Chiamare [RequestAccessAsync](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver)per assicurarsi che l'utente abbia autorizzato l'applicazione a usare le funzionalità di mapping spaziale del dispositivo.
  - Creare un'istanza di un oggetto SpatialSurfaceObserver.
  - Chiamare [SetBoundingVolumes per](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) specificare le aree di spazio in cui si desiderano informazioni sulle superfici spaziali. È possibile modificare queste aree in futuro chiamando di nuovo questa funzione. Ogni area viene specificata usando [spatialBoundingVolume.](/uwp/api/Windows.Perception.Spatial.SpatialBoundingVolume)
  - Registrarsi [per l'evento ObservedSurfacesChanged,](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) che verrà generato ogni volta che sono disponibili nuove informazioni sulle superfici spaziali nelle aree dello spazio specificate.
- **Eventi Process ObservedSurfacesChanged**
  - Nel gestore eventi chiamare [GetObservedSurfaces](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) per ricevere una mappa di oggetti SpatialSurfaceInfo. Usando questa mappa, è possibile aggiornare i record delle superfici spaziali [presenti nell'ambiente dell'utente.](../../design/spatial-mapping.md#mesh-caching)
  - Per ogni oggetto SpatialSurfaceInfo, è possibile eseguire una query [su TryGetBounds](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo) per determinare gli extent spaziali della superficie, espressi in un sistema di [coordinate](../../design/coordinate-systems.md) spaziali di propria scelta.
  - Se si decide di richiedere una mesh per una superficie spaziale, chiamare [TryComputeLatestMeshAsync.](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo) È possibile fornire opzioni che specificano la densità dei triangoli e il formato dei dati della mesh restituiti.
- **Ricevere ed elaborare mesh**
  - Ogni chiamata a TryComputeLatestMeshAsync restituirà in modo asincrono un oggetto SpatialSurfaceMesh.
  - Da questo oggetto è possibile accedere agli oggetti SpatialSurfaceMeshBuffer contenuti, che consente di accedere agli indici triangolare, alle posizioni dei vertici e alle normali dei vertici della mesh, se richiesto. Questi dati saranno in un formato direttamente compatibile con le API [Direct3D 11 usate](/windows/win32/api/d3d11/nf-d3d11-id3d11device-createbuffer) per il rendering delle mesh.
  - Da qui l'applicazione può facoltativamente analizzare o [elaborare](../../design/spatial-mapping.md#mesh-processing) i dati della mesh e usarli per il [rendering](../../design/spatial-mapping.md#rendering) e [il raycasting fisico e la collisione.](../../design/spatial-mapping.md#raycasting-and-collision)
  - Un dettaglio importante da notare è che è necessario applicare una scala alle posizioni dei vertici mesh (ad esempio nel vertex shader usato per il rendering delle mesh) per convertirle dalle unità integer ottimizzate in cui sono archiviate nel buffer, in metri. È possibile recuperare questa scala chiamando [VertexPositionScale.](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh)

### <a name="troubleshooting"></a>Risoluzione dei problemi
* Non dimenticare di ridimensionare le posizioni dei vertici mesh nel vertex shader, usando la scala restituita da [SpatialSurfaceMesh.VertexPositionScale](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh)

## <a name="spatial-mapping-code-sample-walkthrough"></a>Procedura dettagliata per l'esempio di codice di mapping spaziale

L'esempio di codice di mapping spaziale [olografico](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) include codice che è possibile usare per iniziare a caricare mesh di superficie nell'app, inclusa l'infrastruttura per la gestione e il rendering delle mesh di superficie.

A questo punto, viene illustrato come aggiungere funzionalità di mapping della superficie all'app DirectX. È possibile aggiungere questo codice al progetto Windows modello di [app Holographic](creating-a-holographic-directx-project.md) oppure è possibile seguire la procedura esplorando l'esempio di codice indicato in precedenza. Questo esempio di codice è basato sul modello Windows'app Holographic.

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Configurare l'app per l'uso della funzionalità spatialPerception

L'app può usare la funzionalità di mapping spaziale. Ciò è necessario perché la mesh spaziale è una rappresentazione dell'ambiente dell'utente, che può essere considerata dati privati. Dichiarare questa funzionalità nel file package.appxmanifest per l'app. Ecco un esempio:

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

La funzionalità proviene dallo spazio dei nomi **uap2.** Per ottenere l'accesso a questo spazio dei nomi nel manifesto, includerlo come attributo *xlmns* nell'elemento &lt; package>. Ecco un esempio:

```xml
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>Verificare il supporto delle funzionalità di mapping spaziale

Windows Mixed Reality supporta un'ampia gamma di dispositivi, inclusi quelli che non supportano il mapping spaziale. Se l'app può usare il mapping spaziale o deve usare il mapping spaziale per fornire funzionalità, verificare che il mapping spaziale sia supportato prima di provare a usarlo. Ad esempio, se il mapping spaziale è richiesto dall'app di realtà mista, dovrebbe essere visualizzato un messaggio a tale effetto se un utente prova a eseguire il mapping spaziale in un dispositivo. Oppure, l'app può eseguire il rendering del proprio ambiente virtuale al posto dell'ambiente dell'utente, offrendo un'esperienza simile a quella che accadrebbe se fosse disponibile il mapping spaziale. In ogni caso, questa API consente all'app di essere a conoscenza di quando non otterrà i dati di mapping spaziale e risponderà nel modo appropriato.

Per verificare il supporto del mapping spaziale nel dispositivo corrente, verificare prima di tutto che il contratto UWP sia al livello 4 o superiore e quindi chiamare SpatialSurfaceObserver::IsSupported(). Ecco come eseguire questa operazione nel contesto dell'esempio di codice di mapping [spaziale olografico.](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) Il supporto viene controllato subito prima di richiedere l'accesso.

L'API SpatialSurfaceObserver::IsSupported() è disponibile a partire dalla versione 15063 dell'SDK. Se necessario, ridestinare il progetto alla versione 15063 della piattaforma prima di usare questa API.

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

Quando il contratto UWP è inferiore al livello 4, l'app deve procedere come se il dispositivo fosse in grado di eseguire il mapping spaziale.

### <a name="request-access-to-spatial-mapping-data"></a>Richiedere l'accesso ai dati di mapping spaziale

L'app deve richiedere l'autorizzazione per accedere ai dati di mapping spaziale prima di provare a creare qualsiasi osservatore di superficie. Di seguito è riportato un esempio basato sull'esempio di codice surface mapping, con altri dettagli forniti più avanti in questa pagina:

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a>Creare un osservatore di superficie

Lo spazio dei nomi **Windows::P erception::Spatial::Surfaces** include la [classe SpatialSurfaceObserver,](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) che osserva uno o più volumi specificati in [SpatialCoordinateSystem.](/uwp/api/Windows.Perception.Spatial.SpatialCoordinateSystem) Usare [un'istanza spatialSurfaceObserver](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) per accedere ai dati della mesh di superficie in tempo reale.

Da **AppMain.h:**

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

Come specificato nella sezione precedente, è necessario richiedere l'accesso ai dati di mapping spaziale prima che l'app possa usarli. Questo accesso viene concesso automaticamente nel HoloLens.

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

Successivamente, è necessario configurare l'osservatore di superficie per osservare un volume di delimitazione specifico. Qui si osserva una casella di 20x20x5 metri, centrata all'origine del sistema di coordinate.

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

È invece possibile impostare più volumi di delimitazione.

*Si tratta di uno pseudocodice:*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

È anche possibile usare altre forme di delimitazione, ad esempio un frustum di visualizzazione o un rettangolo di selezione non allineato all'asse.

*Si tratta di uno pseudocodice:*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

Se l'app deve eseguire operazioni diverse quando i dati di mapping della superficie non sono disponibili, è possibile scrivere codice per rispondere al caso in cui [SpatialPerceptionAccessStatus](/uwp/api/Windows.Perception.Spatial.SpatialPerceptionAccessStatus) non è **Consentito.** Ad esempio, non sarà consentito nei PC con dispositivi immersive collegati perché tali dispositivi non dispongono di hardware per il mapping spaziale. Per questi dispositivi, è invece consigliabile basarsi sulla fase spaziale per informazioni sulla configurazione dell'ambiente e del dispositivo dell'utente.

### <a name="initialize-and-update-the-surface-mesh-collection"></a>Inizializzare e aggiornare la raccolta di mesh di superficie

Se l'osservatore di superficie è stato creato correttamente, è possibile continuare a inizializzare la raccolta della mesh di superficie. In questo caso si usa l'API del modello pull per ottenere immediatamente il set corrente di superfici osservate:

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

È disponibile anche un modello push per ottenere i dati della mesh di superficie. È possibile progettare l'app in modo che usi solo il modello pull, se si sceglie, nel qual caso si esegue il polling dei dati ogni tanto, ad esempio una volta per fotogramma, o durante un periodo di tempo specifico, ad esempio durante la configurazione del gioco. In tal caso, il codice precedente è quello necessario.

Nell'esempio di codice è stato scelto di illustrare l'uso di entrambi i modelli per scopi didattici. In questo caso, viene sottoscritto un evento per ricevere dati di mesh di superficie aggiornati ogni volta che il sistema riconosce una modifica.

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

Anche l'esempio di codice è configurato per rispondere a questi eventi. Verrà ora illustrato come eseguire questa operazione.

**NOTA:** Questo potrebbe non essere il modo più efficiente per la gestione dei dati mesh da parte dell'app. Questo codice viene scritto per maggiore chiarezza e non è ottimizzato.

I dati della mesh di superficie vengono forniti in una mappa di sola lettura che archivia [gli oggetti SpatialSurfaceInfo](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo) usando [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) come valori chiave.

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

Per elaborare questi dati, si cerca prima di tutto i valori di chiave che non sono presenti nella raccolta. I dettagli sulla modalità di archiviazione dei dati nell'app di esempio verranno presentati più avanti in questo argomento.

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

È anche necessario rimuovere le mesh di superficie presenti nella raccolta di mesh di superficie, ma che non sono più presenti nella raccolta di sistema. A tale scopo, è necessario eseguire un'operazione simile all'opposto di quanto appena illustrato per l'aggiunta e l'aggiornamento delle mesh. Si esegue un ciclo nella raccolta dell'app e si verifica se il **GUID** è presente nella raccolta di sistema. Se non è presente nella raccolta di sistema, viene rimosso dalla raccolta.

Dal gestore eventi in AppMain.cpp:

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

Implementazione dell'eliminazione di mesh in RealtimeSurfaceMeshRenderer.cpp:

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>Acquisire e usare buffer di dati surface mesh

Ottenere le informazioni sulla mesh di superficie è stato semplice come eseguire il pull di una raccolta dati ed elaborare gli aggiornamenti a tale raccolta. A questo punto, verranno fornite informazioni dettagliate su come usare i dati.

Nell'esempio di codice si è scelto di usare le mesh di superficie per il rendering. Si tratta di uno scenario comune per ologrammi ologrammi dietro le superfici reali. È anche possibile eseguire il rendering delle mesh o delle versioni elaborate per mostrare all'utente quali aree della stanza vengono analizzate prima di iniziare a fornire funzionalità di app o giochi.

L'esempio di codice avvia il processo quando riceve gli aggiornamenti della mesh di superficie dal gestore eventi descritto nella sezione precedente. L'importante riga di codice in questa funzione è la chiamata per aggiornare la mesh di superficie: a questo punto le informazioni sulla *mesh* sono già state elaborate e si stanno per ottenere i dati di vertice e indice per l'uso in base alle esigenze.

Da RealtimeSurfaceMeshRenderer.cpp:

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

Il codice di esempio è progettato in modo che una classe di dati, **SurfaceMesh**, gestisca l'elaborazione e il rendering dei dati mesh. Queste mesh sono ciò di **cui RealtimeSurfaceMeshRenderer** mantiene effettivamente una mappa. Ognuno ha un riferimento all'elemento SpatialSurfaceMesh di origine, quindi è possibile usarlo ogni volta che è necessario accedere al vertice della mesh o ai buffer di indice o ottenere una trasformazione per la mesh. Per il momento, la mesh viene contrassegnata come necessaria per un aggiornamento.

Da SurfaceMesh.cpp:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

Alla successiva richiesta di disegnare la mesh, verrà prima verificata la bandierina. Se è necessario un aggiornamento, i buffer vertice e indice verranno aggiornati nella GPU.

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

Per prima cosa, si acquisiscono i buffer di dati non elaborati:

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

Vengono quindi creati buffer del dispositivo Direct3D con i dati mesh forniti dal HoloLens:

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

**NOTA:** Per la funzione helper CreateDirectXBuffer usata nel frammento di codice precedente, vedere l'esempio di codice di Surface Mapping: SurfaceMesh.cpp, GetDataFromIBuffer.h. La creazione della risorsa del dispositivo è stata completata e la mesh viene considerata caricata e pronta per l'aggiornamento e il rendering.

### <a name="update-and-render-surface-meshes"></a>Aggiornare ed eseguire il rendering delle mesh di superficie

La classe SurfaceMesh ha una funzione di aggiornamento specializzata. Ogni [SpatialSurfaceMesh](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh) ha una propria trasformazione e l'esempio usa il sistema di coordinate corrente per **SpatialStationaryReferenceFrame** per acquisire la trasformazione. Quindi aggiorna il buffer costante del modello nella GPU.

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

Quando è il momento di eseguire il rendering delle mesh di superficie, vengono eseguite alcune operazioni di preparazione prima di eseguire il rendering della raccolta. La pipeline shader è stata impostata per la configurazione di rendering corrente e la fase dell'assembler di input. La classe helper fotocamera olografica **CameraResources.cpp** ha già configurato il buffer costante di visualizzazione/proiezione.

Da **RealtimeSurfaceMeshRenderer::Render**:

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

Al termine, si esegue un ciclo sulle mesh e si dice a ognuno di disegnare se stesso. **NOTA:** Questo codice di esempio non è ottimizzato per l'uso di qualsiasi tipo di frustum culling, ma è consigliabile includere questa funzionalità nell'app.

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

Le singole mesh sono responsabili della configurazione del vertice e dell'index buffer, dello stride e del buffer costante di trasformazione del modello. Come per il cubo rotante nel modello Windows'app Holographic, il rendering viene eseguito in buffer stereoscopici usando l'instancing.

Da **SurfaceMesh::D raw**:

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a>Scelte di rendering con Surface Mapping

L'esempio di codice di Mapping superficie offre codice per il rendering solo occlusione dei dati della mesh di superficie e per il rendering su schermo dei dati della mesh di superficie. Il percorso scelto, o entrambi, dipende dall'applicazione. In questo documento verranno trattate entrambe le configurazioni.

**Rendering dei buffer di occlusione per l'effetto olografico**

Per iniziare, cancellare la visualizzazione di destinazione di rendering per la fotocamera virtuale corrente.

Da AppMain.cpp:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

Si tratta di un passaggio di "pre-rendering". In questo caso, si crea un buffer di occlusione richiedendo al renderer mesh di eseguire il rendering solo della profondità. In questa configurazione non viene collegata una visualizzazione di destinazione di rendering e il renderer mesh imposta la fase pixel shader su **nullptr** in modo che la GPU non si preoccupa di disegnare pixel. La geometria verrà rasterizzata nel buffer di profondità e la pipeline grafica verrà interrotta.

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

È possibile disegnare ologrammi con un test di profondità aggiuntivo rispetto al buffer di occlusione di Surface Mapping. In questo esempio di codice viene eseguito il rendering dei pixel del cubo di un colore diverso se sono dietro una superficie.

Da AppMain.cpp:

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

In base al codice di SpecialEffectPixelShader.hlsl:

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

**Nota:** Per la **routine GatherDepthLess,** vedere l'esempio di codice di Surface Mapping: SpecialEffectPixelShader.hlsl.

**Rendering dei dati della mesh di superficie nella visualizzazione**

È anche possibile disegnare semplicemente le mesh di superficie nei buffer di visualizzazione stereo. È stato scelto di disegnare visi completi con illuminazione, ma è possibile disegnare wireframe, elaborare mesh prima del rendering, applicare una mappa trame e così via.

In questo esempio di codice viene indicato al renderer mesh di disegnare la raccolta. Questa volta non si specifica un passaggio di solo profondità, verrà collegato un pixel shader e verrà completata la pipeline di rendering usando le destinazioni specificate per la fotocamera virtuale corrente.

```cpp
// Spatial Mapping mesh rendering pass: Draw Spatial Mapping mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a>Vedi anche
* [Creazione di un progetto DirectX olografico](creating-a-holographic-directx-project.md)
* [Windows. Perception.Spatial API](/uwp/api/Windows.Perception.Spatial)