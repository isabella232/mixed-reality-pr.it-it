---
title: Visualizzazione dello stato
description: Informazioni sul modo in cui i controlli di stato forniscono all'utente feedback sull'esecuzione di un'operazione di lunga durata nelle app per realtà mista.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, controlli, interfaccia utente, UX, indicatore di stato, auricolare realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, HoloLens, MRTK, Toolkit realtà mista
ms.openlocfilehash: 489f4bd9fea31126f936673db7acafeab27d9cd9
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009461"
---
# <a name="progress-indicator"></a><span data-ttu-id="56fd7-104">Indicatore di stato</span><span class="sxs-lookup"><span data-stu-id="56fd7-104">Progress indicator</span></span>

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="56fd7-105">Un controllo progress fornisce il feedback che è in corso un'operazione a esecuzione prolungata.</span><span class="sxs-lookup"><span data-stu-id="56fd7-105">A progress control provides feedback that a long-running operation is underway.</span></span> <span data-ttu-id="56fd7-106">Quando un indicatore di stato è visibile, gli utenti possono visualizzare il tempo di attesa e non possono interagire con l'app.</span><span class="sxs-lookup"><span data-stu-id="56fd7-106">When a progress indicator is visible, users can see the wait time and can't interact with the app.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="56fd7-107">Tipi di stato</span><span class="sxs-lookup"><span data-stu-id="56fd7-107">Types of progress</span></span>

