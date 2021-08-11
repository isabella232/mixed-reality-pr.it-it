---
title: Esperienze condivise nella realtà mista
description: Le app olografiche possono condividere ancoraggi nello spazio da un HoloLens a un altro, consentendo agli utenti di eseguire il rendering di un ologramma nella stessa posizione del mondo reale, su più dispositivi.
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: esperienza condivisa, realtà mista, ologramma, ancoraggio nello spazio, multi-utente, più
ms.openlocfilehash: fe738d07e57bd2f62cab8036a09ca6ab31d6544bdd9b6dacc8dde3445fa58214
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193591"
---
# <a name="shared-experiences-in-mixed-reality"></a>Esperienze condivise nella realtà mista

Ologrammi non è necessario rimanere privati per un solo utente. Le app olografiche possono condividere ancoraggi nello spazio da un dispositivo HoloLens, iOS o Android a un altro, consentendo agli utenti di eseguire il rendering di un ologramma nella stessa posizione nel mondo reale tra più dispositivi. [](../../design/spatial-anchors.md)

## <a name="six-questions-to-define-shared-scenarios"></a>Sei domande per definire scenari condivisi

Prima di iniziare la progettazione per le esperienze condivise, è importante definire gli scenari di destinazione. Questi scenari consentono di chiarire ciò che si sta progettando e di stabilire un vocabolario comune per confrontare e contrapporre le funzionalità necessarie nell'esperienza. Comprendere il problema principale e i diversi modi per trovare soluzioni è fondamentale per scoprire opportunità inerenti a questo nuovo supporto.

Tramite prototipi interni ed esplorazioni delle HoloLens partner, abbiamo creato sei domande per facilitare la definizione di scenari condivisi. Queste domande formano un framework, non destinato a essere esaustivo, per contribuire a estrarre gli attributi importanti degli scenari.

### <a name="1-how-are-they-sharing"></a>1. In che modo condividono?

Una presentazione può essere guidata da un singolo utente virtuale, mentre più utenti possono collaborare o un docente può fornire indicazioni agli studenti virtuali che lavorano con materiali virtuali. La complessità delle esperienze aumenta in base al livello di agenzia che un utente ha o può avere in uno scenario.

![Man and women with holograph on table](images/man-and-women-with-holograph-on-table-500px.png)

Esistono molti modi per condividere, ma è stato rilevato che la maggior parte di essi rientra in tre categorie:

* **Presentazione:** quando lo stesso contenuto viene visualizzato a più utenti. Ad esempio: un insegnante sta offrendo una lezione a diversi studenti usando lo stesso materiale olografico presentato a tutti. Il insegnante, tuttavia, potrebbe avere i propri suggerimenti e note che potrebbero non essere visibili ad altri.
* **Collaborazione:** quando le persone lavorano insieme per raggiungere alcuni obiettivi comuni. Ad esempio: il docente ha dato un progetto per imparare a fare un attacco di memoria. Gli studenti si associano e creano un'esperienza di lab con competenze condivise, che consente agli studenti medici di collaborare al modello di apprendimento del cuore.
* **Indicazioni:** quando una persona aiuta a risolvere un problema in un'interazione più uno-a-uno. Ad esempio: il docente che fornisce indicazioni a uno studente quando sta eseguendo il lab per le competenze relative alle competenze di assistenza al cervello nell'esperienza condivisa.

### <a name="2-what-is-the-group-size"></a>2. Quali sono le dimensioni del gruppo?

