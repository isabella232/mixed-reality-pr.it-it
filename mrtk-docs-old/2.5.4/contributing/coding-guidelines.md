---
title: CodingGuidelines
description: principi e convenzioni di codifica da seguire per contribuire a MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, C#,
ms.openlocfilehash: 35f45966279f4e34609e4ea7eb40b801b4073682
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682144"
---
# <a name="coding-guidelines"></a><span data-ttu-id="e6a7e-104">Linee guida sulla codifica</span><span class="sxs-lookup"><span data-stu-id="e6a7e-104">Coding guidelines</span></span>

<span data-ttu-id="e6a7e-105">Questo documento descrive i principi e le convenzioni di codifica da seguire per contribuire a MRTK.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-105">This document outlines coding principles and conventions to follow when contributing to MRTK.</span></span>

---

## <a name="philosophy"></a><span data-ttu-id="e6a7e-106">Filosofia</span><span class="sxs-lookup"><span data-stu-id="e6a7e-106">Philosophy</span></span>

### <a name="be-concise-and-strive-for-simplicity"></a><span data-ttu-id="e6a7e-107">Essere conciso e impegnarsi per semplicità</span><span class="sxs-lookup"><span data-stu-id="e6a7e-107">Be concise and strive for simplicity</span></span>

<span data-ttu-id="e6a7e-108">La soluzione più semplice è spesso la scelta migliore.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-108">The simplest solution is often the best.</span></span> <span data-ttu-id="e6a7e-109">Si tratta di un obiettivo sostitutivo di queste linee guida e dovrebbe essere l'obiettivo di tutte le attività di codifica.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-109">This is an overriding aim of these guidelines and should be the goal of all coding activity.</span></span> <span data-ttu-id="e6a7e-110">Parte della semplicità è concisa e coerente con il codice esistente.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-110">Part of being simple is being concise, and consistent with existing code.</span></span> <span data-ttu-id="e6a7e-111">Provare a semplificare il codice.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-111">Try to keep your code simple.</span></span>

<span data-ttu-id="e6a7e-112">I lettori devono rilevare solo gli elementi che forniscono informazioni utili.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-112">Readers should only encounter artifacts that provide useful information.</span></span> <span data-ttu-id="e6a7e-113">Ad esempio, i commenti che riformulano gli elementi evidenti non forniscono informazioni aggiuntive e aumentano il rapporto tra rumore e segnale.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-113">For example, comments that restate what is obvious provide no extra information and increase the noise to signal ratio.</span></span>

<span data-ttu-id="e6a7e-114">Semplificare la logica del codice.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-114">Keep code logic simple.</span></span> <span data-ttu-id="e6a7e-115">Si noti che non si tratta di un'istruzione sull'utilizzo del minor numero di righe, riducendo al minimo le dimensioni dei nomi degli identificatori o dello stile della parentesi graffa, ma per ridurre il numero di concetti e massimizzare la visibilità di tali linee tramite modelli noti.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-115">Note that this is not a statement about using the fewest number of lines, minimizing the size of identifier names or brace style, but about reducing the number of concepts and maximizing the visibility of those through familiar patterns.</span></span>

### <a name="produce-consistent-readable-code"></a><span data-ttu-id="e6a7e-116">Produrre codice coerente e leggibile</span><span class="sxs-lookup"><span data-stu-id="e6a7e-116">Produce consistent, readable code</span></span>

<span data-ttu-id="e6a7e-117">La leggibilità del codice è correlata a frequenze di difetti ridotte.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-117">Code readability is correlated with low defect rates.</span></span> <span data-ttu-id="e6a7e-118">Sforzarsi di creare codice facile da leggere.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-118">Strive to create code that is easy to read.</span></span> <span data-ttu-id="e6a7e-119">Sforzarsi di creare codice con una logica semplice e riutilizzare i componenti esistenti, in quanto consente inoltre di garantire la correttezza.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-119">Strive to create code that has simple logic and re-uses existing components as it will also help ensure correctness.</span></span>

<span data-ttu-id="e6a7e-120">Tutti i dettagli del codice prodotto, dai dettagli più semplici sulla correttezza allo stile e alla formattazione coerenti.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-120">All details of the code you produce matter, from the most basic detail of correctness to consistent style and formatting.</span></span> <span data-ttu-id="e6a7e-121">Mantieni lo stile di codifica coerente con quello che esiste già, anche se non corrisponde alle tue preferenze.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-121">Keep your coding style consistent with what already exists, even if it is not matching your preference.</span></span> <span data-ttu-id="e6a7e-122">Ciò aumenta la leggibilità della codebase complessiva.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-122">This increases the readability of the overall codebase.</span></span>

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a><span data-ttu-id="e6a7e-123">Supportare la configurazione dei componenti sia nell'editor che in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="e6a7e-123">Support configuring components both in editor and at run-time</span></span>

<span data-ttu-id="e6a7e-124">MRTK supporta un set di utenti diversificato, ovvero persone che preferiscono configurare i componenti nell'editor di Unity e caricare i prefabbricati e gli utenti che devono creare istanze e configurare oggetti in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-124">MRTK supports a diverse set of users – people who prefer to configure components in the Unity editor and load prefabs, and people who need to instantiate and configure objects at run-time.</span></span>

<span data-ttu-id="e6a7e-125">Tutto il codice dovrebbe funzionare sia aggiungendo un componente a un GameObject in una scena salvata, sia creando un'istanza del componente nel codice.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-125">All your code should work by BOTH adding a component to a GameObject in a saved scene, and by instantiating that component in code.</span></span> <span data-ttu-id="e6a7e-126">I test devono includere una test case sia per la creazione di un'istanza di prefabbricati che per la creazione di istanze, configurazione del componente in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="e6a7e-126">Tests should include a test case both for instantiating prefabs and instantiating, configuring the component at runtime.</span></span>

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a><span data-ttu-id="e6a7e-127">Play-in-Editor è la prima piattaforma di destinazione principale</span><span class="sxs-lookup"><span data-stu-id="e6a7e-127">Play-in-editor is your first and primary target platform</span></span>

<span data-ttu-id="e6a7e-128">Play-in-Editor è il modo più rapido per eseguire un'iterazione in Unity.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-128">Play-In-Editor is the fastest way to iterate in Unity.</span></span> <span data-ttu-id="e6a7e-129">Fornire modi per consentire ai clienti di eseguire rapidamente l'iterazione consente loro di sviluppare soluzioni in modo più rapido e provare altre idee.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-129">Providing ways for our customers to iterate quickly allows them to both develop solutions more quickly and try out more ideas.</span></span> <span data-ttu-id="e6a7e-130">In altre parole, l'ottimizzazione della velocità di iterazione consente ai clienti di ottenere maggiori risultati.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-130">In other words, maximizing the speed of iteration empowers our customers to achieve more.</span></span>

