---
title: 'Case study : primo anno nel team HoloLens design'
description: Il mio viaggio da una flatland 2D al mondo 3D è iniziato quando sono entrata a far parte del team HoloLens design nel gennaio 2016.
author: designnomad
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, design, editoriale, personale
ms.openlocfilehash: 2defa24b8e53b28f90a8eb613afcbae7d1b9b1f2d12caaf885e405593df01ffe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192875"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>Case study : primo anno nel team HoloLens design

Il mio viaggio da una flatland 2D al mondo 3D è iniziato quando sono entrata a far parte del team HoloLens design nel gennaio 2016. Prima di entrare nel team, ho avuto pochissima esperienza nella progettazione 3D. Era come il proverbio cinese su un viaggio di migliaia di miglia a partire da un singolo passaggio, tranne nel mio caso che il primo passaggio è stato un salto.

![Salto da 2D a 3D](../develop/platform-capabilities-and-apis/images/2D_to_3D-800px.gif)<br>
*Il salto da 2D a 3D*

> *"Mi sono sentito come se mi fossero buttati sul seggiolino del guidatore senza sapere come guidare l'auto. Sono rimasto sopraffatto e impaurito, ma molto mirato."*<br>
> — Hae Jin Lee

Nell'ultimo anno ho raccolto competenze e conoscenze il più velocemente possibile, ma ho ancora molto da imparare. In questo caso, sono state scritte 4 osservazioni con un'esercitazione video che documenta la transizione da un modello 2D a un modello 3D interaction designer. Mi auguriamo che la mia esperienza possa ispirare altri designer a fare il salto in 3D.

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>Frame di buona notizia. Interfaccia utente hello spatial/diegetic

Ogni volta che ho progettato poster, riviste, siti Web o schermate dell'app, un frame definito (in genere un rettangolo) era una costante per ogni problema. A meno che questo post non venga letto in un  HoloLens o in un altro dispositivo VR, lo si sta osservando dall'esterno tramite uno schermo 2D sorvegliato in modo sicuro all'interno di un frame. Il contenuto è esterno all'utente. Tuttavia, il visore di realtà mista elimina il *frame,* quindi ci si trova all'interno dello spazio dei contenuti, cercando e passando attraverso il contenuto dall'interno all'esterno.

L'ho compreso concettualmente, ma all'inizio ho commesso l'errore di trasferire semplicemente il pensare 2D nello spazio 3D. Questo ovviamente non ha funzionato bene perché lo spazio 3D ha proprietà univoche, ad esempio una modifica della visualizzazione (in base al movimento della testa dell'utente) e un requisito diverso per il comfort dell'utente [(in](https://www.youtube.com/watch?v=-606oZKLa_s/) base alle proprietà dei dispositivi e degli esseri umani che li usano). Ad esempio, in uno spazio di progettazione dell'interfaccia utente 2D, il blocco degli elementi dell'interfaccia utente nell'angolo di uno schermo è un modello molto comune, ma questa interfaccia utente in stile HUD (Head Up Display) non sembra naturale nelle esperienze MR/VR; impedisce l'esperienza dell'utente nello spazio e provoca disagi per l'utente. È come avere una particella di polvero fastidiosa sugli occhiali di cui si sta morendo la voglia di liberarsi. Nel corso del tempo, ho appreso che è più naturale posizionare il contenuto nello spazio 3D e aggiungere un comportamento di blocco del corpo che fa sì che il contenuto segua l'utente a una distanza fissa relativa.

![Corpo bloccato](../develop/platform-capabilities-and-apis/images/bodylockedtagalong.gif)<br>
*Corpo bloccato*

<br>

![Blocco del mondo](../develop/platform-capabilities-and-apis/images/worldlocked.gif)<br>
*Blocco del mondo*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>Frammenti: un esempio di grande interfaccia utente diegetic