**Le esperienze di condivisione uno-a-uno** possono fornire una baseline solida e idealmente è possibile creare i propri criteri di verifica a questo livello. Tenere tuttavia presente che la condivisione con gruppi di grandi dimensioni (oltre sei persone) può causare difficoltà sia tecniche (dati e rete) che social (l'impatto di essere in una stanza con diversi [avatar).](https://vimeo.com/160704056) La complessità aumenta in modo esponenziale quando si passa da **gruppi piccoli** a gruppi di **grandi dimensioni.**

È stato rilevato che le esigenze dei gruppi possono essere suddivise in tre categorie di dimensioni:
* 1:1
* Small < 7
* Large >= 7

La dimensione del gruppo costituisce una domanda importante perché influisce su:

* Rappresentazioni di persone nello spazio olografico
* Scalabilità degli oggetti
* Scalabilità dell'ambiente

### <a name="3-where-is-everyone"></a>3. Dove sono tutti?

La forza della realtà mista entra in gioco quando un'esperienza condivisa può avere luogo nella stessa posizione. Tale oggetto è detto **con lo stato colocato.** Al contrario, quando il gruppo viene distribuito e almeno un partecipante non si trova nello stesso spazio fisico (come spesso accade con la realtà virtuale), viene chiamata esperienza **remota**. Spesso è il caso che il  gruppo abbia partecipanti con una consociata e remota (ad esempio, due gruppi in sale riunioni).

![Tre persone con ologramma sul tavolo](images/three-people-with-holograph-on-table-500px.png)

Le categorie seguenti consentono di comunicare dove si trovano gli utenti:

* **Percorso con percorso:** tutti gli utenti saranno nello stesso spazio fisico.
* **Remoto:** tutti gli utenti saranno in spazi fisici separati.
* **Entrambi:** gli utenti saranno una combinazione di spazi condivisi e remoti.

Questa domanda è fondamentale perché influisce su:

* Come comunicano le persone?
    * Ad esempio: se devono avere avatar?
* Oggetti visualizzati. Tutti gli oggetti sono condivisi?
* Se è necessario adattarsi al proprio ambiente?

### <a name="4-when-are-they-sharing"></a>4. Quando condividono?

In genere si pensa **alle esperienze sincrone** quando vengono a mente le esperienze condivise: tutte le esperienze vengono condivise. Tuttavia, se si include un singolo elemento virtuale aggiunto da un altro utente, si ha uno scenario **asincrono.** Imagine una nota, o promemoria vocale, lasciata in un ambiente virtuale. Come si gestiscono 100 promemoria virtuali rimasti nella progettazione? Cosa succede se vengono da decine di persone con livelli di privacy diversi?

Considerare le esperienze come una di queste categorie di tempo:

* **In modo sincrono:** condivisione dell'esperienza olografica nello stesso momento. Ad esempio: due studenti che fanno il lab delle competenze contemporaneamente.
* **In modo asincrono:** condivisione dell'esperienza olografica in momenti diversi. Ad esempio: due studenti che fanno il lab di competenze ma lavorano su sezioni separate in momenti diversi.
* **Entrambi:** gli utenti a volte condivideranno in modo sincrono, ma altre volte in modo asincrono. Ad esempio: un docente che classifica l'assegnazione eseguita dagli studenti in un secondo momento e lascia gli appunti agli studenti per il giorno successivo.

Questa domanda è importante perché influisce su:

* Persistenza dell'oggetto e dell'ambiente. Ad esempio: archiviazione degli stati in modo che possano essere recuperati.
* Prospettiva dell'utente. Ad esempio: forse ricordando ciò che l'utente stava guardando quando lascia gli appunti.

### <a name="5-how-similar-are-their-physical-environments"></a>5. Quanto sono simili i loro ambienti fisici?

La probabilità che due ambienti reali identici, al di fuori delle esperienze condivise, siano difficili a meno che tali ambienti non siano stati progettati per essere identici. È più probabile che si abbia **ambienti** simili. Ad esempio, le sale riunioni sono simili, in genere hanno un tavolo situato a livello centrale, racchiuso tra le camere. I camere da casa, d'altra parte, sono diversi** e possono includere un numero qualsiasi di mobili in una matrice infinita di layout.

![Ologramma sulla tabella](images/holograph-on-table-500px.png)

Considerare le esperienze di condivisione che si adattano a una di queste due categorie:

* **Simile:** ambienti che tendono ad avere mobili simili, luce ambientale e suono, dimensioni fisiche della stanza. Ad esempio: il docenti si trova nell'atrio A e gli studenti sono nell'atrio B. La sala delle lezioni A potrebbe avere meno lezioni rispetto a B, ma entrambi possono avere una postazione fisica su cui posizionare gli ologrammi.
* **Diverso: ambienti diversi** in ambienti di mobili, dimensioni delle camere, considerazioni sulla luce e sul suono. Ad esempio: un insegnante si trova in una sala di interesse, ma gli studenti sono in una grande sala riunioni, piena di studenti e docenti.

È importante pensare [all'ambiente](/hololens/hololens-environment-considerations), perché influirà su:

* Modalità di utilizzo di questi oggetti da parte degli utenti. Ad esempio: se l'esperienza è ottimale in una tabella e l'utente non ha una tabella? Oppure su una superficie piana del piano, ma l'utente ha uno spazio disordinato.
* Scala degli oggetti. Ad esempio: l'inserimento di un modello umano da sei piedi su un tavolo potrebbe essere difficile, ma un modello di memoria funziona bene.

### <a name="6-what-devices-are-they-using"></a>6. Quali dispositivi usano?

Oggi è spesso probabile che si risivano esperienze condivise tra due dispositivi [**immersive**](../../discover/immersive-headset-hardware-details.md) (questi dispositivi potrebbero differire leggermente per i pulsanti e le funzionalità relative, ma non notevolmente) o due dispositivi **olografici** in base alle soluzioni destinate a questi dispositivi. Considerare tuttavia se **i dispositivi 2D** (un partecipante o un osservatore di dispositivi mobili/desktop) saranno una considerazione necessaria, soprattutto nelle situazioni di dispositivi **2D e 3D misti.** Comprendere i tipi di dispositivi che verranno utilizzati dai partecipanti è importante, non solo perché hanno diverse fedeltà, vincoli e opportunità per i dati, ma anche perché gli utenti hanno aspettative univoche per ogni piattaforma.

## <a name="exploring-the-potential-of-shared-experiences"></a>Esplorazione del potenziale delle esperienze condivise

Le risposte alle domande precedenti possono essere combinate per comprendere meglio lo scenario condiviso, ampliando le sfide quando si espande l'esperienza. Per il team Microsoft, questo ha consentito di definire una mappa di percorso per migliorare le esperienze usate oggi, comprendendo la sfumatura di questi problemi complessi e come sfruttare le esperienze condivise nella realtà mista.

Si consideri, ad esempio, uno degli scenari di Skype dal lancio [](https://www.youtube.com/watch?v=iBfzs3G8BEA) di HoloLens: un utente ha illustrato come correggere un interruttore di luce guasto con l'aiuto di un esperto di una posizione remota.

![Correzione di un interruttore leggero con assistenza tramite Skype per HoloLens](images/fix-a-broken-switch-with-hololens-640px.jpg)

*Un esperto **fornisce indicazioni 1:1** dal computer desktop **2D** a un utente di un **dispositivo di realtà mista 3D.** Le **linee** guida **sono sincrone e** gli ambienti fisici sono **diversi.***

Un'esperienza come questa è un passaggio rispetto all'esperienza corrente, ovvero l'applicazione del paradigma di video e voce a un nuovo supporto. Tuttavia, quando si guarda al futuro, è necessario definire meglio l'opportunità degli scenari e creare esperienze che riflettano la forza della realtà mista.

Si [consideri lo strumento di collaborazione OnSight,](https://www.youtube.com/watch?v=XtUyUJAVQ6w)sviluppato dal Jet Disaziale della NASA. Gli scienziati che lavorano sui dati delle missioni rover di Mars possono collaborare con i colleghi in tempo reale all'interno dei dati provenienti dal panorama marziano.

![Collaborazione tra colleghi separati in remoto per pianificare il lavoro per mars rover](images/onsight-nasa-jpl.gif)

*Uno scienziato esplora un ambiente usando un dispositivo **3D** di  realtà mista con un piccolo gruppo di colleghi remoti che usano dispositivi  **3D e 2D.** La **collaborazione** è **sincrona** (ma può essere rivisitata in modo asincrono) e gli ambienti fisici sono (virtualmente) **simili.***

Esperienze come OnSight offrono nuove opportunità di collaborazione. Dal punto di vista fisico degli elementi nell'ambiente virtuale alla posizione accanto a un collega e alla condivisione della loro prospettiva mentre spiegano i risultati. OnSight usa l'obiettivo dell'immersione e della presenza per rivisitire le esperienze di condivisione nella realtà mista.

La collaborazione intuitiva è il fondamento della conversazione, la collaborazione e la comprensione di come è possibile applicare questa intuitività alla complessità della realtà mista è fondamentale. Se non solo è possibile ricreare esperienze di condivisione nella realtà mista, ma sovrapprezzo, si tratta di un cambio di paradigma per il futuro del lavoro. Progettare esperienze condivise nella realtà mista è uno spazio nuovo ed interessante e siamo solo all'inizio.

## <a name="get-started-building-shared-experiences"></a>Introduzione alla creazione di esperienze condivise

A seconda dell'applicazione e dello scenario, saranno necessari diversi requisiti per ottenere l'esperienza desiderata. tra cui:

* **Creazione di corrispondenze:** possibilità di creare sessioni, annunciare sessioni, individuare e invitare utenti specifici, sia in locale che in remoto, a partecipare alla sessione.
* **Condivisione dell'ancoraggio:** possibilità di allineare le coordinate tra più dispositivi in uno spazio locale comune, in modo che gli ologrammi vengano visualizzati nella stessa posizione per tutte le persone.
* **Rete:** possibilità di sincronizzare in tempo reale posizioni, interazioni e movimenti di persone e ologrammi tra tutti i partecipanti.
* **Archiviazione dello stato:** possibilità di archiviare le caratteristiche e le posizioni degli ologrammi nello spazio per l'aggiunta a metà sessione, il richiamo in un secondo momento e la solidità in caso di problemi di rete.

La chiave per le esperienze condivise è fare in modo che più utenti vedano gli stessi ologrammi nel mondo sul proprio dispositivo, spesso tramite la condivisione di ancoraggi per allineare le coordinate tra i dispositivi.

Per condividere gli ancoraggi, usare [Ancoraggi nello spaziale di Azure:](/azure/spatial-anchors)

* Prima l'utente inserisce l'ologramma.
* L'app crea [un ancoraggio](../../design/spatial-anchors.md)spaziale per bloccare l'ologramma con precisione nel mondo.
* Gli ancoraggi possono essere condivisi HoloLens dispositivi iOS e Android tramite [Ancoraggi nello spazio di Azure.](/azure/spatial-anchors/)

Con un ancoraggio spaziale condiviso, l'app in ogni dispositivo dispone ora di un sistema di [coordinate](../../design/coordinate-systems.md) comune in cui è possibile inserire il contenuto. Ora l'app può assicurarsi di posizionare e orientare l'ologramma nella stessa posizione.

Nei HoloLens, è anche possibile condividere gli ancoraggi offline da un dispositivo a un altro.  Usare i collegamenti seguenti per decidere cosa è meglio per l'applicazione.

## <a name="evaluating-tech-options"></a>Valutazione delle opzioni tecniche

Sono disponibili varie opzioni di servizi e tecnologie che consentono di creare esperienze di realtà mista multi-utente.  Può essere difficile scegliere un percorso, quindi, considerando una prospettiva incentrata su uno scenario, alcune opzioni sono dettagliate di seguito.

## <a name="shared-static-holograms-no-interactions"></a>Ologrammi statici condivisi (nessuna interazione)

Sfruttare [ancoraggi nello spaziale di Azure](/azure/spatial-anchors/) nell'app.  L'abilitazione e la condivisione di ancoraggi nello spazio tra dispositivi consente di creare un'applicazione in cui gli utenti vedono gli ologrammi nello stesso punto contemporaneamente.  È necessaria una sincronizzazione aggiuntiva tra dispositivi per consentire agli utenti di interagire con gli ologrammi e visualizzare i movimenti o gli aggiornamenti dello stato degli ologrammi.

## <a name="share-first-person-perspective"></a>Condividere la prospettiva in prima persona

Sfruttare il supporto Miracast per gli utenti locali quando si dispone di un ricevitore Miracast supportato, ad esempio un PC o un TV. Non è necessario alcun codice dell'app aggiuntivo.

Sfruttare [MixedReality-WebRTC](https://github.com/microsoft/mixedreality-webrtc) nell'app, per gli utenti remoti o quando si dispone di dispositivi non Miracast che si desidera condividere.  L'abilitazione di una connessione WebRTC abilita flussi audio/video 1:1 tra gli utenti, con un canale dati per la messaggistica tra dispositivi.  L'implementazione di realtà mista è ottimizzata per HoloLens, fornendo ad altri utenti il flusso video di acquisizione di realtà mista della visualizzazione HoloLens'utente.  Se si vuole aumentare lo streaming video a più client remoti, viene in genere usato un provider di servizi [MCU](https://webrtcglossary.com/mcu/) (Unità di conferenza multipoint), ad esempio [SignalWire](https://signalwire.com/).  Una distribuzione SignalWire in Azure con un clic è disponibile tramite [Freeswitch.](https://github.com/andywolk/azure-freeswitch-gpu-windows)

> [!NOTE]
> Si noti che SignalWire è un servizio a pagamento e non è di proprietà o affiliato a Microsoft.

## <a name="presenter-spectator-applications-and-demos"></a>Presenter-Spectator applicazioni e demo

Sfruttare [MixedReality-SpectatorView](https://github.com/microsoft/MixedReality-SpectatorView) per portare [la funzionalità di visualizzazione degli spettatori](spectator-view.md) nell'app.  Abilitare altri dispositivi (HL, Android, iOS e videocamere) per vedere cosa vede il HoloLens da una prospettiva diversa nella stessa posizione e ricevere aggiornamenti sulle interazioni dell'utente HoloLens host che interagisce con gli ologrammi.  Guardare, scattare foto e registrare video di ciò che l'host fa con gli ologrammi nell'applicazione dal proprio punto di vista spaziale con lo spettante complementare della stessa app.

**Nota:** Le immagini vengono scattate tramite screenshot nei dispositivi iOS/Android.

## <a name="multi-user-collaborative-experience"></a>Esperienza collaborativa multi-utente

Iniziare con [l'esercitazione](../unity/tutorials/mr-learning-sharing-02.md)sull'apprendimento multi-utente, che sfrutta Ancoraggi nello stato di [Azure](/azure/spatial-anchors/) per gli utenti locali e [Photon SDK](https://www.photonengine.com/PUN) per sincronizzare il contenuto/stato nella scena. Creare applicazioni collaborative in locale in cui ogni utente ha la propria prospettiva sugli ologrammi nella scena e può interagire completamente con gli ologrammi.  Gli aggiornamenti vengono forniti in tutti i dispositivi e la gestione dei conflitti di interazione viene gestita da Photon.

> [!NOTE]
> Si noti che [Photon](https://www.photonengine.com/) è un prodotto non Microsoft, quindi potrebbe essere necessaria una relazione di fatturazione con Photon per la productizzazione e la scalabilità per un utilizzo più elevato.

## <a name="future-work"></a>Lavoro futuro

Le funzionalità e le interfacce dei componenti consentono di fornire coerenza comune e un supporto affidabile nei vari scenari e tecnologie sottostanti.  Fino ad allora, scegliere il percorso migliore che si allinea allo scenario che si sta tentando di ottenere nell'applicazione.

Scenario o voglia di usare un'altra tecnologia/servizio? Inviare commenti GitHub problemi nel relativo repo, nella parte inferiore di questa pagina, oppure contattare [HoloDevelopers slack.](https://holodevelopers.slack.com/)

## <a name="see-also"></a>Vedere anche

* [Ancoraggi nello spazio di Azure](/azure/spatial-anchors)
* [Ancoraggi nello spazio condivisi in DirectX](shared-spatial-anchors-in-directx.md)
* [Esperienze condivise in Unity](../unity/shared-experiences-in-unity.md)
* [Visualizzazione spettatore](spectator-view.md)