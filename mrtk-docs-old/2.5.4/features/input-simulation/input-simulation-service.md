---
title: InputSimulationServices
description: Documentazione sul servizio di simulazione input in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 0c6ffc730882d0550b85e441e8acd3e91e9ac0552285e344596aec295def2202
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212676"
---
# <a name="input-simulation-service"></a>Servizio di simulazione input

Il servizio di simulazione input emula il comportamento di dispositivi e piattaforme che potrebbero non essere disponibili nell'editor di Unity. Alcuni esempi:

* HoloLens o il rilevamento della testa del dispositivo VR
* HoloLens movimenti della mano
* HoloLens 2 tracciamento delle mani articolato
* HoloLens 2 tracciamento oculare
* Controller del dispositivo VR

Gli utenti possono usare una combinazione convenzionale di tastiera e mouse per controllare i dispositivi simulati in fase di esecuzione. Questo approccio consente di testare le interazioni nell'editor di Unity senza prima eseguire la distribuzione in un dispositivo.

> [!WARNING]
> Questa operazione non funziona quando si usa l'emulazione olografica XR di Unity > emulazione = "Simula nell'editor". La simulazione nell'editor di Unity prenderà il controllo dalla simulazione di input di MRTK. Per usare il servizio di simulazione dell'input MRTK, è necessario impostare XR Holographic Emulation (Emulazione olografica XR) su Emulation Mode = *"None"*

## <a name="enabling-the-input-simulation-service"></a>Abilitazione del servizio di simulazione dell'input

La simulazione di input è abilitata per impostazione predefinita nei profili forniti con MRTK.

La simulazione di input è tuttavia un servizio di [realtà](../../architecture/mixed-reality-services.md) mista facoltativo e può essere rimosso come provider di dati nel profilo [input system](../input/input-providers.md).

Nella configurazione del provider di dati del sistema di input, il servizio Simulazione input può essere configurato con quanto segue.

* **Il** tipo deve *essere Microsoft.MixedReality.Toolkit. Input > InputSimulationService*.
* **Le piattaforme supportate per impostazione predefinita** includono tutte le piattaforme *dell'editor,* poiché il servizio usa l'input da tastiera e mouse.

> [!NOTE]
> Il servizio Simulazione input può essere usato in altri  endpoint della piattaforma, ad esempio autonomi, modificando la proprietà Piattaforme supportate in modo da includere le destinazioni desiderate.
> ![Piattaforme supportate per la simulazione di input](../images/input-simulation/InputSimulationSupportedPlatforms.gif)

## <a name="input-simulation-tools-window"></a>Finestra Degli strumenti di simulazione input

Abilitare la finestra degli strumenti di simulazione input dal menu **Mixed Reality Toolkit** Utilities Input Simulation  >    >  **(Simulazione input** utilità di realtà mista). Questa finestra consente di accedere allo stato della simulazione di input durante la modalità di riproduzione.

## <a name="viewport-buttons"></a>Pulsanti viewport

