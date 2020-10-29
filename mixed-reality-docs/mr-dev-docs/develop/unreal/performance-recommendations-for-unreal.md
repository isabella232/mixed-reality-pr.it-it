---
title: Consigli sulle prestazioni per Unreal
description: Consigli per ottenere prestazioni ottimali per le app di realtà mista in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, prestazioni, ottimizzazione, impostazioni, documentazione
ms.openlocfilehash: 64c8cdf4900234a4486cf9b575671321a8430160
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91697234"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="6f5ab-104">Consigli sulle prestazioni per Unreal</span><span class="sxs-lookup"><span data-stu-id="6f5ab-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="6f5ab-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="6f5ab-105">Overview</span></span>

<span data-ttu-id="6f5ab-106">Questo articolo si basa sugli argomenti affrontati in [Consigli sulle prestazioni per la realtà mista](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), ma si concentra in particolare su funzionalità specifiche di Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="6f5ab-107">Prima di proseguire, è consigliabile approfondire le conoscenze sui colli di bottiglia delle applicazioni, sull'analisi e la profilazione delle app in realtà mista e sulle correzioni delle prestazioni generali.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="6f5ab-108">Impostazioni consigliate per il progetto Unreal</span><span class="sxs-lookup"><span data-stu-id="6f5ab-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="6f5ab-109">Tutte le impostazioni seguenti sono disponibili in **Edit > Project Settings** (Modifica > Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="6f5ab-109">You can find each of the following settings in **Edit > Project Settings** .</span></span>

1. <span data-ttu-id="6f5ab-110">Uso del renderer VR per dispositivi mobili:</span><span class="sxs-lookup"><span data-stu-id="6f5ab-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="6f5ab-111">Scorri fino alla sezione **Project** (Progetto), seleziona **Target Hardware** (Hardware di destinazione) e imposta la piattaforma di destinazione su **Mobile/Tablet** (Cellulare/Tablet).</span><span class="sxs-lookup"><span data-stu-id="6f5ab-111">Scroll to the **Project** section, select **Target Hardware** , and set the target platform to **Mobile/Tablet**</span></span>

