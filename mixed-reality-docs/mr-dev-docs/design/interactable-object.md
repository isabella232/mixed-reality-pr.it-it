---
title: Oggetto che supporta interazioni
description: Informazioni su come attivare eventi, fornire segnali visivi e interagire con gli oggetti nelle applicazioni di realtà mista.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/06/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, segnali, interfaccia utente, esperienza utente, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens, MRTK, realtà mista Toolkit, audio
ms.openlocfilehash: f1fe68c7f35fecb9fbee888893fb15a83a8595ec
ms.sourcegitcommit: 4f1697b11e5638db9bbd0bd7a671d846d54c6389
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "122683000"
---
# <a name="interactable-object"></a>Oggetto che supporta interazioni

![Oggetti interactible](images/UX_Hero_Interactable.jpg)

Un pulsante è da tempo una metafora usata per attivare un evento nel mondo astratto 2D. Nel mondo della realtà mista tridimensionale non è più necessario limitarsi a questo mondo di astrazione. Qualsiasi elemento può essere **un oggetto intervienibile** che attiva un evento. Un oggetto che può interagire può essere qualsiasi cosa, da una tazzina da caffè su un tavolo a un balloon in midair. I pulsanti tradizionali vengono ancora utilizzati in determinate situazioni, ad esempio nell'interfaccia utente della finestra di dialogo. La rappresentazione visiva del pulsante dipende dal contesto.

<br>

---

## <a name="important-properties-of-the-interactable-object"></a>Proprietà importanti dell'oggetto con interazione

### <a name="visual-cues"></a>Visivi

I segnali visivi sono segnali sensoriali provenienti dalla luce, ricevuti dall'occhio ed elaborati dal sistema visivo durante la percezione visiva. Poiché il sistema visivo è dominante in molte specie, in particolare gli esseri umani, i segnali visivi sono una grande fonte di informazioni sul modo in cui viene percepito il mondo.

Poiché gli oggetti olografici vengono misti con l'ambiente reale nella realtà mista, potrebbe essere difficile comprendere con quali oggetti è possibile interagire. Per tutti gli oggetti che possono interagire nell'esperienza, è importante fornire segnali visivi differenziati per ogni stato di input. Ciò consente all'utente di comprendere quale parte dell'esperienza può interagire e rende l'utente sicuro usando un metodo di interazione coerente.

<br>

---

### <a name="far-interactions"></a>Interazioni da lontano

Per tutti gli oggetti che l'utente può interagire con lo sguardo fisso, il raggio della mano e il raggio del controller del movimento, è consigliabile avere un segnale visivo diverso per questi tre stati di input:

:::row:::
    :::column:::
       ![Oggetto con interazione con stato predefinito](images/interactibleobject-states-default.jpg)<br>
       **Stato predefinito (osservazione)**<br>
        Stato di inattività predefinito dell'oggetto.
    Il cursore non si trova sull'oggetto. La mano non viene rilevata.
    :::column-end:::
    :::column:::
       ![Oggetto con interazione con stato di destinazione e passaggio del mouse](images/interactibleobject-states-targeted.jpg)<br>
        **Stato di destinazione (passaggio del mouse)**<br>
        Quando l'oggetto è indirizzato con il cursore sguardo fisso, la prossimità del dito o il puntatore del controller del movimento.
    Il cursore si trova sull'oggetto . La mano viene rilevata, pronta.
    :::column-end:::
    :::column:::
       ![Oggetto con interazione con stato premuto](images/interactibleobject-states-pressed.jpg)<br>
       **Stato premuto**<br>
        Quando l'oggetto viene premuto con un movimento di tocco, la pressione del dito o il pulsante di selezione del controller del movimento.
    Il cursore si trova sull'oggetto . Viene rilevata la mano, viene toccata l'aria.
    :::column-end:::
:::row-end:::

<br>

---

È possibile usare tecniche come l'evidenziazione o il ridimensionamento per fornire segnali visivi per lo stato di input dell'utente. Nella realtà mista è possibile trovare esempi di visualizzazione di stati di input diversi nel menu Start e con i pulsanti della barra dell'app. 

Ecco l'aspetto di questi stati su un **pulsante olografico:**

