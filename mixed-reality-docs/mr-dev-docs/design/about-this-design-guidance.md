---
title: Informazioni su queste linee guida per la progettazione
description: Queste linee guida sono state create da progettisti, sviluppatori, program manager e ricercatori Microsoft impegnati nella realizzazione di dispositivi olografici (come HoloLens) e dispositivi di tipo immersive (come i visori VR di Windows Mixed Reality Acer e HP).
author: mrwied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, introduzione, guida, cuffie per realtà mista, auricolare di realtà mista di Windows, auricolare di realtà virtuale, UX, risorse
ms.openlocfilehash: f731ad91d48cdb50ad12b6a9cc250b6561eebaff
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847696"
---
# <a name="about-this-design-guidance"></a>Informazioni su queste linee guida per la progettazione

## <a name="introduction"></a>Introduzione

**Salve e Benvenuti alle linee guida di progettazione per la realtà mista.**

Questa guida è stata scritta da Microsoft designer, sviluppatori, Program Manager e ricercatori. Il lavoro dei nostri writer è esteso a dispositivi olografici, tra cui HoloLens, dispositivi immersivi, andAcer e auricolari per la realtà mista di HP Windows. Si consiglia di considerare questo articolo come un set di argomenti per la progettazione montata con Windows Head.

Stiamo immettendo una nuova ed entusiasmante esperienza di calcolo. Le scoperte negli schermi montati, i suoni spaziali, i sensori, la consapevolezza ambientale, l'input e la grafica 3D portano a definire nuovi tipi di esperienze. La nuova frontiera è notevolmente più personale, intuitiva, immersiva e contestuale.

Laddove possibile, offriamo indicazioni di progettazione di utilità pratica con il codice correlato in GitHub. Ciò premesso, dal momento che si sta imparando insieme a te, non possiamo sempre offrire indicazioni specifiche e fruibili. Una parte di ciò che condividiamo si troverà nello spirito di "lezioni apprese" ed evitando di incorrere in tale percorso.

E sappiamo che molte innovazioni saranno generate dalla più ampia community di progettazione. Quindi, siamo lieti di ricevere notizie da te, imparando da te e lavorando a stretto contatto con te. Il nostro meglio per condividere le nostre informazioni, anche se sono esplorative e anticipate. Il nostro obiettivo è aiutare gli sviluppatori e i progettisti a progettare, procedure consigliate, procedure consigliate e controlli, modelli e app di esempio correlati, che puoi usare direttamente nel tuo lavoro.

## <a name="overview"></a>Panoramica

Ecco una rapida panoramica del modo in cui sono organizzate le linee guida di progettazione:

