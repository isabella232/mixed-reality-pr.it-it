---
title: Aggiungere la comunicazione remota olografica
description: Viene illustrato come usare la comunicazione remota olografica per eseguire il rendering degli ologrammi in una HoloLens in rete.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, comunicazione remota olografica, rendering remoto, rendering di rete, HoloLens, ologrammi remoti, cuffie per realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 809258d3387b5e45885c0eb207544c176f891a1d
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530304"
---
# <a name="add-holographic-remoting-hololens-first-gen"></a><span data-ttu-id="cface-104">Aggiungere la comunicazione remota olografica (HoloLens (First Gen))</span><span class="sxs-lookup"><span data-stu-id="cface-104">Add Holographic Remoting (HoloLens (first gen))</span></span>

>[!IMPORTANT]
> <span data-ttu-id="cface-105">Questo documento descrive la creazione di un'applicazione host per HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="cface-105">This document describes the creation of a host application for HoloLens 1.</span></span> <span data-ttu-id="cface-106">L'applicazione host per **HoloLens (1st Gen)** deve usare il pacchetto NuGet versione **1. x. x**.</span><span class="sxs-lookup"><span data-stu-id="cface-106">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="cface-107">Ciò implica che le applicazioni host scritte per HoloLens 1 non sono compatibili con HoloLens 2 e viceversa.</span><span class="sxs-lookup"><span data-stu-id="cface-107">This implies that host applications written for HoloLens 1 are not compatible with HoloLens 2 and vice versa.</span></span>

## <a name="hololens-2"></a><span data-ttu-id="cface-108">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="cface-108">HoloLens 2</span></span>

<span data-ttu-id="cface-109">Gli sviluppatori HoloLens che usano la comunicazione remota olografica dovranno aggiornare le proprie app per renderle compatibili con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cface-109">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span> <span data-ttu-id="cface-110">Questa operazione richiede una nuova versione del pacchetto NuGet di comunicazione remota olografica.</span><span class="sxs-lookup"><span data-stu-id="cface-110">This requires a new version of the Holographic Remoting NuGet package.</span></span> <span data-ttu-id="cface-111">Assicurarsi di usare la versione 2.0.0.0 o successiva del pacchetto NuGet per la comunicazione remota olografica quando ci si connette al lettore di comunicazione remota olografica in HoloLens 2. in caso contrario, la connessione non riuscirà.</span><span class="sxs-lookup"><span data-stu-id="cface-111">Be sure to use version 2.0.0.0 or above of the Holographic Remoting NuGet package when connecting to the Holographic Remoting Player on HoloLens 2 or the connection will fail.</span></span>

>[!NOTE]
> <span data-ttu-id="cface-112">Le linee guida specifiche per HoloLens 2 sono disponibili [qui](holographic-remoting-create-remote-wmr.md).</span><span class="sxs-lookup"><span data-stu-id="cface-112">Guidance specific to HoloLens 2 can be found [here](holographic-remoting-create-remote-wmr.md).</span></span>


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="cface-113">Aggiungere la comunicazione remota olografica all'app desktop o UWP</span><span class="sxs-lookup"><span data-stu-id="cface-113">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="cface-114">Questa pagina descrive come aggiungere la comunicazione remota olografica a un'app desktop o UWP.</span><span class="sxs-lookup"><span data-stu-id="cface-114">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="cface-115">La comunicazione remota olografica consente all'app di avere come destinazione un HoloLens con contenuto olografico ospitato in un computer desktop o in un dispositivo UWP, ad esempio Xbox One.</span><span class="sxs-lookup"><span data-stu-id="cface-115">Holographic remoting lets your app target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One.</span></span> <span data-ttu-id="cface-116">È anche possibile accedere a più risorse di sistema, rendendo possibile l'integrazione di [visualizzazioni immersive](../../design/app-views.md) remote in software per PC desktop esistenti.</span><span class="sxs-lookup"><span data-stu-id="cface-116">You also have access to more system resources, making it possible to integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="cface-117">Un'app host Remoting riceve un flusso di dati di input da un HoloLens, esegue il rendering del contenuto in una visualizzazione immersiva virtuale e trasmette i frame di contenuto a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cface-117">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="cface-118">La connessione viene eseguita usando il Wi-Fi standard.</span><span class="sxs-lookup"><span data-stu-id="cface-118">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="cface-119">Per usare la comunicazione remota, usare un pacchetto NuGet per aggiungere la comunicazione remota olografica all'app desktop o UWP, quindi scrivere il codice per gestire la connessione ed eseguire il rendering di una visualizzazione immersiva.</span><span class="sxs-lookup"><span data-stu-id="cface-119">To use remoting, use a NuGet package to add holographic remoting to your desktop or UWP app, then write code to handle the connection and render an immersive view.</span></span> <span data-ttu-id="cface-120">Le librerie helper sono incluse nell'esempio di codice che semplificano l'attività di gestione della connessione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cface-120">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="cface-121">Una tipica connessione remota avrà una bassa di 50 ms di latenza.</span><span class="sxs-lookup"><span data-stu-id="cface-121">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="cface-122">L'App Player può segnalare la latenza in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="cface-122">The player app can report the latency in real time.</span></span>

