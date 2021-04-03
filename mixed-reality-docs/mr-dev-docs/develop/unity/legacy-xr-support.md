---
title: Uso del supporto di XR incorporato legacy
description: Informazioni su come configurare i progetti Unity con e senza MRTK usando il supporto integrato per la versione precedente di XR.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realtà mista, sviluppo, Guida introduttiva, nuovo progetto, realtà mista di Windows, UWP, XR, prestazioni, legacy, MRTK
ms.openlocfilehash: 09989b3b2b7fa1d351235a2cc9b885d4795dc2b6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088530"
---
# <a name="using-legacy-built-in-xr-support"></a><span data-ttu-id="1701d-104">Uso del supporto di XR incorporato legacy</span><span class="sxs-lookup"><span data-stu-id="1701d-104">Using Legacy built-in XR support</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="1701d-105">Impostazione del progetto con MRTK</span><span class="sxs-lookup"><span data-stu-id="1701d-105">Setting up your project with MRTK</span></span>

<span data-ttu-id="1701d-106">MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali.</span><span class="sxs-lookup"><span data-stu-id="1701d-106">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="1701d-107">MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="1701d-107">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="1701d-108">Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.</span><span class="sxs-lookup"><span data-stu-id="1701d-108">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1701d-109">Prova le nostre esercitazioni su MRTK</span><span class="sxs-lookup"><span data-stu-id="1701d-109">Try out our MRTK tutorials</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=wsa)

<span data-ttu-id="1701d-110">Per altri dettagli sulle funzionalità, vedere la [documentazione di MRTK](/windows/mixed-reality/mrtk-unity) .</span><span class="sxs-lookup"><span data-stu-id="1701d-110">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="1701d-111">Installazione manuale senza MRTK</span><span class="sxs-lookup"><span data-stu-id="1701d-111">Manual setup without MRTK</span></span>

<span data-ttu-id="1701d-112">Se la destinazione è Desktop VR, è consigliabile usare la piattaforma autonoma per PC selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="1701d-112">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra impostazioni di compilazione aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

<span data-ttu-id="1701d-114">Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="1701d-114">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="1701d-115">Seleziona **File > impostazioni di compilazione...**</span><span class="sxs-lookup"><span data-stu-id="1701d-115">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="1701d-116">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco piattaforma e selezionare **Switch Platform (Cambia piattaforma** )</span><span class="sxs-lookup"><span data-stu-id="1701d-116">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="1701d-117">Impostare l' **architettura** su **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="1701d-117">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="1701d-118">Impostare il **dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="1701d-118">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="1701d-119">Imposta **tipo di compilazione** su **D3D**</span><span class="sxs-lookup"><span data-stu-id="1701d-119">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="1701d-120">Impostare **UWP SDK** sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="1701d-120">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="1701d-121">Impostare la **configurazione della compilazione** su **Release** a causa di problemi noti relativi alle prestazioni con debug</span><span class="sxs-lookup"><span data-stu-id="1701d-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot della finestra impostazioni di compilazione aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](images/wmr-config-img-4.png)

<span data-ttu-id="1701d-123">Dopo aver impostato la piattaforma, è necessario consentire a Unity di creare una [visualizzazione immersiva](../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.</span><span class="sxs-lookup"><span data-stu-id="1701d-123">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="1701d-124">La versione precedente di XR è deprecata in Unity 2019 ed è stata rimossa in Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="1701d-124">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="1701d-125">Apri **Impostazioni lettore...** dalle **impostazioni di compilazione... ed espandere il gruppo di** **impostazioni di XR**</span><span class="sxs-lookup"><span data-stu-id="1701d-125">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="1701d-126">Nella sezione **impostazioni di XR** selezionare **realtà virtuale supportata** per aggiungere l'elenco dispositivi della realtà virtuale</span><span class="sxs-lookup"><span data-stu-id="1701d-126">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="1701d-127">Imposta la profondità del **formato** a **16 bit** e Abilita la **condivisione del buffer di profondità**</span><span class="sxs-lookup"><span data-stu-id="1701d-127">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="1701d-128">Impostare la **modalità di rendering stereo** su **istanza Single Pass**</span><span class="sxs-lookup"><span data-stu-id="1701d-128">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="1701d-129">Selezionare la **comunicazione remota per WSA olografica supportata** se si vuole usare la comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="1701d-129">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la sezione delle impostazioni del lettore evidenziata](images/wmr-config-img-9.png)