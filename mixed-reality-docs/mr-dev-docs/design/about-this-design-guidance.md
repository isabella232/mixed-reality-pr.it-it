---
title: Informazioni su queste linee guida per la progettazione
description: Queste linee guida sono state create da progettisti, sviluppatori, program manager e ricercatori Microsoft impegnati nella realizzazione di dispositivi olografici (come HoloLens) e dispositivi di tipo immersive (come i visori VR di Windows Mixed Reality Acer e HP).
author: mrwied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, progettazione, introduzione, linee guida, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, esperienza utente, risorse
ms.openlocfilehash: 0bd70e08d55f8d556ff3a612dbbc979dc895cebbfc9950f18d8d474ff347407b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198644"
---
# <a name="about-this-design-guidance"></a>Informazioni su queste linee guida per la progettazione

## <a name="introduction"></a>Introduzione

**Benvenuti nelle linee guida di progettazione per la realtà mista.**

Queste linee guida sono scritte da progettisti, sviluppatori, program manager e ricercatori Microsoft. Il lavoro degli autori si estende su dispositivi olografici, tra cui HoloLens, dispositivi immersive e visori VR Windows Mixed Reality HP. È consigliabile pensare a questo articolo come a un set di argomenti per Windows con head montato.

Stiamo per entrare in una nuova era di calcolo estremamente interessante insieme a te. Le innovazioni negli schermi montati con la testa, l'audio spaziale, i sensori, la consapevolezza ambientale, l'input e la grafica 3D portano a definire nuovi tipi di esperienze. La nuova frontiera è notevolmente più personale, intuitiva, immersiva e contestuale.

Laddove possibile, verranno offerte linee guida di progettazione utilizzabili con codice correlato GitHub. Detto questo, poiché microsoft sta imparando con l'utente, non sempre è possibile offrire indicazioni specifiche e utilizzabili qui. Alcuni di ciò che si condivideranno saranno nel corso delle "lezioni apprese" ed "evitare di andare lungo tale percorso".

E si sa che molte innovazioni verranno generate dalla più ampia community di progettazione. Non vediamo quindi l'ora di ascoltare l'utente, imparare da te e lavorare a stretto contatto con te. Il nostro lavoro è quello di condividere le informazioni dettagliate, anche se sono esplorativa e tempestiva. L'obiettivo è aiutare gli sviluppatori e i progettisti con il loro modo di pensare alla progettazione, le procedure consigliate e i controlli open source, i modelli e le app di esempio correlati che è possibile usare direttamente nel proprio lavoro.

## <a name="overview"></a>Panoramica

Ecco una rapida panoramica dell'organizzazione di queste linee guida per la progettazione:

