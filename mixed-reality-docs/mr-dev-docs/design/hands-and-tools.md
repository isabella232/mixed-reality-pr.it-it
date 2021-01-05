---
title: Mani e controller del movimento
description: Informazioni sui modelli di interazione di hands and Motion Controllers, che possono rimuovere il limite tra il virtuale e il fisico.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Realtà mista, praticità, controller di movimento, interazione, progettazione, cuffie per realtà mista, cuffie con la realtà mista di Windows, cuffie per realtà virtuale, HoloLens, MRTK, Toolkit realtà mista
ms.openlocfilehash: 1dffdd5f3471993dfdb5e504e4c5b87ec0bfef7d
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847318"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="45ecc-104">Mani e controller del movimento</span><span class="sxs-lookup"><span data-stu-id="45ecc-104">Hands and motion controllers</span></span>

## <a name="scenarios"></a><span data-ttu-id="45ecc-105">Scenari</span><span class="sxs-lookup"><span data-stu-id="45ecc-105">Scenarios</span></span>

<span data-ttu-id="45ecc-106">Dopo aver letto la [Panoramica sull'interazione](interaction-fundamentals.md), è possibile scegliere il modello di interazione del controller di movimento e della mano.</span><span class="sxs-lookup"><span data-stu-id="45ecc-106">After reading the [interaction overview](interaction-fundamentals.md), you choose the hand and motion controller interaction model.</span></span> <span data-ttu-id="45ecc-107">Ciò significa che si sta sviluppando un'applicazione che richiede agli utenti di usare due mani per interagire con il mondo olografico.</span><span class="sxs-lookup"><span data-stu-id="45ecc-107">This means you're developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="45ecc-108">L'applicazione è in grado di raggiungere l'obiettivo di rimuovere il limite tra virtuale e fisico.</span><span class="sxs-lookup"><span data-stu-id="45ecc-108">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="45ecc-109">Alcuni scenari specifici potrebbero essere:</span><span class="sxs-lookup"><span data-stu-id="45ecc-109">Some specific scenarios might be:</span></span>
* <span data-ttu-id="45ecc-110">Fornire agli Information Worker schermate virtuali 2D con inviti dell'interfaccia utente per visualizzare e controllare il contenuto</span><span class="sxs-lookup"><span data-stu-id="45ecc-110">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="45ecc-111">Esercitazione e guide per i ruoli di lavoro di prima linea per le linee di assemblaggio Factory</span><span class="sxs-lookup"><span data-stu-id="45ecc-111">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="45ecc-112">Sviluppare strumenti professionali per l'assistenza e la formazione per professionisti medici</span><span class="sxs-lookup"><span data-stu-id="45ecc-112">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="45ecc-113">Usare oggetti virtuali 3D per decorare il mondo reale o creare un secondo mondo</span><span class="sxs-lookup"><span data-stu-id="45ecc-113">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="45ecc-114">Creare servizi e giochi basati sulla posizione usando il mondo reale come sfondo</span><span class="sxs-lookup"><span data-stu-id="45ecc-114">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="45ecc-115">Modalità di controllo delle mani e del movimento</span><span class="sxs-lookup"><span data-stu-id="45ecc-115">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="45ecc-116">[![Manipolazione diretta con le mani](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="45ecc-116">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsbr"></a>[<span data-ttu-id="45ecc-117">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="45ecc-117">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="45ecc-118">Modalità di applicazione della potenza di mano che gli utenti possono usare per toccare e modificare gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="45ecc-118">Modality applying the power of hands that users can use to touch and manipulate holograms.</span></span> <span data-ttu-id="45ecc-119">Grazie all'uso di esperienze quotidiane e alla creazione di affordances visivi appropriati, gli utenti possono usare lo stesso modo per modificare gli oggetti reali per interagire con quelli virtuali.</span><span class="sxs-lookup"><span data-stu-id="45ecc-119">By using daily life experiences and providing proper visual affordances, users can use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="45ecc-120">[![Puntamento e commit con le mani](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="45ecc-120">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handsbr"></a>[<span data-ttu-id="45ecc-121">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="45ecc-121">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="45ecc-122">Questa modalità consente agli utenti di interagire con gli ologrammi a distanza.</span><span class="sxs-lookup"><span data-stu-id="45ecc-122">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="45ecc-123">Consente agli utenti di sfruttare al meglio i dintorni.</span><span class="sxs-lookup"><span data-stu-id="45ecc-123">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="45ecc-124">Gli utenti possono posizionare gli ologrammi ovunque e continuare ad accedervi da qualsiasi distanza.</span><span class="sxs-lookup"><span data-stu-id="45ecc-124">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="45ecc-125">I modelli e i movimenti mentali per controllare e modificare gli ologrammi 2D e 3D sono sincronizzati con quelli di manipolazione diretta.</span><span class="sxs-lookup"><span data-stu-id="45ecc-125">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="45ecc-126">[![Controller del movimento](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="45ecc-126">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersbr"></a>[<span data-ttu-id="45ecc-127">Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="45ecc-127">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="45ecc-128">I controller di movimento estendono le funzionalità fisiche dell'utente con interazioni precise in un intervallo di distanze durante l'uso di una o entrambe le mani.</span><span class="sxs-lookup"><span data-stu-id="45ecc-128">Motion controllers extend the user's physical capabilities with precise interactions across a range of distances while using one or both hands.</span></span> <span data-ttu-id="45ecc-129">Questi accessori hardware forniscono collegamenti a molte interazioni di uso comune e forniscono commenti e suggerimenti tattili per varie azioni.</span><span class="sxs-lookup"><span data-stu-id="45ecc-129">These hardware accessories provide shortcuts to many commonly used interactions and provide sure-footed, tactile feedback for various actions.</span></span> <span data-ttu-id="45ecc-130">Attualmente, i controller di movimento sono disponibili solo per gli scenari di realtà mista di Windows (WMR).</span><span class="sxs-lookup"><span data-stu-id="45ecc-130">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="45ecc-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="45ecc-131">See also</span></span>
* [<span data-ttu-id="45ecc-132">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="45ecc-132">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="45ecc-133">Puntamento con la testa e attesa</span><span class="sxs-lookup"><span data-stu-id="45ecc-133">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="45ecc-134">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="45ecc-134">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="45ecc-135">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="45ecc-135">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="45ecc-136">Mani libere</span><span class="sxs-lookup"><span data-stu-id="45ecc-136">Hands-free</span></span>](hands-free.md)
