---
title: Scelta di una versione di Unity e di un plug-in XR
description: Rimanere aggiornati sulle raccomandazioni più recenti dei plug-in Unity e XR per lo sviluppo di applicazioni HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale, unity
ms.openlocfilehash: 11f930f014ff579db1f8845d52b7a2d65dd85d6b
ms.sourcegitcommit: 4ea9ba1ca1cde426b016111c4176a4b0a9c17553
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113080698"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Scelta di una versione di Unity e di un plug-in XR

Anche se attualmente è consigliabile installare **Unity 2020.3 LTS** con il plug-in OpenXR di realtà mista più recente per lo sviluppo di realtà mista, è possibile compilare app anche con altre configurazioni di Unity.

## <a name="unity-20203-lts-recommended"></a>Unity 2020.3 LTS (scelta consigliata)

La configurazione di Unity consigliata di Microsoft per lo sviluppo HoloLens 2 e Windows Mixed Reality è **Unity 2020.3 LTS** con il plug-in OpenXR di Realtà mista più recente. È NECESSARIO usare la patch unity versione 2020.3.8f1 o successiva per evitare problemi di prestazioni noti con le build precedenti della versione 2020.3.

> [!IMPORTANT]
> Unity 2020 non supporta la destinazione di HoloLens (prima generazione). Questi visori rimangono supportati in **[Unity 2019 LTS](#unity-20194-lts)** con legacy built-in XR per l'intero ciclo di vita di Unity 2019 LTS fino a metà 2022.
>
> [!NOTE]
> Rendering remoto di Azure non è ancora stata fornita una versione aggiornata che supporta Unity 2020.
>
> Se il progetto Unity usa Rendering remoto di Azure, è consigliabile evitare di aggiornare il progetto a Unity 2020 fino a quando non è disponibile un pacchetto aggiornato.

Il modo migliore per installare e gestire Unity è tramite <a href="https://unity3d.com/get-unity/download" target="_blank">l'hub unity.</a> Al termine dell'installazione, aprire Unity Hub:

1. Selezionare la **scheda Installazioni** e scegliere **AGGIUNGI**
2. Selezionare Unity 2020.3 LTS e fare clic su **Avanti**

![Unity hub instal new version](images/unity-hub-img-01.png)

3. Controllare i componenti seguenti in **"Piattaforme"**
    * **piattaforma UWP (Universal Windows Platform) di compilazione**
    * **Supporto per la compilazione di Windows (IL2CPP)**

![Opzione supporto piattaforma UWP (Universal Windows Platform) compilazione di Unity](../images/Unity_Install_Option_UWP.png)

4. Se Unity è stato installato senza queste opzioni, è possibile aggiungerle tramite il menu **"Aggiungi moduli"** in Unity Hub:

![Opzione supporto compilazione Di Unity per Windows](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [Uso del plug-in OpenXR](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> Sebbene sia consigliabile usare OpenXR per tutti i nuovi progetti, Unity 2020.3 LTS supporta anche il plug-in [Windows XR.](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr) Questo plug-in è completamente supportato, anche se non riceverà nuove funzionalità, ad esempio il supporto di AR Foundation 4.0.

## <a name="unity-20194-lts"></a>Unity 2019.4 LTS

Se è necessario usare Unity 2019, è possibile usare **Unity 2019 LTS con XR incorporato legacy.** Per iniziare a usare Legacy Built-in XR in Unity 2019.4 LTS, fare clic qui:

> [!div class="nextstepaction"]
> [Configurare la versione XR incorporata legacy](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> Unity ha deprecato il supporto XR incorporato legacy a data di Unity 2019.  Anche se Unity 2019 offre un nuovo framework plug-in XR, Microsoft attualmente non consiglia questo percorso in Unity 2019 a causa delle incompatibilità di Ancoraggi nello stato di Azure con AR Foundation 2.  In Unity 2020, Ancoraggi nello spaziali di Azure è supportato all'interno del framework plug-in XR.

Se si sviluppano app per HoloLens (prima generazione), questi visori rimangono supportati in Unity 2019 LTS con XR legacy incorporato per l'intero ciclo di vita di Unity 2019 LTS fino alla metà del 2022.

## <a name="unity-20211"></a>Unity 2021.1

Se si provano le prime build **di Unity 2021.1,** è consigliabile passare al **plug-in OpenXR,** perché il plug-in Windows XR è deprecato.  A partire da Unity 2021.2, il plug-in OpenXR sarà l'unico percorso per lo sviluppo di realtà mista, perché il plug-in Windows XR non sarà più supportato.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Se si ha già un progetto che usa Unity 2018.4 LTS, il motore unity continuerà a essere supportato per 2 anni dopo il rilascio.  Unity 2018 LTS raggiungerà la fine del servizio nella primavera del 2021.
