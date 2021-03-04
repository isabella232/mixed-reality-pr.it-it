---
title: ReleaseNotes
description: Release abbiend della versione corrente di MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: da70601a0e1d2fc2b383a9cbcfcb4b9dd2de4323
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782821"
---
# <a name="microsoft-mixed-reality-toolkit-250-release-notes"></a>Note sulla versione di Microsoft Mixed Reality Toolkit 2.5.0

- [Novità](#whats-new)
- [Modifiche di rilievo](#breaking-changes)
- [Aggiornamento delle linee guida](../updates-deployment/Updating.md#upgrading-to-a-new-version-of-mrtk)
- [Problemi noti](#known-issues)

## <a name="whats-new"></a>Novità

### <a name="unity-package-manager-upm-support"></a>Supporto di gestione pacchetti Unity (UPM)

Il Toolkit di realtà mista ora può essere gestito con gestione pacchetti Unity.

![Pacchetto UPM MRTK Foundation](../features/Images/Packaging/MRTK_FoundationUPM.png)

> [!Note]
> Per importare i pacchetti UPM MRTK, è necessario eseguire alcuni passaggi manuali. Per ulteriori informazioni, vedere il [Toolkit di realtà misto e gestione pacchetti Unity](usingupm.md) .

### <a name="oculus-quest-xrsdk-support"></a>Supporto per Oculus quest XRSDK

MRTK supporta ora l'esecuzione di auricolari e controller di Oculus-quest usando la pipeline nativa di XR SDK. Il rilevamento manuale è supportato anche con il [pacchetto Oculus Integration Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) grazie al lavoro di [Eric Provencher](https://twitter.com/prvncher) su MRTK-quest!

Per istruzioni su come distribuire il dispositivo in Oculus quest usando la nuova pipeline, vedere la Guida all' [installazione di Oculus quest](../features/CrossPlatform/OculusQuestMRTK.md) .

### <a name="scrolling-object-collection"></a>Scorrimento della raccolta di oggetti

Il componente MRTK UX è stato aggiornato da una funzionalità sperimentale e offre maggiore libertà per il layout del contenuto 3D di diverse dimensioni con supporto aggiunto per gli oggetti che non dispongono di Collider collegati. È stata aggiunta anche una nuova opzione per disabilitare la maschera del contenuto, semplificando la creazione di prototipi.

Per ulteriori informazioni, vedere [scorrimento della raccolta di oggetti](../features/README_ScrollingObjectCollection.md) .

![Scorrimento della raccolta di oggetti](https://user-images.githubusercontent.com/16922045/94465118-51537900-01b7-11eb-8f8b-bf864a8fee03.gif)

### <a name="teleport-pointer-animation-handling-and-sound-improvements"></a>Miglioramenti all'animazione, alla gestione e al suono del puntatore Teleport

Il puntatore Teleport ora ha migliorato le animazioni e il feedback audio. È stata anche migliorata la gestione del puntatore Teleport, in modo da gestire la smussatura quando si passa dal puntatore a una superficie vicina a una superficie più lontana.

[https://streamable.com/3f222q](https://streamable.com/3f222q)

### <a name="input-simulation-cheat-sheet"></a>Foglio informativo sulla simulazione di input

La scena HandInteractionExamples dispone ora di un collegamento configurabile per visualizzare una pagina della Guida per la simulazione di input

![Foglio informativo sulla simulazione di input](https://user-images.githubusercontent.com/13754172/93232433-dea8cd80-f7b4-11ea-8500-eaee202f606f.png)

### <a name="input-simulation-eye-gaze-with-mouse"></a>Occhio simulazione di input con il mouse

Gli utenti possono ora usare il mouse per simulare il rilevamento degli occhi. Vedere il `Eye Simulation Mode` campo nel profilo simulazione di input e impostarlo su mouse. Sostituisce il campo precedente `Simulate Eye Position`

![Mouse con sguardo occhi](https://user-images.githubusercontent.com/39840334/87720928-892b5280-c76a-11ea-9411-73ab69fc756c.gif)

### <a name="input-simulation-motion-controller-in-editor-play-mode"></a>Controller di movimento della simulazione di input in modalità di riproduzione dell'editor

Gli utenti possono ora simulare il controller di movimento esattamente come le mani in modalità di riproduzione dell'editor. I pulsanti trigger, Acquisisci e menu sono attualmente supportati.

### <a name="conical-grab-pointer"></a>Puntatore a pinza conica

È ora possibile configurare i puntatori di cattura per eseguire una query per gli oggetti vicini usando un cono dal punto di recupero anziché una sfera. Questo comportamento è molto simile a quello dell'interfaccia predefinita Hololens 2, che esegue una query per gli oggetti vicini usando un cono. Il DefaultHoloLens2InputSystemProfile è stato anche regolato per usare il nuovo `ConicalGrabPointer` .

![Puntatore a pinza conica](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

### <a name="testutilities-package"></a>Pacchetto TestUtilities

È ora disponibile un pacchetto (Microsoft. MixedReality. Toolkit. Unity. TestUtilities. 2.5.0. file unitypackage Tools) che contiene l'infrastruttura di test PlayMode e TestMode utilizzata dal MRTK per creare test end-to-end. Questa infrastruttura è stata molto utile per il team di MRTK e siamo entusiasti che i clienti lo usino per aggiungere il code coverage dei test ai propri progetti.

Il codice seguente illustra come creare una mano di test, visualizzarla in una determinata posizione, spostarla, quindi pizzicarla e aprirla.

```csharp
TestHand leftHand = new TestHand(Handedness.Left);
yield return leftHand.Show(new Vector3(-0.1f, -0.1f, 0.5f));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Pinch);
yield return leftHand.Move(new Vector3(0.2f, 0.2f, 0));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Open);
```

Per istruzioni su come scrivere un test usando questi TestUtilities, vedere la sezione relativa alla [scrittura](../Contributing/UnitTests.md#writing-tests) di test

Per esempi di test esistenti che usano questa infrastruttura, vedere MRTK ' s [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests)

### <a name="support-for-the-leap-motion-451-unity-modules"></a>Supporto per i moduli Leap Motion 4.5.1 Unity

È stato aggiunto il supporto per i moduli Leap Motion Unity versione 4.5.1 e il supporto per gli asset 4.4.0 è stato rimosso. Le versioni attualmente supportate dei moduli Leap Motion Unity sono 4.5.0 e 4.5.1.

Per ulteriori informazioni, vedere [How to configure the Leap Motion Hand Tracking in MRTK](../features/CrossPlatform/LeapMotionMRTK.md) per altre informazioni.

### <a name="spatial-awareness-mesh-observer-better-handles-customization-of-materials"></a>L'osservatore mesh di consapevolezza spaziale gestisce meglio la personalizzazione dei materiali

Con questa versione, i `Windows Mixed Reality Spatial Mesh Observer` componenti e `Generic XR SDK Spatial Mesh Observer` hanno migliorato la gestione dei materiali visivi. I materiali vengono ora conservati quando una mesh è stata aggiornata dall'Observer in cui, in precedenza, sono state reimpostate sul valore predefinito VisibleMaterial come configurato nel profilo.

Ciò consente agli sviluppatori di modificare il materiale mesh senza sovrascrivere le modifiche in modo imprevisto.

### <a name="linkxml-created-in-the-mixedrealitytoolkitgenerated-folder"></a>Link.xml creato nella cartella MixedRealityToolkit. generated

Con l'introduzione di MRTK Package Manager di Unity, MRTK scrive ora un `link.xml` file nella `Assets/MixedRealityToolkit.Generated` cartella, se non è presente alcun file. Si consiglia di aggiungere il file (e) da aggiungere `link.xml.meta` al controllo del codice sorgente. Link.xml viene usato per influenzare la funzionalità di [rimozione del codice gestito](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) del linker di Unity.

Altre informazioni sul file MRTK link.xml sono disponibili nell'articolo relativo alla [rimozione di MRTK e codice gestito](../out-of-scope/MRTK_and_managed_code_stripping.md) .

### <a name="unity-20193-mrtk-configuration-dialog-no-longer-attempts-to-enable-legacy-xr-support"></a>Unity 2019.3 +: MRTK Configuration Dialog non tenta più di abilitare il supporto legacy XR

Per evitare potenziali conflitti quando si usa la piattaforma XR di Unity, l'opzione per abilitare il supporto legacy XR è stata rimossa dalla finestra di dialogo di configurazione di MRTK. Se lo si desidera, è possibile abilitare il supporto legacy XR, in Unity 2019, usando **modifica**  >  **Impostazioni progetto**  >
 **lettore**  >  **XR impostazioni**  >  **realtà virtuale supportata**.

### <a name="reduction-in-initializeonload-overhead"></a>Riduzione del sovraccarico del InitializeOnLoad

Abbiamo lavorato per ridurre la quantità di lavoro eseguito nei gestori InitializeOnLoad, che dovrebbe causare miglioramenti nella velocità di sviluppo del ciclo interno. I gestori InitializeOnLoad vengono eseguiti ogni volta che viene compilato uno script, prima di entrare in modalità di riproduzione e anche all'avvio dell'editor. Questi gestori vengono ora eseguiti in un minor numero di casi, con conseguente miglioramento della velocità di risposta di Unity.

In alcuni casi si è verificato un compromesso da effettuare:

- Vedere [Leap Motion Tracking Configuration](../features/CrossPlatform/LeapMotionMRTK.md) per il passaggio di integrazione aggiuntivo.
- Per chi usa ARFoundation, è ora disponibile un ulteriore passaggio manuale nei passaggi introduttivi.
Per i nuovi passaggi, vedere [ARFoundation](../features/CrossPlatform/UsingARFoundation.md#install-required-packages) .
- Per coloro che useranno la [comunicazione remota olografica con la pipeline XR legacy](../features/Tools/HolographicRemoting.md#legacy-xr-setup-instructions) in HoloLens 2, è ora necessario eseguire un [passaggio manuale](../features/Tools/HolographicRemoting.md#dotnetwinrt_present-define-written-into-player-settings) .

### <a name="bounds-control-graduated"></a>Graduazione del controllo dei limiti

![Il controllo dei limiti del controllo dei limiti è stato superato da quello ](../features/Images/BoundsControl/MRTK_BoundsControl_Main.png)
 [](../features/README_BoundsControl.md) sperimentale e include una serie di nuove funzionalità e tonnellate di correzioni di bug.
Ecco un elenco delle novità di questo aggiornamento:

- le proprietà vengono suddivise in configurazioni che rendono più semplice la configurazione del controllo dei limiti
- le configurazioni possono essere condivise tramite oggetti con script
- ogni proprietà di proprietà/script è configurabile in fase di esecuzione
- il rig di controllo dei limiti non viene più ricreato nelle modifiche delle proprietà
- supporto degli handle di traduzione
- supporto completo dei vincoli tramite Gestione vincoli
- integrazione di sistemi elastici (sperimentale)

Il rettangolo di delimitazione precedente è ora deprecato ed è possibile aggiornare gli oggetti di gioco esistenti tramite il rettangolo di delimitazione [mediante lo strumento di migrazione](../features/Tools/MigrationWindow.md) o il [controllo riquadro](../features/README_BoundingBox.md#migrating-to-bounds-control).

### <a name="constraint-manager-component"></a>Componente Gestione vincoli

È ora possibile usare i vincoli sia dal controllo dei limiti che dal manipolatore di oggetti tramite il nuovo [componente di gestione dei vincoli](../features/README_ConstraintManager.md). Entrambi i componenti creeranno un gestore di vincoli per impostazione predefinita ed elaborerà automaticamente eventuali vincoli collegati.

Inoltre, la gestione dei vincoli di comportamento automatico viene fornita con una modalità manuale che consente agli utenti di decidere quale vincolo deve essere elaborato.
Per questo motivo il modo in cui vengono visualizzati i vincoli nel controllo proprietà è cambiato leggermente.

<img src="../features/Images/ConstraintManager/ManualSelection.png" width="600" alt="Manual selection">

I vincoli applicati al componente sono ora visualizzati come un elenco nel componente Gestione vincoli, mentre il componente che usa Gestione vincoli ( [controllo dei limiti](../features/README_BoundsControl.md#constraint-system) o [manipolatore di oggetti](../features/README_ObjectManipulator.md#constraint-manager)) visualizzerà ora la modalità e la gestione dei vincoli selezionati (auto o Manual).
Per altre informazioni, vedere la sezione [gestione dei vincoli](../features/README_ConstraintManager.md) nella documentazione.

### <a name="hololens-2-button-material-update"></a>Aggiornamento materiale del pulsante HoloLens 2

Aggiornamento del materiale della gabbia anteriore del pulsante HoloLens 2 per rimuovere il colore nero in MRC.

![Aggiornamento materiale del pulsante HoloLens 2](https://user-images.githubusercontent.com/13754172/94341269-dcf7c900-0042-11eb-9028-e55abd2ead67.png)

### <a name="description-panel-update-movable-example-scene"></a>Aggiornamento del pannello Descrizione, scena di esempio mobile

Pannello Descrizione aggiornato. (SceneDescriptionPanelRev. prefabbricate) la nuova progettazione offre una barra superiore afferrabile che consente all'utente di modificare o spostare l'intera scena.

![Aggiornamento pannello Descrizione](https://user-images.githubusercontent.com/13754172/91176366-28a21480-e71d-11ea-9e80-7e219595de9c.png)

### <a name="spatial-mesh-visualization---pulse-on-air-tap"></a>Visualizzazione Mesh spaziale-Pulse on aria

Esempio di Pulse shader aggiornato per la mesh spaziale per la corrispondenza del comportamento della shell di HoloLens 2.

![Pulse in aria](https://user-images.githubusercontent.com/13754172/90310153-d0536180-df29-11ea-939a-e9572d4f5670.gif)

### <a name="elastic-system---experimental"></a>Sistema elastico: sperimentale

![System2 elastico](../features/Images/Elastics/Elastics_Main.gif)

MRTK include ora un [sistema di simulazione elastica](../features/Elastics/ElasticSystem.md) che include una vasta gamma di sottoclassi estendibili e flessibili, che offrono binding per le molle a quaternione 4-dimensionali, le molle di volume tridimensionali e i sistemi Spring lineare semplici.

Attualmente i componenti MRTK seguenti che supportano [Elastics Manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) possono sfruttare le funzionalità di elasticità:

- [Controllo dei limiti](../features/README_BoundsControl.md#elastics-experimental)
- [Manipolatore di oggetti](../features/README_ObjectManipulator.md#elastics-experimental)  

<img src="https://user-images.githubusercontent.com/5544935/88151572-568cba00-cbaf-11ea-91c2-d6b51829b638.gif" width="38%" alt="Bounds control">
<img src="https://user-images.githubusercontent.com/5544935/88151578-58567d80-cbaf-11ea-8f96-d24f2cf0d6e9.gif" width="45.7%" alt="Boject manupulator">

### <a name="joystick-experimental"></a>Joystick (sperimentale)

Esempio di interfaccia del joystick che può controllare un oggetto di destinazione di grandi dimensioni.

![Joystick](https://user-images.githubusercontent.com/43013191/86156887-769ef100-babb-11ea-85be-ed6a6aed89d2.png)

### <a name="color-picker-experimental"></a>Selezione colori (sperimentale)

Controllo sperimentale che semplifica la modifica dei colori materiali per qualsiasi oggetto in fase di esecuzione.
![Selezione colori](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)

![Selezione colori](https://user-images.githubusercontent.com/43013191/85468994-fa0f8e00-b561-11ea-89f2-0810d1998518.png)

<br/><br/>

## <a name="breaking-changes"></a>Modifiche che causano un'interruzione

### <a name="assembly-definition-files-changes"></a>Modifiche ai file di definizione dell'assembly

Alcuni file asmdef vengono modificati e ora supportano solo Unity 2018.4.13 F1 o versioni successive. Gli errori di compilazione vengono visualizzati quando upating MRTK 2,5 nelle versioni precedenti di Unity. Per risolvere il problema, passare alla `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` finestra del progetto e rimuovere il riferimento mancante nel controllo. Ripetere questi passaggi con `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` e `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` . Nota è necessario annullare le modifiche sostituendo questi tre file asmdef con quelli originali, ovvero non modificati, durante l'aggiornamento a Unity 2019.

### <a name="imixedrealitypointermediator"></a>IMixedRealityPointerMediator

Questa interfaccia è stata aggiornata per avere una nuova funzione:

```csharp
void SetPointerPreferences(IPointerPreferences pointerPreferences);
```

Se si dispone di un Mediator del puntatore personalizzato che non esegue la sottoclasse DefaultPointerMediator, sarà necessario implementare questa nuova funzione. Per ulteriori informazioni sui motivi dell'aggiunta, vedere [questo problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) . Questo è stato aggiunto per garantire che le preferenze del puntatore vengano passate in modo esplicito al Mediator, invece di essere eseguite in modo implicito in base alla presenza di un costruttore che ha accettato un IPointerPreferences.

### <a name="rest--device-portal-api"></a>API portale Rest/dispositivo

La `UseSSL` proprietà statica è stata spostata da `Rest` a `DevicePortal` .

Se questa operazione è stata eseguita in precedenza...

```csharp
Rest.UseSSL = true
```

Esegui ora...

```csharp
DevicePortal.UseSSL = true
```

### <a name="linkxml"></a>Link.xml

Se un'applicazione utilizzava in precedenza la distribuzione NuGet di MRTK, il `link.xml` file è stato rimosso dal pacchetto di base. Per ripristinare le regole di conservazione del codice, aprendo il progetto in Unity una volta creerà un `link.xml` file predefinito in `Assets/MixedRealityToolkit.Generated` . È consigliabile aggiungere il file (e `link.xml.meta` ) al controllo del codice sorgente.

### <a name="transform-constraint-changes"></a>Modifiche ai vincoli di trasformazione

La proprietà TargetTransform è stata contrassegnata come obsoleta perché non è stata usata dal sistema di vincoli. La logica del vincolo è basata sulla trasformazione passata nei metodi Initialize e Apply. I vincoli utente derivati che si basano su questa proprietà possono memorizzare nella cache il TargetTransform nell'implementazione archiviando la trasformazione del componente vincolo per ottenere lo stesso comportamento.

Il tipo di dati iniziale archiviato del mondo `worldPoseOnManipulationStart` è stato modificato da MixedRealityPose a MixedRealityTransform, che include il valore della scala locale dell'oggetto modificato. Con questa modifica non è più necessario memorizzare nella cache separatamente i valori di scala iniziali.

### <a name="new-property-in-imixedrealitydictationsystem"></a>Nuova proprietà in IMixedRealityDictationSystem

`AudioClip`È stata aggiunta una nuova proprietà all'interfaccia IMixedRealityDictationSystem. La `AudioClip` proprietà consente l'accesso al clip audio associato alla sessione di dettatura corrente. Gli utenti devono implementare la proprietà nei rispettivi script che implementano l'interfaccia.

### <a name="service-facades-turn-down"></a>Le facciate del servizio si spengono

La [facciata dei servizi](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/06a06778e38da622b37cc299a93f16e143b7bdeb/Assets/MRTK/Core/Inspectors/MixedRealityToolkitFacadeHandler.cs) verrà disattivata in 2,5. Questa funzionalità è stata originariamente aggiunta per semplificare la configurazione dei profili MRTK (creando GameObject fasulli che rappresentavano ognuno dei servizi di MRTK). A lungo termine, vogliamo evitare la creazione di oggetti fittizi nel gioco e il tentativo di mantenerli sincronizzati (come la sincronizzazione dei dati e i problemi di origine di verità sono notoriamente difficili da scalare e ottenere a destra).

In 2,5, i gestori della facciata del servizio sono conservati per garantire che l'aggiornamento del progetto venga eseguito senza problemi. tutte le facciate presenti nel progetto verranno eliminate dal gestore della facciata del servizio per assicurarsi che le scene aperte in 2,5 vengano automaticamente corrette.

Il codice rimanente associato alla funzionalità di facciata del servizio verrà rimosso in una versione futura.

### <a name="addition-of-motion-controller-to-input-simulation-service"></a>Aggiunta del controller di movimento al servizio di simulazione di input

La simulazione del controller di movimento è ora disponibile nella modalità di riproduzione dell'editor lungo il lato della simulazione della mano esistente. Per abilitare questa modifica, molte funzioni/campi/proprietà correnti sono ora contrassegnate come obsolete e sono state `InputSimulationService.cs` `MixedRealityInputSimulationProfile.cs` apportate le modifiche più significative. La logica e il comportamento del codice pertinente rimangono in gran parte identici e la maggior parte delle funzioni obsolete e così via sono correlate alla sostituzione del riferimento a "Hand" con il termine più generico "controller", ad esempio da `DefaultHandSimulationMode` a `DefaultControllerSimulationMode` . Oltre a ottenere nuovi nomi, il tipo restituito di determinate nuove funzioni viene aggiornato in modo che corrisponda alla modifica del nome o del comportamento (ad esempio, `GetControllerDevice` in base all'origine `GetHandDevice` ora restituisce `BaseController` anziché `SimulatedHand` ).

`IInputSimulationService` dispone ora di nuove proprietà `MotionControllerDataLeft` e `MotionControllerDataRight` . `MixedRealityInputSimulationProfile` include ora nuovi campi per il mapping della tastiera di determinati pulsanti del controller di movimento.

## <a name="known-issues"></a>Problemi noti

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache può creare una nuova fotocamera alla chiusura

In alcune situazioni, ad esempio quando si usa il provider LeapMotion nell'editor di Unity, è possibile che CameraCache ricrei il MainCamera all'arresto. Per ulteriori informazioni, vedere [questo problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) .

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException quando vengono importati esempi tramite Gestione pacchetti Unity

A seconda della lunghezza del percorso del progetto, l'importazione di esempi tramite Gestione pacchetti Unity può generare messaggi FileNotFoundException nella console di Unity. La cui origine è il percorso del file "mancante" che supera MAX_PATH (256 caratteri). Per risolvere il progetto, abbreviare la lunghezza del percorso del progetto.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>Non è stato specificato alcun Spatializer. L'applicazione non supporterà il suono spaziale

Se non è configurato un Spatializer audio, viene visualizzato un avviso "nessun Spatializer specificato". Questo problema può verificarsi se non è installato alcun pacchetto XR, perché Unity include spatializers in questi pacakges.

Per risolverlo, verificare quanto segue:

- **Finestra**  >  di In **Gestione pacchetti** sono installati uno o più pacchetti XR
- Toolkit per realtà **mista**  >  **Utilità**  >  di **Configurare il progetto Unity** ed effettuare una selezione per **Spatializer audio**

  ![Seleziona Apatializer audio](../features/Images/ReleaseNotes/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException: riferimento all'oggetto non impostato su un'istanza di un oggetto (SceneTransitionService.Initialize)

In alcune situazioni, l'apertura `EyeTrackingDemo-00-RootScene` può causare un'eccezione NullReferenceException nel metodo Initialize della classe SceneTransitionService.
Questo errore è dovuto al fatto che il profilo di configurazione del servizio transizione della scena non è stato impostato. Per risolverlo, attenersi alla procedura seguente:

- Passare all' `MixedRealityToolkit` oggetto nella gerarchia
- Nella finestra di controllo selezionare `Extensions`
- Se non è espanso, espandere `Scene Transition Service`
- Impostare il valore di `Configuration Profile` su **MRTKExamplesHubSceneTransitionServiceProfile**

<img src="../features/Images/ReleaseNotes/FixSceneTransitionProfile.png" width="500px" alt="Fix scene transition">

### <a name="oculus-quest"></a>Oculus-ricerca

Attualmente esiste un problema noto per l'uso del [plug-in Oculus XR con quando si fa riferimento a piattaforme autonome](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).  Per gli aggiornamenti, vedere le note sulla versione, i forum e la registrazione di Oculus bug.

Il bug è identificato da questo set di 3 errori:

![Errore del plug-in Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI e TextMeshPro

Esiste un problema noto per le versioni più recenti di TextMeshPro (1.5.0 + o 2.1.1 +), in cui la dimensione del carattere predefinita per i menu a discesa e la spaziatura dei caratteri in grassetto è stata modificata.

![Immagine TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Per risolvere il problema, è possibile effettuare il downgrade a una versione precedente di TextMeshPro. Per ulteriori informazioni, vedere la pagina relativa al [problema #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) .
