---
title: Menu a mano
description: I menu a mano consentono agli utenti di visualizzare rapidamente l'interfaccia utente collegata a mano per le funzioni usate di frequente.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: hand, menu, button, quick access, layout, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f007ada2d7a594f141d30a3619d4d80ac74621d8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600330"
---
# <a name="hand-menu"></a>Menu a mano

![Posizione sul lato Ulnar](images/UX_Hero_HandMenu.jpg)

Il menu a forma di mano è uno dei modelli di esperienza utente più univoci in HoloLens 2. Consente di visualizzare rapidamente l'interfaccia utente collegata a mano. Poiché è accessibile in qualsiasi momento e può essere visualizzato e nascosto facilmente, è ideale per le azioni rapide.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

Le procedure consigliate per l'uso dei menu a mano sono disponibili nell'elenco seguente. È anche possibile trovare una scena di esempio che illustra il menu a mano in [MRTK.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)

<br>

---

## <a name="best-practices"></a>Procedure consigliate

**Mantenere ridotto il numero di pulsanti** 

A causa della distanza vicina tra un menu bloccato a mano e gli occhi e della tendenza degli utenti a concentrarsi su un'area visiva relativamente piccola in qualsiasi momento (il cono di vista attenzionale è di circa 10 gradi), è consigliabile mantenere ridotto il numero di pulsanti. In base all'esplorazione, una colonna con tre pulsanti funziona bene mantenendo tutto il contenuto all'interno del campo di visualizzazione anche quando un utente sposta le mani al centro della fov. 

**Usare il menu a mano per un'azione rapida** 

Alzare un arm e mantenere la posizione potrebbe facilmente causare l'affaticamento del mano. Usare un metodo bloccato a mano per il menu che richiede una breve interazione. Se il menu è complesso e richiede tempi di interazione estesi, è consigliabile usare il blocco del mondo o il blocco del corpo. 

**Angolo pulsante/pannello**

I menu devono essere posizionati verso la fronte opposta e al centro della testa: ciò consente un movimento naturale della mano per interagire con il menu con la mano opposta ed evitare eventuali posizioni della mano difficili o difficili da toccare quando si toccano i pulsanti. 

**Valutare la possibilità di supportare operazioni a una mano o a mani libere**

Non presupporre che entrambe le mani dell'utente siano sempre disponibili. Prendere in considerazione un'ampia gamma di contesti quando una o entrambe le mani non sono disponibili e assicurarsi che la progettazione account per tali situazioni. Per supportare un menu con una mano, è possibile provare a eseguire la transizione del posizionamento del menu da mano bloccata a bloccata al mondo quando la mano capovolge (si inverte il palmo). Per gli scenari senza mani, è consigliabile usare un comando vocale per richiamare il menu a mano.

**Evitare di aggiungere pulsanti accanto al vicino (pulsante Pagina iniziale del sistema)**

Se i pulsanti del menu a mano sono posizionati troppo vicino al pulsante Pagina iniziale, è possibile che venga attivato accidentalmente durante l'interazione con il menu a mano.

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>Menu a mano con controlli dell'interfaccia utente grandi e complessi

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
È consigliabile limitare il numero di pulsanti o controlli dell'interfaccia utente nei menu collegati manualmente. Questo perché l'interazione estesa con un numero elevato di elementi dell'interfaccia utente può causare problemi di arm. Se l'esperienza richiede un menu di grandi dimensioni, fornire all'utente un modo semplice per bloccare il menu. Una tecnica consigliata consiste nel bloccare il mondo e quindi nel menu quando la mano scende o si allontana dall'utente. Una seconda tecnica consiste nel consentire all'utente di afferrare direttamente il menu con l'altra mano. Quando l'utente rilascia il menu, il menu dovrebbe bloccarsi a livello mondiale. In questo modo, un utente può interagire con vari elementi dell'interfaccia utente in modo semplice e sicuro per un lungo periodo di tempo. 

Quando il menu è bloccato a livello mondiale, assicurarsi di fornire un modo per spostare il menu e chiuderlo quando non è più necessario. Rendere il menu mobile fornendo punti di controllo sui lati o nella parte superiore del menu. Aggiungere un pulsante chiudi per consentire la chiusura del menu. Consentire il ricollegare il menu alla mano quando la mano dell'utente si trova di fronte all'utente. È anche consigliabile che gli utenti fissano la mano per impedire attivazioni false (vedere di seguito).

**Menu di grandi dimensioni che mostra un problema di usabilità**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**Menu a portata di mano bloccato**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**Afferrare manualmente & il pull per bloccare il mondo nel menu**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a>Come impedire l'attivazione falsa

Se si usa solo palm-up come evento per attivare il menu della mano, è possibile che venga visualizzato accidentalmente quando non è necessario (falso positivo), perché le persone spostano le mani intenzionalmente (per la comunicazione e la manipolazione degli oggetti) e accidentalmente. Per ridurre le attivazioni false, aggiungi un passaggio aggiuntivo oltre all'evento palm-up per richiamare il menu della mano (ad esempio le dita completamente aperte o l'utente che guarda intenzionalmente la mano).

