---
title: Uso del plug-in Windows XR
description: Informazioni su come configurare i progetti Unity con e senza MRTK usando il supporto di Windows XR.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realtà mista, sviluppo, introduzione, nuovo progetto, Windows Mixed Reality, UWP, XR, prestazioni, legacy, mrtk, windows
ms.openlocfilehash: c9733d58236d97db370ce4f58dc1760bdf4eda86
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110231"
---
# <a name="using-windows-xr-plugin"></a><span data-ttu-id="d3d9e-104">Uso del plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="d3d9e-104">Using Windows XR plugin</span></span>

<span data-ttu-id="d3d9e-105">Per gli sviluppatori che hanno come destinazione Unity 2020, il plug-in Windows XR consente l'accesso alle funzionalità di realtà mista HoloLens 2 e Windows Mixed Reality visori VR.</span><span class="sxs-lookup"><span data-stu-id="d3d9e-105">For developers targeting Unity 2020, the Windows XR plugin enables access to mixed reality features on HoloLens 2 and Windows Mixed Reality headsets.</span></span>  <span data-ttu-id="d3d9e-106">Questo plug-in è supportato anche in Unity 2019, anche se esistono alcune incompatibilità note con Ancoraggi nello stato di Azure quando si usa questo plug-in in tale versione.</span><span class="sxs-lookup"><span data-stu-id="d3d9e-106">This plugin is also supported on Unity 2019, although there are some known incompatibilities with Azure Spatial Anchors when using this plugin on that version.</span></span>

<span data-ttu-id="d3d9e-107">Anche se Microsoft e la community hanno creato strumenti opensource come [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) che configurano automaticamente l'ambiente WMR, molti sviluppatori vogliono creare le proprie esperienze da zero.</span><span class="sxs-lookup"><span data-stu-id="d3d9e-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="d3d9e-108">La documentazione seguente illustra come configurare correttamente un progetto per lo sviluppo di realtà mista indipendentemente dal fatto che si utilizzi o meno MRTK.</span><span class="sxs-lookup"><span data-stu-id="d3d9e-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="d3d9e-109">Le impostazioni che è necessario modificare sono suddivise in due categorie: impostazioni per progetto e impostazioni per scena.</span><span class="sxs-lookup"><span data-stu-id="d3d9e-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="d3d9e-110">Configurazione del progetto con MRTK</span><span class="sxs-lookup"><span data-stu-id="d3d9e-110">Setting up your project with MRTK</span></span>

<span data-ttu-id="d3d9e-111">MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali.</span><span class="sxs-lookup"><span data-stu-id="d3d9e-111">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="d3d9e-112">MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="d3d9e-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="d3d9e-113">Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.</span><span class="sxs-lookup"><span data-stu-id="d3d9e-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d3d9e-114">Provare le esercitazioni su MRTK</span><span class="sxs-lookup"><span data-stu-id="d3d9e-114">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=winxr)

<span data-ttu-id="d3d9e-115">Per altri dettagli sulle funzionalità, vedere la documentazione di [MRTK.](/windows/mixed-reality/mrtk-unity)</span><span class="sxs-lookup"><span data-stu-id="d3d9e-115">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="d3d9e-116">Configurazione manuale senza MRTK</span><span class="sxs-lookup"><span data-stu-id="d3d9e-116">Manual setup without MRTK</span></span>

<span data-ttu-id="d3d9e-117">Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="d3d9e-117">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

<span data-ttu-id="d3d9e-119">Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="d3d9e-119">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="d3d9e-120">Selezionare **Impostazioni > file...**</span><span class="sxs-lookup"><span data-stu-id="d3d9e-120">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="d3d9e-121">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**</span><span class="sxs-lookup"><span data-stu-id="d3d9e-121">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="d3d9e-122">Impostare **Architecture (Architettura)** **su ARM 64**</span><span class="sxs-lookup"><span data-stu-id="d3d9e-122">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="d3d9e-123">Impostare **Dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="d3d9e-123">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="d3d9e-124">Impostare **Tipo di compilazione** su **D3D**</span><span class="sxs-lookup"><span data-stu-id="d3d9e-124">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="d3d9e-125">Impostare **UWP SDK su** Latest installed **(Versione più recente installata)**</span><span class="sxs-lookup"><span data-stu-id="d3d9e-125">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="d3d9e-126">Impostare **Build configuration (Configurazione build)** **su Release (Versione)** perché sono presenti problemi di prestazioni noti con Debug</span><span class="sxs-lookup"><span data-stu-id="d3d9e-126">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](images/wmr-config-img-4.png)