<span data-ttu-id="e6a7e-131">Eseguire tutte le operazioni nell'editor, quindi fare in modo che funzioni in qualsiasi altra piattaforma.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-131">Make everything work in editor, then make it work on any other platform.</span></span> <span data-ttu-id="e6a7e-132">Mantenerlo funzionante nell'editor.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-132">Keep it working in the editor.</span></span> <span data-ttu-id="e6a7e-133">È facile aggiungere una nuova piattaforma a Play-in-Editor.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-133">It is easy to add a new platform to Play-In-Editor.</span></span> <span data-ttu-id="e6a7e-134">È molto difficile ottenere il funzionamento di Play-in-Editor se l'app funziona solo in un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-134">It is very difficult to get Play-In-Editor working if your app only works on a device.</span></span>

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a><span data-ttu-id="e6a7e-135">Aggiunta di nuovi campi pubblici, proprietà, metodi e campi privati serializzati con attenzione</span><span class="sxs-lookup"><span data-stu-id="e6a7e-135">Add new public fields, properties, methods and serialized private fields with care</span></span>

<span data-ttu-id="e6a7e-136">Ogni volta che si aggiunge un metodo pubblico, Field, Property, diventa parte della superficie dell'API pubblica di MRTK.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-136">Every time you add a public method, field, property, it becomes part of MRTK’s public API surface.</span></span> <span data-ttu-id="e6a7e-137">I campi privati contrassegnati con `[SerializeField]` espongono anche campi all'editor e fanno parte della superficie dell'API pubblica.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-137">Private fields marked with `[SerializeField]` also expose fields to the editor and are part of the public API surface.</span></span> <span data-ttu-id="e6a7e-138">Altri utenti possono usare il metodo pubblico, configurare i prefabbricati personalizzati con il campo pubblico e assumere una dipendenza.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-138">Other people might use that public method, configure custom prefabs with your public field, and take a dependency on it.</span></span>

<span data-ttu-id="e6a7e-139">È necessario esaminare attentamente i nuovi membri pubblici.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-139">New public members should be carefully examined.</span></span> <span data-ttu-id="e6a7e-140">In futuro sarà necessario mantenere un campo pubblico.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-140">Any public field will need to be maintained in the future.</span></span> <span data-ttu-id="e6a7e-141">Tenere presente che, se il tipo di un campo pubblico (o di un campo privato serializzato) cambia o viene rimosso da un monocomportamento, questo potrebbe comportare l'insorgere di altre persone.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-141">Remember that if the type of a public field (or serialized private field) changes or gets removed from a MonoBehaviour, that could break other people.</span></span> <span data-ttu-id="e6a7e-142">Il campo deve essere prima deprecato per una versione e il codice per eseguire la migrazione delle modifiche per gli utenti che hanno eseguito dipendenze deve essere fornito.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-142">The field will need to first be deprecated for a release, and code to migrate changes for people that have taken dependencies would need to be provided.</span></span>

### <a name="prioritize-writing-tests"></a><span data-ttu-id="e6a7e-143">Assegnare priorità ai test di scrittura</span><span class="sxs-lookup"><span data-stu-id="e6a7e-143">Prioritize writing tests</span></span>

<span data-ttu-id="e6a7e-144">MRTK è un progetto di community, modificato da un'ampia gamma di collaboratori.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-144">MRTK is a community project, modified by a diverse range of contributors.</span></span> <span data-ttu-id="e6a7e-145">Questi collaboratori potrebbero non essere a conoscenza dei dettagli della correzione o della funzionalità di bug e interrompere accidentalmente la funzionalità.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-145">These contributors may not know the details of your bug fix / feature, and accidentally break your feature.</span></span> <span data-ttu-id="e6a7e-146">[MRTK esegue i test di integrazione continua](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) prima di completare ogni richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-146">[MRTK runs continuous integration tests](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) before completing every pull request.</span></span> <span data-ttu-id="e6a7e-147">Non è possibile archiviare le modifiche che interrompono i test.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-147">Changes that break tests cannot be checked in.</span></span> <span data-ttu-id="e6a7e-148">Pertanto, i test rappresentano il modo migliore per garantire che altri utenti non interrompano la funzionalità.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-148">Therefore, tests are the best way to ensure that other people do not break your feature.</span></span>

<span data-ttu-id="e6a7e-149">Quando si corregge un bug, scrivere un test per assicurarsi che non venga regressione in futuro.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-149">When you fix a bug, write a test to ensure it does not regress in the future.</span></span> <span data-ttu-id="e6a7e-150">Se si aggiunge una funzionalità, scrivere i test per verificare il funzionamento della funzionalità.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-150">If adding a feature, write tests that verify your feature works.</span></span> <span data-ttu-id="e6a7e-151">Questa operazione è necessaria per tutte le funzionalità di UX ad eccezione delle funzionalità sperimentali.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-151">This is required for all UX features except experimental features.</span></span>

## <a name="c-coding-conventions"></a><span data-ttu-id="e6a7e-152">Convenzioni di codifica C#</span><span class="sxs-lookup"><span data-stu-id="e6a7e-152">C# Coding conventions</span></span>

### <a name="script-license-information-headers"></a><span data-ttu-id="e6a7e-153">Intestazioni delle informazioni di licenza per script</span><span class="sxs-lookup"><span data-stu-id="e6a7e-153">Script license information headers</span></span>

<span data-ttu-id="e6a7e-154">Tutti i dipendenti Microsoft che contribuiscono ai nuovi file devono aggiungere l'intestazione di licenza standard seguente all'inizio di tutti i nuovi file, esattamente come mostrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="e6a7e-154">All Microsoft employees contributing new files should add the following standard License header at the top of any new files, exactly as shown below:</span></span>

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a><span data-ttu-id="e6a7e-155">Intestazioni di riepilogo funzione/metodo</span><span class="sxs-lookup"><span data-stu-id="e6a7e-155">Function / method summary headers</span></span>

<span data-ttu-id="e6a7e-156">Tutte le classi, le strutture, le enumerazioni, le funzioni, le proprietà, i campi pubblicati in MRTK devono essere descritti in modo analogo allo scopo e all'uso, esattamente come mostrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="e6a7e-156">All public classes, structs, enums, functions, properties, fields posted to the MRTK should be described as to its purpose and use, exactly as shown below:</span></span>

```c#
/// <summary>
/// The Controller definition defines the Controller as defined by the SDK / Unity.
/// </summary>
public struct Controller
{
    /// <summary>
    /// The ID assigned to the Controller
    /// </summary>
    public string ID;
}
```

<span data-ttu-id="e6a7e-157">In questo modo la documentazione viene generata e divulgata correttamente per tutte le classi, i metodi e le proprietà.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-157">This ensures documentation is properly generated and disseminated for all all classes, methods, and properties.</span></span>

<span data-ttu-id="e6a7e-158">Eventuali file di script inviati senza tag di riepilogo appropriati verranno rifiutati.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-158">Any script files submitted without proper summary tags will be rejected.</span></span>

### <a name="mrtk-namespace-rules"></a><span data-ttu-id="e6a7e-159">Regole dello spazio dei nomi MRTK</span><span class="sxs-lookup"><span data-stu-id="e6a7e-159">MRTK namespace rules</span></span>

