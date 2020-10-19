---
title: Configurare Windows Mixed Reality
description: Come configurare i controller di movimento per la realtà mista di Windows, il riconoscimento vocale e l'audio e definire il limite della stanza per uno spazio di riproduzione sicuro.
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, introduzione, installazione, controller di movimento, controller, sintesi vocale, audio, seduto, in piedi, confine, driver grafici, Microsoft Edge, cromo
ms.openlocfilehash: 71775ba03cb143b83f1a4514f62f20df903df96d
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174464"
---
# <a name="set-up-windows-mixed-reality"></a>Configurare Windows Mixed Reality

## <a name="get-ready"></a>Preparazione

Per eseguire la realtà mista di Windows, è necessario:

* Un headset immersivo A realtà mista compatibile. [Altre informazioni](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)
* Un [PC con la realtà mista di Windows](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) con le porte corrette per la cuffia
* [Controller](controllers-in-wmr.md)di movimento, controller Xbox o mouse e tastiera
* Cuffie con MIC (se non sono state compilate le cuffie)
* Ampio spazio aperto

## <a name="get-set"></a>Ottenere set

Preparare lo spazio (incluso lo spazio su sovraccarico). Assicurarsi che non vi siano ostacoli, rischi o elementi fragili nell'area in uso. Non impostare nella parte superiore di una scala o sotto una ventola a soffitto molto bassa. Rimuovere fragili e gli ostacoli dall'area e assicurarsi che tutti gli utenti che usano l'auricolare leggano e conoscano le [linee guida](https://support.microsoft.com/help/4039969)per la sicurezza.

## <a name="go"></a>Per

Quando lo spazio è pronto, collegare la cuffia, ma non inserirla ancora, prima di tutto è necessario eseguire alcune operazioni di configurazione nel PC. Si eseguirà un controllo del PC, si scaricherà il software, si connetteranno i controller e si creerà un [limite](boundary-questions.md) che consente di evitare ostacoli.

Viene quindi visualizzata la parte divertente, che viene inserita nell'auricolare e si entra nel mondo misto. Cortana sarà in attesa di offrire una presentazione. Buon divertimento!

## <a name="get-familiar-with-your-motion-controllers"></a>Acquisire familiarità con i controller di movimento

Se la cuffia ha una radio predefinita, i controller inclusi nell'auricolare vengono associati alla Factory. Quando si accende per la prima volta i nuovi controller e l'auricolare, questi saranno già abbinati.

Se si dispone di un auricolare senza una radio incorporata, sarà necessario configurare i controller di movimento associando i controller al PC (la maggior parte degli auricolari prodotti dopo 2018 avrà la radio predefinita).

Se si prevede di usare solo un gamepad Xbox o una tastiera e un mouse, non è necessario associare i controller.  Se si prevede di usare i controller, è probabile che sia possibile associarli.

**Nota**: i controller di movimento per la realtà mista di Windows richiedono Bluetooth 4,0. Se il PC non dispone di Bluetooth integrato, sarà necessario collegare una scheda Bluetooth USB che supporti Bluetooth 4,0 per abilitare i controller di movimento. Se si usa la radio predefinita nell'auricolare, non è necessaria una scheda Bluetooth.

![Acquisire familiarità con i controller di movimento](images/get_to_know_controllers.png)