>[!NOTE]
><span data-ttu-id="cface-123">I frammenti di codice in questo articolo illustrano attualmente l'uso di C++/CX anziché C + 17 conforme a C++/WinRT come usato nel [modello di progetto olografico c++](../native/creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="cface-123">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](../native/creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="cface-124">I concetti sono equivalenti per un progetto C++/WinRT, anche se è necessario tradurre il codice.</span><span class="sxs-lookup"><span data-stu-id="cface-124">The concepts are equivalent for a C++/WinRT project, though you'll need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="cface-125">Ottenere i pacchetti NuGet per la comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="cface-125">Get the remoting NuGet packages</span></span>

<span data-ttu-id="cface-126">Seguire questa procedura per ottenere il pacchetto NuGet per la comunicazione remota olografica e aggiungere un riferimento dal progetto:</span><span class="sxs-lookup"><span data-stu-id="cface-126">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="cface-127">Passare al progetto in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cface-127">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="cface-128">Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Gestisci pacchetti NuGet...**</span><span class="sxs-lookup"><span data-stu-id="cface-128">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="cface-129">Nel pannello **visualizzato selecct cercare** "comunicazione remota olografica".</span><span class="sxs-lookup"><span data-stu-id="cface-129">In the panel that appears, selecct **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="cface-130">Selezionare **Microsoft. olografic. Remoting** e selecct **Install**.</span><span class="sxs-lookup"><span data-stu-id="cface-130">Select **Microsoft.Holographic.Remoting** and selecct **Install**.</span></span>
5. <span data-ttu-id="cface-131">Se viene visualizzata la finestra di dialogo **Anteprima** , fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="cface-131">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="cface-132">Selezionare **Accetto** quando viene visualizzata la finestra di dialogo contratto di licenza.</span><span class="sxs-lookup"><span data-stu-id="cface-132">Select **I Accept** when the license agreement dialog appears.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="cface-133">Creare il HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="cface-133">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="cface-134">Prima di tutto, è necessario aggiungere un'istanza di HolographicStreamerHelpers alla classe che gestirà la comunicazione remota.</span><span class="sxs-lookup"><span data-stu-id="cface-134">First, we need to add an instance of HolographicStreamerHelpers to the class that will handle remoting.</span></span>

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="cface-135">Sarà inoltre necessario tenere traccia dello stato della connessione.</span><span class="sxs-lookup"><span data-stu-id="cface-135">You'll also need to track connection state.</span></span> <span data-ttu-id="cface-136">Se si desidera eseguire il rendering dell'anteprima, è necessario disporre di una trama in cui copiarla.</span><span class="sxs-lookup"><span data-stu-id="cface-136">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="cface-137">Sono necessari anche alcuni elementi, ad esempio un blocco dello stato della connessione, un modo per archiviare l'indirizzo IP di HoloLens e così via.</span><span class="sxs-lookup"><span data-stu-id="cface-137">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="cface-138">Inizializzare HolographicStreamerHelpers e connettersi a HoloLens</span><span class="sxs-lookup"><span data-stu-id="cface-138">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="cface-139">Per connettersi a un dispositivo HoloLens, creare un'istanza di HolographicStreamerHelpers e connettersi all'indirizzo IP di destinazione.</span><span class="sxs-lookup"><span data-stu-id="cface-139">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="cface-140">È necessario impostare la dimensione del fotogramma video in modo che corrisponda alla larghezza e all'altezza di visualizzazione HoloLens, perché la libreria remota olografica prevede che le risoluzioni del codificatore e del decodificatore corrispondano esattamente.</span><span class="sxs-lookup"><span data-stu-id="cface-140">You'll need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

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

