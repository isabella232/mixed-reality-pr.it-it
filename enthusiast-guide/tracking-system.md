---
title: Funzionamento del tracciamento dall'interno verso l'esterno
description: Informazioni sul sistema di tracciamento interno basato su fotocamera usato nei visori WINDOWS MIXED REALITY visori VR.
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, inside-out, inside-out, tracciamento, fotocamera
ms.openlocfilehash: 579ef23c1eca2c184d07878c4e71ce298c5ad9922255b5e43643458a256b61bf
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197865"
---
# <a name="inside-out-tracking"></a>Tracciamento dall'interno verso l'esterno

## <a name="how-does-inside-out-tracking-work"></a>Come funziona il rilevamento inside-out?

**Risposta rapida: il** sistema di rilevamento usa due fotocamere a bassa risoluzione a luce visibile per osservare le funzionalità nell'ambiente in uso. Le fotocamere uniranno quindi le informazioni con i dati IMU per determinare una posizione precisa del dispositivo nell'ambiente.

**Altri dettagli:** Il sistema di rilevamento usa due fotocamere in bianco e nero a bassa risoluzione per identificare le caratteristiche dell'ambiente in luce visibile. Il sistema trilatere la propria posizione in base alle caratteristiche osservate, che quindi integra le informazioni fusing high rate IMU data to produce a continuous pose estimation for the HMD in your environment( Stima della posizione continua per l'HMD nell'ambiente in uso). Le informazioni sulla posizione vengono usate da entrambe le applicazioni per eseguire il rendering di una scena e dal sistema per correggere il rendering per eventuali stime erre nel tempo e nella posizione. Il PC archivia le informazioni sull'ambiente in modo che il sistema di rilevamento possa richiamare dati specifici dell'ambiente, ad esempio la posizione fisica dei limiti della stanza. Se si usa il dispositivo in più stanze, è possibile configurare limiti diversi in ogni stanza e il sistema di tracciamento può richiamare il limite specifico per la stanza specifica.

