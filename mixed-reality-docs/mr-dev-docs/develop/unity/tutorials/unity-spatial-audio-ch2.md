---
title: Esercitazioni sull'audio spaziale - 2. Spazializzazione dei suoni di interazione del pulsante
description: Aggiungere un pulsante al progetto e spazializzare i suoni di interazione del pulsante.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens2, spatial audio, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head-related transfer function, reverb, Microsoft Spatializer, prefabs, volume curve
ms.openlocfilehash: e0f916ecf8cd8da81e0738b082021c76c55a7f2031517a37b959575e1b21ce16
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209838"
---
# <a name="2-spatializing-button-interaction-sounds"></a>2. Spazializzazione dei suoni di interazione del pulsante

## <a name="overview"></a>Panoramica

In questa esercitazione si apprenderà come spazializzare i suoni di interazione del pulsante e come usare un clip audio per testare l'interazione con il pulsante spazializzato.  

## <a name="objectives"></a>Obiettivi

* Aggiungere e spazializzare i suoni di clic del pulsante

## <a name="add-a-button"></a>Aggiungere un pulsante

Per aggiungere il prefab button, nella finestra Project **selezionare** **Pacchetti** e digitare "PressableButtonHoloLens2" nella barra di ricerca.

![Prefab dei pulsanti in Asset](images/spatial-audio/spatial-audio-02-section1-step1-1.PNG)

Il prefab del pulsante è la voce rappresentata da un'icona blu. Fare clic e trascinare il prefab **PressableButtonHoloLens2** nella gerarchia. Con **l'oggetto PressableButtonHoloLens2** ancora selezionato, nella finestra Inspector configurare **il componente Transform** come indicato di seguito:

* **Posizione:** X = 0, Y = -0,4, Z = 2
* **Rotation** (Rotazione): X = 0, Y = 0, Z = 0
* **Scale** (Scala): X = 1, Y = 1, Z = 1

![Trasformazione pulsante](images/spatial-audio/spatial-audio-02-section1-step1-2.PNG)

Per concentrarsi sugli oggetti nella scena, è possibile fare doppio clic sull'oggetto **PressableButtonHoloLens2** e quindi eseguire di nuovo lo zoom avanti leggermente:

## <a name="spatialize-button-feedback"></a>Commenti e suggerimenti sui pulsanti Spazializza

In questo passaggio si spazializzerà il feedback audio per il pulsante. Per suggerimenti di progettazione correlati, vedere [Progettazione del suono spaziale.](../../../design/spatial-sound-design.md)

Nella finestra **Mixer** audio si definiranno le destinazioni denominate **gruppi** Mixer , per la riproduzione audio dai **componenti origine** audio.

Per aprire la **finestra Audio Mixer,** nel menu Unity selezionare **Finestra**  >  **Audio**  >  **audio Mixer**: Apri audio Mixer ![ finestra](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)

 Creare un **Mixer** facendo clic su "+" accanto a **Mixer** e immettere un nome appropriato per il Mixer ad esempio, _Spatial Audio Mixer_. Il nuovo mixer includerà un gruppo **predefinito** denominato **Master**.

![Mixer pannello con il primo mixer](images/spatial-audio/spatial-audio-02-section2-step1-2.PNG)

> [!NOTE]
> Fino a quando il riverbero non viene abilitato nel [5° capitolo:](unity-spatial-audio-ch5.md)Uso del riverbero per aggiungere la distanza all'audio spaziale, il misuratore del volume del mixer non mostra l'attività per i suoni riprodotti tramite Microsoft Spatializer

Nella finestra Hierarchy (Gerarchia) selezionare **PressableButtonHoloLens2** e quindi nella finestra Inspector (Controllo) trovare il componente Audio Source (Origine **audio)** e Configure the Audio Source component (Configura origine audio) come indicato di seguito:

1. Per la **proprietà Output** fare clic sul selettore e scegliere il **Mixer** creato.
2. Selezionare la **casella di controllo Spazializza.**
3. Spostare il **dispositivo di scorrimento Fusione** spaziale su 3D (1).

![Origine audio del pulsante](images/spatial-audio/spatial-audio-02-section2-step1-3.PNG)

> [!NOTE]
> Se si sposta **Spatial Blend** su 1 (3D) senza selezionare la casella di controllo **Spatialize,** Unity userà il suo spazializzatore di panoramica, anziché **Microsoft Spatializer** con HRTFs.

## <a name="adjust-the-volume-curve"></a>Regolare la curva del volume

Per impostazione predefinita, Unity attenua i suoni spazializzati quando si allontanano dal listener. Quando questa attenuazione viene applicata ai suoni di feedback dell'interazione, l'interfaccia può diventare più difficile da usare.

Per disabilitare questa attenuazione, è necessario regolare la **curva del volume** nel componente **Origine** audio.

Nella finestra Hierarchy (Gerarchia) selezionare **PressableButtonHoloLens2** e quindi nella finestra Inspector (Controllo) passare a **Audio Source**  >  **3D Sound (Audio Source 3D Sound) Impostazioni** e Configure (Configura) come indicato di seguito:

1. Impostare la **proprietà Rolloff del** volume su Rolloff lineare
2. Trascinare l'endpoint sulla **curva volume** (curva rossa) da "0" sull'asse y fino a "1"
3. Per regolare la forma della curva **volume** in modo che sia piana, trascinare il controllo della forma della curva bianca in modo che sia parallelo all'asse X

![Impostazioni del suono 3D del pulsante](images/spatial-audio/spatial-audio-02-section3-step1-1.PNG)

## <a name="testing-the-spatialize-audio"></a>Test dell'audio spazializza

Per testare l'audio spazializzabile nell'editor unity, è necessario aggiungere un clip audio nel componente **Origine** audio con **l'opzione Ciclo** selezionata nell'oggetto **PressableButtonHoloLens2.**

In modalità di riproduzione spostare **l'oggetto PressableButtonHoloLens2** da sinistra a destra e confrontare con e senza audio spaziale abilitato nella workstation. È anche possibile modificare le impostazioni di Origine audio per i test:

* Spostamento della **proprietà Spatial Blend** tra 0 e 1 (suono 2D non spazializzato e 3D spazializzato)
* Controllo e deselezione della **proprietà Spatialize**

Provare l'app in HoloLens 2. Nell'app è possibile fare clic sul pulsante e ascoltare i suoni di interazione dei pulsanti spazializzati.

> [!TIP]
> Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come spazializzare i suoni di interazione del pulsante e usare un clip audio per testare l'interazione con il pulsante spazializzato. Nell'esercitazione successiva si apprenderà come spazializzare l'audio da un'origine video.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 3. Spazializzazione dell'audio da un video](unity-spatial-audio-ch3.md)
