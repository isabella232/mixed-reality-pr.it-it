---
title: Tavola periodica degli elementi
description: La tabella periodica degli elementi è un'app di esempio Open Source di Microsoft Mixed Reality Design Labs. Informazioni su come definire il layout di una matrice di oggetti nello spazio 3D con vari tipi di superficie usando una raccolta di oggetti.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, app di esempio, controlli, MRTK, Toolkit per realtà mista, Unity, app di esempio, app di esempio, open source, Microsoft Store, HoloLens, auricolare per realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: a4099c889fee886e63d3a8b773398a250621f26e
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010182"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="d781a-105">Tavola periodica degli elementi</span><span class="sxs-lookup"><span data-stu-id="d781a-105">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="d781a-106">Questo articolo illustra un esempio esplorativo creato nei [laboratori di progettazione della realtà mista](https://github.com/Microsoft/MRDesignLabs_Unity), un posto in cui si condividono le informazioni e suggerimenti per lo sviluppo di app di realtà miste.</span><span class="sxs-lookup"><span data-stu-id="d781a-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="d781a-107">Gli articoli e il codice correlati alla progettazione si evolveranno Man mano che si effettuano nuove individuazioni.</span><span class="sxs-lookup"><span data-stu-id="d781a-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="d781a-108">[La tabella periodica degli elementi](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) è un'app di esempio Open Source di Microsoft Mixed Reality Design Labs.</span><span class="sxs-lookup"><span data-stu-id="d781a-108">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="d781a-109">Informazioni su come disporre una matrice di oggetti nello spazio 3D con vari tipi di superficie usando una **[raccolta di oggetti](../../design/object-collection.md)**.</span><span class="sxs-lookup"><span data-stu-id="d781a-109">Learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="d781a-110">Viene inoltre illustrato come creare oggetti interagibili che rispondono agli input standard da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d781a-110">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="d781a-111">È possibile usare i componenti di questo progetto per creare un'esperienza di app per realtà mista.</span><span class="sxs-lookup"><span data-stu-id="d781a-111">You can use this project's components to create your own mixed reality app experience.</span></span>

