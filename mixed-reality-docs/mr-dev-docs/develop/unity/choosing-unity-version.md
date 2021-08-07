---
title: Scelta di una versione di Unity e di un plug-in XR
description: Rimanere aggiornati sulle raccomandazioni più recenti per i plug-in Unity e XR HoloLens sviluppo di applicazioni.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, unity
ms.openlocfilehash: 7d22ccee301345352ae384f8b237415f925bbd254e0923197130caf48540c171
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210888"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Scelta di una versione di Unity e di un plug-in XR

Anche se attualmente è consigliabile installare **Unity 2020.3 LTS** con il plug-in OpenXR di Realtà mista più recente per lo sviluppo di realtà mista, è possibile creare app anche con altre configurazioni unity.

## <a name="unity-20203-lts-recommended"></a>Unity 2020.3 LTS (scelta consigliata)

L'attuale configurazione di Unity consigliata da Microsoft per lo sviluppo HoloLens 2 e Windows Mixed Reality è **Unity 2020.3 LTS** con il plug-in OpenXR di Realtà mista più recente. È **necessario** usare la patch unity versione 2020.3.8f1 o successiva per evitare problemi di prestazioni noti con le build precedenti della versione 2020.3.

> [!IMPORTANT]
> Unity 2020 non supporta la destinazione HoloLens (prima generazione). Questi visori VR rimangono supportati in **[Unity 2019 LTS](#unity-20194-lts)** con XR legacy incorporato per l'intero ciclo di vita di Unity 2019 LTS fino alla metà del 2022.

Il modo migliore per installare e gestire Unity è tramite **Unity Hub:**

1. Installare <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub.**</a>
2. Selezionare la **scheda Installazioni** e scegliere **Aggiungi.**
3. Selezionare **Unity 2020.3 LTS** e fare clic su **Avanti.**

![Installare la nuova versione di Unity Hub](images/unity-hub-img-01.png)

4. Controllare i componenti seguenti in **"Piattaforme":**
    * **Supporto per la compilazione della piattaforma Windows universali**
    * **Windows Supporto della compilazione (IL2CPP)**

![Opzione supporto per la compilazione di Unity universal Windows Platform](../images/Unity_Install_Option_UWP.png)

5. Se Unity è stato installato in precedenza senza queste opzioni, è possibile aggiungerlo tramite il menu **"Aggiungi moduli"** in Unity Hub:

![Opzione supporto Windows compilazione di Unity](../images/Unity_Install_Option_UWP2.png)

Dopo aver installato Unity 2020.3, iniziare a creare un progetto o ad aggiornare un progetto esistente usando il plug-in OpenXR di Realtà mista:

> [!div class="nextstepaction"]
> [Configurare il progetto con il plug-in OpenXR](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> Anche se è consigliabile usare OpenXR per tutti i nuovi progetti, Unity 2020.3 LTS supporta anche Windows [plug-in XR.](xr-project-setup.md?tabs=windowsxr) Questo plug-in è completamente supportato, anche se non riceverà nuove funzionalità, ad esempio il supporto di AR Foundation 4.0.

## <a name="unity-20194-lts"></a>Unity 2019.4 LTS

Se è necessario usare Unity 2019, è possibile usare **Unity 2019 LTS con XR incorporato legacy.** Per iniziare a usare XR incorporato legacy in Unity 2019.4 LTS, fare clic qui:

> [!div class="nextstepaction"]
> [Configurare il progetto con XR predefinito legacy](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> Unity ha deprecato il supporto XR incorporato legacy a livello di Unity 2019.  Anche se Unity 2019 offre un nuovo framework plug-in XR, Microsoft attualmente non consiglia tale percorso in Unity 2019 a causa delle incompatibilità di Ancoraggi nello stato di Azure con AR Foundation 2.  In Unity 2020 Ancoraggi nello stato di Azure è supportato all'interno del framework plug-in XR.

Se si sviluppano app per HoloLens (prima generazione), questi visori VR rimangono supportati in Unity 2019 LTS con XR legacy incorporato per l'intero ciclo di vita di Unity 2019 LTS fino alla metà del 2022.

## <a name="unity-20212"></a>Unity 2021.2

Se si provano le prime build **di Unity 2021.2,** iniziare a usare il plug-in [**OpenXR di Realtà mista.**](xr-project-setup.md?tabs=openxr) Il plug-in OpenXR è l'unico percorso per lo sviluppo di realtà mista in Unity 2021.2 e versioni successive, perché la versione finale di Unity per supportare il plug-in Windows XR è Unity 2021.1.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Unity 2018.4 LTS ha raggiunto la fine della finestra di supporto di Long-Term per due anni di Unity e non riceve più aggiornamenti da Unity, anche se i progetti continueranno a essere eseguiti.

Se si ha un progetto Unity 2018, è consigliabile pianificare una migrazione a Unity 2020.3 LTS e al plug-in OpenXR di Realtà mista.