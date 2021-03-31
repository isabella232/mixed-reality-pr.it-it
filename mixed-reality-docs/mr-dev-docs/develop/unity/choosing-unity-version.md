---
title: Scelta di una versione di Unity e plug-in XR
description: È possibile rimanere sempre aggiornati sulle raccomandazioni di Unity e plug-in di XR più recenti per lo sviluppo di applicazioni HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, auricolare realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale, Unity
ms.openlocfilehash: b8f5f0131da811393ee053541e0c2fa0c735472e
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938139"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="f1fc6-104">Scelta di una versione di Unity e plug-in XR</span><span class="sxs-lookup"><span data-stu-id="f1fc6-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="f1fc6-105">Sebbene si **consigli attualmente l'installazione di unity 2019,4 LTS e l'uso di XR integrato legacy** per lo sviluppo di realtà miste, è possibile creare anche app con altre configurazioni Unity.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="f1fc6-106">Unity 2019,4 LTS (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="f1fc6-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="f1fc6-107">La configurazione attuale di Unity consigliata da Microsoft per HoloLens 2 e lo sviluppo di realtà mista di Windows è **unity 2019,4 LTS che usa il supporto predefinito di XR** .</span><span class="sxs-lookup"><span data-stu-id="f1fc6-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="f1fc6-108">Il modo migliore per installare e gestire Unity è quello di <a href="https://unity3d.com/get-unity/download" target="_blank">[Hub Unity]</a>.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="f1fc6-109">Quando è installato, aprire Hub Unity:</span><span class="sxs-lookup"><span data-stu-id="f1fc6-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="f1fc6-110">Selezionare la scheda **Installa** e scegliere **Aggiungi** .</span><span class="sxs-lookup"><span data-stu-id="f1fc6-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="f1fc6-111">Selezionare Unity 2019,4 LTS e fare clic su **Next**</span><span class="sxs-lookup"><span data-stu-id="f1fc6-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Nuova versione di installazione Hub Unity](images/unity-hub-img-01.png)

3. <span data-ttu-id="f1fc6-113">Controllare i componenti seguenti in **' piattaforme '**</span><span class="sxs-lookup"><span data-stu-id="f1fc6-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="f1fc6-114">**Supporto di piattaforma UWP (Universal Windows Platform) Build**</span><span class="sxs-lookup"><span data-stu-id="f1fc6-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="f1fc6-115">**Supporto per Windows Build (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="f1fc6-115">**Windows Build Support (IL2CPP)**</span></span>

![Opzione di supporto per Unity piattaforma UWP (Universal Windows Platform) Build](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="f1fc6-117">Se Unity è stata installata senza queste opzioni, è possibile aggiungerle tramite il menu **' Aggiungi moduli '** nell'hub Unity:</span><span class="sxs-lookup"><span data-stu-id="f1fc6-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Opzione di supporto build di Windows Unity](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="f1fc6-119">Per iniziare a usare la versione precedente di XR incorporata in Unity 2019,4 LTS, fare clic qui:</span><span class="sxs-lookup"><span data-stu-id="f1fc6-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f1fc6-120">Configurare XR integrato legacy</span><span class="sxs-lookup"><span data-stu-id="f1fc6-120">Set up Legacy Built-in XR</span></span>](legacy-xr-support.md)

> [!NOTE]
> <span data-ttu-id="f1fc6-121">Unity ha deprecato il supporto di XR incorporato legacy a partire da Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="f1fc6-122">Sebbene Unity 2019 offra un nuovo Framework di plug-in di XR, Microsoft non è attualmente in grado di consigliare tale percorso in Unity 2019 a causa di incompatibilità con AR Foundation 2 per gli ancoraggi spaziali di Azure.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="f1fc6-123">In Unity 2020, gli ancoraggi spaziali di Azure sono supportati all'interno del Framework di plug-in XR.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="f1fc6-124">Se si sviluppano app per HoloLens (1a generazione), questi auricolari rimangono supportati in Unity 2019 LTS con XR incorporato legacy per il ciclo di vita completo di Unity 2019 LTS fino a metà 2022.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="f1fc6-125">Unity 2020,3 LTS</span><span class="sxs-lookup"><span data-stu-id="f1fc6-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="f1fc6-126">Se si usa **unity 2020,3 LTS**, è possibile usare il **plug-in Windows XR** per sviluppare applicazioni per la realtà mista HoloLens 2 e Windows.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-126">If you’re using **Unity 2020.3 LTS**, you can use the **Windows XR plugin** to develop HoloLens 2 and Windows Mixed Reality applications.</span></span>

<span data-ttu-id="f1fc6-127">Tuttavia, esistono problemi noti che influiscono sulla stabilità degli ologrammi e altre funzionalità in HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="f1fc6-127">However, there are known issues that affect hologram stability and other features on HoloLens 2:</span></span> 

* <span data-ttu-id="f1fc6-128">L'invio del buffer di profondità è stato regressione nelle compilazioni recenti di Unity 2020, con conseguente instabilità dell'ologramma grave.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-128">Depth buffer submission has regressed in recent Unity 2020 builds, which results in severe hologram instability.</span></span>
* <span data-ttu-id="f1fc6-129">Le applicazioni di comunicazione remota di app olografiche che usano la destinazione di compilazione piattaforma UWP (Universal Windows Platform) non funzionano.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-129">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
* <span data-ttu-id="f1fc6-130">Il sistema di processi grafici Unity è impostato sul valore predefinito, anche se non è compatibile con i progetti HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-130">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

<span data-ttu-id="f1fc6-131">Se si sceglie di avviare un nuovo progetto in Unity 2020 oggi, assicurarsi di seguire i prossimi mesi per le compilazioni Unity aggiornate e le compilazioni di plug-in di Windows XR prima di distribuire l'app.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-131">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming months for updated Unity builds and Windows XR plugin builds before shipping your app.</span></span>  <span data-ttu-id="f1fc6-132">In questo modo si garantisce che gli utenti sperimentino una corretta stabilità degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-132">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f1fc6-133">Uso del plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="f1fc6-133">Using the Windows XR plugin</span></span>](windows-xr-plugin.md)

### <a name="using-openxr"></a><span data-ttu-id="f1fc6-134">Uso di OpenXR</span><span class="sxs-lookup"><span data-stu-id="f1fc6-134">Using OpenXR</span></span>

<span data-ttu-id="f1fc6-135">Unity 2020,3 LTS supporta inoltre un'anteprima pubblica del plug-in OpenXR per la **realtà mista** .</span><span class="sxs-lookup"><span data-stu-id="f1fc6-135">Unity 2020.3 LTS also supports a public preview of the **Mixed Reality OpenXR** plugin.</span></span>

<span data-ttu-id="f1fc6-136">Il plug-in OpenXR realtà mista supporta completamente AR Foundation 4,0, fornendo implementazioni ARPlaneManager e ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-136">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="f1fc6-137">In questo modo è possibile scrivere codice di hit testing una volta che si estende su HoloLens 2 e ARCore/ARKit Phone e tablet.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-137">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span> 

<span data-ttu-id="f1fc6-138">Successivamente quest'anno, **unity 2020,3 LTS con il plug** -in OpenXR diventerà la configurazione di Unity consigliata e le funzionalità future di HoloLens 2 in Unity verranno esposte solo tramite questo plug-in.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-138">Later this year, **Unity 2020.3 LTS with the OpenXR plugin** will become the recommended Unity configuration, and future HoloLens 2 features in Unity will be exposed only through this plugin.</span></span>  <span data-ttu-id="f1fc6-139">È possibile avviare il progetto per il momento. Tuttavia, se il progetto è destinato a HoloLens 2, si verificherà attualmente la stabilità dell'ologramma Unity 2020 e altri problemi elencati sopra.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-139">You can start your project here for now - however, if your project targets HoloLens 2, you will currently encounter the Unity 2020 hologram stability and other issues listed above.</span></span>  <span data-ttu-id="f1fc6-140">Prima di spedire l'app, assicurarsi di consultare i prossimi mesi per le compilazioni Unity aggiornate e le compilazioni di plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-140">Be sure to check back in the coming months for updated Unity builds and OpenXR plugin builds before shipping your app.</span></span>  <span data-ttu-id="f1fc6-141">In questo modo si garantisce che gli utenti sperimentino una corretta stabilità degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-141">This will ensure that your users experience proper hologram stability.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="f1fc6-142">Uso del plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="f1fc6-142">Using the OpenXR plugin</span></span>](openxr-getting-started.md)

## <a name="unity-20211"></a><span data-ttu-id="f1fc6-143">Unity 2021,1</span><span class="sxs-lookup"><span data-stu-id="f1fc6-143">Unity 2021.1</span></span>

<span data-ttu-id="f1fc6-144">Se si sta provando a eseguire prime **unity 2021,1** Build, è consigliabile passare al **plug**-in OpenXR, perché il plug-in di Windows XR è deprecato.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-144">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="f1fc6-145">A partire da Unity 2021,2, il plug-in OpenXR sarà l'unico percorso per lo sviluppo di realtà miste, perché il plug-in di Windows XR non sarà più supportato.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-145">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="f1fc6-146">Unity 2018,4 LTS</span><span class="sxs-lookup"><span data-stu-id="f1fc6-146">Unity 2018.4 LTS</span></span>

<span data-ttu-id="f1fc6-147">Se si dispone già di un progetto con Unity 2018,4 LTS, il motore Unity continuerà a essere supportato per 2 anni dopo il relativo rilascio.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-147">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="f1fc6-148">Unity 2018 LTS raggiungerà la fine del servizio nella primavera del 2021.</span><span class="sxs-lookup"><span data-stu-id="f1fc6-148">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
