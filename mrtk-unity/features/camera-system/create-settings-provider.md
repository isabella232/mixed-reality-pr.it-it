---
title: Creazione di un provider di impostazioni della fotocamera
description: Provider di dati per le impostazioni della fotocamera in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 2151887a6162239e993634d5d346065362f1c428
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282032"
---
# <a name="creating-a-camera-settings-provider"></a><span data-ttu-id="921ac-104">Creazione di un provider di impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="921ac-104">Creating a camera settings provider</span></span>

<span data-ttu-id="921ac-105">Il sistema camera è un sistema estendibile per fornire il supporto per le configurazioni della fotocamera specifiche della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="921ac-105">The Camera system is an extensible system for providing support for platform specific camera configurations.</span></span> <span data-ttu-id="921ac-106">Per aggiungere il supporto per una nuova configurazione della fotocamera, potrebbe essere necessario un provider di impostazioni personalizzato.</span><span class="sxs-lookup"><span data-stu-id="921ac-106">To add support for a new camera configuration, a custom settings provider may be required.</span></span>

> [!NOTE]
> <span data-ttu-id="921ac-107">Il codice sorgente completo usato in questo esempio è disponibile nella **cartella MRTK/Providers/UnityAR.**</span><span class="sxs-lookup"><span data-stu-id="921ac-107">The complete source code used in this example can be found in the **MRTK/Providers/UnityAR** folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="921ac-108">Spazio dei nomi e struttura di cartelle</span><span class="sxs-lookup"><span data-stu-id="921ac-108">Namespace and folder structure</span></span>

<span data-ttu-id="921ac-109">I provider di dati possono essere distribuiti in uno dei due modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="921ac-109">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="921ac-110">Componenti aggiuntivi di terze parti</span><span class="sxs-lookup"><span data-stu-id="921ac-110">Third party add-ons</span></span>
1. <span data-ttu-id="921ac-111">Parte di Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="921ac-111">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="921ac-112">Il processo di approvazione per l'invio di nuovi provider di dati a MRTK varia caso per caso e verrà comunicato al momento della proposta iniziale.</span><span class="sxs-lookup"><span data-stu-id="921ac-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="921ac-113">Le proposte possono essere inviate creando un nuovo problema relativo al [ *tipo di richiesta* di funzionalità](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span><span class="sxs-lookup"><span data-stu-id="921ac-113">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-ons"></a><span data-ttu-id="921ac-114">Componenti aggiuntivi di terze parti</span><span class="sxs-lookup"><span data-stu-id="921ac-114">Third party add-ons</span></span>

<span data-ttu-id="921ac-115">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="921ac-115">**Namespace**</span></span>

<span data-ttu-id="921ac-116">I provider di dati devono disporre di uno spazio dei nomi per ridurre i potenziali conflitti di nomi.</span><span class="sxs-lookup"><span data-stu-id="921ac-116">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="921ac-117">È consigliabile che lo spazio dei nomi includa i componenti seguenti.</span><span class="sxs-lookup"><span data-stu-id="921ac-117">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="921ac-118">Nome della società che produce il componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="921ac-118">Company name producing the add-on</span></span>
- <span data-ttu-id="921ac-119">Area funzionale</span><span class="sxs-lookup"><span data-stu-id="921ac-119">Feature area</span></span>

<span data-ttu-id="921ac-120">Ad esempio, un provider di impostazioni della fotocamera creato e spedito dalla società Contoso può essere *"Contoso.MixedReality.Toolkit. Camera".*</span><span class="sxs-lookup"><span data-stu-id="921ac-120">For example, a camera settings provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.Camera"*.</span></span>

<span data-ttu-id="921ac-121">**Struttura di cartelle**</span><span class="sxs-lookup"><span data-stu-id="921ac-121">**Folder structure**</span></span>

<span data-ttu-id="921ac-122">È consigliabile che il codice sorgente per i provider di dati sia disponibile in una gerarchia di cartelle, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="921ac-122">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Esempio di struttura di cartelle](../images/camera-system/ExampleProviderFolderStructure.png)

<span data-ttu-id="921ac-124">Dove la cartella *ContosoCamera* contiene l'implementazione del provider di dati, la cartella *Editor* contiene il controllo (e qualsiasi altro codice specifico dell'editor unity) e la cartella *Profiles* contiene uno o più oggetti predefiniti del profilo che è possibile creare script.</span><span class="sxs-lookup"><span data-stu-id="921ac-124">Where the *ContosoCamera* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="921ac-125">Invio di MRTK</span><span class="sxs-lookup"><span data-stu-id="921ac-125">MRTK submission</span></span>

<span data-ttu-id="921ac-126">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="921ac-126">**Namespace**</span></span>

