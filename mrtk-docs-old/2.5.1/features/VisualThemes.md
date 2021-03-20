---
title: VisualThemes
description: Panoramica dei temi visivi controllo flessibile degli asset UX in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, MRTK temi,
ms.openlocfilehash: 04a1b69b32846e235f8095c9018b7919971ab907
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683904"
---
# <a name="visual-themes"></a>Temi visivi

I temi consentono un controllo flessibile delle risorse UX in risposta a diverse transizioni degli Stati. Questo può comportare la modifica del colore di un pulsante, il ridimensionamento di un elemento in risposta allo stato attivo e così via. Il Framework dei temi visivi è costituito da due componenti chiave: 1) configurazione e 2) motori di Runtime.

Le [configurazioni dei temi](#theme-configuration) sono definizioni di proprietà e tipi, mentre i motori di [tema](#theme-engines) sono classi che utilizzano le configurazioni e implementano la logica per aggiornare le trasformazioni, i materiali e molto altro in fase di esecuzione.

## <a name="theme-configuration"></a>Configurazione del tema

Le configurazioni del tema sono [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) che definiscono la modalità di inizializzazione motori di tema in fase di esecuzione. Definiscono le proprietà e i valori da usare in risposta all'input o ad altre modifiche di stato quando l'app è in esecuzione. Come asset [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) , le configurazioni dei temi possono essere definite una volta e quindi riutilizzate tra diversi componenti UX.

Per creare un nuovo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset:

1) Fare clic con il pulsante destro del mouse nella *finestra del progetto*
1) Selezionare **Crea**  >  tema del **Toolkit di realtà mista**  >  

Gli asset di configurazione del tema di esempio sono disponibili in `MRTK/SDK/Features/UX/Interactable/Themes` .

![Esempio di ScriptableObject del tema in Inspector](images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a>Stati

Quando si crea un nuovo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) , il primo elemento da impostare è quali Stati sono disponibili. La proprietà *States* indica il numero di valori che devono essere definiti da una configurazione di tema poiché sarà presente un valore per stato. Nell'immagine di esempio precedente, gli [stati predefiniti definiti per il componente interagibile](ux-building-blocks/Interactable.md#general-input-settings) sono *default*, *Focus*, *Pressed* e *disabled*. Questi vengono definiti nel `DefaultInteractableStates` file di asset (assets/MRTK/SDK/features/UX/interactable/States).

Per creare un nuovo [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) asset:

1) Fare clic con il pulsante destro del mouse nella *finestra del progetto*
1) Selezionare **Crea**  >  stato del **Toolkit di realtà mista**  >  

![Esempio di ScriptableObject di stati in Inspector](images/interactable/DefaultInteractableStates.png)

