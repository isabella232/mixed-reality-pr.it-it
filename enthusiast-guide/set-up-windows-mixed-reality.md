---
title: Configurare Windows Mixed Reality
description: Come configurare i controller di Windows Mixed Reality, voce e audio e definire il limite della stanza per uno spazio di riproduzione sicuro.
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: Windows Mixed Reality, realtà mista, realtà virtuale, VR, MR, introduzione, configurazione, controller di movimento, controller, voce, audio, seduti, in piedi, limite, driver di grafica, Microsoft Edge, cromo
ms.openlocfilehash: e30fe5919bbd1345f413902f8f7acd36eed76bb5
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436835"
---
# <a name="set-up-windows-mixed-reality"></a>Configurare Windows Mixed Reality

## <a name="get-ready"></a>Preparazione

Per eseguire Windows Mixed Reality, è necessario:

* Visore vr immersivo di realtà mista compatibile. [Scopri di più](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)
* Un [WINDOWS MIXED REALITY pc pronto per l'uso](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) con le porte corrette per il visore
* Controller [di movimento,](controllers-in-wmr.md)controller Xbox o mouse e tastiera
* Cuffia con microfono (se il visore non è integrato)
* Uno spazio aperto di grandi dimensioni

## <a name="get-set"></a>Get set (Ottieni set)

Preparare lo spazio (incluso lo spazio di sovraccarico). Assicurarsi che non siano presenti ostacoli, rischi o elementi deboli nell'area che si sta usando. Non configurare nella parte superiore di una scala o sotto un ventilatore a soffitto extra-basso. Rimuovere eventuali ostacoli o interruttori dall'area e assicurarsi che tutti gli utenti del visore leggono e comprendano le linee guida sulla sicurezza.

Quando lo spazio è pronto, collegare il visore, ma non lo si mette ancora, prima di tutto sarà necessario eseguire una configurazione nel PC. Verrà eseguito un controllo del PC, verrà scaricato del [](boundary-questions.md) software, si connetteranno i controller e si creerà un limite per evitare ostacoli.

Viene quindi la parte divertente: mettere il visore e entrare nel mondo misto. Cortana sarà in attesa di una presentazione. Buon divertimento!

## <a name="go"></a>Per

Quando lo spazio è pronto, collegare il visore, ma non lo si mette ancora, prima di tutto sarà necessario eseguire una configurazione nel PC. Verrà eseguito un controllo del PC, verrà scaricato del [](boundary-questions.md) software, si connetteranno i controller e si creerà un limite per evitare ostacoli.

Viene quindi la parte divertente: mettere il visore e entrare nel mondo misto. Cortana sarà in attesa di una presentazione. Buon divertimento!

## <a name="get-familiar-with-your-motion-controllers"></a>Acquisire familiarità con i controller di movimento

Se il visore ha una radio incorporata, i controller che vengono con il visore vengono associati in fabbrica. Quando si attivano per la prima volta i nuovi controller e visori, questi saranno già associati.

Se si ha un visore senza una radio predefinita, sarà necessario configurare i controller di movimento associandoli al PC. La maggior parte dei visori prodotti dopo il 2018 ha una radio incorporata.

Non è necessario associare i controller se si prevede di usare solo un gamepad Xbox o una tastiera e un mouse.  Se si prevede di usare i controller, è consigliabile associarli.

**Nota:** Windows Mixed Reality di movimento richiedono Bluetooth 4.0. Se il PC non ha un Bluetooth integrato, è necessario collegare un adattatore Bluetooth USB che supporta Bluetooth 4.0 per abilitare i controller di movimento. Non è necessario un adattatore Bluetooth per usare la radio incorporata nel visore.

![Acquisire familiarità con i controller di movimento](images/get_to_know_controllers.png)

Se è necessario associare i controller di movimento, esaminare i [controller nell Windows Mixed Reality](controllers-in-wmr.md) articolo.

## <a name="set-up-your-room-boundary"></a>Configurare il limite della stanza

Scegliere un'esperienza di scalabilità di stanza o da tavolo:

**Opzione 1: La** configurazione per tutte le esperienze (nota anche come scalabilità di stanza) consente di spostarsi nella stanza ed è l'esperienza di realtà mista più immersiva. È consigliabile liberare almeno cinque metri x sette piedi (1,5 metri x 2 metri) di spazio per la realtà mista.

**Opzione 2: la** configurazione per l'esperienza da seduti e in piedi (nota anche come scala della scrivania) funzionerà alla propria scrivania. È una buona opzione se lo spazio non è grande. Significa anche che si usa il visore senza limiti. È necessario rimanere in un'unica posizione, in quanto non sarà presente alcun limite per evitare ostacoli fisici. Alcune app e giochi non sono progettati per essere un'esperienza limite, quindi potrebbero non funzionare come previsto.

![Scegliere una configurazione](images/1050px-chooseasetup.png)

### <a name="if-you-choose-set-me-up-for-all-experiences"></a>Se si sceglie "Configura per tutte le esperienze"

Presto la stanza diventerà un mondo virtuale in cui è possibile spostarsi e interagire. Alzarsi e liberare spazio nella stanza per l'esecuzione di realtà mista. È consigliabile cancellare almeno cinque metri x sette piedi, o 1,5 metri x 2 metri, di spazio per la realtà mista.

![Assicurarsi che lo spazio sia vuoto](images/1050px-createaboundary.png)

Assicurarsi che lo spazio sia libero.

![Centrare il visore](images/1050px-createaboundary-2.png)

Centrare il visore.

![Tracciare il limite](images/1050px-createaboundary-3.png)

Tracciare il limite.

![Rimanere puntati verso il PC](images/1050px-createaboundary-4.png)

Mantenere il visore puntato verso il PC.

![Ecco il limite](images/1050px-createaboundary-5.png)

Ecco il limite.

### <a name="if-you-choose-set-me-up-for-seated-and-standing"></a>Se si sceglie "Set me up for seated and standing"

Non sono necessari passaggi aggiuntivi se si sceglie questa opzione.

## <a name="what-is-the-maximum-size-of-the-boundary"></a>Qual è la dimensione massima del limite?

La dimensione massima del limite supportata in Windows Mixed Reality è un raggio di 5,7 x 5,7 metri o 4 metri dal centro. Le dimensioni del limite dipendono dal punto di ancoraggio e dalla distanza dal punto di ancoraggio che è possibile spostare prima di rischiare la stabilità del limite.  Windows Mixed Reality si basa su un'astrazione della fase, che rappresenta lo spazio in cui ci si sposta. Questa fase dipende da un singolo ancoraggio, che quasi tutte le app presuppongono: è il modo in cui Vive e Oculus funzionano anche con il singolo sistema di coordinate.  Questo è importante perché con il rilevamento interno, mentre ci si sposta più lontano da un punto di ancoraggio, il rilevamento visore è affidabile per mantenere il limite stabile.  Quando il limite è destinato a evitare ostacoli fisici, diventa più un problema più lontano dal centro.  Due fattori hanno preso la decisione sulle dimensioni massime del limite. La distanza massima alla quale i visori Windows Mixed Reality possono offrire la migliore esperienza di scalabilità della stanza con un limite e la lunghezza del cavo visore, che per la maggior parte dei visori Windows Mixed Reality è di 3 metri.

## <a name="set-up-speech"></a>Configurare il riconoscimento vocale

È possibile abilitare Cortana comandi in realtà mista, che consente di usare i comandi vocali per teletrasportare e aprire le app. Per altre informazioni su queste azioni, vedere [il](learn-mixed-reality.md) capitolo Esercitazione per la realtà mista.

![La realtà mista è migliore con il parlato](images/1050px-betterwithspeech.png)

## <a name="set-up-your-audio-headset"></a>Configurare il visore audio

A meno che non sia stato acquistato un dispositivo Samsung HMD Odyssey con le cuffia AKG integrate e la matrice a doppio microfono, è necessario ottenere un visore audio con microfono e cuffia e collegarlo al jack audio da 3,5 mm del visore. Il jack audio da 3,5 mm per il visore si trova nella parte inferiore della visiera o alla fine di un breve cavo audio collegato alla visiera, a seconda del modello di visore.

## <a name="adjusting-your-headsets-display-settings"></a>Regolazione delle impostazioni di visualizzazione del visore

Windows Mixed Reality automaticamente le impostazioni di visualizzazione che bilanciano qualità e prestazioni, in base alla configurazione hardware del PC. Per modificare queste impostazioni, passare a Impostazioni > **realtà mista > visore.**

### <a name="visuals"></a>Oggetti visivi

Questa impostazione controlla la qualità visiva della home page di realtà mista. Il valore predefinito è "Automatico".

### <a name="resolution"></a>Risoluzione

La risoluzione nativa del visore è illustrata qui.

Se si collega un visore con schermi con risoluzione più elevata al PC, ad esempio visori con schermi da 4320x2160, verrà visualizzata un'impostazione per regolare la risoluzione dello schermo in realtà mista.

* Questa impostazione offre l'opzione per il rendering nativo dello stack di composizione Windows Mixed Reality (ad esempio, a 4320x2160) o per fare in modo che lo stack di composizione esemplii una risoluzione e una scalabilità inferiori (ad esempio, il rendering a 2880x1440 e l'upscale a 4320x2160).
* L'impostazione predefinita consente di eseguire il rendering in modo nativo (ad esempio, **l'opzione 4320 x 2160 (migliore qualità)** per offrire la migliore qualità visiva possibile dal visore.
* Usare **l'opzione Scalabilità automatica (prestazioni ottimali)** se:
    * Il PC non soddisfa i requisiti hardware di grafica minimi per il visore con schermi con risoluzione superiore
    * Vengono visualizzati problemi di prestazioni della grafica

