---
title: Progettazione di contenuto per la visualizzazione olografica
description: Linee guida per la progettazione e procedure consigliate per la visualizzazione olografica
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Progettazione dell'interfaccia utente, schermo olografico, progettazione del contenuto, tema scuro, tema chiaro, auricolare realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, progettazione, pixel
ms.openlocfilehash: ea3fbda7aff80f0878521deb433c88b16abeab19
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702637"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="1aa44-104">Progettazione di contenuto per la visualizzazione olografica</span><span class="sxs-lookup"><span data-stu-id="1aa44-104">Designing content for holographic display</span></span>

![Posizione della mano del lato ulnare](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="1aa44-106">Quando si progettano contenuti per le visualizzazioni olografiche, è necessario prendere in considerazione diversi elementi per ottenere un'esperienza ottimale.</span><span class="sxs-lookup"><span data-stu-id="1aa44-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="1aa44-107">Di seguito sono elencate alcune delle raccomandazioni ed è possibile ottenere altre informazioni sulle caratteristiche delle visualizzazioni olografiche nella pagina [colore, luce e materiali](color-light-and-materials.md) .</span><span class="sxs-lookup"><span data-stu-id="1aa44-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="1aa44-108">Problemi con colore luminoso su larga superficie</span><span class="sxs-lookup"><span data-stu-id="1aa44-108">Challenges with bright color on a large surface</span></span> 
<span data-ttu-id="1aa44-109">In base alla ricerca e al test degli utenti su diversi tipi di esperienza HoloLens, abbiamo scoperto che l'uso di colori luminosi in un'area di grandi dimensioni della visualizzazione può causare diversi problemi:</span><span class="sxs-lookup"><span data-stu-id="1aa44-109">Based on our user research and testing on various types of HoloLens experiences, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="1aa44-110">**Affaticamento degli occhi**</span><span class="sxs-lookup"><span data-stu-id="1aa44-110">**Eye fatigue**</span></span> 

<span data-ttu-id="1aa44-111">Poiché la visualizzazione olografica è additiva, colore chiaro usa una maggiore luminosità per visualizzare gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="1aa44-111">Since holographic display is additive, bright color uses more light to display holograms.</span></span> <span data-ttu-id="1aa44-112">Un colore chiaro e a tinta unita in un'area di grandi dimensioni dello schermo può causare la fatica degli occhi per l'utente.</span><span class="sxs-lookup"><span data-stu-id="1aa44-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="1aa44-113">**Occlusione mano**</span><span class="sxs-lookup"><span data-stu-id="1aa44-113">**Hand occlusion**</span></span> 

<span data-ttu-id="1aa44-114">Il colore luminoso rende difficile per l'utente vedere le proprie mani quando si interagisce direttamente con gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="1aa44-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="1aa44-115">Poiché l'utente non può visualizzare le loro mani, diventa difficile percepire la profondità o la distanza tra la mano/il dito e la superficie di destinazione.</span><span class="sxs-lookup"><span data-stu-id="1aa44-115">Since the user cannot see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="1aa44-116">Il cursore del dito aiuta a compensare questo problema, ma può comunque essere difficile su una superficie bianca luminosa.</span><span class="sxs-lookup"><span data-stu-id="1aa44-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="1aa44-117">![Occlusione di colore e mano ](images/color_handocclusion.jpg)
 *difficili da visualizzare la mano sul Backplate del contenuto colorato*</span><span class="sxs-lookup"><span data-stu-id="1aa44-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="1aa44-118">**Uniformità del colore**</span><span class="sxs-lookup"><span data-stu-id="1aa44-118">**Color uniformity**</span></span>

<span data-ttu-id="1aa44-119">A causa delle caratteristiche delle visualizzazioni olografiche, una grande area luminosa sullo schermo può diventare chiazzata.</span><span class="sxs-lookup"><span data-stu-id="1aa44-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="1aa44-120">Con le combinazioni di colori scure è possibile ridurre il problema.</span><span class="sxs-lookup"><span data-stu-id="1aa44-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines"></a><span data-ttu-id="1aa44-121">Linee guida di progettazione</span><span class="sxs-lookup"><span data-stu-id="1aa44-121">Design guidelines</span></span>

<span data-ttu-id="1aa44-122">**Usa colore scuro per lo sfondo dell'interfaccia utente**</span><span class="sxs-lookup"><span data-stu-id="1aa44-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="1aa44-123">Utilizzando la combinazione di colori scura, è possibile ridurre al minimo l'affaticamento degli occhi e migliorare la confidenza sulle interazioni con la mano diretta.</span><span class="sxs-lookup"><span data-stu-id="1aa44-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="1aa44-124">![Esempi di interfaccia utente scura ](images/color_dark_examples.jpg)
 *esempi di colore scuro usati per lo sfondo del contenuto*</span><span class="sxs-lookup"><span data-stu-id="1aa44-124">![Dark UI examples](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="1aa44-125">**USA SemiBold o spessore carattere grassetto**</span><span class="sxs-lookup"><span data-stu-id="1aa44-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="1aa44-126">HoloLens consente alla tua esperienza di mostrare un bel testo ad alta risoluzione.</span><span class="sxs-lookup"><span data-stu-id="1aa44-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="1aa44-127">Tuttavia, si consiglia di evitare i pesi dei tipi di carattere sottili, ad esempio Light o Semilight, perché i tratti verticali possono ingrandire le dimensioni del tipo di carattere ridotto.</span><span class="sxs-lookup"><span data-stu-id="1aa44-127">However, it is recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="1aa44-128">![Esempi di interfaccia utente scura ](images/color_font_examples.jpg)
 *spessore del carattere grassetto o semi-grassetto (pannello superiore) migliora la leggibilità*</span><span class="sxs-lookup"><span data-stu-id="1aa44-128">![Dark UI examples](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="1aa44-129">**Usa il materiale HolographicBackplate di MRTK**</span><span class="sxs-lookup"><span data-stu-id="1aa44-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="1aa44-130">Il materiale HolographicBackplate viene applicato a diversi pannelli dell'interfaccia utente nella shell di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1aa44-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="1aa44-131">Una delle sue funzionalità è un effetto iridescenza che è visibile agli utenti mentre spostano la posizione in relazione al pannello.</span><span class="sxs-lookup"><span data-stu-id="1aa44-131">One of its features is an iridescence effect that is visible to users as they shift their position in relation to the panel.</span></span> <span data-ttu-id="1aa44-132">Il colore del backplate si sposta leggermente in uno spettro predefinito, creando un effetto visivo accattivante e dinamico senza interferire con la leggibilità del contenuto.</span><span class="sxs-lookup"><span data-stu-id="1aa44-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="1aa44-133">Questo piccolo cambiamento di colore serve anche per compensare eventuali irregolarità dei colori minori.</span><span class="sxs-lookup"><span data-stu-id="1aa44-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="1aa44-134">Problemi con la contropiastra dell'interfaccia utente trasparente o traslucida</span><span class="sxs-lookup"><span data-stu-id="1aa44-134">Challenges with transparent or translucent UI backplate</span></span> 
<span data-ttu-id="1aa44-135">![Esempi di interfaccia utente trasparente ](images/color_transparent_examples.jpg)
 *esempi di backplating dell'interfaccia utente trasparente*</span><span class="sxs-lookup"><span data-stu-id="1aa44-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="1aa44-136">**Complessità visiva e accessibilità**</span><span class="sxs-lookup"><span data-stu-id="1aa44-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="1aa44-137">Poiché gli oggetti olografici vengono combinati con l'ambiente fisico, la leggibilità del contenuto o dell'interfaccia utente nella finestra trasparente o traslucido potrebbe essere degradata.</span><span class="sxs-lookup"><span data-stu-id="1aa44-137">Since holographic objects are blended with the physical environment, the legibility of the content or UI on the transparent or translucent window could be degraded.</span></span> <span data-ttu-id="1aa44-138">Inoltre, quando gli oggetti olografici trasparenti sono sovrapposti l'uno sull'altro, potrebbe rendere difficile per l'utente interagire a causa del livello di confusione.</span><span class="sxs-lookup"><span data-stu-id="1aa44-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="1aa44-139">**Prestazioni**</span><span class="sxs-lookup"><span data-stu-id="1aa44-139">**Performance**</span></span>

<span data-ttu-id="1aa44-140">Per eseguire il rendering corretto degli oggetti trasparenti o traslucidi, è necessario ordinarli e combinarli con tutti gli oggetti presenti in background.</span><span class="sxs-lookup"><span data-stu-id="1aa44-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects which exist in the background.</span></span> <span data-ttu-id="1aa44-141">L'ordinamento degli oggetti trasparenti presenta un modesto costo della CPU, mentre la fusione ha un notevole costo della GPU, perché non consente alla GPU di eseguire la rimozione della superficie nascosta tramite l'abbattimento z, ovvero</span><span class="sxs-lookup"><span data-stu-id="1aa44-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it does not allow the GPU to perform hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="1aa44-142">test di profondità).</span><span class="sxs-lookup"><span data-stu-id="1aa44-142">depth testing).</span></span> <span data-ttu-id="1aa44-143">Se non si consente la rimozione della superficie nascosta, aumenta il numero di operazioni che devono essere calcolate per il pixel finale sottoposto a rendering e in questo modo viene maggiore la pressione sui vincoli di velocità di riempimento.</span><span class="sxs-lookup"><span data-stu-id="1aa44-143">Not allowing hidden surface removal increases the number of operations that need to be computed for the final rendered pixel, and thus puts more pressure on fill rate constraints.</span></span>

<span data-ttu-id="1aa44-144">**Problema di stabilità degli ologrammi con tecnologia Depth LSR**</span><span class="sxs-lookup"><span data-stu-id="1aa44-144">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="1aa44-145">Per migliorare la riproiezione olografica o la stabilità dell'ologramma, un'applicazione può inviare un buffer di profondità al sistema per ogni frame sottoposto a rendering.</span><span class="sxs-lookup"><span data-stu-id="1aa44-145">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="1aa44-146">Quando si usa il buffer di profondità per la riproiezione, una regola è che per ogni pixel di colore di cui è stato eseguito il rendering è necessario scrivere un valore di profondità corrispondente nel buffer di profondità (e qualsiasi pixel con un valore di profondità deve avere anche un valore di colore).</span><span class="sxs-lookup"><span data-stu-id="1aa44-146">When using the depth buffer for reprojection one rule is that for every color pixel rendered a corresponding depth value must be written to the depth buffer (and any pixel with a depth value should also have color value).</span></span> <span data-ttu-id="1aa44-147">Se il materiale sussidiario sopra indicato non viene seguito, le aree dell'immagine di cui è stato eseguito il rendering che non dispongono di informazioni di profondità valide possono essere riproiettate in modo da produrre artefatti (spesso visibili come distorsioni di tipo Wave).</span><span class="sxs-lookup"><span data-stu-id="1aa44-147">If the above guidance is not followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts (often visible as a wave-like distortion).</span></span>


## <a name="design-guidelines"></a><span data-ttu-id="1aa44-148">Linee guida di progettazione</span><span class="sxs-lookup"><span data-stu-id="1aa44-148">Design guidelines</span></span>
<span data-ttu-id="1aa44-149">**Usa sfondo interfaccia utente opaco**</span><span class="sxs-lookup"><span data-stu-id="1aa44-149">**Use opaque UI background**</span></span>

<span data-ttu-id="1aa44-150">Per impostazione predefinita, gli oggetti trasparenti o traslucidi non scrivono la profondità per consentire la corretta combinazione.</span><span class="sxs-lookup"><span data-stu-id="1aa44-150">By default, transparent or translucent objects do not write depth to allow for proper blending.</span></span> <span data-ttu-id="1aa44-151">I modi per attenuare questo problema includono l'utilizzo di oggetti opachi, assicurando che gli oggetti traslucidi siano visualizzati vicino a oggetti opachi, ad esempio un pulsante traslucido davanti a un Backplate opaco, forzando gli oggetti traslucidi a scrivere profondità (non applicabile in tutti gli scenari) o eseguendo il rendering di oggetti proxy che contribuiscono solo a valori di profondità alla fine del frame.</span><span class="sxs-lookup"><span data-stu-id="1aa44-151">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="1aa44-152">Soluzioni in MRTK-Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="1aa44-152">Solutions within MRTK-Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="1aa44-153">Grazie a una contropiastra solida e opaca, possiamo proteggere la leggibilità e la confidenza dell'interazione.</span><span class="sxs-lookup"><span data-stu-id="1aa44-153">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="1aa44-154">**Ridurre al minimo il numero di pixel interessati**</span><span class="sxs-lookup"><span data-stu-id="1aa44-154">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="1aa44-155">Se il progetto deve usare oggetti trasparenti, provare a ridurre al minimo il numero di pixel interessati.</span><span class="sxs-lookup"><span data-stu-id="1aa44-155">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="1aa44-156">Se, ad esempio, un oggetto è visibile solo in determinate condizioni (ad esempio un effetto di bagliore additivo), disabilitare l'oggetto quando è completamente invisibile, anziché impostare il colore additivo su nero.</span><span class="sxs-lookup"><span data-stu-id="1aa44-156">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it is fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="1aa44-157">Per le semplici forme 2D create usando un quad con una maschera alfa, provare a creare una rappresentazione mesh della forma con uno shader opaco.</span><span class="sxs-lookup"><span data-stu-id="1aa44-157">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="1aa44-158">Esempi di interfaccia utente scura in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="1aa44-158">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="1aa44-159">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornisce molti esempi di blocchi di compilazione dell'interfaccia utente basati sulle combinazioni di colori oscuri.</span><span class="sxs-lookup"><span data-stu-id="1aa44-159">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="1aa44-160">Menu vicino</span><span class="sxs-lookup"><span data-stu-id="1aa44-160">Near Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [<span data-ttu-id="1aa44-161">Finestra di dialogo</span><span class="sxs-lookup"><span data-stu-id="1aa44-161">Dialog</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [<span data-ttu-id="1aa44-162">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="1aa44-162">Hand Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="1aa44-163">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1aa44-163">See also</span></span>
* [<span data-ttu-id="1aa44-164">Colore, luce e materiali</span><span class="sxs-lookup"><span data-stu-id="1aa44-164">Color, light and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="1aa44-165">Cursori</span><span class="sxs-lookup"><span data-stu-id="1aa44-165">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="1aa44-166">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="1aa44-166">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="1aa44-167">Button</span><span class="sxs-lookup"><span data-stu-id="1aa44-167">Button</span></span>](button.md)
* [<span data-ttu-id="1aa44-168">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="1aa44-168">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="1aa44-169">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="1aa44-169">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="1aa44-170">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="1aa44-170">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="1aa44-171">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="1aa44-171">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="1aa44-172">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="1aa44-172">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="1aa44-173">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="1aa44-173">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="1aa44-174">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="1aa44-174">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="1aa44-175">Tastiera</span><span class="sxs-lookup"><span data-stu-id="1aa44-175">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="1aa44-176">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="1aa44-176">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="1aa44-177">Slate</span><span class="sxs-lookup"><span data-stu-id="1aa44-177">Slate</span></span>](slate.md)
* [<span data-ttu-id="1aa44-178">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="1aa44-178">Slider</span></span>](slider.md)
* [<span data-ttu-id="1aa44-179">Shader</span><span class="sxs-lookup"><span data-stu-id="1aa44-179">Shader</span></span>](shader.md)
* [<span data-ttu-id="1aa44-180">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="1aa44-180">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="1aa44-181">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="1aa44-181">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="1aa44-182">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="1aa44-182">Surface magnetism</span></span>](surface-magnetism.md)