<span data-ttu-id="e6a7e-160">Il Toolkit di realtà mista Usa un modello di spazio dei nomi basato su funzionalità, in cui tutti gli spazi dei nomi fondamentali iniziano con "Microsoft. MixedReality. Toolkit".</span><span class="sxs-lookup"><span data-stu-id="e6a7e-160">The Mixed Reality Toolkit uses a feature based namespace model, where all foundational namespaces begin with "Microsoft.MixedReality.Toolkit".</span></span> <span data-ttu-id="e6a7e-161">In generale, non è necessario specificare il livello Toolkit (ad esempio Core, providers, servizi) negli spazi dei nomi.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-161">In general, you need not specify the toolkit layer (ex: Core, Providers, Services) in your namespaces.</span></span>

<span data-ttu-id="e6a7e-162">Gli spazi dei nomi attualmente definiti sono:</span><span class="sxs-lookup"><span data-stu-id="e6a7e-162">The currently defined namespaces are:</span></span>

- <span data-ttu-id="e6a7e-163">Microsoft. MixedReality. Toolkit</span><span class="sxs-lookup"><span data-stu-id="e6a7e-163">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="e6a7e-164">Microsoft. MixedReality. Toolkit. Boundary</span><span class="sxs-lookup"><span data-stu-id="e6a7e-164">Microsoft.MixedReality.Toolkit.Boundary</span></span>
- <span data-ttu-id="e6a7e-165">Microsoft. MixedReality. Toolkit. Diagnostics</span><span class="sxs-lookup"><span data-stu-id="e6a7e-165">Microsoft.MixedReality.Toolkit.Diagnostics</span></span>
- <span data-ttu-id="e6a7e-166">Microsoft. MixedReality. Toolkit. Editor</span><span class="sxs-lookup"><span data-stu-id="e6a7e-166">Microsoft.MixedReality.Toolkit.Editor</span></span>
- <span data-ttu-id="e6a7e-167">Microsoft. MixedReality. Toolkit. input</span><span class="sxs-lookup"><span data-stu-id="e6a7e-167">Microsoft.MixedReality.Toolkit.Input</span></span>
- <span data-ttu-id="e6a7e-168">Microsoft. MixedReality. Toolkit. SpatialAwareness</span><span class="sxs-lookup"><span data-stu-id="e6a7e-168">Microsoft.MixedReality.Toolkit.SpatialAwareness</span></span>
- <span data-ttu-id="e6a7e-169">Microsoft. MixedReality. Toolkit. Teleport</span><span class="sxs-lookup"><span data-stu-id="e6a7e-169">Microsoft.MixedReality.Toolkit.Teleport</span></span>
- <span data-ttu-id="e6a7e-170">Microsoft. MixedReality. Toolkit. Utilities</span><span class="sxs-lookup"><span data-stu-id="e6a7e-170">Microsoft.MixedReality.Toolkit.Utilities</span></span>

<span data-ttu-id="e6a7e-171">Per gli spazi dei nomi con una grande quantità di tipi, è accettabile creare un numero limitato di sottospazi dei nomi per facilitare l'utilizzo dell'ambito.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-171">For namespaces with a large amount of types, it is acceptable to create a limited number of sub-namespaces to aid in scoping usage.</span></span>

<span data-ttu-id="e6a7e-172">L'omissione dello spazio dei nomi per un'interfaccia, una classe o un tipo di dati provocherà il blocco della modifica.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-172">Omitting the namespace for an interface, class or data type will cause your change to be blocked.</span></span>

### <a name="adding-new-monobehaviour-scripts"></a><span data-ttu-id="e6a7e-173">Aggiunta di nuovi script monobehavior</span><span class="sxs-lookup"><span data-stu-id="e6a7e-173">Adding new MonoBehaviour scripts</span></span>

<span data-ttu-id="e6a7e-174">Quando si aggiungono nuovi script monobehavior con una richiesta pull, assicurarsi [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) che l'attributo venga applicato a tutti i file applicabili.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-174">When adding new MonoBehaviour scripts with a pull request, ensure the [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) attribute is applied to all applicable files.</span></span> <span data-ttu-id="e6a7e-175">Ciò garantisce che il componente sia facilmente individuabile nell'editor sotto il pulsante *Aggiungi componente* .</span><span class="sxs-lookup"><span data-stu-id="e6a7e-175">This ensures the component is easily discoverable in the editor under the *Add Component* button.</span></span> <span data-ttu-id="e6a7e-176">Il flag di attributo non è necessario se il componente non può essere visualizzato nell'editor, ad esempio una classe astratta.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-176">The attribute flag is not necessary if the component cannot show up in editor such as an abstract class.</span></span>

<span data-ttu-id="e6a7e-177">Nell'esempio seguente il *pacchetto* deve essere compilato con il percorso del pacchetto del componente.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-177">In the example below, the *Package here* should be filled with the package location of the component.</span></span> <span data-ttu-id="e6a7e-178">Se si posiziona un elemento nella cartella *MRTK/SDK* , il pacchetto sarà *SDK*.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-178">If placing an item in *MRTK/SDK* folder, then the package will be *SDK*.</span></span>

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a><span data-ttu-id="e6a7e-179">Aggiunta di nuovi script di Unity Inspector</span><span class="sxs-lookup"><span data-stu-id="e6a7e-179">Adding new Unity inspector scripts</span></span>

<span data-ttu-id="e6a7e-180">In generale, provare a evitare di creare script di controllo personalizzati per i componenti di MRTK.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-180">In general, try to avoid creating custom inspector scripts for MRTK components.</span></span> <span data-ttu-id="e6a7e-181">Aggiunge overhead e gestione aggiuntivi della codebase che potrebbero essere gestiti dal motore Unity.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-181">It adds additional overhead and management of the codebase that could be handled by the Unity engine.</span></span>

<span data-ttu-id="e6a7e-182">Se è necessaria una classe Inspector, provare a usare Unity [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) .</span><span class="sxs-lookup"><span data-stu-id="e6a7e-182">If an inspector class is necessary, try to use Unity's [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html).</span></span> <span data-ttu-id="e6a7e-183">Questa operazione semplifica di nuovo la classe Inspector e lascia gran parte del lavoro a Unity.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-183">This again simplifies the inspector class and leaves much of the work to Unity.</span></span>

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

<span data-ttu-id="e6a7e-184">Se nella classe Inspector è necessario il rendering personalizzato, provare a utilizzare [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) e [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) .</span><span class="sxs-lookup"><span data-stu-id="e6a7e-184">If custom rendering is required in the inspector class, try to utilize [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) and [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html).</span></span> <span data-ttu-id="e6a7e-185">In questo modo Unity gestisce correttamente il rendering dei prefabbricati annidati e i valori modificati.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-185">This will ensure Unity correctly handles rendering nested prefabs and modified values.</span></span>

