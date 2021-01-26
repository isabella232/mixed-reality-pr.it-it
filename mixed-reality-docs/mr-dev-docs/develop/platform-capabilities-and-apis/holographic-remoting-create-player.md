---
title: Scrivere un lettore Holographic Remoting personalizzato
description: Creare un'app hologaphic Remoting personalizzata per visualizzare il contenuto di cui è stato eseguito il rendering in un computer remoto in HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica, NuGet, manifesto dell'applicazione, contesto del lettore, app remota, auricolare in realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 391650025398b4bdd89e30db1df7df5e3d6ab5f2
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810122"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="84c10-104">Scrivere un'app lettore Holographic Remoting personalizzata</span><span class="sxs-lookup"><span data-stu-id="84c10-104">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="84c10-105">Questo documento descrive la creazione di un'applicazione lettore personalizzata per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="84c10-105">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="84c10-106">I lettori personalizzati scritti per HoloLens 2 non sono compatibili con le applicazioni remote scritte per HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="84c10-106">Custom players written for HoloLens 2 are not compatible with remote applications written for HoloLens 1.</span></span> <span data-ttu-id="84c10-107">Questo implica che entrambe le applicazioni devono usare il pacchetto NuGet versione **2.** x. x.</span><span class="sxs-lookup"><span data-stu-id="84c10-107">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="84c10-108">Grazie alla creazione di un'app lettore di comunicazione remota olografica personalizzata, è possibile creare un'applicazione personalizzata in grado di visualizzare [visualizzazioni immersive](../../design/app-views.md) da in un computer remoto nel HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="84c10-108">By creating a custom Holographic Remoting player app, you can create a custom application capable of displaying [immersive views](../../design/app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="84c10-109">Tutto il codice in questa pagina e i progetti di lavoro sono disponibili nel [repository GitHub degli esempi di comunicazione remota olografica](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="84c10-109">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="84c10-110">Un lettore di comunicazione remota olografica consente all'app di visualizzare il [rendering](rendering.md) di contenuto olografico in un computer desktop o in un dispositivo UWP come Xbox One con accesso a più risorse di sistema.</span><span class="sxs-lookup"><span data-stu-id="84c10-110">A Holographic Remoting player lets your app display holographic content [rendered](rendering.md) on a desktop PC or UWP device like the Xbox One with access to more system resources.</span></span> <span data-ttu-id="84c10-111">Un'app lettore di comunicazione remota olografica trasmette i dati di input a un'applicazione remota olografica remota e riceve una visualizzazione immersiva come flusso video e audio.</span><span class="sxs-lookup"><span data-stu-id="84c10-111">A Holographic Remoting player app streams input data to a Holographic Remoting remote application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="84c10-112">La connessione viene eseguita usando il Wi-Fi standard.</span><span class="sxs-lookup"><span data-stu-id="84c10-112">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="84c10-113">Per creare un'app per giocatori, usare un pacchetto NuGet per aggiungere la comunicazione remota olografica all'app UWP.</span><span class="sxs-lookup"><span data-stu-id="84c10-113">To create a player app, use a NuGet package to add Holographic Remoting to your UWP app.</span></span> <span data-ttu-id="84c10-114">Scrivere quindi il codice per gestire la connessione e visualizzare una visualizzazione immersiva.</span><span class="sxs-lookup"><span data-stu-id="84c10-114">Then write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="84c10-115">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="84c10-115">Prerequisites</span></span>