:::row:::
    :::column:::
       ![Pulsante olografico nello stato predefinito](images/MRTK_InteractableState-default.jpg)<br>
       **Stato predefinito (osservazione)**<br>
    :::column-end:::
    :::column:::
       ![Pulsante olografico nello stato di destinazione e passaggio del mouse](images/MRTK_InteractableState-targeted.jpg)<br>
        **Stato di destinazione (passaggio del mouse)**<br>
    :::column-end:::
    :::column:::
       ![Pulsante olografico nello stato premuto](images/MRTK_InteractableState-pressed.jpg)<br>
       **Stato premuto**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>Interazioni near (diretta) 

HoloLens 2 supporta l'input di tracciamento delle mani articolato, che consente di interagire con gli oggetti. Senza feedback attico e percezione della profondità perfetta, può essere difficile stabilire quanto la mano è distante da un oggetto o se lo si sta toccando. È importante fornire segnali visivi sufficienti per comunicare lo stato dell'oggetto, in particolare lo stato delle mani in base a tale oggetto.

Usare il feedback visivo per comunicare gli stati seguenti:
* **Predefinito (osservazione):** stato di inattività predefinito dell'oggetto.
* **Passaggio** del mouse: quando una mano si trova vicino a un ologramma, modificare gli oggetti visivi per comunicare che la mano è la destinazione dell'ologramma. 
* **Distanza e punto di interazione:** quando la mano si avvicina a un ologramma, progettare il feedback per comunicare il punto di interazione proiettato e la distanza dall'oggetto del dito
* **Inizio contatto:** modifica gli oggetti visivi (luce, colore) per comunicare che si è verificato un tocco
* **Afferrato:** modifica gli oggetti visivi (luce, colore) quando l'oggetto viene afferrato
* **Fine contatto:** modifica gli oggetti visivi (luce, colore) al termine del tocco

<br>

---

