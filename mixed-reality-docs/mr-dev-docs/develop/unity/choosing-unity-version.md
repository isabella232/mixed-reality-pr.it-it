---
title: Scelta di una versione di Unity e di un plug-in XR
description: Rimanere aggiornati sulle raccomandazioni più recenti per i plug-in Unity e XR per lo sviluppo di applicazioni HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, unity
ms.openlocfilehash: f37dbdccf175a5cea9a647f0c14b90682b19dfb3
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906856"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="a0eeb-104">Scelta di una versione di Unity e di un plug-in XR</span><span class="sxs-lookup"><span data-stu-id="a0eeb-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="a0eeb-105">Anche se attualmente è consigliabile installare **Unity 2019.4 LTS** e usare XR incorporato legacy per lo sviluppo di realtà mista, è possibile compilare app anche con altre configurazioni di Unity.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="a0eeb-106">Unity 2019.4 LTS (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="a0eeb-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="a0eeb-107">L'attuale configurazione di Unity consigliata da Microsoft per lo sviluppo HoloLens 2 e Windows Mixed Reality è **Unity 2019.4 LTS** con il supporto XR incorporato legacy.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="a0eeb-108">Il modo migliore per installare e gestire Unity è <a href="https://unity3d.com/get-unity/download" target="_blank">tramite [Unity Hub]</a>.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="a0eeb-109">Al termine dell'installazione, aprire Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="a0eeb-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="a0eeb-110">Selezionare la **scheda Installazioni** e scegliere **AGGIUNGI**</span><span class="sxs-lookup"><span data-stu-id="a0eeb-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="a0eeb-111">Selezionare Unity 2019.4 LTS e fare clic su **Avanti**</span><span class="sxs-lookup"><span data-stu-id="a0eeb-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Nuova versione dell'hub unity](images/unity-hub-img-2019.png)

3. <span data-ttu-id="a0eeb-113">Controllare i componenti seguenti in **"Piattaforme"**</span><span class="sxs-lookup"><span data-stu-id="a0eeb-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="a0eeb-114">**piattaforma UWP (Universal Windows Platform) di compilazione**</span><span class="sxs-lookup"><span data-stu-id="a0eeb-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="a0eeb-115">**Supporto per la compilazione di Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="a0eeb-115">**Windows Build Support (IL2CPP)**</span></span>

![Opzione supporto piattaforma UWP (Universal Windows Platform) compilazione di Unity](images/Unity_Install_Option_UWP_2019.png)

4. <span data-ttu-id="a0eeb-117">Se Unity è stato installato senza queste opzioni, è possibile aggiungerlo tramite il menu **"Aggiungi moduli"** in Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="a0eeb-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Opzione Unity Windows Build Support (Supporto per la compilazione di Windows in Unity)](images/Unity_Install_Option_UWP2_2019.png)

<span data-ttu-id="a0eeb-119">Per iniziare a usare legacy built-in XR in Unity 2019.4 LTS, fare clic qui:</span><span class="sxs-lookup"><span data-stu-id="a0eeb-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a0eeb-120">Configurare la versione legacy di XR incorporata</span><span class="sxs-lookup"><span data-stu-id="a0eeb-120">Set up Legacy Built-in XR</span></span>](./xr-project-setup.md?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="a0eeb-121">Unity ha deprecato il supporto XR incorporato legacy a livello di Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="a0eeb-122">Anche se Unity 2019 offre un nuovo framework plug-in XR, Microsoft attualmente non consiglia tale percorso in Unity 2019 a causa delle incompatibilità di Ancoraggi nello stato di Azure con AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="a0eeb-123">In Unity 2020 Ancoraggi nello stato di Azure è supportato all'interno del framework plug-in XR.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="a0eeb-124">Se stai sviluppando app per HoloLens (prima generazione), questi visori VR rimangono supportati in Unity 2019 LTS con XR legacy incorporato per l'intero ciclo di vita di Unity 2019 LTS fino alla metà del 2022.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="a0eeb-125">Unity 2020.3 LTS</span><span class="sxs-lookup"><span data-stu-id="a0eeb-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="a0eeb-126">Se si usa **Unity 2020.3 LTS,** la raccomandazione corrente di Microsoft è il plug-in **OpenXR di Realtà mista più recente.**</span><span class="sxs-lookup"><span data-stu-id="a0eeb-126">If you’re using **Unity 2020.3 LTS**, Microsoft’s current recommendation is the latest **Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="a0eeb-127">È NECESSARIO usare la patch di Unity versione 2020.3.8f1 o successiva per evitare problemi di prestazioni noti con le build precedenti della versione 2020.3.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-127">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

<span data-ttu-id="a0eeb-128">Il plug-in OpenXR di realtà mista supporta completamente AR Foundation 4.0, fornendo implementazioni ARPlaneManager e ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-128">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="a0eeb-129">In questo modo è possibile scrivere il codice di hit testing una volta che si estende su HoloLens 2 e su telefoni e tablet ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-129">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

<span data-ttu-id="a0eeb-130">Esistono tuttavia problemi noti che interessano i progetti Unity 2020 LTS:</span><span class="sxs-lookup"><span data-stu-id="a0eeb-130">However, there are known issues that affect Unity 2020 LTS projects:</span></span>

* <span data-ttu-id="a0eeb-131">La pipeline di rendering universale (URP) 10.5.0 o versione precedente presenta una penalità per le prestazioni HoloLens 2 dispositivi.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-131">The Universal Rendering Pipeline (URP) 10.5.0 or older has performance penalties on HoloLens 2 devices.</span></span>

<span data-ttu-id="a0eeb-132">Se si sceglie di avviare un nuovo progetto in Unity 2020 oggi stesso, assicurarsi di seguire le prossime settimane per le compilazioni Unity aggiornate e i pacchetti URP prima di spedire l'app.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-132">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming weeks for updated Unity builds and URP packages before shipping your app.</span></span>  <span data-ttu-id="a0eeb-133">Ciò garantisce che gli utenti sperimentino una corretta stabilità dell'ologramma.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-133">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a0eeb-134">Uso del plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="a0eeb-134">Using the OpenXR plugin</span></span>](./xr-project-setup.md?tabs=openxr)

## <a name="unity-20211"></a><span data-ttu-id="a0eeb-135">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="a0eeb-135">Unity 2021.1</span></span>

<span data-ttu-id="a0eeb-136">Se si provano le prime build di **Unity 2021.1,** è consigliabile passare al plug-in **OpenXR,** perché il plug-in Windows XR è deprecato.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-136">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="a0eeb-137">A partire da Unity 2021.2, il plug-in OpenXR sarà l'unico percorso per lo sviluppo di realtà mista, perché il plug-in Windows XR non sarà più supportato.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-137">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="a0eeb-138">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="a0eeb-138">Unity 2018.4 LTS</span></span>

<span data-ttu-id="a0eeb-139">Se si ha già un progetto che usa Unity 2018.4 LTS, il motore Unity continuerà a essere supportato per 2 anni dopo il rilascio.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-139">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="a0eeb-140">Unity 2018 LTS raggiungerà la fine del servizio nella primavera del 2021.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-140">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>