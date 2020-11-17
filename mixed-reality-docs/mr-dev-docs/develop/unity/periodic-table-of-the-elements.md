---
title: Tavola periodica degli elementi
description: La tabella periodica degli elementi è un'app di esempio Open Source di Microsoft Mixed Reality Design Labs, in cui è possibile apprendere come disporre una matrice di oggetti nello spazio 3D con vari tipi di superficie usando una raccolta di oggetti.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, app di esempio, controlli, MRTK, Toolkit per realtà mista, Unity, app di esempio, app di esempio, open source, Microsoft Store, HoloLens, auricolare per realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 4b85631fb044ee0b24c003f7808fd0455b87deec
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677680"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="8a496-104">Tavola periodica degli elementi</span><span class="sxs-lookup"><span data-stu-id="8a496-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="8a496-105">Questo articolo illustra un esempio esplorativo creato nei [laboratori di progettazione della realtà mista](https://github.com/Microsoft/MRDesignLabs_Unity), un posto in cui si condividono le informazioni e suggerimenti per lo sviluppo di app di realtà miste.</span><span class="sxs-lookup"><span data-stu-id="8a496-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="8a496-106">Gli articoli e il codice correlati alla progettazione si evolveranno Man mano che si effettuano nuove individuazioni.</span><span class="sxs-lookup"><span data-stu-id="8a496-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="8a496-107">[La tabella periodica degli elementi](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) è un'app di esempio Open Source di Microsoft Mixed Reality Design Labs.</span><span class="sxs-lookup"><span data-stu-id="8a496-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="8a496-108">Con questo progetto è possibile apprendere come disporre una matrice di oggetti nello spazio 3D con vari tipi di superficie usando una **[raccolta di oggetti](../../design/object-collection.md)**.</span><span class="sxs-lookup"><span data-stu-id="8a496-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="8a496-109">Viene inoltre illustrato come creare oggetti interagibili che rispondono agli input standard da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8a496-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="8a496-110">È possibile usare i componenti di questo progetto per creare un'esperienza di app per realtà mista.</span><span class="sxs-lookup"><span data-stu-id="8a496-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Tabella del periodo dell'app elementi](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="8a496-112">Video dimostrativo</span><span class="sxs-lookup"><span data-stu-id="8a496-112">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="8a496-113">Registrato con HoloLens 2 con l'acquisizione di realtà mista</span><span class="sxs-lookup"><span data-stu-id="8a496-113">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="8a496-114">Informazioni sull'app</span><span class="sxs-lookup"><span data-stu-id="8a496-114">About the app</span></span>

<span data-ttu-id="8a496-115">La tabella periodica degli elementi Visualizza gli elementi chimici e ognuna delle relative proprietà in uno spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="8a496-115">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="8a496-116">Incorpora le interazioni di base di HoloLens, ad esempio lo sguardo e il tocco aereo.</span><span class="sxs-lookup"><span data-stu-id="8a496-116">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="8a496-117">Gli utenti possono ottenere informazioni sugli elementi con i modelli 3D animati.</span><span class="sxs-lookup"><span data-stu-id="8a496-117">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="8a496-118">Possono comprendere visivamente la Shell degli elettroni di un elemento e il suo nucleo, composto da protoni e neutroni.</span><span class="sxs-lookup"><span data-stu-id="8a496-118">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="8a496-119">Sfondo</span><span class="sxs-lookup"><span data-stu-id="8a496-119">Background</span></span>

<span data-ttu-id="8a496-120">Dopo la prima volta che ho sperimentato HoloLens, un'app di tabella periodica era un'idea che ho voluto sperimentare in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="8a496-120">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="8a496-121">Poiché ogni elemento dispone di molti punti dati visualizzati con testo, ho pensato che sarebbe stato molto soggetto per l'esplorazione della composizione tipografica in uno spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="8a496-121">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="8a496-122">La possibilità di visualizzare il modello Electron dell'elemento era un'altra parte interessante di questo progetto.</span><span class="sxs-lookup"><span data-stu-id="8a496-122">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="8a496-123">Progettazione</span><span class="sxs-lookup"><span data-stu-id="8a496-123">Design</span></span>

<span data-ttu-id="8a496-124">Per la visualizzazione predefinita della tabella periodica, ho immaginato le caselle tridimensionali che contenevano il modello Electron di ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="8a496-124">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="8a496-125">La superficie di ogni casella sarà translucida, in modo che l'utente possa ottenere un'idea approssimativa del volume dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="8a496-125">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="8a496-126">Con lo sguardo e il tocco aereo, l'utente può aprire una visualizzazione dettagliata di ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="8a496-126">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="8a496-127">Per fare in modo che la transizione tra la visualizzazione tabella e la visualizzazione dei dettagli sia uniforme e naturale, è stata creata in modo analogo all'interazione fisica di una scatola aperta in vita reale.</span><span class="sxs-lookup"><span data-stu-id="8a496-127">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="8a496-128">![Schizzo di progettazione](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="8a496-128">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="8a496-129">*Schizzi di progettazione*</span><span class="sxs-lookup"><span data-stu-id="8a496-129">*Design sketches*</span></span>

<span data-ttu-id="8a496-130">In visualizzazione dettagli, ho voluto visualizzare le informazioni di ogni elemento con un testo con rendering bello nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="8a496-130">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="8a496-131">Il modello di elettroni 3D animato viene visualizzato nell'area centrale e può essere visualizzato da diverse angolazioni.</span><span class="sxs-lookup"><span data-stu-id="8a496-131">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interazione](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="8a496-133">![Prototipi](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="8a496-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="8a496-134">*Prototipi di interazione*</span><span class="sxs-lookup"><span data-stu-id="8a496-134">*Interaction prototypes*</span></span>

<span data-ttu-id="8a496-135">L'utente può modificare il tipo di superficie per aria toccando i pulsanti nella parte inferiore della tabella, che possono spostarsi tra il piano, il cilindro, la sfera e la dispersione.</span><span class="sxs-lookup"><span data-stu-id="8a496-135">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="8a496-136">Controlli e modelli comuni usati in questa app</span><span class="sxs-lookup"><span data-stu-id="8a496-136">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="8a496-137">Oggetto interagibile (pulsante)</span><span class="sxs-lookup"><span data-stu-id="8a496-137">Interactable object (button)</span></span>

<span data-ttu-id="8a496-138">L' [oggetto interagibile](../../design/interactable-object.md) è un oggetto che può rispondere agli input HoloLens di base.</span><span class="sxs-lookup"><span data-stu-id="8a496-138">[Interactable object](../../design/interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="8a496-139">Viene fornito come prefabbricato/script che è possibile applicare facilmente a qualsiasi oggetto.</span><span class="sxs-lookup"><span data-stu-id="8a496-139">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="8a496-140">Ad esempio, è possibile rendere interattivo un caffè nella scena e rispondere a input come lo sguardo, il tocco aereo, i movimenti di spostamento e manipolazione.</span><span class="sxs-lookup"><span data-stu-id="8a496-140">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="8a496-141">Scopri di più</span><span class="sxs-lookup"><span data-stu-id="8a496-141">Learn more</span></span>](../../design/interactable-object.md)

![oggetto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="8a496-143">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="8a496-143">Object collection</span></span>

<span data-ttu-id="8a496-144">La [raccolta](../../design/object-collection.md) di oggetti è un oggetto che consente di disporre più oggetti in varie forme.</span><span class="sxs-lookup"><span data-stu-id="8a496-144">[Object collection](../../design/object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="8a496-145">Supporta piani, cilindri, sfere e dispersione.</span><span class="sxs-lookup"><span data-stu-id="8a496-145">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="8a496-146">È possibile configurare proprietà aggiuntive, ad esempio raggio, numero di righe e spaziatura.</span><span class="sxs-lookup"><span data-stu-id="8a496-146">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="8a496-147">Scopri di più</span><span class="sxs-lookup"><span data-stu-id="8a496-147">Learn more</span></span>](../../design/object-collection.md)

![Raccolta di oggetti](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="8a496-149">Dettagli tecnici</span><span class="sxs-lookup"><span data-stu-id="8a496-149">Technical details</span></span>

<span data-ttu-id="8a496-150">È possibile trovare gli script e i prefabbricati per la tabella periodica dell'app elementi nel [progetto Mixed Reality Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="8a496-150">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="8a496-151">Storia di porting per HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8a496-151">Porting story for HoloLens 2</span></span>

<span data-ttu-id="8a496-152">Leggere la storia relativa alla modalità di aggiornamento della tabella periodica dell'app elementi con le interazioni istintive di HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8a496-152">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="8a496-153">Tavola periodica degli elementi 2.0</span><span class="sxs-lookup"><span data-stu-id="8a496-153">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="8a496-154">Informazioni sull'autore</span><span class="sxs-lookup"><span data-stu-id="8a496-154">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="8a496-155"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="8a496-155"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="8a496-156">Designer di esperienza utente @Microsoft</span><span class="sxs-lookup"><span data-stu-id="8a496-156">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="8a496-157">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8a496-157">See also</span></span>

* <span data-ttu-id="8a496-158">[Hub di esempi MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="8a496-158">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="8a496-159">[Superfici](sampleapp-surfaces.md) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="8a496-159">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="8a496-160">Tavola periodica degli elementi 2.0</span><span class="sxs-lookup"><span data-stu-id="8a496-160">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="8a496-161">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="8a496-161">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)