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
# <a name="coding-guidelines"></a>Linee guida sulla codifica

Questo documento illustra i principi e le convenzioni di codifica da seguire quando si contribuisce a MRTK.

---

## <a name="philosophy"></a>Filosofia

### <a name="be-concise-and-strive-for-simplicity"></a>Essere concisi e cercare semplicità

La soluzione più semplice è spesso la migliore. Si tratta di un obiettivo di override di queste linee guida e deve essere l'obiettivo di tutte le attività di codifica. Una parte di essere semplice è essere concisa e coerente con il codice esistente. Provare a mantenere il codice semplice.

I lettori devono riscontrare solo elementi che forniscono informazioni utili. Ad esempio, i commenti che restate ciò che è ovvio non forniscono informazioni aggiuntive e aumentano il rapporto rumore-segnale.

Mantenere semplice la logica del codice. Si noti che non si tratta di un'istruzione sull'uso del numero più ridotto di righe, riducendo al minimo le dimensioni dei nomi degli identificatori o dello stile delle parentesi graffe, ma sulla riduzione del numero di concetti e sull'ottimizzazione della visibilità di tali righe tramite modelli familiari.

### <a name="produce-consistent-readable-code"></a>Produrre codice coerente e leggibile

La leggibilità del codice è correlata alle basse percentuali di difetti. Cercare di creare codice di facile lettura. Cercare di creare codice con logica semplice e di ri-usare i componenti esistenti perché consente anche di garantire la correttezza.

Tutti i dettagli del codice prodotto sono importanti, dal dettaglio più semplice della correttezza allo stile e alla formattazione coerenti. Mantenere lo stile di codifica coerente con ciò che esiste già, anche se non corrisponde alle preferenze. Ciò aumenta la leggibilità della codebase complessiva.

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a>Supporto della configurazione dei componenti sia nell'editor che in fase di esecuzione

MRTK supporta un set diversificato di utenti: utenti che preferiscono configurare i componenti nell'editor di Unity e caricare i prefab e utenti che devono creare istanze e configurare oggetti in fase di esecuzione.

Tutto il codice dovrebbe funzionare aggiungendo un componente a gameobject in una scena salvata e creando un'istanza di tale componente nel codice. I test devono includere un test case per la creazione di istanze di prefab e la creazione di istanze, la configurazione del componente in fase di esecuzione.

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a>Play-in-editor è la prima piattaforma di destinazione primaria

Play-In-Editor è il modo più rapido per eseguire l'iterazione in Unity. Offrire ai clienti la possibilità di eseguire rapidamente l'iterazione consente di sviluppare soluzioni più rapidamente e di provare altre idee. In altre parole, ottimizzare la velocità di iterazione consente ai clienti di ottenere di più.

Fare in modo che tutto funzioni nell'editor e quindi farlo funzionare in qualsiasi altra piattaforma. Mantenere il funzionamento nell'editor. È facile aggiungere una nuova piattaforma a Play-In-Editor. È molto difficile far funzionare Play-In-Editor se l'app funziona solo in un dispositivo.

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a>Aggiungere nuovi campi pubblici, proprietà, metodi e campi privati serializzati con attenzione

Ogni volta che si aggiunge un metodo pubblico, un campo, una proprietà, questo diventa parte della superficie api pubblica di MRTK. I campi privati contrassegnati `[SerializeField]` con espongono anche i campi all'editor e fanno parte della superficie api pubblica. Altri utenti potrebbero usare questo metodo pubblico, configurare prefab personalizzati con il campo pubblico e assumere una dipendenza da esso.

I nuovi membri pubblici devono essere esaminati con attenzione. Qualsiasi campo pubblico dovrà essere gestito in futuro. Tenere presente che se il tipo di un campo pubblico (o di un campo privato serializzato) cambia o viene rimosso da un oggetto MonoBehaviour, ciò potrebbe interrompere altri utenti. Il campo dovrà prima essere deprecato per una versione e il codice per eseguire la migrazione delle modifiche per gli utenti che hanno assunto dipendenze dovrà essere fornito.

### <a name="prioritize-writing-tests"></a>Assegnare priorità alla scrittura di test

MRTK è un progetto della community, modificato da una vasta gamma di collaboratori. Questi collaboratori potrebbero non conoscere i dettagli della correzione/funzionalità dei bug e interrompere accidentalmente la funzionalità. [MRTK esegue test di integrazione continua](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) prima di completare ogni richiesta pull. Le modifiche che interrompno i test non possono essere archiviate. Pertanto, i test sono il modo migliore per garantire che altri utenti non interrompano la funzionalità.