<span data-ttu-id="921ac-127">Se un provider di impostazioni della fotocamera viene inviato al [repository mixed reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity), lo spazio dei nomi **deve** iniziare con Microsoft.MixedReality. Toolkit (ad *esempio: Microsoft.MixedReality.Toolkit. CameraSystem*).</span><span class="sxs-lookup"><span data-stu-id="921ac-127">If a camera settings provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.CameraSystem*).</span></span>

<span data-ttu-id="921ac-128">**Struttura di cartelle**</span><span class="sxs-lookup"><span data-stu-id="921ac-128">**Folder structure**</span></span>

<span data-ttu-id="921ac-129">Tutto il codice deve trovarsi in una cartella sotto MRTK/Providers (ad esempio: MRTK/Providers/UnityAR).</span><span class="sxs-lookup"><span data-stu-id="921ac-129">All code must be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/UnityAR).</span></span>

## <a name="define-the-camera-settings-object"></a><span data-ttu-id="921ac-130">Definire l'oggetto impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="921ac-130">Define the camera settings object</span></span>

<span data-ttu-id="921ac-131">Il primo passaggio per la creazione di un provider di impostazioni della fotocamera consiste nel determinare il tipo di dati (ad esempio mesh o piani) che fornirà alle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="921ac-131">The first step in creating a camera settings provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="921ac-132">Tutti gli oggetti dati spaziali devono implementare [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) l'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="921ac-132">All spatial data objects must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface.</span></span>

## <a name="implement-the-settings-provider"></a><span data-ttu-id="921ac-133">Implementare il provider di impostazioni</span><span class="sxs-lookup"><span data-stu-id="921ac-133">Implement the settings provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="921ac-134">Specificare l'ereditarietà dell'interfaccia e/o della classe base</span><span class="sxs-lookup"><span data-stu-id="921ac-134">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="921ac-135">Tutti i provider di impostazioni della fotocamera devono implementare l'interfaccia , che [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) specifica la funzionalità minima richiesta dal sistema di fotocamera.</span><span class="sxs-lookup"><span data-stu-id="921ac-135">All camera settings providers must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface, which specifies the minimum functionality required by the camera system.</span></span> <span data-ttu-id="921ac-136">La base di MRTK include [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) la classe che fornisce un'implementazione predefinita della funzionalità richiesta.</span><span class="sxs-lookup"><span data-stu-id="921ac-136">The MRTK foundation includes the [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) class which provides a default implementation of the required functionality.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="921ac-137">Applicare l'attributo MixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="921ac-137">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="921ac-138">Un passaggio chiave nella creazione di un provider di impostazioni della fotocamera consiste nell'applicare [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) l'attributo alla classe .</span><span class="sxs-lookup"><span data-stu-id="921ac-138">A key step in creating a camera settings provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="921ac-139">Questo passaggio abilita l'impostazione del profilo e delle piattaforme predefiniti per il provider di dati, se selezionato nel profilo Sistema fotocamera, nonché nome, percorso della cartella e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="921ac-139">This step enables setting the default profile and platform(s) for the data provider, when selected in the Camera System profile as well as name, folder path, and more.</span></span>

