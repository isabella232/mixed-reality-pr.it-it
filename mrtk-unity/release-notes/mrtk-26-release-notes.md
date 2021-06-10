---
title: Note sulla versione di MRTK 2.6
description: Note sulla versione di MRTK versione 2.6
author: polar-kev
ms.author: kesemple
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 4ac82f7e07135e840886fef810844ff00ef1ac1e
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647188"
---
# <a name="microsoft-mixed-reality-toolkit-26-release-notes"></a>Note sulla versione di Microsoft Mixed Reality Toolkit 2.6

> [!IMPORTANT]
> Esiste un problema noto del compilatore che influisce sulle applicazioni compilate per Microsoft HoloLens 2 con ARM64. Questo problema viene risolto aggiornando Visual Studio 2019 alla versione 16.8 o successiva. Se non è possibile aggiornare Visual Studio, importare il `com.microsoft.mixedreality.toolkit.tools` pacchetto per applicare una soluzione alternativa.

## <a name="whats-new-in-262"></a>Novità nella versione 2.6.2

### <a name="corrects-parenting-of-the-spatial-mesh"></a>Corregge l'elemento padre della mesh spaziale

Corregge il problema [per cui](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) le mesh spaziali non venivano individuate correttamente dopo lo spostamento dell'oggetto Playspace di realtà mista (ad esempio tramite un teletrasporto).

## <a name="whats-new-in-261"></a>Novità nella versione 2.6.1

### <a name="fixes-openxr-not-running-on-hololens-2--uwp"></a>Correzioni di OpenXR non in esecuzione HoloLens 2/UWP

Corregge una regressione che impediva l'esecuzione del supporto OpenXR di MRTK nella UWP.

### <a name="fixes-leap-motion-objectmanipulator-not-rotating"></a>Corregge l'oggetto movimento intercalareManipulator non ruota

Corregge una regressione in cui la rotazione di una mano leap motion non è stata presa in considerazione dallo script ObjectManipulator.

### <a name="sample-scene-updates"></a>Aggiornamenti della scena di esempio

Aggiorna la scena di esempio di comprensione della scena per riflettere correttamente lo stato fornito del plug-in Unity. Aggiorna anche l'esempio in modo che non abbia più una dipendenza dalla scena di esempio di consapevolezza spaziale importata. Prima di eseguire l'aggiornamento alla versione 2.6.1, è necessario eliminare i campioni importati di comprensione della scena e di consapevolezza spaziale, se presenti nel progetto, per evitare possibili conflitti. Se questi esempi non sono stati rimosso e si verificano conflitti correlati a quelli nella console di , rimuovere entrambi gli esempi (o la cartella ) e quindi riprovare a `Assets/Samples/Mixed Reality Toolkit Examples` eseguire l'importazione.

Aggiorna la scena di esempio del dialogo per descrivere correttamente gli scenari di dialogo correnti.

## <a name="whats-new-in-260"></a>Novità nella versione 2.6.0
<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>

### <a name="add-support-for-openxr"></a>Aggiunta del supporto per OpenXR

È stato aggiunto il supporto iniziale per il pacchetto di anteprima OpenXR di Unity e il pacchetto OpenXR di Realtà mista di Microsoft. Per altre informazioni, vedi la pagina introduttiva di [MRTK/XRSDK,](../configuration/getting-started-with-mrtk-and-xrsdk.md)il post del forum di [Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)o la documentazione di [Microsoft.](/windows/mixed-reality/develop/unity/openxr-getting-started)

> [!IMPORTANT]
> OpenXR in Unity è supportato solo in Unity 2020.2 e versioni successive.
>
> Attualmente supporta solo le build x64 e ARM64.

### <a name="asset-swap-utility"></a>Utilità di scambio di asset

Scambiare più asset in una scena Unity con la nuova [utilità di scambio di asset](../features/tools/asset-swap-utility.md).

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a>HP Motion Controller è ora supportato con MRTK

