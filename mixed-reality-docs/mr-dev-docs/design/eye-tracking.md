---
title: Tracciamento oculare
description: Informazioni sul tracciamento oculare HoloLens 2 e sui nuovi livelli di comprensione umana, se disponibili in esperienze olografiche.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Tracciamento oculare, realtà mista, input, sguardo fisso, calibrazione, visore per realtà mista, visore per realtà mista windows, visore di realtà virtuale, HoloLens, MRTK, Toolkit, finalità, azioni
ms.openlocfilehash: ce8ffcb6b8b59b6b0484ba4b3db256a8df5810ea2719416bea9e3f4366ad6afe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214146"
---
# <a name="eye-tracking-on-hololens-2"></a>Tracciamento oculare in HoloLens 2

![Demo di tracciamento oculare in MRTK](images/mrtk_et_scenemenu.jpg)

HoloLens 2 consente un nuovo livello di contesto e comprensione umana all'interno dell'esperienza olografica, offrendo agli sviluppatori la possibilità di usare informazioni su ciò che l'utente sta esaminando. Questa pagina illustra come gli sviluppatori possono trarre vantaggio dal tracciamento oculare per vari casi d'uso e cosa cercare quando progettano interazioni utente basate su sguardo oculare. 

L'API di tracciamento oculare è stata progettata in base alla privacy dell'utente, evitando di passare informazioni identificabili, in particolare la biometria. Per le applicazioni con funzionalità di tracciamento oculare, l'utente deve concedere all'app l'autorizzazione per usare le informazioni di tracciamento oculare.

### <a name="device-support"></a>Supporto di dispositivi

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

<br>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demo dei concetti di progettazione del rilevamento oculare e della testa

Se si desidera vedere i concetti di progettazione di Head e Eye Tracking in azione, vedere la demo video Progettazione **di Ologrammi - Tracciamento** testina e tracciamento oculare di seguito. Al termine, continuare per un'analisi più dettagliata di argomenti specifici.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Questo video è stato tratto dall'app "Progettazione Ologrammi" HoloLens 2 app. Scaricare e usufruire dell'esperienza completa [qui.](https://aka.ms/dhapp)*

## <a name="calibration"></a>Calibrazione 

Per il corretto funzionamento del tracciamento oculare, ogni utente deve eseguire una calibrazione dell'utente di tracciamento oculare per cui l'utente deve esaminare un set di obiettivi olografici. [](/hololens/hololens-calibration) Ciò consente al dispositivo di regolare il sistema per un'esperienza di visualizzazione più comoda e di qualità superiore per l'utente e di garantire un monitoraggio oculare accurato allo stesso tempo. 

Il tracciamento oculare dovrebbe funzionare per la maggior parte degli utenti, ma in rari casi un utente non può eseguire correttamente la calibrazione. La calibrazione potrebbe non riuscire per vari motivi, tra cui: 
* L'utente ha precedentemente scelto esplicitamente di rifiutare esplicitamente il processo di calibrazione
* L'utente si è distratto e non ha seguito gli obiettivi di calibrazione
* L'utente ha alcuni tipi di lenti a contatto e occhiali, che il sistema non supporta ancora 
* L'utente ha determinate fisiologia oculare, condizioni oculare o ha avuto un intervento oculare, che il sistema non supporta ancora  
* Fattori esterni che inibiscono il tracciamento oculare affidabile, ad esempio sbavature sulla visiera o sugli occhiali HoloLens, luce solare diretta intensa e occlusioni dovute ai peli davanti agli occhi

Gli sviluppatori devono assicurarsi di fornire un supporto adeguato per gli utenti per i quali i dati di tracciamento oculare potrebbero non essere disponibili (che non sono in grado di calibrare correttamente). Sono stati forniti consigli per le soluzioni di fallback nella sezione nella parte inferiore di questa pagina. 