<span data-ttu-id="cface-141">La connessione del dispositivo è asincrona.</span><span class="sxs-lookup"><span data-stu-id="cface-141">The device connection is asynchronous.</span></span> <span data-ttu-id="cface-142">L'app deve fornire gestori eventi per gli eventi di connessione, disconnessione e invio frame.</span><span class="sxs-lookup"><span data-stu-id="cface-142">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="cface-143">L'evento OnConnected può aggiornare l'interfaccia utente, avviare il rendering e così via.</span><span class="sxs-lookup"><span data-stu-id="cface-143">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="cface-144">Nell'esempio di codice desktop, viene aggiornato il titolo della finestra con un messaggio "Connected".</span><span class="sxs-lookup"><span data-stu-id="cface-144">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="cface-145">L'evento disconnected può gestire la riconnessione, gli aggiornamenti dell'interfaccia utente e così via.</span><span class="sxs-lookup"><span data-stu-id="cface-145">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="cface-146">In questo esempio viene riconnessa se si verifica un errore temporaneo.</span><span class="sxs-lookup"><span data-stu-id="cface-146">In this example, we reconnect if there's a transient failure.</span></span>

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

<span data-ttu-id="cface-147">Quando il componente remoto è pronto per l'invio di un frame, l'app ha la possibilità di crearne una copia nella SendFrameEvent.</span><span class="sxs-lookup"><span data-stu-id="cface-147">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="cface-148">Qui viene copiato il frame in una catena di scambio in modo che sia possibile visualizzarlo in una finestra di anteprima.</span><span class="sxs-lookup"><span data-stu-id="cface-148">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

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

### <a name="render-holographic-content"></a><span data-ttu-id="cface-149">Rendering del contenuto olografico</span><span class="sxs-lookup"><span data-stu-id="cface-149">Render holographic content</span></span>

<span data-ttu-id="cface-150">Per eseguire il rendering del contenuto usando la comunicazione remota, è necessario configurare un IFrameworkView virtuale all'interno dell'app desktop o UWP ed elaborare i frame olografici dalla comunicazione remota.</span><span class="sxs-lookup"><span data-stu-id="cface-150">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="cface-151">Tutte le API olografiche di Windows vengono utilizzate allo stesso modo da questa visualizzazione, ma sono configurate in modo leggermente diverso.</span><span class="sxs-lookup"><span data-stu-id="cface-151">All of the Windows Holographic APIs are used the same way by this view, but it's set up slightly differently.</span></span>

<span data-ttu-id="cface-152">Invece di crearli autonomamente, i componenti di spazio olografico e vocale provengono dalla classe HolographicRemotingHelpers:</span><span class="sxs-lookup"><span data-stu-id="cface-152">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="cface-153">Invece di usare un ciclo di aggiornamento in un metodo Run, è necessario fornire gli aggiornamenti del ciclo principale dell'app desktop o UWP.</span><span class="sxs-lookup"><span data-stu-id="cface-153">Instead of using an update loop in a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="cface-154">Ciò consente all'app desktop o UWP di rimanere in controllo dell'elaborazione dei messaggi.</span><span class="sxs-lookup"><span data-stu-id="cface-154">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="cface-155">Il metodo di sequenza () del segno di visualizzazione dell'app olografica completa un'iterazione del ciclo di aggiornamento, di estrazione e di presentazione.</span><span class="sxs-lookup"><span data-stu-id="cface-155">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

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

