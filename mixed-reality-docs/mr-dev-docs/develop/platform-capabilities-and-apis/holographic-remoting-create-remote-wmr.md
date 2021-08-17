---
title: Scrittura di un'app remota Holographic Remoting (WMR)
description: Informazioni su come trasmettere il contenuto remoto di cui è stato eseguito il rendering in un computer HoloLens 2 con app Holographic Remoting con HolographicSpace.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Comunicazione remota, Holographic Remoting, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, NuGet
ms.openlocfilehash: 0c5943ff92ce797e39ec0d2d98c129fa91eb3f14
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184722"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a>Scrittura di un'app remota Holographic Remoting con l'API HolographicSpace

>[!IMPORTANT]
>Questo documento descrive la creazione di un'applicazione remota per HoloLens 2 [l'API HolographicSpace](../native/getting-a-holographicspace.md). Le applicazioni remote **per HoloLens (prima generazione)** devono usare NuGet pacchetto **1.x.x.** Ciò implica che le applicazioni remote scritte per HoloLens 2 non sono compatibili con HoloLens 1 e viceversa. La documentazione per HoloLens 1 è disponibile [qui.](add-holographic-remoting.md)

Le app holographic Remoting possono trasmettere contenuto sottoposto a rendering remoto HoloLens 2 e Windows Mixed Reality visori VR immersive. È anche possibile accedere a più risorse di sistema e integrare [visualizzazioni immersive remote](../../design/app-views.md) nel software per PC desktop esistente. Un'app remota riceve un flusso di dati di input da HoloLens 2, esegue il rendering del contenuto in una visualizzazione immersiva virtuale e trasmettere i frame di contenuto a HoloLens 2. La connessione viene stabilita usando il Wi-Fi standard. Holographic Remoting viene aggiunto a un'app desktop o UWP tramite NuGet pacchetto. È necessario codice aggiuntivo che gestisce la connessione ed esegue il rendering in una visualizzazione immersiva. Una tipica connessione remota avrà fino a 50 ms di latenza. L'app lettore può segnalare la latenza in tempo reale.

Tutto il codice in questa pagina e i progetti di lavoro sono disponibili nel repository GitHub degli esempi di [Holographic Remoting.](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)

## <a name="prerequisites"></a>Prerequisiti

Un buon punto di partenza è un'app desktop o UWP basata su DirectX funzionante, destinata [all'API HolographicSpace.](../native/getting-a-holographicspace.md) Per informazioni dettagliate, [vedere Panoramica dello sviluppo DirectX.](../native/directx-development-overview.md) Il [modello di progetto olografico C++](../native/creating-a-holographic-directx-project.md) è un buon punto di partenza.

>[!IMPORTANT]
>Tutte le app che usano Holographic Remoting devono essere scritte per usare un [apartment multi-thread.](/windows/win32/com/multithreaded-apartments) L'uso di [un apartment](/windows/win32/com/single-threaded-apartments) a thread singolo è supportato, ma può causare prestazioni non ottimali ed eventualmente stuttering durante la riproduzione. Quando si usa C++/WinRT [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) apartment multi-thread è l'impostazione predefinita.



## <a name="get-the-holographic-remoting-nuget-package"></a>Ottenere il pacchetto di NuGet Holographic Remoting

I passaggi seguenti sono necessari per aggiungere il pacchetto NuGet a un progetto in Visual Studio.
1. Aprire il progetto in Visual Studio.
2. Fare clic con il pulsante destro del mouse sul nodo **del progetto e scegliere Gestisci NuGet pacchetti...**
3. Nel pannello visualizzato selezionare **Sfoglia** e quindi cercare "Holographic Remoting".
4. Selezionare **Microsoft.Holographic.Remoting,** assicurarsi di selezionare la versione **2.x.x** più recente e selezionare **Installa.**
5. Se viene **visualizzata la** finestra di dialogo Anteprima, selezionare **OK.**
6. Selezionare **Accetto quando** viene visualizzata la finestra di dialogo del contratto di licenza.