Quando si corregge un bug, scrivere un test per assicurarsi che non regredisca in futuro. Se si aggiunge una funzionalità, scrivere test che verificano il funzionamento della funzionalità. Questa operazione è necessaria per tutte le funzionalità dell'esperienza utente, ad eccezione delle funzionalità sperimentali.

## <a name="c-coding-conventions"></a>Convenzioni di codifica C#

### <a name="script-license-information-headers"></a>Intestazioni delle informazioni sulla licenza di script

Tutti i dipendenti Microsoft che contribuiscono a nuovi file devono aggiungere l'intestazione Licenza standard seguente nella parte superiore di tutti i nuovi file, esattamente come illustrato di seguito:

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a>Intestazioni di riepilogo di funzioni/metodi

Tutte le classi pubbliche, gli struct, le enumerazioni, le funzioni, le proprietà, i campi inseriti in MRTK devono essere descritti in base allo scopo e all'uso, esattamente come illustrato di seguito:

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

In questo modo la documentazione viene generata e diffusa correttamente per tutte le classi, i metodi e le proprietà.

Tutti i file script inviati senza tag di riepilogo adeguati verranno rifiutati.

### <a name="mrtk-namespace-rules"></a>Regole dello spazio dei nomi MRTK

L'Toolkit realtà mista usa un modello di spazio dei nomi basato su funzionalità, in cui tutti gli spazi dei nomi di base iniziano con "Microsoft.MixedReality. Toolkit". In generale, non è necessario specificare il livello del toolkit (ad esempio Core, Provider, Servizi) negli spazi dei nomi.

Gli spazi dei nomi attualmente definiti sono:

- Microsoft.MixedReality. Toolkit
- Microsoft.MixedReality. Toolkit. Confine
- Microsoft.MixedReality. Toolkit. Diagnostica
- Microsoft.MixedReality. Toolkit. Editore
- Microsoft.MixedReality. Toolkit. Input
- Microsoft.MixedReality. Toolkit. SpatialAwareness
- Microsoft.MixedReality. Toolkit. Teletrasporto
- Microsoft.MixedReality. Toolkit. Utilità

Per gli spazi dei nomi con una grande quantità di tipi, è accettabile creare un numero limitato di sotto-spazi dei nomi per facilitare l'utilizzo dell'ambito.

Se si omette lo spazio dei nomi per un'interfaccia, una classe o un tipo di dati, la modifica verrà bloccata.

### <a name="adding-new-monobehaviour-scripts"></a>Aggiunta di nuovi script MonoBehaviour

Quando si aggiungono nuovi script MonoBehaviour con una richiesta pull, assicurarsi che [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) l'attributo sia applicato a tutti i file applicabili. In questo modo il componente è facilmente individuabile nell'editor sotto il *pulsante Aggiungi* componente. Il flag di attributo non è necessario se il componente non può essere visualizzato nell'editor, ad esempio una classe astratta.

Nell'esempio seguente il *pacchetto* deve essere compilato con il percorso del pacchetto del componente. Se si inserisce un *elemento nella cartella MRTK/SDK,* il pacchetto sarà *SDK.*

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a>Aggiunta di nuovi script di controllo unity

In generale, provare a evitare di creare script di controllo personalizzati per i componenti MRTK. Aggiunge un sovraccarico aggiuntivo e la gestione della codebase che può essere gestita dal motore unity.

Se è necessaria una classe inspector, provare a usare . [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) Questo semplifica di nuovo la classe inspector e lascia gran parte del lavoro a Unity.

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

Se è necessario eseguire il rendering personalizzato nella classe inspector, provare a utilizzare [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) e [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) . In questo modo Unity gestisce correttamente il rendering dei prefab annidati e dei valori modificati.

Se [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) non è possibile usare a causa di un requisito nella logica personalizzata, assicurarsi che tutto l'utilizzo sia racchiuso in un oggetto [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) . In questo modo Unity esegue correttamente il rendering del controllo per i prefab annidati e i valori modificati con la proprietà specificata.

Provare inoltre a decorare la classe inspector personalizzata con un [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) oggetto . Questo tag garantisce che più oggetti con questo componente nella scena possano essere selezionati e modificati insieme. Qualsiasi nuova classe inspector deve testare che il codice funzioni in questa situazione nella scena.

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

### <a name="adding-new-scriptableobjects"></a>Aggiunta di nuovi oggetti ScriptableObject

