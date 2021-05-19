---
title: Scelta di una versione di Unity e di un plug-in XR
description: Rimanere aggiornati sulle raccomandazioni più recenti per i plug-in Unity e XR per lo sviluppo di applicazioni HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, unity
ms.openlocfilehash: 3bdaa35f495d7a647a7cbf37ddcd4f85e96d74d0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143676"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="9d001-104">Scelta di una versione di Unity e di un plug-in XR</span><span class="sxs-lookup"><span data-stu-id="9d001-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="9d001-105">Anche se attualmente è consigliabile installare **Unity 2019.4 LTS** e usare XR incorporato legacy per lo sviluppo di realtà mista, è possibile compilare app anche con altre configurazioni di Unity.</span><span class="sxs-lookup"><span data-stu-id="9d001-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="9d001-106">Unity 2019.4 LTS (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="9d001-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="9d001-107">L'attuale configurazione di Unity consigliata da Microsoft per lo sviluppo HoloLens 2 e Windows Mixed Reality è **Unity 2019.4 LTS** con il supporto XR incorporato legacy.</span><span class="sxs-lookup"><span data-stu-id="9d001-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="9d001-108">Il modo migliore per installare e gestire Unity è <a href="https://unity3d.com/get-unity/download" target="_blank">tramite [Unity Hub]</a>.</span><span class="sxs-lookup"><span data-stu-id="9d001-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="9d001-109">Al termine dell'installazione, aprire Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="9d001-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="9d001-110">Selezionare la **scheda Installazioni** e scegliere **AGGIUNGI**</span><span class="sxs-lookup"><span data-stu-id="9d001-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="9d001-111">Selezionare Unity 2019.4 LTS e fare clic su **Avanti**</span><span class="sxs-lookup"><span data-stu-id="9d001-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Nuova versione dell'hub unity](images/unity-hub-img-01.png)

3. <span data-ttu-id="9d001-113">Controllare i componenti seguenti in **"Piattaforme"**</span><span class="sxs-lookup"><span data-stu-id="9d001-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="9d001-114">**piattaforma UWP (Universal Windows Platform) di compilazione**</span><span class="sxs-lookup"><span data-stu-id="9d001-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="9d001-115">**Supporto per la compilazione di Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="9d001-115">**Windows Build Support (IL2CPP)**</span></span>

