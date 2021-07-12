---
title: Scelta di una versione di Unity e di un plug-in XR
description: Rimanere aggiornati sulle raccomandazioni più recenti dei plug-in Unity e XR per lo HoloLens di applicazioni.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale, unity
ms.openlocfilehash: c69576e991f3fe32ae69fce10069ecdae65b3f9a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603682"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Scelta di una versione di Unity e di un plug-in XR

Anche se attualmente è consigliabile installare **Unity 2020.3 LTS** con il plug-in OpenXR di realtà mista più recente per lo sviluppo di realtà mista, è possibile compilare app anche con altre configurazioni di Unity.

## <a name="unity-20203-lts-recommended"></a>Unity 2020.3 LTS (scelta consigliata)

La configurazione corrente consigliata di Microsoft per lo sviluppo HoloLens 2 e Windows Mixed Reality è **Unity 2020.3 LTS** con il plug-in OpenXR di realtà mista più recente. È **necessario** usare la patch unity versione 2020.3.8f1 o successiva per evitare problemi di prestazioni noti con le build precedenti della versione 2020.3.

> [!IMPORTANT]
> Unity 2020 non supporta la destinazione HoloLens (prima generazione). Questi visori rimangono supportati in **[Unity 2019 LTS](#unity-20194-lts)** con legacy built-in XR per l'intero ciclo di vita di Unity 2019 LTS fino a metà 2022.

Il modo migliore per installare e gestire Unity è tramite **l'hub unity:**

1. Installare <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub**</a>.
2. Selezionare la **scheda Installazioni** e scegliere **Aggiungi**.
3. Selezionare **Unity 2020.3 LTS** e fare clic su **Avanti.**

![Installare la nuova versione dell'hub Unity](images/unity-hub-img-01.png)

4. Controllare i componenti seguenti in **"Piattaforme":**
    * **Supporto per Windows piattaforma universali**
    * **Windows Supporto della compilazione (IL2CPP)**

![Opzione di supporto per Windows di Unity Universal Windows Platform](../images/Unity_Install_Option_UWP.png)

5. Se Unity è stato installato in precedenza senza queste opzioni, è possibile aggiungerle tramite il menu **"Aggiungi moduli"** in Unity Hub:

![Opzione supporto Windows compilazione di Unity](../images/Unity_Install_Option_UWP2.png)

Dopo aver installato Unity 2020.3, iniziare a creare un progetto o aggiornare un progetto esistente usando il plug-in OpenXR di realtà mista:

> [!div class="nextstepaction"]
> [Configurare il progetto con il plug-in OpenXR](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> Sebbene sia consigliabile usare OpenXR per tutti i nuovi progetti, Unity 2020.3 LTS supporta anche il [plug-Windows XR.](xr-project-setup.md?tabs=windowsxr) Questo plug-in è completamente supportato, anche se non riceverà nuove funzionalità, ad esempio il supporto di AR Foundation 4.0.

## <a name="unity-20194-lts"></a>Unity 2019.4 LTS

Se è necessario usare Unity 2019, è possibile usare **Unity 2019 LTS con XR incorporato legacy.** Per iniziare a usare Legacy Built-in XR in Unity 2019.4 LTS, fare clic qui:

> [!div class="nextstepaction"]
> [Configurare il progetto con XR predefinito legacy](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> Unity ha deprecato il supporto XR incorporato legacy a data di Unity 2019.  Anche se Unity 2019 offre un nuovo framework plug-in XR, Microsoft attualmente non consiglia questo percorso in Unity 2019 a causa delle incompatibilità di Ancoraggi nello stato di Azure con AR Foundation 2.  In Unity 2020, Ancoraggi nello spaziali di Azure è supportato all'interno del framework plug-in XR.

Se si sviluppano app per HoloLens (prima generazione), questi visori rimangono supportati in Unity 2019 LTS con XR legacy incorporato per l'intero ciclo di vita di Unity 2019 LTS fino alla metà del 2022.

## <a name="unity-20212"></a>Unity 2021.2

Se si provano le prime build **di Unity 2021.2,** iniziare a usare il [**plug-in OpenXR di realtà mista.**](xr-project-setup.md?tabs=openxr) Il plug-in OpenXR è l'unico percorso per lo sviluppo di realtà mista in Unity 2021.2 e versioni successive, perché l'ultima versione di Unity per supportare il plug-in Windows XR è unity 2021.1.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Unity 2018.4 LTS ha raggiunto la fine della finestra di supporto Long-Term di Unity di due anni e non riceve più aggiornamenti da Unity, anche se i progetti continueranno a essere eseguiti.

Se si ha un progetto Unity 2018, è consigliabile pianificare una migrazione in avanti a Unity 2020.3 LTS e al plug-in OpenXR di realtà mista.