[Frammenti,](https://www.microsoft.com/p/fragments/9nblggh5ggm8)un giallo di criminalità in prima persona sviluppato da [Asobo Studio](https://www.asobostudio.com/) HoloLens un'ottima interfaccia utente diegetic. In questo gioco l'utente diventa un personaggio principale, un detective che prova a risolvere un giallo. Gli indizi chiave per risolvere questo giallo si sparpagliano nella stanza fisica dell'utente e spesso vengono incorporati all'interno di un oggetto fittizio invece di essere esistenti da soli. Questa interfaccia utente diegetic tende a essere meno individuabile rispetto all'interfaccia utente bloccata dal corpo, quindi il team di Asobo ha usato sapientemente molti segnali, tra cui la direzione dello sguardo, il suono, la luce e le guide dei caratteri virtuali (ad esempio, la freccia che punta la posizione dell'indizio) per attirare l'attenzione dell'utente.

![Frammenti - Esempi di interfaccia utente diegetic](../develop/platform-capabilities-and-apis/images/fragments-game-example-1.jpg)<br>
*Frammenti - Esempi di interfaccia utente diegetic*

### <a name="observations-about-diegetic-ui"></a>Osservazioni sull'interfaccia utente diegetic

L'interfaccia utente spaziale (sia con corpo bloccato che con blocco del mondo) e l'interfaccia utente diegetic hanno i propri punti di forza e punti deboli. I progettisti invitano i progettisti a provare il maggior numero possibile di app MR/VR e a sviluppare la propria comprensione e sensibilità per vari metodi di posizionamento dell'interfaccia utente.

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>Il ritorno dello skeuomorfismo e dell'interazione magica

Lo skeuomorfismo, un'interfaccia digitale che simula la forma degli oggetti reali è stata "uncool" negli ultimi 5-7 anni nel settore della progettazione. Quando Apple ha definitivamente lasciato il modo di progettare flat in iOS 7, sembra che lo Skeuomorphism fosse definitivamente inattivo come metodologia di progettazione dell'interfaccia. Tuttavia, un nuovo visore MR/VR di medie dimensioni è arrivato sul mercato e sembra che lo Skeuomorphism sia tornato di nuovo. : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>Simulatore di processo: un esempio di progettazione vr skeuomorfica

[Simulatore](https://jobsimulatorgame.com/)di processi, un gioco capriccioso sviluppato da [Owlchemy Labs](https://owlchemylabs.com/) è uno degli esempi più diffusi per la progettazione di VR skeuomorfico. All'interno di questo gioco, i giocatori vengono trasportati in un futuro in cui i robot sostituiscono gli esseri umani e visitano un ristorante per sperimentare come ci si prova a eseguire attività banali in uno dei quattro diversi processi: Meccanico automatico, Chef chef chef, impiegato del negozio o Office Worker.

Il vantaggio dello skeuomorfismo è chiaro. Gli ambienti e gli oggetti familiari all'interno di questo gioco aiutano i nuovi utenti vr a essere più a proprio agio e presenti nello spazio virtuale. Li fa anche sentire in controllo associando conoscenze e comportamenti familiari agli oggetti e alle reazioni fisiche corrispondenti. Ad esempio, per berne una tazza di caffè, le persone devono semplicemente andare a piedi verso la macchina per il caffè, premere un pulsante, afferrare la maniglia della tazza e inclinarla verso la loro bocca come farebbe nel mondo reale.

![Simulatore di processi](../develop/platform-capabilities-and-apis/images/job-simulator.gif)<br>
*Simulatore di processi*

Poiché MR/VR è ancora un mezzo di sviluppo, l'uso di un certo grado di skeuomorfismo è necessario per demistificare la tecnologia MR/VR e per introdurla a un pubblico più ampio in tutto il mondo. Inoltre, l'uso dello skeuomorfismo o della rappresentazione realistica potrebbe essere vantaggioso per tipi specifici di applicazioni come la simulazione di simulazione di voli o interventi di simulazione. Poiché l'obiettivo di queste app è sviluppare e perfezionare competenze specifiche che possono essere applicate direttamente nel mondo reale, più la simulazione è vicina al mondo reale, più è trasferibile la conoscenza.

Tenere presente che lo skeuomorfismo è solo un approccio. Il potenziale del mondo MR/VR è molto più grande di questo e i progettisti devono cercare di creare magiche interazioni iper-naturali, nuove opportunità che sono univocamente possibili nel mondo MR/VR. Per iniziare, è consigliabile aggiungere magiche competenze agli oggetti ordinari per consentire agli utenti di soddisfare i propri desideri fondamentali, tra cui il teletrasporto e l'onnipresentità.

![Porta magica di Doraemon (a sinistra) e ruby(destra)](../develop/platform-capabilities-and-apis/images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Porta magica di Doraemon (a sinistra) e sciorsi ruby (a destra)*

### <a name="observations-about-skeuomorphism-in-vr"></a>Osservazioni sullo skeuomorfismo nella realtà virtuale

Da "Via d'ingresso" in Doraemon, "Ruby Perle" in The Wizard of Oz a "Maurader's map" (Mappa di Maurader) in Harry Potter, esempi di oggetti comuni con potere magico abbondano nella narrativa popolare. Questi oggetti magici consentono di visualizzare una connessione tra il mondo reale e il fantastico, tra ciò che è e ciò che potrebbe essere. Tenere presente che quando si progetta l'oggetto magico o magico è necessario trovare un equilibrio tra funzionalità e intrattenimento. Attenzione alla tentazione di creare qualcosa di puramente magico solo per motivi di novità.

## <a name="understanding-different-input-methods"></a>Informazioni sui diversi metodi di input

Quando ho progettato per il supporto 2D, ho dovuto concentrarmi sulle interazioni con tocco, mouse e tastiera per gli input. Nello spazio di progettazione MR/VR il corpo diventa l'interfaccia e gli utenti possono usare una selezione più ampia di metodi di input, tra cui voce, sguardo, movimento, controller [a 6 dof](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)e guanto che consentono una connessione più intuitiva e diretta con gli oggetti virtuali.

![Input disponibili in HoloLens](../develop/platform-capabilities-and-apis/images/inputs.jpg)<br>
*Input disponibili in HoloLens*

> *"Tutto è ideale per qualcosa e peggiore per qualcos'altro".*<br>
> — [Bill Buxton](https://www.billbuxton.com/)

Ad esempio, l'input dei movimenti usando sensori di mano e fotocamera bare su un dispositivo HMD libera gli utenti dal tenere i controller o portare i guanto sudati, ma l'uso frequente può causare affaticamento fisico (ovvero un braccio di gorilla). Inoltre, gli utenti devono tenere le mani all'interno della linea di vista; se la fotocamera non riesce a vedere le mani, non è possibile usare le mani.

L'input vocale è utile per attraversare attività complesse perché consente agli utenti di tagliare i menu annidati con un solo comando ,ad esempio "Show me the movies made by Laika studio." e anche molto economico se abbinato ad altre modalità (ad esempio, il comando "Guardami" orienta l'ologramma che un utente sta osservando verso l'utente). Tuttavia, l'input vocale potrebbe non funzionare correttamente in un ambiente rumoroso o potrebbe non essere appropriato in uno spazio molto silenzioso.

Oltre al movimento e al parlato, i controller tracciati manualmente (ad esempio, oculus touch, Vive e così via) sono metodi di input molto diffusi perché sono facili da usare, accurati, sfruttano la [proprioception](https://en.wikipedia.org/wiki/Proprioception)delle persone e forniscono segnali aptici passivi. Tuttavia, questi vantaggi hanno il costo di non essere in grado di essere a mani snodati e di usare il tracciamento completo delle dita.

![Senso (sinistra) e Manus VR (destra)](../develop/platform-capabilities-and-apis/images/senso-and-manus-vr.jpg)<br>
*Senso (sinistra) e Manus VR (destra)*

Anche se non sono popolari come i controller, i guanto stanno di nuovo guadagnando vigore grazie all'ondata MR/VR. Più di recente, l'input del cervello/mente ha iniziato a acquisire trazione come interfaccia per gli ambienti virtuali integrando il sensore EEG o EMG nel visore (ad esempio [MindMaze VR).](https://www.mindmaze.com/)

### <a name="observations-about-input-methods"></a>Osservazioni sui metodi di input

Si tratta solo di un esempio di dispositivi di input disponibili sul mercato per MR/VR. Continueranno a proliferare fino a quando il settore non maturerà e non accetterà le procedure consigliate. Fino ad allora, i progettisti devono rimanere a conoscenza dei nuovi dispositivi di input ed essere ben esperti nei metodi di input specifici per il progetto specifico. I progettisti devono cercare soluzioni creative all'interno delle limitazioni, pur riproducendo i punti di forza di un dispositivo.

## <a name="sketch-the-scene-and-test-in-the-headset"></a>Creare uno sketch della scena e testare il visore

Quando lavoravo in 2D, disegnavo principalmente solo il contenuto. Tuttavia, nello spazio della realtà mista non era sufficiente. Ho dovuto delineare l'intera scena per immaginare meglio le relazioni tra l'utente e gli oggetti virtuali. Per aiutare il mio modo di pensare nello spaziale, ho iniziato a disegnare scene in [Cinema 4D](https://www.maxon.net/en/products/cinema-4d/overview/) e talvolta a creare asset semplici per la creazione di prototipi in [Maya.](https://www.autodesk.com/products/maya/overview/) Non ho mai usato nessuno dei due programmi prima di entrare nel team di HoloLens e sono ancora un principiante, ma lavorare con questi programmi 3D mi ha sicuramente consentito di avere familiarità con la nuova terminologia, ad esempio [shader](https://en.wikipedia.org/wiki/Shader) e [IK (cinetica inversa).](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/)

**"Indipendentemente dal livello di attenzione con cui ho delineato la scena in 3D, l'esperienza effettiva nel visore non è quasi mai la stessa dello sketch. Ecco perché è importante testare la scena nei visori di destinazione." - Hae Jin Lee**

Per HoloLens di prototipazione, ho provato tutte le esercitazioni in [Esercitazioni di](../develop/unity/tutorials.md) realtà mista per iniziare. Ho quindi iniziato a giocare con [HoloToolkit.Unity](https://github.com/Microsoft/HoloToolkit-Unity/) che Microsoft fornisce agli sviluppatori per accelerare lo sviluppo di applicazioni olografiche. Quando mi sono bloccato con qualcosa, ho pubblicato la mia domanda HoloLens [domanda & Answer Forum](https://forums.hololens.com/categories/questions-and-answers/).

Dopo aver acquisito informazioni di base HoloLens prototipazione, ho voluto consentire ad altri non codificatori di creare prototipi da soli. Ho quindi creato un'esercitazione video che illustra come sviluppare un semplice proiettore usando HoloLens. I concetti di base vengono brevemente illustrati, quindi anche se non si ha esperienza HoloLens sviluppo, è consigliabile seguire questa procedura.

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*Ho fatto questa semplice esercitazione per i non programmatori come me.*

Per la creazione di prototipi VR, ho partecipato a corsi presso [VR Dev School](https://learn.vrdev.school/) e ho anche partecipato alla creazione di contenuti [3D](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/) per la realtà virtuale Lynda.com. Vr Dev School mi ha fornito una conoscenza più approfondita del codice e il corso Lynda mi ha offerto una breve introduzione alla creazione di asset per la realtà virtuale.

## <a name="take-the-leap"></a>Fare il salto

Un anno fa, mi sono sentito come se tutto questo fosse un po' eccessivo. Ora posso dirvi che è valsa al 100% la pena. MR/VR è ancora molto giovane e ci sono così tante possibilità interessanti in attesa di essere realizzate. Mi sembra di poter svolgere una piccola parte nella progettazione del futuro. Spero che ci si unirà a me nel viaggio nello spazio 3D.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="../develop/platform-capabilities-and-apis/images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae Jin Lee</b><br>Designer di esperienza utente @Microsoft</td>
</tr>
</table>

 
