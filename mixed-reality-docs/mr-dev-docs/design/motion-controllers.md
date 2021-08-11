---
title: Controller del movimento
description: Informazioni su come configurare, associare e manager le interazioni di input usando i controller di movimento di realtà mista nelle applicazioni.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof controller, controller di movimento, associazione, visore di realtà mista, visore di realtà mista windows, visore di realtà virtuale, HoloLens, scorrimento, grip, stato
ms.openlocfilehash: bced0115eee5e753ef01d129ae10910acdca2b7b91020117f53b2ebf8833a130
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224884"
---
# <a name="motion-controllers"></a>Controller del movimento

:::row:::
    :::column:::
        I controller di movimento [sono accessori hardware che](../discover/hardware-accessories.md) consentono agli utenti di intervenire in realtà mista. Un vantaggio dei controller di movimento [rispetto](gaze-and-commit.md#composite-gestures) ai movimenti è che i controller hanno una posizione precisa nello spazio, consentendo un'interazione granulare con gli oggetti digitali. Per Windows Mixed Reality visori immersivi, i controller di movimento sono il modo principale in cui gli utenti possono intervenire nel proprio mondo.<br>
        <br>
        *Immagine: un controller Windows Mixed Reality movimento*
    :::column-end:::
        :::column:::
       ![Windows Mixed Reality di movimento](images/winmr-ck-1080x1080-350px.jpg)<br> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="device-support"></a>Supporto di dispositivi

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Funzionalità</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
</tr>
<tr>
     <td>Controller del movimento</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>Dettagli dell'hardware

<iframe width="940" height="530" src="https://www.youtube.com/embed/1nlcdDNOdm8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Windows Mixed Reality controller di movimento offrono un rilevamento preciso e reattivo del movimento nel campo di visualizzazione usando i sensori nel visore immersivo. Non è necessario installare l'hardware sulle pareti nel proprio spazio. Questi controller di movimento offriranno la stessa facilità di configurazione e portabilità Windows Mixed Reality visori immersivi. I partner di dispositivi pianificano di commercializzazione e vendita di questi controller sugli scaffali delle vendite al dettaglio in questa festività.

![Conoscere il controller](images/controllerimage-750px.png)<br>
*Conoscere il controller*

**Caratteristiche:**
* Rilevamento ottico
* Trigger
* Pulsante Di selezione
* Levetta personale
* Touchpad

## <a name="setup"></a>Eseguire la configurazione

### <a name="before-you-begin"></a>Prima di iniziare

**Saranno necessari gli elementi seguenti:**
* Set di due controller di movimento.
* Quattro batterie AA.
* UN PC con Bluetooth 4.0.

**Verificare la disponibilità di Windows, Unity e driver**
* Vedere [Installare gli strumenti per](../develop/install-the-tools.md) le versioni preferite di Windows, Unity e così via, per lo sviluppo di realtà mista.
* Assicurarsi di avere i driver di visore e controller di movimento più [aggiornati.](/windows/mixed-reality/enthusiast-guide/mixed-reality-software)

### <a name="pairing-controllers"></a>Controller di associazione

I controller di movimento possono essere associati al PC host usando Windows come qualsiasi altro Bluetooth dispositivo.

1. Inserire due batterie AA nella parte posteriore del controller. Per il momento, lasciare spenta la copertura della batteria.
2. Se si usa un adattatore Bluetooth USB esterno anziché una radio Bluetooth integrata, [](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) esaminare le procedure consigliate Bluetooth prima di procedere. Per la configurazione desktop con radio predefinita, assicurarsi che l'antenna sia connessa.
3. Aprire **Windows Impostazioni** Dispositivi Aggiungi Bluetooth o altro dispositivo Bluetooth e rimuovere tutte le istanze precedenti di "Controller di movimento - Destra" e "Controller di movimento  ->    ->    ->   - Sinistra". Selezionare anche La categoria Altri dispositivi nella parte inferiore dell'elenco.
4. Selezionare **Aggiungi Bluetooth o altro dispositivo** e verificare che inizi a individuare Bluetooth dispositivi.
5. Premere e tenere premuto il pulsante Windows controller per attivare il controller, rilasciare una volta che si alza.
6. Tenere premuto il pulsante di associazione (tab nel vano batteria) fino a quando i LED non iniziano a pulsare.

:::row:::
    :::column:::
7. Attendere che "Controller di movimento - Sinistra" o "Controller di movimento - Destra" venga visualizzato in fondo all'elenco. Selezionare per associare. Il controller vibra una volta quando è connesso.<br>
        <br>
        *Immagine: selezionare "Controller di movimento" da associare; Se sono presenti più istanze, selezionarne una nella parte inferiore dell'elenco*
    :::column-end:::
        :::column:::
       ![Selezionare Controller di movimento da associare, se più istanze ne selezionano una nella parte inferiore dell'elenco](images/450px-bluetooth-add-a-device-300px.png)<br> 
    :::column-end:::
:::row-end:::
   
8. Il controller verrà visualizzato nelle impostazioni Bluetooth nella categoria **"Mouse,** tastiera & penna" come **Connesso**. A questo punto, è possibile ottenere un aggiornamento del firmware. Vedere [la sezione successiva.](motion-controllers.md#updating-controller-firmware)
9. Ricollegare il coperchio della batteria.
10. Ripetere i passaggi da 1 a 9 per il secondo controller.

<br>

:::row:::
    :::column:::
        Dopo aver associato correttamente entrambi i controller, le impostazioni dovrebbero essere simili alle seguenti, nella **categoria "Mouse, tastiera & penna"** <br>
        <br>
        *Immagine: Controller di movimento connessi*
    :::column-end:::
        :::column:::
       ![Controller di movimento connessi](images/450px-motion-controller-connected-300px.png)<br>
    :::column-end:::
:::row-end:::

Se i controller vengono disattivati dopo l'associazione, il relativo stato verrà visualizzato come Associato. Per i controller in modo permanente nella categoria "Altri dispositivi", l'associazione potrebbe essere stata completata solo parzialmente. In questo caso, eseguire di nuovo i passaggi di associazione per ottenere il controller funzionante.

### <a name="updating-controller-firmware"></a>Aggiornamento del firmware del controller

* Se è disponibile un visore vr immersivo connesso al PC con il nuovo firmware del controller, il firmware verrà inserito automaticamente nei controller di movimento alla successiva attivazione. Gli aggiornamenti del firmware del controller sono indicati da un modello di quadranti LED illuminati in un movimento circolare e sono necessari da 1 a 2 minuti.


:::row:::
    :::column:::
* Al termine dell'aggiornamento del firmware, i controller verranno riavviati e riconnessi. Entrambi i controller devono essere connessi ora. <br>
        <br>
        *Immagine: Controller connessi nelle impostazioni Bluetooth*
    :::column-end:::
        :::column:::
       ![Controller connessi](images/cyk-connected-300px.jpg)<br>
    :::column-end:::
:::row-end:::


* Verificare che i controller funzionino correttamente:
    1. Avviare **Portale realtà mista** e immettere la home page della realtà mista.
    2. Spostare i controller e verificare il rilevamento, testare i pulsanti e verificare che il [teletrasporto](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) funzioni. In caso contrario, vedere risoluzione dei problemi del [controller di movimento](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers).

## <a name="gazing-and-pointing"></a>Guardare e puntare

Windows Mixed Reality supporta due modelli chiave per l'interazione; **sguardo, commit** e **punta e commit**:
* Con **lo sguardo e il commit,** gli utenti hanno come destinazione un oggetto con lo sguardo e quindi selezionano gli oggetti con i tocchi di mano, un gamepad, un clicker o la voce. [](gaze-and-commit.md)
* Con **il punto e il commit,** un utente può puntare un controller di movimento che supporta il puntamento all'oggetto di destinazione e quindi selezionare gli oggetti con il trigger del controller.

Le app che supportano il puntamento con i controller di movimento devono anche abilitare le interazioni con lo sguardo fisso, laddove possibile, per offrire agli utenti la possibilità di scegliere i dispositivi di input che usano.

### <a name="managing-recoil-when-pointing"></a>Gestione del recupero quando si punta

Quando si usano controller di movimento per puntare ed eseguire il commit, gli utenti useranno il controller per scegliere come destinazione e interagire tramite pull del trigger. Gli utenti che estraeno il trigger in modo aggressivo possono terminare puntando il controller più in alto al termine del pull del trigger rispetto a quanto previsto.

Per gestire tali recoil che possono verificarsi quando gli utenti estraeno il trigger, l'app può allineare il raggio di destinazione quando il valore dell'asse analogico del trigger è superiore a 0,0. È quindi possibile intervenire usando il raggio di destinazione alcuni fotogrammi in un secondo momento quando il valore del trigger raggiunge 1,0, purché la pressione finale si verifichi entro un breve intervallo di tempo. Quando si usa il movimento tocco composito di livello [superiore,](gaze-and-commit.md#composite-gestures)Windows gestirà automaticamente l'acquisizione e il timeout del raggio di destinazione.

## <a name="grip-pose-vs-pointing-pose"></a>Posizione di aderenza rispetto alla posizione di puntamento

Windows Mixed Reality supporta i controller di movimento in fattori di forma diversi, con la progettazione di ogni controller diversa nella relazione tra la posizione della mano dell'utente e la direzione naturale "in avanti" che le app devono usare per puntare durante il rendering del controller.

Per rappresentare meglio questi controller, è possibile analizzare due tipi di pose per ogni origine di interazione. la **posizione del grip e** il **puntatore pongono**.

### <a name="grip-pose"></a>Posizione del grip

La **posizione del grip** rappresenta la posizione del palmo di una mano rilevata da un HoloLens o del palmo che contiene un controller di movimento.

Nei visori vr immersivi, la posizione del grip è più adatta per eseguire il rendering della mano **dell'utente** o di un oggetto in mano **dell'utente,** ad esempio un'avaria o una mitragliatrice. La posizione del grip viene usata anche quando  si visualizza un controller di movimento, perché il modello di rendering fornito da Windows per un controller di movimento usa la posizione di presa come origine e centro di rotazione.

La posizione del grip è definita in modo specifico come segue:
* Posizione **del grip:** centroide del palmo quando si tiene il controller naturalmente, regolato a sinistra o a destra per centrare la posizione all'interno del grip. Nel controller Windows Mixed Reality movimento, questa posizione è in genere allineata al pulsante Afferra.
* Asse destro dell'orientamento del grip: quando si apre completamente la mano per formare una posizione a cinque dita piana, il raggio normale al palmo (in avanti dal palmo sinistro, **all'indietro** dal palmo destro)
* Asse avanti **dell'orientamento** del grip: quando si chiude parzialmente la mano (come se si tiene il controller), il raggio che punta in avanti attraverso il canale formato dalle dita non del pollice.
* Asse **su dell'orientamento del** grip: asse Su implicito dalle definizioni Right e Forward.

### <a name="pointer-pose"></a>Posizione del puntatore

La **posizione dell'indicatore** di misura rappresenta la punta del controller che punta in avanti.

La posizione dell'indicatore di misura fornita dal sistema è più adatta per il raycast quando si esegue **il rendering del modello controller stesso.** Se si esegue il rendering di un altro oggetto virtuale al posto del controller, ad esempio una canna virtuale, è necessario puntare con un raggio più naturale per tale oggetto virtuale, ad esempio un raggio che si sposta lungo il raggio del modello di mitra definito dall'app. Poiché gli utenti possono visualizzare l'oggetto virtuale e non il controller fisico, il puntamento con l'oggetto virtuale sarà probabilmente più naturale per gli utenti che usano l'app.

## <a name="controller-tracking-state"></a>Stato di rilevamento del controller

Analogamente ai visori VR, Windows Mixed Reality controller del movimento non richiede la configurazione di sensori di rilevamento esterni. Al contrario, i controller vengono monitorati dai sensori nel visore VR stesso.

Se l'utente sposta i controller fuori dal campo di visualizzazione del visore VR, nella maggior parte dei casi Windows continuerà a dedurre le posizioni del controller e a fornirle all'app. Quando il controller ha perso il rilevamento visivo per un tempo sufficiente, le posizioni del controller scenderanno in posizioni di accuratezza approssimativa.

A questo punto, il sistema blocca il corpo del controller per l'utente, tenendo traccia della posizione dell'utente mentre si sposta, esponendo comunque il vero orientamento del controller usando i sensori di orientamento interni. Molte app che usano controller per puntare e attivare gli elementi dell'interfaccia utente possono funzionare normalmente, con un'accuratezza approssimativa senza che l'utente se ne noti.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/rkDpRllbLII" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="reasoning-about-tracking-state-explicitly"></a>Ragionamento sul rilevamento dello stato in modo esplicito

Le app che vogliono trattare le posizioni in modo diverso in base allo stato di rilevamento possono andare oltre e controllare le proprietà sullo stato del controller, ad esempio SourceLossRisk e PositionAccuracy:

<table>
<tr>
<th> Stato di rilevamento </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Accuratezza elevata</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Accuratezza elevata (a rischio di perdita)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Accuratezza approssimativa</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Con approssimazione </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Nessuna posizione</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Con approssimazione </td><td style="background-color: orange"> false</td>
</tr>
</table>

Questi stati di rilevamento del controller del movimento sono definiti come segue:
* **Accuratezza elevata:** Mentre il controller del movimento si trova all'interno del campo visivo del visore VR, in genere fornirà posizioni di accuratezza elevata, in base al rilevamento visivo. Un controller in movimento che lascia temporaneamente il campo di visualizzazione o viene temporaneamente nascosto dai sensori del visore VR (ad esempio, dall'altra mano dell'utente) continuerà a restituire posizioni di accuratezza elevata per un breve periodo di tempo, in base al rilevamento inerziale del controller stesso.
* **Accuratezza elevata (a rischio di perdita):** Quando l'utente sposta il controller del movimento oltre il bordo del campo visivo del visore VR, il visore VR non sarà in grado di tenere traccia visivamente della posizione del controller. L'app sa quando il controller ha raggiunto questo limite per le applicazioni a pagina mobile. Il **valore di SourceLossRisk** raggiunge la versione 1.0. A questo punto, l'app può scegliere di sospendere i movimenti del controller che richiedono un flusso costante di posizioni di alta qualità.
* **Accuratezza approssimativa:** Quando il controller ha perso il rilevamento visivo per un tempo sufficiente, le posizioni del controller scenderanno in posizioni di accuratezza approssimativa. A questo punto, il sistema blocca il corpo del controller per l'utente, tenendo traccia della posizione dell'utente mentre si sposta, esponendo comunque il vero orientamento del controller usando i sensori di orientamento interni. Molte app che usano controller per puntare e attivare gli elementi dell'interfaccia utente possono funzionare come di consueto, con un'accuratezza approssimativa senza che l'utente se ne sia abili. Le app con requisiti di input più  pesanti  possono scegliere di scegliere questo calo da Accuratezza elevata a Accuratezza approssimativa controllando la **proprietà PositionAccuracy,** ad esempio per offrire all'utente un hitbox più preciso sulle destinazioni fuori schermo durante questo periodo di tempo.
* **Nessuna posizione:** Anche se il controller può operare con accuratezza approssimativa per molto tempo, a volte il sistema sa che anche una posizione di blocco del corpo non è significativa al momento. Ad esempio, un controller che è stato attivato potrebbe non essere mai stato osservato visivamente o un utente può disattivare un controller che viene quindi prelevato da un altro utente. In questi casi, il sistema non fornirà alcuna posizione all'app e **TryGetPosition** restituirà false.

## <a name="interactions-low-level-spatial-input"></a>Interazioni: input spaziale di basso livello

Le interazioni principali tra le mani e i controller del movimento sono **Select**, **Menu**, **Hands**, **Touchpad,** **Thumbstick** e **Home**.
* **Selezionare** è l'interazione principale per attivare un ologramma, costituito da una pressione seguita da una versione. Per i controller del movimento, si esegue una pressione Seleziona usando il trigger del controller. Altri modi per eseguire una selezione sono pronunciando il [comando vocale](voice-input.md) "Seleziona". La stessa interazione di selezione può essere usata all'interno di qualsiasi app. Si pensi a Select come l'equivalente di un clic del mouse; un'azione universale che si apprende una sola volta e quindi si applica a tutte le app.
* **Menu** è l'interazione secondaria per agire su un oggetto, usata per estrarre un menu di scelta rapida o eseguire un'altra azione secondaria. Con i controller del movimento è possibile eseguire un'azione di menu usando il pulsante di *menu del controller.* ovvero il pulsante con l'icona "menu" hamburger
* **La** comprensione è il modo in cui gli utenti possono intervenire direttamente sugli oggetti a loro disposizione per manipolarli. Con i controller del movimento è possibile eseguire un'azione afferrando strettamente la mano. Un controller del movimento può rilevare un'afferramento con un pulsante di afferramento, un palmo o un altro sensore.
* **Il touchpad** consente all'utente di regolare un'azione in due dimensioni lungo la superficie del touchpad di un controller del movimento, commettendo l'azione facendo clic sul touchpad. I touchpad forniscono uno stato premuto, lo stato toccato e le coordinate XY normalizzate. L'intervallo X e Y va da -1 a 1 nell'intervallo del touchpad circolare, con un centro in corrispondenza di (0, 0). Per X, -1 si trova a sinistra e 1 a destra. Per Y, -1 si trova nella parte inferiore e 1 nella parte superiore.
* **La levetta** consente all'utente di regolare un'azione in due dimensioni spostando la levetta di un controller del movimento all'interno dell'intervallo circolare, commettendo l'azione facendo clic sulla levetta. Le levette forniscono anche uno stato premuto e coordinate XY normalizzate. L'intervallo X e Y va da -1 a 1 nell'intervallo del touchpad circolare, con un centro in corrispondenza di (0, 0). Per X, -1 si trova a sinistra e 1 a destra. Per Y, -1 si trova nella parte inferiore e 1 nella parte superiore.
* **Home** è una speciale azione di sistema usata per tornare al menu Start. È simile a premere il tasto Windows tastiera o il pulsante Xbox in un controller Xbox. È possibile passare a Home premendo il pulsante Windows su un controller del movimento. Si noti che è sempre possibile tornare a Start pronunciando "Hey Cortana, Go Home". Le app non possono reagire in modo specifico alle azioni Home, perché vengono gestite dal sistema.

## <a name="composite-gestures-high-level-spatial-input"></a>Movimenti compositi: input spaziale di alto livello

È [possibile tenere traccia dei](gaze-and-commit.md#composite-gestures) movimenti della mano e dei controller del movimento nel corso del tempo per rilevare un set comune di movimenti **[compositi di alto livello.](gaze-and-commit.md#composite-gestures)** In questo modo l'app può rilevare  movimenti di tocco di alto **livello,** tenere premuto **,** manipolazione e navigazione, indipendentemente dal fatto che gli utenti finitino con le mani o i controller. 

## <a name="rendering-the-motion-controller-model"></a>Rendering del modello di controller del movimento

**I modelli controller 3D Windows** rendono disponibile alle app un modello visualizzabile di ogni controller del movimento attualmente attivo nel sistema. Facendo in modo che l'app carichi e articola in modo dinamico questi modelli di controller forniti dal sistema in fase di esecuzione, è possibile assicurarsi che l'app sia compatibile con qualsiasi progettazione futura del controller.

È consigliabile eseguire il  rendering di tutti i modelli di cui è possibile eseguire il rendering in corrispondenza della posizione di controllo del controller, perché l'origine del modello è allineata a questo punto nel mondo fisico. Se si esegue il rendering dei modelli controller, è possibile che si voglia eseguire il raycast nella scena dalla posizione dell'indicatore di misura **,** che rappresenta il raggio lungo il quale gli utenti si aspettano naturalmente di puntare, in base alla progettazione fisica del controller.

Per altre informazioni su come caricare i modelli di controller in modo dinamico in Unity, vedere la sezione [Rendering del modello di controller del movimento in Unity.](../develop/unity/gestures-in-unity.md#rendering-the-motion-controller-model-in-unity)

**Linea di controller 2D** Anche se è consigliabile collegare i suggerimenti e i comandi del controller in-app ai modelli di controller in-app stessi, alcuni sviluppatori potrebbero voler usare rappresentazioni line-art 2D dei controller del movimento nell'interfaccia utente semplice "tutorial" o "how-to". Per questi sviluppatori, sono stati resi disponibili .png line art del controller del movimento sia in bianco che in nero (fare clic con il pulsante destro del mouse per salvare).

![Anteprima della line art dei controller del movimento](images/motioncontrollers-black-preview-300px.png)

[Line art dei controller del movimento a risoluzione completa in '''white'''](images/motioncontrollers-white.png)
 
[Line art dei controller del movimento a risoluzione completa in '''black'''](images/motioncontrollers-black.png)

## <a name="faq"></a>Domande frequenti

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>È possibile associare controller del movimento a più PC?

I controller del movimento supportano l'associazione a un singolo PC. Seguire le istruzioni sulla [configurazione del controller del movimento](motion-controllers.md#setup) per associare i controller.

### <a name="how-do-i-update-motion-controller-firmware"></a>Ricerca per categorie il firmware del controller del movimento?

Il firmware del controller del movimento fa parte del driver del visore VR e verrà aggiornato automaticamente alla connessione, se necessario. Gli aggiornamenti del firmware richiedono in genere 1-2 minuti a seconda Bluetooth radio e della qualità del collegamento. In rari casi, gli aggiornamenti del firmware del controller possono richiedere fino a 10 minuti, il che può indicare problemi Bluetooth connettività o interferenza radio. Vedere [Bluetooth procedure consigliate nella Guida per gli](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) appassionati per risolvere i problemi di connettività. Dopo un aggiornamento del firmware, i controller si riavviano e si riconnettono al PC host (si potrebbe notare che i LED sono luminosi per il rilevamento). Se un aggiornamento del firmware viene interrotto (ad esempio, i controller perdono l'alimentazione), verrà eseguito un nuovo tentativo alla successiva accensione dei controller.

### <a name="how-i-can-check-battery-level"></a>Come è possibile controllare il livello della batteria?

Nella home [Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)è possibile riattivare il controller per visualizzarne il livello della batteria sul lato inverso del modello virtuale. Non è presente alcun indicatore del livello della batteria fisica.

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>È possibile usare questi controller senza visore VR? Solo per l'inputstick/trigger/etc?

Non per le applicazioni universali Windows universali.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Vedere [risoluzione dei problemi del controller del movimento](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) nella Guida per gli appassionati.

## <a name="filing-motion-controller-feedbackbugs"></a>Invio di commenti e suggerimenti/bug del controller del movimento

[Inviare commenti e](/hololens/hololens-feedback) suggerimenti Hub di Feedback, usando la categoria "Mixed Reality -> Input" (Input > realtà mista).

## <a name="see-also"></a>Vedi anche

* [Controller del movimento in Unity](../develop/unity/motion-controllers-in-unity.md)
* [Mani e controller del movimento in DirectX](../develop/native/hands-and-motion-controllers-in-directx.md)
* [Movimenti](gaze-and-commit.md#composite-gestures)
* [Guida per gli appassionati: La tua Windows Mixed Reality casa](/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [Guida per gli appassionati: Uso di giochi & app in Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [Funzionamento del tracciamento dall'interno verso l'esterno](/windows/mixed-reality/enthusiast-guide/tracking-system)