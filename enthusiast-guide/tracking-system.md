---
title: Funzionamento del tracciamento dall'interno verso l'esterno
description: Informazioni sul sistema di rilevamento basato su fotocamera, interno esterno usato negli auricolari per la realtà mista di Windows.
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, Inside-out, Inside out, tracking, videocamera
ms.openlocfilehash: a91b5fba399e9bb328fd579811a64aee03b49efd
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174335"
---
# <a name="inside-out-tracking"></a>Rilevamento interno

## <a name="how-does-inside-out-tracking-work"></a>Funzionamento del rilevamento interno

**Risposta rapida:** il sistema di rilevamento usa due fotocamere a bassa risoluzione visibili per osservare le funzionalità nell'ambiente e fonde queste informazioni con i dati di IMU per determinare una posizione precisa del dispositivo nell'ambiente in uso.

**Altri dettagli:** Il sistema di rilevamento usa due fotocamere nere e bianche a bassa risoluzione per identificare le funzionalità nell'ambiente in chiaro. Il sistema effettuerà la triangolazione della posizione in base alle funzionalità osservate e completerà queste informazioni fondendo i dati IMU a frequenza elevata per produrre una stima di posa continua per HMD nell'ambiente in uso. Le informazioni sulla posizione vengono usate da entrambe le applicazioni per eseguire il rendering di una scena e dal sistema per correggere il rendering per qualsiasi stima errata nel tempo e nella posizione. Le informazioni sull'ambiente sono archiviate nel PC, in modo che il sistema di rilevamento possa richiamare i dati specifici dell'ambiente, ad esempio la posizione fisica del limite nella chat room. Se si usa il dispositivo in più chat, è possibile configurare limiti diversi in ogni stanza e il sistema di rilevamento potrà richiamare il limite specifico per la stanza specifica.

