---
title: Debug gestito con Unity IL2CPP
description: Questo articolo illustra come eseguire un debugger gestito nel progetto Unity IL2CPP UWP.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, debug, il2cpp, HoloLens, cuffie per realtà mista, cuffie con realtà mista di Windows, cuffie per realtà virtuale, UWP
ms.openlocfilehash: 4b21e4888e467e6bd5f1938024a1b8312d8ecbcb
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010242"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>Debug gestito con Unity IL2CPP

Seguire questa procedura per aggiungere un debugger gestito alla build Unity IL2CPP UWP per HoloLens e HoloLens 2.

1. È necessario trovarsi in una rete che supporta il [multicast](https://en.wikipedia.org/wiki/Multicast).
2. Passare a **UWP Publishing Settings capabilities** e controllare **InternetClientServer** e **PrivateNetworkClientServer**:

    ![Funzionalità delle impostazioni di pubblicazione UWP](images/il2cpp-debugging-capabilities.png)

3. Configurare le impostazioni di compilazione UWP per Unity:
    - Development Build
    - Debug degli script
    - Attendi debugger gestito (facoltativo)

    ![Impostazioni di compilazione UWP](images/il2cpp-debugging-build.png)

4. Compilazione in Unity.
5. Compilare e distribuire dalla soluzione Visual Studio al dispositivo. È necessario compilare con le configurazioni di **debug** o di **rilascio** . La configurazione **Master** Disabilita il profiler di Unity ed è in grado di impedire il debug ottimale. Facoltativamente, verificare la **connessione Internet (client & Server)** e le **Reti Private (client & Server)** nell'elenco delle funzionalità di Package. appxmanifest nella soluzione.
6. Verificare che il dispositivo sia connesso alla stessa rete del PC e avviare l'app nel dispositivo.
7. Verificare che il dispositivo **non sia** connesso al PC tramite USB.
8. Fare doppio clic su uno degli script in Unity e passare alla soluzione Visual Studio che si apre per visualizzare e modificare.
9. Debug-> connessione del debugger Unity.

    ![Collega debugger Unity](images/il2cpp-debugging-attach.png)

10. Selezionare il dispositivo nell'elenco e fare clic su "OK" per connettersi.

    ![Elenco dei dispositivi](images/il2cpp-debugging-machines.png)