<span data-ttu-id="56fd7-108">È importante fornire le informazioni sull'utente su ciò che accade.</span><span class="sxs-lookup"><span data-stu-id="56fd7-108">It's important to provide the user information about what is happening.</span></span> <span data-ttu-id="56fd7-109">In realtà mista, gli utenti possono essere facilmente distratti dall'ambiente fisico o dagli oggetti se l'app non ha un feedback visivo valido.</span><span class="sxs-lookup"><span data-stu-id="56fd7-109">In mixed reality, users can be easily distracted by the physical environment or objects if your app doesn't have good visual feedback.</span></span> <span data-ttu-id="56fd7-110">Per le situazioni in cui sono necessari alcuni secondi, ad esempio quando i dati vengono caricati o una scena viene aggiornata, è consigliabile mostrare un indicatore visivo.</span><span class="sxs-lookup"><span data-stu-id="56fd7-110">For situations that take a few seconds, like when data is loading or a scene is updating, it's a good idea to show a visual indicator.</span></span> <span data-ttu-id="56fd7-111">Sono disponibili due opzioni per indicare all'utente che è in corso un'operazione, ovvero un indicatore di **stato** o un **anello di avanzamento**.</span><span class="sxs-lookup"><span data-stu-id="56fd7-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="56fd7-112">Barra di stato</span><span class="sxs-lookup"><span data-stu-id="56fd7-112">Progress bar</span></span><br>
        <span data-ttu-id="56fd7-113">Un indicatore di stato Mostra la percentuale di completamento di un'attività.</span><span class="sxs-lookup"><span data-stu-id="56fd7-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="56fd7-114">Deve essere usato durante un'operazione la cui durata è nota (determinata), ma lo stato di avanzamento non dovrebbe bloccare l'interazione dell'utente con l'app.</span><span class="sxs-lookup"><span data-stu-id="56fd7-114">It should be used during an operation whose duration is known (determinate), but its progress shouldn't block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="56fd7-115">*Image: esempio di indicatore di stato in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="56fd7-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="56fd7-116">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="56fd7-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="56fd7-117">![Esempio di indicatore di stato in HoloLens](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="56fd7-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="56fd7-118">Anello di stato</span><span class="sxs-lookup"><span data-stu-id="56fd7-118">Progress ring</span></span><br>
        <span data-ttu-id="56fd7-119">Un anello di avanzamento ha uno stato indeterminato e deve essere usato quando l'interazione dell'utente viene bloccata fino al completamento dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="56fd7-119">A Progress ring only has an indeterminate state, and should be used when user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="56fd7-120">*Immagine: esempio di anello di stato in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="56fd7-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="56fd7-121">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="56fd7-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="56fd7-122">![Esempio di anello di stato nel dispositivo HoloLens](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="56fd7-122">![Progress ring example on HoloLens device](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="56fd7-123">Stato di avanzamento con un oggetto personalizzato</span><span class="sxs-lookup"><span data-stu-id="56fd7-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="56fd7-124">È possibile aggiungere la personalità e l'identità del marchio dell'app personalizzando il controllo dello stato di avanzamento con oggetti 2D/3D personalizzati.</span><span class="sxs-lookup"><span data-stu-id="56fd7-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="56fd7-125">*Immagine: esempio di avanzamento con mesh personalizzato in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="56fd7-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="56fd7-126">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="56fd7-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="56fd7-127">![Esempio di avanzamento con mesh personalizzato in HoloLens](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="56fd7-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="56fd7-128">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="56fd7-128">Best practices</span></span>
* <span data-ttu-id="56fd7-129">È strettamente correlato alla visualizzazione dello stato di avanzamento [, in quanto](billboarding-and-tag-along.md) l'utente può facilmente spostarne l'intestazione in uno spazio vuoto e perdere il contesto.</span><span class="sxs-lookup"><span data-stu-id="56fd7-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="56fd7-130">È possibile che l'app si trovi in modo anomalo se l'utente non è in grado di visualizzare alcun elemento.</span><span class="sxs-lookup"><span data-stu-id="56fd7-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="56fd7-131">Il tabellone e i tag-along sono incorporati nella prefabbrica di avanzamento.</span><span class="sxs-lookup"><span data-stu-id="56fd7-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="56fd7-132">È sempre opportuno fornire informazioni sullo stato relative a ciò che accade all'utente.</span><span class="sxs-lookup"><span data-stu-id="56fd7-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="56fd7-133">Il prefabbricato di avanzamento fornisce vari stili visivi, tra cui lo stato di avanzamento del tipo di anello standard di Windows.</span><span class="sxs-lookup"><span data-stu-id="56fd7-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="56fd7-134">È anche possibile usare una mesh personalizzata con un'animazione se si vuole che lo stile dello stato di avanzamento sia allineato al marchio dell'app.</span><span class="sxs-lookup"><span data-stu-id="56fd7-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="56fd7-135">Indicatore di stato in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="56fd7-135">Progress indicator in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="56fd7-136">MRTK-prefabbricati indicatore di stato</span><span class="sxs-lookup"><span data-stu-id="56fd7-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="56fd7-137">MRTK-servizio di transizione della scena</span><span class="sxs-lookup"><span data-stu-id="56fd7-137">MRTK - Scene transition service</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="56fd7-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="56fd7-138">See also</span></span>

* [<span data-ttu-id="56fd7-139">Cursori</span><span class="sxs-lookup"><span data-stu-id="56fd7-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="56fd7-140">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="56fd7-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="56fd7-141">Button</span><span class="sxs-lookup"><span data-stu-id="56fd7-141">Button</span></span>](button.md)
* [<span data-ttu-id="56fd7-142">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="56fd7-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="56fd7-143">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="56fd7-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="56fd7-144">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="56fd7-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="56fd7-145">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="56fd7-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="56fd7-146">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="56fd7-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="56fd7-147">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="56fd7-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="56fd7-148">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="56fd7-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="56fd7-149">Tastiera</span><span class="sxs-lookup"><span data-stu-id="56fd7-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="56fd7-150">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="56fd7-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="56fd7-151">Slate</span><span class="sxs-lookup"><span data-stu-id="56fd7-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="56fd7-152">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="56fd7-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="56fd7-153">Shader</span><span class="sxs-lookup"><span data-stu-id="56fd7-153">Shader</span></span>](shader.md)
* [<span data-ttu-id="56fd7-154">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="56fd7-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="56fd7-155">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="56fd7-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="56fd7-156">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="56fd7-156">Surface magnetism</span></span>](surface-magnetism.md)