<span data-ttu-id="e6a7e-186">Se [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) non può essere usato a causa di un requisito nella logica personalizzata, assicurarsi che tutti i dati di utilizzo siano racchiusi in un oggetto [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) .</span><span class="sxs-lookup"><span data-stu-id="e6a7e-186">If [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) cannot be used due to a requirement in custom logic, ensure all usage is wrapped around a [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html).</span></span> <span data-ttu-id="e6a7e-187">In questo modo Unity esegue il rendering corretto del controllo per i prefabbricati annidati e i valori modificati con la proprietà specificata.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-187">This will ensure Unity renders the inspector correctly for nested prefabs and modified values with the given property.</span></span>

<span data-ttu-id="e6a7e-188">Inoltre, provare a decorare la classe Inspector personalizzata con un oggetto [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) .</span><span class="sxs-lookup"><span data-stu-id="e6a7e-188">Furthermore, try to decorate the custom inspector class with a [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html).</span></span> <span data-ttu-id="e6a7e-189">Questo tag assicura che più oggetti con questo componente nella scena possano essere selezionati e modificati insieme.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-189">This tag ensure multiple objects with this component in the scene can be selected and modified together.</span></span> <span data-ttu-id="e6a7e-190">Tutte le nuove classi di controllo dovrebbero testare il funzionamento del codice in questa situazione nella scena.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-190">Any new inspector classes should test that their code works in this situation in the scene.</span></span>

```c#
    // Example inspector class demonstrating usage of SerializedProperty & EditorGUILayout.PropertyField
    // as well as use of EditorGUI.PropertyScope for custom property logic
    [CustomEditor(typeof(MyComponent))]
    public class MyComponentInspector : UnityEditor.Editor
    {
        private SerializedProperty myProperty;
        private SerializedProperty handedness;

        protected virtual void OnEnable()
        {
            myProperty = serializedObject.FindProperty("myProperty");
            handedness = serializedObject.FindProperty("handedness");
        }

        public override void OnInspectorGUI()
        {
            EditorGUILayout.PropertyField(destroyOnSourceLost);

            Rect position = EditorGUILayout.GetControlRect();
            var label = new GUIContent(handedness.displayName);
            using (new EditorGUI.PropertyScope(position, label, handedness))
            {
                var currentHandedness = (Handedness)handedness.enumValueIndex;

                handedness.enumValueIndex = (int)(Handedness)EditorGUI.EnumPopup(
                    position,
                    label,
                    currentHandedness,
                    (value) => {
                        // This function is executed by Unity to determine if a possible enum value
                        // is valid for selection in the editor view
                        // In this case, only Handedness.Left and Handedness.Right can be selected
                        return (Handedness)value == Handedness.Left
                        || (Handedness)value == Handedness.Right;
                    });
            }
        }
    }
```

### <a name="adding-new-scriptableobjects"></a><span data-ttu-id="e6a7e-191">Aggiunta di nuovi ScriptableObjects</span><span class="sxs-lookup"><span data-stu-id="e6a7e-191">Adding new ScriptableObjects</span></span>

<span data-ttu-id="e6a7e-192">Quando si aggiungono nuovi script ScriptableObject, assicurarsi [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) che l'attributo venga applicato a tutti i file applicabili.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-192">When adding new ScriptableObject scripts, ensure the [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) attribute is applied to all applicable files.</span></span> <span data-ttu-id="e6a7e-193">Ciò garantisce che il componente sia facilmente individuabile nell'editor tramite i menu di creazione dell'asset.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-193">This ensures the component is easily discoverable in the editor via the asset creation menus.</span></span> <span data-ttu-id="e6a7e-194">Il flag di attributo non è necessario se il componente non può essere visualizzato nell'editor, ad esempio una classe astratta.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-194">The attribute flag is not necessary if the component cannot show up in editor such as an abstract class.</span></span>

<span data-ttu-id="e6a7e-195">Nell'esempio seguente, la *sottocartella* deve essere riempita con la sottocartella MRTK, se applicabile.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-195">In the example below, the *Subfolder* should be filled with the MRTK subfolder, if applicable.</span></span> <span data-ttu-id="e6a7e-196">Se si posiziona un elemento nella cartella *MRTK/Providers* , il pacchetto sarà *providers*.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-196">If placing an item in *MRTK/Providers* folder, then the package will be *Providers*.</span></span> <span data-ttu-id="e6a7e-197">Se si posiziona un elemento nella cartella *MRTK/Core* , impostarlo su "Profiles".</span><span class="sxs-lookup"><span data-stu-id="e6a7e-197">If placing an item in the *MRTK/Core* folder, set this to "Profiles".</span></span>

<span data-ttu-id="e6a7e-198">Nell'esempio seguente *MyNewService | MyNewProvider* deve essere compilato con il nome della nuova classe, se applicabile.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-198">In the example below, the *MyNewService | MyNewProvider* should be filled with the your new class' name, if applicable.</span></span> <span data-ttu-id="e6a7e-199">Se si posiziona un elemento nella cartella *MixedRealityToolkit* , lasciare questa stringa.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-199">If placing an item in the *MixedRealityToolkit* folder, leave this string out.</span></span>

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a><span data-ttu-id="e6a7e-200">Registrazione</span><span class="sxs-lookup"><span data-stu-id="e6a7e-200">Logging</span></span>

<span data-ttu-id="e6a7e-201">Quando si aggiungono nuove funzionalità o si aggiornano le funzionalità esistenti, è consigliabile aggiungere i log DebugUtilities. LogVerbose al codice interessante che può risultare utile per il debug futuro.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-201">When adding new features or updating existing features, consider adding DebugUtilities.LogVerbose logs to interesting code that may be useful for future debugging.</span></span> <span data-ttu-id="e6a7e-202">C'è un compromesso tra l'aggiunta della registrazione e il rumore aggiunto e la registrazione non sufficiente, che rende difficile la diagnosi.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-202">There's a tradeoff here between adding logging and the added noise and not enough logging (which makes diagnosis difficult).</span></span>

<span data-ttu-id="e6a7e-203">Un esempio interessante in cui la registrazione è utile (insieme al payload interessante):</span><span class="sxs-lookup"><span data-stu-id="e6a7e-203">An interesting example where having logging is useful (along with interesting payload):</span></span>

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

<span data-ttu-id="e6a7e-204">Questo tipo di registrazione può essere utile per rilevare problemi come [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) , causati da eventi di origine non corrispondenti rilevati e da eventi persi.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-204">This type of logging can help catch issues like [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016), which were caused by mismatched source detected and source lost events.</span></span>

<span data-ttu-id="e6a7e-205">Evitare di aggiungere log per i dati e gli eventi che si verificano in ogni frame. la registrazione idealmente dovrebbe coprire eventi "interessanti" basati su input utente distinti, ad esempio un "clic" da un utente e il set di modifiche ed eventi provenienti da interessanti da registrare.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-205">Avoid adding logs for data and events that are occurring on every frame - ideally logging should cover "interesting" events driven by distinct user inputs (i.e. a "click" by a user and the set of changes and events that come from that are interesting to log).</span></span> <span data-ttu-id="e6a7e-206">Lo stato attuale di "utente è ancora in possesso di un gesto" registrato ogni frame non è interessante e sovraccarica i log.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-206">The ongoing state of "user is still holding a gesture" logged every frame is not interesting and will overwhelm the logs.</span></span>

