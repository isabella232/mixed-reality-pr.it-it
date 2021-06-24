---
title: Note sulla versione di MRTK 2.5
description: Note sulla versione per MRTK versione 2.5
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 536a37b56b4c7de9875ce1e1642922bd363fecb1
ms.sourcegitcommit: f7839221c9549e60a2c3ac2dbd39f07a6851dcd2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2021
ms.locfileid: "112562491"
---
# <a name="microsoft-mixed-reality-toolkit-25-release-notes"></a>Note sulla versione di Microsoft Mixed Reality Toolkit 2.5

> [!IMPORTANT]
> Esiste un problema noto del compilatore che influisce sulle applicazioni compilate per Microsoft HoloLens 2 con ARM64. Questo problema viene risolto aggiornando Visual Studio 2019 alla versione 16.8 o successiva. Se non è possibile aggiornare Visual Studio, importare il `com.microsoft.mixedreality.toolkit.tools` pacchetto per applicare una soluzione alternativa.

## <a name="whats-new-in-254"></a>Novità nella versione 2.5.4

### <a name="fixes-a-bug-with-oculus-integration-when-using-upm"></a>Correzione di un bug con Oculus Integration quando si usa UPM

Quando si usa UPM, OculusXRSDKDeviceManagerProfile ha sempre i [prefab impostati su None all'avvio](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160)di . Questa versione configura Gestione dispositivi in modo che punti a una working set di prefab all'avvio.

### <a name="fixes-an-issue-with-openxr-via-upm"></a>Correzione di un problema con OpenXR tramite UPM

Correzione di un problema a causa del quale i provider OpenXR non sono stati aggiunti al link.xml per impostazione predefinita, causando l'esito negativo dell'esecuzione di nuovi progetti sul dispositivo quando si usano OpenXR e MRTK tramite il Gestione pacchetti di Unity. I progetti esistenti aggiornati dovranno comunque essere aggiunti manualmente.

## <a name="whats-new-in-253"></a>Novità nella versione 2.5.3

### <a name="fixes-a-regression-with-oculus-introduced-in-252"></a>Corregge una regressione con Oculus introdotto nella versione 2.5.2

Nella versione 2.5.2 è stato [introdotto un problema di compilazione durante l'integrazione di Oculus SDK.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083) Questa versione ripristina il problema.

## <a name="whats-new-in-252"></a>Novità nella versione 2.5.2

### <a name="add-support-for-openxr"></a>Aggiunta del supporto per OpenXR

È stato aggiunto il supporto iniziale per il pacchetto di anteprima OpenXR di Unity e il pacchetto OpenXR di Realtà mista di Microsoft. Per altre informazioni, vedi la pagina introduttiva di [MRTK/XRSDK,](../configuration/getting-started-with-mrtk-and-xrsdk.md)il post del forum di [Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)o la documentazione di [Microsoft.](/windows/mixed-reality/develop/unity/openxr-getting-started)

> [!IMPORTANT]
> OpenXR in Unity è supportato solo in Unity 2020.3 e versioni successive.
> Supporta anche solo build x64, ARM e ARM64.

### <a name="boundary-visualization-errors-fixed"></a>Correzione degli errori di visualizzazione dei limiti

Le visualizzazioni dei limiti, ad esempio il piano o le pareti, saranno ora configurate correttamente e visibili in fase di esecuzione in base al profilo limite.

### <a name="msbuild-for-unity-support"></a>Supporto di MSBuild per Unity

Il supporto per MSBuild per Unity è stato rimosso dalla versione 2.5.2, per allinearsi alle nuove linee guida [per i pacchetti di Unity.](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)

## <a name="whats-new-in-251"></a>Novità nella versione 2.5.1

### <a name="package-dependency-errors-fixed"></a>Correzione degli errori di dipendenza del pacchetto

Questa versione corregge le dipendenze non corrette tra i file tra pacchetti (ad esempio, i file negli asset standard non fanno più riferimento in modo errato ai file in Foundation). La versione 2.5.1 aggiunge anche una dipendenza esplicita da Text Mesh Pro.

### <a name="standard-assets-package-shaders-copied-to-assetsmrtkshaders"></a>Shader del pacchetto asset standard copiati in Assets/MRTK/Shaders

Quando il pacchetto Asset Standard viene installato tramite UPM, gli shader verranno copiati nella cartella Assets/MRTK/Shaders in modo che non siano più immutabili. In questo modo viene risolto il problema degli shader aggiornati per la pipeline di rendering universale (URP) che ripristinano il comportamento legacy al successivo caricamento del progetto.

### <a name="fixed-teleport-cursor-sticking-to-hands"></a>Correzione del cursore di teletrasporto che si fissa alle mani

Questa versione corregge un problema [a causa del](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) quale il cursore di destinazione del teletrasporto può rimanere a disposizione degli oggetti visivi.

## <a name="whats-new-in-250"></a>Novità nella versione 2.5.0

### <a name="unity-package-manager-upm-support"></a>Supporto di Unity Gestione pacchetti (UPM)

Mixed Reality Toolkit può ora essere gestito usando unity Gestione pacchetti.

![Pacchetto UPM MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> Per importare i pacchetti UPM di MRTK sono necessari alcuni passaggi manuali. Per altre [informazioni, vedere Mixed Reality Toolkit e Unity Gestione pacchetti](../configuration/usingupm.md) informazioni.

### <a name="oculus-quest-xr-sdk-support"></a>Supporto di Oculus Quest XR SDK

MRTK supporta ora l'esecuzione di visori VR e controller Oculus Quest usando la pipeline XR SDK nativa. Il tracciamento delle mani è supportato anche con il pacchetto [Oculus Integration Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) grazie al lavoro di [Eric Provencher](https://twitter.com/prvncher) su MRTK-Quest!

Per istruzioni su come distribuire il dispositivo in Oculus Quest usando la nuova pipeline, vedere la Guida alla configurazione [di Oculus Quest](../supported-devices/oculus-quest-mrtk.md)

### <a name="scrolling-object-collection"></a>Raccolta di oggetti scrolling

Il componente UX di MRTK è stato aggiornato da una funzionalità sperimentale e offre maggiore libertà per il layout di contenuto 3D di dimensioni diverse con supporto aggiunto per gli oggetti senza collisori collegati. È stata aggiunta anche una nuova opzione per disabilitare la maschera del contenuto, semplificando la creazione di prototipi.

Per [altre informazioni, vedere Scrolling Object Collection](../features/ux-building-blocks/scrolling-object-collection.md) .

![Raccolta di oggetti scrolling](https://user-images.githubusercontent.com/16922045/94465118-51537900-01b7-11eb-8f8b-bf864a8fee03.gif)

### <a name="teleport-pointer-animation-handling-and-sound-improvements"></a>Miglioramenti all'animazione, alla gestione e al suono del puntatore del teletrasporto

L'indicatore di misura del teletrasporto ora include animazioni e feedback audio migliorati. È stata anche migliorata la gestione dell'indicatore di misura del teletrasporto in modo che gestisca più agevolmente quando si passa dal puntamento su superfici vicine a superfici più vicine.

### <a name="input-simulation-cheat-sheet"></a>Foglio di controllo della simulazione di input

La scena HandInteractionExamples include ora un collegamento configurabile per visualizzare una pagina della Guida per la simulazione dell'input

![Foglio di controllo della simulazione dell'input](https://user-images.githubusercontent.com/13754172/93232433-dea8cd80-f7b4-11ea-8500-eaee202f606f.png)

### <a name="input-simulation-eye-gaze-with-mouse"></a>Sguardo fisso di simulazione input con il mouse

Gli utenti possono ora usare il mouse per simulare il tracciamento oculare. Visualizzare il `Eye Simulation Mode` campo nel profilo di simulazione di input e impostarlo su Mouse. Sostituisce il campo `Simulate Eye Position` precedente.

![Mouse sguardo fisso](https://user-images.githubusercontent.com/39840334/87720928-892b5280-c76a-11ea-9411-73ab69fc756c.gif)

### <a name="input-simulation-motion-controller-in-editor-play-mode"></a>Controller del movimento di simulazione input in modalità di riproduzione dell'editor

Gli utenti possono ora simulare il controller del movimento esattamente come le mani in modalità di riproduzione dell'editor. I pulsanti trigger, grab e menu sono attualmente supportati.

### <a name="conical-grab-pointer"></a>Puntatore di cattura conico

È ora possibile configurare i puntatori di cattura per eseguire query per gli oggetti vicini usando un cono dal punto di cattura anziché una sfera. Questo comportamento è più simile al comportamento dell'interfaccia di HoloLens 2 predefinita, che esegue una query per gli oggetti nelle vicinanze usando un cono. Anche DefaultHoloLens2InputSystemProfile è stato modificato per usare il nuovo `ConicalGrabPointer` oggetto .

![Puntatore di cattura conico](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

### <a name="testutilities-package"></a>Pacchetto TestUtilities

È ora disponibile un pacchetto (Microsoft.MixedReality.Toolkit.Unity.TestUtilities.2.5.0.unitypackage) che contiene l'infrastruttura di test PlayMode e TestMode che MRTK usa per creare test end-to-end. Questa infrastruttura è stata estremamente utile per il team di MRTK stesso e siamo molto contenti che i consumer lo usino per aggiungere la copertura dei test ai propri progetti.

Il codice seguente illustra come creare una mano di test, mostrarla in una determinata posizione, spostarla e quindi avvicinarla e aprirla.

```csharp
TestHand leftHand = new TestHand(Handedness.Left);
yield return leftHand.Show(new Vector3(-0.1f, -0.1f, 0.5f));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Pinch);
yield return leftHand.Move(new Vector3(0.2f, 0.2f, 0));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Open);
```

Per istruzioni su come scrivere un test usando queste testUtilities, vedere questa sezione sulla scrittura [di test.](../contributing/unit-tests.md#writing-tests)

Per esempi di test esistenti che usano questa infrastruttura, vedere [PlayModeTests di](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests)MRTK.

### <a name="support-for-the-leap-motion-451-unity-modules"></a>Supporto per i moduli Unity Leap Motion 4.5.1

È stato aggiunto il supporto per i moduli Leap Motion Unity versione 4.5.1 e il supporto per gli asset 4.4.0 è stato rimosso. Le versioni attualmente supportate dei moduli Leap Motion Unity sono 4.5.0 e 4.5.1.

È anche disponibile un passaggio aggiuntivo per l'integrazione iniziale di Leap Motion. Per altre informazioni, vedere How to Configure the Leap Motion Hand Tracking in MRTK (Come configurare il tracciamento delle mani del movimento leap [in MRTK).](../supported-devices/leap-motion-mrtk.md)

### <a name="spatial-awareness-mesh-observer-better-handles-customization-of-materials"></a>Spatial Awareness Mesh Observer gestisce meglio la personalizzazione dei materiali

Con questa versione, i `Windows Mixed Reality Spatial Mesh Observer` componenti e hanno migliorato la gestione dei materiali `Generic XR SDK Spatial Mesh Observer` visivi. I materiali vengono ora conservati quando una mesh è stata aggiornata dall'osservatore dove, in precedenza, sono stati reimpostati sul valore predefinito VisibleMaterial, come configurato nel profilo.

In questo modo gli sviluppatori possono modificare il materiale della mesh senza che le modifiche vengono sovrascritte in modo imprevisto.

### <a name="linkxml-created-in-the-mixedrealitytoolkitgenerated-folder"></a>Link.xml creato nella cartella MixedRealityToolkit.Generated

Con l'introduzione di Unity Package Manger MRTK, MRTK ora scrive un file nella cartella, se `link.xml` `Assets/MixedRealityToolkit.Generated` non è presente. È consigliabile aggiungere questo file (e `link.xml.meta` ) al controllo del codice sorgente. Link.xml viene usato per influenzare la [funzionalità di stripping del](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) codice gestito del linker Unity.

Altre informazioni sul file di link.xml MRTK sono disponibili nell'articolo [MRTK and managed code stripping (MrTK e stripping del codice](../updates-deployment/mrtk-and-managed-code-stripping.md) gestito).

### <a name="unity-20193-mrtk-configuration-dialog-no-longer-attempts-to-enable-legacy-xr-support"></a>Unity 2019.3+: la finestra di dialogo di configurazione di MRTK non tenta più di abilitare il supporto XR legacy

Per evitare potenziali conflitti quando si usa la piattaforma XR di Unity, l'opzione per abilitare il supporto XR legacy è stata rimossa dalla finestra di dialogo di configurazione di MRTK. Se si desidera, il supporto XR legacy può essere abilitato, in Unity 2019, usando **Edit**  >  **Project Settings**  >
 **Player**  >  **XR Settings** Virtual Reality  >  **Supported**.

### <a name="reduction-in-initializeonload-overhead"></a>Riduzione del sovraccarico di InitializeOnLoad

È stato eseguito un lavoro per ridurre la quantità di lavoro eseguita nei gestori InitializeOnLoad, con il rischio di migliorare la velocità di sviluppo del ciclo interno. I gestori InitializeOnLoad vengono eseguiti ogni volta che viene compilato uno script, prima di entrare in modalità di riproduzione e anche all'avvio dell'editor. Questi gestori vengono ora eseguiti in molti meno casi, con conseguente miglioramento generale della velocità di risposta di Unity.

In alcuni casi è stato necessario trovare un compromesso:

- Vedere [Leap Motion Hand Tracking Configuration per](../supported-devices/leap-motion-mrtk.md) il passaggio di integrazione aggiuntivo.
- Per gli utenti che usano ARFoundation, è ora disponibile un passaggio manuale aggiuntivo nei passaggi introduttivi.
  Per i nuovi passaggi, vedere [ARFoundation.](../supported-devices/using-ar-foundation.md#install-required-packages)
- Per gli utenti che usano [Holographic Remoting](../features/tools/holographic-remoting.md#legacy-xr-setup-instructions) con la pipeline XR legacy HoloLens 2, è ora disponibile un [passaggio](../features/tools/holographic-remoting.md#dotnetwinrt_present-define-written-into-player-settings) manuale da eseguire.

### <a name="bounds-control-graduated"></a>Controllo dei limiti 3D

![Controllo Limiti](../features/images/bounds-control/MRTK_BoundsControl_Main.png)

[Il controllo dei limiti](../features/ux-building-blocks/bounds-control.md) è stato gradualmente sperimentale e include una serie di nuove funzionalità e moltissime correzioni di bug.
Di seguito è riportato un elenco delle caratteristiche principali di questo aggiornamento:

- Le proprietà sono suddivise in configurazioni che semplificano la configurazione del controllo dei limiti
- Le configurazioni possono essere condivise tramite oggetti gestibili tramite script
- ogni proprietà/proprietà configurabile da script è configurabile in fase di esecuzione
- Il dispositivo di controllo bounds non viene più ricreato in base alle modifiche delle proprietà
- supporto degli handle di conversione
- supporto completo dei vincoli tramite Gestione vincoli
- Integrazione del sistema elastics (sperimentale)

Il vecchio rettangolo di selezione è ora deprecato e [](../features/tools/migration-window.md) gli oggetti gioco esistenti che usano il rettangolo di selezione possono essere aggiornati usando lo strumento di migrazione o il controllo [del rettangolo di selezione.](../features/ux-building-blocks/bounding-box.md#migrating-to-bounds-control)

### <a name="constraint-manager-component"></a>Componente Gestione vincoli

I vincoli possono ora essere usati sia dal controllo dei limiti che dal manipolatore di oggetti tramite il nuovo [componente di gestione vincoli](../features/ux-building-blocks/constraint-manager.md). Entrambi i componenti creeranno una gestione vincoli per impostazione predefinita ed eelaborare automaticamente tutti i vincoli collegati.

Inoltre, la gestione vincoli di comportamento automatico include anche una modalità manuale che consente agli utenti di decidere quale vincolo elaborare.
Per questo motivo, la modalità di visualizzazione dei vincoli nel controllo proprietà è cambiata leggermente.

<img src="../features/images/constraint-manager/ManualSelection.png" width="600" alt="Inspector view showing manual constraint manager selection">

I vincoli applicati al componente vengono ora visualizzati come elenco nel componente di gestione [](../features/ux-building-blocks/bounds-control.md#constraint-system) vincoli, mentre il componente che usa la gestione vincoli (controllo limiti o manipolatore di [oggetti)](../features/ux-building-blocks/object-manipulator.md#constraint-manager)visualizza ora la modalità e la gestione vincoli selezionate (automatica o manuale).
Per altre informazioni, vedere [la sezione Gestione](../features/ux-building-blocks/constraint-manager.md) vincoli nella documentazione.

### <a name="hololens-2-button-material-update"></a>HoloLens 2 del materiale del pulsante

Aggiornamento HoloLens 2 materiale della scatola anteriore del pulsante per rimuovere il colore nero in MRC.

![HoloLens 2 del materiale del pulsante](https://user-images.githubusercontent.com/13754172/94341269-dcf7c900-0042-11eb-9028-e55abd2ead67.png)

### <a name="description-panel-update-movable-example-scene"></a>Aggiornamento del pannello di descrizione, scena di esempio mobile

Pannello di descrizione aggiornato. (SceneDescriptionPanelRev.prefab) Il nuovo progetto offre una barra superiore afferrabile che consente all'utente di regolare/spostare l'intera scena.

![Aggiornamento del pannello di descrizione](https://user-images.githubusercontent.com/13754172/91176366-28a21480-e71d-11ea-9e80-7e219595de9c.png)

### <a name="spatial-mesh-visualization---pulse-on-air-tap"></a>Visualizzazione della mesh spaziale: pulsazione dell'aria

Aggiornamento dell'esempio di pulse shader per la mesh spaziale in modo HoloLens 2 comportamento della shell dell'utente.

![Pulse on air-tap](https://user-images.githubusercontent.com/13754172/90310153-d0536180-df29-11ea-939a-e9572d4f5670.gif)

### <a name="elastic-system-experimental"></a>Sistema elastico (sperimentale)

![Elastic System2](../features/images/elastics/Elastics_Main.gif)

MRTK include ora un sistema di simulazione [elastico](../features/elastics/elastic-system.md) che include un'ampia gamma di sottoclassi estendibili e flessibili, che offrono associazioni per quaternione 4-dimensionale, volume in 3 dimensioni e semplici sistemi a sorgente lineare.

Attualmente i componenti MRTK seguenti che supportano il gestore [elastici](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) possono sfruttare le funzionalità elastiche:

- [Controllo Limiti](../features/ux-building-blocks/bounds-control.md#elastics-experimental)
- [Manipolatore di oggetti](../features/ux-building-blocks/object-manipulator.md#elastics-experimental)

<img src="https://user-images.githubusercontent.com/5544935/88151572-568cba00-cbaf-11ea-91c2-d6b51829b638.gif" width="38%" alt="Expanding an elastic menu">
<img src="https://user-images.githubusercontent.com/5544935/88151578-58567d80-cbaf-11ea-8f96-d24f2cf0d6e9.gif" width="45.7%" alt="Grabbing an elastic coffee cup">

### <a name="joystick-experimental"></a>Azzarre (sperimentale)

Esempio di interfaccia a levetta in grado di controllare un oggetto di destinazione di grandi dimensioni.

![Joystick](https://user-images.githubusercontent.com/43013191/86156887-769ef100-babb-11ea-85be-ed6a6aed89d2.png)

### <a name="color-picker-experimental"></a>Selezione colori (sperimentale)

Controllo sperimentale che semplifica la modifica dei colori dei materiali in qualsiasi oggetto in fase di esecuzione.

![Tre diversi metodi di controllo selezione colori](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)

![Quattro diversi metodi di controllo di selezione colori](https://user-images.githubusercontent.com/43013191/85468994-fa0f8e00-b561-11ea-89f2-0810d1998518.png)

## <a name="breaking-changes"></a>Modifiche che causano un'interruzione

### <a name="assembly-definition-files-changes"></a>Modifiche ai file di definizione dell'assembly

Alcuni file asmdef sono stati modificati e ora supportano solo Unity 2018.4.13f1 o versione successiva. Gli errori di compilazione vengono visualizzati durante l'aggiornamento a MRTK 2.5 nelle versioni precedenti di Unity. Questo problema può essere risolto selezionando `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` nella finestra del progetto e rimuovendo il riferimento mancante nel controllo. Ripetere questi passaggi con `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` e `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` . Si noti che è necessario ripristinare le modifiche sostituendo i tre file asmdef con quelli originali (ovvero non modificati) durante l'aggiornamento a Unity 2019.

### <a name="imixedrealitypointermediator"></a>IMixedRealityPointerMediator

Questa interfaccia è stata aggiornata per avere una nuova funzione:

```csharp
void SetPointerPreferences(IPointerPreferences pointerPreferences);
```

Se si dispone di un mediatore puntatore personalizzato che non crea una sottoclasse di DefaultPointerMediator, è necessario implementare questa nuova funzione. Vedere [questo problema per](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) altre informazioni sul motivo per cui è stato aggiunto. Questa operazione è stata aggiunta per garantire che le preferenze del puntatore verrebbero passate in modo esplicito al mediatore, anziché essere eseguite in modo implicito in base alla presenza di un costruttore che accetta un oggetto IPointerPreferences.

### <a name="rest--device-portal-api"></a>API REST/Portale di dispositivi

La `UseSSL` proprietà statica è stata spostata da `Rest` a `DevicePortal` .

Se è stato fatto in precedenza...

```csharp
Rest.UseSSL = true
```

Eseguire questa operazione ora...

```csharp
DevicePortal.UseSSL = true
```

### <a name="linkxml"></a>Link.xml

Se un'applicazione usava in precedenza la distribuzione NuGet di MRTK, il `link.xml` file è stato rimosso dal pacchetto Foundation. Per ripristinare le regole di conservazione del codice, l'apertura del progetto in Unity una volta creerà un `link.xml` file predefinito in `Assets/MixedRealityToolkit.Generated` . È consigliabile aggiungere questo file (e `link.xml.meta` ) al controllo del codice sorgente.

### <a name="transform-constraint-changes"></a>Modifiche ai vincoli di trasformazione

La proprietà TargetTransform è stata contrassegnata come obsoleta perché non è stata usata dal sistema di vincoli. La logica dei vincoli è basata sulla trasformazione passata nei metodi Initialize e Apply. I vincoli utente derivati che si basano su questa proprietà possono memorizzare nella cache TargetTransform nella propria implementazione archiviando la trasformazione del componente vincolo per ottenere lo stesso comportamento.

Il tipo di dati della posizione globale iniziale archiviata è stato modificato da `worldPoseOnManipulationStart` MixedRealityPose a MixedRealityTransform, che include il valore di scala locale dell'oggetto modificato. Con questa modifica non è più necessario memorizzare nella cache separatamente i valori di scalabilità iniziali.

### <a name="new-property-in-imixedrealitydictationsystem"></a>Nuova proprietà in IMixedRealityDictationSystem

È stata aggiunta `AudioClip` una nuova proprietà all'interfaccia IMixedRealityDictationSystem. La `AudioClip` proprietà consente l'accesso al clip audio associato alla sessione di dettatura corrente. Gli utenti devono implementare la proprietà nei propri script che implementano l'interfaccia .

### <a name="service-facades-turn-down"></a>Le facciate dei servizi si disattivano

Le facciate dei servizi vengono disattivate nella versione 2.5. Questa funzionalità è stata originariamente aggiunta per semplificare la configurazione dei profili MRTK (creando gameobject fittizi nella scena che rappresentavano ognuno dei servizi di MRTK). A lungo termine, si vuole evitare di creare oggetti fittizi nel gioco e tentare di mantenerli sincronizzati (poiché i problemi di sincronizzazione dei dati e "origine di verità" sono di difficile scalabilità e risoluzione dei problemi).

Nella versione 2.5 i gestori dell'interfaccia del servizio vengono mantenuti in modo da garantire che l'aggiornamento del progetto sia corretto. Tutte le facciate presenti nel progetto verranno eliminate dal gestore dell'interfaccia del servizio per garantire che le scene aperte nella versione 2.5 siano automaticamente fisse.

Il codice rimanente associato alla funzionalità di facciata del servizio verrà rimosso in una versione futura.

### <a name="addition-of-motion-controller-to-input-simulation-service"></a>Aggiunta del controller del movimento al servizio di simulazione di input

La simulazione del controller del movimento è ora disponibile in modalità di riproduzione dell'editor insieme alla simulazione manuale esistente. Per abilitare questa modifica, molte funzioni/campi/proprietà correnti sono ora contrassegnate come obsolete, con `InputSimulationService.cs` e ottenendo le modifiche più `MixedRealityInputSimulationProfile.cs` significative. La logica e il comportamento del codice pertinente rimangono in gran parte invariati e la maggior parte delle funzioni obsolete e così via è correlata alla sostituzione del riferimento a "mano" al termine più generico "controller" (ad esempio da a `DefaultHandSimulationMode` `DefaultControllerSimulationMode` ). Oltre a ottenere nuovi nomi, il tipo restituito di alcune nuove funzioni viene aggiornato in modo che corrisponda alla modifica di nome/comportamento (ad esempio, in base all'originale ora restituisce `GetControllerDevice` `GetHandDevice` invece di `BaseController` `SimulatedHand` ).

`IInputSimulationService` dispone ora di nuove proprietà `MotionControllerDataLeft` e `MotionControllerDataRight` . `MixedRealityInputSimulationProfile` include ora nuovi campi per il mapping della tastiera di determinati pulsanti del controller del movimento.

## <a name="known-issues"></a>Problemi noti

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache può creare una nuova fotocamera all'arresto

In alcune situazioni,ad esempio quando si usa il provider LeapMotion nell'editor di Unity, è possibile che CameraCache crei nuovamente MainCamera all'arresto. Per altre [informazioni, vedere](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) questo problema.

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException quando gli esempi vengono importati tramite Unity Gestione pacchetti

A seconda della lunghezza del percorso del progetto, l'importazione di esempi tramite Unity Gestione pacchetti può generare messaggi FileNotFoundException nella console di Unity. La causa è che il percorso del file "mancante" è più lungo MAX_PATH (256 caratteri). Per risolvere il problema, abbreviare la lunghezza del percorso del progetto.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>Non è stato specificato alcun spazializzatore. L'applicazione non supporterà l'audio spaziale

Se non è configurato un spazializzatore audio, viene visualizzato un avviso che indica che non è stato specificato alcun spazializzatore. Ciò può verificarsi se non è installato alcun pacchetto XR, perché Unity include spazializzatori in questi pacchetti.

Per risolvere il problema, assicurarsi che:

- **Finestra**  >  **Gestione pacchetti** sono installati uno o più pacchetti XR
- **Mixed Reality Toolkit**  >  **Utilità**  >  **Configurare Unity Project** ed effettuare una selezione per **Audio Spatializer**

  ![Selezionare Spazializzatore audio](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException: riferimento all'oggetto non impostato su un'istanza di un oggetto (SceneTransitionService.Initialize)

In alcuni casi, `EyeTrackingDemo-00-RootScene` l'apertura può causare un'eccezione NullReferenceException nel metodo Initialize della classe SceneTransitionService.
Questo errore è dovuto all'annullamento dell'impostazione del profilo di configurazione del servizio di transizione scena. Per risolvere il problema, seguire questa procedura:

- Passare `MixedRealityToolkit` all'oggetto nella gerarchia
- Nella finestra Inspector (Controllo) selezionare `Extensions`
- Se non è espansa, espandere `Scene Transition Service`
- Impostare il valore di `Configuration Profile` su **MRTKExamplesHubSceneTransitionServiceProfile**

![Correzione della transizione della scena](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Oculus Quest

Esiste attualmente un problema noto per l'uso del [plug-in Oculus XR con quando si usano le piattaforme autonome.](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/) Per gli aggiornamenti, vedere oculus bug tracker/forums/release notes (Rilevamento bug Oculus/forums/note sulla versione).

Il bug è indicato con questo set di 3 errori:

![Errore del plug-in Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI e TextMeshPro

Esiste un problema noto per le versioni più recenti di TextMeshPro (1.5.0+ o 2.1.1+), in cui è stata modificata la dimensione del carattere predefinita per gli elenchi a discesa e la spaziatura dei caratteri in grassetto.

![Immagine TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Per risolvere questo problema, eseguire il downgrade a una versione precedente di TextMeshPro. Per [altri dettagli, vedere #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) problema.
