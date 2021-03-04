---
title: DocumentationGuide
description: linee guida e standard per la documentazione per MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: cc940aa1458db3e67c1ab30ea243adfc51eca7af
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783717"
---
# <a name="documentation-guidelines"></a><span data-ttu-id="f5fab-104">Linee guida sulla documentazione</span><span class="sxs-lookup"><span data-stu-id="f5fab-104">Documentation guidelines</span></span>

![Logo di MRTK](../features/images/MRTK_Logo_Rev.png)

<span data-ttu-id="f5fab-106">Questo documento descrive le linee guida e gli standard della documentazione per il Toolkit di realtà mista (MRTK).</span><span class="sxs-lookup"><span data-stu-id="f5fab-106">This document outlines the documentation guidelines and standards for the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="f5fab-107">Viene fornita un'introduzione agli aspetti tecnici della scrittura e della generazione della documentazione, per evidenziare i problemi comuni e per descrivere lo stile di scrittura consigliato.</span><span class="sxs-lookup"><span data-stu-id="f5fab-107">This provides an introduction to technical aspects of documentation writing and generation, to highlight common pitfalls, and to describe the recommended writing style.</span></span>

<span data-ttu-id="f5fab-108">La pagina stessa dovrebbe fungere da esempio, quindi usa lo stile designato e le funzionalità di markup più comuni della documentazione.</span><span class="sxs-lookup"><span data-stu-id="f5fab-108">The page itself is supposed to serve as an example, therefore it uses the intended style and the most common markup features of the documentation.</span></span>