Se è necessario associare i controller di movimento, rivedere i [controller nell'articolo relativo alla realtà mista di Windows](controllers-in-wmr.md) .

## <a name="set-up-your-room-boundary"></a>Configurare il limite della stanza

Scegliere un'esperienza di scalabilità o di scalabilità della scrivania:

**Opzione 1: configurare per tutte le esperienze (anche nota come scalabilità a livello di spazio)** consente di esplorare la stanza ed è l'esperienza di realtà mista più immersiva. Per la realtà mista è consigliabile cancellare almeno 5 piedi x 7 piedi (1,5 metri x 2 metri) di spazio.

**Opzione 2: l'esperienza di configurazione per la scalabilità (anche nota come scala desk) può essere** utilizzata sulla scrivania. È una buona opzione se non si ha molto spazio nello spazio. Significa anche che l'auricolare verrà usato senza un limite. Dovrai rimanere in un'unica posizione, perché non avrai alcun limite per aiutarti a evitare ostacoli fisici. Inoltre, alcune app e giochi possono essere progettati per essere usati con un limite, quindi potrebbero non funzionare come previsto.

![Scegliere un'installazione](images/1050px-chooseasetup.png)

### <a name="if-you-choose-set-me-up-for-all-experiences"></a>Se si sceglie "Configura per tutte le esperienze"

A breve, la tua stanza diventerà un mondo virtuale in cui è possibile esplorare e interagire. Metti in risalto e pulisci spazio nella tua stanza per l'esecuzione di realtà mista (ad esempio, cancella una certa superficie e sposta la poltrona sul lato della stanza). Per la realtà mista è consigliabile cancellare almeno 5 piedi x 7 piedi (1,5 metri x 2 metri) di spazio.

![Assicurarsi che lo spazio sia chiaro](images/1050px-createaboundary.png)

Assicurarsi che lo spazio sia chiaro.

![Centrare l'auricolare](images/1050px-createaboundary-2.png)

Centrare l'auricolare.

![Tracciare il limite](images/1050px-createaboundary-3.png)

Tracciare il limite.

![Rimanere puntati verso il PC](images/1050px-createaboundary-4.png)

Mantieni la cuffia rivolta verso il PC.

![Ecco il limite](images/1050px-createaboundary-5.png)

Ecco il limite.

### <a name="if-you-choose-set-me-up-for-seated-and-standing"></a>Se scegli "Configurami per la seduta e la posizione"

Non sono necessari passaggi aggiuntivi se si sceglie questa opzione.

## <a name="what-is-the-maximum-size-of-the-boundary"></a>Qual è la dimensione massima del limite?

Le dimensioni massime attualmente supportate per la realtà mista di Windows sono 18x18ft (5.7 x 5.7 m) o 13ft (4m) RADIUS dal centro.  Le dimensioni limite dipendono dal punto di ancoraggio e dalla distanza del punto di ancoraggio che è possibile spostare prima di rischiare la stabilità del limite.  La realtà mista di Windows si basa su un'astrazione della fase nella piattaforma, la fase è lo spazio in cui ci si sposta e la fase dipende da un singolo ancoraggio (che quasi tutte le app presuppone anche che sia il modo in cui vive e Oculus funziona, perché hanno solo un unico sistema di coordinate).  Il motivo per cui questo aspetto è importante è che con il rilevamento interno, man mano che ci si allontana da un punto di ancoraggio, il rilevamento della cuffia è affidabile per mantenere stabile il limite.  Laddove il limite è concepito per evitare ostacoli fisici, diventa sempre più problematico, dal centro.  Due fattori sono passati alla decisione sulla dimensione massima del limite; la distanza massima tra le cuffie per la realtà mista di Windows potrebbe offrire la migliore esperienza di scalabilità delle chat con un limite e la lunghezza del cavo auricolare, che per la maggior parte delle cuffie per la realtà mista di Windows è 10ft (3M). 

## <a name="set-up-speech"></a>Configura sintesi vocale

È possibile abilitare i comandi Cortana all'interno di realtà mista. In questo modo è possibile usare i comandi vocali all'interno della realtà mista per teletrasportarsi, aprire app ed eseguire altre operazioni. Ulteriori informazioni su questo articolo sono disponibili nel capitolo [informazioni sulla realtà mista](learn-mixed-reality.md) .

![La realtà mista è migliore con la sintesi vocale](images/1050px-betterwithspeech.png)

## <a name="set-up-your-audio-headset"></a>Configurare la cuffia audio

A meno che non sia stato acquistato un Samsung HMD Odyssey (che ha integrato cuffie AKG e un array dual microphone integrato), è necessario ottenere una cuffia audio (con microfono e cuffia) e collegarla all'audio jack da 3,5 mm dell'auricolare. Il jack audio da 3,5 mm per la cuffia, a seconda del modello di auricolare, deve trovarsi sul lato inferiore della visiera auricolare o alla fine di un cavo audio breve che fuoriesce dalla visiera auricolare.

## <a name="adjusting-your-headsets-display-settings"></a>Regolazione delle impostazioni di visualizzazione dell'auricolare

La realtà mista di Windows sceglie automaticamente le impostazioni di visualizzazione che bilanciano la qualità e le prestazioni, in base alla configurazione hardware del PC. Per modificare queste impostazioni, passare a **impostazioni > realtà mista > visualizzazione dell'auricolare**.

### <a name="visuals"></a>Oggetti visivi

Questa impostazione controlla la qualità visiva della Home realtà mista. Il valore predefinito è "Automatic".

### <a name="resolution"></a>Soluzione

Qui viene visualizzata la risoluzione nativa dell'auricolare.

Se al PC si connette una cuffia con schermi con risoluzione superiore (ad esempio, cuffie con 4320x2160), verrà visualizzata un'impostazione per regolare la risoluzione dello schermo della realtà mista.

* Questa impostazione fornisce l'opzione per lo stack di composizione della realtà mista di Windows per eseguire il rendering in modo nativo (ad esempio, in 4320x2160) o per fare in modo che lo stack di composizione esegua il rendering con una risoluzione e una scalabilità inferiori (ad esempio, eseguire il rendering in 2880x1440 e scalare su 4320x2160.
* L'impostazione predefinita prevede il rendering nativo, ad esempio l'opzione **4320 x 2160 (qualità migliore)** , per fornire la migliore qualità visiva possibile dall'auricolare.
* Se il PC non soddisfa i requisiti minimi dell'hardware grafico per la cuffia con schermi con risoluzione superiore e/o se si verificano problemi di prestazioni della grafica, è possibile provare a usare la selezione dell'opzione di **scalabilità automatica (prestazioni ottimali)** .

Questa impostazione è disponibile in Windows 10, versione 1903 o successive.

### <a name="calibration"></a>Calibrazione

Questa impostazione consente di modificare la taratura dpi per gli auricolari con supporto di software dpi.

### <a name="experience-options"></a>Opzioni di esperienza

Questa impostazione avanzata sostituisce l'esperienza di frequenza di aggiornamento dello schermo della cuffia predefinita.

* **Automatico (impostazione predefinita)**: seleziona automaticamente l'esperienza 60Hz o 90Hz in base alla configurazione hardware del PC.
* **60Hz**
* **90Hz**

>[!Note]
>L'impostazione della frequenza di aggiornamento automatico per HP Reverb G2 è 90Hz

Alcune funzionalità della realtà mista di Windows, tra cui l'anteprima del portale misto reality e la visualizzazione di un auricolare più grande, sono disponibili solo con l'esperienza 90Hz.

### <a name="input-switching"></a>Cambio di input

Questa impostazione controlla il comportamento della realtà mista di Windows in risposta al sensore di presenza dell'auricolare:

* **Cambia automaticamente usando il sensore di presenza dell'auricolare** (impostazione predefinita): Windows indirizza automaticamente l'input (tastiera, mouse...) alla realtà mista di Windows quando si indossa l'auricolare. È possibile eseguire l'override in qualsiasi momento con Win + Y.
* **Passa manualmente usando il tasto logo Windows + Y**: Windows non userà il sensore di presenza dell'auricolare per rilevare quando si sta indossando la cuffia. È necessario usare Win + Y per cambiare l'input tra il desktop del PC e la realtà mista di Windows.

Questa impostazione è disponibile in Windows 10, versione 1903 o successive.

## <a name="installing-microsoft-edge"></a>Installazione di Microsoft Edge 

Per usare il nuovo Microsoft Edge basato su cromo nella Home realtà mista di Windows, eseguire l'aggiornamento a Windows 10 versione 1903 o successiva per il supporto nativo di applicazioni Win32, come il nuovo Microsoft Edge, nella Home realtà mista di Windows. Controllare Windows Update o [installare manualmente la versione più recente di Windows 10](https://www.microsoft.com/software-download/windows10).

>[!IMPORTANT]
>Il nuovo Microsoft Edge viene avviato con supporto per WebXR, il nuovo standard per la creazione di esperienze Web Immersive per le cuffie VR. Se si installa il nuovo Microsoft Edge, non sarà più possibile riprodurre esperienze WebVR in Microsoft Edge.

### <a name="issues-with-the-new-microsoft-edge-in-windows-mixed-reality"></a>Problemi con il nuovo Microsoft Edge in realtà mista di Windows

**Problemi noti risolti dall'aggiornamento cumulativo 2020-01 per Windows 10 versione 1903 (o versioni successive)**

- L'avvio di qualsiasi app Win32, incluso il nuovo Microsoft Edge, causa un blocco breve della visualizzazione dell'auricolare.
- Il riquadro Microsoft Edge scompare dal menu Start della realtà mista di Windows (è possibile trovarlo nella cartella "app classiche").
- Windows dal Microsoft Edge precedente è ancora situato intorno alla Home realtà mista, ma non può essere usato. Il tentativo di attivare tali finestre viene avviato all'interno dell'app desktop.
- Selezionando un collegamento ipertestuale nella Home realtà mista viene avviato un Web browser sul desktop anziché la Home realtà mista.
- L'app WebVR Showcase è presente nella Home realtà mista, nonostante WebVR non sia più supportata.
- Miglioramenti generali al lancio da tastiera e agli oggetti visivi.

**Problemi noti aggiuntivi**

- I siti Web aperti in realtà mista di Windows andranno perduti quando si chiude il portale di realtà mista, anche se le finestre Microsoft Edge rimarranno nella posizione in cui sono state inserite nella Home realtà mista.
- L'audio da Microsoft Edge Windows non è spaziale.
- Correzione della versione dell'estensione del Visualizzatore 360 2.3.8: l'apertura di un video 360 da YouTube in realtà mista di Windows può comportare la distorsione del video nell'auricolare. Il riavvio di Edge dovrebbe aggiornare in modo invisibile l'estensione del Visualizzatore 360 per risolvere il problema. Per verificare quale versione dell'estensione è possibile immettere `edge://system/` nella barra degli indirizzi e selezionare il pulsante "Espandi" accanto a "estensioni".
- Durante le sessioni di realtà mista di Windows, i monitoraggi virtuali verranno visualizzati come monitoraggi fisici generici nelle **impostazioni > visualizzazione > di sistema**.

## <a name="launching-mixed-reality-after-the-first-time"></a>Avvio della realtà mista dopo la prima volta

La possibilità di entrare in realtà mista una seconda volta è semplice quanto riportare l'auricolare mentre è connesso al PC. È anche possibile avviare manualmente l'applicazione del portale per la realtà mista aprendola dal menu Start. L'input e l'audio verranno indirizzati automaticamente all'auricolare quando lo si inserisce. in alternativa, è possibile attivare questa impostazione manualmente premendo **Windows + Y** sulla tastiera.

## <a name="see-also"></a>Vedere anche

* [Contattare la community](https://answers.microsoft.com)
* [Contattaci per assistenza](https://support.microsoft.com/contactus/)
* [Risoluzione dei problemi relativi all'installazione](installation_errors.md)
* [Risoluzione dei problemi di installazione](set-up-questions.md)
* [Esercitazione per la realtà mista](learn-mixed-reality.md)
* [Funzionamento dei controller del movimento](controllers-in-wmr.md)
* [Funzionamento del tracciamento dall'interno verso l'esterno](tracking-system.md)
