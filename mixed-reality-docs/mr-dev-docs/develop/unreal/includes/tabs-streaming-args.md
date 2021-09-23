---
ms.openlocfilehash: 12634c1fc18366e28a51688b19fc739ea69d37ec
ms.sourcegitcommit: 71c2a4884bd83599e35dd894771a5e43e951b574
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2021
ms.locfileid: "128184627"
---
# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

| Opzione | Descrizione |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | Accetta l'indirizzo IP e la porta facoltativa del dispositivo HoloLens 2 a cui connettersi. Se non viene specificata alcuna porta, il valore predefinito è 8265. |
| `-RemotingBitrate=<bitrate>` | (Facoltativa) Il valore predefinito è 8000. Velocità massima di trasferimento di rete (KB/s). |
| `-HoloLensRemotingListen` | (Facoltativa) Avvia un server di ascolto. |
| `-HoloLensRemotingListenPort=<port>` | (Facoltativa) Accetta la porta per l'ascolto. Usata per la connessione a un PC o una macchina virtuale da un dispositivo HoloLens. |
| `-HoloLens1Remoting=<IP address>` | (Deprecata nella versione 4.26) Accetta l'indirizzo IP del dispositivo HoloLens 1 a cui connettersi. |
| `-eyetracking=WindowsMixedRealityEyeTracker` | (facoltativo) Usare il tracciatore Windows Mixed Reality oculare |

# <a name="openxr"></a>[OpenXR](#tab/openxr)

| Opzione | Descrizione |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | Accetta l'indirizzo IP (e la porta facoltativa, valore predefinito 8265) del dispositivo HoloLens 2 a cui connettersi o la porta su cui l'app deve restare in ascolto per le connessioni. |
| `-EnableAudio` | (Facoltativa) Usa l'audio da PC durante la comunicazione remota.  |
| `-Listen` | (Facoltativa) Avvia un server di ascolto. |
| `-RemotingBitrate=<bitrate>` | (Facoltativa) Il valore predefinito è 8000. Velocità massima di trasferimento di rete (KB/s). |
| `-RemotingCodec=<codec>` | (Facoltativa) Codec di connessione.  |
| `-eyetracking=OpenXREyeTracker` | (facoltativo) Usare il localizzatore oculare OpenXR |