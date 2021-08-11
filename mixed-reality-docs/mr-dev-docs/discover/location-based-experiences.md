---
title: Location Based Entertainment con Windows Mixed Reality
description: 'Informazioni sui Windows Mixed Reality per Location Based Entertainment: hardware, PC per lo zainetto, rilevamento, configurazione e supporto.'
author: jessemcculloch
ms.author: ishitak
ms.date: 08/03/2020
ms.topic: article
keywords: realtà mista, vr, lbe, posizione, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, hardware, HoloLens, multi-player, servizi cloud, Azure
ms.openlocfilehash: e9cff1184ca60f4b64be5346a187666e7b401aab06fee87c179917e300aa07f3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196785"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a>Location Based Entertainment con Windows Mixed Reality

Negli ultimi due anni è stata osservata una crescita e un'innovazione straordinarie nella categoria Location Based Entertainment. Le sedi tradizionali come il tema park e i cinema hanno iniziato a offrire esperienze coinvolgenti e multi-player come esperienze complementari per le corse e le installazioni esistenti. Nuovi operatori e sedi stanno portando esperienze multi-giocatore e multi-sensoriali uniche a un prezzo interessante per le messe. Tutte queste esperienze stanno spingendo la busta per ottenere ciò che è possibile con la realtà mista.

Questo documento è una guida per iniziare a usare Windows Mixed Reality nella categoria Location Based Entertainment. Le linee guida seguenti possono essere applicabili anche alle esperienze basate sulla posizione oltre all'intrattenimento, ad esempio formazione, progettazione di prodotti e altri casi d'uso.

## <a name="engineering-faq"></a>Domande frequenti sulla progettazione

### <a name="hardware"></a>Hardware

**D: Quale hardware è disponibile da Microsoft e dai suoi partner che è possibile usare nella configurazione?**

A: Microsoft e i partner OEM offrono un portfolio accattivante di dispositivi tra cui scegliere a seconda delle esigenze.  

Se le esperienze che si offrono ai clienti richiedono un visore per la realtà virtuale, i visori sul mercato di HP, Samsung e Acer sono molto adatti. Ogni visore ha i propri attributi differenziati. Altri dettagli su ognuno di essi sono riportati di seguito.