**Require Flat Palm**

Richiedendo una mano aperta piana, è possibile impedire l'attivazione falsa che potrebbe verificarsi quando l'utente modifica oggetti o movimenti durante la comunicazione all'interno di un ambiente. 

**Richiedi sguardo fisso**

Richiedendo all'utente di guardare la mano (con sguardo fisso o sguardo con la testa), impedisce attivazioni false perché l'utente deve indirizzare l'attenzione alla mano come passaggio di attivazione secondario (con una soglia di distanza regolabile usata per consentire il comfort dell'utente).  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>Procedure consigliate per il posizionamento dei menu a mano

Nell'anatomia umana, l'ulnar erre è un'esca che si trova vicino all'ulna. L'ulna è un longino che si trova nell'avambraccio che si estende dal gomito al dito più piccolo.

Di seguito sono riportati due posizionamenti consigliati in base alle esplorazioni:

:::row:::
    :::column:::
        ![Posizione della mano laterale Ulnar all'interno del palmo](images/UlnarSideHandMenu.gif)<br>
        **A. Ulnar inside palm**<br>
        Questa posizione è affidabile perché le mani non si sovrappongono. Questo è fondamentale per il rilevamento e il rilevamento delle mani accurati.
    :::column-end:::
    :::column:::
        ![Posizione sul lato Ulnar sopra la mano](images/UlnarAboveHandMenu.gif)<br>
        **B. Ulnar sopra la mano**<br>
        Questa posizione è comoda per gli utenti perché non è necessario alzare troppo le mani per interagire con il menu a mano. È consigliabile posizionare i menu **13 cm** sopra il palmo e allineare i pulsanti all'interno del palmo ulnar. [Altre informazioni sulle dimensioni ottimali dei pulsanti](interactable-object.md)<br>
        <br>
        Per motivi tecnici, è consigliabile usare questa posizione con un'implementazione obbligatoria: lo sviluppatore dovrà bloccare il menu quando la mano opposta dell'utente si avvicina all'interazione con esso. In questo modo si evita l'instabilità delle mani sovrapposte e si consente anche una scelta più rapida dei pulsanti.<br>
        <br>
        HoloLens 2 fotocamere identificano le mani in modo accurato quando sono separate l'una dall'altra. Eventuali mani sovrapposte possono far sì che i menu delle mani si spostino dalla posizione di ancoraggio.<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a>Posizioni dei menu non consigliate

Sono state eseguite ricerche degli utenti con layout e posizioni di menu diversi. Le posizioni di menu seguenti **NON** sono consigliate. Trovare i contro di ogni studio di seguito:

:::row:::
    :::column:::
        ![Sopra arm](images/AboveArm.gif)<br>
        **Sopra il arm**<br>
        1 - Difficile mantenere un buon tracciamento delle mani<br>
        2 - Causa l'affaticamento dell'utente a causa di una posizione non naturale
    :::column-end:::
    :::column:::
        ![Sopra le dita](images/AboveFingers.gif)<br>
        **Sopra le dita**<br>
        1 - Affaticamento della mano a causa della lunga attesa<br>
        2 - Problemi di tracciamento della mano sull'indice e sulle dita medie
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Sopra il palmo centrale](images/handCenter.gif)<br>
        **Palmo sopra il centro**<br>
        1 - Problemi di tracciamento della mano a causa della sovrapposizione delle mani<br>
        2 - Affaticamento della mano a causa della tenere le mani per molto tempo per interagire con i menu
    :::column-end:::
    :::column:::
        ![Punta del dito ](images/TopFingerTip.gif) **superiore Punta del dito superiore**<br>
        1 - Problemi di tracciamento della mano<br>
        2 - Affaticamento della mano dalla mano al di sopra della normale postura<br>
        3 - Problemi di pressione accidentale di pulsanti con altre dita a causa dello spazio limitato tra le dita
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Parte posteriore dell'arm](images/BackOfTheArm.gif)<br>
        **Parte posteriore dell'arm**<br>
        1 - Può attivare il pulsante Pagina iniziale per errore<br>
        2 - Posizione non naturale o comoda
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>Menu mano in MRTK (Mixed Reality Toolkit) per Unity

**[MRTK fornisce](https://github.com/Microsoft/MixedRealityToolkit-Unity)** script e scene di esempio per il menu a mano. Lo script del risolutore HandConstraintPalmUp consente di collegare qualsiasi oggetto alle mani con varie opzioni configurabili. Gli esempi di menu con la mano di MRTK includono opzioni utili, ad esempio il requisito del palmo piana e dello sguardo fisso per impedire l'attivazione falsa.

* [Documentazione del menu a mano](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [Scena di esempio del menu a mano](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

È possibile provare gli esempi di menu a mano in HoloLens 2'app Hub degli esempi di MRTK.

* [Scena di menu manuale nell'hub degli esempi di MRTK](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

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