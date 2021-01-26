---
title: Scrittura di un'app remota olografica remota (WMR)
description: Informazioni su come trasmettere il rendering del contenuto remoto in un computer remoto a HoloLens 2 con app Remote Remoting con HolographicSpace.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica, auricolare realtà mista, cuffia a realtà mista di Windows, auricolare della realtà virtuale, NuGet
ms.openlocfilehash: 6884c2679b155c36a21bcf89352524e4957a9f20
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810073"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a><span data-ttu-id="e3517-104">Scrittura di un'app remota di comunicazione remota olografica tramite l'API HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="e3517-104">Writing a Holographic Remoting remote app using the HolographicSpace API</span></span>

>[!IMPORTANT]
><span data-ttu-id="e3517-105">Questo documento descrive la creazione di un'applicazione remota per HoloLens 2 con l' [API HolographicSpace](../native/getting-a-holographicspace.md).</span><span class="sxs-lookup"><span data-stu-id="e3517-105">This document describes the creation of a remote application for HoloLens 2 using the [HolographicSpace API](../native/getting-a-holographicspace.md).</span></span> <span data-ttu-id="e3517-106">Le applicazioni remote per **HoloLens (1a Gen)** devono usare il pacchetto NuGet versione **1. x. x**.</span><span class="sxs-lookup"><span data-stu-id="e3517-106">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="e3517-107">Ciò implica che le applicazioni remote scritte per HoloLens 2 non sono compatibili con HoloLens 1 e viceversa.</span><span class="sxs-lookup"><span data-stu-id="e3517-107">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="e3517-108">La documentazione per HoloLens 1 è disponibile [qui](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="e3517-108">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="e3517-109">Le app di comunicazione remota olografica possono trasmettere contenuti con rendering remoto a HoloLens 2 e agli auricolari immersivi con la realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="e3517-109">Holographic Remoting apps can stream remotely rendered content to HoloLens 2 and Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="e3517-110">È inoltre possibile accedere a più risorse di sistema e integrare [visualizzazioni immersive](../../design/app-views.md) remote in software per PC desktop esistenti.</span><span class="sxs-lookup"><span data-stu-id="e3517-110">You can also access more system resources and integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="e3517-111">Un'app remota riceve un flusso di dati di input da HoloLens 2, esegue il rendering del contenuto in una visualizzazione immersiva virtuale e trasmette nuovamente i frame di contenuto a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e3517-111">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="e3517-112">La connessione viene eseguita usando il Wi-Fi standard.</span><span class="sxs-lookup"><span data-stu-id="e3517-112">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="e3517-113">La comunicazione remota olografica viene aggiunta a un'app desktop o UWP tramite un pacchetto NuGet.</span><span class="sxs-lookup"><span data-stu-id="e3517-113">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="e3517-114">È necessario codice aggiuntivo che gestisce la connessione e ne esegue il rendering in una visualizzazione immersiva.</span><span class="sxs-lookup"><span data-stu-id="e3517-114">Additional code is required which handles the connection and renders in an immersive view.</span></span> <span data-ttu-id="e3517-115">Una tipica connessione remota avrà una bassa di 50 ms di latenza.</span><span class="sxs-lookup"><span data-stu-id="e3517-115">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="e3517-116">L'App Player può segnalare la latenza in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="e3517-116">The player app can report the latency in real time.</span></span>

<span data-ttu-id="e3517-117">Tutto il codice in questa pagina e i progetti di lavoro sono disponibili nel [repository GitHub degli esempi di comunicazione remota olografica](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="e3517-117">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e3517-118">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="e3517-118">Prerequisites</span></span>

<span data-ttu-id="e3517-119">Un punto di partenza efficace è un'app desktop o UWP basata su DirectX funzionante, che ha come destinazione l' [API HolographicSpace](../native/getting-a-holographicspace.md).</span><span class="sxs-lookup"><span data-stu-id="e3517-119">A good starting point is a working DirectX based Desktop or UWP app, which targets the [HolographicSpace API](../native/getting-a-holographicspace.md).</span></span> <span data-ttu-id="e3517-120">Per informazioni dettagliate, vedere [Cenni preliminari sullo sviluppo DirectX](../native/directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e3517-120">For details see [DirectX development overview](../native/directx-development-overview.md).</span></span> <span data-ttu-id="e3517-121">Il [modello di progetto olografico C++](../native/creating-a-holographic-directx-project.md) è un punto di partenza valido.</span><span class="sxs-lookup"><span data-stu-id="e3517-121">The [C++ holographic project template](../native/creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="e3517-122">Qualsiasi app che usa la comunicazione remota olografica deve essere creata per usare un [Apartment](/windows/win32/com/multithreaded-apartments)multithread.</span><span class="sxs-lookup"><span data-stu-id="e3517-122">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](/windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="e3517-123">L'uso di un [Apartment a thread singolo](/windows/win32/com/single-threaded-apartments) è supportato, ma comporta prestazioni ottimali e possibilmente balbettanti durante la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="e3517-123">The use of a [single-threaded apartment](/windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="e3517-124">Quando si usa C++/WinRT [WinRT:: init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) un apartment multithread è il valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="e3517-124">When using C++/WinRT [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="e3517-125">Ottenere il pacchetto NuGet per la comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="e3517-125">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="e3517-126">I passaggi seguenti sono necessari per aggiungere il pacchetto NuGet a un progetto in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e3517-126">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="e3517-127">Aprire il progetto in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e3517-127">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="e3517-128">Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Gestisci pacchetti NuGet...**</span><span class="sxs-lookup"><span data-stu-id="e3517-128">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="e3517-129">Nel pannello visualizzato selezionare **Sfoglia** e quindi cercare "comunicazione remota olografica".</span><span class="sxs-lookup"><span data-stu-id="e3517-129">In the panel that appears, select **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="e3517-130">Selezionare **Microsoft. olografic. Remoting**, assicurarsi di selezionare la versione **2. x.** x più recente e selezionare **Installa**.</span><span class="sxs-lookup"><span data-stu-id="e3517-130">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and select **Install**.</span></span>
5. <span data-ttu-id="e3517-131">Se viene visualizzata la finestra di dialogo **Anteprima** , fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="e3517-131">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="e3517-132">Selezionare **Accetto** quando viene visualizzata la finestra di dialogo contratto di licenza.</span><span class="sxs-lookup"><span data-stu-id="e3517-132">Select **I Accept** when the license agreement dialog pops up.</span></span>

>[!NOTE]
><span data-ttu-id="e3517-133">La versione **1. x.** x del pacchetto NuGet è ancora disponibile per gli sviluppatori che desiderano utilizzare HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="e3517-133">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="e3517-134">Per informazioni dettagliate, vedere [aggiungere la comunicazione remota olografica (HoloLens (1st Gen))](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="e3517-134">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="e3517-135">Creare il contesto remoto</span><span class="sxs-lookup"><span data-stu-id="e3517-135">Create the remote context</span></span>

<span data-ttu-id="e3517-136">Come primo passaggio, l'applicazione deve creare un contesto remoto.</span><span class="sxs-lookup"><span data-stu-id="e3517-136">As a first step the application should create a remote context.</span></span>

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
><span data-ttu-id="e3517-137">La comunicazione remota olografica funziona sostituendo il runtime della realtà mista di Windows che fa parte di Windows con un runtime specifico di .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="e3517-137">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="e3517-138">Questa operazione viene eseguita durante la creazione del contesto remoto.</span><span class="sxs-lookup"><span data-stu-id="e3517-138">This is done during the creation of the remote context.</span></span> <span data-ttu-id="e3517-139">Per questo motivo qualsiasi chiamata a qualsiasi API di realtà mista di Windows prima di creare il contesto remoto può causare un comportamento imprevisto.</span><span class="sxs-lookup"><span data-stu-id="e3517-139">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="e3517-140">L'approccio consigliato consiste nel creare il contesto remoto il prima possibile prima di interagire con qualsiasi API di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="e3517-140">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="e3517-141">Non combinare mai oggetti creati o recuperati tramite qualsiasi API di realtà mista di Windows prima della chiamata a CreateRemoteContext con gli oggetti creati o recuperati in seguito.</span><span class="sxs-lookup"><span data-stu-id="e3517-141">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="e3517-142">Successivamente, è necessario creare lo spazio olografico.</span><span class="sxs-lookup"><span data-stu-id="e3517-142">Next the holographic space needs to be created.</span></span> <span data-ttu-id="e3517-143">La specifica di un CoreWindow non è obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="e3517-143">Specifying a CoreWindow isn't required.</span></span> <span data-ttu-id="e3517-144">Le app desktop che non dispongono di un CoreWindow possono semplicemente passare un ```nullptr``` .</span><span class="sxs-lookup"><span data-stu-id="e3517-144">Desktop apps that don't have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="e3517-145">Connetti al dispositivo</span><span class="sxs-lookup"><span data-stu-id="e3517-145">Connect to the device</span></span>

<span data-ttu-id="e3517-146">Quando l'app remota è pronta per il rendering del contenuto, è possibile stabilire una connessione al dispositivo Player.</span><span class="sxs-lookup"><span data-stu-id="e3517-146">When the remote app is ready for rendering content a connection to the player device can be established.</span></span>

<span data-ttu-id="e3517-147">La connessione può essere eseguita in uno dei due modi seguenti.</span><span class="sxs-lookup"><span data-stu-id="e3517-147">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="e3517-148">L'app remota si connette al lettore in esecuzione sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e3517-148">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="e3517-149">Il lettore in esecuzione sul dispositivo si connette all'app remota.</span><span class="sxs-lookup"><span data-stu-id="e3517-149">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="e3517-150">Per stabilire una connessione dall'app remota al dispositivo Player, chiamare il ```Connect``` metodo sul contesto remoto specificando il nome host e la porta.</span><span class="sxs-lookup"><span data-stu-id="e3517-150">To establish a connection from the remote app to the player device call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="e3517-151">La porta usata dal lettore di comunicazione remota olografica è **8265**.</span><span class="sxs-lookup"><span data-stu-id="e3517-151">The port used by the Holographic Remoting Player is **8265**.</span></span>

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
><span data-ttu-id="e3517-152">Come per qualsiasi API C++/WinRT, ```Connect``` può generare un WinRT:: hresult_error che deve essere gestito.</span><span class="sxs-lookup"><span data-stu-id="e3517-152">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="e3517-153">Per evitare di usare la proiezione del linguaggio [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/) ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` , è possibile includere il file che si trova all'interno del pacchetto NuGet di comunicazione remota olografica.</span><span class="sxs-lookup"><span data-stu-id="e3517-153">To avoid using [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="e3517-154">Contiene le dichiarazioni delle interfacce COM sottostanti.</span><span class="sxs-lookup"><span data-stu-id="e3517-154">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="e3517-155">Tuttavia, è consigliabile utilizzare C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="e3517-155">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="e3517-156">L'ascolto delle connessioni in ingresso nell'app remota può essere eseguito chiamando il ```Listen``` metodo.</span><span class="sxs-lookup"><span data-stu-id="e3517-156">Listening for incoming connections on the remote app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="e3517-157">Durante questa chiamata è possibile specificare sia la porta di handshake che la porta di trasporto.</span><span class="sxs-lookup"><span data-stu-id="e3517-157">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="e3517-158">La porta di handshake viene utilizzata per l'handshake iniziale.</span><span class="sxs-lookup"><span data-stu-id="e3517-158">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="e3517-159">I dati vengono quindi inviati tramite la porta di trasporto.</span><span class="sxs-lookup"><span data-stu-id="e3517-159">The data is then sent over the transport port.</span></span> <span data-ttu-id="e3517-160">Per impostazione predefinita vengono usati **8265** e **8266** .</span><span class="sxs-lookup"><span data-stu-id="e3517-160">By default **8265** and **8266** are used.</span></span>

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
><span data-ttu-id="e3517-161">Il contenuto del ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` pacchetto NuGet contiene la documentazione dettagliata per l'API esposta dalla comunicazione remota olografica.</span><span class="sxs-lookup"><span data-stu-id="e3517-161">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="e3517-162">Gestione di eventi specifici della comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="e3517-162">Handling Remoting specific events</span></span>

<span data-ttu-id="e3517-163">Il contesto remoto espone tre eventi, che sono importanti per monitorare lo stato di una connessione.</span><span class="sxs-lookup"><span data-stu-id="e3517-163">The remote context exposes three events, which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="e3517-164">OnConnected: attivato quando una connessione al dispositivo è stata stabilita correttamente.</span><span class="sxs-lookup"><span data-stu-id="e3517-164">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="e3517-165">Disconnected: attivato se una connessione stabilita è chiusa o non è stato possibile stabilire una connessione.</span><span class="sxs-lookup"><span data-stu-id="e3517-165">OnDisconnected: Triggered if an established connection is closed or a connection couldn't be established.</span></span>
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
3) <span data-ttu-id="e3517-166">Onlistening: durante l'ascolto delle connessioni in ingresso viene avviato.</span><span class="sxs-lookup"><span data-stu-id="e3517-166">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="e3517-167">Inoltre, è possibile eseguire query sullo stato della connessione utilizzando la ```ConnectionState``` proprietà nel contesto remoto.</span><span class="sxs-lookup"><span data-stu-id="e3517-167">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="e3517-168">Gestione degli eventi di sintesi vocale</span><span class="sxs-lookup"><span data-stu-id="e3517-168">Handling speech events</span></span>

<span data-ttu-id="e3517-169">Usando l'interfaccia di sintesi vocale remota è possibile registrare trigger di sintesi vocale con HoloLens 2 e renderli remoti all'applicazione remota.</span><span class="sxs-lookup"><span data-stu-id="e3517-169">Using the remote speech interface it's possible to register speech triggers with HoloLens 2 and have them remoted to the remote application.</span></span>

<span data-ttu-id="e3517-170">Questo membro aggiuntivo è necessario per tenere traccia dello stato del discorso remoto.</span><span class="sxs-lookup"><span data-stu-id="e3517-170">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="e3517-171">Prima di tutto è necessario recuperare l'interfaccia vocale remota.</span><span class="sxs-lookup"><span data-stu-id="e3517-171">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="e3517-172">Utilizzando un metodo helper asincrono è quindi possibile inizializzare il riconoscimento vocale remoto.</span><span class="sxs-lookup"><span data-stu-id="e3517-172">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="e3517-173">Questa operazione deve essere eseguita in modo asincrono perché l'inizializzazione potrebbe richiedere una quantità di tempo considerevole.</span><span class="sxs-lookup"><span data-stu-id="e3517-173">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="e3517-174">[Le operazioni di concorrenza e asincrone con c++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency) spiegano come creare funzioni asincrone con c++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="e3517-174">[Concurrency and asynchronous operations with C++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

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

<span data-ttu-id="e3517-175">Esistono due modi per specificare le frasi da riconoscere.</span><span class="sxs-lookup"><span data-stu-id="e3517-175">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="e3517-176">Specifica all'interno di un file XML di grammatica vocale.</span><span class="sxs-lookup"><span data-stu-id="e3517-176">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="e3517-177">Per informazioni dettagliate, vedere [come creare una grammatica XML di base](/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) .</span><span class="sxs-lookup"><span data-stu-id="e3517-177">See [How to create a basic XML Grammar](/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="e3517-178">Specificare passandoli all'interno del vettore del dizionario a ```ApplyParameters``` .</span><span class="sxs-lookup"><span data-stu-id="e3517-178">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="e3517-179">All'interno del callback OnRecognizedSpeech, gli eventi di riconoscimento vocale possono essere elaborati:</span><span class="sxs-lookup"><span data-stu-id="e3517-179">Inside the OnRecognizedSpeech callback, the speech events can then be processed:</span></span>

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

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="e3517-180">Anteprima del contenuto trasmesso localmente</span><span class="sxs-lookup"><span data-stu-id="e3517-180">Preview streamed content locally</span></span>

<span data-ttu-id="e3517-181">Per visualizzare lo stesso contenuto nell'app remota inviata al dispositivo ```OnSendFrame``` , è possibile usare l'evento del contesto remoto.</span><span class="sxs-lookup"><span data-stu-id="e3517-181">To display the same content in the remote app that is sent to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="e3517-182">L' ```OnSendFrame``` evento viene attivato ogni volta che la libreria remota olografica invia il frame corrente al dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="e3517-182">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="e3517-183">Questo è il momento ideale per eseguire il contenuto, blit anche nella finestra desktop o UWP.</span><span class="sxs-lookup"><span data-stu-id="e3517-183">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

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

## <a name="depth-reprojection"></a><span data-ttu-id="e3517-184">Riproiezione profondità</span><span class="sxs-lookup"><span data-stu-id="e3517-184">Depth Reprojection</span></span>

<span data-ttu-id="e3517-185">A partire dalla versione [2.1.0](holographic-remoting-version-history.md#v2.1.0), la comunicazione remota olografica supporta la [riproiezione approfondita](hologram-stability.md#reprojection).</span><span class="sxs-lookup"><span data-stu-id="e3517-185">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0), Holographic Remoting supports [Depth Reprojection](hologram-stability.md#reprojection).</span></span> <span data-ttu-id="e3517-186">Questa operazione richiede che sia il buffer di colore che il buffer di profondità vengano trasmessi dall'applicazione remota a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e3517-186">This requires both the color buffer and depth buffer to be streamed from the Remote application to the HoloLens 2.</span></span> <span data-ttu-id="e3517-187">Per impostazione predefinita, il flusso del buffer di profondità è abilitato e configurato per utilizzare la metà della risoluzione del buffer di colore.</span><span class="sxs-lookup"><span data-stu-id="e3517-187">By default depth buffer streaming is enabled and configured to use half the resolution of the color buffer.</span></span> <span data-ttu-id="e3517-188">Questo può essere modificato come segue:</span><span class="sxs-lookup"><span data-stu-id="e3517-188">This can be changed as follows:</span></span>

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

<span data-ttu-id="e3517-189">Si noti che se i valori predefiniti non devono essere usati, ```ConfigureDepthVideoStream``` è necessario chiamare prima di stabilire una connessione a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e3517-189">Note, if default values should not be used ```ConfigureDepthVideoStream``` must be called before establishing a connection to the HoloLens 2.</span></span> <span data-ttu-id="e3517-190">Il posto migliore è quello giusto dopo aver creato il contesto remoto.</span><span class="sxs-lookup"><span data-stu-id="e3517-190">The best place is right after you have created the remote context.</span></span> <span data-ttu-id="e3517-191">I valori possibili per DepthBufferStreamResolution sono:</span><span class="sxs-lookup"><span data-stu-id="e3517-191">Possible values for DepthBufferStreamResolution are:</span></span>

* <span data-ttu-id="e3517-192">Full_Resolution</span><span class="sxs-lookup"><span data-stu-id="e3517-192">Full_Resolution</span></span>
* <span data-ttu-id="e3517-193">Half_Resolution</span><span class="sxs-lookup"><span data-stu-id="e3517-193">Half_Resolution</span></span>
* <span data-ttu-id="e3517-194">Quarter_Resolution</span><span class="sxs-lookup"><span data-stu-id="e3517-194">Quarter_Resolution</span></span>
* <span data-ttu-id="e3517-195">Disabilitato (aggiunto con la versione [2.1.3](holographic-remoting-version-history.md#v2.1.3) e se utilizzato non viene creato alcun flusso video di profondità aggiuntivo)</span><span class="sxs-lookup"><span data-stu-id="e3517-195">Disabled (added with version [2.1.3](holographic-remoting-version-history.md#v2.1.3) and if used no additional depth video stream is created)</span></span>

<span data-ttu-id="e3517-196">Tenere presente che l'uso di un buffer di profondità di risoluzione completa influiscono anche sui requisiti della larghezza di banda e deve essere considerato nel valore della larghezza di banda massima fornito a ```CreateRemoteContext``` .</span><span class="sxs-lookup"><span data-stu-id="e3517-196">Keep in mind that using a full resolution depth buffer also affects bandwidth requirements and needs to be accounted for in the maximum bandwidth value you provide to ```CreateRemoteContext```.</span></span>

<span data-ttu-id="e3517-197">Oltre a configurare la risoluzione, è inoltre necessario eseguire il commit di un buffer di profondità tramite [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span><span class="sxs-lookup"><span data-stu-id="e3517-197">Beside configuring the resolution, you also have to commit a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>

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

<span data-ttu-id="e3517-198">Per verificare se la riproiezione approfondita funziona correttamente in HoloLens 2, è possibile abilitare un visualizzatore di profondità tramite il portale del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e3517-198">To verify if depth reprojection is correctly working on HoloLens 2, you can enable a depth visualizer via the Device Portal.</span></span> <span data-ttu-id="e3517-199">Per informazioni dettagliate, vedere [Verifica della profondità](hologram-stability.md#verifying-depth-is-set-correctly) .</span><span class="sxs-lookup"><span data-stu-id="e3517-199">See [Verifying Depth is Set Correctly](hologram-stability.md#verifying-depth-is-set-correctly) for details.</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="e3517-200">Facoltativo: canali di dati personalizzati</span><span class="sxs-lookup"><span data-stu-id="e3517-200">Optional: Custom data channels</span></span>

<span data-ttu-id="e3517-201">I canali di dati personalizzati possono essere utilizzati per inviare dati utente tramite la connessione remota già stabilita.</span><span class="sxs-lookup"><span data-stu-id="e3517-201">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="e3517-202">Per ulteriori informazioni, vedere [canali di dati personalizzati](holographic-remoting-custom-data-channels.md) .</span><span class="sxs-lookup"><span data-stu-id="e3517-202">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3517-203">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e3517-203">See Also</span></span>
* [<span data-ttu-id="e3517-204">Scrivere un'app lettore Holographic Remoting personalizzata</span><span class="sxs-lookup"><span data-stu-id="e3517-204">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="e3517-205">Canali di dati di Holographic Remoting personalizzati</span><span class="sxs-lookup"><span data-stu-id="e3517-205">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="e3517-206">Stabilire una connessione sicura con Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="e3517-206">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="e3517-207">Limitazioni e risoluzione dei problemi di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="e3517-207">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="e3517-208">Condizioni di licenza software per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="e3517-208">Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="e3517-209">Informativa sulla privacy di Microsoft</span><span class="sxs-lookup"><span data-stu-id="e3517-209">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)