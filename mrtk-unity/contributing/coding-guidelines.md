---
title: Linee guida sulla codifica
description: Principi e convenzioni di codifica da seguire quando si contribuisce a MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, C#,
ms.openlocfilehash: c14f5f72d391c5474a01c798bfdaa5529700a509
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175330"
---
# <a name="coding-guidelines"></a><span data-ttu-id="7fa4d-104">Linee guida sulla codifica</span><span class="sxs-lookup"><span data-stu-id="7fa4d-104">Coding guidelines</span></span>

<span data-ttu-id="7fa4d-105">Questo documento illustra i principi e le convenzioni di codifica da seguire quando si contribuisce a MRTK.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-105">This document outlines coding principles and conventions to follow when contributing to MRTK.</span></span>

---

## <a name="philosophy"></a><span data-ttu-id="7fa4d-106">Filosofia</span><span class="sxs-lookup"><span data-stu-id="7fa4d-106">Philosophy</span></span>

### <a name="be-concise-and-strive-for-simplicity"></a><span data-ttu-id="7fa4d-107">Essere concisi e cercare semplicità</span><span class="sxs-lookup"><span data-stu-id="7fa4d-107">Be concise and strive for simplicity</span></span>

<span data-ttu-id="7fa4d-108">La soluzione più semplice è spesso la migliore.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-108">The simplest solution is often the best.</span></span> <span data-ttu-id="7fa4d-109">Si tratta di un obiettivo di override di queste linee guida e deve essere l'obiettivo di tutte le attività di codifica.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-109">This is an overriding aim of these guidelines and should be the goal of all coding activity.</span></span> <span data-ttu-id="7fa4d-110">Una parte di essere semplice è essere concisa e coerente con il codice esistente.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-110">Part of being simple is being concise, and consistent with existing code.</span></span> <span data-ttu-id="7fa4d-111">Provare a mantenere il codice semplice.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-111">Try to keep your code simple.</span></span>

<span data-ttu-id="7fa4d-112">I lettori devono riscontrare solo elementi che forniscono informazioni utili.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-112">Readers should only encounter artifacts that provide useful information.</span></span> <span data-ttu-id="7fa4d-113">Ad esempio, i commenti che restate ciò che è ovvio non forniscono informazioni aggiuntive e aumentano il rapporto rumore-segnale.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-113">For example, comments that restate what is obvious provide no extra information and increase the noise to signal ratio.</span></span>

<span data-ttu-id="7fa4d-114">Mantenere semplice la logica del codice.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-114">Keep code logic simple.</span></span> <span data-ttu-id="7fa4d-115">Si noti che non si tratta di un'istruzione sull'uso del numero più ridotto di righe, riducendo al minimo le dimensioni dei nomi degli identificatori o dello stile delle parentesi graffe, ma sulla riduzione del numero di concetti e sull'ottimizzazione della visibilità di tali righe tramite modelli familiari.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-115">Note that this is not a statement about using the fewest number of lines, minimizing the size of identifier names or brace style, but about reducing the number of concepts and maximizing the visibility of those through familiar patterns.</span></span>

### <a name="produce-consistent-readable-code"></a><span data-ttu-id="7fa4d-116">Produrre codice coerente e leggibile</span><span class="sxs-lookup"><span data-stu-id="7fa4d-116">Produce consistent, readable code</span></span>

<span data-ttu-id="7fa4d-117">La leggibilità del codice è correlata alle basse percentuali di difetti.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-117">Code readability is correlated with low defect rates.</span></span> <span data-ttu-id="7fa4d-118">Cercare di creare codice di facile lettura.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-118">Strive to create code that is easy to read.</span></span> <span data-ttu-id="7fa4d-119">Cercare di creare codice con logica semplice e di ri-usare i componenti esistenti perché consente anche di garantire la correttezza.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-119">Strive to create code that has simple logic and re-uses existing components as it will also help ensure correctness.</span></span>

<span data-ttu-id="7fa4d-120">Tutti i dettagli del codice prodotto sono importanti, dal dettaglio più semplice della correttezza allo stile e alla formattazione coerenti.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-120">All details of the code you produce matter, from the most basic detail of correctness to consistent style and formatting.</span></span> <span data-ttu-id="7fa4d-121">Mantenere lo stile di codifica coerente con ciò che esiste già, anche se non corrisponde alle preferenze.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-121">Keep your coding style consistent with what already exists, even if it is not matching your preference.</span></span> <span data-ttu-id="7fa4d-122">Ciò aumenta la leggibilità della codebase complessiva.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-122">This increases the readability of the overall codebase.</span></span>

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a><span data-ttu-id="7fa4d-123">Supporto della configurazione dei componenti sia nell'editor che in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="7fa4d-123">Support configuring components both in editor and at run-time</span></span>

<span data-ttu-id="7fa4d-124">MRTK supporta un set diversificato di utenti: utenti che preferiscono configurare i componenti nell'editor di Unity e caricare i prefab e utenti che devono creare istanze e configurare oggetti in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-124">MRTK supports a diverse set of users – people who prefer to configure components in the Unity editor and load prefabs, and people who need to instantiate and configure objects at run-time.</span></span>

<span data-ttu-id="7fa4d-125">Tutto il codice dovrebbe funzionare aggiungendo un componente a gameobject in una scena salvata e creando un'istanza di tale componente nel codice.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-125">All your code should work by BOTH adding a component to a GameObject in a saved scene, and by instantiating that component in code.</span></span> <span data-ttu-id="7fa4d-126">I test devono includere un test case per la creazione di istanze di prefab e la creazione di istanze, la configurazione del componente in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-126">Tests should include a test case both for instantiating prefabs and instantiating, configuring the component at runtime.</span></span>

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a><span data-ttu-id="7fa4d-127">Play-in-editor è la prima piattaforma di destinazione primaria</span><span class="sxs-lookup"><span data-stu-id="7fa4d-127">Play-in-editor is your first and primary target platform</span></span>

<span data-ttu-id="7fa4d-128">Play-In-Editor è il modo più rapido per eseguire l'iterazione in Unity.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-128">Play-In-Editor is the fastest way to iterate in Unity.</span></span> <span data-ttu-id="7fa4d-129">Offrire ai clienti la possibilità di eseguire rapidamente l'iterazione consente di sviluppare soluzioni più rapidamente e di provare altre idee.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-129">Providing ways for our customers to iterate quickly allows them to both develop solutions more quickly and try out more ideas.</span></span> <span data-ttu-id="7fa4d-130">In altre parole, ottimizzare la velocità di iterazione consente ai clienti di ottenere di più.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-130">In other words, maximizing the speed of iteration empowers our customers to achieve more.</span></span>