Poiché il monitoraggio Windows Mixed Reality visori VR immersive funziona come il rilevamento [Microsoft HoloLens](https://www.microsoft.com/en-us/hololens), può risultare utile questo video:

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="what-do-i-need-to-make-tracking-work-well"></a>Cosa è necessario per fare in modo che il rilevamento funzioni correttamente?

Esistono due problemi da risolvere per garantire che il monitoraggio funzioni correttamente:
1. Assicurarsi che il PC soddisfi i requisiti per l'esecuzione Windows Mixed Reality. Se il PC soddisfa i requisiti minimi per Windows Mixed Reality, il rilevamento avrà risorse sufficienti per l'esecuzione nel PC.
2. Assicurarsi che l'ambiente sia adatto al tipo di rilevamento visivo utilizzato dal dispositivo. È consigliabile usare il dispositivo in un ambiente con una luce sufficiente. Poiché il dispositivo funziona osservando l'ambiente nella luce visibile, deve essere presente una luce sufficiente per poter osservare l'ambiente. Per il funzionamento del sistema di rilevamento, è necessario che siano disponibili funzionalità visive di distinzione sufficienti(in altre parole, effetti, punti di contrasto e così via).

## <a name="how-much-light-is-enough-light"></a>Quanta luce è sufficiente?

Se è possibile spostarsi nell'ambiente senza che sia troppo scuro e se è possibile osservare le caratteristiche di altre persone che si trovano dall'altra parte della stanza, è probabile che il sistema di tracciamento abbia una luce sufficiente. Tenere presente che è presente una quantità di luce troppo grande. Se si guarda il sole, le fotocamere possono essere saturate e non vengono rilevate in modo affidabile. 

## <a name="what-is-the-recommended-number-of-environmental-features"></a>Qual è il numero consigliato di caratteristiche ambientali?

Il prodotto è stato progettato per funzionare in ambienti normali. Si consideri l'esperimento di pensare seguente: se ci si trovasse in una stanza vuota con pareti bianchi, un controsoffitto bianco e un piano bianco, il sistema di tracciamento non troverà funzionalità da tenere traccia e avrà esito negativo. Se ci si trovasse in una stanza coperta di arte e decorazione, il sistema di tracciamento troverà molte funzionalità da tenere traccia e funzionerà bene. In genere, le case e gli uffici decorati sono stati dimostrati con dettagli sufficienti per tenere traccia del meglio.

## <a name="how-fast-can-i-move-with-the-device"></a>Con quale velocità è possibile spostarsi con il dispositivo?

Il dispositivo è progettato per supportare il movimento in eccesso a quello normalmente riscontrato dal movimento della testa umana. È possibile spostarsi a PDE. Tieni presente che hai ridotto la consapevolezza dell'ambiente fisico in un visore VR immersive, quindi assicurati di spostarti in modo sicuro nell'ambiente.

## <a name="where-will-tracking-not-work"></a>Dove non funzionerà il rilevamento?

Il rilevamento non funzionerà in una stanza scura in cui le fotocamere non possono visualizzare funzionalità sufficienti a causa della luce bassa. Il tracciamento non funzionerà correttamente (o a volte funzionerà affatto) nei veicoli in movimento, ad esempio aerei, bus, veicoli, automobili o ascensori. Il rilevamento può avere esito negativo anche in situazioni in cui la luce è troppo leggera o una differenza di luce forte. Ad esempio, se è presente un flusso diretto di saturazioni in una stanza, le fotocamere possono ridurre l'esposizione per ridurre la saturazione e non vedono le normali caratteristiche naturali. È consigliabile attenersi a un'illuminazione relativamente uniforme e, se è necessario squitire o trovare qualcosa di poco intelligente, il sistema di tracciamento potrebbe non essere molto utile. 

## <a name="what-is-the-difference-between-3dof-and-6dof"></a>Qual è la differenza tra 3DOF e 6DOF?

In primo luogo, DOF è una scelta abbreviata per "gradi di libertà". Quando si esaminano i sistemi di rilevamento, ciò significa i gradi o i tipi di movimento che possono essere rilevati. Questi movimenti sono suddivisi in due categorie principali: "rotazione" e "rotazione con traslazione". 3DOF si riferisce a 3 gradi di libertà e rappresenta le rotazioni su ogni asse. In parole semplici, il rilevamento 3DOF consente di guardare a sinistra/destra, su/giù e inclinare la testa (rullo) da lato a lato. Non è possibile tradurre o andare avanti/indietro in 3DOF. 6DOF è l'abbreviato in 6 gradi di libertà. Si basa sulle rotazioni di 3DOF e aggiunge traduzioni. Ciò significa che è possibile spostarsi avanti/indietro, spostarsi verso sinistra/destra e accovacciarsi e alzarsi. Il rilevamento di tre dof è il tipo di rilevamento che in genere si trova in un telefono o in un prodotto VR basato su dispositivi mobili, mentre 6DOF è disponibile su piattaforme VR più potenti. Alcune esperienze sono personalizzate in base a 3DOF e consentiranno solo il movimento 3DOF (rotazioni), anche se il dispositivo supporta il rilevamento 6DOF. Un esempio è la visione di un video a 360 Windows Mixed Reality. Il video consentirà di guardarsi attorno, ma non di entrare nel proprio ambiente.

## <a name="things-are-jittering-or-stuttering-in-my-headset-is-my-tracking-not-working"></a>Le cose si instabilità o stuttering nel visore VR. Il rilevamento non funziona?

Esistono un paio di origini di questo tipo di errore. È importante attribuite ciò che si sta osservando alla causa giusta in modo che possa essere affrontata. Vedere la [sezione sulla risoluzione](tracking.md) dei problemi per comprendere il motivo per cui ciò potrebbe verificarsi.

## <a name="can-i-bring-my-own-tracking-technology-to-windows-mixed-reality"></a>È possibile usare la propria tecnologia di rilevamento per Windows Mixed Reality?

Questa funzionalità non è attualmente supportata.

## <a name="why-do-i-see-ui-that-says-cant-find-your-boundary"></a>Perché viene visualizzata l'interfaccia utente che indica "Non è possibile trovare il limite?"

Poiché il limite di sicurezza è specifico per una posizione fisica, se si usa il dispositivo in una posizione diversa, il sistema non è in grado di trovare i limiti. Inoltre, dopo aver configurato il limite, il sistema lo cerca sempre, anche se si usa il dispositivo in una posizione fisica diversa. Questa interfaccia utente verrà visualizzata ogni volta che si usa il dispositivo in una posizione diversa e non è ancora stato configurato un limite in tale posizione. È possibile configurare limiti in ogni posizione in cui si usa il dispositivo e il dispositivo richiama i limiti specifici della posizione.

Se si usa il dispositivo in una posizione in cui è stato configurato in precedenza un limite e il dispositivo non è ancora in grado di trovarlo, è possibile configurare un nuovo limite o cancellare tutti i dati dell'ambiente per rimuovere tutti i limiti dal dispositivo. Vedere la [sezione sulla](tracking.md) risoluzione dei problemi per comprendere perché il sistema non è in grado di trovare i limiti e i passaggi per correggerlo.

## <a name="how-do-i-set-up-tracking"></a>Ricerca per categorie configurare il rilevamento?

Tenere traccia Windows Mixed Reality è semplice da usare, non è necessaria alcuna infrastruttura o configurazione. Se si sceglie questa opzione, è possibile configurare un limite virtuale per l'uso. Per altre [informazioni, vedere la](set-up-windows-mixed-reality.md#set-up-your-room-boundary) sezione relativa alla configurazione del limite.

## <a name="how-do-i-clear-tracking-and-environment-data"></a>Ricerca per categorie dati di monitoraggio e dell'ambiente chiari?

Il sistema di rilevamento archivia alcuni dati dell'ambiente in modo da poter richiamare la posizione fisica reale di elementi come i limiti di sicurezza. Queste informazioni, inclusi i limiti di sicurezza, possono essere rimosse in qualsiasi momento. Se queste informazioni vengono rimosse, il sistema non riconoscerà più lo spazio o richiamirà i limiti di sicurezza. Se si vogliono usare i limiti di sicurezza dopo la cancellazione dei dati dell'ambiente, sarà necessario configurarlo di nuovo. Vedere la sezione sulla [configurazione del limite](set-up-windows-mixed-reality.md#set-up-your-room-boundary) per configurare un nuovo limite. Per rimuovere tutti questi dati, aprire Impostazioni, passare a "Realtà mista" e selezionare la sezione Ambiente del menu a sinistra. Selezionare il pulsante "Cancella dati ambiente" per rimuovere tutti i dati di ambiente e di rilevamento.

## <a name="see-also"></a>Vedi anche
* [Risoluzione dei problemi del sistema di rilevamento](tracking.md)
* [Controller del movimento](controllers-in-wmr.md)
* [Ambiente iniziale di Windows Mixed Reality](your-mixed-reality-home.md)
* [Uso di giochi e app in Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
