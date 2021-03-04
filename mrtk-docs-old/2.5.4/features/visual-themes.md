---
title: VisualThemes
description: Panoramica dei temi visivi controllo flessibile degli asset UX in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, MRTK temi,
ms.openlocfilehash: fa5407120a13e6af56afd6f89bd813cdf63d23ea
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781936"
---
# <a name="visual-themes"></a><span data-ttu-id="e230b-104">Temi visivi</span><span class="sxs-lookup"><span data-stu-id="e230b-104">Visual themes</span></span>

<span data-ttu-id="e230b-105">I temi consentono un controllo flessibile delle risorse UX in risposta a diverse transizioni degli Stati.</span><span class="sxs-lookup"><span data-stu-id="e230b-105">Themes allow for flexible control of UX assets in response to various states transitions.</span></span> <span data-ttu-id="e230b-106">Questo può comportare la modifica del colore di un pulsante, il ridimensionamento di un elemento in risposta allo stato attivo e così via. Il Framework dei temi visivi è costituito da due componenti chiave: 1) configurazione e 2) motori di Runtime.</span><span class="sxs-lookup"><span data-stu-id="e230b-106">This may involve changing a button's color, resizing an element in response to focus, etc. The Visual Themes framework is made up of two key pieces: 1) configuration and 2) runtime engines.</span></span>

<span data-ttu-id="e230b-107">Le [configurazioni dei temi](#theme-configuration) sono definizioni di proprietà e tipi, mentre i motori di [tema](#theme-engines) sono classi che utilizzano le configurazioni e implementano la logica per aggiornare le trasformazioni, i materiali e molto altro in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="e230b-107">[Theme configurations](#theme-configuration) are definitions of properties and types while [Theme Engines](#theme-engines) are classes that consume the configurations and implement the logic to update transforms, materials, and more at runtime.</span></span>

## <a name="theme-configuration"></a><span data-ttu-id="e230b-108">Configurazione del tema</span><span class="sxs-lookup"><span data-stu-id="e230b-108">Theme configuration</span></span>

<span data-ttu-id="e230b-109">Le configurazioni del tema sono [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) che definiscono la modalità di inizializzazione motori di tema in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="e230b-109">Theme configurations are [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) that define how Theme Engines will be initialized at runtime.</span></span> <span data-ttu-id="e230b-110">Definiscono le proprietà e i valori da usare in risposta all'input o ad altre modifiche di stato quando l'app è in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="e230b-110">They define what properties and values to utilize in response to input or other state changes when the app is running.</span></span> <span data-ttu-id="e230b-111">Come asset [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) , le configurazioni dei temi possono essere definite una volta e quindi riutilizzate tra diversi componenti UX.</span><span class="sxs-lookup"><span data-stu-id="e230b-111">As [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) assets, theme configurations can be defined once and then re-used across different UX components.</span></span>

<span data-ttu-id="e230b-112">Per creare un nuovo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset:</span><span class="sxs-lookup"><span data-stu-id="e230b-112">To create a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset:</span></span>

1) <span data-ttu-id="e230b-113">Fare clic con il pulsante destro del mouse nella *finestra del progetto*</span><span class="sxs-lookup"><span data-stu-id="e230b-113">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="e230b-114">Selezionare **Crea**  >  tema del **Toolkit di realtà mista**  >  </span><span class="sxs-lookup"><span data-stu-id="e230b-114">Select **Create** > **Mixed Reality Toolkit** > **Theme**</span></span>

<span data-ttu-id="e230b-115">Gli asset di configurazione del tema di esempio sono disponibili in `MRTK/SDK/Features/UX/Interactable/Themes` .</span><span class="sxs-lookup"><span data-stu-id="e230b-115">Example Theme configuration assets can be found under `MRTK/SDK/Features/UX/Interactable/Themes`.</span></span>