<span data-ttu-id="7fa4d-131">Fare in modo che tutto funzioni nell'editor e quindi farlo funzionare in qualsiasi altra piattaforma.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-131">Make everything work in editor, then make it work on any other platform.</span></span> <span data-ttu-id="7fa4d-132">Mantenere il funzionamento nell'editor.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-132">Keep it working in the editor.</span></span> <span data-ttu-id="7fa4d-133">È facile aggiungere una nuova piattaforma a Play-In-Editor.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-133">It is easy to add a new platform to Play-In-Editor.</span></span> <span data-ttu-id="7fa4d-134">È molto difficile far funzionare Play-In-Editor se l'app funziona solo in un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-134">It is very difficult to get Play-In-Editor working if your app only works on a device.</span></span>

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a><span data-ttu-id="7fa4d-135">Aggiungere nuovi campi pubblici, proprietà, metodi e campi privati serializzati con attenzione</span><span class="sxs-lookup"><span data-stu-id="7fa4d-135">Add new public fields, properties, methods and serialized private fields with care</span></span>

<span data-ttu-id="7fa4d-136">Ogni volta che si aggiunge un metodo pubblico, un campo, una proprietà, questo diventa parte della superficie api pubblica di MRTK.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-136">Every time you add a public method, field, property, it becomes part of MRTK’s public API surface.</span></span> <span data-ttu-id="7fa4d-137">I campi privati contrassegnati `[SerializeField]` con espongono anche i campi all'editor e fanno parte della superficie api pubblica.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-137">Private fields marked with `[SerializeField]` also expose fields to the editor and are part of the public API surface.</span></span> <span data-ttu-id="7fa4d-138">Altri utenti potrebbero usare questo metodo pubblico, configurare prefab personalizzati con il campo pubblico e assumere una dipendenza da esso.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-138">Other people might use that public method, configure custom prefabs with your public field, and take a dependency on it.</span></span>

<span data-ttu-id="7fa4d-139">I nuovi membri pubblici devono essere esaminati con attenzione.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-139">New public members should be carefully examined.</span></span> <span data-ttu-id="7fa4d-140">Qualsiasi campo pubblico dovrà essere gestito in futuro.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-140">Any public field will need to be maintained in the future.</span></span> <span data-ttu-id="7fa4d-141">Tenere presente che se il tipo di un campo pubblico (o di un campo privato serializzato) cambia o viene rimosso da un oggetto MonoBehaviour, ciò potrebbe interrompere altri utenti.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-141">Remember that if the type of a public field (or serialized private field) changes or gets removed from a MonoBehaviour, that could break other people.</span></span> <span data-ttu-id="7fa4d-142">Il campo dovrà prima essere deprecato per una versione e il codice per eseguire la migrazione delle modifiche per gli utenti che hanno assunto dipendenze dovrà essere fornito.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-142">The field will need to first be deprecated for a release, and code to migrate changes for people that have taken dependencies would need to be provided.</span></span>

### <a name="prioritize-writing-tests"></a><span data-ttu-id="7fa4d-143">Assegnare priorità alla scrittura di test</span><span class="sxs-lookup"><span data-stu-id="7fa4d-143">Prioritize writing tests</span></span>

<span data-ttu-id="7fa4d-144">MRTK è un progetto della community, modificato da una vasta gamma di collaboratori.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-144">MRTK is a community project, modified by a diverse range of contributors.</span></span> <span data-ttu-id="7fa4d-145">Questi collaboratori potrebbero non conoscere i dettagli della correzione/funzionalità dei bug e interrompere accidentalmente la funzionalità.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-145">These contributors may not know the details of your bug fix / feature, and accidentally break your feature.</span></span> <span data-ttu-id="7fa4d-146">[MRTK esegue test di integrazione continua](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) prima di completare ogni richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-146">[MRTK runs continuous integration tests](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) before completing every pull request.</span></span> <span data-ttu-id="7fa4d-147">Le modifiche che interrompno i test non possono essere archiviate.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-147">Changes that break tests cannot be checked in.</span></span> <span data-ttu-id="7fa4d-148">Pertanto, i test sono il modo migliore per garantire che altri utenti non interrompano la funzionalità.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-148">Therefore, tests are the best way to ensure that other people do not break your feature.</span></span>

<span data-ttu-id="7fa4d-149">Quando si corregge un bug, scrivere un test per assicurarsi che non regredisca in futuro.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-149">When you fix a bug, write a test to ensure it does not regress in the future.</span></span> <span data-ttu-id="7fa4d-150">Se si aggiunge una funzionalità, scrivere test che verificano il funzionamento della funzionalità.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-150">If adding a feature, write tests that verify your feature works.</span></span> <span data-ttu-id="7fa4d-151">Questa operazione è necessaria per tutte le funzionalità dell'esperienza utente, ad eccezione delle funzionalità sperimentali.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-151">This is required for all UX features except experimental features.</span></span>

## <a name="c-coding-conventions"></a><span data-ttu-id="7fa4d-152">Convenzioni di codifica C#</span><span class="sxs-lookup"><span data-stu-id="7fa4d-152">C# Coding conventions</span></span>

### <a name="script-license-information-headers"></a><span data-ttu-id="7fa4d-153">Intestazioni delle informazioni sulla licenza di script</span><span class="sxs-lookup"><span data-stu-id="7fa4d-153">Script license information headers</span></span>

<span data-ttu-id="7fa4d-154">Tutti i dipendenti Microsoft che contribuiscono a nuovi file devono aggiungere l'intestazione Licenza standard seguente nella parte superiore di tutti i nuovi file, esattamente come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="7fa4d-154">All Microsoft employees contributing new files should add the following standard License header at the top of any new files, exactly as shown below:</span></span>

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a><span data-ttu-id="7fa4d-155">Intestazioni di riepilogo di funzioni/metodi</span><span class="sxs-lookup"><span data-stu-id="7fa4d-155">Function / method summary headers</span></span>

<span data-ttu-id="7fa4d-156">Tutte le classi pubbliche, gli struct, le enumerazioni, le funzioni, le proprietà, i campi inseriti in MRTK devono essere descritti in base allo scopo e all'uso, esattamente come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="7fa4d-156">All public classes, structs, enums, functions, properties, fields posted to the MRTK should be described as to its purpose and use, exactly as shown below:</span></span>

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