Quando si aggiungono nuovi script ScriptableObject, assicurarsi che [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) l'attributo sia applicato a tutti i file applicabili. Ciò garantisce che il componente sia facilmente individuabile nell'editor tramite i menu di creazione dell'asset. Il flag di attributo non è necessario se il componente non può essere visualizzato nell'editor, ad esempio una classe astratta.

Nell'esempio seguente la *sottocartella* deve essere compilata con la sottocartella MRTK, se applicabile. Se si inserisce un *elemento nella cartella MRTK/Providers,* il pacchetto sarà *Providers*. Se si inserisce un elemento nella *cartella MRTK/Core,* impostarla su "Profiles".

Nell'esempio seguente, *myNewService | MyNewProvider deve* essere compilato con il nome della nuova classe, se applicabile. Se si inserisce un elemento *nella cartella MixedRealityToolkit,* lasciare vuota questa stringa.

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a>Registrazione

Quando si aggiungono nuove funzionalità o si aggiornano le funzionalità esistenti, è consigliabile aggiungere log DebugUtilities.LogVerbose a codice interessante che potrebbe essere utile per il debug futuro. C'è un compromesso tra l'aggiunta della registrazione e il rumore aggiunto e la registrazione non sufficiente (il che rende difficile la diagnosi).

Un esempio interessante in cui la registrazione è utile (insieme a un payload interessante):

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

Questo tipo di registrazione consente di rilevare problemi come , che sono stati causati da un'origine non corrispondente rilevata [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) e da eventi di origine persi.

Evitare di aggiungere log per dati ed eventi che si verificano in ogni frame. La registrazione ideale dovrebbe riguardare eventi "interessanti" generati da input utente distinti (ad esempio un "clic" da parte di un utente e il set di modifiche ed eventi provenienti da che sono interessanti da registrare). Lo stato in corso di "utente è ancora in possesso di un movimento" registrato ogni frame non è interessante e sovraccaricerà i log.

Si noti che questa registrazione dettagliata non è attivata per impostazione predefinita (deve essere abilitata nelle impostazioni [del sistema di diagnostica](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging))

### <a name="spaces-vs-tabs"></a>Spazi e tabulazioni

Assicurarsi di usare 4 spazi invece di tabulazioni quando si contribuisce a questo progetto.

### <a name="spacing"></a>Spaziatura

Non aggiungere altri spazi tra parentesi quadre e parentesi:

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

Usare sempre `PascalCase` per le proprietà. Usare `camelCase` per la maggior parte dei campi, ad eccezione di quelli per e `PascalCase` `static readonly` `const` . L'unica eccezione è per le strutture di dati che richiedono la serializzazione dei campi da parte di `JsonUtility` .

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

- Tutti i metodi API unity devono essere per impostazione predefinita, a meno che non sia necessario `private` eseguirne l'override in una classe derivata. In questo caso `protected` è consigliabile usare .

- I campi devono essere sempre `private` , con o funzioni di accesso alle `public` `protected` proprietà.

- Usare [i membri con corpo di espressione](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) e le proprietà auto [laddove](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) possibile

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

### <a name="use-braces"></a>Usare le parentesi graffe

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

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a>Le classi, gli struct e le enumerazioni pubbliche devono essere tutti presenti nei propri file

Se la classe, lo struct o l'enumerazione possono essere resi privati, è possibile includere nello stesso file.  In questo modo si evitano problemi di compilazione con Unity e si garantisce che si verifichi un'astrazione corretta del codice, riducendo anche i conflitti e le modifiche che causano un'interruzione quando il codice deve cambiare.

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

### <a name="initialize-enums"></a>Inizializzare enumerazioni

Per assicurarsi che tutte le enumerazioni vengano inizializzate correttamente a partire da 0, .NET offre un collegamento ordinato per inizializzare automaticamente l'enumerazione aggiungendo semplicemente il primo valore (iniziale). (ad esempio, il valore 1 = 0 I valori rimanenti non sono obbligatori)

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

### <a name="order-enums-for-appropriate-extension"></a>Ordinare le enumerazioni per l'estensione appropriata

È fondamentale che, se è probabile che un'enumerazione sia estesa in futuro, per ordinare le impostazioni predefinite all'inizio dell'enumerazione, ciò garantisce che gli indici Enum non siano interessati dalle nuove aggiunte.

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

### <a name="review-enum-use-for-bitfields"></a>Esaminare l'uso dell'enumerazione per i campi di bit

Se è possibile che un'enumerazione richieda più stati come valore, ad esempio Handedness = Left & Right. L'enumerazione deve quindi essere decorata correttamente con BitFlags per consentirla di essere usata correttamente

