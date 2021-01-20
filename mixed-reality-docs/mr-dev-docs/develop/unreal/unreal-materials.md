---
title: Raccomandazioni sui materiali in Unreal
description: Panoramica dei materiali in Unreal Engine.
author: hferrone
ms.author: safarooq
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal Engine 4, UE4, HoloLens, HoloLens 2, sviluppo, materiali, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi, cuffie per realtà mista, auricolare di realtà mista di Windows, auricolare di realtà virtuale
ms.openlocfilehash: bfe70e730c5fbd6e5d103737b03e76bfd0ab65f6
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580791"
---
# <a name="material-recommendations-in-unreal"></a><span data-ttu-id="4cdad-104">Raccomandazioni sui materiali in Unreal</span><span class="sxs-lookup"><span data-stu-id="4cdad-104">Material recommendations in Unreal</span></span>

<span data-ttu-id="4cdad-105">I materiali usati possono influenzare direttamente il modo in cui i progetti vengono eseguiti in Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="4cdad-105">The materials you use can directly affect how well your projects run in Unreal Engine.</span></span> <span data-ttu-id="4cdad-106">Questa pagina funge da avvio rapido per le impostazioni di base che è necessario usare per ottenere prestazioni ottimali dalle applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="4cdad-106">This page acts as a quick-start for the basic settings you should be using to get the best performance out of your mixed reality applications.</span></span>

## <a name="using-customizeduvs"></a><span data-ttu-id="4cdad-107">Uso di CustomizedUVs</span><span class="sxs-lookup"><span data-stu-id="4cdad-107">Using CustomizedUVs</span></span>

<span data-ttu-id="4cdad-108">Se è necessario fornire il rivestimento UV sul materiale, usare CustomizedUVs invece di modificare direttamente l'UV del nodo di trama.</span><span class="sxs-lookup"><span data-stu-id="4cdad-108">If you need to provide UV tiling on your material, use CustomizedUVs rather than modifying the UV of the texture node directly.</span></span> <span data-ttu-id="4cdad-109">CustomizedUVs consentono di modificare le UV nei vertex shader invece che nel pixel shader.</span><span class="sxs-lookup"><span data-stu-id="4cdad-109">CustomizedUVs let you manipulate UVs in the Vertex shaders rather than the Pixel shader.</span></span>

![Impostazioni del materiale in Unreal](images/unreal-materials-img-01c.png)

<span data-ttu-id="4cdad-111">È possibile trovare i dettagli relativi al materiale nella [documentazione di Unreal Engine](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) ed esempi di procedure consigliate negli screenshot seguenti:</span><span class="sxs-lookup"><span data-stu-id="4cdad-111">You can find material details in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) and best practice examples in the screenshots below:</span></span>

