---
title: Oggetti visiviThemes
description: Panoramica del controllo flessibile dei temi visivi degli asset dell'esperienza utente in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, temi MRTK,
ms.openlocfilehash: 6e09540f090a2964c0bc2ec154c0bf3f294c59adba5fd9a7d45e2ff110260527
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213398"
---
# <a name="visual-themes"></a>Temi visivi

I temi consentono un controllo flessibile degli asset dell'esperienza utente in risposta a diverse transizioni di stati. Ciò può comportare la modifica del colore di un pulsante, il ridimensionamento di un elemento in risposta all'attivazione e così via. Il framework temi visivi è costituito da due parti chiave: 1) configurazione e 2) motori di runtime.

[Le configurazioni](#theme-configuration) del tema [](#theme-engines) sono definizioni di proprietà e tipi, mentre i motori tema sono classi che utilizzano le configurazioni e implementano la logica per aggiornare trasformazioni, materiali e altro ancora in fase di esecuzione.

## <a name="theme-configuration"></a>Configurazione del tema

Le configurazioni del tema [sono ScriptableObject che](https://docs.unity3d.com/Manual/class-ScriptableObject.html) definiscono la modalità di inizializzazione dei motori tema in fase di esecuzione. Definiscono le proprietà e i valori da utilizzare in risposta all'input o ad altre modifiche dello stato quando l'app è in esecuzione. Come [asset ScriptableObjects,](https://docs.unity3d.com/Manual/class-ScriptableObject.html) le configurazioni del tema possono essere definite una sola volta e quindi riutilizzabili in diversi componenti dell'esperienza utente.

Per creare un nuovo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset:

1) Fare clic con il pulsante destro *del mouse Project finestra*
1) Selezionare **Crea**  >  **tema Toolkit** realtà  >  **mista**

Gli asset di configurazione del tema di esempio sono disponibili in `MRTK/SDK/Features/UX/Interactable/Themes` .

![Esempio scriptableObject del tema nel controllo](images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a>Stati

Quando si crea un nuovo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) , la prima cosa da impostare è quali stati sono disponibili. La *proprietà States* indica il numero di valori che una configurazione theme deve definire perché sarà presente un valore per stato. Nell'immagine di esempio precedente, gli stati predefiniti definiti per il componente [Interactable](ux-building-blocks/interactable.md#general-input-settings) sono *Default*, *Focus*, *Pressed* e *Disabled*. Questi sono definiti nel `DefaultInteractableStates` file di asset (Assets/MRTK/SDK/Features/UX/Interactable/States).

Per creare un nuovo [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) asset:

1) Fare clic con il pulsante destro *del mouse Project finestra*
1) Selezionare **Crea**  >  **realtà mista Toolkit**  >  **stato**

![Esempio di ScriptableObject di stati nel controllo](images/interactable/DefaultInteractableStates.png)

ScriptableObject definisce sia l'elenco di stati che il [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) tipo di *StateModel* da creare per questi stati. StateModel *è* una classe che estende e implementa la logica della macchina a [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) stati per generare lo stato corrente in fase di esecuzione. Lo stato corrente di questa classe viene in genere usato dai motori tema in fase di esecuzione per indicare quali valori impostare sulle proprietà del materiale, sulle trasformazioni GameObject e altro ancora.

### <a name="theme-engine-properties"></a>Proprietà del motore del tema

