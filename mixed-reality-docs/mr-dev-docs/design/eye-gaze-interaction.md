---
title: Interazione basata su sguardo fisso
description: Scopri le interazioni basate su occhi e sguardi su HoloLens 2 e i nuovi livelli di contesto e comprensione umana, se disponibili in esperienze olografiche.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Rilevamento degli occhi, realtà mista, input, sguardi oculari, cuffie per realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, progettazione, interazioni
ms.openlocfilehash: b5091b92fd048f72184212401d54ad0b7353875c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008581"
---
# <a name="eye-gaze-based-interaction-on-hololens-2"></a>Interazione basata sugli sguardi su HoloLens 2

![Demo sul rilevamento degli occhi in MRTK](images/mrtk_et_scenemenu.jpg)

Una delle nuove interessanti funzionalità di HoloLens 2 è la verifica degli occhi. Nella pagina [HoloLens 2](eye-tracking.md) è stata illustrata la necessità di ogni utente di eseguire una [calibrazione](https://docs.microsoft.com/hololens/hololens-calibration), fornite alcune indicazioni per gli sviluppatori e casi d'uso evidenziati per la verifica degli occhi. L'input con sguardo oculare è ancora un nuovo tipo di input dell'utente ed è necessario apprendere molto. 

Anche se l'input con sguardo oculare viene usato solo in modo impercettibile nell'esperienza della shell olografica (l'interfaccia utente visualizzata quando si avvia HoloLens 2), più app, ad esempio ["HoloLens Playground"](https://www.microsoft.com/p/mr-playground/9nb31lh723s2), presentano esempi eccezionali sul modo in cui l'input dello sguardo può essere aggiunto alla magia dell'esperienza olografica.
In questa pagina vengono illustrate le considerazioni di progettazione per l'integrazione dell'input Eye-sguardi per interagire con le applicazioni olografiche.

Verranno fornite informazioni sui vantaggi principali, oltre a una sfida univoca in grado di ottenere un input mirato. In base a questi, sono disponibili diversi consigli per la progettazione che consentono di creare interfacce utente supportate da sguardi oculisti. 

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
     <td><a href="../hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
</tr>
<tr>
     <td>Sguardo attento</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>


## <a name="eye-gaze-input-design-guidelines"></a>Linee guida per la progettazione di input con sguardo attento

La creazione di un'interazione che sfrutta la scelta rapida per gli occhi in rapida evoluzione può risultare complessa. In questa sezione vengono riepilogati i vantaggi e le questioni principali da considerare durante la progettazione dell'applicazione. 

### <a name="benefits-of-eye-gaze-input"></a>Vantaggi dell'input con sguardo a occhio

- **Puntamento ad alta velocità.** Il muscolo occhi è il muscolo più veloce nel corpo umano. 

- **Sforzo limitato.** Non sono quasi necessari movimenti fisici. 

- **Natura implicita.** Spesso descritta dagli utenti come "lettura mentale", le informazioni sui movimenti degli occhi di un utente consentono al sistema di sapere quale destinazione prevede l'intervento dell'utente. 

- **Canale di input alternativo.** Eye-sguardi può offrire un potente input di supporto per l'input vocale e di mano che si basa su anni di esperienza degli utenti in base al coordinamento degli occhi.

- **Attenzione visiva.** Un altro vantaggio importante è la possibilità di dedurre ciò a cui un utente presta attenzione. Questo può essere utile in diverse aree applicative, da valutare in modo più efficace le diverse progettazioni per aiutare le interfacce utente più intelligenti e suggerimenti sociali avanzati per la comunicazione remota.

In breve, l'uso di Eye-sguardi come input offre un segnale di input contestuale rapido e semplice. Questa funzionalità è potente se combinata con altri input, ad esempio la *voce* e l'input *manuale* , per confermare le finalità dell'utente.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Problemi di Eye-sguardi come input

Sebbene sia possibile usare gli sguardi per creare esperienze utente soddisfacenti, che rendono un supereroe, è anche importante sapere che cosa non è adatto a tenere in considerazione questo aspetto. Nell'elenco seguente vengono illustrate alcune delle *questioni* da prendere in considerazione e come risolverle quando si lavora con l'input Eye-sguardi: 

- **Il controllo degli sguardi è "always on"** Nel momento in cui si aprono i coperchi degli occhi, gli occhi iniziano a fissando su elementi nell'ambiente. Reagire a ogni aspetto effettuato e rilasciare accidentalmente le azioni, perché si è verificato un problema troppo lungo, comporterebbe un'esperienza insoddisfacente.
Si consiglia di combinare gli sguardi con un *comando vocale*, un *gesto della mano*, un clic del *pulsante* o un'abitazione estesa per attivare la selezione di una destinazione (per altre informazioni, vedere [Eye-sguardi e commit](gaze-and-commit-eyes.md)).
Questa soluzione consente anche una modalità in cui l'utente può esaminarsi liberamente senza essere sopraffatto dall'attivazione involontaria di qualcosa. Questo problema deve essere preso in considerazione anche quando si progettano commenti visivi e uditivi quando si esamina una destinazione.
Provare a non sovraccaricare l'utente con effetti di pop-out immediati o rumori al passaggio del mouse. La sottigliezza è Key. Verranno illustrate alcune procedure consigliate per questo più avanti quando si parlano le [raccomandazioni di progettazione](eye-gaze-interaction.md#design-recommendations).

- **Confronto tra osservazione e controllo** Si supponga di voler raddrizzare con precisione una fotografia sulla parete. Guardi pertanto i bordi e l'area circostante per verificare che l'immagine sia allineata correttamente. A questo punto, si supponga di voler usare il proprio sguardo come input per spostare l'immagine. L'esecuzione diventa veramente difficoltosa. Viene descritto il doppio ruolo degli occhi quando è necessario sia per l'input che per il controllo. 

- **Lasciare prima di fare clic su:** Per le selezioni di destinazione rapide, la ricerca ha dimostrato che lo sguardo a un utente può proseguire prima di concludere un clic manuale (ad esempio, un rubinetto aria). Prestare particolare attenzione alla sincronizzazione del segnale di sguardo rapido con un input di controllo più lento (ad esempio, Voice, Hands, controller).

- **Destinazioni di piccole dimensioni:** Si conosce la sensazione quando si tenta di leggere il testo che è troppo piccolo per leggere comodamente? Questa sensazione di limitazione degli sguardi può comportare la disattivazione e l'esaurimento, perché si tenta di modificare gli occhi per concentrarsi meglio.
Si tratta di un sentimento che è possibile richiamare negli utenti quando si impone loro di selezionare destinazioni troppo piccole nell'applicazione usando la destinazione degli occhi.
Durante la progettazione, per creare un'esperienza piacevole e confortevole per gli utenti, è consigliabile definire destinazioni con un angolo visivo di almeno 2 gradi.

- **Spostamenti occhi** incompleti Gli occhi eseguono movimenti rapidi dalla fissa alla fissa. Se guardi i percorsi di analisi dei movimenti oculari registrati, noterai che risultano irregolari. Gli occhi si spostano rapidamente e in salti spontanei rispetto ai movimenti a *capo* o a *mano*.  

- **Verifica dell'affidabilità:** L'accuratezza del rilevamento degli sguardi può compromettere leggermente la luce quando gli occhi si adattano alle nuove condizioni.
Sebbene questo non debba necessariamente influire sulla progettazione dell'applicazione, in quanto l'accuratezza dovrebbe rientrare nel limite di 2 °, potrebbe essere necessario che l'utente ricalibra nuovamente. 


## <a name="design-recommendations"></a>Suggerimenti per la progettazione
Di seguito è riportato un elenco di raccomandazioni di progettazione specifiche in base ai vantaggi e alle problemi descritti per l'input degli sguardi:

1. **Gli sguardi occhi non sono gli stessi:**
    - **Considerare se i movimenti degli occhi veloci ma incompleti si adattano all'attività di input:** Sebbene i nostri movimenti rapidi e incompleti siano molto rapidi quando si selezionano rapidamente le destinazioni nel campo di visualizzazione, è meno applicabile per le attività che richiedono traiettorie di input uniformi, ad esempio la creazione o l'inclusione di annotazioni. In questo caso, è preferibile usare il puntamento con la mano o con la testa.
  
    - **Evitare di allungare direttamente gli sguardi degli utenti (ad esempio, un dispositivo di scorrimento o un cursore).**
Con i cursori, questo può comportare un effetto di "cursore in fuga" a causa di lievi offset nel segnale di sguardo proiettato. Con un dispositivo di scorrimento, può essere in conflitto con il doppio ruolo del controllo del dispositivo di scorrimento con gli occhi, ma anche per verificare se l'oggetto si trova nella posizione corretta. Per l'esempio del dispositivo di scorrimento, è opportuno usare gli sguardi in combinazione con i movimenti della mano. Ciò significa che l'utente può spostarsi rapidamente e senza fatica tra molti dispositivi di scorrimento, sollevando la mano e pizzicando il pollice e l'indice per spostarlo. Quando il pizzico viene rilasciato, il dispositivo di scorrimento smette di essere spostato. Gli utenti possono diventare sopraffatti e distratti, soprattutto se il segnale è impreciso per tale utente. 
  
2. **Combinare gli sguardi con gli altri input:** L'integrazione di Eye Tracking con altri input, ad esempio movimenti della mano, comandi vocali o pressioni dei pulsanti, offre diversi vantaggi:
    - **Consenti l'osservazione gratuita:** Dato che il ruolo principale degli occhi è osservare l'ambiente, è importante che gli utenti siano autorizzati a cercare senza attivare commenti o azioni (visivi, uditivi e così via). 
    La combinazione di rilevamento degli occhi con un altro controllo di input consente una transizione uniforme tra le modalità di osservazione e controllo di input.
  
    - **Potente provider di contesto:** Usando le informazioni su dove e cosa si sta osservando l'utente mentre viene detto un comando vocale o usando un movimento mano, è possibile canalizzare facilmente l'input nel campo della visualizzazione. Ad esempio, supponiamo di _inserire_ un ologramma per selezionare e posizionare in modo rapido e scorrevole un ologramma nella scena osservando una destinazione e la destinazione desiderata. 

    - **Necessità di sincronizzare gli input multimodali:** La combinazione di movimenti di occhi rapidi con input più complessi, ad esempio comandi di tipo Long Voice o movimenti della mano, presenta il rischio che l'utente continui a esaminare prima che il comando di input aggiuntivo venga terminato e riconosciuto. Se si creano controlli di input personalizzati, ad esempio movimenti della mano personalizzati, assicurarsi di registrare l'inizio di questo input o la durata approssimativa per correlarla a ciò che un utente ha esaminato in passato.
    
3. **Feedback sottile per l'input di rilevamento degli occhi:** È utile per fornire commenti e suggerimenti quando viene esaminata una destinazione per indicare che il sistema funziona come previsto, ma deve essere mantenuto sottile. Questo può includere la fusione lenta in uscita, le evidenziazioni visive o altri comportamenti di destinazione più sottili, ad esempio movimenti lenti, ad esempio un lieve aumento delle dimensioni di destinazione. Ciò indica che il sistema ha rilevato correttamente che l'utente sta esaminando una destinazione senza interrompere inutilmente il flusso di lavoro corrente dell'utente. 

4. **Evitare di applicare movimenti degli occhi non naturali come input:** Non forzare gli utenti a usare movimenti oculari specifici (movimenti sguardi) per attivare azioni nell'applicazione.

5. **Account per l'imprecisione:** Vengono distinti due tipi di imprecisioni, che sono evidenti per gli utenti: offset e jitter. Il modo più semplice per risolvere un offset consiste nel fornire destinazioni sufficientemente grandi per interagire con. Si consiglia di usare un angolo visivo maggiore di 2 ° come riferimento. Ad esempio, l'anteprima è di circa 2 ° nell'angolo visivo quando si allunga il ARM. Segui pertanto le indicazioni seguenti:
    - Non forzare gli utenti a selezionare destinazioni minuscole. La ricerca ha dimostrato che se le destinazioni sono sufficientemente grandi e il sistema è progettato correttamente, gli utenti ne descrivono le interazioni in modo semplice e magico. Se le destinazioni diventano troppo piccole, gli utenti descrivono l'esperienza come stancante e frustrante.
  
<br>

Questa pagina offre una panoramica corretta per iniziare a comprendere gli sguardi come input in realtà mista. Per iniziare a sviluppare, vedere le nostre informazioni sugli sguardi [in Unity](https://aka.ms/mrtk-eyes) e sugli [sguardi in DirectX](../develop/native/gaze-in-directx.md).


## <a name="see-also"></a>Vedere anche
* [Comodità](comfort.md)
* [Eye-sguardi in DirectX](../develop/native/gaze-in-directx.md)
* [Eye-sguardi in Unity (Toolkit realtà mista)](https://aka.ms/mrtk-eyes)
* [Tracciamento oculare in HoloLens 2](eye-tracking.md)
* [Sguardo e commit](gaze-and-commit.md)
* [Sguardo fisso e attesa](gaze-and-dwell.md)
* [Input vocale](../out-of-scope/voice-design.md)