>[!NOTE]
>La **versione 1.x.x** del pacchetto NuGet è ancora disponibile per gli sviluppatori che vogliono usare come destinazione HoloLens 1. Per informazioni [dettagliate, vedere Aggiungere Holographic Remoting (HoloLens (prima generazione)).](add-holographic-remoting.md)

## <a name="create-the-remote-context"></a>Creare il contesto remoto

Come primo passaggio, l'applicazione deve creare un contesto remoto.

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
>Holographic Remoting sostituisce il runtime Windows Mixed Reality che fa parte di Windows con un runtime specifico della comunicazione remota. Questa operazione viene eseguita durante la creazione del contesto remoto. Per questo motivo qualsiasi chiamata a qualsiasi API Windows Mixed Reality prima di creare il contesto remoto può comportare un comportamento imprevisto. L'approccio consigliato consiste nel creare il contesto remoto il prima possibile prima dell'interazione con qualsiasi API di realtà mista. Non combinare mai oggetti creati o recuperati tramite un'API Windows Mixed Reality prima della chiamata a CreateRemoteContext con oggetti creati o recuperati in un secondo momento.

Successivamente, è necessario creare lo spazio olografico. Non è necessario specificare un oggetto CoreWindow. Le app desktop che non hanno CoreWindow possono semplicemente passare un ```nullptr``` oggetto .

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>Connessione al dispositivo

Quando l'app remota è pronta per il rendering del contenuto, è possibile stabilire una connessione al dispositivo lettore.

La connessione può essere eseguita in uno dei due modi seguenti.
1) L'app remota si connette al lettore in esecuzione nel dispositivo.
2) Il lettore in esecuzione nel dispositivo si connette all'app remota.

Per stabilire una connessione dall'app remota al dispositivo lettore, chiamare il metodo nel contesto remoto ```Connect``` specificando il nome host e la porta. La porta usata da Holographic Remoting Player è **8265.**

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>Come per qualsiasi API C++/WinRT, può generare un'eccezione ```Connect``` winrt::hresult_error che deve essere gestita.

>[!TIP]
>Per evitare di usare la proiezione del linguaggio [C++/WinRT,](/windows/uwp/cpp-and-winrt-apis/) è possibile includere il file all'interno del NuGet ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` holographic Remoting. Contiene le dichiarazioni delle interfacce COM sottostanti. È tuttavia consigliabile usare C++/WinRT.

