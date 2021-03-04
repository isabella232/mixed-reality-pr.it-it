---
title: CodingGuidelines
description: principi e convenzioni di codifica da seguire per contribuire a MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, C#,
ms.openlocfilehash: 12fbf24f5cc75abb6fd9dd7e4c5564f053b06f6d
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783719"
---
# <a name="coding-guidelines"></a>Linee guida sulla codifica

Questo documento descrive i principi e le convenzioni di codifica da seguire per contribuire a MRTK.

---

## <a name="philosophy"></a>Filosofia

### <a name="be-concise-and-strive-for-simplicity"></a>Essere conciso e impegnarsi per semplicità

La soluzione più semplice è spesso la scelta migliore. Si tratta di un obiettivo sostitutivo di queste linee guida e dovrebbe essere l'obiettivo di tutte le attività di codifica. Parte della semplicità è concisa e coerente con il codice esistente. Provare a semplificare il codice.

I lettori devono rilevare solo gli elementi che forniscono informazioni utili. Ad esempio, i commenti che riformulano gli elementi evidenti non forniscono informazioni aggiuntive e aumentano il rapporto tra rumore e segnale.

Semplificare la logica del codice. Si noti che non si tratta di un'istruzione sull'utilizzo del minor numero di righe, riducendo al minimo le dimensioni dei nomi degli identificatori o dello stile della parentesi graffa, ma per ridurre il numero di concetti e massimizzare la visibilità di tali linee tramite modelli noti.

### <a name="produce-consistent-readable-code"></a>Produrre codice coerente e leggibile

La leggibilità del codice è correlata a frequenze di difetti ridotte. Sforzarsi di creare codice facile da leggere. Sforzarsi di creare codice con una logica semplice e riutilizzare i componenti esistenti, in quanto consente inoltre di garantire la correttezza.

Tutti i dettagli del codice prodotto, dai dettagli più semplici sulla correttezza allo stile e alla formattazione coerenti. Mantieni lo stile di codifica coerente con quello che esiste già, anche se non corrisponde alle tue preferenze. Ciò aumenta la leggibilità della codebase complessiva.

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a>Supportare la configurazione dei componenti sia nell'editor che in fase di esecuzione

MRTK supporta un set di utenti diversificato, ovvero persone che preferiscono configurare i componenti nell'editor di Unity e caricare i prefabbricati e gli utenti che devono creare istanze e configurare oggetti in fase di esecuzione.

Tutto il codice dovrebbe funzionare sia aggiungendo un componente a un GameObject in una scena salvata, sia creando un'istanza del componente nel codice. I test devono includere una test case sia per la creazione di un'istanza di prefabbricati che per la creazione di istanze, configurazione del componente in fase di esecuzione

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a>Play-in-Editor è la prima piattaforma di destinazione principale

Play-in-Editor è il modo più rapido per eseguire un'iterazione in Unity. Fornire modi per consentire ai clienti di eseguire rapidamente l'iterazione consente loro di sviluppare soluzioni in modo più rapido e provare altre idee. In altre parole, l'ottimizzazione della velocità di iterazione consente ai clienti di ottenere maggiori risultati.

Eseguire tutte le operazioni nell'editor, quindi fare in modo che funzioni in qualsiasi altra piattaforma. Mantenerlo funzionante nell'editor. È facile aggiungere una nuova piattaforma a Play-in-Editor. È molto difficile ottenere il funzionamento di Play-in-Editor se l'app funziona solo in un dispositivo.

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a>Aggiunta di nuovi campi pubblici, proprietà, metodi e campi privati serializzati con attenzione

Ogni volta che si aggiunge un metodo pubblico, Field, Property, diventa parte della superficie dell'API pubblica di MRTK. I campi privati contrassegnati con `[SerializeField]` espongono anche campi all'editor e fanno parte della superficie dell'API pubblica. Altri utenti possono usare il metodo pubblico, configurare i prefabbricati personalizzati con il campo pubblico e assumere una dipendenza.

