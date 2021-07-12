---
title: Scelta di una versione di Unity e di un plug-in XR
description: Rimanere aggiornati sulle raccomandazioni più recenti dei plug-in Unity e XR per lo HoloLens di applicazioni.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale, unity
ms.openlocfilehash: c69576e991f3fe32ae69fce10069ecdae65b3f9a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603682"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="4fd8f-104">Scelta di una versione di Unity e di un plug-in XR</span><span class="sxs-lookup"><span data-stu-id="4fd8f-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="4fd8f-105">Anche se attualmente è consigliabile installare **Unity 2020.3 LTS** con il plug-in OpenXR di realtà mista più recente per lo sviluppo di realtà mista, è possibile compilare app anche con altre configurazioni di Unity.</span><span class="sxs-lookup"><span data-stu-id="4fd8f-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="4fd8f-106">Unity 2020.3 LTS (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="4fd8f-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="4fd8f-107">La configurazione corrente consigliata di Microsoft per lo sviluppo HoloLens 2 e Windows Mixed Reality è **Unity 2020.3 LTS** con il plug-in OpenXR di realtà mista più recente.</span><span class="sxs-lookup"><span data-stu-id="4fd8f-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="4fd8f-108">È **necessario** usare la patch unity versione 2020.3.8f1 o successiva per evitare problemi di prestazioni noti con le build precedenti della versione 2020.3.</span><span class="sxs-lookup"><span data-stu-id="4fd8f-108">You **must** use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4fd8f-109">Unity 2020 non supporta la destinazione HoloLens (prima generazione).</span><span class="sxs-lookup"><span data-stu-id="4fd8f-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="4fd8f-110">Questi visori rimangono supportati in **[Unity 2019 LTS](#unity-20194-lts)** con legacy built-in XR per l'intero ciclo di vita di Unity 2019 LTS fino a metà 2022.</span><span class="sxs-lookup"><span data-stu-id="4fd8f-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

<span data-ttu-id="4fd8f-111">Il modo migliore per installare e gestire Unity è tramite **l'hub unity:**</span><span class="sxs-lookup"><span data-stu-id="4fd8f-111">The best way to install and manage Unity is through the **Unity Hub**:</span></span>

1. <span data-ttu-id="4fd8f-112">Installare <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub**</a>.</span><span class="sxs-lookup"><span data-stu-id="4fd8f-112">Install <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub**</a>.</span></span>
2. <span data-ttu-id="4fd8f-113">Selezionare la **scheda Installazioni** e scegliere **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="4fd8f-113">Select the **Installs** tab and choose **Add**.</span></span>
3. <span data-ttu-id="4fd8f-114">Selezionare **Unity 2020.3 LTS** e fare clic su **Avanti.**</span><span class="sxs-lookup"><span data-stu-id="4fd8f-114">Select **Unity 2020.3 LTS** and click **Next**.</span></span>