* **[Panoramica](design.md)** : informazioni sul processo di progettazione, i concetti di base e i fattori di interazione da considerare.
* **[Concetti di base](core-concepts-landingpage.md)** : informazioni su comfort, frame olografico, mapping spaziale e altri concetti di base da considerare.
* **[Modelli di interazione](interaction-fundamentals.md)** : questa guida è strutturata intorno a tre modelli di interazione principali.
* **[Elementi UX](app-patterns-landingpage.md)** : usare controlli e comportamenti come blocchi predefiniti per creare un'esperienza di applicazione personalizzata.
* **[Risorse](design.md#choose-a-prototyping-option)** : avviare il progetto con strumenti di progettazione e opzioni di creazione di prototipi.

Per tutte le versioni precedenti, si intende fornire la corretta combinazione di testo, illustrazioni e video. Ci consentirà di sperimentare diversi formati e tecniche, con lo scopo di ottenere gli elementi necessari. E nei prossimi mesi, la tassonomia verrà espansa per includere un set più ampio di argomenti di progettazione. Quando possibile, verranno fornite le informazioni relative a ciò che verrà visualizzato successivamente.

## <a name="objectives"></a>Obiettivi

Ecco una rapida panoramica di alcuni obiettivi di alto livello che guidano questo lavoro per poter capire da dove provengono

### <a name="help-solve-customer-challenges"></a>Contribuire alla risoluzione delle esigenze dei clienti

![Contribuire alla risoluzione delle esigenze dei clienti](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Si affrontano molti degli stessi problemi che è possibile eseguire e si comprende il modo in cui il lavoro è complesso. È entusiasmante esplorare e definire una nuova frontiera... e può anche essere scoraggiante. I paradigmi e le pratiche precedenti sono stati ripensati, i clienti hanno bisogno di nuove esperienze e sono molto potenziali per l'innovazione. Poiché si vuole che il lavoro sia il più completo possibile, andare oltre una guida di stile. Miriamo a offrire un set completo di linee guida per la progettazione che riguardano interazione tra realtà mista, comandi, navigazione, input e stile, il tutto in scenari e comportamenti umani. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Puntare a una nuova modalità di calcolo più umana

![Puntare a una nuova modalità di calcolo più umana](images/500px-man-and-women-with-holograph-on-table.png)<br>

Sebbene sia importante concentrarsi sui problemi specifici dei clienti, è anche possibile effettuare il push per offrire altro. Ci riteniamo che la progettazione eccezionale non sia "solo" la risoluzione dei problemi, ma anche un modo per attivare in modo significativo l'evoluzione umana. Nuove modalità di comportamento umano, relazioni interpersonali, attività e ambienti alimentano l'innovazione. Si vuole che le linee guida riflettano tutti questi modi più ambiziosi. 

### <a name="meet-creators-where-they-are"></a>Scopri i creatori in cui sono

![Scopri i creatori in cui sono](images/500px-creators.jpg) <br>

Ci auguriamo che molti destinatari trovino questa guida per essere utile. Sono disponibili diversi skillsets (inizio, intermedio, avanzato), usare diversi strumenti (Unity, DirectX, C++, C#, other), che hanno familiarità con le varie piattaforme (Windows, iOS, Android), derivano da diversi sfondi (per dispositivi mobili, aziendali e di gioco) e lavorano su team di dimensioni diverse (solo, piccolo, medio, grande). Questo materiale sussidiario può quindi essere visualizzato con diverse prospettive e esigenze. Quando possibile, si proverà a tenere presente questa diversità e si renderà le indicazioni più rilevanti possibile per il maggior numero di persone possibile. Sappiamo che molti di voi sono già in GitHub. Quindi, ci concentreremo direttamente sui repository GitHub e sui forum che ti consentiranno di ottenere le tue esigenze. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>Condividi quanto più possibile, da sperimentale a esplicita

![Condividi quanto più possibile, da sperimentale a esplicita](images/500px-man-playinggame.jpg) <br>

Una delle implicazioni dell'offerta di linee guida di progettazione in questo nuovo supporto 3D è che non è sempre disponibile una guida definitiva da offrire. Proprio come te, stiamo imparando, sperimentando, eseguendo prototipi, risolvendo problemi e modificando gli ostacoli che abbiamo raggiunto. Invece di attendere qualche momento futuro, quando abbiamo capito tutto, vogliamo condividere il nostro pensiero in tempo reale, anche se non è conclusivo. Il nostro obiettivo finale è quello di essere definitivo ovunque possiamo, fornendo linee guida di progettazione chiare e flessibili associate a codice open source e interoperabile negli strumenti di sviluppo e progettazione Microsoft. Tuttavia, raggiungere questo punto richiede molti cicli di iterazione e apprendimento. Si vuole interagire con l'utente e acquisire familiarità con l'utente. La nostra soluzione migliore è quella di condividere il nostro lavoro, anche con le nostre cose sperimentali. 

### <a name="the-right-balance-of-global-and-local-design"></a>Il giusto equilibrio tra progettazione globale e locale

![Il giusto equilibrio tra progettazione globale e locale](images/500px-fluentdesign.jpg) <br>

Offriamo due livelli di linee guida per la progettazione: globale e locale. Le linee guida di progettazione "globali" sono incluse nel [sistema di progettazione Fluent](https://fluent.microsoft.com). Informazioni dettagliate sul modo in cui consideriamo i concetti di base quali luce, profondità, movimento, materiale e scalabilità in tutta la progettazione Microsoft, ovvero dispositivi, prodotti, strumenti e servizi. Detto ciò, esistono differenze significative specifiche del dispositivo in questo sistema più ampio. Quindi, le linee guida di progettazione "locale" per gli schermi montati illustrano la progettazione di dispositivi olografici e immersivi che spesso hanno metodi di input e output diversi e scenari e esigenze utente differenti. Le linee guida sulla progettazione locale riguardano argomenti specifici di HMDs. Ad esempio: ambienti e oggetti 3D; ambienti condivisi; l'uso di sensori, monitoraggio degli occhi e mapping spaziale; e le opportunità di audio spaziale. Per tutte le linee guida, è probabile che ci si riferisca a questi aspetti globali e locali. Speriamo che ciò consentirà di basare il lavoro in una base di progettazione più ampia sfruttando al contempo le differenze di progettazione tra dispositivi specifici.

### <a name="have-a-discussion"></a>Discussione

![Discussione](images/500px-share.jpg) <br>

Soprattutto, desideriamo coinvolgere l'utente, la community di sviluppatori e progettisti olografici e coinvolgenti, per definire questa nuova era interessante di progettazione. Come indicato in precedenza, sappiamo che non sono disponibili tutte le risposte. Questo è il motivo per cui si ritiene che si ritengano molte interessanti soluzioni e innovazioni. L'obiettivo è quello di essere aperti e disponibili per ascoltarli, discutere con l'utente online e gli eventi e aggiungere valore ovunque sia possibile. Siamo entusiasti di essere parte integrante di questa straordinaria community di progettazione, che è stata affrontata insieme a un'avventura. 

## <a name="dive-in"></a>Approfondimenti

Ci auguriamo che questo articolo introduttivo fornisca un contesto significativo durante l'esplorazione delle linee guida di progettazione. Scopri le tue opinioni nei forum di GitHub che troverai nei nostri articoli oppure in Microsoft Design su [Twitter](https://twitter.com/MicrosoftDesign) e [Facebook](https://www.facebook.com/microsoftdesign/). È ora di co-progettare il futuro insieme.
