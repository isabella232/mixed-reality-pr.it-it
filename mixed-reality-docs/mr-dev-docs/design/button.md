---
title: Button
description: Informazioni su come attivare un'azione immediata con i pulsanti, uno dei componenti di base della realtà mista.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, interfaccia utente, esperienza utente, visore per realtà mista, visore windows di realtà mista, visore per realtà virtuale, HoloLens, MRTK, realtà mista Toolkit, pulsante
ms.openlocfilehash: 4b3a9bda852c7a83ee603c3f2340d44f4be89f4d
ms.sourcegitcommit: 4f1697b11e5638db9bbd0bd7a671d846d54c6389
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "122682974"
---
# <a name="button"></a>Button

![Button](images/UX_Hero_Button.jpg)

Un pulsante è uno degli elementi più fondamentali e fondamentali dell'interfaccia utente nella realtà mista. Consente agli utenti di attivare azioni immediate. Poiché nella realtà mista non sono presenti feedback fisici, è fondamentale fornire un feedback visivo e audio sufficiente per aumentare la confidenza di interazione dell'utente. 

Nella progettazione HoloLens 2 pulsante, basata su molte iterazioni di progettazione, prototipi e studi di ricerca degli utenti, sono stati integrati più suggerimenti visivi e segnali audio che aiutano la percezione della profondità e l'interazione dell'utente nello spazio vuoto. 

## <a name="visual-affordances"></a>Convenienze visive

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWJHgW]


:::row:::
    :::column:::
       ![Pulsante con l'effetto di luce di prossimità visualizzato](images/UX_Button_Affordance_ProximityLight.jpg)<br>
       **Luce di prossimità**<br>
    :::column-end:::
    :::column:::
       ![Pulsante selezionato con l'effetto evidenziazione dello stato attivo visualizzato](images/UX_Button_Affordance_FocusHighlight.jpg)<br>
        **Evidenziazione dello stato attivo**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![Pulsante premuto con l'effetto della compressione della cella visualizzata](images/UX_Button_Affordance_Compression.jpg)<br>
       **Compressione di una cella**<br>
    :::column-end:::
    :::column:::
       ![Pulsante premuto con l'effetto trigger pulse visualizzato](images/UX_Button_Affordance_Pulse.jpg)<br>
        **Pulse on trigger**<br>
    :::column-end:::
:::row-end:::

<br>

## <a name="audio-cues"></a>Segnali audio

Un feedback audio corretto può migliorare notevolmente l'esperienza utente. HoloLens 2 del pulsante fornisce feedback audio per comunicare i segnali seguenti:
* **Inizia contatto:** riprodurre l'audio all'inizio del tocco (quasi interazione)
* **Estremità del contatto:** riprodurre il suono all'estremità del tocco (vicino all'interazione)
* **Inizia a avvicinare** le dita: riproduci il suono al momento della selezione delle dita (interazione da lontano con lo sguardo fisso o i raggi)
* **Estremità delle dita:** riprodurre il suono al rilascio delle dita (interazione da lontano con lo sguardo fisso o i raggi)

<br>

---

:::row:::
    :::column:::
        ## <a name="voice-commandingbr"></a>Esecuzione di comandi vocali<br>
        Per tutti i pulsanti nella realtà mista, è importante supportare opzioni di interazione alternative. Per impostazione predefinita, è consigliabile che i comandi vocali siano supportati per tutti i pulsanti. Nella progettazione HoloLens 2 del pulsante, viene visualizzata una descrizione comando durante lo stato del passaggio del mouse per migliorare l'individuabilità.
    :::column-end:::
        :::column:::
       ![Input vocale](images/UX_Hero_VoiceCommand.jpg)<br>
        *Immagine: Descrizione comando vocale*
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

### <a name="target-size-for-buttons"></a>Dimensioni di destinazione per i pulsanti

Quando si creano pulsanti per l'interazione diretta, è consigliabile avere dimensioni minime maggiori di 3,2 x 3,2 cm per assicurarsi che sia disponibile spazio sufficiente per contenere un'icona e potenzialmente del testo.

| Distanza | Dimensione minima |
|---------|---------|
| 45 cm  | 3,2 x 3,2 cm |

![Dimensioni di destinazione per i pulsanti](images/TargetSizingButtons.png)<br>
*Dimensioni di destinazione per i pulsanti*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Dimensioni di destinazione per l'interazione con il raggio della mano o lo sguardo
| Distanza | Angolo di visualizzazione | Dimensione |
|---------|---------|---------|
| 2 m  | non inferiore a 1° | 3,5 x 3,5 cm |

![Dimensioni di destinazione per l'interazione con il raggio della mano o lo sguardo](images/TargetSizingFar.jpg)<br>
*Dimensioni di destinazione per l'interazione con il raggio della mano o lo sguardo*

<br>

---

## <a name="design-guidelines"></a>Linee guida di progettazione

### <a name="avoid-transparent-backplate"></a>Evitare backplate trasparente
Quando si progetta l'interfaccia utente dei menu con pulsanti, è consigliabile usare backplate opaco. Le backplate trasparenti non sono consigliate per i motivi seguenti:
* Difficile interagire con perché è difficile comprendere la profondità del pulsante da premere per attivare l'evento
* Problema di leggibilità nell'ambiente fisico complesso
* Ologrammi visualizzati attraverso la lastra trasparente possono mostrare problemi di effetto di nuoto se usati con la tecnologia di stabilizzazione Depth LSR.

Per [altri dettagli sulle scelte](designing-content-for-holographic-display.md) di colore e sulle linee guida per la visualizzazione olografica, vedere Progettazione di contenuto per la visualizzazione olografica.

![Esempi di interfaccia utente ](images/color_transparent_examples.jpg)
 *trasparente Esempi di backplate dell'interfaccia utente trasparente*

<br>

### <a name="use-shared-backplate"></a>Usare backplate condiviso
Per più pulsanti, è consigliabile usare backplate condiviso anziché il backplate del singolo pulsante.

* Ridurre il disturbo visivo e la complessità
* Cancellare il raggruppamento  

![Esempi di backplate condivisi ](images/Button_Design_SharedBackplate.png
)
 *Esempi di backplate dell'interfaccia utente condivisa*

<br>

---

## <a name="button-in-mrtk-mixed-reality-toolkit"></a>Pulsante in MRTK (mixed reality Toolkit)
**[MRTK per Unity](/windows/mixed-reality/mrtk-unity/)** e **[MRTK per Unreal](/windows/mixed-reality/develop/unreal/unreal-mrtk-introduction)** forniscono vari tipi di prefab dei pulsanti, inclusi i pulsanti HoloLens 2 stile. Il HoloLens 2 pulsante contiene tutti i commenti e i dettagli dell'interazione visivi introdotti in questa pagina. Usandolo, è possibile sfruttare il risultato di molte iterazioni progettuali e ricerche degli utenti eseguite dai progettisti, dagli sviluppatori e dai ricercatori.

Per altre istruzioni ed esempi personalizzati, vedere [MRTK - Pulsante.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)

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