---
title: Consigli sulle prestazioni per Unreal
description: Consigli per ottenere prestazioni ottimali per le app di realtà mista in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, prestazioni, ottimizzazione, impostazioni, documentazione
ms.openlocfilehash: 21bd3ee9fb7db23eab9365e41adfd0033aa0046e
ms.sourcegitcommit: 520c69eb761ad6083b36f448bbcfab89e343e40d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2020
ms.locfileid: "94549129"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="065b7-104">Consigli sulle prestazioni per Unreal</span><span class="sxs-lookup"><span data-stu-id="065b7-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="065b7-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="065b7-105">Overview</span></span>

<span data-ttu-id="065b7-106">Questo articolo si basa sugli argomenti affrontati in [Consigli sulle prestazioni per la realtà mista](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), ma si concentra in particolare su funzionalità specifiche di Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="065b7-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="065b7-107">Prima di proseguire, è consigliabile approfondire le conoscenze sui colli di bottiglia delle applicazioni, sull'analisi e la profilazione delle app in realtà mista e sulle correzioni delle prestazioni generali.</span><span class="sxs-lookup"><span data-stu-id="065b7-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="065b7-108">Impostazioni consigliate per il progetto Unreal</span><span class="sxs-lookup"><span data-stu-id="065b7-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="065b7-109">Tutte le impostazioni seguenti sono disponibili in **Edit > Project Settings** (Modifica > Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="065b7-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="065b7-110">Uso del renderer VR per dispositivi mobili:</span><span class="sxs-lookup"><span data-stu-id="065b7-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="065b7-111">Scorri fino alla sezione **Project** (Progetto), seleziona **Target Hardware** (Hardware di destinazione) e imposta la piattaforma di destinazione su **Mobile/Tablet** (Cellulare/Tablet).</span><span class="sxs-lookup"><span data-stu-id="065b7-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Impostazione di dispositivi mobili come destinazione](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="065b7-113">Uso del renderer di avanzamento:</span><span class="sxs-lookup"><span data-stu-id="065b7-113">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="065b7-114">Questa funzionalità è molto più efficiente per la realtà mista rispetto alla pipeline predefinita di rendering posticipato.</span><span class="sxs-lookup"><span data-stu-id="065b7-114">This feature is much better for Mixed Reality than the default Deferred rendering pipeline.</span></span> <span data-ttu-id="065b7-115">Questo è dovuto principalmente al numero di funzionalità che è possibile disabilitare singolarmente.</span><span class="sxs-lookup"><span data-stu-id="065b7-115">This is primarily because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="065b7-116">Per altre informazioni, vedere la [documentazione di Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span><span class="sxs-lookup"><span data-stu-id="065b7-116">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![Rendering di avanzamento](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="065b7-118">Uso delle visualizzazioni multiple dei dispositivi mobili:</span><span class="sxs-lookup"><span data-stu-id="065b7-118">Using mobile multi-view:</span></span>
    * <span data-ttu-id="065b7-119">Scorri fino alla sezione **Engine** (Motore), seleziona **Rendering**, espandi la sezione **VR** e abilita **Instanced Stereo** (Stereo con istanze) e **Mobile Multi-View** (Visualizzazioni multiple dispositivi mobili).</span><span class="sxs-lookup"><span data-stu-id="065b7-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="065b7-120">L'opzione Mobile HDR (HDR per dispositivi mobili) deve essere deselezionata.</span><span class="sxs-lookup"><span data-stu-id="065b7-120">Mobile HDR should be unchecked.</span></span>

![Impostazioni di rendering VR](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="065b7-122">Verificare che sia selezionato **Default** (Predefinito) o **D3D12** come **Default RHI** (RHI predefinito) quando si usa OpenXR.</span><span class="sxs-lookup"><span data-stu-id="065b7-122">Ensure **Default** or **D3D12** is the selected **Default RHI** when using OpenXR.</span></span>
    * <span data-ttu-id="065b7-123">La selezione di **D3D11** avrà un impatto negativo sulle prestazioni a causa del passaggio di rendering aggiuntivo eseguito dalla piattaforma.</span><span class="sxs-lookup"><span data-stu-id="065b7-123">Selecting **D3D11** will have a negative performance impact due to the platform performing an additional render pass.</span></span> <span data-ttu-id="065b7-124">**D3D12** dovrebbe offrire miglioramenti delle prestazioni di rendering, oltre a evitare il passaggio di rendering aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="065b7-124">**D3D12** should provide rendering performance improvements besides avoiding the additional render pass.</span></span>

![RHI predefinito](images/unreal/performance-recommendations-img-09.png)

5. <span data-ttu-id="065b7-126">Disabilitazione dell'annebbiamento ai vertici:</span><span class="sxs-lookup"><span data-stu-id="065b7-126">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="065b7-127">La funzionalità di annebbiamento ai vertici applica calcoli di annebbiamento a ogni vertice di un poligono e quindi interpola i risultati in tutta la faccia del poligono.</span><span class="sxs-lookup"><span data-stu-id="065b7-127">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="065b7-128">Se il gioco non prevede la nebbia, è necessario scegliere questa impostazione per disabilitare la nebbia e aumentare le prestazioni di ombreggiatura.</span><span class="sxs-lookup"><span data-stu-id="065b7-128">If your game does not use fog, you should choose this setting to disable fog to increase shading performance.</span></span>

![Opzioni di annebbiamento ai vertici](images/unreal/performance-recommendations-img-05.png)

6. <span data-ttu-id="065b7-130">Disabilitazione del culling delle occlusioni:</span><span class="sxs-lookup"><span data-stu-id="065b7-130">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="065b7-131">Scorri fino alla sezione **Engine** (Motore), seleziona **Rendering**, espandi la sezione **Culling** e deseleziona **Occlusion Culling** (Culling occlusioni).</span><span class="sxs-lookup"><span data-stu-id="065b7-131">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="065b7-132">Se è necessario il culling delle occlusioni per il rendering di una scena molto dettagliata, è consigliabile abilitare **Support Software Occlusion Culling** (Supporta culling occlusioni software) in **Engine > Rendering** (Motore > Rendering).</span><span class="sxs-lookup"><span data-stu-id="065b7-132">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="065b7-133">Ciò consente ad Unreal di operare sulla CPU ed evitare query di occlusione della GPU, che influiscono negativamente sulle prestazioni di HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="065b7-133">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="065b7-134">Il culling delle occlusioni sulla GPU dei dispositivi mobili è lento.</span><span class="sxs-lookup"><span data-stu-id="065b7-134">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="065b7-135">In generale, è auspicabile che la GPU si occupi principalmente di rendering.</span><span class="sxs-lookup"><span data-stu-id="065b7-135">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="065b7-136">Se si ha la sensazione che l'occlusione possa aiutare le prestazioni, provare ad abilitare l'occlusione del software.</span><span class="sxs-lookup"><span data-stu-id="065b7-136">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> <span data-ttu-id="065b7-137">Si noti che l'abilitazione dell'occlusione del software potrebbe peggiorare le prestazioni se si è già vincolati alla CPU da un elevato numero di chiamate di disegno.</span><span class="sxs-lookup"><span data-stu-id="065b7-137">Note that enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![Disabilitare il culling delle occlusioni](images/unreal/performance-recommendations-img-02.png)

7. <span data-ttu-id="065b7-139">Disabilitazione del passaggio dello stencil di profondità personalizzato:</span><span class="sxs-lookup"><span data-stu-id="065b7-139">Disabling Custom Depth-Stencil Pass:</span></span>
    * <span data-ttu-id="065b7-140">Questa funzionalità richiede un'ulteriore approvazione perché è lenta.</span><span class="sxs-lookup"><span data-stu-id="065b7-140">This feature requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="065b7-141">Anche la traslucenza è lenta in Unreal.</span><span class="sxs-lookup"><span data-stu-id="065b7-141">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="065b7-142">Per altre informazioni, vedere la [documentazione di Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span><span class="sxs-lookup"><span data-stu-id="065b7-142">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![Stencil profondità](images/unreal/performance-recommendations-img-06.png)

8. <span data-ttu-id="065b7-144">Riduzione delle mappe delle ombreggiature a cascata:</span><span class="sxs-lookup"><span data-stu-id="065b7-144">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="065b7-145">La riduzione del numero di mappe delle ombreggiature determina un miglioramento delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="065b7-145">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="065b7-146">In generale, questo valore deve essere impostato su 1, altrimenti si verifica una visibile perdita di qualità.</span><span class="sxs-lookup"><span data-stu-id="065b7-146">Generally, this should be set to 1 unless there is a visible quality loss.</span></span> 

![Mappe delle ombreggiature a cascata](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="065b7-148">Impostazioni facoltative</span><span class="sxs-lookup"><span data-stu-id="065b7-148">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="065b7-149">Le impostazioni seguenti possono migliorare le prestazioni, causando tuttavia la disabilitazione di alcune funzionalità.</span><span class="sxs-lookup"><span data-stu-id="065b7-149">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="065b7-150">Usare queste impostazioni solo se si è certi di non dover usare le funzionalità in questione.</span><span class="sxs-lookup"><span data-stu-id="065b7-150">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="065b7-151">Riduzione delle permutazioni degli shader per dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="065b7-151">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="065b7-152">Se le luci non si muovono in modo indipendente dalla fotocamera, è possibile impostare questo valore tranquillamente su 0.</span><span class="sxs-lookup"><span data-stu-id="065b7-152">If your lights don't move independently of the camera, then you can safely set this value to 0.</span></span> <span data-ttu-id="065b7-153">Il vantaggio principale è che consentirà a Unreal di escludere diverse permutazioni degli shader, accelerando la compilazione degli shader stessi.</span><span class="sxs-lookup"><span data-stu-id="065b7-153">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![Riduzione delle permutazioni degli shader per dispositivi mobili](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="065b7-155">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="065b7-155">See also</span></span>
* [<span data-ttu-id="065b7-156">Linee guida sulle prestazioni di Unreal Engine per dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="065b7-156">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)