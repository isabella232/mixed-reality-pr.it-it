---
title: Esercitazioni sull'audio spaziale - 1. Aggiunta di audio spaziale al progetto
description: Aggiungere il plug-in Microsoft Spatializer al progetto Unity per accedere HoloLens 2'offload hardware HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens2, spatial audio, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head-related transfer function, reverb, Microsoft Spatializer
ms.openlocfilehash: 7f40e99e72a90de777e672f131afff5d05fe6416bd225c5b656678e340cc813d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211733"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. Aggiunta dell'audio spaziale al progetto Unity

## <a name="overview"></a>Panoramica

Benvenuti nell'esercitazione sull'audio spaziale per Unity in HoloLens2. Questa serie di esercitazioni illustra come usare l'offload della funzione di trasferimento correlato alla testa (HRTF) in HoloLens 2 e Come abilitare il riverbero quando si usa l'offload HRTF.

Il [repository Microsoft Spatializer GitHub](https://github.com/microsoft/spatialaudio-unity) ha un progetto Unity completato di questa sequenza di esercitazioni.

Per comprendere cosa significa spazializzare i suoni usando tecnologie di spazializzazione basate su HRTF e consigli su quando può essere utile, vedere Progettazione del suono [spaziale](/windows/mixed-reality/spatial-sound-design).

## <a name="what-is-hrtf-offload"></a>Che cos'è l'offload HRTF?

L'elaborazione dell'audio con algoritmi basati su HRTF richiede una grande quantità di calcoli specializzati. HoloLens 2 include hardware dedicato che può essere utilizzato per evitare di gravare sul processore dell'applicazione, "offload" dell'elaborazione di algoritmi basati su HRTF.  Il plug-in microsoft spatializer offre un modo semplice per l'applicazione di sfruttare l'hardware HRTF dedicato in modo che l'applicazione possa usare più del processore dell'applicazione per operazioni diverse dall'audio spaziale.

## <a name="objectives"></a>Obiettivi

* Importazione e abilitazione del plug-in microsoft spatializer
* Abilitazione dell'audio spaziale nella workstation di sviluppo

## <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti
* Conoscenza della programmazione C# di base
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020/2019 LTS montato e il modulo Universal Windows Platform Build Support aggiunto

È **consigliabile** completare la serie [di](mr-learning-base-01.md) esercitazioni introduttive o avere un'esperienza di base precedente con Unity e MRTK prima di continuare.

> [!Important]
> Questa serie di esercitazioni supporta unity 2020 LTS (attualmente 2020.3.x) se si usa Open XR o Windows XR Plugin e anche Unity 2019 LTS (attualmente 2019.4.x) se si usa Legacy WSA o Windows XR Plugin. Questa istruzione sostituisce gli eventuali requisiti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.

## <a name="creating-and-preparing-the-unity-project"></a>Creazione e preparazione del progetto Unity

In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.

A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), che include i passaggi seguenti:

1. [Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*
2. [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#configuring-the-unity-project)
3. [Importazione delle risorse essenziali TextMeshPro](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Importazione del progetto Toolkit realtà mista e configurazione del progetto Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Creazione e configurazione della scena e](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) assegnare alla scena un nome appropriato, ad esempio *SpatialAudio*

Seguire quindi [](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) le istruzioni relative alla modifica dell'opzione di visualizzazione della consapevolezza spaziale per assicurarsi che il profilo di configurazione MRTK per la scena sia **DefaultHoloLens2ConfigurationProfile** e modificare le opzioni di visualizzazione per la mesh di riconoscimento spaziale in **Occlusion**.

## <a name="adding-microsoft-spatializer-to-the-project"></a>Aggiunta di Microsoft Spatializer alla Project

Scaricare e importare  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">microsoft.Spatializer Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a>

>[!TIP]
> Per un promemoria su come importare un pacchetto personalizzato di Unity, è possibile fare riferimento alle istruzioni sull'importazione degli [asset dell'esercitazione.](mr-learning-base-04.md#importing-the-tutorial-assets)

## <a name="enable-the-microsoft-spatializer-plugin"></a>Abilitare il plug-in Microsoft Spatializer

Dopo aver importato Microsoft Spatializer nel progetto Unity, verrà visualizzata la finestra **MRTK Project Configurator,** usare l'elenco a discesa **Spazializzatore audio** per selezionare **Microsoft Spatializer** e quindi fare clic sul pulsante Applica per applicare l'impostazione:

![Configuratore Project MRTK](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

È anche possibile abilitare manualmente Microsoft Spatializer: Open **Edit -> Project Impostazioni -> Audio** e impostare **Spatializer Plugin** su "Microsoft Spatializer".

![Project Impostazioni il plug-in dello spazializzatore](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a>Abilitare l'audio spaziale nella workstation

Nelle versioni desktop di Windows, l'audio spaziale è disabilitato per impostazione predefinita. Abilitarlo facendo clic con il pulsante destro del mouse sull'icona del volume nella barra delle applicazioni. Per ottenere la migliore rappresentazione di ciò che si HoloLens 2, scegliere **Suono spaziale -> Windows Sonic per cuffie**.

![Impostazioni audio spaziali del desktop](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> Questa impostazione è necessaria solo se si prevede di testare il progetto nell'editor di Unity.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come importare e abilitare il plug-in Microsoft Spatializer e come abilitare l'audio spaziale nella workstation.
Nell'esercitazione successiva si apprenderà come aggiungere audio spaziale nel progetto unity.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 2. Spazializzazione dei suoni di interazione del pulsante](unity-spatial-audio-ch2.md)
