---
title: Puntamento con la testa e commit
description: Introduzione al modello di input head-gaze e commit, tra cui ridimensionamento, posizionamento e stabilizzazione della destinazione.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Realtà mista, sguardo, targeting dello sguardo, interazione, progettazione, visore per realtà mista, visore per realtà mista windows, visore per realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit, destinazione, messa a fuoco, smoothing
ms.openlocfilehash: 74f963a6b450d1fb7f1302886a01c12cf79ce28a
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196516"
---
# <a name="head-gaze-and-commit"></a>Puntamento con la testa e commit

_Head-gaze and commit_ è un caso speciale del modello di input [gaze and commit](gaze-and-commit.md) che prevede la destinazione di un oggetto con una direzione di testa degli utenti. È possibile agire sulla destinazione con un input secondario, ad esempio il tocco dell'aria del movimento della mano o il comando vocale "Seleziona". 

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modello di input</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Puntamento con la testa e commit</td>
        <td>✔️ Consigliato</td>
        <td>✔️ Consigliato (terza scelta - <a href="interaction-fundamentals.md">Vedi le altre opzioni</a>)</td>
        <td>➕ Opzione alternativa</td>
    </tr>
</table>

---

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demo dei concetti di progettazione del rilevamento oculare e della testa

Se si desidera vedere i concetti di progettazione di Head e Eye Tracking in azione, vedere la demo video **Designing Holograms - Head Tracking and Eye Tracking** (Progettazione di ologrammi - Rilevamento della testa e tracciamento oculare) di seguito. Al termine, continuare per un'analisi più dettagliata di argomenti specifici.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Questo video è stato tratto dall'app "Designing Holograms" (Progettazione di ologrammi) HoloLens 2 app. Scaricare e usufruire dell'esperienza completa [qui.](https://aka.ms/dhapp)*

## <a name="target-sizing-and-feedback"></a>Dimensioni della destinazione e feedback

Il vettore dello sguardo fisso della testa è stato ripetutamente indicato come utilizzabile per la destinazione fine, ma spesso funziona meglio per il targeting lordo, acquisendo obiettivi più grandi. Le dimensioni minime di destinazione da 1 a 1,5 gradi consentono azioni utente riuscite nella maggior parte degli scenari, anche se le destinazioni di 3 gradi spesso consentono una maggiore velocità. Le dimensioni di destinazione dell'utente sono effettivamente un'area 2D anche per gli elementi 3D, a seconda della proiezione che li sta affrontando, deve essere l'area di destinazione. È utile fornire un segnale saliente che un elemento è "attivo" (che l'utente sta indicando come destinazione). Può trattarsi di effetti visibili di "hover", evidenziazioni audio o clic o di un allineamento chiaro di un cursore con un elemento.

![Dimensioni ottimali della destinazione a una distanza di 2 metri](images/gazetargeting-size-1000px.jpg)<br>
*Dimensioni ottimali della destinazione a 2 metri di distanza*

<br>

![Esempio di evidenziazione di un oggetto selezionato come destinazione con lo sguardo fisso](images/gazetargeting-highlighting-940px.jpg)<br>
*Esempio di evidenziazione di un oggetto selezionato come destinazione con lo sguardo fisso*

## <a name="target-placement"></a>Posizionamento della destinazione

Gli utenti spesso non riescono a trovare gli elementi dell'interfaccia utente che si trovano troppo in alto o in basso nel campo di visualizzazione. La maggior parte della loro attenzione finisce sulle aree intorno alla loro attenzione principale, che è approssimativamente a livello oculare. Può pertanto rivelarsi utile posizionare la maggior parte delle destinazioni in una fascia ragionevole attorno al livello degli occhi. Data la tendenza degli utenti a concentrarsi su un'area visiva relativamente piccola in qualsiasi momento (il cono di vista attento è di circa 10 gradi), il raggruppamento degli elementi dell'interfaccia utente nella misura concettuale in cui sono correlati può usare comportamenti di concatenamento dell'attenzione da elemento a elemento quando un utente sposta lo sguardo fisso in un'area. Quando progetti l'interfaccia utente, tieni presente la grande differenza potenziale di campo visivo tra i visori HoloLens e i visori VR immersive.