<span data-ttu-id="e6a7e-207">Si noti che questa registrazione dettagliata non è attivata per impostazione predefinita e deve essere abilitata nelle [impostazioni del sistema di diagnostica](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging).</span><span class="sxs-lookup"><span data-stu-id="e6a7e-207">Note that this verbose logging is not turned on by default (it must be enabled in the [Diagnostic System settings](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging))</span></span>

### <a name="spaces-vs-tabs"></a><span data-ttu-id="e6a7e-208">Spazi vs schede</span><span class="sxs-lookup"><span data-stu-id="e6a7e-208">Spaces vs tabs</span></span>

<span data-ttu-id="e6a7e-209">Per contribuire a questo progetto, assicurarsi di usare 4 spazi anziché le schede.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-209">Please be sure to use 4 spaces instead of tabs when contributing to this project.</span></span>

### <a name="spacing"></a><span data-ttu-id="e6a7e-210">Spaziatura</span><span class="sxs-lookup"><span data-stu-id="e6a7e-210">Spacing</span></span>

<span data-ttu-id="e6a7e-211">Non aggiungere spazi aggiuntivi tra parentesi quadre e parentesi:</span><span class="sxs-lookup"><span data-stu-id="e6a7e-211">Do not to add additional spaces between square brackets and parenthesis:</span></span>

#### <a name="dont"></a><span data-ttu-id="e6a7e-212">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-212">Don't</span></span>

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a><span data-ttu-id="e6a7e-213">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-213">Do</span></span>

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a><span data-ttu-id="e6a7e-214">Convenzioni di denominazione</span><span class="sxs-lookup"><span data-stu-id="e6a7e-214">Naming conventions</span></span>

<span data-ttu-id="e6a7e-215">Usare sempre `PascalCase` per le proprietà.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-215">Always use `PascalCase` for properties.</span></span> <span data-ttu-id="e6a7e-216">Usare `camelCase` per la maggior parte dei campi, ad eccezione `PascalCase` dell'uso dei `static readonly` `const` campi e.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-216">Use `camelCase` for most fields, except use `PascalCase` for `static readonly` and `const` fields.</span></span> <span data-ttu-id="e6a7e-217">L'unica eccezione è rappresentata dalle strutture di dati che richiedono la serializzazione dei campi da parte di `JsonUtility` .</span><span class="sxs-lookup"><span data-stu-id="e6a7e-217">The only exception to this is for data structures that require the fields to be serialized by the `JsonUtility`.</span></span>

#### <a name="dont"></a><span data-ttu-id="e6a7e-218">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-218">Don't</span></span>

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a><span data-ttu-id="e6a7e-219">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-219">Do</span></span>

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a><span data-ttu-id="e6a7e-220">Modificatori di accesso</span><span class="sxs-lookup"><span data-stu-id="e6a7e-220">Access modifiers</span></span>

<span data-ttu-id="e6a7e-221">Dichiarare sempre un modificatore di accesso per tutti i campi, le proprietà e i metodi.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-221">Always declare an access modifier for all fields, properties and methods.</span></span>

- <span data-ttu-id="e6a7e-222">Tutti i metodi dell'API Unity devono essere `private` per impostazione predefinita, a meno che non sia necessario eseguirne l'override in una classe derivata.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-222">All Unity API Methods should be `private` by default, unless you need to override them in a derived class.</span></span> <span data-ttu-id="e6a7e-223">In questo caso `protected` deve essere usato.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-223">In this case `protected` should be used.</span></span>

- <span data-ttu-id="e6a7e-224">I campi devono essere sempre `private` , con le `public` funzioni di accesso alle proprietà o `protected` .</span><span class="sxs-lookup"><span data-stu-id="e6a7e-224">Fields should always be `private`, with `public` or `protected` property accessors.</span></span>

- <span data-ttu-id="e6a7e-225">Usare [membri con corpo di espressione](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) e [proprietà automatiche](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) laddove possibile</span><span class="sxs-lookup"><span data-stu-id="e6a7e-225">Use [expression-bodied members](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) and [auto properties](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) where possible</span></span>

#### <a name="dont"></a><span data-ttu-id="e6a7e-226">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-226">Don't</span></span>

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a><span data-ttu-id="e6a7e-227">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-227">Do</span></span>

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a><span data-ttu-id="e6a7e-228">USA parentesi graffe</span><span class="sxs-lookup"><span data-stu-id="e6a7e-228">Use braces</span></span>

<span data-ttu-id="e6a7e-229">Usare sempre le parentesi graffe dopo ogni blocco di istruzioni e posizionarle nella riga successiva.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-229">Always use braces after each statement block, and place them on the next line.</span></span>

#### <a name="dont"></a><span data-ttu-id="e6a7e-230">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-230">Don't</span></span>

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a><span data-ttu-id="e6a7e-231">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-231">Don't</span></span>

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a><span data-ttu-id="e6a7e-232">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-232">Do</span></span>

```c#
private Foo()
{
    if (Bar==true)
    {
        DoThing();
    }
    else
    {
        DoTheOtherThing();
    }
}
```

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a><span data-ttu-id="e6a7e-233">Le classi, gli struct e le enumerazioni pubbliche dovrebbero tutti entrare nei propri file</span><span class="sxs-lookup"><span data-stu-id="e6a7e-233">Public classes, structs, and enums should all go in their own files</span></span>

<span data-ttu-id="e6a7e-234">Se la classe, lo struct o l'enum può essere reso privato, è accettabile essere incluso nello stesso file.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-234">If the class, struct, or enum can be made private then it's okay to be included in the same file.</span></span>  <span data-ttu-id="e6a7e-235">In questo modo si evitano i problemi di compilazione con Unity e si garantisce che si verifichi l'astrazione corretta del codice, ma anche i conflitti e le modifiche di rilievo quando il codice deve essere modificato</span><span class="sxs-lookup"><span data-stu-id="e6a7e-235">This avoids compilations issues with Unity and ensure that proper code abstraction occurs, it also reduces conflicts and breaking changes when code needs to change.</span></span>

#### <a name="dont"></a><span data-ttu-id="e6a7e-236">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-236">Don't</span></span>

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a><span data-ttu-id="e6a7e-237">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-237">Do</span></span>

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a><span data-ttu-id="e6a7e-238">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-238">Do</span></span>

<span data-ttu-id="e6a7e-239">Struct. cs</span><span class="sxs-lookup"><span data-stu-id="e6a7e-239">MyStruct.cs</span></span>

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

<span data-ttu-id="e6a7e-240">MyEnumType. cs</span><span class="sxs-lookup"><span data-stu-id="e6a7e-240">MyEnumType.cs</span></span>

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

<span data-ttu-id="e6a7e-241">MyClass. cs</span><span class="sxs-lookup"><span data-stu-id="e6a7e-241">MyClass.cs</span></span>

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a><span data-ttu-id="e6a7e-242">Inizializzazione delle enumerazioni</span><span class="sxs-lookup"><span data-stu-id="e6a7e-242">Initialize enums</span></span>

