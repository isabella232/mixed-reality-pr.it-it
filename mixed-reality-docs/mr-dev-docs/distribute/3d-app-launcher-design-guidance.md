---
title: Linee guida per la progettazione di launcher di app 3D
description: Un avvio di app 3D è un oggetto "fisico" nella casa della realtà mista dell'utente che può selezionare per avviare un'app.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, avvio di app 3D, auricolare immersivo, cubo Live, auricolare in realtà mista, auricolare di realtà mista di Windows, headset di realtà virtuale, UWP, Win32, illuminazione, colore
ms.openlocfilehash: 2edb09e47da5bcbae34a37f004853002f3f65cf3
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757729"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="db98b-104">Linee guida per la progettazione di launcher di app 3D</span><span class="sxs-lookup"><span data-stu-id="db98b-104">3D app launcher design guidance</span></span>

<span data-ttu-id="db98b-105">Quando si inserisce una cuffia a realtà mista di Windows (VR), si immette la Home realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="db98b-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home.</span></span> <span data-ttu-id="db98b-106">La casa viene visualizzata come casa in una rupe circondata da montagne e acqua, ma è possibile [scegliere altri ambienti e persino crearne di personalizzati](../design/add-custom-home-environments.md).</span><span class="sxs-lookup"><span data-stu-id="db98b-106">The home is visualized as a house on a cliff surrounded by mountains and water, but you can [choose other environments and even create your own](../design/add-custom-home-environments.md)).</span></span> <span data-ttu-id="db98b-107">All'interno dello spazio di casa, un utente può organizzare e organizzare gli oggetti e le app 3D a cui si è interessati.</span><span class="sxs-lookup"><span data-stu-id="db98b-107">Within the home's space, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="db98b-108">Un **avvio di app 3D** è un oggetto "fisico" nella casa della realtà mista dell'utente che può selezionare per avviare un'app.</span><span class="sxs-lookup"><span data-stu-id="db98b-108">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="db98b-109">![Esempio: utilità di avvio delle app 3D Floaty Bird](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="db98b-109">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="db98b-110">*Esempio di utilità di avvio di app 3D Floaty Bird (app fittizia)*</span><span class="sxs-lookup"><span data-stu-id="db98b-110">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="db98b-111">processo di creazione dell'utilità di avvio delle app 3D</span><span class="sxs-lookup"><span data-stu-id="db98b-111">3D app launcher creation process</span></span>

<span data-ttu-id="db98b-112">Per la creazione di un avvio di app 3D sono necessari tre passaggi:</span><span class="sxs-lookup"><span data-stu-id="db98b-112">There are 3 steps to creating a 3D app launcher:</span></span>

