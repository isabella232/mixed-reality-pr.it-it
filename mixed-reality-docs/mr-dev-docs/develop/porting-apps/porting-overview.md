---
title: Panoramica della conversione
description: Panoramica delle varie opzioni di porting per l'uso delle applicazioni esistenti per la realtà mista per HoloLens e VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: porting, Unity, middleware, motore, UWP, Win32
ms.openlocfilehash: 5b89d3448a7baf12cc76dd3677140fcf6e297ee2
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299786"
---
# <a name="porting-overview"></a><span data-ttu-id="60fb5-104">Panoramica della conversione</span><span class="sxs-lookup"><span data-stu-id="60fb5-104">Porting overview</span></span>

<span data-ttu-id="60fb5-105">Quando si tratta di eseguire il porting o l'aggiornamento dei progetti esistenti per la realtà mista, il percorso di porting dipende dal fatto che l'app venga compilata con Unity o Unreal Engine e abbia come destinazione HoloLens (1st Gen) o HoloLens 2 o SteamVR.</span><span class="sxs-lookup"><span data-stu-id="60fb5-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="60fb5-106">Questa pagina di panoramica contiene le raccomandazioni correnti per ogni piattaforma e dispositivo. Assicurarsi di controllare quando questi processi cambiano sempre.</span><span class="sxs-lookup"><span data-stu-id="60fb5-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="60fb5-107">Per prima cosa, configurare la destinazione del progetto in base a [Unity](#unity) e ai consigli non [reali](#unreal) , quindi seguire uno o più dei nostri scenari di porting:</span><span class="sxs-lookup"><span data-stu-id="60fb5-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="60fb5-108">HoloLens (1a generazione) a HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="60fb5-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="60fb5-109">Visori VR di Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="60fb5-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="60fb5-110">App SteamVR</span><span class="sxs-lookup"><span data-stu-id="60fb5-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="60fb5-111">app UWP 2D</span><span class="sxs-lookup"><span data-stu-id="60fb5-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="60fb5-112">Destinazioni progetto consigliate</span><span class="sxs-lookup"><span data-stu-id="60fb5-112">Recommended project targets</span></span>

<span data-ttu-id="60fb5-113">È importante lasciare aggiornati i progetti, sia che si tratti di trasferire un'app a un altro dispositivo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="60fb5-113">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="60fb5-114">Per le raccomandazioni correnti, fare riferimento alle risorse basate su motore elencate di seguito.</span><span class="sxs-lookup"><span data-stu-id="60fb5-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="60fb5-115">Unity</span><span class="sxs-lookup"><span data-stu-id="60fb5-115">Unity</span></span>

<span data-ttu-id="60fb5-116">L'attuale Consiglio per lo sviluppo di Unity con realtà mista è **unity 2019 LTS che usa il pacchetto XR legacy**.</span><span class="sxs-lookup"><span data-stu-id="60fb5-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="60fb5-117">Se il progetto usa il Toolkit per la realtà mista, verificare che sia disponibile la versione più recente, che attualmente è **MRTK-unity 2,5**.</span><span class="sxs-lookup"><span data-stu-id="60fb5-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="60fb5-118">Sebbene l'SDK di XR sia disponibile con questa versione di Unity, gli ancoraggi spaziali di Azure non sono attualmente compatibili con questa configurazione.</span><span class="sxs-lookup"><span data-stu-id="60fb5-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="60fb5-119">Questa raccomandazione verrà aggiornata con una versione futura del pacchetto di ancoraggi spaziali di Azure per Unity.</span><span class="sxs-lookup"><span data-stu-id="60fb5-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span>
> 
> * <span data-ttu-id="60fb5-120">Se non sono necessari ancoraggi spaziali di Azure, è possibile [configurare il progetto Unity per XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) e iniziare [a usare MRTK e XR SDK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk).</span><span class="sxs-lookup"><span data-stu-id="60fb5-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk).</span></span>
> 
> * <span data-ttu-id="60fb5-121">Se attualmente si usa l'SDK XR nel progetto e si vogliono usare gli ancoraggi spaziali di Azure, disinstallare XR SDK e reinstallare il pacchetto XR legacy per ripristinare le impostazioni del progetto.</span><span class="sxs-lookup"><span data-stu-id="60fb5-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>

### <a name="unreal"></a><span data-ttu-id="60fb5-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="60fb5-122">Unreal</span></span>

<span data-ttu-id="60fb5-123">Il nostro Consiglio attuale per lo sviluppo non reale con realtà mista è **Unreal Engine 4,26**.</span><span class="sxs-lookup"><span data-stu-id="60fb5-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="60fb5-124">Se il progetto usa gli strumenti UX reality Toolkit, assicurarsi di usare la versione più recente, attualmente **UXT 0,10**.</span><span class="sxs-lookup"><span data-stu-id="60fb5-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="60fb5-125">Scenari di porting</span><span class="sxs-lookup"><span data-stu-id="60fb5-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="60fb5-126">HoloLens (1st Gen) Unity Apps to HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="60fb5-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="60fb5-127">Se si dispone di un'applicazione HoloLens (1st Gen) Unity esistente che si desidera trasferire a un HoloLens 2, seguire le istruzioni contenute nell'articolo relativo al [porting di HoloLens](./porting-hl1-hl2.md).</span><span class="sxs-lookup"><span data-stu-id="60fb5-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="60fb5-128">Visori VR di Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="60fb5-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="60fb5-129">Se è stato compilato contenuto per altri dispositivi, ad esempio Oculus Rift o HP Reverb G2, sarà necessario ridestinare gli SDK VR specifici del fornitore e le API di mapping di input.</span><span class="sxs-lookup"><span data-stu-id="60fb5-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to retarget vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="60fb5-130">È possibile trovare informazioni per gli scenari Unity e Unreal porting nella [Guida alla portabilità delle app immersive](porting-guides.md).</span><span class="sxs-lookup"><span data-stu-id="60fb5-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="60fb5-131">Applicazioni SteamVR</span><span class="sxs-lookup"><span data-stu-id="60fb5-131">SteamVR applications</span></span>

<span data-ttu-id="60fb5-132">Per qualsiasi esperienza SteamVR che si vuole aggiornare per gli auricolari di realtà mista di Windows, vedere la [Guida all'aggiornamento di SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="60fb5-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="60fb5-133">applicazioni Windows universali 2D</span><span class="sxs-lookup"><span data-stu-id="60fb5-133">2D Universal Windows applications</span></span>

<span data-ttu-id="60fb5-134">Se si dispone di un'app UWP 2D esistente che si desidera trasferire a un auricolare o a un HoloLens per la realtà mista di Windows, seguire le istruzioni [per il porting di UWP 2D per la realtà mista di Windows](building-2d-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="60fb5-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>