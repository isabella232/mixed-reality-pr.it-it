---
title: Puntamento con la testa e attesa
description: Introduzione a una panoramica del modello di input con sguardo fisso e sguardo fisso, inclusi scenari comuni e principi di progettazione.
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: Realtà mista, sguardo fisso, sguardo fisso, interazione, progettazione, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit, esperienza utente, linee guida, visualizzazione elenco
ms.openlocfilehash: e069b0815f69848b7632cb7b1b85d85f328441b7156ae22ffe097fedc3ed6fc1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223626"
---
# <a name="head-gaze-and-dwell"></a>Puntamento con la testa e attesa

Quando le mani sono occupate con gli attrezzi e le parti, i movimenti possono risultare difficili o addirittura impossibili. I comandi vocali, come i movimenti, possono non essere affidabili in determinati contesti, ad esempio in ambienti particolarmente rumorosi. Inoltre, l'uso della voce per controllare i computer, nonostante conosca una rapida diffusione, non è ancora una pratica comune ovunque. Il modello di input puntamento con la testa e attesa offre un meccanismo già familiare e di facilissima gestione per lavorare in HoloLens con la testa sollevata e senza avere bisogno di usare le mani. Questo modello di input è anche affidabile al 100%, indipendentemente dall'interferenza di possibili rumori o da eventuali obblighi di restare in silenzio nell'ambiente operativo.

## <a name="scenarios"></a>Scenari

Il sguardo fisso e l'sguardo fisso sono molto importanti negli scenari in cui le mani di una persona sono occupate da altre attività. La funzionalità è utile anche quando la voce non è affidabile al 100% o disponibile a causa di vincoli ambientali o sociali. Un buon esempio di questo tipo di situazioni è dato da una persona che indossa un dispositivo HoloLens per la sovrimpressione di informazioni di riferimento mentre ripara il motore di un'automobile. Le sue mani sono occupate con gli attrezzi o devono sostenere il corpo mentre la persona si protende sul vano motore. L'autofficina è rumorosa a causa dei colpi e del ronzio costanti degli attrezzi da lavoro, quindi l'uso dei comandi vocali risulterebbe particolarmente difficoltoso. Lo sguardo con la testa e l'sguardo fisso consentono alla persona che usa il HoloLens di esplorare in modo sicuro il materiale di riferimento senza interrompere il flusso di lavoro. 

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
        <td>Puntamento con la testa e attesa</td>
        <td>✔️ Consigliato</td>
        <td>✔️ Consigliato</td>
        <td>✔️ Consigliato</td>
    </tr>
</table>


## <a name="design-principles"></a>Principi di progettazione

**Evitare di usare lo "sguardo fisso come un'arma"**

Il puntamento con la testa e l'attesa richiedono un feedback visivo intuitivo, ma una mole eccessiva di feedback può produrre ansia. I commenti e suggerimenti dovrebbero aiutare un utente a sapere quale destinazione sta facendo, ma non a selezionare automaticamente l'elemento in base alle proprie finalità. Durante la lettura di testo, icone ed etichette, è necessario fornire agli utenti il tempo necessario per l'assorbimento delle informazioni prima della selezione.
    
**Cercare di ottenere una velocità ottimale**
    
Le interazioni di attesa possono avere timer diversi in base all'impatto sulla navigazione: le funzioni usate con maggiore frequenza in genere traggono vantaggio da tempi di riempimento più ridotti, mentre le funzioni più consequenziali possono trarre vantaggio da tempi di riempimento più lunghi. Quando viene usato un effetto di riempimento per mostrare questi timer, le curve di animazione del colore di riempimento possono indurre positivamente la sensazione che i tempi di riempimento siano più rapidi. Considera questi aspetti per consentire all'utente di prendere le sue decisioni scegliendo override della velocità di riempimento alta/media/bassa.
    
**Evitare l'effetto yo-yo**

L'effetto yo-yo è un modello di movimento della testa che si verifica quando il posizionamento del contenuto e i controlli di posizionamento del contenuto e sguardo fisso/sguardo fisso forzano le persone a cercare più volte. Ad esempio, uno spostamento nell'elenco con il pulsante con lo sguardo con la testa e l'sospensione nella parte inferiore provoca un ciclo di : guardare verso il basso per l'ora, esaminare i risultati, guardare in basso per l'indutto e così via. Il modello risultante è molto azzarto, quindi è consigliabile posizionare i controlli di navigazione in una posizione centralizzata che richiede meno back-and-forth. Il posizionamento dei pulsanti di posizionamento in base ai relativi effetti diventa importante per il comfort.
s
<br>

---

## <a name="ux-guidelines-and-best-practices"></a>Linee guida e procedure consigliate per l'esperienza utente

### <a name="target-sizes"></a>Dimensioni delle destinazioni

Per essere facilmente accessibili, le destinazioni con punta e attesa devono essere sufficientemente grandi da poter guardare con facilità e mantenere la testa stabile sulla destinazione per il tempo prestabilito. È consigliabile una dimensione minima di destinazione di 2 gradi per ottenere l'esperienza più comoda. 

### <a name="visual-feedback"></a>Feedback visivo

Quando usi un riempimento radiale per rappresentare il timer di attesa, inizia dalla parte centrale del pulsante. Una risposta uniforme genera meno confusione di tante indicazioni diverse sui vari pulsanti. 

  * Questa regola può tuttavia essere interrotta per le interazioni direzionali(ad esempio, spostamento su/giù/sinistra/destra e così via). Ad esempio, Microsoft Dynamics 365 Guides fa un'eccezione per AVANTI/INDIETRO, trattandosi di riempimenti sinistra-destra.
  * Prendere in considerazione l'inversione del riempimento radiale dall'esterno, per scenari come la rimozione di un pulsante. La sensazione opposta di premere un pulsante è un effetto visivo piacevole da mantenere. 

