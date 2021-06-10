---
title: Coach mano
description: Informazioni su come vengono attivate le mani 3D usando il pullman quando il sistema non rileva le mani dell'utente per assisterle.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, progettazione, hand coach, visore vr immersivo, MRTK, mani, mani di supporto, visore per realtà mista, visore windows mixed reality, visore di realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 0fe0d87e26d06838c0d1b7935573d9bd8ce258ee
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600430"
---
# <a name="hand-coach"></a><span data-ttu-id="439ec-104">Coach mano</span><span class="sxs-lookup"><span data-stu-id="439ec-104">Hand coach</span></span>

![Esempio: Hand coach](images/HandCoach/MRTK_handCoach.jpg)<br>

<span data-ttu-id="439ec-106">Il pullman attiva le mani modellate 3D quando il sistema non rileva le mani dell'utente.</span><span class="sxs-lookup"><span data-stu-id="439ec-106">Hand coach triggers 3D modeled hands when the system doesn't detect the user’s hands.</span></span> <span data-ttu-id="439ec-107">Questa funzionalità è un componente di "insegnamento" che aiuta a guidare l'utente quando il movimento non è stato insegnato.</span><span class="sxs-lookup"><span data-stu-id="439ec-107">This feature is a “teaching” component that helps guide the user when the gesture hasn't been taught.</span></span> <span data-ttu-id="439ec-108">Se gli utenti non hanno eseguito il movimento specificato per un periodo, le mani scorreranno con un ritardo.</span><span class="sxs-lookup"><span data-stu-id="439ec-108">If users haven't done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="439ec-109">Il hand coach può essere usato per rappresentare la pressione di un pulsante o la selezione di un ologramma.</span><span class="sxs-lookup"><span data-stu-id="439ec-109">The Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>  

## <a name="hand-coach-provided"></a><span data-ttu-id="439ec-110">Hand coach fornito</span><span class="sxs-lookup"><span data-stu-id="439ec-110">Hand coach provided</span></span>

