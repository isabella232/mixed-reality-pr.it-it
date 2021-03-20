---
title: GettingStartedWithMRTKAndXRSDK
description: Pagina di destinazione per MRTK con XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, XRSDK,
ms.openlocfilehash: c1f4baec1927fd97948245f31c40788473c457d0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681274"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="9f5f9-104">Introduzione a MRTK e XR SDK</span><span class="sxs-lookup"><span data-stu-id="9f5f9-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="9f5f9-105">XR SDK è la [nuova pipeline XR di Unity in unity 2019,3 e versioni successive](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="9f5f9-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="9f5f9-106">In Unity 2019, fornisce un'alternativa alla pipeline XR esistente.</span><span class="sxs-lookup"><span data-stu-id="9f5f9-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="9f5f9-107">In Unity 2020, diventerà l'unica pipeline XR in Unity.</span><span class="sxs-lookup"><span data-stu-id="9f5f9-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9f5f9-108">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="9f5f9-108">Prerequisites</span></span>

<span data-ttu-id="9f5f9-109">Per iniziare a usare il Toolkit di realtà mista, seguire [i passaggi forniti](../WelcomeToMRTK.md) per aggiungere MRTK a un progetto.</span><span class="sxs-lookup"><span data-stu-id="9f5f9-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../WelcomeToMRTK.md) to add MRTK to a project.</span></span>

## <a name="add-xr-sdk-to-a-unity-project"></a><span data-ttu-id="9f5f9-110">Aggiungere XR SDK a un progetto Unity</span><span class="sxs-lookup"><span data-stu-id="9f5f9-110">Add XR SDK to a Unity project</span></span>

<span data-ttu-id="9f5f9-111">Per MRTK 2,3, la realtà mista di Windows è supportata in XR SDK.</span><span class="sxs-lookup"><span data-stu-id="9f5f9-111">For MRTK 2.3, Windows Mixed Reality is supported on XR SDK.</span></span>

### <a name="required-in-unity"></a><span data-ttu-id="9f5f9-112">Obbligatorio in Unity</span><span class="sxs-lookup"><span data-stu-id="9f5f9-112">Required in Unity</span></span>

1. <span data-ttu-id="9f5f9-113">Passare a gestione pacchetti di Unity e installare il pacchetto di plug-in di Windows XR, che aggiunge il supporto per la realtà mista di Windows in XR SDK.</span><span class="sxs-lookup"><span data-stu-id="9f5f9-113">Go into Unity's Package Manager and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="9f5f9-114">Verrà anche effettuato il pull di alcuni pacchetti di dipendenze.</span><span class="sxs-lookup"><span data-stu-id="9f5f9-114">This will pull down a few dependency packages as well.</span></span> <span data-ttu-id="9f5f9-115">Verificare che tutti gli elementi seguenti siano stati installati correttamente:</span><span class="sxs-lookup"><span data-stu-id="9f5f9-115">Ensure the following all successfully installed:</span></span>
   1. <span data-ttu-id="9f5f9-116">Gestione dei plug-in XR</span><span class="sxs-lookup"><span data-stu-id="9f5f9-116">XR Plugin Management</span></span>
   1. <span data-ttu-id="9f5f9-117">Plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="9f5f9-117">Windows XR Plugin</span></span>
   1. <span data-ttu-id="9f5f9-118">Helper di input legacy XR</span><span class="sxs-lookup"><span data-stu-id="9f5f9-118">XR Legacy Input Helpers</span></span>
1. <span data-ttu-id="9f5f9-119">Passare a modifica > impostazioni progetto.</span><span class="sxs-lookup"><span data-stu-id="9f5f9-119">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="9f5f9-120">Fare clic sulla scheda Gestione plug-in XR nella finestra Impostazioni progetto.</span><span class="sxs-lookup"><span data-stu-id="9f5f9-120">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="9f5f9-121">Passare alle impostazioni piattaforma UWP (Universal Windows Platform) e verificare che la realtà mista di Windows sia selezionata in provider plug-in.</span><span class="sxs-lookup"><span data-stu-id="9f5f9-121">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
1. <span data-ttu-id="9f5f9-122">Assicurarsi che l'opzione Inizializza XR all'avvio sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="9f5f9-122">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="9f5f9-123">(**_Facoltativo_**) Fare clic sulla scheda realtà mista di Windows in Gestione plug-in XR e creare un profilo delle impostazioni personalizzate per modificare le impostazioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="9f5f9-123">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="9f5f9-124">Se l'elenco delle impostazioni è già presente, non è necessario creare alcun profilo.</span><span class="sxs-lookup"><span data-stu-id="9f5f9-124">If the list of settings are already there, no profile needs to be created.</span></span>

![Gestione dei plug-in](../features/Images/XRSDK/PluginManagement.png)

### <a name="required-in-mrtk"></a><span data-ttu-id="9f5f9-126">Obbligatorio in MRTK</span><span class="sxs-lookup"><span data-stu-id="9f5f9-126">Required in MRTK</span></span>

<span data-ttu-id="9f5f9-127">Scegliere "DefaultXRSDKConfigurationProfile" come profilo attivo o clonarlo per apportare le personalizzazioni.</span><span class="sxs-lookup"><span data-stu-id="9f5f9-127">Choose the "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span> <span data-ttu-id="9f5f9-128">Questo profilo è configurato con i sistemi e i provider di MRTK XR SDK, ove necessario.</span><span class="sxs-lookup"><span data-stu-id="9f5f9-128">This profile is set up with MRTK's XR SDK systems and providers, where needed.</span></span>

<span data-ttu-id="9f5f9-129">Per eseguire la migrazione di un profilo esistente a XR SDK, è necessario aggiornare i servizi e i provider di dati seguenti:</span><span class="sxs-lookup"><span data-stu-id="9f5f9-129">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

#### <a name="camera"></a><span data-ttu-id="9f5f9-130">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="9f5f9-130">Camera</span></span>

<span data-ttu-id="9f5f9-131">Da [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="9f5f9-131">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![Impostazioni della fotocamera legacy](../features/Images/XRSDK/CameraSystemLegacy.png)

<span data-ttu-id="9f5f9-133">a [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **e**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="9f5f9-133">to [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span>

![Impostazioni della fotocamera di XR SDK](../features/Images/XRSDK/CameraSystemXRSDK.png)

#### <a name="input"></a><span data-ttu-id="9f5f9-135">Input</span><span class="sxs-lookup"><span data-stu-id="9f5f9-135">Input</span></span>

<span data-ttu-id="9f5f9-136">Da [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="9f5f9-136">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![Impostazioni di input legacy](../features/Images/XRSDK/InputSystemWMRLegacy.png)

<span data-ttu-id="9f5f9-138">A [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="9f5f9-138">to [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager)</span></span>

![Impostazioni di input di XR SDK](../features/Images/XRSDK/InputSystemWMRXRSDK.png)

#### <a name="boundary"></a><span data-ttu-id="9f5f9-140">Limite</span><span class="sxs-lookup"><span data-stu-id="9f5f9-140">Boundary</span></span>

<span data-ttu-id="9f5f9-141">Da [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="9f5f9-141">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![Impostazioni limite legacy](../features/Images/XRSDK/BoundarySystemLegacy.png)

<span data-ttu-id="9f5f9-143">A  [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="9f5f9-143">to  [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem)</span></span>

![Impostazioni limite SDK XR](../features/Images/XRSDK/BoundarySystemXRSDK.png)

#### <a name="spatial-awareness"></a><span data-ttu-id="9f5f9-145">Consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="9f5f9-145">Spatial awareness</span></span>

<span data-ttu-id="9f5f9-146">Da [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="9f5f9-146">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Impostazioni di consapevolezza spaziale legacy](../features/Images/XRSDK/SpatialAwarenessLegacy.png)

<span data-ttu-id="9f5f9-148">A [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="9f5f9-148">to [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Impostazioni di sensibilizzazione spaziale di XR SDK](../features/Images/XRSDK/SpatialAwarenessXRSDK.png)

#### <a name="controller-mappings"></a><span data-ttu-id="9f5f9-150">Mapping dei controller</span><span class="sxs-lookup"><span data-stu-id="9f5f9-150">Controller mappings</span></span>

<span data-ttu-id="9f5f9-151">Se si usano profili di mapping del controller personalizzato, aprire uno di essi ed eseguire la voce di menu Mixed Reality Toolkit-> Utilities-> Update-> controller mapping del controller per assicurarsi che siano definiti i nuovi tipi di controller di XR SDK.</span><span class="sxs-lookup"><span data-stu-id="9f5f9-151">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f5f9-152">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="9f5f9-152">See also</span></span>

* [<span data-ttu-id="9f5f9-153">Introduzione allo sviluppo AR in Unity</span><span class="sxs-lookup"><span data-stu-id="9f5f9-153">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="9f5f9-154">Introduzione allo sviluppo per VR in Unity</span><span class="sxs-lookup"><span data-stu-id="9f5f9-154">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)
