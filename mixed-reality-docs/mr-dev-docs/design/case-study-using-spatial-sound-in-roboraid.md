---
title: Case study - Uso dell'audio spaziale in RoboRaid
description: L'audio spaziale è una delle funzionalità più interessanti Microsoft HoloLens, consentendo agli utenti di capire cosa succede intorno a loro quando gli oggetti non sono di vista.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, RoboRaid, audio spaziale, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, HoloLens, MRTK, Realtà mista Toolkit, CPU
ms.openlocfilehash: f4a47fe119dffbd32d264cc8e21ae2b3ade7cfcccef8e7e18fbb4491783d0542
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209001"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>Case study - Uso dell'audio spaziale in RoboRaid

Questo articolo descrive le problematiche affrontate Microsoft HoloLens experience team durante la creazione di audio per la prima persona di [RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) in realtà mista.

## <a name="the-tech"></a>La tecnologia

[L'audio](spatial-sound.md) spaziale è una delle funzionalità più interessanti di Microsoft HoloLens, consentendo agli utenti di capire cosa succede intorno a loro quando gli oggetti non sono in vista.

In RoboRaid, l'uso più ovvio ed efficace del suono spaziale è avvisare il giocatore di qualcosa che accade al di fuori della loro visione periferica. Ad esempio, il violatore può entrare da una qualsiasi delle pareti digitalizzate nella stanza. Se non si è di fronte alla posizione in cui si sta immettendo, è possibile che si perdi. Per avvisare l'utente di questa violazione, si udirà una parte distinta di audio proveniente dal punto in cui entra il violatore, che consente di sapere che è necessario agire rapidamente per arrestarlo.

## <a name="behind-the-scenes"></a>Dietro le quinte

La creazione di audio spaziale HoloLens app è così nuova e unica che i problemi possono essere difficili da risolvere perché non ci sono progetti precedenti a cui fare riferimento. Questi esempi di problemi audio che abbiamo dovuto affrontare durante la creazione di RoboRaid saranno utili per creare audio per le tue app.

### <a name="be-mindful-of-taxing-the-cpu"></a>Tenere conto dell'imposta sulla CPU

L'audio spaziale può essere impegnativo per la CPU. Per un'esperienza impegnativa come RoboRaid, era fondamentale mantenere il numero di istanze del suono spaziale a meno di otto in un determinato momento. In genere è stato facile impostare il limite di istanze per eventi audio diversi. Tutte le istanze che si verificano dopo che è stato raggiunto il limite vengono raggiunte. Ad esempio, quando vengono generati i droni, le relative istanze sono limitate a tre istanze in un determinato momento. Considerando che possono essere generati solo quattro droni contemporaneamente, tre sono molti perché il cervello non è in grado di tenere traccia di molti eventi audio simili. In questo modo sono state liberate risorse per altri eventi sonori spaziali, ad esempio le defezioni degli avversari o le difficoltà che si preparano alla preparazione.

### <a name="rewarding-a-successful-dodge"></a>Ricompensa di un gruppo di successo

Il meccanismo di dodging è uno dei meccanismi di gioco più importanti di RoboRaid e anche qualcosa che abbiamo ritenuto davvero unico per l'esperienza HoloLens lavoro. Di conseguenza, abbiamo voluto rendere i giocatori molto gratificanti per il giocatore. Abbiamo ottenuto il "whizz-by" di Doppler per sembrare interessante nelle prime fasi dello sviluppo. Inizialmente, il mio piano era usare un ciclo e modificarlo in tempo reale usando volume, tono e filtro. L'implementazione per questa operazione sarebbe stata molto elaborata. Prima di eseguire il commit delle risorse per creare questo progetto, è stato creato un prototipo economico usando un asset con l'effetto Doppler di cui è stato creato il bake per scoprire come si è percepito. Lo sviluppatore di speaker ha fatto in modo che questo asset whizz-by riprodusse esattamente 0,7 secondi prima che il progettoile fosse passato dall'ascolto del giocatore e i risultati risultavano straordinari. È inutile dire che è stata disassociata la soluzione più complessa ed è stato implementato il prototipo.

*Per altre informazioni sulla creazione di un asset audio con l'effetto Doppler incorporato, vedere [100 Whooshes in 2 Minutes (100 Whooshes in 2 minuti).](http://designingsound.org/2010/02/26/charles-deenen-special-100-whooshes-in-2-minutes/)* 
<br>
![Una corretta esezione del progetto dell'avversario premia il giocatore con un suono di soffio soddisfacente.](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>Ditching di suoni inefficaci

In origine, si voleva riprodurre un suono dell'esplosione dietro il giocatore dopo che il giocatore ha eseguito con successo il progettoile dell'avversario, ma si è deciso di buttarlo per diversi motivi. In primo luogo, non si è sentito efficace come il SFX di whizz-by usato per la partita. Nel momento in cui il proiettore raggiunge una barriera dietro di te, sarebbe successo qualcosa di diverso nel gioco che mascherava il suono. In secondo momento, non si è verificata una collisione sul terreno, quindi non è stato possibile riprodurre l'esplosione quando il progettoile ha raggiunto il piano invece che le pareti. Infine, c'era il costo della CPU per l'audio spaziale. L'avversario dell'eta' (uno che può entrare nella barriera) ha un attacco speciale che schegge circa otto proiettori. Non solo ha fatto un grande confusione nella combinazione, ma ha anche introdotto un crepitare che causava un uso eccessivo della CPU.

### <a name="communicating-a-hit"></a>Comunicazione di un hit

Un problema interessante che si è verificato nel HoloLens era la difficoltà di comunicare in modo efficace che un giocatore era stato raggiunto. Ciò che consente a un'esperienza di realtà mista di avere successo è la impressione che la storia stia avvenendo. Ciò significa che si deve essere in grado di contrastare un robot robot nel proprio living room.

I giocatori ovviamente non provano nulla quando vengono sconsciati, quindi abbiamo dovuto trovare un modo per convincire il giocatore che si è verificato qualcosa di negativo. Nei giochi convenzionali è possibile che venga visualizzata un'animazione che consente di sapere che il tuo carattere ha avuto un successo o che lo schermo potrebbe lampeggiare in rosso e il tuo carattere potrebbe essere un po' grugnito. Poiché questi tipi di segnali non funzionano in un'esperienza di realtà mista, abbiamo deciso di combinare il segnale visivo con un suono danneggiato che indica che hai subito danni. Ho creato un suono grande e lo ho reso così evidente nella combinazione che ha evitato tutto. Quindi, per renderlo ancora più in vista, è stato aggiunto un breve suono di avviso come se un sub fosse in sink. 
<br>
![Quando un giocatore viene raggiunto in RoboRaid, vede un segnale visivo, ma anche un segnale audio danneggiato che indica di aver subito danni.](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>Ottenere un suono di grandi dimensioni da piccoli altoparlanti

HoloLens altoparlanti sono piccoli e leggeri per soddisfare le esigenze del dispositivo, quindi non ci si può aspettare di ascoltare troppo low-end. Analogamente allo sviluppo per smartphone o dispositivi di gioco per dispositivi di gioco, i progettisti di suoni e i compositori devono tenere presente il contenuto della frequenza dell'audio. Si progettano sempre suoni o si scrive musica con una gamma di frequenza completa, perché le cuffie sono un'opzione per gli utenti. Tuttavia, per garantire la compatibilità con i parlanti HoloLens, si esegue occasionalmente un test inserendo un EQ nel master di qualsiasi daw in cui si sta lavorando. L'impostazione EQ è costituita da un filtro ad alta velocità di circa 600 Hz a 700 Hz (non troppo alto) e da un filtro a passi bassi a circa 10.000 (hz). Questo dovrebbe dare un'idea approssimativa del modo in cui i suoni verranno riprodotti nel dispositivo.

Se ci si affida alla musica per dare il senso di cambiare la musica, è possibile che la musica perda completamente il senso della radice quando si applica questa impostazione EQ. Per risolvere questo problema, ho aggiunto un altro livello al suono che è un'ottave più in alto (con alcuni elementi armenici) e lo ho misto per ottenere il senso della radice. In alcuni casi l'uso della distorsione per ampliare le armenie offrirà un contenuto di frequenza sufficiente nell'intervallo superiore per far pensare al cervello che ci sia qualcosa sotto di esso. Questo vale per SFX, ad esempio gli effetti, le esplosione o i suoni per momenti speciali, ad esempio i super attacchi di un capo. In realtà non è possibile affidarsi all'estremità bassa per dare al giocatore un'idea di impatto o peso. Come per la musica, l'uso della distorsione per dare un po' di aiuto è stato sicuramente utile.

### <a name="making-your-audio-cues-stand-out"></a>Fare in modo che i segnali audio si disaltino

Naturalmente, tutti i membri del team desiderano musica mista, forte rumore ed emotiosi; ma voleva anche essere in grado di ascoltare il voiceover o qualsiasi altro segnale audio critico per il gioco.

In un gioco di console con una gamma completa di frequenze, sono disponibili più opzioni per dividere le frequenze in base all'importanza del suono. Per RoboRaid, il numero di intervalli di frequenze che era possibile curvare dai suoni era limitato. Se si usa un filtro a passaggio basso e si esce troppo dall'estremità superiore dello spettro, non sarà rimasto nulla sul suono perché non c'è molto di fascia bassa.

Per far sembrare RoboRaid il più grande possibile sul dispositivo, è stato necessario ridurre la gamma dinamica dell'intera esperienza e fare ampio uso dell'aratro creando una chiara gerarchia di importanza per diversi tipi di suoni. Ho impostato l'accoltellamento da -2 dB a -6 dB a seconda dell'importanza. Personalmente non mi piace l'ovvio gioco, quindi ho dedicato molto tempo all'ottimizzazione del tempo di dissolvenza in entrata/uscita e della quantità di attenuazione del volume. Sono stati impostati bus separati per l'audio spaziale, l'audio non spaziale, il VO e il bus a terra senza riverbero per la musica. Sono stati quindi creati bus con priorità alta, critici e non critici, in modo che gli asset fossero stati impostati per passare ai bus appropriati.

Mi auguriamo che i professionisti audio si divertino e si divertino a lavorare sulle proprie app come ho fatto con RoboRaid. Non vediamo l'ora di vedere (e ascoltare) ciò che gli speaker di Microsoft non hanno bisogno di HoloLens.

## <a name="do-it-yourself"></a>Provare

Un espeditto che ho scoperto per rendere "più grandi" determinati eventi (ad esempio le deflazioni), come stanno riempiendo la stanza, era quello di creare un asset mono per l'audio spaziale e combinarlo con un asset stereo 2D, da riprodurre in 3D. È necessario un po' di ottimizzazione, perché la presenza di troppe informazioni nel contenuto stereo consente di ridurre la direzionalità degli asset mono. Tuttavia, ottenere il giusto equilibrio comporta suoni enormi che permetteranno ai giocatori di ruotare la testa nella direzione giusta.

È possibile provare i suoni più grandi usando gli asset audio seguenti:

**Scenario 1**
1. Scaricare [roboraid_enemy_explo_mono.wav](images/roboraid-enemy-explo-mono.wav) e impostare per riprodurre l'audio spaziale e assegnarlo a un evento.
2. Scaricare [roboraid_enemy_explo_stereo.wav](images/roboraid-enemy-explo-stereo.wav) e impostare per la riproduzione in stereo 2D e assegnare allo stesso evento come sopra. Poiché questi asset vengono normalizzati in Unity, attenuare il volume di entrambi gli asset in modo che non si ritagliano.
3. Riprodurre entrambi i suoni insieme. Sposta la testa per avere un'acustica spaziale.

**Scenario 2**
1. Scaricare [roboraid_enemy_explo_summed.wav e](images/roboraid-enemy-explo-summed.wav) impostare per riprodurre l'audio spaziale e assegnarlo a un evento.
2. Riprodurre questo asset da solo e quindi confrontarlo con l'evento dello scenario 1.
3. Provare un equilibrio diverso tra file mono e stereo.

## <a name="see-also"></a>Vedi anche

* [Audio spaziale](spatial-sound.md)
* [RoboRaid per Microsoft HoloLens](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
