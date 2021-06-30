---
title: Guida alla documentazione
description: linee guida e standard della documentazione per MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 37233141bd43f27db47935574bac7630b8bea8d7
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121389"
---
# <a name="documentation-guidelines"></a><span data-ttu-id="23ae3-104">Linee guida per la documentazione</span><span class="sxs-lookup"><span data-stu-id="23ae3-104">Documentation guidelines</span></span>

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

<span data-ttu-id="23ae3-105">Questo documento illustra le linee guida e gli standard della documentazione per Mixed Reality Toolkit (MRTK).</span><span class="sxs-lookup"><span data-stu-id="23ae3-105">This document outlines the documentation guidelines and standards for the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="23ae3-106">Viene fornita un'introduzione agli aspetti tecnici della scrittura e della generazione della documentazione, per evidenziare le insidie comuni e per descrivere lo stile di scrittura consigliato.</span><span class="sxs-lookup"><span data-stu-id="23ae3-106">This provides an introduction to technical aspects of documentation writing and generation, to highlight common pitfalls, and to describe the recommended writing style.</span></span>

<span data-ttu-id="23ae3-107">La pagina stessa dovrebbe fungere da esempio, pertanto usa lo stile previsto e le funzionalità di markup più comuni della documentazione.</span><span class="sxs-lookup"><span data-stu-id="23ae3-107">The page itself is supposed to serve as an example, therefore it uses the intended style and the most common markup features of the documentation.</span></span>

