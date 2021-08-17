---
title: Aggiungere la comunicazione remota olografica
description: Informazioni su come installare, configurare e usare Holographic Remoting per eseguire il rendering di ologrammi in HoloLens dispositivo in rete.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, ologrammi, comunicazione remota olografica, rendering remoto, rendering di rete, HoloLens, ologrammi remoti, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale
ms.openlocfilehash: 3f9d3d23d18f680ce1001310e4ce49089edaae6a
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184622"
---
# <a name="add-holographic-remoting-hololens-first-gen"></a>Aggiungere Holographic Remoting (HoloLens (prima generazione))

>[!IMPORTANT]
> Questo documento descrive la creazione di un'applicazione host per HoloLens 1. L'applicazione **host HoloLens (prima generazione)** deve usare NuGet pacchetto **1.x.x.** Ciò implica che le applicazioni host scritte per HoloLens 1 non sono compatibili con HoloLens 2 e viceversa.

## <a name="hololens-2"></a>HoloLens 2

HoloLens sviluppatori che usano Holographic Remoting dovranno aggiornare le app per renderle compatibili con HoloLens 2. Questa operazione richiede una nuova versione del pacchetto di NuGet Holographic Remoting. Assicurarsi di usare la versione 2.0.0.0 o successiva del pacchetto di NuGet Holographic Remoting quando ci si connette a Holographic Remoting Player in HoloLens 2, in caso di esito negativo della connessione.

>[!NOTE]
> Le indicazioni specifiche per HoloLens 2 sono disponibili [qui.](holographic-remoting-create-remote-wmr.md)


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Aggiungere la comunicazione remota olografica al desktop o all'app UWP

Questa pagina descrive come aggiungere Holographic Remoting a un'app desktop o UWP.

Holographic Remoting consente all'app di scegliere come destinazione un HoloLens con contenuto olografico ospitato in un PC desktop o in un dispositivo UWP, ad esempio il Xbox One. È anche possibile accedere a più risorse di sistema, rendendo possibile l'integrazione di visualizzazioni [immersive remote](../../design/app-views.md) nel software per PC desktop esistente. Un'app host remota riceve un flusso di dati di input da un HoloLens, esegue il rendering del contenuto in una visualizzazione immersiva virtuale e riporta i frame di contenuto a HoloLens. La connessione viene stabilita usando il Wi-Fi standard. Per usare la comunicazione remota, usa un pacchetto NuGet per aggiungere la comunicazione remota olografica al desktop o all'app UWP, quindi scrivi codice per gestire la connessione ed eseguire il rendering di una visualizzazione immersiva. Nell'esempio di codice sono incluse librerie helper che semplificano l'attività di gestione della connessione del dispositivo.

Una tipica connessione remota avrà fino a 50 ms di latenza. L'app lettore può segnalare la latenza in tempo reale.

>[!NOTE]
>I frammenti di codice in questo articolo illustrano attualmente l'uso di C++/CX anziché di C++17 conforme a C++/WinRT usato nel modello di progetto [olografico C++.](../native/creating-a-holographic-directx-project.md)  I concetti sono equivalenti per un progetto C++/WinRT, anche se dovrai tradurre il codice.

### <a name="get-the-remoting-nuget-packages"></a>Ottenere i pacchetti di NuGet remoti

Seguire questa procedura per ottenere il pacchetto NuGet per la comunicazione remota olografica e aggiungere un riferimento dal progetto:
1. Passare al progetto in Visual Studio.
2. Fare clic con il pulsante destro del mouse sul nodo del progetto **e scegliere Gestisci NuGet pacchetti...**
3. Nel pannello visualizzato selezionare Sfoglia  e quindi cercare "Holographic Remoting".
4. Selezionare **Microsoft.Holographic.Remoting** e selezionare **Installa**.
5. Se viene **visualizzata la** finestra di dialogo Anteprima, selezionare **OK.**
6. Selezionare **Accetto quando** viene visualizzata la finestra di dialogo del contratto di licenza.

### <a name="create-the-holographicstreamerhelpers"></a>Creare HolographicStreamerHelpers

Prima di tutto, è necessario aggiungere un'istanza di HolographicStreamerHelpers alla classe che gestirà la comunicazione remota.

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

È anche necessario tenere traccia dello stato della connessione. Se si vuole eseguire il rendering dell'anteprima, è necessario disporre di una trama in cui copiarla. Sono necessari anche alcuni elementi, ad esempio un blocco dello stato della connessione, un modo per archiviare l'indirizzo IP HoloLens e così via.

