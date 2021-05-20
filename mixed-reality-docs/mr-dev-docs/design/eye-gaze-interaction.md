---
title: Interazione basata su sguardo fisso
description: Informazioni sulle interazioni basate su occhi e sguardo HoloLens 2 e sui nuovi livelli di contesto e comprensione umana, se disponibili in esperienze olografiche.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Tracciamento oculare, realtà mista, input, sguardo fisso, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit, progettazione, interazioni
ms.openlocfilehash: 207f8d0f179f722a2e4dd6d6e2bdd9cbf75b2250
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196576"
---
# <a name="eye-gaze-based-interaction-on-hololens-2"></a>Interazione basata sullo sguardo oculare HoloLens 2

![Demo di tracciamento oculare in MRTK](images/mrtk_et_scenemenu.jpg)

Una delle nuove interessanti funzionalità di HoloLens 2 è il tracciamento oculare. Nella pagina [Tracciamento](eye-tracking.md) oculare HoloLens 2 è stata indicata la necessità per ogni utente di eseguire una [calibrazione,](/hololens/hololens-calibration)sono stati forniti alcuni consigli per gli sviluppatori e sono stati evidenziati casi d'uso per il tracciamento oculare. L'input con sguardo fisso è ancora un nuovo tipo di input dell'utente e c'è molto da imparare. 

