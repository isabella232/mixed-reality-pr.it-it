---
title: Esercitazioni audio spaziali-1. Aggiunta di audio spaziale al progetto
description: Aggiungere il plug-in Microsoft Spatializer al progetto Unity per accedere a HoloLens 2 HRTF hardware offload.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale, MRTK, Toolkit per realtà mista, UWP, Windows 10, HRTF, funzione di trasferimento relativa alla testa, Reverb, Microsoft Spatializer
ms.openlocfilehash: 7d4702a21fccbb18c7c4b07675953c37785ae6db
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580222"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. aggiunta di audio spaziale al progetto Unity

## <a name="overview"></a>Panoramica

Benvenuti nell'esercitazione sull'audio spaziale per Unity in HoloLens2. Con questa serie di esercitazioni si apprenderà come usare l'offload della funzione di trasferimento Head-Related (HRTF) in HoloLens 2 e come abilitare il riverbero quando si usa l'offload HRTF.

Il [repository GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) include un progetto Unity completato di questa sequenza di esercitazione.

Per informazioni su ciò che significa spatialize i suoni usando le tecnologie di spazializzazione basate su HRTF e consigli per quando può essere utile, vedere [progettazione di suoni spaziali](/windows/mixed-reality/spatial-sound-design).

## <a name="what-is-hrtf-offload"></a>Che cos'è HRTF offload?

L'elaborazione di audio con algoritmi basati su HRTF richiede una grande quantità di calcoli specializzati. HoloLens 2 include hardware dedicato che può essere utilizzato per evitare di sovraccaricare il processore di applicazioni, quindi "offload" dell'elaborazione degli algoritmi basati su HRTF.  Il plug-in Microsoft Spatializer offre un modo semplice per consentire all'applicazione di sfruttare i vantaggi dell'hardware HRTF dedicato, in modo che l'applicazione possa usare più processori di applicazioni per operazioni diverse dall'audio spaziale.

## <a name="objectives"></a>Obiettivi

* Importazione e abilitazione del plug-in Microsoft Spatializer
* Abilitazione dell'audio spaziale nella workstation per sviluppatori

## <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti
* Conoscenza della programmazione C# di base
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019 LTS installato e il modulo di supporto per la compilazione UWP (Universal Windows Platform) aggiunto

Prima di continuare, è **consigliabile** completare la serie di esercitazioni [introduttive](mr-learning-base-01.md) oppure avere un'esperienza di base precedente con Unity e MRTK.

> [!IMPORTANT]
>
> * La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019 LTS. Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.

## <a name="creating-and-preparing-the-unity-project"></a>Creazione e preparazione del progetto Unity

In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.

A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), che include i passaggi seguenti:

1. [Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*

1. [Passaggio a un'altra piattaforma di compilazione](mr-learning-base-02.md#configuring-the-unity-project)

1. [Importazione delle risorse essenziali TextMeshPro](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Importazione di Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [Configurazione del progetto Unity](mr-learning-base-02.md#configuring-the-unity-project)

1. [Creazione e impostazione della scena](mr-learning-base-02.md#creating-and-configuring-the-scene) e assegnare alla scena un nome appropriato, ad esempio *SpatialAudio*

Quindi, seguire le istruzioni per la [modifica delle opzioni di visualizzazione di riconoscimento spaziale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) per verificare che il profilo di configurazione MRTK per la scena sia **DefaultXRSDKConfigurationProfile** e modificare le opzioni di visualizzazione per la mesh di riconoscimento spaziale in **occlusione**.

## <a name="adding-microsoft-spatializer-to-the-project"></a>Aggiunta di Microsoft Spatializer al progetto

Scaricare e importare Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft. SpatialAudio. Spatializer. Unity. 1.0.18. file unitypackage Tools </a>

>[!TIP]
> Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, puoi fare riferimento alle istruzioni contenute in [Importare Mixed Reality Toolkit](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Abilitare il plug-in Microsoft Spatializer

Dopo aver importato **Microsoft Spatializer** , è necessario abilitarlo. Aprire **modifica-> impostazioni progetto-> audio** e modificare il **plug** -in Spatializer in "Microsoft Spatializer".

![Impostazioni del progetto che mostrano il plug-in Spatializer](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>Abilitare l'audio spaziale nella workstation

Nelle versioni desktop di Windows, l'audio spaziale è disabilitato per impostazione predefinita. Per abilitarla, fare clic con il pulsante destro del mouse sull'icona del volume sulla barra delle applicazioni. Per ottenere la migliore rappresentazione di ciò che è possibile sentire in HoloLens 2, scegliere **audio spaziale > Windows Sonic per le cuffie**.

![Impostazioni audio spaziali desktop](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> Questa impostazione è necessaria solo se si prevede di testare il progetto nell'editor di Unity.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione è stato illustrato come importare e abilitare il plug-in Microsoft Spatializer e anche per abilitare l'audio spaziale nella workstation.
Nell'esercitazione successiva si apprenderà come aggiungere audio spaziale nel progetto Unity.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 2. suoni di interazione con il pulsante Spatializing](unity-spatial-audio-ch2.md)