![Esempio di ScriptableObject del tema in Inspector](images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a><span data-ttu-id="e230b-117">Stati</span><span class="sxs-lookup"><span data-stu-id="e230b-117">States</span></span>

<span data-ttu-id="e230b-118">Quando si crea un nuovo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) , il primo elemento da impostare è quali Stati sono disponibili.</span><span class="sxs-lookup"><span data-stu-id="e230b-118">When creating a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme), the first thing to set is what states are available.</span></span> <span data-ttu-id="e230b-119">La proprietà *States* indica il numero di valori che devono essere definiti da una configurazione di tema poiché sarà presente un valore per stato.</span><span class="sxs-lookup"><span data-stu-id="e230b-119">The *States* property indicates how many values a Theme configuration needs to define as there will be one value per state.</span></span> <span data-ttu-id="e230b-120">Nell'immagine di esempio precedente, gli [stati predefiniti definiti per il componente interagibile](ux-building-blocks/interactable.md#general-input-settings) sono *default*, *Focus*, *Pressed* e *disabled*.</span><span class="sxs-lookup"><span data-stu-id="e230b-120">In the example image above, the [default states defined for the Interactable](ux-building-blocks/interactable.md#general-input-settings) component are *Default*, *Focus*, *Pressed*, and *Disabled*.</span></span> <span data-ttu-id="e230b-121">Questi vengono definiti nel `DefaultInteractableStates` file di asset (assets/MRTK/SDK/features/UX/interactable/States).</span><span class="sxs-lookup"><span data-stu-id="e230b-121">These are defined in the `DefaultInteractableStates` (Assets/MRTK/SDK/Features/UX/Interactable/States) asset file.</span></span>

<span data-ttu-id="e230b-122">Per creare un nuovo [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) asset:</span><span class="sxs-lookup"><span data-stu-id="e230b-122">To create a new [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) asset:</span></span>

1) <span data-ttu-id="e230b-123">Fare clic con il pulsante destro del mouse nella *finestra del progetto*</span><span class="sxs-lookup"><span data-stu-id="e230b-123">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="e230b-124">Selezionare **Crea**  >  stato del **Toolkit di realtà mista**  >  </span><span class="sxs-lookup"><span data-stu-id="e230b-124">Select **Create** > **Mixed Reality Toolkit** > **State**</span></span>