![Tabella del periodo dell'app elementi](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="d781a-113">Video dimostrativo</span><span class="sxs-lookup"><span data-stu-id="d781a-113">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="d781a-114">Registrato con HoloLens 2 con l'acquisizione di realtà mista</span><span class="sxs-lookup"><span data-stu-id="d781a-114">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="d781a-115">Informazioni sull'app</span><span class="sxs-lookup"><span data-stu-id="d781a-115">About the app</span></span>

<span data-ttu-id="d781a-116">La tabella periodica degli elementi Visualizza gli elementi chimici e ognuna delle relative proprietà in uno spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="d781a-116">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="d781a-117">Incorpora le interazioni di base di HoloLens, ad esempio lo sguardo e il tocco aereo.</span><span class="sxs-lookup"><span data-stu-id="d781a-117">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="d781a-118">Gli utenti possono ottenere informazioni sugli elementi con i modelli 3D animati.</span><span class="sxs-lookup"><span data-stu-id="d781a-118">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="d781a-119">Possono comprendere visivamente la Shell degli elettroni di un elemento e il suo nucleo, composto da protoni e neutroni.</span><span class="sxs-lookup"><span data-stu-id="d781a-119">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="d781a-120">Background</span><span class="sxs-lookup"><span data-stu-id="d781a-120">Background</span></span>

<span data-ttu-id="d781a-121">Dopo aver sperimentato HoloLens, sapevo di voler sperimentare un'app di tabella periodica in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="d781a-121">After I first experienced HoloLens, I knew I wanted to experiment with a periodic table app in mixed reality.</span></span> <span data-ttu-id="d781a-122">Poiché ogni elemento dispone di molti punti dati visualizzati con testo, ho pensato che sarebbe stato molto soggetto per l'esplorazione della composizione tipografica in uno spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="d781a-122">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="d781a-123">Fornire agli utenti la possibilità di visualizzare il modello Electron dell'elemento era un'altra parte interessante di questo progetto.</span><span class="sxs-lookup"><span data-stu-id="d781a-123">Giving users the chance to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="d781a-124">Progettazione</span><span class="sxs-lookup"><span data-stu-id="d781a-124">Design</span></span>

<span data-ttu-id="d781a-125">Per la visualizzazione predefinita della tabella periodica, ho immaginato le caselle tridimensionali che contenevano il modello Electron di ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="d781a-125">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="d781a-126">La superficie di ogni casella sarà translucida, in modo che l'utente possa ottenere un'idea approssimativa del volume dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="d781a-126">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="d781a-127">Con lo sguardo e il tocco aereo, l'utente può aprire una visualizzazione dettagliata di ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="d781a-127">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="d781a-128">Per fare in modo che la transizione tra la visualizzazione tabella e la visualizzazione dei dettagli sia uniforme e naturale, è stata creata in modo analogo all'interazione fisica di una scatola aperta in vita reale.</span><span class="sxs-lookup"><span data-stu-id="d781a-128">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="d781a-129">![Schizzo di progettazione](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="d781a-129">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="d781a-130">*Schizzi di progettazione*</span><span class="sxs-lookup"><span data-stu-id="d781a-130">*Design sketches*</span></span>

<span data-ttu-id="d781a-131">In visualizzazione dettagli, ho voluto visualizzare le informazioni di ogni elemento con un testo con rendering bello nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="d781a-131">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="d781a-132">Il modello di elettroni 3D animato viene visualizzato nell'area centrale e può essere visualizzato da diverse angolazioni.</span><span class="sxs-lookup"><span data-stu-id="d781a-132">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interazione](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="d781a-134">![Prototipi](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="d781a-134">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="d781a-135">*Prototipi di interazione*</span><span class="sxs-lookup"><span data-stu-id="d781a-135">*Interaction prototypes*</span></span>

<span data-ttu-id="d781a-136">L'utente può modificare il tipo di superficie per aria toccando i pulsanti nella parte inferiore della tabella, che possono spostarsi tra il piano, il cilindro, la sfera e la dispersione.</span><span class="sxs-lookup"><span data-stu-id="d781a-136">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere, and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="d781a-137">Controlli e modelli comuni usati in questa app</span><span class="sxs-lookup"><span data-stu-id="d781a-137">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="d781a-138">Oggetto interagibile (pulsante)</span><span class="sxs-lookup"><span data-stu-id="d781a-138">Interactable object (button)</span></span>

<span data-ttu-id="d781a-139">L' [oggetto interagibile](../../design/interactable-object.md) è un oggetto che può rispondere agli input HoloLens di base.</span><span class="sxs-lookup"><span data-stu-id="d781a-139">[Interactable object](../../design/interactable-object.md) is an object, which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="d781a-140">Viene fornito come prefabbricato/script, che è possibile applicare facilmente a qualsiasi oggetto.</span><span class="sxs-lookup"><span data-stu-id="d781a-140">It's provided as a prefab/script, which you can easily apply to any object.</span></span> <span data-ttu-id="d781a-141">Ad esempio, è possibile rendere interattivo un caffè nella scena e rispondere a input come lo sguardo, il tocco aereo, la navigazione e i movimenti di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="d781a-141">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation, and manipulation gestures.</span></span> [<span data-ttu-id="d781a-142">Scopri di più</span><span class="sxs-lookup"><span data-stu-id="d781a-142">Learn more</span></span>](../../design/interactable-object.md)

![oggetto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="d781a-144">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="d781a-144">Object collection</span></span>

<span data-ttu-id="d781a-145">La [raccolta](../../design/object-collection.md) di oggetti è un oggetto che consente di disporre più oggetti in varie forme.</span><span class="sxs-lookup"><span data-stu-id="d781a-145">[Object collection](../../design/object-collection.md) is an object, which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="d781a-146">Supporta piani, cilindri, sfere e dispersione.</span><span class="sxs-lookup"><span data-stu-id="d781a-146">It supports plane, cylinder, sphere, and scatter.</span></span> <span data-ttu-id="d781a-147">È possibile configurare proprietà aggiuntive, ad esempio raggio, numero di righe e spaziatura.</span><span class="sxs-lookup"><span data-stu-id="d781a-147">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="d781a-148">Scopri di più</span><span class="sxs-lookup"><span data-stu-id="d781a-148">Learn more</span></span>](../../design/object-collection.md)

![Raccolta di oggetti](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="d781a-150">Dettagli tecnici</span><span class="sxs-lookup"><span data-stu-id="d781a-150">Technical details</span></span>

<span data-ttu-id="d781a-151">È possibile trovare gli script e i prefabbricati per la tabella periodica dell'app elementi nel [progetto Mixed Reality Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="d781a-151">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="d781a-152">Storia di porting per HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d781a-152">Porting story for HoloLens 2</span></span>

<span data-ttu-id="d781a-153">Leggere la storia relativa alla modalità di aggiornamento della tabella periodica dell'app elementi con le interazioni istintive di HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d781a-153">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="d781a-154">Tavola periodica degli elementi 2.0</span><span class="sxs-lookup"><span data-stu-id="d781a-154">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="d781a-155">Informazioni sull'autore</span><span class="sxs-lookup"><span data-stu-id="d781a-155">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="d781a-156"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="d781a-156"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="d781a-157">Designer di esperienza utente @Microsoft</span><span class="sxs-lookup"><span data-stu-id="d781a-157">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="d781a-158">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d781a-158">See also</span></span>

* <span data-ttu-id="d781a-159">[Hub di esempi MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="d781a-159">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="d781a-160">[Superfici](sampleapp-surfaces.md) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="d781a-160">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="d781a-161">Tavola periodica degli elementi 2.0</span><span class="sxs-lookup"><span data-stu-id="d781a-161">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="d781a-162">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="d781a-162">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)