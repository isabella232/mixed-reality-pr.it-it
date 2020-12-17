---
ms.openlocfilehash: 212aa75ae91a7beebbfa609af6cc47106ba34b55
ms.sourcegitcommit: 0509cf6c57067cffd75a0189106e3369e9ecc5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96855883"
---
# <a name="windows-mixed-reality"></a>[<span data-ttu-id="d69bc-101">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d69bc-101">Windows Mixed Reality</span></span>](#tab/wmr)

| <span data-ttu-id="d69bc-102">Opzione</span><span class="sxs-lookup"><span data-stu-id="d69bc-102">Option</span></span> | <span data-ttu-id="d69bc-103">Descrizione</span><span class="sxs-lookup"><span data-stu-id="d69bc-103">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | <span data-ttu-id="d69bc-104">Accetta l'indirizzo IP e la porta facoltativa del dispositivo HoloLens 2 a cui connettersi.</span><span class="sxs-lookup"><span data-stu-id="d69bc-104">Takes the IP address (and optional port) of the HoloLens 2 device to connect to.</span></span> <span data-ttu-id="d69bc-105">Se non viene specificata alcuna porta, il valore predefinito è 8265.</span><span class="sxs-lookup"><span data-stu-id="d69bc-105">If no port is provided, default to 8265.</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="d69bc-106">(Facoltativa) Il valore predefinito è 8000.</span><span class="sxs-lookup"><span data-stu-id="d69bc-106">(optional) Default 8000.</span></span> <span data-ttu-id="d69bc-107">Velocità massima di trasferimento di rete (KB/s).</span><span class="sxs-lookup"><span data-stu-id="d69bc-107">Max network transfer rate (kb/s).</span></span> |
| `-HoloLensRemotingListen` | <span data-ttu-id="d69bc-108">(Facoltativa) Avvia un server di ascolto.</span><span class="sxs-lookup"><span data-stu-id="d69bc-108">(optional) Start a listen server</span></span> |
| `-HoloLensRemotingListenPort=<port>` | <span data-ttu-id="d69bc-109">(Facoltativa) Accetta la porta per l'ascolto.</span><span class="sxs-lookup"><span data-stu-id="d69bc-109">(optional) Takes the port to listen on.</span></span> <span data-ttu-id="d69bc-110">Usata per la connessione a un PC o una macchina virtuale da un dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d69bc-110">Used for connecting to a PC or VM from a HoloLens device.</span></span> |
| `-HoloLens1Remoting=<IP address>` | <span data-ttu-id="d69bc-111">(Deprecata nella versione 4.26) Accetta l'indirizzo IP del dispositivo HoloLens 1 a cui connettersi.</span><span class="sxs-lookup"><span data-stu-id="d69bc-111">(deprecated in 4.26) Takes the IP address of the HoloLens 1 device to connect to</span></span> |

# <a name="openxr"></a>[<span data-ttu-id="d69bc-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="d69bc-112">OpenXR</span></span>](#tab/openxr)

| <span data-ttu-id="d69bc-113">Opzione</span><span class="sxs-lookup"><span data-stu-id="d69bc-113">Option</span></span> | <span data-ttu-id="d69bc-114">Descrizione</span><span class="sxs-lookup"><span data-stu-id="d69bc-114">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | <span data-ttu-id="d69bc-115">Accetta l'indirizzo IP (e la porta facoltativa, valore predefinito 8265) del dispositivo HoloLens 2 a cui connettersi o la porta su cui l'app deve restare in ascolto per le connessioni.</span><span class="sxs-lookup"><span data-stu-id="d69bc-115">Takes the IP address (and optional port, default 8265) of the HoloLens 2 device to connect to, or the port on which the app should listen on for connections.</span></span> |
| `-EnableAudio` | <span data-ttu-id="d69bc-116">(Facoltativa) Usa l'audio da PC durante la comunicazione remota.</span><span class="sxs-lookup"><span data-stu-id="d69bc-116">(optional) Use audio from PC when remoting</span></span>  |
| `-Listen` | <span data-ttu-id="d69bc-117">(Facoltativa) Avvia un server di ascolto.</span><span class="sxs-lookup"><span data-stu-id="d69bc-117">(optional) Start a listen server</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="d69bc-118">(Facoltativa) Il valore predefinito è 8000.</span><span class="sxs-lookup"><span data-stu-id="d69bc-118">(optional) Default 8000.</span></span> <span data-ttu-id="d69bc-119">Velocità massima di trasferimento di rete (KB/s).</span><span class="sxs-lookup"><span data-stu-id="d69bc-119">Max network transfer rate (kb/s).</span></span> |
| `-RemotingCodec=<codec>` | <span data-ttu-id="d69bc-120">(Facoltativa) Codec di connessione.</span><span class="sxs-lookup"><span data-stu-id="d69bc-120">(optional) Connection codec</span></span>  |