![Esempio di ScriptableObject di stati in Inspector](images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="e230b-126">Un [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject definisce sia l'elenco di Stati che il tipo di *StateModel* da creare per questi Stati.</span><span class="sxs-lookup"><span data-stu-id="e230b-126">A [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject defines both the list of states as well as the type of *StateModel* to create for these states.</span></span> <span data-ttu-id="e230b-127">Un *StateModel* è una classe che estende [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) e implementa la logica della macchina a stati per generare lo stato corrente in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="e230b-127">A *StateModel* is a class that extends [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) and implements the state machine logic to generate the current state at runtime.</span></span> <span data-ttu-id="e230b-128">Lo stato corrente di questa classe viene in genere usato dai motori del tema in fase di esecuzione per determinare quali valori impostare sulle proprietà del materiale, le trasformazioni GameObject e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="e230b-128">The current state from this class is generally used by Theme Engines at runtime to dictate what values to set against material properties, GameObject transforms, and more.</span></span>

### <a name="theme-engine-properties"></a><span data-ttu-id="e230b-129">Proprietà del motore del tema</span><span class="sxs-lookup"><span data-stu-id="e230b-129">Theme engine properties</span></span>

<span data-ttu-id="e230b-130">Al di fuori degli *Stati*, un [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) Asset definisce anche un elenco di motori di tema e le proprietà associate per questi motori.</span><span class="sxs-lookup"><span data-stu-id="e230b-130">Outside of *States*, a [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset also defines a list of Theme Engines and the associated properties for these engines.</span></span> <span data-ttu-id="e230b-131">Un [motore di tema](#theme-engines) definisce di nuovo la logica per impostare i valori corretti rispetto a un GameObject in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="e230b-131">A [Theme engine](#theme-engines) again defines the logic to set the correct values against a GameObject at runtime.</span></span>

<span data-ttu-id="e230b-132">Un [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset può definire più motori di tema per ottenere transizioni di stati visivi sofisticate destinate a più proprietà GameObject.</span><span class="sxs-lookup"><span data-stu-id="e230b-132">A [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset can define multiple Theme Engines to achieve sophisticated visual states transitions targeting multiple GameObject properties.</span></span>

<span data-ttu-id="e230b-133">**Runtime del tema**</span><span class="sxs-lookup"><span data-stu-id="e230b-133">**Theme Runtime**</span></span>

<span data-ttu-id="e230b-134">Definisce il tipo di classe del motore del tema che verrà creato</span><span class="sxs-lookup"><span data-stu-id="e230b-134">Defines the class type of the Theme engine that will be created</span></span>

<span data-ttu-id="e230b-135">**Interpolazione**</span><span class="sxs-lookup"><span data-stu-id="e230b-135">**Easing**</span></span>

<span data-ttu-id="e230b-136">Alcuni *motori di tema*, se definiscono la proprietà [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) su true, supportano l'interpolazione tra gli Stati.</span><span class="sxs-lookup"><span data-stu-id="e230b-136">Some *Theme Engines*, if they define their property [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) as true, support easing between states.</span></span> <span data-ttu-id="e230b-137">Ad esempio, lerping tra due colori quando si verifica una modifica dello stato.</span><span class="sxs-lookup"><span data-stu-id="e230b-137">For example, lerping between two colors when a state change occurs.</span></span> <span data-ttu-id="e230b-138">La *durata* definisce in secondi per quanto tempo è possibile semplificare dal valore iniziale al valore finale e la *curva di animazione* definisce la frequenza di modifica durante tale periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="e230b-138">The *Duration* defines in seconds how long to ease from start value to end value and the *Animation Curve* defines the rate of change during that time period.</span></span>

<span data-ttu-id="e230b-139">**Proprietà shader**</span><span class="sxs-lookup"><span data-stu-id="e230b-139">**Shader properties**</span></span>

<span data-ttu-id="e230b-140">Alcuni *motori di tema*, se definiscono la proprietà [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) su true, modificheranno determinate proprietà dello shader in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="e230b-140">Some *Theme Engines*, if they define their property [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) as true, will modify particular shader properties at runtime.</span></span> <span data-ttu-id="e230b-141">I campi *shader* e *Property* definiscono la proprietà shader di destinazione.</span><span class="sxs-lookup"><span data-stu-id="e230b-141">The *Shader* and *Property* fields define the shader property to target.</span></span>

### <a name="create-a-theme-configuration-via-code"></a><span data-ttu-id="e230b-142">Creare una configurazione del tema tramite codice</span><span class="sxs-lookup"><span data-stu-id="e230b-142">Create a theme configuration via code</span></span>

<span data-ttu-id="e230b-143">In generale, è più facile progettare le configurazioni del tema tramite il controllo Unity, ma in alcuni casi i temi devono essere generati dinamicamente in fase di esecuzione tramite codice.</span><span class="sxs-lookup"><span data-stu-id="e230b-143">In general, it is easier to design Theme configurations via the Unity inspector but there are cases where Themes must be dynamically generated at runtime via code.</span></span> <span data-ttu-id="e230b-144">Il frammento di codice riportato di seguito fornisce un esempio di come eseguire questa attività.</span><span class="sxs-lookup"><span data-stu-id="e230b-144">The code snippet below gives an example of how to accomplish this task.</span></span>

<span data-ttu-id="e230b-145">Per facilitare lo sviluppo, i seguenti metodi helper sono utili per semplificare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="e230b-145">To help expedite development, the following helper methods are useful for simplifying setup.</span></span>

<span data-ttu-id="e230b-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) -Crea un nuovo stato ScriptableObject con i quattro valori di stato predefiniti usati nel componente [interactable](ux-building-blocks/interactable.md) .</span><span class="sxs-lookup"><span data-stu-id="e230b-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) - creates a new States ScriptableObject with the four default state values used in the [Interactable](ux-building-blocks/interactable.md) component.</span></span>

<span data-ttu-id="e230b-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) -Ogni motore di tema definisce una configurazione predefinita con le proprietà corrette necessarie per il tipo di runtime del tema.</span><span class="sxs-lookup"><span data-stu-id="e230b-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) - Every Theme Engine defines a default configuration with the correct properties needed for that Theme runtime type.</span></span> <span data-ttu-id="e230b-148">Questo helper crea una definizione per il tipo di motore di tema specificato.</span><span class="sxs-lookup"><span data-stu-id="e230b-148">This helper creates a definition for the given Theme Engine type.</span></span>

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

## <a name="theme-engines"></a><span data-ttu-id="e230b-149">Motori del tema</span><span class="sxs-lookup"><span data-stu-id="e230b-149">Theme engines</span></span>

<span data-ttu-id="e230b-150">Un [motore di tema](#theme-engines) è una classe che si estende dalla [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) classe.</span><span class="sxs-lookup"><span data-stu-id="e230b-150">A [Theme Engine](#theme-engines) is a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="e230b-151">Queste classi vengono create in fase di esecuzione e configurate con un [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) oggetto come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="e230b-151">These classes are instantiated at runtime and configured with a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object as outlined earlier.</span></span>

### <a name="default-theme-engines"></a><span data-ttu-id="e230b-152">Motori di tema predefiniti</span><span class="sxs-lookup"><span data-stu-id="e230b-152">Default theme engines</span></span>

<span data-ttu-id="e230b-153">MRTK viene fornito con un set predefinito di motori di tema elencati di seguito:</span><span class="sxs-lookup"><span data-stu-id="e230b-153">MRTK ships with a default set of Theme Engines listed below:</span></span>

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

<span data-ttu-id="e230b-154">I motori di tema predefiniti sono disponibili in `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` .</span><span class="sxs-lookup"><span data-stu-id="e230b-154">The default Theme Engines can be found under `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines`.</span></span>

### <a name="custom-theme-engines"></a><span data-ttu-id="e230b-155">Motori di tema personalizzati</span><span class="sxs-lookup"><span data-stu-id="e230b-155">Custom theme engines</span></span>

<span data-ttu-id="e230b-156">Come indicato, un motore di tema viene definito come una classe che si estende dalla [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) classe.</span><span class="sxs-lookup"><span data-stu-id="e230b-156">As stated, a Theme Engine is defined as a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="e230b-157">Pertanto, il nuovo motore di tema deve estendere questa classe e implementare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="e230b-157">Thus, new Theme Engine need only extend this class and implement the following:</span></span>

#### <a name="mandatory-implementations"></a><span data-ttu-id="e230b-158">Implementazioni obbligatorie</span><span class="sxs-lookup"><span data-stu-id="e230b-158">Mandatory implementations</span></span>

<span data-ttu-id="e230b-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (xrif: Microsoft. MixedReality. Toolkit. UI. InteractableThemeBase. SetValue)</span><span class="sxs-lookup"><span data-stu-id="e230b-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.SetValue)</span></span>

<span data-ttu-id="e230b-160">Per la proprietà specificata, che può essere identificata da `ThemeStateProperty.Name` , impostare il valore dello stato corrente sull'host GameObject di destinazione, ad esempio</span><span class="sxs-lookup"><span data-stu-id="e230b-160">For the given property, which can be identified by `ThemeStateProperty.Name`, set its current state value on the targeted GameObject host (i.e</span></span> <span data-ttu-id="e230b-161">impostare il colore del materiale e così via).</span><span class="sxs-lookup"><span data-stu-id="e230b-161">set the material color, etc).</span></span> <span data-ttu-id="e230b-162">L' *Indice* indica il valore dello stato corrente a cui accedere e la *percentuale*, ovvero un valore float compreso tra 0 e 1, per l'interpolazione/lerping tra i valori.</span><span class="sxs-lookup"><span data-stu-id="e230b-162">The *index* indicates the current state value to access and the *percentage*, a float between 0 and 1, is used for easing/lerping between values.</span></span>

<span data-ttu-id="e230b-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xrif: Microsoft. MixedReality. Toolkit. UI. InteractableThemeBase. GetProperty)</span><span class="sxs-lookup"><span data-stu-id="e230b-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetProperty)</span></span>

<span data-ttu-id="e230b-164">Per la proprietà specificata, che può essere identificata da `ThemeStateProperty.Name` , restituire il valore corrente impostato sul GameObject host di destinazione (ad esempio</span><span class="sxs-lookup"><span data-stu-id="e230b-164">For the given property, which can be identified by `ThemeStateProperty.Name`, return the current value set on the targeted Host  GameObject (i.e</span></span> <span data-ttu-id="e230b-165">colore del materiale corrente, offset della posizione locale corrente e così via.</span><span class="sxs-lookup"><span data-stu-id="e230b-165">the current material color, the current local position offset, etc).</span></span> <span data-ttu-id="e230b-166">Questa operazione viene utilizzata principalmente per la memorizzazione nella cache del valore iniziale durante l'interpolazione tra gli Stati.</span><span class="sxs-lookup"><span data-stu-id="e230b-166">This is primarily used for caching the start value when easing between states.</span></span>

<span data-ttu-id="e230b-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xrif: Microsoft. MixedReality. Toolkit. UI. InteractableThemeBase. GetDefaultThemeDefinition)</span><span class="sxs-lookup"><span data-stu-id="e230b-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetDefaultThemeDefinition)</span></span>

<span data-ttu-id="e230b-168">Restituisce un [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) oggetto che definisce le proprietà predefinite e la configurazione necessaria per il tema personalizzato.</span><span class="sxs-lookup"><span data-stu-id="e230b-168">Returns a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object that defines the default properties and configuration needed for the custom theme</span></span>

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

<span data-ttu-id="e230b-169">Variante protetta della definizione Public `SetValue()` , ad eccezione del fatto che ThemePropertyValue è stato impostato anziché indirizzare per usare la configurazione di indice e/o percentuale.</span><span class="sxs-lookup"><span data-stu-id="e230b-169">Protected variant of the public `SetValue()` definition, except provided ThemePropertyValue to set instead of directing to use index and/or percentage configuration.</span></span>

#### <a name="recommended-overrides"></a><span data-ttu-id="e230b-170">Sostituzioni consigliate</span><span class="sxs-lookup"><span data-stu-id="e230b-170">Recommended overrides</span></span>

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

<span data-ttu-id="e230b-171">Eseguire tutti i passaggi di inizializzazione che fanno riferimento al parametro *GameObject* fornito e usando le proprietà e le configurazioni definite nel parametro *ThemeDefinition* .</span><span class="sxs-lookup"><span data-stu-id="e230b-171">Perform any initialization steps here targeting the provided *GameObject* parameter and using the properties and configurations defined in the *ThemeDefinition* parameter.</span></span> <span data-ttu-id="e230b-172">Si consiglia di chiamare `base.Init(host, settings)` all'inizio di una sostituzione.</span><span class="sxs-lookup"><span data-stu-id="e230b-172">It is recommended to call `base.Init(host, settings)` at the beginning of an override.</span></span>

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

<span data-ttu-id="e230b-173">Se il motore del tema personalizzato può supportare l'interpolazione tra i valori configurati tramite la [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) Proprietà.</span><span class="sxs-lookup"><span data-stu-id="e230b-173">If the custom Theme Engine can support easing between values which is configured via the [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) property.</span></span>

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

<span data-ttu-id="e230b-174">Se il motore del tema personalizzato può supportare la destinazione delle proprietà dello shader.</span><span class="sxs-lookup"><span data-stu-id="e230b-174">If the custom Theme Engine can support targeting shader properties.</span></span> <span data-ttu-id="e230b-175">È consigliabile estendere da [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) per trarre vantaggio dall'infrastruttura esistente per impostare/ottenere in modo efficiente le proprietà dello shader tramite [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span><span class="sxs-lookup"><span data-stu-id="e230b-175">It is recommended to extend from [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) to benefit from the existing infrastructure to efficiently set/get shader properties via [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span></span> <span data-ttu-id="e230b-176">Le informazioni sulle proprietà dello shader vengono archiviate in ogni [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) tramite [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) e [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) .</span><span class="sxs-lookup"><span data-stu-id="e230b-176">The shader property information is stored in each [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) via [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) and [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName).</span></span>

> [!NOTE]
> <span data-ttu-id="e230b-177">Se [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) si estende, può anche essere utile eseguire l'override di [InteractableShaderTheme. DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) tramite *New*.</span><span class="sxs-lookup"><span data-stu-id="e230b-177">If extending [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme), it can also be useful to override the [InteractableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) via *new*.</span></span>
>
> <span data-ttu-id="e230b-178">Codice di esempio: `protected new const string DefaultShaderProperty = "_Color";`</span><span class="sxs-lookup"><span data-stu-id="e230b-178">Example code: `protected new const string DefaultShaderProperty = "_Color";`</span></span>
>
> <span data-ttu-id="e230b-179">Inoltre, le classi seguenti estendono la [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) classe che usa di nuovo [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) per modificare i valori delle proprietà dello shader.</span><span class="sxs-lookup"><span data-stu-id="e230b-179">Furthermore, the following classes below extend the [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) class which again uses [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) to modify shader property values.</span></span> <span data-ttu-id="e230b-180">Questo approccio [aiuta a migliorare le prestazioni](https://docs.unity3d.com/Manual/DrawCallBatching.html) perché *MaterialPropertyBlocks* non crea nuovi materiali di istanza quando cambiano i valori.</span><span class="sxs-lookup"><span data-stu-id="e230b-180">This approach [helps performance](https://docs.unity3d.com/Manual/DrawCallBatching.html) because *MaterialPropertyBlocks* do not create new instanced materials when values change.</span></span> <span data-ttu-id="e230b-181">Tuttavia, l'accesso alle proprietà tipiche della classe [Material](https://docs.unity3d.com/ScriptReference/Material.html) non restituisce i valori previsti.</span><span class="sxs-lookup"><span data-stu-id="e230b-181">However, accessing the typical [Material](https://docs.unity3d.com/ScriptReference/Material.html) class properties will not return expected values.</span></span> <span data-ttu-id="e230b-182">Usare *MaterialPropertyBlocks* per ottenere e convalidare i valori delle proprietà materiali correnti (ad esempio</span><span class="sxs-lookup"><span data-stu-id="e230b-182">Use *MaterialPropertyBlocks* to get and validate current material property values (i.e</span></span> <span data-ttu-id="e230b-183">*_Color* o *_MainTex*).</span><span class="sxs-lookup"><span data-stu-id="e230b-183">*_Color* or *_MainTex*).</span></span>
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

<span data-ttu-id="e230b-184">Indica al tema di reimpostare le proprietà modificate sui valori originali impostati nell'host GameObject quando il motore del tema è stato inizializzato.</span><span class="sxs-lookup"><span data-stu-id="e230b-184">Directs the theme to reset any modified properties back to their original values that were set on the host GameObject when this theme engine was initialized.</span></span>  

### <a name="custom-theme-engine-example"></a><span data-ttu-id="e230b-185">Esempio di motore di tema personalizzato</span><span class="sxs-lookup"><span data-stu-id="e230b-185">Custom theme engine example</span></span>

<span data-ttu-id="e230b-186">La classe seguente è un esempio di un nuovo motore di tema personalizzato.</span><span class="sxs-lookup"><span data-stu-id="e230b-186">The class below is an example of a custom new Theme Engine.</span></span> <span data-ttu-id="e230b-187">Questa implementazione troverà un componente [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) sull'oggetto host inizializzato e ne controllerà la visibilità in base allo stato corrente.</span><span class="sxs-lookup"><span data-stu-id="e230b-187">This implementation will find a [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) component on the initialized host object and control its visibility based on the current state.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="e230b-188">Esempio end-to-end</span><span class="sxs-lookup"><span data-stu-id="e230b-188">End-to-end example</span></span>

<span data-ttu-id="e230b-189">Se si estende il motore dei temi personalizzato definito nella sezione precedente, l'esempio di codice seguente illustra come controllare questo tema in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="e230b-189">Extending off of the custom Theme Engine defined in the earlier section, the code example below demonstrates how to control this theme at runtime.</span></span> <span data-ttu-id="e230b-190">In particolare, come impostare lo stato corrente sul tema in modo che la visibilità MeshRenderer venga aggiornata in modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="e230b-190">In particular, how to set the current state on the theme so the MeshRenderer visibility is updated appropriately.</span></span>

> [!NOTE]
> <span data-ttu-id="e230b-191">`theme.OnUpdate(state,force)` in genere deve essere chiamato nel metodo Update () per supportare i motori di tema che usano l'interpolazione/lerping tra i valori.</span><span class="sxs-lookup"><span data-stu-id="e230b-191">`theme.OnUpdate(state,force)` should generally be called in the Update() method to support Theme Engines that utilize easing/lerping between values.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e230b-192">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="e230b-192">See also</span></span>

- [<span data-ttu-id="e230b-193">Con cui</span><span class="sxs-lookup"><span data-stu-id="e230b-193">Interactable</span></span>](ux-building-blocks/interactable.md)
