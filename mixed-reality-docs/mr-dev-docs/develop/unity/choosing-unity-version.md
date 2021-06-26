---
title: Scelta di una versione di Unity e di un plug-in XR
description: Rimanere aggiornati sulle raccomandazioni più recenti dei plug-in Unity e XR per lo sviluppo di applicazioni HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale, unity
ms.openlocfilehash: 646a0ec3b3b332b038509cba39caa085c1590c1a
ms.sourcegitcommit: 593e8f80297ac0b5eccb2488d3f333885eab9adf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112921426"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="0cb78-104">Scelta di una versione di Unity e di un plug-in XR</span><span class="sxs-lookup"><span data-stu-id="0cb78-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="0cb78-105">Anche se attualmente è consigliabile installare **Unity 2020.3 LTS** con il plug-in OpenXR di realtà mista più recente per lo sviluppo di realtà mista, è possibile compilare app anche con altre configurazioni di Unity.</span><span class="sxs-lookup"><span data-stu-id="0cb78-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="0cb78-106">Unity 2020.3 LTS (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="0cb78-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="0cb78-107">La configurazione di Unity consigliata di Microsoft per lo sviluppo HoloLens 2 e Windows Mixed Reality è **Unity 2020.3 LTS** con il plug-in OpenXR di Realtà mista più recente.</span><span class="sxs-lookup"><span data-stu-id="0cb78-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="0cb78-108">È NECESSARIO usare la patch unity versione 2020.3.8f1 o successiva per evitare problemi di prestazioni noti con le build precedenti della versione 2020.3.</span><span class="sxs-lookup"><span data-stu-id="0cb78-108">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0cb78-109">Unity 2020 non supporta la destinazione di HoloLens (prima generazione).</span><span class="sxs-lookup"><span data-stu-id="0cb78-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="0cb78-110">Questi visori rimangono supportati in **[Unity 2019 LTS](#unity-20194-lts)** con legacy built-in XR per l'intero ciclo di vita di Unity 2019 LTS fino a metà 2022.</span><span class="sxs-lookup"><span data-stu-id="0cb78-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>
>
> [!NOTE]
> <span data-ttu-id="0cb78-111">Alcuni pacchetti non sono ancora compatibili con progetti di realtà mista in Unity 2020 LTS:</span><span class="sxs-lookup"><span data-stu-id="0cb78-111">Some packages are not yet compatible with mixed reality projects in Unity 2020 LTS:</span></span>
> 
> * <span data-ttu-id="0cb78-112">La pipeline di rendering universale (URP) 10.5.0 o versione precedente presenta un problema di prestazioni noto HoloLens 2 dispositivi.</span><span class="sxs-lookup"><span data-stu-id="0cb78-112">The Universal Rendering Pipeline (URP) 10.5.0 or older has a known performance issue on HoloLens 2 devices.</span></span> <span data-ttu-id="0cb78-113">_(risolto nella versione URP successiva)_</span><span class="sxs-lookup"><span data-stu-id="0cb78-113">_(fixed in the next URP release)_</span></span>
> * <span data-ttu-id="0cb78-114">Rendering remoto di Azure non è ancora stata fornita una versione aggiornata che supporta Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="0cb78-114">Azure Remote Rendering has not yet shipped an updated release supporting Unity 2020.</span></span>
>
> <span data-ttu-id="0cb78-115">Se il progetto Unity usa universal rendering pipeline o Rendering remoto di Azure, è consigliabile evitare di aggiornare il progetto a Unity 2020 fino a quando non sono disponibili pacchetti aggiornati.</span><span class="sxs-lookup"><span data-stu-id="0cb78-115">If your Unity project uses the Universal Rendering Pipeline or Azure Remote Rendering, we recommend holding off on upgrading your project to Unity 2020 until updated packages are available.</span></span>

<span data-ttu-id="0cb78-116">Il modo migliore per installare e gestire Unity è tramite <a href="https://unity3d.com/get-unity/download" target="_blank">l'hub unity.</a></span><span class="sxs-lookup"><span data-stu-id="0cb78-116">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span></span> <span data-ttu-id="0cb78-117">Al termine dell'installazione, aprire Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="0cb78-117">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="0cb78-118">Selezionare la **scheda Installazioni** e scegliere **AGGIUNGI**</span><span class="sxs-lookup"><span data-stu-id="0cb78-118">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="0cb78-119">Selezionare Unity 2020.3 LTS e fare clic su **Avanti**</span><span class="sxs-lookup"><span data-stu-id="0cb78-119">Select Unity 2020.3 LTS and click **Next**</span></span>