1. <span data-ttu-id="db98b-113">Progettazione e concezione (questo articolo)</span><span class="sxs-lookup"><span data-stu-id="db98b-113">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="db98b-114">Modellazione ed esportazione</span><span class="sxs-lookup"><span data-stu-id="db98b-114">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="db98b-115">Per integrarlo nell'applicazione:</span><span class="sxs-lookup"><span data-stu-id="db98b-115">Integrating it into your application:</span></span>
    * [<span data-ttu-id="db98b-116">App UWP</span><span class="sxs-lookup"><span data-stu-id="db98b-116">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="db98b-117">App Win32</span><span class="sxs-lookup"><span data-stu-id="db98b-117">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="db98b-118">Concetti relativi alla progettazione</span><span class="sxs-lookup"><span data-stu-id="db98b-118">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="db98b-119">Fantastico ma familiare</span><span class="sxs-lookup"><span data-stu-id="db98b-119">Fantastic yet familiar</span></span>

<span data-ttu-id="db98b-120">L'ambiente di realtà mista di Windows in cui si trova l'utilità di avvio delle app è familiare, parte fantastica/sci-fi.</span><span class="sxs-lookup"><span data-stu-id="db98b-120">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="db98b-121">I migliori lanci seguono le regole di questo mondo.</span><span class="sxs-lookup"><span data-stu-id="db98b-121">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="db98b-122">Si pensi a come sia possibile prendere un oggetto familiare, rappresentativo, dall'app, ma è necessario piegare alcune delle regole della realtà reale.</span><span class="sxs-lookup"><span data-stu-id="db98b-122">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="db98b-123">Si otterrà un risultato magico.</span><span class="sxs-lookup"><span data-stu-id="db98b-123">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="db98b-124">Intuitivo</span><span class="sxs-lookup"><span data-stu-id="db98b-124">Intuitive</span></span>

<span data-ttu-id="db98b-125">Quando si esamina l'utilità di avvio delle app, il suo scopo è quello di avviare l'app, che dovrebbe essere ovvia e non dovrebbe causare confusione.</span><span class="sxs-lookup"><span data-stu-id="db98b-125">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="db98b-126">Assicurarsi, ad esempio, che l'utilità di avvio sia un rappresentante abbastanza ovvio dell'app che non verrà confusa per un pezzo di arredamento in Cliff House.</span><span class="sxs-lookup"><span data-stu-id="db98b-126">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="db98b-127">L'utilità di avvio delle app dovrebbe invitare gli utenti a toccarlo/selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="db98b-127">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="db98b-128">![Esempio: avvio dell'app 3D con nota aggiornata](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="db98b-128">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="db98b-129">*Esempio di avvio dell'app 3D (app fittizia)*</span><span class="sxs-lookup"><span data-stu-id="db98b-129">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="db98b-130">Scalabilità domestica</span><span class="sxs-lookup"><span data-stu-id="db98b-130">Home scale</span></span>

<span data-ttu-id="db98b-131">i lanci di app 3D risiedono nella casa di Cliff e le dimensioni predefinite dovrebbero avere senso con gli altri oggetti "fisici" nello spazio.</span><span class="sxs-lookup"><span data-stu-id="db98b-131">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="db98b-132">Se l'utilità di avvio viene posizionata accanto a un impianto di casa o a una parte di mobili, si dovrebbe sentire a casa, ridimensionare.</span><span class="sxs-lookup"><span data-stu-id="db98b-132">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="db98b-133">Un valido punto di partenza consiste nel vedere il modo in cui esamina 30 centimetri cubici, ma tenere presente che gli utenti possono aumentare o ridurre le prestazioni se lo desiderano.</span><span class="sxs-lookup"><span data-stu-id="db98b-133">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="db98b-134">Proprietario</span><span class="sxs-lookup"><span data-stu-id="db98b-134">Own-able</span></span>

<span data-ttu-id="db98b-135">L'utilità di avvio delle app dovrebbe essere simile a un oggetto che una persona sarebbe entusiasta di avere nello spazio.</span><span class="sxs-lookup"><span data-stu-id="db98b-135">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="db98b-136">Si tratteranno praticamente di questi elementi, quindi l'utilità di avvio dovrebbe avere un aspetto simile a quello auspicabile dall'utente per cercarla e mantenerla vicina.</span><span class="sxs-lookup"><span data-stu-id="db98b-136">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="db98b-137">![Esempio: avvio dell'app 3D di Astro Warp](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="db98b-137">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="db98b-138">*Esempio di avvio di app 3D di Astro Warp (app fittizia)*</span><span class="sxs-lookup"><span data-stu-id="db98b-138">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="db98b-139">Riconoscibile</span><span class="sxs-lookup"><span data-stu-id="db98b-139">Recognizable</span></span>

<span data-ttu-id="db98b-140">L'utilità di avvio delle app 3D dovrebbe immediatamente esprimere "il marchio dell'app" agli utenti che lo visualizzano.</span><span class="sxs-lookup"><span data-stu-id="db98b-140">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="db98b-141">Se è presente un carattere a stella o un oggetto particolarmente identificabile nell'app, è consigliabile usarlo come parte significativa della progettazione.</span><span class="sxs-lookup"><span data-stu-id="db98b-141">If you have a star character or an especially identifiable object in your app, we recommend using that as a significant part of your design.</span></span> <span data-ttu-id="db98b-142">In un mondo di realtà mista, un oggetto trarrà maggiore interesse dagli utenti rispetto solo a un logo.</span><span class="sxs-lookup"><span data-stu-id="db98b-142">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="db98b-143">Gli oggetti riconoscibili comunicano il marchio in modo rapido e chiaro.</span><span class="sxs-lookup"><span data-stu-id="db98b-143">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="db98b-144">Volumetrici</span><span class="sxs-lookup"><span data-stu-id="db98b-144">Volumetric</span></span>

<span data-ttu-id="db98b-145">L'app merita di più di inserire il logo su un piano semplice e chiamarlo un giorno.</span><span class="sxs-lookup"><span data-stu-id="db98b-145">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="db98b-146">L'utilità di avvio dovrebbe sembrare un oggetto fisico eccitante, 3D, nello spazio dell'utente.</span><span class="sxs-lookup"><span data-stu-id="db98b-146">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="db98b-147">Un approccio efficace consiste nell'immaginare che l'app avrebbe avuto un pallone nella sfilata del giorno del ringraziamento del Macy.</span><span class="sxs-lookup"><span data-stu-id="db98b-147">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="db98b-148">Se ci si chiede, cosa si può veramente stupire con la strada?</span><span class="sxs-lookup"><span data-stu-id="db98b-148">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="db98b-149">Cosa può sembrare interessante da tutti gli angoli di visualizzazione?</span><span class="sxs-lookup"><span data-stu-id="db98b-149">What would look great from all viewing angles?</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="db98b-150">![Solo logo ](images/20171016-140436-mixedreality-640px.jpg) *logo*</span><span class="sxs-lookup"><span data-stu-id="db98b-150">![Logo only](images/20171016-140436-mixedreality-640px.jpg) *Logo only*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="db98b-151">![Più riconoscibili con un carattere ](images/20171016-140557-mixedreality-640px.jpg) *più riconoscibile con un carattere*</span><span class="sxs-lookup"><span data-stu-id="db98b-151">![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="db98b-152">![Approccio Flat, non sorprendentemente, è un approccio Flat Flat ](images/20171016-155101-mixedreality-640px.jpg) *, non sorprendentemente, sembra piatto*</span><span class="sxs-lookup"><span data-stu-id="db98b-152">![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg) *Flat approach, not surprisingly, feels flat*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="db98b-153">![Un approccio volumetrico che illustra meglio l' ](images/20171016-161407-mixedreality-640px.jpg) *approccio volumetrico per le app mostra meglio l'app*</span><span class="sxs-lookup"><span data-stu-id="db98b-153">![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg) *Volumetric approach better showcases your app*</span></span>
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a><span data-ttu-id="db98b-154">Suggerimenti per modelli 3D efficaci</span><span class="sxs-lookup"><span data-stu-id="db98b-154">Tips for good 3D models</span></span>