<span data-ttu-id="e6a7e-243">Per assicurarsi che tutte le enumerazioni siano inizializzate correttamente a partire da 0, .NET fornisce un collegamento ordinato per inizializzare automaticamente l'enumerazione aggiungendo il primo valore (Starter).</span><span class="sxs-lookup"><span data-stu-id="e6a7e-243">To ensure all enums are initialized correctly starting at 0, .NET gives you a tidy shortcut to automatically initialize the enum by just adding the first (starter) value.</span></span> <span data-ttu-id="e6a7e-244">(ad esempio, il valore 1 = 0 valori rimanenti non sono obbligatori)</span><span class="sxs-lookup"><span data-stu-id="e6a7e-244">(e.g Value 1 = 0 Remaining values are not required)</span></span>

#### <a name="dont"></a><span data-ttu-id="e6a7e-245">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-245">Don't</span></span>

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a><span data-ttu-id="e6a7e-246">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-246">Do</span></span>

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a><span data-ttu-id="e6a7e-247">Ordina enumerazioni per l'estensione appropriata</span><span class="sxs-lookup"><span data-stu-id="e6a7e-247">Order enums for appropriate extension</span></span>

<span data-ttu-id="e6a7e-248">È fondamentale che se è probabile che un'enumerazione venga estesa in futuro, per ordinare le impostazioni predefinite all'inizio dell'enumerazione, ciò garantisce che gli indici enum non siano interessati da nuove aggiunte.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-248">It is critical that if an Enum is likely to be extended in the future, to order defaults at the top of the Enum, this ensures Enum indexes are not affected with new additions.</span></span>

#### <a name="dont"></a><span data-ttu-id="e6a7e-249">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-249">Don't</span></span>

```c#
public enum SDKType
{
    WindowsMR,
    OpenVR,
    OpenXR,
    None, <- default value not at start
    Other <- anonymous value left to end of enum
}
```

#### <a name="do"></a><span data-ttu-id="e6a7e-250">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-250">Do</span></span>

```c#
/// <summary>
/// The SDKType lists the VR SDKs that are supported by the MRTK
/// Initially, this lists proposed SDKs, not all may be implemented at this time (please see ReleaseNotes for more details)
/// </summary>
public enum SDKType
{
    /// <summary>
    /// No specified type or Standalone / non-VR type
    /// </summary>
    None = 0,
    /// <summary>
    /// Undefined SDK.
    /// </summary>
    Other,
    /// <summary>
    /// The Windows 10 Mixed reality SDK provided by the Universal Windows Platform (UWP), for Immersive MR headsets and HoloLens.
    /// </summary>
    WindowsMR,
    /// <summary>
    /// The OpenVR platform provided by Unity (does not support the downloadable SteamVR SDK).
    /// </summary>
    OpenVR,
    /// <summary>
    /// The OpenXR platform. SDK to be determined once released.
    /// </summary>
    OpenXR
}
```

### <a name="review-enum-use-for-bitfields"></a><span data-ttu-id="e6a7e-251">Esaminare l'uso di enum per campi</span><span class="sxs-lookup"><span data-stu-id="e6a7e-251">Review enum use for bitfields</span></span>

<span data-ttu-id="e6a7e-252">Se è possibile che un'enumerazione richieda più Stati come valore, ad esempio manualità = Left & right.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-252">If there is a possibility for an enum to require multiple states as a value, e.g. Handedness = Left & Right.</span></span> <span data-ttu-id="e6a7e-253">L'enumerazione deve quindi essere decorata correttamente con flag per consentirne l'uso corretto</span><span class="sxs-lookup"><span data-stu-id="e6a7e-253">Then the Enum needs to be decorated correctly with BitFlags to enable it to be used correctly</span></span>

<span data-ttu-id="e6a7e-254">Il file Manuality. cs dispone di un'implementazione concreta per</span><span class="sxs-lookup"><span data-stu-id="e6a7e-254">The Handedness.cs file has a concrete implementation for this</span></span>

### <a name="dont"></a><span data-ttu-id="e6a7e-255">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-255">Don't</span></span>

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a><span data-ttu-id="e6a7e-256">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-256">Do</span></span>

```c#
[Flags]
public enum Handedness
{
    None = 0 << 0,
    Left = 1 << 0,
    Right = 1 << 1,
    Both = Left | Right
}
```

### <a name="hard-coded-file-paths"></a><span data-ttu-id="e6a7e-257">Percorsi di file hardcoded</span><span class="sxs-lookup"><span data-stu-id="e6a7e-257">Hard-coded file paths</span></span>

<span data-ttu-id="e6a7e-258">Quando si generano i percorsi dei file di stringa e, in particolare, si scrivono percorsi di stringa hardcoded, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="e6a7e-258">When generating string file paths, and in particular writing hard-coded string paths, do the following:</span></span>

