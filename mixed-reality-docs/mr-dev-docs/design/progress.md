---
title: Visualizzazione dello stato
description: Informazioni su come i controlli di stato forniscono un feedback all'utente che è in corso un'operazione a esecuzione lunga nelle app di realtà mista.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, progettazione, controlli, interfaccia utente, ux, indicatore di stato, visore di realtà mista, visore windows di realtà mista, visore di realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 01f032efb887ecfc6f8d66683fb954cd0574a4f3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600550"
---
# <a name="progress-indicator"></a><span data-ttu-id="ec32a-104">Indicatore di stato</span><span class="sxs-lookup"><span data-stu-id="ec32a-104">Progress indicator</span></span>

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="ec32a-105">Un controllo di stato fornisce il feedback che un'operazione a esecuzione lunga è in corso.</span><span class="sxs-lookup"><span data-stu-id="ec32a-105">A progress control provides feedback that a long-running operation is underway.</span></span> <span data-ttu-id="ec32a-106">Quando un indicatore di stato è visibile, gli utenti possono visualizzare il tempo di attesa e non possono interagire con l'app.</span><span class="sxs-lookup"><span data-stu-id="ec32a-106">When a progress indicator is visible, users can see the wait time and can't interact with the app.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="ec32a-107">Tipi di stato</span><span class="sxs-lookup"><span data-stu-id="ec32a-107">Types of progress</span></span>

