---
title: Modalità di gioco Unity
description: Uso della modalità di riproduzione nell'editor di Unity per visualizzare in anteprima le modifiche apportate a un dispositivo senza distribuire un'app.
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, comunicazione remota, comunicazione remota olografica, lettore di comunicazione remota olografica, HoloLens, cuffia reale mista, auricolare di realtà mista, auricolare di realtà virtuale, modalità di riproduzione
ms.openlocfilehash: 88ffa172c03dea6544ce8475612426e126415908
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679060"
---
# <a name="unity-play-mode"></a>Modalità di gioco Unity

Un modo rapido per lavorare al progetto Unity consiste nell'usare "modalità di riproduzione". L'app viene eseguita localmente nell'editor di Unity nel PC. Unity usa la comunicazione remota olografica per fornire un modo rapido per visualizzare in anteprima il contenuto su un dispositivo HoloLens reale. La modalità di riproduzione può essere usata anche con un auricolare di realtà mista di Windows collegato al PC di sviluppo.

## <a name="unity-play-mode-with-holographic-remoting"></a>Modalità di riproduzione Unity con comunicazione remota olografica

Con la comunicazione remota olografica è possibile sperimentare l'app in HoloLens, mentre è in esecuzione nell'editor di Unity nel PC. L'input dello sguardo, del movimento, della voce e del mapping spaziale viene inviato dal HoloLens al PC. I frame sottoposti a rendering vengono quindi restituiti alla HoloLens. Questo è un ottimo modo per eseguire rapidamente il debug dell'app senza compilare e distribuire un progetto completo.
1. Nella HoloLens passare alla **Microsoft Store** e installare l'app di **[lettore remoto olografico](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .
2. In HoloLens avviare l'app di **lettore remoto olografico** .
3. In Unity andare al menu **finestra** , espandere il sottomenu **XR** e selezionare **emulazione olografica**.
4. Impostare la **modalità di emulazione** su da **remoto a dispositivo**.
5. Per **computer remoto**, immettere l'indirizzo IP del HoloLens.
6. Fare clic su **Connetti**. Si noterà che lo **stato della connessione è stato** modificato in **connesso** e la schermata è vuota in HoloLens.
7. Fare clic sul pulsante **Play (Riproduci** ) per avviare la modalità di riproduzione e sperimentare l'app nella HoloLens.

La comunicazione remota olografica richiede una connessione PC veloce e Wi-Fi. Per i dettagli completi, vedere [lettore remoto olografico](../platform-capabilities-and-apis/holographic-remoting-player.md) .

Per ottenere risultati ottimali, assicurarsi che l'app imposti correttamente il [punto di messa a fuoco](focus-point-in-unity.md). Questo consente ai servizi remoti olografici di adattare al meglio la scena alla latenza della connessione wireless.

## <a name="see-also"></a>Vedere anche
* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