:::row:::
    :::column:::
        ![Passaggio del mouse (lontano)](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **Passaggio del mouse (lontano)**<br>
        Evidenziazione basata sulla prossimità della mano.
    :::column-end:::
    :::column:::
        ![Passaggio del mouse (vicino)](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **Passaggio del mouse (vicino)**<br>
        Le dimensioni dell'evidenziazione cambiano in base alla distanza dalla mano.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Tocco/pressione](images/640px-interactibleobject-states-near-press.jpg)<br>
        **Tocco/pressione**<br>
        Feedback visivo e audio.
    :::column-end:::
    :::column:::
        ![Afferrare](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **Afferrare**<br>
        Feedback visivo e audio.
    :::column-end:::
:::row-end:::

<br>

<br>

---

Un [pulsante in HoloLens 2](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) è un esempio di visualizzazione dei diversi stati di interazione di input:

:::row:::
    :::column:::
        ![Valore predefinito](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **Default**<br>
    :::column-end:::
    :::column:::
        ![Passaggio del mouse](images/640px-interactibleobject-pressablebutton-hover.jpg)<br>
        **Passaggio del mouse**<br>
        Rivela un effetto di illuminazione basato sulla prossimità.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Tocco](images/640px-interactibleobject-pressablebutton-touch.jpg)<br>
        **Tocco**<br>
        Mostra effetto ondulato.
    :::column-end:::
    :::column:::
        ![Premere](images/640px-interactibleobject-pressablebutton-press.jpg)<br>
        **Premere**<br>
        Spostare il pannello anteriore.
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>Segnale visivo "anello" su HoloLens 2<br>
        In HoloLens 2 è presente un segnale visivo aggiuntivo che può aiutare la percezione della profondità da parte dell'utente. Un anello vicino alla punta del dito viene visualizzato e ridimensionato man mano che la punta del dito si avvicina all'oggetto. L'anello converge infine in un punto quando viene raggiunto lo stato premuto. Questo oggetto visivo consente all'utente di comprendere quanto sono distasi dall'oggetto.<br>
        <br>
        *Ciclo video: esempio di feedback visivo basato sulla prossimità di un rettangolo di selezione*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Feedback visivo sulla prossimità manuale](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>Segnali audio

Per le interazioni con la mano diretta, un feedback audio appropriato può migliorare notevolmente l'esperienza utente. Usare il feedback audio per comunicare i segnali seguenti:
* **Inizio contatto:** riproduci l'audio all'inizio del tocco
* **Fine contatto:** riprodurre l'audio all'estremità del tocco
* **Inizia a afferrare:** riproduci l'audio all'avvio della cattura
* **Grab ends (Fine afferra):** riproduci l'audio al termine dell'afferrare

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>Esecuzione di comandi vocali<br>
        Per qualsiasi oggetto con interazione, è importante supportare opzioni di interazione alternative. Per impostazione predefinita, è consigliabile [che l'esecuzione di comandi vocali](../out-of-scope/voice-design.md) sia supportata per tutti gli oggetti che possono interagire. Per migliorare l'individuabilità, è anche possibile fornire una descrizione comando durante lo stato del passaggio del mouse.<br>
        <br>
        *Immagine: Descrizione comando vocale*
    :::column-end:::
        :::column:::
       ![comandi vocali](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a>Consigli sul ridimensionamento

Per garantire che tutti gli oggetti interagiscibili possano essere facilmente toccati, è consigliabile assicurarsi che l'oggetto interagiscibile soddisfi le dimensioni minime in base alla distanza che viene posta dall'utente. L'angolo visivo viene spesso misurato in gradi di arco visivo. L'angolo visivo si basa sulla distanza tra gli occhi dell'utente e l'oggetto e rimane costante, mentre le dimensioni fisiche della destinazione possono cambiare quando cambia la distanza dall'utente. Per determinare le dimensioni fisiche necessarie di un oggetto in base alla distanza dall'utente, provare a usare un calcolatore dell'angolo visivo come [questo](https://elvers.us/perception/visualAngle/).

Di seguito sono riportate le raccomandazioni per le dimensioni minime del contenuto interagiscibile.

### <a name="target-size-for-direct-hand-interaction"></a>Dimensioni di destinazione per l'interazione diretta con la mano

| Distanza | Angolo di visualizzazione | Dimensione |
|---------|---------|---------|
| 45 cm  | non inferiore a 2° | 1,6 x 1,6 cm |

![Dimensioni di destinazione per l'interazione diretta con la mano](images/TargetSizingNear.jpg)<br>
*Dimensioni di destinazione per l'interazione diretta con la mano*


<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Dimensioni di destinazione per l'interazione con il raggio della mano o lo sguardo
| Distanza | Angolo di visualizzazione | Dimensione |
|---------|---------|---------|
| 2 m  | non inferiore a 1° | 3,5 x 3,5 cm |

![Dimensioni di destinazione per l'interazione con il raggio della mano o lo sguardo](images/TargetSizingFar.jpg)<br>
*Dimensioni di destinazione per l'interazione con il raggio della mano o lo sguardo*

<br>

---

## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a>Oggetto interagiscibile in MRTK (Mixed Reality Toolkit) per Unity

In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** è possibile usare lo script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) per fare in modo che gli oggetti rispondano a vari tipi di stati di interazione di input. Supporta vari tipi di temi che consentono di definire gli stati di visualizzazione controllando le proprietà dell'oggetto, ad esempio colore, dimensioni, materiale e shader.

* [Interagibile](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* [Button](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)
* [Scena degli esempi di interazione manuale](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

Lo shader Standard di MixedRealityToolkit  offre varie opzioni, ad esempio la luce di prossimità, che consente di creare segnali visivi e audio.

* [MRTK Standard Shader](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a>Vedi anche

* [Cursori](cursors.md)
* [Raggio della mano](point-and-commit.md)
* [Button](button.md)
* [Oggetto che supporta interazioni](interactable-object.md)
* [Rettangolo di selezione e barra dell'app](app-bar-and-bounding-box.md)
* [Manipolazione](direct-manipulation.md)
* [Menu a mano](hand-menu.md)
* [Menu adiacente](near-menu.md)
* [Raccolta di oggetti](object-collection.md)
* [Comando vocale](voice-input.md)
* [Tastiera](keyboard.md)
* [Descrizione comando](tooltip.md)
* [Slate](slate.md)
* [Dispositivo di scorrimento](slider.md)
* [Shader](shader.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)
* [Visualizzazione dello stato](progress.md)
* [Magnetismo di superficie](surface-magnetism.md)