---
title: Debug gestito con Unity
description: Questo articolo illustra come eseguire un debugger gestito nel progetto UWP Unity IL2CPP.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity, visual studio, debug, il2cpp, HoloLens, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, UWP
ms.openlocfilehash: 48f5fbd4b2ac217a3f840117595aa36fb3d7c10e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394505"
---
# <a name="managed-debugging-with-unity"></a>Debug gestito con Unity

Segui questa procedura per collegare un debugger gestito alla build UWP unity IL2CPP per HoloLens e HoloLens 2.

1. È necessario essere in una rete che supporta il [multicast.](https://en.wikipedia.org/wiki/Multicast)
2. Passare a **Funzionalità delle impostazioni di pubblicazione UWP** e selezionare **InternetClientServer** e **PrivateNetworkClientServer:**

    ![Funzionalità delle impostazioni di pubblicazione UWP](images/il2cpp-debugging-capabilities.png)

3. Configurare le impostazioni di compilazione UWP di Unity:
    - Development Build
    - Debug degli script
    - Attendere il debugger gestito (facoltativo)

    ![Impostazioni di compilazione UWP](images/il2cpp-debugging-build.png)

4. Compilare in Unity.
5. Compilare e distribuire dalla Visual Studio al dispositivo. È consigliabile eseguire la compilazione con **le configurazioni Debug** **o** Release. La **configurazione master** disabilita il profiler Unity e può impedire il debug ottimale. Facoltativamente, verificare **Internet (Client & Server)** e Reti private **(Client & Server)** nell'elenco delle funzionalità in Package.appxmanifest nella soluzione.
6. Assicurarsi che il dispositivo sia connesso alla stessa rete del PC e avviare l'app nel dispositivo.
7. Assicurarsi che il **dispositivo non sia** connesso al PC tramite USB.
8. Fare doppio clic su uno degli script in Unity e passare alla Visual Studio che si apre per visualizzarlo e modificarlo.
9. Debug -> Collegare il debugger unity.

    ![Collega debugger Unity](images/il2cpp-debugging-attach.png)

10. Selezionare il dispositivo nell'elenco e fare clic su "OK" per collegarsi.

    ![Elenco dei dispositivi](images/il2cpp-debugging-machines.png)

## <a name="see-also"></a>Vedi anche 

* [Debug C#](/visualstudio/get-started/csharp/tutorial-debugger)
