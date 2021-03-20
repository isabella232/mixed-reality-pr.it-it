---
title: InputSimulationServices
description: Documentazione sul servizio di simulazione di input in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: a2ff5e30db2d4c8e7d36dcf7faa3297b50f38fdc
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693948"
---
# <a name="input-simulation-service"></a>Servizio di simulazione di input

Il servizio simulazione input emula il comportamento di dispositivi e piattaforme che potrebbero non essere disponibili nell'editor di Unity. Alcuni esempi:

* Rilevamento Head del dispositivo HoloLens o VR
* Movimenti della mano HoloLens
* HoloLens 2-rilevamento a mano articolato
* HoloLens 2 Eye Tracking
* Controller del dispositivo VR

Gli utenti possono usare una combinazione di tastiera e mouse convenzionale per controllare i dispositivi simulati in fase di esecuzione. Questo approccio consente di testare le interazioni nell'editor di Unity senza prima eseguire la distribuzione in un dispositivo.

> [!WARNING]
> Questa operazione non funziona quando si usa l'emulazione olografica XR di Unity > modalità di emulazione = "simula nell'editor". La simulazione nell'editor di Unity eliminerà il controllo dalla simulazione di input di MRTK. Per usare il servizio simulazione input MRTK, è necessario impostare XR olografica emulazione in modalità emulazione = *"None"*

## <a name="enabling-the-input-simulation-service"></a>Abilitazione del servizio di simulazione di input

La simulazione di input è abilitata per impostazione predefinita nei profili forniti con MRTK.

La simulazione di input è un [servizio di realtà mista](../../architecture/MixedRealityServices.md) facoltativo, ma può essere rimosso come provider di dati nel [profilo di sistema di input](../input/InputProviders.md).

Con la configurazione del provider di dati di sistema di input, il servizio di simulazione di input può essere configurato con quanto segue.

* Il **tipo** deve essere *Microsoft. MixedReality. Toolkit. input > InputSimulationService*.
* Per impostazione predefinita, le piattaforme **supportate** includono tutte le piattaforme dell' *Editor* , poiché il servizio usa l'input della tastiera e del mouse.

> [!NOTE]
> Il servizio di simulazione di input può essere usato in altri endpoint della piattaforma, ad esempio autonomo, modificando la proprietà **piattaforme supportate** per includere le destinazioni desiderate.
> ![Piattaforme supportate per la simulazione di input](../images/input-simulation/InputSimulationSupportedPlatforms.gif)

## <a name="input-simulation-tools-window"></a>Finestra degli strumenti di simulazione di input

Abilitare la finestra degli strumenti di simulazione di input dal menu di simulazione di input di utilità di **reality Toolkit misto**  >    >   . Questa finestra consente di accedere allo stato della simulazione di input durante la modalità di riproduzione.

## <a name="viewport-buttons"></a>Pulsanti viewport