```cpp
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>Inizializzare HolographicStreamerHelpers e connettersi a HoloLens

Per connettersi a un HoloLens, creare un'istanza di HolographicStreamerHelpers e connettersi all'indirizzo IP di destinazione. È necessario impostare le dimensioni del fotogramma video in modo che corrispondano alla larghezza e all'altezza dello schermo HoloLens, perché la libreria Holographic Remoting prevede che le risoluzioni del codificatore e del decodificatore corrispondano esattamente.

```cpp
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

La connessione del dispositivo è asincrona. L'app deve fornire gestori eventi per gli eventi di connessione, disconnessione e invio di frame.

L'evento OnConnected può aggiornare l'interfaccia utente, avviare il rendering e così via. Nell'esempio di codice desktop il titolo della finestra viene aggiornato con un messaggio "connesso".

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

L'evento OnDisconnected può gestire la riconnessione, gli aggiornamenti dell'interfaccia utente e così via. In questo esempio viene riconnessa se si verifica un errore temporaneo.

```cpp
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

Quando il componente remoto è pronto per inviare un frame, l'app ha la possibilità di crearne una copia in SendFrameEvent. In questo caso, il frame viene copiato in una catena di scambio in modo da poterlo visualizzare in una finestra di anteprima.

```cpp
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a>Eseguire il rendering del contenuto olografico

Per eseguire il rendering del contenuto usando la comunicazione remota, configura un oggetto IFrameworkView virtuale all'interno dell'app desktop o UWP ed elabora i fotogrammi olografici dalla comunicazione remota. Tutte le API Windows olografica vengono usate nello stesso modo di questa visualizzazione, ma sono impostate in modo leggermente diverso.

Invece di crearli manualmente, i componenti dello spazio olografico e del parlato provengono dalla classe HolographicRemotingHelpers:

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Invece di usare un ciclo di aggiornamento in un metodo Run, fornisci aggiornamenti tick dal ciclo principale dell'app desktop o UWP. Ciò consente all'app desktop o UWP di mantenere il controllo dell'elaborazione dei messaggi.

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

Il metodo Tick() della visualizzazione app olografica completa un'iterazione del ciclo di aggiornamento, disegno e presentazione.

```cpp
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

L'aggiornamento, il rendering e il ciclo di visualizzazione dell'app olografica sono esattamente uguali a quelli dell'esecuzione in HoloLens, ad eccezione del fatto che si ha accesso a una quantità molto maggiore di risorse di sistema nel PC desktop. È possibile eseguire il rendering di molti più triangoli, avere più passaggi di disegno, eseguire più fisicamente e usare processi x64 per caricare contenuto che richiede più di 2 GB di RAM.

### <a name="disconnect-and-end-the-remote-session"></a>Disconnettere e terminare la sessione remota

Per disconnettersi, ad esempio quando l'utente fa clic su un pulsante dell'interfaccia utente per disconnettersi, chiamare Disconnect() su HolographicStreamerHelpers e quindi rilasciare l'oggetto.

```cpp
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a>Ottenere il lettore remoto

Il Windows holographic remoting è disponibile nell'App Store di Windows come endpoint per le app host remote a cui connettersi. Per ottenere il lettore Windows holographic remoting, visitare l'App Store di Windows dal HoloLens, cercare Servizi remoti e scaricare l'app. Il lettore remoto include una funzionalità per visualizzare le statistiche sullo schermo, che può essere utile durante il debug di app host remote.

## <a name="notes-and-resources"></a>Note e risorse

La visualizzazione dell'app olografica avrà bisogno di un modo per fornire all'app il dispositivo Direct3D, che deve essere usato per inizializzare lo spazio olografico. L'app deve usare questo dispositivo Direct3D per copiare e visualizzare il frame di anteprima.

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**Esempio di codice:** È disponibile un esempio di [codice holographic Remoting](https://github.com/Microsoft/HoloLensCompanionKit) completo, che include una visualizzazione applicazione olografica compatibile con i progetti host remoti e remoti per Desktop Win32, UWP DirectX e UWP con XAML. 

**Nota sul debug:** La libreria Holographic Remoting può generare eccezioni first-chance. Queste eccezioni possono essere visibili nelle sessioni di debug, a seconda Visual Studio delle eccezioni attive al momento. Queste eccezioni vengono intercette internamente dalla libreria Holographic Remoting e possono essere ignorate.

## <a name="see-also"></a>Vedere anche
* [Panoramica di Holographic Remoting](holographic-remoting-overview.md)
* [Scrivere un'app lettore Holographic Remoting personalizzata](holographic-remoting-create-player.md)
* [Stabilire una connessione sicura con Holographic Remoting](holographic-remoting-secure-connection.md)
* [Risoluzione dei problemi e limitazioni di Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)