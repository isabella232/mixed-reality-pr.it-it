---
ms.openlocfilehash: 212aa75ae91a7beebbfa609af6cc47106ba34b55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "96855883"
---
# <a name="windows-mixed-reality"></a>[<span data-ttu-id="e92d0-101">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e92d0-101">Windows Mixed Reality</span></span>](#tab/wmr)

| <span data-ttu-id="e92d0-102">Opzione</span><span class="sxs-lookup"><span data-stu-id="e92d0-102">Option</span></span> | <span data-ttu-id="e92d0-103">Descrizione</span><span class="sxs-lookup"><span data-stu-id="e92d0-103">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | <span data-ttu-id="e92d0-104">Accetta l'indirizzo IP e la porta facoltativa del dispositivo HoloLens 2 a cui connettersi.</span><span class="sxs-lookup"><span data-stu-id="e92d0-104">Takes the IP address (and optional port) of the HoloLens 2 device to connect to.</span></span> <span data-ttu-id="e92d0-105">Se non viene specificata alcuna porta, il valore predefinito è 8265.</span><span class="sxs-lookup"><span data-stu-id="e92d0-105">If no port is provided, default to 8265.</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="e92d0-106">(Facoltativa) Il valore predefinito è 8000.</span><span class="sxs-lookup"><span data-stu-id="e92d0-106">(optional) Default 8000.</span></span> <span data-ttu-id="e92d0-107">Velocità massima di trasferimento di rete (KB/s).</span><span class="sxs-lookup"><span data-stu-id="e92d0-107">Max network transfer rate (kb/s).</span></span> |
| `-HoloLensRemotingListen` | <span data-ttu-id="e92d0-108">(Facoltativa) Avvia un server di ascolto.</span><span class="sxs-lookup"><span data-stu-id="e92d0-108">(optional) Start a listen server</span></span> |
| `-HoloLensRemotingListenPort=<port>` | <span data-ttu-id="e92d0-109">(Facoltativa) Accetta la porta per l'ascolto.</span><span class="sxs-lookup"><span data-stu-id="e92d0-109">(optional) Takes the port to listen on.</span></span> <span data-ttu-id="e92d0-110">Usata per la connessione a un PC o una macchina virtuale da un dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e92d0-110">Used for connecting to a PC or VM from a HoloLens device.</span></span> |
| `-HoloLens1Remoting=<IP address>` | <span data-ttu-id="e92d0-111">(Deprecata nella versione 4.26) Accetta l'indirizzo IP del dispositivo HoloLens 1 a cui connettersi.</span><span class="sxs-lookup"><span data-stu-id="e92d0-111">(deprecated in 4.26) Takes the IP address of the HoloLens 1 device to connect to</span></span> |

# <a name="openxr"></a>[<span data-ttu-id="e92d0-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="e92d0-112">OpenXR</span></span>](#tab/openxr)

| <span data-ttu-id="e92d0-113">Opzione</span><span class="sxs-lookup"><span data-stu-id="e92d0-113">Option</span></span> | <span data-ttu-id="e92d0-114">Descrizione</span><span class="sxs-lookup"><span data-stu-id="e92d0-114">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | <span data-ttu-id="e92d0-115">Accetta l'indirizzo IP (e la porta facoltativa, valore predefinito 8265) del dispositivo HoloLens 2 a cui connettersi o la porta su cui l'app deve restare in ascolto per le connessioni.</span><span class="sxs-lookup"><span data-stu-id="e92d0-115">Takes the IP address (and optional port, default 8265) of the HoloLens 2 device to connect to, or the port on which the app should listen on for connections.</span></span> |
| `-EnableAudio` | <span data-ttu-id="e92d0-116">(Facoltativa) Usa l'audio da PC durante la comunicazione remota.</span><span class="sxs-lookup"><span data-stu-id="e92d0-116">(optional) Use audio from PC when remoting</span></span>  |
| `-Listen` | <span data-ttu-id="e92d0-117">(Facoltativa) Avvia un server di ascolto.</span><span class="sxs-lookup"><span data-stu-id="e92d0-117">(optional) Start a listen server</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="e92d0-118">(Facoltativa) Il valore predefinito è 8000.</span><span class="sxs-lookup"><span data-stu-id="e92d0-118">(optional) Default 8000.</span></span> <span data-ttu-id="e92d0-119">Velocità massima di trasferimento di rete (KB/s).</span><span class="sxs-lookup"><span data-stu-id="e92d0-119">Max network transfer rate (kb/s).</span></span> |
| `-RemotingCodec=<codec>` | <span data-ttu-id="e92d0-120">(Facoltativa) Codec di connessione.</span><span class="sxs-lookup"><span data-stu-id="e92d0-120">(optional) Connection codec</span></span>  |