Un [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject definisce sia l'elenco di Stati che il tipo di *StateModel* da creare per questi Stati. Un *StateModel* è una classe che estende [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) e implementa la logica della macchina a stati per generare lo stato corrente in fase di esecuzione. Lo stato corrente di questa classe viene in genere usato dai motori del tema in fase di esecuzione per determinare quali valori impostare sulle proprietà del materiale, le trasformazioni GameObject e altro ancora.

### <a name="theme-engine-properties"></a>Proprietà del motore del tema

Al di fuori degli *Stati*, un [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) Asset definisce anche un elenco di motori di tema e le proprietà associate per questi motori. Un [motore di tema](#theme-engines) definisce di nuovo la logica per impostare i valori corretti rispetto a un GameObject in fase di esecuzione.

Un [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset può definire più motori di tema per ottenere transizioni di stati visivi sofisticate destinate a più proprietà GameObject.

**Runtime del tema**

Definisce il tipo di classe del motore del tema che verrà creato

**Interpolazione**

Alcuni *motori di tema*, se definiscono la proprietà [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) su true, supportano l'interpolazione tra gli Stati. Ad esempio, lerping tra due colori quando si verifica una modifica dello stato. La *durata* definisce in secondi per quanto tempo è possibile semplificare dal valore iniziale al valore finale e la *curva di animazione* definisce la frequenza di modifica durante tale periodo di tempo.

**Proprietà shader**

Alcuni *motori di tema*, se definiscono la proprietà [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) su true, modificheranno determinate proprietà dello shader in fase di esecuzione. I campi *shader* e *Property* definiscono la proprietà shader di destinazione.

### <a name="create-a-theme-configuration-via-code"></a>Creare una configurazione del tema tramite codice

In generale, è più facile progettare le configurazioni del tema tramite il controllo Unity, ma in alcuni casi i temi devono essere generati dinamicamente in fase di esecuzione tramite codice. Il frammento di codice riportato di seguito fornisce un esempio di come eseguire questa attività.

Per facilitare lo sviluppo, i seguenti metodi helper sono utili per semplificare la configurazione.

[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) -Crea un nuovo stato ScriptableObject con i quattro valori di stato predefiniti usati nel componente [interactable](ux-building-blocks/Interactable.md) .

[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) -Ogni motore di tema definisce una configurazione predefinita con le proprietà corrette necessarie per il tipo di runtime del tema. Questo helper crea una definizione per il tipo di motore di tema specificato.

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

## <a name="theme-engines"></a>Motori del tema

Un [motore di tema](#theme-engines) è una classe che si estende dalla [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) classe. Queste classi vengono create in fase di esecuzione e configurate con un [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) oggetto come descritto in precedenza.

### <a name="default-theme-engines"></a>Motori di tema predefiniti

MRTK viene fornito con un set predefinito di motori di tema elencati di seguito:

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

I motori di tema predefiniti sono disponibili in `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` .

### <a name="custom-theme-engines"></a>Motori di tema personalizzati

Come indicato, un motore di tema viene definito come una classe che si estende dalla [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) classe. Pertanto, il nuovo motore di tema deve estendere questa classe e implementare quanto segue:

#### <a name="mandatory-implementations"></a>Implementazioni obbligatorie

`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (xrif: Microsoft. MixedReality. Toolkit. UI. InteractableThemeBase. SetValue)

Per la proprietà specificata, che può essere identificata da `ThemeStateProperty.Name` , impostare il valore dello stato corrente sull'host GameObject di destinazione, ad esempio impostare il colore del materiale e così via). L' *Indice* indica il valore dello stato corrente a cui accedere e la *percentuale*, ovvero un valore float compreso tra 0 e 1, per l'interpolazione/lerping tra i valori.

`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xrif: Microsoft. MixedReality. Toolkit. UI. InteractableThemeBase. GetProperty)

Per la proprietà specificata, che può essere identificata da `ThemeStateProperty.Name` , restituire il valore corrente impostato sul GameObject host di destinazione (ad esempio colore del materiale corrente, offset della posizione locale corrente e così via. Questa operazione viene utilizzata principalmente per la memorizzazione nella cache del valore iniziale durante l'interpolazione tra gli Stati.

`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xrif: Microsoft. MixedReality. Toolkit. UI. InteractableThemeBase. GetDefaultThemeDefinition)

Restituisce un [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) oggetto che definisce le proprietà predefinite e la configurazione necessaria per il tema personalizzato.

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

Variante protetta della definizione Public `SetValue()` , ad eccezione del fatto che ThemePropertyValue è stato impostato anziché indirizzare per usare la configurazione di indice e/o percentuale.

#### <a name="recommended-overrides"></a>Sostituzioni consigliate

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

Eseguire tutti i passaggi di inizializzazione che fanno riferimento al parametro *GameObject* fornito e usando le proprietà e le configurazioni definite nel parametro *ThemeDefinition* . Si consiglia di chiamare `base.Init(host, settings)` all'inizio di una sostituzione.

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

Se il motore del tema personalizzato può supportare l'interpolazione tra i valori configurati tramite la [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) Proprietà.

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

Se il motore del tema personalizzato può supportare la destinazione delle proprietà dello shader. È consigliabile estendere da [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) per trarre vantaggio dall'infrastruttura esistente per impostare/ottenere in modo efficiente le proprietà dello shader tramite [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html). Le informazioni sulle proprietà dello shader vengono archiviate in ogni [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) tramite [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) e [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) .

> [!NOTE]
> Se [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) si estende, può anche essere utile eseguire l'override di [InteractableShaderTheme. DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) tramite *New*.
>
> Codice di esempio: `protected new const string DefaultShaderProperty = "_Color";`
>
> Inoltre, le classi seguenti estendono la [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) classe che usa di nuovo [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) per modificare i valori delle proprietà dello shader. Questo approccio [aiuta a migliorare le prestazioni](https://docs.unity3d.com/Manual/DrawCallBatching.html) perché *MaterialPropertyBlocks* non crea nuovi materiali di istanza quando cambiano i valori. Tuttavia, l'accesso alle proprietà tipiche della classe [Material](https://docs.unity3d.com/ScriptReference/Material.html) non restituisce i valori previsti. Usare *MaterialPropertyBlocks* per ottenere e convalidare i valori delle proprietà materiali correnti (ad esempio *_Color* o *_MainTex*).
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

Indica al tema di reimpostare le proprietà modificate sui valori originali impostati nell'host GameObject quando il motore del tema è stato inizializzato.  

### <a name="custom-theme-engine-example"></a>Esempio di motore di tema personalizzato

La classe seguente è un esempio di un nuovo motore di tema personalizzato. Questa implementazione troverà un componente [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) sull'oggetto host inizializzato e ne controllerà la visibilità in base allo stato corrente.

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

Se si estende il motore dei temi personalizzato definito nella sezione precedente, l'esempio di codice seguente illustra come controllare questo tema in fase di esecuzione. In particolare, come impostare lo stato corrente sul tema in modo che la visibilità MeshRenderer venga aggiornata in modo appropriato.

> [!NOTE]
> `theme.OnUpdate(state,force)` in genere deve essere chiamato nel metodo Update () per supportare i motori di tema che usano l'interpolazione/lerping tra i valori.

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

- [Con cui](ux-building-blocks/Interactable.md)