I controller per HP Reverb G2 ora funzionano in modo nativo con MRTK.

### <a name="experimental-interactive-element--state-visualizer"></a>Elemento interattivo sperimentale + Visualizzatore di stato

Interactive Element è un punto di ingresso centralizzato semplificato al sistema di input MRTK. Contiene i metodi di gestione dello stato, la gestione degli eventi e la logica di impostazione dello stato per gli stati di interazione principali. Per altre informazioni, vedere [La documentazione degli elementi interattivi.](../features/experimental/interactive-element.md)

![InteractiveElementAddCoreState](../features/images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

Il visualizzatore di stato è un componente di animazione che dipende dall'elemento interattivo.  Questo componente crea clip di animazione, imposta fotogrammi chiave e genera una macchina a stati dell'animatore. Per altre informazioni, vedere [La documentazione del visualizzatore di stato](../features/experimental/interactive-element.md#state-visualizer-experimental)

![StateVisualizerColorChangeOnFocus](../features/images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a>Il teletrasporto con il movimento di teletrasporto è ora supportato in tutte le piattaforme

Gli utenti possono ora usare il movimento di teletrasporto per spostarsi all'interno dello spazio di riproduzione tra tutte le piattaforme. Per teletrasportare con un controller nei dispositivi MR con configurazioni predefinite, usare la levetta. Per teletrasportarti con le mani articolate, fai un movimento con il palmo rivolto verso l'alto con l'indice e il pollice che si fiocchi verso l'esterno, completando il teletrasporto arricciando il dito indice. Per teletrasportare con la simulazione di input, vedere la documentazione aggiornata del [servizio di simulazione input](../features/input-simulation/input-simulation-service.md).

  ![Movimento di teletrasporto](../features/images/teleport/handteleport.gif)

### <a name="scene-understanding-now-available-in-mrtk-as-an-experimental-spatial-awareness-observer"></a>Scene Understanding è ora disponibile in MRTK come osservatore di consapevolezza spaziale sperimentale

Il supporto [sperimentale di Scene Understanding](/windows/mixed-reality/scene-understanding) è stato introdotto in MRTK 2.6. Gli utenti possono incorporare le funzionalità di comprensione della scena HoloLens 2 come osservatore di consapevolezza spaziale nei progetti basati su MRTK. Per altre [informazioni, leggere la documentazione](../features/spatial-awareness/scene-understanding.md) di Scene Understanding.

> [!IMPORTANT]
> Scene Understanding è supportato solo in HoloLens 2 e Unity 2019.4 e versioni successive.
>
> Questa funzionalità richiede il pacchetto Scene Understanding, ora disponibile tramite lo strumento [di funzionalità di realtà mista](https://aka.ms/MRFeatureTool).
> Quando si usa lo strumento di funzionalità di realtà mista o si esegue un'importazione tramite UPM, importare l'esempio Demos - SpatialAwareness prima di importare l'esempio Experimental - SceneUnderstanding a causa di un problema di dipendenza. Per altre informazioni, vedere questo problema di [GitHub.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431)

  ![Informazioni sulla scena](images/SceneUnderstanding.gif)

### <a name="runtime-profile-switching-support"></a>Supporto della commutazione del profilo di runtime

MRTK consente ora il passaggio del profilo sia prima dell'inizializzazione dell'istanza di MRTK (ad esempio, il cambio del profilo di inizializzazione precedente a MRTK) che dopo che un profilo è stato in uso attivo (ad esempio, il cambio di profilo attivo). L'opzione precedente può essere usata per abilitare componenti selezionati in base alle funzionalità dell'hardware, mentre quest'ultimo può essere usato per modificare l'esperienza quando l'utente immette una sottoparte dell'applicazione. Per altre informazioni [ed esempi di codice,](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) vedere la documentazione sul cambio di profilo.

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a>Indicatore direzionale e risolutori follow che sono stati esistiti da sperimentali

Due nuovi risolutori sono pronti per l'uso con MRTK mainline.

  ![Risolutore indicatore direzionale](images/DirectionalIndicatorExampleScene.gif)

### <a name="hand-coach-graduated-from-experimental"></a>Hand Hand Emandato da sperimentale

La funzionalità Hand Hand è ora pronta per l'uso con MRTK principale.
  ![Esempio di Hand Hand Hand](/windows/mixed-reality/design/images/handcoach/airtap.gif)

### <a name="dialog-controls-graduated-from-experimental"></a>Controlli della finestra di dialogo non sperimentali

I controlli finestra di dialogo sono ora pronti per l'uso con MRTK principale.

  ![Controlli della finestra di dialogo](https://user-images.githubusercontent.com/13754172/101927792-3326e200-3c18-11eb-88d3-44b4b50c7f7d.png)

### <a name="pulse-shader-graduated-from-experimental"></a>Pulse shader in fase sperimentale

Gli script pulse shader sono stati sperimentali. Per altre informazioni, vedere: [Documentazione di Pulse Shader](../features/rendering/pulse-shader.md)

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

### <a name="input-recording-service-improvements"></a>Miglioramenti del servizio di registrazione di input

`InputRecordingService` e `InputPlaybackService` ora possono registrare e riprodurre l'input dello sguardo fisso. La registrazione è stata ottimizzata per garantire una frequenza dei fotogrammi coerente durante tutto il periodo di registrazione, mentre le dimensioni del file di registrazione e il tempo di salvataggio vengono ridotti di circa il 50%. Il salvataggio e il caricamento dei file di registrazione possono ora essere eseguiti in modo asincrono. Si noti che il formato di file della registrazione [](../features/input-simulation/input-animation-file-format.md) è cambiato in questa versione di MRTK. Per altre informazioni sulle nuove specifiche della versione 1.1, vedere qui.

### <a name="reading-mode"></a>Modalità di lettura

Aggiunta del supporto [per la modalità di](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) lettura HoloLens 2. La modalità di lettura riduce il campo di visualizzazione del sistema, ma elimina il ridimensionamento dell'output di Unity. Un pixel di cui Unity esegue il rendering corrisponderà a un pixel proiettato HoloLens 2. Gli autori di applicazioni devono eseguire test con più utenti per essere certi che si tratta di un compromesso desiderato nell'app.

  ![Windows Mixed Reality di lettura](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a>Supporto per le utilità di avvio delle app 3D nella UWP

Aggiunge la possibilità di impostare un'utilità [di avvio di app 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) per la UWP. Questa impostazione viene esposta sia nella finestra di compilazione di MRTK che nelle impostazioni del progetto MRTK, in Build Settings (Impostazioni di compilazione). Viene scritto automaticamente nel progetto durante la compilazione in Unity.

  ![Impostazioni di compilazione](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a>Modifiche che causano un'interruzione

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a>Alcuni campi degli oggetti GLTF importati sono ora in maiuscolo

A causa di problemi correlati alla deserializzazione, alcuni campi degli oggetti GLTF importati iniziano ora con lettere maiuscole. I campi interessati sono (nei nuovi nomi): `ComponentType` , , , , , , , , `Path` , `Interpolation` `Target` `Type` `Mode` `MagFilter` `MinFilter` `WrapS` `WrapT` .

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a>Il file binario dell'animazione di input ha un formato aggiornato alla versione 1.1

Il file binario dell'animazione di input, usato da e , ha ora un formato di file aggiornato per abilitare le `InputRecordingService` `InputPlaybackService` ottimizzazioni apportate a questi due servizi. Per altre [informazioni sulle](../features/input-simulation/input-animation-file-format.md) nuove specifiche della versione 1.1, vedere qui.

### <a name="msbuild-for-unity-support"></a>Supporto di MSBuild per Unity

Il supporto per MSBuild per Unity è stato rimosso dalla versione 2.5.2, per allinearsi alle nuove linee guida [per i pacchetti di Unity.](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)

## <a name="known-issues"></a>Problemi noti

### <a name="openxr"></a>OpenXR

Esiste attualmente un problema noto con Holographic Remoting e OpenXR, in cui i giunzioni delle mani non sono disponibili in modo coerente.
Inoltre, le scene di esempio di tracciamento oculare non sono attualmente compatibili, anche se il tracciamento *oculare funziona.*

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a>Alcune funzionalità shader standard di Mixed Reality Toolkit richiedono il pacchetto Foundation

Quando vengono importati tramite unity Gestione pacchetti, gli script delle utilità shader standard MRTK (ad esempio HoverLight.cs) non vengono collocati insieme allo shader nel pacchetto Asset standard. Per accedere a questa funzionalità, le applicazioni richiedono l'importazione del pacchetto Foundation.

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache può creare una nuova fotocamera all'arresto

In alcune situazioni,ad esempio quando si usa il provider LeapMotion nell'editor di Unity, è possibile che CameraCache crei nuovamente MainCamera all'arresto. Per altre [informazioni, vedere](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) questo problema.

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException quando gli esempi vengono importati tramite Unity Gestione pacchetti

A seconda della lunghezza del percorso del progetto, l'importazione di esempi tramite Unity Gestione pacchetti può generare messaggi FileNotFoundException nella console di Unity. La causa è che il percorso del file "mancante" è più lungo MAX_PATH (256 caratteri). Per risolvere il problema, abbreviare la lunghezza del percorso del progetto.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>Non è stato specificato alcun spazializzatore. L'applicazione non supporterà l'audio spaziale

Se non è configurato un spazializzatore audio, viene visualizzato l'avviso "Non è stato specificato alcun spazializzatore". Questo problema può verificarsi se non è installato alcun pacchetto XR, perché Unity include spazializzatori in questi pacchetti.

Per risolvere il problema, assicurarsi che:

- **Finestra**  >  **Gestione pacchetti** sono installati uno o più pacchetti XR
- **Mixed Reality Toolkit**  >  **Utilità**  >  **Configurare il progetto Unity** ed effettuare una selezione per **Spazializzatore audio**

  ![Selezionare Spazializzatore audio](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException: riferimento all'oggetto non impostato su un'istanza di un oggetto (SceneTransitionService.Initialize)

In alcune situazioni, `EyeTrackingDemo-00-RootScene` l'apertura può causare un'eccezione NullReferenceException nel metodo Initialize della classe SceneTransitionService.
Questo errore è dovuto all'annullamento dell'impostazione del profilo di configurazione del servizio di transizione della scena. Per risolvere il problema, seguire questa procedura:

- Passare `MixedRealityToolkit` all'oggetto nella gerarchia
- Nella finestra Inspector (Controllo) selezionare `Extensions`
- Se non viene espansa, espandere `Scene Transition Service`
- Impostare il valore di `Configuration Profile` su **MRTKExamplesHubSceneTransitionServiceProfile**

![Correggere il profilo di transizione della scena](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Oculus Quest

Esiste attualmente un problema noto per l'uso del plug-in [Oculus XR con quando](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)la destinazione è piattaforme autonome .  Per gli aggiornamenti, vedere lo strumento di rilevamento dei bug/forum/note sulla versione di Oculus.

Il bug è identificato con questo set di 3 errori:

![Errore del plug-in Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI e TextMeshPro

Esiste un problema noto per le versioni più recenti di TextMeshPro (1.5.0+ o 2.1.1+), in cui sono state modificate le dimensioni del carattere predefinite per gli elenchi a discesa e la spaziatura dei caratteri in grassetto.

![Immagine TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Per risolvere questo problema, eseguire il downgrade a una versione precedente di TextMeshPro. Per [altri dettagli, #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) problema.