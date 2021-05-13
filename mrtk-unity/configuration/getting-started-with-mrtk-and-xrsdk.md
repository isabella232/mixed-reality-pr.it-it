---
title: GettingStartedWithMRTKAndXRSDK
description: Pagina di destinazione per MRTK con XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, XRSDK,
ms.openlocfilehash: fe50de31ae24b415738db64073822b2aff061636
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850427"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="f6c15-104">Introduzione a MRTK e XR SDK</span><span class="sxs-lookup"><span data-stu-id="f6c15-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="f6c15-105">XR SDK è la nuova pipeline XR di [Unity in Unity 2019.3 e oltre.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)</span><span class="sxs-lookup"><span data-stu-id="f6c15-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="f6c15-106">In Unity 2019 offre un'alternativa alla pipeline XR esistente.</span><span class="sxs-lookup"><span data-stu-id="f6c15-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="f6c15-107">In Unity 2020 diventerà l'unica pipeline XR in Unity.</span><span class="sxs-lookup"><span data-stu-id="f6c15-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f6c15-108">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="f6c15-108">Prerequisites</span></span>

<span data-ttu-id="f6c15-109">Per iniziare a usare Mixed Reality Toolkit, seguire [la](../install-the-tools.md#importing-the-mixed-reality-toolkit) procedura fornita per aggiungere MRTK a un progetto.</span><span class="sxs-lookup"><span data-stu-id="f6c15-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="f6c15-110">Configurazione di Unity per la pipeline di XR SDK</span><span class="sxs-lookup"><span data-stu-id="f6c15-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="f6c15-111">La pipeline XR SDK supporta attualmente 3 piattaforme: Windows Mixed Reality, Oculus e OpenXR.</span><span class="sxs-lookup"><span data-stu-id="f6c15-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="f6c15-112">Le sezioni seguenti illustrano i passaggi necessari per configurare XR SDK per ogni piattaforma.</span><span class="sxs-lookup"><span data-stu-id="f6c15-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="f6c15-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f6c15-113">Windows Mixed Reality</span></span>

<span data-ttu-id="f6c15-114">Passare alla **versione di Unity Gestione pacchetti** installare il pacchetto plug-in Windows XR, che aggiunge il supporto per Windows Mixed Reality in XR SDK.</span><span class="sxs-lookup"><span data-stu-id="f6c15-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="f6c15-115">Verrà visualizzato anche alcuni pacchetti di dipendenze.</span><span class="sxs-lookup"><span data-stu-id="f6c15-115">This will pull down a few dependency packages as well.</span></span> 

1. <span data-ttu-id="f6c15-116">Assicurarsi che tutti gli elementi seguenti siano stati installati correttamente:</span><span class="sxs-lookup"><span data-stu-id="f6c15-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="f6c15-117">Gestione plug-in XR</span><span class="sxs-lookup"><span data-stu-id="f6c15-117">XR Plugin Management</span></span>
   * <span data-ttu-id="f6c15-118">Plug-in XR di Windows</span><span class="sxs-lookup"><span data-stu-id="f6c15-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="f6c15-119">Helper di input legacy XR</span><span class="sxs-lookup"><span data-stu-id="f6c15-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="f6c15-120">Passa a **Edit > Project Settings** (Modifica > Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="f6c15-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="f6c15-121">Fare clic sulla scheda Gestione plug-in XR nella finestra Impostazioni progetto.</span><span class="sxs-lookup"><span data-stu-id="f6c15-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="f6c15-122">Passare alle impostazioni piattaforma UWP (Universal Windows Platform) e verificare che Windows Mixed Reality sia selezionato in Provider di plug-in.</span><span class="sxs-lookup"><span data-stu-id="f6c15-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="f6c15-123">Assicurarsi che l'opzione Inizializza XR all'avvio sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="f6c15-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="f6c15-124">(**_Obbligatorio per la comunicazione remota di HoloLens nell'editor, in caso contrario facoltativo_**) Passare a Impostazioni autonome e verificare che Windows Mixed Reality sia selezionata in Provider di plug-in.</span><span class="sxs-lookup"><span data-stu-id="f6c15-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="f6c15-125">Assicurarsi inoltre che l'opzione Initialize XR on Startup (Inizializza XR all'avvio) sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="f6c15-125">Also ensure that Initialize XR on Startup is checked.</span></span>

![Gestione del plug-in XR con la scheda Autonomo selezionata](images/xr-management-img-02.png)

7. <span data-ttu-id="f6c15-127">(**_Facoltativo_**) Fare clic sulla Windows Mixed Reality in XR Plug-in Management (Gestione plug-in XR) e creare un profilo di impostazioni personalizzate per modificare le impostazioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="f6c15-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="f6c15-128">Se l'elenco delle impostazioni è già presente, non è necessario creare alcun profilo.</span><span class="sxs-lookup"><span data-stu-id="f6c15-128">If the list of settings are already there, no profile needs to be created.</span></span>

![Gestione del plug-in XR con la scheda Windows selezionata](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="f6c15-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="f6c15-130">Oculus</span></span>

1. <span data-ttu-id="f6c15-131">Seguire la guida alla fine [come configurare Oculus Quest in MRTK usando la pipeline XR SDK.](../supported-devices/oculus-quest-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="f6c15-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="f6c15-132">La guida illustra i passaggi necessari per configurare Unity e MRTK per l'uso della pipeline XR SDK per Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="f6c15-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="f6c15-133">OpenXR (anteprima)</span><span class="sxs-lookup"><span data-stu-id="f6c15-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f6c15-134">OpenXR in Unity è supportato solo in Unity 2020.2 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f6c15-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="f6c15-135">Attualmente supporta solo le build x64 e ARM64.</span><span class="sxs-lookup"><span data-stu-id="f6c15-135">Currently, it also only supports x64 and ARM64 builds.</span></span>

1. <span data-ttu-id="f6c15-136">Seguire la guida [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) (Uso del plug-in OpenXR di Realtà mista per Unity), inclusi i passaggi per configurare la gestione e l'ottimizzazione dei plug-in XR per installare il plug-in OpenXR nel progetto.</span><span class="sxs-lookup"><span data-stu-id="f6c15-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="f6c15-137">Verificare che gli elementi seguenti siano stati installati correttamente:</span><span class="sxs-lookup"><span data-stu-id="f6c15-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="f6c15-138">Gestione dei plug-in XR</span><span class="sxs-lookup"><span data-stu-id="f6c15-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="f6c15-139">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="f6c15-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="f6c15-140">Plug-in OpenXR per realtà mista</span><span class="sxs-lookup"><span data-stu-id="f6c15-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="f6c15-141">Passare a Modifica impostazioni > progetto.</span><span class="sxs-lookup"><span data-stu-id="f6c15-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="f6c15-142">Fare clic sulla scheda XR Plug-in Management (Gestione plug-in XR) nella finestra Project Settings (Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="f6c15-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="f6c15-143">Assicurarsi che l'opzione Initialize XR on Startup (Inizializza XR all'avvio) sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="f6c15-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="f6c15-144">(**_Facoltativo_**) Se la destinazione HoloLens 2, assicurarsi di essere nella piattaforma UWP e selezionare Microsoft HoloLens set di funzionalità</span><span class="sxs-lookup"><span data-stu-id="f6c15-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![Gestione dei plug-in Open XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="f6c15-146">Se si dispone di un progetto preesistibile che usa MRTK da UPM, assicurarsi che la riga seguente si trovi nel file **link.xml** che si trova nella cartella MixedRealityToolkit.Generated.</span><span class="sxs-lookup"><span data-stu-id="f6c15-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="f6c15-147">Per la versione iniziale di MRTK e OpenXR, sono supportati in modo nativo HoloLens 2 mani articolate e Windows Mixed Reality di movimento.</span><span class="sxs-lookup"><span data-stu-id="f6c15-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="f6c15-148">Nelle prossime versioni verrà aggiunto il supporto per hardware aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="f6c15-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="f6c15-149">Configurazione di MRTK per la pipeline di XR SDK</span><span class="sxs-lookup"><span data-stu-id="f6c15-149">Configuring MRTK for the XR SDK pipeline</span></span>

<span data-ttu-id="f6c15-150">Se si usa OpenXR, scegliere "DefaultOpenXRConfigurationProfile" come profilo attivo o clonarlo per apportare personalizzazioni.</span><span class="sxs-lookup"><span data-stu-id="f6c15-150">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="f6c15-151">Se si usano altri runtime XR nella configurazione di Gestione plug-in XR, ad esempio Windows Mixed Reality o Oculus, scegliere "DefaultXRSDKConfigurationProfile" come profilo attivo o clonarlo per apportare personalizzazioni.</span><span class="sxs-lookup"><span data-stu-id="f6c15-151">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="f6c15-152">Questi profili vengono impostati con i sistemi e i provider corretti, se necessario.</span><span class="sxs-lookup"><span data-stu-id="f6c15-152">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="f6c15-153">Per [altre informazioni sul profilo e](../features/profiles/profiles.md#xr-sdk) sul supporto di esempio con XR SDK, vedere la documentazione sui profili.</span><span class="sxs-lookup"><span data-stu-id="f6c15-153">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>

<span data-ttu-id="f6c15-154">Per eseguire la migrazione di un profilo esistente a XR SDK, è necessario aggiornare i servizi e i provider di dati seguenti:</span><span class="sxs-lookup"><span data-stu-id="f6c15-154">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

### <a name="camera"></a><span data-ttu-id="f6c15-155">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="f6c15-155">Camera</span></span>

<span data-ttu-id="f6c15-156">Da [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="f6c15-156">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![Impostazioni della fotocamera legacy](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="f6c15-158">in</span><span class="sxs-lookup"><span data-stu-id="f6c15-158">to</span></span>

| <span data-ttu-id="f6c15-159">OpenXR</span><span class="sxs-lookup"><span data-stu-id="f6c15-159">OpenXR</span></span> | <span data-ttu-id="f6c15-160">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f6c15-160">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | <span data-ttu-id="f6c15-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**e**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="f6c15-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span> |

![Impostazioni della fotocamera di XR SDK](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="f6c15-163">Input</span><span class="sxs-lookup"><span data-stu-id="f6c15-163">Input</span></span>

<span data-ttu-id="f6c15-164">Da [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="f6c15-164">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![Impostazioni di input legacy](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="f6c15-166">in</span><span class="sxs-lookup"><span data-stu-id="f6c15-166">to</span></span>

| <span data-ttu-id="f6c15-167">OpenXR</span><span class="sxs-lookup"><span data-stu-id="f6c15-167">OpenXR</span></span> | <span data-ttu-id="f6c15-168">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f6c15-168">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="f6c15-169">__OpenXR__:</span><span class="sxs-lookup"><span data-stu-id="f6c15-169">__OpenXR__:</span></span>

![Impostazioni di input OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="f6c15-171">__Windows Mixed Reality__:</span><span class="sxs-lookup"><span data-stu-id="f6c15-171">__Windows Mixed Reality__:</span></span>

![Impostazioni di input di XR SDK](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="f6c15-173">Limite</span><span class="sxs-lookup"><span data-stu-id="f6c15-173">Boundary</span></span>

<span data-ttu-id="f6c15-174">Da [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="f6c15-174">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![Impostazioni dei limiti legacy](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="f6c15-176">in</span><span class="sxs-lookup"><span data-stu-id="f6c15-176">to</span></span>

| <span data-ttu-id="f6c15-177">OpenXR</span><span class="sxs-lookup"><span data-stu-id="f6c15-177">OpenXR</span></span> | <span data-ttu-id="f6c15-178">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f6c15-178">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Impostazioni dei limiti di XR SDK](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="f6c15-180">Consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="f6c15-180">Spatial awareness</span></span>

<span data-ttu-id="f6c15-181">Da [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="f6c15-181">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Impostazioni di consapevolezza spaziale legacy](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="f6c15-183">in</span><span class="sxs-lookup"><span data-stu-id="f6c15-183">to</span></span>

| <span data-ttu-id="f6c15-184">OpenXR</span><span class="sxs-lookup"><span data-stu-id="f6c15-184">OpenXR</span></span> | <span data-ttu-id="f6c15-185">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f6c15-185">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| <span data-ttu-id="f6c15-186">In corso</span><span class="sxs-lookup"><span data-stu-id="f6c15-186">In progress</span></span> | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Impostazioni di consapevolezza spaziale di XR SDK](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="f6c15-188">Mapping dei controller</span><span class="sxs-lookup"><span data-stu-id="f6c15-188">Controller mappings</span></span>

<span data-ttu-id="f6c15-189">Se si usano profili di mapping del controller personalizzati, aprirne uno ed eseguire la voce di menu Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles per assicurarsi che siano definiti i nuovi tipi di controller XR SDK.</span><span class="sxs-lookup"><span data-stu-id="f6c15-189">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6c15-190">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="f6c15-190">See also</span></span>

* [<span data-ttu-id="f6c15-191">Introduzione allo sviluppo ar in Unity</span><span class="sxs-lookup"><span data-stu-id="f6c15-191">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="f6c15-192">Introduzione allo sviluppo della realtà virtuale in Unity</span><span class="sxs-lookup"><span data-stu-id="f6c15-192">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)