![Impostazione di dispositivi mobili come destinazione](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="6f5ab-113">Uso del renderer di avanzamento:</span><span class="sxs-lookup"><span data-stu-id="6f5ab-113">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="6f5ab-114">Questa funzionalità è molto più efficiente per la realtà mista rispetto alla pipeline predefinita di rendering posticipato.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-114">This feature is much better for Mixed Reality than the default Deferred rendering pipeline.</span></span> <span data-ttu-id="6f5ab-115">Questo è dovuto principalmente al numero di funzionalità che è possibile disabilitare singolarmente.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-115">This is primarily because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="6f5ab-116">Per altre informazioni, vedere la [documentazione di Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span><span class="sxs-lookup"><span data-stu-id="6f5ab-116">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![Rendering di avanzamento](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="6f5ab-118">Disabilitazione dell'annebbiamento ai vertici:</span><span class="sxs-lookup"><span data-stu-id="6f5ab-118">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="6f5ab-119">La funzionalità di annebbiamento ai vertici applica calcoli di annebbiamento a ogni vertice di un poligono e quindi interpola i risultati in tutta la faccia del poligono.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-119">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="6f5ab-120">Se il gioco non prevede la nebbia, è necessario scegliere questa impostazione per disabilitare la nebbia e aumentare le prestazioni di ombreggiatura.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-120">If your game does not use fog, you should choose this setting to disable fog to increase shading performance.</span></span>

![Opzioni di annebbiamento ai vertici](images/unreal/performance-recommendations-img-05.png)

4. <span data-ttu-id="6f5ab-122">Disabilitazione del culling delle occlusioni:</span><span class="sxs-lookup"><span data-stu-id="6f5ab-122">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="6f5ab-123">Scorri fino alla sezione **Engine** (Motore), seleziona **Rendering** , espandi la sezione **Culling** e deseleziona **Occlusion Culling** (Culling occlusioni).</span><span class="sxs-lookup"><span data-stu-id="6f5ab-123">Scroll to the **Engine** section, select **Rendering** , expand the **Culling** section, and uncheck **Occlusion Culling** .</span></span>
        + <span data-ttu-id="6f5ab-124">Se è necessario il culling delle occlusioni per il rendering di una scena molto dettagliata, è consigliabile abilitare **Support Software Occlusion Culling** (Supporta culling occlusioni software) in **Engine > Rendering** (Motore > Rendering).</span><span class="sxs-lookup"><span data-stu-id="6f5ab-124">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering** .</span></span> <span data-ttu-id="6f5ab-125">Ciò consente ad Unreal di operare sulla CPU ed evitare query di occlusione della GPU, che influiscono negativamente sulle prestazioni di HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-125">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="6f5ab-126">Il culling delle occlusioni sulla GPU dei dispositivi mobili è lento.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-126">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="6f5ab-127">In generale, è auspicabile che la GPU si occupi principalmente di rendering.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-127">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="6f5ab-128">Se si ha la sensazione che l'occlusione possa aiutare le prestazioni, provare ad abilitare l'occlusione del software.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-128">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> <span data-ttu-id="6f5ab-129">Si noti che l'abilitazione dell'occlusione del software potrebbe peggiorare le prestazioni se si è già vincolati alla CPU da un elevato numero di chiamate di disegno.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-129">Note that enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![Disabilitare il culling delle occlusioni](images/unreal/performance-recommendations-img-02.png)

    
5. <span data-ttu-id="6f5ab-131">Disabilitazione dello stencil profondità:</span><span class="sxs-lookup"><span data-stu-id="6f5ab-131">Disabling Depth-Stencil:</span></span>
    * <span data-ttu-id="6f5ab-132">Questa funzionalità richiede un'ulteriore approvazione perché è lenta.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-132">This feature requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="6f5ab-133">Anche la traslucenza è lenta in Unreal.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-133">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="6f5ab-134">Per altre informazioni, vedere la [documentazione di Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span><span class="sxs-lookup"><span data-stu-id="6f5ab-134">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![Stencil profondità](images/unreal/performance-recommendations-img-06.png)

6. <span data-ttu-id="6f5ab-136">Uso delle visualizzazioni multiple dei dispositivi mobili:</span><span class="sxs-lookup"><span data-stu-id="6f5ab-136">Using mobile multi-view:</span></span>
    * <span data-ttu-id="6f5ab-137">Scorri fino alla sezione **Engine** (Motore), seleziona **Rendering** , espandi la sezione **VR** e abilita **Instanced Stereo** (Stereo con istanze) e **Mobile Multi-View** (Visualizzazioni multiple dispositivi mobili).</span><span class="sxs-lookup"><span data-stu-id="6f5ab-137">Scroll to the **Engine** section, select **Rendering** , expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View** .</span></span> <span data-ttu-id="6f5ab-138">L'opzione Mobile HDR (HDR per dispositivi mobili) deve essere deselezionata.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-138">Mobile HDR should be unchecked.</span></span>

![Impostazioni di rendering VR](images/unreal/performance-recommendations-img-03.png)

7. <span data-ttu-id="6f5ab-140">Riduzione delle mappe delle ombreggiature a cascata:</span><span class="sxs-lookup"><span data-stu-id="6f5ab-140">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="6f5ab-141">La riduzione del numero di mappe delle ombreggiature determina un miglioramento delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-141">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="6f5ab-142">In generale, questo valore deve essere impostato su 1, altrimenti si verifica una visibile perdita di qualità.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-142">Generally, this should be set to 1 unless there is a visible quality loss.</span></span> 

![Mappe delle ombreggiature a cascata](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="6f5ab-144">Impostazioni facoltative</span><span class="sxs-lookup"><span data-stu-id="6f5ab-144">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="6f5ab-145">Le impostazioni seguenti possono migliorare le prestazioni, causando tuttavia la disabilitazione di alcune funzionalità.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-145">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="6f5ab-146">Usare queste impostazioni solo se si è certi di non dover usare le funzionalità in questione.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-146">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="6f5ab-147">Riduzione delle permutazioni degli shader per dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="6f5ab-147">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="6f5ab-148">Se le luci non si muovono in modo indipendente dalla fotocamera, è possibile impostare questo valore tranquillamente su 0.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-148">If your lights don't move independently of the camera, then you can safely set this value to 0.</span></span> <span data-ttu-id="6f5ab-149">Il vantaggio principale è che consentirà a Unreal di escludere diverse permutazioni degli shader, accelerando la compilazione degli shader stessi.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-149">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![Riduzione delle permutazioni degli shader per dispositivi mobili](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="6f5ab-151">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6f5ab-151">See also</span></span>
* [<span data-ttu-id="6f5ab-152">Linee guida sulle prestazioni di Unreal Engine per dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="6f5ab-152">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)