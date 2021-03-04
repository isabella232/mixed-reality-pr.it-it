---
title: GettingStartedWithMRTKAndXRSDK
description: Pagina di destinazione per MRTK con XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, XRSDK,
ms.openlocfilehash: ac0529242a1f9d22876a847501dd32273b8c78b7
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783724"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="09c51-104">Introduzione a MRTK e XR SDK</span><span class="sxs-lookup"><span data-stu-id="09c51-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="09c51-105">XR SDK è la [nuova pipeline XR di Unity in unity 2019,3 e versioni successive](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="09c51-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="09c51-106">In Unity 2019, fornisce un'alternativa alla pipeline XR esistente.</span><span class="sxs-lookup"><span data-stu-id="09c51-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="09c51-107">In Unity 2020, diventerà l'unica pipeline XR in Unity.</span><span class="sxs-lookup"><span data-stu-id="09c51-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="09c51-108">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="09c51-108">Prerequisites</span></span>

<span data-ttu-id="09c51-109">Per iniziare a usare il Toolkit di realtà mista, seguire [i passaggi forniti](../WelcomeToMRTK.md) per aggiungere MRTK a un progetto.</span><span class="sxs-lookup"><span data-stu-id="09c51-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../WelcomeToMRTK.md) to add MRTK to a project.</span></span>

## <a name="add-xr-sdk-to-a-unity-project"></a><span data-ttu-id="09c51-110">Aggiungere XR SDK a un progetto Unity</span><span class="sxs-lookup"><span data-stu-id="09c51-110">Add XR SDK to a Unity project</span></span>

<span data-ttu-id="09c51-111">La realtà mista di Windows e l'Oculus sono supportati in XR SDK.</span><span class="sxs-lookup"><span data-stu-id="09c51-111">Windows Mixed Reality and Oculus are supported on XR SDK.</span></span>

### <a name="required-in-unity"></a><span data-ttu-id="09c51-112">Obbligatorio in Unity</span><span class="sxs-lookup"><span data-stu-id="09c51-112">Required in Unity</span></span>

#### <a name="windows-mixed-reality"></a><span data-ttu-id="09c51-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="09c51-113">Windows Mixed Reality</span></span>

1. <span data-ttu-id="09c51-114">Passare a gestione pacchetti di Unity e installare il pacchetto di plug-in di Windows XR, che aggiunge il supporto per la realtà mista di Windows in XR SDK.</span><span class="sxs-lookup"><span data-stu-id="09c51-114">Go into Unity's Package Manager and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="09c51-115">Verrà anche effettuato il pull di alcuni pacchetti di dipendenze.</span><span class="sxs-lookup"><span data-stu-id="09c51-115">This will pull down a few dependency packages as well.</span></span> <span data-ttu-id="09c51-116">Verificare che tutti gli elementi seguenti siano stati installati correttamente:</span><span class="sxs-lookup"><span data-stu-id="09c51-116">Ensure the following all successfully installed:</span></span>
   1. <span data-ttu-id="09c51-117">Gestione dei plug-in XR</span><span class="sxs-lookup"><span data-stu-id="09c51-117">XR Plugin Management</span></span>
   1. <span data-ttu-id="09c51-118">Plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="09c51-118">Windows XR Plugin</span></span>
   1. <span data-ttu-id="09c51-119">Helper di input legacy XR</span><span class="sxs-lookup"><span data-stu-id="09c51-119">XR Legacy Input Helpers</span></span>
1. <span data-ttu-id="09c51-120">Passare a modifica > impostazioni progetto.</span><span class="sxs-lookup"><span data-stu-id="09c51-120">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="09c51-121">Fare clic sulla scheda Gestione plug-in XR nella finestra Impostazioni progetto.</span><span class="sxs-lookup"><span data-stu-id="09c51-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="09c51-122">Passare alle impostazioni piattaforma UWP (Universal Windows Platform) e verificare che la realtà mista di Windows sia selezionata in provider plug-in.</span><span class="sxs-lookup"><span data-stu-id="09c51-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
1. <span data-ttu-id="09c51-123">Assicurarsi che l'opzione Inizializza XR all'avvio sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="09c51-123">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="09c51-124">(**_Obbligatorio per la comunicazione remota HoloLens nell'editor, in caso contrario facoltativo_**) Passare alle impostazioni autonome e verificare che la realtà mista di Windows sia selezionata in provider plug-in.</span><span class="sxs-lookup"><span data-stu-id="09c51-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="09c51-125">Assicurarsi anche che Initialize XR all'avvio sia selezionato.</span><span class="sxs-lookup"><span data-stu-id="09c51-125">Also ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="09c51-126">(**_Facoltativo_**) Fare clic sulla scheda realtà mista di Windows in Gestione plug-in XR e creare un profilo delle impostazioni personalizzate per modificare le impostazioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="09c51-126">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="09c51-127">Se l'elenco delle impostazioni è già presente, non è necessario creare alcun profilo.</span><span class="sxs-lookup"><span data-stu-id="09c51-127">If the list of settings are already there, no profile needs to be created.</span></span>

![Gestione dei plug-in](../features/images/xrsdk/PluginManagement.png)

### <a name="required-in-mrtk"></a><span data-ttu-id="09c51-129">Obbligatorio in MRTK</span><span class="sxs-lookup"><span data-stu-id="09c51-129">Required in MRTK</span></span>

<span data-ttu-id="09c51-130">Scegliere "DefaultXRSDKConfigurationProfile" come profilo attivo o clonarlo per apportare le personalizzazioni.</span><span class="sxs-lookup"><span data-stu-id="09c51-130">Choose the "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span> <span data-ttu-id="09c51-131">Questo profilo è configurato con i sistemi e i provider di MRTK XR SDK, ove necessario.</span><span class="sxs-lookup"><span data-stu-id="09c51-131">This profile is set up with MRTK's XR SDK systems and providers, where needed.</span></span>

<span data-ttu-id="09c51-132">Per eseguire la migrazione di un profilo esistente a XR SDK, è necessario aggiornare i servizi e i provider di dati seguenti:</span><span class="sxs-lookup"><span data-stu-id="09c51-132">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

#### <a name="camera"></a><span data-ttu-id="09c51-133">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="09c51-133">Camera</span></span>

<span data-ttu-id="09c51-134">Da [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="09c51-134">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![Impostazioni della fotocamera legacy](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="09c51-136">a [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **e**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="09c51-136">to [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span>

![Impostazioni della fotocamera di XR SDK](../features/images/xrsdk/CameraSystemXRSDK.png)

#### <a name="input"></a><span data-ttu-id="09c51-138">Input</span><span class="sxs-lookup"><span data-stu-id="09c51-138">Input</span></span>

<span data-ttu-id="09c51-139">Da [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="09c51-139">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![Impostazioni di input legacy](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="09c51-141">A [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="09c51-141">to [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager)</span></span>

![Impostazioni di input di XR SDK](../features/images/xrsdk/InputSystemWMRXRSDK.png)

#### <a name="boundary"></a><span data-ttu-id="09c51-143">Limite</span><span class="sxs-lookup"><span data-stu-id="09c51-143">Boundary</span></span>

<span data-ttu-id="09c51-144">Da [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="09c51-144">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![Impostazioni limite legacy](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="09c51-146">A  [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="09c51-146">to  [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem)</span></span>

![Impostazioni limite SDK XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

#### <a name="spatial-awareness"></a><span data-ttu-id="09c51-148">Consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="09c51-148">Spatial awareness</span></span>

<span data-ttu-id="09c51-149">Da [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="09c51-149">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Impostazioni di consapevolezza spaziale legacy](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="09c51-151">A [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="09c51-151">to [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Impostazioni di sensibilizzazione spaziale di XR SDK](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

#### <a name="controller-mappings"></a><span data-ttu-id="09c51-153">Mapping dei controller</span><span class="sxs-lookup"><span data-stu-id="09c51-153">Controller mappings</span></span>

<span data-ttu-id="09c51-154">Se si usano profili di mapping del controller personalizzato, aprire uno di essi ed eseguire la voce di menu Mixed Reality Toolkit-> Utilities-> Update-> controller mapping del controller per assicurarsi che siano definiti i nuovi tipi di controller di XR SDK.</span><span class="sxs-lookup"><span data-stu-id="09c51-154">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="09c51-155">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="09c51-155">See also</span></span>

* [<span data-ttu-id="09c51-156">Introduzione allo sviluppo AR in Unity</span><span class="sxs-lookup"><span data-stu-id="09c51-156">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="09c51-157">Introduzione allo sviluppo per VR in Unity</span><span class="sxs-lookup"><span data-stu-id="09c51-157">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)