<span data-ttu-id="cface-156">Il ciclo di aggiornamento, rendering e presenza dell'app olografica è identico a quello che si verifica quando è in esecuzione in HoloLens, ad eccezione del fatto che è possibile accedere a una quantità molto maggiore di risorse di sistema nel PC desktop.</span><span class="sxs-lookup"><span data-stu-id="cface-156">The holographic app view update, render, and present loop are exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="cface-157">È possibile eseguire il rendering di molti più triangoli, avere più passaggi di disegno, eseguire più fisica e usare processi x64 per caricare contenuti che richiedono più di 2 GB di RAM.</span><span class="sxs-lookup"><span data-stu-id="cface-157">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="cface-158">Disconnetti e termina la sessione remota</span><span class="sxs-lookup"><span data-stu-id="cface-158">Disconnect and end the remote session</span></span>

<span data-ttu-id="cface-159">Per disconnettersi, ad esempio, quando l'utente fa clic su un pulsante dell'interfaccia utente per disconnettere-chiamare Disconnect () in HolographicStreamerHelpers e quindi rilasciare l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="cface-159">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

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

## <a name="get-the-remoting-player"></a><span data-ttu-id="cface-160">Ottenere il lettore di comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="cface-160">Get the remoting player</span></span>

<span data-ttu-id="cface-161">Il lettore di comunicazione remota olografica di Windows è disponibile nell'App Store di Windows come endpoint per le applicazioni host Remote a cui connettersi.</span><span class="sxs-lookup"><span data-stu-id="cface-161">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="cface-162">Per ottenere il lettore di comunicazione remota olografica Windows, visitare l'App Store di Windows dalla HoloLens, cercare i servizi remoti e scaricare l'app.</span><span class="sxs-lookup"><span data-stu-id="cface-162">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="cface-163">Il lettore .NET Remoting include una funzionalità per la visualizzazione delle statistiche sullo schermo, che può essere utile quando si esegue il debug di applicazioni host Remote.</span><span class="sxs-lookup"><span data-stu-id="cface-163">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="cface-164">Note e risorse</span><span class="sxs-lookup"><span data-stu-id="cface-164">Notes and resources</span></span>

<span data-ttu-id="cface-165">La visualizzazione dell'app olografica richiede un modo per fornire all'app il dispositivo Direct3D, che deve essere usato per inizializzare lo spazio olografico.</span><span class="sxs-lookup"><span data-stu-id="cface-165">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="cface-166">L'app deve usare questo dispositivo Direct3D per copiare e visualizzare il frame di anteprima.</span><span class="sxs-lookup"><span data-stu-id="cface-166">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="cface-167">**Esempio di codice:** È disponibile un [esempio di codice .NET Remoting](https://github.com/Microsoft/HoloLensCompanionKit) completo, che include una visualizzazione di applicazioni olografica compatibile con i progetti host .NET Remoting e Remoting per desktop Win32, UWP DirectX e UWP con XAML.</span><span class="sxs-lookup"><span data-stu-id="cface-167">**Code sample:** A complete [Holographic Remoting code sample](https://github.com/Microsoft/HoloLensCompanionKit) is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> 

<span data-ttu-id="cface-168">**Nota di debug:** La libreria remota olografica può generare eccezioni first-chance.</span><span class="sxs-lookup"><span data-stu-id="cface-168">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="cface-169">Queste eccezioni possono essere visibili nelle sessioni di debug, a seconda delle impostazioni delle eccezioni di Visual Studio attive al momento.</span><span class="sxs-lookup"><span data-stu-id="cface-169">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="cface-170">Queste eccezioni vengono rilevate internamente dalla libreria di comunicazione remota olografica e possono essere ignorate.</span><span class="sxs-lookup"><span data-stu-id="cface-170">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
