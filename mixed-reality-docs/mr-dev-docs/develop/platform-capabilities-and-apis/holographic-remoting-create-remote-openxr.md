---
title: Scrittura di un'app remota Holographic Remoting (OpenXR)
description: Informazioni su come trasmettere il contenuto remoto sottoposto a rendering in un computer remoto per HoloLens 2 app holographic Remoting con OpenXR.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Comunicazione remota, Holographic Remoting, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, NuGet
ms.openlocfilehash: 3fd210db1b179cbceff057e25bf451be0e7ca843
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184592"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a>Scrittura di un'app remota Holographic Remoting con l'API OpenXR

>[!IMPORTANT]
>Questo documento descrive la creazione di un'applicazione remota per HoloLens 2 e Windows Mixed Reality visori con [l'API OpenXR](../native/openxr.md). Le applicazioni remote **per HoloLens (prima generazione)** devono usare NuGet pacchetto **1.x.x**. Ciò implica che le applicazioni remote scritte per HoloLens 2 non sono compatibili con HoloLens 1 e viceversa. La documentazione per HoloLens 1 è disponibile [qui.](add-holographic-remoting.md)

Le app holographic Remoting possono trasmettere contenuti sottoposti a rendering remoto HoloLens 2 e Windows Mixed Reality visori immersivi. È anche possibile accedere a più risorse di sistema e integrare [visualizzazioni immersive remote](../../design/app-views.md) nel software per PC desktop esistente. Un'app remota riceve un flusso di dati di input da HoloLens 2, esegue il rendering del contenuto in una visualizzazione immersiva virtuale e esegue il flusso di frame di contenuto HoloLens 2. La connessione viene stabilita usando il Wi-Fi standard. Holographic Remoting viene aggiunto a un'app desktop o UWP tramite NuGet pacchetto. È necessario codice aggiuntivo che gestisce la connessione ed esegue il rendering in una visualizzazione immersiva. Una connessione remota tipica avrà fino a 50 ms di latenza. L'app lettore può segnalare la latenza in tempo reale.

Tutto il codice in questa pagina e i progetti di lavoro sono disponibili nel repository github degli esempi [di Holographic Remoting.](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)

## <a name="prerequisites"></a>Prerequisiti

Un buon punto di partenza è un'app desktop o UWP basata su OpenXR funzionante. Per informazioni [dettagliate, vedere Introduzione a OpenXR.](../native/openxr-getting-started.md)

>[!IMPORTANT]
>Tutte le app che usano Holographic Remoting devono essere scritte per usare un [apartment multi-thread.](/windows/win32/com/multithreaded-apartments) L'uso di [un apartment](/windows/win32/com/single-threaded-apartments) a thread singolo è supportato, ma condurrà a prestazioni non ottimali ed eventualmente a uno stub durante la riproduzione. Quando si usa C++/WinRT [winrt::init_apartment'impostazione](/windows/uwp/cpp-and-winrt-apis/get-started) predefinita è un apartment multi-thread.

## <a name="get-the-holographic-remoting-nuget-package"></a>Ottenere il pacchetto NuGet Holographic Remoting

I passaggi seguenti sono necessari per aggiungere il pacchetto NuGet a un progetto in Visual Studio.
1. Aprire il progetto in Visual Studio.
2. Fare clic con il pulsante destro del mouse sul nodo del **progetto e scegliere Gestisci NuGet pacchetti...**
3. Nel pannello visualizzato selezionare **Sfoglia** e quindi cercare "Holographic Remoting".
4. Selezionare **Microsoft.Holographic.Remoting.OpenXr,** assicurarsi di selezionare la versione **2.x.x** più recente e selezionare **Installa**.
5. Se viene **visualizzata la** finestra di dialogo Anteprima, selezionare **OK.**
6. Selezionare **Accetto quando** viene visualizzata la finestra di dialogo del contratto di licenza.
7. Ripetere i passaggi da 3 a 6 per i NuGet seguenti: OpenXR.Headers, OpenXR.Loader

>[!NOTE]
>La **versione 1.x.x** del pacchetto NuGet è ancora disponibile per gli sviluppatori che vogliono usare come destinazione HoloLens 1. Per informazioni [dettagliate, vedere Add Holographic Remoting (HoloLens (1st gen)).](add-holographic-remoting.md)

## <a name="select-the-holographic-remoting-openxr-runtime"></a>Selezionare il runtime OpenXR di Holographic Remoting

Il primo passaggio da eseguire nell'app remota consiste nel selezionare il runtime OpenXR holographic Remoting, che fa parte del pacchetto di NuGet Microsoft.Holographic.Remoting.OpenXr. A tale scopo, impostare la variabile di ambiente sul percorso del RemotingXR.js```XR_RUNTIME_JSON``` nel file all'interno dell'app. Questa variabile di ambiente viene usata dal caricatore OpenXR per non usare il runtime OpenXR predefinito del sistema, ma per reindirizzare al runtime OpenXR holographic Remoting. Quando si usa il pacchetto di NuGet Microsoft.Holographic.Remoting.OpenXr il RemotingXR.jsnel file viene copiato automaticamente durante la compilazione nella cartella di output, la selezione del runtime OpenXR ha in genere l'aspetto seguente.

