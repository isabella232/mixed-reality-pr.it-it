---
title: ExperimentalFeatures
description: Documento relativo alle funzionalità sperimentali in MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: fdd426c0f994a72cd3914f37332600b4133eb0fb
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783003"
---
# <a name="experimental-features"></a><span data-ttu-id="c9b78-104">Funzionalità sperimentali</span><span class="sxs-lookup"><span data-stu-id="c9b78-104">Experimental features</span></span>

<span data-ttu-id="c9b78-105">Alcune funzionalità del team di MRTK sembrano avere molto valore iniziale anche se non sono stati completati i dettagli.</span><span class="sxs-lookup"><span data-stu-id="c9b78-105">Some features the MRTK team works on appear to have a lot of initial value even if we haven’t fully fleshed out the details.</span></span> <span data-ttu-id="c9b78-106">Per questi tipi di funzionalità, è necessario che la community ottenga la possibilità di vederle presto.</span><span class="sxs-lookup"><span data-stu-id="c9b78-106">For these types of features, we want the community to get a chance to see them early.</span></span> <span data-ttu-id="c9b78-107">Poiché si trovano all'inizio del ciclo, le etichette vengono etichettate come sperimentali per indicare che sono in continua evoluzione e soggette a modifiche nel tempo.</span><span class="sxs-lookup"><span data-stu-id="c9b78-107">Because they are early in the cycle, we label them as experimental to indicate that they are still evolving, and subject to change over time.</span></span>

## <a name="what-to-expect-from-an-experimental-feature"></a><span data-ttu-id="c9b78-108">Cosa aspettarsi da una funzionalità sperimentale</span><span class="sxs-lookup"><span data-stu-id="c9b78-108">What to expect from an experimental feature</span></span>

<span data-ttu-id="c9b78-109">Se un componente è contrassegnato come sperimentale, è possibile prevedere quanto segue:</span><span class="sxs-lookup"><span data-stu-id="c9b78-109">If a component is marked experimental you can expect the following:</span></span>

- <span data-ttu-id="c9b78-110">Una scena di esempio che illustra l'utilizzo, disponibile nella `MRTK/Examples/Experimental` sottocartella</span><span class="sxs-lookup"><span data-stu-id="c9b78-110">An example scene demonstrating usage, located under `MRTK/Examples/Experimental` sub-folder</span></span>
- <span data-ttu-id="c9b78-111">Le funzionalità sperimentali potrebbero non avere documenti.</span><span class="sxs-lookup"><span data-stu-id="c9b78-111">Experimental features may not have docs.</span></span>
- <span data-ttu-id="c9b78-112">Probabilmente non hanno test.</span><span class="sxs-lookup"><span data-stu-id="c9b78-112">They probably don't have tests.</span></span>
- <span data-ttu-id="c9b78-113">Le funzionalità sperimentali sono soggette a modifiche.</span><span class="sxs-lookup"><span data-stu-id="c9b78-113">Experimental features are subject to change.</span></span>

## <a name="experimental-feature-guidelines"></a><span data-ttu-id="c9b78-114">Linee guida sulle funzionalità sperimentali</span><span class="sxs-lookup"><span data-stu-id="c9b78-114">Experimental feature guidelines</span></span>

### <a name="experimental-code-should-live-in-a-separate-folder"></a><span data-ttu-id="c9b78-115">Il codice sperimentale dovrebbe risiedere in una cartella separata</span><span class="sxs-lookup"><span data-stu-id="c9b78-115">Experimental code should live in a separate folder</span></span>

<span data-ttu-id="c9b78-116">Il codice sperimentale dovrebbe essere inserito in una cartella sperimentale di primo livello seguita dal nome della funzionalità sperimentale.</span><span class="sxs-lookup"><span data-stu-id="c9b78-116">Experimental code should go into a top-level experimental folder followed by the experimental feature name.</span></span> <span data-ttu-id="c9b78-117">Ad esempio, se si tenta di contribuire a una nuova funzionalità FooBar, inserire il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="c9b78-117">For example, if trying to contribute a new feature FooBar, put code in the following:</span></span>

