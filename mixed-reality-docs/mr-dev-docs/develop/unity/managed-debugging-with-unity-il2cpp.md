---
title: Debug gestito con Unity
description: Questo articolo illustra come eseguire un debugger gestito nel progetto UWP Unity IL2CPP.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity, visual studio, debug, il2cpp, HoloLens, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale, UWP
ms.openlocfilehash: 92b730768b6402b356e550d8f01d85e654832aef1ac382d8f992df615a9ce1b4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196543"
---
# <a name="managed-debugging-with-unity"></a>Debug gestito con Unity

Seguire questa procedura per collegare un debugger gestito alla build UWP di Unity IL2CPP per HoloLens e HoloLens 2.

1. È necessario essere in una rete che supporta [multicast](https://en.wikipedia.org/wiki/Multicast).
2. Passare a Funzionalità Impostazioni pubblicazione **UWP** e selezionare **InternetClientServer** e **PrivateNetworkClientServer:**

    ![Funzionalità di pubblicazione Impostazioni UWP](images/il2cpp-debugging-capabilities.png)

3. Configurare le impostazioni di compilazione UWP di Unity:
    - Development Build
    - Debug degli script
    - Attendere il debugger gestito (facoltativo)

    ![Compilazione UWP Impostazioni](images/il2cpp-debugging-build.png)

4. Compilare in Unity.
5. Compilare e distribuire dalla soluzione Visual Studio nel dispositivo. È consigliabile eseguire la compilazione con **le configurazioni debug** **o versione.** La **configurazione Master** disabilita il profiler Unity e può impedire il debug ottimale. Facoltativamente, verificare **Internet (Client & Server)** e Reti private **(Client & Server)** nell'elenco delle funzionalità in Package.appxmanifest nella soluzione.
6. Assicurarsi che il dispositivo sia connesso alla stessa rete del PC e avviare l'app nel dispositivo.
7. Assicurarsi che il **dispositivo non sia** connesso al PC tramite USB.
8. Fare doppio clic su uno degli script in Unity e passare alla soluzione Visual Studio visualizzata per visualizzarla e modificarla.
9. Debug -> collegare il debugger unity.

    ![Collega debugger Unity](images/il2cpp-debugging-attach.png)

10. Selezionare il dispositivo nell'elenco e fare clic su "OK" per collegarsi.

    ![Elenco dei dispositivi](images/il2cpp-debugging-machines.png)

## <a name="see-also"></a>Vedi anche 

* [Debug C#](/visualstudio/get-started/csharp/tutorial-debugger)
