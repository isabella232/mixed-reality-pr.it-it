---
title: ReleaseNotes
description: Release abbiend della versione corrente di MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 3ed8097a6c6ea0325d772ee7c457f10e3c4f2c0b
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104686564"
---
# <a name="microsoft-mixed-reality-toolkit-251-release-notes"></a><span data-ttu-id="b0386-104">Note sulla versione di Microsoft Mixed Reality Toolkit 2.5.1</span><span class="sxs-lookup"><span data-stu-id="b0386-104">Microsoft Mixed Reality Toolkit 2.5.1 release notes</span></span>

- [<span data-ttu-id="b0386-105">Novità</span><span class="sxs-lookup"><span data-stu-id="b0386-105">What's new</span></span>](#whats-new)
- [<span data-ttu-id="b0386-106">Modifiche di rilievo</span><span class="sxs-lookup"><span data-stu-id="b0386-106">Breaking changes</span></span>](#breaking-changes)
- [<span data-ttu-id="b0386-107">Aggiornamento delle linee guida</span><span class="sxs-lookup"><span data-stu-id="b0386-107">Updating guidance</span></span>](../updates-deployment/Updating.md#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="b0386-108">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="b0386-108">Known issues</span></span>](#known-issues)

> [!IMPORTANT]
> <span data-ttu-id="b0386-109">Si è verificato un problema noto del compilatore che influisca sulle applicazioni compilate per Microsoft HoloLens 2 usando ARM64.</span><span class="sxs-lookup"><span data-stu-id="b0386-109">There is a known compiler issue that impacts applications built for Microsoft HoloLens 2 using ARM64.</span></span> <span data-ttu-id="b0386-110">Questo problema viene risolto aggiornando Visual Studio 2019 alla versione 16,8 o successiva.</span><span class="sxs-lookup"><span data-stu-id="b0386-110">This issue is fixed by updating Visual Studio 2019 to version 16.8 or later.</span></span> <span data-ttu-id="b0386-111">Se non è possibile aggiornare Visual Studio, importare il `com.microsoft.mixedreality.toolkit.tools` pacchetto per applicare una soluzione alternativa.</span><span class="sxs-lookup"><span data-stu-id="b0386-111">If you are unable to update Visual Studio, please import the `com.microsoft.mixedreality.toolkit.tools` package to apply a workaround.</span></span>

## <a name="whats-new"></a><span data-ttu-id="b0386-112">Novità</span><span class="sxs-lookup"><span data-stu-id="b0386-112">What's new</span></span>

### <a name="package-dependency-errors-fixed"></a><span data-ttu-id="b0386-113">Errori di dipendenza del pacchetto corretti</span><span class="sxs-lookup"><span data-stu-id="b0386-113">Package dependency errors fixed</span></span>

<span data-ttu-id="b0386-114">Questa versione corregge le dipendenze dei file tra pacchetti non corrette (ad esempio, i file nelle risorse standard non fanno più riferimento a file in base ai file di base).</span><span class="sxs-lookup"><span data-stu-id="b0386-114">This release fixes incorrect inter-package file dependencies (ex: files in Standard Assets no longer incorrectly reference files in Foundation).</span></span> <span data-ttu-id="b0386-115">La versione 2.5.1 aggiunge anche una dipendenza esplicita da text mesh Pro.</span><span class="sxs-lookup"><span data-stu-id="b0386-115">Version 2.5.1 also adds an explicit dependency on Text Mesh Pro.</span></span>

### <a name="standard-assets-package-shaders-copied-to-assetsmrtkshaders"></a><span data-ttu-id="b0386-116">Gli shader del pacchetto di asset standard sono stati copiati in asset/MRTK/shader</span><span class="sxs-lookup"><span data-stu-id="b0386-116">Standard Assets package shaders copied to Assets/MRTK/Shaders</span></span>

<span data-ttu-id="b0386-117">Quando il pacchetto di asset standard viene installato tramite UPM, gli shader verranno copiati nella cartella assets/MRTK/shaders in modo che non saranno più immutabili.</span><span class="sxs-lookup"><span data-stu-id="b0386-117">When the Standard Assets package is installed via UPM, the shaders will be copied to the Assets/MRTK/Shaders folder so that they will no longer be immutable.</span></span> <span data-ttu-id="b0386-118">Questo consente di risolvere il problema degli shader aggiornati per la pipeline di rendering universale (URP) ripristinando il comportamento legacy alla successiva caricamento del progetto.</span><span class="sxs-lookup"><span data-stu-id="b0386-118">This resolves the issue of shaders updated for the Universal Render Pipeline (URP) reverting the legacy behavior the next time the project is loaded.</span></span>

### <a name="fixed-teleport-cursor-sticking-to-hands"></a><span data-ttu-id="b0386-119">Correzione del cursore Teleport a mano</span><span class="sxs-lookup"><span data-stu-id="b0386-119">Fixed teleport cursor sticking to hands</span></span>

<span data-ttu-id="b0386-120">Questa versione corregge un [problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) per cui il cursore di destinazione Teleport può essere attaccato agli oggetti visivi.</span><span class="sxs-lookup"><span data-stu-id="b0386-120">This release fixes an [issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) where the teleport destination cursor can stick to hand visuals.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="b0386-121">Modifiche che causano un'interruzione</span><span class="sxs-lookup"><span data-stu-id="b0386-121">Breaking changes</span></span>

<span data-ttu-id="b0386-122">Non sono state apportate modifiche di rilievo dalla versione 2.5.0.</span><span class="sxs-lookup"><span data-stu-id="b0386-122">There are no breaking changes since version 2.5.0.</span></span>

## <a name="known-issues"></a><span data-ttu-id="b0386-123">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="b0386-123">Known issues</span></span>

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a><span data-ttu-id="b0386-124">Alcune funzionalità dello shader standard del Toolkit di realtà mista richiedono il pacchetto di base</span><span class="sxs-lookup"><span data-stu-id="b0386-124">Some Mixed Reality Toolkit Standard Shader features require the Foundation package</span></span>

<span data-ttu-id="b0386-125">Quando viene importato tramite Gestione pacchetti Unity, gli script MRTK standard shader Utilities (ad esempio: HoverLight. cs) non sono collocati con lo shader nel pacchetto di asset standard.</span><span class="sxs-lookup"><span data-stu-id="b0386-125">When imported via the Unity Package Manager, the MRTK Standard Shader utilities scripts (ex: HoverLight.cs) are not co-located with the shader in the Standard Assets package.</span></span> <span data-ttu-id="b0386-126">Per accedere a questa funzionalità, le applicazioni richiedono l'importazione del pacchetto di base.</span><span class="sxs-lookup"><span data-stu-id="b0386-126">To access this functionality, applications will require the Foundation package to be imported.</span></span>

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a><span data-ttu-id="b0386-127">CameraCache può creare una nuova fotocamera alla chiusura</span><span class="sxs-lookup"><span data-stu-id="b0386-127">CameraCache may create a new camera on shutdown</span></span>

<span data-ttu-id="b0386-128">In alcune situazioni, ad esempio quando si usa il provider LeapMotion nell'editor di Unity, è possibile che CameraCache ricrei il MainCamera all'arresto.</span><span class="sxs-lookup"><span data-stu-id="b0386-128">In some situations (e.g. when using the LeapMotion provider in the Unity Editor), it is possible for the CameraCache to re-create the MainCamera on shutdown.</span></span> <span data-ttu-id="b0386-129">Per ulteriori informazioni, vedere [questo problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) .</span><span class="sxs-lookup"><span data-stu-id="b0386-129">Please see [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) for more information.</span></span>

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a><span data-ttu-id="b0386-130">FileNotFoundException quando vengono importati esempi tramite Gestione pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="b0386-130">FileNotFoundException when examples are imported via Unity Package Manager</span></span>

<span data-ttu-id="b0386-131">A seconda della lunghezza del percorso del progetto, l'importazione di esempi tramite Gestione pacchetti Unity può generare messaggi FileNotFoundException nella console di Unity.</span><span class="sxs-lookup"><span data-stu-id="b0386-131">Depending on the length of the project path, importing examples via Unity Package Manager may generate FileNotFoundException messages in the Unity Console.</span></span> <span data-ttu-id="b0386-132">La cui origine è il percorso del file "mancante" che supera MAX_PATH (256 caratteri).</span><span class="sxs-lookup"><span data-stu-id="b0386-132">The cause of this is the path to the "missing" file being longer than MAX_PATH (256 characters).</span></span> <span data-ttu-id="b0386-133">Per risolvere il progetto, abbreviare la lunghezza del percorso del progetto.</span><span class="sxs-lookup"><span data-stu-id="b0386-133">To resolve, please shorten the length of the project path.</span></span>

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a><span data-ttu-id="b0386-134">Non è stato specificato alcun Spatializer.</span><span class="sxs-lookup"><span data-stu-id="b0386-134">No spatializer was specified.</span></span> <span data-ttu-id="b0386-135">L'applicazione non supporterà il suono spaziale</span><span class="sxs-lookup"><span data-stu-id="b0386-135">The application will not support Spatial Sound</span></span>

<span data-ttu-id="b0386-136">Se non è configurato un Spatializer audio, viene visualizzato un avviso "nessun Spatializer specificato".</span><span class="sxs-lookup"><span data-stu-id="b0386-136">A "No spatializer was specified" warning will appear if an audio spatializer is not configured.</span></span> <span data-ttu-id="b0386-137">Questo problema può verificarsi se non è installato alcun pacchetto XR, perché Unity include spatializers in questi pacakges.</span><span class="sxs-lookup"><span data-stu-id="b0386-137">This can occur if no XR package is installed, as Unity includes spatializers in these pacakges.</span></span>

<span data-ttu-id="b0386-138">Per risolverlo, verificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="b0386-138">To resolve, please ensure that:</span></span>

- <span data-ttu-id="b0386-139">**Finestra**  >  di In **Gestione pacchetti** sono installati uno o più pacchetti XR</span><span class="sxs-lookup"><span data-stu-id="b0386-139">**Window** > **Package Manager** has one or more XR packages installed</span></span>
- <span data-ttu-id="b0386-140">Toolkit per realtà **mista**  >  **Utilità**  >  di **Configurare il progetto Unity** ed effettuare una selezione per **Spatializer audio**</span><span class="sxs-lookup"><span data-stu-id="b0386-140">**Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and make a selection for **Audio Spatializer**</span></span>

  ![Seleziona Apatializer audio](../features/images/release-notes/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a><span data-ttu-id="b0386-142">NullReferenceException: riferimento all'oggetto non impostato su un'istanza di un oggetto (SceneTransitionService.Initialize)</span><span class="sxs-lookup"><span data-stu-id="b0386-142">NullReferenceException: Object reference not set to an instance of an object (SceneTransitionService.Initialize)</span></span>

<span data-ttu-id="b0386-143">In alcune situazioni, l'apertura `EyeTrackingDemo-00-RootScene` può causare un'eccezione NullReferenceException nel metodo Initialize della classe SceneTransitionService.</span><span class="sxs-lookup"><span data-stu-id="b0386-143">In some situations, opening `EyeTrackingDemo-00-RootScene` may cause a NullReferenceException in the Initialize method of the SceneTransitionService class.</span></span>
<span data-ttu-id="b0386-144">Questo errore è dovuto al fatto che il profilo di configurazione del servizio transizione della scena non è stato impostato.</span><span class="sxs-lookup"><span data-stu-id="b0386-144">This error is due to the Scene Transition Service's configuration profile being unset.</span></span> <span data-ttu-id="b0386-145">Per risolverlo, attenersi alla procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="b0386-145">To resolve, please use the following steps:</span></span>

- <span data-ttu-id="b0386-146">Passare all' `MixedRealityToolkit` oggetto nella gerarchia</span><span class="sxs-lookup"><span data-stu-id="b0386-146">Navigate to the `MixedRealityToolkit` object in the Hierarchy</span></span>
- <span data-ttu-id="b0386-147">Nella finestra di controllo selezionare `Extensions`</span><span class="sxs-lookup"><span data-stu-id="b0386-147">In the Inspector window, select `Extensions`</span></span>
- <span data-ttu-id="b0386-148">Se non è espanso, espandere `Scene Transition Service`</span><span class="sxs-lookup"><span data-stu-id="b0386-148">If not expanded, expand `Scene Transition Service`</span></span>
- <span data-ttu-id="b0386-149">Impostare il valore di `Configuration Profile` su **MRTKExamplesHubSceneTransitionServiceProfile**</span><span class="sxs-lookup"><span data-stu-id="b0386-149">Set the value of `Configuration Profile` to **MRTKExamplesHubSceneTransitionServiceProfile**</span></span>

<img src="../features/images/release-notes/FixSceneTransitionProfile.png" width="500px" alt="Fix Scene Transition">

### <a name="oculus-quest"></a><span data-ttu-id="b0386-150">Oculus-ricerca</span><span class="sxs-lookup"><span data-stu-id="b0386-150">Oculus Quest</span></span>

<span data-ttu-id="b0386-151">Attualmente esiste un problema noto per l'uso del [plug-in Oculus XR con quando si fa riferimento a piattaforme autonome](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span><span class="sxs-lookup"><span data-stu-id="b0386-151">There is currently a known issue for using the [Oculus XR plugin with when targeting Standalone platforms](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span></span>  <span data-ttu-id="b0386-152">Per gli aggiornamenti, vedere le note sulla versione, i forum e la registrazione di Oculus bug.</span><span class="sxs-lookup"><span data-stu-id="b0386-152">Check the Oculus bug tracker/forums/release notes for updates.</span></span>

<span data-ttu-id="b0386-153">Il bug è identificato da questo set di 3 errori:</span><span class="sxs-lookup"><span data-stu-id="b0386-153">The bug is signified with this set of 3 errors:</span></span>

![Errore del plug-in Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a><span data-ttu-id="b0386-155">UnityUI e TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="b0386-155">UnityUI and TextMeshPro</span></span>

<span data-ttu-id="b0386-156">Esiste un problema noto per le versioni più recenti di TextMeshPro (1.5.0 + o 2.1.1 +), in cui la dimensione del carattere predefinita per i menu a discesa e la spaziatura dei caratteri in grassetto è stata modificata.</span><span class="sxs-lookup"><span data-stu-id="b0386-156">There's a known issue for newer versions of TextMeshPro (1.5.0+ or 2.1.1+), where the default font size for dropdowns and bold font character spacing has been altered.</span></span>

![Immagine TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

<span data-ttu-id="b0386-158">Per risolvere il problema, è possibile effettuare il downgrade a una versione precedente di TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="b0386-158">This can be worked around by downgrading to an earlier version of TextMeshPro.</span></span> <span data-ttu-id="b0386-159">Per ulteriori informazioni, vedere la pagina relativa al [problema #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) .</span><span class="sxs-lookup"><span data-stu-id="b0386-159">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span></span>