- [<span data-ttu-id="23ae3-108">Origine</span><span class="sxs-lookup"><span data-stu-id="23ae3-108">Source</span></span>](#source-documentation)
- [<span data-ttu-id="23ae3-109">Procedure</span><span class="sxs-lookup"><span data-stu-id="23ae3-109">How-to</span></span>](#how-to-documentation)
- [<span data-ttu-id="23ae3-110">Progettazione</span><span class="sxs-lookup"><span data-stu-id="23ae3-110">Design</span></span>](#design-documentation)
- [<span data-ttu-id="23ae3-111">Note sulle prestazioni</span><span class="sxs-lookup"><span data-stu-id="23ae3-111">Performance notes</span></span>](#performance-notes)
- [<span data-ttu-id="23ae3-112">Modifiche di rilievo</span><span class="sxs-lookup"><span data-stu-id="23ae3-112">Breaking changes</span></span>](#breaking-changes)

---

## <a name="functionality-and-markup"></a><span data-ttu-id="23ae3-113">Funzionalità e markup</span><span class="sxs-lookup"><span data-stu-id="23ae3-113">Functionality and markup</span></span>

<span data-ttu-id="23ae3-114">In questa sezione vengono descritte le funzionalità necessarie di frequente.</span><span class="sxs-lookup"><span data-stu-id="23ae3-114">This section describes frequently needed features.</span></span> <span data-ttu-id="23ae3-115">Per vedere come funzionano, esaminare il codice sorgente della pagina.</span><span class="sxs-lookup"><span data-stu-id="23ae3-115">To see how they work, look at the source code of the page.</span></span>

1. <span data-ttu-id="23ae3-116">Elenchi numerati</span><span class="sxs-lookup"><span data-stu-id="23ae3-116">Numbered lists</span></span>
   1. <span data-ttu-id="23ae3-117">Elenchi numerati annidati con almeno 3 spazi vuoti iniziali</span><span class="sxs-lookup"><span data-stu-id="23ae3-117">Nested numbered lists with at least 3 leading blank spaces</span></span>
   1. <span data-ttu-id="23ae3-118">Il numero effettivo nel codice è irrilevante. L'analisi si occuperà di impostare il numero di elemento corretto.</span><span class="sxs-lookup"><span data-stu-id="23ae3-118">The actual number in code is irrelevant; parsing will take care of setting the correct item number.</span></span>

- <span data-ttu-id="23ae3-119">Elenchi puntati</span><span class="sxs-lookup"><span data-stu-id="23ae3-119">Bullet point lists</span></span>
  - <span data-ttu-id="23ae3-120">Elenchi di punti elenco annidati</span><span class="sxs-lookup"><span data-stu-id="23ae3-120">Nested bullet point lists</span></span>
- <span data-ttu-id="23ae3-121">Testo in **grassetto con** doppio \* \* asterisco\*\*</span><span class="sxs-lookup"><span data-stu-id="23ae3-121">Text in **bold** with \*\*double asterisk\*\*</span></span>
- <span data-ttu-id="23ae3-122">_testo in_ *corsivo* con carattere \_ di \_ sottolineatura o \* asterisco singolo\*</span><span class="sxs-lookup"><span data-stu-id="23ae3-122">_italic_ *text* with \_underscore\_ or \*single asterisk\*</span></span>
- <span data-ttu-id="23ae3-123">Testo `highlighted as code` all'interno di una \` frase usando le virgolette\`</span><span class="sxs-lookup"><span data-stu-id="23ae3-123">Text `highlighted as code` within a sentence \`using backquotes\`</span></span>
- <span data-ttu-id="23ae3-124">Collegamenti alle pagine della documentazione linee [guida per la documentazione di MRTK](documentation-guide.md)</span><span class="sxs-lookup"><span data-stu-id="23ae3-124">Links to docs pages [MRTK documentation guidelines](documentation-guide.md)</span></span>
- <span data-ttu-id="23ae3-125">Collegamenti agli [ancoraggi all'interno di una pagina;](#style) Gli ancoraggi vengono formati sostituendo gli spazi con trattini e convertendo in minuscolo</span><span class="sxs-lookup"><span data-stu-id="23ae3-125">Links to [anchors within a page](#style); anchors are formed by replacing spaces with dashes, and converting to lowercase</span></span>

<span data-ttu-id="23ae3-126">Per gli esempi di codice si usano i blocchi con tre puntini di secondo e si specifica csharp come linguaggio per \` \` \` l'evidenziazione della sintassi: </span><span class="sxs-lookup"><span data-stu-id="23ae3-126">For code samples we use the blocks with three backticks \`\`\` and specify *csharp* as the language for syntax highlighting:</span></span>

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

<span data-ttu-id="23ae3-127">Quando si cita il codice all'interno di una frase `use a single backtick` .</span><span class="sxs-lookup"><span data-stu-id="23ae3-127">When mentioning code within a sentence `use a single backtick`.</span></span>

### <a name="todos"></a><span data-ttu-id="23ae3-128">Todos</span><span class="sxs-lookup"><span data-stu-id="23ae3-128">TODOs</span></span>

<span data-ttu-id="23ae3-129">Evitare di usare gli oggetti TODO nella documentazione, perché nel corso del tempo questi todo (ad esempio gli elementi TOTOD del codice) tendono ad accumularsi e a ottenere informazioni su come devono essere aggiornati e perché andare persi.</span><span class="sxs-lookup"><span data-stu-id="23ae3-129">Avoid using TODOs in docs, as over time these TODOs (like code TODOs) tend to accumulate and information about how they should be updated and why gets lost.</span></span>

<span data-ttu-id="23ae3-130">Se è assolutamente necessario aggiungere un todo, seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="23ae3-130">If it is absolutely necessary to add a TODO, follow these steps:</span></span>

1. <span data-ttu-id="23ae3-131">Descrizione del contesto alla base del TODO in GitHub e informazioni di base sufficienti per consentire a un altro collaboratore di comprendere e quindi risolvere il problema.</span><span class="sxs-lookup"><span data-stu-id="23ae3-131">File a new issue on Github describing the context behind the TODO, and provide enough background that another contributor would be able to understand and then address the TODO.</span></span>
2. <span data-ttu-id="23ae3-132">Fare riferimento all'URL del problema nella todo nella documentazione.</span><span class="sxs-lookup"><span data-stu-id="23ae3-132">Reference the issue URL in the todo in the docs.</span></span>

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a><span data-ttu-id="23ae3-133">Sezioni evidenziate</span><span class="sxs-lookup"><span data-stu-id="23ae3-133">Highlighted sections</span></span>

<span data-ttu-id="23ae3-134">Per evidenziare punti specifici del lettore, usare *> [!NOTE]* , e per produrre gli stili *> [!WARNING]* *> [!IMPORTANT]* seguenti.</span><span class="sxs-lookup"><span data-stu-id="23ae3-134">To highlight specific points to the reader, use *> [!NOTE]* , *> [!WARNING]* , and *> [!IMPORTANT]* to produce the following styles.</span></span> <span data-ttu-id="23ae3-135">È consigliabile usare le note per i punti generali e i punti di avviso/importanti solo per casi speciali rilevanti.</span><span class="sxs-lookup"><span data-stu-id="23ae3-135">It is recommended to use notes for general points and warning/important points only for special relevant cases.</span></span>

> [!NOTE]
> <span data-ttu-id="23ae3-136">Esempio di nota</span><span class="sxs-lookup"><span data-stu-id="23ae3-136">Example of a note</span></span>

> [!WARNING]
> <span data-ttu-id="23ae3-137">Esempio di avviso</span><span class="sxs-lookup"><span data-stu-id="23ae3-137">Example of a warning</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23ae3-138">Esempio di commento importante</span><span class="sxs-lookup"><span data-stu-id="23ae3-138">Example of an important comment</span></span>

## <a name="page-layout"></a><span data-ttu-id="23ae3-139">Layout di pagina</span><span class="sxs-lookup"><span data-stu-id="23ae3-139">Page layout</span></span>

### <a name="introduction"></a><span data-ttu-id="23ae3-140">Introduzione</span><span class="sxs-lookup"><span data-stu-id="23ae3-140">Introduction</span></span>

<span data-ttu-id="23ae3-141">La parte subito dopo il titolo del capitolo principale deve essere una breve introduzione sul capitolo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-141">The part right after the main chapter title should serve as a short introduction what the chapter is about.</span></span> <span data-ttu-id="23ae3-142">Non rendere questa operazione troppo lunga, ma aggiungere titoli secondari.</span><span class="sxs-lookup"><span data-stu-id="23ae3-142">Do not make this too long, instead add sub headlines.</span></span> <span data-ttu-id="23ae3-143">Questi consentono di collegarsi alle sezioni e possono essere salvati come segnalibri.</span><span class="sxs-lookup"><span data-stu-id="23ae3-143">These allow to link to sections and can be saved as bookmarks.</span></span>

### <a name="main-body"></a><span data-ttu-id="23ae3-144">Corpo principale</span><span class="sxs-lookup"><span data-stu-id="23ae3-144">Main body</span></span>

<span data-ttu-id="23ae3-145">Usare titoli a due e tre livelli per strutturare il resto.</span><span class="sxs-lookup"><span data-stu-id="23ae3-145">Use two-level and three-level headlines to structure the rest.</span></span>

<span data-ttu-id="23ae3-146">**Mini sezioni**</span><span class="sxs-lookup"><span data-stu-id="23ae3-146">**Mini Sections**</span></span>

<span data-ttu-id="23ae3-147">Usare una riga di testo in grassetto per i blocchi che devono distinguersi. Questo potrebbe essere sostituito da titoli in quattro livelli a un certo punto.</span><span class="sxs-lookup"><span data-stu-id="23ae3-147">Use a bold line of text for blocks that should stand out. We might replace this by four-level headlines at some point.</span></span>

### <a name="see-also-section"></a><span data-ttu-id="23ae3-148">Sezione "Vedere anche"</span><span class="sxs-lookup"><span data-stu-id="23ae3-148">'See also' section</span></span>

<span data-ttu-id="23ae3-149">La maggior parte delle pagine deve terminare con un capitolo denominato *Vedere anche*.</span><span class="sxs-lookup"><span data-stu-id="23ae3-149">Most pages should end with a chapter called *See also*.</span></span> <span data-ttu-id="23ae3-150">Questo capitolo è semplicemente un elenco puntato di collegamenti a pagine correlate a questo argomento.</span><span class="sxs-lookup"><span data-stu-id="23ae3-150">This chapter is simply a bullet pointed list of links to pages related to this topic.</span></span> <span data-ttu-id="23ae3-151">Questi collegamenti possono anche essere visualizzati all'interno del testo della pagina, dove appropriato, ma questa operazione non è necessaria.</span><span class="sxs-lookup"><span data-stu-id="23ae3-151">These links may also appear within the page text where appropriate, but this is not required.</span></span> <span data-ttu-id="23ae3-152">Analogamente, il testo della pagina può contenere collegamenti a pagine non correlate all'argomento principale, che non devono essere incluse nell'elenco *Vedere* anche.</span><span class="sxs-lookup"><span data-stu-id="23ae3-152">Similarly, the page text may contain links to pages that are not related to the main topic, these should not be included in the *See also* list.</span></span> <span data-ttu-id="23ae3-153">Vedere [il capitolo "Vedere anche"](#see-also) di questa pagina come esempio per la scelta dei collegamenti.</span><span class="sxs-lookup"><span data-stu-id="23ae3-153">See [this page's ''See also'' chapter](#see-also) as an example for the choice of links.</span></span>

## <a name="table-of-contents-toc"></a><span data-ttu-id="23ae3-154">Sommario</span><span class="sxs-lookup"><span data-stu-id="23ae3-154">Table of Contents (TOC)</span></span>

<span data-ttu-id="23ae3-155">I file toc vengono usati per generare le barre di spostamento nella documentazione github.io MRTK.</span><span class="sxs-lookup"><span data-stu-id="23ae3-155">Toc files are used for generating the navigation bars in the MRTK github.io documentation.</span></span>
<span data-ttu-id="23ae3-156">Ogni volta che viene aggiunto un nuovo file di documentazione, assicurarsi che sia presente una voce per tale file in uno dei file toc.yml della cartella della documentazione.</span><span class="sxs-lookup"><span data-stu-id="23ae3-156">Whenever a new documentation file is added, make sure that there's an entry for that file in one of the toc.yml files of the documentation folder.</span></span> <span data-ttu-id="23ae3-157">Solo gli articoli elencati nei file di sommario verranno visualizzati nella navigazione della documentazione per sviluppatori. Può essere presente un file di sommario per ogni sottocartella nella cartella della documentazione che può essere collegato a qualsiasi file di sommario esistente per aggiungerlo come sottosezione alla parte corrispondente della navigazione.</span><span class="sxs-lookup"><span data-stu-id="23ae3-157">Only articles listed in the toc files will show up in the navigation of the developer docs. There can be a toc file for every subfolder in the documentation folder which can be linked into any existing toc file to add it as a subsection to the corresponding part of the navigation.</span></span>

## <a name="style"></a><span data-ttu-id="23ae3-158">Stile</span><span class="sxs-lookup"><span data-stu-id="23ae3-158">Style</span></span>

### <a name="writing-style"></a><span data-ttu-id="23ae3-159">Stile di scrittura</span><span class="sxs-lookup"><span data-stu-id="23ae3-159">Writing style</span></span>

<span data-ttu-id="23ae3-160">Regola generale: provare a sembrare **professionale.**</span><span class="sxs-lookup"><span data-stu-id="23ae3-160">General rule of thumb: Try to **sound professional**.</span></span> <span data-ttu-id="23ae3-161">Ciò significa in genere evitare un "tono colloquiale".</span><span class="sxs-lookup"><span data-stu-id="23ae3-161">That usually means to avoid a 'conversational tone'.</span></span> <span data-ttu-id="23ae3-162">Provare anche a evitare iperboli e emozionanti.</span><span class="sxs-lookup"><span data-stu-id="23ae3-162">Also try to avoid hyperbole and sensationalism.</span></span>

1. <span data-ttu-id="23ae3-163">Non tentare di essere (e troppo) insoddrò.</span><span class="sxs-lookup"><span data-stu-id="23ae3-163">Don't try to be (overly) funny.</span></span>
2. <span data-ttu-id="23ae3-164">Non scrivere mai 'I'</span><span class="sxs-lookup"><span data-stu-id="23ae3-164">Never write 'I'</span></span>
3. <span data-ttu-id="23ae3-165">Evitare "we".</span><span class="sxs-lookup"><span data-stu-id="23ae3-165">Avoid 'we'.</span></span> <span data-ttu-id="23ae3-166">Questa operazione può essere in genere riformiedata facilmente, usando invece "MRTK".</span><span class="sxs-lookup"><span data-stu-id="23ae3-166">This can usually be rephrased easily, using 'MRTK' instead.</span></span> <span data-ttu-id="23ae3-167">Esempio: "questa funzionalità è supportata" -> "MRTK supporta questa funzionalità" o "le funzionalità seguenti sono supportate...".</span><span class="sxs-lookup"><span data-stu-id="23ae3-167">Example: "we support this feature" -> "MRTK supports this feature" or "the following features are supported ...".</span></span>
4. <span data-ttu-id="23ae3-168">Analogamente, provare a evitare "you".</span><span class="sxs-lookup"><span data-stu-id="23ae3-168">Similarly, try to avoid 'you'.</span></span> <span data-ttu-id="23ae3-169">Esempio: "Con questa semplice modifica lo shader diventa configurabile!"</span><span class="sxs-lookup"><span data-stu-id="23ae3-169">Example: "With this simple change your shader becomes configurable!"</span></span> <span data-ttu-id="23ae3-170">-> "Gli shader possono essere resi configurabili con un minimo sforzo".</span><span class="sxs-lookup"><span data-stu-id="23ae3-170">-> "Shaders can be made configurable with little effort."</span></span>
5. <span data-ttu-id="23ae3-171">Non usare "frasi sloppy".</span><span class="sxs-lookup"><span data-stu-id="23ae3-171">Do not use 'sloppy phrases'.</span></span>
6. <span data-ttu-id="23ae3-172">Evitare di sembrare emozionati e non è necessario vendere nulla.</span><span class="sxs-lookup"><span data-stu-id="23ae3-172">Avoid sounding overly excited, we do not need to sell anything.</span></span>
7. <span data-ttu-id="23ae3-173">Allo stesso modo, evitare di essere troppo erre.</span><span class="sxs-lookup"><span data-stu-id="23ae3-173">Similarly, avoid being overly dramatic.</span></span> <span data-ttu-id="23ae3-174">I punti esclamativi sono raramente necessari.</span><span class="sxs-lookup"><span data-stu-id="23ae3-174">Exclamation marks are rarely needed.</span></span>

### <a name="capitalization"></a><span data-ttu-id="23ae3-175">Uso delle maiuscole</span><span class="sxs-lookup"><span data-stu-id="23ae3-175">Capitalization</span></span>

- <span data-ttu-id="23ae3-176">Usare **la distinzione tra maiuscole e minuscole per i titoli**.</span><span class="sxs-lookup"><span data-stu-id="23ae3-176">Use **Sentence case for headlines**.</span></span> <span data-ttu-id="23ae3-177">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="23ae3-177">Ie.</span></span> <span data-ttu-id="23ae3-178">in maiuscolo la prima lettera e i nomi, ma non altro.</span><span class="sxs-lookup"><span data-stu-id="23ae3-178">capitalize the first letter and names, but nothing else.</span></span>
- <span data-ttu-id="23ae3-179">Usare l'inglese normale per tutti gli altri elementi.</span><span class="sxs-lookup"><span data-stu-id="23ae3-179">Use regular English for everything else.</span></span> <span data-ttu-id="23ae3-180">Ciò significa **che le parole arbitrarie non vengono** maiuscole, anche se contengono un significato speciale in tale contesto.</span><span class="sxs-lookup"><span data-stu-id="23ae3-180">That means **do not capitalize arbitrary words**, even if they hold a special meaning in that context.</span></span> <span data-ttu-id="23ae3-181">Preferire *il testo in corsivo* per l'evidenziazione di determinate parole, vedere di [seguito.](#emphasis-and-highlighting)</span><span class="sxs-lookup"><span data-stu-id="23ae3-181">Prefer *italic text* for highlighting certain words, [see below](#emphasis-and-highlighting).</span></span>
- <span data-ttu-id="23ae3-182">Quando un collegamento è incorporato in una frase (che è il metodo preferito), il nome del capitolo standard usa sempre lettere maiuscole, interrompendo così la regola dell'assenza di maiuscole/minuscole arbitrarie all'interno del testo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-182">When a link is embedded in a sentence (which is the preferred method), the standard chapter name always uses capital letters, thus breaking the rule of no arbitrary capitalization inside text.</span></span> <span data-ttu-id="23ae3-183">Usare quindi un nome di collegamento personalizzato per correggere l'uso di maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="23ae3-183">Therefore use a custom link name to fix the capitalization.</span></span> <span data-ttu-id="23ae3-184">Di seguito è riportato, ad esempio, un collegamento alla documentazione [relativa al controllo dei](../features/ux-building-blocks/bounds-control.md) limiti.</span><span class="sxs-lookup"><span data-stu-id="23ae3-184">As an example, here is a link to the [bounds control](../features/ux-building-blocks/bounds-control.md) documentation.</span></span>
- <span data-ttu-id="23ae3-185">Non convertire in lettere maiuscole i nomi, ad *esempio Unity.*</span><span class="sxs-lookup"><span data-stu-id="23ae3-185">Do capitalize names, such as *Unity*.</span></span>
- <span data-ttu-id="23ae3-186">NON scrivere in maiuscolo l'"editor" quando si scrive *l'editor di Unity.*</span><span class="sxs-lookup"><span data-stu-id="23ae3-186">Do NOT capitalize "editor" when writing *Unity editor*.</span></span>

### <a name="emphasis-and-highlighting"></a><span data-ttu-id="23ae3-187">Enfasi ed evidenziazione</span><span class="sxs-lookup"><span data-stu-id="23ae3-187">Emphasis and highlighting</span></span>

<span data-ttu-id="23ae3-188">Esistono due modi per evidenziare o evidenziare le parole, rendendole in grassetto o corsivo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-188">There are two ways to emphasize or highlight words, making them bold or making them italic.</span></span> <span data-ttu-id="23ae3-189">L'effetto del testo  in grassetto è che il testo in grassetto viene visualizzato e pertanto può essere facilmente notato durante lo scorrimento di una parte di testo o anche semplicemente lo scorrimento su una pagina.</span><span class="sxs-lookup"><span data-stu-id="23ae3-189">The effect of bold text is that **bold text sticks out** and therefore can easily be noticed while skimming a piece of text or even just scrolling over a page.</span></span> <span data-ttu-id="23ae3-190">Il grassetto è ideale per evidenziare le frasi che gli utenti devono ricordare.</span><span class="sxs-lookup"><span data-stu-id="23ae3-190">Bold is great to highlight phrases that people should remember.</span></span> <span data-ttu-id="23ae3-191">Tuttavia, **usare raramente il testo in grassetto** perché in genere è distrazione.</span><span class="sxs-lookup"><span data-stu-id="23ae3-191">However, **use bold text rarely**, because it is generally distracting.</span></span>

<span data-ttu-id="23ae3-192">Spesso si vuole "raggruppare" un elemento che appartiene logicamente o evidenziare un termine specifico, perché ha un significato speciale.</span><span class="sxs-lookup"><span data-stu-id="23ae3-192">Often one wants to either 'group' something that belongs logically together or highlight a specific term, because it has a special meaning.</span></span> <span data-ttu-id="23ae3-193">Non è necessario che tali elementi si distinguono dal testo complessivo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-193">Such things do not need to stand out of the overall text.</span></span> <span data-ttu-id="23ae3-194">Usare il testo in corsivo *come metodo leggero per* evidenziare un elemento.</span><span class="sxs-lookup"><span data-stu-id="23ae3-194">Use italic text as a *lightweight method* to highlight something.</span></span>

<span data-ttu-id="23ae3-195">Analogamente, quando un nome file, un percorso o una voce di menu viene menzionato nel testo, preferisce renderlo corsivo per raggrupparlo in modo logico, senza distrarlo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-195">Similarly, when a filename, a path or a menu-entry is mentioned in text, prefer to make it italic to logically group it, without being distracting.</span></span>

<span data-ttu-id="23ae3-196">In generale, provare a evitare **l'evidenziazione del testo non necessaria.**</span><span class="sxs-lookup"><span data-stu-id="23ae3-196">In general, try to **avoid unnecessary text highlighting**.</span></span> <span data-ttu-id="23ae3-197">I termini speciali possono essere evidenziati una sola volta per rendere il lettore consapevole, non ripetere tale evidenziazione in tutto il testo, quando non serve più a nessuno scopo e si distrae solo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-197">Special terms can be highlighted once to make the reader aware, do not repeat such highlighting throughout the text, when it serves no purpose anymore and only distracts.</span></span>

### <a name="mentioning-menu-entries"></a><span data-ttu-id="23ae3-198">Menzione delle voci di menu</span><span class="sxs-lookup"><span data-stu-id="23ae3-198">Mentioning menu entries</span></span>

<span data-ttu-id="23ae3-199">Quando si cita una voce di menu su cui un utente deve fare clic, la convenzione corrente è: *Project > Files > Create > Leaf*</span><span class="sxs-lookup"><span data-stu-id="23ae3-199">When mentioning a menu entry that a user should click, the current convention is: *Project > Files > Create > Leaf*</span></span>

### <a name="links"></a><span data-ttu-id="23ae3-200">Collegamenti</span><span class="sxs-lookup"><span data-stu-id="23ae3-200">Links</span></span>

<span data-ttu-id="23ae3-201">Inserire il maggior numero possibile di collegamenti utili ad altre pagine, ma ogni collegamento viene inserito una sola volta.</span><span class="sxs-lookup"><span data-stu-id="23ae3-201">Insert as many useful links to other pages as possible, but each link only once.</span></span> <span data-ttu-id="23ae3-202">Si supponga che un lettore fa clic su ogni collegamento nella pagina e pensi a quanto sarebbe fastidioso, se la stessa pagina si apre 20 volte.</span><span class="sxs-lookup"><span data-stu-id="23ae3-202">Assume a reader clicks on every link in the page, and think about how annoying it would be, if the same page opens 20 times.</span></span>

<span data-ttu-id="23ae3-203">Preferisce collegamenti incorporati in una frase:</span><span class="sxs-lookup"><span data-stu-id="23ae3-203">Prefer links embedded in a sentence:</span></span>

- <span data-ttu-id="23ae3-204">BAD: le linee guida sono utili.</span><span class="sxs-lookup"><span data-stu-id="23ae3-204">BAD: Guidelines are useful.</span></span> <span data-ttu-id="23ae3-205">Per [informazioni dettagliate,](../contributing/documentation-guide.md) vedere questo capitolo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-205">See [this chapter](../contributing/documentation-guide.md) for details.</span></span>
- <span data-ttu-id="23ae3-206">BUONA: [le linee guida](documentation-guide.md) sono utili.</span><span class="sxs-lookup"><span data-stu-id="23ae3-206">GOOD: [Guidelines](documentation-guide.md) are useful.</span></span>

<span data-ttu-id="23ae3-207">Evitare collegamenti esterni, che possono diventare obsoleti o contenere contenuti protetti da copyright.</span><span class="sxs-lookup"><span data-stu-id="23ae3-207">Avoid external links, they can become outdated or contain copyrighted content.</span></span>

<span data-ttu-id="23ae3-208">Quando si aggiunge un collegamento, valutare se deve essere elencato anche nella [sezione Vedere](#see-also) anche.</span><span class="sxs-lookup"><span data-stu-id="23ae3-208">When adding a link, consider whether it should also be listed in the [See also](#see-also) section.</span></span> <span data-ttu-id="23ae3-209">Analogamente, controllare se è necessario aggiungere un collegamento alla nuova pagina alla pagina collegata.</span><span class="sxs-lookup"><span data-stu-id="23ae3-209">Similarly, check whether a link to the new page should be added to the linked-to page.</span></span>

### <a name="images--screenshots"></a><span data-ttu-id="23ae3-210">Immagini/screenshot</span><span class="sxs-lookup"><span data-stu-id="23ae3-210">Images / screenshots</span></span>

<span data-ttu-id="23ae3-211">**Usare gli screenshot con moderamento.**</span><span class="sxs-lookup"><span data-stu-id="23ae3-211">**Use screenshots sparingly.**</span></span> <span data-ttu-id="23ae3-212">La gestione delle immagini nella documentazione è molto lavoro, le piccole modifiche all'interfaccia utente possono rendere obsoleti molti screenshot.</span><span class="sxs-lookup"><span data-stu-id="23ae3-212">Maintaining images in documentation is a lot of work, small UI changes can make a lot of screenshots outdated.</span></span> <span data-ttu-id="23ae3-213">Le regole seguenti ridurranno le attività di manutenzione:</span><span class="sxs-lookup"><span data-stu-id="23ae3-213">The following rules will reduce maintenance effort:</span></span>

1. <span data-ttu-id="23ae3-214">Non usare screenshot per elementi che possono essere descritti in testo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-214">Do not use screenshots for things that can be described in text.</span></span> <span data-ttu-id="23ae3-215">In particolare, **non creare mai screenshot di una griglia delle** proprietà al solo scopo di visualizzare i nomi e i valori delle proprietà.</span><span class="sxs-lookup"><span data-stu-id="23ae3-215">Especially, **never screenshot a property grid** for the sole purpose of showing property names and values.</span></span>
2. <span data-ttu-id="23ae3-216">Non includere elementi in uno screenshot irrilevanti per quanto visualizzato.</span><span class="sxs-lookup"><span data-stu-id="23ae3-216">Do not include things in a screenshot that are irrelevant to what is shown.</span></span> <span data-ttu-id="23ae3-217">Ad esempio, quando viene visualizzato un effetto di rendering, creare uno screenshot del viewport, ma escludere qualsiasi interfaccia utente che lo circonda.</span><span class="sxs-lookup"><span data-stu-id="23ae3-217">For instance, when a rendering effect is shown, make a screenshot of the viewport, but exclude any UI around it.</span></span> <span data-ttu-id="23ae3-218">Mostrando un'interfaccia utente, provare a spostare le finestre in modo che solo la parte importante sia presente nell'immagine.</span><span class="sxs-lookup"><span data-stu-id="23ae3-218">Showing some UI, try to move windows around such that only that important part is in the image.</span></span>
3. <span data-ttu-id="23ae3-219">Quando si include l'interfaccia utente dello screenshot, vengono mostrate solo le parti importanti.</span><span class="sxs-lookup"><span data-stu-id="23ae3-219">When including screenshot UI, only show the important parts.</span></span> <span data-ttu-id="23ae3-220">Ad esempio, quando si parla di pulsanti in una barra degli strumenti, creare una piccola immagine che mostra i pulsanti importanti della barra degli strumenti, ma escludere tutto ciò che la circonda.</span><span class="sxs-lookup"><span data-stu-id="23ae3-220">For example, when talking about buttons in a toolbar, make a small image that shows the important toolbar buttons, but exclude everything around it.</span></span>
4. <span data-ttu-id="23ae3-221">Usare solo immagini facili da riprodurre.</span><span class="sxs-lookup"><span data-stu-id="23ae3-221">Only use images that are easy to reproduce.</span></span> <span data-ttu-id="23ae3-222">Ciò significa che non disegnare marcatori o evidenziazioni negli screenshot.</span><span class="sxs-lookup"><span data-stu-id="23ae3-222">That means do not paint markers or highlights into screenshots.</span></span> <span data-ttu-id="23ae3-223">In primo luogo, non esistono regole coerenti sull'aspetto che dovrebbero avere.</span><span class="sxs-lookup"><span data-stu-id="23ae3-223">First, there are no consistent rules how these should look, anyway.</span></span> <span data-ttu-id="23ae3-224">In secondo momento, riprodurre uno screenshot di questo tipo è un'attività aggiuntiva.</span><span class="sxs-lookup"><span data-stu-id="23ae3-224">Second, reproducing such a screenshot is additional effort.</span></span> <span data-ttu-id="23ae3-225">Descrivere invece le parti importanti del testo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-225">Instead, describe the important parts in text.</span></span> <span data-ttu-id="23ae3-226">Esistono eccezioni a questa regola, ma sono rare.</span><span class="sxs-lookup"><span data-stu-id="23ae3-226">There are exceptions to this rule, but they are rare.</span></span>
5. <span data-ttu-id="23ae3-227">Ovviamente, è molto più necessario ricreare un'immagine GIF animata.</span><span class="sxs-lookup"><span data-stu-id="23ae3-227">Obviously, it is much more effort to recreate an animated GIF.</span></span> <span data-ttu-id="23ae3-228">Si prevede di essere responsabile di ricrearla fino alla fine del tempo o di aspettarsi che gli utenti lo scartino, se non vogliono dedicare tale tempo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-228">Expect to be responsible to recreate it until the end of time, or expect people to throw it out, if they don't want to spend that time.</span></span>
6. <span data-ttu-id="23ae3-229">Mantenere basso il numero di immagini in un articolo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-229">Keep the number of images in an article low.</span></span> <span data-ttu-id="23ae3-230">Spesso un metodo efficace è creare uno screenshot complessivo di uno strumento, che mostra tutti gli elementi e quindi descrivere il resto nel testo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-230">Often a good method is to make one overall screenshot of some tool, that shows everything, and then describe the rest in text.</span></span> <span data-ttu-id="23ae3-231">In questo modo è facile sostituire lo screenshot quando necessario.</span><span class="sxs-lookup"><span data-stu-id="23ae3-231">This makes it easy to replace the screenshot when necessary.</span></span>

<span data-ttu-id="23ae3-232">Altri aspetti:</span><span class="sxs-lookup"><span data-stu-id="23ae3-232">Some other aspects:</span></span>

- <span data-ttu-id="23ae3-233">L'interfaccia utente dell'editor per gli screenshot deve usare l'editor del tema grigio chiaro perché non tutti gli utenti hanno accesso al tema scuro e si desidera mantenere gli elementi il più coerenti possibile.</span><span class="sxs-lookup"><span data-stu-id="23ae3-233">The editor UI for screenshots should use light gray theme editor as not all users have access to the dark theme and we'd like to keep things as consistent as possible.</span></span>
- <span data-ttu-id="23ae3-234">La larghezza predefinita dell'immagine è 500 pixel, perché viene visualizzata bene nella maggior parte dei monitor.</span><span class="sxs-lookup"><span data-stu-id="23ae3-234">Default image width is 500 pixels, as this displays well on most monitors.</span></span> <span data-ttu-id="23ae3-235">Provare a non deviare troppo da esso.</span><span class="sxs-lookup"><span data-stu-id="23ae3-235">Try not to deviate too much from it.</span></span> <span data-ttu-id="23ae3-236">La larghezza massima deve essere di 800 pixel.</span><span class="sxs-lookup"><span data-stu-id="23ae3-236">800 pixels width should be the maximum.</span></span>
- <span data-ttu-id="23ae3-237">Usare i PNG per gli screenshot dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="23ae3-237">Use PNGs for screenshots of UI.</span></span>
- <span data-ttu-id="23ae3-238">Usare PNG o JPG per gli screenshot del viewport 3D.</span><span class="sxs-lookup"><span data-stu-id="23ae3-238">Use PNGs or JPGs for 3D viewport screenshots.</span></span> <span data-ttu-id="23ae3-239">Preferisce la qualità rispetto al rapporto di compressione.</span><span class="sxs-lookup"><span data-stu-id="23ae3-239">Prefer quality over compression ratio.</span></span>

### <a name="list-of-component-properties"></a><span data-ttu-id="23ae3-240">Elenco delle proprietà del componente</span><span class="sxs-lookup"><span data-stu-id="23ae3-240">List of component properties</span></span>

<span data-ttu-id="23ae3-241">Quando si documenta un elenco di proprietà, usare il testo in grassetto per evidenziare il nome della proprietà, quindi le interruzioni di riga e il testo normale per descriverle.</span><span class="sxs-lookup"><span data-stu-id="23ae3-241">When documenting a list of properties, use bold text to highlight the property name, then line breaks and regular text to describe them.</span></span> <span data-ttu-id="23ae3-242">Non usare sottosezioni o elenchi puntati.</span><span class="sxs-lookup"><span data-stu-id="23ae3-242">Do not use sub-chapters or bullet point lists.</span></span>

<span data-ttu-id="23ae3-243">Non dimenticare inoltre di completare tutte le frasi con un punto.</span><span class="sxs-lookup"><span data-stu-id="23ae3-243">Also, don't forget to finish all sentences with a period.</span></span>

## <a name="page-completion-checklist"></a><span data-ttu-id="23ae3-244">Elenco di controllo per il completamento della pagina</span><span class="sxs-lookup"><span data-stu-id="23ae3-244">Page completion checklist</span></span>

1. <span data-ttu-id="23ae3-245">Assicurarsi che siano state seguite le linee guida di questo documento.</span><span class="sxs-lookup"><span data-stu-id="23ae3-245">Ensure that this document's guidelines were followed.</span></span>
1. <span data-ttu-id="23ae3-246">Esplorare la struttura del documento e verificare se il nuovo documento può essere menzionato nella [sezione](#see-also) Vedere anche di altre pagine.</span><span class="sxs-lookup"><span data-stu-id="23ae3-246">Browse the document structure and see if the new document could be mentioned under the [See also](#see-also) section of other pages.</span></span>
1. <span data-ttu-id="23ae3-247">Se disponibile, fare in modo che qualcuno con conoscenza dell'argomento leggi la pagina per la correttezza tecnica.</span><span class="sxs-lookup"><span data-stu-id="23ae3-247">If available, have someone with knowledge of the topic proof-read the page for technical correctness.</span></span>
1. <span data-ttu-id="23ae3-248">Fare in modo che qualcuno letta la prova della pagina per lo stile e la formattazione.</span><span class="sxs-lookup"><span data-stu-id="23ae3-248">Have someone proof-read the page for style and formatting.</span></span> <span data-ttu-id="23ae3-249">Può trattarsi di una persona che non ha familiarità con l'argomento, che è anche una buona idea per ottenere commenti e suggerimenti su quanto sia comprensibile la documentazione.</span><span class="sxs-lookup"><span data-stu-id="23ae3-249">This can be someone unfamiliar with the topic, which is also a good idea to get feedback about how understandable the documentation is.</span></span>

## <a name="source-documentation"></a><span data-ttu-id="23ae3-250">Documentazione di origine</span><span class="sxs-lookup"><span data-stu-id="23ae3-250">Source documentation</span></span>

<span data-ttu-id="23ae3-251">La documentazione dell'API verrà generata automaticamente dai file di origine di MRTK.</span><span class="sxs-lookup"><span data-stu-id="23ae3-251">API documentation will be generated automatically from the MRTK source files.</span></span> <span data-ttu-id="23ae3-252">Per semplificare questa operazione, i file di origine devono contenere quanto segue:</span><span class="sxs-lookup"><span data-stu-id="23ae3-252">To facilitate this, source files are required to contain the following:</span></span>

- [<span data-ttu-id="23ae3-253">Blocchi di riepilogo di classi, struct e enumerazioni</span><span class="sxs-lookup"><span data-stu-id="23ae3-253">Class, struct, enum summary blocks</span></span>](#class-struct-enum-summary-blocks)
- [<span data-ttu-id="23ae3-254">Blocchi di riepilogo di proprietà, metodi e eventi</span><span class="sxs-lookup"><span data-stu-id="23ae3-254">Property, method, event summary blocks</span></span>](#property-method-event-summary-blocks)
- [<span data-ttu-id="23ae3-255">Versione e dipendenze dell'introduzione alle funzionalità</span><span class="sxs-lookup"><span data-stu-id="23ae3-255">Feature introduction version and dependencies</span></span>](#feature-introduction-version-and-dependencies)
- [<span data-ttu-id="23ae3-256">Campi serializzati</span><span class="sxs-lookup"><span data-stu-id="23ae3-256">Serialized fields</span></span>](#serialized-fields)
- [<span data-ttu-id="23ae3-257">Valori di enumerazione</span><span class="sxs-lookup"><span data-stu-id="23ae3-257">Enumeration values</span></span>](#enumeration-values)

<span data-ttu-id="23ae3-258">Oltre a quanto sopra, il codice deve essere ben commentato per consentire la manutenzione, le correzioni di bug e la facilità di personalizzazione.</span><span class="sxs-lookup"><span data-stu-id="23ae3-258">In addition to the above, the code should be well commented to allow for maintenance, bug fixes and ease of customization.</span></span>

### <a name="class-struct-enum-summary-blocks"></a><span data-ttu-id="23ae3-259">Blocchi di riepilogo di classi, struct e enumerazioni</span><span class="sxs-lookup"><span data-stu-id="23ae3-259">Class, struct, enum summary blocks</span></span>

<span data-ttu-id="23ae3-260">Se una classe, uno struct o un'enumerazione viene aggiunto a MRTK, è necessario descriverne lo scopo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-260">If a class, struct or enum is being added to the MRTK, its purpose must be described.</span></span> <span data-ttu-id="23ae3-261">Questa operazione deve assumere la forma di un blocco di riepilogo sopra la classe .</span><span class="sxs-lookup"><span data-stu-id="23ae3-261">This is to take the form of a summary block above the class.</span></span>

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

<span data-ttu-id="23ae3-262">Se sono presenti dipendenze a livello di classe, devono essere documentate in un blocco note, immediatamente sotto il riepilogo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-262">If there are any class level dependencies, they should be documented in a remarks block, immediately below the summary.</span></span>

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

<span data-ttu-id="23ae3-263">Le richieste pull inviate senza riepiloghi per classi, strutture o enumerazioni non verranno approvate.</span><span class="sxs-lookup"><span data-stu-id="23ae3-263">Pull Requests submitted without summaries for classes, structures or enums will not be approved.</span></span>

### <a name="property-method-event-summary-blocks"></a><span data-ttu-id="23ae3-264">Blocchi di riepilogo di proprietà, metodi e eventi</span><span class="sxs-lookup"><span data-stu-id="23ae3-264">Property, method, event summary blocks</span></span>

<span data-ttu-id="23ae3-265">Le proprietà, i metodi e gli eventi (PME) e i campi devono essere documentati con blocchi di riepilogo, indipendentemente dalla visibilità del codice (pubblica, privata, protetta e interna).</span><span class="sxs-lookup"><span data-stu-id="23ae3-265">Properties, methods and events (PMEs) as well as fields are to be documented with summary blocks, regardless of code visibility (public, private, protected and internal).</span></span> <span data-ttu-id="23ae3-266">Lo strumento di generazione della documentazione è responsabile dell'applicazione di filtri e della pubblicazione solo delle funzionalità pubbliche e protette.</span><span class="sxs-lookup"><span data-stu-id="23ae3-266">The documentation generation tool is responsible for filtering out and publishing only the public and protected features.</span></span>

<span data-ttu-id="23ae3-267">NOTA: non è necessario un blocco **di** riepilogo per i metodi Unity (ad esempio: Attivo, Avvia, Aggiorna).</span><span class="sxs-lookup"><span data-stu-id="23ae3-267">NOTE: A summary block is **not** required for Unity methods (ex: Awake, Start, Update).</span></span>

<span data-ttu-id="23ae3-268">La documentazione pmE è **necessaria** per l'approvazione di una richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="23ae3-268">PME documentation is **required** for a pull request to be approved.</span></span>

<span data-ttu-id="23ae3-269">Come parte di un blocco di riepilogo PME, sono necessari il significato e lo scopo dei parametri e dei dati restituiti.</span><span class="sxs-lookup"><span data-stu-id="23ae3-269">As part of a PME summary block, the meaning and purpose of parameters and returned data is required.</span></span>

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a><span data-ttu-id="23ae3-270">Versione e dipendenze dell'introduzione alle funzionalità</span><span class="sxs-lookup"><span data-stu-id="23ae3-270">Feature introduction version and dependencies</span></span>

<span data-ttu-id="23ae3-271">Come parte della documentazione di riepilogo dell'API, le informazioni relative alla versione di MRTK in cui è stata introdotta la funzionalità ed eventuali dipendenze devono essere documentate in un blocco note.</span><span class="sxs-lookup"><span data-stu-id="23ae3-271">As part of the API summary documentation, information regarding the MRTK version in which the feature was introduced and any dependencies should be documented in a remarks block.</span></span>

<span data-ttu-id="23ae3-272">Le dipendenze devono includere le dipendenze di estensione e/o piattaforma.</span><span class="sxs-lookup"><span data-stu-id="23ae3-272">Dependencies should include extension and/or platform dependencies.</span></span>

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a><span data-ttu-id="23ae3-273">Campi serializzati</span><span class="sxs-lookup"><span data-stu-id="23ae3-273">Serialized fields</span></span>

<span data-ttu-id="23ae3-274">È consigliabile usare l'attributo tooltip di Unity per fornire la documentazione di runtime per i campi di uno script nel controllo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-274">It is a good practice to use Unity's tooltip attribute to provide runtime documentation for a script's fields in the inspector.</span></span>

<span data-ttu-id="23ae3-275">In modo che le opzioni di configurazione siano  incluse nella documentazione dell'API, gli script devono includere almeno il contenuto della descrizione comando in un blocco di riepilogo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-275">So that configuration options are included in the API documentation, scripts are required to include *at least* the tooltip contents in a summary block.</span></span>

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a><span data-ttu-id="23ae3-276">Valori di enumerazione</span><span class="sxs-lookup"><span data-stu-id="23ae3-276">Enumeration values</span></span>

<span data-ttu-id="23ae3-277">Durante la definizione e l'enumerazione, il codice deve documentare anche il significato dei valori di enumerazione usando un blocco di riepilogo.</span><span class="sxs-lookup"><span data-stu-id="23ae3-277">When defining and enumeration, code must also document the meaning of the enum values using a summary block.</span></span> <span data-ttu-id="23ae3-278">Facoltativamente, i blocchi note possono essere usati per fornire dettagli aggiuntivi per migliorare la comprensione.</span><span class="sxs-lookup"><span data-stu-id="23ae3-278">Remarks blocks can optionally be used to provide additional details to enhance understanding.</span></span>

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a><span data-ttu-id="23ae3-279">Documentazione delle procedura</span><span class="sxs-lookup"><span data-stu-id="23ae3-279">How-to documentation</span></span>

<span data-ttu-id="23ae3-280">Molti utenti di Mixed Reality Toolkit potrebbero non dover usare la documentazione dell'API.</span><span class="sxs-lookup"><span data-stu-id="23ae3-280">Many users of the Mixed Reality Toolkit may not need to use the API documentation.</span></span> <span data-ttu-id="23ae3-281">Questi utenti sfufruiranno dei prefab e degli script predefiniti e riutilizzabili per creare le proprie esperienze.</span><span class="sxs-lookup"><span data-stu-id="23ae3-281">These users will take advantage of our pre-made, reusable prefabs and scripts to create their experiences.</span></span>

<span data-ttu-id="23ae3-282">Ogni area di funzionalità conterrà uno o più file markdown (md) che descrivono a un livello piuttosto elevato, ciò che viene fornito.</span><span class="sxs-lookup"><span data-stu-id="23ae3-282">Each feature area will contain one or more markdown (.md) files that describe at a fairly high level, what is provided.</span></span> <span data-ttu-id="23ae3-283">A seconda delle dimensioni e/o della complessità di una determinata area di funzionalità, potrebbe essere necessario disporre di file aggiuntivi, fino a uno per ogni funzionalità fornita.</span><span class="sxs-lookup"><span data-stu-id="23ae3-283">Depending on the size and/or complexity of a given feature area, there may be a need for additional files, up to one per feature provided.</span></span>

<span data-ttu-id="23ae3-284">Quando viene aggiunta una funzionalità (o viene modificato l'utilizzo), è necessario fornire la documentazione di panoramica.</span><span class="sxs-lookup"><span data-stu-id="23ae3-284">When a feature is added (or the usage is changed), overview documentation must be provided.</span></span>

<span data-ttu-id="23ae3-285">Come parte di questa documentazione, è consigliabile includere sezioni di procedura, incluse le illustrazioni, per assistere i clienti che non hanno mai iniziato a usare una funzionalità o un concetto.</span><span class="sxs-lookup"><span data-stu-id="23ae3-285">As part of this documentation, how-to sections, including illustrations, should be provided to assist customers new to a feature or concept in getting started.</span></span>

## <a name="design-documentation"></a><span data-ttu-id="23ae3-286">Documentazione di progettazione</span><span class="sxs-lookup"><span data-stu-id="23ae3-286">Design documentation</span></span>

<span data-ttu-id="23ae3-287">La realtà mista offre l'opportunità di creare ambienti completamente nuovi.</span><span class="sxs-lookup"><span data-stu-id="23ae3-287">Mixed Reality provides an opportunity to create entirely new worlds.</span></span> <span data-ttu-id="23ae3-288">Parte di questo processo implica probabilmente la creazione di asset personalizzati da usare con MRTK.</span><span class="sxs-lookup"><span data-stu-id="23ae3-288">Part of this is likely to involve the creation of custom assets for use with the MRTK.</span></span> <span data-ttu-id="23ae3-289">Per rendere questa operazione il più possibile gratuita per i clienti, i componenti devono fornire la documentazione di progettazione che descrive qualsiasi formattazione o altri requisiti per gli asset di grafica.</span><span class="sxs-lookup"><span data-stu-id="23ae3-289">To make this as friction free as possible for customers, components should provide design documentation describing any formatting or other requirements for art assets.</span></span>

<span data-ttu-id="23ae3-290">Alcuni esempi in cui la documentazione di progettazione può essere utile:</span><span class="sxs-lookup"><span data-stu-id="23ae3-290">Some examples where design documentation can be helpful:</span></span>

- <span data-ttu-id="23ae3-291">Modelli di cursore</span><span class="sxs-lookup"><span data-stu-id="23ae3-291">Cursor models</span></span>
- <span data-ttu-id="23ae3-292">Visualizzazioni di mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="23ae3-292">Spatial mapping visualizations</span></span>
- <span data-ttu-id="23ae3-293">File dell'effetto sonoro</span><span class="sxs-lookup"><span data-stu-id="23ae3-293">Sound effect files</span></span>

<span data-ttu-id="23ae3-294">Questo tipo di documentazione è **fortemente** consigliato **e** può essere richiesto come parte di una revisione della richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="23ae3-294">This type of documentation is **strongly** recommended, and **may** be requested as part of a pull request review.</span></span>

<span data-ttu-id="23ae3-295">Questo può essere diverso o meno dalla raccomandazione di progettazione nel [sito ms developer](/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="23ae3-295">This may or may not be different from the design recommendation on the [MS Developer site](/windows/mixed-reality/design)</span></span>

## <a name="performance-notes"></a><span data-ttu-id="23ae3-296">Note sulle prestazioni</span><span class="sxs-lookup"><span data-stu-id="23ae3-296">Performance notes</span></span>

<span data-ttu-id="23ae3-297">Alcune funzionalità importanti hanno un costo in termini di prestazioni.</span><span class="sxs-lookup"><span data-stu-id="23ae3-297">Some important features come at a performance cost.</span></span> <span data-ttu-id="23ae3-298">Spesso questo codice dipende molto dalla modalità di configurazione.</span><span class="sxs-lookup"><span data-stu-id="23ae3-298">Often this code will very depending how they are configured.</span></span>

<span data-ttu-id="23ae3-299">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="23ae3-299">For example:</span></span>

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

<span data-ttu-id="23ae3-300">Le note sulle prestazioni sono consigliate per i componenti con utilizzo elevato della CPU e/o della GPU e possono **essere** richieste come parte di una revisione della richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="23ae3-300">Performance notes are recommended for CPU and/or GPU heavy components and **may** be requested as part of a pull request review.</span></span> <span data-ttu-id="23ae3-301">Eventuali note sulle prestazioni applicabili devono essere incluse nella documentazione di API **e** panoramica.</span><span class="sxs-lookup"><span data-stu-id="23ae3-301">Any applicable performance notes are to be included in API **and** overview documentation.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="23ae3-302">Modifiche che causano un'interruzione</span><span class="sxs-lookup"><span data-stu-id="23ae3-302">Breaking changes</span></span>

<span data-ttu-id="23ae3-303">La documentazione relativa alle modifiche di rilievo è costituita da un [file](../contributing/breaking-changes.md) di primo livello che si collega alle singole aree di funzionalità breaking-changes.md.</span><span class="sxs-lookup"><span data-stu-id="23ae3-303">Breaking changes documentation is to consist of a top level [file](../contributing/breaking-changes.md) which links to each feature area's individual breaking-changes.md.</span></span>

<span data-ttu-id="23ae3-304">L'area breaking-changes.md file devono contenere l'elenco di tutte le  modifiche di rilievo note per una determinata versione, nonché la cronologia delle modifiche di rilievo rispetto alle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="23ae3-304">The feature area breaking-changes.md files are to contain the list of all known breaking changes for a given release **as well as** the history of breaking changes from past releases.</span></span>

<span data-ttu-id="23ae3-305">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="23ae3-305">For example:</span></span>

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

<span data-ttu-id="23ae3-306">Le informazioni contenute nel livello di breaking-changes.md file verranno aggregate alle note sulla versione per ogni nuova versione di MRTK.</span><span class="sxs-lookup"><span data-stu-id="23ae3-306">The information contained within the feature level breaking-changes.md files will be aggregated to the release notes for each new MRTK release.</span></span>

<span data-ttu-id="23ae3-307">Tutte le modifiche di rilievo che fanno parte di una modifica **devono** essere documentate come parte di una richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="23ae3-307">Any breaking changes that are part of a change **must** be documented as part of a Pull Request.</span></span>

## <a name="tools-for-editing-markdown"></a><span data-ttu-id="23ae3-308">Strumenti per la modifica di MarkDown</span><span class="sxs-lookup"><span data-stu-id="23ae3-308">Tools for editing MarkDown</span></span>

<span data-ttu-id="23ae3-309">[Visual Studio Code](https://code.visualstudio.com/) è un ottimo strumento per la modifica dei file markdown che fanno parte della documentazione di MRTK.</span><span class="sxs-lookup"><span data-stu-id="23ae3-309">[Visual Studio Code](https://code.visualstudio.com/) is a great tool for editing markdown files that are part of MRTK's documentation.</span></span>

<span data-ttu-id="23ae3-310">Quando si scrive la documentazione, è consigliabile installare anche le due estensioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="23ae3-310">When writing documentation, installing the following two extensions is also highly recommended:</span></span>

- <span data-ttu-id="23ae3-311">Estensione Docs Markdown per Visual Studio Code: usare ALT+M per visualizzare un menu di opzioni di creazione della documentazione.</span><span class="sxs-lookup"><span data-stu-id="23ae3-311">Docs Markdown Extension for Visual Studio Code - Use Alt+M to bring up a menu of docs authoring options.</span></span>

- <span data-ttu-id="23ae3-312">Controllo ortografico del codice: le parole con errori di ortografia verranno sottolineate. Fare clic con il pulsante destro del mouse su una parola con errori di ortografia per modificarla o salvarla nel dizionario.</span><span class="sxs-lookup"><span data-stu-id="23ae3-312">Code Spell Checker - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>

<span data-ttu-id="23ae3-313">Entrambi i pacchetti sono in pacchetto in Docs Authoring Pack pubblicato da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="23ae3-313">Both of these come packaged in the Microsoft published Docs Authoring Pack.</span></span>

## <a name="see-also"></a><span data-ttu-id="23ae3-314">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="23ae3-314">See also</span></span> 

* [<span data-ttu-id="23ae3-315">Collegamento di esempio</span><span class="sxs-lookup"><span data-stu-id="23ae3-315">Example link</span></span>](https://www.google.com)