![Opzione supporto piattaforma UWP (Universal Windows Platform) compilazione di Unity](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="9d001-117">Se Unity è stato installato senza queste opzioni, è possibile aggiungerlo tramite il menu **"Aggiungi moduli"** in Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="9d001-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Opzione Unity Windows Build Support (Supporto per la compilazione di Windows in Unity)](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="9d001-119">Per iniziare a usare XR incorporato legacy in Unity 2019.4 LTS, fare clic qui:</span><span class="sxs-lookup"><span data-stu-id="9d001-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9d001-120">Configurare la versione legacy di XR incorporata</span><span class="sxs-lookup"><span data-stu-id="9d001-120">Set up Legacy Built-in XR</span></span>](legacy-xr-support.md)

> [!NOTE]
> <span data-ttu-id="9d001-121">Unity ha deprecato il supporto XR incorporato legacy a data di Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="9d001-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="9d001-122">Anche se Unity 2019 offre un nuovo framework plug-in XR, Microsoft attualmente non consiglia questo percorso in Unity 2019 a causa delle incompatibilità di Ancoraggi nello stato di Azure con AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="9d001-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="9d001-123">In Unity 2020, Ancoraggi nello spaziali di Azure è supportato all'interno del framework plug-in XR.</span><span class="sxs-lookup"><span data-stu-id="9d001-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="9d001-124">Se si sviluppano app per HoloLens (prima generazione), questi visori rimangono supportati in Unity 2019 LTS con XR legacy incorporato per l'intero ciclo di vita di Unity 2019 LTS fino alla metà del 2022.</span><span class="sxs-lookup"><span data-stu-id="9d001-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="9d001-125">Unity 2020.3 LTS</span><span class="sxs-lookup"><span data-stu-id="9d001-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="9d001-126">Se si usa **Unity 2020.3 LTS,** è possibile usare il **plug-in Windows XR** per sviluppare applicazioni HoloLens 2 e Windows Mixed Reality applicazioni.</span><span class="sxs-lookup"><span data-stu-id="9d001-126">If you’re using **Unity 2020.3 LTS**, you can use the **Windows XR plugin** to develop HoloLens 2 and Windows Mixed Reality applications.</span></span>

<span data-ttu-id="9d001-127">Esistono tuttavia problemi noti che influiscono sulla stabilità dell'ologramma e su altre funzionalità HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="9d001-127">However, there are known issues that affect hologram stability and other features on HoloLens 2:</span></span> 

* <span data-ttu-id="9d001-128">Le applicazioni di comunicazione remota di app olografiche piattaforma UWP (Universal Windows Platform) destinazione di compilazione non funzionano.</span><span class="sxs-lookup"><span data-stu-id="9d001-128">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
* <span data-ttu-id="9d001-129">Il sistema dei processi di grafica unity è stato utilizzato per impostazione predefinita, anche se non è compatibile con i progetti HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9d001-129">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

<span data-ttu-id="9d001-130">Se si sceglie di avviare un nuovo progetto in Unity 2020 oggi stesso, assicurarsi di seguire nei prossimi mesi le compilazioni di Unity aggiornate e le compilazioni del plug-in Windows XR prima di compilare l'app.</span><span class="sxs-lookup"><span data-stu-id="9d001-130">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming months for updated Unity builds and Windows XR plugin builds before shipping your app.</span></span>  <span data-ttu-id="9d001-131">In questo modo si garantisce che gli utenti sperimentino una corretta stabilità dell'ologramma.</span><span class="sxs-lookup"><span data-stu-id="9d001-131">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9d001-132">Uso del plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="9d001-132">Using the Windows XR plugin</span></span>](windows-xr-plugin.md)

### <a name="using-openxr"></a><span data-ttu-id="9d001-133">Uso di OpenXR</span><span class="sxs-lookup"><span data-stu-id="9d001-133">Using OpenXR</span></span>

<span data-ttu-id="9d001-134">Unity 2020.3 LTS supporta anche un'anteprima pubblica del **plug-in OpenXR di realtà mista.**</span><span class="sxs-lookup"><span data-stu-id="9d001-134">Unity 2020.3 LTS also supports a public preview of the **Mixed Reality OpenXR** plugin.</span></span>

<span data-ttu-id="9d001-135">Il plug-in OpenXR di realtà mista supporta completamente AR Foundation 4.0, fornendo implementazioni arPlaneManager e ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="9d001-135">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="9d001-136">In questo modo è possibile scrivere il codice di hit testing una volta che si estende su HoloLens 2 telefoni e tablet ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="9d001-136">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span> 

<span data-ttu-id="9d001-137">Più avanti quest'anno, **Unity 2020.3 LTS** con il plug-in OpenXR diventerà la configurazione di Unity consigliata e le future funzionalità HoloLens 2 in Unity verranno esposte solo tramite questo plug-in.</span><span class="sxs-lookup"><span data-stu-id="9d001-137">Later this year, **Unity 2020.3 LTS with the OpenXR plugin** will become the recommended Unity configuration, and future HoloLens 2 features in Unity will be exposed only through this plugin.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9d001-138">Uso del plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="9d001-138">Using the OpenXR plugin</span></span>](openxr-getting-started.md)

## <a name="unity-20211"></a><span data-ttu-id="9d001-139">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="9d001-139">Unity 2021.1</span></span>

<span data-ttu-id="9d001-140">Se si provano le prime build di **Unity 2021.1,** è consigliabile passare al plug-in **OpenXR,** perché il plug-in Windows XR è deprecato.</span><span class="sxs-lookup"><span data-stu-id="9d001-140">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="9d001-141">A partire da Unity 2021.2, il plug-in OpenXR sarà l'unico percorso per lo sviluppo di realtà mista, perché il plug-in Windows XR non sarà più supportato.</span><span class="sxs-lookup"><span data-stu-id="9d001-141">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="9d001-142">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="9d001-142">Unity 2018.4 LTS</span></span>

<span data-ttu-id="9d001-143">Se si ha già un progetto che usa Unity 2018.4 LTS, il motore Unity continuerà a essere supportato per 2 anni dopo il rilascio.</span><span class="sxs-lookup"><span data-stu-id="9d001-143">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="9d001-144">Unity 2018 LTS raggiungerà la fine del servizio nella primavera del 2021.</span><span class="sxs-lookup"><span data-stu-id="9d001-144">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
