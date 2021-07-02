---
title: Temi degli oggetti visivi
description: "Panoramica: Controllo flessibile dei temi visivi degli asset dell'esperienza utente in MRTK"
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, temi MRTK,
ms.openlocfilehash: d97c470bf1d77299c6848990cdc69d886d432ecb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177176"
---
# <a name="visual-themes"></a>Temi degli oggetti visivi

I temi consentono un controllo flessibile degli asset dell'esperienza utente in risposta a diverse transizioni di stato. Ciò può comportare la modifica del colore di un pulsante, il ridimensionamento di un elemento in risposta all'attivazione e così via. Il framework dei temi visivi è costituito da due parti chiave: 1) configurazione e 2) motori di runtime.

[Le configurazioni](#theme-configuration) dei temi [](#theme-engines) sono definizioni di proprietà e tipi, mentre i motori dei temi sono classi che utilizzano le configurazioni e implementano la logica per aggiornare trasformazioni, materiali e altro ancora in fase di esecuzione.

## <a name="theme-configuration"></a>Configurazione del tema

Le configurazioni dei temi [sono ScriptableObject che](https://docs.unity3d.com/Manual/class-ScriptableObject.html) definiscono come verranno inizializzati i motori dei temi in fase di esecuzione. Definiscono le proprietà e i valori da usare in risposta all'input o ad altre modifiche di stato durante l'esecuzione dell'app. Come [asset ScriptableObjects,](https://docs.unity3d.com/Manual/class-ScriptableObject.html) le configurazioni dei temi possono essere definite una sola volta e quindi riutilizzabili in diversi componenti dell'esperienza utente.

Per creare un nuovo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset:

1) Fare clic con il pulsante destro *del mouse Project finestra*
1) Selezionare Create Mixed Reality Toolkit Theme **(Crea**  >  **tema Toolkit** realtà  >  **mista)**

Gli asset di configurazione del tema di esempio sono disponibili in `MRTK/SDK/Features/UX/Interactable/Themes` .

![Esempio di ScriptableObject del tema nel controllo](../images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a>Stati

Quando si crea un nuovo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) , la prima cosa da impostare è quali stati sono disponibili. La *proprietà States* indica il numero di valori che una configurazione Theme deve definire perché sarà presente un valore per ogni stato. Nell'immagine di esempio precedente, gli stati predefiniti definiti per il componente [Interactable](interactable.md#general-input-settings) sono *Default,* *Focus,* *Pressed* e *Disabled.* Questi sono definiti nel file di `DefaultInteractableStates` asset (Assets/MRTK/SDK/Features/UX/Interactable/States).

Per creare un nuovo [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) asset:

1) Fare clic con il pulsante destro *del mouse Project finestra*
1) Selezionare **Create** Mixed Reality Toolkit State  >  **(Crea stato** Toolkit realtà  >  **mista)**

![Esempio scriptableObject di stati nel controllo](../images/interactable/DefaultInteractableStates.png)

Uno ScriptableObject definisce sia l'elenco di stati che il tipo [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) di *StateModel* da creare per questi stati. StateModel *è* una classe che estende e implementa la logica della macchina a [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) stati per generare lo stato corrente in fase di esecuzione. Lo stato corrente di questa classe viene in genere usato dai motori dei temi in fase di esecuzione per determinato i valori da impostare in base alle proprietà dei materiali, alle trasformazioni GameObject e altro ancora.

### <a name="theme-engine-properties"></a>Proprietà del motore del tema

