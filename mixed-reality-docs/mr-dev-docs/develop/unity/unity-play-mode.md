---
title: Visualizzare in anteprima il lavoro con Holographic Remoting
description: Usare Holographic Remoting in modalità di riproduzione per visualizzare in anteprima le modifiche dell'applicazione in un dispositivo senza distribuire un'app.
author: keveleigh
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: Unity, comunicazione remota, comunicazione remota olografica, lettore di comunicazione remota olografica, HoloLens, visore per realtà mista, visore windows mixed reality, visore di realtà virtuale, modalità di riproduzione unity
ms.openlocfilehash: 0c71791c80a5e84ee48241baa756064a800e5a41
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757213"
---
# <a name="preview-your-work-with-holographic-remoting"></a>Visualizzare in anteprima il lavoro con Holographic Remoting

È possibile usare Holographic Remoting per trasmettere contenuti olografici alle HoloLens 2 in tempo reale. Questo è un ottimo modo per eseguire rapidamente il debug dell'app senza compilare e distribuire un progetto completo. 

Un modo rapido per lavorare al progetto Unity è usare la "modalità di riproduzione", che esegue l'app in locale nell'editor di Unity nel PC. Unity usa Holographic Remoting per offrire un modo rapido per visualizzare in anteprima il contenuto in un dispositivo HoloLens reale. La modalità di riproduzione può essere usata anche con Windows Mixed Reality visore collegato al PC di sviluppo.

## <a name="holographic-remoting-setup"></a>Configurazione della comunicazione remota olografica

1. Prima di tutto, è [necessario installare l'app Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) dal Microsoft Store nel HoloLens 2
2. Eseguire l'app Holographic Remoting Player nel HoloLens 2 e verranno visualizzati il numero di versione e l'indirizzo IP a cui connettersi
    * Per usare il plug-in OpenXR è necessaria la versione 2.4 o successiva

    ![Screenshot di Holographic Remoting Player in esecuzione nel HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Modalità di riproduzione Unity con holographic Remoting

Con Holographic Remoting è possibile sperimentare l'app nel HoloLens mentre viene eseguita nell'editor di Unity nel PC. Lo sguardo, il movimento, la voce e l'input di mapping spaziale vengono inviati dal HoloLens al PC. I fotogrammi sottoposti a rendering vengono quindi inviati di nuovo HoloLens. Questo è un ottimo modo per eseguire rapidamente il debug dell'app senza compilare e distribuire un progetto completo.

[!INCLUDE[](includes/unity-play-mode.md)]

Holographic Remoting richiede un PC veloce e Wi-Fi connessione. Per altri dettagli, vedere la documentazione [di Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)

Per ottenere risultati ottimali, assicurarsi che l'app imposta correttamente il [punto di attivazione.](focus-point-in-unity.md) Ciò consente a Holographic Remoting di adattare al meglio la scena alla latenza della connessione wireless.

## <a name="see-also"></a>Vedere anche

* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
