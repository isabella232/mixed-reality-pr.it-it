---
title: Funzionalità supportate per il plug-in OpenXR in Unity
description: Scopri le funzionalità supportate da OpenXR per lo sviluppo di realtà miste in Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realtà mista, MRTK, Toolkit per realtà mista, realtà aumentata, realtà virtuale, cuffie con realtà mista, informazioni, esercitazione, introduzione
ms.openlocfilehash: bad18c5f30465120bce370aa91c13ff3f229bef6
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496144"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="53621-104">Realtà mista OpenXR le funzionalità supportate in Unity</span><span class="sxs-lookup"><span data-stu-id="53621-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="53621-105">Il pacchetto di plug-in OpenXR per la **realtà mista** è un'estensione del plug-in **OpenXR** di Unity e supporta una suite di funzionalità per gli auricolari per la realtà mista HoloLens 2 e Windows.</span><span class="sxs-lookup"><span data-stu-id="53621-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="53621-106">Prima di continuare, assicurarsi di avere installato **unity 2020,2** o versione successiva, la versione del plug-in **OpenXR 0.1.3 o versione** successiva e che il progetto Unity sia [configurato per OpenXR](openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="53621-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.3** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="53621-107">Attività supportate</span><span class="sxs-lookup"><span data-stu-id="53621-107">What's supported</span></span>

<span data-ttu-id="53621-108">Attualmente sono supportate le funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="53621-108">The following features are currently supported:</span></span>