Questa impostazione è disponibile in Windows 10 versione 1903 o successiva e Windows 11.

### <a name="calibration"></a>Calibrazione

Questa impostazione consente di regolare la calibrazione IPD per i visori con supporto ipd software.

### <a name="experience-options"></a>Opzioni dell'esperienza

Questa impostazione avanzata sostituisce l'esperienza di frequenza di aggiornamento dello schermo visore predefinita.

* **Automatico (impostazione predefinita):** selezionare automaticamente l'esperienza a 60 Hz o 90 Hz in base alla configurazione hardware del PC.
* **60Hz**
* **90 Hz**

>[!Note]
>Quando si configura il visore HP Reverb G2 per la prima volta, l'esperienza verrà modificata in 90 Hz per garantire la migliore esperienza.  Se necessario, è possibile modificare questa impostazione in Automatico.

### <a name="input-switching"></a>Cambio di input

Questa impostazione controlla il comportamento del Windows Mixed Reality in risposta al sensore di presenza del visore:

* **Passa automaticamente** usando il sensore di presenza visore (impostazione predefinita): Windows indirizza automaticamente l'input (tastiera, mouse... ) Windows Mixed Reality ogni volta che indossi il visore. È possibile eseguirne l'override in qualsiasi momento con Win + Y.
* **Passare manualmente usando Windows logo**+ Y: Windows non userà il sensore di presenza del visore per rilevare quando si indossa il visore. È necessario usare Win + Y per cambiare l'input tra il desktop del PC e Windows Mixed Reality.

