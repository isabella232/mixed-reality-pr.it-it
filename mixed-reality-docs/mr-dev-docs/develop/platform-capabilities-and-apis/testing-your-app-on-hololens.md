---
title: Test dell'app in HoloLens
description: Informazioni su indicazioni generali e suggerimenti per i test e l'ottimizzazione delle prestazioni HoloLens applicazioni di realtà mista.
author: jonmlyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, test
ms.openlocfilehash: 2f423560191fea8b516db80d533898b5a1f15973442e7bb6cd8878d486e0ffba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212099"
---
# <a name="testing-your-app-on-hololens"></a>Test dell'app in HoloLens

Il test HoloLens applicazioni è simile al test Windows applicazioni. È comunque necessario considerare funzionalità, interoperabilità, prestazioni, sicurezza, affidabilità e così via. Tuttavia, alcune aree che non vengono aperte nelle app per PC o telefoni richiedono una gestione speciale. Le app olografiche devono essere eseguite senza problemi in un set diversificato di ambienti. Devono anche mantenere le prestazioni e il comfort degli utenti in qualsiasi momento. Questa guida è utile per testare queste aree.

## <a name="performance"></a>Prestazioni

Le app olografiche devono essere eseguite senza problemi in un set diversificato di ambienti. Devono anche mantenere le prestazioni e il comfort degli utenti in qualsiasi momento. Le prestazioni sono così importanti per l'esperienza dell'utente con un'app holografica che è stato dedicato un intero argomento. Assicurarsi di leggere e seguire le informazioni [sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md)

## <a name="testing-3d-in-3d"></a>Test 3D in 3D

1. **Testare l'app nel maggior numero possibile di spazi diversi.** Provare in stanze di grandi dimensioni, stanze piccole, stanze da letto, stanze da letto, uffici e così via. Prendere in considerazione anche le stanze con caratteristiche non standard come le pareti non verticali, le pareti curve, i controsoffitti non orizzontali. Funziona bene quando si passa da una stanza all'altro, da un piano all'altro, da un ingresso all'altro o da una scala all'altro?
2. **Testare l'app in condizioni di illuminazione diverse.** Risponde correttamente a diverse condizioni ambientali, ad esempio illuminazione, superfici nere e superfici trasparenti o riflettenti come gli mirror e le pareti di vetro.
3. **Testare l'app in condizioni di movimento diverse.** Inserire il dispositivo e provare gli scenari in vari stati di movimento. Risponde correttamente a un movimento diverso o a uno stato stabile?
4. **Testare il funzionamento dell'app da angolazioni diverse.** Se si ha un ologramma bloccato dal mondo, cosa accade se l'utente si nasconde dietro di esso? Cosa accade se si verifica qualcosa tra l'utente e l'ologramma? Cosa succede se l'utente esamina l'ologramma dall'alto o dal basso?
5. **Usare segnali spaziali e audio.** Assicurarsi che l'app usi segnali spaziali e audio per impedire all'utente di perdersi.
6. **Testare l'app a diversi livelli di disturbo ambientale.** Se sono stati implementati comandi vocali, provare a richiamarli con diversi livelli di disturbo ambientale.
7. **Testare l'app seduti e in piedi.** Assicurarsi di testare sia da posizioni di posti a posto che da posizione in piedi.
8. **Testare l'app da distanze diverse.** Gli elementi dell'interfaccia utente possono essere letti e interagiti da lontano? L'app reagisce agli utenti che si avvicinano troppo agli ologrammi?
9. **Testare l'app in base alle interazioni comuni della barra dell'app.** Tutti i riquadri delle app e le app universali 2D hanno una barra [delle app](../../discover/navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) che consente di controllare la posizione delle app nel mondo misto. Assicurarsi che facendo clic su Rimuovi il processo dell'app termini correttamente e che il pulsante Indietro sia supportato nel contesto dell'app universale 2D. Provare a ridimensionare e spostare l'app [in](../../discover/navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) modalità Regolazione sia mentre è attiva che mentre è un riquadro dell'app sospeso.

