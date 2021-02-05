---
title: Esercitazioni audio spaziali-2. Spazializzazione dei suoni di interazione del pulsante
description: Aggiungere un pulsante al progetto e spatialize i suoni di interazione dei pulsanti.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale, MRTK, Toolkit per realtà mista, UWP, Windows 10, HRTF, funzione di trasferimento correlato alla testa, riverbero, Microsoft Spatializer, prefabbricati, curva del volume
ms.openlocfilehash: 12d159cb162cbf136483f7be94b0d297319a0737
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590763"
---
# <a name="2-spatializing-button-interaction-sounds"></a>2. Spazializzazione dei suoni di interazione del pulsante

## <a name="overview"></a>Panoramica

In questa esercitazione si apprenderà come spatialize i suoni di interazione dei pulsanti e come usare un clip audio per testare l'interazione con i pulsanti spaziali.  

## <a name="objectives"></a>Obiettivi

* Aggiungi e Spatialize i suoni dei clic del pulsante

## <a name="add-a-button"></a>Aggiungere un pulsante

Per aggiungere il prefabbricato dei pulsanti, nella finestra del **progetto** selezionare **pacchetti** e digitare "PressableButtonHoloLens2" nella barra di ricerca.

![Prefabbricato Button negli asset](images/spatial-audio/spatial-audio-02-section1-step1-1.png)

Il prefabbricato del pulsante è la voce rappresentata da un'icona blu. Fare clic e trascinare il prefabbricato **PressableButtonHoloLens2** nella gerarchia. Con l'oggetto **PressableButtonHoloLens2** ancora selezionato, nella finestra di controllo configurare il componente **Transform** come indicato di seguito:

* **Posizione**: X = 0, Y =-0,4, Z = 2
* **Rotation** (Rotazione): X = 0, Y = 0, Z = 0
* **Scale** (Scala): X = 1, Y = 1, Z = 1

![Trasformazione pulsante](images/spatial-audio/spatial-audio-02-section1-step1-2.png)

Per concentrarsi sugli oggetti nella scena, è possibile fare doppio clic sull'oggetto **PressableButtonHoloLens2** e quindi eseguire di nuovo lo zoom:

## <a name="spatialize-button-feedback"></a>Commenti e suggerimenti sul pulsante Spatialize

In questo passaggio si spatialize il feedback audio per il pulsante. Per suggerimenti sulla progettazione correlati, vedere [progettazione di suoni spaziali](../../../design/spatial-sound-design.md).

Nella finestra **mixer audio** è possibile definire le destinazioni denominate **gruppi di mixer** per la riproduzione audio dai componenti di **origine audio** .

Per aprire la finestra **mixer audio** , nel menu Unity scegliere **finestra**  >  **audio** audio  >  **mixer**: ![ Apri finestra mixer audio](images/spatial-audio/spatial-audio-02-section2-step1-1.png)

 Per creare un **mixer** , fare clic su "+" accanto a **mixer** e immettere un nome adatto al mixer, ad esempio il _mixer audio spaziale_. Il nuovo mixer includerà un **gruppo** predefinito denominato **Master**.

![Pannello mixer con primo mixer](images/spatial-audio/spatial-audio-02-section2-step1-2.png)

> [!NOTE]
> Fino a quando non viene abilitato il riverbero nel [quinto capitolo: uso di Reverb per aggiungere la distanza all'audio spaziale](unity-spatial-audio-ch5.md), il contatore del volume del mixer non Mostra l'attività per i suoni riprodotti tramite Microsoft Spatializer

Nella finestra gerarchia selezionare il **PressableButtonHoloLens2** quindi nella finestra di controllo trovare il componente di **origine audio** e configurare il componente di origine audio come indicato di seguito:

1. Per la proprietà **output** , fare clic sul selettore e scegliere il **mixer** creato.
2. Selezionare la casella di controllo **Spatialize** .
3. Spostare il dispositivo di scorrimento **Blend spaziale** su 3D (1).

![Origine audio pulsante](images/spatial-audio/spatial-audio-02-section2-step1-3.png)

> [!NOTE]
> Se si sposta **Blend spaziale** in 1 (3D) senza selezionare la casella di controllo **Spatialize** , Unity utilizzerà il relativo Spatializer di panoramica anziché **Microsoft Spatializer** con HRTFs.

## <a name="adjust-the-volume-curve"></a>Modificare la curva del volume

Per impostazione predefinita, Unity attenua i suoni spaziali Man mano che si ottengono più lontano dal listener. Quando questa attenuazione viene applicata ai suoni di feedback interazione, l'interfaccia può diventare più difficile da usare.

Per disabilitare questa attenuazione, è necessario modificare la curva del **volume** nel componente di **origine audio** .

Nella finestra gerarchia selezionare il **PressableButtonHoloLens2** quindi nella finestra di controllo passare a impostazioni audio **3D origine audio**  >   e configurare come segue:

1. Impostare la proprietà **volume attenuazione** su attenuazione lineare
2. Trascinare l'endpoint sulla curva del **volume** (la curva rossa) da' 0' sull'asse y fino a' 1'
3. Per regolare la forma della curva del **volume** in modo che sia piatta, trascinare il controllo forma curva bianca in modo che sia parallelo all'asse X

![Impostazioni suono 3D pulsante](images/spatial-audio/spatial-audio-02-section3-step1-1.png)

## <a name="testing-the-spatialize-audio"></a>Test dell'audio spatialize

Per testare l'audio spatialize nell'editor di Unity, è necessario aggiungere una clip audio nel componente **origine audio** con l'opzione **ciclo** archiviato nell'oggetto **PressableButtonHoloLens2** .

In modalità di riproduzione spostare l'oggetto **PressableButtonHoloLens2** da sinistra a destra e confrontare con e senza audio spaziale abilitato sulla workstation. È anche possibile modificare le impostazioni di origine audio per i test:

* Trasferimento della proprietà di **Blend spaziale** tra 0-1 (audio 2D non spaziale e 3D con spaziali)
* Verifica e deselezione della proprietà **Spatialize**

Provare l'app in HoloLens 2. Nell'app è possibile fare clic sul pulsante e sentire i suoni di interazione dei pulsanti spaziali.

> [!TIP]
> Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Lezione completata

In questa esercitazione è stato illustrato come spatialize i suoni di interazione dei pulsanti e come usare un clip audio per testare l'interazione con i pulsanti spaziali. Nell'esercitazione successiva si apprenderà come spatialize audio da un'origine video.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 3. Spatializing audio da un video](unity-spatial-audio-ch3.md)
