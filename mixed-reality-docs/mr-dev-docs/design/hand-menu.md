---
title: Menu a mano
description: I menu a mano consentono agli utenti di visualizzare rapidamente l'interfaccia utente collegata manualmente per le funzioni usate di frequente.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: mano, menu, pulsante, accesso rapido, layout, auricolare realtà mista, auricolare di realtà misto di Windows, auricolare realtà virtuale, HoloLens, MRTK, Toolkit realtà mista
ms.openlocfilehash: e222d792d883ccacc71b177fbde21979c8dfcc77
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299916"
---
# <a name="hand-menu"></a>Menu a mano

![Posizione della mano del lato ulnare](images/UX_Hero_HandMenu.jpg)

Il menu a mano è uno dei modelli UX più esclusivi in HoloLens 2. Consente di visualizzare rapidamente l'interfaccia utente collegata manualmente. Poiché è accessibile in qualsiasi momento e può essere visualizzato e nascosto facilmente, è ideale per le azioni rapide.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

Sono disponibili le procedure consigliate per l'uso dei menu a mano nell'elenco seguente. È anche possibile trovare una scena di esempio che illustra il menu a mano in [MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu).

<br>

---

## <a name="best-practices"></a>Procedure consigliate

**Mantieni il numero di pulsanti piccoli** 

A causa della distanza di chiusura tra un menu con blocco manuale e gli occhi e la tendenza per gli utenti a concentrarsi su un'area visiva relativamente piccola in qualsiasi momento (il cono di attenzione della visione è approssimativamente di 10 gradi), è consigliabile mantenere il numero di pulsanti piccoli. In base all'esplorazione, una colonna con tre pulsanti funziona bene mantenendo tutto il contenuto all'interno del campo di visualizzazione (FOV) anche quando un utente sposta le mani al centro di FOV. 

**Usare il menu a mano per l'azione rapida** 

La generazione di un ARM e la gestione della posizione possono causare un facile affaticamento del braccio. Usare un metodo con blocco manuale per il menu che richiede una breve interazione. Se il menu è complesso e richiede tempi di interazione estesi, prendere in considerazione l'uso di un blocco globale o del corpo. 

**Angolo pulsante/pannello**

I menu devono essere posizionati sulla spalla opposta e al centro della testa: ciò consente a una mano naturale di interagire con il menu con la mano opposta, evitando eventuali posizioni scomode o scomode quando si toccano i pulsanti. 

**Provare a supportare un'operazione a mano o senza mani**

Non presupporre che entrambe le mani dell'utente siano sempre disponibili. Si consideri una vasta gamma di contesti quando una o entrambe le mani non sono disponibili e si verificano gli account di progettazione per tali situazioni. Per supportare un menu a mano singola, è possibile provare a eseguire la transizione della posizione del menu da Hand-locked a blocco globale quando viene eseguito il capovolgimento della mano (passa a una Palma). Per gli scenari senza praticità, provare a usare un comando vocale per richiamare il menu a forma di mano.

**Evitare di aggiungere pulsanti vicino al polso (pulsante Home System)**

Se i pulsanti del menu a mano sono posizionati troppo vicino al pulsante Home, è possibile che venga accidentalmente attivato durante l'interazione con il menu a mano.

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>Menu a mano con controlli dell'interfaccia utente complessi e di grandi dimensioni

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
È consigliabile limitare il numero di pulsanti o controlli dell'interfaccia utente nei menu collegati manualmente. Questo perché l'interazione estesa con un numero elevato di elementi dell'interfaccia utente può causare affaticamento ARM. Se l'esperienza richiede un menu di grandi dimensioni, è possibile consentire all'utente di bloccare il menu in modo semplice. Una tecnica consigliata è quella di bloccare in tutto il mondo quando la mano scende o si capovolge dall'utente. Una seconda tecnica consiste nel consentire all'utente di acquisire direttamente il menu con l'altra parte. Quando l'utente rilascia il menu, il menu deve bloccare il mondo. In questo modo, un utente può interagire con diversi elementi dell'interfaccia utente in modo confortevole e sicuro per un lungo periodo di tempo. 

Quando il menu è bloccato a livello globale, assicurarsi di fornire un modo per spostare il menu e chiudere il menu quando non è più necessario. Rendere il menu mobile fornendo handle sui lati o nella parte superiore del menu. Aggiungere un pulsante Chiudi per consentire la chiusura del menu. Consente di ristabilire la connessione del menu quando l'utente si trova in un altro momento. Si consiglia inoltre di richiedere che gli utenti si trovino a loro disposizione per evitare le attivazioni false (vedere di seguito).

**Menu di grandi dimensioni che mostra un problema di usabilità**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**Menu con blocco globale sulla selezione della mano**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**Manuale di & pull per il menu di scelta rapida**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a>Come impedire l'attivazione falsa

