---
title: Scrittura di un'app remota olografica remota (OpenXR)
description: Informazioni su come trasmettere il rendering del contenuto remoto in un computer remoto a HoloLens 2 con app Remote Remoting con OpenXR.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica, auricolare realtà mista, cuffia a realtà mista di Windows, auricolare della realtà virtuale, NuGet
ms.openlocfilehash: da3114b2c8c4e04d8da9296687f92d0b23945281
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581238"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a>Scrittura di un'app remota di comunicazione remota olografica tramite l'API OpenXR

>[!IMPORTANT]
>Questo documento descrive la creazione di un'applicazione remota per gli auricolari HoloLens 2 e Windows Mixed Reality usando l' [API OpenXR](../native/openxr.md). Le applicazioni remote per **HoloLens (1a Gen)** devono usare il pacchetto NuGet versione **1. x. x**. Ciò implica che le applicazioni remote scritte per HoloLens 2 non sono compatibili con HoloLens 1 e viceversa. La documentazione per HoloLens 1 è disponibile [qui](add-holographic-remoting.md).

Le app di comunicazione remota olografica possono trasmettere contenuti con rendering remoto a HoloLens 2 e agli auricolari immersivi con la realtà mista di Windows. È inoltre possibile accedere a più risorse di sistema e integrare [visualizzazioni immersive](../../design/app-views.md) remote in software per PC desktop esistenti. Un'app remota riceve un flusso di dati di input da HoloLens 2, esegue il rendering del contenuto in una visualizzazione immersiva virtuale e trasmette nuovamente i frame di contenuto a HoloLens 2. La connessione viene eseguita usando il Wi-Fi standard. La comunicazione remota olografica viene aggiunta a un'app desktop o UWP tramite un pacchetto NuGet. È necessario codice aggiuntivo che gestisce la connessione e ne esegue il rendering in una visualizzazione immersiva. Una tipica connessione remota avrà una bassa di 50 ms di latenza. L'App Player può segnalare la latenza in tempo reale.

Tutto il codice in questa pagina e i progetti di lavoro sono disponibili nel [repository GitHub degli esempi di comunicazione remota olografica](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="prerequisites"></a>Prerequisiti

Un punto di partenza valido è un'app desktop o UWP funzionante basata su OpenXR. Per informazioni dettagliate, vedere la pagina relativa [all'introduzione a OpenXR](../native/openxr-getting-started.md).