<span data-ttu-id="d3d9e-128">Dopo aver impostato la piattaforma, è necessario invii a Unity una visualizzazione [immersiva](../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata:</span><span class="sxs-lookup"><span data-stu-id="d3d9e-128">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="d3d9e-129">Nell'editor di Unity passare a **Edit > Project settings (Modifica impostazioni progetto)** e selezionare **XR Plugin Management (Gestione plug-in XR)**</span><span class="sxs-lookup"><span data-stu-id="d3d9e-129">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="d3d9e-130">Selezionare **Install XR Plugin Management (Installa gestione plug-in XR)**</span><span class="sxs-lookup"><span data-stu-id="d3d9e-130">Select **Install XR Plugin Management**</span></span>

![Screenshot della finestra Project Settings (Impostazioni progetto) aperta nell'editor di Unity con la gestione del plug-in XR evidenziata](images/wmr-config-img-5.png)

3. <span data-ttu-id="d3d9e-132">Selezionare Initialize XR on Startup (Inizializza **XR all'avvio)** **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="d3d9e-132">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Screenshot della finestra Delle impostazioni del progetto aperta nell'editor di Unity con la gestione del plug-in XR evidenziata](images/wmr-config-img-7.png)

4. <span data-ttu-id="d3d9e-134">Espandere la **sezione XR Plug-in Management (Gestione plug-in XR)** e selezionare **la scheda Univeral Windows Platform Settings (Impostazioni piattaforma Windows univeral)**</span><span class="sxs-lookup"><span data-stu-id="d3d9e-134">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="d3d9e-135">Se si usa Unity 2020 o versione successiva, verranno visualizzati i controlli **OpenXR** **o Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="d3d9e-135">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="d3d9e-136">È possibile scegliere uno dei due runtime.</span><span class="sxs-lookup"><span data-stu-id="d3d9e-136">You can choose either runtime.</span></span>  <span data-ttu-id="d3d9e-137">Se si sviluppa specificamente per il HoloLens 2 o HP Reverb G2 e si decide di provare **OpenXR,** selezionare la casella OpenXR ed esaminare la guida Uso del plug-in [OpenXR](openxr-getting-started.md) di Realtà mista per Unity per configurare correttamente questi dispositivi prima di tornare a questa esercitazione</span><span class="sxs-lookup"><span data-stu-id="d3d9e-137">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="d3d9e-138">A partire da Unity 2020 LTS, Microsoft sta iniziando lo sviluppo con OpenXR.</span><span class="sxs-lookup"><span data-stu-id="d3d9e-138">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="d3d9e-139">Durante la migrazione a questo percorso, in Unity 2021.1 il plug-in Windows XR verrà deprecato e rimosso nella versione 2021.2 rendendo OpenXR l'unico percorso supportato.</span><span class="sxs-lookup"><span data-stu-id="d3d9e-139">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="d3d9e-140">Per altre informazioni, vedere [Using the Mixed Reality OpenXR plugin (Uso del plug-in OpenXR di Realtà mista).](openxr-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="d3d9e-140">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="d3d9e-141">Se si decide di scegliere il **plug-Windows Mixed Reality,** selezionare tutte le caselle e impostare Modalità di invio **profondità** **su Depth 16 Bit (Profondità 16 bit)**</span><span class="sxs-lookup"><span data-stu-id="d3d9e-141">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Screenshot della finestra Project settings (Impostazioni progetto) aperta nell'editor di Unity con Windows Mixed Reality sezione evidenziata](images/wmr-config-img-8.png)