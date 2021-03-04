---
title: GettingStartedWithMRTKAndXRSDK
description: Pagina di destinazione per MRTK con XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, XRSDK,
ms.openlocfilehash: 10296553786763dca8f0ac8f6507a815eccadeff
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783272"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="ccc03-104">Introduzione a MRTK e XR SDK</span><span class="sxs-lookup"><span data-stu-id="ccc03-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="ccc03-105">XR SDK è la [nuova pipeline XR di Unity in unity 2019,3 e versioni successive](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="ccc03-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="ccc03-106">In Unity 2019, fornisce un'alternativa alla pipeline XR esistente.</span><span class="sxs-lookup"><span data-stu-id="ccc03-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="ccc03-107">In Unity 2020, diventerà l'unica pipeline XR in Unity.</span><span class="sxs-lookup"><span data-stu-id="ccc03-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ccc03-108">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="ccc03-108">Prerequisites</span></span>

<span data-ttu-id="ccc03-109">Per iniziare a usare il Toolkit di realtà mista, seguire [i passaggi forniti](../../2.5.4/welcome-to-mrtk.md) per aggiungere MRTK a un progetto.</span><span class="sxs-lookup"><span data-stu-id="ccc03-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../../2.5.4/welcome-to-mrtk.md) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="ccc03-110">Configurazione di Unity per la pipeline di XR SDK</span><span class="sxs-lookup"><span data-stu-id="ccc03-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="ccc03-111">La pipeline dell'SDK XR supporta attualmente 3 piattaforme: realtà mista di Windows, Oculus e OpenXR.</span><span class="sxs-lookup"><span data-stu-id="ccc03-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="ccc03-112">Le sezioni seguenti illustrano i passaggi necessari per configurare XR SDK per ogni piattaforma.</span><span class="sxs-lookup"><span data-stu-id="ccc03-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

#### <a name="windows-mixed-reality"></a><span data-ttu-id="ccc03-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ccc03-113">Windows Mixed Reality</span></span>

1. <span data-ttu-id="ccc03-114">Passare a gestione pacchetti di Unity e installare il pacchetto di plug-in di Windows XR, che aggiunge il supporto per la realtà mista di Windows in XR SDK.</span><span class="sxs-lookup"><span data-stu-id="ccc03-114">Go into Unity's Package Manager and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="ccc03-115">Verrà anche effettuato il pull di alcuni pacchetti di dipendenze.</span><span class="sxs-lookup"><span data-stu-id="ccc03-115">This will pull down a few dependency packages as well.</span></span> <span data-ttu-id="ccc03-116">Verificare che tutti gli elementi seguenti siano stati installati correttamente:</span><span class="sxs-lookup"><span data-stu-id="ccc03-116">Ensure that the following all successfully installed:</span></span>
   1. <span data-ttu-id="ccc03-117">Gestione dei plug-in XR</span><span class="sxs-lookup"><span data-stu-id="ccc03-117">XR Plugin Management</span></span>
   1. <span data-ttu-id="ccc03-118">Plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="ccc03-118">Windows XR Plugin</span></span>
   1. <span data-ttu-id="ccc03-119">Helper di input legacy XR</span><span class="sxs-lookup"><span data-stu-id="ccc03-119">XR Legacy Input Helpers</span></span>
1. <span data-ttu-id="ccc03-120">Passare a modifica > impostazioni progetto.</span><span class="sxs-lookup"><span data-stu-id="ccc03-120">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="ccc03-121">Fare clic sulla scheda Gestione plug-in XR nella finestra Impostazioni progetto.</span><span class="sxs-lookup"><span data-stu-id="ccc03-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="ccc03-122">Passare alle impostazioni piattaforma UWP (Universal Windows Platform) e verificare che la realtà mista di Windows sia selezionata in provider plug-in.</span><span class="sxs-lookup"><span data-stu-id="ccc03-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
1. <span data-ttu-id="ccc03-123">Assicurarsi che l'opzione Inizializza XR all'avvio sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="ccc03-123">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="ccc03-124">(**_Obbligatorio per la comunicazione remota HoloLens nell'editor, in caso contrario facoltativo_**) Passare alle impostazioni autonome e verificare che la realtà mista di Windows sia selezionata in provider plug-in.</span><span class="sxs-lookup"><span data-stu-id="ccc03-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="ccc03-125">Assicurarsi anche che Initialize XR all'avvio sia selezionato.</span><span class="sxs-lookup"><span data-stu-id="ccc03-125">Also ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="ccc03-126">(**_Facoltativo_**) Fare clic sulla scheda realtà mista di Windows in Gestione plug-in XR e creare un profilo delle impostazioni personalizzate per modificare le impostazioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="ccc03-126">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="ccc03-127">Se l'elenco delle impostazioni è già presente, non è necessario creare alcun profilo.</span><span class="sxs-lookup"><span data-stu-id="ccc03-127">If the list of settings are already there, no profile needs to be created.</span></span>

![Gestione dei plug-in](../features/images/xrsdk/PluginManagement.png)

#### <a name="oculus"></a><span data-ttu-id="ccc03-129">Oculus</span><span class="sxs-lookup"><span data-stu-id="ccc03-129">Oculus</span></span>

1. <span data-ttu-id="ccc03-130">Seguire la [procedura come configurare Oculus quest in MRTK usando la guida alla pipeline dell'SDK XR](../features/cross-platform/oculus-quest-mrtk.md) alla fine.</span><span class="sxs-lookup"><span data-stu-id="ccc03-130">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../features/cross-platform/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="ccc03-131">La guida descrive i passaggi necessari per configurare Unity e MRTK per l'uso della pipeline di XR SDK per l'Oculus quest.</span><span class="sxs-lookup"><span data-stu-id="ccc03-131">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

#### <a name="openxr-preview"></a><span data-ttu-id="ccc03-132">OpenXR (anteprima)</span><span class="sxs-lookup"><span data-stu-id="ccc03-132">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ccc03-133">OpenXR in Unity è supportato solo in Unity 2020,2 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ccc03-133">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="ccc03-134">Attualmente, supporta anche solo le compilazioni x64 e ARM64.</span><span class="sxs-lookup"><span data-stu-id="ccc03-134">Currently, it also only supports x64 and ARM64 builds.</span></span>

1. <span data-ttu-id="ccc03-135">Per installare il plug-in di OpenXR nel progetto, seguire la guida per l'uso del plug-in [reality OpenXR per Unity](https://aka.ms/openxr-unity-install) , inclusi i passaggi per la configurazione della gestione dei plug-in XR e dell'ottimizzazione.</span><span class="sxs-lookup"><span data-stu-id="ccc03-135">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](https://aka.ms/openxr-unity-install) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="ccc03-136">Verificare che siano stati installati i seguenti elementi:</span><span class="sxs-lookup"><span data-stu-id="ccc03-136">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="ccc03-137">Gestione dei plug-in XR</span><span class="sxs-lookup"><span data-stu-id="ccc03-137">XR Plugin Management</span></span>
   1. <span data-ttu-id="ccc03-138">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="ccc03-138">OpenXR Plugin</span></span>
   1. <span data-ttu-id="ccc03-139">Plug-in OpenXR realtà mista</span><span class="sxs-lookup"><span data-stu-id="ccc03-139">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="ccc03-140">Passare a modifica > impostazioni progetto.</span><span class="sxs-lookup"><span data-stu-id="ccc03-140">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="ccc03-141">Fare clic sulla scheda Gestione plug-in XR nella finestra Impostazioni progetto.</span><span class="sxs-lookup"><span data-stu-id="ccc03-141">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="ccc03-142">Assicurarsi che l'opzione Inizializza XR all'avvio sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="ccc03-142">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="ccc03-143">(**_Facoltativo_**) Se la destinazione è HoloLens 2, assicurarsi di trovarsi nella piattaforma UWP e selezionare il set di funzionalità di Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="ccc03-143">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![Gestione plug-in aperto XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="ccc03-145">Se si dispone di un progetto preesistente che usa MRTK da UPM, assicurarsi che la riga seguente si trovi nel file **link.xml** che si trova nella cartella MixedRealityToolkit. generated.</span><span class="sxs-lookup"><span data-stu-id="ccc03-145">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="ccc03-146">Per la versione iniziale di MRTK e OpenXR, sono supportati in modo nativo solo i controller di movimento per la realtà mista HoloLens 2 e Windows.</span><span class="sxs-lookup"><span data-stu-id="ccc03-146">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="ccc03-147">Il supporto per hardware aggiuntivo verrà aggiunto nelle prossime versioni.</span><span class="sxs-lookup"><span data-stu-id="ccc03-147">Support for additional hardware will be added in upcoming releases.</span></span>

### <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="ccc03-148">Configurazione di MRTK per la pipeline di XR SDK</span><span class="sxs-lookup"><span data-stu-id="ccc03-148">Configuring MRTK for the XR SDK pipeline</span></span>

<span data-ttu-id="ccc03-149">Se si usa OpenXR, scegliere "DefaultOpenXRConfigurationProfile" come profilo attivo o clonarlo per apportare le personalizzazioni.</span><span class="sxs-lookup"><span data-stu-id="ccc03-149">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="ccc03-150">Se si usano altri runtime XR nella configurazione di gestione plug-in XR, ad esempio realtà mista di Windows o Oculus, scegliere "DefaultXRSDKConfigurationProfile" come profilo attivo o clonarlo per apportare le personalizzazioni.</span><span class="sxs-lookup"><span data-stu-id="ccc03-150">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="ccc03-151">Questi profili sono configurati con i sistemi e i provider corretti, ove necessario.</span><span class="sxs-lookup"><span data-stu-id="ccc03-151">These profiles are set up with the correct systems and providers, where needed.</span></span>

<span data-ttu-id="ccc03-152">Per eseguire la migrazione di un profilo esistente a XR SDK, è necessario aggiornare i servizi e i provider di dati seguenti:</span><span class="sxs-lookup"><span data-stu-id="ccc03-152">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

#### <a name="camera"></a><span data-ttu-id="ccc03-153">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="ccc03-153">Camera</span></span>

<span data-ttu-id="ccc03-154">Da [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="ccc03-154">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![Impostazioni della fotocamera legacy](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="ccc03-156">in</span><span class="sxs-lookup"><span data-stu-id="ccc03-156">to</span></span>

| <span data-ttu-id="ccc03-157">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ccc03-157">OpenXR</span></span> | <span data-ttu-id="ccc03-158">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ccc03-158">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | <span data-ttu-id="ccc03-159">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**e**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="ccc03-159">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span> |

![Impostazioni della fotocamera di XR SDK](../features/images/xrsdk/CameraSystemXRSDK.png)

#### <a name="input"></a><span data-ttu-id="ccc03-161">Input</span><span class="sxs-lookup"><span data-stu-id="ccc03-161">Input</span></span>

<span data-ttu-id="ccc03-162">Da [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="ccc03-162">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![Impostazioni di input legacy](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="ccc03-164">in</span><span class="sxs-lookup"><span data-stu-id="ccc03-164">to</span></span>

| <span data-ttu-id="ccc03-165">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ccc03-165">OpenXR</span></span> | <span data-ttu-id="ccc03-166">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ccc03-166">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="ccc03-167">__OpenXR__:</span><span class="sxs-lookup"><span data-stu-id="ccc03-167">__OpenXR__:</span></span>

![Impostazioni di input di OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="ccc03-169">__Realtà mista di Windows__:</span><span class="sxs-lookup"><span data-stu-id="ccc03-169">__Windows Mixed Reality__:</span></span>

![Impostazioni di input di XR SDK](../features/images/xrsdk/InputSystemWMRXRSDK.png)

#### <a name="boundary"></a><span data-ttu-id="ccc03-171">Limite</span><span class="sxs-lookup"><span data-stu-id="ccc03-171">Boundary</span></span>

<span data-ttu-id="ccc03-172">Da [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="ccc03-172">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![Impostazioni limite legacy](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="ccc03-174">in</span><span class="sxs-lookup"><span data-stu-id="ccc03-174">to</span></span>

| <span data-ttu-id="ccc03-175">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ccc03-175">OpenXR</span></span> | <span data-ttu-id="ccc03-176">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ccc03-176">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Impostazioni limite SDK XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

#### <a name="spatial-awareness"></a><span data-ttu-id="ccc03-178">Consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="ccc03-178">Spatial awareness</span></span>

<span data-ttu-id="ccc03-179">Da [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="ccc03-179">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Impostazioni di consapevolezza spaziale legacy](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="ccc03-181">in</span><span class="sxs-lookup"><span data-stu-id="ccc03-181">to</span></span>

| <span data-ttu-id="ccc03-182">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ccc03-182">OpenXR</span></span> | <span data-ttu-id="ccc03-183">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ccc03-183">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| <span data-ttu-id="ccc03-184">In corso</span><span class="sxs-lookup"><span data-stu-id="ccc03-184">In progress</span></span> | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Impostazioni di sensibilizzazione spaziale di XR SDK](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

#### <a name="controller-mappings"></a><span data-ttu-id="ccc03-186">Mapping dei controller</span><span class="sxs-lookup"><span data-stu-id="ccc03-186">Controller mappings</span></span>

<span data-ttu-id="ccc03-187">Se si usano profili di mapping del controller personalizzato, aprire uno di essi ed eseguire la voce di menu Mixed Reality Toolkit-> Utilities-> Update-> controller mapping del controller per assicurarsi che siano definiti i nuovi tipi di controller di XR SDK.</span><span class="sxs-lookup"><span data-stu-id="ccc03-187">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccc03-188">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="ccc03-188">See also</span></span>

* [<span data-ttu-id="ccc03-189">Introduzione allo sviluppo AR in Unity</span><span class="sxs-lookup"><span data-stu-id="ccc03-189">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="ccc03-190">Introduzione allo sviluppo per VR in Unity</span><span class="sxs-lookup"><span data-stu-id="ccc03-190">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)
