---
title: Case Study-uso di un suono spaziale in RoboRaid
description: Il suono spaziale è una delle funzionalità più interessanti di Microsoft HoloLens, consentendo agli utenti di percepire gli elementi che interessano quando gli oggetti sono fuori controllo.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HoloLens, RoboRaid, suono spaziale, auricolare realtà mista, cuffia a realtà mista di Windows, auricolare realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, CPU
ms.openlocfilehash: 95650ea7097f16d257c80c11443b84936bece435
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847543"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>Case Study-uso di un suono spaziale in RoboRaid

Questo articolo descrive le sfide del team di Microsoft HoloLens Experience per la creazione di audio per il primo sparatutto in realtà mista [RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) .

## <a name="the-tech"></a>Il Tech

Il [suono spaziale](spatial-sound.md) è una delle funzionalità più interessanti di Microsoft HoloLens, che consente agli utenti di percepire gli elementi che interessano quando gli oggetti non sono in linea.

In RoboRaid, l'uso più ovvio ed efficace del suono spaziale sta inviando un avviso al lettore a un evento che si verifica all'esterno della loro visione periferica. Ad esempio, il violatore può entrare da qualsiasi parete analizzata della stanza. Se non si sta per accedere alla posizione in cui si trova, è possibile che venga persa. Per avvertire l'utente di questa invasione, si riceverà un po' di audio distinto proveniente dal punto in cui si sta immettendo la violazione, che indica che è necessario agire rapidamente per arrestarlo.

## <a name="behind-the-scenes"></a>Dietro le quinte

La creazione di un suono spaziale per le app HoloLens è così nuova e univoca che i problemi possono essere difficili da risolvere perché non ci sono progetti precedenti a cui fare riferimento. Ci auguriamo che questi esempi di problemi audio che abbiamo affrontato durante l'esecuzione di RoboRaid ti aiuteranno a creare audio per le tue app.

### <a name="be-mindful-of-taxing-the-cpu"></a>Tenere conto della tassazione della CPU

Il suono spaziale può richiedere la CPU. Per un'esperienza frenetica come RoboRaid, era fondamentale evitare che il numero di istanze di suoni spaziali fosse inferiore a otto in un determinato momento. In genere, è semplice come impostare il limite di istanze per eventi audio diversi. Tutte le istanze che si verificano dopo il raggiungimento del limite vengono terminate. Ad esempio, quando i droni generano, i loro Scream sono limitati a tre istanze in un determinato momento. Considerando che solo quattro droni possono generare una sola volta, tre Scream sono molto perché non è possibile tenere traccia di molti eventi audio simili. In questo modo sono state liberate risorse per altri eventi audio spaziali, ad esempio esplosioni nemiche o nemici che si preparano a sparare.

### <a name="rewarding-a-successful-dodge"></a>Soddisfazione di una Dodge riuscita

Il meccanico che si sta evitando è uno dei più importanti meccanismi di gioco in RoboRaid, oltre a una cosa che abbiamo ritenuto realmente univoca per l'esperienza HoloLens. Di conseguenza, volevamo che le Dodge fossero molto gratificanti per il lettore. È stato ottenuto il "mago" di Doppler per sembrare piuttosto tempestivo in fase di sviluppo. Inizialmente, il mio piano consisteva nell'usare un ciclo e modificarlo in tempo reale usando volume, pitch e Filter. L'implementazione di questa operazione è stata molto elaborata. Prima di eseguire il commit delle risorse per compilarlo, abbiamo creato un prototipo a basso costo usando un asset con effetto Doppler cotto in solo per scoprirne il funzionamento. Lo sviluppatore di talento lo ha fatto in modo che questo asset venga riprodotto esattamente 0,7 secondo prima che il proiettile fosse passato dall'orecchio del giocatore e i risultati fossero straordinarii. Inutile dirlo, abbiamo abbandonato la soluzione più complessa e implementato il prototipo.

