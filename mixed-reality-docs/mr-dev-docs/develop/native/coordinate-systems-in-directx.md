---
title: Sistemi di coordinate in DirectX
description: Informazioni sui sistemi di coordinate in DirectX e realtà mista con localizzatori spaziali, fotogrammi di riferimento e ancoraggi nello spazio.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: Realtà mista, localizzatore spaziale, frame di riferimento spaziale, sistema di coordinate spaziali, fase spaziale, codice di esempio, stabilizzazione delle immagini, ancoraggio nello spazio, archivio di ancoraggi nello spazio, perdita di traccia, procedura dettagliata, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale
ms.openlocfilehash: 5da521568ef15f0c512984c96846939bd30063d3485709d4b6568dc9b155052a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196452"
---
# <a name="coordinate-systems-in-directx"></a>Sistemi di coordinate in DirectX

> [!NOTE]
> Questo articolo è correlato alle API native WinRT legacy.  Per i nuovi progetti di app native, è consigliabile usare **[l'API OpenXR](openxr-getting-started.md)**.

[I sistemi](../../design/coordinate-systems.md) di coordinate formano la base per la comprensione spaziale offerta Windows Mixed Reality API.

Gli attuali dispositivi VR o VR con singola stanza stabiliscono un sistema di coordinate principale per lo spazio monitorato. I dispositivi di realtà mista HoloLens sono progettati per ambienti non definiti di grandi dimensioni, con il dispositivo che individua e apprende l'ambiente circostante mentre l'utente si aggira. Il dispositivo si adatta per migliorare continuamente le conoscenze sulle stanze dell'utente, ma comporta sistemi di coordinate che modificano la relazione tra loro nel corso della durata delle app. Windows Mixed Reality supporta un'ampia gamma di dispositivi, che vanno da visori VR immersive da seed a fotogrammi di riferimento collegati al mondo.

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l'uso di C++/CX anziché di C++17 conforme a C++/WinRT usato nel modello di progetto [olografico C++.](creating-a-holographic-directx-project.md)  I concetti sono equivalenti per un progetto C++/WinRT, anche se è necessario tradurre il codice.

## <a name="spatial-coordinate-systems-in-windows"></a>Sistemi di coordinate spaziali in Windows

Il tipo di base usato per la motivazione dei sistemi di coordinate reali in Windows è <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem.</a> Un'istanza di questo tipo rappresenta un sistema di coordinate arbitrario, fornendo un metodo per ottenere i dati della matrice di trasformazione che è possibile usare per la trasformazione tra due sistemi di coordinate senza comprendere i dettagli di ognuno.

I metodi che restituiscono informazioni spaziali accetteranno un parametro SpatialCoordinateSystem per consentire di decidere il sistema di coordinate in cui è più utile restituire tali coordinate. Le informazioni spaziali sono rappresentate come punti, raggi o volumi nell'ambiente circostante dell'utente e le unità per queste coordinate saranno sempre in metri.

SpatialCoordinateSystem ha una relazione dinamica con altri sistemi di coordinate, inclusi quelli che rappresentano la posizione del dispositivo. In qualsiasi momento, il dispositivo può individuare alcuni sistemi di coordinate e non altri. Per la maggior parte dei sistemi di coordinate, l'app deve essere pronta a gestire periodi di tempo durante i quali non possono essere individuati.

L'applicazione non deve creare direttamente SpatialCoordinateSystems, ma deve essere utilizzata tramite le API Perception. Esistono tre origini principali dei sistemi di coordinate nelle API Perception, ognuna delle quali è mappata a un concetto descritto nella pagina [Sistemi di](../../design/coordinate-systems.md) coordinate:
* Per ottenere un frame zionario di riferimento, creare <a href="/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">un oggetto SpatialStationaryFrameOfReference</a> o ottenerne uno dall'oggetto <a href="/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference corrente.</a>
* Per ottenere un ancoraggio nello spaziale, creare <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">un spatialAnchor</a>.
* Per ottenere un frame collegato di riferimento, creare <a href="/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">un spatialLocatorAttachedFrameOfReference.</a>

Tutti i sistemi di coordinate restituiti da questi oggetti sono a destra, con +y in alto, +x a destra e +z indietro. È possibile ricordare la direzione dei punti positivi dell'asse z puntando le dita della mano sinistra o destra nella direzione x positiva e arricciandole nella direzione y positiva. La direzione verso cui punta il cursore, verso o fuori dall'utente, è la direzione verso cui punta l'asse z positivo per il sistema di coordinate. La figura seguente mostra questi due sistemi di coordinate.

![Sistemi di coordinate a sinistra e a destra](images/left-hand-right-hand.gif)<br>
*Sistemi di coordinate a sinistra e a destra*

Usare la <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">classe SpatialLocator</a> per creare una cornice di riferimento collegata o stazionaria da avviare in spatialCoordinateSystem in base alla HoloLens posizione. Continuare con la sezione successiva per altre informazioni su questo processo.

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>Posizionare gli ologrammi nel mondo usando una fase spaziale

È possibile accedere al sistema di coordinate per Windows Mixed Reality visori VR immersive usando la proprietà <a href="/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">statica SpatialStageFrameOfReference::Current.</a> Questa API fornisce:

* Un sistema di coordinate
* Informazioni sul fatto che il lettore sia sesato o mobile
* Limite di un'area sicura per spostarsi se il giocatore è mobile
* Indicazione che indica se il visore VR è direzionale. 
* Gestore eventi per gli aggiornamenti alla fase spaziale.

In primo luogo, si ottiene la fase spaziale e si sottoscrive per gli aggiornamenti: 

Codice per **l'inizializzazione della fase spaziale**

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

Nel metodo OnCurrentChanged l'app deve esaminare la fase spaziale e aggiornare l'esperienza del giocatore. In questo esempio viene illustrata una visualizzazione del limite della fase e la posizione iniziale specificata dall'utente e l'intervallo di visualizzazione e intervallo di proprietà di spostamento della fase. Si esegue anche il fall back al proprio sistema di coordinate stazionarie, quando non è possibile specificare una fase.


Codice per **l'aggiornamento della fase spaziale**

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

Il set di vertici che definiscono il limite della fase viene fornito in senso orario. La Windows Mixed Reality traccia un limite al limite quando l'utente si avvicina, ma è possibile triangolare l'area per scopi personalizzati. L'algoritmo seguente può essere usato per triangolare la fase.


Codice per **la triangolazione della fase spaziale**

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>Posizionare gli ologrammi nel mondo usando una cornice di riferimento stazionaria

La [classe SpatialStationaryFrameOfReference](/uwp/api/Windows.Perception.Spatial.SpatialStationaryFrameOfReference) rappresenta una [](../../design/coordinate-systems.md#stationary-frame-of-reference) cornice di riferimento che rimane stazionaria rispetto all'ambiente circostante dell'utente mentre l'utente si sposta. Questo frame di riferimento assegna priorità mantenendo le coordinate stabili vicino al dispositivo. Un uso chiave di SpatialStationaryFrameOfReference è fungere da sistema di coordinate del mondo sottostante all'interno di un motore di rendering durante il rendering degli ologrammi.

Per ottenere un spatialStationaryFrameOfReference, usare la [classe SpatialLocator](/uwp/api/Windows.Perception.Spatial.SpatialLocator) e chiamare [CreateStationaryFrameOfReferenceAtCurrentLocation.](/uwp/api/Windows.Perception.Spatial.SpatialLocator)

Dal codice Windows modello di app Holographic:

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* I fotogrammi di riferimento stazionari sono progettati per offrire una posizione ottimale rispetto allo spazio complessivo. Le singole posizioni all'interno di tale frame di riferimento possono deviare leggermente. Questo è normale perché il dispositivo apprende di più sull'ambiente.
* Quando è necessario un posizionamento preciso dei singoli ologrammi, è necessario usare un SpatialAnchor per ancorare il singolo ologramma a una posizione nel mondo reale, ad esempio un punto che l'utente indica di essere di particolare interesse. Le posizioni dell'ancoraggio non si distondono, ma possono essere corrette. L'ancoraggio userà la posizione corretta a partire dal fotogramma successivo dopo che è stata apportata la correzione.

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>Posizionare gli ologrammi nel mondo usando ancoraggi nello spazio

[Gli ancoraggi](../../design/coordinate-systems.md#spatial-anchors) nello spazio sono un ottimo modo per posizionare gli ologrammi in una posizione specifica nel mondo reale, con il sistema che garantisce che l'ancoraggio rimanga in posizione nel tempo. Questo argomento illustra come creare e usare un ancoraggio e come usare i dati di ancoraggio.

È possibile creare un spatialAnchor in qualsiasi posizione e orientamento all'interno di SpatialCoordinateSystem di propria scelta. Il dispositivo deve essere in grado di individuare il sistema di coordinate al momento e il sistema non deve aver raggiunto il limite di ancoraggi nello spazio.

Una volta definito, il sistema di coordinate di un SpatialAnchor si regola continuamente per mantenere la posizione e l'orientamento precisi della posizione iniziale. È quindi possibile usare questo SpatialAnchor per eseguire il rendering di ologrammi che verranno visualizzati fissi nell'ambiente circostante dell'utente in quella posizione esatta.

Gli effetti delle regolazioni che mantengono l'ancoraggio sul posto vengono ingranditi con l'aumentare della distanza dall'ancoraggio. È consigliabile evitare di eseguire il rendering del contenuto rispetto a un ancoraggio che si trova a più di 3 metri circa dall'origine di tale ancoraggio.

La [proprietà CoordinateSystem](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) ottiene un sistema di coordinate che consente di posizionare il contenuto rispetto all'ancoraggio, con l'easing applicato quando il dispositivo regola la posizione precisa dell'ancoraggio.

Usare la [proprietà RawCoordinateSystem](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) e l'evento [RawCoordinateSystemAdjusted](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) corrispondente per gestire manualmente queste modifiche.

### <a name="persist-and-share-spatial-anchors"></a>Salvare in modo permanente e condividere ancoraggi nello spaziale

È possibile rendere persistente un oggetto SpatialAnchor in locale usando la classe [SpatialAnchorStore](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore) e quindi riportarlo in una sessione futura dell'app nello stesso HoloLens dispositivo.

Con Ancoraggi nello stato <a href="/azure/spatial-anchors/overview" target="_blank">di Azure</a>è possibile creare un ancoraggio di cloud durevole da un spatialAnchor locale, che l'app può quindi individuare in più dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio nello spazio comune tra più dispositivi, ogni utente può visualizzare il rendering del contenuto relativo a tale ancoraggio nella stessa posizione fisica in tempo reale. 

È anche possibile usare <a href="/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello stato di Azure</a> per la persistenza asincrona degli ologrammi nei dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio nello spaziale cloud durevole, più dispositivi possono osservare lo stesso ologramma persistente nel tempo, anche se tali dispositivi non sono presenti contemporaneamente.

Per iniziare a creare esperienze condivise nell'app HoloLens, provare la guida introduttiva di Ancoraggi nello <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">spazio di Azure HoloLens di 5 minuti.</a>

Quando si è in esecuzione con Ancoraggi nello spazio di Azure, è possibile creare e individuare <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">ancoraggi in HoloLens</a>.  Sono disponibili procedure dettagliate anche per Android e <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">iOS,</a> che consentono di condividere gli stessi ancoraggi in tutti i dispositivi.

### <a name="create-spatialanchors-for-holographic-content"></a>Creare spatialAnchors per contenuto olografico

Per questo esempio di codice è stato modificato Windows modello di app Holographic per creare ancoraggi quando viene rilevato il **movimento Pressed.** Il cubo viene quindi posizionato in corrispondenza dell'ancoraggio durante il passaggio di rendering.

Poiché la classe helper supporta più ancoraggi, è possibile inserire tutti i cubi che si vuole usare in questo esempio di codice.

> [!NOTE]
> Gli ID per gli ancoraggi sono un elemento che puoi controllare nell'app. In questo esempio è stato creato uno schema di denominazione sequenziale basato sul numero di ancoraggi attualmente archiviati nella raccolta di ancoraggi dell'app.

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>Caricare e memorizzare nella cache in modo asincrono SpatialAnchorStore

Verrà ora illustrato come scrivere una classe SampleSpatialAnchorHelper che consente di gestire questa persistenza, tra cui:
* Archiviazione di una raccolta di ancoraggi in memoria, indicizzata da una chiave Platform::String.
* Caricamento di ancoraggi dall'oggetto SpatialAnchorStore del sistema, che viene mantenuto separato dalla raccolta in memoria locale.
* Salvataggio della raccolta locale di ancoraggi in memoria in SpatialAnchorStore quando l'app sceglie di eseguire questa operazione.

Ecco come salvare gli [oggetti SpatialAnchor](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) in [SpatialAnchorStore.](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore)

All'avvio della classe, viene richiesto SpatialAnchorStore in modo asincrono. Ciò comporta l'I/O di sistema quando l'API carica l'archivio di ancoraggio e questa API viene resa asincrona in modo che l'I/O non sia bloccante.

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

Ti verrà assegnato un spatialAnchorStore che puoi usare per salvare gli ancoraggi. Si tratta di un oggetto IMapView che associa valori di chiave che sono Stringhe, con valori di dati SpatialAnchors. Nel codice di esempio viene archiviata in una variabile membro di classe privata accessibile tramite una funzione pubblica della classe helper.

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>Non dimenticare di associare gli eventi di sospensione/ripresa per salvare e caricare l'archivio di ancoraggio.

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a>Salvare il contenuto nell'archivio di ancoraggio

Quando il sistema sospende l'app, devi salvare gli ancoraggi nello spazio nell'archivio di ancoraggi. Puoi anche scegliere di salvare gli ancoraggi nell'archivio di ancoraggi in altri momenti, perché ti trovi necessario per l'implementazione dell'app.

Quando si è pronti per provare a salvare gli ancoraggi in memoria in SpatialAnchorStore, è possibile scorrere la raccolta e provare a salvare ognuno di essi.

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>Caricare contenuto dall'archivio di ancoraggio quando l'app riprende

Puoi ripristinare gli ancoraggi salvati in AnchorStore trasferendoli da IMapView dell'archivio di ancoraggi al tuo database in memoria di SpatialAnchors quando l'app riprende o in qualsiasi momento.

Per ripristinare gli ancoraggi da SpatialAnchorStore, ripristina tutti gli ancoraggi a cui sei interessato nella tua raccolta in memoria.

È necessario un database in memoria di SpatialAnchors per associare le stringhe agli SpatialAnchors creati. Nel codice di esempio si sceglie di usare un Windows::Foundation::Collections::IMap per archiviare gli ancoraggi, semplificando l'uso della stessa chiave e dello stesso valore di dati per SpatialAnchorStore.

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>Un ancoraggio ripristinato potrebbe non essere immediatamente localizzato. Ad esempio, potrebbe essere un ancoraggio in una stanza separata o in un edificio diverso. Gli ancoraggi recuperati da AnchorStore devono essere testati per verificane l'individuabilità prima di usarli.

<br>

>[!NOTE]
>In questo codice di esempio vengono recuperati tutti gli ancoraggi da AnchorStore. Questo non è un requisito. L'app può anche scegliere un determinato subset di ancoraggi usando valori di chiave String significativi per l'implementazione.

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a>Cancellare l'archivio di ancoraggio, quando necessario

In alcuni casi, è necessario cancellare lo stato dell'app e scrivere nuovi dati. Ecco come eseguire questa operazione con [SpatialAnchorStore](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore).

Usando la classe helper, non è quasi necessario eseguire il wrapping della funzione Clear. Si sceglie di farlo nell'implementazione di esempio, perché la classe helper ha la responsabilità di essere proprietaria dell'istanza SpatialAnchorStore.

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>Esempio: relazione tra i sistemi di coordinate di ancoraggio e i sistemi di coordinate dei fotogrammi di riferimento stazionari

Supponiamo di avere un ancoraggio e di voler correlare un elemento nel sistema di coordinate dell'ancoraggio all'oggetto SpatialStationaryReferenceFrame già in uso per l'altro contenuto. Puoi usare [TryGetTransformTo](/uwp/api/Windows.Perception.Spatial.SpatialCoordinateSystem) per ottenere una trasformazione dal sistema di coordinate dell'ancoraggio a quello del fotogramma di riferimento zionario:

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

Questo processo è utile in due modi:
1. Indica se i due frame di riferimento possono essere compresi l'uno rispetto all'altro e;
2. In tal caso, fornisce una trasformazione per passare direttamente da un sistema di coordinate all'altro.

Con queste informazioni, si ha una conoscenza della relazione spaziale tra gli oggetti tra i due frame di riferimento.

Per il rendering, è spesso possibile ottenere risultati migliori raggruppando gli oggetti in base al frame o all'ancoraggio di riferimento originale. Eseguire un passaggio di disegno separato per ogni gruppo. Le matrici di visualizzazione sono più accurate per gli oggetti con trasformazioni del modello create inizialmente usando lo stesso sistema di coordinate.

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>Creare ologrammi usando una cornice di riferimento collegata al dispositivo

A volte si vuole eseguire il rendering [](../../design/coordinate-systems.md#attached-frame-of-reference) di un ologramma che rimane collegato alla posizione del dispositivo, ad esempio un pannello con informazioni di debug o un messaggio informativo quando il dispositivo è in grado di determinarne solo l'orientamento e non la posizione nello spazio. A tale scopo, viene utilizzato un frame di riferimento collegato.

La classe SpatialLocatorAttachedFrameOfReference definisce i sistemi di coordinate, che sono relativi al dispositivo anziché al mondo reale. Questo frame ha un'intestazione fissa rispetto all'ambiente circostante dell'utente che punta nella direzione verso cui l'utente si trovava quando è stato creato il frame di riferimento. Da quel punto in poi, tutti gli orientamenti in questo frame di riferimento sono relativi a tale intestazione fissa, anche quando l'utente ruota il dispositivo.

Ad HoloLens, l'origine del sistema di coordinate di questo frame si trova al centro della rotazione della testa dell'utente, in modo che la sua posizione non sia influenzata dalla rotazione della testa. L'app può specificare un offset rispetto a questo punto per posizionare gli ologrammi davanti all'utente.

Per ottenere un spatialLocatorAttachedFrameOfReference, usare la classe SpatialLocator e chiamare CreateAttachedFrameOfReferenceAtCurrentHeading.

Questo vale per l'intera gamma di Windows Mixed Reality dispositivi.

### <a name="use-a-reference-frame-attached-to-the-device"></a>Usare un frame di riferimento collegato al dispositivo

Queste sezioni descrivono cosa è stato modificato nel modello di app Windows Holographic per abilitare un frame di riferimento collegato al dispositivo usando questa API. Questo ologramma "collegato" funzionerà insieme agli ologrammi stazionari o ancorati e può essere usato anche quando il dispositivo non è temporaneamente in grado di trovare la sua posizione nel mondo.

In primo luogo, è stato modificato il modello per archiviare spatialLocatorAttachedFrameOfReference anziché SpatialStationaryFrameOfReference:

Da **HolographicTagAlongSampleMain.h:**

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

Da **HolographicTagAlongSampleMain.cpp:**

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

Durante l'aggiornamento, si ottiene ora il sistema di coordinate in corrispondenza del timestamp ottenuto da con la stima del fotogramma.

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>Ottenere una posizione dell'indicatore di misura spaziale e seguire lo sguardo dell'utente

Si vuole che l'ologramma di [](../../design/gaze-and-commit.md)esempio segua lo sguardo dell'utente, in modo simile a come la shell olografica può seguire lo sguardo dell'utente. A tale scopo, è necessario ottenere SpatialPointerPose dallo stesso timestamp.

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

Questo SpatialPointerPose contiene le informazioni necessarie per posizionare l'ologramma in base [all'intestazione corrente dell'utente.](gaze-in-directx.md)

Per il comfort dell'utente, viene utilizzata l'interpolazione lineare ("lerp") per uniformare la modifica della posizione in un periodo di tempo. Questa operazione è più comoda per l'utente rispetto al blocco dell'ologramma al proprio sguardo. Il lerping della posizione del tag lungo l'ologramma consente anche di stabilizzare l'ologramma smorzando il movimento. Se non fosse stato fatto questo smorzamento, l'utente dovrebbe vedere l'instabilità dell'ologramma a causa di ciò che in genere viene considerato un movimento impercettibile della testa dell'utente.

Da **StationaryQuadRenderer::P ositionHologram**:

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
>Nel caso di un pannello di debug, è possibile scegliere di riposizionare leggermente l'ologramma sul lato in modo che non ostrui la visualizzazione. Ecco un esempio di come eseguire questa operazione.

Per **StationaryQuadRenderer::P ositionHologram**:

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a>Ruotare l'ologramma per affrontare la fotocamera

Non è sufficiente posizionare l'ologramma, che in questo caso è un quad; È anche necessario ruotare l'oggetto per affrontare l'utente. Questa rotazione si verifica nello spazio mondiale, perché questo tipo di rotazione consente all'ologramma di rimanere parte dell'ambiente dell'utente. L'accesso allo spazio di visualizzazione non è così comodo perché l'ologramma viene bloccato in base all'orientamento dello schermo; In tal caso, sarebbe anche necessario eseguire l'interpolazione tra le matrici di visualizzazione sinistra e destra per acquisire una trasformazione del pannello dello spazio di visualizzazione che non interrompa il rendering stereo. Qui si ruotano gli assi X e Z per affrontare l'utente.

Da **StationaryQuadRenderer::Update**:

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a>Eseguire il rendering dell'ologramma collegato

Per questo esempio, si sceglie anche di eseguire il rendering dell'ologramma nel sistema di coordinate di SpatialLocatorAttachedReferenceFrame, dove è stato posizionato l'ologramma. Se si fosse deciso di eseguire il rendering usando un altro sistema di coordinate, sarebbe stato necessario acquisire una trasformazione dal sistema di coordinate del frame di riferimento collegato al dispositivo a tale sistema di coordinate.

Da **HolographicTagAlongSampleMain::Render**:

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

Questo è tutto. L'ologramma ora "insegue" una posizione di 2 metri davanti alla direzione dello sguardo dell'utente.

>[!NOTE]
>Questo esempio carica anche contenuto aggiuntivo. Vedere StationaryQuadRenderer.cpp.

## <a name="handling-tracking-loss"></a>Gestione della perdita di rilevamento

Quando il dispositivo non è in grado di individuarsi nel mondo, l'app verifica la perdita. Windows Mixed Reality app devono essere in grado di gestire tali interruzioni al sistema di rilevamento posizionale. È possibile osservare queste interruzioni e creare risposte usando l'evento LocatabilityChanged nell'oggetto SpatialLocator predefinito.

Da **AppMain::SetHolographicSpace:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

Quando l'app riceve un evento LocatabilityChanged, può modificare il comportamento in base alle esigenze. Ad esempio, nello stato PositionalTrackingInhibited l'app può sospendere il normale funzionamento ed eseguire il rendering di un [ologramma](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) lungo il tag che visualizza un messaggio di avviso.

Il Windows di app Holographic viene fornito con un gestore LocatabilityChanged già creato automaticamente. Per impostazione predefinita, viene visualizzato un avviso nella console di debug quando il rilevamento posizionale non è disponibile. È possibile aggiungere codice a questo gestore per fornire una risposta in base alle esigenze dell'app.

Da **AppMain.cpp:**

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a>Mapping spaziale

Le [API di mapping](spatial-mapping-in-directx.md) spaziale usano i sistemi di coordinate per ottenere le trasformazioni del modello per le mesh di superficie.

## <a name="see-also"></a>Vedi anche
* [Sistemi di coordinate](../../design/coordinate-systems.md)
* [Ancoraggi nello spazio](../../design/spatial-anchors.md)
* <a href="/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* [Puntamento con la testa e sguardo fisso in DirectX](gaze-in-directx.md)
* [Mani e controller del movimento in DirectX](hands-and-motion-controllers-in-directx.md)
* [Mapping spaziale in DirectX](spatial-mapping-in-directx.md)