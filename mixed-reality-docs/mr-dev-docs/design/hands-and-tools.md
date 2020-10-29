---
title: Mani e controller del movimento
description: Informazioni sui modelli di interazione di hands and Motion Controllers, che possono rimuovere il limite tra il virtuale e il fisico.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Realtà mista, mani, controller di movimento, interazione, progettazione
ms.openlocfilehash: 8b2ed6127708204d0c4a537c56b2225ff26e0d0f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686892"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="a1abd-104">Mani e controller del movimento</span><span class="sxs-lookup"><span data-stu-id="a1abd-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="a1abd-105">Scenari</span><span class="sxs-lookup"><span data-stu-id="a1abd-105">Scenarios</span></span>
<span data-ttu-id="a1abd-106">Se si sceglie di adottare questo modello di interazione dopo aver letto la [Panoramica sull'interazione](interaction-fundamentals.md), significa che si sta sviluppando un'applicazione che richiede agli utenti di usare due mani per interagire con il mondo olografico.</span><span class="sxs-lookup"><span data-stu-id="a1abd-106">If you choose to adopt this interaction model after reading the [interaction overview](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="a1abd-107">L'applicazione è in grado di raggiungere l'obiettivo di rimuovere il limite tra virtuale e fisico.</span><span class="sxs-lookup"><span data-stu-id="a1abd-107">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="a1abd-108">Alcuni scenari specifici potrebbero essere:</span><span class="sxs-lookup"><span data-stu-id="a1abd-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="a1abd-109">Fornire agli Information Worker schermate virtuali 2D con inviti dell'interfaccia utente per visualizzare e controllare il contenuto</span><span class="sxs-lookup"><span data-stu-id="a1abd-109">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="a1abd-110">Esercitazione e guide per i ruoli di lavoro di prima linea per le linee di assemblaggio Factory</span><span class="sxs-lookup"><span data-stu-id="a1abd-110">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="a1abd-111">Sviluppare strumenti professionali per l'assistenza e la formazione per professionisti medici</span><span class="sxs-lookup"><span data-stu-id="a1abd-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="a1abd-112">Usare oggetti virtuali 3D per decorare il mondo reale o creare un secondo mondo</span><span class="sxs-lookup"><span data-stu-id="a1abd-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="a1abd-113">Creare servizi e giochi basati sulla posizione usando il mondo reale come sfondo</span><span class="sxs-lookup"><span data-stu-id="a1abd-113">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="a1abd-114">Modalità di controllo delle mani e del movimento</span><span class="sxs-lookup"><span data-stu-id="a1abd-114">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="a1abd-115">[![Manipolazione diretta con le mani](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="a1abd-115">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsbr"></a>[<span data-ttu-id="a1abd-116">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="a1abd-116">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="a1abd-117">Si tratta di una modalità sfruttando la potenza di Hands, con cui gli utenti sono in grado di toccare e modificare direttamente gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="a1abd-117">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="a1abd-118">Sfruttando le esperienze quotidiane e fornendo affordances visivi appropriati, gli utenti possono usare lo stesso modo per modificare gli oggetti reali per interagire con quelli virtuali.</span><span class="sxs-lookup"><span data-stu-id="a1abd-118">By leveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a1abd-119">[![Puntamento e commit con le mani](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="a1abd-119">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handsbr"></a>[<span data-ttu-id="a1abd-120">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="a1abd-120">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="a1abd-121">Questa modalità consente agli utenti di interagire con gli ologrammi a distanza.</span><span class="sxs-lookup"><span data-stu-id="a1abd-121">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="a1abd-122">Consente agli utenti di sfruttare al meglio i dintorni.</span><span class="sxs-lookup"><span data-stu-id="a1abd-122">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="a1abd-123">Gli utenti possono posizionare gli ologrammi ovunque e continuare ad accedervi da qualsiasi distanza.</span><span class="sxs-lookup"><span data-stu-id="a1abd-123">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="a1abd-124">I modelli e i movimenti mentali per controllare e modificare gli ologrammi 2D e 3D sono sincronizzati con quelli di manipolazione diretta.</span><span class="sxs-lookup"><span data-stu-id="a1abd-124">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a1abd-125">[![Controller del movimento](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="a1abd-125">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersbr"></a>[<span data-ttu-id="a1abd-126">Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="a1abd-126">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="a1abd-127">I controller di movimento sono strumenti che estendono le funzionalità fisiche dell'utente fornendo interazioni precise in un'ampia gamma di distanze durante l'uso di una o entrambe le mani.</span><span class="sxs-lookup"><span data-stu-id="a1abd-127">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="a1abd-128">Questi accessori hardware forniscono collegamenti a molte interazioni di uso comune e forniscono surefooted e commenti tattili per diverse azioni.</span><span class="sxs-lookup"><span data-stu-id="a1abd-128">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="a1abd-129">Attualmente, i controller di movimento sono disponibili solo per gli scenari di realtà mista di Windows (WMR).</span><span class="sxs-lookup"><span data-stu-id="a1abd-129">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="a1abd-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a1abd-130">See also</span></span>
* [<span data-ttu-id="a1abd-131">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="a1abd-131">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="a1abd-132">Puntamento con la testa e attesa</span><span class="sxs-lookup"><span data-stu-id="a1abd-132">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="a1abd-133">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="a1abd-133">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a1abd-134">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="a1abd-134">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="a1abd-135">Mani libere</span><span class="sxs-lookup"><span data-stu-id="a1abd-135">Hands-free</span></span>](hands-free.md)
