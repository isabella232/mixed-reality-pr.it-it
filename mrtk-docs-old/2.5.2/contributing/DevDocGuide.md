---
title: DevDocGuide
description: Portale per sviluppatori gudie per MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, GitHub
ms.openlocfilehash: e752508bf111169c91a2d7d96e1adaace86a64e7
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783718"
---
# <a name="developer-portal-generation-guide"></a><span data-ttu-id="ccaa2-104">Guida alla generazione del portale per sviluppatori</span><span class="sxs-lookup"><span data-stu-id="ccaa2-104">Developer portal generation guide</span></span>

<span data-ttu-id="ccaa2-105">MRTK USA [docfx](https://dotnet.github.io/docfx/index.html) per generare la documentazione HTML dai commenti a barra tripla nei file di codice e MD nel repository MRTK.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-105">MRTK uses [docfx](https://dotnet.github.io/docfx/index.html) to generate html documentation out of triple slash comments in code and .md files in the MRTK repository.</span></span> <span data-ttu-id="ccaa2-106">La generazione della documentazione di Docfx viene attivata automaticamente da CI nelle richieste pull completate nel ramo mrtk_development.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-106">Docfx documentation generation is automatically triggered by CI on completed PRs in the mrtk_development branch.</span></span>
<span data-ttu-id="ccaa2-107">Lo stato corrente della documentazione per gli sviluppatori è disponibile nella [pagina MRTK github.io](https://microsoft.github.io/MixedRealityToolkit-Unity/)</span><span class="sxs-lookup"><span data-stu-id="ccaa2-107">The current state of the developer documentation can be found on the [MRTK github.io page](https://microsoft.github.io/MixedRealityToolkit-Unity/)</span></span>

<span data-ttu-id="ccaa2-108">Docfx supporta DFM Docfx Flavored Markdown, che include GFM GitHub Flavored Markdown.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-108">Docfx supports DFM Docfx Flavored Markdown which includes GFM Github Flavored Markdown.</span></span> <span data-ttu-id="ccaa2-109">La documentazione completa e l'elenco delle funzionalità sono disponibili [qui](https://dotnet.github.io/docfx/tutorial/docfx.exe_user_manual.html)</span><span class="sxs-lookup"><span data-stu-id="ccaa2-109">The full documentation and feature list can be found [here](https://dotnet.github.io/docfx/tutorial/docfx.exe_user_manual.html)</span></span>

<span data-ttu-id="ccaa2-110">Docfx non solo converte ma controlla anche tutti i collegamenti locali usati nella documentazione.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-110">Docfx is not only converting but also checking all used local links in the documentation.</span></span> <span data-ttu-id="ccaa2-111">Se non è possibile risolvere un percorso, non verrà convertito nell'equivalente HTML.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-111">If a path can't be resolved it won't be converted into its html equivalent.</span></span> <span data-ttu-id="ccaa2-112">Per questo è importante usare i percorsi relativi solo quando si fa riferimento ad altri file locali.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-112">Therefor it's important to only use relative paths when referring to other local files.</span></span>

## <a name="building-docfx-locally"></a><span data-ttu-id="ccaa2-113">Compilazione di docfx localmente</span><span class="sxs-lookup"><span data-stu-id="ccaa2-113">Building docfx locally</span></span>

<span data-ttu-id="ccaa2-114">I file di compilazione docfx nel repository MRTK possono essere usati per creare una versione locale della documentazione per gli sviluppatori in una sottocartella/documento nella radice del progetto.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-114">The docfx build files in the MRTK repo can be used to create a local version of the developer documentation in a doc/ subfolder in the root of the project.</span></span>

### <a name="setup"></a><span data-ttu-id="ccaa2-115">Configurazione</span><span class="sxs-lookup"><span data-stu-id="ccaa2-115">Setup</span></span>

* <span data-ttu-id="ccaa2-116">ottenere la versione più recente di [docfx](https://dotnet.github.io/docfx/index.html)</span><span class="sxs-lookup"><span data-stu-id="ccaa2-116">get the latest version of [docfx](https://dotnet.github.io/docfx/index.html)</span></span>
* <span data-ttu-id="ccaa2-117">estrarre i file in una cartella del computer</span><span class="sxs-lookup"><span data-stu-id="ccaa2-117">extract the files in a folder on your computer</span></span>
* <span data-ttu-id="ccaa2-118">aggiungere la cartella al percorso nelle variabili di ambiente</span><span class="sxs-lookup"><span data-stu-id="ccaa2-118">add the folder to your PATH in your environment variables</span></span>

### <a name="generation"></a><span data-ttu-id="ccaa2-119">Generation</span><span class="sxs-lookup"><span data-stu-id="ccaa2-119">Generation</span></span>

* <span data-ttu-id="ccaa2-120">aprire un prompt di PowerShell o cmd nella radice del progetto MRTK</span><span class="sxs-lookup"><span data-stu-id="ccaa2-120">open a powershell or cmd prompt in the root of the MRTK project</span></span>
* <span data-ttu-id="ccaa2-121">Execute `docfx docfx.json` (facoltativamente con l'opzione-f per forzare una ricompilazione dei file doc)</span><span class="sxs-lookup"><span data-stu-id="ccaa2-121">execute `docfx docfx.json` (optionally with the -f option to force a rebuild of doc files)</span></span>
* <span data-ttu-id="ccaa2-122">Execute `docfx serve doc` (facoltativamente con-p *NumeroPorta* se non si vuole usare la porta predefinita 8888)</span><span class="sxs-lookup"><span data-stu-id="ccaa2-122">execute `docfx serve doc` (optionally with -p *portnumber* if you don't want to use the 8888 default port)</span></span>
* <span data-ttu-id="ccaa2-123">aprire un Web browser con localhost:*NumeroPorta*</span><span class="sxs-lookup"><span data-stu-id="ccaa2-123">open a web browser with localhost:*portnumber*</span></span>

<span data-ttu-id="ccaa2-124">Si noti che durante l'esecuzione del comando docfx nel file di compilazione JSON docfx visualizzerà eventuali collegamenti interrotti nella documentazione come avviso.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-124">Note that on executing the docfx command on the json build file docfx will show any broken links in the documentation as warning.</span></span>
<span data-ttu-id="ccaa2-125">Assicurarsi che ogni volta che si apportano modifiche ai file di documentazione o all'API per aggiornare tutti i collegamenti che puntano a questi articoli o codice.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-125">Please make sure whenever you perform changes on any of the documentation files or API to update all links pointing to these articles or code.</span></span>

## <a name="verifying-docfx-on-github"></a><span data-ttu-id="ccaa2-126">Verifica di docfx su GitHub</span><span class="sxs-lookup"><span data-stu-id="ccaa2-126">Verifying docfx on github</span></span>

<span data-ttu-id="ccaa2-127">Ogni volta che una richiesta pull include una modifica che potrebbe influire sulla documentazione CI deve essere eseguita per eseguire un controllo in docfx per i collegamenti interrotti.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-127">Whenever a PR includes a change that might affect documentation CI has to be executed to run a check on docfx for broken links.</span></span> <span data-ttu-id="ccaa2-128">Questa operazione può essere attivata inviando il comando `/azp run mrtk_docs` nella richiesta pull se l'utente dispone di diritti sufficienti a tale scopo.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-128">This can be triggered by posting the command `/azp run mrtk_docs` into the PR if the user has sufficient rights to do so.</span></span> <span data-ttu-id="ccaa2-129">Il comando attiverà un processo CI che consente di aggiungere una compilazione di docs alla sezione dei controlli della richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-129">The command will trigger a CI job which will add a docs build to the checks section of the PR.</span></span>

## <a name="using-crefs-and-hrefs-in--documented-code"></a><span data-ttu-id="ccaa2-130">Uso di cRefs e hrefs in///codice documentato</span><span class="sxs-lookup"><span data-stu-id="ccaa2-130">Using crefs and hrefs in /// documented code</span></span>

<span data-ttu-id="ccaa2-131">Docfx supporta cRefs nel codice documentato///.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-131">Docfx supports crefs in /// documented code.</span></span> <span data-ttu-id="ccaa2-132">Questi riferimenti verranno tradotti nei collegamenti che puntano alla documentazione dell'API generata o ai siti Web della documentazione esterna.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-132">It will translate those references to links pointing to the generated api documentation or to external documentation websites.</span></span>
<span data-ttu-id="ccaa2-133">È possibile aggiungere i servizi External xrif per la risoluzione dei collegamenti a librerie/API esterne al docfx.jsnel file di impostazioni di compilazione nella proprietà *xrefService*.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-133">External xref services for resolving links to external libraries/apis can be added to the docfx.json build settings file in the property *xrefService*.</span></span>

<span data-ttu-id="ccaa2-134">Per le API esterne che non forniscono un href del servizio dell'xrif al sito Web della documentazione, è possibile aggiungere ai commenti.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-134">For external apis that don't provide an xref service hrefs to the documentation website can be added to the comments.</span></span>

<span data-ttu-id="ccaa2-135">Esempi:</span><span class="sxs-lookup"><span data-stu-id="ccaa2-135">Examples:</span></span>

```c#
/// Links to MRTK internal class SystemType
/// <see cref="Microsoft.MixedReality.Toolkit.Utilities.SystemType"/>

/// Links to external API - link provided by xref service
/// <see cref="System.Collections.Generic.ICollection{Type}.Contains"/>

/// Links to Unity web API reference
/// <see href="https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyField.html">EditorGUI.PropertyField</see>
```

## <a name="linking-in-md-documentation-files"></a><span data-ttu-id="ccaa2-136">Collegamento in file di documentazione. MD</span><span class="sxs-lookup"><span data-stu-id="ccaa2-136">Linking in .md documentation files</span></span>

<span data-ttu-id="ccaa2-137">Docfx sta traducendo e convalidando tutti i collegamenti locali relativi alla generazione, non è necessaria alcuna sintassi speciale.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-137">Docfx is translating and validating all relative local links on generation, there's no special syntax required.</span></span> <span data-ttu-id="ccaa2-138">Per fare riferimento a un altro articolo della documentazione, è necessario fare riferimento al file. MD corrispondente, mai al file HTML generato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-138">Referring to another documentation article should always be done by referring to the corresponding .md file, never the auto generated .html file.</span></span> <span data-ttu-id="ccaa2-139">Si noti che tutti i collegamenti ai file locali devono essere relativi al file che si sta modificando.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-139">Please note that all links to local files need to be relative to the file you're modifying.</span></span>

<span data-ttu-id="ccaa2-140">Il collegamento alla documentazione dell'API può essere eseguito usando [riferimenti incrociati](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html).</span><span class="sxs-lookup"><span data-stu-id="ccaa2-140">Linking to the API documentation can be done by using [cross references](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html).</span></span> <span data-ttu-id="ccaa2-141">Docfx ha generato automaticamente gli UID per tutti i documenti dell'API facendo la firma.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-141">Docfx automatically generated UIDs for all API docs by mangling the signature.</span></span>

<span data-ttu-id="ccaa2-142">Esempio:</span><span class="sxs-lookup"><span data-stu-id="ccaa2-142">Example:</span></span>

<span data-ttu-id="ccaa2-143">Questo collegamento all' [API BoundarySystem](xref:Microsoft.MixedReality.Toolkit.Boundary) , oltre a questa breve versione: @Microsoft.MixedReality.Toolkit.Boundary</span><span class="sxs-lookup"><span data-stu-id="ccaa2-143">This links to the [BoundarySystem API](xref:Microsoft.MixedReality.Toolkit.Boundary) as well as this short version: @Microsoft.MixedReality.Toolkit.Boundary</span></span>

```md
This links to the [BoundarySystem API](xref:Microsoft.MixedReality.Toolkit.Boundary)
as well as this short version: @Microsoft.MixedReality.Toolkit.Boundary
```

## <a name="enumerating-available-xrefs"></a><span data-ttu-id="ccaa2-144">Enumerazione degli xrif disponibili</span><span class="sxs-lookup"><span data-stu-id="ccaa2-144">Enumerating available xrefs</span></span>

<span data-ttu-id="ccaa2-145">La sintassi dell'xrif può essere difficile da ricordare: è possibile enumerare tutti gli ID di riferimento di riferimento disponibili eseguendo prima docfx localmente:</span><span class="sxs-lookup"><span data-stu-id="ccaa2-145">Xref syntax can be difficult to remember - it's possible to enumerate all of the available xref IDs by first running docfx locally:</span></span>

> <span data-ttu-id="ccaa2-146">docfx docfx.json</span><span class="sxs-lookup"><span data-stu-id="ccaa2-146">docfx docfx.json</span></span>

<span data-ttu-id="ccaa2-147">Verrà generato un file xrefmap. yml, disponibile in docs/xrefmap. yml.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-147">This will generate an xrefmap.yml file, which will be located in docs/xrefmap.yml.</span></span>

<span data-ttu-id="ccaa2-148">Ad esempio, per collegare l'overload seguente di HandleEvent, la sintassi è piuttosto Arcale:</span><span class="sxs-lookup"><span data-stu-id="ccaa2-148">For example, in order to link the following overload of HandleEvent, the syntax is fairly arcane:</span></span>

```yml
- uid: Microsoft.MixedReality.Toolkit.BaseEventSystem.HandleEvent``1(BaseEventData,ExecuteEvents.EventFunction{``0})
  name: HandleEvent<T>(BaseEventData, ExecuteEvents.EventFunction<T>)
  href: api/Microsoft.MixedReality.Toolkit.BaseEventSystem.html#Microsoft_MixedReality_Toolkit_BaseEventSystem_HandleEvent__1_BaseEventData_ExecuteEvents_EventFunction___0__
  commentId: M:Microsoft.MixedReality.Toolkit.BaseEventSystem.HandleEvent``1(BaseEventData,ExecuteEvents.EventFunction{``0})
  name.vb: HandleEvent(Of T)(BaseEventData, ExecuteEvents.EventFunction(Of T))
  fullName: Microsoft.MixedReality.Toolkit.BaseEventSystem.HandleEvent<T>(BaseEventData, ExecuteEvents.EventFunction<T>)
  fullName.vb: Microsoft.MixedReality.Toolkit.BaseEventSystem.HandleEvent(Of T)(BaseEventData, ExecuteEvents.EventFunction(Of T))
  nameWithType: BaseEventSystem.HandleEvent<T>(BaseEventData, ExecuteEvents.EventFunction<T>)
  nameWithType.vb: BaseEventSystem.HandleEvent(Of T)(BaseEventData, ExecuteEvents.EventFunction(Of T))
```

<span data-ttu-id="ccaa2-149">Tuttavia, è facile cercare il nome e quindi usare l'intero **campo uid** come xrif.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-149">It's easy, however, to search for the name and then use the entire **uid field** as the xref.</span></span>

<span data-ttu-id="ccaa2-150">In questo esempio, l'xrif avrà un aspetto simile al seguente: (xrif: Microsoft. MixedReality. Toolkit. BaseEventSystem. HandleEvent ``1(BaseEventData,ExecuteEvents.EventFunction{`` 0}))</span><span class="sxs-lookup"><span data-stu-id="ccaa2-150">In this example, the xref would look like: (xref:Microsoft.MixedReality.Toolkit.BaseEventSystem.HandleEvent``1(BaseEventData,ExecuteEvents.EventFunction{``0}))</span></span>

## <a name="adding-new-md-files-to-developer-docs"></a><span data-ttu-id="ccaa2-151">Aggiunta di nuovi file. MD alla documentazione per sviluppatori</span><span class="sxs-lookup"><span data-stu-id="ccaa2-151">Adding new .md files to developer docs</span></span>

<span data-ttu-id="ccaa2-152">Docfx rileverà tutti i file. MD in cartelle che vengono aggiunte come file di contenuto nella sezione build del docfx.jsin e generano file HTML.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-152">Docfx will pick up any .md files in folders that are added as content files in the build section of the docfx.json and generate html files out of them.</span></span> <span data-ttu-id="ccaa2-153">Per le nuove cartelle è necessario aggiungere una voce corrispondente nel file di compilazione.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-153">For new folders a corresponding entry in the build file needs to be added.</span></span>

### <a name="navigation-entries"></a><span data-ttu-id="ccaa2-154">Voci di navigazione</span><span class="sxs-lookup"><span data-stu-id="ccaa2-154">Navigation entries</span></span>

<span data-ttu-id="ccaa2-155">Per determinare le voci della navigazione nella documentazione per sviluppatori docfx USA TOC. yml/TOC. MD-Table of content files.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-155">To determine the entries of the navigation in the developer docs docfx uses toc.yml/toc.md - table of content files.</span></span>
<span data-ttu-id="ccaa2-156">Il file TOC nella radice del progetto definisce le voci nella barra di spostamento superiore mentre i file TOC. yml nelle sottocartelle del repository definiscono gli argomenti secondari nell'esplorazione della barra laterale.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-156">The toc file in the root of the project defines entries in the top navigation bar whereas the toc.yml files in the subfolders of the repo define subtopics in the sidebar navigation.</span></span>
<span data-ttu-id="ccaa2-157">i file TOC. yml possono essere usati per la strutturazione ed è possibile che siano presenti quantità di tali file.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-157">toc.yml files can be used for structuring and there can be any amount of those files.</span></span> <span data-ttu-id="ccaa2-158">Per altre informazioni sulla definizione delle voci per TOC. yml, vedere la [voce della documentazione di docfx in sommario](https://dotnet.github.io/docfx/tutorial/intro_toc.html).</span><span class="sxs-lookup"><span data-stu-id="ccaa2-158">For more info about defining entries for toc.yml check the [docfx documentation entry on toc](https://dotnet.github.io/docfx/tutorial/intro_toc.html).</span></span>

## <a name="resource-files"></a><span data-ttu-id="ccaa2-159">File di risorse</span><span class="sxs-lookup"><span data-stu-id="ccaa2-159">Resource files</span></span>

<span data-ttu-id="ccaa2-160">Sono disponibili alcuni file, ad esempio immagini, video o file PDF a cui la documentazione può fare riferimento ma che non sono stati convertiti da docfx.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-160">There are some files like images, videos or PDFs that the documentation can refer to but are not converted by docfx.</span></span> <span data-ttu-id="ccaa2-161">Per questi file è presente una sezione relativa alle risorse nell'docfx.js.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-161">For those files there's a resource section in the docfx.json.</span></span> <span data-ttu-id="ccaa2-162">I file in tale sezione verranno copiati solo senza eseguire alcuna conversione su di essi.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-162">Files in that section will only be copied over without performing any conversion on them.</span></span>

<span data-ttu-id="ccaa2-163">Attualmente esiste una definizione per i tipi di risorse seguenti:</span><span class="sxs-lookup"><span data-stu-id="ccaa2-163">Currently there's a definition for the following resource types:</span></span>

| <span data-ttu-id="ccaa2-164">ResourceType</span><span class="sxs-lookup"><span data-stu-id="ccaa2-164">ResourceType</span></span> | <span data-ttu-id="ccaa2-165">Percorso</span><span class="sxs-lookup"><span data-stu-id="ccaa2-165">Path</span></span> |
| --- | --- |
| <span data-ttu-id="ccaa2-166">Immagini</span><span class="sxs-lookup"><span data-stu-id="ccaa2-166">Images</span></span> | <span data-ttu-id="ccaa2-167">Documentazione/immagini/</span><span class="sxs-lookup"><span data-stu-id="ccaa2-167">Documentation/Images/</span></span> |

## <a name="releasing-a-new-version"></a><span data-ttu-id="ccaa2-168">Rilascio di una nuova versione</span><span class="sxs-lookup"><span data-stu-id="ccaa2-168">Releasing a new version</span></span>

<span data-ttu-id="ccaa2-169">Sono supportate più versioni dei documenti per sviluppatori e possono essere disattivate dall'elenco a discesa versione nella barra dei menu superiore.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-169">Multiple versions of developer docs are supported and can be switched by the version drop down in the top menu bar.</span></span> <span data-ttu-id="ccaa2-170">Se si sta rilasciando una nuova versione, seguire questa procedura per avere la versione nella pagina dei documenti per sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-170">If you're releasing a new version perform the following steps to have your version on the developer docs page.</span></span>

1. <span data-ttu-id="ccaa2-171">Facoltativo: modifica della docfx.js</span><span class="sxs-lookup"><span data-stu-id="ccaa2-171">Optional: Adjusting your docfx.json</span></span>  
<span data-ttu-id="ccaa2-172">A seconda se si vuole che il "miglioramento di questo documento" in modo che punti a una versione specifica del repository GitHub, sarà necessario aggiungere la voce seguente alla sezione globalMetaData nel file docfx.jssu prima di chiamare il comando docfx:</span><span class="sxs-lookup"><span data-stu-id="ccaa2-172">Depending on whether you want to have the "Improve this doc" to point to a specific version of the github repo you will have to add the following entry to the globalMetaData section in the docfx.json file before calling the docfx command:</span></span>

    ```json
    "_gitContribute": {
        "repo": "https://github.com/Microsoft/MixedRealityToolkit-Unity.git",
        "branch": "mrtk_development"
    }
    ```

    <span data-ttu-id="ccaa2-173">Se non si configura questa impostazione, docfx utilizzerà per impostazione predefinita il ramo e il repository della cartella corrente da cui si sta chiamando docfx.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-173">If you don't set this up docfx will default to the branch and repo of the current folder you're calling docfx from.</span></span>

1. <span data-ttu-id="ccaa2-174">Creare la documentazione di docfx chiamando docfx docfx.json nella radice del repository</span><span class="sxs-lookup"><span data-stu-id="ccaa2-174">Create your docfx docs by calling docfx docfx.json in the root of the repo</span></span>
1. <span data-ttu-id="ccaa2-175">Creare una cartella con il nome della versione nella cartella Version del ramo GH-Pages e copiare il contenuto della cartella doc generata in tale cartella.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-175">Create a folder with the name of your version in the version folder of the gh-pages branch and copy the contents of the generated doc folder into that folder</span></span>
1. <span data-ttu-id="ccaa2-176">Aggiungere il numero di versione in versionArray in Web/version.js</span><span class="sxs-lookup"><span data-stu-id="ccaa2-176">Add your version number into the versionArray in web/version.js</span></span>
1. <span data-ttu-id="ccaa2-177">Eseguire il push del version.js modificato per mrtk_development ramo e le modifiche nel ramo GH-Pages</span><span class="sxs-lookup"><span data-stu-id="ccaa2-177">Push the modified version.js to mrtk_development branch and the changes in gh-pages branch</span></span>

<span data-ttu-id="ccaa2-178">CI rileverà le modifiche apportate al file di version.js e aggiornerà automaticamente l'elenco a discesa della versione.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-178">CI will pick up the changes done to the version.js file and update the version dropdown automatically.</span></span>

### <a name="supporting-development-branches-on-ci"></a><span data-ttu-id="ccaa2-179">Supporto di rami di sviluppo in CI</span><span class="sxs-lookup"><span data-stu-id="ccaa2-179">Supporting development branches on CI</span></span>

<span data-ttu-id="ccaa2-180">Il sistema di controllo delle versioni può essere usato anche per visualizzare le versioni dei documenti da altri branch di sviluppo compilati da CI.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-180">The versioning system can also be used for showing doc versions from other dev branches that are built by CI.</span></span> <span data-ttu-id="ccaa2-181">Quando si configura l'integrazione continua per uno di questi rami, assicurarsi che lo script di PowerShell in CI copi il contenuto dell'output docfx generato in una cartella della versione denominata dopo il ramo e aggiungere la corrispondente voce di versione nel file Web/version.js.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-181">When setting up CI for one of those branches make sure your powershell script on CI copies the contents of the generated docfx output into a version folder named after your branch and add the corresponding version entry into the web/version.js file.</span></span>

## <a name="good-practices-for-developers"></a><span data-ttu-id="ccaa2-182">Procedure ottimali per gli sviluppatori</span><span class="sxs-lookup"><span data-stu-id="ccaa2-182">Good practices for developers</span></span>

* <span data-ttu-id="ccaa2-183">Usare **percorsi relativi** ogni volta che si fa riferimento a pagine interne MRTK</span><span class="sxs-lookup"><span data-stu-id="ccaa2-183">Use **relative paths** whenever referring to MRTK internal pages</span></span>
* <span data-ttu-id="ccaa2-184">Usare i **riferimenti incrociati** per il collegamento a qualsiasi pagina dell'API MRTK usando l' **UID modificato**</span><span class="sxs-lookup"><span data-stu-id="ccaa2-184">Use **cross references** for linking to any MRTK API page by using the **mangled UID**</span></span>
* <span data-ttu-id="ccaa2-185">Usare **cRefs e hrefs** per collegarsi alla documentazione interna o esterna nei **Commenti///**</span><span class="sxs-lookup"><span data-stu-id="ccaa2-185">Use **crefs and hrefs** to link to internal or external documentation in **/// comments**</span></span>
* <span data-ttu-id="ccaa2-186">Usa le cartelle indicate in questo documento per i file di risorse</span><span class="sxs-lookup"><span data-stu-id="ccaa2-186">Use the indicated folders in this doc for resource files</span></span>
* <span data-ttu-id="ccaa2-187">**Eseguire docfx localmente** e verificare la presenza di avvisi nell'output ogni volta che si modificano le API esistenti o si aggiornano le pagine della documentazione</span><span class="sxs-lookup"><span data-stu-id="ccaa2-187">**Run docfx locally** and check for warnings in the output whenever you modify existing APIs or update documentation pages</span></span>
* <span data-ttu-id="ccaa2-188">Guarda gli avvisi di docfx **su ci** dopo il completamento e l'Unione della richiesta pull in uno dei rami MRTK ufficiali</span><span class="sxs-lookup"><span data-stu-id="ccaa2-188">Watch out for docfx **warnings on CI** after completing and merging your PR into one of the official MRTK branches</span></span>

## <a name="common-errors-when-generating-docs"></a><span data-ttu-id="ccaa2-189">Errori comuni durante la generazione di documenti</span><span class="sxs-lookup"><span data-stu-id="ccaa2-189">Common errors when generating docs</span></span>

* <span data-ttu-id="ccaa2-190">errori TOC. yml: in genere si verifica quando un file con estensione MD viene spostato/rinominato o rimosso, ma la tabella del file di contenuto (TOC. yml) che punta a tale file non è stata aggiornata di conseguenza.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-190">toc.yml errors: usually happens when an .md file gets moved/renamed or removed but the table of content file (toc.yml) pointing to that file wasn't updated accordingly.</span></span> <span data-ttu-id="ccaa2-191">Sul sito Web verrà visualizzato un collegamento interruppe nel primo livello o nell'esplorazione laterale</span><span class="sxs-lookup"><span data-stu-id="ccaa2-191">On the website this will result in a broken link on our top level or side navigation</span></span>
* <span data-ttu-id="ccaa2-192">errori relativi ai commenti</span><span class="sxs-lookup"><span data-stu-id="ccaa2-192">/// comments errors</span></span>
  * <span data-ttu-id="ccaa2-193">errori dei tag XML: docfx come qualsiasi altro parser XML non è in grado di gestire i tag XML in formato non valido.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-193">xml tag errors - docfx like any other xml parser can't handle malformed xml tags.</span></span>
  * <span data-ttu-id="ccaa2-194">errori di digitazione in cRefs</span><span class="sxs-lookup"><span data-stu-id="ccaa2-194">typos in crefs</span></span>
  * <span data-ttu-id="ccaa2-195">identificatori dello spazio dei nomi incompleti: docfx non richiede lo spazio dei nomi completo al simbolo a cui si fa riferimento, ma la parte relativa dello spazio dei nomi non inclusa nello spazio dei nomi adiacente di cref.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-195">incomplete namespace identifiers - docfx won't need the full namespace to the symbol you're referring to but the relative part of the namespace that's not included in the surrounding namespace of the cref.</span></span>
    * <span data-ttu-id="ccaa2-196">Esempio: se ci si trova in uno spazio dei nomi Microsoft. MixedReality. Toolkit. Core. Providers. UnityInput e il file che si vuole collegare è Microsoft. MixedReality. Toolkit. Core. Interfaces. IMixedRealityServiceRegistrar, il cref può essere simile al seguente: cref = "Interfaces. IMixedRealityServiceRegistrar"</span><span class="sxs-lookup"><span data-stu-id="ccaa2-196">Example: if you're in a namespace Microsoft.MixedReality.Toolkit.Core.Providers.UnityInput and the file you want to link in is Microsoft.MixedReality.Toolkit.Core.Interfaces.IMixedRealityServiceRegistrar your cref can look like this: cref="Interfaces.IMixedRealityServiceRegistrar"</span></span>
  * <span data-ttu-id="ccaa2-197">External cRefs: se non è disponibile alcun servizio dell'elenco di funzioni di riferimento (ed è elencato nel file di compilazione docfx), cRefs alle librerie esterne non funzionerà.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-197">External crefs - As long as there's no xref service available (and listed in the docfx build file) crefs to external libraries won't work.</span></span> <span data-ttu-id="ccaa2-198">Se si vuole ancora creare un collegamento a un simbolo esterno specifico che non dispone di un servizio dell'xrif, ma una documentazione sull'API online, è invece possibile usare href.</span><span class="sxs-lookup"><span data-stu-id="ccaa2-198">If you still want to link to a specific external symbol that doesn't have xref service but an online api documentation you can use a href instead.</span></span> <span data-ttu-id="ccaa2-199">Esempio: collegamento a EditorPrefs di Unity: `<see href="https://docs.unity3d.com/ScriptReference/EditorPrefs.html">EditorPrefs</see>`</span><span class="sxs-lookup"><span data-stu-id="ccaa2-199">Example: linking to EditorPrefs of Unity: `<see href="https://docs.unity3d.com/ScriptReference/EditorPrefs.html">EditorPrefs</see>`</span></span>

## <a name="see-also"></a><span data-ttu-id="ccaa2-200">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="ccaa2-200">See also</span></span>

* [<span data-ttu-id="ccaa2-201">Guida alla documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="ccaa2-201">MRTK documentation guide</span></span>](DocumentationGuide.md)
* [<span data-ttu-id="ccaa2-202">Documentazione per gli sviluppatori MRTK su github.io</span><span class="sxs-lookup"><span data-stu-id="ccaa2-202">MRTK developer documentation on github.io</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/)
* [<span data-ttu-id="ccaa2-203">DocFX</span><span class="sxs-lookup"><span data-stu-id="ccaa2-203">DocFX</span></span>](https://dotnet.github.io/docfx/index.html)