* **[Panoramica:](design.md)** informazioni sul processo di progettazione, i concetti di base e i fattori di interazione da considerare.
* **[Concetti di](core-concepts-landingpage.md)** base: informazioni su comfort, cornice olografica, mapping spaziale e altri concetti di base da considerare.
* **[Modelli di interazione:](interaction-fundamentals.md)** queste linee guida sono strutturate in base a tre modelli di interazione principali.
* **[Elementi dell'esperienza utente:](app-patterns-landingpage.md)** usare controlli e comportamenti come blocchi predefiniti per creare un'esperienza dell'applicazione personalizzata.
* **[Risorse:](design.md#choose-a-prototyping-option)** consente di avviare rapidamente il progetto con strumenti di progettazione e opzioni di prototipazione.

Per tutte le informazioni precedenti, l'obiettivo è offrire la giusta combinazione di testo, illustrazioni e video. Si proverà a sperimentare con formati e tecniche diversi, il tutto con lo scopo di offrire ciò che serve. Nei prossimi mesi questa tassonomia verrà estesa in modo da includere un set più ampio di argomenti di progettazione. Ogni volta che è possibile, verrà visualizzato un messaggio di testa su ciò che verrà fatto successivamente, quindi è importante controllare di nuovo.

## <a name="objectives"></a>Obiettivi

Ecco una rapida panoramica di alcuni obiettivi di alto livello che guidano questo lavoro, in modo da poter capire da dove proviene

### <a name="help-solve-customer-challenges"></a>Aiutare a risolvere le sfide dei clienti

![Aiutare a risolvere le sfide dei clienti](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Molti degli stessi problemi che si verificano sono molto diversi e si comprende quanto sia complesso il proprio lavoro. È interessante esplorare e definire una nuova frontiera... e può anche essere ossessione. I paradigmi e le procedure precedenti vengono ritroso, i clienti necessitano di nuove esperienze e c'è così tanto potenziale per l'innovazione. Poiché si vuole che questo lavoro sia il più completo possibile, va oltre una guida di stile. L'obiettivo è offrire un set completo di linee guida per la progettazione che riguardano l'interazione con realtà mista, l'esecuzione di comandi, la navigazione, l'input e lo stile, il tutto alla base del comportamento e degli scenari umani. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Puntare la strada verso un nuovo modo di calcolo più umano

![Puntare la strada verso un nuovo modo di calcolo più umano](images/500px-man-and-women-with-holograph-on-table.png)<br>

Anche se è importante concentrarsi su problemi specifici dei clienti, è anche necessario fare il possibile per offrire altre informazioni. Microsoft ritiene che la progettazione ideale non sia "solo" la risoluzione dei problemi, ma anche un modo per attivare in modo significativo l'evoluzione umana. I nuovi modi di comportamento umano, le relazioni interpersonali, le attività e gli ambienti alimentano l'innovazione. Si vuole che le linee guida riflettano anche tutti questi modi di pensare più abili. 

### <a name="meet-creators-where-they-are"></a>Conoscere i creatori dove si trova

![Conoscere i creatori dove si trova](images/500px-creators.jpg) <br>

Ci auguriamo che molti destinatari trovino queste linee guida utili. Si hanno set di competenze diversi (a partire da, intermedio, avanzato), si usano diversi strumenti (Unity, DirectX, C++, C#, altro), si ha familiarità con varie piattaforme (Windows, iOS, Android), provengono da background diversi (dispositivi mobili, aziendali, giochi) e lavorano su team di dimensioni diverse (solo, piccole, medie, grandi). Queste linee guida possono quindi essere visualizzate con prospettive e esigenze diverse. Quando possibile, si tenterà di tenere presente questa diversità e di rendere le linee guida il più rilevanti possibile per il maggior numero possibile di persone. Molti utenti sono già in GitHub. Quindi, verrà fatto direttamente un collegamento GitHub repository e forum per conoscere la posizione in cui ci si trova già. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>Condividere il più possibile, da sperimentale ad esplicito

![Condividere il più possibile, da sperimentale ad esplicito](images/500px-man-playinggame.jpg) <br>

Una delle sfide dell'offerta di linee guida per la progettazione in questo nuovo supporto 3D è che non sempre sono disponibili indicazioni definitive da offrire. Proprio come te, stiamo imparando, sperimentando, prototipando, risolvendo i problemi e modificando man appena si verificano problemi. Invece di attendere un momento futuro mitico quando tutto è stato risolto, l'obiettivo è condividere il nostro modo di pensare con l'utente in tempo reale, anche se non è definitivo. L'obiettivo finale è quello di essere definitivi ovunque sia possibile, fornendo linee guida di progettazione chiare e flessibili legate al codice open source e utilizzabili negli strumenti di sviluppo e progettazione Microsoft. Tuttavia, per raggiungere questo punto sono necessari molti cicli di iterazione e apprendimento. Microsoft vuole interagire con l'utente e imparare a interagire con l'utente durante il processo. Si proverà a condividere le informazioni man via, anche con le funzionalità sperimentali. 

### <a name="the-right-balance-of-global-and-local-design"></a>Il giusto equilibrio tra progettazione globale e locale

![Il giusto equilibrio tra progettazione globale e locale](images/500px-fluentdesign.jpg) <br>

Verranno offerti due livelli di linee guida per la progettazione: globale e locale. Le linee guida di progettazione "globali" sono incluse nel [Fluent Design System](https://fluent.microsoft.com). Fluent informazioni dettagliate su concetti fondamentali come luce, profondità, movimento, materiale e scalabilità in tutta la progettazione Microsoft, ad esempio dispositivi, prodotti, strumenti e servizi. Ciò detto, esistono differenze significative specifiche del dispositivo in questo sistema più grande. Quindi, le linee guida di progettazione "locali" per i display montati con la testa descrivono la progettazione per dispositivi olografici e immersive che spesso hanno metodi di input e output diversi e esigenze e scenari diversi per gli utenti. Le linee guida per la progettazione locale trattano argomenti specifici dei HMD. Ad esempio: ambienti e oggetti 3D; ambienti condivisi; l'uso di sensori, tracciamento oculare e mapping spaziale; e le opportunità dell'audio spaziale. In tutte le linee guida verrà probabilmente fatto riferimento a questi aspetti globali e locali. Ci auguriamo che questo possa aiutare a fondo il lavoro su una base di progettazione più ampia, sfruttando al tempo stesso le differenze di progettazione tra dispositivi specifici.

### <a name="have-a-discussion"></a>Discussione

![Discussione](images/500px-share.jpg) <br>

L'aspetto più importante è che l'utente, la community di progettisti e sviluppatori olografici e immersive, voglia definire questa nuova e interessante era di progettazione. Come accennato in precedenza, è possibile sapere che non sono disponibili tutte le risposte. Questo è il motivo per cui si ritiene che molte interessanti soluzioni e innovazioni verranno da te. L'obiettivo è essere aperti e disponibili per essere a loro disposizione, discutere con l'utente online e in eventi e aggiungere valore ovunque sia possibile. Siamo molto contenti di far parte di questa straordinaria community di progettazione, che si avvia insieme a un'adventure. 

## <a name="dive-in"></a>Approfondimento

Ci auguriamo che questo articolo introduttivo fornisce un contesto significativo durante l'esplorazione delle linee guida per la progettazione. Approfondire e invii commenti e idee nei forum GitHub che sono disponibili negli articoli o in Microsoft Design su [Twitter](https://twitter.com/MicrosoftDesign) e [Facebook.](https://www.facebook.com/microsoftdesign/) È possibile progettare insieme il futuro.
