---
title: Frame olografico
description: Informazioni su come gli utenti vedono il mondo della realtà mista tramite il frame olografico e come progettare al meglio l'esperienza.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/25/2020
ms.topic: article
keywords: HoloLens, Windows Mixed Reality, frame olografico, campo di visualizzazione, FOV, visore per realtà mista, visore windows mixed reality, visore di realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit, interazioni, navigazione, menu
ms.openlocfilehash: 5edab22751b9f2196f02a500279c4de385b57b5d
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196556"
---
# <a name="holographic-frame"></a>Frame olografico

Gli utenti vedono il mondo della realtà mista attraverso un riquadro di visualizzazione rettangolare controllato tramite il visore VR. In HoloLens quest'area rettangolare è detta frame olografico e consente agli utenti di visualizzare il contenuto digitale sovrapposto al mondo reale circostante. La progettazione di esperienze ottimizzate per il frame olografico crea opportunità, mitiga le sfide e migliora l'esperienza utente delle applicazioni di realtà mista.

## <a name="designing-for-content"></a>Progettazione per il contenuto

Spesso i progettisti sentono la necessità di limitare l'ambito della propria esperienza a ciò che l'utente può vedere immediatamente, sacrificando la scalabilità reale per garantire che l'utente veda un oggetto nella sua interezza. Analogamente, le finestre di progettazione con applicazioni complesse spesso sovraccaricano il frame olografico con contenuto, sovraccarico degli utenti con interazioni difficili e interfacce ingombranti. I progettisti che creano contenuto di realtà mista non devono limitare l'esperienza a direttamente davanti all'utente e all'interno della visualizzazione immediata. Se viene eseguito il mapping del mondo fisico intorno all'utente, tutte queste superfici devono essere considerate un potenziale canvas per il contenuto digitale e le interazioni. Una corretta progettazione delle interazioni e dei contenuti all'interno di un'esperienza deve invitare l'utente a spostarsi nel proprio spazio, indirizzando l'attenzione sui contenuti chiave e consentendo di vedere il potenziale completo della realtà mista.

Forse la tecnica più importante per favorire lo spostamento e l'esplorazione all'interno di un'app consiste nel consentire agli **utenti di adattarsi all'esperienza**. Concedere agli utenti un breve periodo di tempo "senza attività" con il dispositivo. Questo può essere semplice come posizionare un oggetto nello spazio e consentire agli utenti di spostarsi all'esterno o di raccontare un'introduzione all'esperienza. Questo tempo deve essere privo di attività critiche o movimenti specifici, ad esempio il tocco in aria. Lo scopo è consentire agli utenti di visualizzare il contenuto tramite il dispositivo prima di richiedere interattività o procedere con l'app. Ciò è particolarmente importante per gli utenti che hanno familiarità con la visualizzazione del contenuto attraverso la cornice olografica e la natura degli ologrammi.

### <a name="large-objects"></a>Oggetti di grandi dimensioni

Spesso il contenuto che un'esperienza richiede, in particolare il contenuto reale, sarà più grande del frame olografico. Gli oggetti che normalmente non possono rientrare nel frame olografico devono essere ridotti per adattarsi alla prima introduzione (su scala più piccola o a distanza). La chiave è consentire **agli utenti di visualizzare le dimensioni complete dell'oggetto** prima che la scala sovraccarici il frame. Ad esempio, deve essere visualizzato un elemento olografico per adattarsi completamente all'interno del fotogramma. In questo modo gli utenti possono ottenere una comprensione spaziale della forma complessiva dell'animale, prima di ridimensionarla in scala reale [vicino](scale.md) all'utente.

Con le dimensioni complete dell'oggetto, gli utenti hanno l'aspettativa di dove spostarsi e cercare parti specifiche di tale oggetto. In un'esperienza con contenuto immersivo, è utile avere un modo per fare riferimento alle dimensioni complete di tale contenuto. Ad esempio, se l'esperienza implica la descrizione di un modello di una casa virtuale, è utile avere una versione più piccola dell'esperienza per individuare dove si trova all'interno della casa.