<span data-ttu-id="ec32a-108">È importante fornire all'utente informazioni su ciò che accade.</span><span class="sxs-lookup"><span data-stu-id="ec32a-108">It's important to provide the user information about what is happening.</span></span> <span data-ttu-id="ec32a-109">In realtà mista, gli utenti possono essere facilmente distratti dall'ambiente fisico o dagli oggetti se l'app non ha un buon feedback visivo.</span><span class="sxs-lookup"><span data-stu-id="ec32a-109">In mixed reality, users can be easily distracted by the physical environment or objects if your app doesn't have good visual feedback.</span></span> <span data-ttu-id="ec32a-110">In situazioni che possono richiedere alcuni secondi, ad esempio durante il caricamento dei dati o l'aggiornamento di una scena, è buona idea visualizzare un indicatore visivo.</span><span class="sxs-lookup"><span data-stu-id="ec32a-110">For situations that take a few seconds, like when data is loading or a scene is updating, it's a good idea to show a visual indicator.</span></span> <span data-ttu-id="ec32a-111">Sono disponibili due opzioni per mostrare all'utente che è in corso un'operazione: un indicatore **di** stato o un **anello di stato**.</span><span class="sxs-lookup"><span data-stu-id="ec32a-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="ec32a-112">Barra di stato</span><span class="sxs-lookup"><span data-stu-id="ec32a-112">Progress bar</span></span><br>
        <span data-ttu-id="ec32a-113">Un indicatore di stato mostra la percentuale di completamento di un'attività.</span><span class="sxs-lookup"><span data-stu-id="ec32a-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="ec32a-114">Deve essere usato durante un'operazione la cui durata è nota (determinata), ma lo stato di avanzamento non deve bloccare l'interazione dell'utente con l'app.</span><span class="sxs-lookup"><span data-stu-id="ec32a-114">It should be used during an operation whose duration is known (determinate), but its progress shouldn't block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="ec32a-115">*Immagine: Esempio di indicatore di stato in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="ec32a-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="ec32a-116">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="ec32a-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="ec32a-117">![Esempio di indicatore di stato in HoloLens](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="ec32a-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="ec32a-118">Anello di stato</span><span class="sxs-lookup"><span data-stu-id="ec32a-118">Progress ring</span></span><br>
        <span data-ttu-id="ec32a-119">Un anello Di stato ha solo uno stato indeterminato e deve essere usato quando l'interazione dell'utente viene bloccata fino al completamento dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="ec32a-119">A Progress ring only has an indeterminate state, and should be used when user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="ec32a-120">*Immagine: Esempio di anello di stato in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="ec32a-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="ec32a-121">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="ec32a-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="ec32a-122">![Esempio di anello di stato nel dispositivo HoloLens](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="ec32a-122">![Progress ring example on HoloLens device](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="ec32a-123">Avanzamento con un oggetto personalizzato</span><span class="sxs-lookup"><span data-stu-id="ec32a-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="ec32a-124">È possibile aggiungere alla personalità e all'identità del marchio dell'app personalizzando il controllo Stato con i propri oggetti 2D/3D personalizzati.</span><span class="sxs-lookup"><span data-stu-id="ec32a-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="ec32a-125">*Immagine: Stato dell'esempio di mesh personalizzata in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="ec32a-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="ec32a-126">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="ec32a-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="ec32a-127">![Avanzamento con l'esempio di mesh personalizzata in HoloLens](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="ec32a-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="ec32a-128">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="ec32a-128">Best practices</span></span>

* <span data-ttu-id="ec32a-129">Coppia stretta di [manifesti o tag-along](billboarding-and-tag-along.md) per la visualizzazione di Progress poiché l'utente può spostare facilmente la testa nello spazio vuoto e perdere il contesto.</span><span class="sxs-lookup"><span data-stu-id="ec32a-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="ec32a-130">L'app potrebbe sembrare che si sia verificata in modo anomalo se l'utente non riesce a visualizzare alcun elemento.</span><span class="sxs-lookup"><span data-stu-id="ec32a-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="ec32a-131">I tag e i tag sono incorporati nel prefab Stato di avanzamento.</span><span class="sxs-lookup"><span data-stu-id="ec32a-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="ec32a-132">È sempre bene fornire informazioni sullo stato di ciò che accade all'utente.</span><span class="sxs-lookup"><span data-stu-id="ec32a-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="ec32a-133">Il prefab Stato fornisce vari stili di visualizzazione, tra cui lo stato di avanzamento del tipo di anello standard di Windows per fornire lo stato.</span><span class="sxs-lookup"><span data-stu-id="ec32a-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="ec32a-134">È anche possibile usare una mesh personalizzata con un'animazione se si vuole che lo stile dello stato di avanzamento sia allineato al marchio dell'app.</span><span class="sxs-lookup"><span data-stu-id="ec32a-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="ec32a-135">Indicatore di stato in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="ec32a-135">Progress indicator in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="ec32a-136">MRTK - Prefab indicatore di stato</span><span class="sxs-lookup"><span data-stu-id="ec32a-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="ec32a-137">MRTK - Servizio di transizione della scena</span><span class="sxs-lookup"><span data-stu-id="ec32a-137">MRTK - Scene transition service</span></span>](/windows/mixed-reality/mrtk-unity/features/extensions/scene-transition-service)


<br>

---

## <a name="see-also"></a><span data-ttu-id="ec32a-138">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="ec32a-138">See also</span></span>

* [<span data-ttu-id="ec32a-139">Cursori</span><span class="sxs-lookup"><span data-stu-id="ec32a-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="ec32a-140">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="ec32a-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="ec32a-141">Button</span><span class="sxs-lookup"><span data-stu-id="ec32a-141">Button</span></span>](button.md)
* [<span data-ttu-id="ec32a-142">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="ec32a-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="ec32a-143">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="ec32a-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="ec32a-144">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="ec32a-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="ec32a-145">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="ec32a-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="ec32a-146">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="ec32a-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="ec32a-147">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="ec32a-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="ec32a-148">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="ec32a-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="ec32a-149">Tastiera</span><span class="sxs-lookup"><span data-stu-id="ec32a-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="ec32a-150">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="ec32a-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="ec32a-151">Slate</span><span class="sxs-lookup"><span data-stu-id="ec32a-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="ec32a-152">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="ec32a-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="ec32a-153">Shader</span><span class="sxs-lookup"><span data-stu-id="ec32a-153">Shader</span></span>](shader.md)
* [<span data-ttu-id="ec32a-154">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="ec32a-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="ec32a-155">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="ec32a-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="ec32a-156">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="ec32a-156">Surface magnetism</span></span>](surface-magnetism.md)