>[!IMPORTANT]
>Qualsiasi app che usa la comunicazione remota olografica deve essere creata per usare un [Apartment](//windows/win32/com/multithreaded-apartments)multithread. L'uso di un [Apartment a thread singolo](//windows/win32/com/single-threaded-apartments) è supportato, ma comporta prestazioni ottimali e possibilmente balbettanti durante la riproduzione. Quando si usa C++/WinRT [WinRT:: init_apartment](//windows/uwp/cpp-and-winrt-apis/get-started) un apartment multithread è il valore predefinito.

## <a name="get-the-holographic-remoting-nuget-package"></a>Ottenere il pacchetto NuGet per la comunicazione remota olografica

I passaggi seguenti sono necessari per aggiungere il pacchetto NuGet a un progetto in Visual Studio.
1. Aprire il progetto in Visual Studio.
2. Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Gestisci pacchetti NuGet...**
3. Nel pannello visualizzato selezionare **Sfoglia** e quindi cercare "comunicazione remota olografica".
4. Selezionare **Microsoft. olografic. Remoting. OpenXr**, assicurarsi di selezionare la versione **2. x.** x più recente e selezionare **Installa**.
5. Se viene visualizzata la finestra di dialogo **Anteprima** , fare clic su **OK**.
6. Selezionare **Accetto** quando viene visualizzata la finestra di dialogo contratto di licenza.
7. Ripetere i passaggi da 3 a 6 per i pacchetti NuGet seguenti: OpenXR. Headers, OpenXR. loader

>[!NOTE]
>La versione **1. x.** x del pacchetto NuGet è ancora disponibile per gli sviluppatori che desiderano utilizzare HoloLens 1. Per informazioni dettagliate, vedere [aggiungere la comunicazione remota olografica (HoloLens (1st Gen))](add-holographic-remoting.md).

## <a name="select-the-holographic-remoting-openxr-runtime"></a>Selezionare il runtime OpenXR di comunicazione remota olografica

Il primo passaggio da eseguire nell'app remota consiste nel selezionare il runtime OpenXR di comunicazione remota olografica, che fa parte del pacchetto NuGet Microsoft. Olografic. Remoting. OpenXr. Questa operazione può essere eseguita impostando la ```XR_RUNTIME_JSON``` variabile di ambiente sul percorso del RemotingXR.jsnel file all'interno dell'app. Questa variabile di ambiente viene usata dal caricatore OpenXR per non usare il runtime OpenXR predefinito del sistema, ma viene invece reindirizzato al runtime OpenXR della comunicazione remota olografica. Quando si usa il pacchetto NuGet Microsoft. Olografic. Remoting. OpenXr, il RemotingXR.jsnel file viene copiato automaticamente durante la compilazione nella cartella di output, la selezione del runtime di OpenXR è in genere simile alla seguente.

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

## <a name="create-xrinstance-with-holographic-remoting-extension"></a>Creare XrInstance con estensione per la comunicazione remota olografica

Il primo passaggio di un'app OpenXR tipica consiste nel selezionare le estensioni OpenXR e creare un XrInstance. La specifica OpenXR Core non fornisce alcuna API per servizi remoti specifici. Per questo motivo, la comunicazione remota olografica introduce una propria estensione OpenXR denominata ```XR_MSFT_holographic_remoting``` . Assicurarsi che quando si chiama xrCreateInstance ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` sia incluso in XrInstanceCreateInfo.

>[!TIP]
>Per impostazione predefinita, il contenuto di cui è stato eseguito il rendering dell'app viene trasmesso solo al lettore di comunicazione remota olografico in esecuzione su un HoloLens 2 o su un headset di realtà mista di Windows. Per visualizzare anche il contenuto sottoposto a rendering nel computer remoto, tramite una catena di scambio di una finestra, ad esempio, la comunicazione remota olografica fornisce una seconda estensione OpenXR denominata ```XR_MSFT_holographic_remoting_frame_mirroring``` . Assicurarsi di abilitare anche questa estensione usando ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` nel caso in cui si desideri usare tale funzionalità.

>[!IMPORTANT]
>Per informazioni sull'API dell'estensione OpenXR per la comunicazione remota olografica, vedere la [specifica](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) che si trova nel [repository GitHub degli esempi di comunicazione remota olografica](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="connect-to-the-device"></a>Connetti al dispositivo

Dopo che l'app remota ha creato il XrInstance ed eseguito una query su XrSystemId tramite xrGetSystem, è possibile stabilire una connessione al dispositivo Player.

>[!WARNING]
> Il runtime OpenXR di comunicazione remota olografica è in grado di fornire solo i dati specifici del dispositivo, ad esempio le configurazioni della vista o le modalità di combinazione dell'ambiente dopo aver stabilito una connessione. ```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews``` , ```xrGetViewConfigurationProperties``` , ```xrEnumerateEnvironmentBlendModes``` e ```xrGetSystemProperties``` forniranno i valori predefiniti, corrispondenti a quello che in genere si ottiene se ci si connette a un lettore che esegue in un HoloLens 2, prima di essere completamente connessi.
Si consiglia vivamente di non chiamare questi metodi prima che sia stata stabilita una connessione. Il suggerimento viene usato questi metodi dopo che il XrSession è stato creato correttamente e lo stato della sessione è almeno XR_SESSION_STATE_READY.

È possibile configurare le proprietà generali come la velocità in bit massima, l'audio abilitato, il codec video o la risoluzione del flusso del buffer di profondità tramite ```xrRemotingSetContextPropertiesMSFT``` come indicato di seguito.

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
1) L'app remota si connette al lettore in esecuzione sul dispositivo.
2) Il lettore in esecuzione sul dispositivo si connette all'app remota.

Per stabilire una connessione dall'app remota al dispositivo Player, chiamare il ```xrRemotingConnectMSFT``` metodo specificando il nome host e la porta tramite la  ```XrRemotingConnectInfoMSFT``` struttura. La porta usata dal lettore di comunicazione remota olografica è **8265**.

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