* <span data-ttu-id="53621-109">Supporta le applicazioni UWP per HoloLens 2 e l'ottimizzazione per il modello di applicazione HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="53621-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="53621-110">Supporta le applicazioni Win32 VR per l'auricolare di realtà mista Windows con i profili controller più recenti e la comunicazione remota delle app olografiche</span><span class="sxs-lookup"><span data-stu-id="53621-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="53621-111">Rilevamento della scalabilità globale tramite ancoraggi e spazio non vincolato.</span><span class="sxs-lookup"><span data-stu-id="53621-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="53621-112">[API di archiviazione di ancoraggio per salvare](#anchors-and-anchor-persistence) in modo permanente gli ancoraggi nell'archivio locale HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="53621-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="53621-113">[Motion controller e Hand Interactions](#motion-controller-and-hand-interactions), incluso il nuovo controller HP Reverb G2.</span><span class="sxs-lookup"><span data-stu-id="53621-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="53621-114">Tracciatura manuale articolata con 26 giunzioni e input RADIUS Uniti.</span><span class="sxs-lookup"><span data-stu-id="53621-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="53621-115">Interazione con gli occhi su HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="53621-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="53621-116">Individuazione della fotocamera Photo/video (PV) in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="53621-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="53621-117">Acquisizione di realtà mista tramite il rendering di 3 occhi attraverso la fotocamera FV.</span><span class="sxs-lookup"><span data-stu-id="53621-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="53621-118">Supporta ["Play" in HoloLens 2 con l'app di comunicazione remota olografica](#holographic-remoting-in-unity-editor-play-mode), consentendo agli sviluppatori di eseguire il debug degli script senza compilare e distribuire nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="53621-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="53621-119">Compatibile con MRTK Unity 2.5.3 e versioni successive tramite il [supporto del provider OpenXR MRTK](openxr-getting-started.md#using-mrtk-with-openxr-support).</span><span class="sxs-lookup"><span data-stu-id="53621-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="53621-120">Compatibile con Unity [ARFoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="53621-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later.</span></span>
* <span data-ttu-id="53621-121">(Aggiunto in 0.1.3) Supporta la [comunicazione remota olografica dell'app desktop](#holographic-remoting-in-desktop-app) da un'app autonoma Windows compilata e distribuita.</span><span class="sxs-lookup"><span data-stu-id="53621-121">(Added in 0.1.3) Supports [desktop app Holographic Remoting](#holographic-remoting-in-desktop-app) from a built and deployed Windows Standalone app.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="53621-122">Configurazione della comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="53621-122">Holographic Remoting setup</span></span>

1. <span data-ttu-id="53621-123">Per prima cosa, è necessario [installare l'app del lettore di comunicazione remota olografica](https://www.microsoft.com/store/productId/9NBLGGH4SV40) dal Microsoft Store nel HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="53621-123">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="53621-124">Eseguire l'app del lettore di comunicazione remota olografica in HoloLens 2 per visualizzare il numero di versione e l'indirizzo IP per la connessione</span><span class="sxs-lookup"><span data-stu-id="53621-124">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="53621-125">Per usare il plug-in OpenXR, è necessario usare la versione 2.4 o successiva.</span><span class="sxs-lookup"><span data-stu-id="53621-125">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Screenshot del lettore di comunicazione remota olografico in esecuzione in HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="53621-127">Comunicazione remota olografica in modalità di riproduzione dell'editor Unity</span><span class="sxs-lookup"><span data-stu-id="53621-127">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="53621-128">La creazione di un progetto Unity UWP nel progetto di Visual Studio e quindi la creazione del pacchetto e la distribuzione in un dispositivo HoloLens 2 possono richiedere del tempo.</span><span class="sxs-lookup"><span data-stu-id="53621-128">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="53621-129">Una soluzione consiste nell'abilitare la funzionalità di comunicazione remota dell'editor olografica, che consente di eseguire il debug dello script C# usando la modalità "Play" direttamente in un dispositivo HoloLens 2 sulla rete.</span><span class="sxs-lookup"><span data-stu-id="53621-129">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="53621-130">Questo scenario consente di evitare il sovraccarico dovuto alla creazione e alla distribuzione di un pacchetto UWP nel dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="53621-130">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="53621-131">Seguire i passaggi dell' [installazione di comunicazione remota olografica](#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="53621-131">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="53621-132">Aprire la finestra di dialogo **modifica-> impostazioni progetto**, passare alla **Gestione plug-in XR** e selezionare la casella **set di funzionalità di realtà mista di Windows** :</span><span class="sxs-lookup"><span data-stu-id="53621-132">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con la gestione dei plug-in di XR evidenziata](images/openxr-features-img-02.png)

3. <span data-ttu-id="53621-134">Espandere la sezione **funzionalità** in **OpenXR** e selezionare **Mostra tutto**</span><span class="sxs-lookup"><span data-stu-id="53621-134">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="53621-135">Controllare la casella di controllo **Remote editor olografico** e immettere l'indirizzo IP ottenuto dall'app di comunicazione remota olografica:</span><span class="sxs-lookup"><span data-stu-id="53621-135">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con le funzionalità evidenziate](images/openxr-features-img-03.png)

<span data-ttu-id="53621-137">A questo punto è possibile fare clic sul pulsante "Riproduci" per riprodurre l'app Unity nell'app per la comunicazione remota olografica nella HoloLens.</span><span class="sxs-lookup"><span data-stu-id="53621-137">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="53621-138">È anche possibile [aggiungere Visual Studio a Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) per eseguire il debug degli script C# in modalità Play.</span><span class="sxs-lookup"><span data-stu-id="53621-138">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="53621-139">A partire dalla versione 0.1.0, il runtime di comunicazione remota olografica non supporta ancoraggi e le funzionalità di ARAnchorManager non funzioneranno tramite la comunicazione remota.</span><span class="sxs-lookup"><span data-stu-id="53621-139">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="53621-140">Questa funzionalità è disponibile nelle versioni future.</span><span class="sxs-lookup"><span data-stu-id="53621-140">This feature is coming in future releases.</span></span>

## <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="53621-141">Comunicazione remota olografica nell'app desktop</span><span class="sxs-lookup"><span data-stu-id="53621-141">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="53621-142">Il supporto per la comunicazione remota delle app autonome di Windows è stato aggiunto nella versione del pacchetto 0.1.3.</span><span class="sxs-lookup"><span data-stu-id="53621-142">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="53621-143">A partire dalla versione 0.1.3, questa funzionalità non supporta le compilazioni UWP.</span><span class="sxs-lookup"><span data-stu-id="53621-143">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="53621-144">Seguire i passaggi dell' [installazione di comunicazione remota olografica](#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="53621-144">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="53621-145">Aprire **le impostazioni del progetto Edit->**, passare a **Gestione plug-in XR** e selezionare la casella **set di funzionalità di realtà mista di Windows** .</span><span class="sxs-lookup"><span data-stu-id="53621-145">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="53621-146">Deselezionare anche **Initialize XR all'avvio**:</span><span class="sxs-lookup"><span data-stu-id="53621-146">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con Initialize XR all'avvio deselezionato](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="53621-148">Espandere la sezione **funzionalità** in **OpenXR** e selezionare **Mostra tutto**</span><span class="sxs-lookup"><span data-stu-id="53621-148">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="53621-149">Selezionare la casella di controllo **Remote app Remoting** :</span><span class="sxs-lookup"><span data-stu-id="53621-149">Check the **Holographic App Remoting** checkbox:</span></span>

    ![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con la comunicazione remota delle app abilitata](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="53621-151">Scrivere quindi del codice per impostare la configurazione remota e attivare l'inizializzazione di XR.</span><span class="sxs-lookup"><span data-stu-id="53621-151">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="53621-152">L'app di esempio distribuita con il plug-in di [OpenXR realtà mista](openxr-getting-started.md#hololens-2-samples) contiene AppRemoting.cs, che mostra uno scenario di esempio per la connessione a un indirizzo IP specifico in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="53621-152">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#hololens-2-samples) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="53621-153">Se si distribuisce l'app di esempio in un computer locale, in questa fase verrà visualizzato un campo di input dell'indirizzo IP con un pulsante Connetti.</span><span class="sxs-lookup"><span data-stu-id="53621-153">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="53621-154">Digitando un indirizzo IP e facendo clic su Connetti verrà inizializzato XR e si tenterà di connettersi al dispositivo di destinazione:</span><span class="sxs-lookup"><span data-stu-id="53621-154">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![Screenshot dell'app di esempio che Visualizza l'interfaccia utente remota dell'app di esempio](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="53621-156">Per scrivere codice di connessione personalizzato, chiamare `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` con un oggetto compilato `RemotingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="53621-156">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="53621-157">L'app di esempio espone questo oggetto nel controllo e Mostra come compilare l'indirizzo IP da un campo di testo.</span><span class="sxs-lookup"><span data-stu-id="53621-157">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="53621-158">La chiamata a `Connect` imposterà la configurazione e inizializza automaticamente XR, motivo per cui deve essere chiamata come coroutine:</span><span class="sxs-lookup"><span data-stu-id="53621-158">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="53621-159">Durante l'esecuzione, è possibile ottenere lo stato di connessione corrente con l' `AppRemoting.TryGetConnectionState` API e, facoltativamente, disconnettere e deinizializzare XR usando `AppRemoting.Disconnect()` .</span><span class="sxs-lookup"><span data-stu-id="53621-159">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="53621-160">Questa operazione può essere usata per disconnettersi e riconnettersi a un dispositivo diverso all'interno della stessa sessione dell'app.</span><span class="sxs-lookup"><span data-stu-id="53621-160">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="53621-161">L'app di esempio fornisce un cubo selezionabile che consente di disconnettere la sessione remota, se toccata.</span><span class="sxs-lookup"><span data-stu-id="53621-161">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="53621-162">Migrazione da API precedenti</span><span class="sxs-lookup"><span data-stu-id="53621-162">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="53621-163">UnityEngine. XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="53621-163">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="53621-164">Dal codice di esempio sui [documenti di Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span><span class="sxs-lookup"><span data-stu-id="53621-164">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="53621-165">XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="53621-165">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="53621-166">OpenXR. Remoting. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="53621-166">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="53621-167">[N/A: si verifica automaticamente quando si chiama `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="53621-167">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="53621-168">UnityEngine. XR. WindowsMR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="53621-168">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="53621-169">XR. WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="53621-169">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="53621-170">OpenXR. Remoting. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="53621-170">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="53621-171">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` e `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="53621-171">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="53621-172">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="53621-172">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="53621-173">Passato in `AppRemoting.Connect` tramite lo `RemotingConfiguration` struct</span><span class="sxs-lookup"><span data-stu-id="53621-173">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="53621-174">Ancoraggi e persistenza di ancoraggio</span><span class="sxs-lookup"><span data-stu-id="53621-174">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="53621-175">Il plug-in di OpenXR realtà mista fornisce la funzionalità di ancoraggio di base tramite un'implementazione di ARFoundation **ARAnchorManager** di Unity.</span><span class="sxs-lookup"><span data-stu-id="53621-175">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="53621-176">Per apprendere le nozioni di base su **ARAnchor** in ARFoundation, vedere il [Manuale di ARFoundation per AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="53621-176">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="53621-177">A partire dalla versione 0.1.0, questo plug-in supporta tutte le funzionalità di ARAnchorManager, ad eccezione della creazione di ancoraggi collegati a un piano, che sarà disponibile in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="53621-177">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="53621-178">Persistenza di ancoraggio e XRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="53621-178">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="53621-179">Un'API aggiuntiva denominata **XRAnchorStore** consente di salvare in modo permanente gli ancoraggi tra le sessioni.</span><span class="sxs-lookup"><span data-stu-id="53621-179">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="53621-180">XRAnchorStore è una rappresentazione degli ancoraggi salvati nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="53621-180">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="53621-181">Gli ancoraggi possono essere salvati in permanenza da **ARAnchors** nella scena Unity, caricati dall'archiviazione in nuovi **ARAnchors** o eliminati dall'archivio.</span><span class="sxs-lookup"><span data-stu-id="53621-181">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="53621-182">Questi ancoraggi devono essere salvati e caricati nello stesso dispositivo.</span><span class="sxs-lookup"><span data-stu-id="53621-182">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="53621-183">L'archiviazione di ancoraggio tra dispositivi verrà supportata tramite ancoraggi spaziali di Azure in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="53621-183">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="53621-184">Per caricare XRAnchorStore, il plug-in fornisce un metodo di estensione in XRAnchorSubsystem, il sottosistema di un ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="53621-184">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="53621-185">Per usare questo metodo di estensione, accedervi dal sottosistema di ARAnchorManager come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="53621-185">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="53621-186">Per un esempio completo di come salvare in modo permanente/non permanente gli ancoraggi, vedere gli script di ancoraggio-> di esempio GameObject e AnchorsSample.cs nella scena di [esempio di plug-in realtà mista OpenXR](openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="53621-186">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![Screenshot del pannello gerarchia aperto nell'editor di Unity con l'esempio Anchors evidenziato](images/openxr-features-img-04.png)

![Screenshot del pannello Inspector aperto nell'editor di Unity con lo script di esempio Anchors evidenziato](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="53621-189">Interazioni tra controller di movimento e mano</span><span class="sxs-lookup"><span data-stu-id="53621-189">Motion controller and hand interactions</span></span>

<span data-ttu-id="53621-190">Per apprendere le nozioni di base sulle interazioni tra realtà mista in Unity, vedere il [Manuale di Unity per Unity XR input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span><span class="sxs-lookup"><span data-stu-id="53621-190">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="53621-191">Questa documentazione di Unity riguarda i mapping da input specifici del controller a **InputFeatureUsage** più generalizzabili, il modo in cui possono essere identificati e categorizzati gli input XR disponibili, come leggere i dati da questi input e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="53621-191">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="53621-192">Il plug-in OpenXR per la realtà mista fornisce profili di interazione di input aggiuntivi, mappati a **InputFeatureUsage** standard, come descritto di seguito:</span><span class="sxs-lookup"><span data-stu-id="53621-192">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="53621-193">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="53621-193">InputFeatureUsage</span></span> | <span data-ttu-id="53621-194">Controller HP Reverb G2 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="53621-194">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="53621-195">Mano HoloLens (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="53621-195">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="53621-196">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="53621-196">primary2DAxis</span></span> | <span data-ttu-id="53621-197">Joystick</span><span class="sxs-lookup"><span data-stu-id="53621-197">Joystick</span></span> | |
| <span data-ttu-id="53621-198">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="53621-198">primary2DAxisClick</span></span> | <span data-ttu-id="53621-199">Joystick-fare clic</span><span class="sxs-lookup"><span data-stu-id="53621-199">Joystick - Click</span></span> | |
| <span data-ttu-id="53621-200">trigger</span><span class="sxs-lookup"><span data-stu-id="53621-200">trigger</span></span> | <span data-ttu-id="53621-201">Trigger</span><span class="sxs-lookup"><span data-stu-id="53621-201">Trigger</span></span>  | |
| <span data-ttu-id="53621-202">ridimensionamento</span><span class="sxs-lookup"><span data-stu-id="53621-202">grip</span></span> | <span data-ttu-id="53621-203">Ridimensionamento</span><span class="sxs-lookup"><span data-stu-id="53621-203">Grip</span></span> | <span data-ttu-id="53621-204">Toccare o fare pressione</span><span class="sxs-lookup"><span data-stu-id="53621-204">Air tap or squeeze</span></span> |
| <span data-ttu-id="53621-205">primaryButton</span><span class="sxs-lookup"><span data-stu-id="53621-205">primaryButton</span></span> | <span data-ttu-id="53621-206">[X/A]-premere</span><span class="sxs-lookup"><span data-stu-id="53621-206">[X/A] - Press</span></span> | <span data-ttu-id="53621-207">Simulazione del tocco</span><span class="sxs-lookup"><span data-stu-id="53621-207">Air tap</span></span> |
| <span data-ttu-id="53621-208">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="53621-208">secondaryButton</span></span> | <span data-ttu-id="53621-209">[S/B]-premere</span><span class="sxs-lookup"><span data-stu-id="53621-209">[Y/B] - Press</span></span> | |
| <span data-ttu-id="53621-210">gripButton</span><span class="sxs-lookup"><span data-stu-id="53621-210">gripButton</span></span> | <span data-ttu-id="53621-211">Pressione del pulsante</span><span class="sxs-lookup"><span data-stu-id="53621-211">Grip - Press</span></span> | |
| <span data-ttu-id="53621-212">triggerButton</span><span class="sxs-lookup"><span data-stu-id="53621-212">triggerButton</span></span> | <span data-ttu-id="53621-213">Trigger-premere</span><span class="sxs-lookup"><span data-stu-id="53621-213">Trigger - Press</span></span> | |
| <span data-ttu-id="53621-214">menuButton</span><span class="sxs-lookup"><span data-stu-id="53621-214">menuButton</span></span> | <span data-ttu-id="53621-215">Menu</span><span class="sxs-lookup"><span data-stu-id="53621-215">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="53621-216">Pose AIM e grip</span><span class="sxs-lookup"><span data-stu-id="53621-216">Aim and Grip Poses</span></span>

<span data-ttu-id="53621-217">È possibile accedere a due set di pose tramite interazioni di input OpenXR:</span><span class="sxs-lookup"><span data-stu-id="53621-217">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="53621-218">Il grip si pone per il rendering degli oggetti a mano</span><span class="sxs-lookup"><span data-stu-id="53621-218">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="53621-219">L'obiettivo si pone per puntare al mondo.</span><span class="sxs-lookup"><span data-stu-id="53621-219">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="53621-220">Altre informazioni su questa progettazione e sulle differenze tra le due pose sono reperibili nella [specifica OpenXR-sottopercorsi di input](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span><span class="sxs-lookup"><span data-stu-id="53621-220">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="53621-221">Le pose fornite da InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity** e **DeviceAngularVelocity** rappresentano tutti la postura del **grip** OpenXR.</span><span class="sxs-lookup"><span data-stu-id="53621-221">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="53621-222">InputFeatureUsages correlate alle pose del grip sono definite in [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)di Unity.</span><span class="sxs-lookup"><span data-stu-id="53621-222">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="53621-223">Le pose fornite da InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity** e **PointerAngularVelocity** rappresentano tutti il OpenXR **AIM** pose.</span><span class="sxs-lookup"><span data-stu-id="53621-223">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="53621-224">Questi InputFeatureUsages non sono definiti in alcun file C# incluso, quindi è necessario definire il proprio InputFeatureUsages come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="53621-224">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="53621-225">Haptics</span><span class="sxs-lookup"><span data-stu-id="53621-225">Haptics</span></span>

<span data-ttu-id="53621-226">Per informazioni sull'uso di haptics nel sistema di input XR di Unity, è possibile trovare la documentazione nel [Manuale di Unity per Unity XR input-haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span><span class="sxs-lookup"><span data-stu-id="53621-226">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="53621-227">Presto disponibile</span><span class="sxs-lookup"><span data-stu-id="53621-227">What's coming soon</span></span>

<span data-ttu-id="53621-228">I problemi e le funzionalità mancanti seguenti sono noti con la versione del plug-in OpenXR della realtà mista **0.1.0**.</span><span class="sxs-lookup"><span data-stu-id="53621-228">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="53621-229">Stiamo lavorando a questi e verranno rilasciate correzioni e nuove funzionalità nelle prossime versioni.</span><span class="sxs-lookup"><span data-stu-id="53621-229">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="53621-230">**ARPlaneSubsystem** non è ancora supportato.</span><span class="sxs-lookup"><span data-stu-id="53621-230">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="53621-231">Le API **ARPlaneManager**, **ARRaycastManager** e related, ad esempio **ARAnchorManager. AttachAnchor** , non sono supportate in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="53621-231">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="53621-232">L' **ancoraggio** non è ancora supportato dalla comunicazione remota olografica, ma sarà disponibile a breve in futuro.</span><span class="sxs-lookup"><span data-stu-id="53621-232">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="53621-233">Il rilevamento della **mesh manuale** , i **codici QR** e **XRMeshSubsystem** non sono ancora supportati.</span><span class="sxs-lookup"><span data-stu-id="53621-233">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="53621-234">Il supporto di **ancoraggi spaziali di Azure** è disponibile in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="53621-234">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="53621-235">**Arm64** è l'unica piattaforma supportata per le app HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="53621-235">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="53621-236">La piattaforma **ARM** sarà disponibile in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="53621-236">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="53621-237">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="53621-237">Troubleshooting</span></span>

<span data-ttu-id="53621-238">Quando si sospende e si riprende un'app Unity in HoloLens 2, l'app non può essere ripresa correttamente, il che comporta 4 puntini di rotazione nella visualizzazione HoloLens.</span><span class="sxs-lookup"><span data-stu-id="53621-238">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>

* <span data-ttu-id="53621-239">Impostare la **modalità di invio di profondità** su **None** nelle impostazioni del progetto OpenXR come soluzione alternativa</span><span class="sxs-lookup"><span data-stu-id="53621-239">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