Per altre informazioni sulla calibrazione e su come garantire un'esperienza uniforme, vedere la pagina di [calibrazione](/hololens/hololens-calibration) dell'utente di tracciamento oculare.

<br>

## <a name="available-eye-tracking-data"></a>Dati di tracciamento oculare disponibili

Prima di illustrare in dettaglio casi d'uso specifici per l'input dello sguardo fisso, è necessario illustrare brevemente le funzionalità fornite dall'API di HoloLens 2 [Eye Tracking.](/uwp/api/windows.perception.people.eyespose) Gli sviluppatori possono accedere a un singolo raggio visivo (origine e direzione dello sguardo) a _circa 30 FPS (30 Hz)._
Per informazioni più dettagliate su come accedere ai dati di tracciamento oculare, vedere le guide per gli sviluppatori per l'uso dello sguardo fisso [in DirectX](../develop/native/gaze-in-directx.md) e dello sguardo [fisso in Unity.](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

Lo sguardo oculare previsto è approssimativamente entro 1,5 gradi nell'angolo visivo intorno alla destinazione effettiva (vedere la figura seguente). Come si prevede, gli sviluppatori devono pianificare un margine intorno a questo valore con limite inferiore (ad esempio, 2,0-3,0 gradi può comportare un'esperienza molto più comoda). Di seguito verrà descritto come risolvere la selezione di destinazioni di piccole dimensioni. Per un accurato funzionamento del tracciamento oculare, ogni utente deve essere sottoposto a un'apposita calibrazione. 

![Dimensioni ottimali della destinazione a una distanza di 2 metri](images/gazetargeting-size-1000px.jpg)<br>
*Dimensioni ottimali della destinazione a una distanza di 2 metri*

<br>

## <a name="use-cases"></a>Casi d'uso

Il tracciamento oculare consente alle applicazioni di tenere traccia di dove guarda l'utente in tempo reale. I casi d'uso seguenti descrivono alcune interazioni possibili con il tracciamento oculare HoloLens 2 in realtà mista.
Questi casi d'uso non fanno ancora parte dell'esperienza holographic Shell, ovvero l'interfaccia visualizzata all'avvio del HoloLens 2.
È possibile provare alcuni di essi in [Mixed Reality Toolkit ,](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)che offre diversi esempi interessanti e potenti per l'uso del tracciamento oculare, ad esempio selezioni rapide e senza sforzo di destinazione supportate dagli occhi e scorrimento automatico del testo in base all'aspetto dell'utente. 

### <a name="user-intent"></a>Operazione che l'utente intende eseguire

Le informazioni su dove e cosa un utente esamina forniscono un contesto potente per altri **input,** ad esempio voce, mani e controller.
Tali informazioni possono essere usate per diverse attività.
Ad esempio, questo può variare da  una destinazione rapida e senza sforzo all'interno della scena osservando un ologramma e pronunciando *"select"* (vedere anche [gaze and commit)](gaze-and-commit.md)o *"put this...",* quindi esaminando dove l'utente vuole posizionare l'ologramma e *pronunciare "... there"*. Per alcuni esempi, vedi [Mixed Reality Toolkit - Selezione della destinazione con lo sguardo](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) e [Mixed Reality Toolkit - Posizionamento della destinazione con lo sguardo](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-positioning).

Inoltre, un esempio per la finalità dell'utente può includere l'uso di informazioni su ciò che gli utenti guardano per migliorare l'engagement con agenti virtuali e ologrammi interattivi. Ad esempio, gli agenti virtuali potrebbero adattare le opzioni disponibili e il relativo comportamento, in base al contenuto attualmente visualizzato. 

### <a name="implicit-actions"></a>Azioni implicite

