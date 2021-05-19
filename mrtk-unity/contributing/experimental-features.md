---
title: Funzionalità sperimentali
description: Documento relativo alle funzionalità sperimentali in MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 705b7ab96d22c5c94c04476de30e5524095c1ce2
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144786"
---
# <a name="experimental-features"></a><span data-ttu-id="6c205-104">Funzionalità sperimentali</span><span class="sxs-lookup"><span data-stu-id="6c205-104">Experimental features</span></span>

<span data-ttu-id="6c205-105">Alcune funzionalità a cui lavora il team di MRTK sembrano avere un valore iniziale molto grande anche se i dettagli non sono stati completamente dettagliati.</span><span class="sxs-lookup"><span data-stu-id="6c205-105">Some features the MRTK team works on appear to have a lot of initial value even if we haven’t fully fleshed out the details.</span></span> <span data-ttu-id="6c205-106">Per questi tipi di funzionalità, la community vuole avere la possibilità di vederle in anticipo.</span><span class="sxs-lookup"><span data-stu-id="6c205-106">For these types of features, we want the community to get a chance to see them early.</span></span> <span data-ttu-id="6c205-107">Poiché sono all'inizio del ciclo, vengono etichettati come sperimentali per indicare che sono ancora in evoluzione e soggetti a modifiche nel tempo.</span><span class="sxs-lookup"><span data-stu-id="6c205-107">Because they are early in the cycle, we label them as experimental to indicate that they are still evolving, and subject to change over time.</span></span>

## <a name="what-to-expect-from-an-experimental-feature"></a><span data-ttu-id="6c205-108">Cosa aspettarsi da una funzionalità sperimentale</span><span class="sxs-lookup"><span data-stu-id="6c205-108">What to expect from an experimental feature</span></span>

<span data-ttu-id="6c205-109">Se un componente è contrassegnato come sperimentale, è possibile prevedere quanto segue:</span><span class="sxs-lookup"><span data-stu-id="6c205-109">If a component is marked experimental you can expect the following:</span></span>

- <span data-ttu-id="6c205-110">Scena di esempio che illustra l'utilizzo, che si trova `MRTK/Examples/Experimental` nella sottocartella</span><span class="sxs-lookup"><span data-stu-id="6c205-110">An example scene demonstrating usage, located under `MRTK/Examples/Experimental` sub-folder</span></span>
- <span data-ttu-id="6c205-111">Le funzionalità sperimentali potrebbero non avere documenti.</span><span class="sxs-lookup"><span data-stu-id="6c205-111">Experimental features may not have docs.</span></span>
- <span data-ttu-id="6c205-112">Probabilmente non hanno test.</span><span class="sxs-lookup"><span data-stu-id="6c205-112">They probably don't have tests.</span></span>
- <span data-ttu-id="6c205-113">Le funzionalità sperimentali sono soggette a modifiche.</span><span class="sxs-lookup"><span data-stu-id="6c205-113">Experimental features are subject to change.</span></span>

## <a name="experimental-feature-guidelines"></a><span data-ttu-id="6c205-114">Linee guida sulle funzionalità sperimentali</span><span class="sxs-lookup"><span data-stu-id="6c205-114">Experimental feature guidelines</span></span>

### <a name="experimental-code-should-live-in-a-separate-folder"></a><span data-ttu-id="6c205-115">Il codice sperimentale deve essere contenuto in una cartella separata</span><span class="sxs-lookup"><span data-stu-id="6c205-115">Experimental code should live in a separate folder</span></span>

<span data-ttu-id="6c205-116">Il codice sperimentale deve essere inserito in una cartella sperimentale di primo livello seguita dal nome della funzionalità sperimentale.</span><span class="sxs-lookup"><span data-stu-id="6c205-116">Experimental code should go into a top-level experimental folder followed by the experimental feature name.</span></span> <span data-ttu-id="6c205-117">Ad esempio, se si prova a fornire una nuova funzionalità FooBar, inserire il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="6c205-117">For example, if trying to contribute a new feature FooBar, put code in the following:</span></span>

- <span data-ttu-id="6c205-118">Scene di esempio, script `MRTK/Examples/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="6c205-118">Example scenes, scripts go into `MRTK/Examples/Experimental/FooBar/`</span></span>
- <span data-ttu-id="6c205-119">Script dei componenti, prefab `MRTK/SDK/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="6c205-119">Component scripts, prefabs go into `MRTK/SDK/Experimental/FooBar/`</span></span>
- <span data-ttu-id="6c205-120">I controlli dei componenti passano a `MRTK/SDK/Inspectors/Experimental/FooBar`</span><span class="sxs-lookup"><span data-stu-id="6c205-120">Component inspectors go into `MRTK/SDK/Inspectors/Experimental/FooBar`</span></span>