L'ascolto delle connessioni in ingresso nell'app remota può essere eseguito chiamando il ```Listen``` metodo . Durante questa chiamata è possibile specificare sia la porta dell'handshake che la porta di trasporto. La porta dell'handshake viene usata per l'handshake iniziale. I dati vengono quindi inviati sulla porta di trasporto. Per impostazione predefinita, vengono usati **8265** e **8266.**

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```All'interno del NuGet contiene la documentazione dettagliata per l'API esposta da Holographic Remoting.

## <a name="handling-remoting-specific-events"></a>Gestione di eventi specifici della comunicazione remota

Il contesto remoto espone tre eventi, che sono importanti per monitorare lo stato di una connessione.
1) OnConnected: attivata quando viene stabilita una connessione al dispositivo.
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) OnDisconnected: attivata se una connessione stabilita viene chiusa o non è stato possibile stabilire una connessione.
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) OnListening: quando viene avviato l'ascolto delle connessioni in ingresso.
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

È anche possibile eseguire query sullo stato della connessione usando ```ConnectionState``` la proprietà nel contesto remoto.
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>Gestione degli eventi vocali

Usando l'interfaccia di riconoscimento vocale remoto è possibile registrare i trigger di riconoscimento vocale con HoloLens 2 e fare in modo che i trigger di riconoscimento vocale si sviino all'applicazione remota.

Questo membro aggiuntivo è necessario per tenere traccia dello stato della voce remota.

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

Prima di tutto è necessario recuperare l'interfaccia di riconoscimento vocale remoto.

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

Usando un metodo helper asincrono è quindi possibile inizializzare la voce remota. Questa operazione deve essere eseguita in modo asincrono perché l'inizializzazione potrebbe richiedere una notevole quantità di tempo. [La concorrenza e le operazioni asincrone con C++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency) illustrano come creare funzioni asincrone con C++/WinRT.

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

Esistono due modi per specificare le frasi da riconoscere.
1) Specifica all'interno di un file XML della grammatica vocale. Per [informazioni dettagliate, vedere Come creare una grammatica XML](/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) di base.
2) Specificarli passandoli all'interno del vettore del dizionario a ```ApplyParameters``` .

All'interno del callback OnRecognizedSpeech, gli eventi vocali possono quindi essere elaborati:

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a>Anteprima del contenuto trasmesso in streaming in locale

Per visualizzare lo stesso contenuto nell'app remota che viene inviato al dispositivo, è possibile usare l'evento del ```OnSendFrame``` contesto remoto. ```OnSendFrame```L'evento viene attivato ogni volta che la libreria Holographic Remoting invia il frame corrente al dispositivo remoto. Questo è il momento ideale per portare il contenuto e anche b blit nella finestra desktop o UWP.

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a>Depth Reprojection

A partire dalla [versione 2.1.0,](holographic-remoting-version-history.md#v2.1.0)Holographic Remoting supporta [depth reprojection.](hologram-stability.md#reprojection) A questo scopo, è necessario che il buffer dei colori e il buffer di profondità siano trasmessi dall'applicazione remota al HoloLens 2. Per impostazione predefinita, il flusso del buffer di profondità è abilitato e configurato in modo da usare la metà della risoluzione del buffer dei colori. Questa impostazione può essere modificata nel modo seguente:

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

Si noti che se i valori predefiniti non devono essere usati, è necessario chiamare prima ```ConfigureDepthVideoStream``` di stabilire una connessione al HoloLens 2. La posizione migliore è subito dopo aver creato il contesto remoto. I valori possibili per DepthBufferStreamResolution sono:

* Full_Resolution
* Half_Resolution
* Quarter_Resolution
* Disabilitato (aggiunto con la [versione 2.1.3](holographic-remoting-version-history.md#v2.1.3) e, se usato, non viene creato alcun flusso video di profondità aggiuntivo)

Tenere presente che l'uso di un buffer di profondità della risoluzione completa influisce anche sui requisiti di larghezza di banda e deve essere in considerazione nel valore massimo della larghezza di banda fornito a ```CreateRemoteContext``` .

Oltre a configurare la risoluzione, è anche necessario eseguire il commit di un buffer di profondità [tramite HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

Per verificare se la nuovaproiezione della profondità funziona correttamente HoloLens 2, è possibile abilitare un visualizzatore di profondità tramite il Portale di dispositivi. Per [informazioni dettagliate, vedere Verifying Depth is Set Correctly](hologram-stability.md#verifying-depth-is-set-correctly) (Verifica che la profondità sia impostata correttamente).

## <a name="optional-custom-data-channels"></a>Facoltativo: canali di dati personalizzati

I canali di dati personalizzati possono essere usati per inviare dati utente tramite la connessione remota già stabilita. Per [altre informazioni, vedere canali](holographic-remoting-custom-data-channels.md) di dati personalizzati.

## <a name="see-also"></a>Vedere anche
* [Panoramica di Holographic Remoting](holographic-remoting-overview.md)
* [Scrivere un'app lettore Holographic Remoting personalizzata](holographic-remoting-create-player.md)
* [Canali di dati di Holographic Remoting personalizzati](holographic-remoting-custom-data-channels.md)
* [Stabilire una connessione sicura con Holographic Remoting](holographic-remoting-secure-connection.md)
* [Risoluzione dei problemi e limitazioni di Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)