È necessario esaminare attentamente i nuovi membri pubblici. In futuro sarà necessario mantenere un campo pubblico. Tenere presente che, se il tipo di un campo pubblico (o di un campo privato serializzato) cambia o viene rimosso da un monocomportamento, questo potrebbe comportare l'insorgere di altre persone. Il campo deve essere prima deprecato per una versione e il codice per eseguire la migrazione delle modifiche per gli utenti che hanno eseguito dipendenze deve essere fornito.

### <a name="prioritize-writing-tests"></a>Assegnare priorità ai test di scrittura

MRTK è un progetto di community, modificato da un'ampia gamma di collaboratori. Questi collaboratori potrebbero non essere a conoscenza dei dettagli della correzione o della funzionalità di bug e interrompere accidentalmente la funzionalità. [MRTK esegue i test di integrazione continua](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) prima di completare ogni richiesta pull. Non è possibile archiviare le modifiche che interrompono i test. Pertanto, i test rappresentano il modo migliore per garantire che altri utenti non interrompano la funzionalità.

Quando si corregge un bug, scrivere un test per assicurarsi che non venga regressione in futuro. Se si aggiunge una funzionalità, scrivere i test per verificare il funzionamento della funzionalità. Questa operazione è necessaria per tutte le funzionalità di UX ad eccezione delle funzionalità sperimentali.

## <a name="c-coding-conventions"></a>Convenzioni di codifica C#

### <a name="script-license-information-headers"></a>Intestazioni delle informazioni di licenza per script

Tutti i dipendenti Microsoft che contribuiscono ai nuovi file devono aggiungere l'intestazione di licenza standard seguente all'inizio di tutti i nuovi file, esattamente come mostrato di seguito:

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a>Intestazioni di riepilogo funzione/metodo

Tutte le classi, le strutture, le enumerazioni, le funzioni, le proprietà, i campi pubblicati in MRTK devono essere descritti in modo analogo allo scopo e all'uso, esattamente come mostrato di seguito:

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

In questo modo la documentazione viene generata e divulgata correttamente per tutte le classi, i metodi e le proprietà.

Eventuali file di script inviati senza tag di riepilogo appropriati verranno rifiutati.

### <a name="mrtk-namespace-rules"></a>Regole dello spazio dei nomi MRTK

Il Toolkit di realtà mista Usa un modello di spazio dei nomi basato su funzionalità, in cui tutti gli spazi dei nomi fondamentali iniziano con "Microsoft. MixedReality. Toolkit". In generale, non è necessario specificare il livello Toolkit (ad esempio Core, providers, servizi) negli spazi dei nomi.

Gli spazi dei nomi attualmente definiti sono:

- Microsoft. MixedReality. Toolkit
- Microsoft. MixedReality. Toolkit. Boundary
- Microsoft. MixedReality. Toolkit. Diagnostics
- Microsoft. MixedReality. Toolkit. Editor
- Microsoft. MixedReality. Toolkit. input
- Microsoft. MixedReality. Toolkit. SpatialAwareness
- Microsoft. MixedReality. Toolkit. Teleport
- Microsoft. MixedReality. Toolkit. Utilities

Per gli spazi dei nomi con una grande quantità di tipi, è accettabile creare un numero limitato di sottospazi dei nomi per facilitare l'utilizzo dell'ambito.

L'omissione dello spazio dei nomi per un'interfaccia, una classe o un tipo di dati provocherà il blocco della modifica.

### <a name="adding-new-monobehaviour-scripts"></a>Aggiunta di nuovi script monobehavior

Quando si aggiungono nuovi script monobehavior con una richiesta pull, assicurarsi [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) che l'attributo venga applicato a tutti i file applicabili. Ciò garantisce che il componente sia facilmente individuabile nell'editor sotto il pulsante *Aggiungi componente* . Il flag di attributo non è necessario se il componente non può essere visualizzato nell'editor, ad esempio una classe astratta.

Nell'esempio seguente il *pacchetto* deve essere compilato con il percorso del pacchetto del componente. Se si posiziona un elemento nella cartella *MRTK/SDK* , il pacchetto sarà *SDK*.

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a>Aggiunta di nuovi script di Unity Inspector

