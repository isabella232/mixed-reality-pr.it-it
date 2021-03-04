---
title: ReleaseNotes
description: Release abbiend della versione corrente di MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 8cf6617a408c35be8a6fe042a9d557849be45785
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781569"
---
# <a name="microsoft-mixed-reality-toolkit-254-release-notes"></a>Note sulla versione di Microsoft Mixed Reality Toolkit 2.5.4

- [Novità](#whats-new)
- [Aggiornamento delle linee guida](../updates-deployment/updating.md#upgrading-to-a-new-version-of-mrtk)
- [Problemi noti](#known-issues)

> [!IMPORTANT]
> Si è verificato un problema noto del compilatore che influisca sulle applicazioni compilate per Microsoft HoloLens 2 usando ARM64. Questo problema viene risolto aggiornando Visual Studio 2019 alla versione 16,8 o successiva. Se non è possibile aggiornare Visual Studio, importare il `com.microsoft.mixedreality.toolkit.tools` pacchetto per applicare una soluzione alternativa.

## <a name="whats-new"></a>Novità

### <a name="fixes-a-bug-with-oculus-integration-when-using-upm"></a>Corregge un bug con l'integrazione di Oculus quando si usa UPM

Quando si usa il sistema di gestione delle dipendenze, il OculusXRSDKDeviceManagerProfile deve avere sempre i [prefabbricati impostati su None all'avvio](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160). Questa versione configura il Gestione dispositivi in modo che punti a una working set di prefabbricati all'avvio.

### <a name="fixes-an-issue-with-openxr-via-upm"></a>Corregge un problema con OpenXR tramite UPM

Corregge un problema per cui i provider OpenXR non sono stati aggiunti al link.xml per impostazione predefinita, causando l'esito negativo dell'esecuzione di nuovi progetti sul dispositivo quando si usano OpenXR e MRTK tramite Gestione pacchetti di Unity. I progetti esistenti aggiornati dovranno ancora essere aggiunti manualmente.

## <a name="what-was-new-in-253"></a>Novità di 2.5.3

### <a name="fixes-a-regression-with-oculus-introduced-in-252"></a>Corregge una regressione con Oculus introdotta in 2.5.2

in 2.5.2 è stato introdotto [un problema di compilazione durante l'integrazione di Oculus SDK](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083). Questa versione ripristina il problema.

### <a name="add-support-for-openxr"></a>Aggiungere il supporto per OpenXR

È stato aggiunto il supporto iniziale per il pacchetto di anteprima OpenXR di Unity e il pacchetto OpenXR per la realtà mista Microsoft. Per altre informazioni, vedere la pagina introduttiva di [MRTK/XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md), [post del forum di Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)o [documentazione di Microsoft](https://aka.ms/openxr-unity-install) .

> [!IMPORTANT]
> OpenXR in Unity è supportato solo in Unity 2020,2 e versioni successive.
>
> Attualmente, supporta anche solo le compilazioni x64 e ARM64.

### <a name="boundary-visualization-errors-fixed"></a>Errori di visualizzazione limite corretti

Le visualizzazioni dei limiti, come il piano o i muri, ora verranno configurate correttamente e visibili in fase di esecuzione in base al profilo limite.

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

  ![Seleziona Apatializer audio](../features/images/release-notes/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException: riferimento all'oggetto non impostato su un'istanza di un oggetto (SceneTransitionService.Initialize)

In alcune situazioni, l'apertura `EyeTrackingDemo-00-RootScene` può causare un'eccezione NullReferenceException nel metodo Initialize della classe SceneTransitionService.
Questo errore è dovuto al fatto che il profilo di configurazione del servizio transizione della scena non è stato impostato. Per risolverlo, attenersi alla procedura seguente:

- Passare all' `MixedRealityToolkit` oggetto nella gerarchia
- Nella finestra di controllo selezionare `Extensions`
- Se non è espanso, espandere `Scene Transition Service`
- Impostare il valore di `Configuration Profile` su **MRTKExamplesHubSceneTransitionServiceProfile**

<img src="../features/images/release-notes/FixSceneTransitionProfile.png" width="500px" alt="Fix Scene Transition">

### <a name="oculus-quest"></a>Oculus-ricerca

Attualmente esiste un problema noto per l'uso del [plug-in Oculus XR con quando si fa riferimento a piattaforme autonome](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).  Per gli aggiornamenti, vedere le note sulla versione, i forum e la registrazione di Oculus bug.

Il bug è identificato da questo set di 3 errori:

![Errore del plug-in Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI e TextMeshPro

Esiste un problema noto per le versioni più recenti di TextMeshPro (1.5.0 + o 2.1.1 +), in cui la dimensione del carattere predefinita per i menu a discesa e la spaziatura dei caratteri in grassetto è stata modificata.

![Immagine TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Per risolvere il problema, è possibile effettuare il downgrade a una versione precedente di TextMeshPro. Per ulteriori informazioni, vedere la pagina relativa al [problema #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) .
