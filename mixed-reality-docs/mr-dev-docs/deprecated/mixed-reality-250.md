---
title: 'Condivisione MR 250: HoloLens visori VR immersive'
description: Seguire questa procedura dettagliata per la scrittura del codice usando visori VR Unity, Visual Studio, HoloLens e Windows Mixed Reality per informazioni dettagliate sulla condivisione di ologrammi tra dispositivi di realtà mista.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, immersive, controller del movimento, condivisione, controller xbox, rete, tra dispositivi
ms.openlocfilehash: 9f1b136193feefece3235d853503c05c69dbd451f9c2916fb178f1bcac0e3972
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208311"
---
# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>Condivisione MR 250: HoloLens e visori VR immersivi

>[!NOTE]
>Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](../develop/unity/tutorials/mr-learning-base-01.md).

Grazie alla flessibilità della piattaforma UWP (Universal Windows Platform), è facile creare un'applicazione che si estende su più dispositivi. Grazie a questa flessibilità, è possibile creare esperienze che sfruttano i punti di forza di ogni dispositivo. Questa esercitazione illustra un'esperienza condivisa di base che viene eseguita in HoloLens e Windows Mixed Reality visori VR immersive. Questo contenuto è stato originariamente recapitato alla conferenza Microsoft Build 2017 a Seattle, WA.

**In questa esercitazione si apprenderà come:**

* Configurare una rete usando UNET.
* Condividere ologrammi tra dispositivi di realtà mista.
* Stabilire una visualizzazione diversa dell'applicazione a seconda del dispositivo di realtà mista usato.
* Creare un'esperienza condivisa in cui gli HoloLens guidano gli utenti di visori VR immersive attraverso alcuni semplici cassoni.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>Condivisione MR 250: HoloLens e visori VR immersivi</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un Windows 10 PC con gli strumenti [di sviluppo necessari](../develop/install-the-tools.md) e configurato per supportare un visore VR Windows Mixed Reality [immersive.](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* Un controller Xbox che funziona con il PC.
* Almeno un dispositivo HoloLens e un visore VR immersive.
* Una rete che consente la trasmissione UDP per l'individuazione.

### <a name="project-files"></a>File di progetto