In generale, provare a evitare di creare script di controllo personalizzati per i componenti di MRTK. Aggiunge overhead e gestione aggiuntivi della codebase che potrebbero essere gestiti dal motore Unity.

Se è necessaria una classe Inspector, provare a usare Unity [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) . Questa operazione semplifica di nuovo la classe Inspector e lascia gran parte del lavoro a Unity.

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

Se nella classe Inspector è necessario il rendering personalizzato, provare a utilizzare [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) e [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) . In questo modo Unity gestisce correttamente il rendering dei prefabbricati annidati e i valori modificati.

Se [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) non può essere usato a causa di un requisito nella logica personalizzata, assicurarsi che tutti i dati di utilizzo siano racchiusi in un oggetto [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) . In questo modo Unity esegue il rendering corretto del controllo per i prefabbricati annidati e i valori modificati con la proprietà specificata.

Inoltre, provare a decorare la classe Inspector personalizzata con un oggetto [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) . Questo tag assicura che più oggetti con questo componente nella scena possano essere selezionati e modificati insieme. Tutte le nuove classi di controllo dovrebbero testare il funzionamento del codice in questa situazione nella scena.

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

### <a name="adding-new-scriptableobjects"></a>Aggiunta di nuovi ScriptableObjects

Quando si aggiungono nuovi script ScriptableObject, assicurarsi [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) che l'attributo venga applicato a tutti i file applicabili. Ciò garantisce che il componente sia facilmente individuabile nell'editor tramite i menu di creazione dell'asset. Il flag di attributo non è necessario se il componente non può essere visualizzato nell'editor, ad esempio una classe astratta.

Nell'esempio seguente, la *sottocartella* deve essere riempita con la sottocartella MRTK, se applicabile. Se si posiziona un elemento nella cartella *MRTK/Providers* , il pacchetto sarà *providers*. Se si posiziona un elemento nella cartella *MRTK/Core* , impostarlo su "Profiles".

Nell'esempio seguente *MyNewService | MyNewProvider* deve essere compilato con il nome della nuova classe, se applicabile. Se si posiziona un elemento nella cartella *MixedRealityToolkit* , lasciare questa stringa.

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a>Registrazione

Quando si aggiungono nuove funzionalità o si aggiornano le funzionalità esistenti, è consigliabile aggiungere i log DebugUtilities. LogVerbose al codice interessante che può risultare utile per il debug futuro. C'è un compromesso tra l'aggiunta della registrazione e il rumore aggiunto e la registrazione non sufficiente, che rende difficile la diagnosi.

Un esempio interessante in cui la registrazione è utile (insieme al payload interessante):

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

Questo tipo di registrazione può essere utile per intercettare il problema, ad esempio [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) , causato da eventi di origine non corrispondenti rilevati e da eventi persi nel codice sorgente.

Evitare di aggiungere log per i dati e gli eventi che si verificano in ogni frame. la registrazione idealmente dovrebbe coprire eventi "interessanti" basati su input utente distinti, ad esempio un "clic" da un utente e il set di modifiche ed eventi provenienti da interessanti da registrare. Lo stato attuale di "utente è ancora in possesso di un gesto" registrato ogni frame non è interessante e sovraccarica i log.