![Esempio di elementi dell'interfaccia utente raggruppati per facilitare la selezione della destinazione con lo sguardo fisso in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Esempio di elementi dell'interfaccia utente raggruppati per facilitare la selezione della destinazione con lo sguardo fisso in Galaxy Explorer*

## <a name="improving-targeting-behaviors&quot;></a>Miglioramento dei comportamenti di selezione della destinazione

Se l'intento dell'utente di specificare come destinazione un elemento può essere determinato o approssimato in modo molto approssimativo, può essere utile accettare tentativi di interazione quasi non riusciti come se fossero stati indirizzati correttamente. Ecco alcuni metodi di successo che possono essere incorporati nelle esperienze di realtà mista:

### <a name=&quot;head-gaze-stabilization-gravity-wells&quot;></a>Stabilizzazione del puntamento con la testa (&quot;pozzi di gravità")

Questa opzione deve essere attivata per la maggior parte o per tutto il tempo. Questa tecnica rimuove gli instabilità naturali della testa e del collo che gli utenti potrebbero avere anche il movimento a causa dei comportamenti di aspetto e di pronuncia.

### <a name="closest-link-algorithms"></a>Algoritmi di collegamento più vicino

Questi algoritmi funzionano meglio nelle aree con contenuto interattivo di tipo sparse. Se esiste un'alta probabilità che sia possibile determinare con quale elemento un utente sta tentando di interagire, è possibile integrare le capacità di destinazione presupponendo un certo livello di finalità.

### <a name="backdating-and-postdating-actions"></a>Backdating e postdating actions

Questo meccanismo è utile per le attività che richiedono velocità. Quando un utente sta passando attraverso una serie di richieste di destinazione e attivazione a velocità elevata, è utile presupporre una certa finalità. È anche utile consentire ai passaggi non esigibili di agire sulle destinazioni che l'utente aveva in stato di interesse leggermente prima o dopo il tocco (50 ms prima/dopo erano efficaci nei primi test).

### <a name="smoothing"></a>Definizione di movimenti uniformi

Questo meccanismo è utile per il pathing dei movimenti, riducendo i lievi instabilità e gli instabilità a causa delle caratteristiche naturali del movimento della testa. Quando si smussa sui movimenti tracciati, smussare in base alle dimensioni e alla distanza dei movimenti anziché nel tempo.

### <a name="magnetism"></a>Magnetismo

Questo meccanismo può essere pensato come una versione più generale degli algoritmi di collegamento più vicini: il disegno di un cursore verso una destinazione o semplicemente l'aumento di hitbox, in modo visibile o meno, quando gli utenti si avvicinano alle destinazioni più probabili usando una certa conoscenza del layout interattivo per approcciare meglio la finalità dell'utente. Ciò può essere efficace per destinazioni di piccole dimensioni.

### <a name="focus-stickiness"></a>Spostamento dello stato attivo in base all'elemento di interesse corrente

Quando si determinano gli elementi interattivi vicini a cui assegnare lo stato attivo, l'aderenza dello stato attivo fornisce una distorsione all'elemento attualmente attivo. Ciò consente di ridurre i comportamenti di cambio dello stato attivo irregolare quando si fluttua a un punto intermedio tra due elementi con disturbo naturale.

## <a name="see-also"></a>Vedi anche

* [Interazione basata sullo sguardo](eye-gaze-interaction.md)
* [Sguardo fisso e attesa](gaze-and-dwell.md)
* [Mani - Manipolazione diretta](direct-manipulation.md)
* [Mani - Movimenti](gaze-and-commit.md#composite-gestures)
* [Mani - Puntamento e commit](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input vocale](voice-input.md)