<span data-ttu-id="4cdad-112">[ ![ Impostazioni del materiale consigliate nella ](images/unreal-materials-img-01.png) configurazione del ](images/unreal-materials-img-01.png#lightbox) 
 *materiale sconsigliato*</span><span class="sxs-lookup"><span data-stu-id="4cdad-112">[ ![Recommended material settings in Unreal](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox)
*Recommended material setup*</span></span>

<span data-ttu-id="4cdad-113">[ ![ Impostazioni del materiale non consigliate in ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)un' 
 *installazione non consigliata di materiali*</span><span class="sxs-lookup"><span data-stu-id="4cdad-113">[ ![Non recommended material settings in Unreal](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)
*Non-recommended material setup*</span></span>

## <a name="changing-blend-mode"></a><span data-ttu-id="4cdad-114">Modifica della modalità di Blend</span><span class="sxs-lookup"><span data-stu-id="4cdad-114">Changing Blend Mode</span></span>

<span data-ttu-id="4cdad-115">È consigliabile impostare la modalità di Blend su opaca a meno che non esista un motivo sicuro per eseguire altre operazioni.</span><span class="sxs-lookup"><span data-stu-id="4cdad-115">We recommend setting the blend mode to opaque unless there's a strong reason to do otherwise.</span></span> <span data-ttu-id="4cdad-116">I materiali mascherati e traslucidi sono lenti.</span><span class="sxs-lookup"><span data-stu-id="4cdad-116">Masked and Translucent materials are slow.</span></span> <span data-ttu-id="4cdad-117">Per ulteriori informazioni sui materiali, vedere la [documentazione relativa a Unreal Engine](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span><span class="sxs-lookup"><span data-stu-id="4cdad-117">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Modifica della modalità di Blend](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a><span data-ttu-id="4cdad-119">Aggiornamento dell'illuminazione per dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="4cdad-119">Updating lighting for mobile</span></span>

<span data-ttu-id="4cdad-120">La precisione completa deve essere disattivata.</span><span class="sxs-lookup"><span data-stu-id="4cdad-120">Full precision should be turned off.</span></span> <span data-ttu-id="4cdad-121">L'illuminazione lightmap può essere disattivata trasformando le informazioni direzionali.</span><span class="sxs-lookup"><span data-stu-id="4cdad-121">Lightmap lighting can be dialed down by turning of directional information.</span></span> <span data-ttu-id="4cdad-122">Se disabilitata, l'illuminazione da lightmaps sarà piatta, ma più economica.</span><span class="sxs-lookup"><span data-stu-id="4cdad-122">When disabled, lighting from lightmaps will be flat but cheaper.</span></span>

![Impostazioni del materiale mobile in Unreal](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a><span data-ttu-id="4cdad-124">Regolazione dell'ombreggiatura diretta</span><span class="sxs-lookup"><span data-stu-id="4cdad-124">Adjusting Forward Shading</span></span>

<span data-ttu-id="4cdad-125">Queste opzioni migliorano la fedeltà visiva a scapito delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="4cdad-125">These options improve visual fidelity at the cost of performance.</span></span> <span data-ttu-id="4cdad-126">Devono essere disattivate per ottenere prestazioni ottimali.</span><span class="sxs-lookup"><span data-stu-id="4cdad-126">They should be turned off for maximum performance.</span></span>

![Impostazioni del materiale ombreggiatura di avanzamento in Unreal](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a><span data-ttu-id="4cdad-128">Impostazione della traslucidità del materiale</span><span class="sxs-lookup"><span data-stu-id="4cdad-128">Setting material translucency</span></span>

<span data-ttu-id="4cdad-129">Indica che il materiale traslucido non deve essere influenzato da Bloom o DOF.</span><span class="sxs-lookup"><span data-stu-id="4cdad-129">Indicates that the translucent material should not be affected by bloom or DOF.</span></span> <span data-ttu-id="4cdad-130">Poiché entrambi gli effetti sono rari in MR, questa impostazione deve essere attiva per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="4cdad-130">Since both those effects are rare in MR, this setting should be on by default.</span></span>

![Impostazione della traslucidità separata per dispositivi mobili in Unreal](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a><span data-ttu-id="4cdad-132">Impostazioni facoltative</span><span class="sxs-lookup"><span data-stu-id="4cdad-132">Optional settings</span></span>

<span data-ttu-id="4cdad-133">Le impostazioni seguenti possono migliorare le prestazioni, ma si noti che disabilitano alcune funzionalità.</span><span class="sxs-lookup"><span data-stu-id="4cdad-133">The following settings may improve performance, but note that they disable certain features.</span></span> <span data-ttu-id="4cdad-134">Usare queste impostazioni solo se si è certi di non dover usare le funzionalità in questione.</span><span class="sxs-lookup"><span data-stu-id="4cdad-134">Only use these settings if you're sure you don't need the features in question.</span></span>

![Impostazioni del materiale facoltativo in Unreal](images/unreal-materials-img-06.jpg)

<span data-ttu-id="4cdad-136">Se il materiale non richiede riflessi o lucentezza, l'impostazione di questa opzione può offrire un notevole miglioramento delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="4cdad-136">If your material doesn't require reflections or shine, then setting this option can provide a tremendous performance boost.</span></span> <span data-ttu-id="4cdad-137">Nel test interno, è veloce come "spento" e fornisce informazioni sull'illuminazione.</span><span class="sxs-lookup"><span data-stu-id="4cdad-137">In internal testing, it's as fast as "unlit" while providing lighting information.</span></span>

## <a name="best-practices"></a><span data-ttu-id="4cdad-138">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="4cdad-138">Best practices</span></span>

<span data-ttu-id="4cdad-139">Di seguito sono illustrate le procedure consigliate relative ai materiali.</span><span class="sxs-lookup"><span data-stu-id="4cdad-139">The following aren't "settings" as much as they're best practices related to Materials.</span></span>

<span data-ttu-id="4cdad-140">Quando si creano parametri, è preferibile usare "parametri statici" laddove possibile.</span><span class="sxs-lookup"><span data-stu-id="4cdad-140">When creating parameters, prefer to use "Static Parameters" wherever possible.</span></span> <span data-ttu-id="4cdad-141">È possibile utilizzare le opzioni statiche per rimuovere un intero ramo di un materiale senza costi di Runtime.</span><span class="sxs-lookup"><span data-stu-id="4cdad-141">Static Switches can be used to remove an entire branch of a material with no runtime cost.</span></span> <span data-ttu-id="4cdad-142">Le istanze possono avere valori diversi, rendendo possibile la configurazione di uno shader basato su modelli senza perdita delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="4cdad-142">Instances can have different values, making it possible to have a templated shader set up with no performance loss.</span></span> <span data-ttu-id="4cdad-143">Lo svantaggio è che vengono create diverse permutazioni che comporteranno la ricompilazione dello shader.</span><span class="sxs-lookup"><span data-stu-id="4cdad-143">The downside, is that several permutations are created that will cause shader recompilation.</span></span> <span data-ttu-id="4cdad-144">Provare a ridurre al minimo il numero di parametri statici nel materiale e il numero di permutazioni dei parametri statici utilizzati.</span><span class="sxs-lookup"><span data-stu-id="4cdad-144">Try to minimize the number of static parameters in the material and the number of permutations of those static parameters that are used.</span></span> <span data-ttu-id="4cdad-145">Per ulteriori informazioni sui parametri del materiale di rendering, vedere la [documentazione di Unreal Engine](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span><span class="sxs-lookup"><span data-stu-id="4cdad-145">You can find more details on rendering material parameters in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span></span>

![Procedure consigliate per le impostazioni del materiale](images/unreal-materials-img-07.jpg)

<span data-ttu-id="4cdad-147">Quando si creano istanze di materiale, è necessario assegnare una preferenza alla **costante dell'istanza Material** su un'istanza del materiale dinamica.</span><span class="sxs-lookup"><span data-stu-id="4cdad-147">When creating Material Instances, preference should be given to **Material Instance Constant** over Material Instance Dynamic.</span></span> <span data-ttu-id="4cdad-148">La **costante dell'istanza Material** è un materiale di istanza che viene calcolato solo una volta prima del runtime.</span><span class="sxs-lookup"><span data-stu-id="4cdad-148">**Material Instance Constant** is an instanced Material that calculates only once before runtime.</span></span>

<span data-ttu-id="4cdad-149">L'istanza del materiale creata tramite il browser del contenuto (**fare clic con il pulsante destro del mouse > Crea istanza del materiale**) è una costante dell'istanza del materiale.</span><span class="sxs-lookup"><span data-stu-id="4cdad-149">The material instance created via the Content Browser (**right-click > Create Material Instance**) is a Material Instance Constant.</span></span> <span data-ttu-id="4cdad-150">L'istanza del materiale dinamica viene creata tramite codice.</span><span class="sxs-lookup"><span data-stu-id="4cdad-150">Material Instance Dynamic are created via code.</span></span> <span data-ttu-id="4cdad-151">Per ulteriori informazioni sulle istanze di materiale, vedere la [documentazione di Unreal Engine](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span><span class="sxs-lookup"><span data-stu-id="4cdad-151">You can find more details on material instances in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span></span>

![Creazione di istanze di materiale in Unreal](images/unreal-materials-img-08.png)

<span data-ttu-id="4cdad-153">Tenere sotto controllo la complessità dei materiali e degli shader.</span><span class="sxs-lookup"><span data-stu-id="4cdad-153">Keep an eye on the complexity of your materials/shaders.</span></span> <span data-ttu-id="4cdad-154">È possibile visualizzare il costo del materiale su diverse piattaforme facendo clic sull'icona Statistiche piattaforma.</span><span class="sxs-lookup"><span data-stu-id="4cdad-154">You can view the cost of your Material on various platforms by clicking on the Platform Stats icon.</span></span> <span data-ttu-id="4cdad-155">Per ulteriori informazioni sui materiali, vedere la documentazione di [Unreal Engine](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span><span class="sxs-lookup"><span data-stu-id="4cdad-155">You can also find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Creazione di impostazioni dinamiche dell'istanza Material in Unreal](images/unreal-materials-img-09.png)

<span data-ttu-id="4cdad-157">È possibile ottenere una rapida idea della complessità relativa dello shader tramite la [modalità di visualizzazione](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)complessità dello shader.</span><span class="sxs-lookup"><span data-stu-id="4cdad-157">You can get a quick idea of the relative complexity of your shader via the Shader Complexity [View mode](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).</span></span>

* <span data-ttu-id="4cdad-158">Tasto di scelta rapida modalità di visualizzazione: Alt + 8</span><span class="sxs-lookup"><span data-stu-id="4cdad-158">View Mode Hotkey: Alt + 8</span></span>
* <span data-ttu-id="4cdad-159">Comando della console: ViewMode shadercomplexity</span><span class="sxs-lookup"><span data-stu-id="4cdad-159">Console command: viewmode shadercomplexity</span></span>

![Complessità del materiale in Unreal](images/unreal-materials-img-10.png)

## <a name="see-also"></a><span data-ttu-id="4cdad-161">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4cdad-161">See also</span></span>
* [<span data-ttu-id="4cdad-162">Materiali mobili</span><span class="sxs-lookup"><span data-stu-id="4cdad-162">Mobile materials</span></span>](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [<span data-ttu-id="4cdad-163">Modalità di visualizzazione</span><span class="sxs-lookup"><span data-stu-id="4cdad-163">View modes</span></span>](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [<span data-ttu-id="4cdad-164">Istanze del materiale</span><span class="sxs-lookup"><span data-stu-id="4cdad-164">Material instances</span></span>](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