Si noti che questa registrazione dettagliata non è attivata per impostazione predefinita e deve essere abilitata nelle [impostazioni del sistema di diagnostica](../features/diagnostics/ConfiguringDiagnostics.md#enable-verbose-logging).

### <a name="spaces-vs-tabs"></a>Spazi vs schede

Per contribuire a questo progetto, assicurarsi di usare 4 spazi anziché le schede.

### <a name="spacing"></a>Spaziatura

Non aggiungere spazi aggiuntivi tra parentesi quadre e parentesi:

#### <a name="dont"></a>Cosa non fare

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a>Cosa fare

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a>Convenzioni di denominazione

Usare sempre `PascalCase` per le proprietà. Usare `camelCase` per la maggior parte dei campi, ad eccezione `PascalCase` dell'uso dei `static readonly` `const` campi e. L'unica eccezione è rappresentata dalle strutture di dati che richiedono la serializzazione dei campi da parte di `JsonUtility` .

#### <a name="dont"></a>Cosa non fare

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a>Cosa fare

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a>Modificatori di accesso

Dichiarare sempre un modificatore di accesso per tutti i campi, le proprietà e i metodi.

- Tutti i metodi dell'API Unity devono essere `private` per impostazione predefinita, a meno che non sia necessario eseguirne l'override in una classe derivata. In questo caso `protected` deve essere usato.

- I campi devono essere sempre `private` , con le `public` funzioni di accesso alle proprietà o `protected` .

- Usare [membri con corpo di espressione](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) e [proprietà automatiche](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) laddove possibile

#### <a name="dont"></a>Cosa non fare

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a>Cosa fare

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a>USA parentesi graffe

Usare sempre le parentesi graffe dopo ogni blocco di istruzioni e posizionarle nella riga successiva.

#### <a name="dont"></a>Cosa non fare

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a>Cosa non fare

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a>Cosa fare

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

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a>Le classi, gli struct e le enumerazioni pubbliche dovrebbero tutti entrare nei propri file

Se la classe, lo struct o l'enum può essere reso privato, è accettabile essere incluso nello stesso file.  In questo modo si evitano i problemi di compilazione con Unity e si garantisce che si verifichi l'astrazione corretta del codice, ma anche i conflitti e le modifiche di rilievo quando il codice deve essere modificato

#### <a name="dont"></a>Cosa non fare

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a>Cosa fare

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a>Cosa fare

MyStruct.cs

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

MyEnumType.cs

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

MyClass.cs

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a>Inizializzazione delle enumerazioni

Per assicurarsi che tutte le enumerazioni siano inizializzate correttamente a partire da 0, .NET fornisce un collegamento ordinato per inizializzare automaticamente l'enumerazione aggiungendo il primo valore (Starter). (ad esempio, il valore 1 = 0 valori rimanenti non sono obbligatori)

#### <a name="dont"></a>Cosa non fare

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a>Cosa fare

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a>Ordina enumerazioni per l'estensione appropriata

È fondamentale che se è probabile che un'enumerazione venga estesa in futuro, per ordinare le impostazioni predefinite all'inizio dell'enumerazione, ciò garantisce che gli indici enum non siano interessati da nuove aggiunte.

#### <a name="dont"></a>Cosa non fare

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

#### <a name="do"></a>Cosa fare

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

### <a name="review-enum-use-for-bitfields"></a>Esaminare l'uso di enum per campi

Se è possibile che un'enumerazione richieda più Stati come valore, ad esempio manualità = Left & right. L'enumerazione deve quindi essere decorata correttamente con flag per consentirne l'uso corretto

Il file Handedness.cs dispone di un'implementazione concreta per

### <a name="dont"></a>Cosa non fare

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a>Cosa fare

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

### <a name="hard-coded-file-paths"></a>Percorsi di file hardcoded

Quando si generano i percorsi dei file di stringa e, in particolare, si scrivono percorsi di stringa hardcoded, eseguire le operazioni seguenti:

1. Usare le [ `Path` API](https://docs.microsoft.com/dotnet/api/system.io.path?view=netframework-4.8add&preserve-view=true) di C#, laddove possibile, ad esempio `Path.Combine` o `Path.GetFullPath` .
1. Utilizzare/o [`Path.DirectorySeparatorChar`](https://docs.microsoft.com/dotnet/api/system.io.path.directoryseparatorchar?view=netframework-4.8add&preserve-view=true) anziché \ o \\ \\ .

Questi passaggi assicurano che MRTK funzioni nei sistemi Windows e UNIX.

### <a name="dont"></a>Cosa non fare

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a>Cosa fare

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a>Procedure consigliate, incluse le raccomandazioni Unity

Per alcune delle piattaforme di destinazione di questo progetto è necessario prendere in considerazione le prestazioni. Tenendo presente questo aspetto, prestare attenzione quando si alloca la memoria in un codice denominato spesso in cicli o algoritmi di aggiornamento stretti.

### <a name="encapsulation"></a>Incapsulamento

Usare sempre i campi privati e le proprietà pubbliche se è necessario l'accesso al campo dall'esterno della classe o dello struct.  Assicurarsi di condividere il percorso del campo privato e della proprietà pubblica. In questo modo è più semplice visualizzare, a colpo d'occhio, le informazioni che consentono di eseguire il backup della proprietà e che il campo è modificabile dallo script.

> [!NOTE]
> L'unica eccezione è rappresentata dalle strutture di dati che richiedono che i campi vengano serializzati da `JsonUtility` , in cui è necessario che una classe di dati disponga di tutti i campi pubblici affinché la serializzazione funzioni.

#### <a name="dont"></a>Cosa non fare

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

#### <a name="do"></a>Cosa fare

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

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a>Memorizzare nella cache i valori e serializzarli nella scena o nella prefabbricazione, quando possibile

Tenendo presente il HoloLens, è preferibile ottimizzare per le prestazioni e i riferimenti alla cache nella scena o nel prefabbricato per limitare le allocazioni di memoria di Runtime.

#### <a name="dont"></a>Cosa non fare

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a>Cosa fare

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

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a>Memorizzare nella cache i riferimenti ai materiali, non chiamare ogni volta il "materiale".

Unity creerà un nuovo materiale ogni volta che si usa ". Material", che causerà una perdita di memoria se non viene eseguita la pulizia corretta.

#### <a name="dont"></a>Cosa non fare

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

#### <a name="do"></a>Cosa fare

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
> In alternativa, usare la proprietà "SharedMaterial" di Unity che non crea un nuovo materiale ogni volta che vi si fa riferimento.

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a>Usare la [compilazione dipendente dalla piattaforma](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) per assicurarsi che il Toolkit non interrompa la compilazione in un'altra piattaforma

- Usare per `WINDOWS_UWP` usare API specifiche di UWP e non Unity. In questo modo si eviterà di provare a eseguire nell'editor o su piattaforme non supportate. Equivale a `UNITY_WSA && !UNITY_EDITOR` e deve essere usato a favore di.
- Usare `UNITY_WSA` per usare le API Unity specifiche di UWP, ad esempio lo `UnityEngine.XR.WSA` spazio dei nomi. Questa operazione verrà eseguita nell'editor quando la piattaforma è impostata su UWP, oltre che nelle app UWP compilate.

Questo grafico può essere utile per decidere quale `#if` usare, a seconda dei casi d'uso e delle impostazioni di compilazione previsti.

|Piattaforma | IL2CPP UWP | UWP .NET | Editor |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | False | False | True |
| `UNITY_WSA` | True | True | True |
| `WINDOWS_UWP` | True | True | False |
| `UNITY_WSA && !UNITY_EDITOR` | True | True | False |
| `ENABLE_WINMD_SUPPORT` | True | True | False |
| `NETFX_CORE` | False | True | Falso |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a>Preferisci DateTime. UtcNow su DateTime. Now

DateTime. UtcNow è più veloce di DateTime. Now. Nelle analisi delle prestazioni precedenti è stato rilevato che l'utilizzo di DateTime. ora aggiunge un sovraccarico significativo soprattutto se utilizzato nel ciclo Update (). [Altri hanno raggiunto lo stesso problema](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now).

Preferire l'uso di DateTime. UtcNow, a meno che non siano effettivamente necessarie le ore localizzate (un motivo legittimo potrebbe essere quello di visualizzare l'ora corrente nel fuso orario dell'utente). Se si gestiscono le ore relative (ad esempio, il delta tra un ultimo aggiornamento e ora), è preferibile usare DateTime. UtcNow per evitare il sovraccarico dovuto alla conversione del fuso orario.

## <a name="powershell-coding-conventions"></a>Convenzioni di codifica di PowerShell

Un subset della codebase MRTK USA PowerShell per l'infrastruttura della pipeline e vari script e utilità. Il nuovo codice PowerShell deve seguire lo [stile PoshCode](https://poshcode.gitbooks.io/powershell-practice-and-style/).

## <a name="see-also"></a>Vedi anche

 [Convenzioni di codifica C# da MSDN](https://docs.microsoft.com/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)