<span data-ttu-id="6c205-121">Quando si usano sottocartelle sotto il nome della funzionalità sperimentale, provare a eseguire il mirroring della stessa struttura di cartelle di MRTK.</span><span class="sxs-lookup"><span data-stu-id="6c205-121">When using sub-folders under the experimental feature name, try to mirror the same folder structure of MRTK.</span></span>

<span data-ttu-id="6c205-122">Ad esempio, i risolutori verrebbero sotto `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span><span class="sxs-lookup"><span data-stu-id="6c205-122">For example, solvers would go under `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span></span>

<span data-ttu-id="6c205-123">Tenere le scene in una cartella della scena nella parte superiore: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span><span class="sxs-lookup"><span data-stu-id="6c205-123">Keep scenes in a scene folder near the top: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span></span>

> [!NOTE]
> <span data-ttu-id="6c205-124">Si è considerato di non avere una singola cartella radice sperimentale e di inserire sperimentale in say `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` .</span><span class="sxs-lookup"><span data-stu-id="6c205-124">We considered not having a single Experimental root folder and instead putting Experimental under say `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity`.</span></span> <span data-ttu-id="6c205-125">Si è deciso di aggiungere cartelle alla base per semplificare l'individuazione delle funzionalità sperimentali.</span><span class="sxs-lookup"><span data-stu-id="6c205-125">We decided to go with folders at the base to make the experimental features easier to discover.</span></span>

### <a name="experimental-code-should-be-in-a-special-namespace"></a><span data-ttu-id="6c205-126">Il codice sperimentale deve essere in uno spazio dei nomi speciale</span><span class="sxs-lookup"><span data-stu-id="6c205-126">Experimental code should be in a special namespace</span></span>

<span data-ttu-id="6c205-127">Assicurarsi che il codice sperimentale si trova in uno spazio dei nomi sperimentale corrispondente alla posizione non sperimentale.</span><span class="sxs-lookup"><span data-stu-id="6c205-127">Ensure that the experimental code lives in an experimental namespace that matches the non-experimental location.</span></span> <span data-ttu-id="6c205-128">Ad esempio, se il componente fa parte di risolutori in `Microsoft.MixedReality.Toolkit.Utilities.Solvers` , il relativo spazio dei nomi deve essere `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` .</span><span class="sxs-lookup"><span data-stu-id="6c205-128">For example, if your component is part of solvers at `Microsoft.MixedReality.Toolkit.Utilities.Solvers`, its namespace should be `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers`.</span></span>

<span data-ttu-id="6c205-129">Per [un esempio, vedere](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) questa richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="6c205-129">See [this PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) for an example.</span></span>

### <a name="experimental-features-should-have-an-experimental-attribute"></a><span data-ttu-id="6c205-130">Le funzionalità sperimentali devono avere un attributo [Sperimentale]</span><span class="sxs-lookup"><span data-stu-id="6c205-130">Experimental features should have an [Experimental] attribute</span></span>

<span data-ttu-id="6c205-131">Aggiungere un attributo sopra uno dei campi per visualizzare una piccola finestra di dialogo nell'editor dei componenti che indica che la funzionalità è sperimentale e soggetta `[Experimental]` a modifiche significative.</span><span class="sxs-lookup"><span data-stu-id="6c205-131">Add an `[Experimental]` attribute above one of your fields to have a small dialog appear in the component editor that mentions your feature is experimental and subject to significant changes.</span></span>

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a><span data-ttu-id="6c205-132">I menu per le funzionalità sperimentali devono essere disponibili nel sottomenu "Sperimentale"</span><span class="sxs-lookup"><span data-stu-id="6c205-132">Menus for experimental features should go under "Experimental" sub-menu</span></span>

<span data-ttu-id="6c205-133">Assicurarsi che le funzionalità sperimentali siano disponibili nei sottomenu "sperimentali" quando si aggiungono comandi ai menu nell'editor.</span><span class="sxs-lookup"><span data-stu-id="6c205-133">Ensure that experimental features are under "experimental" sub-menus when adding commands to menus in the editor.</span></span> <span data-ttu-id="6c205-134">Ecco alcuni esempi:</span><span class="sxs-lookup"><span data-stu-id="6c205-134">Here are a few examples:</span></span>

<span data-ttu-id="6c205-135">Aggiunta di un comando di menu di primo livello:</span><span class="sxs-lookup"><span data-stu-id="6c205-135">Adding a top-level menu command:</span></span>

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

<span data-ttu-id="6c205-136">Aggiunta di un menu dei componenti:</span><span class="sxs-lookup"><span data-stu-id="6c205-136">Adding a component menu:</span></span>

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a><span data-ttu-id="6c205-137">Documentazione</span><span class="sxs-lookup"><span data-stu-id="6c205-137">Documentation</span></span>