*Per altre informazioni sulla creazione di un asset audio con l'effetto Doppler incorporato, vedere [100 Whooshes in 2 minuti](http://designingsound.org/2010/02/26/charles-deenen-special-100-whooshes-in-2-minutes/).* 
<br>
![Il tentativo di schivare il proiettile del nemico premia il lettore con un suono che soddisfa le esigenze.](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>Ammaraggio di suoni inefficaci

Originariamente, avevamo voluto riprodurre un suono di esplosione dietro il lettore una volta che il proiettile nemico è stato schivato, ma abbiamo deciso di abbandonarlo per diversi motivi. In primo luogo, non si riteneva così efficace come il mago-by SFX usato per Dodge. Nel momento in cui il proiettile raggiunge un muro dietro l'altro, si sarebbe verificato un altro problema nel gioco che mascherava tale suono. In secondo luogo, non abbiamo avuto collisioni sul pavimento, quindi non riuscivamo a far giocare l'esplosione quando il proiettile raggiungeva il pavimento anziché i muri. Infine, c'era il costo della CPU del suono spaziale. L'Elite Scorpion Enemy (uno che può eseguire la ricerca per indicizzazione all'interno della parete) ha un attacco speciale che spara circa otto proiettili. Non solo questa situazione ha comportato una grande confusione nella combinazione, ma ha anche introdotto una terribile incrinatura perché la CPU era troppo complessa.

### <a name="communicating-a-hit"></a>Comunicazione di un riscontro

Un problema interessante che abbiamo incontrato in HoloLens è stato la difficoltà di comunicare efficacemente che un giocatore era stato raggiunto. Ciò che rende un'esperienza di realtà mista riuscita è la sensazione che la storia si sta verificando. Ciò significa che è necessario ritenere che si stia combattendo un'invasione di robot alieni nel proprio salotto.

Ovviamente, i giocatori non hanno alcuna sensazione quando vengono colpiti, quindi è necessario trovare un modo per convincere il giocatore che si è verificato un errore. Nei giochi convenzionali è possibile che venga visualizzata un'animazione che consente di conoscere il carattere che ha raggiunto un riscontro. in alternativa, è possibile che la schermata sia Flash rossa e che il carattere possa grugnire un po'. Poiché questi tipi di indicazioni non funzionano in un'esperienza di realtà mista, abbiamo deciso di combinare il segnale visivo con un suono esagerato che indica che hai causato danni. Ho creato una grande sonorità e ho reso questo aspetto molto importante nella combinazione di tutti gli elementi. Quindi, per fare in modo che risulti ancora più, abbiamo aggiunto un breve messaggio di avviso come se fosse stato effettuato il sink di un sommergibile nucleare. 
<br>
![Quando un giocatore si trova in RoboRaid, viene visualizzato un segnale visivo, ma anche un segnale audio esagerato che indica che hanno causato danni.](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>Ottenere un grande suono da piccoli speaker

I relatori HoloLens sono piccoli e leggeri per soddisfare le esigenze del dispositivo, quindi non è possibile aspettarsi di ricevere troppo basso. Analogamente allo sviluppo per Smart Phone o dispositivi di gioco palmari, le finestre di progettazione e i compositori sono tenuti a tenere conto del contenuto della frequenza dei propri audio. È sempre necessario progettare suoni o scrivere musica con intervallo di frequenza completo, perché l'uso di cuffie è un'opzione per gli utenti. Tuttavia, per garantire la compatibilità con I relatori HoloLens, eseguo un test occasionalmente inserendo un EQ nel master di qualsiasi DAW che sto lavorando. L'impostazione EQ è costituita da un filtro High-Pass che si aggira da 600 Hz a 700 Hz (non troppo ripida) e da un filtro low-pass a circa 10.000 (ripida). Questo dovrebbe dare un'idea approssimativa del modo in cui i suoni verranno riprodotti nel dispositivo.

Se si fa affidamento sui bassi per dare il senso della modifica dell'accordo nella musica, è possibile che la musica perda completamente il senso della radice quando si applica questa impostazione EQ. Per risolvere questo problema, ho aggiunto un altro livello alla spigola che è un'ottava più alta (con alcune armoniche avanzate) e la mescolo per ottenere il senso della radice. In alcuni casi, l'uso della distorsione per accelerare le armoniche consentirà un contenuto di frequenza sufficiente nell'intervallo superiore per fare in modo che il nostro cervello pensi che vi sia qualcosa sotto di esso. Questa operazione è valida per gli SFX come gli effetti, le esplosioni o i suoni per i momenti speciali, ad esempio i super attacchi del boss. In realtà non è possibile fare affidamento sul lato basso per dare al giocatore un senso di impatto o peso. Come per la musica, l'uso della distorsione per offrire una certa crunch è stata decisamente utile.

### <a name="making-your-audio-cues-stand-out"></a>Emergenze dei segnali audio

Naturalmente, tutti gli utenti del team volevano musica Robo, pistole forti e esplosioni pazzesche; ma volevano anche essere in grado di ascoltare VoiceOver o qualsiasi altro spunto audio critico per i giochi.

In un gioco console con una gamma completa di frequenza, sono disponibili più opzioni per dividere le frequenze a seconda dell'importanza del suono. Per RoboRaid, ero limitato al numero di intervalli di frequenze che potevo scegliere tra i suoni. Se si usa un filtro low-pass e si curva eccessivamente dall'estremità superiore dello spettro, non si avrà nulla sul suono perché non è molto basso.

Per fare in modo che RoboRaid sia il più grande possibile sul dispositivo, è stato necessario ridurre l'intervallo dinamico dell'intera esperienza e si è fatto ampio uso di ducking creando una gerarchia chiara di importanza per diversi tipi di suoni. Ho impostato il ducking da-2 dB a-6 dB a seconda dell'importanza. Personalmente non mi piace ovviare ai giochi, quindi ho impiegato molto tempo per ottimizzare l'intervallo di dissolvenza in entrata/uscita e la quantità di attenuazione del volume. Sono stati configurati bus distinti per i suoni spaziali, non spaziali, VO e il bus secco senza Riverb per la musica. Sono stati quindi creati bus di priorità elevata, critici e non critici, in modo che gli asset siano stati configurati per accedere ai bus appropriati.

Spero che i professionisti audio siano in possesso di una grande quantità di divertimento e entusiasmo a lavorare sulle proprie app, come ho fatto per lavorare a RoboRaid. Non posso aspettare di vedere (e ascoltare) quali sono le persone di talento all'esterno di Microsoft per HoloLens.

## <a name="do-it-yourself"></a>Provare

Un trucco che ho scoperto per far sembrare "più grande" alcuni eventi, ad esempio le esplosioni, è quello di creare un asset mono per il suono spaziale e combinarlo con un asset stereo 2D, per riprodurlo in 3D. Questa operazione non comporta alcuna ottimizzazione, perché la presenza di una quantità eccessiva di informazioni nel contenuto stereo diminuisce la direzionalità degli asset mono. Tuttavia, l'ottenimento del giusto equilibrio comporterà la visualizzazione di grandi quantità di suoni che conterranno ai giocatori di trasformare le loro teste nella direzione giusta.

È possibile provare i grandi suoni usando le risorse audio seguenti:

**Scenario 1**
1. Scaricare [roboraid_enemy_explo_mono. wav](images/roboraid-enemy-explo-mono.wav) e impostarlo per riprodurre i suoni spaziali e assegnarli a un evento.
2. Scaricare [roboraid_enemy_explo_stereo. wav](images/roboraid-enemy-explo-stereo.wav) e impostare la riproduzione in stereo 2D e assegnarlo allo stesso evento indicato in precedenza. Poiché queste risorse vengono normalizzate in Unity, attenuare il volume di entrambi gli asset in modo da non ritagliare.
3. Riprodurre entrambi i suoni insieme. Spostare la testa per sentire la spazialità.

**Scenario 2**
1. Scaricare [roboraid_enemy_explo_summed. wav](images/roboraid-enemy-explo-summed.wav) e impostare per riprodurre tramite il suono spaziale e assegnarlo a un evento.
2. Riprodurre questo asset da solo e confrontarlo con l'evento dello scenario 1.
3. Provare a eseguire un saldo diverso di file mono e stereo.

## <a name="see-also"></a>Vedi anche

* [Audio spaziale](spatial-sound.md)
* [RoboRaid per Microsoft HoloLens](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