Al di *fuori degli* stati , un asset definisce anche un elenco di motori tema e le proprietà associate per [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) questi motori. Un [motore tema definisce](#theme-engines) di nuovo la logica per impostare i valori corretti su un GameObject in fase di esecuzione.

Un asset può definire più motori tema per ottenere transizioni sofisticate degli stati di visualizzazione che hanno come [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) destinazione più proprietà GameObject.

**Runtime del tema**

Definisce il tipo di classe del motore tema che verrà creato

**Allentamento**

Alcuni *motori tema,* se definiscono la proprietà [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) come true, supportano l'easing tra gli stati. Ad esempio, la lerping tra due colori quando si verifica una modifica dello stato. La *durata* definisce in secondi per quanto tempo è  possibile passare dal valore iniziale al valore finale e la curva di animazione definisce la velocità di modifica durante tale periodo di tempo.

**Proprietà dello shader**

Alcuni *motori tema,* se definiscono la proprietà [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) come true, modificheranno determinate proprietà dello shader in fase di esecuzione. I *campi Shader* e *Proprietà* definiscono la proprietà shader di destinazione.

### <a name="create-a-theme-configuration-via-code"></a>Creare una configurazione del tema tramite codice

In generale, è più semplice progettare configurazioni dei temi tramite il controllo Unity, ma in alcuni casi i temi devono essere generati dinamicamente in fase di esecuzione tramite codice. Il frammento di codice seguente fornisce un esempio di come eseguire questa attività.

Per accelerare lo sviluppo, i metodi helper seguenti sono utili per semplificare la configurazione.

[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable): crea un nuovo States ScriptableObject con i quattro valori di stato predefiniti usati nel [componente Interactable.](ux-building-blocks/interactable.md)

[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) - Ogni motore tema definisce una configurazione predefinita con le proprietà corrette necessarie per il tipo di runtime Theme. Questo helper crea una definizione per il tipo di motore tema specificato.

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

## <a name="theme-engines"></a>Motori a tema

Un [motore tema](#theme-engines) è una classe che si estende dalla classe [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) . Viene creata un'istanza di queste classi in fase di esecuzione e configurata con un [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) oggetto come descritto in precedenza.

### <a name="default-theme-engines"></a>Motori tema predefiniti

MRTK viene fornito con un set predefinito di motori a tema elencati di seguito:

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

I motori tema predefiniti sono disponibili in `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` .

### <a name="custom-theme-engines"></a>Motori tema personalizzati

Come indicato, un motore tema è definito come classe che si estende dalla [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) classe . Di conseguenza, il nuovo motore dei temi deve estendere solo questa classe e implementare quanto segue:

#### <a name="mandatory-implementations"></a>Implementazioni obbligatorie

`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)`(xref:Microsoft.MixedReality. Toolkit. Ui. InteractableThemeBase.SetValue)

Per la proprietà specificata, che può essere identificata da , impostare il relativo valore di stato corrente nell'host GameObject di `ThemeStateProperty.Name` destinazione, ad esempio impostare il colore del materiale e così via). *L'indice* indica il valore dello stato corrente a cui accedere e la *percentuale,* un valore float compreso tra 0 e 1, viene usato per l'easing/lerping tra valori.

`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality. Toolkit. Ui. InteractableThemeBase.GetProperty)

Per la proprietà specificata, che può essere identificata da , restituisce il valore corrente impostato nell'oggetto GameObject host di `ThemeStateProperty.Name` destinazione, ad esempio il colore del materiale corrente, l'offset della posizione locale corrente e così via). Viene usato principalmente per memorizzare nella cache il valore iniziale durante l'allerta tra gli stati.

`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality. Toolkit. Ui. InteractableThemeBase.GetDefaultThemeDefinition)

Restituisce un [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) oggetto che definisce le proprietà predefinite e la configurazione necessarie per il tema personalizzato

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

Variante protetta della definizione pubblica, ad eccezione di ThemePropertyValue fornito da impostare invece di indirizzare all'uso `SetValue()` della configurazione dell'indice e/o della percentuale.

#### <a name="recommended-overrides"></a>Sostituzioni consigliate

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

Eseguire qui i passaggi di inizializzazione che hanno come destinazione il parametro *GameObject* fornito e usando le proprietà e le configurazioni definite nel *parametro ThemeDefinition.* È consigliabile chiamare `base.Init(host, settings)` all'inizio di un override.

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

Se il motore tema personalizzato può supportare l'easing tra i valori configurati tramite la [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) proprietà .

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

Se il motore tema personalizzato può supportare la destinazione delle proprietà dello shader. È consigliabile estendere da per trarre vantaggio dall'infrastruttura esistente per impostare/ottenere in modo efficiente le proprietà [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) dello shader tramite [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html). Le informazioni sulle proprietà dello shader vengono archiviate in [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) ogni tramite [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) e [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) .

> [!NOTE]
> Se si [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) estende , può anche essere utile eseguire l'override di [InteractableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) tramite *il nuovo*.
>
> Codice di esempio: `protected new const string DefaultShaderProperty = "_Color";`
>
> Inoltre, le classi seguenti estendono la classe che usa di nuovo [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) per modificare i valori delle proprietà shader. Questo approccio [consente di migliorare le](https://docs.unity3d.com/Manual/DrawCallBatching.html) prestazioni perché *MaterialPropertyBlocks* non crea nuovi materiali con istanze quando i valori cambiano. Tuttavia, l'accesso alle proprietà [tipiche della](https://docs.unity3d.com/ScriptReference/Material.html) classe Material non restituirà i valori previsti. Usare *MaterialPropertyBlocks* per ottenere e convalidare i valori correnti delle proprietà del materiale,ad esempio *_Color* o *_MainTex*).
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

Indica al tema di reimpostare le proprietà modificate sui valori originali impostati nell'host GameObject quando questo motore del tema è stato inizializzato.  

### <a name="custom-theme-engine-example"></a>Esempio di motore tema personalizzato

La classe seguente è un esempio di un nuovo motore tema personalizzato. Questa implementazione troverà un [componente MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) nell'oggetto host inizializzato e ne controlla la visibilità in base allo stato corrente.

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

Estendendo il motore tema personalizzato definito nella sezione precedente, l'esempio di codice seguente illustra come controllare questo tema in fase di esecuzione. In particolare, come impostare lo stato corrente sul tema in modo che la visibilità di MeshRenderer sia aggiornata in modo appropriato.

> [!NOTE]
> `theme.OnUpdate(state,force)` in genere deve essere chiamato nel metodo Update() per supportare i motori a tema che utilizzano l'easing/lerping tra i valori.

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

## <a name="see-also"></a>Vedi anche

- [Interagibile](ux-building-blocks/interactable.md)