<span data-ttu-id="6c205-138">Seguire questa procedura per aggiungere la documentazione per la funzionalità sperimentale:</span><span class="sxs-lookup"><span data-stu-id="6c205-138">Follow these steps to add documentation for your experimental feature:</span></span>

1. <span data-ttu-id="6c205-139">Qualsiasi documentazione per una funzionalità sperimentale deve essere in un `readme.md` file nella cartella sperimentale.</span><span class="sxs-lookup"><span data-stu-id="6c205-139">Any documentation for an experimental feature should go in a `readme.md` file in the experimental folder.</span></span> <span data-ttu-id="6c205-140">Ad esempio, MRTK/SDK/Experimental/PulseShader/readme.md.</span><span class="sxs-lookup"><span data-stu-id="6c205-140">For example, MRTK/SDK/Experimental/PulseShader/readme.md.</span></span>

1. <span data-ttu-id="6c205-141">In *Cenni preliminari sulle* funzionalità aggiungere un collegamento nella sezione *Sperimentale* all'indirizzo [`Documentation/toc.yml`](../toc.yml) .</span><span class="sxs-lookup"><span data-stu-id="6c205-141">Under *Feature Overviews* Add a link in the *Experimental* section at [`Documentation/toc.yml`](../toc.yml).</span></span>

### <a name="minimize-impact-to-mrtk-code"></a><span data-ttu-id="6c205-142">Ridurre al minimo l'impatto sul codice MRTK</span><span class="sxs-lookup"><span data-stu-id="6c205-142">Minimize impact to MRTK code</span></span>

<span data-ttu-id="6c205-143">Anche se la modifica di MRTK potrebbe far funzionare l'esperimento, potrebbe influire su altre persone in modi non previsti.</span><span class="sxs-lookup"><span data-stu-id="6c205-143">While your MRTK change might get your experiment to work, it could impact other people in ways you do not expect.</span></span>
<span data-ttu-id="6c205-144">Eventuali regressioni apportate al codice principale di MRTK comportano il ripristino della richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="6c205-144">Any regressions you make to the MRTK core code would result in your pull request getting reverted.</span></span>

<span data-ttu-id="6c205-145">L'obiettivo è avere zero modifiche nelle cartelle diverse da quelle sperimentali.</span><span class="sxs-lookup"><span data-stu-id="6c205-145">Aim to have zero changes in folders other than experimental folders.</span></span> <span data-ttu-id="6c205-146">Ecco un elenco di cartelle che possono avere modifiche sperimentali:</span><span class="sxs-lookup"><span data-stu-id="6c205-146">Here is a list of folders that can have experimental changes:</span></span>

- <span data-ttu-id="6c205-147">MRTK/SDK/Sperimentale</span><span class="sxs-lookup"><span data-stu-id="6c205-147">MRTK/SDK/Experimental</span></span>
- <span data-ttu-id="6c205-148">MRTK/SDK/Inspectors/Experimental</span><span class="sxs-lookup"><span data-stu-id="6c205-148">MRTK/SDK/Inspectors/Experimental</span></span>
- <span data-ttu-id="6c205-149">MRTK/Examples/Experimental</span><span class="sxs-lookup"><span data-stu-id="6c205-149">MRTK/Examples/Experimental</span></span>

<span data-ttu-id="6c205-150">Le modifiche all'esterno di queste cartelle devono essere considerate con attenzione.</span><span class="sxs-lookup"><span data-stu-id="6c205-150">Changes outside of these folders should be treated very carefully.</span></span> <span data-ttu-id="6c205-151">Se la funzionalità sperimentale deve includere modifiche al codice principale MRTK, provare a suddividere le modifiche MRTK in una richiesta pull separata che include test e documentazione.</span><span class="sxs-lookup"><span data-stu-id="6c205-151">If your experimental feature must include changes to MRTK core code, consider splitting out MRTK changes into a separate pull request that includes tests and documentation.</span></span>

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a><span data-ttu-id="6c205-152">L'uso della funzionalità sperimentale non dovrebbe influire sulla capacità degli utenti di usare i controlli di base</span><span class="sxs-lookup"><span data-stu-id="6c205-152">Using your experimental feature should not impact people's ability to use core controls</span></span>

<span data-ttu-id="6c205-153">La maggior parte delle persone usa componenti principali dell'esperienza utente come il pulsante ManipulationHandler e Interactable molto frequentemente.</span><span class="sxs-lookup"><span data-stu-id="6c205-153">Most people use core UX components like the button, ManipulationHandler and Interactable very frequently.</span></span> <span data-ttu-id="6c205-154">È probabile che non usino la funzionalità sperimentale se impedisce loro di usare i pulsanti.</span><span class="sxs-lookup"><span data-stu-id="6c205-154">They will likely not use your experimental feature if it prevents them from using buttons.</span></span>