La categoria delle azioni implicite è strettamente correlata all'intenzione dell'utente.
L'idea è che gli ologrammi o gli elementi dell'interfaccia utente reagiscono in modo istintivo che potrebbe anche non sembrare che l'utente interagisca con il sistema, ma piuttosto che il sistema e l'utente siano sincronizzati. Un esempio  è lo scorrimento automatico basato sullo sguardo oculare in cui l'utente può leggere un testo lungo, che inizia automaticamente a scorrere quando l'utente arriva alla fine della casella di testo per mantenere l'utente nel flusso di lettura, senza alzare un dito.  
Un aspetto chiave di questo è che la velocità di scorrimento si adatta alla velocità di lettura dell'utente.
Un altro esempio è **lo zoom e** la panoramica supportati dagli occhi in cui l'utente può avere l'voglia di concentrarsi esattamente su ciò su cui è concentrata. L'attivazione e il controllo della velocità di zoom possono essere controllati dall'input vocale o manuale, che è importante per fornire all'utente la possibilità di controllare senza sovraccaricare. Queste considerazioni di progettazione verranno trattate in modo più dettagliato di seguito. Una volta ingrandito, l'utente può seguire senza problemi, ad esempio, il corso di una strada per esplorare il proprio vicinato usando lo sguardo fisso.
Alcune demo di esempio per questi tipi di interazioni sono disponibili in [Mixed Reality Toolkit - Navigazione con gli occhi](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation).

Altri casi d'uso per _le azioni implicite_ possono includere:
- **Notifiche intelligenti:** Mai infastidire le notifiche che spuntano proprio nel punto in cui si sta cercando? Tenendo conto di ciò che un utente presta attenzione, è possibile migliorare questa esperienza compensando le notifiche dal punto in cui l'utente sta attualmente guardando. Ciò limita le distrazioni e le ignora automaticamente al termine della lettura da parte dell'utente. 
- **Ologrammi con attenzione: Ologrammi** reagiscono in modo subdolamente quando vengono guardati. Questo può variare da elementi dell'interfaccia utente leggermente incandescenti, un fiore che fiorisce lentamente a un cane virtuale che inizia a guardare indietro l'utente e a insaccare la coda. Questa interazione può offrire un interessante senso di connettività e soddisfazione nell'applicazione.

### <a name="attention-tracking"></a>Tracciamento dell'attenzione

