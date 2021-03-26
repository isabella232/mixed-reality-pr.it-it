---
title: Note sulla versione di MRTK 2,5
description: Release abbiend della versione corrente di MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 4d16707ab09fda3cbc511fc96bb2d385c21e3898
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550911"
---
# <a name="microsoft-mixed-reality-toolkit-254-release-notes"></a><span data-ttu-id="b3cd1-104">Note sulla versione di Microsoft Mixed Reality Toolkit 2.5.4</span><span class="sxs-lookup"><span data-stu-id="b3cd1-104">Microsoft Mixed Reality Toolkit 2.5.4 release notes</span></span>

- [<span data-ttu-id="b3cd1-105">Novità</span><span class="sxs-lookup"><span data-stu-id="b3cd1-105">What's new</span></span>](#whats-new)
- [<span data-ttu-id="b3cd1-106">Aggiornamento delle linee guida</span><span class="sxs-lookup"><span data-stu-id="b3cd1-106">Updating guidance</span></span>](../updates-deployment/updating.md#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="b3cd1-107">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="b3cd1-107">Known issues</span></span>](#known-issues)

> [!IMPORTANT]
> <span data-ttu-id="b3cd1-108">Si è verificato un problema noto del compilatore che influisca sulle applicazioni compilate per Microsoft HoloLens 2 usando ARM64.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-108">There is a known compiler issue that impacts applications built for Microsoft HoloLens 2 using ARM64.</span></span> <span data-ttu-id="b3cd1-109">Questo problema viene risolto aggiornando Visual Studio 2019 alla versione 16,8 o successiva.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-109">This issue is fixed by updating Visual Studio 2019 to version 16.8 or later.</span></span> <span data-ttu-id="b3cd1-110">Se non è possibile aggiornare Visual Studio, importare il `com.microsoft.mixedreality.toolkit.tools` pacchetto per applicare una soluzione alternativa.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-110">If you are unable to update Visual Studio, please import the `com.microsoft.mixedreality.toolkit.tools` package to apply a workaround.</span></span>

## <a name="whats-new"></a><span data-ttu-id="b3cd1-111">Novità</span><span class="sxs-lookup"><span data-stu-id="b3cd1-111">What's new</span></span>

### <a name="fixes-a-bug-with-oculus-integration-when-using-upm"></a><span data-ttu-id="b3cd1-112">Corregge un bug con l'integrazione di Oculus quando si usa UPM</span><span class="sxs-lookup"><span data-stu-id="b3cd1-112">Fixes a bug with Oculus Integration when using UPM</span></span>

<span data-ttu-id="b3cd1-113">Quando si usa il sistema di gestione delle dipendenze, il OculusXRSDKDeviceManagerProfile deve avere sempre i [prefabbricati impostati su None all'avvio](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160).</span><span class="sxs-lookup"><span data-stu-id="b3cd1-113">When using UPM, the OculusXRSDKDeviceManagerProfile would always have its [prefabs set to None on startup](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160).</span></span> <span data-ttu-id="b3cd1-114">Questa versione configura il Gestione dispositivi in modo che punti a una working set di prefabbricati all'avvio.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-114">This release configures the Device Manager to point to a working set of prefabs on startup.</span></span>

### <a name="fixes-an-issue-with-openxr-via-upm"></a><span data-ttu-id="b3cd1-115">Corregge un problema con OpenXR tramite UPM</span><span class="sxs-lookup"><span data-stu-id="b3cd1-115">Fixes an issue with OpenXR via UPM</span></span>

<span data-ttu-id="b3cd1-116">Corregge un problema per cui i provider OpenXR non sono stati aggiunti al link.xml per impostazione predefinita, causando l'esito negativo dell'esecuzione di nuovi progetti sul dispositivo quando si usano OpenXR e MRTK tramite Gestione pacchetti di Unity.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-116">Fixes an issue where the OpenXR providers weren't added to the link.xml by default, causing new projects to fail to run on-device when using OpenXR and MRTK via Unity's Package Manager.</span></span> <span data-ttu-id="b3cd1-117">I progetti esistenti aggiornati dovranno ancora essere aggiunti manualmente.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-117">Existing projects that are upgraded will still need this added manually.</span></span>

## <a name="what-was-new-in-253"></a><span data-ttu-id="b3cd1-118">Novità di 2.5.3</span><span class="sxs-lookup"><span data-stu-id="b3cd1-118">What was new in 2.5.3</span></span>

### <a name="fixes-a-regression-with-oculus-introduced-in-252"></a><span data-ttu-id="b3cd1-119">Corregge una regressione con Oculus introdotta in 2.5.2</span><span class="sxs-lookup"><span data-stu-id="b3cd1-119">Fixes a regression with Oculus introduced in 2.5.2</span></span>

<span data-ttu-id="b3cd1-120">in 2.5.2 è stato introdotto [un problema di compilazione durante l'integrazione di Oculus SDK](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083).</span><span class="sxs-lookup"><span data-stu-id="b3cd1-120">2.5.2 introduced [a build issue when integrating the Oculus SDK](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083).</span></span> <span data-ttu-id="b3cd1-121">Questa versione ripristina il problema.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-121">This release reverts that issue.</span></span>

### <a name="add-support-for-openxr"></a><span data-ttu-id="b3cd1-122">Aggiungere il supporto per OpenXR</span><span class="sxs-lookup"><span data-stu-id="b3cd1-122">Add support for OpenXR</span></span>

<span data-ttu-id="b3cd1-123">È stato aggiunto il supporto iniziale per il pacchetto di anteprima OpenXR di Unity e il pacchetto OpenXR per la realtà mista Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-123">Initial support for Unity's OpenXR preview package and Microsoft's Mixed Reality OpenXR package has been added.</span></span> <span data-ttu-id="b3cd1-124">Per altre informazioni, vedere la pagina introduttiva di [MRTK/XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md), [post del forum di Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)o [documentazione di Microsoft](/windows/mixed-reality/develop/unity/openxr-getting-started) .</span><span class="sxs-lookup"><span data-stu-id="b3cd1-124">See [the MRTK/XRSDK getting started page](../configuration/getting-started-with-mrtk-and-xrsdk.md), [Unity's forum post](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/), or [Microsoft's documentation](/windows/mixed-reality/develop/unity/openxr-getting-started) for more information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b3cd1-125">OpenXR in Unity è supportato solo in Unity 2020,2 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-125">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="b3cd1-126">Attualmente, supporta anche solo le compilazioni x64 e ARM64.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-126">Currently, it also only supports x64 and ARM64 builds.</span></span>

### <a name="boundary-visualization-errors-fixed"></a><span data-ttu-id="b3cd1-127">Errori di visualizzazione limite corretti</span><span class="sxs-lookup"><span data-stu-id="b3cd1-127">Boundary visualization errors fixed</span></span>

<span data-ttu-id="b3cd1-128">Le visualizzazioni dei limiti, come il piano o i muri, ora verranno configurate correttamente e visibili in fase di esecuzione in base al profilo limite.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-128">Boundary visualizations, like the floor or walls, will now be properly configured and visible at runtime according to the boundary profile.</span></span>

### <a name="msbuild-for-unity-support"></a><span data-ttu-id="b3cd1-129">Supporto di MSBuild per Unity</span><span class="sxs-lookup"><span data-stu-id="b3cd1-129">MSBuild for Unity support</span></span>

<span data-ttu-id="b3cd1-130">Il supporto per MSBuild per Unity è stato rimosso al rilascio di 2.5.2, per essere allineato con le [nuove linee guida per i pacchetti di Unity](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).</span><span class="sxs-lookup"><span data-stu-id="b3cd1-130">Support for MSBuild for Unity has been removed as of the 2.5.2 release, to align with [Unity's new package guidance](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).</span></span>

## <a name="known-issues"></a><span data-ttu-id="b3cd1-131">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="b3cd1-131">Known issues</span></span>

### <a name="openxr"></a><span data-ttu-id="b3cd1-132">OpenXR</span><span class="sxs-lookup"><span data-stu-id="b3cd1-132">OpenXR</span></span>

<span data-ttu-id="b3cd1-133">Attualmente esiste un problema noto con la comunicazione remota olografica e OpenXR, in cui le giunzioni a mano non sono costantemente disponibili.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-133">There's currently a known issue with Holographic Remoting and OpenXR, where hand joints aren't consistently available.</span></span>
<span data-ttu-id="b3cd1-134">Inoltre, le scene di esempio per la verifica degli occhi non sono attualmente compatibili, ma *il rilevamento degli occhi funziona.*</span><span class="sxs-lookup"><span data-stu-id="b3cd1-134">Additionally, the eye tracking sample scenes aren't currently compatible, though eye tracking *does* work.</span></span>

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a><span data-ttu-id="b3cd1-135">Alcune funzionalità dello shader standard del Toolkit di realtà mista richiedono il pacchetto di base</span><span class="sxs-lookup"><span data-stu-id="b3cd1-135">Some Mixed Reality Toolkit Standard Shader features require the Foundation package</span></span>

<span data-ttu-id="b3cd1-136">Quando viene importato tramite Gestione pacchetti Unity, gli script MRTK standard shader Utilities (ad esempio: HoverLight. cs) non sono collocati con lo shader nel pacchetto di asset standard.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-136">When imported via the Unity Package Manager, the MRTK Standard Shader utilities scripts (ex: HoverLight.cs) are not co-located with the shader in the Standard Assets package.</span></span> <span data-ttu-id="b3cd1-137">Per accedere a questa funzionalità, le applicazioni richiedono l'importazione del pacchetto di base.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-137">To access this functionality, applications will require the Foundation package to be imported.</span></span>

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a><span data-ttu-id="b3cd1-138">CameraCache può creare una nuova fotocamera alla chiusura</span><span class="sxs-lookup"><span data-stu-id="b3cd1-138">CameraCache may create a new camera on shutdown</span></span>

<span data-ttu-id="b3cd1-139">In alcune situazioni, ad esempio quando si usa il provider LeapMotion nell'editor di Unity, è possibile che CameraCache ricrei il MainCamera all'arresto.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-139">In some situations (e.g. when using the LeapMotion provider in the Unity Editor), it is possible for the CameraCache to re-create the MainCamera on shutdown.</span></span> <span data-ttu-id="b3cd1-140">Per ulteriori informazioni, vedere [questo problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) .</span><span class="sxs-lookup"><span data-stu-id="b3cd1-140">Please see [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) for more information.</span></span>

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a><span data-ttu-id="b3cd1-141">FileNotFoundException quando vengono importati esempi tramite Gestione pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="b3cd1-141">FileNotFoundException when examples are imported via Unity Package Manager</span></span>

<span data-ttu-id="b3cd1-142">A seconda della lunghezza del percorso del progetto, l'importazione di esempi tramite Gestione pacchetti Unity può generare messaggi FileNotFoundException nella console di Unity.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-142">Depending on the length of the project path, importing examples via Unity Package Manager may generate FileNotFoundException messages in the Unity Console.</span></span> <span data-ttu-id="b3cd1-143">La cui origine è il percorso del file "mancante" che supera MAX_PATH (256 caratteri).</span><span class="sxs-lookup"><span data-stu-id="b3cd1-143">The cause of this is the path to the "missing" file being longer than MAX_PATH (256 characters).</span></span> <span data-ttu-id="b3cd1-144">Per risolvere il progetto, abbreviare la lunghezza del percorso del progetto.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-144">To resolve, please shorten the length of the project path.</span></span>

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a><span data-ttu-id="b3cd1-145">Non è stato specificato alcun Spatializer.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-145">No spatializer was specified.</span></span> <span data-ttu-id="b3cd1-146">L'applicazione non supporterà il suono spaziale</span><span class="sxs-lookup"><span data-stu-id="b3cd1-146">The application will not support Spatial Sound</span></span>

<span data-ttu-id="b3cd1-147">Se non è configurato un Spatializer audio, viene visualizzato un avviso "nessun Spatializer specificato".</span><span class="sxs-lookup"><span data-stu-id="b3cd1-147">A "No spatializer was specified" warning will appear if an audio spatializer is not configured.</span></span> <span data-ttu-id="b3cd1-148">Questo problema può verificarsi se non è installato alcun pacchetto XR, perché Unity include spatializers in questi pacchetti.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-148">This can occur if no XR package is installed, as Unity includes spatializers in these packages.</span></span>

<span data-ttu-id="b3cd1-149">Per risolverlo, verificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="b3cd1-149">To resolve, please ensure that:</span></span>

- <span data-ttu-id="b3cd1-150">**Finestra**  >  di In **Gestione pacchetti** sono installati uno o più pacchetti XR</span><span class="sxs-lookup"><span data-stu-id="b3cd1-150">**Window** > **Package Manager** has one or more XR packages installed</span></span>
- <span data-ttu-id="b3cd1-151">Toolkit per realtà **mista**  >  **Utilità**  >  di **Configurare il progetto Unity** ed effettuare una selezione per **Spatializer audio**</span><span class="sxs-lookup"><span data-stu-id="b3cd1-151">**Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and make a selection for **Audio Spatializer**</span></span>

  ![Seleziona Apatializer audio](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a><span data-ttu-id="b3cd1-153">NullReferenceException: riferimento all'oggetto non impostato su un'istanza di un oggetto (SceneTransitionService.Initialize)</span><span class="sxs-lookup"><span data-stu-id="b3cd1-153">NullReferenceException: Object reference not set to an instance of an object (SceneTransitionService.Initialize)</span></span>

<span data-ttu-id="b3cd1-154">In alcune situazioni, l'apertura `EyeTrackingDemo-00-RootScene` può causare un'eccezione NullReferenceException nel metodo Initialize della classe SceneTransitionService.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-154">In some situations, opening `EyeTrackingDemo-00-RootScene` may cause a NullReferenceException in the Initialize method of the SceneTransitionService class.</span></span>
<span data-ttu-id="b3cd1-155">Questo errore è dovuto al fatto che il profilo di configurazione del servizio transizione della scena non è stato impostato.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-155">This error is due to the Scene Transition Service's configuration profile being unset.</span></span> <span data-ttu-id="b3cd1-156">Per risolverlo, attenersi alla procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="b3cd1-156">To resolve, please use the following steps:</span></span>

- <span data-ttu-id="b3cd1-157">Passare all' `MixedRealityToolkit` oggetto nella gerarchia</span><span class="sxs-lookup"><span data-stu-id="b3cd1-157">Navigate to the `MixedRealityToolkit` object in the Hierarchy</span></span>
- <span data-ttu-id="b3cd1-158">Nella finestra di controllo selezionare `Extensions`</span><span class="sxs-lookup"><span data-stu-id="b3cd1-158">In the Inspector window, select `Extensions`</span></span>
- <span data-ttu-id="b3cd1-159">Se non è espanso, espandere `Scene Transition Service`</span><span class="sxs-lookup"><span data-stu-id="b3cd1-159">If not expanded, expand `Scene Transition Service`</span></span>
- <span data-ttu-id="b3cd1-160">Impostare il valore di `Configuration Profile` su **MRTKExamplesHubSceneTransitionServiceProfile**</span><span class="sxs-lookup"><span data-stu-id="b3cd1-160">Set the value of `Configuration Profile` to **MRTKExamplesHubSceneTransitionServiceProfile**</span></span>

![Correzione della transizione della scena](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a><span data-ttu-id="b3cd1-162">Oculus-ricerca</span><span class="sxs-lookup"><span data-stu-id="b3cd1-162">Oculus Quest</span></span>

<span data-ttu-id="b3cd1-163">Attualmente esiste un problema noto per l'uso del [plug-in Oculus XR con quando si fa riferimento a piattaforme autonome](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span><span class="sxs-lookup"><span data-stu-id="b3cd1-163">There is currently a known issue for using the [Oculus XR plugin with when targeting Standalone platforms](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span></span>  <span data-ttu-id="b3cd1-164">Per gli aggiornamenti, vedere le note sulla versione, i forum e la registrazione di Oculus bug.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-164">Check the Oculus bug tracker/forums/release notes for updates.</span></span>

<span data-ttu-id="b3cd1-165">Il bug è identificato da questo set di 3 errori:</span><span class="sxs-lookup"><span data-stu-id="b3cd1-165">The bug is signified with this set of 3 errors:</span></span>

![Errore del plug-in Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a><span data-ttu-id="b3cd1-167">UnityUI e TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="b3cd1-167">UnityUI and TextMeshPro</span></span>

<span data-ttu-id="b3cd1-168">Esiste un problema noto per le versioni più recenti di TextMeshPro (1.5.0 + o 2.1.1 +), in cui la dimensione del carattere predefinita per i menu a discesa e la spaziatura dei caratteri in grassetto è stata modificata.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-168">There's a known issue for newer versions of TextMeshPro (1.5.0+ or 2.1.1+), where the default font size for dropdowns and bold font character spacing has been altered.</span></span>

![Immagine TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

<span data-ttu-id="b3cd1-170">Per risolvere il problema, è possibile effettuare il downgrade a una versione precedente di TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="b3cd1-170">This can be worked around by downgrading to an earlier version of TextMeshPro.</span></span> <span data-ttu-id="b3cd1-171">Per ulteriori informazioni, vedere la pagina relativa al [problema #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) .</span><span class="sxs-lookup"><span data-stu-id="b3cd1-171">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span></span>