<span data-ttu-id="6c205-155">L'uso del componente non deve interrompere pulsanti, ManipulationHandler, BoundingBox o interactable.</span><span class="sxs-lookup"><span data-stu-id="6c205-155">Using your component should not break buttons, ManipulationHandler, BoundingBox, or interactable.</span></span>

<span data-ttu-id="6c205-156">In questa richiesta pull [ScrollableObjectCollection,](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001)ad esempio, l'aggiunta di un oggetto ScrollableObjectCollection ha causato la non possibilità di usare i prefab del pulsante HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6c205-156">For example, in [this ScrollableObjectCollection PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001), adding a ScrollableObjectCollection caused people to not be able to use the HoloLens button prefabs.</span></span> <span data-ttu-id="6c205-157">Anche se questo non è stato causato da un bug nella richiesta pull (ma piuttosto ha esposto un bug esistente), ha impedito l'accesso alla richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="6c205-157">Even though this was not caused by a bug in the PR (but rather exposed an existing bug), it prevented the PR from getting checked in.</span></span>

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a><span data-ttu-id="6c205-158">Fornire una scena di esempio che illustra come usare la funzionalità</span><span class="sxs-lookup"><span data-stu-id="6c205-158">Provide an example scene that demonstrates how to use the feature</span></span>

<span data-ttu-id="6c205-159">Gli utenti devono vedere come usare la funzionalità e come testarla.</span><span class="sxs-lookup"><span data-stu-id="6c205-159">People need to see how to use your feature, and how to test it.</span></span>

<span data-ttu-id="6c205-160">Fornire un esempio in MRTK/Examples/Experimental/YOUR_FEATURE</span><span class="sxs-lookup"><span data-stu-id="6c205-160">Provide an example under MRTK/Examples/Experimental/YOUR_FEATURE</span></span>

### <a name="minimize-user-visible-flaws-in-experimental-features"></a><span data-ttu-id="6c205-161">Ridurre al minimo i difetti visibili dell'utente nelle funzionalità sperimentali</span><span class="sxs-lookup"><span data-stu-id="6c205-161">Minimize user visible flaws in experimental features</span></span>

<span data-ttu-id="6c205-162">Altri utenti non useranno la funzionalità sperimentale se non funziona, non si diplondono a una funzionalità.</span><span class="sxs-lookup"><span data-stu-id="6c205-162">Others will not use the experimental feature if it does not work, it will not graduate to a feature.</span></span>

<span data-ttu-id="6c205-163">Testare la scena di esempio nella piattaforma di destinazione, assicurarsi che funzioni come previsto.</span><span class="sxs-lookup"><span data-stu-id="6c205-163">Test your example scene on your target platform, make sure it works as expected.</span></span> <span data-ttu-id="6c205-164">Assicurarsi che la funzionalità funzioni anche nell'editor, in modo che gli utenti possano eseguire rapidamente l'iterazione e visualizzare la funzionalità anche se non hanno la piattaforma di destinazione.</span><span class="sxs-lookup"><span data-stu-id="6c205-164">Make sure your feature also works in editor, so people can rapidly iterate and see your feature even if they don’t have the target platform.</span></span>

## <a name="graduating-experimental-code-into-mrtk-code"></a><span data-ttu-id="6c205-165">Frammentazione del codice sperimentale nel codice MRTK</span><span class="sxs-lookup"><span data-stu-id="6c205-165">Graduating experimental code into MRTK code</span></span>

<span data-ttu-id="6c205-166">Se una funzionalità finisce per essere molto utile, è consigliabile trasformarla in codice MRTK di base.</span><span class="sxs-lookup"><span data-stu-id="6c205-166">If a feature ends up seeing quite a lot of use, then we should graduate it into core MRTK code.</span></span> <span data-ttu-id="6c205-167">A tale scopo, la funzionalità deve avere test, documentazione e una scena di esempio.</span><span class="sxs-lookup"><span data-stu-id="6c205-167">To do this, the feature should have tests, documentation, and an example scene.</span></span>

<span data-ttu-id="6c205-168">Quando si è pronti a modificare la funzionalità MRTK, creare un problema da controllare nella richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="6c205-168">When you are ready to graduate the feature MRTK, create an issue to check in your PR against.</span></span> <span data-ttu-id="6c205-169">La richiesta pull deve includere tutti gli elementi necessari per rendere questa funzionalità di base: test, documentazione e una scena di esempio che mostra l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="6c205-169">The PR should include all the things needed to make this a core feature: tests, documentation, and an example scene showing usage.</span></span>

<span data-ttu-id="6c205-170">Non dimenticare inoltre di aggiornare gli spazi dei nomi per rimuovere il sottospazio "Sperimentale".</span><span class="sxs-lookup"><span data-stu-id="6c205-170">Also, don’t forget to update the namespaces to remove the “Experimental” subspace.</span></span>