Le informazioni su dove o cosa gli utenti guardano possono essere uno strumento estremamente potente. Può aiutare a valutare l'usabilità delle progettazioni e a identificare i problemi nei flussi di lavoro per renderli più efficienti.
La visualizzazione e l'analisi del tracciamento oculare sono una pratica comune in varie aree dell'applicazione. Con HoloLens 2, viene data una nuova dimensione a questa comprensione, perché gli ologrammi 3D possono essere posizionati in contesti reali e valutati di conseguenza. [L'Toolkit](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main) di realtà mista fornisce esempi di base per la registrazione e il caricamento dei dati di tracciamento oculare e come visualizzarli.
Microsoft è dedicata a facilitare l'innovazione garantendo al tempo stesso agli utenti un'esperienza informata e trasparente sull'uso delle informazioni di tracciamento oculare.  Collaboraremo con gli sviluppatori e i team dell'esperienza utente per fornire indicazioni a terze parti per garantire che le esperienze siano centrate sull'utente.  

Di seguito sono riportate altre applicazioni in questo settore: 
-   **Visualizzazione dello sguardo remoto:** Visualizzazioni dello sguardo remoto: consente di visualizzare ciò che i collaboratori remoti stanno osservando, per poter fornire commenti e suggerimenti immediati e facilitare un'elaborazione delle informazioni più accurata.
-   **Studi di ricerca degli utenti:** Il rilevamento dell'attenzione può aiutare i ricercatori a ottenere informazioni più dettagliate sul modo in cui gli utenti percepiscono e interagiscono con l'ambiente naturale, senza interferire, per progettare interazioni umane-computer più istintiva. Il tracciamento oculare può fornire informazioni non direttamente articolate dai partecipanti allo studio, che altrimenti potrebbero essere facilmente perse dal ricercatore. 
-   **Training e monitoraggio delle prestazioni:** Praticare e ottimizzare l'esecuzione delle attività identificando i colli di bottiglia in modo più efficace nel flusso di esecuzione. Il tracciamento oculare può fornire informazioni naturali, in tempo reale e oggettivi per migliorare la formazione, la produttività e la sicurezza sul posto di lavoro. 
-   **Valutazioni di progettazione, marketing e ricerca per i consumatori:** Il tracciamento oculare consente alle aziende commerciali di eseguire studi di marketing e consumer in ambienti reali o analizzare ciò che cattura l'attenzione di un utente per migliorare la progettazione di prodotti o spazi. 

### <a name="other-use-cases"></a>Altri casi d'uso

- **Giochi:** Mai desiderato avere superpoteri? Ora hai questa opportunità. È possibile levitare gli ologrammi fissandoli. Fotografare i raggi laser dagli occhi: provarlo in [RoboRaid per HoloLens 2](https://www.microsoft.com/p/roboraid/9nblggh5fv3j).
Trasformare i tuoi avversari in una roccia o congelarli. oppure usare la tua vista a raggi x per esplorare l'interno degli edifici. Insomma, con la tua immaginazione potrai superare ogni ostacolo.
Fare attenzione a non travolgere l'utente. Per altre informazioni, vedere le linee guida per la progettazione dell'input basate su sguardo [fisso.](eye-gaze-interaction.md)

- **Avatar espressivi:** Il tracciamento oculare aiuta gli avatar 3D più espressivi usando i dati di tracciamento oculare live per animare gli occhi dell'avatar che indicano ciò che l'utente sta osservando. 

- **Immissione di testo:** Il tracciamento oculare può essere usato come alternativa per l'immissione di testo a basso sforzo, soprattutto quando il parlato o le mani non sono utili. 

<br>

## <a name="using-eye-gaze-for-interaction"></a>Uso dello sguardo fisso per l'interazione

La creazione di un'interazione che sfrutta il targeting oculare in rapido movimento può essere complessa.
Da un lato, gli occhi si spostano così velocemente che è necessario prestare attenzione a come usare l'input dello sguardo fisso, perché in caso contrario gli utenti potrebbero trovare l'esperienza travolgente o distrazione. D'altra parte, è anche possibile creare esperienze magiche che ecciteranno gli utenti. Per facilitare l'interazione, vedere la panoramica dei vantaggi principali, delle sfide e delle raccomandazioni di progettazione per [l'interazione con lo sguardo visivo.](eye-gaze-interaction.md) 
 
## <a name="fallback-solutions-when-eye-tracking-isnt-available"></a>Soluzioni di fallback quando il tracciamento oculare non è disponibile

In rari casi, i dati di tracciamento oculare potrebbero non essere disponibili.
Ciò può essere dovuto a diversi motivi tra cui i più comuni sono elencati di seguito:
* Il sistema non è riuscito [a calibrare l'utente](/hololens/hololens-calibration).
* L'utente ha ignorato [la calibrazione](/hololens/hololens-calibration).   
* L'utente è calibrato, ma ha deciso di non concedere all'app l'autorizzazione per usare i dati di tracciamento oculare.    
* L'utente ha occhiali univoci o alcune condizioni oculare che il sistema non supporta ancora. 
* Fattori esterni che inibiscono il tracciamento oculare affidabile, ad esempio sbavature sulla visiera o sugli occhiali HoloLens, intensa luce solare diretta e occlusioni a causa dei peli davanti agli occhi.

Gli sviluppatori devono assicurarsi che sia presente un supporto di fallback appropriato per questi utenti. Nella pagina [Tracciamento oculare in DirectX](../develop/native/gaze-in-directx.md#fallback-when-eye-tracking-isnt-available) vengono illustrate le API necessarie per rilevare se i dati di tracciamento oculare sono disponibili. 

Anche se alcuni utenti possono aver deciso consapevolmente di revocare, l'accesso ai dati di tracciamento oculare e sono ok con il compromesso di un'esperienza utente inferiore alla privacy di non fornire l'accesso ai dati di tracciamento oculare, in alcuni casi questo potrebbe essere involontario. Se l'app usa il tracciamento oculare e questa è una parte importante dell'esperienza, è consigliabile comunicare chiaramente questo aspetto all'utente.   

Informare gentilmente l'utente perché il tracciamento oculare è fondamentale per l'applicazione (magari elencando anche alcune funzionalità avanzate) per sperimentare il potenziale completo dell'applicazione, può aiutare l'utente a comprendere meglio ciò che sta rinunciando. Aiutare l'utente a identificare il motivo per cui il tracciamento oculare potrebbe non funzionare (in base ai controlli precedenti) e offrire alcuni suggerimenti per risolvere rapidamente i potenziali problemi. 

Ad esempio, se è possibile rilevare che il sistema supporta il tracciamento oculare, l'utente è calibrato e ha anche dato l'autorizzazione, ma non vengono ricevuti dati di tracciamento oculare, potrebbe puntare ad altri problemi, ad esempio sbavature o occhi che vengono occluded. 

Esistono rari casi di utenti per i quali il tracciamento oculare potrebbe non funzionare. Di conseguenza, è necessario rispettare questo aspetto consentendo di ignorare o persino disabilitare i promemoria per abilitare il tracciamento oculare nell'app.

### <a name="fall-back-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>Eseguire il fall back per le app usando lo sguardo fisso come puntatore di input primario

Se l'app usa lo sguardo fisso come input del puntatore per selezionare rapidamente gli ologrammi sulla scena, ma i dati di tracciamento oculare non sono disponibili, è consigliabile tornare alla testa e iniziare a visualizzare il cursore con lo sguardo rivolto verso la testa. È consigliabile usare un timeout (ad esempio, 500-1500 ms) per determinare se passare o meno. Questa azione impedisce la visualizzazione dei cursori ogni volta che il sistema può perdere brevemente il rilevamento a causa di rapidi movimenti oculare o a winks e lampeggianti. Se si è uno sviluppatore unity, il fallback automatico allo sguardo alla testa è già gestito nel modello di realtà mista Toolkit. Gli sviluppatori DirectX devono gestire questa opzione manualmente.

### <a name="fall-back-for-other-eye-tracking-specific-applications"></a>Eseguire il fall back per altre applicazioni specifiche del tracciamento oculare

L'app può usare lo sguardo fisso in modo univoco, adattato in modo specifico agli occhi. Ad esempio, animando gli occhi di un avatar o per le mappe termoresche di attenzione basate sugli occhi basandosi su informazioni precise sull'attenzione visiva. In questo caso, non è presente alcun fallback chiaro. Se il tracciamento oculare non è disponibile, potrebbe essere necessario disabilitare queste funzionalità.
Anche in questo caso, è consigliabile comunicarlo chiaramente all'utente che potrebbe non essere a conoscenza del fatto che la funzionalità non funziona.

<br>

Questa pagina ha probabilmente fornito una buona panoramica per iniziare a comprendere il ruolo del tracciamento oculare e dell'input dello sguardo HoloLens 2. Per iniziare a sviluppare, vedere le informazioni sul ruolo dello sguardo fisso per interagire con [gli ologrammi,](eye-gaze-interaction.md)lo sguardo in [Unity](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main) e lo sguardo fisso [in DirectX.](../develop/native/gaze-in-directx.md)

## <a name="see-also"></a>Vedi anche

* [Calibrazione](/hololens/hololens-calibration)
* [Comodità](comfort.md)
* [Interazione basata su sguardo fisso](eye-gaze-interaction.md)
* [Sguardo fisso in DirectX](../develop/native/gaze-in-directx.md)
* [Sguardo fisso in Unity (realtà mista Toolkit)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)
* [Sguardo e commit](gaze-and-commit.md)
* [Input vocale](../out-of-scope/voice-design.md)