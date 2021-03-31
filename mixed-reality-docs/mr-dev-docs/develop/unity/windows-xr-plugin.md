---
title: Uso del plug-in Windows XR
description: Informazioni su come configurare i progetti Unity con e senza MRTK con il supporto di Windows XR.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realtà mista, sviluppo, Guida introduttiva, nuovo progetto, realtà mista di Windows, UWP, XR, prestazioni, legacy, MRTK, Windows
ms.openlocfilehash: 24da4b5116b926cfd5eda12db6eedee2f9e85621
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938121"
---
# <a name="using-windows-xr-plugin"></a><span data-ttu-id="338de-104">Uso del plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="338de-104">Using Windows XR plugin</span></span>

<span data-ttu-id="338de-105">Per gli sviluppatori che hanno come destinazione Unity 2020, il plug-in Windows XR consente l'accesso a funzionalità di realtà mista in HoloLens 2 e Windows Mixed Reality Headset.</span><span class="sxs-lookup"><span data-stu-id="338de-105">For developers targeting Unity 2020, the Windows XR plugin enables access to mixed reality features on HoloLens 2 and Windows Mixed Reality headsets.</span></span>  <span data-ttu-id="338de-106">Questo plug-in è supportato anche in Unity 2019, sebbene ci siano alcune incompatibilità note con i Anchor spaziali di Azure quando si usa questo plug-in in questa versione.</span><span class="sxs-lookup"><span data-stu-id="338de-106">This plugin is also supported on Unity 2019, although there are some known incompatibilities with Azure Spatial Anchors when using this plugin on that version.</span></span>

<span data-ttu-id="338de-107">Microsoft e la community hanno creato strumenti opensource come il Toolkit di [realtà mista (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) che configurerà automaticamente l'ambiente WMR, molti sviluppatori desiderano creare le proprie esperienze da zero.</span><span class="sxs-lookup"><span data-stu-id="338de-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="338de-108">Nella documentazione seguente viene illustrato come configurare correttamente un progetto per lo sviluppo di realtà mista se si utilizza MRTK o no.</span><span class="sxs-lookup"><span data-stu-id="338de-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="338de-109">Le impostazioni che è necessario modificare sono suddivise in due categorie: impostazioni per progetto e impostazioni per scena.</span><span class="sxs-lookup"><span data-stu-id="338de-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="338de-110">Impostazione del progetto con MRTK</span><span class="sxs-lookup"><span data-stu-id="338de-110">Setting up your project with MRTK</span></span>

<span data-ttu-id="338de-111">MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali.</span><span class="sxs-lookup"><span data-stu-id="338de-111">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="338de-112">MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="338de-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="338de-113">Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.</span><span class="sxs-lookup"><span data-stu-id="338de-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="338de-114">Prova le nostre esercitazioni su MRTK</span><span class="sxs-lookup"><span data-stu-id="338de-114">Try out our MRTK tutorials</span></span>](tutorials/mr-learning-base-01.md)

<span data-ttu-id="338de-115">Per altri dettagli sulle funzionalità, vedere la [documentazione di MRTK](/windows/mixed-reality/mrtk-unity) .</span><span class="sxs-lookup"><span data-stu-id="338de-115">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="338de-116">Installazione manuale senza MRTK</span><span class="sxs-lookup"><span data-stu-id="338de-116">Manual setup without MRTK</span></span>

<span data-ttu-id="338de-117">Se la destinazione è Desktop VR, è consigliabile usare la piattaforma autonoma per PC selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="338de-117">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra impostazioni di compilazione aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

<span data-ttu-id="338de-119">Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="338de-119">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="338de-120">Seleziona **File > impostazioni di compilazione...**</span><span class="sxs-lookup"><span data-stu-id="338de-120">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="338de-121">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco piattaforma e selezionare **Switch Platform (Cambia piattaforma** )</span><span class="sxs-lookup"><span data-stu-id="338de-121">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="338de-122">Impostare l' **architettura** su **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="338de-122">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="338de-123">Impostare il **dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="338de-123">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="338de-124">Imposta **tipo di compilazione** su **D3D**</span><span class="sxs-lookup"><span data-stu-id="338de-124">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="338de-125">Impostare **UWP SDK** sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="338de-125">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="338de-126">Impostare la **configurazione della compilazione** su **Release** a causa di problemi noti relativi alle prestazioni con debug</span><span class="sxs-lookup"><span data-stu-id="338de-126">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot della finestra impostazioni di compilazione aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](images/wmr-config-img-4.png)

<span data-ttu-id="338de-128">Dopo aver impostato la piattaforma, è necessario consentire a Unity di creare una [visualizzazione immersiva](../../design/app-views.md) invece di una visualizzazione 2D quando viene esportata:</span><span class="sxs-lookup"><span data-stu-id="338de-128">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="338de-129">Nell'editor di Unity passare a **Edit > Settings Project** e selezionare **XR plugin Management**</span><span class="sxs-lookup"><span data-stu-id="338de-129">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="338de-130">Selezionare **Install XR plugin Management**</span><span class="sxs-lookup"><span data-stu-id="338de-130">Select **Install XR Plugin Management**</span></span>

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la gestione dei plug-in XR evidenziata](images/wmr-config-img-5.png)

3. <span data-ttu-id="338de-132">Selezionare **Inizializza XR all'avvio** e **realtà mista di Windows**</span><span class="sxs-lookup"><span data-stu-id="338de-132">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la gestione dei plug-in XR evidenziata](images/wmr-config-img-7.png)

4. <span data-ttu-id="338de-134">Espandere la sezione **Gestione plug-in XR** e selezionare la scheda **impostazioni della piattaforma Windows Univeral**</span><span class="sxs-lookup"><span data-stu-id="338de-134">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="338de-135">Se si usa Unity 2020 o versioni successive, verranno visualizzate le opzioni per controllare **OpenXR** o la **realtà mista di Windows**.</span><span class="sxs-lookup"><span data-stu-id="338de-135">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="338de-136">È possibile scegliere Runtime.</span><span class="sxs-lookup"><span data-stu-id="338de-136">You can choose either runtime.</span></span>  <span data-ttu-id="338de-137">Se si sta sviluppando in modo specifico per HoloLens 2 o HP Reverb G2 e si decide di provare il **OpenXR**, selezionare la casella OpenXR ed esaminare la Guida all' [uso del plug-in realtà mista OpenXR per Unity](openxr-getting-started.md) per configurarlo correttamente per questi dispositivi prima di tornare a questa esercitazione</span><span class="sxs-lookup"><span data-stu-id="338de-137">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="338de-138">A partire da Unity 2020 LTS, Microsoft abbraccia lo sviluppo con OpenXR.</span><span class="sxs-lookup"><span data-stu-id="338de-138">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="338de-139">Quando si esegue la migrazione a questo percorso, in Unity 2021,1 il plug-in Windows XR verrà deprecato e rimosso in 2021,2 rendendo OpenXR l'unico percorso supportato.</span><span class="sxs-lookup"><span data-stu-id="338de-139">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="338de-140">Altre informazioni sono disponibili in [uso del plug-in OpenXR per la realtà mista](openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="338de-140">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="338de-141">Se si decide di scegliere il plug-in per la **realtà mista di Windows** , selezionare tutte le caselle e impostare la **modalità di invio profondità** su **profondità a 16 bit**</span><span class="sxs-lookup"><span data-stu-id="338de-141">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la sezione realtà mista di Windows evidenziata](images/wmr-config-img-8.png)