Anche se l'input dello sguardo fisso viene usato solo in modo secondario nell'esperienza Holographic Shell (l'interfaccia utente visualizzata quando si avvia il HoloLens 2), diverse app, ad esempio ["HoloLens Playground",](https://www.microsoft.com/p/mr-playground/9nb31lh723s2)illustrano esempi di come l'input dello sguardo fisso può essere aggiunto alla magia dell'esperienza olografica.
In questa pagina vengono illustrate considerazioni di progettazione per l'integrazione dell'input dello sguardo fisso per interagire con le applicazioni olografiche.

Si apprenderanno i vantaggi principali e le sfide uniche che si presentano con l'input dello sguardo fisso. In base a queste informazioni, vengono fornite diverse raccomandazioni di progettazione che consentono di creare interfacce utente con supporto dello sguardo fisso. 

## <a name="device-support"></a>Supporto di dispositivi

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Funzionalità</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
</tr>
<tr>
     <td>Sguardo fisso</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demo dei concetti di progettazione del rilevamento oculare e della testa

Se si desidera vedere i concetti di progettazione di Head e Eye Tracking in azione, vedere la demo video Designing Holograms - Head Tracking and Eye Tracking (Progettazione di **ologrammi - Tracciamento** testina e tracciamento oculare) riportata di seguito. Al termine, continuare per un'analisi più dettagliata di argomenti specifici.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Questo video è stato tratto dall'app "Designing Holograms" (Progettazione di ologrammi) HoloLens 2 app. Scaricare e usufruire dell'esperienza completa [qui.](https://aka.ms/dhapp)*

## <a name="eye-gaze-input-design-guidelines"></a>Linee guida per la progettazione dell'input con sguardo fisso

La creazione di un'interazione che sfrutta il targeting oculare in rapido movimento può essere complessa. In questa sezione vengono riepilogati i vantaggi e le sfide principali da considerare durante la progettazione dell'applicazione. 

### <a name="benefits-of-eye-gaze-input"></a>Vantaggi dell'input dello sguardo fisso

- **Puntamento ad alta velocità.** La reazione oculare è la più veloce che reagisce nel corpo umano. 

- **Sforzo limitato.** Non sono quasi necessari movimenti fisici. 

- **Natura implicita.** Spesso descritte dagli utenti come "lettura della mente", le informazioni sui movimenti oculari di un utente consentono al sistema di sapere quale destinazione l'utente intende interagire. 

- **Canale di input alternativo.** Lo sguardo fisso può fornire un potente input di supporto per l'input della mano e della voce basato su anni di esperienza da parte degli utenti in base alla coordinazione tra mano e occhio.

- **Attenzione visiva.** Un altro vantaggio importante è la possibilità di dedurre ciò che un utente sta prestando attenzione. Ciò può essere utile in diverse aree dell'applicazione, dalla valutazione più efficace di progettazioni diverse all'assistenza in interfacce utente più intelligenti e suggerimenti social migliorati per la comunicazione remota.

In breve, l'uso dello sguardo fisso come input offre un segnale di input contestuale veloce e semplice. Questa funzionalità è efficace se combinata  con altri input, ad esempio input vocale e *manuale,* per confermare la finalità dell'utente.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Problemi di sguardo fisso come input

Anche se lo sguardo fisso può essere usato per creare esperienze utente soddisfacenti, che ti fanno provare a essere un sodalio, è anche importante sapere cosa non è valido per tenere conto di questo aspetto in modo appropriato. L'elenco seguente illustra alcune *problematiche da* considerare e come affrontarle quando si lavora con l'input dello sguardo fisso: 

- **Lo sguardo fisso è "sempre on"** Nel momento in cui si aprono i lecce, gli occhi iniziano a fissarsi sugli elementi nell'ambiente. La reazione a ogni aspetto e l'emissione accidentale di azioni, perché si è visto qualcosa per troppo tempo, avrebbe comportato un'esperienza insoddisfacente.
È consigliabile combinare lo sguardo fisso  con un comando *vocale,* un movimento della *mano,* un clic del pulsante o un'sospensione estesa per attivare la selezione di una destinazione. Per altre informazioni, vedere Sguardo fisso e [commit.](gaze-and-commit-eyes.md)
Questa soluzione consente anche una modalità in cui l'utente può liberamente guardarsi attorno senza essere sovraccaricato dall'attivazione involontaria di qualcosa. Questo problema deve essere considerato anche quando si progetta un feedback visivo e udinte quando si esamina una destinazione.
Provare a non sovraccaricare l'utente con effetti popup o suoni al passaggio del mouse immediati. La sottigliezza è fondamentale. Di seguito verranno illustrate alcune procedure consigliate per questo argomento quando si parla di [consigli di progettazione.](eye-gaze-interaction.md#design-recommendations)

- **Osservazione e controllo** Si supponga di voler raddrizzare con precisione una foto sulla parete. Guardi pertanto i bordi e l'area circostante per verificare che l'immagine sia allineata correttamente. Si supponga ora di usare lo sguardo fisso come input per spostare l'immagine. L'esecuzione diventa veramente difficoltosa. Viene descritto il doppio ruolo dello sguardo fisso quando è necessario sia per l'input che per il controllo. 

- **Lasciare prima di fare clic:** Per le selezioni di destinazione rapide, la ricerca ha dimostrato che lo sguardo oculare di un utente può andare avanti prima di concludere un clic manuale (ad esempio, un tocco dell'aria). Prestare particolare attenzione alla sincronizzazione del segnale di sguardo veloce con un input di controllo più lento (ad esempio, voce, mani, controller).

- **Destinazioni di piccole dimensioni:** Si conosce la periore quando si prova a leggere un testo un po' troppo piccolo per leggere comodamente? Questo senso di stress sugli occhi può far sì che ci si senta affaticati e usurati, perché si cerca di regolare gli occhi per concentrarsi meglio.
Si tratta di un'impressione che si potrebbe richiamare negli utenti quando gli utenti forzano a selezionare destinazioni troppo piccole nell'applicazione usando il puntamento oculare.
Durante la progettazione, per creare un'esperienza piacevole e confortevole per gli utenti, è consigliabile definire destinazioni con un angolo visivo di almeno 2 gradi.

- **Movimenti degli occhi frastagliati** Gli occhi eseguono rapidi movimenti dalla fissazione alla fissazione. Se guardi i percorsi di analisi dei movimenti oculari registrati, noterai che risultano irregolari. Gli occhi si muovono rapidamente e in salti spontanei rispetto ai movimenti della testa *o* *della mano.*  

- **Monitoraggio dell'affidabilità:** L'accuratezza del tracciamento oculare può peggiorare leggermente nel cambiare la luce quando gli occhi si adattano alle nuove condizioni.
Anche se questo non deve necessariamente influire sulla progettazione dell'applicazione, poiché l'accuratezza deve rientrare nella limitazione di 2°, potrebbe essere necessario che l'utente calibra nuovamente. 


## <a name="design-recommendations"></a>Suggerimenti per la progettazione
Di seguito è riportato un elenco di raccomandazioni di progettazione specifiche in base ai vantaggi e alle sfide descritti per l'input dello sguardo oculare:

1. **Lo sguardo oculare non è lo stesso di Head-gaze:**
    - **Valutare se i movimenti oculari veloci ma instagliati si adattano all'attività di input:** Anche se i movimenti oculari veloci e instabili sono ottimi nella selezione rapida delle destinazioni nel campo visivo, è meno applicabile per le attività che richiedono movimenti di input uniformi(ad esempio, disegnare o circondare annotazioni). In questo caso, è preferibile usare il puntamento con la mano o con la testa.
  
    - **Evitare di collegare un elemento direttamente al sguardo fisso dell'utente, ad esempio un dispositivo di scorrimento o un cursore.**
Con i cursori, questo può comportare un effetto di "cursore che si alza" a causa di lievi offset nel segnale di sguardo fisso proiettato. Con un dispositivo di scorrimento, può essere in conflitto con il doppio ruolo di controllo del dispositivo di scorrimento con gli occhi e allo stesso tempo voler controllare se l'oggetto si trova nella posizione corretta. Per l'esempio del dispositivo di scorrimento, è più opportuno usare lo sguardo fisso in combinazione con i movimenti della mano. Ciò significa che l'utente può passare rapidamente e facilmente da un dispositivo di scorrimento all'altro, alzando la mano e avvicinando il pollice e il dito indice per afferrarlo e spostarlo. Quando l'avvicinamento delle dita viene rilasciato, il dispositivo di scorrimento smette di spostarsi. Gli utenti potrebbero essere sovraccaricati e distratti, soprattutto se il segnale è impreciso per tale utente. 
  
2. **Combinare lo sguardo fisso con altri input:** L'integrazione del tracciamento oculare con altri input, ad esempio movimenti della mano, comandi vocali o pressione di pulsanti, offre diversi vantaggi:
    - **Consentire l'osservazione gratuita:** Dato che il ruolo principale degli occhi è osservare l'ambiente, è importante che gli utenti siano autorizzati a guardarsi attorno senza attivare commenti o azioni (visivi, auditive e così via). 
    La combinazione del tracciamento oculare con un altro controllo di input consente una transizione uniforme tra l'osservazione del tracciamento oculare e le modalità di controllo di input.
  
    - **Provider di contesto potente:** L'uso di informazioni su dove e cosa sta guardando l'utente durante la pronuncia di un comando vocale o l'uso di un movimento della mano consente di incanalare facilmente l'input nel campo di visualizzazione. Ad esempio: _pronunciare "put that there"_ per selezionare e posizionare rapidamente e fluentemente un ologramma sulla scena osservando una destinazione e la destinazione desiderata. 

    - **Necessità di sincronizzare gli input multimodali:** La combinazione di rapidi movimenti oculari con input più complessi, ad esempio lunghi comandi vocali o movimenti della mano, presenta il rischio che l'utente continui già a guardarsi intorno prima che il comando di input aggiuntivo venga completato e riconosciuto. Se si creano controlli di input personalizzati(ad esempio, movimenti personalizzati della mano), assicurarsi di registrare l'inizio di questo input o la durata approssimativa per correlarlo con ciò che un utente ha esaminato in passato.
    
3. **Feedback sottile per l'input di tracciamento oculare:** È utile fornire commenti e suggerimenti quando si osserva una destinazione per indicare che il sistema funziona come previsto, ma deve essere mantenuto sottile. Ciò può includere la fusione lenta, l'evidenziazione visiva o l'esecuzione di altri comportamenti di destinazione sottili, ad esempio i movimenti lenti, ad esempio un leggero aumento delle dimensioni di destinazione. Ciò indica che il sistema ha rilevato correttamente che l'utente sta esaminando una destinazione senza interrompere inutilmente il flusso di lavoro corrente dell'utente. 

4. **Evitare di forzare movimenti oculari innaturali come input:** Non forzare gli utenti a usare movimenti oculari specifici (movimenti dello sguardo) per attivare azioni nell'applicazione.

5. **Considerazione delle imprecisioni:** Distinguiamo due tipi di imprecisioni, che sono evidenti per gli utenti: offset e jitter. Il modo più semplice per risolvere un offset è fornire destinazioni sufficientemente grandi con cui interagire. È consigliabile usare un angolo visivo maggiore di 2° come riferimento. Ad esempio, l'anteprima è di circa 2° nell'angolo visivo quando si estende il braccio. Segui pertanto le indicazioni seguenti:
    - Non forzare gli utenti a selezionare destinazioni di piccole dimensioni. La ricerca ha dimostrato che se le destinazioni sono sufficientemente grandi e il sistema è progettato bene, gli utenti descrivono le interazioni come facili e magiche. Se le destinazioni diventano troppo piccole, gli utenti descrivono l'esperienza come stancante e frustrante.
  
<br>

Questa pagina ha fornito una buona panoramica per iniziare a comprendere lo sguardo fisso come input nella realtà mista. Per iniziare a sviluppare, vedere le informazioni sullo sguardo fisso [in Unity](https://aka.ms/mrtk-eyes) e lo [sguardo fisso in DirectX.](../develop/native/gaze-in-directx.md)


## <a name="see-also"></a>Vedere anche
* [Comodità](comfort.md)
* [Sguardo fisso in DirectX](../develop/native/gaze-in-directx.md)
* [Sguardo fisso in Unity (Mixed Reality Toolkit)](https://aka.ms/mrtk-eyes)
* [Tracciamento oculare in HoloLens 2](eye-tracking.md)
* [Sguardo e commit](gaze-and-commit.md)
* [Sguardo fisso e attesa](gaze-and-dwell.md)
* [Input vocale](../out-of-scope/voice-design.md)