Il file Handedness.cs ha un'implementazione concreta per questo

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

### <a name="hard-coded-file-paths"></a>Percorsi di file hard-coded

Quando si generano percorsi di file di stringa e in particolare si scrivono percorsi di stringa hard-coded, eseguire le operazioni seguenti:

1. Usare le API di C# [ `Path` quando](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) possibile, ad esempio `Path.Combine` o `Path.GetFullPath` .
1. Usare / o [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) invece di \ o \\ \\ .

Questi passaggi garantiscono che MRTK funzioni sia nei sistemi Windows e basati su Unix.

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

## <a name="best-practices-including-unity-recommendations"></a>Procedure consigliate, incluse le raccomandazioni di Unity

Alcune delle piattaforme di destinazione di questo progetto richiedono di prendere in considerazione le prestazioni. A questo scopo, prestare sempre attenzione quando si alloca memoria nel codice chiamato di frequente in algoritmi o cicli di aggiornamento ristretti.

### <a name="encapsulation"></a>Incapsulamento

Usare sempre campi privati e proprietà pubbliche se l'accesso al campo è necessario dall'esterno della classe o dello struct.  Assicurarsi di co-individuare il campo privato e la proprietà pubblica. In questo modo è più semplice vedere, a colpo d'occhio, ciò che sosporta la proprietà e che il campo è modificabile tramite script.

> [!NOTE]
> L'unica eccezione è per le strutture di dati che richiedono la serializzazione dei campi da parte di , in cui una classe di dati deve avere tutti i campi pubblici per il funzionamento della `JsonUtility` serializzazione.

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

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a>Memorizzare nella cache i valori e serializzarli nella scena/prefab quando possibile

Con il HoloLens in mente, è meglio ottimizzare le prestazioni e i riferimenti alla cache nella scena o nel prefab per limitare le allocazioni di memoria di runtime.

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

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a>Memorizzare nella cache i riferimenti ai materiali, non chiamare ogni volta ".material"

Unity creerà un nuovo materiale ogni volta che si usa ".material", causando una perdita di memoria se non viene pulita correttamente.

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

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a>Usare [la compilazione dipendente dalla](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) piattaforma per assicurarsi che Toolkit non interrompa la compilazione in un'altra piattaforma

- Usare per usare API non Unity specifiche della `WINDOWS_UWP` UWP. Ciò impedirà loro di provare a eseguire nell'editor o in piattaforme non supportate. Equivale a `UNITY_WSA && !UNITY_EDITOR` e deve essere usato a favore di .
- Usare per usare API Unity specifiche della `UNITY_WSA` UWP, ad esempio lo spazio dei `UnityEngine.XR.WSA` nomi . Verrà eseguito nell'editor quando la piattaforma è impostata su UWP, nonché nelle app UWP create.

Questo grafico consente di decidere quale usare, a seconda dei casi `#if` d'uso e delle impostazioni di compilazione previste.

|Piattaforma | UWP IL2CPP | UWP .NET | Editor |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | False | False | True |
| `UNITY_WSA` | True | True | True |
| `WINDOWS_UWP` | True | True | False |
| `UNITY_WSA && !UNITY_EDITOR` | True | True | False |
| `ENABLE_WINMD_SUPPORT` | True | True | False |
| `NETFX_CORE` | False | True | Falso |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a>Preferire DateTime.UtcNow rispetto a DateTime.Now

DateTime.UtcNow è più veloce di DateTime.Now. Nelle indagini sulle prestazioni precedenti è stato rilevato che l'uso di DateTime.Now aggiunge un overhead significativo soprattutto se usato nel ciclo Update(). [Altri hanno raggiunto lo stesso problema.](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now)

Preferire l'uso di DateTime.UtcNow a meno che non siano effettivamente necessari gli orari localizzati (un motivo legittimo potrebbe essere che si vuole visualizzare l'ora corrente nel fuso orario dell'utente). Se si hanno a che fare con orari relativi(ad esempio, il delta tra l'ultimo aggiornamento e ora), è meglio usare DateTime.UtcNow per evitare il sovraccarico delle conversioni del fuso orario.

## <a name="powershell-coding-conventions"></a>Convenzioni di codifica di PowerShell

Un subset della codebase MRTK usa PowerShell per l'infrastruttura della pipeline e vari script e utilità. Il nuovo codice di PowerShell deve seguire lo [stile PoshCode](https://poshcode.gitbooks.io/powershell-practice-and-style/).

## <a name="see-also"></a>Vedere anche

 [Convenzioni di codifica C# da MSDN](/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)
