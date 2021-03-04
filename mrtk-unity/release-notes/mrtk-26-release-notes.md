---
title: ReleaseNotes
description: Note sulla versione di MRTK versione 2,6
author: polar-kev
ms.author: kesemple
ms.date: 02/28/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: a232543da9b53969cb38c52a9cbd04a84e131561
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782885"
---
# <a name="microsoft-mixed-reality-toolkit-260-release-notes"></a>Note sulla versione di Microsoft Mixed Reality Toolkit 2.6.0

- [Novità](#whats-new)
- [Modifiche di rilievo](#breaking-changes)
- [Aggiornamento delle linee guida](Updating.md#upgrading-to-a-new-version-of-mrtk)
- [Problemi noti](#known-issues)

> [!IMPORTANT]
> Si è verificato un problema noto del compilatore che influisca sulle applicazioni compilate per Microsoft HoloLens 2 usando ARM64. Questo problema viene risolto aggiornando Visual Studio 2019 alla versione 16,8 o successiva. Se non è possibile aggiornare Visual Studio, importare il `com.microsoft.mixedreality.toolkit.tools` pacchetto per applicare una soluzione alternativa.

## <a name="whats-new"></a>Novità

### <a name="add-support-for-openxr"></a>Aggiungere il supporto per OpenXR

È stato aggiunto il supporto iniziale per il pacchetto di anteprima OpenXR di Unity e il pacchetto OpenXR per la realtà mista Microsoft. Per altre informazioni, vedere la pagina introduttiva di [MRTK/XRSDK](configuration/getting-started-with-mrtk-and-xrsdk.md), [post del forum di Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)o [documentazione di Microsoft](https://aka.ms/openxr-unity-install) .

> [!IMPORTANT]
> OpenXR in Unity è supportato solo in Unity 2020,2 e versioni successive.
>
> Attualmente, supporta anche solo le compilazioni x64 e ARM64.

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a>I controller di movimento HP sono ora supportati con MRTK

I controller per i Riverb di HP G2 ora funzionano in modo nativo con MRTK.

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a>Teleporting con il gesto Teleport ora supportato in tutte le piattaforme

Gli utenti possono ora usare il gesto Teleport per spostarsi sullo spazio di riproduzione in tutte le piattaforme. Per teletrasportarsi con un controller nei dispositivi MR con configurazioni predefinite, usare levetta. Per teletrasportarsi con le mani articolate, creare un gesto con la Palma rivolto verso l'alto con l'indice e il pollice verso l'alto, completando il teletrasporto arricciando il dito dell'indice. Per teletrasportarsi con la simulazione di input, vedere la documentazione aggiornata del [servizio di simulazione di input](features/input-simulation/input-simulation-service.md).

  ![Movimento Teleport](images/handteleport.gif)

### <a name="runtime-profile-switching-support"></a>Supporto del cambio del profilo di runtime

MRTK consente ora il cambio del profilo prima dell'inizializzazione dell'istanza di MRTK (ad esempio, l'opzione del profilo di inizializzazione pre-MRTK) e dopo che un profilo è stato usato in modo attivo (ad esempio, commutatore profilo attivo). Il cambio precedente può essere usato per abilitare i componenti selezionati in base alle funzionalità dell'hardware, mentre quest'ultimo può essere usato per modificare l'esperienza quando l'utente immette un sottoparte dell'applicazione. Per ulteriori informazioni ed esempi di codice, leggere la [documentazione relativa al cambio del profilo](configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) .

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a>Indicatore direzionale e i risolutori seguono laureati da sperimentale

Due nuovi risolutori sono pronti per l'uso con MRTK principali.

  ![Risolutore indicatori direzionali](images/DirectionalIndicatorExampleScene.gif)

### <a name="input-recording-service-improvements"></a>Miglioramenti del servizio registrazione input

`InputRecordingService` e `InputPlaybackService` ora possono registrare e riprodurre l'input dello sguardo. La registrazione è stata ottimizzata in modo da garantire un framerate coerente per tutto il periodo di registrazione durante la registrazione delle dimensioni del file e il tempo di risparmio viene ridotto del 50% circa. Il salvataggio e il caricamento dei file di registrazione possono ora essere eseguiti in modo asincrono. Si noti che il formato di file della registrazione è stato modificato in questa versione di MRTK. per ulteriori informazioni sulle nuove specifiche della versione 1,1, vedere [qui](InputSimulation/InputAnimationFileFormat.md) .

### <a name="reading-mode"></a>Modalità di lettura

Aggiunta del supporto per la [modalità di lettura](https://docs.microsoft.com/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) su HoloLens 2. La modalità di lettura riduce il campo di visualizzazione del sistema, ma elimina la scalabilità dell'output di Unity. Un pixel sottoposto a rendering da Unity corrisponderà a un pixel proiettato in HoloLens 2. Gli autori di applicazioni devono eseguire test con più utenti per assicurarsi che questo sia un compromesso che desiderano nell'app.

  ![Modalità di lettura della realtà mista di Windows](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a>Supporto per i lanci di app 3D in UWP

Aggiunge la possibilità di impostare un [utilità di avvio delle app 3D](https://docs.microsoft.com/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) per UWP. Questa impostazione viene esposta sia nella finestra di compilazione MRTK che nelle impostazioni del progetto MRTK, in impostazioni di compilazione. Viene scritto automaticamente nel progetto durante la compilazione in Unity.

  ![Impostazioni di compilazione](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a>Modifiche che causano un'interruzione

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a>Alcuni campi degli oggetti GLTF importati sono ora in maiuscolo

A causa di problemi correlati alla deserializzazione, alcuni campi degli oggetti GLTF importati ora iniziano con lettere maiuscole. I campi interessati sono (nei nuovi nomi): `ComponentType` , `Path` , `Interpolation` , `Target` , `Type` , `Mode` , `MagFilter` , `MinFilter` , `WrapS` , `WrapT` .

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a>Il file binario animazione input ha un formato versione 1,1 aggiornato

Il file binario di animazione di input, usato da `InputRecordingService` e `InputPlaybackService` , dispone ora di un formato di file aggiornato per abilitare le ottimizzazioni apportate a questi due servizi. Per ulteriori informazioni sulle nuove specifiche della versione 1,1, vedere [qui](features/input-simulation/input-animation-file-format.md) .

### <a name="msbuild-for-unity-support"></a>Supporto di MSBuild per Unity

Il supporto per MSBuild per Unity è stato rimosso al rilascio di 2.5.2, per essere allineato con le [nuove linee guida per i pacchetti di Unity](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).

## <a name="known-issues"></a>Problemi noti

### <a name="openxr"></a>OpenXR

Attualmente esiste un problema noto con la comunicazione remota olografica e OpenXR, in cui le giunzioni a mano non sono costantemente disponibili.
Inoltre, le scene di esempio per la verifica degli occhi non sono attualmente compatibili, ma *il rilevamento degli occhi funziona.*

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a>Alcune funzionalità dello shader standard del Toolkit di realtà mista richiedono il pacchetto di base

Quando viene importato tramite Gestione pacchetti Unity, gli script MRTK standard shader Utilities (ad esempio: HoverLight.cs) non sono condivisi con lo shader nel pacchetto di asset standard. Per accedere a questa funzionalità, le applicazioni richiedono l'importazione del pacchetto di base.

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache può creare una nuova fotocamera alla chiusura

In alcune situazioni, ad esempio quando si usa il provider LeapMotion nell'editor di Unity, è possibile che CameraCache ricrei il MainCamera all'arresto. Per ulteriori informazioni, vedere [questo problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) .

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException quando vengono importati esempi tramite Gestione pacchetti Unity

A seconda della lunghezza del percorso del progetto, l'importazione di esempi tramite Gestione pacchetti Unity può generare messaggi FileNotFoundException nella console di Unity. La cui origine è il percorso del file "mancante" che supera MAX_PATH (256 caratteri). Per risolvere il progetto, abbreviare la lunghezza del percorso del progetto.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>Non è stato specificato alcun Spatializer. L'applicazione non supporterà il suono spaziale

Se non è configurato un Spatializer audio, viene visualizzato un avviso "nessun Spatializer specificato". Questo problema può verificarsi se non è installato alcun pacchetto XR, perché Unity include spatializers in questi pacchetti.

Per risolverlo, verificare quanto segue:

- **Finestra**  >  di In **Gestione pacchetti** sono installati uno o più pacchetti XR
- Toolkit per realtà **mista**  >  **Utilità**  >  di **Configurare il progetto Unity** ed effettuare una selezione per **Spatializer audio**

  ![Seleziona Spatializer audio](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException: riferimento all'oggetto non impostato su un'istanza di un oggetto (SceneTransitionService.Initialize)

In alcune situazioni, l'apertura `EyeTrackingDemo-00-RootScene` può causare un'eccezione NullReferenceException nel metodo Initialize della classe SceneTransitionService.
Questo errore è dovuto al fatto che il profilo di configurazione del servizio transizione della scena non è stato impostato. Per risolverlo, attenersi alla procedura seguente:

- Passare all' `MixedRealityToolkit` oggetto nella gerarchia
- Nella finestra di controllo selezionare `Extensions`
- Se non è espanso, espandere `Scene Transition Service`
- Impostare il valore di `Configuration Profile` su **MRTKExamplesHubSceneTransitionServiceProfile**

<img src="Images/ReleaseNotes/FixSceneTransitionProfile.png" width="500px">

### <a name="oculus-quest"></a>Oculus-ricerca

Attualmente esiste un problema noto per l'uso del [plug-in Oculus XR con quando si fa riferimento a piattaforme autonome](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).  Per gli aggiornamenti, vedere le note sulla versione, i forum e la registrazione di Oculus bug.

Il bug è identificato da questo set di 3 errori:

![Errore del plug-in Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI e TextMeshPro

Esiste un problema noto per le versioni più recenti di TextMeshPro (1.5.0 + o 2.1.1 +), in cui la dimensione del carattere predefinita per i menu a discesa e la spaziatura dei caratteri in grassetto è stata modificata.

![Immagine TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Per risolvere il problema, è possibile effettuare il downgrade a una versione precedente di TextMeshPro. Per ulteriori informazioni, vedere la pagina relativa al [problema #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) .