```cpp
bool EnableRemotingXR() {
    wchar_t executablePath[MAX_PATH];
    if (GetModuleFileNameW(NULL, executablePath, ARRAYSIZE(executablePath)) == 0) {
        return false;
    }
    
    std::filesystem::path filename(executablePath);
    filename = filename.replace_filename("RemotingXR.json");

    if (std::filesystem::exists(filename)) {
        SetEnvironmentVariableW(L"XR_RUNTIME_JSON", filename.c_str());
            return true;
        }

    return false;
}
```

## <a name="create-xrinstance-with-holographic-remoting-extension"></a>Creare XrInstance con l'estensione Holographic Remoting

Il primo passaggio che una tipica app OpenXR deve eseguire è selezionare le estensioni OpenXR e creare una XrInstance. La specifica di base OpenXR non fornisce alcuna API specifica per la comunicazione remota. Per questo motivo Holographic Remoting introduce la propria estensione OpenXR denominata ```XR_MSFT_holographic_remoting``` . Assicurarsi che quando si chiama xrCreateInstance ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` sia incluso in XrInstanceCreateInfo.

>[!TIP]
>Per impostazione predefinita, il contenuto sottoposto a rendering dell'app viene trasmesso solo al lettore Holographic Remoting in esecuzione in un HoloLens 2 o in un visore Windows Mixed Reality visori. Per visualizzare anche il contenuto sottoposto a rendering nel PC remoto, ad esempio tramite una catena di scambio di una finestra, Holographic Remoting fornisce una seconda estensione OpenXR denominata ```XR_MSFT_holographic_remoting_frame_mirroring``` . Assicurarsi di abilitare anche questa estensione usando nel caso ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` in cui si voglia usare tale funzionalità.

>[!IMPORTANT]
>Per altre informazioni sull'API di estensione OpenXR [](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) di Holographic Remoting, vedere la specifica disponibile nel repository GitHub degli esempi di [Holographic Remoting.](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)

## <a name="connect-to-the-device"></a>Connessione al dispositivo

Dopo che l'app remota ha creato XrInstance ed ha sottoposto a query XrSystemId tramite xrGetSystem, è possibile stabilire una connessione al dispositivo lettore.

>[!WARNING]
> Il runtime OpenXR di Holographic Remoting è in grado di fornire dati specifici del dispositivo, ad esempio configurazioni di visualizzazione o modalità di fusione dell'ambiente dopo che è stata stabilita una connessione. ```xrEnumerateViewConfigurations```, , , e forniscono valori predefiniti, corrispondenti a quanto si ottiene in genere se ci si connette a un lettore in esecuzione in un HoloLens 2, prima di ```xrEnumerateViewConfigurationViews``` ```xrGetViewConfigurationProperties``` essere completamente ```xrEnumerateEnvironmentBlendModes``` ```xrGetSystemProperties``` connessi.
È consigliabile non chiamare questi metodi prima che venga stabilita una connessione. Il suggerimento viene usato dopo che XrSession è stato creato correttamente e lo stato della sessione è almeno XR_SESSION_STATE_READY.

Le proprietà generali, ad esempio velocità in bit massima, audio abilitato, codec video o risoluzione del flusso del buffer di profondità, possono essere configurate ```xrRemotingSetContextPropertiesMSFT``` tramite come indicato di seguito.

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

La connessione può essere eseguita in uno dei due modi seguenti.
1) L'app remota si connette al lettore in esecuzione nel dispositivo.
2) Il lettore in esecuzione nel dispositivo si connette all'app remota.

Per stabilire una connessione dall'app remota al dispositivo lettore, chiamare il metodo specificando il nome host e la ```xrRemotingConnectMSFT``` porta tramite la struttura  ```XrRemotingConnectInfoMSFT``` . La porta usata da Holographic Remoting Player è **8265**.

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

L'ascolto delle connessioni in ingresso nell'app remota può essere eseguito chiamando il ```xrRemotingListenMSFT``` metodo . Sia la porta dell'handshake che la porta di trasporto possono essere specificate tramite la ```XrRemotingListenInfoMSFT``` struttura . La porta dell'handshake viene usata per l'handshake iniziale. I dati vengono quindi inviati sulla porta di trasporto. Per impostazione **predefinita vengono usati 8265** e **8266.**

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

Lo stato della connessione deve essere disconnesso quando si chiama ```xrRemotingConnectMSFT``` o ```xrRemotingListenMSFT``` . È possibile ottenere lo stato della connessione in qualsiasi momento dopo aver creato un oggetto XrInstance e aver sottoposto a query XrSystemId tramite ```xrRemotingGetConnectionStateMSFT``` .

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

Gli stati di connessione disponibili sono:
- XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT

