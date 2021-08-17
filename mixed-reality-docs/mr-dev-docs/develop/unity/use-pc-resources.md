---
title: Usare le risorse del PC per alimentare l'app con Holographic Remoting
description: Usare le risorse del PC, invece di affidarsi alla potenza di elaborazione di bordo del HoloLens, per alimentare l'app con Holographic Remoting
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realtà mista, MRTK, mixed reality Toolkit, realtà aumentata, realtà virtuale, visori di realtà mista, apprendimento, esercitazione, introduzione, comunicazione remota olografica, desktop, anteprima, debug
ms.openlocfilehash: 634e1a5e92ade79d1d9f0e7bfdd994cfdfb5866b
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203850"
---
# <a name="use-pc-resources-to-power-your-app-with-holographic-remoting"></a>Usare le risorse del PC per alimentare l'app con Holographic Remoting

Questo articolo illustra il caso d'uso seguente per Holographic Remoting:

-  **Si** vuole che le risorse di un PC possano alimentare l'app invece di basarsi sulle risorse HoloLens di bordo: è possibile creare e compilare un'app con la funzionalità Holographic Remoting. L'utente sperimenta l'app nel HoloLens, ma l'app viene effettivamente eseguita in un PC, che consente all'app di sfruttare le risorse più potenti del PC. Questo può essere particolarmente utile se l'app dispone di asset o modelli ad alta risoluzione e non si vuole che la frequenza dei fotogrammi ne risenti. Si tratta di un'app remota _Holographic Remoting._ Gli input del HoloLens, ad esempio lo sguardo, il movimento, la voce e il mapping spaziale, vengono inviati al PC, in cui viene eseguito il rendering del contenuto in una visualizzazione virtuale immersiva. I fotogrammi sottoposti a rendering vengono quindi inviati al HoloLens.

Questo tipo di comunicazione remota Holographic è disponibile anche per Windows Mixed Reality immersive (WMR). Questo può essere utile se, ad esempio, il visore WMR è connesso a un PC per lo zainetto e si vuole trasmettere l'app da un PC più potente al PC dello zainetto.

Per altre informazioni sulla comunicazione remota holografica, vedere [Panoramica di Holographic Remoting](../platform-capabilities-and-apis/holographic-remoting-overview.md)

Si noti che è anche possibile usare Holographic Remoting se si vuole visualizzare in anteprima ed eseguire [il debug dell'app durante il processo di sviluppo.](preview-and-debug-your-app.md)

## <a name="set-up-holographic-remoting"></a>Configurare Holographic Remoting

Per usare Holographic Remoting, è necessario installare l'app [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) dal Microsoft Store nel HoloLens 2. Come illustrato di seguito, dopo aver scaricato ed eseguito l'app, verranno visualizzati il numero di versione e l'indirizzo IP a cui connettersi. **Per usare il plug-in OpenXR** è necessaria la versione 2.4 o successiva.

Holographic Remoting richiede un PC veloce e una Wi-Fi connessione. Per altri dettagli, vedere l'articolo holographic Remoting Player collegato in precedenza.

![Screenshot di Holographic Remoting Player in esecuzione nel HoloLens](images/openxr-features-img-01.png)

1. Sulla barra dei menu selezionare **Modifica > Project Impostazioni**.
1. Nella colonna a sinistra selezionare **Gestione plug-in XR.**
1. Nella sezione **XR Plug-in Management (Gestione plug-in XR)** selezionare **Microsoft HoloLens feature group** e Holographic Remoting remote app feature group (Gruppo di funzionalità **dell'app remota Holographic Remoting).**
1. Deselezionare **Inizializza XR all'avvio**:

    ![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con l'opzione Inizializza XR all'avvio deselezionata](images/001-openxr-features.png)

1. Scrivere codice per impostare la configurazione remota e attivare l'inizializzazione XR. L'app di esempio distribuita con il [plug-in OpenXR](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) di realtà mista contiene AppRemoting.cs, che illustra uno scenario di esempio per la connessione a un indirizzo IP specifico in fase di esecuzione. La distribuzione dell'app di esempio in un computer locale a questo punto visualizza un campo di input dell'indirizzo IP con un pulsante connetti. Digitando un indirizzo IP e facendo clic Connessione verrà inizializzato XR e si tenterà di connettersi al dispositivo di destinazione:

    ![Screenshot dell'app di esempio che visualizza l'interfaccia utente remota dell'app di esempio](images/openxr-sample-app-remoting.png)

1. Per scrivere codice di connessione personalizzato, `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` chiamare con un oggetto `RemotingConfiguration` compilato. L'app di esempio lo espone nel controllo e mostra come compilare l'indirizzo IP da un campo di testo. La chiamata di imposta la configurazione e inizializza automaticamente XR, motivo per cui deve `Connect` essere chiamata come coroutine:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

1. Durante l'esecuzione, è possibile ottenere lo stato di connessione corrente con l'API e facoltativamente disconnettere e `AppRemoting.TryGetConnectionState` de-inizializzare XR usando `AppRemoting.Disconnect()` . Può essere usato per disconnettersi e riconnettersi a un dispositivo diverso all'interno della stessa sessione dell'app. L'app di esempio fornisce un cubo di esempio che disconnetterà la sessione remota, se toccato.

## <a name="migrate-from-previous-holographic-remoting-apis"></a>Eseguire la migrazione da API holographic remoting precedenti

Per altre informazioni sulla comunicazione remota holografica, vedere [Panoramica di Holographic Remoting](../platform-capabilities-and-apis/holographic-remoting-overview.md)

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

## <a name="see-also"></a>Vedere anche

* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [Visualizzare in anteprima ed eseguire il debug dell'app con la modalità Holographic Remoting e Play](preview-and-debug-your-app.md)
* [Esercitazione: Introduzione a PC Holographic Remoting](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Esercitazione: Creazione di un'applicazione per PC Holographic Remoting](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
