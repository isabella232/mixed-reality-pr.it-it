---
title: Menu a mano
description: I menu a mano consentono agli utenti di visualizzare rapidamente l'interfaccia utente collegata a mano per le funzioni usate di frequente.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: mano, menu, pulsante, accesso rapido, layout, visore per realtà mista, visore per realtà mista windows, visore per realtà virtuale, HoloLens, MRTK, realtà mista Toolkit
ms.openlocfilehash: 76338f75250054c531560dc0b6cb18aa7130c09fe30a49b4afc3fd409f88fdc0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201977"
---
# <a name="hand-menu"></a>Menu a mano

![Posizione della mano laterale ulnar](images/UX_Hero_HandMenu.jpg)

Il menu a forma di mano è uno dei modelli di esperienza utente più univoci in HoloLens 2. Consente di visualizzare rapidamente l'interfaccia utente collegata a mano. Poiché è accessibile in qualsiasi momento e può essere visualizzato e nascosto facilmente, è ideale per le azioni rapide.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

Nell'elenco seguente sono disponibili le procedure consigliate per l'uso dei menu a mano. È anche possibile trovare una scena di esempio che illustra il menu della mano in [MRTK.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)

<br>

---

## <a name="best-practices"></a>Procedure consigliate

**Mantenere il numero di pulsanti piccoli** 

A causa della distanza ravvicinata tra un menu bloccato a mano e gli occhi e della tendenza degli utenti a concentrarsi su un'area visiva relativamente piccola in qualsiasi momento (il cono di visione attenzionale è di circa 10 gradi), è consigliabile mantenere il numero di pulsanti piccoli. In base all'esplorazione, una colonna con tre pulsanti funziona correttamente mantenendo tutto il contenuto all'interno del campo di visualizzazione (FOV) anche quando un utente sposta le mani al centro dell'FOV. 

**Usare il menu a mano per un'azione rapida** 

Alzare un braccio e mantenere la posizione può facilmente causare affaticamento del braccetto. Usare un metodo bloccato a mano per il menu che richiede una breve interazione. Se il menu è complesso e richiede tempi di interazione estesi, è consigliabile usare il blocco del mondo o il blocco del corpo. 

**Angolo pulsante/pannello**

I menu devono essere posizionati sulla parte opposta della testa e sulla parte centrale della testa: ciò consente a uno spostamento naturale della mano di interagire con il menu con la mano opposta ed evita qualsiasi posizione della mano scomoda o fastidiosa quando si toccano i pulsanti. 

**Valutare la possibilità di supportare operazioni con una sola mano o senza mani**

Non presupporre che entrambe le mani dell'utente siano sempre disponibili. Si consideri un'ampia gamma di contesti quando una o entrambe le mani non sono disponibili e assicurarsi che i propri account di progettazione siano in base a tali situazioni. Per supportare un menu con una mano sola, è possibile provare a eseguire la transizione del posizionamento del menu da bloccato a mano a quello bloccato a livello del mondo quando la mano viene capovolta (diventa il palmo verso il basso). Per gli scenari hands-free, è consigliabile usare un comando vocale per richiamare il menu a mano.

**Evitare di aggiungere pulsanti vicino al polso (pulsante Home del sistema)**

Se i pulsanti del menu a mano sono posizionati troppo vicino al pulsante Home, è possibile che venga attivato accidentalmente durante l'interazione con il menu a mano.

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>Menu a mano con controlli dell'interfaccia utente di grandi dimensioni e complessi

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
È consigliabile limitare il numero di pulsanti o controlli dell'interfaccia utente nei menu collegati manualmente. Questo perché l'interazione estesa con un numero elevato di elementi dell'interfaccia utente può causare affaticamento del braccio. Se l'esperienza richiede un menu di grandi dimensioni, fornire un modo semplice per consentire all'utente di bloccare il menu. Una tecnica consigliata consiste nel bloccare il mondo e quindi nel menu quando la mano scende o si capovolge dall'utente. Una seconda tecnica consiste nel consentire all'utente di afferrare direttamente il menu con l'altra mano. Quando l'utente rilascia il menu, il menu dovrebbe bloccarsi a livello mondiale. In questo modo, un utente può interagire con vari elementi dell'interfaccia utente comodamente e con sicurezza per un lungo periodo di tempo. 

Quando il menu è bloccato a livello mondiale, assicurarsi di fornire un modo per spostare il menu e chiudere il menu quando non è più necessario. Rendere il menu mobile fornendo punti di manipolazione sui lati o nella parte superiore del menu. Aggiungere un pulsante chiudi per consentire la chiusura del menu. Consentire al menu di ricollegare la mano quando la mano dell'utente si trova di fronte all'utente. È anche consigliabile che gli utenti guardino la mano per evitare false attivazioni (vedere di seguito).

**Menu di grandi dimensioni che mostra un problema di usabilità**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**Menu bloccato a livello mondiale al rilascio manuale**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**Selezione manuale & pull per bloccare il menu**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a>Come impedire l'attivazione falsa