* <span data-ttu-id="db98b-155">Quando si pianificano le dimensioni per l'utilità di avvio delle app, si scatta approssimativamente un cubo da 30 cm.</span><span class="sxs-lookup"><span data-stu-id="db98b-155">When planning dimensions for your app launcher, shoot for roughly a 30-cm cube.</span></span> <span data-ttu-id="db98b-156">Quindi, un rapporto di dimensioni 1:1:1.</span><span class="sxs-lookup"><span data-stu-id="db98b-156">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="db98b-157">I modelli devono essere sotto 10.000 poligoni.</span><span class="sxs-lookup"><span data-stu-id="db98b-157">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="db98b-158">Altre informazioni sui conteggi dei triangoli e sui livelli di dettaglio (LODs)</span><span class="sxs-lookup"><span data-stu-id="db98b-158">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="db98b-159">Eseguire test su un auricolare immersivo.</span><span class="sxs-lookup"><span data-stu-id="db98b-159">Test on an immersive headset.</span></span>
* <span data-ttu-id="db98b-160">Consente di compilare i dettagli nella geometria del modello, laddove possibile, non basarsi sulle trame per i dettagli.</span><span class="sxs-lookup"><span data-stu-id="db98b-160">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="db98b-161">Compila la geometria chiusa "acqua stretta".</span><span class="sxs-lookup"><span data-stu-id="db98b-161">Build “water tight” closed geometry.</span></span> <span data-ttu-id="db98b-162">Non ci sono buchi che non sono modellati in.</span><span class="sxs-lookup"><span data-stu-id="db98b-162">No holes that aren't modeled in.</span></span>
* <span data-ttu-id="db98b-163">Usare materiali naturali nell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="db98b-163">Use natural materials in your object.</span></span> <span data-ttu-id="db98b-164">Immagina di crearlo nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="db98b-164">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="db98b-165">Verificare che il modello sia ben letto a distanza e dimensioni diverse.</span><span class="sxs-lookup"><span data-stu-id="db98b-165">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="db98b-166">Quando il modello è pronto per l'uso, leggere le [linee guida](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)per l'esportazione degli asset.</span><span class="sxs-lookup"><span data-stu-id="db98b-166">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="db98b-167">![Modello con dettagli sottili nella trama](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="db98b-167">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="db98b-168">*Modello con dettagli sottili nella trama*</span><span class="sxs-lookup"><span data-stu-id="db98b-168">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="db98b-169">Da evitare</span><span class="sxs-lookup"><span data-stu-id="db98b-169">What to avoid</span></span>

* <span data-ttu-id="db98b-170">Non usare dettagli a contrasto elevato o modelli e trame di dimensioni ridotte e occupate.</span><span class="sxs-lookup"><span data-stu-id="db98b-170">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="db98b-171">Non usare la geometria sottile: non funziona bene a una distanza e l'alias non è corretto.</span><span class="sxs-lookup"><span data-stu-id="db98b-171">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="db98b-172">Non lasciare che le parti del modello si estendano troppo oltre il rapporto dimensioni 1:1:1.</span><span class="sxs-lookup"><span data-stu-id="db98b-172">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="db98b-173">Si creeranno problemi di scalabilità.</span><span class="sxs-lookup"><span data-stu-id="db98b-173">It will create scaling problems.</span></span>

<span data-ttu-id="db98b-174">![Evitare i modelli a contrasto elevato, piccoli modelli di occupato](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="db98b-174">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="db98b-175">*Evitare i modelli a contrasto elevato, piccoli e occupati*</span><span class="sxs-lookup"><span data-stu-id="db98b-175">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="db98b-176">Come gestire il tipo</span><span class="sxs-lookup"><span data-stu-id="db98b-176">How to handle type</span></span>

* <span data-ttu-id="db98b-177">È consigliabile che il tipo riprenda circa 1/3 dell'utilità di avvio dell'app (o più).</span><span class="sxs-lookup"><span data-stu-id="db98b-177">We recommend your type takes up about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="db98b-178">Il tipo è l'elemento principale che offre agli utenti un'idea del fatto che l'utilità di avvio è, di fatto, un'utilità di avvio, quindi è interessante se è sostanziale.</span><span class="sxs-lookup"><span data-stu-id="db98b-178">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s substantial.</span></span>
* <span data-ttu-id="db98b-179">Evitare di rendere il tipo Super Wide: provare a mantenerlo entro i limiti delle dimensioni di base dei lanci di app (più o meno).</span><span class="sxs-lookup"><span data-stu-id="db98b-179">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="db98b-180">Il tipo flat può funzionare, ma può essere difficile da visualizzare da determinati angoli e da determinati ambienti.</span><span class="sxs-lookup"><span data-stu-id="db98b-180">Flat type can work, but it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="db98b-181">È possibile considerare di inserirlo in un oggetto solido o in uno sfondo per facilitare questa operazione.</span><span class="sxs-lookup"><span data-stu-id="db98b-181">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="db98b-182">L'aggiunta di una dimensione al tipo è gradevole in 3D.</span><span class="sxs-lookup"><span data-stu-id="db98b-182">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="db98b-183">L'ombreggiatura dei lati del tipo un colore più scuro può essere utile per migliorare la leggibilità.</span><span class="sxs-lookup"><span data-stu-id="db98b-183">Shading the sides of the type a different, darker color can help with readability.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="db98b-184">![Il tipo Flat senza uno sfondo può essere difficile da visualizzare da determinati angoli e in determinati ambienti ](images/flattype-640px.png) *il tipo Flat senza uno sfondo può essere difficile da visualizzare da determinati angoli e in determinati ambienti*</span><span class="sxs-lookup"><span data-stu-id="db98b-184">![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png) *Flat type without a backdrop can be hard to view from certain angles and in certain environments*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="db98b-185">![Il tipo con uno sfondo incorporato può funzionare correttamente ](images/flattypeandbkg-640px.png) *con uno sfondo incorporato*</span><span class="sxs-lookup"><span data-stu-id="db98b-185">![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="db98b-186">![Il tipo estruso può funzionare correttamente se si ombreggiano i lati il ](images/20171016-160221-mixedreality-640px.jpg) *tipo estruso può funzionare correttamente se si ombreggiano i lati*</span><span class="sxs-lookup"><span data-stu-id="db98b-186">![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg) *Extruded type can work well if you shade the sides*</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="db98b-187">**Colori del tipo che funzionano**</span><span class="sxs-lookup"><span data-stu-id="db98b-187">**Type colors that work**</span></span>

* <span data-ttu-id="db98b-188">White</span><span class="sxs-lookup"><span data-stu-id="db98b-188">White</span></span>
* <span data-ttu-id="db98b-189">Black</span><span class="sxs-lookup"><span data-stu-id="db98b-189">Black</span></span>
* <span data-ttu-id="db98b-190">Colore luminoso semi-saturato</span><span class="sxs-lookup"><span data-stu-id="db98b-190">Bright semi-saturated color</span></span>

<span data-ttu-id="db98b-191">![Digitare i colori che funzionano.](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="db98b-191">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="db98b-192">*Colori del tipo che funzionano*</span><span class="sxs-lookup"><span data-stu-id="db98b-192">*Type colors that work*</span></span>

### <a name="colors-to-avoid"></a><span data-ttu-id="db98b-193">Colori da evitare</span><span class="sxs-lookup"><span data-stu-id="db98b-193">Colors to avoid</span></span>

<span data-ttu-id="db98b-194">I colori del tipo che provocano problemi includono:</span><span class="sxs-lookup"><span data-stu-id="db98b-194">Type colors that cause trouble include:</span></span>

* <span data-ttu-id="db98b-195">Frequenze medie</span><span class="sxs-lookup"><span data-stu-id="db98b-195">Mid-tones</span></span>
* <span data-ttu-id="db98b-196">Grigio</span><span class="sxs-lookup"><span data-stu-id="db98b-196">Gray</span></span>
* <span data-ttu-id="db98b-197">Colori eccessivamente saturi o colori desaturi</span><span class="sxs-lookup"><span data-stu-id="db98b-197">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="db98b-198">![Tipi di colori che provocano problemi.](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="db98b-198">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="db98b-199">*Tipi di colori che provocano problemi*</span><span class="sxs-lookup"><span data-stu-id="db98b-199">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="db98b-200">Luce</span><span class="sxs-lookup"><span data-stu-id="db98b-200">Lighting</span></span>

<span data-ttu-id="db98b-201">L'illuminazione per l'utilità di avvio dell'app deriva dall'ambiente Cliff House.</span><span class="sxs-lookup"><span data-stu-id="db98b-201">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="db98b-202">Assicurarsi di testare l'utilità di avvio in diversi punti della casa, in modo da ottenere un aspetto positivo sia in chiaro che in ombreggiatura.</span><span class="sxs-lookup"><span data-stu-id="db98b-202">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="db98b-203">La buona notizia è che, se sono state seguite le altre linee guida di progettazione di questo documento, l'utilità di avvio dovrebbe essere in buona forma per la maggior parte dell'illuminazione della casa Cliff.</span><span class="sxs-lookup"><span data-stu-id="db98b-203">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="db98b-204">Un posto ideale per testare il modo in cui l'utilità di avvio Guarda le varie luci nell'ambiente è lo studio, la media room, in qualsiasi punto all'esterno e sul patio (l'area concreta con il prato).</span><span class="sxs-lookup"><span data-stu-id="db98b-204">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="db98b-205">Un altro test efficace consiste nell'inserirlo a metà luce e metà ombreggiatura per vedere come appare.</span><span class="sxs-lookup"><span data-stu-id="db98b-205">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="db98b-206">![Assicurarsi che l'utilità di avvio sia corretta sia in chiaro che in ombreggiatura.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="db98b-206">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="db98b-207">*Assicurarsi che l'utilità di avvio sia corretta in chiaro e in ombra*</span><span class="sxs-lookup"><span data-stu-id="db98b-207">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="db98b-208">Texturing</span><span class="sxs-lookup"><span data-stu-id="db98b-208">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="db98b-209">Creazione di trame</span><span class="sxs-lookup"><span data-stu-id="db98b-209">Authoring your textures</span></span>

<span data-ttu-id="db98b-210">Il formato finale dell'utilità di avvio delle app 3D sarà un file con estensione GLB, che viene creato usando la pipeline di PBR (rendering fisico).</span><span class="sxs-lookup"><span data-stu-id="db98b-210">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="db98b-211">Questo può essere un processo complesso, ora è il momento giusto per impiegare un artista tecnico, se non è già stato fatto.</span><span class="sxs-lookup"><span data-stu-id="db98b-211">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="db98b-212">Se si è bravi fai da te, il tempo necessario per la [ricerca e l'apprendimento della terminologia di PBR](https://wiki.polycount.com/wiki/PBR) e cosa accade dietro le quinte prima di iniziare ti aiuterà a evitare errori comuni.</span><span class="sxs-lookup"><span data-stu-id="db98b-212">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](https://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="db98b-213">![Esempio: app nota aggiornata](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="db98b-213">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="db98b-214">*Esempio di avvio dell'app 3D (app fittizia)*</span><span class="sxs-lookup"><span data-stu-id="db98b-214">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="recommended-authoring-tool"></a><span data-ttu-id="db98b-215">Strumento di creazione consigliato</span><span class="sxs-lookup"><span data-stu-id="db98b-215">Recommended authoring tool</span></span>

<span data-ttu-id="db98b-216">Per creare il file finale, è consigliabile usare il [pittore di sostanze](https://www.allegorithmic.com/products/substance-painter) Allegorithmic.</span><span class="sxs-lookup"><span data-stu-id="db98b-216">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="db98b-217">Se non si ha familiarità con la creazione di shader PBR in sostanza Painter, ecco un' [esercitazione](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span><span class="sxs-lookup"><span data-stu-id="db98b-217">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="db98b-218">(In alternativa [, il](https://3dcoat.com/home/) [Quixel Suite 2](https://quixel.se/suite2/)o [uistitì toolbag](https://www.marmoset.co/toolbag/) funziona anche se si ha familiarità con uno di questi).</span><span class="sxs-lookup"><span data-stu-id="db98b-218">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="db98b-219">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="db98b-219">Best practices</span></span>

* <span data-ttu-id="db98b-220">Se l'oggetto di avvio dell'app è stato creato per PBR, dovrebbe essere semplice convertirlo per l'ambiente Cliff House.</span><span class="sxs-lookup"><span data-stu-id="db98b-220">If your app launcher object was authored for PBR, it should be straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="db98b-221">Lo shader sta aspettando un flusso di lavoro di metallo/rugosità: lo shader Unreal PBR è un facsimile di chiusura.</span><span class="sxs-lookup"><span data-stu-id="db98b-221">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="db98b-222">Quando si esportano le trame, tenere presenti le [dimensioni consigliate](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) .</span><span class="sxs-lookup"><span data-stu-id="db98b-222">When exporting your textures, keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="db98b-223">Assicurarsi di compilare gli oggetti per l'illuminazione in tempo reale, ovvero:</span><span class="sxs-lookup"><span data-stu-id="db98b-223">Make sure to build your objects for real-time lighting—this means:</span></span>
  * <span data-ttu-id="db98b-224">Evitare le ombre cotte o disegnare le ombre</span><span class="sxs-lookup"><span data-stu-id="db98b-224">Avoid baked shadows – or painted shadows</span></span>
  * <span data-ttu-id="db98b-225">Evitare l'illuminazione al forno nelle trame</span><span class="sxs-lookup"><span data-stu-id="db98b-225">Avoid baked lighting in the textures</span></span>
  * <span data-ttu-id="db98b-226">Usare uno dei pacchetti di creazione materiali di PBR per ottenere le mappe corrette generate per lo shader</span><span class="sxs-lookup"><span data-stu-id="db98b-226">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="db98b-227">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="db98b-227">See also</span></span>

* [<span data-ttu-id="db98b-228">Creare modelli 3D da usare nella Home realtà mista</span><span class="sxs-lookup"><span data-stu-id="db98b-228">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="db98b-229">Implementare utilità di avvio per app 3D (app UWP)</span><span class="sxs-lookup"><span data-stu-id="db98b-229">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="db98b-230">Implementare utilità di avvio per app 3D (app Win32)</span><span class="sxs-lookup"><span data-stu-id="db98b-230">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
