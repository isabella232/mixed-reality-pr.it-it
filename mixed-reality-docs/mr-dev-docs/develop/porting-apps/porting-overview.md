---
title: Panoramica della conversione
description: Panoramica delle varie opzioni di porting per portare le applicazioni esistenti in Realtà mista per HoloLens e VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: porting, unity, middleware, motore, UWP, Win32
ms.openlocfilehash: 9b056bd81a725fea23c1e7f3bfcd9844680086c6
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600500"
---
# <a name="porting-overview"></a><span data-ttu-id="f933e-104">Panoramica della conversione</span><span class="sxs-lookup"><span data-stu-id="f933e-104">Porting overview</span></span>

<span data-ttu-id="f933e-105">Quando si tratta di eseguire il porting o l'aggiornamento dei progetti esistenti per la realtà mista, il percorso di porting dipende dal fatto che l'app sia compilata con Unity o Unreal Engine e che sia destinata a HoloLens (prima generazione) o HoloLens 2 o a SteamVR.</span><span class="sxs-lookup"><span data-stu-id="f933e-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="f933e-106">Questa pagina di panoramica contiene le raccomandazioni correnti per ogni piattaforma e dispositivo. Assicurarsi di controllare di nuovo perché questi processi cambiano sempre.</span><span class="sxs-lookup"><span data-stu-id="f933e-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="f933e-107">Prima di tutto, configurare la destinazione del progetto in base alle raccomandazioni [di Unity](#unity) e [Unreal,](#unreal) quindi seguire uno o più scenari di porting:</span><span class="sxs-lookup"><span data-stu-id="f933e-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="f933e-108">HoloLens (prima generazione) per HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f933e-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="f933e-109">Visori VR di Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f933e-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="f933e-110">App di SteamVR</span><span class="sxs-lookup"><span data-stu-id="f933e-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="f933e-111">App UWP 2D</span><span class="sxs-lookup"><span data-stu-id="f933e-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="f933e-112">Destinazioni del progetto consigliate</span><span class="sxs-lookup"><span data-stu-id="f933e-112">Recommended project targets</span></span>

<span data-ttu-id="f933e-113">È importante mantenere aggiornati i progetti, indipendentemente dal fatto che si trasla un'app in un altro dispositivo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="f933e-113">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="f933e-114">Per le raccomandazioni correnti, vedere le risorse basate sul motore elencate di seguito.</span><span class="sxs-lookup"><span data-stu-id="f933e-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="f933e-115">Unity</span><span class="sxs-lookup"><span data-stu-id="f933e-115">Unity</span></span>

<span data-ttu-id="f933e-116">La raccomandazione corrente per lo sviluppo di Unity con Realtà mista **è Unity 2019 LTS usando il pacchetto XR legacy.**</span><span class="sxs-lookup"><span data-stu-id="f933e-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="f933e-117">Se il progetto usa Mixed Reality Toolkit, verificare di avere la versione più recente, attualmente **MRTK-Unity 2.5.**</span><span class="sxs-lookup"><span data-stu-id="f933e-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="f933e-118">Anche se XR SDK è disponibile con questa versione di Unity, Ancoraggi nello spazio di Azure non è attualmente compatibile con questa configurazione.</span><span class="sxs-lookup"><span data-stu-id="f933e-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="f933e-119">Questa raccomandazione verrà aggiornata con una versione futura del pacchetto Ancoraggi nello stato di Azure per Unity.</span><span class="sxs-lookup"><span data-stu-id="f933e-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span>
> 
> * <span data-ttu-id="f933e-120">Se non sono necessari ancoraggi nello stato di Azure, è possibile configurare il progetto Unity per [XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) e iniziare a usare [MRTK e XR SDK.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk)</span><span class="sxs-lookup"><span data-stu-id="f933e-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk).</span></span>
> 
> * <span data-ttu-id="f933e-121">Se si usa XR SDK nel progetto e si vuole usare Ancoraggi nello spaziali di Azure, disinstallare XR SDK e reinstallare il pacchetto XR legacy per ripristinare le impostazioni del progetto.</span><span class="sxs-lookup"><span data-stu-id="f933e-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>

### <a name="unreal"></a><span data-ttu-id="f933e-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="f933e-122">Unreal</span></span>

<span data-ttu-id="f933e-123">La raccomandazione corrente per lo sviluppo unreal con realtà mista **è Unreal Engine 4.26.**</span><span class="sxs-lookup"><span data-stu-id="f933e-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="f933e-124">Se il progetto usa Mixed Reality Toolkit UX Tools, assicurarsi di usare la versione più recente, attualmente **UXT 0.10.**</span><span class="sxs-lookup"><span data-stu-id="f933e-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="f933e-125">Scenari di porting</span><span class="sxs-lookup"><span data-stu-id="f933e-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="f933e-126">App Unity holoLens (prima generazione) da HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f933e-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="f933e-127">Se si dispone di un'applicazione Unity HoloLens (prima generazione) che si desidera convertire in un HoloLens 2, seguire le istruzioni nell'articolo sulla portabilità di [HoloLens.](./porting-hl1-hl2.md)</span><span class="sxs-lookup"><span data-stu-id="f933e-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="f933e-128">Visori VR di Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f933e-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="f933e-129">Se hai creato contenuto per altri dispositivi, ad esempio Oculus Rift o HP Reverb G2, dovrai ridestinare gli SDK VR specifici del fornitore e potenzialmente le API di mapping dell'input.</span><span class="sxs-lookup"><span data-stu-id="f933e-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to retarget vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="f933e-130">Le informazioni per gli scenari di porting Unity e Unreal sono disponibili nella guida alla porting delle [app immersive.](porting-guides.md)</span><span class="sxs-lookup"><span data-stu-id="f933e-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="f933e-131">Applicazioni di SteamVR</span><span class="sxs-lookup"><span data-stu-id="f933e-131">SteamVR applications</span></span>

<span data-ttu-id="f933e-132">Per tutte le esperienze di SteamVR che si vuole aggiornare per Windows Mixed Reality visori, vedere la guida all'aggiornamento di [SteamVR.](updating-your-steamvr-application-for-windows-mixed-reality.md)</span><span class="sxs-lookup"><span data-stu-id="f933e-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="f933e-133">Applicazioni 2D universali di Windows</span><span class="sxs-lookup"><span data-stu-id="f933e-133">2D Universal Windows applications</span></span>

<span data-ttu-id="f933e-134">Se si ha un'app UWP 2D esistente che si desidera convertire in un visore vr immersivo Windows Mixed Reality o HoloLens, seguire le istruzioni per il porting delle app [UWP 2D](building-2d-apps.md) per Windows Mixed Reality video.</span><span class="sxs-lookup"><span data-stu-id="f933e-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>