### <a name="progressive-disclosure"></a>Rivelazione progressiva

Con la rilevazione progressiva vengono mostrati solo i dettagli rilevanti in ciascuna fase di un'interazione. Per l'avaio, ciò significa che la destinazione dell'avaio viene rivelata durante l'evidenziazione (ad esempio, in un controllo elenco).

 ### <a name="oversized-targets"></a>Destinazioni di dimensioni eccessive

L'area di attesa può essere più grande dell'icona inattiva per agevolare l'uso, come nel caso del pulsante Indietro in Microsoft Dynamics 365 Guides.

### <a name="prevent-flickering-with-delayed-feedback"></a>Evitare lo sfarfallio con un feedback ritardato

Aggiungi un breve ritardo prima di avviare il feedback visivo per evitare lo sfarfallio quando qualcuno passa su una destinazione di attesa.
* Per i pulsanti con cui si interagisce di frequente, tenere breve il ritardo in modo che l'applicazione sia reattiva.
* Per i pulsanti con cui si interagisce raramente, un ritardo più lungo può essere appropriato per evitare che l'interfaccia si rivoluzioni.

<br>

---

## <a name="ui-patterns"></a>Modelli per l'interfaccia utente

### <a name="high-frequency-buttons"></a>Pulsanti usati frequentemente

:::row:::
    :::column:::
        I pulsanti ad alta frequenza sono pulsanti usati comunemente in un'applicazione. Un buon esempio è rappresentato dai pulsanti Avanti e Indietro in Microsoft Dynamics 365 Guides.<br>
        <br>
        **Indicazioni**<br>
  * I pulsanti ad alta frequenza devono essere di grandi dimensioni, più facili da premere con lo sguardo fisso con la testa
  * Rimanere vicino all'altezza degli occhi per evitare che si esercitino le affaticazioni.<br>
        <br>
*Immagine: Pulsante Dynamics 365 Guides Avanti di Microsoft*
    :::column-end:::
        :::column:::
       ![Pulsante Dynamics 365 Guides Successivo di Microsoft](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a>Pulsanti usati raramente

I pulsanti a bassa frequenza sono pulsanti con cui non si interagisce regolarmente in tutta l'applicazione. Un buon esempio è rappresentato da un pulsante che consente di accedere al menu delle impostazioni o di cancellare tutto il lavoro svolto.

* Prova a posizionare questi pulsanti in modo che non intralcino i percorsi di puntamento con la testa di uso frequente per evitare che vengano attivati accidentalmente. 

<br>

---

### <a name="confirmations"></a>Conferme

:::row:::
    :::column:::
        Quando un'azione ha un impatto significativo, ad esempio l'addebito di denaro, l'eliminazione di lavoro o l'avvio di un lungo processo, è utile verificare che una persona intendesse selezionare un pulsante.<br>
        <br>
        **Indicazioni**<br>
  * Mostra l'evidenziazione della selezione sul pulsante principale.
  * Rivela la destinazione dell'attesa contemporaneamente all'evidenziazione della selezione.
  * Per il pulsante secondario, rivela la destinazione dell'attesa al momento del puntamento con la testa.<br>
        <br>
*Immagine: finestra di dialogo di conferma Dynamics 365 Guides Microsoft*
    :::column-end:::
        :::column:::
       ![Finestra di dialogo di Dynamics 365 Guides microsoft](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a>Interruttori

Per funzionare correttamente, gli interruttori necessitano di una logica più sottile. Quando una persona si attiva e si attiva un interruttore, deve uscire dal pulsante e quindi tornare a riavviare la logica di sospensione. È importante che i pulsanti aggregabili hanno uno stato attivo chiaro rispetto a inattivo. 

<br>

---

### <a name="list-views"></a>Visualizzazioni elenco

:::row:::
    :::column:::
        Le visualizzazioni elenco presentano una particolare sfida per l'input di sguardo con la testa e di sguardo fisso. Gli utenti possono eseguire la scansione del contenuto senza avere la sensazione di dover fare una mancia intorno alle destinazioni di insodssibili.<br>
        <br>
**Indicazioni**<br>
  * Fare in modo che l'intera riga sia evidenziata quando viene fisso con la testa, ma non inizia l'insodrezione a meno che il sguardo con la testa non sia sulla destinazione di un'ora specifica.
  * Mostra la destinazione di invadamento solo quando la riga è evidenziata per ridurre il rumore visivo.
  * Essere chiari e coerenti con la posizione delle destinazioni di allocazione.
  * Non visualizzare tutte le destinazioni di invii contemporaneamente per evitare un'interfaccia utente ripetitiva.
  * Riutilizzare lo stesso modello il più spesso possibile per acquisire familiarità con l'esperienza utente.<br>
        <br>
*Immagine: Elenco Dynamics 365 Guides Microsoft*
    :::column-end:::
        :::column:::
       ![Elenco Dynamics 365 Guides Microsoft](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a>Vedi anche

* [Sguardo e commit](gaze-and-commit.md)
* [Mani - Manipolazione diretta](direct-manipulation.md)
* [Mani - Movimenti](gaze-and-commit.md#composite-gestures)
* [Mani - Puntamento e commit](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input vocale](voice-input.md)