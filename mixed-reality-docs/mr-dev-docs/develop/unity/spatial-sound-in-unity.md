---
title: Audio spaziale in Unity
description: Viene illustrato come riprodurre e attenuare i suoni spaziali da uno specifico punto 3D nella scena Unity con esempi.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, audio spaziale, HRTF, dimensioni della stanza, auricolare in realtà mista, auricolare di realtà mista di Windows, auricolare realtà virtuale, MRTK, Toolkit realtà mista, Spatializer, Reverb
ms.openlocfilehash: ec2703aa89925cb68860670f574a1e43f672e247
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009271"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="c8298-104">Audio spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="c8298-104">Spatial sound in Unity</span></span>

<span data-ttu-id="c8298-105">Questa pagina contiene collegamenti a risorse per il suono spaziale in Unity.</span><span class="sxs-lookup"><span data-stu-id="c8298-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="c8298-106">Opzioni di Spatializer</span><span class="sxs-lookup"><span data-stu-id="c8298-106">Spatializer options</span></span>

<span data-ttu-id="c8298-107">Le opzioni di Spatializer per le applicazioni di realtà mista includono:</span><span class="sxs-lookup"><span data-stu-id="c8298-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="c8298-108">Unity fornisce il *HRTF MS Spatializer* come parte del pacchetto facoltativo di *realtà mista di Windows* .</span><span class="sxs-lookup"><span data-stu-id="c8298-108">Unity provides the *MS HRTF Spatializer* as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="c8298-109">Viene eseguito sulla CPU in un'architettura a più costi ' single-source '.</span><span class="sxs-lookup"><span data-stu-id="c8298-109">Runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="c8298-110">Fornito per la compatibilità con le versioni precedenti con le applicazioni HoloLens originali.</span><span class="sxs-lookup"><span data-stu-id="c8298-110">Provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="c8298-111">*Microsoft Spatializer* è disponibile nel [repository GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="c8298-111">The *Microsoft Spatializer* is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="c8298-112">Usa un'architettura a più livelli di costo inferiore.</span><span class="sxs-lookup"><span data-stu-id="c8298-112">Uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="c8298-113">Offload a un acceleratore hardware in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c8298-113">Offloaded to a hardware accelerator on the HoloLens 2.</span></span> 

<span data-ttu-id="c8298-114">Per le nuove applicazioni, è consigliabile *Microsoft Spatializer*.</span><span class="sxs-lookup"><span data-stu-id="c8298-114">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="c8298-115">Abilita spazializzazione</span><span class="sxs-lookup"><span data-stu-id="c8298-115">Enable spatialization</span></span>

<span data-ttu-id="c8298-116">Usare [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) per installare _Microsoft. SpatialAudio. Spatializer. Unity_ e scegliere **Microsoft Spatializer** nelle impostazioni audio del progetto.</span><span class="sxs-lookup"><span data-stu-id="c8298-116">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="c8298-117">Quindi:</span><span class="sxs-lookup"><span data-stu-id="c8298-117">Then:</span></span>
* <span data-ttu-id="c8298-118">Alleghi un' **origine audio** a un oggetto nella gerarchia</span><span class="sxs-lookup"><span data-stu-id="c8298-118">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="c8298-119">Selezionare la casella di controllo **Abilita spazializzazione**</span><span class="sxs-lookup"><span data-stu-id="c8298-119">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="c8298-120">Spostare il dispositivo di scorrimento di **Blend spaziale** su "1"</span><span class="sxs-lookup"><span data-stu-id="c8298-120">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="c8298-121">Verificare che l'audio spaziale sia abilitato nella workstation per sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="c8298-121">Ensure spatial audio is enabled on your developer workstation.</span></span> 
    * <span data-ttu-id="c8298-122">Fare clic con il pulsante destro del mouse sull'icona del volume sulla barra delle applicazioni e verificare che l'audio spaziale sia impostato su un valore diverso da "off".</span><span class="sxs-lookup"><span data-stu-id="c8298-122">Right-click on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off".</span></span> 
    * <span data-ttu-id="c8298-123">Scegliere **Windows Sonic per le cuffie** per ottenere la migliore rappresentazione di ciò che verrà ascoltato in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c8298-123">Choose **Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