<span data-ttu-id="7fa4d-157">In questo modo la documentazione viene generata e diffusa correttamente per tutte le classi, i metodi e le proprietà.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-157">This ensures documentation is properly generated and disseminated for all all classes, methods, and properties.</span></span>

<span data-ttu-id="7fa4d-158">Tutti i file script inviati senza tag di riepilogo adeguati verranno rifiutati.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-158">Any script files submitted without proper summary tags will be rejected.</span></span>

### <a name="mrtk-namespace-rules"></a><span data-ttu-id="7fa4d-159">Regole dello spazio dei nomi MRTK</span><span class="sxs-lookup"><span data-stu-id="7fa4d-159">MRTK namespace rules</span></span>

<span data-ttu-id="7fa4d-160">L'Toolkit realtà mista usa un modello di spazio dei nomi basato su funzionalità, in cui tutti gli spazi dei nomi di base iniziano con "Microsoft.MixedReality. Toolkit".</span><span class="sxs-lookup"><span data-stu-id="7fa4d-160">The Mixed Reality Toolkit uses a feature based namespace model, where all foundational namespaces begin with "Microsoft.MixedReality.Toolkit".</span></span> <span data-ttu-id="7fa4d-161">In generale, non è necessario specificare il livello del toolkit (ad esempio Core, Provider, Servizi) negli spazi dei nomi.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-161">In general, you need not specify the toolkit layer (ex: Core, Providers, Services) in your namespaces.</span></span>

<span data-ttu-id="7fa4d-162">Gli spazi dei nomi attualmente definiti sono:</span><span class="sxs-lookup"><span data-stu-id="7fa4d-162">The currently defined namespaces are:</span></span>

- <span data-ttu-id="7fa4d-163">Microsoft.MixedReality. Toolkit</span><span class="sxs-lookup"><span data-stu-id="7fa4d-163">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="7fa4d-164">Microsoft.MixedReality. Toolkit. Confine</span><span class="sxs-lookup"><span data-stu-id="7fa4d-164">Microsoft.MixedReality.Toolkit.Boundary</span></span>
- <span data-ttu-id="7fa4d-165">Microsoft.MixedReality. Toolkit. Diagnostica</span><span class="sxs-lookup"><span data-stu-id="7fa4d-165">Microsoft.MixedReality.Toolkit.Diagnostics</span></span>
- <span data-ttu-id="7fa4d-166">Microsoft.MixedReality. Toolkit. Editore</span><span class="sxs-lookup"><span data-stu-id="7fa4d-166">Microsoft.MixedReality.Toolkit.Editor</span></span>
- <span data-ttu-id="7fa4d-167">Microsoft.MixedReality. Toolkit. Input</span><span class="sxs-lookup"><span data-stu-id="7fa4d-167">Microsoft.MixedReality.Toolkit.Input</span></span>
- <span data-ttu-id="7fa4d-168">Microsoft.MixedReality. Toolkit. SpatialAwareness</span><span class="sxs-lookup"><span data-stu-id="7fa4d-168">Microsoft.MixedReality.Toolkit.SpatialAwareness</span></span>
- <span data-ttu-id="7fa4d-169">Microsoft.MixedReality. Toolkit. Teletrasporto</span><span class="sxs-lookup"><span data-stu-id="7fa4d-169">Microsoft.MixedReality.Toolkit.Teleport</span></span>
- <span data-ttu-id="7fa4d-170">Microsoft.MixedReality. Toolkit. Utilità</span><span class="sxs-lookup"><span data-stu-id="7fa4d-170">Microsoft.MixedReality.Toolkit.Utilities</span></span>

<span data-ttu-id="7fa4d-171">Per gli spazi dei nomi con una grande quantità di tipi, è accettabile creare un numero limitato di sotto-spazi dei nomi per facilitare l'utilizzo dell'ambito.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-171">For namespaces with a large amount of types, it is acceptable to create a limited number of sub-namespaces to aid in scoping usage.</span></span>

<span data-ttu-id="7fa4d-172">Se si omette lo spazio dei nomi per un'interfaccia, una classe o un tipo di dati, la modifica verrà bloccata.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-172">Omitting the namespace for an interface, class or data type will cause your change to be blocked.</span></span>

### <a name="adding-new-monobehaviour-scripts"></a><span data-ttu-id="7fa4d-173">Aggiunta di nuovi script MonoBehaviour</span><span class="sxs-lookup"><span data-stu-id="7fa4d-173">Adding new MonoBehaviour scripts</span></span>

<span data-ttu-id="7fa4d-174">Quando si aggiungono nuovi script MonoBehaviour con una richiesta pull, assicurarsi che [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) l'attributo sia applicato a tutti i file applicabili.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-174">When adding new MonoBehaviour scripts with a pull request, ensure the [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) attribute is applied to all applicable files.</span></span> <span data-ttu-id="7fa4d-175">In questo modo il componente è facilmente individuabile nell'editor sotto il *pulsante Aggiungi* componente.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-175">This ensures the component is easily discoverable in the editor under the *Add Component* button.</span></span> <span data-ttu-id="7fa4d-176">Il flag di attributo non è necessario se il componente non può essere visualizzato nell'editor, ad esempio una classe astratta.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-176">The attribute flag is not necessary if the component cannot show up in editor such as an abstract class.</span></span>

<span data-ttu-id="7fa4d-177">Nell'esempio seguente il *pacchetto* deve essere compilato con il percorso del pacchetto del componente.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-177">In the example below, the *Package here* should be filled with the package location of the component.</span></span> <span data-ttu-id="7fa4d-178">Se si inserisce un *elemento nella cartella MRTK/SDK,* il pacchetto sarà *SDK.*</span><span class="sxs-lookup"><span data-stu-id="7fa4d-178">If placing an item in *MRTK/SDK* folder, then the package will be *SDK*.</span></span>

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a><span data-ttu-id="7fa4d-179">Aggiunta di nuovi script di controllo unity</span><span class="sxs-lookup"><span data-stu-id="7fa4d-179">Adding new Unity inspector scripts</span></span>