### <a name="environmental-test-matrix"></a>Matrice di test ambientale

![Matrice di test dell'ambiente per HoloLens di app](images/environment-matrix-600px.png)

## <a name="comfort"></a>Comfort

1. **Piani di ritaglio.** Prestare attenzione alla posizione [in cui viene eseguito il rendering degli ologrammi.](hologram-stability.md#hologram-render-distances)
2. **Evitare lo spostamento virtuale incoerente con lo spostamento effettivo della testa.** Evitare di spostare la fotocamera in modo che non sia rappresentativo del movimento effettivo dell'utente. Se l'app richiede lo spostamento dell'utente attraverso una scena, rendere il movimento prevedibile, ridurre al minimo l'accelerazione e consentire all'utente di controllare lo spostamento.
3. **Seguire le linee guida sulla qualità degli ologrammi.** Le app performanti che implementano le linee guida sulla qualità [degli ologrammi](hologram-stability.md) hanno meno probabilità di causare disagio per l'utente.
4. **Distribuire gli ologrammi orizzontalmente anziché verticalmente.** Forzare l'utente a dedicare lunghi periodi di tempo alla ricerca verso l'alto o verso il basso può causare affaticamento al collo.

## <a name="input"></a>Input

### <a name="interaction-models"></a>Modelli di interazione

Assicurarsi che le interazioni ologramma funzionino con il modello di [interazione scelto.](../../design/interaction-fundamentals.md)
È anche buona idea convalidare con diversi accessori, ad esempio mouse e tastiera, se sono necessari per supportare l'accessibilità.

**Convalidare quando l'app ha un comportamento diverso con il mouse e il tocco.** Identifica le incoerenze e aiuta a prendere decisioni di progettazione per rendere l'esperienza più naturale per gli utenti. Ad esempio, l'attivazione di un'azione in base al passaggio del mouse.


### <a name="custom-voice-commands"></a>Comandi vocali personalizzati

[L'input](../../design/voice-input.md) vocale è una forma naturale di interazione. L'esperienza utente può essere magica o confusa a seconda della scelta dei comandi e del modo in cui vengono esposti. Come regola generale, non è consigliabile usare comandi vocali di sistema come "Seleziona" o "Hey Cortana" come comandi personalizzati. Ecco alcuni punti da considerare:
1. **Evitare di usare comandi simili.** Può potenzialmente attivare il comando non corretto.
2. **Se possibile, scegliere parole foneticamente ricche.** Riduce al minimo e/o evita false attivazioni.

### <a name="peripherals"></a>Periferiche

Gli utenti possono interagire con l'app [tramite periferiche](../../discover/hardware-accessories.md). Le app non devono fare nulla di speciale per sfruttare questa funzionalità, ma è opportuno controllare un paio di elementi.
1. **Convalidare le interazioni personalizzate.** Come i tasti di scelta rapida personalizzati per l'app.
2. **Convalidare il cambio di tipi di input.** Tentativo di usare più metodi di input per completare un'attività, ad esempio voce, movimento, mouse e tastiera, tutti nello stesso scenario.

## <a name="system-integration"></a>Integrazione del sistema

### <a name="battery"></a>Batteria

Testare l'applicazione senza una fonte di alimentazione connessa per comprendere la velocità con cui svuota la batteria. È possibile comprendere facilmente lo stato della batteria esaminando le letture dei LED di alimentazione. 

![Stati LED che indicano l'alimentazione della batteria](images/batterypowerledindication-500px.png)<br>

*Stati LED che indicano l'alimentazione della batteria*

### <a name="power-state-transitions"></a>Transizioni dello stato di alimentazione

Gli scenari chiave di convalida funzionano come previsto durante la transizione tra stati di alimentazione. Ad esempio, l'applicazione rimane nella posizione originale? Il relativo stato viene mantenuto correttamente? Continua a funzionare come previsto?
1. **Stand-by/Resume.** Per entrare in standby, è possibile premere e rilasciare immediatamente il pulsante di alimentazione. Il dispositivo entra automaticamente in standby anche dopo 3 minuti di inattività. Per riprendere dalla modalità standby, è possibile premere e rilasciare immediatamente il pulsante di alimentazione. Il dispositivo riprenderà anche se lo si connette o si disconnette da una fonte di alimentazione.
2. **Arresto/riavvio.** Per arrestare il sistema, tenere premuto il pulsante di alimentazione in modo continuo per 6 secondi. Per riavviare, premere il pulsante di accensione.

### <a name="multi-app-scenarios"></a>Scenari multi-app

Convalidare le funzionalità principali delle app quando si passa da un'app all'altra, soprattutto se è stata implementata un'attività in background. Anche l'integrazione Cortana copia/incolla è opportuno verificare dove applicabile.

## <a name="telemetry"></a>Telemetria

Usare la telemetria e l'analisi per guidare l'utente. L'integrazione dell'analisi nell'app consente di ottenere informazioni dettagliate sull'app dai tester beta e dagli utenti finali. Questi dati possono essere usati per ottimizzare l'app prima dell'invio a Store e per gli aggiornamenti futuri. Sono disponibili molte opzioni di analisi. Se non si è certi di dove iniziare, vedere [App Insights](https://www.visualstudio.com/products/application-insights-vs.aspx).

Domande da considerare:
1. In che modo gli utenti usano lo spazio?
2. In che modo l'app inserisce oggetti nel mondo: è possibile rilevare i problemi?
3. Quanto tempo impiegano nelle diverse fasi dell'applicazione?
4. Quanto tempo impiegano nell'app?
5. Quali sono i percorsi di utilizzo più comuni che gli utenti stanno provando?
6. Gli utenti stanno per raggiungere stati o errori imprevisti?

## <a name="emulator-and-simulated-input"></a>Emulator input simulato

[L HoloLens emulatore](using-the-hololens-emulator.md) è un ottimo modo per testare in modo efficiente l'app Holographic con diversi tipi di caratteristiche utente simulate e spazi. Ecco alcuni suggerimenti per usare in modo efficace l'emulatore per testare l'app:
1. **Usare le stanze virtuali dell'emulatore per espandere i test.** L'emulatore include un set di stanze virtuali che è possibile usare per testare l'app in un numero ancora maggiore di ambienti.
2. **Usare l'emulatore per esaminare l'app da tutte le angolazioni.** Le chiavi PageUp/PageDn renderanno l'utente simulato più alto o più breve.
3. **Testare l'app con una HoloLens.** Il HoloLens Emulator è un ottimo strumento che consente di eseguire rapidamente l'iterazione di un'app e rilevare nuovi bug, ma assicurarsi di testare anche un HoloLens fisico prima di inviarlo a Windows Store. Questo è importante per garantire che le prestazioni e l'esperienza siano ottimali per l'hardware reale.

## <a name="automated-testing-with-perception-simulation"></a>Test automatizzati con la simulazione della percezione

Alcuni sviluppatori di app potrebbero voler automatizzare i test delle app. Oltre ai semplici unit test, è possibile usare lo [stack](perception-simulation.md) di simulazione della percezione in HoloLens per automatizzare l'input umano e mondiale per l'app. L'API di simulazione della percezione può inviare input simulato all'emulatore HoloLens o a un dispositivo HoloLens.

## <a name="windows-app-certification-kit"></a>Kit di certificazione app Windows

Per offrire all'app la migliore possibilità di essere pubblicata in [Windows Store,](../../distribute/submitting-an-app-to-the-microsoft-store.md)convalidarla e testarla in locale prima di inviarla per la certificazione. Se l'app è destinata al Windows. Famiglia di dispositivi olografici, Windows [kit](/windows/uwp/debug-test-perf/windows-app-certification-kit) di certificazione app eseguirà solo test di analisi statica locali nel PC. Non verrà eseguito alcun test nel HoloLens.

## <a name="see-also"></a>Vedi anche

* [Invio di un'app a Windows Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)