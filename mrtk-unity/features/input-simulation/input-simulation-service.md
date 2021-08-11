---
title: Servizio di simulazione input
description: Documentazione sul servizio di simulazione input in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: f329cceded5e510d3d4fc1a1c13b5a504f1f3669ad408b733267595e77dd15a6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227584"
---
# <a name="input-simulation-service"></a>Servizio di simulazione input

![Simulazione input MRTK](../images/input-simulation/MRTK_InputSimulation_Hero.jpg)

Con la simulazione di input di MRTK è possibile testare vari tipi di interazioni nell'editor di Unity senza compilare e distribuire in un dispositivo. In questo modo è possibile scorrere rapidamente le idee nel processo di progettazione e sviluppo. Usare combinazioni di tastiera e mouse per controllare gli input simulati.

Il servizio di simulazione input emula il comportamento dei dispositivi e delle piattaforme che potrebbero non essere disponibili nell'editor di Unity. Alcuni esempi:

* HoloLens rilevamento della testa del dispositivo VR
* HoloLens movimenti della mano
* HoloLens 2 tracciamento manuale articolato
* HoloLens 2 tracciamento oculare
* Controller di dispositivo VR

> [!WARNING]
> Questa operazione non funziona quando si usa l'emulazione Olografica XR di Unity > emulazione = "Simulate in Editor". La simulazione nell'editor di Unity prenderà il controllo dalla simulazione di input di MRTK. Per usare il servizio di simulazione dell'input MRTK, è necessario impostare L'emulazione holografica XR su Modalità di emulazione = *"Nessuno"*

## <a name="how-to-use-mrtk-input-simulation"></a>Come usare la simulazione dell'input MRTK 

La simulazione di input è abilitata per impostazione predefinita nei profili forniti con MRTK. È sufficiente fare clic sul **pulsante Riproduci** per eseguire la scena con il supporto della simulazione di input.

* Premere **i tasti W, A, S, D, Q, E** per spostare la fotocamera.
* Tenere premuto **il pulsante destro del mouse** e spostare il mouse per guardarsi intorno.
* Per visualizzare le mani simulate, premere barra **spaziatrice (destra)** o **MAIUSC sinistro (sinistra)**
* Per mantenere le mani simulate nella visualizzazione, premere **il tasto T** o **Y**
* Per ruotare le mani simulate, tenere premuto **CTRL e** spostare il mouse

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OYrm]

## <a name="in-editor-input-simulation-cheat-sheet"></a>Nel foglio di verifica della simulazione di input dell'editor

Premere **CTRL SINISTRO + H** nella scena HandInteractionExamples per visualizzare un foglio di trucchi con i controlli di simulazione input.

> ![Scheda di controllo della simulazione di input MRTK](../images/input-simulation/MRTK_InputSimulation_CheatSheet.png)


## <a name="enabling-the-input-simulation-service"></a>Abilitazione del servizio di simulazione dell'input

Nella configurazione del provider di dati del sistema di input, il servizio Simulazione input può essere configurato con quanto segue.

* **Il** tipo deve *essere Microsoft.MixedReality.Toolkit. Input > InputSimulationService*.
* **Le piattaforme supportate per impostazione predefinita** includono tutte le piattaforme *editor,* poiché il servizio usa l'input tramite tastiera e mouse.

> [!NOTE]
> Il servizio Simulazione input può essere usato in altri endpoint della piattaforma, ad esempio autonomo, modificando la proprietà **Piattaforma/i supportata/i** in modo da includere le destinazioni desiderate.
> <br/><img src="../images/input-simulation/InputSimulationSupportedPlatforms.gif" alt="Input Simulation Supported Platforms" width="550px">

## <a name="camera-control"></a>Controllo fotocamera

Lo spostamento della testa può essere emulato dal servizio simulazione di input.

### <a name="rotating-the-camera"></a>Rotazione della fotocamera

1. Passare il puntatore del mouse sulla finestra dell'editor del riquadro di visualizzazione.
    *Potrebbe essere necessario fare clic sulla finestra per assegnare lo stato attivo all'input se i pulsanti non funzionano.*