<span data-ttu-id="7fa4d-180">In generale, provare a evitare di creare script di controllo personalizzati per i componenti MRTK.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-180">In general, try to avoid creating custom inspector scripts for MRTK components.</span></span> <span data-ttu-id="7fa4d-181">Aggiunge un sovraccarico aggiuntivo e la gestione della codebase che può essere gestita dal motore unity.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-181">It adds additional overhead and management of the codebase that could be handled by the Unity engine.</span></span>

<span data-ttu-id="7fa4d-182">Se è necessaria una classe inspector, provare a usare . [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html)</span><span class="sxs-lookup"><span data-stu-id="7fa4d-182">If an inspector class is necessary, try to use Unity's [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html).</span></span> <span data-ttu-id="7fa4d-183">Questo semplifica di nuovo la classe inspector e lascia gran parte del lavoro a Unity.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-183">This again simplifies the inspector class and leaves much of the work to Unity.</span></span>

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

<span data-ttu-id="7fa4d-184">Se è necessario eseguire il rendering personalizzato nella classe inspector, provare a utilizzare [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) e [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) .</span><span class="sxs-lookup"><span data-stu-id="7fa4d-184">If custom rendering is required in the inspector class, try to utilize [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) and [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html).</span></span> <span data-ttu-id="7fa4d-185">In questo modo Unity gestisce correttamente il rendering dei prefab annidati e dei valori modificati.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-185">This will ensure Unity correctly handles rendering nested prefabs and modified values.</span></span>

<span data-ttu-id="7fa4d-186">Se [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) non è possibile usare a causa di un requisito nella logica personalizzata, assicurarsi che tutto l'utilizzo sia racchiuso in un oggetto [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) .</span><span class="sxs-lookup"><span data-stu-id="7fa4d-186">If [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) cannot be used due to a requirement in custom logic, ensure all usage is wrapped around a [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html).</span></span> <span data-ttu-id="7fa4d-187">In questo modo Unity esegue correttamente il rendering del controllo per i prefab annidati e i valori modificati con la proprietà specificata.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-187">This will ensure Unity renders the inspector correctly for nested prefabs and modified values with the given property.</span></span>

<span data-ttu-id="7fa4d-188">Provare inoltre a decorare la classe inspector personalizzata con un [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) oggetto .</span><span class="sxs-lookup"><span data-stu-id="7fa4d-188">Furthermore, try to decorate the custom inspector class with a [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html).</span></span> <span data-ttu-id="7fa4d-189">Questo tag garantisce che più oggetti con questo componente nella scena possano essere selezionati e modificati insieme.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-189">This tag ensure multiple objects with this component in the scene can be selected and modified together.</span></span> <span data-ttu-id="7fa4d-190">Qualsiasi nuova classe inspector deve testare che il codice funzioni in questa situazione nella scena.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-190">Any new inspector classes should test that their code works in this situation in the scene.</span></span>

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

### <a name="adding-new-scriptableobjects"></a><span data-ttu-id="7fa4d-191">Aggiunta di nuovi oggetti ScriptableObject</span><span class="sxs-lookup"><span data-stu-id="7fa4d-191">Adding new ScriptableObjects</span></span>

<span data-ttu-id="7fa4d-192">Quando si aggiungono nuovi script ScriptableObject, assicurarsi che [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) l'attributo sia applicato a tutti i file applicabili.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-192">When adding new ScriptableObject scripts, ensure the [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) attribute is applied to all applicable files.</span></span> <span data-ttu-id="7fa4d-193">Ciò garantisce che il componente sia facilmente individuabile nell'editor tramite i menu di creazione dell'asset.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-193">This ensures the component is easily discoverable in the editor via the asset creation menus.</span></span> <span data-ttu-id="7fa4d-194">Il flag di attributo non è necessario se il componente non può essere visualizzato nell'editor, ad esempio una classe astratta.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-194">The attribute flag is not necessary if the component cannot show up in editor such as an abstract class.</span></span>

<span data-ttu-id="7fa4d-195">Nell'esempio seguente la *sottocartella* deve essere compilata con la sottocartella MRTK, se applicabile.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-195">In the example below, the *Subfolder* should be filled with the MRTK subfolder, if applicable.</span></span> <span data-ttu-id="7fa4d-196">Se si inserisce un *elemento nella cartella MRTK/Providers,* il pacchetto sarà *Providers*.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-196">If placing an item in *MRTK/Providers* folder, then the package will be *Providers*.</span></span> <span data-ttu-id="7fa4d-197">Se si inserisce un elemento nella *cartella MRTK/Core,* impostarla su "Profiles".</span><span class="sxs-lookup"><span data-stu-id="7fa4d-197">If placing an item in the *MRTK/Core* folder, set this to "Profiles".</span></span>

<span data-ttu-id="7fa4d-198">Nell'esempio seguente, *myNewService | MyNewProvider deve* essere compilato con il nome della nuova classe, se applicabile.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-198">In the example below, the *MyNewService | MyNewProvider* should be filled with the your new class' name, if applicable.</span></span> <span data-ttu-id="7fa4d-199">Se si inserisce un elemento *nella cartella MixedRealityToolkit,* lasciare vuota questa stringa.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-199">If placing an item in the *MixedRealityToolkit* folder, leave this string out.</span></span>

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a><span data-ttu-id="7fa4d-200">Registrazione</span><span class="sxs-lookup"><span data-stu-id="7fa4d-200">Logging</span></span>

<span data-ttu-id="7fa4d-201">Quando si aggiungono nuove funzionalità o si aggiornano le funzionalità esistenti, è consigliabile aggiungere log DebugUtilities.LogVerbose a codice interessante che potrebbe essere utile per il debug futuro.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-201">When adding new features or updating existing features, consider adding DebugUtilities.LogVerbose logs to interesting code that may be useful for future debugging.</span></span> <span data-ttu-id="7fa4d-202">C'è un compromesso tra l'aggiunta della registrazione e il rumore aggiunto e la registrazione non sufficiente (il che rende difficile la diagnosi).</span><span class="sxs-lookup"><span data-stu-id="7fa4d-202">There's a tradeoff here between adding logging and the added noise and not enough logging (which makes diagnosis difficult).</span></span>

<span data-ttu-id="7fa4d-203">Un esempio interessante in cui la registrazione è utile (insieme a un payload interessante):</span><span class="sxs-lookup"><span data-stu-id="7fa4d-203">An interesting example where having logging is useful (along with interesting payload):</span></span>

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

<span data-ttu-id="7fa4d-204">Questo tipo di registrazione consente di rilevare problemi come , che sono stati causati da un'origine non corrispondente rilevata [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) e da eventi di origine persi.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-204">This type of logging can help catch issues like [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016), which were caused by mismatched source detected and source lost events.</span></span>

