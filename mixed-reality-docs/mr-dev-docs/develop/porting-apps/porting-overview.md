---
title: Panoramica della conversione
description: Panoramica delle varie opzioni di porting per portare le applicazioni esistenti in Realtà mista per HoloLens e VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: porting, unity, middleware, motore, UWP, Win32
ms.openlocfilehash: 167559d69cc4e65f971a8970b56e41e6e3ca8b22
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042272"
---
# <a name="porting-overview"></a><span data-ttu-id="2a77b-104">Panoramica della conversione</span><span class="sxs-lookup"><span data-stu-id="2a77b-104">Porting overview</span></span>

<span data-ttu-id="2a77b-105">Quando si tratta di eseguire il porting o l'aggiornamento dei progetti esistenti per la realtà mista, il percorso di porting dipende dal fatto che l'app sia compilata con Unity o Unreal Engine e che sia destinata a HoloLens (prima generazione) o HoloLens 2 o a SteamVR.</span><span class="sxs-lookup"><span data-stu-id="2a77b-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="2a77b-106">Questa pagina di panoramica contiene le raccomandazioni correnti per ogni piattaforma e dispositivo. Assicurarsi di controllare di nuovo perché questi processi cambiano sempre.</span><span class="sxs-lookup"><span data-stu-id="2a77b-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="2a77b-107">Prima di tutto, configurare la destinazione del progetto in base alle raccomandazioni [di Unity](#unity) e [Unreal,](#unreal) quindi seguire uno o più scenari di porting:</span><span class="sxs-lookup"><span data-stu-id="2a77b-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="2a77b-108">HoloLens (prima generazione) per HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2a77b-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="2a77b-109">Visori VR immersive</span><span class="sxs-lookup"><span data-stu-id="2a77b-109">Immersive VR headsets</span></span>](#immersive-vr-headsets)
- [<span data-ttu-id="2a77b-110">App UWP 2D</span><span class="sxs-lookup"><span data-stu-id="2a77b-110">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="2a77b-111">Destinazioni del progetto consigliate</span><span class="sxs-lookup"><span data-stu-id="2a77b-111">Recommended project targets</span></span>

<span data-ttu-id="2a77b-112">È importante mantenere aggiornati i progetti, indipendentemente dal fatto che si trasla un'app in un altro dispositivo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="2a77b-112">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="2a77b-113">Per le raccomandazioni correnti, vedere le risorse basate sul motore elencate di seguito.</span><span class="sxs-lookup"><span data-stu-id="2a77b-113">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="2a77b-114">Unity</span><span class="sxs-lookup"><span data-stu-id="2a77b-114">Unity</span></span>

<span data-ttu-id="2a77b-115">Per informazioni aggiornate sulle versioni [consigliate](../unity/choosing-unity-version.md) di Unity e MRTK, vedere la pagina Scelta di una versione di Unity.</span><span class="sxs-lookup"><span data-stu-id="2a77b-115">See the [Choosing a Unity version](../unity/choosing-unity-version.md) page for up-to-date guidance on the recommended Unity and MRTK versions.</span></span>

### <a name="unreal"></a><span data-ttu-id="2a77b-116">Unreal</span><span class="sxs-lookup"><span data-stu-id="2a77b-116">Unreal</span></span>

<span data-ttu-id="2a77b-117">Per informazioni aggiornate sulle versioni consigliate di Unreal e MRTK, vedere la pagina Configurazione del progetto [Unreal.](../unreal/unreal-project-setup.md)</span><span class="sxs-lookup"><span data-stu-id="2a77b-117">See the [Setting up your Unreal project](../unreal/unreal-project-setup.md) page for up-to-date guidance on the recommended Unreal and MRTK versions.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="2a77b-118">Scenari di porting</span><span class="sxs-lookup"><span data-stu-id="2a77b-118">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="2a77b-119">App Unity holoLens (prima generazione) da HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2a77b-119">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="2a77b-120">Se si dispone di un'applicazione Unity HoloLens (prima generazione) che si desidera convertire in un HoloLens 2, seguire le istruzioni nell'articolo sulla portabilità di [HoloLens.](./porting-hl1-hl2.md)</span><span class="sxs-lookup"><span data-stu-id="2a77b-120">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="immersive-vr-headsets"></a><span data-ttu-id="2a77b-121">Visori VR immersive</span><span class="sxs-lookup"><span data-stu-id="2a77b-121">Immersive VR headsets</span></span>

<span data-ttu-id="2a77b-122">Se hai creato contenuto per altri dispositivi VR, dovrai ridestinare gli SDK VR specifici del fornitore e le API di mapping degli input potenzialmente.</span><span class="sxs-lookup"><span data-stu-id="2a77b-122">If you've built content for other VR devices, you'll need to retarget any vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="2a77b-123">Le informazioni per gli scenari di porting Unity e Unreal sono disponibili nella guida alla porting delle [app immersive.](porting-guides.md)</span><span class="sxs-lookup"><span data-stu-id="2a77b-123">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

<span data-ttu-id="2a77b-124">Per le esperienze di SteamVR da aggiornare per Windows Mixed Reality visori, vedere la guida all'aggiornamento [di SteamVR.](updating-your-steamvr-application-for-windows-mixed-reality.md)</span><span class="sxs-lookup"><span data-stu-id="2a77b-124">For SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="2a77b-125">Applicazioni 2D universali di Windows</span><span class="sxs-lookup"><span data-stu-id="2a77b-125">2D Universal Windows applications</span></span>

<span data-ttu-id="2a77b-126">Se si ha un'app UWP 2D esistente che si desidera convertire in un visore vr immersivo Windows Mixed Reality o HoloLens, seguire le istruzioni per il porting delle app [UWP 2D](building-2d-apps.md) per Windows Mixed Reality video.</span><span class="sxs-lookup"><span data-stu-id="2a77b-126">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>