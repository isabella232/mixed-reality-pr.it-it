---
title: Comunicazione remota olografica nell'app desktop
description: Informazioni su come usare Holographic Remoting in un'app desktop con OpenXR.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realtà mista, MRTK, Mixed Reality Toolkit, realtà aumentata, realtà virtuale, visori di realtà mista, apprendimento, esercitazione, introduzione, comunicazione remota olografica, desktop
ms.openlocfilehash: b04f7e003cff41ae6970bef71c37231b2475ca75
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906727"
---
# <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="158df-104">Comunicazione remota olografica nell'app desktop</span><span class="sxs-lookup"><span data-stu-id="158df-104">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="158df-105">Il supporto per la comunicazione remota delle app autonome di Windows è stato aggiunto nella versione del pacchetto 0.1.3.</span><span class="sxs-lookup"><span data-stu-id="158df-105">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="158df-106">A causa della versione 0.1.3, questa funzionalità non supporta le compilazioni UWP.</span><span class="sxs-lookup"><span data-stu-id="158df-106">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="158df-107">Seguire la procedura descritta in [Holographic Remoting setup (Configurazione di Holographic Remoting)](unity-play-mode.md#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="158df-107">Follow the steps in [Holographic Remoting setup](unity-play-mode.md#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="158df-108">Aprire **Modifica -> Impostazioni** progetto, passare a Gestione **plug-in XR** e selezionare la Windows Mixed Reality **set di funzionalità.**</span><span class="sxs-lookup"><span data-stu-id="158df-108">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="158df-109">Deselezionare anche **Inizializza XR all'avvio**:</span><span class="sxs-lookup"><span data-stu-id="158df-109">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con l'opzione Inizializza XR all'avvio deselezionata](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="158df-111">Espandere la **sezione Funzionalità** in **OpenXR** e selezionare **Mostra tutto**</span><span class="sxs-lookup"><span data-stu-id="158df-111">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="158df-112">Selezionare la casella **di controllo Holographic App Remoting** :</span><span class="sxs-lookup"><span data-stu-id="158df-112">Check the **Holographic App Remoting** checkbox:</span></span>

    ![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con la comunicazione remota delle app abilitata](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="158df-114">Scrivere quindi codice per impostare la configurazione remota e attivare l'inizializzazione XR.</span><span class="sxs-lookup"><span data-stu-id="158df-114">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="158df-115">L'app di esempio distribuita con il [plug-in OpenXR](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) di realtà mista contiene AppRemoting.cs, che illustra uno scenario di esempio per la connessione a un indirizzo IP specifico in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="158df-115">The sample app distributed with the [Mixed Reality OpenXR Plugin](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="158df-116">La distribuzione dell'app di esempio in un computer locale a questo punto visualizza un campo di input dell'indirizzo IP con un pulsante connetti.</span><span class="sxs-lookup"><span data-stu-id="158df-116">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="158df-117">Digitando un indirizzo IP e facendo clic su Connetti si inizializza XR e si tenta di connettersi al dispositivo di destinazione:</span><span class="sxs-lookup"><span data-stu-id="158df-117">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![Screenshot dell'app di esempio che visualizza l'interfaccia utente remota dell'app di esempio](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="158df-119">Per scrivere codice di connessione personalizzato, chiamare con un `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` oggetto `RemotingConfiguration` compilato.</span><span class="sxs-lookup"><span data-stu-id="158df-119">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="158df-120">L'app di esempio lo espone nel controllo e mostra come compilare l'indirizzo IP da un campo di testo.</span><span class="sxs-lookup"><span data-stu-id="158df-120">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="158df-121">La chiamata di imposta la configurazione e inizializza automaticamente XR, motivo per cui deve `Connect` essere chiamata come coroutine:</span><span class="sxs-lookup"><span data-stu-id="158df-121">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="158df-122">Durante l'esecuzione, è possibile ottenere lo stato di connessione corrente con l'API e facoltativamente disconnettere e `AppRemoting.TryGetConnectionState` de-inizializzare XR usando `AppRemoting.Disconnect()` .</span><span class="sxs-lookup"><span data-stu-id="158df-122">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="158df-123">Può essere usato per disconnettersi e riconnettersi a un dispositivo diverso all'interno della stessa sessione dell'app.</span><span class="sxs-lookup"><span data-stu-id="158df-123">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="158df-124">L'app di esempio fornisce un cubo di esempio che disconnetterà la sessione remota, se toccato.</span><span class="sxs-lookup"><span data-stu-id="158df-124">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="158df-125">Migrazione da API precedenti</span><span class="sxs-lookup"><span data-stu-id="158df-125">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="158df-126">UnityEngine.XR.WSA.HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="158df-126">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="158df-127">Dal codice di esempio [nella documentazione di Unity:](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)</span><span class="sxs-lookup"><span data-stu-id="158df-127">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="158df-128">Xr. Wsa. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="158df-128">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="158df-129">OpenXR.Remoting.AppRemoting</span><span class="sxs-lookup"><span data-stu-id="158df-129">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="158df-130">[N/D: si verifica automaticamente quando si chiama `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="158df-130">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="158df-131">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="158df-131">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="158df-132">Xr. WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="158df-132">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="158df-133">OpenXR.Remoting.AppRemoting</span><span class="sxs-lookup"><span data-stu-id="158df-133">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="158df-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` e `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="158df-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="158df-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="158df-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="158df-136">Passato a `AppRemoting.Connect` tramite `RemotingConfiguration` lo struct</span><span class="sxs-lookup"><span data-stu-id="158df-136">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`