<span data-ttu-id="7fa4d-205">Evitare di aggiungere log per dati ed eventi che si verificano in ogni frame. La registrazione ideale dovrebbe riguardare eventi "interessanti" generati da input utente distinti (ad esempio un "clic" da parte di un utente e il set di modifiche ed eventi provenienti da che sono interessanti da registrare).</span><span class="sxs-lookup"><span data-stu-id="7fa4d-205">Avoid adding logs for data and events that are occurring on every frame - ideally logging should cover "interesting" events driven by distinct user inputs (i.e. a "click" by a user and the set of changes and events that come from that are interesting to log).</span></span> <span data-ttu-id="7fa4d-206">Lo stato in corso di "utente è ancora in possesso di un movimento" registrato ogni frame non è interessante e sovraccaricerà i log.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-206">The ongoing state of "user is still holding a gesture" logged every frame is not interesting and will overwhelm the logs.</span></span>

<span data-ttu-id="7fa4d-207">Si noti che questa registrazione dettagliata non è attivata per impostazione predefinita (deve essere abilitata nelle impostazioni [del sistema di diagnostica](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging))</span><span class="sxs-lookup"><span data-stu-id="7fa4d-207">Note that this verbose logging is not turned on by default (it must be enabled in the [Diagnostic System settings](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging))</span></span>

### <a name="spaces-vs-tabs"></a><span data-ttu-id="7fa4d-208">Spazi e tabulazioni</span><span class="sxs-lookup"><span data-stu-id="7fa4d-208">Spaces vs tabs</span></span>

<span data-ttu-id="7fa4d-209">Assicurarsi di usare 4 spazi invece di tabulazioni quando si contribuisce a questo progetto.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-209">Please be sure to use 4 spaces instead of tabs when contributing to this project.</span></span>

### <a name="spacing"></a><span data-ttu-id="7fa4d-210">Spaziatura</span><span class="sxs-lookup"><span data-stu-id="7fa4d-210">Spacing</span></span>

<span data-ttu-id="7fa4d-211">Non aggiungere altri spazi tra parentesi quadre e parentesi:</span><span class="sxs-lookup"><span data-stu-id="7fa4d-211">Do not to add additional spaces between square brackets and parenthesis:</span></span>

#### <a name="dont"></a><span data-ttu-id="7fa4d-212">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-212">Don't</span></span>

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a><span data-ttu-id="7fa4d-213">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-213">Do</span></span>

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a><span data-ttu-id="7fa4d-214">Convenzioni di denominazione</span><span class="sxs-lookup"><span data-stu-id="7fa4d-214">Naming conventions</span></span>

<span data-ttu-id="7fa4d-215">Usare sempre `PascalCase` per le proprietà.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-215">Always use `PascalCase` for properties.</span></span> <span data-ttu-id="7fa4d-216">Usare `camelCase` per la maggior parte dei campi, ad eccezione di quelli per e `PascalCase` `static readonly` `const` .</span><span class="sxs-lookup"><span data-stu-id="7fa4d-216">Use `camelCase` for most fields, except use `PascalCase` for `static readonly` and `const` fields.</span></span> <span data-ttu-id="7fa4d-217">L'unica eccezione è per le strutture di dati che richiedono la serializzazione dei campi da parte di `JsonUtility` .</span><span class="sxs-lookup"><span data-stu-id="7fa4d-217">The only exception to this is for data structures that require the fields to be serialized by the `JsonUtility`.</span></span>

#### <a name="dont"></a><span data-ttu-id="7fa4d-218">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-218">Don't</span></span>

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a><span data-ttu-id="7fa4d-219">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-219">Do</span></span>

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a><span data-ttu-id="7fa4d-220">Modificatori di accesso</span><span class="sxs-lookup"><span data-stu-id="7fa4d-220">Access modifiers</span></span>

<span data-ttu-id="7fa4d-221">Dichiarare sempre un modificatore di accesso per tutti i campi, le proprietà e i metodi.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-221">Always declare an access modifier for all fields, properties and methods.</span></span>

- <span data-ttu-id="7fa4d-222">Tutti i metodi API unity devono essere per impostazione predefinita, a meno che non sia necessario `private` eseguirne l'override in una classe derivata.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-222">All Unity API Methods should be `private` by default, unless you need to override them in a derived class.</span></span> <span data-ttu-id="7fa4d-223">In questo caso `protected` è consigliabile usare .</span><span class="sxs-lookup"><span data-stu-id="7fa4d-223">In this case `protected` should be used.</span></span>

- <span data-ttu-id="7fa4d-224">I campi devono essere sempre `private` , con o funzioni di accesso alle `public` `protected` proprietà.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-224">Fields should always be `private`, with `public` or `protected` property accessors.</span></span>

- <span data-ttu-id="7fa4d-225">Usare [i membri con corpo di espressione](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) e le proprietà auto [laddove](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) possibile</span><span class="sxs-lookup"><span data-stu-id="7fa4d-225">Use [expression-bodied members](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) and [auto properties](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) where possible</span></span>

#### <a name="dont"></a><span data-ttu-id="7fa4d-226">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-226">Don't</span></span>

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a><span data-ttu-id="7fa4d-227">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-227">Do</span></span>

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a><span data-ttu-id="7fa4d-228">Usare le parentesi graffe</span><span class="sxs-lookup"><span data-stu-id="7fa4d-228">Use braces</span></span>

<span data-ttu-id="7fa4d-229">Usare sempre le parentesi graffe dopo ogni blocco di istruzioni e posizionarle nella riga successiva.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-229">Always use braces after each statement block, and place them on the next line.</span></span>

#### <a name="dont"></a><span data-ttu-id="7fa4d-230">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-230">Don't</span></span>

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a><span data-ttu-id="7fa4d-231">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-231">Don't</span></span>

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a><span data-ttu-id="7fa4d-232">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-232">Do</span></span>

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

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a><span data-ttu-id="7fa4d-233">Le classi, gli struct e le enumerazioni pubbliche devono essere tutti presenti nei propri file</span><span class="sxs-lookup"><span data-stu-id="7fa4d-233">Public classes, structs, and enums should all go in their own files</span></span>