HP Reverb: [Dettagli](https://hp.com/go/Reverbpro)

Samsung Odyssey+: [Dettagli](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)

Acer: [Dettagli](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)

Se la posizione è specializzata in esperienze di realtà mista o aumentata con visori see-through, vedere il Microsoft HoloLens 2.  

HoloLens 2: [Pre-order interest](https://www.microsoft.com//hololens/buy)

Se si stanno sperimentando esperienze che usano funzionalità avanzate di visione computer, riconoscimento vocale e rilevamento del corpo, azure Kinect DK è una buona idea.  

Azure Kinect: [dettagli](https://azure.microsoft.com//services/kinect-dk/)

**D: Qual è il portfolio di PC che è possibile usare per eseguire le esperienze VR con tethering pc?**

Per le esperienze VR con tethering per PC, gli OEM offrono un'incredibile selezione di PC per lo zainetto creati esattamente per le proprie necessità.

HP ha appena lanciato hp VR vr G2, il PC indossabile più potente al mondo, ottimizzato per esperienze di roaming gratuito, ora con il 30% di potenza in più con una GPU RTX 2080 all'interno. [Dettagli](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a>Eseguire la configurazione

**D: Come è possibile configurare e personalizzare più facilmente il Portale realtà mista per LBE?**

>[!NOTE]
>Questa funzionalità richiede la versione 2000.19061.1011.0 o successiva.  

È possibile che sia necessaria una personalizzazione più Portale realtà mista di quella normalmente disponibile tramite l'app per la distribuzione di app in modalità tutto schermo o esperienze personalizzate. L'aggiornamento più recente di Portale realtà mista supporta diverse impostazioni avanzate, che è possibile impostare tramite un file di configurazione:  

Consenti controlli di sistema non riusciti: in genere il processo di installazione verifica la compatibilità del PC Windows Mixed Reality prima di completare la configurazione. Il bypass dei controlli di compatibilità può causare problemi durante il tentativo di Windows Mixed Reality se si verificano problemi di compatibilità.  

Ignora app complementare del dispositivo: DCA fornisce i passaggi di configurazione specifici del visore forniti dal produttore e consente di aggiornare il firmware del visore.  

Ignora la configurazione della stanza: invece di chiedere di creare un limite della stanza, è possibile continuare direttamente nel visore in modalità Seduti/In piedi.  

Ignora l'installazione di app dallo Store: il normale programma di installazione installa diverse app dello Store Visualizzatore 3D e il componente aggiuntivo Edge 360 Viewer. L'installazione di queste app verrà ignorata, ma potrebbe mancare la funzionalità del dispositivo.  

Mostra anteprima a schermo intero: Portale realtà mista l'anteprima del visore verrà visualizzata per impostazione predefinita a schermo intero nel PC desktop mentre il visore è in uso.  

Nascondi nuovo per il pannello laterale: impedisce l'espansione del pannello Nuovo automaticamente all'avvio del Portale realtà mista.  

#### <a name="how-to-configure"></a>Modalità di configurazione:  

Per impostare una di queste configurazioni, è necessario creare un file denominato _UserConfig.js_ in in questa directory: _$env:LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState \\_

Per la maggior parte degli utenti, sarà simile a: _C:\Users \<username> \AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState \\_

Il file JSON deve avere il contenuto seguente con "true" impostato per una delle impostazioni precedenti che si desidera sia abilitata:  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
**D: Sono disponibili indicazioni per la configurazione dello spazio di gioco?**

A: La configurazione di uno spazio di gioco deve essere eseguita come si farebbe con un'esperienza di configurazione consumer. Il processo di configurazione della stanza consente anche di definire i limiti della stanza. Per altre informazioni sulla configurazione dei limiti della stanza, vedere [qui](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).

Come illustrato nel documento precedente, lo spazio di gioco a singola coordinata ragionevole è di circa 5mx5m. Se si vuole avere un'area più ampia, è possibile usare la funzionalità Ancoraggi nello stack di API Windows Holographic. L'uso di questa API richiederà una progettazione personalizzata nelle esperienze che si stanno producendo.  

Per altre informazioni su come ottimizzare il contenuto per dimensioni di spazio diverse, vedere [qui](/windows/mixed-reality/coordinate-systems).
 

**D: Lo spazio è troppo grande e si verificano errori quando si prova a configurare un'esperienza in piedi con limiti. Cosa è necessario fare per configurare un'esperienza di roaming gratuito di grandi dimensioni?**

A: Per configurare uno spazio maggiore di ~18x18ft, non è possibile usare l'esperienza di limite fornita dal sistema.  I sistemi limite si basano su un singolo "ancoraggio" a coordinate fisse, che può diventare instabile quando un utente è troppo lontano dall'ancoraggio della fase centrale. 

È possibile configurare la modalità "seduti", che non visualizza il limite né configura un limite di fase o uno spazio di gioco.  È necessario configurare più ancoraggi nello spazio all'interno dell'app per fare riferimento ad aree limite fisiche. 

Lo sviluppatore dell'applicazione è responsabile di visualizzare le misure di sicurezza necessarie in modo che gli utenti non collidono con l'ambiente fisico.  Possono trattarsi di pareti digitali all'interno dell'esperienza o di un oggetto visivo limite del gioco personalizzato. 

Le linee guida per la configurazione del limite della stanza con WMR sono disponibili [qui.](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)

**D: Dove è l'origine dello spazio di gioco?**

A: L'origine dello spazio di gioco è determinata dall'esperienza di configurazione della stanza, in particolare dalla posizione HMD quando viene premuto il pulsante Center durante la configurazione. 

### <a name="multi-player-setup"></a>CONFIGURAZIONE MULTI-PLAYER

**D: Sto distribuendo un'esperienza multi-player in nella sede. È supportato in Windows Mixed Reality?**

A: Se si acconsente esplicitamente Windows 20H1 o versione successiva tramite il programma Insider, è possibile accedere a una nuova interfaccia per la condivisione delle mappe. Questa nuova funzionalità è disponibile tramite [l'interfaccia di Gestione](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) mappe del portale Windows dispositivo. Per usare questo strumento, seguire questa procedura:
* Assicurarsi di aver scelto 20H1 o versione successiva: dopo settembre 2019, questo significa usare il programma Insider
* Abilitare il Windows Portale di dispositivi (WDP) usando queste [istruzioni](/windows/uwp/debug-test-perf/device-portal-desktop)
* Collegare un Windows Mixed Reality HMD da cui si vuole scaricare una mappa esistente o importarne una nuova
* Passare al WDP nel browser preferito usando l'URL fornito nella schermata delle impostazioni.
    * Passare alla sezione "Realtà mista" e selezionare "Gestione mappe".
    * È ora possibile usare il pulsante "Download" per esportare una mappa esistente dal computer.
    * È possibile usare il pulsante "Upload un file di mappa" per importare una mappa da un'esportazione precedente (ad esempio in un computer diverso).
    * È possibile usare "Importa" per consentire al sistema di usare tale mappa per questo HMD in questo computer.

> [!NOTE] 
> In precedenza, tuttavia, era possibile usare lo strumento Spatial Data Packager Tool, originariamente rilasciato come non supportato e ora ufficialmente deprecato e non più funzionante in 20H1. Usare invece lo strumento Gestione [mappe posta in](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) arrivo come descritto in precedenza. 

### <a name="tracking"></a>Monitoraggio

D: Come funziona la tecnologia di rilevamento Windows Mixed Reality visori?  

La realtà mista condivide la stessa tecnologia di rilevamento del HoloLens. Per altre informazioni sul sistema di rilevamento interno, vedere la documentazione [qui.](/windows/mixed-reality/enthusiast-guide/tracking-system)

Per una descrizione del funzionamento del sistema di mapping spaziale di livello superiore, vedere la [descrizione qui](../design/spatial-mapping.md).

**D: Esistono procedure consigliate per ottenere un volume di rilevamento affidabile?**

Per configurare al meglio l'ambiente per il rilevamento dell'esito positivo, è possibile leggere le procedure consigliate in questo [post.](/hololens/hololens-environment-considerations)

**D: Esistono sfumature specifiche per il rilevamento negli spazi di scalabilità del magazzino o nelle ottimizzazioni da considerare?**

A: Le procedure seguenti consentono di ottenere un volume di rilevamento più affidabile:  

Fornire funzionalità diverse nella stanza che si sovrappongono in più posizioni consente al sistema di rilevamento di ottenere un blocco solido. Si pensi a scheggiature e tratteggi casuali invece di usare linee in stile contorno a tinta unita. 

Ridurre al minimo l'intervallo dinamico di illuminazione nell'area, laddove possibile. Le fotocamere di rilevamento sui HMD di realtà mista non sono HDR e hanno agC (guadagno automatico) e AEC (esposizione automatica) che si occuperà di illuminazione diversa. A seconda della distribuzione di luce della superficie, modelli e contrasto, AGC o AEC può concludere di essere in una stanza molto bianca o nera, che può lavare le funzionalità che possono essere nel "colore" opposto. Se si sta tentando di scattare una foto interna davanti a una finestra esterna con luce diurna brillante dietro e si regola l'esposizione in modo da poter visualizzare i dettagli all'esterno, tutto ciò che si trova all'interno è sottoesploso e nero. Oppure, se impostato per all'interno, tutto il contenuto esterno è ora sovraesposizione e tutto bianco.  

Faretti in una stanza (anche in testa) che sono in vista se le telecamere di rilevamento possono talvolta essere responsabili, che confondono l'AEC/AGC delle telecamere di rilevamento. L'illuminazione piana/diffusa aiuta.  

### <a name="mixed-reality-cloud-services-and-azure"></a>SERVIZI CLOUD DI REALTÀ MISTA E AZURE 

**D: In che modo Microsoft Azure la scalabilità aziendale?**

A: Azure basato sulla gestione locale e remota può aiutare l'azienda a essere basata sui dati, ridurre i costi operativi e ridimensionare la distribuzione in posizioni nuove e esistenti. I servizi cloud di Azure come Archiviazione di Azure, Funzioni di Azure, servizio app, Rete di Azure e hub IOT possono essere utili nei casi d'uso seguenti:  

Gestione della distribuzione remota & dispositivi 

Real-Time analisi in sede 

Intelligent Adaptable LBE Gioco 

Flusso e distribuzione del contenuto LBE 

Mappa termica delle preferenze del lettore LBE 

Sistema di prenotazione e prenotazione LBE 

**D: Si sta sviluppando un MMOG spaziale per la distribuzione su un footprint di grandi dimensioni. Servizi che consentono di gestire il contenuto e la persistenza degli oggetti?**

A: Ancoraggi nello stato di Azure è un nuovo servizio di realtà mista che consente esperienze di realtà mista multi-utente e con informazioni spaziali nei dispositivi HoloLens, iOS e Android. Per altre informazioni su Ancoraggi nello spazio di [Azure, vedere](https://azure.microsoft.com//services/spatial-anchors/).

**D. La sede è specializzata in esperienze multi-lettore e mi piace concentrare il tempo di sviluppo sul contenuto e sullo sviluppo front-end. Sono disponibili offerte che consentono di eseguire il bootstrap o l'offload dello sviluppo back-end?**

A: Azure PlayFab è una piattaforma back-end completa per giochi live. Per altre informazioni, [vedere](https://playfab.com/)qui .

### <a name="misc"></a>Varie

**D: Per distribuire le esperienze, si usa SteamVR. La Windows Mixed Reality funziona con SteamVR?**

A: Windows Mixed Reality for SteamVR consente agli utenti di eseguire esperienze Dirvr su Windows Mixed Reality visori VR immersive. Altre informazioni su SteamVR con WMR [sono qui.](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)

### <a name="support-and-community"></a>Supporto e community  

Sono disponibili alcune risorse utili che consentono di interagire con gli esperti in materia del team, ottenere supporto per la risoluzione dei problemi e contribuire alla più ampia community di sviluppatori di realtà mista.  

Se si verificano problemi con le funzionalità rilasciate pubblicamente, determinare un bug usando Hub di Feedback. Per indicazioni, vedere questa [pagina](/windows/mixed-reality/enthusiast-guide/filing-feedback).

Per altre informazioni sulla risoluzione dei problemi relativi a WMR, richiedere [assistenza](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782) al team di supporto clienti.

Partecipa al canale Slack HoloDevelopers per interagire con gli sviluppatori di realtà mista e gli esperti in materia: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)

Twitter: segui il nostro team di relazioni con sviluppatori di realtà mista per notizie, eventi e aggiornamenti @MxdRealityDev 

Se ci si verifica a San Francisco o nelle città di San Francisco, c'è sempre qualcosa che accade in Microsoft Reactor. È possibile visualizzare il calendario degli eventi [qui.](https://developer.microsoft.com//reactor/Location/San%20Francisco)