L'ascolto delle connessioni in ingresso nell'app remota può essere eseguito chiamando il ```xrRemotingListenMSFT``` metodo. È possibile specificare sia la porta di handshake che la porta di trasporto tramite la ```XrRemotingListenInfoMSFT``` struttura. La porta di handshake viene utilizzata per l'handshake iniziale. I dati vengono quindi inviati tramite la porta di trasporto. Per impostazione predefinita vengono usati **8265** e **8266** .

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

Lo stato della connessione deve essere disconnesso quando si chiama ```xrRemotingConnectMSFT``` o ```xrRemotingListenMSFT``` . È possibile ottenere lo stato di connessione in qualsiasi momento dopo aver creato un XrInstance ed eseguito una query per XrSystemId tramite ```xrRemotingGetConnectionStateMSFT``` .

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

Gli Stati di connessione disponibili sono:
- XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT

>[!IMPORTANT]
> ```xrRemotingConnectMSFT``` oppure ```xrRemotingListenMSFT``` deve essere chiamato prima di provare a creare un XrSession tramite xrCreateSession. Se si tenta di creare un XrSession mentre lo stato della connessione è ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` la creazione della sessione avrà esito positivo, ma lo stato della sessione passerà immediatamente a XR_SESSION_STATE_LOSS_PENDING.

L'implementazione di comunicazione remota olografica ```xrCreateSession``` supporta l'attesa della creazione di una connessione. È possibile chiamare ```xrRemotingConnectMSFT``` o ```xrRemotingListenMSFT``` immediatamente seguito da una chiamata a, che blocca e attende che venga stabilita una connessione. Il timeout è fisso a 10 secondi. Se è possibile stabilire una connessione entro questo periodo di tempo, la creazione del XrSession avrà esito positivo e lo stato della sessione passerà a XR_SESSION_STATE_READY. Se non è possibile stabilire alcuna connessione, la creazione della sessione riesce anche ma passa immediatamente a XR_SESSION_STATE_LOSS_PENDING.

In generale, lo stato di connessione è coppia con lo stato XrSession. Qualsiasi modifica allo stato della connessione influisca anche sullo stato della sessione. Ad esempio, se lo stato della connessione passa da `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` a ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` stato sessione, passerà anche a XR_SESSION_STATE_LOSS_PENDING.

## <a name="handling-remoting-specific-events"></a>Gestione di eventi specifici della comunicazione remota

Il runtime OpenXR di comunicazione remota olografica espone tre eventi, che sono importanti per monitorare lo stato di una connessione.
1) ```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Attivato quando una connessione al dispositivo è stata stabilita correttamente.
2) ```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Attivato se una connessione stabilita è chiusa o non è stato possibile stabilire una connessione.
3) ```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: Quando viene avviata l'attesa delle connessioni in ingresso.

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

## <a name="preview-streamed-content-locally"></a>Anteprima del contenuto trasmesso localmente

Per visualizzare lo stesso contenuto nell'app remota inviata al dispositivo ```XR_MSFT_holographic_remoting_frame_mirroring``` , è possibile usare l'estensione. Con questa estensione, è possibile inviare una trama a xrEndFrame usando l'oggetto ```XrRemotingFrameMirrorImageInfoMSFT``` che non è concatenato a XrFrameEndInfo come indicato di seguito.

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

L'esempio precedente usa una trama a catena di scambio DX11 e visualizza la finestra immediatamente dopo la chiamata a xrEndFrame. L'utilizzo non è limitato alle trame a catena di scambio e non è necessaria alcuna sincronizzazione aggiuntiva della GPU. Per informazioni dettagliate sull'utilizzo e sui vincoli, vedere la [specifica dell'estensione](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).
Se l'app remota USA DX12, usare XrRemotingFrameMirrorImageD3D12MSFT anziché XrRemotingFrameMirrorImageD3D11MSFT.

## <a name="see-also"></a>Vedere anche
* [Scrivere un'app lettore Holographic Remoting personalizzata](holographic-remoting-create-player.md)
* [Stabilire una connessione sicura con Holographic Remoting](holographic-remoting-secure-connection.md)
* [Limitazioni e risoluzione dei problemi di comunicazione remota olografica](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)