<span data-ttu-id="7fa4d-234">Se la classe, lo struct o l'enumerazione possono essere resi privati, è possibile includere nello stesso file.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-234">If the class, struct, or enum can be made private then it's okay to be included in the same file.</span></span>  <span data-ttu-id="7fa4d-235">In questo modo si evitano problemi di compilazione con Unity e si garantisce che si verifichi un'astrazione corretta del codice, riducendo anche i conflitti e le modifiche che causano un'interruzione quando il codice deve cambiare.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-235">This avoids compilations issues with Unity and ensure that proper code abstraction occurs, it also reduces conflicts and breaking changes when code needs to change.</span></span>

#### <a name="dont"></a><span data-ttu-id="7fa4d-236">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-236">Don't</span></span>

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a><span data-ttu-id="7fa4d-237">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-237">Do</span></span>

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a><span data-ttu-id="7fa4d-238">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-238">Do</span></span>

<span data-ttu-id="7fa4d-239">MyStruct.cs</span><span class="sxs-lookup"><span data-stu-id="7fa4d-239">MyStruct.cs</span></span>

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

<span data-ttu-id="7fa4d-240">MyEnumType.cs</span><span class="sxs-lookup"><span data-stu-id="7fa4d-240">MyEnumType.cs</span></span>

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

<span data-ttu-id="7fa4d-241">MyClass.cs</span><span class="sxs-lookup"><span data-stu-id="7fa4d-241">MyClass.cs</span></span>

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a><span data-ttu-id="7fa4d-242">Inizializzare enumerazioni</span><span class="sxs-lookup"><span data-stu-id="7fa4d-242">Initialize enums</span></span>

<span data-ttu-id="7fa4d-243">Per assicurarsi che tutte le enumerazioni vengano inizializzate correttamente a partire da 0, .NET offre un collegamento ordinato per inizializzare automaticamente l'enumerazione aggiungendo semplicemente il primo valore (iniziale).</span><span class="sxs-lookup"><span data-stu-id="7fa4d-243">To ensure all enums are initialized correctly starting at 0, .NET gives you a tidy shortcut to automatically initialize the enum by just adding the first (starter) value.</span></span> <span data-ttu-id="7fa4d-244">(ad esempio, il valore 1 = 0 I valori rimanenti non sono obbligatori)</span><span class="sxs-lookup"><span data-stu-id="7fa4d-244">(e.g Value 1 = 0 Remaining values are not required)</span></span>

#### <a name="dont"></a><span data-ttu-id="7fa4d-245">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-245">Don't</span></span>

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a><span data-ttu-id="7fa4d-246">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-246">Do</span></span>

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a><span data-ttu-id="7fa4d-247">Ordinare le enumerazioni per l'estensione appropriata</span><span class="sxs-lookup"><span data-stu-id="7fa4d-247">Order enums for appropriate extension</span></span>

<span data-ttu-id="7fa4d-248">È fondamentale che, se è probabile che un'enumerazione sia estesa in futuro, per ordinare le impostazioni predefinite all'inizio dell'enumerazione, ciò garantisce che gli indici Enum non siano interessati dalle nuove aggiunte.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-248">It is critical that if an Enum is likely to be extended in the future, to order defaults at the top of the Enum, this ensures Enum indexes are not affected with new additions.</span></span>

#### <a name="dont"></a><span data-ttu-id="7fa4d-249">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-249">Don't</span></span>

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

#### <a name="do"></a><span data-ttu-id="7fa4d-250">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-250">Do</span></span>

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

### <a name="review-enum-use-for-bitfields"></a><span data-ttu-id="7fa4d-251">Esaminare l'uso dell'enumerazione per i campi di bit</span><span class="sxs-lookup"><span data-stu-id="7fa4d-251">Review enum use for bitfields</span></span>

<span data-ttu-id="7fa4d-252">Se è possibile che un'enumerazione richieda più stati come valore, ad esempio Handedness = Left & Right.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-252">If there is a possibility for an enum to require multiple states as a value, e.g. Handedness = Left & Right.</span></span> <span data-ttu-id="7fa4d-253">L'enumerazione deve quindi essere decorata correttamente con BitFlags per consentirla di essere usata correttamente</span><span class="sxs-lookup"><span data-stu-id="7fa4d-253">Then the Enum needs to be decorated correctly with BitFlags to enable it to be used correctly</span></span>

<span data-ttu-id="7fa4d-254">Il file Handedness.cs ha un'implementazione concreta per questo</span><span class="sxs-lookup"><span data-stu-id="7fa4d-254">The Handedness.cs file has a concrete implementation for this</span></span>

### <a name="dont"></a><span data-ttu-id="7fa4d-255">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-255">Don't</span></span>

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a><span data-ttu-id="7fa4d-256">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-256">Do</span></span>

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

### <a name="hard-coded-file-paths"></a><span data-ttu-id="7fa4d-257">Percorsi di file hard-coded</span><span class="sxs-lookup"><span data-stu-id="7fa4d-257">Hard-coded file paths</span></span>

<span data-ttu-id="7fa4d-258">Quando si generano percorsi di file di stringa e in particolare si scrivono percorsi di stringa hard-coded, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="7fa4d-258">When generating string file paths, and in particular writing hard-coded string paths, do the following:</span></span>

1. <span data-ttu-id="7fa4d-259">Usare le API di C# [ `Path` quando](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) possibile, ad esempio `Path.Combine` o `Path.GetFullPath` .</span><span class="sxs-lookup"><span data-stu-id="7fa4d-259">Use C#'s [`Path` APIs](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) whenever possible such as `Path.Combine` or `Path.GetFullPath`.</span></span>
1. <span data-ttu-id="7fa4d-260">Usare / o [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) invece di \ o \\ \\ .</span><span class="sxs-lookup"><span data-stu-id="7fa4d-260">Use / or [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) instead of \ or \\\\.</span></span>

<span data-ttu-id="7fa4d-261">Questi passaggi garantiscono che MRTK funzioni sia nei sistemi Windows e basati su Unix.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-261">These steps ensure that MRTK works on both Windows and Unix-based systems.</span></span>

### <a name="dont"></a><span data-ttu-id="7fa4d-262">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-262">Don't</span></span>

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a><span data-ttu-id="7fa4d-263">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-263">Do</span></span>

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a><span data-ttu-id="7fa4d-264">Procedure consigliate, incluse le raccomandazioni di Unity</span><span class="sxs-lookup"><span data-stu-id="7fa4d-264">Best practices, including Unity recommendations</span></span>