Questa impostazione è disponibile in Windows 10 versione 1903 o successiva e Windows 11.

## <a name="installing-microsoft-edge"></a>Installazione di Microsoft Edge 

Per usare il nuovo Microsoft Edge basato su Chromium nella home page di Windows Mixed Reality, eseguire l'aggiornamento a Windows 10 versione 1903 o successiva o Windows 11 per il supporto nativo delle applicazioni Win32 (come il nuovo Microsoft Edge) in Windows Mixed Reality home page. Controllare Windows Update, [installare manualmente la](https://www.microsoft.com/software-download/windows10)versione più recente di Windows 10 o installare la versione più recente di Windows [11](https://www.microsoft.com/software-download/windows11).

>[!IMPORTANT]
>Il nuovo Microsoft Edge viene avviato con il supporto per WebXR, il nuovo standard per la creazione di esperienze Web immersive per visori VR. Non sarà più possibile riprodurre esperienze WebVR in Microsoft Edge se si installa il nuovo Microsoft Edge.

### <a name="issues-with-the-new-microsoft-edge-in-windows-mixed-reality"></a>Problemi con il nuovo Microsoft Edge in Windows Mixed Reality

**Problemi noti risolti dall'aggiornamento cumulativo 2020-01 per Windows 10 versione 1903 (o successiva)**