<span data-ttu-id="439ec-111">Il modello di interazione corrente rappresenta un'ampia gamma di controlli movimento, ad esempio scorrimento, selezione estrema e tocco vicino.</span><span class="sxs-lookup"><span data-stu-id="439ec-111">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="439ec-112">Di seguito è riportato un elenco completo dei movimenti della mano esistenti disponibili in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK:</a></span><span class="sxs-lookup"><span data-stu-id="439ec-112">Below is a full list of existing hand gestures provided in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="439ec-113">![Esempio di near select](images/HandCoach/NearSelect.gif)</span><span class="sxs-lookup"><span data-stu-id="439ec-113">![Example of Near Select](images/HandCoach/NearSelect.gif)</span></span><br>
       <span data-ttu-id="439ec-114">**Esempio di Near Select - Usato per illustrare come selezionare pulsanti o chiudere oggetti interagiscibili**</span><span class="sxs-lookup"><span data-stu-id="439ec-114">**Example of Near Select - Used show how to select buttons or close interactable objects**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="439ec-115">![Esempio di Air Tap](images/HandCoach/AirTap.gif)</span><span class="sxs-lookup"><span data-stu-id="439ec-115">![Example of Air Tap](images/HandCoach/AirTap.gif)</span></span><br>
        <span data-ttu-id="439ec-116">**Esempio di Air Tap: usato per mostrare come selezionare oggetti che si sono allontanati**</span><span class="sxs-lookup"><span data-stu-id="439ec-116">**Example of Air Tap - Used to show how to select objects that are far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="439ec-117">![Esempio di spostamento](images/HandCoach/Move.gif)</span><span class="sxs-lookup"><span data-stu-id="439ec-117">![Example of Move](images/HandCoach/Move.gif)</span></span><br>
       <span data-ttu-id="439ec-118">**Esempio di spostamento di un oggetto nello spazio Usato per mostrare come spostare un ologramma nello spazio**</span><span class="sxs-lookup"><span data-stu-id="439ec-118">**Example of Moving an object in space-Used to show how to move a hologram in space**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="439ec-119">![Esempio di rotazione](images/HandCoach/Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="439ec-119">![Example of Rotate](images/HandCoach/Rotate.gif)</span></span><br>
       <span data-ttu-id="439ec-120">**Esempio di Rotate-Used per mostrare come ruotare ologrammi o oggetti**</span><span class="sxs-lookup"><span data-stu-id="439ec-120">**Example of Rotate-Used to show how to rotate holograms or objects**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="439ec-121">![Esempio di scalabilità](images/HandCoach/Scale.gif)</span><span class="sxs-lookup"><span data-stu-id="439ec-121">![Example of Scale](images/HandCoach/Scale.gif)</span></span><br>
       <span data-ttu-id="439ec-122">**Esempio di Scala: usato per illustrare come modificare gli ologrammi in modo che siano più grandi o più piccoli**</span><span class="sxs-lookup"><span data-stu-id="439ec-122">**Example of Scale- Used to show how to manipulate holograms to be bigger or smaller**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="439ec-123">![Esempio di Palm Up](images/HandCoach/PalmUp.gif)</span><span class="sxs-lookup"><span data-stu-id="439ec-123">![Example of Palm Up](images/HandCoach/PalmUp.gif)</span></span><br>
        <span data-ttu-id="439ec-124">**Esempio di Palm up - Uso consigliato per visualizzare i menu della mano**</span><span class="sxs-lookup"><span data-stu-id="439ec-124">**Example of Palm up – Suggested use, to bring up hand menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="439ec-125">![Esempio di HandFlip](images/HandCoach/HandFlip.gif)</span><span class="sxs-lookup"><span data-stu-id="439ec-125">![Example of HandFlip](images/HandCoach/HandFlip.gif)</span></span><br>
       <span data-ttu-id="439ec-126">**Exmaple of Hand Flip : un altro modo per visualizzare i menu a mano**</span><span class="sxs-lookup"><span data-stu-id="439ec-126">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="439ec-127">![Esempio di scorrimento](images/HandCoach/Scoll.gif)</span><span class="sxs-lookup"><span data-stu-id="439ec-127">![Example of Scroll](images/HandCoach/Scoll.gif)</span></span><br>
       <span data-ttu-id="439ec-128">**Esempio di scorrimento: usato per scorrere un elenco o un documento lungo**</span><span class="sxs-lookup"><span data-stu-id="439ec-128">**Example of Scroll – Used for scrolling a list or a long document**</span></span><br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a><span data-ttu-id="439ec-129">Concetti relativi alla progettazione</span><span class="sxs-lookup"><span data-stu-id="439ec-129">Design concepts</span></span>

<span data-ttu-id="439ec-130">Per Hololens2, sono state progettate interazioni con la mano in base a movimenti istintiva e naturali della mano.</span><span class="sxs-lookup"><span data-stu-id="439ec-130">For Hololens2, we designed out hand interactions based on instinctual and natural hand gestures.</span></span> <span data-ttu-id="439ec-131">Si ritiene che siano intuitivi per la maggior parte degli utenti, quindi non sono stati creati momenti dedicati di apprendimento dei movimenti.</span><span class="sxs-lookup"><span data-stu-id="439ec-131">We believe these to be intuitive to most users, so we didn't create dedicated gesture learning moments.</span></span> <span data-ttu-id="439ec-132">È stato invece creato il hand coach per aiutare gli utenti a conoscere questi movimenti se si bloccano o non hanno familiarità con le interazioni con ologrammi.</span><span class="sxs-lookup"><span data-stu-id="439ec-132">Instead, we created the hand coach to help users learn about these gestures if they get stuck or are unfamiliar with hologram interactions.</span></span> <span data-ttu-id="439ec-133">Senza un momento di apprendimento, si è ritenuto che mostrare agli utenti come eseguire un'azione dimostrando che sarebbe stata l'opzione migliore.</span><span class="sxs-lookup"><span data-stu-id="439ec-133">Without a learning moment, we felt that showing users how to perform an action by demonstrating it would be the best option.</span></span> <span data-ttu-id="439ec-134">È stato rilevato che gli utenti erano in grado di capire il movimento, ma che erano necessarie alcune indicazioni.</span><span class="sxs-lookup"><span data-stu-id="439ec-134">We found that users were able to figure out the gesture but needed a little guidance.</span></span> <span data-ttu-id="439ec-135">Se si rileva che un utente non interagisce con un oggetto per un periodo di tempo, viene attivato un hand coach che mostra la corretta posizione di mano e dito.</span><span class="sxs-lookup"><span data-stu-id="439ec-135">If we detect a user doesn't interact with an object for a period, a Hand coach would be triggered demonstrating the correct hand and finger placement.</span></span> 

### <a name="intuitive"></a><span data-ttu-id="439ec-136">intuitivo</span><span class="sxs-lookup"><span data-stu-id="439ec-136">Intuitive</span></span>

<span data-ttu-id="439ec-137">Quando si animano le mani, dovrebbe essere ovvio e non deve causare confusione.</span><span class="sxs-lookup"><span data-stu-id="439ec-137">When animating hands, it should be obvious and shouldn't cause any confusion.</span></span> <span data-ttu-id="439ec-138">L'animazione manuale è una rappresentazione del movimento che si sta tentando di chiedere all'utente di comprendere.</span><span class="sxs-lookup"><span data-stu-id="439ec-138">The hand animation is a representation of the gesture you're trying to prompt the user to understand.</span></span> 

<span data-ttu-id="439ec-139">Ad esempio, se si vuole che un utente premo un pulsante, viene attivata una mano che preme un pulsante.</span><span class="sxs-lookup"><span data-stu-id="439ec-139">For example, if you wish a user to press a button, a hand pressing a button would be triggered.</span></span>

<span data-ttu-id="439ec-140">![Esempio: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span><span class="sxs-lookup"><span data-stu-id="439ec-140">![Example: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span></span><br>
<span data-ttu-id="439ec-141">*Hand Coach che illustra near tapping a gem*</span><span class="sxs-lookup"><span data-stu-id="439ec-141">*Hand Coach demonstrating Near Tapping a Gem*</span></span>  

### <a name="hand-scale"></a><span data-ttu-id="439ec-142">Scalabilità manuale</span><span class="sxs-lookup"><span data-stu-id="439ec-142">Hand scale</span></span>

<span data-ttu-id="439ec-143">Sono state testate varie dimensioni della mano con i menu dell'interfaccia utente e si è ritenuto che se le mani fossero vere per le dimensioni, questo ha dato un'impressione minacciante.</span><span class="sxs-lookup"><span data-stu-id="439ec-143">We tested various hand sizes with the UI menus and felt that if the hands were true to size, it gave a menacing feeling.</span></span> <span data-ttu-id="439ec-144">Se erano troppo piccoli, era difficile vedere e comprendere il movimento.</span><span class="sxs-lookup"><span data-stu-id="439ec-144">If they were too small, it was hard to see and understand the gesture.</span></span> 

<span data-ttu-id="439ec-145">**Voice over e hands**</span><span class="sxs-lookup"><span data-stu-id="439ec-145">**Voice over and hands**</span></span>

<span data-ttu-id="439ec-146">Non aspettarsi che gli utenti possano ascoltare un set di istruzioni tramite voice over e guardare istruzioni diverse tramite Hand coach.</span><span class="sxs-lookup"><span data-stu-id="439ec-146">Don’t expect users can listen to one set of instructions via voice over and watch different instructions via Hand coach.</span></span> <span data-ttu-id="439ec-147">Sequenziare le istruzioni per aiutare gli utenti a concentrarsi rispetto alla concorrenza per la loro attenzione per ridurre il sovraccarico sensoriale.</span><span class="sxs-lookup"><span data-stu-id="439ec-147">Sequence your instructions to help users focus versus compete for their attention to reduce sensory overload.</span></span>


## <a name="can-i-create-my-own"></a><span data-ttu-id="439ec-148">È possibile crearne uno personalizzato?</span><span class="sxs-lookup"><span data-stu-id="439ec-148">Can I create my own?</span></span>

<span data-ttu-id="439ec-149">Sì.</span><span class="sxs-lookup"><span data-stu-id="439ec-149">Yes!</span></span> <span data-ttu-id="439ec-150">Ti invitiamo a creare un movimento unico per il tuo gioco e a contribuire alla community.</span><span class="sxs-lookup"><span data-stu-id="439ec-150">We encourage you to create your own unique gesture for your game and contribute back to the community!</span></span>
<span data-ttu-id="439ec-151">È stato fornito un file Maya di una mano <a href="files/HandCoach_MRTK.zip">ritardata</a> che può essere usata per l'app, che può essere scaricato qui: Scaricare HandCoach_MRTK.zip</span><span class="sxs-lookup"><span data-stu-id="439ec-151">We've provided a Maya file of a Rigged hand that can be used for your app, which can be downloaded here: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip </a></span></span>

<span data-ttu-id="439ec-152">![Esempio di Mani animate in Maya](images/HandCoach/MayaSelect_Gif.gif)</span><span class="sxs-lookup"><span data-stu-id="439ec-152">![Example of Animated Hands in Maya](images/HandCoach/MayaSelect_Gif.gif)</span></span><br>
<span data-ttu-id="439ec-153">*Esempio di hand poking animato di una casella in Maya*</span><span class="sxs-lookup"><span data-stu-id="439ec-153">*Example of animated Hand Poking a box in Maya*</span></span>


<span data-ttu-id="439ec-154">**Strumento di creazione consigliato**</span><span class="sxs-lookup"><span data-stu-id="439ec-154">**Recommended authoring tool**</span></span>

<span data-ttu-id="439ec-155">Tra gli artisti 3D, molti scelgono di usare Maya di Autodesk, che può usare [HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) per trasformare il modo in cui vengono creati gli asset.</span><span class="sxs-lookup"><span data-stu-id="439ec-155">Among 3D artists, many choose to use [Autodesk’s Maya, which can use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="439ec-156">Il file hands fornito è un file binario Maya, quindi è consigliabile usare Maya per animare ed esportare le mani.</span><span class="sxs-lookup"><span data-stu-id="439ec-156">The hands file provided is a Maya Binary File, so it's recommended to use Maya to animate and export the hands.</span></span> <span data-ttu-id="439ec-157">Se si preferisce usare un altro programma 3D, ecco <b>un . FBX:</b> <a href="files/HandCoachMRTK_FBX.zip"> scaricare HandCoachMRTK_FBX.zip </a> per creare la configurazione del controller.</span><span class="sxs-lookup"><span data-stu-id="439ec-157">If you prefer to use another 3D program, here's a <b>.FBX</b>: <a href="files/HandCoachMRTK_FBX.zip"> Download HandCoachMRTK_FBX.zip </a> to create your own controller setup.</span></span> 

<span data-ttu-id="439ec-158">Se si usa il file di mano maya scaricabile fornito, è consigliabile ridimensionare le mani in unity fino a 0,6.</span><span class="sxs-lookup"><span data-stu-id="439ec-158">If using the downloadable maya Hand File provided, it's suggested to scale down the hands in unity to 0.6.</span></span>

<span data-ttu-id="439ec-159">![Esempio: hand coach rig in Maya](images/HandCoach/MayaExample.png)</span><span class="sxs-lookup"><span data-stu-id="439ec-159">![Example: Hand coach rig in Maya](images/HandCoach/MayaExample.png)</span></span><br>
<span data-ttu-id="439ec-160">*Mani truccate*</span><span class="sxs-lookup"><span data-stu-id="439ec-160">*Rigged Hands*</span></span>

### <a name="technical-specs"></a><span data-ttu-id="439ec-161">Specifiche tecniche</span><span class="sxs-lookup"><span data-stu-id="439ec-161">Technical Specs</span></span>

*   <span data-ttu-id="439ec-162">Il file a due mani è disponibile in formato Maya Ascii</span><span class="sxs-lookup"><span data-stu-id="439ec-162">Two handed File is available in Maya Ascii format</span></span>
*    <span data-ttu-id="439ec-163">La mano destra e la mano sinistra sono disponibili in formato binario Maya</span><span class="sxs-lookup"><span data-stu-id="439ec-163">Right and Left Hand is available in Maya Binary format</span></span>
*   <span data-ttu-id="439ec-164">Impostare il file Maya su 24 FPS</span><span class="sxs-lookup"><span data-stu-id="439ec-164">Set your Maya file to 24 FPS</span></span>
*   <span data-ttu-id="439ec-165">All'interno del file sono presenti una mano sinistra e una destra, che possono essere usate per i movimenti a due mani o con una sola mano.</span><span class="sxs-lookup"><span data-stu-id="439ec-165">Within the file, there's a left and right hand, which can be used for two handed or single-handed gestures.</span></span> <span data-ttu-id="439ec-166">La mano destra sarà visibile solo per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="439ec-166">The right hand will only be visible by default.</span></span>
*   <span data-ttu-id="439ec-167">È consigliabile lasciare un buffer di circa 10 fotogrammi all'inizio e alla fine per le dissolvenze</span><span class="sxs-lookup"><span data-stu-id="439ec-167">It's suggested to leave a buffer of about 10 frames at the beginning and end for fades</span></span>
*   <span data-ttu-id="439ec-168">Se si anima un oggetto con una destinazione specificata, è consigliabile aggiungere un'animazione a una casella Predefinita o Null.</span><span class="sxs-lookup"><span data-stu-id="439ec-168">If animating an object with a specified target, its best practice to animate to a Default box or Null.</span></span>
*   <span data-ttu-id="439ec-169">Se la mano anima un oggetto fisico, ad esempio una casella, è consigliabile non animare la traduzione in Maya, ma attendere di animarla in Unity o nel codice.</span><span class="sxs-lookup"><span data-stu-id="439ec-169">If the hand is animating a physical object such as a box, its best practice to not animate the translation in Maya but wait to animate it in Unity or in Code.</span></span>
*   <span data-ttu-id="439ec-170">L'animazione visibile deve essere di 1,5 secondi per trasmettere tutte le informazioni significative</span><span class="sxs-lookup"><span data-stu-id="439ec-170">Visible Animation should be 1.5 secs for any meaningful information to be conveyed</span></span>
*   <span data-ttu-id="439ec-171">Quando si è soddisfatti dell'animazione:</span><span class="sxs-lookup"><span data-stu-id="439ec-171">When you feel satisfied with your animation:</span></span>
    *   <span data-ttu-id="439ec-172">Selezionare tutti i giunzioni e bake fotogrammi chiave</span><span class="sxs-lookup"><span data-stu-id="439ec-172">Select all joints and bake key frames</span></span>
    *   <span data-ttu-id="439ec-173">Eliminare i controller, selezionare le giunzioni e la mesh ed esportare come FBX</span><span class="sxs-lookup"><span data-stu-id="439ec-173">Delete the Controllers, Select the joints and mesh and export as an FBX</span></span>
    *  <span data-ttu-id="439ec-174">Se sono presenti più animazioni, è possibile usare l'esportatore di giochi incorporato di Maya: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span><span class="sxs-lookup"><span data-stu-id="439ec-174">If there are Multiple Animations, you can use Maya’s built-in Game Exporter: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span></span>

## <a name="exporting-from-maya"></a><span data-ttu-id="439ec-175">Esportazione da Maya</span><span class="sxs-lookup"><span data-stu-id="439ec-175">Exporting from Maya</span></span>

<span data-ttu-id="439ec-176">Dopo aver soddisfatto l'animazione</span><span class="sxs-lookup"><span data-stu-id="439ec-176">After you're satisfied with your animation</span></span>
* <span data-ttu-id="439ec-177">Seleziona tutti i giunzioni: selezionare > gerarchia</span><span class="sxs-lookup"><span data-stu-id="439ec-177">Select all joints: Select > Hierarchy</span></span>

     ![Esempio: Gerarchia nel menu](images/HandCoach/Hierarchy.png)<br>
* <span data-ttu-id="439ec-179">Preparare l'animazione: passare all'animazione > chiave > Bake Animation</span><span class="sxs-lookup"><span data-stu-id="439ec-179">Bake out your animation: Switch to Animation > Key > Bake Animation</span></span>

     ![Esempio: Bake Animation Menu Location](images/HandCoach/BakeAnimation.png)<br>
* <span data-ttu-id="439ec-181">Eliminare il rig controller: outliner > MainR_Grp o MainL_Grp</span><span class="sxs-lookup"><span data-stu-id="439ec-181">Delete the Controller Rig: Outliner > MainR_Grp or MainL_Grp</span></span>

     ![Esempio: Posizione menu rig controller](images/HandCoach/ControllerRig.png)<br>

* <span data-ttu-id="439ec-183">Esporta come FBX: selezionare JNT + Mesh: Selezione > file (casella di opzione) > Esporta selezione</span><span class="sxs-lookup"><span data-stu-id="439ec-183">Export as FBX: Select JNT + Mesh: File > Export Selection (option box) > Export Selection</span></span>

     ![Esempio: Esportare la posizione del menu di selezione](images/HandCoach/OptionBox.png)<br>

     ![Esempio: Posizione menu](images/HandCoach/SelectionExport.png)<br>

     ![Esempio: Percorso del menu Opzioni di esportazione](images/HandCoach/FBXSelection.png)<br>


 <span data-ttu-id="439ec-187">Quando si esegue l'esportazione come FBX e si esegue l'importazione in Unity, ridimensionare le mani fino a 0,6.</span><span class="sxs-lookup"><span data-stu-id="439ec-187">When exporting as an FBX and brought into Unity, scale the hands down to 0.6.</span></span> <span data-ttu-id="439ec-188">È stato rilevato che si tratta di un equilibrio perfetto per la visualizzazione delle mani.</span><span class="sxs-lookup"><span data-stu-id="439ec-188">We found that this was perfect balance for displaying the hands.</span></span> 

<span data-ttu-id="439ec-189">![Esempio: Impostazioni di Unity](images/HandCoach/HandHintScale.png)</span><span class="sxs-lookup"><span data-stu-id="439ec-189">![Example: Unity Settings](images/HandCoach/HandHintScale.png)</span></span><br>
<span data-ttu-id="439ec-190">*Impostazioni unity per HandCoach_R prefab trovato in MRTK*</span><span class="sxs-lookup"><span data-stu-id="439ec-190">*Unity Settings for HandCoach_R prefab found in MRTK*</span></span>


## <a name="implementing-hands-into-your-unity-project"></a><span data-ttu-id="439ec-191">Implementazione di Hands nel progetto Unity</span><span class="sxs-lookup"><span data-stu-id="439ec-191">Implementing Hands into your Unity project</span></span>

### <a name="best-practices"></a><span data-ttu-id="439ec-192">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="439ec-192">Best practices</span></span>

* <span data-ttu-id="439ec-193">È consigliabile ridimensionare le mani in unity fino a 0,6</span><span class="sxs-lookup"><span data-stu-id="439ec-193">It's suggested to scale down the hands in unity to 0.6</span></span>
* <span data-ttu-id="439ec-194">Le mani devono essere riprodotte due volte e, se non sono completate, viene eseguito un ciclo continuo fino al completamento del movimento.</span><span class="sxs-lookup"><span data-stu-id="439ec-194">Hands should be played twice and if not completed then continuously looped until gesture is completed.</span></span> <span data-ttu-id="439ec-195">Le mani devono essere registrate due volte per assicurarsi che l'utente sia in grado di registrarsi e visualizzare il movimento.</span><span class="sxs-lookup"><span data-stu-id="439ec-195">The hands should be looped twice to ensure the user had time to register and see the gesture.</span></span> <span data-ttu-id="439ec-196">Le mani devono dissolvenza in entrata e in uscita tra i cicli.</span><span class="sxs-lookup"><span data-stu-id="439ec-196">The hands should fade in and out between loops.</span></span> 
 *  <span data-ttu-id="439ec-197">Se le mani dell'utente sono visibili dalle fotocamere HL2, ma gli utenti non stanno effettuando l'interazione necessaria, le mani verranno visualizzate dopo 10 secondi.</span><span class="sxs-lookup"><span data-stu-id="439ec-197">If user’s hands are visible by HL2 cameras but users aren't doing the interaction needed of them the hands will appear after 10 seconds.</span></span>
*   <span data-ttu-id="439ec-198">Se le mani dell'utente NON sono visibili dalle fotocamere HL2, le mani verranno visualizzate dopo 5 secondi.</span><span class="sxs-lookup"><span data-stu-id="439ec-198">If user’s hands are NOT visible by HL2 cameras, the hands will appear after 5 seconds.</span></span>  
*   <span data-ttu-id="439ec-199">Se le mani dell'utente vengono monitorate in modo visibile dalle fotocamere HL2 al centro dell'animazione, l'animazione verrà completata e dissolvenza in dissolvenza.</span><span class="sxs-lookup"><span data-stu-id="439ec-199">If user’s hands are visibly tracked by HL2 cameras in the middle of the animation, the animation will complete and fade out.</span></span>
*   <span data-ttu-id="439ec-200">Se si include voice over, è consigliabile che corrisponda al movimento della mano.</span><span class="sxs-lookup"><span data-stu-id="439ec-200">If you're including voice over, we suggest that it corresponds to the gesture of the hand.</span></span>
*   <span data-ttu-id="439ec-201">Se le mani sono state insegnate almeno una volta, ripetere il movimento solo se viene rilevato che l'utente è bloccato.</span><span class="sxs-lookup"><span data-stu-id="439ec-201">If you've taught the hands at least once, only repeat the gesture if it's detected that the user is stuck.</span></span>
*   <span data-ttu-id="439ec-202">Se posizioni specifiche del dito o della mano sono fondamentali, assicurarsi che gli utenti possano vedere chiaramente queste sfumature nell'animazione.</span><span class="sxs-lookup"><span data-stu-id="439ec-202">If specific finger/hand positions are critical, ensure users can clearly see these nuances in the animation.</span></span> <span data-ttu-id="439ec-203">Provare a angling le mani in modo che le parti più importanti siano chiaramente visibili.</span><span class="sxs-lookup"><span data-stu-id="439ec-203">Try angling the hands so the most important parts are clearly visible.</span></span> 
* <span data-ttu-id="439ec-204">Se si nota una distorsione sulle mani, è necessario passare alle impostazioni di Qualità di Unity per aumentare il numero di esche.</span><span class="sxs-lookup"><span data-stu-id="439ec-204">If you notice distortion on the hands, you need to go to Unity's Quality settings increase the number of bones.</span></span> 
 <span data-ttu-id="439ec-205">Passare a Modifica impostazioni > progetto di Unity > qualità > altri pesi > blend.</span><span class="sxs-lookup"><span data-stu-id="439ec-205">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="439ec-206">Assicurarsi che sia selezionata l'opzione "4 esche" per visualizzare Smooth Joints (Giunzioni smooth).</span><span class="sxs-lookup"><span data-stu-id="439ec-206">Make sure "4 bones" are selected to see Smooth Joints.</span></span>

   ![Esempio: finestra Impostazioni progetto](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a><span data-ttu-id="439ec-208">Da evitare</span><span class="sxs-lookup"><span data-stu-id="439ec-208">What to avoid</span></span>

* <span data-ttu-id="439ec-209">Ridimensionamento delle mani troppo grande</span><span class="sxs-lookup"><span data-stu-id="439ec-209">Scaling the Hands too large</span></span>
* <span data-ttu-id="439ec-210">posizionamento delle mani troppo vicino all'utente</span><span class="sxs-lookup"><span data-stu-id="439ec-210">placing the Hands too close to the user</span></span>
* <span data-ttu-id="439ec-211">Le mani devono essere insegnate una sola volta.</span><span class="sxs-lookup"><span data-stu-id="439ec-211">Hands should only be taught once.</span></span> <span data-ttu-id="439ec-212">L'over teaching può causare confusione e confusione</span><span class="sxs-lookup"><span data-stu-id="439ec-212">Over teaching can cause confusion and messiness</span></span>
* <span data-ttu-id="439ec-213">Per scaricarlo in Unity, scaricare la versione più recente di MRTK qui: https://github.com/microsoft/MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="439ec-213">Bringing it into Unity, download the latest MRTK  here: https://github.com/microsoft/MixedRealityToolkit-Unity</span></span>
  * <span data-ttu-id="439ec-214">Materiale: Teaching_Hand2</span><span class="sxs-lookup"><span data-stu-id="439ec-214">Material: Teaching_Hand2</span></span>
  * <span data-ttu-id="439ec-215">Script: fare riferimento alle linee guida di MRTK per <a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach"> il hand coach MRTK </a></span><span class="sxs-lookup"><span data-stu-id="439ec-215">Scripts: Refer to MRTK guidelines for <a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach"> MRTK hand coach </a></span></span>
  * <span data-ttu-id="439ec-216">Impostazione per progetto</span><span class="sxs-lookup"><span data-stu-id="439ec-216">Per- project setting</span></span>
    * <span data-ttu-id="439ec-217">Scena impostata su UWP: le istruzioni sono disponibili in [Configurare il progetto Unity](../develop/unity/Configure-Unity-Project.md) per Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="439ec-217">Scene set to UWP: Instruction can be found on the [Configure Unity Project](../develop/unity/Configure-Unity-Project.md) for Windows Mixed Reality</span></span>

## <a name="see-also"></a><span data-ttu-id="439ec-218">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="439ec-218">See also</span></span>

* [<span data-ttu-id="439ec-219">Nozioni fondamentali sull'interazione</span><span class="sxs-lookup"><span data-stu-id="439ec-219">Interaction-fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="439ec-220">Processo di creazione di asset</span><span class="sxs-lookup"><span data-stu-id="439ec-220">Asset Creation Process</span></span>](asset-creation-process.md)
* [<span data-ttu-id="439ec-221">Movimenti</span><span class="sxs-lookup"><span data-stu-id="439ec-221">Gestures</span></span>](./interaction-fundamentals.md)
* [<span data-ttu-id="439ec-222">Installare gli strumenti</span><span class="sxs-lookup"><span data-stu-id="439ec-222">Install the Tools</span></span>](../develop/install-the-tools.md)
* [<span data-ttu-id="439ec-223">Configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="439ec-223">Configure Unity Project</span></span>](../develop/unity/Configure-Unity-Project.md)
* [<span data-ttu-id="439ec-224">Panoramica dello sviluppo per Unity</span><span class="sxs-lookup"><span data-stu-id="439ec-224">Unity development overview</span></span>](../develop/unity/unity-development-overview.md)
* [<span data-ttu-id="439ec-225">MRTK 101</span><span class="sxs-lookup"><span data-stu-id="439ec-225">MRTK 101</span></span>](/windows/mixed-reality/mrtk-unity/)