<span data-ttu-id="7fa4d-265">Alcune delle piattaforme di destinazione di questo progetto richiedono di prendere in considerazione le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-265">Some of the target platforms of this project require to take performance into consideration.</span></span> <span data-ttu-id="7fa4d-266">A questo scopo, prestare sempre attenzione quando si alloca memoria nel codice chiamato di frequente in algoritmi o cicli di aggiornamento ristretti.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-266">With this in mind always be careful when allocating memory in frequently called code in tight update loops or algorithms.</span></span>

### <a name="encapsulation"></a><span data-ttu-id="7fa4d-267">Incapsulamento</span><span class="sxs-lookup"><span data-stu-id="7fa4d-267">Encapsulation</span></span>

<span data-ttu-id="7fa4d-268">Usare sempre campi privati e proprietà pubbliche se l'accesso al campo è necessario dall'esterno della classe o dello struct.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-268">Always use private fields and public properties if access to the field is needed from outside the class or struct.</span></span>  <span data-ttu-id="7fa4d-269">Assicurarsi di co-individuare il campo privato e la proprietà pubblica.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-269">Be sure to co-locate the private field and the public property.</span></span> <span data-ttu-id="7fa4d-270">In questo modo è più semplice vedere, a colpo d'occhio, ciò che sosporta la proprietà e che il campo è modificabile tramite script.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-270">This makes it easier to see, at a glance, what backs the property and that the field is modifiable by script.</span></span>

> [!NOTE]
> <span data-ttu-id="7fa4d-271">L'unica eccezione è per le strutture di dati che richiedono la serializzazione dei campi da parte di , in cui una classe di dati deve avere tutti i campi pubblici per il funzionamento della `JsonUtility` serializzazione.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-271">The only exception to this is for data structures that require the fields to be serialized by the `JsonUtility`, where a data class is required to have all public fields for the serialization to work.</span></span>

#### <a name="dont"></a><span data-ttu-id="7fa4d-272">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-272">Don't</span></span>

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

#### <a name="do"></a><span data-ttu-id="7fa4d-273">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-273">Do</span></span>

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

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a><span data-ttu-id="7fa4d-274">Memorizzare nella cache i valori e serializzarli nella scena/prefab quando possibile</span><span class="sxs-lookup"><span data-stu-id="7fa4d-274">Cache values and serialize them in the scene/prefab whenever possible</span></span>

<span data-ttu-id="7fa4d-275">Con il HoloLens in mente, è meglio ottimizzare le prestazioni e i riferimenti alla cache nella scena o nel prefab per limitare le allocazioni di memoria di runtime.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-275">With the HoloLens in mind, it's best to optimize for performance and cache references in the scene or prefab to limit runtime memory allocations.</span></span>

#### <a name="dont"></a><span data-ttu-id="7fa4d-276">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-276">Don't</span></span>

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a><span data-ttu-id="7fa4d-277">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-277">Do</span></span>

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

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a><span data-ttu-id="7fa4d-278">Memorizzare nella cache i riferimenti ai materiali, non chiamare ogni volta ".material"</span><span class="sxs-lookup"><span data-stu-id="7fa4d-278">Cache references to materials, do not call the ".material" each time</span></span>

<span data-ttu-id="7fa4d-279">Unity creerà un nuovo materiale ogni volta che si usa ".material", causando una perdita di memoria se non viene pulita correttamente.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-279">Unity will create a new material each time you use ".material", which will cause a memory leak if not cleaned up properly.</span></span>

#### <a name="dont"></a><span data-ttu-id="7fa4d-280">Cosa non fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-280">Don't</span></span>

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

#### <a name="do"></a><span data-ttu-id="7fa4d-281">Cosa fare</span><span class="sxs-lookup"><span data-stu-id="7fa4d-281">Do</span></span>

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
> <span data-ttu-id="7fa4d-282">In alternativa, usare la proprietà "SharedMaterial" di Unity che non crea un nuovo materiale ogni volta che vi si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-282">Alternatively, use Unity's "SharedMaterial" property which does not create a new material each time it is referenced.</span></span>

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a><span data-ttu-id="7fa4d-283">Usare [la compilazione dipendente dalla](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) piattaforma per assicurarsi che Toolkit non interrompa la compilazione in un'altra piattaforma</span><span class="sxs-lookup"><span data-stu-id="7fa4d-283">Use [platform dependent compilation](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) to ensure the Toolkit won't break the build on another platform</span></span>

- <span data-ttu-id="7fa4d-284">Usare per usare API non Unity specifiche della `WINDOWS_UWP` UWP.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-284">Use `WINDOWS_UWP` in order to use UWP-specific, non-Unity APIs.</span></span> <span data-ttu-id="7fa4d-285">Ciò impedirà loro di provare a eseguire nell'editor o in piattaforme non supportate.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-285">This will prevent them from trying to run in the Editor or on unsupported platforms.</span></span> <span data-ttu-id="7fa4d-286">Equivale a `UNITY_WSA && !UNITY_EDITOR` e deve essere usato a favore di .</span><span class="sxs-lookup"><span data-stu-id="7fa4d-286">This is equivalent to `UNITY_WSA && !UNITY_EDITOR` and should be used in favor of.</span></span>
- <span data-ttu-id="7fa4d-287">Usare per usare API Unity specifiche della `UNITY_WSA` UWP, ad esempio lo spazio dei `UnityEngine.XR.WSA` nomi .</span><span class="sxs-lookup"><span data-stu-id="7fa4d-287">Use `UNITY_WSA` to use UWP-specific Unity APIs, such as the `UnityEngine.XR.WSA` namespace.</span></span> <span data-ttu-id="7fa4d-288">Verrà eseguito nell'editor quando la piattaforma è impostata su UWP, nonché nelle app UWP create.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-288">This will run in the Editor when the platform is set to UWP, as well as in built UWP apps.</span></span>

<span data-ttu-id="7fa4d-289">Questo grafico consente di decidere quale usare, a seconda dei casi `#if` d'uso e delle impostazioni di compilazione previste.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-289">This chart can help you decide which `#if` to use, depending on your use cases and the build settings you expect.</span></span>

