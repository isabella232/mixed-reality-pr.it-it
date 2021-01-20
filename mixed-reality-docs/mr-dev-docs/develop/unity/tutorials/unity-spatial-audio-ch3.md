---
title: Esercitazioni audio spaziali-3. Spazializzazione dell'audio da un video
description: Importare un asset video nel progetto Unity e spatialize l'audio dal video.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale, MRTK, Toolkit per realtà mista, UWP, Windows 10, HRTF, funzione di trasferimento relativa alla testa, Reverb, Microsoft Spatializer, importazione video, lettore video
ms.openlocfilehash: 6474da522e650d23349a21c3deeac00222b8ce93
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578573"
---
# <a name="3-spatializing-audio-from-a-video"></a>3. Spazializzazione dell'audio da un video

## <a name="overview"></a>Panoramica

In questa esercitazione si apprenderà come spatialize audio da un'origine video e come testarlo nell'editor di Unity e in HoloLens 2.

## <a name="objectives"></a>Obiettivi

* Importare un video e aggiungere un lettore video
* Riprodurre il video su un quadrilatero
* Indirizzare l'audio dal video al quadrilatero e spatialize l'audio

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a>Importa un video e Aggiungi un lettore video alla scena

Per questa esercitazione è possibile usare [questo video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) dal progetto di esempio di audio spaziale.

Per importare video nel progetto Unity. nel menu di Unity selezionare **Asset**  >  **Importa nuovo** asset 
 ![ importazione asset](images/spatial-audio/spatial-audio-03-section1-step1-1.png)

Nella finestra **Importa nuovo asset...** selezionare il file **Microsoft HoloLens-Spatial Sound-PTPvx7mDon4** scaricato e fare clic sul pulsante **Apri** per importare l'asset nel progetto:

![Selezione asset](images/spatial-audio/spatial-audio-03-section1-step1-2.png)

La regolazione delle impostazioni di qualità nel clip video può garantire la riproduzione uniforme in HoloLens 2. Selezionare il file video nella finestra del **progetto** e nella finestra di controllo del file video, **sostituire** le impostazioni per le **app di Windows Store** e:

* Abilita **transcodifica**
* Imposta **codec** su H264
* Impostare la **Modalità bitrate** su low
* Impostare la **qualità spaziale** su una qualità media spaziale

Dopo queste modifiche, fare clic su Applica per modificare l'impostazione qualità nel clip video.

![Modifica proprietà video](images/spatial-audio/spatial-audio-03-section1-step1-3.png)

Fare clic con il pulsante destro del mouse sulla gerarchia e selezionare **video**  >  **video player** per aggiungere il componente lettore video.

![Aggiungi lettore video](images/spatial-audio/spatial-audio-03-section1-step1-4.png)

## <a name="play-video-onto-a-quadrangle"></a>Riprodurre video su un quadrilatero

L'oggetto **Player video** necessita di un oggetto gioco con trama per il rendering del video.

Fare clic con il pulsante destro del mouse sulla gerarchia, selezionare **oggetto 3D**  >  **Quad** per creare un quad e configurarne il componente **Transform** come indicato di seguito:

* **Posizione**: X = 0, Y = 0, Z = 2
* **Rotation** (Rotazione): X = 0, Y = 0, Z = 0
* **Scala**: X = 1,28, Y = 0,72, Z = 1

![Aggiungere un quad](images/spatial-audio/spatial-audio-03-section2-step1-1.png)

A questo punto è necessario creare una trama del **Quad** con il video, nella finestra del **progetto** , fare clic con il pulsante destro del mouse e scegliere **Crea**  >  **trama di rendering** per creare un componente di trama di rendering, immettere un nome appropriato per la trama di rendering, ad esempio, _trama audio spaziale_:

![Crea trama di rendering](images/spatial-audio/spatial-audio-03-section2-step1-2.png)

Selezionare la **trama di rendering** e nella finestra di controllo impostare la proprietà **dimensioni** in modo che corrisponda alla risoluzione nativa del video 1280x720. Quindi, per garantire prestazioni di rendering ottimali in HoloLens 2, impostare la proprietà **depth buffer** su almeno **16 bit di profondità**.

![Proprietà trama di rendering](images/spatial-audio/spatial-audio-03-section2-step1-3.png)

Successivamente, usare la trama dell' **audio spaziale** di rendering creata come trama per il **Quad**:

1. Trascinare la **trama audio spaziale** dalla finestra del **progetto** nel **Quad** della gerarchia per aggiungere la trama di rendering al quad
2. Per garantire prestazioni ottimali in HoloLens 2, selezionare quad nella gerarchia e nella finestra di controllo per shader selezionare lo shader standard di **mixed reality Toolkit**  >   .

![Proprietà trama quad](images/spatial-audio/spatial-audio-03-section2-step1-4.png)

Per impostare il **lettore video** e la **trama di rendering** per riprodurre il clip video, selezionare il **lettore video** nella **gerarchia** e nella finestra di **controllo** ,

* Impostare la proprietà **video clip** sul file video scaricato ' Microsoft HoloLens-Spatial Sound-PTPvx7mDon4'
* Casella di controllo **ciclo**
* Imposta la **trama di destinazione** sulla nuova trama dell' **audio spaziale** della trama di rendering

![Proprietà lettore video](images/spatial-audio/spatial-audio-03-section2-step1-5.png)

## <a name="spatialize-the-audio-from-the-video"></a>Spatialize l'audio dal video

Nella finestra gerarchia selezionare oggetto **Quad** , quindi nella finestra di controllo usare il pulsante **Aggiungi componente** per aggiungere l' **origine audio** a cui indirizzare l'audio dal video.

Nell' **origine audio**:

* Imposta **output** sul **mixer audio spaziale**
* Controllare la casella **Spatialize**
* Spostare il dispositivo di scorrimento di **Blend spaziale** su 1 (3D)

![Controllo origine audio quad](images/spatial-audio/spatial-audio-03-section3-step1-1.png)

Per impostare il lettore video in modo da instradare l'audio all' **origine audio**, selezionare il **lettore video** nella finestra gerarchia e nell'oggetto video player del controllo eseguire le modifiche seguenti.

* Impostare la **modalità di output audio** su **origine audio**
* Impostare la proprietà di **origine audio** sul **Quad**

![Origine audio del set di lettori video](images/spatial-audio/spatial-audio-03-section3-step1-2.png)

> [!TIP]
> Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come spatialize audio da un'origine video provare l'app in un HoloLens 2 o nell'editor di Unity. Il video viene visualizzato e l'audio del video è spaziale.

Nell'esercitazione successiva si apprenderà come abilitare e disabilitare la spazializzazione in fase di esecuzione

> [!div class="nextstepaction"]
> [Esercitazione successiva: 4. Abilitazione e disabilitazione della spazializzazione in fase di esecuzione](unity-spatial-audio-ch4.md)
