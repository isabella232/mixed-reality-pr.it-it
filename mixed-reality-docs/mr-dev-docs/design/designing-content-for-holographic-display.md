---
title: Progettazione di contenuto per la visualizzazione olografica
description: Informazioni sulle linee guida di progettazione e sulle procedure consigliate per la visualizzazione olografica nei dispositivi HoloLens.
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: progettazione dell'interfaccia utente, visualizzazione olografica, progettazione del contenuto, tema scuro, tema chiaro, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit, progettazione, pixel
ms.openlocfilehash: 2c68acb5478bfbd438c8bbb9dd2f8d9686bcefc5
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600320"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="18757-104">Progettazione di contenuto per la visualizzazione olografica</span><span class="sxs-lookup"><span data-stu-id="18757-104">Designing content for holographic display</span></span>

![Posizione sul lato Ulnar](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="18757-106">Quando si progettano contenuti per schermi olografici, è necessario prendere in considerazione diversi elementi per ottenere un'esperienza ottimale.</span><span class="sxs-lookup"><span data-stu-id="18757-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="18757-107">Di seguito sono elencate alcune raccomandazioni. Per altre informazioni sulle caratteristiche degli schermi olografici, vedere la pagina [Colore, luce e](color-light-and-materials.md) materiali.</span><span class="sxs-lookup"><span data-stu-id="18757-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="18757-108">Problemi con il colore chiaro su una superficie di grandi dimensioni</span><span class="sxs-lookup"><span data-stu-id="18757-108">Challenges with bright color on a large surface</span></span> 

<span data-ttu-id="18757-109">In base alle ricerche e ai test dell'esperienza HoloLens, è stato rilevato che l'uso di colori chiari in un'area di grandi dimensioni dello schermo può causare diversi problemi:</span><span class="sxs-lookup"><span data-stu-id="18757-109">Based on our HoloLens experience research and testing, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="18757-110">**Affaticamento oculare**</span><span class="sxs-lookup"><span data-stu-id="18757-110">**Eye fatigue**</span></span> 

<span data-ttu-id="18757-111">Poiché la visualizzazione olografica è additiva, gli ologrammi con colori chiari usano più luce.</span><span class="sxs-lookup"><span data-stu-id="18757-111">Since holographic display is additive, holograms with bright colors use more light.</span></span> <span data-ttu-id="18757-112">Un colore chiaro e a tinta unita in un'area di grandi dimensioni dello schermo può causare facilmente affaticamento oculare per l'utente.</span><span class="sxs-lookup"><span data-stu-id="18757-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="18757-113">**Occlusione manuale**</span><span class="sxs-lookup"><span data-stu-id="18757-113">**Hand occlusion**</span></span> 

<span data-ttu-id="18757-114">Il colore chiaro rende difficile per l'utente visualizzare le mani quando interagisce direttamente con gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="18757-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="18757-115">Poiché l'utente non può vedere le mani, diventa difficile percepirne la profondità/distanza tra la mano e il dito rispetto alla superficie di destinazione.</span><span class="sxs-lookup"><span data-stu-id="18757-115">Since the user can't see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="18757-116">Il cursore del dito consente di compensare questo problema, ma può comunque risultare complesso su una superficie bianca.</span><span class="sxs-lookup"><span data-stu-id="18757-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="18757-117">![Colore e occlusione della mano ](images/color_handocclusion.jpg)
 *Difficile vedere la mano sul backplate del contenuto* di colore chiaro</span><span class="sxs-lookup"><span data-stu-id="18757-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="18757-118">**Uniformità dei colori**</span><span class="sxs-lookup"><span data-stu-id="18757-118">**Color uniformity**</span></span>

<span data-ttu-id="18757-119">A causa delle caratteristiche degli schermi olografici, un'area di grandi dimensioni sullo schermo può diventare di tipo blotchy.</span><span class="sxs-lookup"><span data-stu-id="18757-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="18757-120">L'uso di combinazioni di colori scuri consente di ridurre al minimo questo problema.</span><span class="sxs-lookup"><span data-stu-id="18757-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines-for-color-choices"></a><span data-ttu-id="18757-121">Linee guida di progettazione per le scelte di colore</span><span class="sxs-lookup"><span data-stu-id="18757-121">Design guidelines for color choices</span></span>

<span data-ttu-id="18757-122">**Usare il colore scuro per lo sfondo dell'interfaccia utente**</span><span class="sxs-lookup"><span data-stu-id="18757-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="18757-123">Usando la combinazione colori scura, è possibile ridurre al minimo l'affaticamento oculare e migliorare l'attendibilità delle interazioni dirette con la mano.</span><span class="sxs-lookup"><span data-stu-id="18757-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="18757-124">![Esempi di colore scuro usato per lo sfondo del contenuto ](images/color_dark_examples.jpg)
 *Esempi di colore scuro usato per lo sfondo del contenuto*</span><span class="sxs-lookup"><span data-stu-id="18757-124">![Examples of dark color used for the content background](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="18757-125">**Usare lo spessore del carattere semibold o bold**</span><span class="sxs-lookup"><span data-stu-id="18757-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="18757-126">HoloLens consente all'esperienza di visualizzare testo ad alta risoluzione.</span><span class="sxs-lookup"><span data-stu-id="18757-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="18757-127">Tuttavia, è consigliabile evitare spessori del carattere leggeri o semi-leggeri, perché i tratti verticali possono instabilità nelle dimensioni ridotte del carattere.</span><span class="sxs-lookup"><span data-stu-id="18757-127">However, it's recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="18757-128">![Lo spessore del carattere in grassetto o semi grassetto (pannello superiore) migliora la leggibilità Del carattere grassetto o semi ](images/color_font_examples.jpg)
 *grassetto (pannello superiore)* migliora la leggibilità</span><span class="sxs-lookup"><span data-stu-id="18757-128">![Bold or semi-bold font weight (upper panel) improves the legibility](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="18757-129">**Usare il materiale HolographicBackplate di MRTK**</span><span class="sxs-lookup"><span data-stu-id="18757-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="18757-130">Il materiale HolographicBackplate viene applicato a diversi pannelli dell'interfaccia utente nella shell di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="18757-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="18757-131">Una delle funzionalità è un effetto di iridescenza visibile agli utenti quando si spostano in base al pannello.</span><span class="sxs-lookup"><span data-stu-id="18757-131">One of its features is an iridescence effect that is visible to users as they shift their position based on the panel.</span></span> <span data-ttu-id="18757-132">Il colore del backplate si sposta in modo secondario in uno spettro predefinito, creando un effetto visivo coinvolgente e dinamico senza interferire con la leggibilità del contenuto.</span><span class="sxs-lookup"><span data-stu-id="18757-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="18757-133">Questo lieve cambiamento di colore serve anche a compensare eventuali piccole irregolarità di colore.</span><span class="sxs-lookup"><span data-stu-id="18757-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="18757-134">Problemi con backplate dell'interfaccia utente trasparente o traslucido</span><span class="sxs-lookup"><span data-stu-id="18757-134">Challenges with transparent or translucent UI backplate</span></span> 

<span data-ttu-id="18757-135">![Esempi di interfaccia utente ](images/color_transparent_examples.jpg)
 *trasparente Esempi di backplate dell'interfaccia utente trasparente*</span><span class="sxs-lookup"><span data-stu-id="18757-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="18757-136">**Complessità visiva e accessibilità**</span><span class="sxs-lookup"><span data-stu-id="18757-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="18757-137">Poiché gli oggetti olografici si integrano con l'ambiente fisico, il contenuto o la leggibilità dell'interfaccia utente nelle finestre trasparenti o traslucidi potrebbero essere ridotte.</span><span class="sxs-lookup"><span data-stu-id="18757-137">Since holographic objects blend with the physical environment, content or UI legibility on transparent or translucent windows could be degraded.</span></span> <span data-ttu-id="18757-138">Inoltre, quando gli oggetti olografici trasparenti sono sovrapposti l'uno all'altro, potrebbe rendere difficile l'interazione dell'utente a causa della profondità confusa.</span><span class="sxs-lookup"><span data-stu-id="18757-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="18757-139">**Prestazioni**</span><span class="sxs-lookup"><span data-stu-id="18757-139">**Performance**</span></span>

<span data-ttu-id="18757-140">Per eseguire correttamente il rendering degli oggetti trasparenti o traslucidi, è necessario ordinare e unire gli oggetti esistenti sullo sfondo.</span><span class="sxs-lookup"><span data-stu-id="18757-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects, which exist in the background.</span></span> <span data-ttu-id="18757-141">L'ordinamento degli oggetti trasparenti ha un costo medio della CPU, la fusione ha un costo notevole per la GPU perché non consente alla GPU di eseguire la rimozione della superficie nascosta tramite z-culling (ad esempio</span><span class="sxs-lookup"><span data-stu-id="18757-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it doesn't allow the GPU to do hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="18757-142">test di profondità).</span><span class="sxs-lookup"><span data-stu-id="18757-142">depth testing).</span></span> <span data-ttu-id="18757-143">Se non si consente la rimozione della superficie nascosta, aumenta il numero di operazioni necessarie per il pixel finale sottoposto a rendering.</span><span class="sxs-lookup"><span data-stu-id="18757-143">Not allowing hidden surface removal increases the number of operations needed for the final rendered pixel.</span></span> <span data-ttu-id="18757-144">In questo modo si imposta una maggiore pressione fill rate vincoli.</span><span class="sxs-lookup"><span data-stu-id="18757-144">This puts on more pressure fill rate constraints.</span></span>

<span data-ttu-id="18757-145">**Problema di stabilità dell'ologramma con la tecnologia Depth LSR**</span><span class="sxs-lookup"><span data-stu-id="18757-145">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="18757-146">Per migliorare la proiezione olografica o la stabilità dell'ologramma, un'applicazione può inviare un buffer di profondità al sistema per ogni frame sottoposto a rendering.</span><span class="sxs-lookup"><span data-stu-id="18757-146">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="18757-147">Quando si usa il buffer di profondità per la riepilazione, è necessario scrivere un buffer di profondità per ogni pixel di cui è stato eseguito il rendering di colore a una profondità corrispondente.</span><span class="sxs-lookup"><span data-stu-id="18757-147">When using the depth buffer for reprojection, you need to write a depth buffer for every color rendered pixel a corresponding depth.</span></span> <span data-ttu-id="18757-148">Anche i pixel con un valore di profondità devono avere un valore di colore.</span><span class="sxs-lookup"><span data-stu-id="18757-148">Any pixel with a depth value should also have color value.</span></span> <span data-ttu-id="18757-149">Se le indicazioni precedenti non vengono seguite, le aree dell'immagine di cui è stato eseguito il rendering che non dispongono di informazioni di profondità valide possono essere riposizionate in modo da produrre artefatti, spesso visibili come distorsioni simili a onde.</span><span class="sxs-lookup"><span data-stu-id="18757-149">If the above guidance isn't followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts, which are often visible as a wave-like distortion.</span></span>


## <a name="design-guidelines-for-transparent-elements"></a><span data-ttu-id="18757-150">Linee guida di progettazione per gli elementi trasparenti</span><span class="sxs-lookup"><span data-stu-id="18757-150">Design guidelines for transparent elements</span></span>

<span data-ttu-id="18757-151">**Usare lo sfondo opaco dell'interfaccia utente**</span><span class="sxs-lookup"><span data-stu-id="18757-151">**Use opaque UI background**</span></span>

<span data-ttu-id="18757-152">Per impostazione predefinita, gli oggetti trasparenti o traslucidi non scrivono profondità per consentire la fusione corretta.</span><span class="sxs-lookup"><span data-stu-id="18757-152">By default, transparent or translucent objects don't write depth to allow for proper blending.</span></span> <span data-ttu-id="18757-153">I modi per attenuare questo problema includono l'uso di oggetti opachi, la garanzia che gli oggetti traslucidi vengano visualizzati vicino agli oggetti opachi (ad esempio un pulsante traslucido davanti a un backplate opaco), la forzatura degli oggetti traslucidi alla profondità di scrittura (non applicabile in tutti gli scenari) o il rendering di oggetti proxy, che contribuiscono solo ai valori di profondità alla fine del frame.</span><span class="sxs-lookup"><span data-stu-id="18757-153">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects, which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="18757-154">Soluzioni all'interno di MRTK-Unity: /windows/mixed-reality/mrtk-unity/performance/ologram-stabilization#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="18757-154">Solutions within MRTK-Unity: /windows/mixed-reality/mrtk-unity/performance/hologram-stabilization#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="18757-155">Usando un backplate solido e opaco, è possibile proteggere la leggibilità e l'attendibilità dell'interazione.</span><span class="sxs-lookup"><span data-stu-id="18757-155">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="18757-156">**Ridurre al minimo il numero di pixel interessati**</span><span class="sxs-lookup"><span data-stu-id="18757-156">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="18757-157">Se il progetto deve usare oggetti trasparenti, provare a ridurre al minimo il numero di pixel interessati.</span><span class="sxs-lookup"><span data-stu-id="18757-157">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="18757-158">Ad esempio, se un oggetto è visibile solo in determinate condizioni (ad esempio un effetto di alone additivo), disabilitare l'oggetto quando è completamente invisibile (invece di impostare il colore additivo su nero).</span><span class="sxs-lookup"><span data-stu-id="18757-158">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it's fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="18757-159">Per le forme 2D semplici create usando un quad con una maschera alfa, prendere in considerazione la creazione di una rappresentazione mesh della forma con uno shader opaco.</span><span class="sxs-lookup"><span data-stu-id="18757-159">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="18757-160">Esempi di interfaccia utente scura in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="18757-160">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="18757-161">**[MRTK offre molti](https://github.com/Microsoft/MixedRealityToolkit-Unity)** esempi di blocchi predefiniti dell'interfaccia utente basati sulle combinazioni di colori scuri.</span><span class="sxs-lookup"><span data-stu-id="18757-161">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="18757-162">Menu vicino</span><span class="sxs-lookup"><span data-stu-id="18757-162">Near Menu</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/near-menu)
* [<span data-ttu-id="18757-163">Finestra di dialogo</span><span class="sxs-lookup"><span data-stu-id="18757-163">Dialog</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog)
* [<span data-ttu-id="18757-164">Menu mano</span><span class="sxs-lookup"><span data-stu-id="18757-164">Hand Menu</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)

<br>

---

## <a name="see-also"></a><span data-ttu-id="18757-165">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="18757-165">See also</span></span>

* [<span data-ttu-id="18757-166">Colore, luce e materiali</span><span class="sxs-lookup"><span data-stu-id="18757-166">Color, light, and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="18757-167">Cursori</span><span class="sxs-lookup"><span data-stu-id="18757-167">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="18757-168">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="18757-168">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="18757-169">Button</span><span class="sxs-lookup"><span data-stu-id="18757-169">Button</span></span>](button.md)
* [<span data-ttu-id="18757-170">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="18757-170">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="18757-171">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="18757-171">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="18757-172">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="18757-172">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="18757-173">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="18757-173">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="18757-174">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="18757-174">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="18757-175">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="18757-175">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="18757-176">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="18757-176">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="18757-177">Tastiera</span><span class="sxs-lookup"><span data-stu-id="18757-177">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="18757-178">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="18757-178">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="18757-179">Slate</span><span class="sxs-lookup"><span data-stu-id="18757-179">Slate</span></span>](slate.md)
* [<span data-ttu-id="18757-180">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="18757-180">Slider</span></span>](slider.md)
* [<span data-ttu-id="18757-181">Shader</span><span class="sxs-lookup"><span data-stu-id="18757-181">Shader</span></span>](shader.md)
* [<span data-ttu-id="18757-182">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="18757-182">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="18757-183">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="18757-183">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="18757-184">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="18757-184">Surface magnetism</span></span>](surface-magnetism.md)