Dal momento che il rilevamento degli auricolari per la realtà mista di Windows funziona come il monitoraggio in [Microsoft HoloLens](https://www.microsoft.com/en-us/hololens), questo video può risultare utile:

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="what-do-i-need-to-make-tracking-work-well"></a>Cosa devo fare per tenere traccia del lavoro?

È necessario risolvere due problemi per garantire che il rilevamento funzioni correttamente:
1. Verificare che il PC soddisfi i requisiti per l'esecuzione di realtà mista di Windows. Se il PC soddisfa i requisiti minimi per la realtà mista di Windows, il rilevamento avrà risorse sufficienti per essere eseguito correttamente nel PC.
2. Assicurarsi che l'ambiente sia adatto per il tipo di rilevamento visivo utilizzato dal dispositivo. È consigliabile usare il dispositivo in un ambiente con una luce sufficiente. Poiché il dispositivo funziona osservando l'ambiente con la luce visibile, è necessario che la luce sia sufficiente per poter osservare l'ambiente. Per il corretto funzionamento del sistema di rilevamento è inoltre necessario distinguere le funzionalità visive (in altre parole, decorazioni, punti di contrasto e così via).

## <a name="how-much-light-is-enough-light"></a>Quanto luce è sufficiente?

Una regola empirica è costituita dal fatto che, se si è in grado di spostarsi nell'ambiente senza ritenere che sia troppo scuro e se è possibile osservare le funzionalità di un'altra persona da tutta la stanza, è probabile che il sistema di rilevamento disponga di una luce sufficiente.

## <a name="what-is-the-recommended-amount-of-environmental-features"></a>Qual è la quantità consigliata di funzionalità ambientali?

Il prodotto è stato progettato per funzionare in ambienti normali. Si consideri l'esperimento di riflessione seguente: se ci si trova in una stanza completamente vuota (muri bianchi, soffitto bianco, piano bianco), il sistema di rilevamento non troverà alcuna funzionalità da rilevare e avrà esito negativo. Se ci si trovava in una stanza coperta da lavoro artistico e decorazione, il sistema di rilevamento avrebbe trovato molte funzionalità da tenere traccia e funzionerebbe bene. Nella maggior parte dei casi, le sedi e gli uffici decorati sono stati dimostrati in modo da avere un numero sufficiente di dettagli sulle funzionalità.

## <a name="how-fast-can-i-move-with-the-device"></a>Con quale velocità è possibile spostarsi con il dispositivo?

Il dispositivo è progettato per supportare il movimento in eccesso rispetto a quello normalmente sperimentato dal movimento della testa umana. È possibile passare a. Si tenga presente che, in caso di un auricolare immersivo, è stata ridotta la consapevolezza dell'ambiente fisico, quindi è necessario assicurarsi di passare al proprio ambiente.

## <a name="where-will-tracking-not-work"></a>Dove il rilevamento non funziona?

Il rilevamento non funzionerà in una stanza scura in cui le fotocamere non saranno in grado di visualizzare le funzionalità sufficienti a causa di una scarsa luminosità. Il rilevamento in genere non viene eseguito correttamente (o a volte funziona) in veicoli mobili come aeroplani, bus, treni, automobili o ascensori.

## <a name="what-is-the-difference-between-3dof-and-6dof"></a>Qual è la differenza tra 3DOF e 6DOF?

In primo luogo, DOF è la parte più breve per "gradi di libertà". Quando si discutono i sistemi di rilevamento, questo significa i gradi o i tipi di spostamento che possono essere rilevati. Questi movimenti sono suddivisi in due categorie principali: "Rotation" e "Rotation with translation". 3DOF fa riferimento a 3 gradi di libertà e rappresenta le rotazioni relative a ogni asse. In poche parole, 3DOF Tracking consente di cercare verso sinistra/destra, verso l'alto o verso il basso e inclinare il lato destro del mouse. Non è possibile tradurre o andare avanti/indietro in 3DOF. 6DOF è breve per 6 gradi di libertà. Si basa sulle rotazioni di 3DOF e aggiunge le traduzioni it. Ciò significa che è possibile spostarsi in avanti e indietro, Strafe a sinistra/destra e accovacciarsi. 3 il rilevamento è il tipo di rilevamento che in genere si trova in un prodotto VR basato su telefono o per dispositivi mobili, mentre 6DOF sarà disponibile su piattaforme VR più potenti. Alcune esperienze sono personalizzate per 3DOF e consentiranno solo 3DOF Motion (rotazioni), anche se il dispositivo supporta il rilevamento del 6DOF. Un esempio di questo problema sarebbe guardare un video di 360 in realtà mista di Windows. Il video consentirà di individuare ma non consentirà di passare all'ambiente.

## <a name="things-are-jittering-or-stuttering-in-my-headset-is-my-tracking-not-working"></a>Si tratta di un aspetto più nervoso o balbettante nell'auricolare. Il mio rilevamento non funziona?

Sono presenti due origini di questo tipo di errore. È importante essere in grado di attribuire ciò che si sta osservando alla giusta ragione, in modo che possa essere risolta. Vedere la sezione relativa alla [risoluzione dei problemi](tracking.md) per comprendere il motivo per cui è possibile che si verifichi questo problema.

## <a name="can-i-bring-my-own-tracking-technology-to-windows-mixed-reality"></a>Posso importare la mia tecnologia di rilevamento per la realtà mista di Windows?

Questa opzione non è attualmente supportata.

## <a name="why-do-i-see-ui-that-says-cant-find-your-boundary"></a>Perché viene visualizzata l'interfaccia utente che indica che "non è possibile trovare il limite?"

Poiché il limite di sicurezza è specifico di una posizione fisica, se si usa il dispositivo in un percorso diverso, il sistema non sarà in grado di trovare i limiti. Inoltre, dopo aver configurato il limite, il sistema lo cercherà sempre, anche se si usa il dispositivo in una posizione fisica diversa. Questa interfaccia utente verrà visualizzata ogni volta che si usa il dispositivo in un percorso diverso e non è ancora stato configurato un limite in tale percorso. È possibile configurare i limiti in ogni posizione in cui si usa il dispositivo e il dispositivo richiamerà i limiti specifici della località.

Se si usa il dispositivo in un percorso precedentemente configurato, il dispositivo non riesce a trovarlo, è possibile configurare un nuovo limite oppure deselezionare tutti i dati dell'ambiente per rimuovere tutti i limiti dal dispositivo. Vedere la sezione relativa alla [risoluzione dei problemi](tracking.md) per comprendere il motivo per cui il sistema non è in grado di individuare i limiti e i passaggi per correggerli.

## <a name="how-do-i-set-up-tracking"></a>Ricerca per categorie configurare il rilevamento?

Il rilevamento in realtà mista di Windows è semplice da usare. Non è necessaria alcuna infrastruttura o configurazione e il dispositivo non funzionerà più. Se si sceglie di, è possibile configurare un limite virtuale da usare. Per ulteriori informazioni, vedere la sezione relativa alla [configurazione del limite](set-up-windows-mixed-reality.md#set-up-your-room-boundary) .

## <a name="how-do-i-clear-tracking-and-environment-data"></a>Ricerca per categorie cancellare i dati di rilevamento e dell'ambiente?

Il sistema di rilevamento archivia alcuni dati dell'ambiente in modo da poter richiamare la posizione fisica del mondo reale di elementi come i limiti di sicurezza. Queste informazioni, inclusi i limiti di sicurezza, possono essere rimosse in qualsiasi momento. Se queste informazioni vengono rimosse, il sistema non rileverà più lo spazio o potrà richiamare i limiti di sicurezza. Se si vogliono usare i limiti di sicurezza dopo aver cancellato i dati dell'ambiente, sarà necessario configurarli di nuovo. Vedere la sezione relativa alla [configurazione dei limiti](set-up-windows-mixed-reality.md#set-up-your-room-boundary) per configurare un nuovo limite. Per rimuovere tutti i dati, aprire Impostazioni, passare a "realtà mista" e selezionare la sezione ambiente nel menu a sinistra. Fare clic sul pulsante "Cancella dati ambiente" per rimuovere tutti i dati relativi all'ambiente e al rilevamento.

## <a name="see-also"></a>Vedere anche
* [Risoluzione dei problemi del sistema di rilevamento](tracking.md)
* [Funzionamento dei controller del movimento](controller-in-wmr.md)
* [Ambiente iniziale di Windows Mixed Reality](your-mixed-reality-home.md)
* [Uso di giochi e app in realtà mista di Windows](using-games-and-apps-in-windows-mixed-reality.md)
