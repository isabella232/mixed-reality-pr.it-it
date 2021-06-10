---
title: Tavola periodica degli elementi
description: Informazioni su come impostare il disaserazione di una matrice di oggetti nello spazio 3D con vari tipi di superficie usando una raccolta Di oggetti con la tabella periodica dell'app di esempio Elements.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, progettazione, app di esempio, controlli, MRTK, Mixed Reality Toolkit, Unity, app di esempio, app di esempio, open source, Microsoft Store, HoloLens, visore per realtà mista, visore per realtà mista windows, visore per realtà virtuale
ms.openlocfilehash: ed8c35fc6467322c25b92924b134f176fa4a9b47
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743410"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="db46a-104">Tavola periodica degli elementi</span><span class="sxs-lookup"><span data-stu-id="db46a-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="db46a-105">Questo articolo illustra un esempio esplorativo creato in [Mixed Reality Design Labs,](https://github.com/Microsoft/MRDesignLabs_Unity)un luogo in cui vengono illustrate le informazioni e i suggerimenti per lo sviluppo di app di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="db46a-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="db46a-106">Gli articoli e il codice relativi alla progettazione si evolvono man appena si effettuano nuove individuazioni.</span><span class="sxs-lookup"><span data-stu-id="db46a-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="db46a-107">[La tabella periodica degli elementi è](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) un'app di esempio open source di Microsoft Mixed Reality Design Labs.</span><span class="sxs-lookup"><span data-stu-id="db46a-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="db46a-108">Informazioni su come impostare una matrice di oggetti nello spazio 3D con vari tipi di superficie usando una **[raccolta Di oggetti](../../design/object-collection.md)**.</span><span class="sxs-lookup"><span data-stu-id="db46a-108">Learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="db46a-109">Informazioni anche su come creare oggetti interagiscibili che rispondono agli input standard da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="db46a-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="db46a-110">È possibile usare i componenti di questo progetto per creare un'esperienza di app di realtà mista personalizzata.</span><span class="sxs-lookup"><span data-stu-id="db46a-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Tabella Period dell'app Elements](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="db46a-112">Video demo</span><span class="sxs-lookup"><span data-stu-id="db46a-112">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="db46a-113">Registrato con HoloLens 2 usando Acquisizione realtà mista</span><span class="sxs-lookup"><span data-stu-id="db46a-113">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="db46a-114">Informazioni sull'app</span><span class="sxs-lookup"><span data-stu-id="db46a-114">About the app</span></span>

<span data-ttu-id="db46a-115">La tabella periodica degli elementi visualizza gli elementi chimica e ognuna delle relative proprietà in uno spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="db46a-115">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="db46a-116">Incorpora le interazioni di base di HoloLens, ad esempio lo sguardo e il tocco dell'aria.</span><span class="sxs-lookup"><span data-stu-id="db46a-116">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="db46a-117">Gli utenti possono ottenere informazioni sugli elementi con modelli 3D animati.</span><span class="sxs-lookup"><span data-stu-id="db46a-117">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="db46a-118">Possono comprendere visivamente la shell degli elettroni di un elemento e il relativo nucleo, costituito da protoni e neutroni.</span><span class="sxs-lookup"><span data-stu-id="db46a-118">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="db46a-119">Sfondo</span><span class="sxs-lookup"><span data-stu-id="db46a-119">Background</span></span>

<span data-ttu-id="db46a-120">Dopo aver provato HoloLens per la prima volta, ho voluto sperimentare un'app per tabelle periodiche in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="db46a-120">After I first experienced HoloLens, I knew I wanted to experiment with a periodic table app in mixed reality.</span></span> <span data-ttu-id="db46a-121">Poiché ogni elemento ha molti punti dati visualizzati con testo, ho pensato che sarebbe stato un argomento importante per esplorare la composizione tipografica in uno spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="db46a-121">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="db46a-122">Offrire agli utenti la possibilità di visualizzare il modello di elettroni dell'elemento è stata un'altra parte interessante di questo progetto.</span><span class="sxs-lookup"><span data-stu-id="db46a-122">Giving users the chance to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="db46a-123">Progettazione</span><span class="sxs-lookup"><span data-stu-id="db46a-123">Design</span></span>

<span data-ttu-id="db46a-124">Per la visualizzazione predefinita della tabella periodica, ho pensato a caselle tridimensionali che conterrebbero il modello di elettroni di ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="db46a-124">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="db46a-125">La superficie di ogni scatola sarebbe traslucida in modo che l'utente possa avere un'idea approssimativa del volume dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="db46a-125">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="db46a-126">Con lo sguardo fisso e il tocco dell'aria, l'utente può aprire una visualizzazione dettagliata di ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="db46a-126">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="db46a-127">Per rendere la transizione tra la visualizzazione tabella e la visualizzazione dettagli uniforme e naturale, l'ho resa simile all'interazione fisica di un box che si apre nella vita reale.</span><span class="sxs-lookup"><span data-stu-id="db46a-127">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="db46a-128">![Sketch di progettazione](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="db46a-128">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="db46a-129">*Progettare gli sketch*</span><span class="sxs-lookup"><span data-stu-id="db46a-129">*Design sketches*</span></span>

<span data-ttu-id="db46a-130">Nella visualizzazione dettagli, si desiderava visualizzare le informazioni di ogni elemento con testo ben sottoposto a rendering nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="db46a-130">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="db46a-131">Il modello di elettroni 3D animato viene visualizzato nell'area centrale e può essere visualizzato da angolazioni diverse.</span><span class="sxs-lookup"><span data-stu-id="db46a-131">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interazione](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="db46a-133">![Prototipi](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="db46a-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="db46a-134">*Prototipi di interazione*</span><span class="sxs-lookup"><span data-stu-id="db46a-134">*Interaction prototypes*</span></span>

<span data-ttu-id="db46a-135">L'utente può modificare il tipo di superficie toccando in aria i pulsanti nella parte inferiore della tabella. È possibile passare da un piano, un cilindro, una sfera e una dispersione.</span><span class="sxs-lookup"><span data-stu-id="db46a-135">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere, and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="db46a-136">Controlli e modelli comuni usati in questa app</span><span class="sxs-lookup"><span data-stu-id="db46a-136">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="db46a-137">Oggetto interagiscibile (pulsante)</span><span class="sxs-lookup"><span data-stu-id="db46a-137">Interactable object (button)</span></span>

<span data-ttu-id="db46a-138">[L'oggetto interagiscibile](../../design/interactable-object.md) è un oggetto che può rispondere agli input HoloLens di base.</span><span class="sxs-lookup"><span data-stu-id="db46a-138">[Interactable object](../../design/interactable-object.md) is an object, which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="db46a-139">Viene fornito come prefab/script, che è possibile applicare facilmente a qualsiasi oggetto.</span><span class="sxs-lookup"><span data-stu-id="db46a-139">It's provided as a prefab/script, which you can easily apply to any object.</span></span> <span data-ttu-id="db46a-140">Ad esempio, è possibile rendere una tazzina di caffè nella scena interagibile e rispondere a input come lo sguardo, il tocco dell'aria, la navigazione e i movimenti di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="db46a-140">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation, and manipulation gestures.</span></span> [<span data-ttu-id="db46a-141">Scopri di più</span><span class="sxs-lookup"><span data-stu-id="db46a-141">Learn more</span></span>](../../design/interactable-object.md)

![Oggetto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="db46a-143">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="db46a-143">Object collection</span></span>

<span data-ttu-id="db46a-144">[La raccolta](../../design/object-collection.md) di oggetti è un oggetto che consente di eseguire il disaser di più oggetti in varie forme.</span><span class="sxs-lookup"><span data-stu-id="db46a-144">[Object collection](../../design/object-collection.md) is an object, which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="db46a-145">Supporta piano, cilindro, sfera e dispersione.</span><span class="sxs-lookup"><span data-stu-id="db46a-145">It supports plane, cylinder, sphere, and scatter.</span></span> <span data-ttu-id="db46a-146">È possibile configurare proprietà aggiuntive, ad esempio raggio, numero di righe e spaziatura.</span><span class="sxs-lookup"><span data-stu-id="db46a-146">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="db46a-147">Scopri di più</span><span class="sxs-lookup"><span data-stu-id="db46a-147">Learn more</span></span>](../../design/object-collection.md)

![Raccolta di oggetti](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="db46a-149">Dettagli tecnici</span><span class="sxs-lookup"><span data-stu-id="db46a-149">Technical details</span></span>

<span data-ttu-id="db46a-150">Gli script e i prefab per la tabella periodica dell'app Elements sono disponibili in [GitHub di Mixed Reality Design Labs.](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)</span><span class="sxs-lookup"><span data-stu-id="db46a-150">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="db46a-151">Storia di porting per HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="db46a-151">Porting story for HoloLens 2</span></span>

<span data-ttu-id="db46a-152">Leggere la storia su come è stata aggiornata l'app Tabella periodica degli elementi con HoloLens 2 interazioni istintiva del cliente.</span><span class="sxs-lookup"><span data-stu-id="db46a-152">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="db46a-153">Tavola periodica degli elementi 2.0</span><span class="sxs-lookup"><span data-stu-id="db46a-153">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="db46a-154">Informazioni sull'autore</span><span class="sxs-lookup"><span data-stu-id="db46a-154">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="db46a-155"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="db46a-155"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="db46a-156">Designer di esperienza utente @Microsoft</span><span class="sxs-lookup"><span data-stu-id="db46a-156">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="db46a-157">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="db46a-157">See also</span></span>

* <span data-ttu-id="db46a-158">[Hub di esempi MRTK](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="db46a-158">[MRTK Examples Hub](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="db46a-159">[Superfici](sampleapp-surfaces.md) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="db46a-159">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="db46a-160">Tavola periodica degli elementi 2.0</span><span class="sxs-lookup"><span data-stu-id="db46a-160">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="db46a-161">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="db46a-161">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)