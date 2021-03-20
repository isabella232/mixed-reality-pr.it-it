---
title: ReleaseNotes
description: Release abbiend della versione corrente di MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 300998965ac5e43282b6d18c0b9e71429a40cb50
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681604"
---
# <a name="microsoft-mixed-reality-toolkit-251-release-notes"></a>Note sulla versione di Microsoft Mixed Reality Toolkit 2.5.1

- [Novità](#whats-new)
- [Modifiche di rilievo](#breaking-changes)
- [Aggiornamento delle linee guida](../updates-deployment/Updating.md#upgrading-to-a-new-version-of-mrtk)
- [Problemi noti](#known-issues)

> [!IMPORTANT]
> Si è verificato un problema noto del compilatore che influisca sulle applicazioni compilate per Microsoft HoloLens 2 usando ARM64. Questo problema viene risolto nel prossimo aggiornamento 16,8 per Visual Studio 2019. Fino a quando l'aggiornamento non è disponibile, importare il `com.microsoft.mixedreality.toolkit.tools` pacchetto per applicare una soluzione alternativa.

## <a name="whats-new"></a>Novità

### <a name="package-dependency-errors-fixed"></a>Errori di dipendenza del pacchetto corretti

Questa versione corregge le dipendenze dei file tra pacchetti non corrette (ad esempio, i file nelle risorse standard non fanno più riferimento a file in base ai file di base). La versione 2.5.1 aggiunge anche una dipendenza esplicita da text mesh Pro.

### <a name="standard-assets-package-shaders-copied-to-assetsmrtkshaders"></a>Gli shader del pacchetto di asset standard sono stati copiati in asset/MRTK/shader

Quando il pacchetto di asset standard viene installato tramite UPM, gli shader verranno copiati nella cartella assets/MRTK/shaders in modo che non saranno più immutabili. Questo consente di risolvere il problema degli shader aggiornati per la pipeline di rendering universale (URP) ripristinando il comportamento legacy alla successiva caricamento del progetto.

### <a name="fixed-teleport-cursor-sticking-to-hands"></a>Correzione del cursore Teleport a mano

Questa versione corregge un [problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) per cui il cursore di destinazione Teleport può essere attaccato agli oggetti visivi.

## <a name="breaking-changes"></a>Modifiche che causano un'interruzione

Non sono state apportate modifiche di rilievo dalla versione 2.5.0.

## <a name="known-issues"></a>Problemi noti

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a>Alcune funzionalità dello shader standard del Toolkit di realtà mista richiedono il pacchetto di base

Quando viene importato tramite Gestione pacchetti Unity, gli script MRTK standard shader Utilities (ad esempio: HoverLight. cs) non sono collocati con lo shader nel pacchetto di asset standard. Per accedere a questa funzionalità, le applicazioni richiedono l'importazione del pacchetto di base.

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache può creare una nuova fotocamera alla chiusura

In alcune situazioni, ad esempio quando si usa il provider LeapMotion nell'editor di Unity, è possibile che CameraCache ricrei il MainCamera all'arresto. Per ulteriori informazioni, vedere [questo problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) .

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException quando vengono importati esempi tramite Gestione pacchetti Unity

A seconda della lunghezza del percorso del progetto, l'importazione di esempi tramite Gestione pacchetti Unity può generare messaggi FileNotFoundException nella console di Unity. La cui origine è il percorso del file "mancante" che supera MAX_PATH (256 caratteri). Per risolvere il progetto, abbreviare la lunghezza del percorso del progetto.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>Non è stato specificato alcun Spatializer. L'applicazione non supporterà il suono spaziale

Se non è configurato un Spatializer audio, viene visualizzato un avviso "nessun Spatializer specificato". Questo problema può verificarsi se non è installato alcun pacchetto XR, perché Unity include spatializers in questi pacakges.

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

<img src="../features/images/release-notes/FixSceneTransitionProfile.png" width="500px" alt="Fix Scene Transition Profile">

### <a name="oculus-quest"></a>Oculus-ricerca

Attualmente esiste un problema noto per l'uso del [plug-in Oculus XR con quando si fa riferimento a piattaforme autonome](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).  Per gli aggiornamenti, vedere le note sulla versione, i forum e la registrazione di Oculus bug.

Il bug è identificato da questo set di 3 errori:

![Errore del plug-in Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI e TextMeshPro

Esiste un problema noto per le versioni più recenti di TextMeshPro (1.5.0 + o 2.1.1 +), in cui la dimensione del carattere predefinita per i menu a discesa e la spaziatura dei caratteri in grassetto è stata modificata.

![Immagine TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Per risolvere il problema, è possibile effettuare il downgrade a una versione precedente di TextMeshPro. Per ulteriori informazioni, vedere la pagina relativa al [problema #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) .