1. Tenere premuto il pulsante **Di visualizzazione del mouse** (impostazione predefinita: Pulsante destro del mouse).
1. Spostare il mouse nella finestra del viewport per ruotare la fotocamera.
1. Usare la rotellina di scorrimento per ruotare la fotocamera intorno alla direzione di visualizzazione.

La velocità di rotazione della fotocamera può essere configurata modificando l'impostazione **Mouse Look Speed** nel profilo di simulazione di input.

In alternativa, usare gli assi **Look Horizontal** Look Vertical (Look Horizontal Look Vertical) per ruotare la fotocamera (impostazione predefinita: la levetta destra del /  controller di gioco).

### <a name="moving-the-camera"></a>Spostamento della videocamera

Usare gli **assi Sposta** / **orizzontale verticale** per spostare la fotocamera (impostazione predefinita: tasti WASD o levetta a sinistra del controller di gioco).

La posizione e gli angoli di rotazione della fotocamera possono essere impostati in modo esplicito anche nella finestra degli strumenti. La fotocamera può essere reimpostata sul valore predefinito usando il **pulsante** Reimposta.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a>Simulazione controller

La simulazione di input supporta dispositivi controller emulati (ad esempio controller di movimento e mani). Questi controller virtuali possono interagire con qualsiasi oggetto che supporta controller regolari, ad esempio pulsanti o oggetti afferrabili.

### <a name="controller-simulation-mode"></a>Modalità di simulazione controller