* Scaricare i [file](https://github.com/Microsoft/MixedReality250/archive/master.zip) richiesti dal progetto. Estrarre i file in un percorso facile da ricordare.
* Questo progetto richiede la [versione consigliata di Unity con Windows Mixed Reality supporto](../develop/install-the-tools.md).

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è disponibile [in GitHub](https://github.com/Microsoft/MixedReality250).

## <a name="chapter-1---holo-world"></a>Capitolo 1 - Holo World

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>Obiettivi

Assicurarsi che l'ambiente di sviluppo sia pronto per l'uso con un progetto semplice.

### <a name="what-we-will-build"></a>Elementi che verranno compilati

Applicazione che mostra un ologramma su un dispositivo HoloLens o un visore VR Windows Mixed Reality immersive.

### <a name="steps"></a>Passaggi

* Aprire Unity.
    * Selezionare **Open** (Apri).
    * Passare alla posizione in cui sono stati estratti i file di progetto.
    * Fare clic su **Seleziona cartella**.
    * *La prima volta che Unity elabora il progetto, è necessario un po' di tempo.*
* Verificare che la realtà mista sia abilitata in Unity.
    * Aprire la finestra di dialogo delle impostazioni di compilazione **(CTRL+MAIUSC+B** o **File > Build Impostazioni...**).
    * Selezionare **Universal Windows Platform e quindi** fare clic su Switch Platform **(Cambia piattaforma).**
    * Selezionare **Modifica>Player Impostazioni**.
    * Nel pannello **Inspector** (Controllo) sul lato destro espandere **XR Impostazioni**.
    * Selezionare la **casella Virtual Reality Supported (Realtà** virtuale supportata).
    * *Windows Mixed Reality deve essere Virtual Reality SDK.*
* Creare una scena.
    * In Hierarchy **(Gerarchia)** fare clic **con il pulsante destro del mouse su Main Camera (Fotocamera** **principale) e selezionare Delete (Elimina).**
    * Da **HoloToolkit > Input > prefab** trascinare **MixedRealityCameraParent** nella **gerarchia**.
* Aggiungere Ologrammi alla scena
    * Da **AppPrefabs trascinare** **Skybox** in **Scene View**.
    * Da **AppPrefabs trascinare** **Manager** nella **gerarchia**.
    * Da **AppPrefabs trascinare** **Isola** in **Gerarchia**.
* Salvare e compilare
    * Salva **(CTRL+S** o **File > Salva scena**)
    * Poiché si tratta di una nuova scena, è necessario assegnare un nome. Il nome non è importante, ma si usa SharedMixedReality.
* Esporta in Visual Studio
    * Aprire il menu di compilazione **(CTRL+MAIUSC+B** o **File > Compila Impostazioni**)
    * Fare clic **su Aggiungi scene aperte.**
    * Controllare **i progetti C# di Unity**
    * Fare clic su **Compila**.
    * Nella finestra di Esplora file visualizzata creare una nuova cartella denominata **App**.
    * Fare clic sulla **cartella App.**
    * Fare clic **su Seleziona cartella.**
    * **Attendere il completamento della compilazione**
    * Nella finestra di Esplora file visualizzata passare alla **cartella App.**
    * Fare doppio clic **su SharedMixedReality.sln** per avviare Visual Studio
* Compilare da Visual Studio
    * Usando la barra degli strumenti superiore modificare la destinazione **in Release** e **x86**.
    * Fare clic sulla freccia accanto a **Computer locale** e **selezionare Dispositivo** da distribuire in HoloLens
    * Fare clic sulla freccia accanto a **Dispositivo e selezionare** **Computer** locale per eseguire la distribuzione per il visore VR di realtà mista.
    * Fare **clic su Debug->Avvia senza eseguire debug** o Premere **CTRL+F5** per avviare l'applicazione.

### <a name="digging-into-the-code"></a>Analisi del codice

Nel pannello del progetto passare a **Assets\HoloToolkit\Input\Scripts\Utilities** e fare doppio clic su **MixedRealityCameraManager.cs** per aprirlo.

**Panoramica:** MixedRealityCameraManager.cs è uno script semplice che regola il livello di qualità e le impostazioni dello sfondo in base al dispositivo. La chiave è HolographicSettings.IsDisplayOpaque, che consente a uno script di rilevare se il dispositivo è un HoloLens (IsDisplayOpaque restituisce false) o un visore VR immersive (IsDisplayOpaque restituisce true).

### <a name="enjoy-your-progress"></a>I tuoi progressi

A questo punto l'applicazione eseguirà semplicemente il rendering di un ologramma. L'interazione verrà aggiunta all'ologramma in un secondo momento. Entrambi i dispositivi eseguiranno lo stesso rendering dell'ologramma. Il visore VR immersive eseguirà anche il rendering di un cielo blu e di uno sfondo cloud.

## <a name="chapter-2---interaction"></a>Capitolo 2 - Interazione

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>Obiettivi

Illustra come gestire l'input per un'Windows Mixed Reality applicazione.

### <a name="what-we-will-build"></a>Elementi che verranno compilati

Sulla base dell'applicazione del capitolo 1, si aggiungeranno funzionalità per consentire all'utente di prelevare l'ologramma e posizionarlo su una superficie reale in HoloLens o su un tavolo virtuale in un visore VR immersive.

**Aggiornamento input:** Nella HoloLens il movimento di selezione è il **tocco dell'aria.** Nei visori VR immersive si userà il **pulsante A** nel controller Xbox. Per altre informazioni, vedere la panoramica [del modello di interazione.](../design/interaction-fundamentals.md)

### <a name="steps"></a>Passaggi

* Aggiungere Gestione input
    * Da **HoloToolkit > Input > prefab** trascinare **InputManager** in **Hierarchy** come elemento figlio di **Managers.**
    * Da **HoloToolkit > Input > prefab > cursore** **trascinare Cursore** in **Hierarchy**.
* Aggiungere il mapping spaziale
    * Da **HoloToolkit > SpatialMapping > Prefab** **trascinare SpatialMapping** in **Hierarchy**.
* Aggiungere lo spazio di riproduzione virtuale
    * In **Hierarchy (Gerarchia)** **espandere MixedRealityCameraParent e** selezionare Boundary **(Limite)**
    * Nel **pannello Inspector** (Controllo) selezionare la casella per abilitare Boundary **(Limite)**
    * Da **AppPrefabs trascinare** **VRRoom** in **Hierarchy**.
* Aggiungere WorldAnchorManager
    * In **Gerarchia** selezionare **Manager.**
    * In **Inspector (Controllo)** fare clic **su Add Component (Aggiungi componente).**
    * Digitare **World Anchor Manager**.
    * Selezionare **World Anchor Manager (Gestione ancoraggi** del mondo) per aggiungerlo.
* Aggiungere TapToPlace all'isola
    * In **Gerarchia** espandere **Isola**.
    * Selezionare **MixedRealityLand.**
    * In **Inspector (Controllo)** fare clic **su Add Component (Aggiungi componente).**
    * Digitare **Tap To Place (Toccare** per posizionare) e selezionarlo.
    * Selezionare **Place Parent (Inserisci elemento padre) al tocco.**
    * Impostare **Offset posizionamento** **su (0, 0.1, 0).**
* Salvare e compilare come in precedenza

### <a name="digging-into-the-code"></a>Analisi del codice

**Script 1 - GamepadInput.cs**

Nel pannello del progetto passare a **Assets\HoloToolkit\Input\Scripts\InputSources** e fare doppio clic su **GamepadInput.cs** per aprirlo. Nello stesso percorso nel pannello del progetto fare doppio clic su **InteractionSourceInputSource.cs.**

Si noti che entrambi gli script hanno una classe di base comune, BaseInputSource.

BaseInputSource mantiene un riferimento a un InputManager, che consente a uno script di attivare gli eventi. In questo caso, l'evento InputClicked è rilevante. Questo sarà importante da ricordare quando si arriva allo script 2, TapToPlace. Nel caso di GamePadInput, viene eseguito il polling del pulsante A nel controller da premere, quindi viene generato l'evento InputClicked. Nel caso di InteractionSourceInputSource, viene generato l'evento InputClicked in risposta a TappedEvent.

**Script 2 - TapToPlace.cs**

Nel pannello del progetto passare a **Assets\HoloToolkit\SpatialMapping\Scripts** e fare doppio clic **su TapToPlace.cs** per aprirlo.

La prima cosa che molti sviluppatori vogliono implementare durante la creazione di un'applicazione olografica è lo Ologrammi con l'input di movimento. Di conseguenza, si è provato a commentare accuratamente questo script. Per questa esercitazione vale la pena evidenziare alcuni aspetti.

Si noti innanzitutto che TapToPlace implementa IInputClickHandler. IInputClickHandler espone le funzioni che gestiscono l'evento InputClicked generato da GamePadInput.cs o InteractionSourceInputSource.cs. OnInputClicked viene chiamato quando BaseInputSource rileva un clic mentre l'oggetto con TapToPlace è attivo. Il airtapping HoloLens o premendo il pulsante A nel controller Xbox attiverà l'evento.

In secondo luogo, il codice viene eseguito in fase di aggiornamento per verificare se viene osservata una superficie in modo da poter posizionare l'oggetto gioco su una superficie, ad esempio una tabella. Il visore VR immersive non ha un concetto di superfici reali, quindi l'oggetto che rappresenta la parte superiore della tabella (Vroom > TableThingy > Cube) è stato contrassegnato con il livello fisico SpatialMapping, quindi il ray cast in Update entra in conflitto con la parte superiore della tabella virtuale.

### <a name="enjoy-your-progress"></a>I tuoi progressi

Questa volta è possibile selezionare l'isola per spostarla. In HoloLens è possibile spostare l'isola su una superficie reale. Nel visore VR immersive è possibile spostare l'isola nella tabella virtuale aggiunta.

## <a name="chapter-3---sharing"></a>Capitolo 3 - Condivisione

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>Obiettivi

Assicurarsi che la rete sia configurata correttamente e dettagli sulla modalità di condivisione degli ancoraggi nello spazio tra i dispositivi.

### <a name="what-we-will-build"></a>Elementi che verranno compilati

Il progetto verrà convertito in un progetto multiplayer. Verranno aggiunti l'interfaccia utente e la logica per ospitare o partecipare alle sessioni. HoloLens gli utenti si vedranno nella sessione con cloud sopra la testa e gli utenti di visori VR immersive avranno cloud vicino alla posizione dell'ancoraggio. Gli utenti nei visori VR immersive visualizzano i HoloLens relativi all'origine della scena. HoloLens gli utenti visualizzano tutti l'ologramma dell'isola nello stesso punto. È fondamentale notare che gli utenti dei visori VR immersive non saranno sull'isola durante questo capitolo, ma si comporteranno in modo molto simile a HoloLens, con una vista panoramica dell'isola.

### <a name="steps"></a>Passaggi

* Rimuovere Isola e VRRoom
    * In **Gerarchia fare** clic con il pulsante destro **del mouse su Isola** e **scegliere Elimina**
    * In **Gerarchia fare** clic con il pulsante destro **del mouse su VRRoom** **e scegliere Elimina**
* Aggiungere Usland
    * Da **AppPrefabs trascinare** **Usland** in **Hierarchy**.
* Da **AppPrefabs trascinare** ognuno degli elementi seguenti in **Hierarchy (Gerarchia):**
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* Salvare e compilare come in precedenza

### <a name="digging-into-the-code"></a>Analisi del codice

Nel pannello del progetto passare a **Assets\AppPrefabs\Support\SharingWithUnet\Scripts** e fare doppio clic su **UnetAnchorManager.cs.** La possibilità per un HoloLens di condividere le informazioni di rilevamento con un altro HoloLens in modo che entrambi i dispositivi possano condividere lo stesso spazio è quasi impossibile. La potenza della realtà mista si attiva quando due o più persone possono collaborare usando gli stessi dati digitali.

Ecco alcuni aspetti da fare riferimento a questo script:

Nella funzione start osservare la presenza di **IsDisplayOpaque**. In questo caso, si finge che l'ancoraggio sia stato stabilito. Ciò è dovuto al fatto che i visori VR immersive non espongono un modo per importare o esportare ancoraggi. Se invece si esegue un'HoloLens, questo script implementa la condivisione di ancoraggi tra i dispositivi. Il dispositivo che avvia la sessione creerà un ancoraggio per l'esportazione. Il dispositivo che partecipa a una sessione richiederà l'ancoraggio dal dispositivo che ha avviato la sessione.

**Esportazione:**

Quando un utente crea una sessione, NetworkDiscoveryWithAnchors chiamerà la funzione CREATEAnchor UNETAnchorManagers. Si seguirà il flusso CreateAnchor.

Si inizia con alcune attività di pulizia, cancellando tutti i dati raccolti per gli ancoraggi precedenti. Viene quindi verificata la presenza di un ancoraggio memorizzato nella cache da caricare. I dati di ancoraggio tendono a essere compresi tra 5 e 20 MB, quindi il riutilizzo degli ancoraggi memorizzati nella cache può risparmiare sulla quantità di dati che è necessario trasferire in rete. Il funzionamento verrà illustrato più avanti. Anche se si riutilizza l'ancoraggio, è necessario prepararne i dati nel caso in cui un nuovo client si aggiusti senza l'ancoraggio.

A proposito di preparazione dei dati di ancoraggio, la classe WorldAnchorTransferBatch espone la funzionalità per preparare i dati di ancoraggio per l'invio a un altro dispositivo o applicazione e la funzionalità per importare i dati di ancoraggio. Poiché si è sul percorso di esportazione, si aggiungerà l'ancoraggio a WorldAnchorTransferBatch e si chiamerà la funzione ExportAsync. ExportAsync chiamerà quindi il callback WriteBuffer mentre genera i dati per l'esportazione. Quando tutti i dati sono stati esportati, verrà chiamato ExportComplete. In WriteBuffer si aggiunge il blocco di dati a un elenco che si mantiene per l'esportazione. In ExportComplete l'elenco viene convertito in una matrice. Viene impostata anche la variabile AnchorName, che attiverà altri dispositivi per richiedere l'ancoraggio se non lo hanno.

In alcuni casi l'ancoraggio non verrà esportato o creerà così pochi dati da riprovare. Qui è sufficiente chiamare nuovamente CreateAnchor.

Una funzione finale nel percorso di esportazione è AnchorFoundRemotely. Quando un altro dispositivo trova l'ancoraggio, lo indica all'host e l'host lo usa come segnale che l'ancoraggio è un "ancoraggio utile" e può essere memorizzato nella cache.

**Importazione:**

Quando un HoloLens si unisce a una sessione, deve importare un ancoraggio. Nella funzione Update di UNETAnchorManager viene eseguito il polling di AnchorName. Quando il nome dell'ancoraggio cambia, inizia il processo di importazione. In primo luogo, si prova a caricare l'ancoraggio con il nome specificato dall'archivio di ancoraggio locale. Se è già presente, è possibile usarlo senza scaricare di nuovo i dati. Se non è già stato fatto, viene chiamato WaitForAnchor che avvierà il download.

Al termine del download, viene NetworkTransmitter_dataReadyEvent chiamata a . Questo segnalerà al ciclo Update di chiamare ImportAsync con i dati scaricati. ImportAsync chiamerà ImportComplete al termine del processo di importazione. Se l'importazione ha esito positivo, l'ancoraggio verrà salvato nell'archivio locale del lettore. PlayerController.cs esegue effettivamente la chiamata a AnchorFoundRemotely per intuire all'host che è stato stabilito un buon ancoraggio.

### <a name="enjoy-your-progress"></a>I tuoi progressi

Questa volta un utente con un HoloLens ospiterà una sessione usando il **pulsante Avvia** sessione nell'interfaccia utente. Altri utenti, sia in HoloLens visore VR immersive, selezioneranno la sessione e quindi selezioneranno il pulsante **Partecipa alla** sessione nell'interfaccia utente. Se sono presenti più persone con HoloLens dispositivi, avranno una nuvola rossa sopra la testa. Sarà presente anche una cloud blu per ogni visore VR immersive, ma le cloud blu non saranno sopra i visori VR, perché i visori VR non cercano di trovare lo stesso spazio delle coordinate del mondo dei dispositivi HoloLens.

Questo punto del progetto è un'applicazione di condivisione contenuta. non fa molto e può fungere da baseline. Nei capitoli successivi inizieremo a creare un'esperienza per gli utenti. Per altre indicazioni sulla progettazione dell'esperienza condivisa, vedere qui.

## <a name="chapter-4---immersion-and-teleporting"></a>Capitolo 4 - Coinvolgimento e teletrasporto

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>Obiettivi

Adattare l'esperienza a ogni tipo di dispositivo di realtà mista.

### <a name="what-we-will-build"></a>Elementi che verranno compilati

L'applicazione verrà aggiornata per consentire agli utenti di visori VR immersive di accedere all'isola con una visualizzazione immersiva. HoloLens gli utenti avranno ancora la vista a vista d'occhio dell'isola. Gli utenti di ogni tipo di dispositivo possono visualizzare altri utenti così come appaiono nel mondo. Ad esempio, gli utenti di visori VR immersive possono visualizzare gli altri avatar in altri percorsi dell'isola e gli utenti HoloLens come cloud enormi sopra l'isola. Gli utenti di visori VR immersive visualizzano anche il cursore del raggio HoloLens sguardo fisso dell'utente se HoloLens'utente sta guardando l'isola. HoloLens gli utenti visualizzano un avatar sull'isola per rappresentare ogni utente di visore VR immersive.

**Aggiornamento dell'input per il dispositivo immersive:**

* I pulsanti del bumper sinistro e destro del controller Xbox ruotano il lettore
* Tenendo premuto il pulsante Y sul controller Xbox, verrà abilitato un [cursore di teletrasporto.](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) Se il cursore ha un indicatore di freccia rotante quando si rilascia il pulsante Y, si verrà teletrasportati alla posizione del cursore.

### <a name="steps"></a>Passaggi

* Aggiungere MixedRealityTeleport a MixedRealityCameraParent
    * In **Hierarchy (Gerarchia)** selezionare **Usland.**
    * In **Inspector (Controllo)** abilitare **Level Control (Controllo livello).**
    * In **Hierarchy (Gerarchia)** selezionare **MixedRealityCameraParent.**
    * In **Inspector (Controllo)** fare clic **su Add Component (Aggiungi componente).**
    * Digitare **Mixed Reality Teleport e** selezionarlo.

### <a name="digging-into-the-code"></a>Analisi del codice

Gli utenti di visori VR immersive verranno connessi ai PC con un cavo, ma l'isola è più grande del cavo lungo. Per compensare, è necessario poter spostare la fotocamera indipendentemente dal movimento dell'utente. Per altre informazioni [sulla progettazione dell'applicazione](../design/comfort.md) di realtà mista (in particolare automozione e movimento), vedi la pagina di comfort.

Per descrivere questo processo, sarà utile definire due termini. In primo **luogo, dolly** sarà l'oggetto che sposta la fotocamera indipendentemente dall'utente. Un oggetto gioco figlio del **dolly** sarà la **fotocamera principale.** La fotocamera principale è collegata alla testa dell'utente.

Nel pannello del progetto passare a **Assets\AppPrefabs\Support\Scripts\GameLogic** e fare doppio clic su **MixedRealityTeleport.cs.**

MixedRealityTeleport ha due processi. In primo luogo, gestisce la rotazione usando i paraurti. Nella funzione di aggiornamento viene eseguito il polling di 'ButtonUp' su LeftBumper e RightBumper. GetButtonUp restituisce true solo nel primo frame in cui un pulsante è attivo dopo essere stato premuto. Se uno dei due pulsanti è stato generato, l'utente deve ruotare.

Quando si ruota si esegue una dissolvenza in uscita e una dissolvenza in entrata usando un semplice script denominato "controllo dissolvenza". In questo modo si impedisce all'utente di visualizzare un movimento innaturale che potrebbe causare disagi. L'effetto dissolvenza in entrata e in uscita è piuttosto semplice. È presente un quad nero anteriore alla **fotocamera principale.** Quando si svada, si esegue la transizione del valore alfa da 0 a 1. Ciò fa sì che i pixel neri del quad eserevano e nascondevano tutto ciò che si nasconde dietro di essi. Quando si torna indietro, il valore alfa viene nuovamente impostato su zero.

Quando si calcola la rotazione, si noti che si sta ruotando il **dolly** ma calcolando la rotazione intorno alla **fotocamera principale.** Questo è importante perché  più lontano dalla fotocamera principale è lontano da 0,0,0, meno accurata sarebbe una rotazione intorno al dolly dal punto di vista dell'utente. Infatti, se non si ruota intorno alla posizione della fotocamera, l'utente si sposterà su un arco intorno al **dolly** anziché ruotare.

Il secondo processo per MixedRealityTeleport è gestire lo spostamento **del dolly**. Questa operazione viene eseguita in SetWorldPosition. SetWorldPosition accetta la posizione del mondo desiderata, la posizione in cui l'utente vuole perciere che l'utente sia insoddisfiato. È necessario inserire la **dolly** in tale posizione meno la posizione locale della **fotocamera principale,** perché tale offset verrà aggiunto a ogni fotogramma.

Un secondo script chiama SetWorldPosition. Diamo un'occhiata a questo script. Nel pannello del progetto passare a **Assets\AppPrefabs\Support\Scripts\GameLogic** e fare doppio clic su **TeleportScript.cs.**

Questo script è leggermente più coinvolto rispetto a MixedRealityTeleport. Lo script verifica che il pulsante Y nel controller Xbox sia premuto. Mentre il pulsante viene premuto, viene eseguito il rendering di un cursore di teletrasporto e lo script esegue il cast di un raggio dalla posizione dello sguardo fisso dell'utente. Se il raggio entra in conflitto con una superficie più o meno che punta verso l'alto, la superficie verrà considerata una buona superficie su cui teletrasportare e l'animazione sul cursore di teletrasporto verrà abilitata. Se il raggio non entra in conflitto con una superficie più o meno che punta verso l'alto, l'animazione sul cursore verrà disabilitata. Quando il pulsante Y viene rilasciato e il punto calcolato del raggio è una posizione valida, lo script chiama SetWorldPosition con la posizione intersecata dal raggio.

### <a name="enjoy-your-progress"></a>I tuoi progressi

Questa volta è necessario trovare un amico.

Ancora una volta, un utente con il HoloLens ospiterà una sessione. Altri utenti verranno uniti alla sessione. L'applicazione inserirà i primi tre utenti per l'aggiunta da un visore VR immersive in uno dei tre percorsi dell'isola. È possibile esplorare l'isola in questa sezione.

Dettagli da notare:

1. È possibile visualizzare i visi nei cloud, che consentono a un utente immerso di vedere in quale direzione HoloLens'utente.
2. Gli avatar sull'isola hanno le erre che ruotano. Non seguiranno ciò che l'utente sta facendo in realtà reale (non sono disponibili tali informazioni), ma è un'esperienza ottimale.
3. Se l HoloLens utente sta guardando l'isola, gli utenti immersi possono visualizzare il cursore.
4. Le cloud che rappresentano l'HoloLens gli utenti proiettano ombreggiature.

## <a name="chapter-5---finale"></a>Capitolo 5 - Finale

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>Obiettivi

Creare un'esperienza interattiva collaborativa tra i due tipi di dispositivi.

### <a name="what-we-will-build"></a>Elementi che verranno compilati

In base al capitolo 4, quando un utente con un visore VR immersive si avvicina a un disassociato nell'isola, gli utenti di HoloLens riceveranno una descrizione comando con un'indicazione del problema. Una volta che tutti gli utenti del visore VR immersivo hanno passato i loro cassoni sul "pad pronto" nella sala razzo, il razzo verrà lanciato.

### <a name="steps"></a>Passaggi

* In **Hierarchy (Gerarchia)** selezionare **Usland.**
* In **Controllo** selezionare **Abilita** collaborazione in Controllo **di livello.**

### <a name="digging-into-the-code"></a>Analisi del codice

Si esamini ora LevelControl.cs. Questo script è il nucleo della logica del gioco e mantiene lo stato del gioco. Poiché si tratta di un gioco multiplayer che usa UNET, è necessario comprendere il flusso dei dati, almeno sufficientemente da modificare questa esercitazione. Per una panoramica più completa di UNET, vedere la documentazione di Unity.

Nel pannello del progetto passare a **Assets\AppPrefabs\Support\Scripts\GameLogic** e fare doppio clic su **LevelControl.cs.**

È possibile comprendere in che modo un visore VR immersive indica che è pronto per il lancio del razzo. L'idoneità per Rocket Launch viene comunicata impostando uno dei tre elementi in un elenco di campi corrispondenti ai tre percorsi dell'isola. Il valore bool di un percorso verrà impostato quando l'utente assegnato al percorso si trova sopra il riquadro marrone all'interno della stanza del razzo. A questo punto, per i dettagli.

Si inizierà con la funzione Update(). Si noterà che è presente una funzione "cheat". È stato usato in fase di sviluppo per testare il lancio del razzo e reimpostare la sequenza. Non funzionerà nell'esperienza multi-utente. Nel momento in cui si internalizza l'infromation seguente, è possibile farlo funzionare. Dopo aver verificata la presenza di bari, si verifica se il giocatore locale è immerso. L'obiettivo è concentrarsi sul modo in cui ci si trova all'obiettivo. All'interno del controllo if (Immersed) è presente una chiamata a CheckGoal nascosta dietro il bool **EnableCollaboration.** Corrisponde alla casella di controllo selezionata durante il completamento dei passaggi per questo capitolo. All'interno di EnableCollaboration viene visualizzata una chiamata a CheckGoal().

CheckGoal esegue alcune operazioni matematiche per verificare se è più o meno in piedi sul pad. In questo caso, Debug.Log "È arrivato all'obiettivo" e quindi si chiama "SendAtGoalMessage()". In SendAtGoalMessage viene chiamato playerController.SendAtGoal. Per risparmiare tempo, ecco il codice:

```cs
private void CmdSendAtGoal(int GoalIndex)
{
    levelState.SetGoalIndex(GoalIndex);
}
```

```cs
public void SendAtGoal(int GoalIndex)
{
    if (isLocalPlayer)
    {
        Debug.Log("sending at goal " + GoalIndex);
        CmdSendAtGoal(GoalIndex);
    }
}
```

Si noti che SendAtGoalMessage chiama CmdSendAtGoal, che chiama levelState.SetGoalIndex, che è di nuovo in LevelControl.cs. A prima vista sembra strano. Perché non chiamare semplicemente SetGoalIndex anziché questo routing strano attraverso il controller del lettore? Il motivo è che microsoft è conforme al modello di dati utilizzato da UNET per mantenere sincronizzati i dati. Per evitare bare e thrashing, UNET richiede che ogni oggetto abbia un utente che ha l'autorità di modificare le variabili sincronizzate. Inoltre, solo l'host (l'utente che ha avviato la sessione) può modificare direttamente i dati. Gli utenti che non sono l'host, ma hanno l'autorità, devono inviare un "comando" all'host che modificherà la variabile. Per impostazione predefinita, l'host ha l'autorità su tutti gli oggetti, ad eccezione dell'oggetto generato per rappresentare l'utente. In questo caso questo oggetto contiene lo script playercontroller. Esiste un modo per richiedere l'autorità per un oggetto e quindi apportare modifiche, ma si sceglie di sfruttare il fatto che il controller del giocatore ha l'autorità autonoma e instradare i comandi attraverso il controller del giocatore.

Detto in altro modo, quando ci siamo trovati al nostro obiettivo, il giocatore deve dire all'organizzatore e l'organizzatore lo dirà a tutti gli altri.

Tornare a LevelControl.cs e vedere SetGoalIndex. In questo caso viene impostato il valore di un valore in un elenco di sincronizzazione (AtGoal). Tenere presente che si è nel contesto dell'host durante questa operazione. Analogamente a un comando, una RPC è un elemento che l'host può emettere che causerà l'esecuzione di codice da parte di tutti i client. Qui viene chiamato "RpcCheckAllGoals". Ogni client verifica singolarmente se sono impostati tutti e tre gli AtGoal e, in tal caso, lancia il razzo.

### <a name="enjoy-your-progress"></a>I tuoi progressi

Sulla base del capitolo precedente, la sessione verrà avviata come in precedenza. Questa volta, quando gli utenti del visore VR immersive ottengono la "porta" sul percorso, viene visualizzata una descrizione comando che può essere visualizzata solo HoloLens utenti. Il HoloLens utenti è responsabile della comunicazione di questo indizio agli utenti nel visore VR immersive. Il razzo verrà lanciato nello spazio una volta che ogni avatar ha fatto un passo nel corrispondente pad brown all'interno del vulcano. La scena verrà reimpostata dopo 60 secondi in modo da poterla eseguire di nuovo.

## <a name="see-also"></a>Vedi anche

* [Input MR 213: Controller del movimento](mixed-reality-213.md)