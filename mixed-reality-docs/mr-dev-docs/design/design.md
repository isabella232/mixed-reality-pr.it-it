---
title: Iniziare a progettare e a creare prototipi
description: Se sei pronto per iniziare a creare, di seguito vengono illustrati i concetti di base che ti serviranno per iniziare a progettare e a creare prototipi.
author: grbury
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Realtà mista, individuare, distribuire, indice, pagina di destinazione, progettazione, sviluppo, esercitazioni, app di esempio, nozioni di base, case study, risorse, guide pratiche per HoloLens, progetti open source, concetti di base, interazione, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: d106b295b72a3087461ccbe8818a7cc23c311f46e3ae20a748c8ce22ec4f89b9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213363"
---
# <a name="start-designing-and-prototyping"></a>Iniziare a progettare e a creare prototipi

![Progettazione astratta di realtà mista](images/design-hero-image.png)

Le applicazioni di realtà mista sono diverse da tutte le altre applicazioni oggi esistenti e la loro progettazione è estremamente complessa. Non solo è necessario tenere conto delle nuove combinazioni di mondi reali e virtuali che si creano, ma anche delle nuove esperienze utente offerte. Poiché la realtà mista abbraccia un'area molto vasta, sono stati selezionati i punti più importanti lungo lo spettro di progettazione e sono stati esposti di seguito sotto forma di una serie di checkpoint. Questi checkpoint sono stati pensati per essere eseguiti in sequenza, ma se si ha già esperienza in materia è possibile passare a una qualsiasi delle sezioni seguenti. 

Per iniziare, guardare il video introduttivo sulla progettazione:

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4LhlW]

## <a name="design-checkpoints"></a>Progettare checkpoint

Usare i checkpoint seguenti per trasferire le idee e i concetti relativi alle applicazioni nel mondo della realtà mista.

### <a name="1-getting-started"></a>1. Guida introduttiva

Come tutti i percorsi, anche quello che riguarda la progettazione di applicazioni di realtà mista inizia dagli elementi di base. È consigliabile acquisire familiarità con i concetti illustrati negli articoli [Che cos'è la realtà mista?](../discover/mixed-reality.md) e [Che cos'è un ologramma?](../discover/hologram.md) per prepararsi psicologicamente alla progettazione immersiva. Dopo aver completato la lettura, è possibile iniziare il percorso di progettazione della realtà mista.