- [<span data-ttu-id="f5fab-109">Origine</span><span class="sxs-lookup"><span data-stu-id="f5fab-109">Source</span></span>](#source-documentation)
- [<span data-ttu-id="f5fab-110">Procedure</span><span class="sxs-lookup"><span data-stu-id="f5fab-110">How-to</span></span>](#how-to-documentation)
- [<span data-ttu-id="f5fab-111">Progettazione</span><span class="sxs-lookup"><span data-stu-id="f5fab-111">Design</span></span>](#design-documentation)
- [<span data-ttu-id="f5fab-112">Note sulle prestazioni</span><span class="sxs-lookup"><span data-stu-id="f5fab-112">Performance notes</span></span>](#performance-notes)
- [<span data-ttu-id="f5fab-113">Modifiche di rilievo</span><span class="sxs-lookup"><span data-stu-id="f5fab-113">Breaking changes</span></span>](#breaking-changes)

---

## <a name="functionality-and-markup"></a><span data-ttu-id="f5fab-114">Funzionalità e markup</span><span class="sxs-lookup"><span data-stu-id="f5fab-114">Functionality and markup</span></span>

<span data-ttu-id="f5fab-115">Questa sezione descrive le funzionalità di uso frequente.</span><span class="sxs-lookup"><span data-stu-id="f5fab-115">This section describes frequently needed features.</span></span> <span data-ttu-id="f5fab-116">Per verificarne il funzionamento, esaminare il codice sorgente della pagina.</span><span class="sxs-lookup"><span data-stu-id="f5fab-116">To see how they work, look at the source code of the page.</span></span>

1. <span data-ttu-id="f5fab-117">Elenchi numerati</span><span class="sxs-lookup"><span data-stu-id="f5fab-117">Numbered lists</span></span>
   1. <span data-ttu-id="f5fab-118">Elenchi numerati annidati con almeno 3 spazi vuoti iniziali</span><span class="sxs-lookup"><span data-stu-id="f5fab-118">Nested numbered lists with at least 3 leading blank spaces</span></span>
   1. <span data-ttu-id="f5fab-119">Il numero effettivo nel codice è irrilevante; l'analisi si occuperà di impostare il numero di elemento corretto.</span><span class="sxs-lookup"><span data-stu-id="f5fab-119">The actual number in code is irrelevant; parsing will take care of setting the correct item number.</span></span>

- <span data-ttu-id="f5fab-120">Elenchi punti elenco</span><span class="sxs-lookup"><span data-stu-id="f5fab-120">Bullet point lists</span></span>
  - <span data-ttu-id="f5fab-121">Elenchi punti puntati annidati</span><span class="sxs-lookup"><span data-stu-id="f5fab-121">Nested bullet point lists</span></span>
- <span data-ttu-id="f5fab-122">Testo in **grassetto** con \* \* asterisco doppio\*\*</span><span class="sxs-lookup"><span data-stu-id="f5fab-122">Text in **bold** with \*\*double asterisk\*\*</span></span>
- <span data-ttu-id="f5fab-123"> *testo* corsivo con carattere di \_ sottolineatura \_ o \* asterisco singolo\*</span><span class="sxs-lookup"><span data-stu-id="f5fab-123">_italic_ *text* with \_underscore\_ or \*single asterisk\*</span></span>
- <span data-ttu-id="f5fab-124">Testo `highlighted as code` all'interno di una frase \` con le virgolette\`</span><span class="sxs-lookup"><span data-stu-id="f5fab-124">Text `highlighted as code` within a sentence \`using backquotes\`</span></span>
- <span data-ttu-id="f5fab-125">Collegamenti alle pagine di docs [MRTK linee guida sulla documentazione](DocumentationGuide.md)</span><span class="sxs-lookup"><span data-stu-id="f5fab-125">Links to docs pages [MRTK documentation guidelines](DocumentationGuide.md)</span></span>
- <span data-ttu-id="f5fab-126">Collegamenti a [ancoraggi all'interno di una pagina](#style); gli ancoraggi sono formati sostituendo gli spazi con trattini e convertendo in lettere minuscole</span><span class="sxs-lookup"><span data-stu-id="f5fab-126">Links to [anchors within a page](#style); anchors are formed by replacing spaces with dashes, and converting to lowercase</span></span>

<span data-ttu-id="f5fab-127">Per gli esempi di codice vengono usati i blocchi con tre apice \` \` \` e si specifica *CSharp* come lingua per l'evidenziazione della sintassi:</span><span class="sxs-lookup"><span data-stu-id="f5fab-127">For code samples we use the blocks with three backticks \`\`\` and specify *csharp* as the language for syntax highlighting:</span></span>

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

<span data-ttu-id="f5fab-128">Quando si menziona il codice all'interno di una frase `use a single backtick` .</span><span class="sxs-lookup"><span data-stu-id="f5fab-128">When mentioning code within a sentence `use a single backtick`.</span></span>

### <a name="todos"></a><span data-ttu-id="f5fab-129">Elementi todo</span><span class="sxs-lookup"><span data-stu-id="f5fab-129">TODOs</span></span>

<span data-ttu-id="f5fab-130">Evitare di usare TODOs in docs, nel tempo questi oggetti TODOs (come il codice TODOs) tendono a accumularsi e a sapere come devono essere aggiornati e perché andranno persi.</span><span class="sxs-lookup"><span data-stu-id="f5fab-130">Avoid using TODOs in docs, as over time these TODOs (like code TODOs) tend to accumulate and information about how they should be updated and why gets lost.</span></span>

<span data-ttu-id="f5fab-131">Se è assolutamente necessario aggiungere una TODO, attenersi alla procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="f5fab-131">If it is absolutely necessary to add a TODO, follow these steps:</span></span>

1. <span data-ttu-id="f5fab-132">Inserire un nuovo problema in GitHub che descrive il contesto dietro il TODO e fornire un background sufficiente che un altro collaboratore possa comprendere e quindi risolvere il problema.</span><span class="sxs-lookup"><span data-stu-id="f5fab-132">File a new issue on Github describing the context behind the TODO, and provide enough background that another contributor would be able to understand and then address the TODO.</span></span>
2. <span data-ttu-id="f5fab-133">Fare riferimento all'URL del problema nell'attività todo nella documentazione.</span><span class="sxs-lookup"><span data-stu-id="f5fab-133">Reference the issue URL in the todo in the docs.</span></span>

\<\!-- TODO: [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE)  A brief blurb on the issue --\>

### <a name="highlighted-sections"></a><span data-ttu-id="f5fab-134">Sezioni evidenziate</span><span class="sxs-lookup"><span data-stu-id="f5fab-134">Highlighted sections</span></span>

<span data-ttu-id="f5fab-135">Per evidenziare punti specifici del lettore, utilizzare *> [!NOTE]* , *> [!WARNING]* e *> [!IMPORTANT]* per produrre gli stili seguenti.</span><span class="sxs-lookup"><span data-stu-id="f5fab-135">To highlight specific points to the reader, use *> [!NOTE]* , *> [!WARNING]* , and *> [!IMPORTANT]* to produce the following styles.</span></span> <span data-ttu-id="f5fab-136">Si consiglia di utilizzare note per punti generali e avvisi/punti importanti solo per i casi speciali rilevanti.</span><span class="sxs-lookup"><span data-stu-id="f5fab-136">It is recommended to use notes for general points and warning/important points only for special relevant cases.</span></span>

> [!NOTE]
> <span data-ttu-id="f5fab-137">Esempio di una nota</span><span class="sxs-lookup"><span data-stu-id="f5fab-137">Example of a note</span></span>

> [!WARNING]
> <span data-ttu-id="f5fab-138">Esempio di avviso</span><span class="sxs-lookup"><span data-stu-id="f5fab-138">Example of a warning</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5fab-139">Esempio di commento importante</span><span class="sxs-lookup"><span data-stu-id="f5fab-139">Example of an important comment</span></span>

## <a name="page-layout"></a><span data-ttu-id="f5fab-140">Layout di pagina</span><span class="sxs-lookup"><span data-stu-id="f5fab-140">Page layout</span></span>

### <a name="introduction"></a><span data-ttu-id="f5fab-141">Introduzione</span><span class="sxs-lookup"><span data-stu-id="f5fab-141">Introduction</span></span>

<span data-ttu-id="f5fab-142">La parte immediatamente successiva al titolo del capitolo principale dovrebbe fungere da breve introduzione sul capitolo.</span><span class="sxs-lookup"><span data-stu-id="f5fab-142">The part right after the main chapter title should serve as a short introduction what the chapter is about.</span></span> <span data-ttu-id="f5fab-143">Non eseguire questa operazione troppo a lungo, bensì aggiungere i sottotitoli.</span><span class="sxs-lookup"><span data-stu-id="f5fab-143">Do not make this too long, instead add sub headlines.</span></span> <span data-ttu-id="f5fab-144">Che consentono di eseguire il collegamento a sezioni e possono essere salvate come segnalibri.</span><span class="sxs-lookup"><span data-stu-id="f5fab-144">These allow to link to sections and can be saved as bookmarks.</span></span>

### <a name="main-body"></a><span data-ttu-id="f5fab-145">Corpo principale</span><span class="sxs-lookup"><span data-stu-id="f5fab-145">Main body</span></span>

<span data-ttu-id="f5fab-146">Usare i titoli a due livelli e a tre livelli per strutturare il resto.</span><span class="sxs-lookup"><span data-stu-id="f5fab-146">Use two-level and three-level headlines to structure the rest.</span></span>

<span data-ttu-id="f5fab-147">**Sezioni mini**</span><span class="sxs-lookup"><span data-stu-id="f5fab-147">**Mini Sections**</span></span>

<span data-ttu-id="f5fab-148">Consente di utilizzare una riga di testo in grassetto per i blocchi che devono essere rilevati. Questa operazione può essere sostituita da titoli di quattro livelli a un certo punto.</span><span class="sxs-lookup"><span data-stu-id="f5fab-148">Use a bold line of text for blocks that should stand out. We might replace this by four-level headlines at some point.</span></span>

### <a name="see-also-section"></a><span data-ttu-id="f5fab-149">Sezione ' See also '</span><span class="sxs-lookup"><span data-stu-id="f5fab-149">'See also' section</span></span>

<span data-ttu-id="f5fab-150">La maggior parte delle pagine deve terminare con un capitolo denominato *vedere anche*.</span><span class="sxs-lookup"><span data-stu-id="f5fab-150">Most pages should end with a chapter called *See also*.</span></span> <span data-ttu-id="f5fab-151">Questo capitolo è semplicemente un elenco puntato ai collegamenti alle pagine correlate a questo argomento.</span><span class="sxs-lookup"><span data-stu-id="f5fab-151">This chapter is simply a bullet pointed list of links to pages related to this topic.</span></span> <span data-ttu-id="f5fab-152">Questi collegamenti possono anche essere visualizzati all'interno del testo della pagina, laddove appropriato, ma ciò non è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="f5fab-152">These links may also appear within the page text where appropriate, but this is not required.</span></span> <span data-ttu-id="f5fab-153">Analogamente, il testo della pagina può contenere collegamenti a pagine non correlate all'argomento principale, che non devono essere incluse nell'elenco *vedere anche* .</span><span class="sxs-lookup"><span data-stu-id="f5fab-153">Similarly, the page text may contain links to pages that are not related to the main topic, these should not be included in the *See also* list.</span></span> <span data-ttu-id="f5fab-154">Vedere [anche il capitolo '' di questa pagina](#see-also) come esempio per la scelta dei collegamenti.</span><span class="sxs-lookup"><span data-stu-id="f5fab-154">See [this page's ''See also'' chapter](#see-also) as an example for the choice of links.</span></span>

## <a name="table-of-contents-toc"></a><span data-ttu-id="f5fab-155">Sommario (sommario)</span><span class="sxs-lookup"><span data-stu-id="f5fab-155">Table of Contents (TOC)</span></span>

<span data-ttu-id="f5fab-156">I file di sommario vengono usati per generare le barre di navigazione nella documentazione di MRTK github.io.</span><span class="sxs-lookup"><span data-stu-id="f5fab-156">Toc files are used for generating the navigation bars in the MRTK github.io documentation.</span></span>
<span data-ttu-id="f5fab-157">Ogni volta che viene aggiunto un nuovo file di documentazione, assicurarsi che sia presente una voce per il file in uno dei file TOC. yml della cartella della documentazione.</span><span class="sxs-lookup"><span data-stu-id="f5fab-157">Whenever a new documentation file is added, make sure that there's an entry for that file in one of the toc.yml files of the documentation folder.</span></span> <span data-ttu-id="f5fab-158">Solo gli articoli elencati nei file di sommario vengono visualizzati nell'esplorazione della documentazione per sviluppatori. Può essere presente un file di sommario per ogni sottocartella della cartella della documentazione che può essere collegata a qualsiasi file di sommario esistente per aggiungerlo come sottosezione alla parte corrispondente della navigazione.</span><span class="sxs-lookup"><span data-stu-id="f5fab-158">Only articles listed in the toc files will show up in the navigation of the developer docs. There can be a toc file for every subfolder in the documentation folder which can be linked into any existing toc file to add it as a subsection to the corresponding part of the navigation.</span></span>

## <a name="style"></a><span data-ttu-id="f5fab-159">Stile</span><span class="sxs-lookup"><span data-stu-id="f5fab-159">Style</span></span>

### <a name="writing-style"></a><span data-ttu-id="f5fab-160">Stile di scrittura</span><span class="sxs-lookup"><span data-stu-id="f5fab-160">Writing style</span></span>

<span data-ttu-id="f5fab-161">Regola empirica generale: prova a **suonare Professional**.</span><span class="sxs-lookup"><span data-stu-id="f5fab-161">General rule of thumb: Try to **sound professional**.</span></span> <span data-ttu-id="f5fab-162">Che in genere significa evitare un "tono conversazione".</span><span class="sxs-lookup"><span data-stu-id="f5fab-162">That usually means to avoid a 'conversational tone'.</span></span> <span data-ttu-id="f5fab-163">Provare anche a evitare iperboli e sensazioni.</span><span class="sxs-lookup"><span data-stu-id="f5fab-163">Also try to avoid hyperbole and sensationalism.</span></span>

1. <span data-ttu-id="f5fab-164">Non provare a essere (troppo) divertente.</span><span class="sxs-lookup"><span data-stu-id="f5fab-164">Don't try to be (overly) funny.</span></span>
2. <span data-ttu-id="f5fab-165">Non scrivere mai ' I '</span><span class="sxs-lookup"><span data-stu-id="f5fab-165">Never write 'I'</span></span>
3. <span data-ttu-id="f5fab-166">Evitare "We".</span><span class="sxs-lookup"><span data-stu-id="f5fab-166">Avoid 'we'.</span></span> <span data-ttu-id="f5fab-167">Questo può essere in genere riformulato con facilità, usando invece ' MRTK '.</span><span class="sxs-lookup"><span data-stu-id="f5fab-167">This can usually be rephrased easily, using 'MRTK' instead.</span></span> <span data-ttu-id="f5fab-168">Esempio: "supporto di questa funzionalità"-> "MRTK supporta questa funzionalità" o "sono supportate le funzionalità seguenti...".</span><span class="sxs-lookup"><span data-stu-id="f5fab-168">Example: "we support this feature" -> "MRTK supports this feature" or "the following features are supported ...".</span></span>
4. <span data-ttu-id="f5fab-169">In modo analogo, provare a evitare "You".</span><span class="sxs-lookup"><span data-stu-id="f5fab-169">Similarly, try to avoid 'you'.</span></span> <span data-ttu-id="f5fab-170">Esempio: "con questa semplice modifica lo shader diventa configurabile!"</span><span class="sxs-lookup"><span data-stu-id="f5fab-170">Example: "With this simple change your shader becomes configurable!"</span></span> <span data-ttu-id="f5fab-171">-> "shader può essere reso configurabile con scarso sforzo".</span><span class="sxs-lookup"><span data-stu-id="f5fab-171">-> "Shaders can be made configurable with little effort."</span></span>
5. <span data-ttu-id="f5fab-172">Non usare "frasi imprecise".</span><span class="sxs-lookup"><span data-stu-id="f5fab-172">Do not use 'sloppy phrases'.</span></span>
6. <span data-ttu-id="f5fab-173">Evitare di sembrare eccessivamente entusiasti, non è necessario vendere niente.</span><span class="sxs-lookup"><span data-stu-id="f5fab-173">Avoid sounding overly excited, we do not need to sell anything.</span></span>
7. <span data-ttu-id="f5fab-174">Analogamente, evitare di essere eccessivamente drammatici.</span><span class="sxs-lookup"><span data-stu-id="f5fab-174">Similarly, avoid being overly dramatic.</span></span> <span data-ttu-id="f5fab-175">I punti esclamativi sono raramente necessari.</span><span class="sxs-lookup"><span data-stu-id="f5fab-175">Exclamation marks are rarely needed.</span></span>

### <a name="capitalization"></a><span data-ttu-id="f5fab-176">Uso delle maiuscole</span><span class="sxs-lookup"><span data-stu-id="f5fab-176">Capitalization</span></span>

- <span data-ttu-id="f5fab-177">Usare **la frase maiuscola per i titoli**.</span><span class="sxs-lookup"><span data-stu-id="f5fab-177">Use **Sentence case for headlines**.</span></span> <span data-ttu-id="f5fab-178">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f5fab-178">Ie.</span></span> <span data-ttu-id="f5fab-179">capitalizzare la prima lettera e i nomi, ma nient'altro.</span><span class="sxs-lookup"><span data-stu-id="f5fab-179">capitalize the first letter and names, but nothing else.</span></span>
- <span data-ttu-id="f5fab-180">Usare la lingua inglese normale per tutti gli altri elementi.</span><span class="sxs-lookup"><span data-stu-id="f5fab-180">Use regular English for everything else.</span></span> <span data-ttu-id="f5fab-181">Ciò significa che non viene eseguita la **capitalizzazione di parole arbitrarie**, anche se contengono un significato speciale in tale contesto.</span><span class="sxs-lookup"><span data-stu-id="f5fab-181">That means **do not capitalize arbitrary words**, even if they hold a special meaning in that context.</span></span> <span data-ttu-id="f5fab-182">Preferire il *testo in corsivo* per evidenziare determinate parole, vedere di [seguito](#emphasis-and-highlighting).</span><span class="sxs-lookup"><span data-stu-id="f5fab-182">Prefer *italic text* for highlighting certain words, [see below](#emphasis-and-highlighting).</span></span>
- <span data-ttu-id="f5fab-183">Quando un collegamento viene incorporato in una frase (ovvero il metodo preferito), il nome del capitolo standard usa sempre le lettere maiuscole, suddividendo quindi la regola di nessuna maiuscola arbitraria all'interno del testo.</span><span class="sxs-lookup"><span data-stu-id="f5fab-183">When a link is embedded in a sentence (which is the preferred method), the standard chapter name always uses capital letters, thus breaking the rule of no arbitrary capitalization inside text.</span></span> <span data-ttu-id="f5fab-184">Usare quindi un nome di collegamento personalizzato per correggere le maiuscole.</span><span class="sxs-lookup"><span data-stu-id="f5fab-184">Therefore use a custom link name to fix the capitalization.</span></span> <span data-ttu-id="f5fab-185">Ad esempio, di seguito è riportato un collegamento alla documentazione relativa al [controllo dei limiti](../features/ux-building-blocks/BoundsControl.md) .</span><span class="sxs-lookup"><span data-stu-id="f5fab-185">As an example, here is a link to the [bounds control](../features/ux-building-blocks/BoundsControl.md) documentation.</span></span>
- <span data-ttu-id="f5fab-186">Usare i nomi in maiuscolo, ad esempio *Unity*.</span><span class="sxs-lookup"><span data-stu-id="f5fab-186">Do capitalize names, such as *Unity*.</span></span>
- <span data-ttu-id="f5fab-187">NON capitalizzare "Editor" durante la scrittura dell' *editor di Unity*.</span><span class="sxs-lookup"><span data-stu-id="f5fab-187">Do NOT capitalize "editor" when writing *Unity editor*.</span></span>

### <a name="emphasis-and-highlighting"></a><span data-ttu-id="f5fab-188">Enfasi ed evidenziazione</span><span class="sxs-lookup"><span data-stu-id="f5fab-188">Emphasis and highlighting</span></span>

<span data-ttu-id="f5fab-189">Esistono due modi per evidenziare o evidenziare parole, rendendoli in grassetto o in corsivo.</span><span class="sxs-lookup"><span data-stu-id="f5fab-189">There are two ways to emphasize or highlight words, making them bold or making them italic.</span></span> <span data-ttu-id="f5fab-190">L'effetto del testo in grassetto è che il **testo in grassetto è allineato** e pertanto può essere facilmente notato durante lo scorrimento di una parte di testo o anche semplicemente lo scorrimento su una pagina.</span><span class="sxs-lookup"><span data-stu-id="f5fab-190">The effect of bold text is that **bold text sticks out** and therefore can easily be noticed while skimming a piece of text or even just scrolling over a page.</span></span> <span data-ttu-id="f5fab-191">Grassetto è molto interessante per evidenziare le frasi da ricordare.</span><span class="sxs-lookup"><span data-stu-id="f5fab-191">Bold is great to highlight phrases that people should remember.</span></span> <span data-ttu-id="f5fab-192">Tuttavia, **utilizzare raramente il testo in grassetto**, perché in genere si distrae.</span><span class="sxs-lookup"><span data-stu-id="f5fab-192">However, **use bold text rarely**, because it is generally distracting.</span></span>

<span data-ttu-id="f5fab-193">Spesso si vuole che un elemento "Group" appartenga logicamente insieme o evidenzi un termine specifico, perché ha un significato speciale.</span><span class="sxs-lookup"><span data-stu-id="f5fab-193">Often one wants to either 'group' something that belongs logically together or highlight a specific term, because it has a special meaning.</span></span> <span data-ttu-id="f5fab-194">Non è necessario che tali elementi riescano dal testo generale.</span><span class="sxs-lookup"><span data-stu-id="f5fab-194">Such things do not need to stand out of the overall text.</span></span> <span data-ttu-id="f5fab-195">Usare il testo corsivo come *metodo leggero* per evidenziare un elemento.</span><span class="sxs-lookup"><span data-stu-id="f5fab-195">Use italic text as a *lightweight method* to highlight something.</span></span>

<span data-ttu-id="f5fab-196">Analogamente, quando un nome di file, un percorso o una voce di menu è indicato nel testo, preferisce renderlo in corsivo per raggrupparlo logicamente, senza distrazioni.</span><span class="sxs-lookup"><span data-stu-id="f5fab-196">Similarly, when a filename, a path or a menu-entry is mentioned in text, prefer to make it italic to logically group it, without being distracting.</span></span>

<span data-ttu-id="f5fab-197">In generale, provare a **evitare un'evidenziazione del testo non necessaria**.</span><span class="sxs-lookup"><span data-stu-id="f5fab-197">In general, try to **avoid unnecessary text highlighting**.</span></span> <span data-ttu-id="f5fab-198">I termini speciali possono essere evidenziati una volta per far sì che il lettore sia in grado di riconoscere, non ripetere tale evidenziazione in tutto il testo, quando non serve più e solo distrae.</span><span class="sxs-lookup"><span data-stu-id="f5fab-198">Special terms can be highlighted once to make the reader aware, do not repeat such highlighting throughout the text, when it serves no purpose anymore and only distracts.</span></span>

### <a name="mentioning-menu-entries"></a><span data-ttu-id="f5fab-199">Menzione voci di menu</span><span class="sxs-lookup"><span data-stu-id="f5fab-199">Mentioning menu entries</span></span>

<span data-ttu-id="f5fab-200">Quando si menziona una voce di menu che un utente deve fare clic, la convenzione corrente è: *progetto > file > creare > foglia*</span><span class="sxs-lookup"><span data-stu-id="f5fab-200">When mentioning a menu entry that a user should click, the current convention is: *Project > Files > Create > Leaf*</span></span>

### <a name="links"></a><span data-ttu-id="f5fab-201">Collegamenti</span><span class="sxs-lookup"><span data-stu-id="f5fab-201">Links</span></span>

<span data-ttu-id="f5fab-202">Inserire il maggior numero possibile di collegamenti utili ad altre pagine, ma ogni collegamento viene eseguito una sola volta.</span><span class="sxs-lookup"><span data-stu-id="f5fab-202">Insert as many useful links to other pages as possible, but each link only once.</span></span> <span data-ttu-id="f5fab-203">Si supponga che un lettore faccia clic su ogni collegamento nella pagina e che si pensi a che cosa sarebbe fastidioso, se la stessa pagina si apre 20 volte.</span><span class="sxs-lookup"><span data-stu-id="f5fab-203">Assume a reader clicks on every link in the page, and think about how annoying it would be, if the same page opens 20 times.</span></span>

<span data-ttu-id="f5fab-204">Preferire i collegamenti incorporati in una frase:</span><span class="sxs-lookup"><span data-stu-id="f5fab-204">Prefer links embedded in a sentence:</span></span>

- <span data-ttu-id="f5fab-205">BAD: le linee guida sono utili.</span><span class="sxs-lookup"><span data-stu-id="f5fab-205">BAD: Guidelines are useful.</span></span> <span data-ttu-id="f5fab-206">Per informazioni dettagliate, vedere [questo capitolo](DocumentationGuide.md) .</span><span class="sxs-lookup"><span data-stu-id="f5fab-206">See [this chapter](DocumentationGuide.md) for details.</span></span>
- <span data-ttu-id="f5fab-207">BENE: le [linee guida](DocumentationGuide.md) sono utili.</span><span class="sxs-lookup"><span data-stu-id="f5fab-207">GOOD: [Guidelines](DocumentationGuide.md) are useful.</span></span>

<span data-ttu-id="f5fab-208">Evitare i collegamenti esterni, possono diventare obsoleti o contenere contenuti con copyright.</span><span class="sxs-lookup"><span data-stu-id="f5fab-208">Avoid external links, they can become outdated or contain copyrighted content.</span></span>

<span data-ttu-id="f5fab-209">Quando si aggiunge un collegamento, valutare se deve essere elencato anche nella sezione [vedere anche](#see-also) .</span><span class="sxs-lookup"><span data-stu-id="f5fab-209">When adding a link, consider whether it should also be listed in the [See also](#see-also) section.</span></span> <span data-ttu-id="f5fab-210">Analogamente, controllare se è necessario aggiungere un collegamento alla pagina nuova alla pagina collegata.</span><span class="sxs-lookup"><span data-stu-id="f5fab-210">Similarly, check whether a link to the new page should be added to the linked-to page.</span></span>

### <a name="images--screenshots"></a><span data-ttu-id="f5fab-211">Immagini/screenshot</span><span class="sxs-lookup"><span data-stu-id="f5fab-211">Images / screenshots</span></span>

<span data-ttu-id="f5fab-212">**Usare schermate sporadicamente.**</span><span class="sxs-lookup"><span data-stu-id="f5fab-212">**Use screenshots sparingly.**</span></span> <span data-ttu-id="f5fab-213">La gestione delle immagini nella documentazione è molto lavoro, le piccole modifiche dell'interfaccia utente possono rendere obsolete diverse schermate.</span><span class="sxs-lookup"><span data-stu-id="f5fab-213">Maintaining images in documentation is a lot of work, small UI changes can make a lot of screenshots outdated.</span></span> <span data-ttu-id="f5fab-214">Le regole seguenti ridurrà il lavoro richiesto per la manutenzione:</span><span class="sxs-lookup"><span data-stu-id="f5fab-214">The following rules will reduce maintenance effort:</span></span>

1. <span data-ttu-id="f5fab-215">Non usare screenshot per elementi che possono essere descritti nel testo.</span><span class="sxs-lookup"><span data-stu-id="f5fab-215">Do not use screenshots for things that can be described in text.</span></span> <span data-ttu-id="f5fab-216">In particolare, **non è mai stata catturata una griglia di proprietà** al solo scopo di visualizzare i nomi e i valori delle proprietà.</span><span class="sxs-lookup"><span data-stu-id="f5fab-216">Especially, **never screenshot a property grid** for the sole purpose of showing property names and values.</span></span>
2. <span data-ttu-id="f5fab-217">Non includere elementi in uno screenshot irrilevanti per quanto visualizzato.</span><span class="sxs-lookup"><span data-stu-id="f5fab-217">Do not include things in a screenshot that are irrelevant to what is shown.</span></span> <span data-ttu-id="f5fab-218">Ad esempio, quando viene visualizzato un effetto di rendering, creare una schermata del viewport, ma escludere qualsiasi interfaccia utente intorno ad essa.</span><span class="sxs-lookup"><span data-stu-id="f5fab-218">For instance, when a rendering effect is shown, make a screenshot of the viewport, but exclude any UI around it.</span></span> <span data-ttu-id="f5fab-219">Visualizzazione di un'interfaccia utente, provare a spostare le finestre in modo tale che solo questa parte importante sia presente nell'immagine.</span><span class="sxs-lookup"><span data-stu-id="f5fab-219">Showing some UI, try to move windows around such that only that important part is in the image.</span></span>
3. <span data-ttu-id="f5fab-220">Quando si include l'interfaccia utente screenshot, visualizzare solo le parti importanti.</span><span class="sxs-lookup"><span data-stu-id="f5fab-220">When including screenshot UI, only show the important parts.</span></span> <span data-ttu-id="f5fab-221">Se, ad esempio, si parla di pulsanti in una barra degli strumenti, creare un'immagine di dimensioni ridotte che mostri i pulsanti importanti della barra degli strumenti, ma escludere tutto il resto.</span><span class="sxs-lookup"><span data-stu-id="f5fab-221">For example, when talking about buttons in a toolbar, make a small image that shows the important toolbar buttons, but exclude everything around it.</span></span>
4. <span data-ttu-id="f5fab-222">Usare solo immagini facili da riprodurre.</span><span class="sxs-lookup"><span data-stu-id="f5fab-222">Only use images that are easy to reproduce.</span></span> <span data-ttu-id="f5fab-223">Ciò significa che non è possibile disegnare marcatori o evidenziare le schermate.</span><span class="sxs-lookup"><span data-stu-id="f5fab-223">That means do not paint markers or highlights into screenshots.</span></span> <span data-ttu-id="f5fab-224">In primo luogo, non esistono regole coerenti come dovrebbero apparire.</span><span class="sxs-lookup"><span data-stu-id="f5fab-224">First, there are no consistent rules how these should look, anyway.</span></span> <span data-ttu-id="f5fab-225">In secondo luogo, la riproduzione di uno screenshot di questo tipo è un'operazione aggiuntiva.</span><span class="sxs-lookup"><span data-stu-id="f5fab-225">Second, reproducing such a screenshot is additional effort.</span></span> <span data-ttu-id="f5fab-226">Descrivere invece le parti importanti del testo.</span><span class="sxs-lookup"><span data-stu-id="f5fab-226">Instead, describe the important parts in text.</span></span> <span data-ttu-id="f5fab-227">Esistono eccezioni a questa regola, ma sono rare.</span><span class="sxs-lookup"><span data-stu-id="f5fab-227">There are exceptions to this rule, but they are rare.</span></span>
5. <span data-ttu-id="f5fab-228">Ovviamente, è molto più impegnativo per ricreare un GIF animato.</span><span class="sxs-lookup"><span data-stu-id="f5fab-228">Obviously, it is much more effort to recreate an animated GIF.</span></span> <span data-ttu-id="f5fab-229">Si presume che sia responsabile della ricreazione fino alla fine del periodo di tempo o che gli utenti possano lasciarlo, se non vogliono dedicarsi a questo periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="f5fab-229">Expect to be responsible to recreate it until the end of time, or expect people to throw it out, if they don't want to spend that time.</span></span>
6. <span data-ttu-id="f5fab-230">Mantieni il numero di immagini in un articolo basso.</span><span class="sxs-lookup"><span data-stu-id="f5fab-230">Keep the number of images in an article low.</span></span> <span data-ttu-id="f5fab-231">Spesso un metodo valido consiste nel creare una schermata complessiva di uno strumento, che Mostra tutto e quindi descrivere il resto nel testo.</span><span class="sxs-lookup"><span data-stu-id="f5fab-231">Often a good method is to make one overall screenshot of some tool, that shows everything, and then describe the rest in text.</span></span> <span data-ttu-id="f5fab-232">In questo modo è più semplice sostituire lo screenshot quando necessario.</span><span class="sxs-lookup"><span data-stu-id="f5fab-232">This makes it easy to replace the screenshot when necessary.</span></span>

<span data-ttu-id="f5fab-233">Altri aspetti:</span><span class="sxs-lookup"><span data-stu-id="f5fab-233">Some other aspects:</span></span>

- <span data-ttu-id="f5fab-234">L'interfaccia utente dell'editor per le schermate dovrebbe usare un editor di tema grigio chiaro, perché non tutti gli utenti hanno accesso al tema scuro e si vuole rendere il più coerente possibile.</span><span class="sxs-lookup"><span data-stu-id="f5fab-234">The editor UI for screenshots should use light gray theme editor as not all users have access to the dark theme and we'd like to keep things as consistent as possible.</span></span>
- <span data-ttu-id="f5fab-235">La larghezza dell'immagine predefinita è 500 pixel, in quanto viene visualizzato correttamente nella maggior parte dei monitoraggi.</span><span class="sxs-lookup"><span data-stu-id="f5fab-235">Default image width is 500 pixels, as this displays well on most monitors.</span></span> <span data-ttu-id="f5fab-236">Provare a non deviare troppa parte.</span><span class="sxs-lookup"><span data-stu-id="f5fab-236">Try not to deviate too much from it.</span></span> <span data-ttu-id="f5fab-237">800 pixel larghezza deve essere il valore massimo.</span><span class="sxs-lookup"><span data-stu-id="f5fab-237">800 pixels width should be the maximum.</span></span>
- <span data-ttu-id="f5fab-238">Usare PNG per gli screenshot dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="f5fab-238">Use PNGs for screenshots of UI.</span></span>
- <span data-ttu-id="f5fab-239">Usare PNG o jpg per gli screenshot del viewport 3D.</span><span class="sxs-lookup"><span data-stu-id="f5fab-239">Use PNGs or JPGs for 3D viewport screenshots.</span></span> <span data-ttu-id="f5fab-240">Preferisce la qualità rispetto al rapporto di compressione.</span><span class="sxs-lookup"><span data-stu-id="f5fab-240">Prefer quality over compression ratio.</span></span>

### <a name="list-of-component-properties"></a><span data-ttu-id="f5fab-241">Elenco delle proprietà dei componenti</span><span class="sxs-lookup"><span data-stu-id="f5fab-241">List of component properties</span></span>

<span data-ttu-id="f5fab-242">Quando si documenta un elenco di proprietà, usare il testo in grassetto per evidenziare il nome della proprietà, quindi le interruzioni di riga e il testo normale per descriverli.</span><span class="sxs-lookup"><span data-stu-id="f5fab-242">When documenting a list of properties, use bold text to highlight the property name, then line breaks and regular text to describe them.</span></span> <span data-ttu-id="f5fab-243">Non usare i sottocapitoli o gli elenchi di punti elenco.</span><span class="sxs-lookup"><span data-stu-id="f5fab-243">Do not use sub-chapters or bullet point lists.</span></span>

<span data-ttu-id="f5fab-244">Inoltre, non dimenticare di terminare tutte le frasi con un punto.</span><span class="sxs-lookup"><span data-stu-id="f5fab-244">Also, don't forget to finish all sentences with a period.</span></span>

## <a name="page-completion-checklist"></a><span data-ttu-id="f5fab-245">Elenco di controllo completamento pagina</span><span class="sxs-lookup"><span data-stu-id="f5fab-245">Page completion checklist</span></span>

1. <span data-ttu-id="f5fab-246">Verificare che siano state seguite le linee guida del documento.</span><span class="sxs-lookup"><span data-stu-id="f5fab-246">Ensure that this document's guidelines were followed.</span></span>
1. <span data-ttu-id="f5fab-247">Esplorare la struttura del documento e verificare se il nuovo documento è indicato nella sezione [vedere anche](#see-also) di altre pagine.</span><span class="sxs-lookup"><span data-stu-id="f5fab-247">Browse the document structure and see if the new document could be mentioned under the [See also](#see-also) section of other pages.</span></span>
1. <span data-ttu-id="f5fab-248">Se disponibile, chiedere a un utente di conoscere l'argomento di prova: leggere la pagina per la correttezza tecnica.</span><span class="sxs-lookup"><span data-stu-id="f5fab-248">If available, have someone with knowledge of the topic proof-read the page for technical correctness.</span></span>
1. <span data-ttu-id="f5fab-249">Fare in modo che qualcuno legga la pagina per lo stile e la formattazione.</span><span class="sxs-lookup"><span data-stu-id="f5fab-249">Have someone proof-read the page for style and formatting.</span></span> <span data-ttu-id="f5fab-250">Questo può essere un utente che non ha familiarità con l'argomento, che è anche una corretta idea di ricevere commenti e suggerimenti sulla comprensione della documentazione.</span><span class="sxs-lookup"><span data-stu-id="f5fab-250">This can be someone unfamiliar with the topic, which is also a good idea to get feedback about how understandable the documentation is.</span></span>

## <a name="source-documentation"></a><span data-ttu-id="f5fab-251">Documentazione di origine</span><span class="sxs-lookup"><span data-stu-id="f5fab-251">Source documentation</span></span>

<span data-ttu-id="f5fab-252">La documentazione dell'API verrà generata automaticamente dai file di origine MRTK.</span><span class="sxs-lookup"><span data-stu-id="f5fab-252">API documentation will be generated automatically from the MRTK source files.</span></span> <span data-ttu-id="f5fab-253">Per semplificare questa operazione, è necessario che i file di origine contengano gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="f5fab-253">To facilitate this, source files are required to contain the following:</span></span>

- [<span data-ttu-id="f5fab-254">Blocchi di riepilogo Class, struct, enum</span><span class="sxs-lookup"><span data-stu-id="f5fab-254">Class, struct, enum summary blocks</span></span>](#class-struct-enum-summary-blocks)
- [<span data-ttu-id="f5fab-255">Proprietà, metodo, blocchi di riepilogo eventi</span><span class="sxs-lookup"><span data-stu-id="f5fab-255">Property, method, event summary blocks</span></span>](#property-method-event-summary-blocks)
- [<span data-ttu-id="f5fab-256">Versione e dipendenze dell'introduzione alle funzionalità</span><span class="sxs-lookup"><span data-stu-id="f5fab-256">Feature introduction version and dependencies</span></span>](#feature-introduction-version-and-dependencies)
- [<span data-ttu-id="f5fab-257">Campi serializzati</span><span class="sxs-lookup"><span data-stu-id="f5fab-257">Serialized fields</span></span>](#serialized-fields)
- [<span data-ttu-id="f5fab-258">Valori di enumerazione</span><span class="sxs-lookup"><span data-stu-id="f5fab-258">Enumeration values</span></span>](#enumeration-values)

<span data-ttu-id="f5fab-259">Oltre a quanto sopra, il codice deve essere commentato in modo da consentire la manutenzione, le correzioni di bug e la facilità di personalizzazione.</span><span class="sxs-lookup"><span data-stu-id="f5fab-259">In addition to the above, the code should be well commented to allow for maintenance, bug fixes and ease of customization.</span></span>

### <a name="class-struct-enum-summary-blocks"></a><span data-ttu-id="f5fab-260">Blocchi di riepilogo Class, struct, enum</span><span class="sxs-lookup"><span data-stu-id="f5fab-260">Class, struct, enum summary blocks</span></span>

<span data-ttu-id="f5fab-261">Se è in corso l'aggiunta di una classe, struct o enum a MRTK, è necessario descriverne lo scopo.</span><span class="sxs-lookup"><span data-stu-id="f5fab-261">If a class, struct or enum is being added to the MRTK, its purpose must be described.</span></span> <span data-ttu-id="f5fab-262">Questo è il formato di un blocco di riepilogo sopra la classe.</span><span class="sxs-lookup"><span data-stu-id="f5fab-262">This is to take the form of a summary block above the class.</span></span>

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

<span data-ttu-id="f5fab-263">Se sono presenti dipendenze a livello di classe, queste devono essere documentate in un blocco di osservazioni immediatamente sotto il riepilogo.</span><span class="sxs-lookup"><span data-stu-id="f5fab-263">If there are any class level dependencies, they should be documented in a remarks block, immediately below the summary.</span></span>

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

<span data-ttu-id="f5fab-264">Le richieste pull inviate senza riepiloghi per classi, strutture o enumerazioni non verranno approvate.</span><span class="sxs-lookup"><span data-stu-id="f5fab-264">Pull Requests submitted without summaries for classes, structures or enums will not be approved.</span></span>

### <a name="property-method-event-summary-blocks"></a><span data-ttu-id="f5fab-265">Proprietà, metodo, blocchi di riepilogo eventi</span><span class="sxs-lookup"><span data-stu-id="f5fab-265">Property, method, event summary blocks</span></span>

<span data-ttu-id="f5fab-266">Le proprietà, i metodi e gli eventi (PMEs) e i campi devono essere documentati con blocchi di riepilogo, indipendentemente dalla visibilità del codice (Public, private, protected e Internal).</span><span class="sxs-lookup"><span data-stu-id="f5fab-266">Properties, methods and events (PMEs) as well as fields are to be documented with summary blocks, regardless of code visibility (public, private, protected and internal).</span></span> <span data-ttu-id="f5fab-267">Lo strumento di generazione della documentazione è responsabile del filtraggio e della pubblicazione solo delle funzionalità pubbliche e protette.</span><span class="sxs-lookup"><span data-stu-id="f5fab-267">The documentation generation tool is responsible for filtering out and publishing only the public and protected features.</span></span>

<span data-ttu-id="f5fab-268">Nota: **non** è necessario un blocco di riepilogo per i metodi Unity (ad esempio: svegli, Start, Update).</span><span class="sxs-lookup"><span data-stu-id="f5fab-268">NOTE: A summary block is **not** required for Unity methods (ex: Awake, Start, Update).</span></span>

<span data-ttu-id="f5fab-269">Per approvare una richiesta pull, è **necessaria** la documentazione PME.</span><span class="sxs-lookup"><span data-stu-id="f5fab-269">PME documentation is **required** for a pull request to be approved.</span></span>

<span data-ttu-id="f5fab-270">Come parte di un blocco di riepilogo PME, il significato e lo scopo dei parametri e i dati restituiti sono obbligatori.</span><span class="sxs-lookup"><span data-stu-id="f5fab-270">As part of a PME summary block, the meaning and purpose of parameters and returned data is required.</span></span>

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a><span data-ttu-id="f5fab-271">Versione e dipendenze dell'introduzione alle funzionalità</span><span class="sxs-lookup"><span data-stu-id="f5fab-271">Feature introduction version and dependencies</span></span>

<span data-ttu-id="f5fab-272">Come parte della documentazione di riepilogo delle API, informazioni sulla versione di MRTK in cui è stata introdotta la funzionalità e tutte le dipendenze devono essere documentate in un blocco di note.</span><span class="sxs-lookup"><span data-stu-id="f5fab-272">As part of the API summary documentation, information regarding the MRTK version in which the feature was introduced and any dependencies should be documented in a remarks block.</span></span>

<span data-ttu-id="f5fab-273">Le dipendenze devono includere le dipendenze di estensione e/o di piattaforma.</span><span class="sxs-lookup"><span data-stu-id="f5fab-273">Dependencies should include extension and/or platform dependencies.</span></span>

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a><span data-ttu-id="f5fab-274">Campi serializzati</span><span class="sxs-lookup"><span data-stu-id="f5fab-274">Serialized fields</span></span>

<span data-ttu-id="f5fab-275">È consigliabile usare l'attributo ToolTip di Unity per fornire la documentazione di runtime per i campi di uno script nel controllo.</span><span class="sxs-lookup"><span data-stu-id="f5fab-275">It is a good practice to use Unity's tooltip attribute to provide runtime documentation for a script's fields in the inspector.</span></span>

<span data-ttu-id="f5fab-276">Per includere le opzioni di configurazione nella documentazione dell'API, è necessario che gli script *includano almeno il* contenuto della descrizione comando in un blocco di riepilogo.</span><span class="sxs-lookup"><span data-stu-id="f5fab-276">So that configuration options are included in the API documentation, scripts are required to include *at least* the tooltip contents in a summary block.</span></span>

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a><span data-ttu-id="f5fab-277">Valori di enumerazione</span><span class="sxs-lookup"><span data-stu-id="f5fab-277">Enumeration values</span></span>

<span data-ttu-id="f5fab-278">Quando si definisce l'enumerazione e, il codice deve anche documentare il significato dei valori di enumerazione usando un blocco di riepilogo.</span><span class="sxs-lookup"><span data-stu-id="f5fab-278">When defining and enumeration, code must also document the meaning of the enum values using a summary block.</span></span> <span data-ttu-id="f5fab-279">Facoltativamente, i blocchi di osservazioni possono essere utilizzati per fornire dettagli aggiuntivi per migliorare la comprensione.</span><span class="sxs-lookup"><span data-stu-id="f5fab-279">Remarks blocks can optionally be used to provide additional details to enhance understanding.</span></span>

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a><span data-ttu-id="f5fab-280">Documentazione relativa alle procedure</span><span class="sxs-lookup"><span data-stu-id="f5fab-280">How-to documentation</span></span>

<span data-ttu-id="f5fab-281">Molti utenti del Toolkit di realtà mista potrebbero non dover usare la documentazione dell'API.</span><span class="sxs-lookup"><span data-stu-id="f5fab-281">Many users of the Mixed Reality Toolkit may not need to use the API documentation.</span></span> <span data-ttu-id="f5fab-282">Questi utenti utilizzeranno gli script e i prefabbricati riutilizzabili predefiniti per creare le proprie esperienze.</span><span class="sxs-lookup"><span data-stu-id="f5fab-282">These users will take advantage of our pre-made, reusable prefabs and scripts to create their experiences.</span></span>

<span data-ttu-id="f5fab-283">Ogni area funzionale conterrà uno o più file Markdown (. MD) che descrivono a un livello piuttosto elevato, cosa viene fornito.</span><span class="sxs-lookup"><span data-stu-id="f5fab-283">Each feature area will contain one or more markdown (.md) files that describe at a fairly high level, what is provided.</span></span> <span data-ttu-id="f5fab-284">A seconda delle dimensioni e/o della complessità di una determinata area funzionale, potrebbe essere necessario aggiungere altri file, fino a una delle funzionalità disponibili.</span><span class="sxs-lookup"><span data-stu-id="f5fab-284">Depending on the size and/or complexity of a given feature area, there may be a need for additional files, up to one per feature provided.</span></span>

<span data-ttu-id="f5fab-285">Quando viene aggiunta una funzionalità (o l'utilizzo viene modificato), è necessario fornire la documentazione introduttiva.</span><span class="sxs-lookup"><span data-stu-id="f5fab-285">When a feature is added (or the usage is changed), overview documentation must be provided.</span></span>

<span data-ttu-id="f5fab-286">Come parte di questa documentazione, è necessario fornire le sezioni procedure, incluse le illustrazioni, per aiutare i clienti a una nuova funzionalità o a un concetto di Guida introduttiva.</span><span class="sxs-lookup"><span data-stu-id="f5fab-286">As part of this documentation, how-to sections, including illustrations, should be provided to assist customers new to a feature or concept in getting started.</span></span>

## <a name="design-documentation"></a><span data-ttu-id="f5fab-287">Documentazione di progettazione</span><span class="sxs-lookup"><span data-stu-id="f5fab-287">Design documentation</span></span>

<span data-ttu-id="f5fab-288">La realtà mista offre la possibilità di creare mondi completamente nuovi.</span><span class="sxs-lookup"><span data-stu-id="f5fab-288">Mixed Reality provides an opportunity to create entirely new worlds.</span></span> <span data-ttu-id="f5fab-289">Parte di questo può comportare la creazione di asset personalizzati da usare con MRTK.</span><span class="sxs-lookup"><span data-stu-id="f5fab-289">Part of this is likely to involve the creation of custom assets for use with the MRTK.</span></span> <span data-ttu-id="f5fab-290">Per rendere questa operazione più semplice per i clienti, i componenti devono fornire la documentazione di progettazione che descrive la formattazione o altri requisiti per le risorse dell'arte.</span><span class="sxs-lookup"><span data-stu-id="f5fab-290">To make this as friction free as possible for customers, components should provide design documentation describing any formatting or other requirements for art assets.</span></span>

<span data-ttu-id="f5fab-291">Di seguito sono riportati alcuni esempi in cui la documentazione di progettazione può essere utile:</span><span class="sxs-lookup"><span data-stu-id="f5fab-291">Some examples where design documentation can be helpful:</span></span>

- <span data-ttu-id="f5fab-292">Modelli di cursore</span><span class="sxs-lookup"><span data-stu-id="f5fab-292">Cursor models</span></span>
- <span data-ttu-id="f5fab-293">Visualizzazioni di mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="f5fab-293">Spatial mapping visualizations</span></span>
- <span data-ttu-id="f5fab-294">File effetto audio</span><span class="sxs-lookup"><span data-stu-id="f5fab-294">Sound effect files</span></span>

<span data-ttu-id="f5fab-295">Questo tipo di documentazione è **fortemente** consigliato e **può** essere richiesto come parte di una verifica della richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="f5fab-295">This type of documentation is **strongly** recommended, and **may** be requested as part of a pull request review.</span></span>

<span data-ttu-id="f5fab-296">Questo può essere diverso dalla raccomandazione di progettazione nel [sito Microsoft Developer](https://docs.microsoft.com/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="f5fab-296">This may or may not be different from the design recommendation on the [MS Developer site](https://docs.microsoft.com/windows/mixed-reality/design)</span></span>

## <a name="performance-notes"></a><span data-ttu-id="f5fab-297">Note sulle prestazioni</span><span class="sxs-lookup"><span data-stu-id="f5fab-297">Performance notes</span></span>

<span data-ttu-id="f5fab-298">Alcune funzionalità importanti hanno un costo in termini di prestazioni.</span><span class="sxs-lookup"><span data-stu-id="f5fab-298">Some important features come at a performance cost.</span></span> <span data-ttu-id="f5fab-299">Spesso questo codice dipende in modo molto da come sono configurate.</span><span class="sxs-lookup"><span data-stu-id="f5fab-299">Often this code will very depending how they are configured.</span></span>

<span data-ttu-id="f5fab-300">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f5fab-300">For example:</span></span>

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

<span data-ttu-id="f5fab-301">Le note sulle prestazioni sono consigliate per i componenti pesanti CPU e/o GPU e **possono** essere richieste come parte di una verifica della richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="f5fab-301">Performance notes are recommended for CPU and/or GPU heavy components and **may** be requested as part of a pull request review.</span></span> <span data-ttu-id="f5fab-302">Eventuali note sulle prestazioni applicabili devono essere incluse nell'API **e** nella documentazione di panoramica.</span><span class="sxs-lookup"><span data-stu-id="f5fab-302">Any applicable performance notes are to be included in API **and** overview documentation.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="f5fab-303">Modifiche che causano un'interruzione</span><span class="sxs-lookup"><span data-stu-id="f5fab-303">Breaking changes</span></span>

<span data-ttu-id="f5fab-304">La documentazione di modifiche di rilievo è costituita da un [file](BreakingChanges.md) di livello superiore che si collega a singoli [BreakingChanges.MD](BreakingChanges.md)di ogni area di funzionalità.</span><span class="sxs-lookup"><span data-stu-id="f5fab-304">Breaking changes documentation is to consist of a top level [file](BreakingChanges.md) which links to each feature area's individual [BreakingChanges.md](BreakingChanges.md).</span></span>

<span data-ttu-id="f5fab-305">I file [BreakingChanges.MD](BreakingChanges.md) dell'area funzionale devono contenere l'elenco di tutte le modifiche di rilievo note per una determinata versione **,** nonché la cronologia delle modifiche di rilievo apportate nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f5fab-305">The feature area [BreakingChanges.md](BreakingChanges.md) files are to contain the list of all known breaking changes for a given release **as well as** the history of breaking changes from past releases.</span></span>

<span data-ttu-id="f5fab-306">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f5fab-306">For example:</span></span>

```md
Spatial sound breaking changes

2018.07.2
* Spatialization of the imaginary effect is now required.
* Management of randomized AudioClip files requires an entropy value in the manager node.

2018.07.1
No known breaking changes

2018.07.0
...
```

<span data-ttu-id="f5fab-307">Le informazioni contenute nei file [BreakingChanges.MD](BreakingChanges.md) a livello di funzionalità verranno aggregate alle note sulla versione per ogni nuova versione di MRTK.</span><span class="sxs-lookup"><span data-stu-id="f5fab-307">The information contained within the feature level [BreakingChanges.md](BreakingChanges.md) files will be aggregated to the release notes for each new MRTK release.</span></span>

<span data-ttu-id="f5fab-308">Tutte le modifiche di rilievo che fanno parte di una modifica **devono** essere documentate come parte di una richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="f5fab-308">Any breaking changes that are part of a change **must** be documented as part of a Pull Request.</span></span>

## <a name="tools-for-editing-markdown"></a><span data-ttu-id="f5fab-309">Strumenti per la modifica di MarkDown</span><span class="sxs-lookup"><span data-stu-id="f5fab-309">Tools for editing MarkDown</span></span>

<span data-ttu-id="f5fab-310">[Visual Studio Code](https://code.visualstudio.com/) è un ottimo strumento per modificare i file Markdown che fanno parte della documentazione di MRTK.</span><span class="sxs-lookup"><span data-stu-id="f5fab-310">[Visual Studio Code](https://code.visualstudio.com/) is a great tool for editing markdown files that are part of MRTK's documentation.</span></span>

<span data-ttu-id="f5fab-311">Quando si scrive la documentazione, è consigliabile anche installare le due estensioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f5fab-311">When writing documentation, installing the following two extensions is also highly recommended:</span></span>

- <span data-ttu-id="f5fab-312">Estensione docs Markdown per Visual Studio Code: usare Alt + M per visualizzare un menu di opzioni di creazione di documenti.</span><span class="sxs-lookup"><span data-stu-id="f5fab-312">Docs Markdown Extension for Visual Studio Code - Use Alt+M to bring up a menu of docs authoring options.</span></span>

- <span data-ttu-id="f5fab-313">Controllo ortografico codice: le parole con ortografia errata verranno sottolineate; fare clic con il pulsante destro del mouse su una parola digitata in modo errato per modificarla o salvarla nel dizionario.</span><span class="sxs-lookup"><span data-stu-id="f5fab-313">Code Spell Checker - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>

<span data-ttu-id="f5fab-314">Entrambi sono inclusi nel pacchetto Microsoft Published Docs Authoring Pack.</span><span class="sxs-lookup"><span data-stu-id="f5fab-314">Both of these come packaged in the Microsoft published Docs Authoring Pack.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5fab-315">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="f5fab-315">See also</span></span>

- [<span data-ttu-id="f5fab-316">Guida alla generazione del portale della documentazione</span><span class="sxs-lookup"><span data-stu-id="f5fab-316">Documentation portal generation guide</span></span>](DevDocGuide.md)
