---
title: Scelta di una versione di Unity e di un plug-in XR
description: Rimanere aggiornati sulle raccomandazioni più recenti dei plug-in Unity e XR per lo sviluppo di applicazioni HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale, unity
ms.openlocfilehash: febeb46972935a02d9c945e2a0cafabebedd0715
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333383"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Scelta di una versione di Unity e di un plug-in XR

Anche se attualmente è consigliabile installare **Unity 2019.4 LTS** e usare XR incorporato legacy per lo sviluppo di realtà mista, è possibile compilare app anche con altre configurazioni di Unity.

## <a name="unity-20194-lts-recommended"></a>Unity 2019.4 LTS (scelta consigliata)

La configurazione di Unity consigliata di Microsoft per lo sviluppo HoloLens 2 e Windows Mixed Reality è **Unity 2019.4 LTS** usando il supporto XR incorporato legacy.

Il modo migliore per installare e gestire Unity è <a href="https://unity3d.com/get-unity/download" target="_blank">tramite [Hub Unity]</a>. Al termine dell'installazione, aprire Unity Hub:

1. Selezionare la **scheda Installazioni** e scegliere **AGGIUNGI**
2. Selezionare Unity 2019.4 LTS e fare clic su **Avanti**

![Unity hub instal new version](images/unity-hub-img-01.png)

3. Controllare i componenti seguenti in **"Piattaforme"**
    * **piattaforma UWP (Universal Windows Platform) di compilazione** 
    * **Supporto per la compilazione di Windows (IL2CPP)**

![Opzione supporto piattaforma UWP (Universal Windows Platform) compilazione di Unity](../images/Unity_Install_Option_UWP.png)

4. Se Unity è stato installato senza queste opzioni, è possibile aggiungerle tramite il menu **"Aggiungi moduli"** in Unity Hub:

![Opzione supporto compilazione Di Unity per Windows](../images/Unity_Install_Option_UWP2.png)

Per iniziare a usare Legacy Built-in XR in Unity 2019.4 LTS, fare clic qui:

> [!div class="nextstepaction"]
> [Configurare la versione XR incorporata legacy](legacy-xr-support.md)

> [!NOTE]
> Unity ha deprecato il supporto XR incorporato legacy a livello di Unity 2019.  Anche se Unity 2019 offre un nuovo framework plug-in XR, Microsoft attualmente non consiglia tale percorso in Unity 2019 a causa delle incompatibilità di Ancoraggi nello stato di Azure con AR Foundation 2.  In Unity 2020 Ancoraggi nello stato di Azure è supportato all'interno del framework plug-in XR.

Se stai sviluppando app per HoloLens (prima generazione), questi visori VR rimangono supportati in Unity 2019 LTS con XR legacy incorporato per l'intero ciclo di vita di Unity 2019 LTS fino alla metà del 2022.

## <a name="unity-20203-lts"></a>Unity 2020.3 LTS 

Se si usa **Unity 2020.3 LTS,** è possibile usare il plug-in **Windows XR** per sviluppare HoloLens 2 e Windows Mixed Reality applicazioni.

Esistono tuttavia problemi noti che influiscono sulla stabilità degli ologrammi e su altre funzionalità HoloLens 2: 

* Le applicazioni di comunicazione remota di app olografiche che piattaforma UWP (Universal Windows Platform) destinazione di compilazione non funzionano.
* Il sistema di processi grafici unity è quello predefinito, anche se non è compatibile con i progetti HoloLens.

Se si sceglie di usare Unity 2020, assicurarsi di eseguire l'aggiornamento a Unity 2020.3.6f1 o versioni successive per garantire la corretta stabilità dell'ologramma.

> [!div class="nextstepaction"]
> [Uso del plug-in Windows XR](windows-xr-plugin.md)

### <a name="using-openxr"></a>Uso di OpenXR

Unity 2020.3 LTS supporta anche un'anteprima pubblica del plug-in **OpenXR di Realtà** mista.

Il plug-in OpenXR di realtà mista supporta completamente AR Foundation 4.0, fornendo implementazioni ARPlaneManager e ARRaycastManager. In questo modo è possibile scrivere il codice di hit testing una volta che si estende su HoloLens 2 e su telefoni e tablet ARCore/ARKit. 

Più avanti quest'anno, **Unity 2020.3 LTS** con il plug-in OpenXR diventerà la configurazione di Unity consigliata e le future funzionalità HoloLens 2 in Unity verranno esposte solo tramite questo plug-in.

> [!div class="nextstepaction"]
> [Uso del plug-in OpenXR](openxr-getting-started.md)

## <a name="unity-20211"></a>Unity 2021.1

Se si provano le prime build di **Unity 2021.1,** è consigliabile passare al plug-in **OpenXR,** perché il plug-in Windows XR è deprecato.  A partire da Unity 2021.2, il plug-in OpenXR sarà l'unico percorso per lo sviluppo di realtà mista, perché il plug-in Windows XR non sarà più supportato.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Se si ha già un progetto che usa Unity 2018.4 LTS, il motore unity continua a essere supportato per 2 anni dopo il rilascio.  Unity 2018 LTS raggiungerà la fine del servizio nella primavera del 2021.
