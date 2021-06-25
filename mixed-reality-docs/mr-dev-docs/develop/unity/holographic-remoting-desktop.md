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
# <a name="holographic-remoting-in-desktop-app"></a>Comunicazione remota olografica nell'app desktop

> [!NOTE]
> Il supporto per la comunicazione remota delle app autonome di Windows è stato aggiunto nella versione del pacchetto 0.1.3.
> A causa della versione 0.1.3, questa funzionalità non supporta le compilazioni UWP.

1. Seguire la procedura descritta in [Holographic Remoting setup (Configurazione di Holographic Remoting)](unity-play-mode.md#holographic-remoting-setup)
2. Aprire **Modifica -> Impostazioni** progetto, passare a Gestione **plug-in XR** e selezionare la Windows Mixed Reality **set di funzionalità.** Deselezionare anche **Inizializza XR all'avvio**:

    ![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con l'opzione Inizializza XR all'avvio deselezionata](images/openxr-features-img-02-app.png)

3. Espandere la **sezione Funzionalità** in **OpenXR** e selezionare **Mostra tutto**
4. Selezionare la casella **di controllo Holographic App Remoting** :

    ![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con la comunicazione remota delle app abilitata](images/openxr-features-img-03-app.png)

5. Scrivere quindi codice per impostare la configurazione remota e attivare l'inizializzazione XR. L'app di esempio distribuita con il [plug-in OpenXR](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) di realtà mista contiene AppRemoting.cs, che illustra uno scenario di esempio per la connessione a un indirizzo IP specifico in fase di esecuzione. La distribuzione dell'app di esempio in un computer locale a questo punto visualizza un campo di input dell'indirizzo IP con un pulsante connetti. Digitando un indirizzo IP e facendo clic su Connetti si inizializza XR e si tenta di connettersi al dispositivo di destinazione:

    ![Screenshot dell'app di esempio che visualizza l'interfaccia utente remota dell'app di esempio](images/openxr-sample-app-remoting.png)

6. Per scrivere codice di connessione personalizzato, chiamare con un `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` oggetto `RemotingConfiguration` compilato. L'app di esempio lo espone nel controllo e mostra come compilare l'indirizzo IP da un campo di testo. La chiamata di imposta la configurazione e inizializza automaticamente XR, motivo per cui deve `Connect` essere chiamata come coroutine:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. Durante l'esecuzione, è possibile ottenere lo stato di connessione corrente con l'API e facoltativamente disconnettere e `AppRemoting.TryGetConnectionState` de-inizializzare XR usando `AppRemoting.Disconnect()` . Può essere usato per disconnettersi e riconnettersi a un dispositivo diverso all'interno della stessa sessione dell'app. L'app di esempio fornisce un cubo di esempio che disconnetterà la sessione remota, se toccato.

### <a name="migration-from-previous-apis"></a>Migrazione da API precedenti

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine.XR.WSA.HolographicRemoting

Dal codice di esempio [nella documentazione di Unity:](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)

| Xr. Wsa. HolographicRemoting | OpenXR.Remoting.AppRemoting |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| [N/D: si verifica automaticamente quando si chiama `AppRemoting.Connect` ]  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a>UnityEngine.XR.WindowsMR.WindowsMRRemoting

| Xr. WindowsMR.WindowsMRRemoting | OpenXR.Remoting.AppRemoting |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| `WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` e `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName` | Passato a `AppRemoting.Connect` tramite `RemotingConfiguration` lo struct |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`