<span data-ttu-id="84c10-116">Un punto di partenza valido è un'app UWP basata su DirectX funzionante che ha già come destinazione l'API di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="84c10-116">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="84c10-117">Per informazioni dettagliate, vedere [Cenni preliminari sullo sviluppo DirectX](../native/directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="84c10-117">For details see [DirectX development overview](../native/directx-development-overview.md).</span></span> <span data-ttu-id="84c10-118">Se non si dispone di un'app esistente e si desidera iniziare da zero, il [modello di progetto olografico C++](../native/creating-a-holographic-directx-project.md) è un punto di partenza valido.</span><span class="sxs-lookup"><span data-stu-id="84c10-118">If you don't have an existing app and want to start from scratch the [C++ holographic project template](../native/creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="84c10-119">Qualsiasi app che usa la comunicazione remota olografica deve essere creata per usare un [Apartment](/windows/win32/com/multithreaded-apartments)multithread.</span><span class="sxs-lookup"><span data-stu-id="84c10-119">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](/windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="84c10-120">L'uso di un [Apartment a thread singolo](/windows/win32/com/single-threaded-apartments) è supportato, ma comporta prestazioni ottimali e possibilmente balbettanti durante la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="84c10-120">The use of a [single-threaded apartment](/windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="84c10-121">Quando si usa C++/WinRT [WinRT:: init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) un apartment multithread è il valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="84c10-121">When using C++/WinRT [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="84c10-122">Ottenere il pacchetto NuGet per la comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="84c10-122">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="84c10-123">I passaggi seguenti sono necessari per aggiungere il pacchetto NuGet a un progetto in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="84c10-123">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="84c10-124">Aprire il progetto in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="84c10-124">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="84c10-125">Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Gestisci pacchetti NuGet...**</span><span class="sxs-lookup"><span data-stu-id="84c10-125">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="84c10-126">Nel pannello visualizzato selezionare **Sfoglia** e quindi cercare "comunicazione remota olografica".</span><span class="sxs-lookup"><span data-stu-id="84c10-126">In the panel that appears, select **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="84c10-127">Selezionare **Microsoft. olografic. Remoting**, assicurarsi di selezionare la versione **2. x.** x più recente e selezionare **Installa**.</span><span class="sxs-lookup"><span data-stu-id="84c10-127">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and select **Install**.</span></span>
5. <span data-ttu-id="84c10-128">Se viene visualizzata la finestra di dialogo **Anteprima** , fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="84c10-128">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="84c10-129">Selezionare **Accetto** quando viene visualizzata la finestra di dialogo contratto di licenza.</span><span class="sxs-lookup"><span data-stu-id="84c10-129">Select **I Accept** when the license agreement dialog appears.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="84c10-130">Il contenuto del ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` pacchetto NuGet contiene la documentazione dettagliata per l'API esposta dalla comunicazione remota olografica.</span><span class="sxs-lookup"><span data-stu-id="84c10-130">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="84c10-131">Modificare il pacchetto. appxmanifest dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="84c10-131">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="84c10-132">Per fare in modo che l'applicazione sia in grado di riconoscere il Microsoft.Holographic.AppRemoting.dll aggiunto dal pacchetto NuGet, è necessario eseguire i passaggi seguenti per il progetto:</span><span class="sxs-lookup"><span data-stu-id="84c10-132">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="84c10-133">Nella Esplora soluzioni fare clic con il pulsante destro del mouse sul file **Package. appxmanifest** e scegliere **Apri con...**</span><span class="sxs-lookup"><span data-stu-id="84c10-133">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="84c10-134">Seleziona **editor XML (testo)** e seleziona **OK**</span><span class="sxs-lookup"><span data-stu-id="84c10-134">Select **XML (Text) Editor** and select **OK**</span></span>
3. <span data-ttu-id="84c10-135">Aggiungere le righe seguenti al file e salvare</span><span class="sxs-lookup"><span data-stu-id="84c10-135">Add the following lines to the file and save</span></span>
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a><span data-ttu-id="84c10-136">Creare il contesto del lettore</span><span class="sxs-lookup"><span data-stu-id="84c10-136">Create the player context</span></span>

<span data-ttu-id="84c10-137">Come primo passaggio, l'applicazione deve creare un contesto del lettore.</span><span class="sxs-lookup"><span data-stu-id="84c10-137">As a first step the application should create a player context.</span></span>

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
><span data-ttu-id="84c10-138">La comunicazione remota olografica funziona sostituendo il runtime della realtà mista di Windows che fa parte di Windows con un runtime specifico di .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="84c10-138">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="84c10-139">Questa operazione viene eseguita durante la creazione del contesto del lettore.</span><span class="sxs-lookup"><span data-stu-id="84c10-139">This is done during the creation of the player context.</span></span> <span data-ttu-id="84c10-140">Per questo motivo qualsiasi chiamata a qualsiasi API di realtà mista di Windows prima di creare il contesto del lettore può causare un comportamento imprevisto.</span><span class="sxs-lookup"><span data-stu-id="84c10-140">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="84c10-141">L'approccio consigliato consiste nel creare il contesto del lettore il prima possibile prima di interagire con qualsiasi API di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="84c10-141">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="84c10-142">Non combinare mai oggetti creati o recuperati tramite qualsiasi API di realtà mista di Windows prima della chiamata a ```PlayerContext::Create``` con gli oggetti creati o recuperati in seguito.</span><span class="sxs-lookup"><span data-stu-id="84c10-142">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="84c10-143">Successivamente, è possibile creare HolographicSpace, chiamando [HolographicSpace. CreateForCoreWindow](/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span><span class="sxs-lookup"><span data-stu-id="84c10-143">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a><span data-ttu-id="84c10-144">Connettersi all'app remota</span><span class="sxs-lookup"><span data-stu-id="84c10-144">Connect to the remote app</span></span>

<span data-ttu-id="84c10-145">Quando l'App Player è pronta per il rendering del contenuto, è possibile stabilire una connessione all'app remota.</span><span class="sxs-lookup"><span data-stu-id="84c10-145">Once the player app is ready for rendering content a connection to the remote app can be established.</span></span>

<span data-ttu-id="84c10-146">La connessione può essere stabilita in uno dei modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="84c10-146">The connection can be established in one of the following ways:</span></span>
1) <span data-ttu-id="84c10-147">L'App Player in esecuzione su HoloLens 2 si connette all'app remota.</span><span class="sxs-lookup"><span data-stu-id="84c10-147">The player app running on HoloLens 2 connects to the remote app.</span></span>
2) <span data-ttu-id="84c10-148">L'app remota si connette all'App Player in esecuzione su HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="84c10-148">The remote app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="84c10-149">Per connettersi dall'App Player all'app remota, chiamare il ```Connect``` metodo sul contesto del lettore specificando il nome host e la porta.</span><span class="sxs-lookup"><span data-stu-id="84c10-149">To connect from the player app to the remote app call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="84c10-150">La porta predefinita è **8265**.</span><span class="sxs-lookup"><span data-stu-id="84c10-150">The default port is **8265**.</span></span>

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
><span data-ttu-id="84c10-151">Come per qualsiasi API C++/WinRT, ```Connect``` può generare un WinRT:: hresult_error che deve essere gestito.</span><span class="sxs-lookup"><span data-stu-id="84c10-151">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="84c10-152">L'ascolto delle connessioni in ingresso nell'App Player può essere eseguito chiamando il ```Listen``` metodo.</span><span class="sxs-lookup"><span data-stu-id="84c10-152">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="84c10-153">Durante questa chiamata è possibile specificare sia la porta di handshake che la porta di trasporto.</span><span class="sxs-lookup"><span data-stu-id="84c10-153">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="84c10-154">La porta di handshake viene utilizzata per l'handshake iniziale.</span><span class="sxs-lookup"><span data-stu-id="84c10-154">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="84c10-155">I dati vengono quindi inviati tramite la porta di trasporto.</span><span class="sxs-lookup"><span data-stu-id="84c10-155">The data is then sent over the transport port.</span></span> <span data-ttu-id="84c10-156">Per impostazione predefinita vengono usati il numero di porta **8265** e **8266** .</span><span class="sxs-lookup"><span data-stu-id="84c10-156">By default port number **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a><span data-ttu-id="84c10-157">Gestione degli eventi correlati alla connessione</span><span class="sxs-lookup"><span data-stu-id="84c10-157">Handling connection-related events</span></span>

<span data-ttu-id="84c10-158">```PlayerContext```Espone tre eventi per monitorare lo stato della connessione.</span><span class="sxs-lookup"><span data-stu-id="84c10-158">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="84c10-159">OnConnected: attivato quando una connessione all'app remota è stata stabilita correttamente.</span><span class="sxs-lookup"><span data-stu-id="84c10-159">OnConnected: Triggered when a connection to the remote app has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="84c10-160">Disconnected: attivato se una connessione stabilita viene terminata o non è stato possibile stabilire una connessione.</span><span class="sxs-lookup"><span data-stu-id="84c10-160">OnDisconnected: Triggered if an established connection is terminated or a connection couldn't be established.</span></span>
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
><span data-ttu-id="84c10-161">I ```ConnectionFailureReason``` valori possibili sono documentati nel ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span><span class="sxs-lookup"><span data-stu-id="84c10-161">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="84c10-162">Onlistening: durante l'ascolto delle connessioni in ingresso viene avviato.</span><span class="sxs-lookup"><span data-stu-id="84c10-162">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="84c10-163">Inoltre, è possibile eseguire query sullo stato della connessione utilizzando la ```ConnectionState``` proprietà nel contesto del lettore.</span><span class="sxs-lookup"><span data-stu-id="84c10-163">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="84c10-164">Visualizzare il frame sottoposto a rendering remoto</span><span class="sxs-lookup"><span data-stu-id="84c10-164">Display the remotely rendered frame</span></span>

<span data-ttu-id="84c10-165">Per visualizzare il contenuto di cui è stato eseguito il rendering in remoto, chiamare ```PlayerContext::BlitRemoteFrame``` durante il rendering di un [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe).</span><span class="sxs-lookup"><span data-stu-id="84c10-165">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame``` while rendering a [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="84c10-166">```BlitRemoteFrame``` richiede che il buffer nascosto per la HolographicFrame corrente sia associato come destinazione di rendering.</span><span class="sxs-lookup"><span data-stu-id="84c10-166">```BlitRemoteFrame``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="84c10-167">Il buffer nascosto può essere ricevuto da [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) tramite la proprietà [Direct3D11BackBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) .</span><span class="sxs-lookup"><span data-stu-id="84c10-167">The back buffer can be received from the [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="84c10-168">Quando viene chiamato, ```BlitRemoteFrame``` copia l'ultimo frame ricevuto dall'applicazione remota nel buffer di HolographicFrame.</span><span class="sxs-lookup"><span data-stu-id="84c10-168">When called, ```BlitRemoteFrame``` copies the latest received frame from the remote application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="84c10-169">Inoltre, il set di punti di interesse è impostato, se l'applicazione remota ha specificato un punto di attivazione durante il rendering del frame remoto.</span><span class="sxs-lookup"><span data-stu-id="84c10-169">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="84c10-170">```PlayerContext::BlitRemoteFrame``` potenzialmente sovrascrive il punto di messa a fuoco per il frame corrente.</span><span class="sxs-lookup"><span data-stu-id="84c10-170">```PlayerContext::BlitRemoteFrame``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="84c10-171">Per specificare un punto di attivazione di fallback, chiamare [HolographicCameraRenderingParameters:: SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) prima di ```PlayerContext::BlitRemoteFrame``` .</span><span class="sxs-lookup"><span data-stu-id="84c10-171">To specify a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame```.</span></span> 
>- <span data-ttu-id="84c10-172">Per sovrascrivere il punto di attivazione remota, chiamare [HolographicCameraRenderingParameters:: SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  dopo ```PlayerContext::BlitRemoteFrame``` .</span><span class="sxs-lookup"><span data-stu-id="84c10-172">To overwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame```.</span></span>

<span data-ttu-id="84c10-173">Se l'operazione riesce, ```BlitRemoteFrame``` restituisce ```BlitResult::Success_Color``` .</span><span class="sxs-lookup"><span data-stu-id="84c10-173">On success, ```BlitRemoteFrame``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="84c10-174">In caso contrario, restituisce il motivo dell'errore:</span><span class="sxs-lookup"><span data-stu-id="84c10-174">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="84c10-175">```BlitResult::Failed_NoRemoteFrameAvailable```: Operazione non riuscita perché non è disponibile un frame remoto.</span><span class="sxs-lookup"><span data-stu-id="84c10-175">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="84c10-176">```BlitResult::Failed_NoCamera```: Operazione non riuscita perché non è presente alcuna fotocamera.</span><span class="sxs-lookup"><span data-stu-id="84c10-176">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>
- <span data-ttu-id="84c10-177">```BlitResult::Failed_RemoteFrameTooOld```: Non riuscito perché il frame remoto è troppo vecchio (vedere la proprietà PlayerContext:: BlitRemoteFrameTimeout).</span><span class="sxs-lookup"><span data-stu-id="84c10-177">```BlitResult::Failed_RemoteFrameTooOld```: Failed because remote frame is too old (see PlayerContext::BlitRemoteFrameTimeout property).</span></span>

>[!IMPORTANT]
> <span data-ttu-id="84c10-178">A partire dalla versione [2.1.0](holographic-remoting-version-history.md#v2.1.0) è possibile usare un lettore personalizzato per usare la riproiezione di profondità tramite la comunicazione remota olografica.</span><span class="sxs-lookup"><span data-stu-id="84c10-178">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) it is possible with a custom player to use depth reprojection via Holographic Remoting.</span></span>

<span data-ttu-id="84c10-179">```BlitResult``` può restituire anche ```BlitResult::Success_Color_Depth``` nelle condizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="84c10-179">```BlitResult``` can also return ```BlitResult::Success_Color_Depth``` under the following conditions:</span></span>

- <span data-ttu-id="84c10-180">L'app remota ha eseguito il commit di un buffer di profondità tramite [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span><span class="sxs-lookup"><span data-stu-id="84c10-180">The remote app has committed a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>
- <span data-ttu-id="84c10-181">L'App Player personalizzata ha associato un buffer di profondità valido prima di chiamare ```BlitRemoteFrame``` .</span><span class="sxs-lookup"><span data-stu-id="84c10-181">The custom player app has bound a valid depth buffer before calling ```BlitRemoteFrame```.</span></span>

<span data-ttu-id="84c10-182">Se queste condizioni vengono soddisfatte ```BlitRemoteFrame``` , blit la profondità remota nel buffer di profondità locale attualmente associato.</span><span class="sxs-lookup"><span data-stu-id="84c10-182">If these conditions are met ```BlitRemoteFrame``` will blit the remote depth into the currently bound local depth buffer.</span></span> <span data-ttu-id="84c10-183">È quindi possibile eseguire il rendering di contenuto locale aggiuntivo, che avrà una profondità di intersezione con il contenuto di cui è stato eseguito il rendering remoto.</span><span class="sxs-lookup"><span data-stu-id="84c10-183">You can then render additional local content, which will have depth intersection with the remote rendered content.</span></span> <span data-ttu-id="84c10-184">Inoltre, è possibile eseguire il commit del buffer di profondità locale tramite [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) nel lettore personalizzato per ottenere una riproiezione della profondità per il contenuto remoto e locale di cui è stato eseguito il rendering.</span><span class="sxs-lookup"><span data-stu-id="84c10-184">Additionally you can commit the local depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) in your custom player to have depth reprojection for remote and local rendered content.</span></span> <span data-ttu-id="84c10-185">Per informazioni dettagliate, vedere [riproiezione approfondita](hologram-stability.md#reprojection) .</span><span class="sxs-lookup"><span data-stu-id="84c10-185">See [Depth Reprojection](hologram-stability.md#reprojection) for details.</span></span>

### <a name="projection-transform-mode"></a><span data-ttu-id="84c10-186">Modalità di trasformazione proiezione</span><span class="sxs-lookup"><span data-stu-id="84c10-186">Projection Transform Mode</span></span>

<span data-ttu-id="84c10-187">Un problema che emerge quando si usa la riproiezione di profondità tramite la comunicazione remota olografica è che il contenuto remoto può essere sottoposto a rendering con una trasformazione di proiezione diversa rispetto al contenuto locale di cui è stato eseguito il rendering direttamente dall'App Player personalizzata.</span><span class="sxs-lookup"><span data-stu-id="84c10-187">One problem, which surfaces when using depth reprojection via Holographic Remoting is that the remote content can be rendered with a different projection transform than local content directly rendered by your custom player app.</span></span> <span data-ttu-id="84c10-188">Un caso d'uso comune è quello di specificare valori diversi per il piano near e lontano (tramite [HolographicCamera:: SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) e [HolographicCamera:: SetFarPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) sul lato Player e sul lato remoto.</span><span class="sxs-lookup"><span data-stu-id="84c10-188">A common use-case is to specify different values for near and far plane (via [HolographicCamera::SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) and [HolographicCamera::SetFarPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) on the player side and the remote side.</span></span> <span data-ttu-id="84c10-189">In questo caso, non è chiaro se la trasformazione della proiezione sul lato Player deve riflettere le distanze del piano remoto vicino/lontano o quelle locali.</span><span class="sxs-lookup"><span data-stu-id="84c10-189">In this case, it's not clear if the projection transform on the player side should reflect the remote near/far plane distances or the local ones.</span></span>

<span data-ttu-id="84c10-190">A partire dalla versione [2.1.0](holographic-remoting-version-history.md#v2.1.0) è possibile controllare la modalità di trasformazione della proiezione tramite ```PlayerContext::ProjectionTransformConfig``` .</span><span class="sxs-lookup"><span data-stu-id="84c10-190">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) you can control the projection transform mode via ```PlayerContext::ProjectionTransformConfig```.</span></span> <span data-ttu-id="84c10-191">I valori supportati sono:</span><span class="sxs-lookup"><span data-stu-id="84c10-191">Supported values are:</span></span>

- <span data-ttu-id="84c10-192">```Local``` - [HolographicCameraPose::P rojectiontransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) restituisce una trasformazione di proiezione, che riflette le distanze del piano vicino/lontano impostate dall'App Player personalizzata in HolographicCamera.</span><span class="sxs-lookup"><span data-stu-id="84c10-192">```Local``` - [HolographicCameraPose::ProjectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) returns a projection transform, which reflects the near/far plane distances set by your custom player app on the HolographicCamera.</span></span>
- <span data-ttu-id="84c10-193">```Remote``` -La trasformazione della proiezione riflette le distanze del piano vicino/lontano specificate dall'app remota.</span><span class="sxs-lookup"><span data-stu-id="84c10-193">```Remote``` - Projection transform reflects the near/far plane distances specified by the remote app.</span></span>
- <span data-ttu-id="84c10-194">```Merged``` -Le distanze del piano vicino/estremo dall'app remota e l'app per giocatori personalizzata sono unite.</span><span class="sxs-lookup"><span data-stu-id="84c10-194">```Merged``` - Near/Far plane distances from your remote app and your custom player app are merged.</span></span> <span data-ttu-id="84c10-195">Per impostazione predefinita, questa operazione viene eseguita impostando il valore minimo delle distanze vicino al piano e il valore massimo delle distanze del piano lontano.</span><span class="sxs-lookup"><span data-stu-id="84c10-195">By default this is done by taking the minimum of the near plane distances and the maximum of the far plane distances.</span></span> <span data-ttu-id="84c10-196">Nel caso in cui il lato remoto o locale sia invertito, ad esempio lontano < vicino, le distanze del piano remoto vicino/lontano vengono capovolte.</span><span class="sxs-lookup"><span data-stu-id="84c10-196">In case either the remote or local side are inverted, say far < near, the remote near/far plane distances are flipped.</span></span>

## <a name="optional-set-blitremoteframetimeout"></a><span data-ttu-id="84c10-197">Facoltativo: set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span><span class="sxs-lookup"><span data-stu-id="84c10-197">Optional: Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span></span>
>[!IMPORTANT]
> <span data-ttu-id="84c10-198">```PlayerContext::BlitRemoteFrameTimeout``` è supportato a partire dalla versione [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="84c10-198">```PlayerContext::BlitRemoteFrameTimeout``` is supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 

<span data-ttu-id="84c10-199">La ```PlayerContext::BlitRemoteFrameTimeout``` proprietà specifica l'intervallo di tempo in cui un frame remoto viene riutilizzato se non viene ricevuto alcun nuovo frame remoto.</span><span class="sxs-lookup"><span data-stu-id="84c10-199">The ```PlayerContext::BlitRemoteFrameTimeout``` property specifies the amount of time a remote frame is reused if no new remote frame is received.</span></span> 

<span data-ttu-id="84c10-200">Un caso d'uso comune è quello di abilitare il timeout BlitRemoteFrame per visualizzare una schermata vuota se non vengono ricevuti nuovi frame per un determinato periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="84c10-200">A common use-case is to enable the BlitRemoteFrame timeout to display a blank screen if no new frames are received for a certain amount of time.</span></span> <span data-ttu-id="84c10-201">Quando è abilitata ```BlitRemoteFrame``` , è possibile usare il tipo restituito del metodo anche per passare a un contenuto di fallback sottoposto a rendering in locale.</span><span class="sxs-lookup"><span data-stu-id="84c10-201">When enabled the return type of the ```BlitRemoteFrame``` method can also be used to switch to a locally rendered fallback content.</span></span> 

<span data-ttu-id="84c10-202">Per abilitare il timeout, impostare il valore della proprietà su una durata uguale o maggiore di 100 ms.</span><span class="sxs-lookup"><span data-stu-id="84c10-202">To enable the timeout, set the property value to a duration equal or greater than 100 ms.</span></span> <span data-ttu-id="84c10-203">Per disabilitare il timeout, impostare la proprietà su zero Duration.</span><span class="sxs-lookup"><span data-stu-id="84c10-203">To disable the timeout, set the property to zero duration.</span></span> <span data-ttu-id="84c10-204">Se il timeout è abilitato e non viene ricevuto un frame remoto per la durata del set, BlitRemoteFrame avrà esito negativo e restituirà ```Failed_RemoteFrameTooOld``` un risultato fino a quando non viene ricevuto un nuovo frame remoto.</span><span class="sxs-lookup"><span data-stu-id="84c10-204">If the timeout is enabled and no remote frame is received for the set duration, BlitRemoteFrame will fail and return ```Failed_RemoteFrameTooOld``` until a new remote frame is received.</span></span>

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="84c10-205">Facoltativo: ottenere le statistiche sull'ultimo frame remoto</span><span class="sxs-lookup"><span data-stu-id="84c10-205">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="84c10-206">Per diagnosticare problemi di prestazioni o di rete, è possibile recuperare le statistiche sull'ultimo frame remoto tramite la ```PlayerContext::LastFrameStatistics``` Proprietà.</span><span class="sxs-lookup"><span data-stu-id="84c10-206">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="84c10-207">Le statistiche vengono aggiornate durante la chiamata a [HolographicFrame::P resentusingcurrentprediction](/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span><span class="sxs-lookup"><span data-stu-id="84c10-207">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="84c10-208">Per ulteriori informazioni, vedere la ```PlayerFrameStatistics``` documentazione nel ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span><span class="sxs-lookup"><span data-stu-id="84c10-208">For more information, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="84c10-209">Facoltativo: canali di dati personalizzati</span><span class="sxs-lookup"><span data-stu-id="84c10-209">Optional: Custom data channels</span></span>

<span data-ttu-id="84c10-210">I canali di dati personalizzati possono essere utilizzati per inviare dati utente tramite la connessione remota già stabilita.</span><span class="sxs-lookup"><span data-stu-id="84c10-210">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="84c10-211">Per ulteriori informazioni, vedere [canali di dati personalizzati](holographic-remoting-custom-data-channels.md) .</span><span class="sxs-lookup"><span data-stu-id="84c10-211">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="84c10-212">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="84c10-212">See Also</span></span>
* [<span data-ttu-id="84c10-213">Scrittura di un'app remota olografica remota usando le API di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="84c10-213">Writing a Holographic Remoting remote app using Windows Mixed Reality APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="84c10-214">Scrittura di un'app remota di comunicazione remota olografica usando le API di OpenXR</span><span class="sxs-lookup"><span data-stu-id="84c10-214">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="84c10-215">Canali di dati di Holographic Remoting personalizzati</span><span class="sxs-lookup"><span data-stu-id="84c10-215">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="84c10-216">Stabilire una connessione sicura con Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="84c10-216">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="84c10-217">Limitazioni e risoluzione dei problemi di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="84c10-217">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="84c10-218">Condizioni di licenza software per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="84c10-218">Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="84c10-219">Informativa sulla privacy di Microsoft</span><span class="sxs-lookup"><span data-stu-id="84c10-219">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)