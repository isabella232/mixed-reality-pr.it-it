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
# <a name="udp-packets-in-unity-uwp-apps"></a>Pacchetti UDP nelle app UWP Unity

È possibile configurare le app di Unity piattaforma UWP (Universal Windows Platform) (UWP) per ricevere pacchetti UDP con l'ausilio di un client e un server socket UDP. I socket UDP non mantengono la connessione su entrambi gli endpoint, quindi sono una soluzione rapida e semplice per la rete tra computer remoti. Tuttavia, sarà necessario controllare se i pacchetti vengono inviati alla destinazione, perché i socket UDP non eseguono questa operazione automaticamente.

## <a name="setup"></a>Configurazione

Aprire i progetti HoloLens manifest.jssu file e assicurarsi di aver abilitato:
* **Internet (client & Server)** 
* **Reti private (Client & Server)**.

## <a name="build-your-socket-client-and-server"></a>Compilare il client e il server socket 

Seguire le istruzioni per la [compilazione di un client e un server socket UDP di base](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server). Si userà la classe [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) per inviare e ricevere dati tramite UDP e formare un client e un server echo. Si consiglia anche di leggere le altre sezioni delle risorse di questo articolo, in quanto si applicano ai casi d'uso più personalizzati e complessi. 

> [!IMPORTANT]
> Se si verificano problemi durante l'invio di pacchetti UDP da PC a PC, verificare che la rete consenta queste operazioni. Se la rete blocca i pacchetti UDP in qualsiasi modo, il dispositivo HoloLens non sarà in grado di ascoltarli.

È possibile scaricare un'app di esempio UDP DatagramSocket completa dal collegamento seguente:

> [!div class="nextstepaction"]
> [Installare gli strumenti](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a>Vedere anche 
* [Esperimenti con ologrammi condivisi e archiviazione BLOB di Azure/multicast UDP](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)