```c#
    [MixedRealityDataProvider(
        typeof(IMixedRealityCameraSystem),
        SupportedPlatforms.Android | SupportedPlatforms.IOS,
        "Unity AR Foundation Camera Settings",
        "UnityAR/Profiles/DefaultUnityARCameraSettingsProfile.asset",
        "MixedRealityToolkit.Providers")]
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="921ac-140">Implementare i metodi IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="921ac-140">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="921ac-141">Dopo aver definito la classe , il passaggio successivo consiste nel fornire l'implementazione [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) dell'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="921ac-141">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="921ac-142">La [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) classe , tramite la classe , fornisce [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) implementazioni vuote per i metodi [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) .</span><span class="sxs-lookup"><span data-stu-id="921ac-142">The [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="921ac-143">I dettagli di questi metodi sono in genere specifici del provider di dati.</span><span class="sxs-lookup"><span data-stu-id="921ac-143">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="921ac-144">I metodi che devono essere implementati dal provider di dati sono:</span><span class="sxs-lookup"><span data-stu-id="921ac-144">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> <span data-ttu-id="921ac-145">Non tutti i provider di impostazioni richiedono implementazioni per tutti questi metodi.</span><span class="sxs-lookup"><span data-stu-id="921ac-145">Not all settings providers will require implementations for all of these methods.</span></span> <span data-ttu-id="921ac-146">È consigliabile che `Destroy()` e `Initialize()` siano implementati come minimo.</span><span class="sxs-lookup"><span data-stu-id="921ac-146">It is highly recommended that `Destroy()` and `Initialize()` be implemented at a minimum.</span></span>

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="921ac-147">Implementare la logica del provider di dati</span><span class="sxs-lookup"><span data-stu-id="921ac-147">Implement the data provider logic</span></span>

<span data-ttu-id="921ac-148">Il passaggio successivo consiste nell'aggiungere la logica del provider di impostazioni implementando [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) .</span><span class="sxs-lookup"><span data-stu-id="921ac-148">The next step is to add the logic of the settings provider by implementing [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider).</span></span> <span data-ttu-id="921ac-149">Questa parte del provider di dati sarà in genere specifica della configurazione della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="921ac-149">This portion of the data provider will typically be camera configuration specific.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="921ac-150">Creare il profilo e il controllo</span><span class="sxs-lookup"><span data-stu-id="921ac-150">Create the profile and inspector</span></span>

<span data-ttu-id="921ac-151">Nel modello di realtà Toolkit, i provider di dati vengono configurati usando [i profili](../profiles/profiles.md).</span><span class="sxs-lookup"><span data-stu-id="921ac-151">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="921ac-152">Definire il profilo</span><span class="sxs-lookup"><span data-stu-id="921ac-152">Define the profile</span></span>

<span data-ttu-id="921ac-153">Il contenuto del profilo deve rispecchiare le opzioni di configurazione selezionabili dallo sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="921ac-153">Profile contents should mirror the developer selectable configuration options.</span></span> <span data-ttu-id="921ac-154">Anche tutte le proprietà configurabili dall'utente definite in ogni interfaccia devono essere contenute nel profilo.</span><span class="sxs-lookup"><span data-stu-id="921ac-154">Any user configurable properties defined in each interface should also be contained with the profile.</span></span>

```c#
using UnityEngine.SpatialTracking;

namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CreateAssetMenu(
        menuName = "Mixed Reality Toolkit/Profiles/Unity AR Camera Settings Profile",
        fileName = "UnityARCameraSettingsProfile",
        order = 100)]
    public class UnityARCameraSettingsProfile : BaseCameraSettingsProfile
    {
        [SerializeField]
        [Tooltip("The portion of the device (ex: color camera) from which to read the pose.")]
        private ArTrackedPose poseSource = TrackedPoseDriver.TrackedPose.ColorCamera;

        /// <summary>
        /// The portion of the device (ex: color camera) from which to read the pose.
        /// </summary>
        public ArTrackedPose PoseSource => poseSource;

        [SerializeField]
        [Tooltip("The type of tracking (position and/or rotation) to apply.")]
        private ArTrackingType trackingType = TrackedPoseDriver.TrackingType.RotationAndPosition;

        /// <summary>
        /// The type of tracking (position and/or rotation) to apply.
        /// </summary>
        public ArTrackingType TrackingType => trackingType;

        [SerializeField]
        [Tooltip("Specifies when (during Update and/or just before rendering) to update the tracking of the pose.")]
        private ArUpdateType updateType = TrackedPoseDriver.UpdateType.UpdateAndBeforeRender;

        /// <summary>
        /// Specifies when (during Update and/or just before rendering) to update the tracking of the pose.
        /// </summary>
        public ArUpdateType UpdateType => updateType;
    }
}
```

<span data-ttu-id="921ac-155">L'attributo può essere applicato alla classe del profilo per consentire ai clienti di creare un'istanza del profilo usando il menu Create `CreateAssetMenu`   >  **Assets**  >  **Mixed Reality Toolkit** Profiles (Crea asset Toolkit  >  **profili).**</span><span class="sxs-lookup"><span data-stu-id="921ac-155">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="921ac-156">Implementare il controllo</span><span class="sxs-lookup"><span data-stu-id="921ac-156">Implement the inspector</span></span>

<span data-ttu-id="921ac-157">I controlli profilo sono l'interfaccia utente per la configurazione e la visualizzazione del contenuto del profilo.</span><span class="sxs-lookup"><span data-stu-id="921ac-157">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="921ac-158">Ogni controllo profilo deve estendere la [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) classe .</span><span class="sxs-lookup"><span data-stu-id="921ac-158">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="921ac-159">`CustomEditor`L'attributo indica a Unity il tipo di asset a cui si applica il controllo.</span><span class="sxs-lookup"><span data-stu-id="921ac-159">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="921ac-160">Creare definizioni di assembly</span><span class="sxs-lookup"><span data-stu-id="921ac-160">Create assembly definition(s)</span></span>

<span data-ttu-id="921ac-161">L'Toolkit realtà mista usa i file di definizione dell'assembly (con estensione[asmdef)](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)per specificare le dipendenze tra i componenti e per aiutare Unity a ridurre il tempo di compilazione.</span><span class="sxs-lookup"><span data-stu-id="921ac-161">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="921ac-162">È consigliabile creare file di definizione dell'assembly per tutti i provider di dati e i relativi componenti dell'editor.</span><span class="sxs-lookup"><span data-stu-id="921ac-162">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="921ac-163">Usando la [struttura di cartelle](#namespace-and-folder-structure) nell'esempio precedente, saranno presenti due file con estensione asmdef per il provider di dati ContosoCamera.</span><span class="sxs-lookup"><span data-stu-id="921ac-163">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoCamera data provider.</span></span>

<span data-ttu-id="921ac-164">La prima definizione di assembly è per il provider di dati.</span><span class="sxs-lookup"><span data-stu-id="921ac-164">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="921ac-165">Per questo esempio, si chiamerà ContosoCamera e si trova nella cartella *ContosoCamera* dell'esempio.</span><span class="sxs-lookup"><span data-stu-id="921ac-165">For this example, it will be called ContosoCamera and will be located in the example's *ContosoCamera* folder.</span></span> <span data-ttu-id="921ac-166">Questa definizione di assembly deve specificare una dipendenza da Microsoft.MixedReality. Toolkit e qualsiasi altro assembly da cui dipende.</span><span class="sxs-lookup"><span data-stu-id="921ac-166">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="921ac-167">La definizione dell'assembly ContosoCameraEditor specificherà il controllo del profilo e qualsiasi codice specifico dell'editor.</span><span class="sxs-lookup"><span data-stu-id="921ac-167">The ContosoCameraEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="921ac-168">Questo file deve trovarsi nella cartella radice del codice dell'editor.</span><span class="sxs-lookup"><span data-stu-id="921ac-168">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="921ac-169">In questo esempio il file si trova nella *cartella ContosoCamera\Editor.*</span><span class="sxs-lookup"><span data-stu-id="921ac-169">In this example, the file will be located in the *ContosoCamera\Editor* folder.</span></span> <span data-ttu-id="921ac-170">Questa definizione di assembly conterrà un riferimento all'assembly ContosoCamera, nonché:</span><span class="sxs-lookup"><span data-stu-id="921ac-170">This assembly definition will contain a reference to the ContosoCamera assembly as well as:</span></span>

- <span data-ttu-id="921ac-171">Microsoft.MixedReality. Toolkit</span><span class="sxs-lookup"><span data-stu-id="921ac-171">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="921ac-172">Microsoft.MixedReality. Toolkit. Editor.Inspectors</span><span class="sxs-lookup"><span data-stu-id="921ac-172">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="921ac-173">Microsoft.MixedReality. Toolkit. Editor.Utilities</span><span class="sxs-lookup"><span data-stu-id="921ac-173">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="921ac-174">Registrare il provider di dati</span><span class="sxs-lookup"><span data-stu-id="921ac-174">Register the data provider</span></span>

<span data-ttu-id="921ac-175">Una volta creato, il provider di dati può essere registrato con il sistema Camera da usare nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="921ac-175">Once created, the data provider can be registered with the Camera system to be used in the application.</span></span>

![Selezione del provider di impostazioni della fotocamera](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="921ac-177">Creazione di pacchetti e distribuzione</span><span class="sxs-lookup"><span data-stu-id="921ac-177">Packaging and distribution</span></span>

<span data-ttu-id="921ac-178">I provider di dati distribuiti come componenti di terze parti hanno i dettagli specifici dei pacchetti e della distribuzione lasciati alle preferenze dello sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="921ac-178">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="921ac-179">È probabile che la soluzione più comune sia generare un file con estensione unitypackage e distribuirsi tramite Unity Asset Store.</span><span class="sxs-lookup"><span data-stu-id="921ac-179">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="921ac-180">Se un provider di dati viene inviato e accettato come parte del pacchetto Microsoft Mixed Reality Toolkit, il team di Microsoft MRTK lo inserirà in un pacchetto e lo distribuirà come parte delle offerte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="921ac-180">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="921ac-181">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="921ac-181">See also</span></span>

- [<span data-ttu-id="921ac-182">Panoramica del sistema di fotocamera</span><span class="sxs-lookup"><span data-stu-id="921ac-182">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="921ac-183">Classe `BaseCameraSettingsProvider`</span><span class="sxs-lookup"><span data-stu-id="921ac-183">`BaseCameraSettingsProvider` class</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [<span data-ttu-id="921ac-184">`IMixedRealityCameraSettingsProvider` Interfaccia</span><span class="sxs-lookup"><span data-stu-id="921ac-184">`IMixedRealityCameraSettingsProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [<span data-ttu-id="921ac-185">`IMixedRealityDataProvider` Interfaccia</span><span class="sxs-lookup"><span data-stu-id="921ac-185">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