Se si usa solo il Palm-up come un evento per attivare il menu a mano, è possibile che venga accidentalmente visualizzato quando non è necessario (falso positivo), perché le persone spostano le mani intenzionalmente (per la manipolazione delle comunicazioni e degli oggetti) e non intenzionalmente. Per ridurre le attivazioni false, aggiungere un passaggio aggiuntivo oltre all'evento di backup per richiamare il menu a forma di mano, ad esempio le dita completamente aperte, o l'utente che sta intenzionalmente guardando la mano.

**Richiedi Palma piatta**

Richiedendo una mano piatta aperta, è possibile impedire l'attivazione falsa che può verificarsi quando l'utente manipola oggetti o movimenti durante la comunicazione all'interno di un ambiente. 

**Richiedi lo sguardo**

Richiedendo all'utente di guardare la mano (con lo sguardo o con lo sguardo), impedisce le attivazioni false a causa dell'impossibilità da parte dell'utente di indirizzare l'attenzione alla mano come passaggio di attivazione secondaria (con una soglia di distanza ottimizzabile usata per consentire la comodità dell'utente).  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>Procedure consigliate per la selezione dei menu a mano

Nell'anatomia umana, il nervo ulnare è un nervo che viene eseguito in prossimità dell'osso ulna. L'ulna è un osso lungo trovato sull'avambraccio che si estende dal gomito al dito più piccolo.

Di seguito sono riportate due località consigliate in base alle nostre esplorazioni:

:::row:::
    :::column:::
        ![Posizione della mano del lato ulnare all'interno di Palm](images/UlnarSideHandMenu.gif)<br>
        **A. ulnare all'interno di Palm**<br>
        Questa posizione è affidabile perché le mani non si sovrappongono. Si tratta di un fattore fondamentale per il rilevamento e il rilevamento delle carte accurate.
    :::column-end:::
    :::column:::
        ![Posizione sulla mano del lato ulnare](images/UlnarAboveHandMenu.gif)<br>
        **B. oltre la mano del ulnare**<br>
        Questa posizione è comoda per gli utenti perché non è necessario aumentare il proprio ARM per interagire con il menu a mano. È consigliabile posizionare i menu **13 cm** sopra la Palma e allineare i pulsanti all'interno della palma ulnar. [Altre informazioni sulle dimensioni dei pulsanti ottimali](interactable-object.md)<br>
        <br>
        Per motivi tecnici, è consigliabile usare questa località con una sola implementazione necessaria: lo sviluppatore dovrà bloccare il menu una volta che l'utente si avvicina a una mano all'altra. In questo modo si eviterà che nervosismo si sovrappongano e anche un targeting più rapido dei pulsanti.<br>
        <br>
        Le fotocamere HoloLens 2 identificano le mani accuratamente quando sono separate tra loro. Qualsiasi mano sovrapposta può causare la disattivazione dei menu a mano dalla posizione di ancoraggio.<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a>Posizioni dei menu non consigliate

La ricerca degli utenti è stata eseguita con layout e percorsi di menu diversi. i percorsi dei menu seguenti **non sono consigliati**. trovare i svantaggi di ogni studio di seguito:

:::row:::
    :::column:::
        ![Sopra ARM](images/AboveArm.gif)<br>
        **Sopra il ARM**<br>
        1-difficile mantenere il rilevamento della mano corretta<br>
        2-causa la fatica dell'utente a causa di una posizione non naturale
    :::column-end:::
    :::column:::
        ![Sopra le dita](images/AboveFingers.gif)<br>
        **Sopra le dita**<br>
        affaticamento a 1 mano a causa del mantenimento della mano da molto tempo<br>
        problemi di rilevamento a due mani sull'indice e le dita centrali
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Sopra il centro Palm](images/handCenter.gif)<br>
        **Sopra-centro Palm**<br>
        problemi di rilevamento a una mano a causa di una sovrapposizione delle mani<br>
        affaticamento a due mani a causa del tempo di attesa lungo per interagire con i menu
    :::column-end:::
    :::column:::
        ![Parte superiore ](images/TopFingerTip.gif) della parte superiore **della mano**<br>
        problemi di rilevamento a una mano<br>
        un affaticamento a 2 mano da tenere sotto la postura normale<br>
        3-problemi durante la pressione di pulsanti con altre dita per errore a causa di spazio limitato tra le dita
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Back of the ARM](images/BackOfTheArm.gif)<br>
        **Back of the ARM**<br>
        1-è possibile attivare il pulsante Home per errore<br>
        2-posizione naturale o comoda
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>Menu a mano in MRTK (Mixed Reality Toolkit) per Unity

**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornisce gli script e le scene di esempio per il menu a mano. Lo script del Risolutore HandConstraintPalmUp consente di associare qualsiasi oggetto a mani con diverse opzioni configurabili. Gli esempi di menu della mano di MRTK includono opzioni utili, ad esempio il requisito della palma piatta e lo sguardo per impedire l'attivazione falsa.

* [Documenti menu a mano](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [Scena di esempio del menu a mano](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

È possibile provare esempi di menu a mano in HoloLens 2 con l'App Hub esempi di MRTK.

* [Scena menu a mano nell'hub esempi MRTK](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---

## <a name="see-also"></a>Vedere anche

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