Se si usa solo palm-up come evento per attivare il menu della mano, è possibile che venga visualizzato accidentalmente quando non è necessario (falso positivo), perché gli utenti spostano le mani intenzionalmente (per la comunicazione e la manipolazione degli oggetti) e accidentalmente. Per ridurre le attivazioni false, aggiungere un passaggio aggiuntivo oltre all'evento palm-up per richiamare il menu della mano ,ad esempio le dita completamente aperte o l'utente che guarda intenzionalmente la mano.

**Richiedi Flat Palm**

Richiedendo una mano aperta piatta, è possibile impedire l'attivazione falsa che potrebbe verificarsi quando l'utente modifica oggetti o movimenti durante la comunicazione all'interno di un ambiente. 

**Richiedi sguardo fisso**

Richiedendo all'utente di guardare la mano (con lo sguardo o la testa), impedisce false attivazioni a causa del fatto che l'utente deve indirizzare l'attenzione sulla mano come passaggio di attivazione secondario (con una soglia di distanza regolabile usata per consentire il comfort dell'utente).  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>Procedure consigliate per il posizionamento dei menu a mano

Nell'anatomia umana, il nervino ulnar è un nervino che corre vicino all'osso dell'ulna. L'ulna è un lungo osso trovato nell'avambraccio che si estende dal gomito al dito più piccolo.

Di seguito sono riportati due posizionamenti consigliati in base alle esplorazioni:

:::row:::
    :::column:::
        ![Posizione della mano laterale ulnar all'interno del palmo](images/UlnarSideHandMenu.gif)<br>
        **A. Ulnar all'interno del palmo**<br>
        Questa posizione è affidabile perché le mani non si sovrappongono. Questo è fondamentale per il rilevamento e il rilevamento accurati della mano.
    :::column-end:::
    :::column:::
        ![Posizione della mano laterale ulnar sopra la mano](images/UlnarAboveHandMenu.gif)<br>
        **B. Ulnar sopra la mano**<br>
        Questa posizione è comoda per gli utenti perché non è necessario alzare troppo il braccio per interagire con il menu della mano. È consigliabile posizionare i menu **13 cm** sopra il palmo e allineare i pulsanti all'interno del palmo ulnar. [Altre informazioni sulle dimensioni ottimali dei pulsanti](interactable-object.md)<br>
        <br>
        Per motivi tecnici, è consigliabile usare questa posizione con un'implementazione obbligatoria: lo sviluppatore dovrà bloccare il menu quando la mano opposta dell'utente si avvicina all'interazione con esso. In questo modo si eviteranno instabilità dalle mani sovrapposte e si otterranno anche un targeting più rapido dei pulsanti.<br>
        <br>
        HoloLens 2 fotocamere identificano con precisione le mani quando sono separate l'una dall'altra. Qualsiasi mano sovrapposta può causare l'allontanarsi dei menu della mano dalla posizione di ancoraggio.<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a>Posizioni di menu non consigliate

Sono state eseguite ricerche utente con layout e posizioni di menu diversi, le posizioni di menu seguenti **NON sono** consigliate, trovare i contro di ogni studio di seguito:

:::row:::
    :::column:::
        ![Sopra il braccio](images/AboveArm.gif)<br>
        **Sopra il braccio**<br>
        1 - Difficile mantenere un buon tracciamento delle mani<br>
        2 - Causa affaticamento dell'utente a causa di una posizione innaturale
    :::column-end:::
    :::column:::
        ![Sopra le dita](images/AboveFingers.gif)<br>
        **Sopra le dita**<br>
        1 - Affaticamento della mano a causa di tenere la mano per molto tempo<br>
        2 - Problemi di rilevamento delle mani sull'indice e sulle dita medie
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Sopra il palmo centrale](images/handCenter.gif)<br>
        **Palmo sopra il centro**<br>
        1 - Problemi di rilevamento delle mani a causa di mani sovrapposte<br>
        2 - Affaticamento della mano a causa della stretta di mano per lungo tempo per interagire con i menu
    :::column-end:::
    :::column:::
        ![Punta del dito superiore ](images/TopFingerTip.gif) **Punta del dito superiore**<br>
        1 - Problemi di rilevamento delle mani<br>
        2 - Affaticamento della mano dal tenere la mano sopra la postura normale<br>
        3 - Problemi di pressione accidentale dei pulsanti con le altre dita a causa dello spazio limitato tra le dita
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Back of the Arm](images/BackOfTheArm.gif)<br>
        **Indietro del braccetto**<br>
        1 - Può attivare il pulsante Home per errore<br>
        2 - Non è una posizione naturale o comoda
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>Menu mano in MRTK (Mixed Reality Toolkit) per Unity

**[MRTK fornisce](https://github.com/Microsoft/MixedRealityToolkit-Unity)** script e scene di esempio per il menu a mano. Lo script del risolutore HandConstraintPalmUp consente di collegare qualsiasi oggetto alle mani con varie opzioni configurabili. Gli esempi di menu a forma di mano di MRTK includono opzioni utili, ad esempio il requisito di palmo piatto e sguardo fisso per impedire l'attivazione falsa.

* [Documentazione del menu a mano](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [Scena di esempio del menu a mano](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

È possibile provare esempi di menu a mano in HoloLens 2 con l'app Hub esempi MRTK.

* [Scena del menu a mano nell'hub degli esempi MRTK](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

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