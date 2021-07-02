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
# <a name="visual-themes"></a><span data-ttu-id="139f5-104">Temi degli oggetti visivi</span><span class="sxs-lookup"><span data-stu-id="139f5-104">Visual themes</span></span>

<span data-ttu-id="139f5-105">I temi consentono un controllo flessibile degli asset dell'esperienza utente in risposta a diverse transizioni di stato.</span><span class="sxs-lookup"><span data-stu-id="139f5-105">Themes allow for flexible control of UX assets in response to various states transitions.</span></span> <span data-ttu-id="139f5-106">Ciò può comportare la modifica del colore di un pulsante, il ridimensionamento di un elemento in risposta all'attivazione e così via. Il framework dei temi visivi è costituito da due parti chiave: 1) configurazione e 2) motori di runtime.</span><span class="sxs-lookup"><span data-stu-id="139f5-106">This may involve changing a button's color, resizing an element in response to focus, etc. The Visual Themes framework is made up of two key pieces: 1) configuration and 2) runtime engines.</span></span>

<span data-ttu-id="139f5-107">[Le configurazioni](#theme-configuration) dei temi [](#theme-engines) sono definizioni di proprietà e tipi, mentre i motori dei temi sono classi che utilizzano le configurazioni e implementano la logica per aggiornare trasformazioni, materiali e altro ancora in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="139f5-107">[Theme configurations](#theme-configuration) are definitions of properties and types while [Theme Engines](#theme-engines) are classes that consume the configurations and implement the logic to update transforms, materials, and more at runtime.</span></span>

## <a name="theme-configuration"></a><span data-ttu-id="139f5-108">Configurazione del tema</span><span class="sxs-lookup"><span data-stu-id="139f5-108">Theme configuration</span></span>

<span data-ttu-id="139f5-109">Le configurazioni dei temi [sono ScriptableObject che](https://docs.unity3d.com/Manual/class-ScriptableObject.html) definiscono come verranno inizializzati i motori dei temi in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="139f5-109">Theme configurations are [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) that define how Theme Engines will be initialized at runtime.</span></span> <span data-ttu-id="139f5-110">Definiscono le proprietà e i valori da usare in risposta all'input o ad altre modifiche di stato durante l'esecuzione dell'app.</span><span class="sxs-lookup"><span data-stu-id="139f5-110">They define what properties and values to utilize in response to input or other state changes when the app is running.</span></span> <span data-ttu-id="139f5-111">Come [asset ScriptableObjects,](https://docs.unity3d.com/Manual/class-ScriptableObject.html) le configurazioni dei temi possono essere definite una sola volta e quindi riutilizzabili in diversi componenti dell'esperienza utente.</span><span class="sxs-lookup"><span data-stu-id="139f5-111">As [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) assets, theme configurations can be defined once and then re-used across different UX components.</span></span>

<span data-ttu-id="139f5-112">Per creare un nuovo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset:</span><span class="sxs-lookup"><span data-stu-id="139f5-112">To create a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset:</span></span>

1) <span data-ttu-id="139f5-113">Fare clic con il pulsante destro *del mouse Project finestra*</span><span class="sxs-lookup"><span data-stu-id="139f5-113">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="139f5-114">Selezionare Create Mixed Reality Toolkit Theme **(Crea**  >  **tema Toolkit** realtà  >  **mista)**</span><span class="sxs-lookup"><span data-stu-id="139f5-114">Select **Create** > **Mixed Reality Toolkit** > **Theme**</span></span>

<span data-ttu-id="139f5-115">Gli asset di configurazione del tema di esempio sono disponibili in `MRTK/SDK/Features/UX/Interactable/Themes` .</span><span class="sxs-lookup"><span data-stu-id="139f5-115">Example Theme configuration assets can be found under `MRTK/SDK/Features/UX/Interactable/Themes`.</span></span>

![Esempio di ScriptableObject del tema nel controllo](../images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a><span data-ttu-id="139f5-117">Stati</span><span class="sxs-lookup"><span data-stu-id="139f5-117">States</span></span>

<span data-ttu-id="139f5-118">Quando si crea un nuovo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) , la prima cosa da impostare è quali stati sono disponibili.</span><span class="sxs-lookup"><span data-stu-id="139f5-118">When creating a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme), the first thing to set is what states are available.</span></span> <span data-ttu-id="139f5-119">La *proprietà States* indica il numero di valori che una configurazione Theme deve definire perché sarà presente un valore per ogni stato.</span><span class="sxs-lookup"><span data-stu-id="139f5-119">The *States* property indicates how many values a Theme configuration needs to define as there will be one value per state.</span></span> <span data-ttu-id="139f5-120">Nell'immagine di esempio precedente, gli stati predefiniti definiti per il componente [Interactable](interactable.md#general-input-settings) sono *Default,* *Focus,* *Pressed* e *Disabled.*</span><span class="sxs-lookup"><span data-stu-id="139f5-120">In the example image above, the [default states defined for the Interactable](interactable.md#general-input-settings) component are *Default*, *Focus*, *Pressed*, and *Disabled*.</span></span> <span data-ttu-id="139f5-121">Questi sono definiti nel file di `DefaultInteractableStates` asset (Assets/MRTK/SDK/Features/UX/Interactable/States).</span><span class="sxs-lookup"><span data-stu-id="139f5-121">These are defined in the `DefaultInteractableStates` (Assets/MRTK/SDK/Features/UX/Interactable/States) asset file.</span></span>