1. <span data-ttu-id="e6a7e-259">Usare le [ `Path` API](https://docs.microsoft.com/dotnet/api/system.io.path?view=netframework-4.8&preserve-view=true) di C#, laddove possibile, ad esempio `Path.Combine` o `Path.GetFullPath` .</span><span class="sxs-lookup"><span data-stu-id="e6a7e-259">Use C#'s [`Path` APIs](https://docs.microsoft.com/dotnet/api/system.io.path?view=netframework-4.8&preserve-view=true) whenever possible such as `Path.Combine` or `Path.GetFullPath`.</span></span>
1. <span data-ttu-id="e6a7e-260">Utilizzare/o [`Path.DirectorySeparatorChar`](https://docs.microsoft.com/dotnet/api/system.io.path.directoryseparatorchar?view=netframework-4.8&preserve-view=true) anziché \ o \\ \\ .</span><span class="sxs-lookup"><span data-stu-id="e6a7e-260">Use / or [`Path.DirectorySeparatorChar`](https://docs.microsoft.com/dotnet/api/system.io.path.directoryseparatorchar?view=netframework-4.8&preserve-view=true) instead of \ or \\\\.</span></span>

<span data-ttu-id="e6a7e-261">Questi passaggi assicurano che MRTK funzioni nei sistemi Windows e UNIX.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-261">These steps ensure that MRTK works on both Windows and Unix-based systems.</span></span>

### <a name="dont"></a><span data-ttu-id="e6a7e-262">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-262">Don't</span></span>

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a><span data-ttu-id="e6a7e-263">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-263">Do</span></span>

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a><span data-ttu-id="e6a7e-264">Procedure consigliate, incluse le raccomandazioni Unity</span><span class="sxs-lookup"><span data-stu-id="e6a7e-264">Best practices, including Unity recommendations</span></span>

<span data-ttu-id="e6a7e-265">Per alcune delle piattaforme di destinazione di questo progetto è necessario prendere in considerazione le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-265">Some of the target platforms of this project require to take performance into consideration.</span></span> <span data-ttu-id="e6a7e-266">Tenendo presente questo aspetto, prestare attenzione quando si alloca la memoria in un codice denominato spesso in cicli o algoritmi di aggiornamento stretti.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-266">With this in mind always be careful when allocating memory in frequently called code in tight update loops or algorithms.</span></span>

### <a name="encapsulation"></a><span data-ttu-id="e6a7e-267">Incapsulamento</span><span class="sxs-lookup"><span data-stu-id="e6a7e-267">Encapsulation</span></span>

<span data-ttu-id="e6a7e-268">Usare sempre i campi privati e le proprietà pubbliche se è necessario l'accesso al campo dall'esterno della classe o dello struct.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-268">Always use private fields and public properties if access to the field is needed from outside the class or struct.</span></span>  <span data-ttu-id="e6a7e-269">Assicurarsi di condividere il percorso del campo privato e della proprietà pubblica.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-269">Be sure to co-locate the private field and the public property.</span></span> <span data-ttu-id="e6a7e-270">In questo modo è più semplice visualizzare, a colpo d'occhio, le informazioni che consentono di eseguire il backup della proprietà e che il campo è modificabile dallo script.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-270">This makes it easier to see, at a glance, what backs the property and that the field is modifiable by script.</span></span>

> [!NOTE]
> <span data-ttu-id="e6a7e-271">L'unica eccezione è rappresentata dalle strutture di dati che richiedono che i campi vengano serializzati da `JsonUtility` , in cui è necessario che una classe di dati disponga di tutti i campi pubblici affinché la serializzazione funzioni.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-271">The only exception to this is for data structures that require the fields to be serialized by the `JsonUtility`, where a data class is required to have all public fields for the serialization to work.</span></span>

#### <a name="dont"></a><span data-ttu-id="e6a7e-272">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-272">Don't</span></span>

```c#
private float myValue1;
private float myValue2;

public float MyValue1
{
    get{ return myValue1; }
    set{ myValue1 = value }
}

public float MyValue2
{
    get{ return myValue2; }
    set{ myValue2 = value }
}
```

#### <a name="do"></a><span data-ttu-id="e6a7e-273">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-273">Do</span></span>

```c#
// Enable field to be configurable in the editor and available externally to other scripts (field is correctly serialized in Unity)
[SerializeField]
[ToolTip("If using a tooltip, the text should match the public property's summary documentation, if appropriate.")]
private float myValue; // <- Notice we co-located the backing field above our corresponding property.

/// <summary>
/// If using a tooltip, the text should match the public property's summary documentation, if appropriate.
/// </summary>
public float MyValue
{
    get => myValue;
    set => myValue = value;
}

/// <summary>
/// Getter/Setters not wrapping a value directly should contain documentation comments just as public functions would
/// </summary>
public float AbsMyValue
{
    get
    {
        if (MyValue < 0)
        {
            return -MyValue;
        }

        return MyValue
    }
}
```

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a><span data-ttu-id="e6a7e-274">Memorizzare nella cache i valori e serializzarli nella scena o nella prefabbricazione, quando possibile</span><span class="sxs-lookup"><span data-stu-id="e6a7e-274">Cache values and serialize them in the scene/prefab whenever possible</span></span>

<span data-ttu-id="e6a7e-275">Tenendo presente il HoloLens, è preferibile ottimizzare per le prestazioni e i riferimenti alla cache nella scena o nel prefabbricato per limitare le allocazioni di memoria di Runtime.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-275">With the HoloLens in mind, it's best to optimize for performance and cache references in the scene or prefab to limit runtime memory allocations.</span></span>

#### <a name="dont"></a><span data-ttu-id="e6a7e-276">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-276">Don't</span></span>

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a><span data-ttu-id="e6a7e-277">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-277">Do</span></span>

```c#
[SerializeField] // To enable setting the reference in the inspector.
private Renderer myRenderer;

private void Awake()
{
    // If you didn't set it in the inspector, then we cache it on awake.
    if (myRenderer == null)
    {
        myRenderer = gameObject.GetComponent<Renderer>();
    }
}

private void Update()
{
    myRenderer.Foo(Bar);
}
```

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a><span data-ttu-id="e6a7e-278">Memorizzare nella cache i riferimenti ai materiali, non chiamare ogni volta il "materiale".</span><span class="sxs-lookup"><span data-stu-id="e6a7e-278">Cache references to materials, do not call the ".material" each time</span></span>

<span data-ttu-id="e6a7e-279">Unity creerà un nuovo materiale ogni volta che si usa ". Material", che causerà una perdita di memoria se non viene eseguita la pulizia corretta.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-279">Unity will create a new material each time you use ".material", which will cause a memory leak if not cleaned up properly.</span></span>

#### <a name="dont"></a><span data-ttu-id="e6a7e-280">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-280">Don't</span></span>

```c#
public class MyClass
{
    void Update()
    {
        Material myMaterial = GetComponent<Renderer>().material;
        myMaterial.SetColor("_Color", Color.White);
    }
}
```

#### <a name="do"></a><span data-ttu-id="e6a7e-281">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="e6a7e-281">Do</span></span>

```c#
// Private references for use inside the class only
public class MyClass
{
    private Material cachedMaterial;

    private void Awake()
    {
        cachedMaterial = GetComponent<Renderer>().material;
    }

    void Update()
    {
        cachedMaterial.SetColor("_Color", Color.White);
    }

    private void OnDestroy()
    {
        Destroy(cachedMaterial);
    }
}
```

> [!NOTE]
> <span data-ttu-id="e6a7e-282">In alternativa, usare la proprietà "SharedMaterial" di Unity che non crea un nuovo materiale ogni volta che vi si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-282">Alternatively, use Unity's "SharedMaterial" property which does not create a new material each time it is referenced.</span></span>

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a><span data-ttu-id="e6a7e-283">Usare la [compilazione dipendente dalla piattaforma](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) per assicurarsi che il Toolkit non interrompa la compilazione in un'altra piattaforma</span><span class="sxs-lookup"><span data-stu-id="e6a7e-283">Use [platform dependent compilation](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) to ensure the Toolkit won't break the build on another platform</span></span>

- <span data-ttu-id="e6a7e-284">Usare per `WINDOWS_UWP` usare API specifiche di UWP e non Unity.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-284">Use `WINDOWS_UWP` in order to use UWP-specific, non-Unity APIs.</span></span> <span data-ttu-id="e6a7e-285">In questo modo si eviterà di provare a eseguire nell'editor o su piattaforme non supportate.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-285">This will prevent them from trying to run in the Editor or on unsupported platforms.</span></span> <span data-ttu-id="e6a7e-286">Equivale a `UNITY_WSA && !UNITY_EDITOR` e deve essere usato a favore di.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-286">This is equivalent to `UNITY_WSA && !UNITY_EDITOR` and should be used in favor of.</span></span>
- <span data-ttu-id="e6a7e-287">Usare `UNITY_WSA` per usare le API Unity specifiche di UWP, ad esempio lo `UnityEngine.XR.WSA` spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-287">Use `UNITY_WSA` to use UWP-specific Unity APIs, such as the `UnityEngine.XR.WSA` namespace.</span></span> <span data-ttu-id="e6a7e-288">Questa operazione verrà eseguita nell'editor quando la piattaforma è impostata su UWP, oltre che nelle app UWP compilate.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-288">This will run in the Editor when the platform is set to UWP, as well as in built UWP apps.</span></span>

<span data-ttu-id="e6a7e-289">Questo grafico può essere utile per decidere quale `#if` usare, a seconda dei casi d'uso e delle impostazioni di compilazione previsti.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-289">This chart can help you decide which `#if` to use, depending on your use cases and the build settings you expect.</span></span>

|<span data-ttu-id="e6a7e-290">Piattaforma</span><span class="sxs-lookup"><span data-stu-id="e6a7e-290">Platform</span></span> | <span data-ttu-id="e6a7e-291">IL2CPP UWP</span><span class="sxs-lookup"><span data-stu-id="e6a7e-291">UWP IL2CPP</span></span> | <span data-ttu-id="e6a7e-292">UWP .NET</span><span class="sxs-lookup"><span data-stu-id="e6a7e-292">UWP .NET</span></span> | <span data-ttu-id="e6a7e-293">Editor</span><span class="sxs-lookup"><span data-stu-id="e6a7e-293">Editor</span></span> |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | <span data-ttu-id="e6a7e-294">False</span><span class="sxs-lookup"><span data-stu-id="e6a7e-294">False</span></span> | <span data-ttu-id="e6a7e-295">False</span><span class="sxs-lookup"><span data-stu-id="e6a7e-295">False</span></span> | <span data-ttu-id="e6a7e-296">True</span><span class="sxs-lookup"><span data-stu-id="e6a7e-296">True</span></span> |
| `UNITY_WSA` | <span data-ttu-id="e6a7e-297">True</span><span class="sxs-lookup"><span data-stu-id="e6a7e-297">True</span></span> | <span data-ttu-id="e6a7e-298">True</span><span class="sxs-lookup"><span data-stu-id="e6a7e-298">True</span></span> | <span data-ttu-id="e6a7e-299">True</span><span class="sxs-lookup"><span data-stu-id="e6a7e-299">True</span></span> |
| `WINDOWS_UWP` | <span data-ttu-id="e6a7e-300">True</span><span class="sxs-lookup"><span data-stu-id="e6a7e-300">True</span></span> | <span data-ttu-id="e6a7e-301">True</span><span class="sxs-lookup"><span data-stu-id="e6a7e-301">True</span></span> | <span data-ttu-id="e6a7e-302">False</span><span class="sxs-lookup"><span data-stu-id="e6a7e-302">False</span></span> |
| `UNITY_WSA && !UNITY_EDITOR` | <span data-ttu-id="e6a7e-303">True</span><span class="sxs-lookup"><span data-stu-id="e6a7e-303">True</span></span> | <span data-ttu-id="e6a7e-304">True</span><span class="sxs-lookup"><span data-stu-id="e6a7e-304">True</span></span> | <span data-ttu-id="e6a7e-305">False</span><span class="sxs-lookup"><span data-stu-id="e6a7e-305">False</span></span> |
| `ENABLE_WINMD_SUPPORT` | <span data-ttu-id="e6a7e-306">True</span><span class="sxs-lookup"><span data-stu-id="e6a7e-306">True</span></span> | <span data-ttu-id="e6a7e-307">True</span><span class="sxs-lookup"><span data-stu-id="e6a7e-307">True</span></span> | <span data-ttu-id="e6a7e-308">False</span><span class="sxs-lookup"><span data-stu-id="e6a7e-308">False</span></span> |
| `NETFX_CORE` | <span data-ttu-id="e6a7e-309">False</span><span class="sxs-lookup"><span data-stu-id="e6a7e-309">False</span></span> | <span data-ttu-id="e6a7e-310">True</span><span class="sxs-lookup"><span data-stu-id="e6a7e-310">True</span></span> | <span data-ttu-id="e6a7e-311">Falso</span><span class="sxs-lookup"><span data-stu-id="e6a7e-311">False</span></span> |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a><span data-ttu-id="e6a7e-312">Preferisci DateTime. UtcNow su DateTime. Now</span><span class="sxs-lookup"><span data-stu-id="e6a7e-312">Prefer DateTime.UtcNow over DateTime.Now</span></span>

<span data-ttu-id="e6a7e-313">DateTime. UtcNow è più veloce di DateTime. Now.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-313">DateTime.UtcNow is faster than DateTime.Now.</span></span> <span data-ttu-id="e6a7e-314">Nelle analisi delle prestazioni precedenti è stato rilevato che l'utilizzo di DateTime. ora aggiunge un sovraccarico significativo soprattutto se utilizzato nel ciclo Update ().</span><span class="sxs-lookup"><span data-stu-id="e6a7e-314">In previous performance investigations we've found that using DateTime.Now adds significant overhead especially when used in the Update() loop.</span></span> <span data-ttu-id="e6a7e-315">[Altri hanno raggiunto lo stesso problema](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now).</span><span class="sxs-lookup"><span data-stu-id="e6a7e-315">[Others have hit the same issue](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now).</span></span>

<span data-ttu-id="e6a7e-316">Preferire l'uso di DateTime. UtcNow, a meno che non siano effettivamente necessarie le ore localizzate (un motivo legittimo potrebbe essere quello di visualizzare l'ora corrente nel fuso orario dell'utente).</span><span class="sxs-lookup"><span data-stu-id="e6a7e-316">Prefer using DateTime.UtcNow unless you actually need the localized times (a legitimate reason may be you wanting to show the current time in the user's time zone).</span></span> <span data-ttu-id="e6a7e-317">Se si gestiscono le ore relative (ad esempio, il delta tra un ultimo aggiornamento e ora), è preferibile usare DateTime. UtcNow per evitare il sovraccarico dovuto alla conversione del fuso orario.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-317">If you are dealing with relative times (i.e. the delta between some last update and now), it's best to use DateTime.UtcNow to avoid the overhead of doing timezone conversions.</span></span>

## <a name="powershell-coding-conventions"></a><span data-ttu-id="e6a7e-318">Convenzioni di codifica di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e6a7e-318">PowerShell coding conventions</span></span>

<span data-ttu-id="e6a7e-319">Un subset della codebase MRTK USA PowerShell per l'infrastruttura della pipeline e vari script e utilità.</span><span class="sxs-lookup"><span data-stu-id="e6a7e-319">A subset of the MRTK codebase uses PowerShell for pipeline infrastructure and various scripts and utilities.</span></span> <span data-ttu-id="e6a7e-320">Il nuovo codice PowerShell deve seguire lo [stile PoshCode](https://poshcode.gitbooks.io/powershell-practice-and-style/).</span><span class="sxs-lookup"><span data-stu-id="e6a7e-320">New PowerShell code should follow the [PoshCode style](https://poshcode.gitbooks.io/powershell-practice-and-style/).</span></span>

## <a name="see-also"></a><span data-ttu-id="e6a7e-321">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="e6a7e-321">See also</span></span>

 [<span data-ttu-id="e6a7e-322">Convenzioni di codifica C# da MSDN</span><span class="sxs-lookup"><span data-stu-id="e6a7e-322">C# coding conventions from MSDN</span></span>](https://docs.microsoft.com/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)