![Installare la nuova versione dell'hub Unity](images/unity-hub-img-01.png)

4. <span data-ttu-id="4fd8f-116">Controllare i componenti seguenti in **"Piattaforme":**</span><span class="sxs-lookup"><span data-stu-id="4fd8f-116">Check the following components under **'Platforms'**:</span></span>
    * <span data-ttu-id="4fd8f-117">**Supporto per Windows piattaforma universali**</span><span class="sxs-lookup"><span data-stu-id="4fd8f-117">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="4fd8f-118">**Windows Supporto della compilazione (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="4fd8f-118">**Windows Build Support (IL2CPP)**</span></span>

![Opzione di supporto per Windows di Unity Universal Windows Platform](../images/Unity_Install_Option_UWP.png)

5. <span data-ttu-id="4fd8f-120">Se Unity è stato installato in precedenza senza queste opzioni, è possibile aggiungerle tramite il menu **"Aggiungi moduli"** in Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="4fd8f-120">If you previously installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Opzione supporto Windows compilazione di Unity](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="4fd8f-122">Dopo aver installato Unity 2020.3, iniziare a creare un progetto o aggiornare un progetto esistente usando il plug-in OpenXR di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="4fd8f-122">Once you have Unity 2020.3 installed, get started creating a project or upgrading an existing project using the Mixed Reality OpenXR plugin:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4fd8f-123">Configurare il progetto con il plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="4fd8f-123">Set up your project with the OpenXR plugin</span></span>](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="4fd8f-124">Sebbene sia consigliabile usare OpenXR per tutti i nuovi progetti, Unity 2020.3 LTS supporta anche il [plug-Windows XR.](xr-project-setup.md?tabs=windowsxr)</span><span class="sxs-lookup"><span data-stu-id="4fd8f-124">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](xr-project-setup.md?tabs=windowsxr).</span></span> <span data-ttu-id="4fd8f-125">Questo plug-in è completamente supportato, anche se non riceverà nuove funzionalità, ad esempio il supporto di AR Foundation 4.0.</span><span class="sxs-lookup"><span data-stu-id="4fd8f-125">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="4fd8f-126">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="4fd8f-126">Unity 2019.4 LTS</span></span>

<span data-ttu-id="4fd8f-127">Se è necessario usare Unity 2019, è possibile usare **Unity 2019 LTS con XR incorporato legacy.**</span><span class="sxs-lookup"><span data-stu-id="4fd8f-127">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="4fd8f-128">Per iniziare a usare Legacy Built-in XR in Unity 2019.4 LTS, fare clic qui:</span><span class="sxs-lookup"><span data-stu-id="4fd8f-128">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4fd8f-129">Configurare il progetto con XR predefinito legacy</span><span class="sxs-lookup"><span data-stu-id="4fd8f-129">Set up your project with Legacy Built-in XR</span></span>](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="4fd8f-130">Unity ha deprecato il supporto XR incorporato legacy a data di Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="4fd8f-130">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="4fd8f-131">Anche se Unity 2019 offre un nuovo framework plug-in XR, Microsoft attualmente non consiglia questo percorso in Unity 2019 a causa delle incompatibilità di Ancoraggi nello stato di Azure con AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="4fd8f-131">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="4fd8f-132">In Unity 2020, Ancoraggi nello spaziali di Azure è supportato all'interno del framework plug-in XR.</span><span class="sxs-lookup"><span data-stu-id="4fd8f-132">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="4fd8f-133">Se si sviluppano app per HoloLens (prima generazione), questi visori rimangono supportati in Unity 2019 LTS con XR legacy incorporato per l'intero ciclo di vita di Unity 2019 LTS fino alla metà del 2022.</span><span class="sxs-lookup"><span data-stu-id="4fd8f-133">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20212"></a><span data-ttu-id="4fd8f-134">Unity 2021.2</span><span class="sxs-lookup"><span data-stu-id="4fd8f-134">Unity 2021.2</span></span>

<span data-ttu-id="4fd8f-135">Se si provano le prime build **di Unity 2021.2,** iniziare a usare il [**plug-in OpenXR di realtà mista.**](xr-project-setup.md?tabs=openxr)</span><span class="sxs-lookup"><span data-stu-id="4fd8f-135">If you are trying out early **Unity 2021.2** builds, get started with the [**Mixed Reality OpenXR plugin**](xr-project-setup.md?tabs=openxr).</span></span> <span data-ttu-id="4fd8f-136">Il plug-in OpenXR è l'unico percorso per lo sviluppo di realtà mista in Unity 2021.2 e versioni successive, perché l'ultima versione di Unity per supportare il plug-in Windows XR è unity 2021.1.</span><span class="sxs-lookup"><span data-stu-id="4fd8f-136">The OpenXR plugin is the only path for mixed reality development in Unity 2021.2 and later, as the final Unity version to support the Windows XR plugin was Unity 2021.1.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="4fd8f-137">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="4fd8f-137">Unity 2018.4 LTS</span></span>

<span data-ttu-id="4fd8f-138">Unity 2018.4 LTS ha raggiunto la fine della finestra di supporto Long-Term di Unity di due anni e non riceve più aggiornamenti da Unity, anche se i progetti continueranno a essere eseguiti.</span><span class="sxs-lookup"><span data-stu-id="4fd8f-138">Unity 2018.4 LTS has reached the end of Unity's two-year Long-Term Support window and is no longer receiving updates from Unity, although your projects will continue to run.</span></span>

<span data-ttu-id="4fd8f-139">Se si ha un progetto Unity 2018, è consigliabile pianificare una migrazione in avanti a Unity 2020.3 LTS e al plug-in OpenXR di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="4fd8f-139">If you have a Unity 2018 project, you should consider planning for a migration forward to Unity 2020.3 LTS and the Mixed Reality OpenXR plugin.</span></span>