Nella finestra [degli strumenti di simulazione dell'input](#input-simulation-tools-window) **l'impostazione Modalità simulazione controller predefinita** passa da tre modelli di input distinti. Questa modalità predefinita può essere impostata anche nel profilo di simulazione di input.

* *Mani articolate:* simula un dispositivo a mano completamente articolato con dati sulla posizione delle giunzione.

   Emula HoloLens 2 di interazione.

   Le interazioni basate sul posizionamento preciso della mano o sull'uso del tocco possono essere simulate in questa modalità.

* *Movimenti della mano:* simula un modello di mano semplificato con il tocco dell'aria e i movimenti di base.

   Emula [HoloLens di interazione.](/windows/mixed-reality/gestures)

   Lo stato attivo viene controllato usando il puntatore Sguardo fisso. Il *movimento Air Tap* viene usato per interagire con i pulsanti.

* *Controller di movimento:* simula un controller di movimento usato con visori VR che funziona in modo analogo alle interazioni da lontano con le mani articolate.

   Emula il modello di interazione vr con controller.

   I tasti trigger, grab e menu vengono simulati tramite input da tastiera e mouse.

### <a name="simulating-controller-movement"></a>Simulazione del movimento del controller

Premere e tenere premuto il tasto di manipolazione del **controller sinistro/destro** (impostazione predefinita: Maiusc *sinistro* per il controller sinistro e *Spazio* per il controller destro) per ottenere il controllo di uno dei due controller. Mentre viene premuto il tasto di manipolazione, il controller verrà visualizzato nel viewport. Una volta rilasciata la chiave di manipolazione, i controller scompariranno dopo un breve **timeout di nascondi controller**.

I controller possono essere attivati e bloccati rispetto alla fotocamera nella finestra degli strumenti di simulazione [di input](#input-simulation-tools-window) o premendo Il tasto Toggle **Left/Right Controller (Attiva/Disattiva** tasto controller sinistro/destro) (impostazione predefinita: *T* per sinistra e *Y* per destra). Premere di nuovo il tasto di attivazione/disattivazione per nascondere nuovamente i controller. Per modificare i controller, **deve essere mantenuta la** chiave di manipolazione del controller sinistro/destro. Toccando due volte **il tasto di manipolazione del controller sinistro/destro** è anche possibile attivare/disattivare i controller.

Lo spostamento del mouse sposterà il controller nel piano di visualizzazione. I controller possono essere spostati più avanti o più vicino alla fotocamera usando la **rotellina del mouse.**

Per ruotare i controller usando il mouse, tenere premuto il  tasto di manipolazione del **controller sinistro/destro** *(MAIUSC* sinistro o *SPAZIO)* e il pulsante Ruota controller **(impostazione** predefinita: tasto *CTRL* SINISTRO) e quindi spostare il mouse per ruotare il controller. La velocità di rotazione del controller può essere configurata modificando l'impostazione **Velocità rotazione controller mouse** nel profilo di simulazione di input.

Tutto il posizionamento della mano può essere modificato anche nella finestra degli [strumenti di simulazione dell'input,](#input-simulation-tools-window)inclusa la reimpostazione delle mani sul valore predefinito.

### <a name="additional-profile-settings"></a>Impostazioni del profilo aggiuntive

* **Il moltiplicatore di profondità del** controller controlla la sensibilità dello spostamento della profondità della rotellina del mouse. Un numero maggiore velocizza lo zoom del controller.
* **Distanza controller predefinita** è la distanza iniziale dei controller dalla fotocamera. Facendo clic **sul pulsante Reimposta,** i controller verranno posizionati anche a questa distanza.
* **Quantità di jitter del** controller aggiunge movimento casuale ai controller. Questa funzionalità può essere usata per simulare un rilevamento non accurato del controller nel dispositivo e garantire che le interazioni funzionino correttamente con l'input rumoroso.

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a>Movimenti della mano

È anche possibile simulare movimenti della mano, ad esempio avvicinamento, afferramento, poking e così via.

1. Abilitare il controllo manuale usando il tasto di manipolazione del **controller sinistro/destro** (*MAIUSC sinistro* o *SPAZIO*)

2. Durante la manipolazione, tenere premuto un pulsante del mouse per eseguire un movimento della mano.

È possibile eseguire il mapping di ognuno dei pulsanti del mouse per trasformare la forma della mano in un movimento diverso usando le impostazioni movimento mano *sinistra/centrale/destra.* Il *movimento manuale predefinito* è la forma della mano quando non viene premuto alcun pulsante.

> [!NOTE]
> Il *movimento avvicinamento* delle dita è l'unico movimento che esegue l'azione "Seleziona" a questo punto.

### <a name="one-hand-manipulation"></a>Manipolazione con una mano

1. Premere e tenere premuto il tasto di manipolazione del **controller sinistro/destro** (*MAIUSC sinistro* o *SPAZIO*)
2. Punto in corrispondenza dell'oggetto
3. Tenere premuto il pulsante del mouse per avvicinare le dita
4. Usare il mouse per spostare l'oggetto
5. Rilasciare il pulsante del mouse per arrestare l'interazione

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a>Manipolazione a due mani

Per la manipolazione di oggetti con due mani contemporaneamente, è consigliabile utilizzare la modalità mano persistente.

1. Attivare o disattivare entrambe le mani premendo i tasti di attivazione/disattivazione (*T/Y*).
1. Manipolare una mano alla volta:
    1. Tenere **premuto Spazio** per controllare la mano destra
    1. Spostare la mano nel punto in cui si vuole afferrare l'oggetto
    1. Premere il **pulsante sinistro del mouse** per attivare il movimento *Avvicinamento delle dita.*
    1. Rilasciare **spazio** per arrestare il controllo della mano destra. La mano verrà bloccata sul posto e bloccata nel movimento *avvicinamento* delle dita perché non viene più manipolata.
1. Ripetere il processo con l'altra mano, afferrando lo stesso oggetto in un secondo punto.
1. Ora che entrambe le mani afferrano lo stesso oggetto, è possibile spostarle per eseguire la manipolazione a due mani.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a>Interazione GGV (sguardo fisso, movimento e voce)

Per impostazione predefinita, l'interazione GGV è abilitata nell'editor mentre nella scena non sono presenti mani articolate.

1. Ruotare la fotocamera in modo che punti il cursore dello sguardo verso l'oggetto interagiscibile (pulsante destro del mouse)
1. Fare clic e tenere premuto **il pulsante sinistro del mouse** per interagire
1. Ruotare di nuovo la fotocamera per modificare l'oggetto

È possibile disattivare questa opzione attivando *l'opzione Is Hand Free Input Enabled* all'interno del profilo di simulazione di input.

Inoltre, è possibile usare le mani simulate per l'interazione GGV

1. Abilitare la simulazione GGV passando **da Modalità** simulazione manuale a *Movimenti* nel profilo [di simulazione di input](#enabling-the-input-simulation-service)
1. Ruotare la fotocamera in modo che punti il cursore dello sguardo verso l'oggetto interagiscibile (pulsante destro del mouse)
1. Tenere **premuto Spazio** per controllare la mano destra
1. Fare clic e tenere premuto **il pulsante sinistro del mouse** per interagire
1. Usare il mouse per spostare l'oggetto
1. Rilasciare il pulsante del mouse per arrestare l'interazione

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a>Generazione di eventi di teletrasporto

Per generare l'evento teletrasporto nella simulazione di input, configurare l'Impostazioni  Movimento mano nel profilo di simulazione di input in modo che uno esegua il movimento di inizio teletrasporto mentre l'altro esegua il movimento di fine **teletrasporto.** Il **movimento Teleport Start** (Inizio teletrasporto) attiva l'indicatore di misura teletrasporto, mentre la gesure **Teleport End** (Fine teletrasporto) completa l'azione di teletrasporto e sposta l'utente.

La posizione y del teletrasporto risultante dipende dall'spostamento della fotocamera lungo l'asse y. Nell'editor questo valore è 0 per impostazione predefinita, quindi usare i tasti **Q** ed **E** per adattarlo all'altezza appropriata.

![Simulazione di input teletrasporto Impostazioni](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a>Interazione del controller di movimento

I controller di movimento simulati possono essere manipolati nello stesso modo delle mani articolate. Il modello di interazione è simile all'interazione estrema della mano articolata, mentre i tasti trigger, grab e menu vengono mappati rispettivamente al pulsante sinistro del *mouse,* al tasto *G* e al tasto *M.*

### <a name="eye-tracking"></a>Tracciamento oculare

[La simulazione del](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) tracciamento oculare può essere abilitata selezionando **l'opzione Simula** posizione oculare in [Profilo simulazione input](#enabling-the-input-simulation-service). Questo non deve essere usato con le interazioni di stile del controller di movimento o GGV (quindi assicurarsi che La modalità simulazione **controller** predefinita sia impostata su *Mano articolata).*

## <a name="input-simulation-tools-window"></a>Finestra degli strumenti di simulazione di input

Abilitare la finestra degli strumenti di simulazione input dal menu **Mixed Reality**  >  **Toolkit** Utilities Input Simulation  >    >  **(Simulazione input utilità di** input). Questa finestra consente di accedere allo stato della simulazione di input durante la modalità di riproduzione.

## <a name="viewport-buttons-optional"></a>Pulsanti del riquadro di visualizzazione (facoltativo)

È possibile specificare un prefab per i pulsanti nell'editor per controllare il posizionamento della mano di base nel profilo di simulazione di input in **Indicators Prefab**. Si tratta di un'utilità facoltativa. È possibile accedere alle stesse funzionalità nella finestra degli strumenti di [simulazione di input](#input-simulation-tools-window).

> [!NOTE]
> Gli indicatori del viewport sono disabilitati per impostazione predefinita, in quanto possono talvolta interferire con le interazioni dell'interfaccia utente di Unity. Vedere il problema [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106). Per abilitare, aggiungere il prefab InputSimulationIndicators a **Indicators Prefab**.

Le icone a mano mostrano lo stato delle mani simulate:

* ![Icona a forma di mano non tracciata](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) La mano non viene tracciata. Fare clic per abilitare la mano.
* ![Icona mano tracciata](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Icona mano tracciata") La mano viene tracciata, ma non controllata dall'utente. Fare clic per nascondere la mano.
* ![Icona della mano controllata](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Icona della mano controllata") La mano viene rilevata e controllata dall'utente. Fare clic per nascondere la mano.
* ![Icona a forma di mano di reimpostazione](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Icona a forma di mano di reimpostazione") Fare clic per ripristinare la posizione predefinita della mano.


## <a name="see-also"></a>Vedi anche

* [Profilo di sistema di input](../input/input-providers.md).