![GIF introduttiva dell'app Designing Holograms](images/HandTracking2.gif)

|  Checkpoint  |  Risultato  |
| --- | --- |
| [Espandere il processo di progettazione](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | Una sguardo in prima persona al processo di progettazione della realtà mista realizzato da designer all'interno e all'esterno di Microsoft |
| [Tipi di app di realtà mista](types-of-mixed-reality-apps.md) | Decidere in quale punto dello spettro della realtà mista si colloca l'esperienza dell'app |
| [App Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) | Apprendere le nozioni di base relative alla progettazione dell'esperienza utente in realtà mista sperimentando comportamenti, suggerimenti e raccomandazioni per la creazione di straordinarie app HoloLens (disponibile per il download da Microsoft Store in HoloLens 2) |
| [MRTK Examples Hub](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4) | Sperimentare comuni interazioni spaziali e blocchi predefiniti per Realtà mista (disponibile per il download da Microsoft Store in HoloLens 2) |
| **Facoltativo** [Scaricare l'Toolkit Figma](figma-toolkit.md) | Il Toolkit Figma fornisce asset da usare per disegnare e delineare l'interfaccia utente in base ai componenti disponibili in MRTK |

### <a name="2-core-concepts"></a>2. Concetti di base

Per lo sviluppo di app per VR o AR, esistono alcuni concetti fondamentali che si applicano alla progettazione di esperienze immersive fluide. Conoscere il punto di vista degli utenti, posizionare gli oggetti e garantire che tutti siano a proprio agio in un ambiente sicuro sono le priorità principali in questa fase del percorso. Alla fine di questa sezione si sarà acquisita una solida base per proseguire con la progettazione delle interazioni.

![Immagine di esempio dei concetti fondamentali](images/fragments-750px.jpg)

|  Concetto  |  Risultato  |
| --- | --- |
| [Frame olografico](holographic-frame.md) | Comprendere il modo in cui gli utenti vedono il contenuto sovrapposto al mondo reale quando indossano i visori VR |
| [Sistemi di coordinate](coordinate-systems.md) | Imparare a posizionare gli ologrammi in punti significativi dell'ambiente, che si tratti di una stanza fisica o di un ambiente virtuale creato |
| [Mapping spaziale](spatial-mapping.md) | Ancorare gli oggetti nel mondo dell'utente e sfruttare i vantaggi delle superfici fisiche del mondo reale |
| [Considerazioni sul comfort](comfort.md) | Garantire il comfort e la sicurezza degli utenti creando e presentando contenuti immersivi in modo da simulare il mondo naturale |

### <a name="3-interaction-design"></a>3. Progettazione delle interazioni

Indipendentemente da quanto sia bella e immersiva, un'esperienza virtuale è inutile senza interazione. Questa sezione descrive in dettaglio i modelli di interazione di base, i controller del movimento e di tracciamento della mano, l'input vocale e la raccolta dei dati di tracciamento oculare degli utenti. Alla fine di questa sezione sarà possibile affrontare l'ultimo importante argomento del percorso di progettazione: l'esperienza utente.

![Fattori di progettazione delle interazioni](images/UX_Hero_Manipulation.jpg)

|  Concetto  |  Risultato  |
| --- | --- |
| [Modelli di interazione](interaction-fundamentals.md) | Fornire agli utenti interazioni istintive attraverso la mano, l'occhio e l'input vocale |
| [Mani e controller del movimento](hands-and-tools.md) | Imparare a interagire con gli ologrammi a corto raggio con le mani di un utente o a lungo raggio con interazioni precise |
| [Input vocale](voice-input.md) | Usare i comandi vocali come input nelle app immersive per controllare gli ologrammi e gli ambienti circostanti  |
| [Tracciamento oculare](eye-tracking.md) | Aggiungere un nuovo livello di contesto e comprensione umana in un'esperienza olografica usando le informazioni relative agli elementi osservati dagli utenti |

### <a name="4-user-experience-elements"></a>4. Elementi dell'esperienza utente

Dopo aver appreso le interazioni di base, è possibile concentrarsi sui punti più fini degli elementi dell'esperienza utente e su come adattarli agli ambienti esclusivi della realtà mista. Verranno illustrati i comportamenti comuni, la progettazione degli asset, il ridimensionamento degli oggetti e gli elementi tipografici, rendendo l'esperienza intuitiva per gli utenti. Questa sezione segna la fine del percorso ufficiale di progettazione della realtà mista. Per proseguire, sono tuttavia disponibili altre risorse nella sezione [Passaggi successivi](#whats-next).

![Elementi UX](images/UX_Hero_BoundingBox.jpg)

|  Concetto  |  Risultato  |
| --- | --- |
| [Controlli e comportamenti comuni](app-patterns-landingpage.md) | Vedere le informazioni sulle interazioni spaziali e sui blocchi predefiniti dell'interfaccia utente più comuni |
| [Colore, luce e materiali](color-light-and-materials.md) | Progettare asset di qualità per la realtà mista per i quali vengano presi in considerazione colore, illuminazione e materiali |
| [Scala degli oggetti](scale.md) | Incorporare il maggior numero possibile di segnali visivi reali per aiutare gli utenti a comprendere la posizione e le dimensioni degli oggetti e il materiale di cui sono fatti |
| [Tipografia](typography.md) | Usare testo chiaro e leggibile nello spazio tridimensionale per fornire agli utenti le informazioni importanti necessarie |

## <a name="whats-next"></a>Passaggi successivi

Il lavoro di un progettista non finisce mai, specialmente quando si tratta di imparare a creare esperienze immersive in un nuovo paradigma. Le sezioni seguenti compiono un passo avanti rispetto al materiale di progettazione di livello principiante già completato, consentendo di accedere al mondo dello sviluppo di realtà mista. Questi argomenti e queste risorse non sono presentati in ordine sequenziale e possono quindi essere esplorati liberamente.

### <a name="choose-a-prototyping-option"></a>Scegliere un'opzione per la creazione di prototipi  

:::row:::   
    :::column:::    
        [![MrTK Figma Toolkit](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)<br>
        **[Figma Toolkit](figma-toolkit.md)**<br>   
        Figma Toolkit fornisce gli asset che possono essere usati per disegnare e delineare l'interfaccia utente. Tutti i controlli dell'interfaccia utente sono basati sui componenti disponibili in MRTK.
    :::column-end:::        
    :::column:::    
       [![Informazioni su Unity](../images/Final_unity_logo.png)](https://learn.unity.com/)<br>
        **[Informazioni su Unity](https://learn.unity.com/)**<br>
        Scopri come creare esperienze interattive con Unity. Impara con la pratica, dall'inizio alla fine.
    :::column-end:::    
    :::column:::    
        [![Mixed Reality Toolkit (MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)<br>
        **[Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/)**<br>  
        Grazie all'interazione spaziale e ai componenti di base dell'interfaccia utente, puoi iniziare subito a progettare e sviluppare realtà miste con Unity.   
    :::column-end:::
    :::column:::    
        [![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)<br>
        **[Microsoft Maquette](https://www.maquette.ms/)**<br>  
        Progetta per la realtà mista. Microsoft Maquette consente di creare prototipi spaziali con un'esperienza semplice, rapida e immersiva. 
    :::column-end:::    
:::row-end:::

<br>

---

### <a name="other-resources"></a>Altre risorse

:::row:::
    :::column:::
       [![Acquisisci i concetti di base](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)<br>
        **[Acquisisci i concetti di base](../discover/get-started-with-mr.md#understand-the-basics)**<br>
        Approfondisci il significato di realtà mista e come viene usata.
    :::column-end:::
    :::column:::
        [![Partecipa a un evento](images/74-16.png)](../whats-new/sf-academy-events.md)<br>
         **[Partecipa a un evento](../whats-new/sf-academy-events.md)**<br>
        Vieni a vedere l'hardware e partecipa all'esercitazione pratica per creare la tua prima applicazione HoloLens 2.
    :::column-end:::
    :::column:::
        [![Installa gli strumenti](images/74-17.png)](../develop/install-the-tools.md)<br>
         **[Installa gli strumenti](../develop/install-the-tools.md)**<br>
        Usa l'elenco di controllo dell'installazione per ottenere gli strumenti necessari per creare app per HoloLens e per la realtà mista.
    :::column-end:::
    :::column:::
        [![Inizia a sviluppare](images/74-18.png)](../develop/development.md)<br>
        **[Inizia a sviluppare](../develop/development.md)**<br>
        Scegli un percorso di sviluppo in base al tuo livello di competenza, al tuo stile di lavoro o all'interesse per le piattaforme.
    :::column-end:::
:::row-end:::

<br>

<br>
