---
title: Scelta di una versione di Unity e plug-in XR
description: È possibile rimanere sempre aggiornati sulle raccomandazioni di Unity e plug-in di XR più recenti per lo sviluppo di applicazioni HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, auricolare realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale, Unity
ms.openlocfilehash: b8f5f0131da811393ee053541e0c2fa0c735472e
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938139"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Scelta di una versione di Unity e plug-in XR

Sebbene si **consigli attualmente l'installazione di unity 2019,4 LTS e l'uso di XR integrato legacy** per lo sviluppo di realtà miste, è possibile creare anche app con altre configurazioni Unity.

## <a name="unity-20194-lts-recommended"></a>Unity 2019,4 LTS (scelta consigliata)

La configurazione attuale di Unity consigliata da Microsoft per HoloLens 2 e lo sviluppo di realtà mista di Windows è **unity 2019,4 LTS che usa il supporto predefinito di XR** .

Il modo migliore per installare e gestire Unity è quello di <a href="https://unity3d.com/get-unity/download" target="_blank">[Hub Unity]</a>. Quando è installato, aprire Hub Unity:

1. Selezionare la scheda **Installa** e scegliere **Aggiungi** .
2. Selezionare Unity 2019,4 LTS e fare clic su **Next**

![Nuova versione di installazione Hub Unity](images/unity-hub-img-01.png)

3. Controllare i componenti seguenti in **' piattaforme '**
    * **Supporto di piattaforma UWP (Universal Windows Platform) Build** 
    * **Supporto per Windows Build (IL2CPP)**

![Opzione di supporto per Unity piattaforma UWP (Universal Windows Platform) Build](../images/Unity_Install_Option_UWP.png)

4. Se Unity è stata installata senza queste opzioni, è possibile aggiungerle tramite il menu **' Aggiungi moduli '** nell'hub Unity:

![Opzione di supporto build di Windows Unity](../images/Unity_Install_Option_UWP2.png)

Per iniziare a usare la versione precedente di XR incorporata in Unity 2019,4 LTS, fare clic qui:

> [!div class="nextstepaction"]
> [Configurare XR integrato legacy](legacy-xr-support.md)

> [!NOTE]
> Unity ha deprecato il supporto di XR incorporato legacy a partire da Unity 2019.  Sebbene Unity 2019 offra un nuovo Framework di plug-in di XR, Microsoft non è attualmente in grado di consigliare tale percorso in Unity 2019 a causa di incompatibilità con AR Foundation 2 per gli ancoraggi spaziali di Azure.  In Unity 2020, gli ancoraggi spaziali di Azure sono supportati all'interno del Framework di plug-in XR.

Se si sviluppano app per HoloLens (1a generazione), questi auricolari rimangono supportati in Unity 2019 LTS con XR incorporato legacy per il ciclo di vita completo di Unity 2019 LTS fino a metà 2022.

## <a name="unity-20203-lts"></a>Unity 2020,3 LTS 

Se si usa **unity 2020,3 LTS**, è possibile usare il **plug-in Windows XR** per sviluppare applicazioni per la realtà mista HoloLens 2 e Windows.

Tuttavia, esistono problemi noti che influiscono sulla stabilità degli ologrammi e altre funzionalità in HoloLens 2: 

* L'invio del buffer di profondità è stato regressione nelle compilazioni recenti di Unity 2020, con conseguente instabilità dell'ologramma grave.
* Le applicazioni di comunicazione remota di app olografiche che usano la destinazione di compilazione piattaforma UWP (Universal Windows Platform) non funzionano.
* Il sistema di processi grafici Unity è impostato sul valore predefinito, anche se non è compatibile con i progetti HoloLens.

Se si sceglie di avviare un nuovo progetto in Unity 2020 oggi, assicurarsi di seguire i prossimi mesi per le compilazioni Unity aggiornate e le compilazioni di plug-in di Windows XR prima di distribuire l'app.  In questo modo si garantisce che gli utenti sperimentino una corretta stabilità degli ologrammi.

> [!div class="nextstepaction"]
> [Uso del plug-in Windows XR](windows-xr-plugin.md)

### <a name="using-openxr"></a>Uso di OpenXR

Unity 2020,3 LTS supporta inoltre un'anteprima pubblica del plug-in OpenXR per la **realtà mista** .

Il plug-in OpenXR realtà mista supporta completamente AR Foundation 4,0, fornendo implementazioni ARPlaneManager e ARRaycastManager. In questo modo è possibile scrivere codice di hit testing una volta che si estende su HoloLens 2 e ARCore/ARKit Phone e tablet. 

Successivamente quest'anno, **unity 2020,3 LTS con il plug** -in OpenXR diventerà la configurazione di Unity consigliata e le funzionalità future di HoloLens 2 in Unity verranno esposte solo tramite questo plug-in.  È possibile avviare il progetto per il momento. Tuttavia, se il progetto è destinato a HoloLens 2, si verificherà attualmente la stabilità dell'ologramma Unity 2020 e altri problemi elencati sopra.  Prima di spedire l'app, assicurarsi di consultare i prossimi mesi per le compilazioni Unity aggiornate e le compilazioni di plug-in OpenXR.  In questo modo si garantisce che gli utenti sperimentino una corretta stabilità degli ologrammi. 

> [!div class="nextstepaction"]
> [Uso del plug-in OpenXR](openxr-getting-started.md)

## <a name="unity-20211"></a>Unity 2021,1

Se si sta provando a eseguire prime **unity 2021,1** Build, è consigliabile passare al **plug**-in OpenXR, perché il plug-in di Windows XR è deprecato.  A partire da Unity 2021,2, il plug-in OpenXR sarà l'unico percorso per lo sviluppo di realtà miste, perché il plug-in di Windows XR non sarà più supportato.

## <a name="unity-20184-lts"></a>Unity 2018,4 LTS

Se si dispone già di un progetto con Unity 2018,4 LTS, il motore Unity continuerà a essere supportato per 2 anni dopo il relativo rilascio.  Unity 2018 LTS raggiungerà la fine del servizio nella primavera del 2021.
