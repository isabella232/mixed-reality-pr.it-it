---
title: README_TextPrefab
description: Panoramica di TextPrefab in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, TMP,
ms.openlocfilehash: f77f654e9be98aeb86bdc4c75e9aaeb464dc5b18
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694848"
---
# <a name="text-prefab"></a><span data-ttu-id="6cb0b-104">Prefabbricato di testo</span><span class="sxs-lookup"><span data-stu-id="6cb0b-104">Text prefab</span></span>

<span data-ttu-id="6cb0b-105">Questi prefabbricati sono ottimizzati per la qualità di rendering in realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-105">These prefabs are optimized for the rendering quality in Windows Mixed Reality.</span></span> <span data-ttu-id="6cb0b-106">Per ulteriori informazioni, leggere il testo della Guida [in Unity in](https://docs.microsoft.com/windows/mixed-reality/text-in-unity) Microsoft Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-106">For more information, please read the guideline [Text in Unity](https://docs.microsoft.com/windows/mixed-reality/text-in-unity) on Microsoft Windows Dev Center.</span></span>

## <a name="prefabs"></a><span data-ttu-id="6cb0b-107">Prefabbricati</span><span class="sxs-lookup"><span data-stu-id="6cb0b-107">Prefabs</span></span>

### <a name="3dtextprefab"></a><span data-ttu-id="6cb0b-108">3DTextPrefab</span><span class="sxs-lookup"><span data-stu-id="6cb0b-108">3DTextPrefab</span></span>

<span data-ttu-id="6cb0b-109">prefabbricato mesh di testo 3D (assets/MRTK/SDK/StandardAssets/prefabrics/Text) con fattore di scala ottimizzato a distanza di 2 metri.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-109">3D Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="6cb0b-110">(Leggere le istruzioni riportate di seguito)</span><span class="sxs-lookup"><span data-stu-id="6cb0b-110">(Please read the instructions below)</span></span>

### <a name="uitextprefab"></a><span data-ttu-id="6cb0b-111">UITextPrefab</span><span class="sxs-lookup"><span data-stu-id="6cb0b-111">UITextPrefab</span></span>

<span data-ttu-id="6cb0b-112">Prefabbricato mesh del testo dell'interfaccia utente (assets/MRTK/SDK/StandardAssets/prefabrics/Text) con fattore di scalabilità ottimizzato a distanza di 2 metri.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-112">UI Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="6cb0b-113">(Leggere le istruzioni riportate di seguito)</span><span class="sxs-lookup"><span data-stu-id="6cb0b-113">(Please read the instructions below)</span></span>

## <a name="fonts"></a><span data-ttu-id="6cb0b-114">Tipi di carattere</span><span class="sxs-lookup"><span data-stu-id="6cb0b-114">Fonts</span></span>

<span data-ttu-id="6cb0b-115">Tipi di carattere Open Source (assets/MRTK/Core/StandardAssets/fonts) inclusi nel Toolkit per realtà mista.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-115">Open-source fonts (Assets/MRTK/Core/StandardAssets/Fonts) included in Mixed Reality Toolkit.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6cb0b-116">Il prefabbricato di testo usa il tipo di carattere Open Source ' Selawik '.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-116">Text Prefab uses the open source font 'Selawik'.</span></span> <span data-ttu-id="6cb0b-117">Per usare il testo prefabbricato con un tipo di carattere diverso, importare il file del tipo di carattere e seguire le istruzioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-117">To use Text Prefab with a different font, please import the font file and follow the instructions below.</span></span> <span data-ttu-id="6cb0b-118">Nell'esempio seguente viene illustrato come utilizzare il tipo di carattere ' Segoe UI ' con il prefabbricato di testo.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-118">Below example shows how to use 'Segoe UI' font with Text Prefab.</span></span>

![Importazione del file del tipo di carattere Segoe UI](Images/TextPrefab/TextPrefabInstructions01.png)

1. <span data-ttu-id="6cb0b-120">Assegnare la trama del carattere al materiale 3DTextSegoeUI. mat.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-120">Assign font texture to 3DTextSegoeUI.mat material.</span></span>

    ![Assegnazione della trama del tipo di carattere](Images/TextPrefab/TextPrefabInstructions02.png)

1. <span data-ttu-id="6cb0b-122">In 3DTextSegoeUI. Mat Material selezionare lo shader Custom/3DTextShader. shader.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-122">On 3DTextSegoeUI.mat material, select the shader Custom/3DTextShader.shader.</span></span>

    ![Assegnazione dello shader](Images/TextPrefab/TextPrefabInstructions03.png)

1. <span data-ttu-id="6cb0b-124">Assegnare Segoe UI tipo di carattere e il materiale 3DTextSegoeUI ai componenti di testo nei prefabbricati.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-124">Assign Segoe UI font and 3DTextSegoeUI material to the text components in the prefabs.</span></span>

    ![Assegnazione del file e del materiale del tipo di carattere](Images/TextPrefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a><span data-ttu-id="6cb0b-126">Uso dei tipi di carattere in Unity</span><span class="sxs-lookup"><span data-stu-id="6cb0b-126">Working with Fonts in Unity</span></span>

<span data-ttu-id="6cb0b-127">Quando si aggiunge un nuovo TextMesh 3D a una scena in Unity, sono presenti due problemi visivi evidenti.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-127">When adding a new 3D TextMesh to a scene in Unity there are two issues that are visually apparent.</span></span> <span data-ttu-id="6cb0b-128">Uno, il tipo di carattere è molto grande e due, il tipo di carattere appare molto sfocato.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-128">One, the font appears very large and two, the font appears very blurry.</span></span> <span data-ttu-id="6cb0b-129">È anche interessante notare che il valore predefinito per le dimensioni del carattere è impostato su zero nel controllo.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-129">It is also interesting to notice that the default Font Size value is set to zero in the Inspector.</span></span> <span data-ttu-id="6cb0b-130">Se si sostituisce questo valore zero con 13, non verrà visualizzata alcuna differenza di dimensione, perché 13 è effettivamente il valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-130">Replacing this zero value with 13 will show no difference in size, because 13 is actually the default value.</span></span>

<span data-ttu-id="6cb0b-131">Unity presuppone che tutti i nuovi elementi aggiunti a una scena corrispondano a 1 unità Unity o alla scala di trasformazione 100%, che si traduce in circa 1 misuratore nella HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-131">Unity assumes all new elements added to a scene is 1 Unity Unit in size, or 100%  Transform scale, which translates to about 1 meter on the HoloLens.</span></span> <span data-ttu-id="6cb0b-132">Nel caso dei tipi di carattere, il rettangolo di delimitazione di un TextMesh 3D viene visualizzato per impostazione predefinita a circa 1 metro in altezza.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-132">In the case of fonts, the bounding box for a 3D TextMesh comes in, by default at about 1 meter in height.</span></span>

### <a name="font-scale-and-font-sizes"></a><span data-ttu-id="6cb0b-133">Scala dei tipi di carattere e dimensioni del carattere</span><span class="sxs-lookup"><span data-stu-id="6cb0b-133">Font Scale and Font Sizes</span></span>

<span data-ttu-id="6cb0b-134">La maggior parte delle finestre di progettazione visiva utilizza punti per definire le dimensioni dei tipi di carattere nel mondo reale, nonché i relativi programmi di progettazione.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-134">Most visual designers use Points to define font sizes in the real world, as well as their design programs.</span></span> <span data-ttu-id="6cb0b-135">Sono presenti circa 2835 (834.645666399962) punti in 1 contatore.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-135">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="6cb0b-136">In base alla conversione del sistema del punto in 1 misuratore e le dimensioni predefinite del tipo di carattere TextMesh di Unity di 13, la matematica semplice di 13 divisa per 2835 è uguale a 0,0046 (0.004586111116 Exact) fornisce una scala standard adeguata per iniziare con, anche se alcune potrebbero voler arrotondare a 0,005.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-136">Based on the point system conversion to 1 meter and Unity's default TextMesh Font Size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with, though some may wish to round to 0.005.</span></span>

<span data-ttu-id="6cb0b-137">In entrambi i casi, il ridimensionamento dell'oggetto o del contenitore di testo a questi valori non consentirà solo la conversione 1:1 delle dimensioni dei tipi di carattere da un programma di progettazione, ma fornisce anche uno standard per garantire la coerenza nell'intera applicazione o gioco.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-137">Either way, scaling the Text object or container to these values will not only allow for the 1:1 conversion of font sizes from a design program, but also provides a standard to maintain consistency throughout the application or game.</span></span>

### <a name="ui-text"></a><span data-ttu-id="6cb0b-138">Testo interfaccia utente </span><span class="sxs-lookup"><span data-stu-id="6cb0b-138">UI Text</span></span>

<span data-ttu-id="6cb0b-139">Quando si aggiunge un'interfaccia utente o un elemento di testo basato su Canvas a una scena, la disparità delle dimensioni è ancora maggiore.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-139">When adding a UI or canvas based Text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="6cb0b-140">Le differenze nelle due dimensioni sono pari a circa il 1000%, che porterebbe il fattore di scala per i componenti di testo basati sull'interfaccia utente a 0,00046 (0.0004586111116) o 0,0005 per il valore arrotondato.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-140">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based Text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="6cb0b-141">**Dichiarazione** di non responsabilità: il valore predefinito di qualsiasi tipo di carattere può essere applicato dalla dimensione della trama del tipo di carattere o dalla modalità di importazione del tipo di carattere in Unity.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-141">**Disclaimer**: The default value of any font may be effected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="6cb0b-142">Questi test sono stati eseguiti in base al tipo di carattere Arial predefinito in Unity, oltre a un altro tipo di carattere importato.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-142">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

![Dimensioni del carattere con fattori di scala](Images/TextPrefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[<span data-ttu-id="6cb0b-144">Text3DSelawik. Mat</span><span class="sxs-lookup"><span data-stu-id="6cb0b-144">Text3DSelawik.mat</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Core/StandardAssets/Materials)

<span data-ttu-id="6cb0b-145">Materiale per 3DTextPrefab con supporto occlusione.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-145">Material for 3DTextPrefab with occlusion support.</span></span> <span data-ttu-id="6cb0b-146">Richiede 3DTextShader. shader</span><span class="sxs-lookup"><span data-stu-id="6cb0b-146">Requires 3DTextShader.shader</span></span>

![Materiale carattere predefinito rispetto al materiale 3DTextSegoeUI](Images/TextPrefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[<span data-ttu-id="6cb0b-148">Text3DShader. shader</span><span class="sxs-lookup"><span data-stu-id="6cb0b-148">Text3DShader.shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Core/StandardAssets/Shaders)

<span data-ttu-id="6cb0b-149">Shader per 3DTextPrefab con supporto occlusione.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-149">Shader for 3DTextPrefab with occlusion support.</span></span>