- <span data-ttu-id="c9b78-118">Scene di esempio, script `MRTK/Examples/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="c9b78-118">Example scenes, scripts go into `MRTK/Examples/Experimental/FooBar/`</span></span>
- <span data-ttu-id="c9b78-119">Script dei componenti, prefabbricati `MRTK/SDK/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="c9b78-119">Component scripts, prefabs go into `MRTK/SDK/Experimental/FooBar/`</span></span>
- <span data-ttu-id="c9b78-120">I controlli componente entrano in `MRTK/SDK/Inspectors/Experimental/FooBar`</span><span class="sxs-lookup"><span data-stu-id="c9b78-120">Component inspectors go into `MRTK/SDK/Inspectors/Experimental/FooBar`</span></span>

<span data-ttu-id="c9b78-121">Quando si usano sottocartelle sotto il nome della funzionalità sperimentale, provare a eseguire il mirroring della stessa struttura di cartelle di MRTK.</span><span class="sxs-lookup"><span data-stu-id="c9b78-121">When using sub-folders under the experimental feature name, try to mirror the same folder structure of MRTK.</span></span>

<span data-ttu-id="c9b78-122">Ad esempio, i risolutori subentrano `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span><span class="sxs-lookup"><span data-stu-id="c9b78-122">For example, solvers would go under `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span></span>

<span data-ttu-id="c9b78-123">Mantieni le scene in una cartella della scena nella parte superiore: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span><span class="sxs-lookup"><span data-stu-id="c9b78-123">Keep scenes in a scene folder near the top: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span></span>

> [!NOTE]
> <span data-ttu-id="c9b78-124">Non è stata considerata una singola cartella radice sperimentale, ma è stato inserito un esperimento sperimentale in say `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` .</span><span class="sxs-lookup"><span data-stu-id="c9b78-124">We considered not having a single Experimental root folder and instead putting Experimental under say `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity`.</span></span> <span data-ttu-id="c9b78-125">Abbiamo deciso di usare le cartelle alla base per semplificare l'individuazione delle funzionalità sperimentali.</span><span class="sxs-lookup"><span data-stu-id="c9b78-125">We decided to go with folders at the base to make the experimental features easier to discover.</span></span>

### <a name="experimental-code-should-be-in-a-special-namespace"></a><span data-ttu-id="c9b78-126">Il codice sperimentale deve trovarsi in uno spazio dei nomi speciale</span><span class="sxs-lookup"><span data-stu-id="c9b78-126">Experimental code should be in a special namespace</span></span>

<span data-ttu-id="c9b78-127">Verificare che il codice sperimentale si trovi in uno spazio dei nomi sperimentale che corrisponda alla posizione non sperimentale.</span><span class="sxs-lookup"><span data-stu-id="c9b78-127">Ensure that the experimental code lives in an experimental namespace that matches the non-experimental location.</span></span> <span data-ttu-id="c9b78-128">Se, ad esempio, il componente fa parte dei risolutori in `Microsoft.MixedReality.Toolkit.Utilities.Solvers` , il relativo spazio dei nomi deve essere `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` .</span><span class="sxs-lookup"><span data-stu-id="c9b78-128">For example, if your component is part of solvers at `Microsoft.MixedReality.Toolkit.Utilities.Solvers`, its namespace should be `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers`.</span></span>