>[!IMPORTANT]
> ```xrRemotingConnectMSFT``` o ```xrRemotingListenMSFT``` deve essere chiamato prima di provare a creare una sessione XrSession tramite xrCreateSession. Se si tenta di creare una sessione XrSession mentre lo stato della connessione è la creazione della sessione avrà esito positivo, ma lo stato della sessione verrà immediatamente ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` XR_SESSION_STATE_LOSS_PENDING.

L'implementazione di Holographic Remoting di ```xrCreateSession``` supporta l'attesa della connessione da stabilire. È possibile chiamare o immediatamente seguito da una chiamata a , che blocca e attende che ```xrRemotingConnectMSFT``` ```xrRemotingListenMSFT``` sia stabilita una connessione. Il timeout è fisso a 10 secondi. Se è possibile stabilire una connessione entro questo periodo, la creazione di XrSession avrà esito positivo e lo stato della sessione verrà XR_SESSION_STATE_READY. Nel caso in cui non sia possibile stabilire alcuna connessione, anche la creazione della sessione ha esito positivo, ma passa immediatamente alla XR_SESSION_STATE_LOSS_PENDING.

In generale, lo stato della connessione è associato allo stato XrSession. Qualsiasi modifica apportata allo stato della connessione influisce anche sullo stato della sessione. Ad esempio, se lo stato della connessione passa dallo stato della sessione allo stato sessione, verrà XR_SESSION_STATE_LOSS_PENDING `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` anche.

## <a name="handling-remoting-specific-events"></a>Gestione di eventi specifici della comunicazione remota

Il runtime OpenXR di Holographic Remoting espone tre eventi, che sono importanti per monitorare lo stato di una connessione.
1) ```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: attivato quando una connessione al dispositivo è stata stabilita correttamente.
2) ```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: attivato se una connessione stabilita viene chiusa o se non è stato possibile stabilire una connessione.
3) ```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: quando viene avviato l'ascolto delle connessioni in ingresso.

Questi eventi vengono inseriti in una coda e l'app remota deve leggere dalla coda con regolarità tramite ```xrPollEvent``` .

```cpp
auto pollEvent = [&](XrEventDataBuffer& eventData) -> bool {
    eventData.type = XR_TYPE_EVENT_DATA_BUFFER;
    eventData.next = nullptr;
    return CHECK_XRCMD(xrPollEvent(m_instance.Get(), &eventData)) == XR_SUCCESS;
};

XrEventDataBuffer eventData{};
while (pollEvent(eventData)) {
    switch (eventData.type) {
    
    ...
    
    case XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Listening on port %d",
                    reinterpret_cast<const XrRemotingEventDataListeningMSFT*>(&eventData)->listeningPort);
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Connected.");
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Disconnected - Reason: %d",
                    reinterpret_cast<const XrRemotingEventDataDisconnectedMSFT*>(&eventData)->disconnectReason);
        break;
    }
}
```

## <a name="preview-streamed-content-locally"></a>Anteprima del contenuto trasmesso in streaming in locale

Per visualizzare lo stesso contenuto nell'app remota che viene inviata al dispositivo, è possibile ```XR_MSFT_holographic_remoting_frame_mirroring``` usare l'estensione. Con questa estensione è possibile inviare una trama a xrEndFrame usando l'oggetto che non è concatenato a ```XrRemotingFrameMirrorImageInfoMSFT``` XrFrameEndInfo come indicato di seguito.

```cpp
XrFrameEndInfo frameEndInfo{XR_TYPE_FRAME_END_INFO};
...

XrRemotingFrameMirrorImageD3D11MSFT mirrorImageD3D11{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_D3D11_MSFT)};
mirrorImageD3D11.texture = m_window->GetNextSwapchainTexture();

XrRemotingFrameMirrorImageInfoMSFT mirrorImageEndInfo{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_INFO_MSFT)};
mirrorImageEndInfo.image = reinterpret_cast<const XrRemotingFrameMirrorImageBaseHeaderMSFT*>(&mirrorImageD3D11);

frameEndInfo.next = &mirrorImageEndInfo;

xrEndFrame(m_session.Get(), &frameEndInfo);

m_window->PresentSwapchain();
```

L'esempio precedente usa una trama della catena di scambio DX11 e presenta la finestra immediatamente dopo la chiamata a xrEndFrame. L'utilizzo non è limitato alle trame della catena di scambio e non è necessaria alcuna sincronizzazione GPU aggiuntiva. Per informazioni dettagliate sull'utilizzo e sui vincoli, vedere la specifica [dell'estensione](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).
Se l'app remota usa DX12, usare XrRemotingFrameMirrorImageD3D12MSFT anziché XrRemotingFrameMirrorImageD3D11MSFT.

## <a name="see-also"></a>Vedere anche
* [Panoramica della comunicazione remota olografica](holographic-remoting-overview.md)
* [Scrivere un'app lettore Holographic Remoting personalizzata](holographic-remoting-create-player.md)
* [Stabilire una connessione sicura con Holographic Remoting](holographic-remoting-secure-connection.md)
* [Risoluzione dei problemi e limitazioni di Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)