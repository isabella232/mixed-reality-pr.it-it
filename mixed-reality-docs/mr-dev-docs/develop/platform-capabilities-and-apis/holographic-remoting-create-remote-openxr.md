---
title: Scrittura di un'app remota olografica remota (OpenXR)
description: Informazioni su come trasmettere il rendering del contenuto remoto in un computer remoto a HoloLens 2 con app Remote Remoting con OpenXR.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica, auricolare realtà mista, cuffia a realtà mista di Windows, auricolare della realtà virtuale, NuGet
ms.openlocfilehash: 616765143309fe2a4883c1393713133fcbe2a9d5
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006491"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a><span data-ttu-id="a183a-104">Scrittura di un'app remota di comunicazione remota olografica tramite l'API OpenXR</span><span class="sxs-lookup"><span data-stu-id="a183a-104">Writing a Holographic Remoting remote app using the OpenXR API</span></span>

>[!IMPORTANT]
><span data-ttu-id="a183a-105">Questo documento descrive la creazione di un'applicazione remota per gli auricolari HoloLens 2 e Windows Mixed Reality usando l' [API OpenXR](../native/openxr.md).</span><span class="sxs-lookup"><span data-stu-id="a183a-105">This document describes the creation of a remote application for HoloLens 2 and Windows Mixed Reality headsets using the [OpenXR API](../native/openxr.md).</span></span> <span data-ttu-id="a183a-106">Le applicazioni remote per **HoloLens (1a Gen)** devono usare il pacchetto NuGet versione **1. x. x**.</span><span class="sxs-lookup"><span data-stu-id="a183a-106">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="a183a-107">Ciò implica che le applicazioni remote scritte per HoloLens 2 non sono compatibili con HoloLens 1 e viceversa.</span><span class="sxs-lookup"><span data-stu-id="a183a-107">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="a183a-108">La documentazione per HoloLens 1 è disponibile [qui](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="a183a-108">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="a183a-109">Le app di comunicazione remota olografica possono trasmettere contenuti con rendering remoto a HoloLens 2 e agli auricolari immersivi con la realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="a183a-109">Holographic Remoting apps can stream remotely rendered content to HoloLens 2 and Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="a183a-110">È inoltre possibile accedere a più risorse di sistema e integrare [visualizzazioni immersive](../../design/app-views.md) remote in software per PC desktop esistenti.</span><span class="sxs-lookup"><span data-stu-id="a183a-110">You can also access more system resources and integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="a183a-111">Un'app remota riceve un flusso di dati di input da HoloLens 2, esegue il rendering del contenuto in una visualizzazione immersiva virtuale e trasmette nuovamente i frame di contenuto a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a183a-111">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="a183a-112">La connessione viene eseguita usando il Wi-Fi standard.</span><span class="sxs-lookup"><span data-stu-id="a183a-112">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="a183a-113">La comunicazione remota olografica viene aggiunta a un'app desktop o UWP tramite un pacchetto NuGet.</span><span class="sxs-lookup"><span data-stu-id="a183a-113">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="a183a-114">È necessario codice aggiuntivo che gestisce la connessione e ne esegue il rendering in una visualizzazione immersiva.</span><span class="sxs-lookup"><span data-stu-id="a183a-114">Additional code is required which handles the connection and renders in an immersive view.</span></span> <span data-ttu-id="a183a-115">Una tipica connessione remota avrà una bassa di 50 ms di latenza.</span><span class="sxs-lookup"><span data-stu-id="a183a-115">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="a183a-116">L'App Player può segnalare la latenza in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="a183a-116">The player app can report the latency in real time.</span></span>

<span data-ttu-id="a183a-117">Tutto il codice in questa pagina e i progetti di lavoro sono disponibili nel [repository GitHub degli esempi di comunicazione remota olografica](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="a183a-117">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a183a-118">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="a183a-118">Prerequisites</span></span>

<span data-ttu-id="a183a-119">Un punto di partenza valido è un'app desktop o UWP funzionante basata su OpenXR.</span><span class="sxs-lookup"><span data-stu-id="a183a-119">A good starting point is a working OpenXR based Desktop or UWP app.</span></span> <span data-ttu-id="a183a-120">Per informazioni dettagliate, vedere la pagina relativa [all'introduzione a OpenXR](../native/openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="a183a-120">For details see [Getting started with OpenXR](../native/openxr-getting-started.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="a183a-121">Qualsiasi app che usa la comunicazione remota olografica deve essere creata per usare un [Apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)multithread.</span><span class="sxs-lookup"><span data-stu-id="a183a-121">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="a183a-122">L'uso di un [Apartment a thread singolo](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) è supportato, ma comporta prestazioni ottimali e possibilmente balbettanti durante la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="a183a-122">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="a183a-123">Quando si usa C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) un apartment multithread è il valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="a183a-123">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="a183a-124">Ottenere il pacchetto NuGet per la comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="a183a-124">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="a183a-125">I passaggi seguenti sono necessari per aggiungere il pacchetto NuGet a un progetto in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a183a-125">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="a183a-126">Aprire il progetto in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a183a-126">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="a183a-127">Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Gestisci pacchetti NuGet...**</span><span class="sxs-lookup"><span data-stu-id="a183a-127">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="a183a-128">Nel pannello visualizzato selezionare **Sfoglia** e quindi cercare "comunicazione remota olografica".</span><span class="sxs-lookup"><span data-stu-id="a183a-128">In the panel that appears, select **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="a183a-129">Selezionare **Microsoft. olografic. Remoting. OpenXr**, assicurarsi di selezionare la versione **2. x.** x più recente e selezionare **Installa**.</span><span class="sxs-lookup"><span data-stu-id="a183a-129">Select **Microsoft.Holographic.Remoting.OpenXr**, ensure to pick the latest **2.x.x** version and select **Install**.</span></span>
5. <span data-ttu-id="a183a-130">Se viene visualizzata la finestra di dialogo **Anteprima** , fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="a183a-130">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="a183a-131">Selezionare **Accetto** quando viene visualizzata la finestra di dialogo contratto di licenza.</span><span class="sxs-lookup"><span data-stu-id="a183a-131">Select **I Accept** when the license agreement dialog pops up.</span></span>
7. <span data-ttu-id="a183a-132">Ripetere i passaggi da 3 a 6 per i pacchetti NuGet seguenti: OpenXR. Headers, OpenXR. loader</span><span class="sxs-lookup"><span data-stu-id="a183a-132">Repeat the steps 3 to 6 for the following NuGet Packages: OpenXR.Headers, OpenXR.Loader</span></span>

>[!NOTE]
><span data-ttu-id="a183a-133">La versione **1. x.** x del pacchetto NuGet è ancora disponibile per gli sviluppatori che desiderano utilizzare HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="a183a-133">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="a183a-134">Per informazioni dettagliate, vedere [aggiungere la comunicazione remota olografica (HoloLens (1st Gen))](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="a183a-134">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="select-the-holographic-remoting-openxr-runtime"></a><span data-ttu-id="a183a-135">Selezionare il runtime OpenXR di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="a183a-135">Select the Holographic Remoting OpenXR runtime</span></span>

<span data-ttu-id="a183a-136">Il primo passaggio da eseguire nell'app remota consiste nel selezionare il runtime OpenXR di comunicazione remota olografica, che fa parte del pacchetto NuGet Microsoft. Olografic. Remoting. OpenXr.</span><span class="sxs-lookup"><span data-stu-id="a183a-136">The first step you need to do in your remote app is to select the Holographic Remoting OpenXR runtime, which is part of the Microsoft.Holographic.Remoting.OpenXr NuGet package.</span></span> <span data-ttu-id="a183a-137">Questa operazione può essere eseguita impostando la ```XR_RUNTIME_JSON``` variabile di ambiente sul percorso del RemotingXR.jsnel file all'interno dell'app.</span><span class="sxs-lookup"><span data-stu-id="a183a-137">You can do this by setting the ```XR_RUNTIME_JSON``` environment variable to the path of the RemotingXR.json file within your app.</span></span> <span data-ttu-id="a183a-138">Questa variabile di ambiente viene usata dal caricatore OpenXR per non usare il runtime OpenXR predefinito del sistema, ma viene invece reindirizzato al runtime OpenXR della comunicazione remota olografica.</span><span class="sxs-lookup"><span data-stu-id="a183a-138">This environment variable is used by the OpenXR loader to not use the system default OpenXR runtime but instead redirect to the Holographic Remoting OpenXR runtime.</span></span> <span data-ttu-id="a183a-139">Quando si usa il pacchetto NuGet Microsoft. Olografic. Remoting. OpenXr, il RemotingXR.jsnel file viene copiato automaticamente durante la compilazione nella cartella di output, la selezione del runtime di OpenXR è in genere simile alla seguente.</span><span class="sxs-lookup"><span data-stu-id="a183a-139">When using the Microsoft.Holographic.Remoting.OpenXr NuGet package the RemotingXR.json file is automatically copied during compilation to the output folder, the OpenXR runtime selection typically looks as follows.</span></span>

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

## <a name="create-xrinstance-with-holographic-remoting-extension"></a><span data-ttu-id="a183a-140">Creare XrInstance con estensione per la comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="a183a-140">Create XrInstance with Holographic Remoting Extension</span></span>

<span data-ttu-id="a183a-141">Il primo passaggio di un'app OpenXR tipica consiste nel selezionare le estensioni OpenXR e creare un XrInstance.</span><span class="sxs-lookup"><span data-stu-id="a183a-141">The first step a typical OpenXR app is supposed to do is to select OpenXR extensions and create an XrInstance.</span></span> <span data-ttu-id="a183a-142">La specifica OpenXR Core non fornisce alcuna API per servizi remoti specifici.</span><span class="sxs-lookup"><span data-stu-id="a183a-142">The OpenXR core specification doesn't provide any remoting specific API.</span></span> <span data-ttu-id="a183a-143">Per questo motivo, la comunicazione remota olografica introduce una propria estensione OpenXR denominata ```XR_MSFT_holographic_remoting``` .</span><span class="sxs-lookup"><span data-stu-id="a183a-143">For that reason Holographic Remoting introduces its own OpenXR extension named ```XR_MSFT_holographic_remoting```.</span></span> <span data-ttu-id="a183a-144">Assicurarsi che quando si chiama xrCreateInstance ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` sia incluso in XrInstanceCreateInfo.</span><span class="sxs-lookup"><span data-stu-id="a183a-144">Ensure that when you call xrCreateInstance the ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` is included in the XrInstanceCreateInfo.</span></span>

>[!TIP]
><span data-ttu-id="a183a-145">Per impostazione predefinita, il contenuto di cui è stato eseguito il rendering dell'app viene trasmesso solo al lettore di comunicazione remota olografico in esecuzione su un HoloLens 2 o su un headset di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="a183a-145">By default the rendered content of your app is only streamed to the Holographic Remoting player either running on a HoloLens 2 or on a Windows Mixed Reality headsets.</span></span> <span data-ttu-id="a183a-146">Per visualizzare anche il contenuto sottoposto a rendering nel computer remoto, tramite una catena di scambio di una finestra, ad esempio, la comunicazione remota olografica fornisce una seconda estensione OpenXR denominata ```XR_MSFT_holographic_remoting_frame_mirroring``` .</span><span class="sxs-lookup"><span data-stu-id="a183a-146">To also display the rendered content on the remote PC, via a swap-chain of a window for instance, Holographic Remoting provides a second OpenXR extension named ```XR_MSFT_holographic_remoting_frame_mirroring```.</span></span> <span data-ttu-id="a183a-147">Assicurarsi di abilitare anche questa estensione usando ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` nel caso in cui si desideri usare tale funzionalità.</span><span class="sxs-lookup"><span data-stu-id="a183a-147">Ensure to also enable this extension using ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` in case you want to use that functionality.</span></span>

>[!IMPORTANT]
><span data-ttu-id="a183a-148">Per informazioni sull'API dell'estensione OpenXR per la comunicazione remota olografica, vedere la [specifica](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) che si trova nel [repository GitHub degli esempi di comunicazione remota olografica](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="a183a-148">To learn about the Holographic Remoting OpenXR extension API, check out the [specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) which can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="connect-to-the-device"></a><span data-ttu-id="a183a-149">Connetti al dispositivo</span><span class="sxs-lookup"><span data-stu-id="a183a-149">Connect to the device</span></span>

<span data-ttu-id="a183a-150">Dopo che l'app remota ha creato il XrInstance ed eseguito una query su XrSystemId tramite xrGetSystem, è possibile stabilire una connessione al dispositivo Player.</span><span class="sxs-lookup"><span data-stu-id="a183a-150">After your remote app has created the XrInstance and queried the XrSystemId via xrGetSystem a connection to the player device can be established.</span></span>

>[!WARNING]
> <span data-ttu-id="a183a-151">Il runtime OpenXR di comunicazione remota olografica è in grado di fornire solo i dati specifici del dispositivo, ad esempio le configurazioni della vista o le modalità di combinazione dell'ambiente dopo aver stabilito una connessione.</span><span class="sxs-lookup"><span data-stu-id="a183a-151">The Holographic Remoting OpenXR runtime is only able to provide device specific data such as view configurations or environment blend modes after a connection has been established.</span></span> <span data-ttu-id="a183a-152">```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews``` , ```xrGetViewConfigurationProperties``` , ```xrEnumerateEnvironmentBlendModes``` e ```xrGetSystemProperties``` forniranno i valori predefiniti, corrispondenti a quello che in genere si ottiene se ci si connette a un lettore che esegue in un HoloLens 2, prima di essere completamente connessi.</span><span class="sxs-lookup"><span data-stu-id="a183a-152">```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews```, ```xrGetViewConfigurationProperties```, ```xrEnumerateEnvironmentBlendModes```, and ```xrGetSystemProperties``` will give you default values, matching what you would typically get if you connect to a player running on a HoloLens 2, before being fully connected.</span></span>
<span data-ttu-id="a183a-153">Si consiglia vivamente di non chiamare questi metodi prima che sia stata stabilita una connessione.</span><span class="sxs-lookup"><span data-stu-id="a183a-153">It is strongly recommended to not call these methods before a connection has been established.</span></span> <span data-ttu-id="a183a-154">Il suggerimento viene usato questi metodi dopo che il XrSession è stato creato correttamente e lo stato della sessione è almeno XR_SESSION_STATE_READY.</span><span class="sxs-lookup"><span data-stu-id="a183a-154">The suggestion is used these methods after the XrSession has been successfully created and the session state is at least XR_SESSION_STATE_READY.</span></span>

<span data-ttu-id="a183a-155">È possibile configurare le proprietà generali come la velocità in bit massima, l'audio abilitato, il codec video o la risoluzione del flusso del buffer di profondità tramite ```xrRemotingSetContextPropertiesMSFT``` come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="a183a-155">General properties such as max bitrate, audio enabled, video codec, or depth buffer stream resolution can be configured via ```xrRemotingSetContextPropertiesMSFT``` as follows.</span></span>

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

<span data-ttu-id="a183a-156">La connessione può essere eseguita in uno dei due modi seguenti.</span><span class="sxs-lookup"><span data-stu-id="a183a-156">The connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="a183a-157">L'app remota si connette al lettore in esecuzione sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a183a-157">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="a183a-158">Il lettore in esecuzione sul dispositivo si connette all'app remota.</span><span class="sxs-lookup"><span data-stu-id="a183a-158">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="a183a-159">Per stabilire una connessione dall'app remota al dispositivo Player, chiamare il ```xrRemotingConnectMSFT``` metodo specificando il nome host e la porta tramite la  ```XrRemotingConnectInfoMSFT``` struttura.</span><span class="sxs-lookup"><span data-stu-id="a183a-159">To establish a connection from the remote app to the player device call the ```xrRemotingConnectMSFT``` method specifying the hostname and port via the  ```XrRemotingConnectInfoMSFT``` structure.</span></span> <span data-ttu-id="a183a-160">La porta usata dal lettore di comunicazione remota olografica è **8265**.</span><span class="sxs-lookup"><span data-stu-id="a183a-160">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

<span data-ttu-id="a183a-161">L'ascolto delle connessioni in ingresso nell'app remota può essere eseguito chiamando il ```xrRemotingListenMSFT``` metodo.</span><span class="sxs-lookup"><span data-stu-id="a183a-161">Listening for incoming connections on the remote app can be done by calling the ```xrRemotingListenMSFT``` method.</span></span> <span data-ttu-id="a183a-162">È possibile specificare sia la porta di handshake che la porta di trasporto tramite la ```XrRemotingListenInfoMSFT``` struttura.</span><span class="sxs-lookup"><span data-stu-id="a183a-162">Both the handshake port and transport port can be specified via the ```XrRemotingListenInfoMSFT``` structure.</span></span> <span data-ttu-id="a183a-163">La porta di handshake viene utilizzata per l'handshake iniziale.</span><span class="sxs-lookup"><span data-stu-id="a183a-163">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="a183a-164">I dati vengono quindi inviati tramite la porta di trasporto.</span><span class="sxs-lookup"><span data-stu-id="a183a-164">The data is then sent over the transport port.</span></span> <span data-ttu-id="a183a-165">Per impostazione predefinita vengono usati **8265** e **8266** .</span><span class="sxs-lookup"><span data-stu-id="a183a-165">By default **8265** and **8266** are used.</span></span>

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

<span data-ttu-id="a183a-166">Lo stato della connessione deve essere disconnesso quando si chiama ```xrRemotingConnectMSFT``` o ```xrRemotingListenMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="a183a-166">The connection state must be disconnected when you call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT```.</span></span> <span data-ttu-id="a183a-167">È possibile ottenere lo stato di connessione in qualsiasi momento dopo aver creato un XrInstance ed eseguito una query per XrSystemId tramite ```xrRemotingGetConnectionStateMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="a183a-167">You can get the connection state at any point after you have created an XrInstance and queried for the XrSystemId via ```xrRemotingGetConnectionStateMSFT```.</span></span>

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

<span data-ttu-id="a183a-168">Gli Stati di connessione disponibili sono:</span><span class="sxs-lookup"><span data-stu-id="a183a-168">Available connection states are:</span></span>
- <span data-ttu-id="a183a-169">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="a183a-169">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span></span>
- <span data-ttu-id="a183a-170">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span><span class="sxs-lookup"><span data-stu-id="a183a-170">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span></span>
- <span data-ttu-id="a183a-171">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="a183a-171">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span></span>

>[!IMPORTANT]
> <span data-ttu-id="a183a-172">```xrRemotingConnectMSFT``` oppure ```xrRemotingListenMSFT``` deve essere chiamato prima di provare a creare un XrSession tramite xrCreateSession.</span><span class="sxs-lookup"><span data-stu-id="a183a-172">```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` must be called before trying to create a XrSession via xrCreateSession.</span></span> <span data-ttu-id="a183a-173">Se si tenta di creare un XrSession mentre lo stato della connessione è ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` la creazione della sessione avrà esito positivo, ma lo stato della sessione passerà immediatamente a XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="a183a-173">If you try to create a XrSession while the connection state is ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session creation will succeed but the session state will immediately transition to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="a183a-174">L'implementazione di comunicazione remota olografica ```xrCreateSession``` supporta l'attesa della creazione di una connessione.</span><span class="sxs-lookup"><span data-stu-id="a183a-174">Holographic Remoting's implementation of ```xrCreateSession``` supports waiting for a connection to be established.</span></span> <span data-ttu-id="a183a-175">È possibile chiamare ```xrRemotingConnectMSFT``` o ```xrRemotingListenMSFT``` immediatamente seguito da una chiamata a, che blocca e attende che venga stabilita una connessione.</span><span class="sxs-lookup"><span data-stu-id="a183a-175">You can call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` immediately followed by a call to, which will block and wait for a connection to be established.</span></span> <span data-ttu-id="a183a-176">Il timeout è fisso a 10 secondi.</span><span class="sxs-lookup"><span data-stu-id="a183a-176">The timeout is fixed to 10 seconds.</span></span> <span data-ttu-id="a183a-177">Se è possibile stabilire una connessione entro questo periodo di tempo, la creazione del XrSession avrà esito positivo e lo stato della sessione passerà a XR_SESSION_STATE_READY.</span><span class="sxs-lookup"><span data-stu-id="a183a-177">If a connection can be established within this time the XrSession creation will succeed and the session state will transition to XR_SESSION_STATE_READY.</span></span> <span data-ttu-id="a183a-178">Se non è possibile stabilire alcuna connessione, la creazione della sessione riesce anche ma passa immediatamente a XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="a183a-178">In case no connection can be established the session creation also succeeds but immediately transitions to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="a183a-179">In generale, lo stato di connessione è coppia con lo stato XrSession.</span><span class="sxs-lookup"><span data-stu-id="a183a-179">In general, the connection state is couple with the XrSession state.</span></span> <span data-ttu-id="a183a-180">Qualsiasi modifica allo stato della connessione influisca anche sullo stato della sessione.</span><span class="sxs-lookup"><span data-stu-id="a183a-180">Any change to the connection state also affects the session state.</span></span> <span data-ttu-id="a183a-181">Ad esempio, se lo stato della connessione passa da `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` a ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` stato sessione, passerà anche a XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="a183a-181">For instance, if the connection state switches from `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` to ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session state will transition to XR_SESSION_STATE_LOSS_PENDING as well.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="a183a-182">Gestione di eventi specifici della comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="a183a-182">Handling Remoting specific events</span></span>

<span data-ttu-id="a183a-183">Il runtime OpenXR di comunicazione remota olografica espone tre eventi, che sono importanti per monitorare lo stato di una connessione.</span><span class="sxs-lookup"><span data-stu-id="a183a-183">The Holographic Remoting OpenXR runtime exposes three events, which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="a183a-184">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Attivato quando una connessione al dispositivo è stata stabilita correttamente.</span><span class="sxs-lookup"><span data-stu-id="a183a-184">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Triggered when a connection to the device has been successfully established.</span></span>
2) <span data-ttu-id="a183a-185">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Attivato se una connessione stabilita è chiusa o non è stato possibile stabilire una connessione.</span><span class="sxs-lookup"><span data-stu-id="a183a-185">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Triggered if an established connection is closed or a connection couldn't be established.</span></span>
3) <span data-ttu-id="a183a-186">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: Quando viene avviata l'attesa delle connessioni in ingresso.</span><span class="sxs-lookup"><span data-stu-id="a183a-186">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: When listening for incoming connections starts.</span></span>

<span data-ttu-id="a183a-187">Questi eventi vengono inseriti in una coda e l'app remota deve leggere dalla coda con regolarità tramite ```xrPollEvent``` .</span><span class="sxs-lookup"><span data-stu-id="a183a-187">These events are placed in a queue and your remote app must read from the queue with regularity via ```xrPollEvent```.</span></span>

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

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="a183a-188">Anteprima del contenuto trasmesso localmente</span><span class="sxs-lookup"><span data-stu-id="a183a-188">Preview streamed content locally</span></span>

<span data-ttu-id="a183a-189">Per visualizzare lo stesso contenuto nell'app remota inviata al dispositivo ```XR_MSFT_holographic_remoting_frame_mirroring``` , è possibile usare l'estensione.</span><span class="sxs-lookup"><span data-stu-id="a183a-189">To display the same content in the remote app that is sent to the device the ```XR_MSFT_holographic_remoting_frame_mirroring``` extension can be used.</span></span> <span data-ttu-id="a183a-190">Con questa estensione, è possibile inviare una trama a xrEndFrame usando l'oggetto ```XrRemotingFrameMirrorImageInfoMSFT``` che non è concatenato a XrFrameEndInfo come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="a183a-190">With this extension, you can submit a texture to xrEndFrame by using the ```XrRemotingFrameMirrorImageInfoMSFT``` that isn't chained to the XrFrameEndInfo as follows.</span></span>

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

<span data-ttu-id="a183a-191">L'esempio precedente usa una trama a catena di scambio DX11 e visualizza la finestra immediatamente dopo la chiamata a xrEndFrame.</span><span class="sxs-lookup"><span data-stu-id="a183a-191">The example above uses a DX11 swap-chain texture and presents the window immediately after the call to xrEndFrame.</span></span> <span data-ttu-id="a183a-192">L'utilizzo non è limitato alle trame a catena di scambio e non è necessaria alcuna sincronizzazione aggiuntiva della GPU.</span><span class="sxs-lookup"><span data-stu-id="a183a-192">The usage isn't restricted to swap-chain textures and no additional GPU synchronization is required.</span></span> <span data-ttu-id="a183a-193">Per informazioni dettagliate sull'utilizzo e sui vincoli, vedere la [specifica dell'estensione](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span><span class="sxs-lookup"><span data-stu-id="a183a-193">For details on usage and constraints check out the [extension specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span></span>
<span data-ttu-id="a183a-194">Se l'app remota USA DX12, usare XrRemotingFrameMirrorImageD3D12MSFT anziché XrRemotingFrameMirrorImageD3D11MSFT.</span><span class="sxs-lookup"><span data-stu-id="a183a-194">If your remote app is using DX12 use XrRemotingFrameMirrorImageD3D12MSFT instead of XrRemotingFrameMirrorImageD3D11MSFT.</span></span>

## <a name="see-also"></a><span data-ttu-id="a183a-195">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a183a-195">See Also</span></span>
* [<span data-ttu-id="a183a-196">Scrivere un'app lettore Holographic Remoting personalizzata</span><span class="sxs-lookup"><span data-stu-id="a183a-196">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="a183a-197">Stabilire una connessione sicura con Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="a183a-197">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="a183a-198">Limitazioni e risoluzione dei problemi di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="a183a-198">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="a183a-199">Condizioni di licenza software per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="a183a-199">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="a183a-200">Informativa sulla privacy di Microsoft</span><span class="sxs-lookup"><span data-stu-id="a183a-200">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