>[!NOTE]
><span data-ttu-id="c8298-124">Se si verifica un errore in Unity che non è in grado di caricare il plug-in Microsoft. SpatialAudio. Spatializer. Unity, perché una delle relative dipendenze non è presente, verificare di disporre della versione più recente di [Microsoft Visual C++ ridistribuibile](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installata nel computer.</span><span class="sxs-lookup"><span data-stu-id="c8298-124">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="c8298-125">Per altre informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="c8298-125">For more information, see:</span></span>
* [<span data-ttu-id="c8298-126">Repository GitHub Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="c8298-126">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="c8298-127">Esercitazione di Spatializer di Microsoft</span><span class="sxs-lookup"><span data-stu-id="c8298-127">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
* [<span data-ttu-id="c8298-128">Documentazione dell'origine audio di Unity</span><span class="sxs-lookup"><span data-stu-id="c8298-128">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="c8298-129">Documentazione di Unity Spatializer</span><span class="sxs-lookup"><span data-stu-id="c8298-129">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="c8298-130">Attenuazione basate sulla distanza</span><span class="sxs-lookup"><span data-stu-id="c8298-130">Distance-based attenuation</span></span>

<span data-ttu-id="c8298-131">Il decadimento basato sulla distanza predefinito di Unity ha una distanza minima di 1 metro e una distanza massima di 500 metri, con un attenuazione logaritmico.</span><span class="sxs-lookup"><span data-stu-id="c8298-131">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="c8298-132">Queste impostazioni possono essere usate per lo scenario in uso oppure è possibile che le origini siano attenuate troppo rapidamente o troppo lentamente.</span><span class="sxs-lookup"><span data-stu-id="c8298-132">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="c8298-133">Per altre informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="c8298-133">For more information, see:</span></span>
* <span data-ttu-id="c8298-134">[Progettazione audio in realtà mista](../../design/spatial-sound-design.md) per le impostazioni consigliate.</span><span class="sxs-lookup"><span data-stu-id="c8298-134">[Sound design in mixed reality](../../design/spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="c8298-135">[Documentazione dell'origine audio di Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) per istruzioni sull'impostazione di queste curve.</span><span class="sxs-lookup"><span data-stu-id="c8298-135">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="c8298-136">Riverbero</span><span class="sxs-lookup"><span data-stu-id="c8298-136">Reverb</span></span>

<span data-ttu-id="c8298-137">_Microsoft Spatializer_ Disabilita gli effetti post-Spatializer per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="c8298-137">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="c8298-138">Per abilitare il riverbero e altri effetti per le origini spaziali:</span><span class="sxs-lookup"><span data-stu-id="c8298-138">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="c8298-139">Alleghi il componente del **livello di invio dell'effetto chat** a ogni origine</span><span class="sxs-lookup"><span data-stu-id="c8298-139">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="c8298-140">Modificare la curva del livello di invio per ogni origine, per controllare il guadagno sull'audio restituito al grafico per l'elaborazione degli effetti</span><span class="sxs-lookup"><span data-stu-id="c8298-140">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="c8298-141">Per informazioni dettagliate, vedere [il capitolo 5 dell'esercitazione su Spatializer](tutorials/unity-spatial-audio-ch5.md) .</span><span class="sxs-lookup"><span data-stu-id="c8298-141">See [Chapter 5 of the spatializer tutorial](tutorials/unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="c8298-142">Esempi di suoni spaziali Unity</span><span class="sxs-lookup"><span data-stu-id="c8298-142">Unity spatial sound examples</span></span>

<span data-ttu-id="c8298-143">Per esempi di suoni spaziali in Unity, vedere:</span><span class="sxs-lookup"><span data-stu-id="c8298-143">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="c8298-144">Demo di MRTK</span><span class="sxs-lookup"><span data-stu-id="c8298-144">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="c8298-145">[Progetto di esempio Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="c8298-145">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="c8298-146">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="c8298-146">Next Development Checkpoint</span></span>

<span data-ttu-id="c8298-147">Se si sta seguendo il percorso di sviluppo di Unity, è possibile esplorare i blocchi predefiniti di base della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="c8298-147">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="c8298-148">Da qui, è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="c8298-148">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c8298-149">Testo</span><span class="sxs-lookup"><span data-stu-id="c8298-149">Text</span></span>](text-in-unity.md)

<span data-ttu-id="c8298-150">In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="c8298-150">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c8298-151">Esperienze condivise</span><span class="sxs-lookup"><span data-stu-id="c8298-151">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="c8298-152">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="c8298-152">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8298-153">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c8298-153">See also</span></span>

* [<span data-ttu-id="c8298-154">Progettazione audio in realtà mista</span><span class="sxs-lookup"><span data-stu-id="c8298-154">Sound design in mixed reality</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="c8298-155">Esercitazione di Spatializer di Microsoft</span><span class="sxs-lookup"><span data-stu-id="c8298-155">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
