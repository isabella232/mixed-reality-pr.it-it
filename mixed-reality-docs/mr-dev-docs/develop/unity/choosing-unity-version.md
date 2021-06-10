---
title: Scelta di una versione di Unity e di un plug-in XR
description: Rimanere aggiornati sulle raccomandazioni più recenti dei plug-in Unity e XR per lo sviluppo di applicazioni HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 05/27/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale, unity
ms.openlocfilehash: 1f658c0e69091ce0aaeb37b7f427e57f060c3fb2
ms.sourcegitcommit: 62e5909b837c9c7ecedd040164f2308868db4723
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2021
ms.locfileid: "111741923"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="fec95-104">Scelta di una versione di Unity e di un plug-in XR</span><span class="sxs-lookup"><span data-stu-id="fec95-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="fec95-105">Anche se attualmente è consigliabile installare **Unity 2020.3 LTS** con il plug-in OpenXR di realtà mista più recente per lo sviluppo di realtà mista, è possibile compilare app anche con altre configurazioni di Unity.</span><span class="sxs-lookup"><span data-stu-id="fec95-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="fec95-106">Unity 2020.3 LTS (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="fec95-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="fec95-107">La configurazione di Unity consigliata di Microsoft per lo sviluppo HoloLens 2 e Windows Mixed Reality è **Unity 2020.3 LTS** con il plug-in OpenXR di Realtà mista più recente.</span><span class="sxs-lookup"><span data-stu-id="fec95-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fec95-108">Unity 2020 non supporta la destinazione di HoloLens (prima generazione).</span><span class="sxs-lookup"><span data-stu-id="fec95-108">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="fec95-109">Questi visori rimangono supportati in **[Unity 2019 LTS](#unity-20194-lts)** con legacy built-in XR per l'intero ciclo di vita di Unity 2019 LTS fino a metà 2022.</span><span class="sxs-lookup"><span data-stu-id="fec95-109">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

<span data-ttu-id="fec95-110">Il plug-in OpenXR di realtà mista supporta completamente AR Foundation 4.0, fornendo implementazioni arPlaneManager e ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="fec95-110">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="fec95-111">In questo modo è possibile scrivere codice di hit testing una volta che si estende su HoloLens 2 telefoni e tablet ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="fec95-111">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

<span data-ttu-id="fec95-112">Il modo migliore per installare e gestire Unity è tramite <a href="https://unity3d.com/get-unity/download" target="_blank">l'hub unity.</a></span><span class="sxs-lookup"><span data-stu-id="fec95-112">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span></span> <span data-ttu-id="fec95-113">Al termine dell'installazione, aprire Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="fec95-113">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="fec95-114">Selezionare la **scheda Installazioni** e scegliere **AGGIUNGI**</span><span class="sxs-lookup"><span data-stu-id="fec95-114">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="fec95-115">Selezionare Unity 2020.3 LTS e fare clic su **Avanti**</span><span class="sxs-lookup"><span data-stu-id="fec95-115">Select Unity 2020.3 LTS and click **Next**</span></span>

![Unity hub instal new version](images/unity-hub-img-01.png)

3. <span data-ttu-id="fec95-117">Controllare i componenti seguenti in **"Piattaforme"**</span><span class="sxs-lookup"><span data-stu-id="fec95-117">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="fec95-118">**piattaforma UWP (Universal Windows Platform) di compilazione**</span><span class="sxs-lookup"><span data-stu-id="fec95-118">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="fec95-119">**Supporto per la compilazione di Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="fec95-119">**Windows Build Support (IL2CPP)**</span></span>

![Opzione supporto piattaforma UWP (Universal Windows Platform) compilazione di Unity](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="fec95-121">Se Unity è stato installato senza queste opzioni, è possibile aggiungerle tramite il menu **"Aggiungi moduli"** in Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="fec95-121">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Opzione supporto compilazione Di Unity per Windows](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="fec95-123">Uso del plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="fec95-123">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="fec95-124">Sebbene sia consigliabile usare OpenXR per tutti i nuovi progetti, Unity 2020.3 LTS supporta anche il plug-in **[Windows XR.](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)**</span><span class="sxs-lookup"><span data-stu-id="fec95-124">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the **[Windows XR plugin](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)**.</span></span> <span data-ttu-id="fec95-125">I problemi noti che influiscono sulla stabilità dell'ologramma e altre funzionalità HoloLens 2 includono:</span><span class="sxs-lookup"><span data-stu-id="fec95-125">Known issues that affect hologram stability and other features on HoloLens 2 include:</span></span>
>
> * <span data-ttu-id="fec95-126">Le applicazioni di comunicazione remota delle app olografiche piattaforma UWP (Universal Windows Platform) destinazione di compilazione non funzionano.</span><span class="sxs-lookup"><span data-stu-id="fec95-126">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
> * <span data-ttu-id="fec95-127">Il sistema dei processi di grafica unity è stato utilizzato per impostazione predefinita, anche se non è compatibile con i progetti HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fec95-127">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="fec95-128">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="fec95-128">Unity 2019.4 LTS</span></span>

<span data-ttu-id="fec95-129">Se è necessario usare Unity 2019, è possibile usare **Unity 2019 LTS con XR incorporato legacy.**</span><span class="sxs-lookup"><span data-stu-id="fec95-129">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="fec95-130">Per iniziare a usare Legacy Built-in XR in Unity 2019.4 LTS, fare clic qui:</span><span class="sxs-lookup"><span data-stu-id="fec95-130">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fec95-131">Configurare la versione XR incorporata legacy</span><span class="sxs-lookup"><span data-stu-id="fec95-131">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="fec95-132">Unity ha deprecato il supporto XR incorporato legacy a data di Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="fec95-132">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="fec95-133">Anche se Unity 2019 offre un nuovo framework plug-in XR, Microsoft attualmente non consiglia questo percorso in Unity 2019 a causa delle incompatibilità di Ancoraggi nello stato di Azure con AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="fec95-133">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="fec95-134">In Unity 2020, Ancoraggi nello spaziali di Azure è supportato all'interno del framework plug-in XR.</span><span class="sxs-lookup"><span data-stu-id="fec95-134">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="fec95-135">Se si sviluppano app per HoloLens (prima generazione), questi visori rimangono supportati in Unity 2019 LTS con XR legacy incorporato per l'intero ciclo di vita di Unity 2019 LTS fino alla metà del 2022.</span><span class="sxs-lookup"><span data-stu-id="fec95-135">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20211"></a><span data-ttu-id="fec95-136">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="fec95-136">Unity 2021.1</span></span>

<span data-ttu-id="fec95-137">Se si provano le prime build **di Unity 2021.1,** è consigliabile passare al **plug-in OpenXR,** perché il plug-in Windows XR è deprecato.</span><span class="sxs-lookup"><span data-stu-id="fec95-137">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="fec95-138">A partire da Unity 2021.2, il plug-in OpenXR sarà l'unico percorso per lo sviluppo di realtà mista, perché il plug-in Windows XR non sarà più supportato.</span><span class="sxs-lookup"><span data-stu-id="fec95-138">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="fec95-139">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="fec95-139">Unity 2018.4 LTS</span></span>

<span data-ttu-id="fec95-140">Se si ha già un progetto che usa Unity 2018.4 LTS, il motore unity continuerà a essere supportato per 2 anni dopo il rilascio.</span><span class="sxs-lookup"><span data-stu-id="fec95-140">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="fec95-141">Unity 2018 LTS raggiungerà la fine del servizio nella primavera del 2021.</span><span class="sxs-lookup"><span data-stu-id="fec95-141">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
