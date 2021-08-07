---
title: Ottenere un HolographicSpace
description: Informazioni su come usare l'API HolographicSpace per il rendering olografico e l'input spaziale nelle app di realtà mista.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, input spaziale, rendering, catena di scambio, frame olografico, ciclo di aggiornamento, ciclo di gioco, frame di riferimento, individuabilità, codice di esempio, procedura dettagliata, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 986ccdc6e81d1ac7c7b401a427da548218a68eb0352a0057bf7d7aba3c1d6d6a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212169"
---
# <a name="getting-a-holographicspace"></a>Ottenere un HolographicSpace

> [!NOTE]
> Questo articolo è correlato alle API native WinRT legacy.  Per i nuovi progetti di app native, è consigliabile usare **[l'API OpenXR](openxr-getting-started.md)**.

La <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">classe HolographicSpace</a> è il portale nel mondo olografico. Controlla il rendering immersivo, fornisce i dati della fotocamera e fornisce l'accesso alle API di ragionamento spaziale. Ne creerai uno per <a href="/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> dell'app UWP o HWND dell'app Win32.

## <a name="set-up-the-holographic-space"></a>Configurare lo spazio olografico

La creazione dell'oggetto spazio olografico è il primo passaggio per creare l Windows Mixed Reality app. Le Windows tradizionali eseguono il rendering in una catena di scambio Direct3D creata per la finestra principale della visualizzazione dell'applicazione. Questa catena di scambio viene visualizzata in uno slate nell'interfaccia utente olografica. Per rendere olografica la visualizzazione dell'applicazione anziché uno slate 2D, creare uno spazio olografico per la finestra principale anziché una catena di scambio. La presentazione di fotogrammi olografici creati da questo spazio olografico attiva la modalità di rendering a schermo intero dell'app.

Per **un'app UWP** a partire dal modello app [ *Holographic DirectX 11 (Universal Windows),*](creating-a-holographic-directx-project.md)cercare questo codice nel metodo **SetWindow** in AppView.cpp:

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

Se si sta creando **un'app Win32** a partire dall'esempio [ *BasicHologram* Win32,](creating-a-holographic-directx-project.md#creating-a-win32-project)vedere **App::CreateWindowAndHolographicSpace** per un esempio di HWND. È quindi possibile convertirlo in un HWND immersivo creando un <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">oggetto HolographicSpace associato:</a>

```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

Dopo aver ottenuto un holographicSpace per il CoreWindow UWP o Win32 HWND, HolographicSpace può gestire fotocamere olografiche, creare sistemi di coordinate ed eseguire il rendering olografico. Lo spazio olografico corrente viene usato in più posizioni nel modello DirectX:
* La **classe DeviceResources** deve ottenere alcune informazioni dall'oggetto HolographicSpace per creare il dispositivo Direct3D. Si tratta dell'ID adattatore DXGI associato allo schermo olografico. La <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">classe HolographicSpace</a> usa il dispositivo Direct3D 11 dell'app per creare e gestire risorse basate su dispositivo, ad esempio i buffer indietro per ogni fotocamera olografica. Se si è interessati a vedere cosa fa questa funzione, è possibile trovarla in DeviceResources.cpp.
* La funzione **DeviceResources::InitializeUsingHolographicSpace** illustra come ottenere l'adattatore cercando il LUID e come scegliere un adattatore predefinito quando non viene specificato alcun adattatore preferito.
* La classe principale dell'app usa lo spazio olografico di **AppView::SetWindow** o **App::CreateWindowAndHolographicSpace** per gli aggiornamenti e il rendering.

>[!NOTE]
>Mentre le sezioni seguenti menzionano i nomi delle funzioni del modello come **AppView::SetWindow** che presuppongono che sia stato avviato dal modello di app UWP olografico, i frammenti di codice visualizzati verranno applicati in modo uniforme tra le app UWP e Win32.

Verrà ora approfondito il processo di configurazione di **cui SetHolographicSpace** è responsabile nella classe AppMain.

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>Sottoscrivere gli eventi della fotocamera, creare e rimuovere le risorse della fotocamera

Il contenuto olografico dell'app si trova nello spazio olografico e viene visualizzato tramite una o più fotocamere olografiche, che rappresentano prospettive diverse sulla scena. Ora che si dispone dello spazio olografico, è possibile ricevere i dati per le fotocamere olografiche.

L'app deve rispondere **agli eventi CameraAdded** creando tutte le risorse specifiche della fotocamera. Un esempio di questa risorsa è la visualizzazione della destinazione di rendering del buffer nascosto. È possibile visualizzare questo codice nella funzione **DeviceResources::SetHolographicSpace,** chiamata da **AppView::SetWindow** prima che l'app crei fotogrammi olografici:

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

L'app deve anche rispondere agli **eventi CameraRemoved** rilasciando le risorse create per la fotocamera.

Da **DeviceResources::SetHolographicSpace**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

I gestori eventi devono completare alcune operazioni per mantenere uniforme il rendering olografico e il rendering dell'app. Leggere il codice e i commenti per i dettagli: è possibile cercare **OnCameraAdded** e **OnCameraRemoved** nella classe principale per comprendere come la mappa **m_cameraResources** viene gestita **da DeviceResources**.

In questo momento, l'attenzione è incentrata su AppMain e sulla configurazione che esegue per consentire all'app di conoscere le fotocamere olografiche. A questo scopo, è importante prendere nota dei due requisiti seguenti:

1. Per il **gestore dell'evento CameraAdded,** l'app può funzionare in modo asincrono per completare la creazione delle risorse e il caricamento di asset per la nuova fotocamera olografica. Le app che richiedono più frame per completare questo lavoro devono richiedere un rinvio e completare il rinvio dopo il caricamento asincrono. [Un'attività PPL](/cpp/parallel/concrt/parallel-patterns-library-ppl) può essere usata per eseguire operazioni asincrone. L'app deve assicurarsi che sia pronta per il rendering immediatamente alla fotocamera quando esce dal gestore eventi o quando completa il rinvio. L'uscita dal gestore eventi o il completamento del rinvio indica al sistema che l'app è ora pronta per ricevere fotogrammi olografici con la fotocamera inclusa.

2. Quando l'app riceve un **evento CameraRemoved,** deve rilasciare tutti i riferimenti al buffer nascosto e uscire immediatamente dalla funzione. Sono incluse le visualizzazioni di destinazione del rendering e qualsiasi altra risorsa che potrebbe contenere un riferimento a [IDXGIResource](/windows/desktop/api/dxgi/nn-dxgi-idxgiresource). L'app deve anche assicurarsi che il buffer nascosto non sia collegato come destinazione di rendering, come illustrato in **CameraResources::ReleaseResourcesForBackBuffer**. Per velocizzare le operazioni, l'app può rilasciare il buffer nascosto e quindi avviare un'attività per completare in modo asincrono qualsiasi altro lavoro di down down per la fotocamera. Il modello di app olografica include un'attività PPL che è possibile usare a questo scopo.

>[!NOTE]
>Per determinare quando viene visualizzata una fotocamera aggiunta o rimossa nel fotogramma, usare le proprietà **HolographicFrame** [AddedCameras](/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) e [RemovedCameras.](/uwp/api/windows.graphics.holographic.holographicframe.removedcameras)

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Creare un frame di riferimento per il contenuto olografico

Il contenuto dell'app deve essere posizionato in un sistema [di coordinate spaziali](coordinate-systems-in-directx.md) per il rendering in HolographicSpace. Il sistema fornisce due frame di riferimento principali, che è possibile usare per stabilire un sistema di coordinate per gli ologrammi.

Esistono due tipi di fotogrammi di riferimento in Windows Holographic: i fotogrammi di riferimento collegati al dispositivo e i fotogrammi di riferimento che rimangono stazionari mentre il dispositivo si sposta attraverso l'ambiente dell'utente. Per impostazione predefinita, il modello di app olografica usa un frame di riferimento zionario. questo è uno dei modi più semplici per eseguire il rendering di ologrammi bloccati dal mondo.

I fotogrammi di riferimento stazionari sono progettati per stabilizzare le posizioni vicino alla posizione corrente del dispositivo. Ciò significa che le coordinate più lontano dal dispositivo possono derivare leggermente rispetto all'ambiente dell'utente mentre il dispositivo apprende di più sullo spazio che lo circonda. Esistono due modi per creare un frame di riferimento zionario: acquisire il sistema di coordinate dalla fase spaziale o usare <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">l'oggetto SpatialLocator predefinito.</a> [](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage) Se si crea un'app Windows Mixed Reality visore immersive, il punto di partenza consigliato è la [fase spaziale](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage). La fase spaziale fornisce anche informazioni sulle funzionalità del visore immersivo indossato dal giocatore. Qui viene illustrato come usare <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">l'oggetto SpatialLocator predefinito.</a>

Il localizzatore spaziale rappresenta il Windows Mixed Reality e tiene traccia del movimento del dispositivo e fornisce sistemi di coordinate che possono essere compresi in relazione alla relativa posizione.

Da **AppMain::OnHolographicDisplayIsAvailableChanged**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

Creare il frame di riferimento zionario una volta all'avvio dell'app. Questo è analogo alla definizione di un sistema di coordinate del mondo, con l'origine posizionata nella posizione del dispositivo all'avvio dell'app. Questo frame di riferimento non si sposta con il dispositivo.

Da **AppMain::SetHolographicSpace**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

Tutti i fotogrammi di riferimento sono allineati alla gravità, vale a dire che l'asse y punta verso l'alto in relazione all'ambiente dell'utente. Poiché Windows usa sistemi di coordinate "a destra", la direzione dell'asse –z coincide con la direzione "in avanti" rivolta verso il dispositivo quando viene creato il frame di riferimento.

>[!NOTE]
>Quando l'app richiede una posizione precisa di singoli ologrammi, usare <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">spatialAnchor</a> per ancorare il singolo ologramma a una posizione nel mondo reale. Ad esempio, usare un ancoraggio spaziale quando l'utente indica che un punto è di particolare interesse. Le posizioni di ancoraggio non si spostano, ma possono essere regolate. Per impostazione predefinita, quando un ancoraggio viene regolato, facilita la posizione nei fotogrammi successivi dopo la correzione. A seconda dell'applicazione, in questo caso può essere necessario gestire la regolazione in modo diverso, ad esempio rinviandola fino a quando l'ologramma non è visualizzato. La <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">proprietà RawCoordinateSystem</a> e gli <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">eventi RawCoordinateSystemAdjusted</a> abilitano queste personalizzazioni.

## <a name="respond-to-locatability-changed-events"></a>Rispondere agli eventi modificati di individuazione

Per il rendering di ologrammi bloccati in tutto il mondo, il dispositivo deve individuare se stesso nel mondo. Ciò potrebbe non essere sempre possibile a causa di condizioni ambientali e, in tal caso, l'utente potrebbe aspettarsi un'indicazione visiva dell'interruzione del rilevamento. È necessario eseguire il rendering di questa indicazione visiva usando fotogrammi di riferimento collegati al dispositivo, anziché stazionari al mondo.

L'app può richiedere di ricevere una notifica se il rilevamento viene interrotto per qualsiasi motivo. Registrarsi per l'evento LocatabilityChanged per rilevare quando cambia la capacità del dispositivo di individuarsi nel mondo. Da **AppMain::SetHolographicSpace:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

Usare quindi questo evento per determinare quando non è possibile eseguire il rendering di ologrammi stazionari nel mondo.

## <a name="see-also"></a>Vedi anche
* [Rendering in DirectX](rendering-in-directx.md)
* [Sistemi di coordinate in DirectX](coordinate-systems-in-directx.md)