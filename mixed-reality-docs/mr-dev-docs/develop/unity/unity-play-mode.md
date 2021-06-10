---
title: Modalità di gioco Unity
description: Informazioni su come usare la modalità di riproduzione nell'editor di Unity per visualizzare in anteprima le modifiche dell'applicazione in un dispositivo senza distribuire un'app.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, comunicazione remota, comunicazione remota olografica, lettore di comunicazione remota olografica, HoloLens, visore per realtà mista, visore windows mixed reality, visore di realtà virtuale, modalità di gioco unity
ms.openlocfilehash: caa9d7bf11104ee168fda24fc369de490feb7817
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547102"
---
# <a name="unity-play-mode"></a>Modalità di gioco Unity

Un modo rapido per lavorare al progetto Unity è usare la "modalità di riproduzione", che esegue l'app in locale nell'editor di Unity nel PC. Unity usa Holographic Remoting per offrire un modo rapido per visualizzare in anteprima il contenuto in un dispositivo HoloLens reale. La modalità di riproduzione può essere usata anche con Windows Mixed Reality visore collegato al PC di sviluppo.

## <a name="holographic-remoting-setup"></a>Configurazione della comunicazione remota olografica

1. Prima di tutto, è [necessario installare l'app Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) dal Microsoft Store nel HoloLens 2
2. Eseguire l'app Holographic Remoting Player HoloLens 2 e verranno visualizzati il numero di versione e l'indirizzo IP a cui connettersi
    * Per usare il plug-in OpenXR è necessaria la versione 2.4 o successiva

    ![Screenshot di Holographic Remoting Player in esecuzione in HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Comunicazione remota olografica in modalità di riproduzione dell'editor unity

La compilazione di un progetto Unity UWP Visual Studio progetto e quindi la creazione del pacchetto e la distribuzione in un dispositivo HoloLens 2 può richiedere del tempo. Una soluzione consiste nell'abilitare la funzionalità comunicazione remota di Holographic Editor, che consente di eseguire il debug dello script C# usando la modalità "Play" direttamente in un dispositivo HoloLens 2 rete. Questo scenario evita il sovraccarico della compilazione e della distribuzione di un pacchetto UWP nel dispositivo remoto.

1. Seguire la procedura descritta in [Holographic Remoting setup (Configurazione di Holographic Remoting)](#holographic-remoting-setup)
2. Aprire Windows > XR > comunicazione remota **dell'editor OpenXR:**

    ![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con la gestione dei plug-in XR evidenziata](images/openxr-features-img-02.png)

3. Immettere l'indirizzo IP che si ottiene dall'app Holographic Remoting e selezionare Abilita comunicazione remota **dell'editor**

    ![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con funzionalità evidenziate](images/openxr-features-img-03.png)

È ora possibile fare clic sul pulsante "Play" (Riproduci) per riprodurre l'app Unity nell'app Holographic Remoting in HoloLens. È anche possibile [collegare Visual Studio a Unity per](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) eseguire il debug di script C# in modalità di riproduzione.

> [!NOTE]
> A causa della versione 0.1.0, il runtime di Holographic Remoting non supporta ancoraggi e le funzionalità di ARAnchorManager non funzioneranno tramite la comunicazione remota.  Questa funzionalità sarà disponibile nelle versioni future.

## <a name="unity-play-mode-with-holographic-remoting"></a>Modalità di riproduzione Unity con Holographic Remoting

Con Holographic Remoting è possibile sperimentare l'app in HoloLens mentre viene eseguita nell'editor unity nel PC. Lo sguardo, il movimento, la voce e l'input di mapping spaziale vengono inviati dal dispositivo HoloLens al PC. I fotogrammi sottoposti a rendering vengono quindi inviati nuovamente a HoloLens. Questo è un ottimo modo per eseguire rapidamente il debug dell'app senza compilare e distribuire un progetto completo.

[!INCLUDE[](includes/unity-play-mode.md)]

Holographic Remoting richiede un PC veloce e Wi-Fi connessione. Per altri dettagli, vedere la documentazione [di Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)

Per ottenere risultati ottimali, assicurarsi che l'app imposta correttamente il [punto di attivazione.](focus-point-in-unity.md) Ciò consente a Holographic Remoting di adattare al meglio la scena alla latenza della connessione wireless.

## <a name="see-also"></a>Vedere anche

* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