|<span data-ttu-id="7fa4d-290">Piattaforma</span><span class="sxs-lookup"><span data-stu-id="7fa4d-290">Platform</span></span> | <span data-ttu-id="7fa4d-291">UWP IL2CPP</span><span class="sxs-lookup"><span data-stu-id="7fa4d-291">UWP IL2CPP</span></span> | <span data-ttu-id="7fa4d-292">UWP .NET</span><span class="sxs-lookup"><span data-stu-id="7fa4d-292">UWP .NET</span></span> | <span data-ttu-id="7fa4d-293">Editor</span><span class="sxs-lookup"><span data-stu-id="7fa4d-293">Editor</span></span> |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | <span data-ttu-id="7fa4d-294">False</span><span class="sxs-lookup"><span data-stu-id="7fa4d-294">False</span></span> | <span data-ttu-id="7fa4d-295">False</span><span class="sxs-lookup"><span data-stu-id="7fa4d-295">False</span></span> | <span data-ttu-id="7fa4d-296">True</span><span class="sxs-lookup"><span data-stu-id="7fa4d-296">True</span></span> |
| `UNITY_WSA` | <span data-ttu-id="7fa4d-297">True</span><span class="sxs-lookup"><span data-stu-id="7fa4d-297">True</span></span> | <span data-ttu-id="7fa4d-298">True</span><span class="sxs-lookup"><span data-stu-id="7fa4d-298">True</span></span> | <span data-ttu-id="7fa4d-299">True</span><span class="sxs-lookup"><span data-stu-id="7fa4d-299">True</span></span> |
| `WINDOWS_UWP` | <span data-ttu-id="7fa4d-300">True</span><span class="sxs-lookup"><span data-stu-id="7fa4d-300">True</span></span> | <span data-ttu-id="7fa4d-301">True</span><span class="sxs-lookup"><span data-stu-id="7fa4d-301">True</span></span> | <span data-ttu-id="7fa4d-302">False</span><span class="sxs-lookup"><span data-stu-id="7fa4d-302">False</span></span> |
| `UNITY_WSA && !UNITY_EDITOR` | <span data-ttu-id="7fa4d-303">True</span><span class="sxs-lookup"><span data-stu-id="7fa4d-303">True</span></span> | <span data-ttu-id="7fa4d-304">True</span><span class="sxs-lookup"><span data-stu-id="7fa4d-304">True</span></span> | <span data-ttu-id="7fa4d-305">False</span><span class="sxs-lookup"><span data-stu-id="7fa4d-305">False</span></span> |
| `ENABLE_WINMD_SUPPORT` | <span data-ttu-id="7fa4d-306">True</span><span class="sxs-lookup"><span data-stu-id="7fa4d-306">True</span></span> | <span data-ttu-id="7fa4d-307">True</span><span class="sxs-lookup"><span data-stu-id="7fa4d-307">True</span></span> | <span data-ttu-id="7fa4d-308">False</span><span class="sxs-lookup"><span data-stu-id="7fa4d-308">False</span></span> |
| `NETFX_CORE` | <span data-ttu-id="7fa4d-309">False</span><span class="sxs-lookup"><span data-stu-id="7fa4d-309">False</span></span> | <span data-ttu-id="7fa4d-310">True</span><span class="sxs-lookup"><span data-stu-id="7fa4d-310">True</span></span> | <span data-ttu-id="7fa4d-311">Falso</span><span class="sxs-lookup"><span data-stu-id="7fa4d-311">False</span></span> |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a><span data-ttu-id="7fa4d-312">Preferire DateTime.UtcNow rispetto a DateTime.Now</span><span class="sxs-lookup"><span data-stu-id="7fa4d-312">Prefer DateTime.UtcNow over DateTime.Now</span></span>

<span data-ttu-id="7fa4d-313">DateTime.UtcNow è più veloce di DateTime.Now.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-313">DateTime.UtcNow is faster than DateTime.Now.</span></span> <span data-ttu-id="7fa4d-314">Nelle indagini sulle prestazioni precedenti è stato rilevato che l'uso di DateTime.Now aggiunge un overhead significativo soprattutto se usato nel ciclo Update().</span><span class="sxs-lookup"><span data-stu-id="7fa4d-314">In previous performance investigations we've found that using DateTime.Now adds significant overhead especially when used in the Update() loop.</span></span> <span data-ttu-id="7fa4d-315">[Altri hanno raggiunto lo stesso problema.](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now)</span><span class="sxs-lookup"><span data-stu-id="7fa4d-315">[Others have hit the same issue](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now).</span></span>

<span data-ttu-id="7fa4d-316">Preferire l'uso di DateTime.UtcNow a meno che non siano effettivamente necessari gli orari localizzati (un motivo legittimo potrebbe essere che si vuole visualizzare l'ora corrente nel fuso orario dell'utente).</span><span class="sxs-lookup"><span data-stu-id="7fa4d-316">Prefer using DateTime.UtcNow unless you actually need the localized times (a legitimate reason may be you wanting to show the current time in the user's time zone).</span></span> <span data-ttu-id="7fa4d-317">Se si hanno a che fare con orari relativi(ad esempio, il delta tra l'ultimo aggiornamento e ora), è meglio usare DateTime.UtcNow per evitare il sovraccarico delle conversioni del fuso orario.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-317">If you are dealing with relative times (i.e. the delta between some last update and now), it's best to use DateTime.UtcNow to avoid the overhead of doing timezone conversions.</span></span>

## <a name="powershell-coding-conventions"></a><span data-ttu-id="7fa4d-318">Convenzioni di codifica di PowerShell</span><span class="sxs-lookup"><span data-stu-id="7fa4d-318">PowerShell coding conventions</span></span>

<span data-ttu-id="7fa4d-319">Un subset della codebase MRTK usa PowerShell per l'infrastruttura della pipeline e vari script e utilità.</span><span class="sxs-lookup"><span data-stu-id="7fa4d-319">A subset of the MRTK codebase uses PowerShell for pipeline infrastructure and various scripts and utilities.</span></span> <span data-ttu-id="7fa4d-320">Il nuovo codice di PowerShell deve seguire lo [stile PoshCode](https://poshcode.gitbooks.io/powershell-practice-and-style/).</span><span class="sxs-lookup"><span data-stu-id="7fa4d-320">New PowerShell code should follow the [PoshCode style](https://poshcode.gitbooks.io/powershell-practice-and-style/).</span></span>

## <a name="see-also"></a><span data-ttu-id="7fa4d-321">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7fa4d-321">See also</span></span>

 [<span data-ttu-id="7fa4d-322">Convenzioni di codifica C# da MSDN</span><span class="sxs-lookup"><span data-stu-id="7fa4d-322">C# coding conventions from MSDN</span></span>](/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)
