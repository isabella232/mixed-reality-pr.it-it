---
title: Puntamento con la testa e commit
description: Introduzione al modello di input Head-sguardi e commit, inclusi il ridimensionamento, la posizione e la stabilizzazione della destinazione.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Realtà mista, sguardo, targeting, interazione, progettazione, cuffie per realtà mista, cuffie di realtà mista di Windows, headset di realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, target, Focus, smoothing
ms.openlocfilehash: 13a040a8309d084fcfdbfa91cbd9d63b595b004a
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009451"
---
# <a name="head-gaze-and-commit"></a>Puntamento con la testa e commit

_Head-sguardi e commit_ sono un caso speciale del modello di input [sguardo e commit](gaze-and-commit.md) che prevede la destinazione di un oggetto con la direzione di un utente. È possibile agire sulla destinazione con un input secondario, ad esempio il tocco di movimento della mano o il comando vocale "Select". 

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
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Puntamento con la testa e commit</td>
        <td>✔️ Consigliata</td>
        <td>✔️ Consigliato (terza scelta - <a href="interaction-fundamentals.md">Vedi le altre opzioni</a>)</td>
        <td>➕ Opzione alternativa</td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a>Dimensioni della destinazione e feedback

Il vettore di sguardi a capo è stato visualizzato ripetutamente per poter essere usato per obiettivi mirati, ma spesso funziona meglio per il targeting lordo, acquisendo obiettivi più grandi. Le dimensioni di destinazione minime di 1 grado a 1,5 gradi consentono azioni utente riuscite nella maggior parte degli scenari, sebbene le destinazioni di 3 gradi consentano spesso una maggiore velocità. La dimensione che l'utente ha come destinazione è in realtà un'area 2D anche per gli elementi 3D, a seconda che la proiezione sia rivolta a tali elementi sia l'area di destinazione. Fornire un segnale saliente che un elemento è "attivo" (che è destinato all'utente) è utile. Questo può includere trattamenti quali effetti "hover" visibili, evidenziazioni audio o clic oppure un chiaro allineamento di un cursore con un elemento.

![Dimensioni ottimali della destinazione a una distanza di 2 metri](images/gazetargeting-size-1000px.jpg)<br>
*Dimensioni di destinazione ottimali a distanza di 2 metri*

<br>

![Esempio di evidenziazione di un oggetto selezionato come destinazione con lo sguardo fisso](images/gazetargeting-highlighting-940px.jpg)<br>
*Esempio di evidenziazione di un oggetto selezionato come destinazione con lo sguardo fisso*

## <a name="target-placement"></a>Posizionamento della destinazione

Spesso gli utenti non riescono a trovare gli elementi dell'interfaccia utente che si trovano troppo alta o bassa nel campo di visualizzazione. La maggior parte delle loro attenzioni si basa su aree intorno al proprio obiettivo principale, che è approssimativamente a livello di occhio. Può pertanto rivelarsi utile posizionare la maggior parte delle destinazioni in una fascia ragionevole attorno al livello degli occhi. Data la tendenza per gli utenti a concentrarsi su un'area visiva relativamente piccola in qualsiasi momento (il cono di attenzione della visione è approssimativamente di 10 gradi), raggruppare gli elementi dell'interfaccia in modo che siano correlati concettualmente possono usare comportamenti di concatenamento dell'attenzione da elemento a elemento quando un utente sposta il proprio sguardo attraverso un'area. Quando progetti l'interfaccia utente, tieni presente la grande differenza potenziale di campo visivo tra i visori HoloLens e i visori VR immersive.

![Esempio di elementi dell'interfaccia utente raggruppati per facilitare la selezione della destinazione con lo sguardo fisso in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Esempio di elementi dell'interfaccia utente raggruppati per facilitare la selezione della destinazione con lo sguardo fisso in Galaxy Explorer*

## <a name="improving-targeting-behaviors"></a>Miglioramento dei comportamenti di selezione della destinazione

Se è possibile determinare o approssimarsi in modo accurato gli obiettivi dell'utente, può essere utile accettare i tentativi di interazione Near Miss come se fossero destinati correttamente. Ecco alcuni metodi efficaci che possono essere incorporati in esperienze di realtà mista:

### <a name="head-gaze-stabilization-gravity-wells"></a>Stabilizzazione del puntamento con la testa ("pozzi di gravità")

Questa operazione deve essere attivata la maggior parte o tutto il tempo. Questa tecnica consente di rimuovere le instabilità naturale e del collo che possono essere spostate dagli utenti a causa dei comportamenti di ricerca e di pronuncia.

### <a name="closest-link-algorithms"></a>Algoritmi di collegamento più vicino

Questi algoritmi funzionano meglio in aree con contenuto interattivo sparse. Se c'è una probabilità elevata che è possibile determinare ciò che un utente ha tentato di interagire, è possibile integrare le proprie capacità di destinazione supponendo un certo livello di INTENTITà.

### <a name="backdating-and-postdating-actions"></a>Azioni di Ridata e di backdating

Questo meccanismo è utile per le attività che richiedono velocità. Quando un utente passa attraverso una serie di manovre mirate e di attivazione alla velocità, è utile presupporre un certo scopo. È utile anche per consentire la mancata procedura di azione sulle destinazioni in cui l'utente si è concentrato leggermente prima o leggermente dopo il tocco (50 ms prima/dopo è stato efficace nei test iniziali).

### <a name="smoothing"></a>Definizione di movimenti uniformi

Questo meccanismo è utile per i movimenti di percorso, riducendo il lieve jitter e le oscillazioni a causa delle caratteristiche di movimento della testa naturale. Quando si smussano i movimenti del tracciato, è necessario arrotondare le dimensioni e la distanza dei movimenti anziché nel tempo.

### <a name="magnetism"></a>Magnetismo

Questo meccanismo può essere considerato come una versione più generale degli algoritmi di collegamento più vicini, ovvero disegnare un cursore verso una destinazione o semplicemente aumentare hitboxes, in modo visibile o meno, perché gli utenti si avvicinano a destinazioni potenziali usando una certa conoscenza del layout interattivo per migliorare l'approccio degli utenti. Questo può essere potente per le destinazioni di piccole dimensioni.

### <a name="focus-stickiness"></a>Spostamento dello stato attivo in base all'elemento di interesse corrente

Quando si determinano gli elementi interattivi adiacenti da assegnare, lo stato attivo alla viscosità dello stato attivo fornisce una distorsione all'elemento attualmente attivo. Questo consente di ridurre i comportamenti di cambio dello stato attivo quando si esegue il mobile a un punto medio tra due elementi con rumore naturale.

## <a name="see-also"></a>Vedere anche

* [Interazione basata sullo sguardo](eye-gaze-interaction.md)
* [Sguardo fisso e attesa](gaze-and-dwell.md)
* [Mani - Manipolazione diretta](direct-manipulation.md)
* [Mani - Movimenti](gaze-and-commit.md#composite-gestures)
* [Mani - Puntamento e commit](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input vocale](voice-input.md)



