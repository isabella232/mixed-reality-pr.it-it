---
title: Comunicazione remota olografica nell'app desktop
description: Scopri come usare la comunicazione remota olografica in un'app desktop con OpenXR.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realtà mista, MRTK, Toolkit per realtà mista, realtà aumentata, realtà virtuale, cuffie con realtà mista, informazioni, esercitazione, Guida introduttiva, comunicazione remota olografica, desktop
ms.openlocfilehash: f3cf43d59b74b0f47e701acc1d7312544867b0df
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624320"
---
# <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="9c4ff-104">Comunicazione remota olografica nell'app desktop</span><span class="sxs-lookup"><span data-stu-id="9c4ff-104">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="9c4ff-105">Il supporto per la comunicazione remota delle app autonome di Windows è stato aggiunto nella versione del pacchetto 0.1.3.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-105">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="9c4ff-106">A partire dalla versione 0.1.3, questa funzionalità non supporta le compilazioni UWP.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-106">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="9c4ff-107">Seguire i passaggi dell' [installazione di comunicazione remota olografica](openxr-supported-features.md#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="9c4ff-107">Follow the steps in [Holographic Remoting setup](openxr-supported-features.md#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="9c4ff-108">Aprire **le impostazioni del progetto Edit->**, passare a **Gestione plug-in XR** e selezionare la casella **set di funzionalità di realtà mista di Windows** .</span><span class="sxs-lookup"><span data-stu-id="9c4ff-108">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="9c4ff-109">Deselezionare anche **Initialize XR all'avvio**:</span><span class="sxs-lookup"><span data-stu-id="9c4ff-109">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con Initialize XR all'avvio deselezionato](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="9c4ff-111">Espandere la sezione **funzionalità** in **OpenXR** e selezionare **Mostra tutto**</span><span class="sxs-lookup"><span data-stu-id="9c4ff-111">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="9c4ff-112">Selezionare la casella di controllo **Remote app Remoting** :</span><span class="sxs-lookup"><span data-stu-id="9c4ff-112">Check the **Holographic App Remoting** checkbox:</span></span>

    ![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con la comunicazione remota delle app abilitata](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="9c4ff-114">Scrivere quindi del codice per impostare la configurazione remota e attivare l'inizializzazione di XR.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-114">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="9c4ff-115">L'app di esempio distribuita con il plug-in di [OpenXR realtà mista](openxr-getting-started.md#hololens-2-samples) contiene AppRemoting.cs, che mostra uno scenario di esempio per la connessione a un indirizzo IP specifico in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-115">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#hololens-2-samples) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="9c4ff-116">Se si distribuisce l'app di esempio in un computer locale, in questa fase verrà visualizzato un campo di input dell'indirizzo IP con un pulsante Connetti.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-116">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="9c4ff-117">Digitando un indirizzo IP e facendo clic su Connetti verrà inizializzato XR e si tenterà di connettersi al dispositivo di destinazione:</span><span class="sxs-lookup"><span data-stu-id="9c4ff-117">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![Screenshot dell'app di esempio che Visualizza l'interfaccia utente remota dell'app di esempio](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="9c4ff-119">Per scrivere codice di connessione personalizzato, chiamare `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` con un oggetto compilato `RemotingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="9c4ff-119">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="9c4ff-120">L'app di esempio espone questo oggetto nel controllo e Mostra come compilare l'indirizzo IP da un campo di testo.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-120">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="9c4ff-121">La chiamata a `Connect` imposterà la configurazione e inizializza automaticamente XR, motivo per cui deve essere chiamata come coroutine:</span><span class="sxs-lookup"><span data-stu-id="9c4ff-121">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="9c4ff-122">Durante l'esecuzione, è possibile ottenere lo stato di connessione corrente con l' `AppRemoting.TryGetConnectionState` API e, facoltativamente, disconnettere e deinizializzare XR usando `AppRemoting.Disconnect()` .</span><span class="sxs-lookup"><span data-stu-id="9c4ff-122">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="9c4ff-123">Questa operazione può essere usata per disconnettersi e riconnettersi a un dispositivo diverso all'interno della stessa sessione dell'app.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-123">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="9c4ff-124">L'app di esempio fornisce un cubo selezionabile che consente di disconnettere la sessione remota, se toccata.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-124">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="9c4ff-125">Migrazione da API precedenti</span><span class="sxs-lookup"><span data-stu-id="9c4ff-125">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="9c4ff-126">UnityEngine. XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="9c4ff-126">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="9c4ff-127">Dal codice di esempio sui [documenti di Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span><span class="sxs-lookup"><span data-stu-id="9c4ff-127">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="9c4ff-128">XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="9c4ff-128">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="9c4ff-129">OpenXR. Remoting. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="9c4ff-129">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="9c4ff-130">[N/A: si verifica automaticamente quando si chiama `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="9c4ff-130">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="9c4ff-131">UnityEngine. XR. WindowsMR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="9c4ff-131">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="9c4ff-132">XR. WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="9c4ff-132">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="9c4ff-133">OpenXR. Remoting. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="9c4ff-133">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="9c4ff-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` e `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="9c4ff-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="9c4ff-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="9c4ff-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="9c4ff-136">Passato in `AppRemoting.Connect` tramite lo `RemotingConfiguration` struct</span><span class="sxs-lookup"><span data-stu-id="9c4ff-136">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`