Un prefabbricato per i pulsanti nell'editor per controllare la posizione di base della mano può essere specificato nel profilo di simulazione di input sotto gli **indicatori prefabbricati**. Si tratta di un'utilità facoltativa. è possibile accedere alle stesse funzionalità nella [finestra strumenti di simulazione input](#input-simulation-tools-window).

> [!NOTE]
> Gli indicatori del viewport sono disabilitati per impostazione predefinita, in quanto attualmente possono interferire con le interazioni dell'interfaccia utente di Unity. Vedere [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)di problema. Per abilitare, aggiungere la prefabbricazione InputSimulationIndicators agli **indicatori prefabbricati**.

Le icone a mano mostrano lo stato delle mani simulate:

* ![Icona della mano non rilevata](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) La mano non viene verificata. Fare clic per abilitare la mano.
* ![Icona della mano rilevata](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Icona della mano rilevata") La mano viene rilevata, ma non controllata dall'utente. Fare clic per nascondere la mano.
* ![Icona a mano controllata](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Icona a mano controllata") La mano viene rilevata e controllata dall'utente. Fare clic per nascondere la mano.
* ![Icona di reimpostazione della mano](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Icona di reimpostazione della mano") Fare clic per reimpostare la mano nella posizione predefinita.

## <a name="in-editor-input-simulation-cheat-sheet"></a>Nel foglio informativo sulla simulazione di input dell'editor

Premere CTRL + H nella scena HandInteractionExamples per visualizzare un foglio informativo con i controlli di simulazione di input.

![Foglio informativo sulla simulazione di input](https://user-images.githubusercontent.com/39840334/86066480-13637f00-ba27-11ea-8814-d222d548f684.gif)

## <a name="camera-control"></a>Controllo fotocamera

Il movimento Head può essere emulato dal servizio di simulazione input.

### <a name="rotating-the-camera"></a>Rotazione della fotocamera

1. Passare il puntatore sulla finestra dell'editor del viewport.
    *Potrebbe essere necessario fare clic sulla finestra per assegnargli lo stato attivo per l'input se le pressioni dei pulsanti non funzionano.*
1. Premere e tenere premuto il **pulsante di ricerca del mouse** (impostazione predefinita: pulsante destro del mouse).
1. Spostare il mouse nella finestra del viewport per ruotare la fotocamera.
1. Utilizzare la rotellina di scorrimento per ruotare la fotocamera attorno alla direzione di visualizzazione.

La velocità di rotazione della fotocamera può essere configurata modificando l'impostazione della **velocità di ricerca del mouse** nel profilo di simulazione di input.

In alternativa, usare gli assi verticali Cerca aspetto **orizzontale** /  per ruotare la fotocamera (impostazione predefinita: controller del gioco a destra levetta).

### <a name="moving-the-camera"></a>Spostamento della videocamera

Usare gli assi verticali sposta **orizzontali** /  per spostare la fotocamera (impostazione predefinita: chiavi WASD o controller di gioco a sinistra levetta).

Gli angoli di rotazione e posizione della fotocamera possono essere impostati in modo esplicito anche nella finestra degli strumenti. È possibile ripristinare il valore predefinito della fotocamera utilizzando il pulsante **Reimposta** .

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

## <a name="controller-simulation"></a>Simulazione del controller

La simulazione di input supporta i dispositivi controller emulati (ad esempio, i controller di movimento e le mani). Questi controller virtuali possono interagire con qualsiasi oggetto che supporti i controller normali, ad esempio pulsanti o oggetti afferrabili.

### <a name="controller-simulation-mode"></a>Modalità di simulazione del controller

Nella [finestra strumenti di simulazione input](#input-simulation-tools-window) l'impostazione della **modalità di simulazione del controller predefinita** cambia tra tre modelli di input distinti. Questa modalità predefinita può essere impostata anche nel profilo di simulazione di input.

* *Mano articolata*: simula un dispositivo mano completamente articolato con dati di posizione congiunta.

   Emula il modello di interazione HoloLens 2.

   In questa modalità le interazioni basate sul posizionamento preciso della mano o sull'uso del contatto possono essere simulate.

* *Movimenti della mano*: simula un modello a mano semplificato con tocchi aria e movimenti di base.

   Emula il [modello di interazione HoloLens](https://docs.microsoft.com/windows/mixed-reality/gestures).

   Lo stato attivo è controllato tramite il puntatore a sguardi. Il gesto del *rubinetto d'aria* viene usato per interagire con i pulsanti.

* *Motion controller*: simula un controller di movimento usato con auricolari VR che funziona in modo analogo a molte interazioni con le mani articolate.

   Emula la cuffia VR con il modello di interazione dei controller.

   I tasti trigger, Acquisisci e menu vengono simulati tramite input da tastiera e mouse.

### <a name="simulating-controller-movement"></a>Simulazione dello spostamento del controller

Premere e tenere premuto il **tasto di manipolazione del controller di sinistra/destra** (impostazione predefinita: spostamento a *sinistra* per il controller sinistro e *lo spazio* per il controller destro) per ottenere il controllo di uno dei controller. Mentre viene premuto il tasto di manipolazione, il controller verrà visualizzato nel viewport. Una volta rilasciata la chiave di manipolazione, i controller scompariranno dopo un **timeout di Hide del controller** breve.

I controller possono essere attivati e bloccati rispetto alla fotocamera nella [finestra degli strumenti di simulazione di input](#input-simulation-tools-window) o premendo la **chiave del controller di attivazione/disattivazione** (impostazione predefinita: *T* per left e *Y* per Right). Premere di nuovo il tasto di attivazione per nascondere di nuovo i controller. Per modificare i controller, è necessario che venga mantenuta la **chiave di manipolazione del controller di sinistra/destra** . Il doppio tocco della **chiave di manipolazione del controller di sinistra/destra** può anche attivare/disattivare i controller.

Il movimento del mouse sposterà il controller nel piano di visualizzazione. I controller possono essere spostati in modo più o più vicino alla fotocamera usando la **rotellina del mouse**.

Per ruotare i controller con il mouse, tenere premuto il tasto di **manipolazione del controller di sinistra/destra** (spostamento *a* *sinistra* o *spazio*) e il **pulsante ruota del controller** (impostazione predefinita: pulsante *sinistro CTRL* ), quindi spostare il mouse per ruotare il controller. La velocità di rotazione del controller può essere configurata modificando l'impostazione della **velocità di rotazione del controller del mouse** nel profilo di simulazione di input.

È anche possibile modificare la selezione host della mano nella [finestra strumenti di simulazione input](#input-simulation-tools-window), inclusa la reimpostazione delle lancette per impostazione predefinita.

### <a name="additional-profile-settings"></a>Impostazioni del profilo aggiuntive

* Il **moltiplicatore di profondità del controller** controlla la sensibilità del movimento di profondità della rotellina del mouse. Un numero maggiore accelererà lo zoom del controller.
* La **distanza del controller predefinita** è la distanza iniziale dei controller dalla fotocamera. Se si fa clic sui controller dei pulsanti di **reimpostazione** , i controller vengono posizionati a distanza.
* La **quantità di jitter del controller** aggiunge un movimento casuale ai controller. Questa funzionalità può essere usata per simulare un rilevamento del controller non accurato nel dispositivo e garantire che le interazioni funzionino correttamente con l'input rumoroso.

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="hand-gestures"></a>Movimenti della mano

È anche possibile simulare movimenti della mano, ad esempio pizzicare, afferrare, frugare e così via.

1. Abilitare il controllo della mano usando il **tasto di manipolazione del controller sinistro/destro** (*spostamento a sinistra* o *spazio*)

2. Durante la manipolazione, premere e tenere premuto un pulsante del mouse per eseguire un movimento di mano.

È possibile eseguire il mapping di ognuno dei pulsanti del mouse per trasformare la forma mano in un movimento diverso usando le impostazioni di *movimento della mano sinistra/centrale/destra del mouse* . Il *gesto della mano predefinito* è la forma della mano quando non viene premuto alcun pulsante.

> [!NOTE]
> Il gesto del *pizzico* è l'unico gesto che esegue l'azione "Select" a questo punto.

### <a name="one-hand-manipulation"></a>Manipolazione a mano singola

1. Premere e tenere premuto il **tasto di manipolazione del controller di sinistra/destra** (*spostamento a sinistra* o *spazio*)
2. Punto all'oggetto
3. Premere il pulsante del mouse per pizzicare
4. Usare il mouse per spostare l'oggetto
5. Rilasciare il pulsante del mouse per arrestare l'interazione

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="two-hand-manipulation"></a>Manipolazione a due mano

Per la modifica di oggetti con due mani allo stesso tempo, è consigliabile usare la modalità mano permanente.

1. Premere il tasto di attivazione/disattivazione (*T/Y*) per entrambe le mani.
1. Modificare una mano alla volta:
    1. Mantenere lo **spazio** per controllare la mano destra
    1. Spostare la mano nella posizione in cui si desidera ottenere l'oggetto
    1. Premere il **pulsante sinistro del mouse** per attivare il gesto del *pizzico* .
    1. Liberare **spazio** per arrestare il controllo della mano destra. La mano verrà bloccata sul posto e verrà bloccata nel movimento del *pizzico* perché non è più manipolata.
1. Ripetere il processo con l'altra parte, afferrando lo stesso oggetto in una seconda posizione.
1. Ora che entrambe le mani stanno afferrando lo stesso oggetto, è possibile spostarle per eseguire una manipolazione a due mani.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="ggv-gaze-gesture-and-voice-interaction"></a>Interazione tra GGV (sguardi, movimenti e voce)

Per impostazione predefinita, l'interazione GGV è abilitata nell'editor mentre non vi sono mani articolate presenti nella scena.

1. Ruota la fotocamera per puntare il cursore sullo sguardo all'oggetto interagibile (pulsante destro del mouse)
1. Fare clic e tenendo premuto il **pulsante sinistro del mouse** per interagire
1. Ruotare nuovamente la fotocamera per modificare l'oggetto

Per disattivare questa opzione, è possibile attivare o disattivare l'opzione *è abilitata per l'input Hand Free* all'interno del profilo di simulazione di input.

Inoltre, è possibile usare le mani simulate per l'interazione GGV

1. Abilitare la simulazione GGV cambiando la **modalità di simulazione Hand** in *movimenti* nel [profilo di simulazione di input](#enabling-the-input-simulation-service)
1. Ruota la fotocamera per puntare il cursore sullo sguardo all'oggetto interagibile (pulsante destro del mouse)
1. Mantenere lo **spazio** per controllare la mano destra
1. Fare clic e tenendo premuto il **pulsante sinistro del mouse** per interagire
1. Usare il mouse per spostare l'oggetto
1. Rilasciare il pulsante del mouse per arrestare l'interazione

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="motion-controller-interaction"></a>Interazione del controller di movimento

I controller di movimento simulati possono essere manipolati allo stesso modo delle mani articolate. Il modello di interazione è analogo all'interazione tra la mano articolata, mentre il trigger, il tasto di scelta rapida e i tasti di menu vengono mappati rispettivamente al *pulsante sinistro del mouse*, alla chiave *G* e *M* .

### <a name="eye-tracking"></a>Tracciamento oculare

È possibile abilitare la [simulazione di rilevamento degli occhi](../eye-tracking/EyeTracking_BasicSetup.md#simulating-eye-tracking-in-the-unity-editor) selezionando l'opzione **simula posizione occhio** nel [Profilo simulazione di input](#enabling-the-input-simulation-service). Questo non deve essere usato con le interazioni di stile GGV o Motion controller (assicurarsi che la **modalità di simulazione del controller predefinito** sia impostata su *mano articolata*).

## <a name="see-also"></a>Vedi anche

* [Profilo di sistema di input](../input/InputProviders.md).
