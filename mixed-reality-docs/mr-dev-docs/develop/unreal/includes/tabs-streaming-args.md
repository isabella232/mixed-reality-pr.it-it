---
ms.openlocfilehash: 283ef0bedc96a63d34a66fa0d88dee97420957c7744ad3702c6ac3bc34c14310
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218859"
---
# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

| Opzione | Descrizione |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | Accetta l'indirizzo IP e la porta facoltativa del dispositivo HoloLens 2 a cui connettersi. Se non viene specificata alcuna porta, il valore predefinito è 8265. |
| `-RemotingBitrate=<bitrate>` | (Facoltativa) Il valore predefinito è 8000. Velocità massima di trasferimento di rete (KB/s). |
| `-HoloLensRemotingListen` | (Facoltativa) Avvia un server di ascolto. |
| `-HoloLensRemotingListenPort=<port>` | (Facoltativa) Accetta la porta per l'ascolto. Usata per la connessione a un PC o una macchina virtuale da un dispositivo HoloLens. |
| `-HoloLens1Remoting=<IP address>` | (Deprecata nella versione 4.26) Accetta l'indirizzo IP del dispositivo HoloLens 1 a cui connettersi. |

# <a name="openxr"></a>[OpenXR](#tab/openxr)

| Opzione | Descrizione |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | Accetta l'indirizzo IP (e la porta facoltativa, valore predefinito 8265) del dispositivo HoloLens 2 a cui connettersi o la porta su cui l'app deve restare in ascolto per le connessioni. |
| `-EnableAudio` | (Facoltativa) Usa l'audio da PC durante la comunicazione remota.  |
| `-Listen` | (Facoltativa) Avvia un server di ascolto. |
| `-RemotingBitrate=<bitrate>` | (Facoltativa) Il valore predefinito è 8000. Velocità massima di trasferimento di rete (KB/s). |
| `-RemotingCodec=<codec>` | (Facoltativa) Codec di connessione.  |