<span data-ttu-id="139f5-122">Per creare un nuovo [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) asset:</span><span class="sxs-lookup"><span data-stu-id="139f5-122">To create a new [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) asset:</span></span>

1) <span data-ttu-id="139f5-123">Fare clic con il pulsante destro *del mouse Project finestra*</span><span class="sxs-lookup"><span data-stu-id="139f5-123">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="139f5-124">Selezionare **Create** Mixed Reality Toolkit State  >  **(Crea stato** Toolkit realtà  >  **mista)**</span><span class="sxs-lookup"><span data-stu-id="139f5-124">Select **Create** > **Mixed Reality Toolkit** > **State**</span></span>

![Esempio scriptableObject di stati nel controllo](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="139f5-126">Uno ScriptableObject definisce sia l'elenco di stati che il tipo [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) di *StateModel* da creare per questi stati.</span><span class="sxs-lookup"><span data-stu-id="139f5-126">A [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject defines both the list of states as well as the type of *StateModel* to create for these states.</span></span> <span data-ttu-id="139f5-127">StateModel *è* una classe che estende e implementa la logica della macchina a [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) stati per generare lo stato corrente in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="139f5-127">A *StateModel* is a class that extends [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) and implements the state machine logic to generate the current state at runtime.</span></span> <span data-ttu-id="139f5-128">Lo stato corrente di questa classe viene in genere usato dai motori dei temi in fase di esecuzione per determinato i valori da impostare in base alle proprietà dei materiali, alle trasformazioni GameObject e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="139f5-128">The current state from this class is generally used by Theme Engines at runtime to dictate what values to set against material properties, GameObject transforms, and more.</span></span>

### <a name="theme-engine-properties"></a><span data-ttu-id="139f5-129">Proprietà del motore del tema</span><span class="sxs-lookup"><span data-stu-id="139f5-129">Theme engine properties</span></span>

<span data-ttu-id="139f5-130">Al di *fuori di States*, un asset definisce anche un elenco di motori a tema e le proprietà associate per questi [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) motori.</span><span class="sxs-lookup"><span data-stu-id="139f5-130">Outside of *States*, a [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset also defines a list of Theme Engines and the associated properties for these engines.</span></span> <span data-ttu-id="139f5-131">Un [motore Theme definisce](#theme-engines) di nuovo la logica per impostare i valori corretti su un GameObject in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="139f5-131">A [Theme engine](#theme-engines) again defines the logic to set the correct values against a GameObject at runtime.</span></span>

<span data-ttu-id="139f5-132">Un [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset può definire più motori di tema per ottenere transizioni sofisticate degli stati di visualizzazione che hanno come destinazione più proprietà GameObject.</span><span class="sxs-lookup"><span data-stu-id="139f5-132">A [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset can define multiple Theme Engines to achieve sophisticated visual states transitions targeting multiple GameObject properties.</span></span>

<span data-ttu-id="139f5-133">**Runtime del tema**</span><span class="sxs-lookup"><span data-stu-id="139f5-133">**Theme Runtime**</span></span>

<span data-ttu-id="139f5-134">Definisce il tipo di classe del motore Theme che verrà creato</span><span class="sxs-lookup"><span data-stu-id="139f5-134">Defines the class type of the Theme engine that will be created</span></span>

<span data-ttu-id="139f5-135">**Allentamento**</span><span class="sxs-lookup"><span data-stu-id="139f5-135">**Easing**</span></span>

<span data-ttu-id="139f5-136">Alcuni *motori dei temi,* se definiscono la proprietà [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) come true, supportano l'easing tra gli stati.</span><span class="sxs-lookup"><span data-stu-id="139f5-136">Some *Theme Engines*, if they define their property [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) as true, support easing between states.</span></span> <span data-ttu-id="139f5-137">Ad esempio, il lerping tra due colori quando si verifica una modifica dello stato.</span><span class="sxs-lookup"><span data-stu-id="139f5-137">For example, lerping between two colors when a state change occurs.</span></span> <span data-ttu-id="139f5-138">La *durata* definisce in secondi per quanto tempo è  possibile passare dal valore iniziale al valore finale e la curva di animazione definisce la frequenza di modifica durante tale periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="139f5-138">The *Duration* defines in seconds how long to ease from start value to end value and the *Animation Curve* defines the rate of change during that time period.</span></span>

<span data-ttu-id="139f5-139">**Proprietà shader**</span><span class="sxs-lookup"><span data-stu-id="139f5-139">**Shader properties**</span></span>

<span data-ttu-id="139f5-140">Alcuni *motori dei temi,* se definiscono la proprietà [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) come true, modificheranno determinate proprietà dello shader in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="139f5-140">Some *Theme Engines*, if they define their property [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) as true, will modify particular shader properties at runtime.</span></span> <span data-ttu-id="139f5-141">I *campi Shader* e *Proprietà* definiscono la proprietà shader di destinazione.</span><span class="sxs-lookup"><span data-stu-id="139f5-141">The *Shader* and *Property* fields define the shader property to target.</span></span>

### <a name="create-a-theme-configuration-via-code"></a><span data-ttu-id="139f5-142">Creare una configurazione del tema tramite codice</span><span class="sxs-lookup"><span data-stu-id="139f5-142">Create a theme configuration via code</span></span>

<span data-ttu-id="139f5-143">In generale, è più semplice progettare configurazioni dei temi tramite il controllo Unity, ma in alcuni casi i temi devono essere generati dinamicamente in fase di esecuzione tramite codice.</span><span class="sxs-lookup"><span data-stu-id="139f5-143">In general, it is easier to design Theme configurations via the Unity inspector but there are cases where Themes must be dynamically generated at runtime via code.</span></span> <span data-ttu-id="139f5-144">Il frammento di codice seguente offre un esempio di come eseguire questa attività.</span><span class="sxs-lookup"><span data-stu-id="139f5-144">The code snippet below gives an example of how to accomplish this task.</span></span>

<span data-ttu-id="139f5-145">Per accelerare lo sviluppo, i metodi helper seguenti sono utili per semplificare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="139f5-145">To help expedite development, the following helper methods are useful for simplifying setup.</span></span>

<span data-ttu-id="139f5-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable): crea un nuovo States ScriptableObject con i quattro valori di stato predefiniti usati nel [componente Interactable.](interactable.md)</span><span class="sxs-lookup"><span data-stu-id="139f5-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) - creates a new States ScriptableObject with the four default state values used in the [Interactable](interactable.md) component.</span></span>

<span data-ttu-id="139f5-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) - Ogni motore dei temi definisce una configurazione predefinita con le proprietà corrette necessarie per quel tipo di runtime Theme.</span><span class="sxs-lookup"><span data-stu-id="139f5-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) - Every Theme Engine defines a default configuration with the correct properties needed for that Theme runtime type.</span></span> <span data-ttu-id="139f5-148">Questo helper crea una definizione per il tipo di motore del tema specificato.</span><span class="sxs-lookup"><span data-stu-id="139f5-148">This helper creates a definition for the given Theme Engine type.</span></span>

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

## <a name="theme-engines"></a><span data-ttu-id="139f5-149">Motori dei temi</span><span class="sxs-lookup"><span data-stu-id="139f5-149">Theme engines</span></span>

<span data-ttu-id="139f5-150">Un [motore dei temi](#theme-engines) è una classe che si estende dalla classe [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) .</span><span class="sxs-lookup"><span data-stu-id="139f5-150">A [Theme Engine](#theme-engines) is a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="139f5-151">Le istanze di queste classi vengono create in fase di esecuzione e configurate con [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) un oggetto come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="139f5-151">These classes are instantiated at runtime and configured with a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object as outlined earlier.</span></span>

### <a name="default-theme-engines"></a><span data-ttu-id="139f5-152">Motori del tema predefiniti</span><span class="sxs-lookup"><span data-stu-id="139f5-152">Default theme engines</span></span>

<span data-ttu-id="139f5-153">MRTK viene fornito con un set predefinito di motori dei temi elencati di seguito:</span><span class="sxs-lookup"><span data-stu-id="139f5-153">MRTK ships with a default set of Theme Engines listed below:</span></span>

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

<span data-ttu-id="139f5-154">I motori dei temi predefiniti sono disponibili in `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` .</span><span class="sxs-lookup"><span data-stu-id="139f5-154">The default Theme Engines can be found under `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines`.</span></span>

### <a name="custom-theme-engines"></a><span data-ttu-id="139f5-155">Motori dei temi personalizzati</span><span class="sxs-lookup"><span data-stu-id="139f5-155">Custom theme engines</span></span>

<span data-ttu-id="139f5-156">Come indicato, un motore dei temi è definito come una classe che si estende dalla [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) classe .</span><span class="sxs-lookup"><span data-stu-id="139f5-156">As stated, a Theme Engine is defined as a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="139f5-157">Di conseguenza, il nuovo motore dei temi deve estendere solo questa classe e implementare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="139f5-157">Thus, new Theme Engine need only extend this class and implement the following:</span></span>

#### <a name="mandatory-implementations"></a><span data-ttu-id="139f5-158">Implementazioni obbligatorie</span><span class="sxs-lookup"><span data-stu-id="139f5-158">Mandatory implementations</span></span>

<span data-ttu-id="139f5-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)`(xref:Microsoft.MixedReality. Toolkit. Ui. InteractableThemeBase.SetValue)</span><span class="sxs-lookup"><span data-stu-id="139f5-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.SetValue)</span></span>

<span data-ttu-id="139f5-160">Per la proprietà specificata, che può essere identificata da , impostare il relativo valore di stato corrente nell'host GameObject di `ThemeStateProperty.Name` destinazione, ad esempio</span><span class="sxs-lookup"><span data-stu-id="139f5-160">For the given property, which can be identified by `ThemeStateProperty.Name`, set its current state value on the targeted GameObject host (i.e</span></span> <span data-ttu-id="139f5-161">impostare il colore del materiale e così via).</span><span class="sxs-lookup"><span data-stu-id="139f5-161">set the material color, etc).</span></span> <span data-ttu-id="139f5-162">*L'indice* indica il valore dello stato corrente a cui accedere e la percentuale *,* un valore float compreso tra 0 e 1, viene usato per l'easing/lerping tra i valori.</span><span class="sxs-lookup"><span data-stu-id="139f5-162">The *index* indicates the current state value to access and the *percentage*, a float between 0 and 1, is used for easing/lerping between values.</span></span>

<span data-ttu-id="139f5-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality. Toolkit. Ui. InteractableThemeBase.GetProperty)</span><span class="sxs-lookup"><span data-stu-id="139f5-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetProperty)</span></span>

<span data-ttu-id="139f5-164">Per la proprietà specificata, che può essere identificata da , restituisce il valore corrente impostato nel GameObject host di `ThemeStateProperty.Name` destinazione,ad esempio</span><span class="sxs-lookup"><span data-stu-id="139f5-164">For the given property, which can be identified by `ThemeStateProperty.Name`, return the current value set on the targeted Host  GameObject (i.e</span></span> <span data-ttu-id="139f5-165">il colore del materiale corrente, l'offset della posizione locale corrente e così via).</span><span class="sxs-lookup"><span data-stu-id="139f5-165">the current material color, the current local position offset, etc).</span></span> <span data-ttu-id="139f5-166">Viene usato principalmente per memorizzare nella cache il valore iniziale durante l'easing tra gli stati.</span><span class="sxs-lookup"><span data-stu-id="139f5-166">This is primarily used for caching the start value when easing between states.</span></span>

<span data-ttu-id="139f5-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality. Toolkit. Ui. InteractableThemeBase.GetDefaultThemeDefinition)</span><span class="sxs-lookup"><span data-stu-id="139f5-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetDefaultThemeDefinition)</span></span>

<span data-ttu-id="139f5-168">Restituisce un [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) oggetto che definisce le proprietà predefinite e la configurazione necessarie per il tema personalizzato</span><span class="sxs-lookup"><span data-stu-id="139f5-168">Returns a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object that defines the default properties and configuration needed for the custom theme</span></span>

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

<span data-ttu-id="139f5-169">Variante protetta della definizione pubblica, ad eccezione del valore ThemePropertyValue fornito da impostare invece di indirizzare l'uso della configurazione `SetValue()` dell'indice e/o della percentuale.</span><span class="sxs-lookup"><span data-stu-id="139f5-169">Protected variant of the public `SetValue()` definition, except provided ThemePropertyValue to set instead of directing to use index and/or percentage configuration.</span></span>

#### <a name="recommended-overrides"></a><span data-ttu-id="139f5-170">Override consigliati</span><span class="sxs-lookup"><span data-stu-id="139f5-170">Recommended overrides</span></span>

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

<span data-ttu-id="139f5-171">Eseguire qui i passaggi di inizializzazione per il parametro *GameObject* fornito e usando le proprietà e le configurazioni definite nel *parametro ThemeDefinition.*</span><span class="sxs-lookup"><span data-stu-id="139f5-171">Perform any initialization steps here targeting the provided *GameObject* parameter and using the properties and configurations defined in the *ThemeDefinition* parameter.</span></span> <span data-ttu-id="139f5-172">È consigliabile chiamare `base.Init(host, settings)` all'inizio di un override.</span><span class="sxs-lookup"><span data-stu-id="139f5-172">It is recommended to call `base.Init(host, settings)` at the beginning of an override.</span></span>

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

<span data-ttu-id="139f5-173">Se il motore dei temi personalizzato può supportare l'easing tra i valori configurati tramite la [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) proprietà .</span><span class="sxs-lookup"><span data-stu-id="139f5-173">If the custom Theme Engine can support easing between values which is configured via the [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) property.</span></span>

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

<span data-ttu-id="139f5-174">Se il motore dei temi personalizzato può supportare la destinazione delle proprietà dello shader.</span><span class="sxs-lookup"><span data-stu-id="139f5-174">If the custom Theme Engine can support targeting shader properties.</span></span> <span data-ttu-id="139f5-175">È consigliabile estendere da per trarre vantaggio dall'infrastruttura esistente per impostare/ottenere in modo efficiente le proprietà [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) dello shader tramite [MaterialPropertyBlocks.](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)</span><span class="sxs-lookup"><span data-stu-id="139f5-175">It is recommended to extend from [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) to benefit from the existing infrastructure to efficiently set/get shader properties via [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span></span> <span data-ttu-id="139f5-176">Le informazioni sulle proprietà dello shader vengono archiviate in [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) ogni tramite [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) e [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) .</span><span class="sxs-lookup"><span data-stu-id="139f5-176">The shader property information is stored in each [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) via [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) and [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName).</span></span>

> [!NOTE]
> <span data-ttu-id="139f5-177">Se si [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) estende , può anche essere utile eseguire l'override di [InteractableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) tramite *il nuovo .*</span><span class="sxs-lookup"><span data-stu-id="139f5-177">If extending [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme), it can also be useful to override the [InteractableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) via *new*.</span></span>
>
> <span data-ttu-id="139f5-178">Codice di esempio: `protected new const string DefaultShaderProperty = "_Color";`</span><span class="sxs-lookup"><span data-stu-id="139f5-178">Example code: `protected new const string DefaultShaderProperty = "_Color";`</span></span>
>
> <span data-ttu-id="139f5-179">Inoltre, le classi seguenti estendono la [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) classe che usa di nuovo [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) per modificare i valori delle proprietà dello shader.</span><span class="sxs-lookup"><span data-stu-id="139f5-179">Furthermore, the following classes below extend the [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) class which again uses [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) to modify shader property values.</span></span> <span data-ttu-id="139f5-180">Questo approccio [consente di migliorare le](https://docs.unity3d.com/Manual/DrawCallBatching.html) prestazioni perché *MaterialPropertyBlocks* non crea nuovi materiali di cui è stata creata un'istanza quando i valori cambiano.</span><span class="sxs-lookup"><span data-stu-id="139f5-180">This approach [helps performance](https://docs.unity3d.com/Manual/DrawCallBatching.html) because *MaterialPropertyBlocks* do not create new instanced materials when values change.</span></span> <span data-ttu-id="139f5-181">Tuttavia, l'accesso alle proprietà [tipiche della](https://docs.unity3d.com/ScriptReference/Material.html) classe Material non restituirà i valori previsti.</span><span class="sxs-lookup"><span data-stu-id="139f5-181">However, accessing the typical [Material](https://docs.unity3d.com/ScriptReference/Material.html) class properties will not return expected values.</span></span> <span data-ttu-id="139f5-182">Usare *MaterialPropertyBlocks per* ottenere e convalidare i valori correnti delle proprietà dei materiali,ad esempio</span><span class="sxs-lookup"><span data-stu-id="139f5-182">Use *MaterialPropertyBlocks* to get and validate current material property values (i.e</span></span> <span data-ttu-id="139f5-183">*_Color* o *_MainTex*).</span><span class="sxs-lookup"><span data-stu-id="139f5-183">*_Color* or *_MainTex*).</span></span>
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

<span data-ttu-id="139f5-184">Indica al tema di reimpostare le proprietà modificate sui valori originali impostati nel GameObject host quando è stato inizializzato il motore del tema.</span><span class="sxs-lookup"><span data-stu-id="139f5-184">Directs the theme to reset any modified properties back to their original values that were set on the host GameObject when this theme engine was initialized.</span></span>  

### <a name="custom-theme-engine-example"></a><span data-ttu-id="139f5-185">Esempio di motore del tema personalizzato</span><span class="sxs-lookup"><span data-stu-id="139f5-185">Custom theme engine example</span></span>

<span data-ttu-id="139f5-186">La classe seguente è un esempio di un nuovo motore dei temi personalizzato.</span><span class="sxs-lookup"><span data-stu-id="139f5-186">The class below is an example of a custom new Theme Engine.</span></span> <span data-ttu-id="139f5-187">Questa implementazione troverà un [componente MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) nell'oggetto host inizializzato e ne controlla la visibilità in base allo stato corrente.</span><span class="sxs-lookup"><span data-stu-id="139f5-187">This implementation will find a [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) component on the initialized host object and control its visibility based on the current state.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="139f5-188">Esempio end-to-end</span><span class="sxs-lookup"><span data-stu-id="139f5-188">End-to-end example</span></span>

<span data-ttu-id="139f5-189">Estendendo il motore dei temi personalizzato definito nella sezione precedente, l'esempio di codice seguente illustra come controllare questo tema in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="139f5-189">Extending off of the custom Theme Engine defined in the earlier section, the code example below demonstrates how to control this theme at runtime.</span></span> <span data-ttu-id="139f5-190">In particolare, come impostare lo stato corrente sul tema in modo che la visibilità di MeshRenderer sia aggiornata in modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="139f5-190">In particular, how to set the current state on the theme so the MeshRenderer visibility is updated appropriately.</span></span>

> [!NOTE]
> <span data-ttu-id="139f5-191">`theme.OnUpdate(state,force)` in genere deve essere chiamato nel metodo Update() per supportare i motori dei temi che utilizzano l'easing/lerping tra i valori.</span><span class="sxs-lookup"><span data-stu-id="139f5-191">`theme.OnUpdate(state,force)` should generally be called in the Update() method to support Theme Engines that utilize easing/lerping between values.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="139f5-192">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="139f5-192">See also</span></span>

- [<span data-ttu-id="139f5-193">Con interazione</span><span class="sxs-lookup"><span data-stu-id="139f5-193">Interactable</span></span>](interactable.md)