<span data-ttu-id="c9b78-129">Per un esempio, vedere [questa](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="c9b78-129">See [this PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) for an example.</span></span>

### <a name="experimental-features-should-have-an-experimental-attribute"></a><span data-ttu-id="c9b78-130">Le funzionalità sperimentali devono avere un attributo [Experimental]</span><span class="sxs-lookup"><span data-stu-id="c9b78-130">Experimental features should have an [Experimental] attribute</span></span>

<span data-ttu-id="c9b78-131">Aggiungere un `[Experimental]` attributo sopra uno dei campi per visualizzare una piccola finestra di dialogo nell'editor del componente che indica che la funzionalità è sperimentale e soggetta a modifiche significative.</span><span class="sxs-lookup"><span data-stu-id="c9b78-131">Add an `[Experimental]` attribute above one of your fields to have a small dialog appear in the component editor that mentions your feature is experimental and subject to significant changes.</span></span>

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a><span data-ttu-id="c9b78-132">I menu per le funzionalità sperimentali dovrebbero andare sotto il sottomenu "sperimentale"</span><span class="sxs-lookup"><span data-stu-id="c9b78-132">Menus for experimental features should go under "Experimental" sub-menu</span></span>

<span data-ttu-id="c9b78-133">Quando si aggiungono comandi ai menu nell'editor, verificare che le funzionalità sperimentali siano sottomenu "sperimentali".</span><span class="sxs-lookup"><span data-stu-id="c9b78-133">Ensure that experimental features are under "experimental" sub-menus when adding commands to menus in the editor.</span></span> <span data-ttu-id="c9b78-134">Ecco alcuni esempi:</span><span class="sxs-lookup"><span data-stu-id="c9b78-134">Here are a few examples:</span></span>

<span data-ttu-id="c9b78-135">Aggiunta di un comando di menu di primo livello:</span><span class="sxs-lookup"><span data-stu-id="c9b78-135">Adding a top-level menu command:</span></span>

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

<span data-ttu-id="c9b78-136">Aggiunta di un menu componenti:</span><span class="sxs-lookup"><span data-stu-id="c9b78-136">Adding a component menu:</span></span>

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a><span data-ttu-id="c9b78-137">Documentazione</span><span class="sxs-lookup"><span data-stu-id="c9b78-137">Documentation</span></span>

<span data-ttu-id="c9b78-138">Per aggiungere la documentazione per la funzionalità sperimentale, attenersi alla procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="c9b78-138">Follow these steps to add documentation for your experimental feature:</span></span>

1. <span data-ttu-id="c9b78-139">Qualsiasi documentazione relativa a una funzionalità sperimentale dovrebbe andare in un `readme.md` file nella cartella sperimentale.</span><span class="sxs-lookup"><span data-stu-id="c9b78-139">Any documentation for an experimental feature should go in a `readme.md` file in the experimental folder.</span></span> <span data-ttu-id="c9b78-140">ad esempio [`MRTK/SDK/Experimental/PulseShader/readme.md`](../features/experimental/pulse-shader.md).</span><span class="sxs-lookup"><span data-stu-id="c9b78-140">For example, [`MRTK/SDK/Experimental/PulseShader/readme.md`](../features/experimental/pulse-shader.md).</span></span>

1. <span data-ttu-id="c9b78-141">In *Panoramica delle funzionalità* aggiungere un collegamento nella sezione *sperimentale* all'indirizzo [`Documentation/toc.yml`](../toc.yml) .</span><span class="sxs-lookup"><span data-stu-id="c9b78-141">Under *Feature Overviews* Add a link in the *Experimental* section at [`Documentation/toc.yml`](../toc.yml).</span></span>

### <a name="minimize-impact-to-mrtk-code"></a><span data-ttu-id="c9b78-142">Ridurre al minimo l'effetto sul codice MRTK</span><span class="sxs-lookup"><span data-stu-id="c9b78-142">Minimize impact to MRTK code</span></span>

<span data-ttu-id="c9b78-143">Anche se la modifica del MRTK potrebbe far funzionare l'esperimento, può influito su altri utenti in modi non previsti.</span><span class="sxs-lookup"><span data-stu-id="c9b78-143">While your MRTK change might get your experiment to work, it could impact other people in ways you do not expect.</span></span>
<span data-ttu-id="c9b78-144">Tutte le regressioni apportate al codice MRTK Core comporteranno il ripristino della richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="c9b78-144">Any regressions you make to the MRTK core code would result in your pull request getting reverted.</span></span>

<span data-ttu-id="c9b78-145">Scopo di avere zero modifiche in cartelle diverse dalle cartelle sperimentali.</span><span class="sxs-lookup"><span data-stu-id="c9b78-145">Aim to have zero changes in folders other than experimental folders.</span></span> <span data-ttu-id="c9b78-146">Di seguito è riportato un elenco di cartelle che possono avere modifiche sperimentali:</span><span class="sxs-lookup"><span data-stu-id="c9b78-146">Here is a list of folders that can have experimental changes:</span></span>

- <span data-ttu-id="c9b78-147">MRTK/SDK/sperimentale</span><span class="sxs-lookup"><span data-stu-id="c9b78-147">MRTK/SDK/Experimental</span></span>
- <span data-ttu-id="c9b78-148">MRTK/SDK/ispettori/sperimentale</span><span class="sxs-lookup"><span data-stu-id="c9b78-148">MRTK/SDK/Inspectors/Experimental</span></span>
- <span data-ttu-id="c9b78-149">MRTK/esempi/sperimentale</span><span class="sxs-lookup"><span data-stu-id="c9b78-149">MRTK/Examples/Experimental</span></span>

<span data-ttu-id="c9b78-150">Le modifiche al di fuori di queste cartelle devono essere trattate con molta attenzione.</span><span class="sxs-lookup"><span data-stu-id="c9b78-150">Changes outside of these folders should be treated very carefully.</span></span> <span data-ttu-id="c9b78-151">Se la funzionalità sperimentale deve includere modifiche al codice MRTK core, è consigliabile suddividere le modifiche apportate da MRTK in una richiesta pull separata che includa i test e la documentazione.</span><span class="sxs-lookup"><span data-stu-id="c9b78-151">If your experimental feature must include changes to MRTK core code, consider splitting out MRTK changes into a separate pull request that includes tests and documentation.</span></span>

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a><span data-ttu-id="c9b78-152">L'uso della funzionalità sperimentale non dovrebbe influito sulla capacità degli utenti di usare i controlli di base</span><span class="sxs-lookup"><span data-stu-id="c9b78-152">Using your experimental feature should not impact people's ability to use core controls</span></span>

<span data-ttu-id="c9b78-153">La maggior parte degli utenti usa componenti UX di base come Button, ManipulationHandler e interagiscono molto spesso.</span><span class="sxs-lookup"><span data-stu-id="c9b78-153">Most people use core UX components like the button, ManipulationHandler and Interactable very frequently.</span></span> <span data-ttu-id="c9b78-154">Probabilmente non utilizzeranno la funzionalità sperimentale se impedisce l'uso di pulsanti.</span><span class="sxs-lookup"><span data-stu-id="c9b78-154">They will likely not use your experimental feature if it prevents them from using buttons.</span></span>

<span data-ttu-id="c9b78-155">L'uso del componente non dovrebbe interrompere i pulsanti, ManipulationHandler, BoundingBox o interactable.</span><span class="sxs-lookup"><span data-stu-id="c9b78-155">Using your component should not break buttons, ManipulationHandler, BoundingBox, or interactable.</span></span>

<span data-ttu-id="c9b78-156">Ad esempio, in [questa](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001)richiesta pull di ScrollableObjectCollection, l'aggiunta di un ScrollableObjectCollection ha impedito agli utenti di usare i prefabbricati dei pulsanti HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c9b78-156">For example, in [this ScrollableObjectCollection PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001), adding a ScrollableObjectCollection caused people to not be able to use the HoloLens button prefabs.</span></span> <span data-ttu-id="c9b78-157">Anche se ciò non è stato causato da un bug nella richiesta pull (ma è stato invece esposto un bug esistente), non è stato necessario che la richiesta pull venisse archiviata.</span><span class="sxs-lookup"><span data-stu-id="c9b78-157">Even though this was not caused by a bug in the PR (but rather exposed an existing bug), it prevented the PR from getting checked in.</span></span>

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a><span data-ttu-id="c9b78-158">Fornire una scena di esempio in cui viene illustrato come utilizzare la funzionalità</span><span class="sxs-lookup"><span data-stu-id="c9b78-158">Provide an example scene that demonstrates how to use the feature</span></span>

<span data-ttu-id="c9b78-159">Gli utenti devono vedere come usare la funzionalità e come testarla.</span><span class="sxs-lookup"><span data-stu-id="c9b78-159">People need to see how to use your feature, and how to test it.</span></span>

<span data-ttu-id="c9b78-160">Fornire un esempio in MRTK/examples/Experimental/YOUR_FEATURE</span><span class="sxs-lookup"><span data-stu-id="c9b78-160">Provide an example under MRTK/Examples/Experimental/YOUR_FEATURE</span></span>

### <a name="minimize-user-visible-flaws-in-experimental-features"></a><span data-ttu-id="c9b78-161">Ridurre al minimo gli errori visibili per gli utenti nelle funzionalità sperimentali</span><span class="sxs-lookup"><span data-stu-id="c9b78-161">Minimize user visible flaws in experimental features</span></span>

<span data-ttu-id="c9b78-162">Altri utenti non utilizzeranno la funzionalità sperimentale se non funziona, ma non consentirà di laurearsi a una funzionalità.</span><span class="sxs-lookup"><span data-stu-id="c9b78-162">Others will not use the experimental feature if it does not work, it will not graduate to a feature.</span></span>

<span data-ttu-id="c9b78-163">Testare la scena di esempio sulla piattaforma di destinazione e verificare che funzioni come previsto.</span><span class="sxs-lookup"><span data-stu-id="c9b78-163">Test your example scene on your target platform, make sure it works as expected.</span></span> <span data-ttu-id="c9b78-164">Assicurarsi che la funzionalità funzioni anche nell'editor, in modo che gli utenti possano scorrere rapidamente e visualizzare la funzionalità anche se non dispongono della piattaforma di destinazione.</span><span class="sxs-lookup"><span data-stu-id="c9b78-164">Make sure your feature also works in editor, so people can rapidly iterate and see your feature even if they don’t have the target platform.</span></span>

## <a name="graduating-experimental-code-into-mrtk-code"></a><span data-ttu-id="c9b78-165">Graduazione del codice sperimentale nel codice MRTK</span><span class="sxs-lookup"><span data-stu-id="c9b78-165">Graduating experimental code into MRTK code</span></span>

<span data-ttu-id="c9b78-166">Se una funzionalità è molto utile, è necessario configurarla nel codice MRTK principale.</span><span class="sxs-lookup"><span data-stu-id="c9b78-166">If a feature ends up seeing quite a lot of use, then we should graduate it into core MRTK code.</span></span> <span data-ttu-id="c9b78-167">A tale scopo, la funzionalità deve disporre di test, documentazione e una scena di esempio.</span><span class="sxs-lookup"><span data-stu-id="c9b78-167">To do this, the feature should have tests, documentation, and an example scene.</span></span>

<span data-ttu-id="c9b78-168">Quando si è pronti a laureare la funzionalità MRTK, creare un problema per archiviare la richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="c9b78-168">When you are ready to graduate the feature MRTK, create an issue to check in your PR against.</span></span> <span data-ttu-id="c9b78-169">La richiesta pull deve includere tutti gli elementi necessari per rendere questa funzionalità di base: test, documentazione e una scena di esempio che illustra l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="c9b78-169">The PR should include all the things needed to make this a core feature: tests, documentation, and an example scene showing usage.</span></span>

<span data-ttu-id="c9b78-170">Inoltre, non dimenticare di aggiornare gli spazi dei nomi per rimuovere il sottospazio "sperimentale".</span><span class="sxs-lookup"><span data-stu-id="c9b78-170">Also, don’t forget to update the namespaces to remove the “Experimental” subspace.</span></span>
