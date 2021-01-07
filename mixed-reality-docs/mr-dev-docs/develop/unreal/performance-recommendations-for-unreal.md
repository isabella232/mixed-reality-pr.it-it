---
title: Consigli sulle prestazioni per Unreal
description: Consigli per ottenere prestazioni ottimali per le app di realtà mista in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, prestazioni, ottimizzazione, impostazioni, documentazione
ms.openlocfilehash: a369a68f8ebf9b7084c22f0efa3bbf0bf5ecbebf
ms.sourcegitcommit: 9a93c9e9b3b088da942ac4386813ecf263c2e324
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2021
ms.locfileid: "97865426"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="54db5-104">Consigli sulle prestazioni per Unreal</span><span class="sxs-lookup"><span data-stu-id="54db5-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="54db5-105">Unreal Engine offre diverse funzionalità che possono migliorare le prestazioni delle app, in base agli argomenti affrontati in [Consigli sulle prestazioni per la realtà mista](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="54db5-105">Unreal Engine has several features that can increase an apps performance, all based on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span> <span data-ttu-id="54db5-106">Prima di proseguire, è consigliabile approfondire le conoscenze sui colli di bottiglia delle applicazioni, sull'analisi e la profilazione delle app in realtà mista e sulle correzioni delle prestazioni generali.</span><span class="sxs-lookup"><span data-stu-id="54db5-106">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="54db5-107">Impostazioni consigliate per il progetto Unreal</span><span class="sxs-lookup"><span data-stu-id="54db5-107">Recommended Unreal project settings</span></span>
<span data-ttu-id="54db5-108">Tutte le impostazioni seguenti sono disponibili in **Edit > Project Settings** (Modifica > Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="54db5-108">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="54db5-109">Uso del renderer VR per dispositivi mobili:</span><span class="sxs-lookup"><span data-stu-id="54db5-109">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="54db5-110">Scorri fino alla sezione **Project** (Progetto), seleziona **Target Hardware** (Hardware di destinazione) e imposta la piattaforma di destinazione su **Mobile/Tablet** (Cellulare/Tablet).</span><span class="sxs-lookup"><span data-stu-id="54db5-110">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Impostazione di dispositivi mobili come destinazione](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="54db5-112">Uso del renderer di avanzamento:</span><span class="sxs-lookup"><span data-stu-id="54db5-112">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="54db5-113">Il renderer di avanzamento è molto più efficiente per la realtà mista rispetto alla pipeline predefinita di rendering posticipato, a causa del numero di funzionalità che possono essere disattivate singolarmente.</span><span class="sxs-lookup"><span data-stu-id="54db5-113">Forward Renderer is much better for Mixed Reality than the default Deferred rendering pipeline because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="54db5-114">Per altre informazioni, vedere la [documentazione di Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span><span class="sxs-lookup"><span data-stu-id="54db5-114">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![Rendering di avanzamento](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="54db5-116">Uso delle visualizzazioni multiple dei dispositivi mobili:</span><span class="sxs-lookup"><span data-stu-id="54db5-116">Using mobile multi-view:</span></span>
    * <span data-ttu-id="54db5-117">Scorri fino alla sezione **Engine** (Motore), seleziona **Rendering**, espandi la sezione **VR** e abilita **Instanced Stereo** (Stereo con istanze) e **Mobile Multi-View** (Visualizzazioni multiple dispositivi mobili).</span><span class="sxs-lookup"><span data-stu-id="54db5-117">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="54db5-118">L'opzione Mobile HDR (HDR per dispositivi mobili) deve essere deselezionata.</span><span class="sxs-lookup"><span data-stu-id="54db5-118">Mobile HDR should be unchecked.</span></span>

![Impostazioni di rendering VR](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="54db5-120">**[Solo OpenXR]** Verificare che sia selezionato **Default** (Predefinito) o **D3D12** come **Default RHI** (RHI predefinito):</span><span class="sxs-lookup"><span data-stu-id="54db5-120">**[OpenXR only]** Ensure **Default** or **D3D12** is the selected **Default RHI**:</span></span>
    * <span data-ttu-id="54db5-121">La selezione di **D3D11** avrà un impatto negativo sulle prestazioni a causa del passaggio di rendering aggiuntivo eseguito dalla piattaforma.</span><span class="sxs-lookup"><span data-stu-id="54db5-121">Selecting **D3D11** will have a negative performance impact due to the platform performing an additional render pass.</span></span> <span data-ttu-id="54db5-122">**D3D12** dovrebbe offrire miglioramenti delle prestazioni di rendering, oltre a evitare il passaggio di rendering aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="54db5-122">**D3D12** should provide rendering performance improvements besides avoiding the additional render pass.</span></span>

![RHI predefinito](images/unreal/performance-recommendations-img-09.png)

5. <span data-ttu-id="54db5-124">Disabilitazione dell'annebbiamento ai vertici:</span><span class="sxs-lookup"><span data-stu-id="54db5-124">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="54db5-125">La funzionalità di annebbiamento ai vertici applica calcoli di annebbiamento a ogni vertice di un poligono e quindi interpola i risultati in tutta la faccia del poligono.</span><span class="sxs-lookup"><span data-stu-id="54db5-125">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="54db5-126">Se il gioco non prevede la nebbia, è consigliabile disabilitare la funzionalità di annebbiamento ai vertici per aumentare le prestazioni di ombreggiatura.</span><span class="sxs-lookup"><span data-stu-id="54db5-126">If your game does not use fog, we recommend disabling Vertex Fogging to increase shading performance.</span></span>

![Opzioni di annebbiamento ai vertici](images/unreal/performance-recommendations-img-05.png)

6. <span data-ttu-id="54db5-128">Disabilitazione del culling delle occlusioni:</span><span class="sxs-lookup"><span data-stu-id="54db5-128">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="54db5-129">Scorri fino alla sezione **Engine** (Motore), seleziona **Rendering**, espandi la sezione **Culling** e deseleziona **Occlusion Culling** (Culling occlusioni).</span><span class="sxs-lookup"><span data-stu-id="54db5-129">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="54db5-130">Se è necessario il culling delle occlusioni per il rendering di una scena molto dettagliata, è consigliabile abilitare **Support Software Occlusion Culling** (Supporta culling occlusioni software) in **Engine > Rendering** (Motore > Rendering).</span><span class="sxs-lookup"><span data-stu-id="54db5-130">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="54db5-131">Unreal opera sulla CPU ed evita query di occlusione della GPU, che influiscono negativamente sulle prestazioni di HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="54db5-131">Unreal will do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="54db5-132">Il culling delle occlusioni sulla GPU dei dispositivi mobili è lento.</span><span class="sxs-lookup"><span data-stu-id="54db5-132">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="54db5-133">In generale, è auspicabile che la GPU si occupi principalmente di rendering.</span><span class="sxs-lookup"><span data-stu-id="54db5-133">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="54db5-134">Se si ha la sensazione che l'occlusione possa aiutare le prestazioni, provare ad abilitare l'occlusione del software.</span><span class="sxs-lookup"><span data-stu-id="54db5-134">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> 

> [!NOTE]
> <span data-ttu-id="54db5-135">L'abilitazione dell'occlusione del software può peggiorare le prestazioni se si è già vincolati alla CPU da un elevato numero di chiamate di disegno.</span><span class="sxs-lookup"><span data-stu-id="54db5-135">Enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![Disabilitare il culling delle occlusioni](images/unreal/performance-recommendations-img-02.png)

7. <span data-ttu-id="54db5-137">Disabilitazione del passaggio dello stencil di profondità personalizzato:</span><span class="sxs-lookup"><span data-stu-id="54db5-137">Disabling Custom Depth-Stencil Pass:</span></span>
    * <span data-ttu-id="54db5-138">La disabilitazione dello stencil di profondità personalizzato richiede un passaggio aggiuntivo, ovvero è lento.</span><span class="sxs-lookup"><span data-stu-id="54db5-138">Disabling Custom Depth-Stencil requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="54db5-139">Anche la traslucenza è lenta in Unreal.</span><span class="sxs-lookup"><span data-stu-id="54db5-139">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="54db5-140">Per altre informazioni, vedere la [documentazione di Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span><span class="sxs-lookup"><span data-stu-id="54db5-140">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![Stencil profondità](images/unreal/performance-recommendations-img-06.png)

8. <span data-ttu-id="54db5-142">Riduzione delle mappe delle ombreggiature a cascata:</span><span class="sxs-lookup"><span data-stu-id="54db5-142">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="54db5-143">La riduzione del numero di mappe delle ombreggiature determina un miglioramento delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="54db5-143">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="54db5-144">In genere, è consigliabile impostare la proprietà su 1 a meno che non esista una perdita di qualità visibile.</span><span class="sxs-lookup"><span data-stu-id="54db5-144">Generally, you should set the property to 1 unless there's a visible quality loss.</span></span> 

![Mappe delle ombreggiature a cascata](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="54db5-146">Impostazioni facoltative</span><span class="sxs-lookup"><span data-stu-id="54db5-146">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="54db5-147">Le impostazioni seguenti possono migliorare le prestazioni, causando tuttavia la disabilitazione di alcune funzionalità.</span><span class="sxs-lookup"><span data-stu-id="54db5-147">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="54db5-148">Usare queste impostazioni solo se si è certi di non dover usare le funzionalità in questione.</span><span class="sxs-lookup"><span data-stu-id="54db5-148">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="54db5-149">Riduzione delle permutazioni degli shader per dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="54db5-149">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="54db5-150">Se le luci non si muovono in modo indipendente dalla fotocamera, è possibile impostare il valore della proprietà su 0.</span><span class="sxs-lookup"><span data-stu-id="54db5-150">If your lights don't move independently of the camera, then you can safely set the property value to 0.</span></span> <span data-ttu-id="54db5-151">Il vantaggio principale è che consentirà a Unreal di escludere diverse permutazioni degli shader, accelerando la compilazione degli shader stessi.</span><span class="sxs-lookup"><span data-stu-id="54db5-151">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![Riduzione delle permutazioni degli shader per dispositivi mobili](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="54db5-153">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="54db5-153">See also</span></span>
* [<span data-ttu-id="54db5-154">Linee guida sulle prestazioni di Unreal Engine per dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="54db5-154">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)