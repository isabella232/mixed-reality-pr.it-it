---
title: Pacchetti UDP nelle app UWP di Unity
description: Informazioni su come configurare un'app UWP unity per inviare e ricevere pacchetti UDP in una rete protetta.
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP, UWP, Unity, pacchetti UDP, socket, server client, endpoint, rete, computer remoto, datagrammiocket, esempio, .net
ms.openlocfilehash: a24498384ccb2018f62f00523bf33764d2ef7c019dec0cfd8fc70d86b55a81bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192557"
---
# <a name="udp-packets-in-unity-uwp-apps"></a>Pacchetti UDP nelle app UWP di Unity

È possibile configurare le app Unity della piattaforma UWP (Universal Windows Platform) per ricevere pacchetti UDP con l'aiuto di un client e un server socket UDP. I socket UDP non mantengono la connessione su entrambi gli endpoint, quindi sono una soluzione semplice e veloce per la rete tra computer remoti. Tuttavia, l'utente sarà responsabile del controllo se i pacchetti vengono inviati alla destinazione, perché i socket UDP non eserciteranno automaticamente questa operazione.

## <a name="setup"></a>Eseguire la configurazione

Aprire i progetti HoloLens manifest.jsfile e assicurarsi di aver abilitato:
* **Internet (Client & Server)** 
* **Reti private (client & Server)**.

## <a name="build-your-socket-client-and-server"></a>Creare il client e il server socket 

Seguire le istruzioni per la [compilazione di un client e un server socket UDP di base.](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server) Si usa la classe [DatagramSocket](/uwp/api/Windows.Networking.Sockets.DatagramSocket) per inviare e ricevere dati tramite UDP e formare un client e un server echo. È anche consigliabile leggere le altre sezioni relative alle risorse di questo articolo, in quanto si applicano a casi d'uso più personalizzati e complessi. 

> [!IMPORTANT]
> Se si verificano problemi durante l'invio di pacchetti UDP dal PC al PC, verificare che la rete consenta queste operazioni. Se la rete blocca i pacchetti UDP in qualsiasi modo, HoloLens dispositivo non sarà in grado di restare in ascolto.

È possibile scaricare un'app di esempio UDP DatagramSocket completa dal collegamento seguente:

> [!div class="nextstepaction"]
> [Installare gli strumenti](/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a>Vedere anche 
* [Esperimenti con l'autenticazione Ologrammi e il multicasting Archiviazione BLOB di Azure/UDP](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)