È possibile specificare un prefab per i pulsanti nell'editor per controllare il posizionamento delle mani di base nel profilo di simulazione di input in **Indicators Prefab (Prefab indicatori).** Si tratta di un'utilità facoltativa. È possibile accedere alle stesse funzionalità nella finestra degli strumenti di [simulazione di input](#input-simulation-tools-window).

> [!NOTE]
> Gli indicatori del viewport sono disabilitati per impostazione predefinita, perché attualmente possono interferire con le interazioni dell'interfaccia utente di Unity. Vedere il problema [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106). Per abilitare, aggiungere il prefab InputSimulationIndicators a **Indicators Prefab**.

Le icone a mano mostrano lo stato delle mani simulate:

* ![Icona mano non tracciata](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) La mano non viene tracciata. Fare clic per abilitare la mano.
* ![Icona mano tracciata](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Icona mano tracciata") La mano viene tracciata, ma non controllata dall'utente. Fare clic per nascondere la mano.
* ![Icona mano controllata](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Icona mano controllata") La mano viene rilevata e controllata dall'utente. Fare clic per nascondere la mano.
* ![Icona a forma di mano di reimpostazione](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Icona a forma di mano di reimpostazione") Fare clic per ripristinare la posizione predefinita della mano.

## <a name="in-editor-input-simulation-cheat-sheet"></a>Nel foglio di controllo della simulazione dell'input dell'editor

Premere CTRL SINISTRO + H nella scena HandInteractionExamples per visualizzare un foglio di controllo con i controlli simulazione input.

![Foglio di controllo della simulazione dell'input](https://user-images.githubusercontent.com/39840334/86066480-13637f00-ba27-11ea-8814-d222d548f684.gif)

## <a name="camera-control"></a>Controllo fotocamera

Lo spostamento della testa può essere emulato dal servizio di simulazione input.

### <a name="rotating-the-camera"></a>Rotazione della fotocamera

1. Passare il puntatore del mouse sulla finestra dell'editor del viewport.
    *Potrebbe essere necessario fare clic sulla finestra per assegnare lo stato attivo all'input se le pressione del pulsante non funzionano.*
1. Tenere premuto il **pulsante Aspetto del mouse** (impostazione predefinita: Pulsante destro del mouse).
1. Spostare il mouse nella finestra del viewport per ruotare la fotocamera.
1. Usare la rotellina di scorrimento per ruotare la fotocamera intorno alla direzione di visualizzazione.

La velocità di rotazione della fotocamera può essere configurata modificando l'impostazione **Mouse Look Speed (Velocità** dell'aspetto del mouse) nel profilo di simulazione di input.

In alternativa, usare gli assi **Look Horizontal** Look Vertical (Aspetto orizzontale verticale) per ruotare la fotocamera /  (impostazione predefinita: levetta destra del controller di gioco).

### <a name="moving-the-camera"></a>Spostamento della videocamera

Usare gli **assi Sposta spostamento** / **orizzontale Verticale** per spostare la fotocamera (impostazione predefinita: chiavi WASD o levetta sinistra del controller di gioco).

Anche la posizione della fotocamera e gli angoli di rotazione possono essere impostati in modo esplicito nella finestra degli strumenti. La fotocamera può essere reimpostata sul valore predefinito usando il **pulsante Reimposta.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

## <a name="controller-simulation"></a>Simulazione controller

La simulazione di input supporta i dispositivi controller emulati,ad esempio controller del movimento e mani. Questi controller virtuali possono interagire con qualsiasi oggetto che supporta controller normali, ad esempio pulsanti o oggetti afferrabili.

### <a name="controller-simulation-mode"></a>Modalità di simulazione controller

Nella finestra degli [strumenti di simulazione dell'input](#input-simulation-tools-window) **l'impostazione Modalità** di simulazione controller predefinita consente di alternare tre modelli di input distinti. Questa modalità predefinita può essere impostata anche nel profilo di simulazione di input.

* *Mani articolate:* simula un dispositivo a mano completamente articolato con dati di posizione giunzione.

   Emula HoloLens 2 di interazione.

   In questa modalità è possibile simulare interazioni basate sul posizionamento preciso della mano o sull'uso del tocco.

* *Movimenti della mano:* simula un modello di mano semplificato con tocco e movimenti di base.

   Emula [HoloLens di interazione.](https://docs.microsoft.com/windows/mixed-reality/gestures)

   Lo stato attivo viene controllato usando il puntatore Sguardo fisso. Il *movimento tocco viene* usato per interagire con i pulsanti.

* *Controller del* movimento: simula un controller del movimento usato con visori VR che funziona in modo analogo alle interazioni da lontano con le mani articolate.

   Emula il visore VR con il modello di interazione dei controller.

   I tasti di attivazione, cattura e menu vengono simulati tramite input da tastiera e mouse.

### <a name="simulating-controller-movement"></a>Simulazione del movimento del controller

Per ottenere il controllo di uno dei due controller, tieni premuto il tasto di manipolazione del controller **sinistro/destro** (impostazione *predefinita:* Maiusc di sinistra per il controller sinistro e *Spazio* per il controller destro). Mentre viene premuto il tasto di manipolazione, il controller verrà visualizzato nel viewport. Dopo il rilascio della chiave di manipolazione, i controller scompariranno dopo un breve timeout di nascondere **il controller.**

I controller possono essere attivati e bloccati rispetto alla fotocamera nella finestra degli strumenti di simulazione di [input](#input-simulation-tools-window) o premendo Toggle **Left/Right Controller Key (Attiva/Disattiva** tasto controller sinistro/destro) (impostazione predefinita: *T* per sinistra e *Y* per destra). Premere di nuovo l'interruttore per nascondere di nuovo i controller. Per manipolare i controller, **è necessario utilizzare** la chiave di manipolazione del controller sinistro/destro. Toccando due volte **la chiave di manipolazione del controller sinistro/destro** è anche possibile attivare/disattivare i controller.

Lo spostamento del mouse sposterà il controller nel piano di visualizzazione. I controller possono essere spostati più o più vicino alla fotocamera usando la rotellina **del mouse.**

Per ruotare i controller usando il mouse, tieni premuto il  tasto di manipolazione del controller **sinistro/destro** *(MAIUSC* sinistro o BARRA SPAZIATRICE) e il pulsante di rotazione del controller **(impostazione** predefinita: pulsante *CTRL* sinistro) e quindi sposta il mouse per ruotare il controller. La velocità di rotazione del controller può essere configurata modificando l'impostazione **Velocità di rotazione del controller del mouse** nel profilo di simulazione di input.

Tutto il posizionamento della mano può essere modificato anche nella finestra [degli strumenti di simulazione dell'input,](#input-simulation-tools-window)inclusa la reimpostazione delle mani sul valore predefinito.

### <a name="additional-profile-settings"></a>Impostazioni aggiuntive del profilo

* **Il moltiplicatore di profondità del** controller controlla la sensibilità del movimento di profondità della rotellina del mouse. Un numero maggiore velocizza lo zoom del controller.
* **Distanza controller predefinita** è la distanza iniziale dei controller dalla fotocamera. Facendo clic **sul pulsante Reimposta,** i controller verranno posizionati anche a questa distanza.
* **Quantità di instabilità del** controller aggiunge movimento casuale ai controller. Questa funzionalità può essere usata per simulare un monitoraggio del controller non accurato nel dispositivo e garantire che le interazioni funzionino correttamente con l'input rumoroso.

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="hand-gestures"></a>Movimenti della mano

È anche possibile simulare movimenti della mano, ad esempio avvicinamento delle dita, afferramento, simulazione e così via.

1. Abilitare il controllo manuale usando **il tasto di manipolazione del controller sinistro/destro** *(MAIUSC sinistro* o BARRA *SPAZIATRICE)*

2. Durante la manipolazione, tieni premuto un pulsante del mouse per eseguire un movimento della mano.

È possibile eseguire il mapping di ognuno dei pulsanti del mouse per trasformare la forma della mano in un movimento diverso usando le impostazioni Movimento mano *sinistra/centrale/destra* del mouse. Il *movimento della mano predefinito* è la forma della mano quando non viene premuto alcun pulsante.

> [!NOTE]
> Il *movimento avvicinamento* delle dita è l'unico movimento che esegue l'azione "Seleziona" a questo punto.

### <a name="one-hand-manipulation"></a>Manipolazione con una mano

1. Premere e tenere premuto il tasto di manipolazione del **controller sinistro/destro** *(MAIUSC sinistro* o *BARRA SPAZIATRICE)*
2. Punto in corrispondenza dell'oggetto
3. Tenere premuto il pulsante del mouse per avvicinare le dita
4. Usare il mouse per spostare l'oggetto
5. Rilasciare il pulsante del mouse per arrestare l'interazione

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="two-hand-manipulation"></a>Manipolazione a due mani

Per la manipolazione di oggetti con due mani contemporaneamente, è consigliabile la modalità mano persistente.

1. Attivare o disattivare entrambe le mani premendo i tasti di alternanza *(T/Y).*
1. Modificare una mano alla volta:
    1. Tenere **premuto lo** spazio per controllare la mano destra
    1. Spostare la mano nel punto in cui si vuole afferrare l'oggetto
    1. Premere il pulsante **sinistro del mouse per** attivare il movimento *avvicinamento delle dita.*
    1. Rilasciare **lo spazio** per interrompere il controllo della mano destra. La mano verrà bloccata sul posto e bloccata nel movimento *avvicinamento* delle dita perché non viene più manipolata.
1. Ripetere il processo con l'altra mano, afferrando lo stesso oggetto in un secondo punto.
1. Ora che entrambe le mani afferrano lo stesso oggetto, puoi spostarle per eseguire la manipolazione a due mani.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="ggv-gaze-gesture-and-voice-interaction"></a>Interazione GGV (sguardo fisso, movimento e voce)

Per impostazione predefinita, l'interazione GGV è abilitata nell'editor, mentre nella scena non sono presenti mani articolate.

1. Ruotare la fotocamera in modo che punti il cursore dello sguardo fisso sull'oggetto intervienibile (pulsante destro del mouse)
1. Fare clic e tenere **premuto il pulsante sinistro del mouse** per interagire
1. Ruotare di nuovo la fotocamera per modificare l'oggetto

È possibile disattivare questa opzione attivando l'opzione *Is Hand Free Input Enabled (Input* senza mano abilitato) all'interno del profilo di simulazione input.

È anche possibile usare le mani simulate per l'interazione GGV

1. Abilitare la simulazione GGV impostando **Modalità simulazione manuale** su *Movimenti* nel profilo di [simulazione input](#enabling-the-input-simulation-service)
1. Ruotare la fotocamera in modo che punti il cursore dello sguardo fisso sull'oggetto intervienibile (pulsante destro del mouse)
1. Tenere **premuto lo** spazio per controllare la mano destra
1. Fare clic e tenere **premuto il pulsante sinistro del mouse** per interagire
1. Usare il mouse per spostare l'oggetto
1. Rilasciare il pulsante del mouse per arrestare l'interazione

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="motion-controller-interaction"></a>Interazione del controller del movimento

I controller del movimento simulati possono essere manipolati allo stesso modo delle mani articolate. Il modello di interazione è simile all'interazione da lontano della mano articolata, mentre il trigger, la cattura e i tasti di menu sono mappati rispettivamente al pulsante sinistro del *mouse,* ai tasti *G* e *M.*

### <a name="eye-tracking"></a>Tracciamento oculare

[La simulazione del](../eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) tracciamento oculare può essere abilitata selezionando **l'opzione Simulate Eye Position** (Simula posizione oculare) in Input Simulation Profile [(Profilo simulazione input).](#enabling-the-input-simulation-service) Questo non deve essere usato con interazioni di tipo GGV o controller del movimento (assicurarsi quindi che **La** modalità di simulazione controller predefinita sia impostata su *Mano articolata).*

## <a name="see-also"></a>Vedi anche

* [Profilo di sistema di input](../input/input-providers.md).