Per un esempio di progettazione per oggetti di grandi dimensioni, [vedere Automobili Automobili automobili.](holographic-frame.md#volvo-cars)

### <a name="many-objects"></a>Molti oggetti

Le esperienze con molti oggetti o componenti devono considerare l'uso dello spazio completo intorno all'utente per evitare confusione nella cornice olografica direttamente davanti all'utente. È consigliabile rallentare l'introduzione del contenuto a un'esperienza, soprattutto con esperienze che pianificano la distribuzione di molti oggetti all'utente. La chiave è consentire **agli utenti** di comprendere il layout del contenuto nell'esperienza, che consente di acquisire una comprensione spaziale degli elementi che li circondano durante l'aggiornamento del contenuto.

Una tecnica per ottenere questo risultato consiste nel fornire punti persistenti (noti anche come punti di riferimento) nell'esperienza che ancora il contenuto al mondo reale. Ad esempio, un punto di riferimento può essere un oggetto fisico nel mondo reale, ad esempio una tabella in cui viene visualizzato il contenuto digitale, o un oggetto digitale, ad esempio un set di schermate digitali in cui il contenuto viene visualizzato di frequente. Gli oggetti possono anche essere posizionati nella periferia del frame olografico per invitare l'utente a cercare il contenuto chiave. L'individuazione del contenuto oltre la periferia può essere aiutata dai responsabili [dell'attenzione.](holographic-frame.md#attention-directors)

L'inserimento di oggetti nella periferia può invitare gli utenti a guardare al lato e ciò può essere aiutato dai responsabili dell'attenzione, come descritto di seguito. Per altre informazioni sulle considerazioni sui frame olografici, vedere la documentazione [relativa al comfort.](comfort.md#holographic-frame-considerations)

<br>

---

## <a name="interaction-considerations"></a>Considerazioni sull'interazione

Come per il contenuto, le interazioni in un'esperienza di realtà mista non devono essere limitate a ciò che l'utente può visualizzare immediatamente. Le interazioni possono avere luogo ovunque nello spazio reale intorno all'utente. Queste interazioni possono aiutare gli utenti a spostarsi ed esplorare le esperienze.

### <a name="attention-directors"></a>Responsabili dell'attenzione

L'indicazione dei punti di interesse o delle interazioni chiave può essere fondamentale per l'avanzamento degli utenti attraverso un'esperienza. L'attenzione dell'utente e il movimento della cornice olografica possono essere indirizzati in modi sottili o pesanti. Ricordarsi di bilanciare i responsabili dell'attenzione con i periodi di esplorazione gratuita nella realtà mista (soprattutto all'inizio di un'esperienza) per evitare di travolgente l'utente. In generale, esistono due tipi di responsabili dell'attenzione:
* **Amministratori visivi:** Il modo più semplice per indicare all'utente che deve spostarsi in una direzione specifica è fornire un'indicazione visiva. Questa operazione può essere eseguita tramite un effetto visivo (ad esempio, un percorso che l'utente può seguire visivamente verso la parte successiva dell'esperienza) o anche come semplici frecce direzionali. Qualsiasi indicatore visivo deve essere posizionato all'interno dell'ambiente dell'utente, non "collegato" al frame olografico o al cursore.
* **Audio director:** [il suono](spatial-sound-design.md) spaziale può fornire un modo efficace per stabilire gli oggetti in una scena. È possibile avvisare gli utenti in caso di oggetti che entrano in un'esperienza o indirizzare l'attenzione su un punto specifico nello spazio spostando la visualizzazione dell'utente verso gli oggetti chiave. L'uso dell'audio per guidare l'attenzione dell'utente può essere più sottile e meno intrusivo rispetto all'attenzione visiva. In alcuni casi, può essere meglio iniziare con un audio director e quindi passare a un direttore visivo se l'utente non riconosce il segnale. È anche possibile associare audio a elementi visivi per un'enfasi maggiore.

### <a name="commanding-navigation-and-menus"></a>Esecuzione di comandi, navigazione e menu

Le interfacce nelle esperienze di realtà mista idealmente sono strettamente associate al contenuto digitale che controllano. Di conseguenza, i menu 2D a virgola mobile libero spesso non sono ideali per l'interazione e possono essere difficili per gli utenti che si trovano troppo comodamente all'interno della cornice olografica. Per le esperienze che richiedono elementi di interfaccia, ad esempio menu o campi di testo, è consigliabile usare un metodo [tag-along](billboarding-and-tag-along.md) per seguire il frame olografico dopo un breve ritardo. Evitare di bloccare il contenuto della cornice come una visualizzazione a testa in su, perché ciò può disorientare l'utente e interrompere il senso diorientamento per altri oggetti digitali nella scena.

È anche possibile posizionare gli elementi dell'interfaccia direttamente sul contenuto specifico che controllano, consentendo interazioni naturali intorno allo spazio fisico dell'utente. Ad esempio, suddividere un menu complesso in parti separate, con ogni pulsante o gruppo di controlli associato all'oggetto specifico su cui influisce l'interazione. Per approfondire questo concetto, prendere in considerazione l'uso di [oggetti che possono interagire.](interactable-object.md)

### <a name="gaze-and-gaze-targeting"></a>Targeting sguardo fisso e sguardo fisso

La cornice olografica presenta uno strumento che consente allo sviluppatore di attivare le interazioni e valutare dove si trova l'attenzione dell'utente. [Lo](gaze-and-commit.md) sguardo fisso è una delle interazioni principali in [HoloLens,](interaction-fundamentals.md)in cui lo sguardo può essere associato a movimenti [(ad](gaze-and-commit.md#composite-gestures) esempio con tocco d'aria) o alla voce [(consentendo](voice-input.md) interazioni più brevi e più naturali basate sulla voce). Di conseguenza, questo rende il fotogramma olografico uno spazio per l'osservazione del contenuto digitale e l'interazione con esso. Se l'esperienza richiede l'interazione con più oggetti intorno allo spazio dell'utente (ad esempio, la selezione multipla di oggetti intorno allo spazio dell'utente con sguardo e movimento), è consigliabile portare tali oggetti nella visualizzazione dell'utente o limitare la quantità di spostamento della testa necessaria per promuovere il [comfort dell'utente.](comfort.md)

È anche possibile usare lo sguardo fisso per tenere traccia dell'attenzione dell'utente tramite un'esperienza e vedere a quali oggetti o parti della scena l'utente ha prestato maggiore attenzione. Questo può essere particolarmente utile per il debug di un'esperienza, consentendo agli strumenti analitici come le mappe termoreche di vedere dove gli utenti spendono la maggior parte del tempo o mancano determinati oggetti o interazioni. Il rilevamento dello sguardo può anche fornire un potente strumento per facilitatori nelle esperienze (vedere [l'esempio di Lowe's Kitchen).](holographic-frame.md#lowes-kitchen)

Se si desidera vedere i concetti di progettazione di Head and Eye Tracking in azione, vedere la demo video Designing Holograms - Head Tracking and Eye Tracking (Progettazione di **ologrammi - Tracciamento** testina e tracciamento oculare) di seguito:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Questo video è stato tratto dall'app "Designing Holograms" (Progettazione di ologrammi) HoloLens 2 app. Scaricare e usufruire dell'esperienza completa [qui.](https://aka.ms/dhapp)*

<br>

---

## <a name="performance"></a>Prestazioni

L'uso corretto del frame olografico è fondamentale per le esperienze [di qualità delle](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) prestazioni. Una comune sfida tecnica (e usabilità) è l'overload del frame dell'utente con contenuto digitale, causando una riduzione delle prestazioni di rendering. È consigliabile usare invece lo spazio completo intorno all'utente per disporre il contenuto digitale, usando le tecniche descritte in precedenza, per ridurre il carico di rendering e garantire una qualità di visualizzazione ottimale.

Il contenuto digitale all'interno della cornice olografica di HoloLens può anche essere associato al piano di [stabilizzazione](../develop/platform-capabilities-and-apis/case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md) per ottenere prestazioni ottimali e [stabilità dell'ologramma.](../develop/platform-capabilities-and-apis/hologram-stability.md)

<br>

---

## <a name="examples"></a>Esempio

### <a name="volvo-cars"></a>Automobili Di Automobili Di Lusso

<iframe width="940" height="530" src="https://www.youtube.com/embed/DilzwF90vec" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Nell'esperienza di showroom di Automobili Di automobili, i clienti sono invitati a conoscere le funzionalità di una nuova auto in un'esperienza HoloLens guidata da un associato Diocesi. Il modello olografico di Un'auto di dimensioni complete è troppo grande per essere messa accanto a un utente. La soluzione consisteva nell'iniziare l'esperienza con un punto di riferimento fisico, un tavolo centrale nello showroom, con un modello digitale più piccolo dell'auto posizionato sopra il tavolo. Ciò garantisce che l'utente veda l'auto completa quando viene introdotta, consentendo un senso di comprensione spaziale quando l'auto cresce fino alla scala reale in un secondo momento nell'esperienza.

L'esperienza di Dio usa anche la confetto visivo, creando un effetto visivo lungo dal modello di auto su scala ridotta sul tavolo a una barriera nello show room. Ciò comporta un effetto "finestra magica", che mostra la visualizzazione completa dell'auto a distanza, illustrando altre caratteristiche dell'auto su scala reale. Il movimento della testa è orizzontale, senza alcuna interazione diretta da parte dell'utente ,raccogliendo invece segnali visivamente e dalla narrazione dell'esperienza da parte dell'associato Dia.

<br>

---

### <a name="lowes-kitchen"></a>Lowe's Kitchen

Un'esperienza di store di Lowe invita i clienti a un mockup su larga scala di una cucina per presentare diverse opportunità di rimodellamento, come si può vedere tramite HoloLens. La cucina nel negozio offre un ambiente fisico per gli oggetti digitali, un'area di disegno vuota di elettrodomestici, controsoffitti e mobili per l'esperienza di realtà mista da dispiegare.

Le superfici fisiche fungono da punti di riferimento statici in modo che l'utente si basi nell'esperienza, in quanto un associato di Lowe guida l'utente attraverso diverse opzioni di prodotto e termina. In questo modo, l'associato può indirizzare verbalmente l'attenzione dell'utente al "refrigeratore" o al "centro della cucina" per presentare il contenuto digitale.

![Un associato di Lowe usa un tablet per guidare i clienti nell'esperienza HoloLens.](images/loweskitchen-750px.jpg)<br>
*Un associato di Lowe usa un tablet per guidare i clienti nell'esperienza HoloLens.*

L'esperienza dell'utente è in parte gestita da un'esperienza di tablet controllata dall'associato di Lowe. Parte del ruolo dell'associato in questo caso sarebbe anche limitare il movimento eccessivo della testa, indirizzando l'attenzione senza problemi tra i punti di interesse nella cucina. L'esperienza del tablet fornisce anche l'associazione di Lowe ai dati dello sguardo fisso sotto forma di una visualizzazione mappa termica della cucina, consentendo di comprendere dove si trova l'utente (ad esempio, in una specifica area dell'armadio) per fornire loro linee guida per la ristrutturazione in modo più accurato.

Per un'analisi più approfondita dell'esperienza di Lowe's Kitchen, vedere la nota chiave di [Microsoft in Ignite 2016.](https://www.youtube.com/watch?v=gC_4JxF0e_k)

<br>

---

### <a name="fragments"></a>Frammenti

Nel gioco Fragments di HoloLens, il tuo living si trasforma in scena del delitto virtuale che mostra indizi ed prove e in una sala riunioni virtuale, in cui si parla con i personaggi che siedono sulle sedie e si appoggino sulle pareti.

![I frammenti sono stati progettati per l'esecuzione nella casa di un utente, con i caratteri che interagiscono con oggetti e superfici reali.](images/fragments-750px.jpg)<br>
*I frammenti sono stati progettati per l'esecuzione nella casa di un utente, con i caratteri che interagiscono con oggetti e superfici reali.*

Quando gli utenti iniziano inizialmente l'esperienza, viene assegnato loro un breve periodo di regolazione senza alcuna interazione. Sono invece invitati a guardarsi attorno e orientarsi e a garantire che la stanza sia mappata correttamente per il contenuto interattivo del gioco.

Nel corso dell'esperienza, i caratteri diventano punti focali e fungono da amministratori visivi (movimenti della testa tra i caratteri, voltando per guardare o movimenti verso le aree di interesse). Il gioco si basa anche su segnali visivi più importanti quando un utente impiega troppo tempo per trovare un oggetto o un evento e usa molto l'audio spaziale (in particolare con le voci dei caratteri quando entra in una scena).

<br>

---

### <a name="destination-mars"></a>Destinazione: Mars

Nell'esperienza Destination: Mars in primo piano nel Centro spaziale [Della Nasa,](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/)i visitatori sono stati invitati in un viaggio immersivo sulla superficie di Marte, guidato dalla rappresentazione virtuale del celebre astronauta Rondrin.

![Un Ronzio Virtuale Aldrin diventa il punto focale per gli utenti in Destinazione: Mars.](images/destinationmars-750px.png)<br>
*Un Ronzio Virtuale Aldrin diventa il punto focale per gli utenti in Destinazione: Mars.*

Come esperienza immersiva, questi utenti sono stati invitati a guardarsi attorno, spostando la testa in tutte le direzioni per vedere il panorama martiano virtuale. Anche se per garantire il comfort degli utenti, la narrazione e la presenza virtuale di Aldrin hanno fornito un punto focale per tutta l'esperienza. Questa registrazione virtuale di Acustica (creata da Microsoft Acquisizione realtà mista Studios) ha una dimensione reale e umana, [nell'angolo](https://www.microsoft.com/mixed-reality/capture-studios)della stanza, consentendo agli utenti di visualizzarlo in una visualizzazione quasi completa. La narrazione di Mediation ha indirizzato gli utenti a concentrarsi su diversi punti dell'ambiente (ad esempio, un set di rocce martiane sul terreno o un'area montana in distanza) con modifiche o oggetti specifici della scena introdotti da lui.

![Gli assistente vocale virtuali seguiranno il movimento dell'utente, creando un punto focale potente in tutta l'esperienza.](images/gazereset-750px.png)<br>
*Gli assistente vocale virtuali seguiranno il movimento dell'utente, creando un punto focale potente in tutta l'esperienza.*

La rappresentazione realistica di Acustica ha fornito un punto focale potente, completo di tecniche sottintese per fare in modo che l'utente si senta come se fosse presente, pronunciando con te. Man mano che l'utente si sposta sull'esperienza, l'utente passa a una soglia prima di tornare a uno stato neutro se l'utente si sposta troppo oltre la sua periferia. Se l'utente guarda completamente da Senta (ad esempio, per esaminare un elemento altrove nella scena) e quindi torna a Acustica, la posizione direzionale dell'assistente vocale sarà ancora una volta incentrata sull'utente. Tecniche come questa offrono un potente senso di potere e creano un punto focale all'interno della cornice olografica, riducendo il movimento eccessivo della testa e promuovendo il [comfort dell'utente.](comfort.md)

## <a name="see-also"></a>Vedi anche
* [Interazioni istintive](interaction-fundamentals.md)
* [Comodità](comfort.md)
* [Scalabilità](scale.md)
* [Puntamento con la testa e attesa](gaze-and-dwell.md)
* [Stabilità degli ologrammi](../develop/platform-capabilities-and-apis/hologram-stability.md)
