---
title: Uso del supporto XR incorporato legacy
description: Informazioni su come configurare i progetti Unity con e senza MRTK usando il supporto XR incorporato legacy.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realtà mista, sviluppo, introduzione, nuovo progetto, Windows Mixed Reality, UWP, XR, prestazioni, legacy, mrtk
ms.openlocfilehash: b5faa48ec913c5095b12361318729b6f14276f30
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743505"
---
# <a name="using-legacy-built-in-xr-support"></a><span data-ttu-id="2544d-104">Uso del supporto XR incorporato legacy</span><span class="sxs-lookup"><span data-stu-id="2544d-104">Using Legacy built-in XR support</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="2544d-105">Configurazione del progetto con MRTK</span><span class="sxs-lookup"><span data-stu-id="2544d-105">Setting up your project with MRTK</span></span>

<span data-ttu-id="2544d-106">MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali.</span><span class="sxs-lookup"><span data-stu-id="2544d-106">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="2544d-107">MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="2544d-107">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="2544d-108">Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.</span><span class="sxs-lookup"><span data-stu-id="2544d-108">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2544d-109">Provare le esercitazioni su MRTK</span><span class="sxs-lookup"><span data-stu-id="2544d-109">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=wsa)

<span data-ttu-id="2544d-110">Per altri dettagli sulle funzionalità, vedere la documentazione di [MRTK.](/windows/mixed-reality/mrtk-unity)</span><span class="sxs-lookup"><span data-stu-id="2544d-110">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="2544d-111">Configurazione manuale senza MRTK</span><span class="sxs-lookup"><span data-stu-id="2544d-111">Manual setup without MRTK</span></span>

<span data-ttu-id="2544d-112">Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma PC autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="2544d-112">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

<span data-ttu-id="2544d-114">Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="2544d-114">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="2544d-115">Selezionare **Impostazioni > file...**</span><span class="sxs-lookup"><span data-stu-id="2544d-115">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="2544d-116">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**</span><span class="sxs-lookup"><span data-stu-id="2544d-116">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="2544d-117">Impostare **Architecture (Architettura)** **su ARM 64**</span><span class="sxs-lookup"><span data-stu-id="2544d-117">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="2544d-118">Impostare **Dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="2544d-118">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="2544d-119">Impostare **Tipo di compilazione** su **D3D**</span><span class="sxs-lookup"><span data-stu-id="2544d-119">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="2544d-120">Impostare **UWP SDK su** Latest installed **(Versione più recente installata)**</span><span class="sxs-lookup"><span data-stu-id="2544d-120">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="2544d-121">Impostare **La configurazione della build** su **Rilascio** perché sono presenti problemi di prestazioni noti con debug</span><span class="sxs-lookup"><span data-stu-id="2544d-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](images/wmr-config-img-4.png)

<span data-ttu-id="2544d-123">Dopo aver impostato la piattaforma, è necessario invii a Unity una visualizzazione [immersiva](../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.</span><span class="sxs-lookup"><span data-stu-id="2544d-123">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="2544d-124">XR legacy è deprecato in Unity 2019 e rimosso in Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="2544d-124">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="2544d-125">Aprire **Player Settings (Impostazioni lettore)** da Build Settings **(Impostazioni compilazione) ed** espandere il **gruppo XR Settings (Impostazioni XR)**</span><span class="sxs-lookup"><span data-stu-id="2544d-125">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="2544d-126">Nella sezione **XR Settings (Impostazioni XR)** selezionare **Virtual Reality Supported (Realtà virtuale supportata)** per aggiungere l'elenco Virtual Reality Devices (Dispositivi di realtà virtuale)</span><span class="sxs-lookup"><span data-stu-id="2544d-126">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="2544d-127">Impostare **Depth Format (Formato profondità)** su **Depth (Profondità) a 16 bit** e abilitare Depth Buffer Sharing **(Condivisione buffer di profondità)**</span><span class="sxs-lookup"><span data-stu-id="2544d-127">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="2544d-128">Impostare **La modalità di rendering stereo** su Istanza a passaggio **singolo**</span><span class="sxs-lookup"><span data-stu-id="2544d-128">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="2544d-129">Selezionare **WSA Holographic Remoting Supported** se si desidera usare holographic remoting</span><span class="sxs-lookup"><span data-stu-id="2544d-129">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Screenshot della finestra Project settings (Impostazioni progetto) aperta nell'editor di Unity con la sezione Player settings (Impostazioni lettore) evidenziata](images/wmr-config-img-9.png)