- L'avvio di qualsiasi app Win32, incluso il nuovo Microsoft Edge, fa sì che lo schermo del visore si blocchi brevemente.
- Il Microsoft Edge riquadro scompare dal Windows Mixed Reality menu Start (è possibile trovarlo nella cartella "App classiche").
- Windows dal precedente Microsoft Edge sono ancora posizionati intorno al ambiente iniziale, ma non possono essere usati. Il tentativo di attivare tali finestre avvia Edge nell'app Desktop.
- Selezionando un collegamento ipertestuale nel ambiente iniziale viene avviato un Web browser sul desktop anziché nel ambiente iniziale.
- L'app WebVR Showcase è presente nel ambiente iniziale, nonostante WebVR non sia più supportato.
- Miglioramenti generali all'avvio della tastiera e agli oggetti visivi.

**Altri problemi noti**

- I siti Web aperti in Windows Mixed Reality andranno persi quando Portale realtà mista si chiude, anche se le finestre Microsoft Edge rimarranno nella posizione in cui sono stati posizionati ambiente iniziale.
- L'audio Microsoft Edge finestre non è spazializzato.
- Correzione nell'estensione 360 Viewer versione 2.3.8: l'apertura di un video a 360 da YouTube in Windows Mixed Reality può causare la distorsione del video nel visore. Il riavvio di Edge dovrebbe aggiornare in modo invisibile l'estensione 360 Viewer per risolvere il problema. È possibile verificare la versione dell'estensione disponibile immettendo nella barra degli indirizzi e selezionando il pulsante `edge://system/` "Espandi" accanto a "estensioni".
- Durante Windows Mixed Reality sessioni, i monitor virtuali verranno visualizzati come monitor fisici generici in Impostazioni > **sistema > Display**.

## <a name="launching-mixed-reality-after-the-first-time"></a>Avvio della realtà mista dopo la prima volta

Accedere alla realtà mista una seconda volta è semplice come rimetterlo in modalità visore mentre è connesso al PC. È anche possibile avviare l'applicazione Portale realtà mista manualmente aprendola dal menu Start. L'input e l'audio verranno indirizzati automaticamente al visore quando lo si attiva oppure è possibile attivarlo manualmente premendo **Windows + Y** sulla tastiera.

## <a name="see-also"></a>Vedi anche

* [Contattare la community](https://answers.microsoft.com)
* [Per assistenza, contattare Microsoft](https://support.microsoft.com/contactus/)
* [Risoluzione dei problemi relativi all'installazione](installation_errors.md)
* [Risoluzione dei problemi di configurazione](wmr-setup-faq.yml)
* [Esercitazione per la realtà mista](learn-mixed-reality.md)
* [Controller del movimento](controllers-in-wmr.md)
* [Funzionamento del tracciamento dall'interno verso l'esterno](tracking-system.md)