![Unity hub instal new version](images/unity-hub-img-01.png)

3. <span data-ttu-id="0cb78-121">Controllare i componenti seguenti in **"Piattaforme"**</span><span class="sxs-lookup"><span data-stu-id="0cb78-121">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="0cb78-122">**piattaforma UWP (Universal Windows Platform) di compilazione**</span><span class="sxs-lookup"><span data-stu-id="0cb78-122">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="0cb78-123">**Supporto per la compilazione di Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="0cb78-123">**Windows Build Support (IL2CPP)**</span></span>

![Opzione supporto piattaforma UWP (Universal Windows Platform) compilazione di Unity](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="0cb78-125">Se Unity è stato installato senza queste opzioni, è possibile aggiungerle tramite il menu **"Aggiungi moduli"** in Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="0cb78-125">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Opzione supporto compilazione Di Unity per Windows](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="0cb78-127">Uso del plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="0cb78-127">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="0cb78-128">Sebbene sia consigliabile usare OpenXR per tutti i nuovi progetti, Unity 2020.3 LTS supporta anche il plug-in [Windows XR.](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)</span><span class="sxs-lookup"><span data-stu-id="0cb78-128">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr).</span></span> <span data-ttu-id="0cb78-129">Questo plug-in è completamente supportato, anche se non riceverà nuove funzionalità, ad esempio il supporto di AR Foundation 4.0.</span><span class="sxs-lookup"><span data-stu-id="0cb78-129">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="0cb78-130">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="0cb78-130">Unity 2019.4 LTS</span></span>

<span data-ttu-id="0cb78-131">Se è necessario usare Unity 2019, è possibile usare **Unity 2019 LTS con XR incorporato legacy.**</span><span class="sxs-lookup"><span data-stu-id="0cb78-131">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="0cb78-132">Per iniziare a usare Legacy Built-in XR in Unity 2019.4 LTS, fare clic qui:</span><span class="sxs-lookup"><span data-stu-id="0cb78-132">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0cb78-133">Configurare la versione XR incorporata legacy</span><span class="sxs-lookup"><span data-stu-id="0cb78-133">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="0cb78-134">Unity ha deprecato il supporto XR incorporato legacy a data di Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="0cb78-134">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="0cb78-135">Anche se Unity 2019 offre un nuovo framework plug-in XR, Microsoft attualmente non consiglia questo percorso in Unity 2019 a causa delle incompatibilità di Ancoraggi nello stato di Azure con AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="0cb78-135">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="0cb78-136">In Unity 2020, Ancoraggi nello spaziali di Azure è supportato all'interno del framework plug-in XR.</span><span class="sxs-lookup"><span data-stu-id="0cb78-136">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="0cb78-137">Se si sviluppano app per HoloLens (prima generazione), questi visori rimangono supportati in Unity 2019 LTS con XR legacy incorporato per l'intero ciclo di vita di Unity 2019 LTS fino alla metà del 2022.</span><span class="sxs-lookup"><span data-stu-id="0cb78-137">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20211"></a><span data-ttu-id="0cb78-138">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="0cb78-138">Unity 2021.1</span></span>

<span data-ttu-id="0cb78-139">Se si provano le prime build **di Unity 2021.1,** è consigliabile passare al **plug-in OpenXR,** perché il plug-in Windows XR è deprecato.</span><span class="sxs-lookup"><span data-stu-id="0cb78-139">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="0cb78-140">A partire da Unity 2021.2, il plug-in OpenXR sarà l'unico percorso per lo sviluppo di realtà mista, perché il plug-in Windows XR non sarà più supportato.</span><span class="sxs-lookup"><span data-stu-id="0cb78-140">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="0cb78-141">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="0cb78-141">Unity 2018.4 LTS</span></span>

<span data-ttu-id="0cb78-142">Se si ha già un progetto che usa Unity 2018.4 LTS, il motore unity continuerà a essere supportato per 2 anni dopo il rilascio.</span><span class="sxs-lookup"><span data-stu-id="0cb78-142">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="0cb78-143">Unity 2018 LTS raggiungerà la fine del servizio nella primavera del 2021.</span><span class="sxs-lookup"><span data-stu-id="0cb78-143">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