Al di *fuori di States*, un asset definisce anche un elenco di motori a tema e le proprietà associate per questi [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) motori. Un [motore Theme definisce](#theme-engines) di nuovo la logica per impostare i valori corretti su un GameObject in fase di esecuzione.

Un [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset può definire più motori di tema per ottenere transizioni sofisticate degli stati di visualizzazione che hanno come destinazione più proprietà GameObject.

**Runtime del tema**

Definisce il tipo di classe del motore Theme che verrà creato

**Allentamento**

Alcuni *motori dei temi,* se definiscono la proprietà [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) come true, supportano l'easing tra gli stati. Ad esempio, il lerping tra due colori quando si verifica una modifica dello stato. La *durata* definisce in secondi per quanto tempo è  possibile passare dal valore iniziale al valore finale e la curva di animazione definisce la frequenza di modifica durante tale periodo di tempo.

**Proprietà shader**

Alcuni *motori dei temi,* se definiscono la proprietà [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) come true, modificheranno determinate proprietà dello shader in fase di esecuzione. I *campi Shader* e *Proprietà* definiscono la proprietà shader di destinazione.

### <a name="create-a-theme-configuration-via-code"></a>Creare una configurazione del tema tramite codice

In generale, è più semplice progettare configurazioni dei temi tramite il controllo Unity, ma in alcuni casi i temi devono essere generati dinamicamente in fase di esecuzione tramite codice. Il frammento di codice seguente offre un esempio di come eseguire questa attività.

Per accelerare lo sviluppo, i metodi helper seguenti sono utili per semplificare la configurazione.

[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable): crea un nuovo States ScriptableObject con i quattro valori di stato predefiniti usati nel [componente Interactable.](interactable.md)

[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) - Ogni motore dei temi definisce una configurazione predefinita con le proprietà corrette necessarie per quel tipo di runtime Theme. Questo helper crea una definizione per il tipo di motore del tema specificato.

```c#
// This code example builds a Theme ScriptableObject that can be used with an Interactable component.
// A random color is selected for the on pressed state every time this code is executed.

// Use the default states utilized in the Interactable component
var defaultStates = Interactable.GetDefaultInteractableStates();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

// Create the Theme configuration asset
Theme testTheme = ScriptableObject.CreateInstance<Theme>();
testTheme.States = defaultStates;
testTheme.Definitions = new List<ThemeDefinition>() { newThemeType };
```

## <a name="theme-engines"></a>Motori dei temi

Un [motore dei temi](#theme-engines) è una classe che si estende dalla classe [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) . Le istanze di queste classi vengono create in fase di esecuzione e configurate con [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) un oggetto come descritto in precedenza.

### <a name="default-theme-engines"></a>Motori del tema predefiniti

MRTK viene fornito con un set predefinito di motori dei temi elencati di seguito:

- [`InteractableActivateTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableActivateTheme)
- [`InteractableAnimatorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAnimatorTheme)
- [`InteractableAudioTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioTheme)
- [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
- [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
- [`InteractableGrabScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableGrabScaleTheme)
- [`InteractableMaterialTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableMaterialTheme)
- [`InteractableOffsetTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOffsetTheme)
- [`InteractableRotationTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableRotationTheme)
- [`InteractableScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableScaleTheme)
- [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme)
- [`InteractableStringTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStringTheme)
- [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
- [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

I motori dei temi predefiniti sono disponibili in `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` .

### <a name="custom-theme-engines"></a>Motori dei temi personalizzati

Come indicato, un motore dei temi è definito come una classe che si estende dalla [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) classe . Di conseguenza, il nuovo motore dei temi deve estendere solo questa classe e implementare quanto segue:

#### <a name="mandatory-implementations"></a>Implementazioni obbligatorie

`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)`(xref:Microsoft.MixedReality. Toolkit. Ui. InteractableThemeBase.SetValue)

Per la proprietà specificata, che può essere identificata da , impostare il relativo valore di stato corrente nell'host GameObject di `ThemeStateProperty.Name` destinazione, ad esempio impostare il colore del materiale e così via). *L'indice* indica il valore dello stato corrente a cui accedere e la percentuale *,* un valore float compreso tra 0 e 1, viene usato per l'easing/lerping tra i valori.

`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality. Toolkit. Ui. InteractableThemeBase.GetProperty)

Per la proprietà specificata, che può essere identificata da , restituisce il valore corrente impostato nel GameObject host di `ThemeStateProperty.Name` destinazione,ad esempio il colore del materiale corrente, l'offset della posizione locale corrente e così via). Viene usato principalmente per memorizzare nella cache il valore iniziale durante l'easing tra gli stati.

`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality. Toolkit. Ui. InteractableThemeBase.GetDefaultThemeDefinition)

Restituisce un [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) oggetto che definisce le proprietà predefinite e la configurazione necessarie per il tema personalizzato

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

Variante protetta della definizione pubblica, ad eccezione del valore ThemePropertyValue fornito da impostare invece di indirizzare l'uso della configurazione `SetValue()` dell'indice e/o della percentuale.

#### <a name="recommended-overrides"></a>Override consigliati

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

Eseguire qui i passaggi di inizializzazione per il parametro *GameObject* fornito e usando le proprietà e le configurazioni definite nel *parametro ThemeDefinition.* È consigliabile chiamare `base.Init(host, settings)` all'inizio di un override.

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

Se il motore dei temi personalizzato può supportare l'easing tra i valori configurati tramite la [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) proprietà .

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

Se il motore dei temi personalizzato può supportare la destinazione delle proprietà dello shader. È consigliabile estendere da per trarre vantaggio dall'infrastruttura esistente per impostare/ottenere in modo efficiente le proprietà [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) dello shader tramite [MaterialPropertyBlocks.](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) Le informazioni sulle proprietà dello shader vengono archiviate in [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) ogni tramite [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) e [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) .

> [!NOTE]
> Se si [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) estende , può anche essere utile eseguire l'override di [InteractableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) tramite *il nuovo .*
>
> Codice di esempio: `protected new const string DefaultShaderProperty = "_Color";`
>
> Inoltre, le classi seguenti estendono la [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) classe che usa di nuovo [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) per modificare i valori delle proprietà dello shader. Questo approccio [consente di migliorare le](https://docs.unity3d.com/Manual/DrawCallBatching.html) prestazioni perché *MaterialPropertyBlocks* non crea nuovi materiali di cui è stata creata un'istanza quando i valori cambiano. Tuttavia, l'accesso alle proprietà [tipiche della](https://docs.unity3d.com/ScriptReference/Material.html) classe Material non restituirà i valori previsti. Usare *MaterialPropertyBlocks per* ottenere e convalidare i valori correnti delle proprietà dei materiali,ad esempio *_Color* o *_MainTex*).
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

Indica al tema di reimpostare le proprietà modificate sui valori originali impostati nel GameObject host quando è stato inizializzato il motore del tema.  

### <a name="custom-theme-engine-example"></a>Esempio di motore del tema personalizzato

La classe seguente è un esempio di un nuovo motore dei temi personalizzato. Questa implementazione troverà un [componente MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) nell'oggetto host inizializzato e ne controlla la visibilità in base allo stato corrente.

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

// This class demonstrates a custom theme to control a Host's MeshRenderer visibility
public class MeshVisibilityTheme : InteractableThemeBase
{
    // Bool visibility does not make sense for lerping
    public override bool IsEasingSupported => false;

    // No material or shaders are being modified
    public override bool AreShadersSupported => false;

    // Cache reference to the MeshRenderer component on our Host
    private MeshRenderer meshRenderer;

    public MeshVisibilityTheme()
    {
        Types = new Type[] { typeof(MeshRenderer) };
        Name = "Mesh Visibility Theme";
    }

    // Define a default configuration to simplify initialization of this theme engine
    // There is only one state property with a value per available state
    // This state property is a boolean that defines whether the renderer is enabled
    public override ThemeDefinition GetDefaultThemeDefinition()
    {
        return new ThemeDefinition()
        {
            ThemeType = GetType(),
            StateProperties = new List<ThemeStateProperty>()
            {
                new ThemeStateProperty()
                {
                    Name = "Mesh Visible",
                    Type = ThemePropertyTypes.Bool,
                    Values = new List<ThemePropertyValue>(),
                    Default = new ThemePropertyValue() { Bool = true }
                },
            },
            CustomProperties = new List<ThemeProperty>()
        };
    }

    // When initializing, cache a reference to the MeshRenderer component
    public override void Init(GameObject host, ThemeDefinition definition)
    {
        base.Init(host, definition);

        meshRenderer = host.GetComponent<MeshRenderer>();
    }

    // Get the current state of the MeshRenderer visibility
    public override ThemePropertyValue GetProperty(ThemeStateProperty property)
    {
        return new ThemePropertyValue()
        {
            Bool = meshRenderer.enabled
        };
    }

    // Update the MeshRenderer visibility based on the property state value data
    public override void SetValue(ThemeStateProperty property, int index, float percentage)
    {
        meshRenderer.enabled = property.Values[index].Bool;
    }
}
```

## <a name="end-to-end-example"></a>Esempio end-to-end

Estendendo il motore dei temi personalizzato definito nella sezione precedente, l'esempio di codice seguente illustra come controllare questo tema in fase di esecuzione. In particolare, come impostare lo stato corrente sul tema in modo che la visibilità di MeshRenderer sia aggiornata in modo appropriato.

> [!NOTE]
> `theme.OnUpdate(state,force)` in genere deve essere chiamato nel metodo Update() per supportare i motori dei temi che utilizzano l'easing/lerping tra i valori.

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

public class MeshVisibilityController : MonoBehaviour
{
    private MeshVisibilityTheme themeEngine;
    private bool hideMesh = false;

    private void Start()
    {
        // Define the default configuration. State 0 will be on while State 1 will be off
        var themeDefinition = ThemeDefinition.GetDefaultThemeDefinition<MeshVisibilityTheme>().Value;
        themeDefinition.StateProperties[0].Values = new List<ThemePropertyValue>()
        {
            new ThemePropertyValue() { Bool = true }, // show state
            new ThemePropertyValue() { Bool = false }, // hide state
        };

        // Create the actual Theme engine and initialize it with the GameObject we are attached to
        themeEngine = (MeshVisibilityTheme)InteractableThemeBase.CreateAndInitTheme(themeDefinition, this.gameObject);
    }

    private void Update()
    {
        // Update the theme engine to set our MeshRenderer visibility
        // based on our current state (i.e the hideMesh variable)
        themeEngine.OnUpdate(Convert.ToInt32(hideMesh));
    }

    public void ToggleVisibility()
    {
        // Alternate state of visibility
        hideMesh = !hideMesh;
    }
}
```

## <a name="see-also"></a>Vedere anche

- [Con interazione](interactable.md)
