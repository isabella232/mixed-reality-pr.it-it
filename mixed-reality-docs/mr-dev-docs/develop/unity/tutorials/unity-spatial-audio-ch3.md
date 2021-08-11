---
title: Esercitazioni sull'audio spaziale - 3. Spazializzazione dell'audio da un video
description: Importare un asset video nel progetto Unity e spazializzare l'audio dal video.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens2, spatial audio, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head-related transfer function, reverb, Microsoft Spatializer, video importing, Video Player
ms.openlocfilehash: 2926301aac9db67d3e72b0511600720c24e5965f52a23faa1230c381a47c9b90
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202934"
---
# <a name="3-spatializing-audio-from-a-video"></a>3. Spazializzazione dell'audio da un video

## <a name="overview"></a>Panoramica

In questa esercitazione si apprenderà come spazializzare l'audio da un'origine video e testarlo nell'editor unity e HoloLens 2.

## <a name="objectives"></a>Obiettivi

* Importare un video e aggiungere un lettore video
* Riprodurre il video in un quadrangolare
* Instradare l'audio dal video al quadrangolare e spazializzare l'audio

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a>Importare un video e aggiungere un lettore video alla scena

Per questa esercitazione usare È possibile usare [questo video dal progetto](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) di esempio di audio spaziale.

Per importare Video nel progetto unity. Nel menu Unity selezionare **Asset**  >  **Import New Asset Importing** 
 ![ Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)

Nella finestra **Importa nuovo** asset selezionare il file **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** scaricato e fare clic sul pulsante Apri per importare l'asset nel progetto: 

![Selezione dell'asset](images/spatial-audio/spatial-audio-03-section1-step1-2.PNG)

La regolazione delle impostazioni di qualità nel clip video può garantire una riproduzione uniforme HoloLens 2. Selezionare il file video nella **finestra Project** e nella finestra Inspector  (Controllo) del file video sostituire le impostazioni per Windows **Store Apps** e:

* Abilita **transcodifica**
* Impostare **Codec** su H264
* Impostare **La modalità a velocità in bit** su Bassa
* Impostare **Qualità spaziale su** Media Qualità spaziale

Dopo queste modifiche, fare clic su Applica per modificare l'impostazione della qualità nel clip video.

![Modifica della proprietà video](images/spatial-audio/spatial-audio-03-section1-step1-3.PNG)

Fare clic con il pulsante destro del mouse su Hierarchy **(Gerarchia),** selezionare  >  **Video Video Player (Lettore video video)** per aggiungere il componente Lettore video.

![Aggiungere un lettore video](images/spatial-audio/spatial-audio-03-section1-step1-4.PNG)

## <a name="play-video-onto-a-quadrangle"></a>Riprodurre video in un quadrangolare

Per **eseguire il rendering del** video, l'oggetto Lettore video richiede un oggetto gioco con trama.

Fare clic con il pulsante destro del mouse su Hierarchy (Gerarchia), selezionare 3D Object Quad (Quad oggetto **3D)** per  >   creare un quad e configurare il relativo **componente Transform** (Trasforma) come indicato di seguito:

* **Posizione:** X = 0, Y = 0, Z = 2
* **Rotation** (Rotazione): X = 0, Y = 0, Z = 0
* **Scala:** X = 1,28, Y = 0,72, Z = 1

![Aggiungere un quad](images/spatial-audio/spatial-audio-03-section2-step1-1.PNG)

A questo punto  è necessario trameare il quad con il video. Nella finestra **Project** fare clic con il pulsante destro del mouse e scegliere Crea trama di rendering per creare un componente Trama di rendering, immettere un nome appropriato per la trama di rendering, ad esempio  >   Trama _audio_ spaziale:

![Creare una trama di rendering](images/spatial-audio/spatial-audio-03-section2-step1-2.PNG)

Selezionare Trama **di rendering** e nella finestra Controllo impostare la proprietà **Dimensioni** in modo che corrisponda alla risoluzione nativa del video di 1280x720. Quindi, per garantire prestazioni di rendering ottimali HoloLens 2, impostare la proprietà **Depth Buffer** su **Almeno 16 bit di profondità.**

![Proprietà trama di rendering](images/spatial-audio/spatial-audio-03-section2-step1-3.PNG)

Usare quindi render texture **spatial audio texture (Trama audio spaziale** di rendering) creata come trama per il **quad**:

1. Trascinare **la trama audio** spaziale dalla finestra **Project** sul **quad** nella gerarchia per aggiungere la trama di rendering al quad
2. Per garantire prestazioni ottimali HoloLens 2, selezionare Quad nella gerarchia e nella finestra Inspector (Controllo) per lo shader selezionare **mixed reality Toolkit** Standard  >  **Shader(Shader Standard).**

![Proprietà trama quadrupla](images/spatial-audio/spatial-audio-03-section2-step1-4.PNG)

Per impostare **Lettore video e** **Trama di** rendering per  riprodurre il video clip, selezionare il lettore **video** nella gerarchia e nella finestra **Inspector (Controllo).**

* Impostare la **proprietà Video Clip** sul file video scaricato 'Microsoft HoloLens - Spatial Sound-PTPvx7mDon4'
* Selezionare la **casella di controllo** Ciclo
* Impostare **Trama di destinazione** sulla nuova trama di rendering Trama audio **spaziale**

![Proprietà del lettore video](images/spatial-audio/spatial-audio-03-section2-step1-5.PNG)

## <a name="spatialize-the-audio-from-the-video"></a>Spazializzare l'audio dal video

Nella finestra Hierarchy (Gerarchia) selezionare **Quad** object (Oggetto Quad), quindi nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente) per aggiungere **l'origine audio** a cui instradare l'audio dal video.

In **Origine audio**:

* Impostare **Output** **sull'audio spaziale Mixer**
* Selezionare la **casella Spazializza**
* Spostare il **dispositivo di scorrimento Fusione** spaziale su 1 (3D)

![Controllo origine audio quad](images/spatial-audio/spatial-audio-03-section3-step1-1.PNG)

Per impostare il lettore video in modo che instradare l'audio all'origine **audio,** selezionare Il lettore **video** nella finestra Gerarchia e in Lettore video in Controllo apportare le modifiche seguenti.

* Impostare la **modalità di output audio** su Origine **audio**
* Impostare la **proprietà Origine** audio sul **quad**

![Origine audio del set di lettore video](images/spatial-audio/spatial-audio-03-section3-step1-2.PNG)

> [!TIP]
> Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come spazializzare l'audio da un'origine video Provare l'app in un HoloLens 2 o nell'editor di Unity. Il video verrà visualizzato e sentito e l'audio del video verrà spazializzato.

Nell'esercitazione successiva si apprenderà come abilitare e disabilitare la spazializzazione in fase di esecuzione

> [!div class="nextstepaction"]
> [Esercitazione successiva: 4. Abilitazione e disabilitazione della spazializzazione in fase di esecuzione](unity-spatial-audio-ch4.md)
