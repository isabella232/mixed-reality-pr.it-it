---
title: Holographic Remoting in Unity
description: Informazioni su come usare Holographic Remoting in un'app desktop e in modalità Unity Play con OpenXR.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realtà mista, MRTK, realtà mista Toolkit, realtà aumentata, realtà virtuale, visori VR di realtà mista, apprendimento, esercitazione, introduzione, comunicazione remota olografica, desktop
ms.openlocfilehash: 51244a94fb7e54f2eee41d9d1b7f65b0ba373138
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757425"
---
# <a name="holographic-remoting-in-unity"></a>Holographic Remoting in Unity

> [!NOTE]
> Windows Il supporto per la comunicazione remota delle app autonome è stato aggiunto nella versione del pacchetto 0.1.3.
> A livello di versione 0.1.3, questa funzionalità non supporta le build UWP.

[Informazioni di base su Holographic Remoting.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

È possibile usare Holographic Remoting per trasmettere contenuto olografico al HoloLens 2 in tempo reale. Questo è un ottimo modo per eseguire rapidamente il debug dell'app senza compilare e distribuire un progetto completo. 

Prima di iniziare, è importante comprendere le due opzioni principali in Unity:
* **Holographic Remoting in modalità di** riproduzione Unity: esegui l'app in locale nell'editor unity del PC in modalità di riproduzione per offrire un modo rapido per visualizzare in anteprima il contenuto in un HoloLens 2. La modalità di riproduzione può essere usata anche con Windows Mixed Reality visore VR collegato al PC di sviluppo.
* **Holographic Remoting da** un file di compilazione Unity: esegui l'app da un'applicazione remota Unity Holographic Remoting esportata sul desktop nel HoloLens 2. Ciò può essere utile se l'app ha asset o modelli ad alta risoluzione. la GPU desktop gestisce il rendering prima che venga HoloLens 2.

## <a name="holographic-remoting-setup"></a>Configurazione di Holographic Remoting

Indipendentemente dalla route che si sta prendendo con Holographic Remoting, è necessario installare [l'app Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) dal Microsoft Store nel HoloLens 2.

Dopo il download, eseguire l'app Holographic Remoting Player nel HoloLens 2 per visualizzare il numero di versione e l'indirizzo IP a cui connettersi. **Per usare il plug-in OpenXR,** è necessaria la versione 2.4 o successiva.

![Screenshot del lettore Holographic Remoting in esecuzione nel HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Modalità di riproduzione Unity con Holographic Remoting

[!INCLUDE[](includes/unity-play-mode.md)]

Holographic Remoting richiede un PC veloce e Wi-Fi connessione. Per altri dettagli, vedere la documentazione di [Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)

Per ottenere risultati ottimali, assicurarsi che l'app imposta correttamente il [punto di interesse.](focus-point-in-unity.md) Ciò consente a Holographic Remoting di adattare la scena alla latenza della connessione wireless.

## <a name="holographic-remoting-from-a-remote-application"></a>Holographic Remoting da un'applicazione remota

1. Sulla barra dei menu selezionare **Modifica > Project Impostazioni**.
1. Nella colonna sul lato sinistro selezionare **Gestione plug-in XR.**
1. Nella sezione **XR Plug-in Management (Gestione plug-in XR)** selezionare Microsoft HoloLens **funzionalità** e **holographic Remoting remote app feature group (Gruppo di funzionalità dell'app remota Holographic Remoting).**
1. Deselezionare **Inizializza XR all'avvio:**

    ![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con l'opzione Initialize XR on Startup (Inizializza XR all'avvio) deselezionata](images/001-openxr-features.png)

1. Scrivere codice per impostare la configurazione remota e attivare l'inizializzazione XR. L'app di esempio distribuita con il plug-in [OpenXR](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) di realtà mista contiene AppRemoting.cs, che illustra uno scenario di esempio per la connessione a un indirizzo IP specifico in fase di esecuzione. La distribuzione dell'app di esempio in un computer locale a questo punto visualizza un campo di input dell'indirizzo IP con un pulsante di connessione. Digitando un indirizzo IP e facendo clic Connessione verrà inizializzato XR e si tenterà di connettersi al dispositivo di destinazione:

    ![Screenshot dell'app di esempio che mostra l'interfaccia utente remota dell'app di esempio](images/openxr-sample-app-remoting.png)

1. Per scrivere codice di connessione personalizzato, `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` chiamare con un oggetto `RemotingConfiguration` compilato. L'app di esempio espone questo valore nel controllo e mostra come compilare l'indirizzo IP da un campo di testo. La chiamata a imposta la configurazione e inizializza automaticamente XR, motivo per cui deve `Connect` essere chiamata come coroutine:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

1. Durante l'esecuzione, è possibile ottenere lo stato di connessione corrente con l'API e, facoltativamente, disconnettere e `AppRemoting.TryGetConnectionState` de inizializzare XR usando `AppRemoting.Disconnect()` . Può essere usato per disconnettersi e riconnettersi a un dispositivo diverso all'interno della stessa sessione dell'app. L'app di esempio fornisce un cubo che disconnetterà la sessione remota se toccato.

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
| `WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName` | Passato in `AppRemoting.Connect` tramite `RemotingConfiguration` lo struct |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="see-also"></a>Vedere anche

* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [Esercitazione: Introduzione a Holographic Remoting per PC](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Esercitazione: Creazione di un'applicazione per PC Holographic Remoting](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
