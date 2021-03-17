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
# <a name="holographic-remoting-in-desktop-app"></a>Comunicazione remota olografica nell'app desktop

> [!NOTE]
> Il supporto per la comunicazione remota delle app autonome di Windows è stato aggiunto nella versione del pacchetto 0.1.3.
> A partire dalla versione 0.1.3, questa funzionalità non supporta le compilazioni UWP.

1. Seguire i passaggi dell' [installazione di comunicazione remota olografica](openxr-supported-features.md#holographic-remoting-setup)
2. Aprire **le impostazioni del progetto Edit->**, passare a **Gestione plug-in XR** e selezionare la casella **set di funzionalità di realtà mista di Windows** . Deselezionare anche **Initialize XR all'avvio**:

    ![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con Initialize XR all'avvio deselezionato](images/openxr-features-img-02-app.png)

3. Espandere la sezione **funzionalità** in **OpenXR** e selezionare **Mostra tutto**
4. Selezionare la casella di controllo **Remote app Remoting** :

    ![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con la comunicazione remota delle app abilitata](images/openxr-features-img-03-app.png)

5. Scrivere quindi del codice per impostare la configurazione remota e attivare l'inizializzazione di XR. L'app di esempio distribuita con il plug-in di [OpenXR realtà mista](openxr-getting-started.md#hololens-2-samples) contiene AppRemoting.cs, che mostra uno scenario di esempio per la connessione a un indirizzo IP specifico in fase di esecuzione. Se si distribuisce l'app di esempio in un computer locale, in questa fase verrà visualizzato un campo di input dell'indirizzo IP con un pulsante Connetti. Digitando un indirizzo IP e facendo clic su Connetti verrà inizializzato XR e si tenterà di connettersi al dispositivo di destinazione:

    ![Screenshot dell'app di esempio che Visualizza l'interfaccia utente remota dell'app di esempio](images/openxr-sample-app-remoting.png)

6. Per scrivere codice di connessione personalizzato, chiamare `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` con un oggetto compilato `RemotingConfiguration` . L'app di esempio espone questo oggetto nel controllo e Mostra come compilare l'indirizzo IP da un campo di testo. La chiamata a `Connect` imposterà la configurazione e inizializza automaticamente XR, motivo per cui deve essere chiamata come coroutine:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. Durante l'esecuzione, è possibile ottenere lo stato di connessione corrente con l' `AppRemoting.TryGetConnectionState` API e, facoltativamente, disconnettere e deinizializzare XR usando `AppRemoting.Disconnect()` . Questa operazione può essere usata per disconnettersi e riconnettersi a un dispositivo diverso all'interno della stessa sessione dell'app. L'app di esempio fornisce un cubo selezionabile che consente di disconnettere la sessione remota, se toccata.

### <a name="migration-from-previous-apis"></a>Migrazione da API precedenti

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine. XR. WSA. HolographicRemoting

Dal codice di esempio sui [documenti di Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):

| XR. WSA. HolographicRemoting | OpenXR. Remoting. AppRemoting |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| [N/A: si verifica automaticamente quando si chiama `AppRemoting.Connect` ]  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a>UnityEngine. XR. WindowsMR. WindowsMRRemoting

| XR. WindowsMR.WindowsMRRemoting | OpenXR. Remoting. AppRemoting |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| `WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` e `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName` | Passato in `AppRemoting.Connect` tramite lo `RemotingConfiguration` struct |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`