---
title: Scelta di una versione di Unity e di un plug-in XR
description: Rimanere aggiornati sulle raccomandazioni più recenti per i plug-in Unity e XR per lo sviluppo di applicazioni HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, unity
ms.openlocfilehash: f37dbdccf175a5cea9a647f0c14b90682b19dfb3
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906856"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Scelta di una versione di Unity e di un plug-in XR

Anche se attualmente è consigliabile installare **Unity 2019.4 LTS** e usare XR incorporato legacy per lo sviluppo di realtà mista, è possibile compilare app anche con altre configurazioni di Unity.

## <a name="unity-20194-lts-recommended"></a>Unity 2019.4 LTS (scelta consigliata)

L'attuale configurazione di Unity consigliata da Microsoft per lo sviluppo HoloLens 2 e Windows Mixed Reality è **Unity 2019.4 LTS** con il supporto XR incorporato legacy.

Il modo migliore per installare e gestire Unity è <a href="https://unity3d.com/get-unity/download" target="_blank">tramite [Unity Hub]</a>. Al termine dell'installazione, aprire Unity Hub:

1. Selezionare la **scheda Installazioni** e scegliere **AGGIUNGI**
2. Selezionare Unity 2019.4 LTS e fare clic su **Avanti**

![Nuova versione dell'hub unity](images/unity-hub-img-2019.png)

3. Controllare i componenti seguenti in **"Piattaforme"**
    * **piattaforma UWP (Universal Windows Platform) di compilazione** 
    * **Supporto per la compilazione di Windows (IL2CPP)**

![Opzione supporto piattaforma UWP (Universal Windows Platform) compilazione di Unity](images/Unity_Install_Option_UWP_2019.png)

4. Se Unity è stato installato senza queste opzioni, è possibile aggiungerlo tramite il menu **"Aggiungi moduli"** in Unity Hub:

![Opzione Unity Windows Build Support (Supporto per la compilazione di Windows in Unity)](images/Unity_Install_Option_UWP2_2019.png)

Per iniziare a usare legacy built-in XR in Unity 2019.4 LTS, fare clic qui:

> [!div class="nextstepaction"]
> [Configurare la versione legacy di XR incorporata](./xr-project-setup.md?tabs=legacy)

> [!NOTE]
> Unity ha deprecato il supporto XR incorporato legacy a livello di Unity 2019.  Anche se Unity 2019 offre un nuovo framework plug-in XR, Microsoft attualmente non consiglia tale percorso in Unity 2019 a causa delle incompatibilità di Ancoraggi nello stato di Azure con AR Foundation 2.  In Unity 2020 Ancoraggi nello stato di Azure è supportato all'interno del framework plug-in XR.

Se stai sviluppando app per HoloLens (prima generazione), questi visori VR rimangono supportati in Unity 2019 LTS con XR legacy incorporato per l'intero ciclo di vita di Unity 2019 LTS fino alla metà del 2022.

## <a name="unity-20203-lts"></a>Unity 2020.3 LTS 

Se si usa **Unity 2020.3 LTS,** la raccomandazione corrente di Microsoft è il plug-in **OpenXR di Realtà mista più recente.** È NECESSARIO usare la patch di Unity versione 2020.3.8f1 o successiva per evitare problemi di prestazioni noti con le build precedenti della versione 2020.3.

Il plug-in OpenXR di realtà mista supporta completamente AR Foundation 4.0, fornendo implementazioni ARPlaneManager e ARRaycastManager. In questo modo è possibile scrivere il codice di hit testing una volta che si estende su HoloLens 2 e su telefoni e tablet ARCore/ARKit.

Esistono tuttavia problemi noti che interessano i progetti Unity 2020 LTS:

* La pipeline di rendering universale (URP) 10.5.0 o versione precedente presenta una penalità per le prestazioni HoloLens 2 dispositivi.

Se si sceglie di avviare un nuovo progetto in Unity 2020 oggi stesso, assicurarsi di seguire le prossime settimane per le compilazioni Unity aggiornate e i pacchetti URP prima di spedire l'app.  Ciò garantisce che gli utenti sperimentino una corretta stabilità dell'ologramma.

> [!div class="nextstepaction"]
> [Uso del plug-in OpenXR](./xr-project-setup.md?tabs=openxr)

## <a name="unity-20211"></a>Unity 2021.1

Se si provano le prime build di **Unity 2021.1,** è consigliabile passare al plug-in **OpenXR,** perché il plug-in Windows XR è deprecato.  A partire da Unity 2021.2, il plug-in OpenXR sarà l'unico percorso per lo sviluppo di realtà mista, perché il plug-in Windows XR non sarà più supportato.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Se si ha già un progetto che usa Unity 2018.4 LTS, il motore Unity continuerà a essere supportato per 2 anni dopo il rilascio.  Unity 2018 LTS raggiungerà la fine del servizio nella primavera del 2021.