---
title: Pacchetti UDP nelle app UWP Unity
description: Informazioni su come configurare un'app UWP Unity per inviare e ricevere pacchetti UDP su una rete sicura.
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP, UWP, Unity, pacchetti UDP, socket, server client, endpoint, rete, computer remoto, DatagramSocket, esempio, .NET
ms.openlocfilehash: e4fbdc12a1f7fbca44e14f6ace89ef791a09608f
ms.sourcegitcommit: 8647702638f7600c51df1d89d76c761b52bdf0d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2021
ms.locfileid: "99566978"
---
# <a name="udp-packets-in-unity-uwp-apps"></a><span data-ttu-id="5bc9f-104">Pacchetti UDP nelle app UWP Unity</span><span class="sxs-lookup"><span data-stu-id="5bc9f-104">UDP packets in Unity UWP apps</span></span>

<span data-ttu-id="5bc9f-105">È possibile configurare le app di Unity piattaforma UWP (Universal Windows Platform) (UWP) per ricevere pacchetti UDP con l'ausilio di un client e un server socket UDP.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-105">You can setup your Universal Windows Platform (UWP) Unity apps to receive UDP packets with the help of a UDP socket client and server.</span></span> <span data-ttu-id="5bc9f-106">I socket UDP non mantengono la connessione su entrambi gli endpoint, quindi sono una soluzione rapida e semplice per la rete tra computer remoti.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-106">UDP sockets don't maintain connection on both endpoints, so they're a fast and simple solution for networking between remote machines.</span></span> <span data-ttu-id="5bc9f-107">Tuttavia, sarà necessario controllare se i pacchetti vengono inviati alla destinazione, perché i socket UDP non eseguono questa operazione automaticamente.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-107">However, you'll be responsible for checking if the packets get to their destination, as UDP sockets don't do that automatically.</span></span>

## <a name="setup"></a><span data-ttu-id="5bc9f-108">Configurazione</span><span class="sxs-lookup"><span data-stu-id="5bc9f-108">Setup</span></span>

<span data-ttu-id="5bc9f-109">Aprire i progetti HoloLens manifest.jssu file e assicurarsi di aver abilitato:</span><span class="sxs-lookup"><span data-stu-id="5bc9f-109">Open your projects HoloLens manifest.json file and make sure you've enabled:</span></span>
* <span data-ttu-id="5bc9f-110">**Internet (client & Server)**</span><span class="sxs-lookup"><span data-stu-id="5bc9f-110">**Internet (Client & Server)**</span></span> 
* <span data-ttu-id="5bc9f-111">**Reti private (Client & Server)**.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-111">**Private Networks (Client & Server)**.</span></span>

## <a name="build-your-socket-client-and-server"></a><span data-ttu-id="5bc9f-112">Compilare il client e il server socket</span><span class="sxs-lookup"><span data-stu-id="5bc9f-112">Build your socket client and server</span></span> 

<span data-ttu-id="5bc9f-113">Seguire le istruzioni per la [compilazione di un client e un server socket UDP di base](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span><span class="sxs-lookup"><span data-stu-id="5bc9f-113">Follow the instructions for [building a basic UDP socket client and server](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span></span> <span data-ttu-id="5bc9f-114">Si userà la classe [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) per inviare e ricevere dati tramite UDP e formare un client e un server echo.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-114">You'll be using the [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) class to send and receive data over UDP and form an echo client and server.</span></span> <span data-ttu-id="5bc9f-115">Si consiglia anche di leggere le altre sezioni delle risorse di questo articolo, in quanto si applicano ai casi d'uso più personalizzati e complessi.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-115">We also recommend reading through the other resource sections in this article, as they apply to more customized and complex use cases.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="5bc9f-116">Se si verificano problemi durante l'invio di pacchetti UDP da PC a PC, verificare che la rete consenta queste operazioni.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-116">If you're having trouble sending UDP packets from PC to PC, check that your network allows these operations.</span></span> <span data-ttu-id="5bc9f-117">Se la rete blocca i pacchetti UDP in qualsiasi modo, il dispositivo HoloLens non sarà in grado di ascoltarli.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-117">If your network is blocking the UDP packets in any way, your HoloLens device won't be able to listen for them.</span></span>

<span data-ttu-id="5bc9f-118">È possibile scaricare un'app di esempio UDP DatagramSocket completa dal collegamento seguente:</span><span class="sxs-lookup"><span data-stu-id="5bc9f-118">You can download a complete DatagramSocket UDP sample app from the link below:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5bc9f-119">Installare gli strumenti</span><span class="sxs-lookup"><span data-stu-id="5bc9f-119">Install the tools</span></span>](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a><span data-ttu-id="5bc9f-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5bc9f-120">See also</span></span> 
* [<span data-ttu-id="5bc9f-121">Esperimenti con ologrammi condivisi e archiviazione BLOB di Azure/multicast UDP</span><span class="sxs-lookup"><span data-stu-id="5bc9f-121">Experiments with Shared Holograms and Azure Blob Storage/UDP Multicasting</span></span>](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)