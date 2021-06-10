---
title: Esercitazioni sull'audio spaziale - 1. Aggiunta di audio spaziale al progetto
description: Aggiungere il plug-in Microsoft Spatializer al progetto Unity per accedere HoloLens 2 offload hardware HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens2, audio spaziale, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, funzione di trasferimento correlata alla testa, riverbero, Spazialista Microsoft
ms.openlocfilehash: 112531a3248461a5b380ad4b93de34545a2f2c3f
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403362"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. Aggiunta di audio spaziale al progetto Unity

## <a name="overview"></a>Panoramica

Benvenuti nell'esercitazione sull'audio spaziale per Unity in HoloLens2. In questa serie di esercitazioni si apprenderà come usare l'offload della funzione di trasferimento correlato alla testa (HRTF) in HoloLens 2 e Come abilitare il riverbero quando si usa l'offload HRTF.

Il [repository GitHub di Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) include un progetto Unity completato di questa sequenza di esercitazioni.

Per comprendere cosa significa spazializzare i suoni usando tecnologie di spazializzazione basate su HRTF e consigli su quando può essere utile, vedere Spatial Sound Design (Progettazione dei suoni [spaziali).](/windows/mixed-reality/spatial-sound-design)

## <a name="what-is-hrtf-offload"></a>Che cos'è l'offload HRTF?

L'elaborazione audio con algoritmi basati su HRTF richiede una grande quantità di calcoli specializzati. HoloLens 2 include hardware dedicato che può essere utilizzato per evitare il carico di lavoro del processore dell'applicazione, "offload" dell'elaborazione di algoritmi basati su HRTF.  Il plug-in microsoft spatializer offre un modo semplice per l'applicazione di sfruttare l'hardware HRTF dedicato, in modo che l'applicazione possa usare più processori dell'applicazione per operazioni diverse dall'audio spaziale.

## <a name="objectives"></a>Obiettivi

* Importazione e abilitazione del plug-in microsoft spatializer
* Abilitazione dell'audio spaziale nella workstation per sviluppatori

## <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti
* Conoscenza della programmazione C# di base
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020/2019 LTS montato e il modulo piattaforma UWP (Universal Windows Platform) Build Support aggiunto

È **consigliabile** completare la serie [di](mr-learning-base-01.md) esercitazioni introduttive o avere un'esperienza di base precedente con Unity e MRTK prima di continuare.

> [!Important]
> Questa serie di esercitazioni supporta Unity 2020 LTS (attualmente 2020.3.x) se si usa Open XR o Windows XR Plugin e anche Unity 2019 LTS (attualmente 2019.4.x) se si usa WSA legacy o Windows XR Plugin. Questa istruzione sostituisce gli eventuali requisiti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.

## <a name="creating-and-preparing-the-unity-project"></a>Creazione e preparazione del progetto Unity

In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.

A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), che include i passaggi seguenti:

1. [Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*

1. [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#configuring-the-unity-project)

1. [Importazione delle risorse essenziali TextMeshPro](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Importazione di Mixed Reality Toolkit e configurazione del progetto Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)

1. [Creazione e configurazione della scena e](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) assegnare alla scena un nome appropriato, ad esempio *SpatialAudio*

Segui quindi [](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) le istruzioni riportate in Modifica dell'opzione di visualizzazione della consapevolezza spaziale per assicurarti che il profilo di configurazione di MRTK per la scena sia **DefaultHoloLens2ConfigurationProfile** e modifica le opzioni di visualizzazione per la mesh di consapevolezza spaziale in **Occlusion**.

## <a name="adding-microsoft-spatializer-to-the-project"></a>Aggiunta di Microsoft Spatializer al progetto

Scaricare e importare  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a>

>[!TIP]
> Per un promemoria su come importare un pacchetto personalizzato di Unity, vedere le istruzioni relative all'importazione degli [asset dell'esercitazione.](mr-learning-base-02.md#importing-the-tutorial-assets)

## <a name="enable-the-microsoft-spatializer-plugin"></a>Abilitare il plug-in Microsoft Spatializer

Dopo aver importato Microsoft **Spatializer** nel progetto Unity, verrà visualizzata la finestra **MRTK Project Configurator(Configuratore progetto MRTK),** usare l'elenco a discesa **Spazializzatore audio** per selezionare l'utilità di spazializzatore Microsoft e quindi fare clic sul pulsante Applica per applicare l'impostazione:

![Configuratore di progetti MRTK](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

È anche possibile abilitare manualmente Microsoft Spatializer: Open **Edit -> Project Settings -> Audio** e modificare **Spatializer Plugin (Plug-in** spazializzatore Microsoft) in "Microsoft Spatializer".

![Impostazioni del progetto che mostra il plug-in dello spazializzatore](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a>Abilitare l'audio spaziale nella workstation

Nelle versioni desktop di Windows l'audio spaziale è disabilitato per impostazione predefinita. Abilitarla facendo clic con il pulsante destro del mouse sull'icona del volume nella barra delle applicazioni. Per ottenere la migliore rappresentazione di ciò che si HoloLens 2, scegliere Audio spaziale **-> Windows Sonic per cuffie**.

![Impostazioni audio spaziali del desktop](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> Questa impostazione è necessaria solo se si prevede di testare il progetto nell'editor di Unity.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come importare e abilitare il plug-in Microsoft Spatializer e come abilitare l'audio spaziale nella workstation.
Nell'esercitazione successiva si apprenderà come aggiungere audio spaziale nel progetto Unity.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 2. Spazializzazione dei suoni di interazione dei pulsanti](unity-spatial-audio-ch2.md)
