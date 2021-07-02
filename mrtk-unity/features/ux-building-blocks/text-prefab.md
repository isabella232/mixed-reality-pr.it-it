---
title: Prefab di testo
description: Panoramica di TextPrefab in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, TMP,
ms.openlocfilehash: 1839109043cfad9a20697c5d6526b349fd7ea2e4
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175646"
---
# <a name="text-prefab"></a><span data-ttu-id="b0f48-104">Prefab di testo</span><span class="sxs-lookup"><span data-stu-id="b0f48-104">Text prefab</span></span>

<span data-ttu-id="b0f48-105">Questi prefab sono ottimizzati per la qualità di rendering in Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b0f48-105">These prefabs are optimized for the rendering quality in Windows Mixed Reality.</span></span> <span data-ttu-id="b0f48-106">Per altre informazioni, leggere le linee guida Text in Unity on Microsoft Windows Dev Center [(Testo in Unity](/windows/mixed-reality/text-in-unity) in Microsoft Windows Dev Center).</span><span class="sxs-lookup"><span data-stu-id="b0f48-106">For more information, please read the guideline [Text in Unity](/windows/mixed-reality/text-in-unity) on Microsoft Windows Dev Center.</span></span>

## <a name="prefabs"></a><span data-ttu-id="b0f48-107">Prefab</span><span class="sxs-lookup"><span data-stu-id="b0f48-107">Prefabs</span></span>

### <a name="3dtextprefab"></a><span data-ttu-id="b0f48-108">3DTextPrefab</span><span class="sxs-lookup"><span data-stu-id="b0f48-108">3DTextPrefab</span></span>

<span data-ttu-id="b0f48-109">Prefab 3D Text Mesh (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) con fattore di scala ottimizzato a 2 metri di distanza.</span><span class="sxs-lookup"><span data-stu-id="b0f48-109">3D Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="b0f48-110">(Leggere le istruzioni seguenti)</span><span class="sxs-lookup"><span data-stu-id="b0f48-110">(Please read the instructions below)</span></span>

### <a name="uitextprefab"></a><span data-ttu-id="b0f48-111">UITextPrefab</span><span class="sxs-lookup"><span data-stu-id="b0f48-111">UITextPrefab</span></span>

<span data-ttu-id="b0f48-112">Prefab ui Text Mesh (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) con fattore di scala ottimizzato a 2 metri di distanza.</span><span class="sxs-lookup"><span data-stu-id="b0f48-112">UI Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="b0f48-113">(Leggere le istruzioni seguenti)</span><span class="sxs-lookup"><span data-stu-id="b0f48-113">(Please read the instructions below)</span></span>

## <a name="fonts"></a><span data-ttu-id="b0f48-114">Tipi di carattere</span><span class="sxs-lookup"><span data-stu-id="b0f48-114">Fonts</span></span>

<span data-ttu-id="b0f48-115">Tipi di carattere open source (Assets/MRTK/Core/StandardAssets/Fonts) inclusi in Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="b0f48-115">Open-source fonts (Assets/MRTK/Core/StandardAssets/Fonts) included in Mixed Reality Toolkit.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b0f48-116">Text Prefab usa il open source carattere "Selawik".</span><span class="sxs-lookup"><span data-stu-id="b0f48-116">Text Prefab uses the open source font 'Selawik'.</span></span> <span data-ttu-id="b0f48-117">Per usare Il prefab di testo con un tipo di carattere diverso, importare il file del tipo di carattere e seguire le istruzioni riportate di seguito.</span><span class="sxs-lookup"><span data-stu-id="b0f48-117">To use Text Prefab with a different font, please import the font file and follow the instructions below.</span></span> <span data-ttu-id="b0f48-118">L'esempio seguente illustra come usare il tipo di Segoe UI con il prefab di testo.</span><span class="sxs-lookup"><span data-stu-id="b0f48-118">Below example shows how to use 'Segoe UI' font with Text Prefab.</span></span>

![Importazione di Segoe UI file dei tipi di carattere](../images/text-prefab/TextPrefabInstructions01.png)

1. <span data-ttu-id="b0f48-120">Assegnare la trama del carattere al materiale 3DTextSegoeUI.mat.</span><span class="sxs-lookup"><span data-stu-id="b0f48-120">Assign font texture to 3DTextSegoeUI.mat material.</span></span>

    ![Assegnazione della trama del tipo di carattere](../images/text-prefab/TextPrefabInstructions02.png)

1. <span data-ttu-id="b0f48-122">Nel materiale 3DTextSegoeUI.mat selezionare lo shader Custom/3DTextShader.shader.</span><span class="sxs-lookup"><span data-stu-id="b0f48-122">On 3DTextSegoeUI.mat material, select the shader Custom/3DTextShader.shader.</span></span>

    ![Assegnazione di shader](../images/text-prefab/TextPrefabInstructions03.png)

1. <span data-ttu-id="b0f48-124">Assegnare Segoe UI tipo di carattere e materiale 3DTextSegoeUI ai componenti di testo nei prefab.</span><span class="sxs-lookup"><span data-stu-id="b0f48-124">Assign Segoe UI font and 3DTextSegoeUI material to the text components in the prefabs.</span></span>

    ![Assegnazione di file e materiali dei tipi di carattere](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a><span data-ttu-id="b0f48-126">Uso dei tipi di carattere in Unity</span><span class="sxs-lookup"><span data-stu-id="b0f48-126">Working with Fonts in Unity</span></span>

<span data-ttu-id="b0f48-127">Quando si aggiunge un nuovo textmesh 3D a una scena in Unity, esistono due problemi visivamente evidenti.</span><span class="sxs-lookup"><span data-stu-id="b0f48-127">When adding a new 3D TextMesh to a scene in Unity there are two issues that are visually apparent.</span></span> <span data-ttu-id="b0f48-128">Uno, il tipo di carattere appare molto grande e due, il tipo di carattere appare molto sfocato.</span><span class="sxs-lookup"><span data-stu-id="b0f48-128">One, the font appears very large and two, the font appears very blurry.</span></span> <span data-ttu-id="b0f48-129">È anche interessante notare che il valore predefinito Dimensioni carattere è impostato su zero in Inspector.</span><span class="sxs-lookup"><span data-stu-id="b0f48-129">It is also interesting to notice that the default Font Size value is set to zero in the Inspector.</span></span> <span data-ttu-id="b0f48-130">La sostituzione di questo valore zero con 13 non mostrerà alcuna differenza nelle dimensioni, perché 13 è effettivamente il valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="b0f48-130">Replacing this zero value with 13 will show no difference in size, because 13 is actually the default value.</span></span>

<span data-ttu-id="b0f48-131">Unity presuppone che tutti i nuovi elementi aggiunti a una scena siano di dimensioni di 1 unità Unity o una scala di trasformazione al 100%, che si traduce in circa 1 metro nella HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b0f48-131">Unity assumes all new elements added to a scene is 1 Unity Unit in size, or 100%  Transform scale, which translates to about 1 meter on the HoloLens.</span></span> <span data-ttu-id="b0f48-132">Nel caso dei tipi di carattere, viene visualizzato il rettangolo di selezione per un textmesh 3D, per impostazione predefinita a circa 1 metro di altezza.</span><span class="sxs-lookup"><span data-stu-id="b0f48-132">In the case of fonts, the bounding box for a 3D TextMesh comes in, by default at about 1 meter in height.</span></span>

### <a name="font-scale-and-font-sizes"></a><span data-ttu-id="b0f48-133">Scala dei caratteri e dimensioni dei caratteri</span><span class="sxs-lookup"><span data-stu-id="b0f48-133">Font Scale and Font Sizes</span></span>

<span data-ttu-id="b0f48-134">La maggior parte delle finestre di progettazione visiva usa Points per definire le dimensioni dei caratteri nel mondo reale, nonché i relativi programmi di progettazione.</span><span class="sxs-lookup"><span data-stu-id="b0f48-134">Most visual designers use Points to define font sizes in the real world, as well as their design programs.</span></span> <span data-ttu-id="b0f48-135">Sono presenti circa 2835 punti (2.834.645666399962) in 1 contatore.</span><span class="sxs-lookup"><span data-stu-id="b0f48-135">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="b0f48-136">In base alla conversione del sistema di punti in 1 contatore e alle dimensioni del carattere TextMesh predefinite di Unity pari a 13, la semplice matematica di 13 divisa per 2835 equivale a 0,0046 (0,004586111116 per l'esattezza) offre una scala standard adatta per iniziare, anche se alcuni potrebbero voler arrotondare a 0,005.</span><span class="sxs-lookup"><span data-stu-id="b0f48-136">Based on the point system conversion to 1 meter and Unity's default TextMesh Font Size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with, though some may wish to round to 0.005.</span></span>

<span data-ttu-id="b0f48-137">In entrambi i casi, il ridimensionamento dell'oggetto o del contenitore Text a questi valori non solo consentirà la conversione 1:1 delle dimensioni dei caratteri da un programma di progettazione, ma fornisce anche uno standard per mantenere la coerenza in tutta l'applicazione o nel gioco.</span><span class="sxs-lookup"><span data-stu-id="b0f48-137">Either way, scaling the Text object or container to these values will not only allow for the 1:1 conversion of font sizes from a design program, but also provides a standard to maintain consistency throughout the application or game.</span></span>

### <a name="ui-text"></a><span data-ttu-id="b0f48-138">Testo interfaccia utente </span><span class="sxs-lookup"><span data-stu-id="b0f48-138">UI Text</span></span>

<span data-ttu-id="b0f48-139">Quando si aggiunge un elemento Text basato su interfaccia utente o area di disegno a una scena, la disparità di dimensioni è ancora maggiore.</span><span class="sxs-lookup"><span data-stu-id="b0f48-139">When adding a UI or canvas based Text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="b0f48-140">Le differenze nelle due dimensioni sono pari a circa il 1000%, che porterebbe il fattore di scala per i componenti di testo basati sull'interfaccia utente a 0,00046 (0,000458611116 per l'esatto) o 0,0005 per il valore arrotondato.</span><span class="sxs-lookup"><span data-stu-id="b0f48-140">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based Text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="b0f48-141">**Dichiarazione di non responsabilità:** il valore predefinito di qualsiasi tipo di carattere può essere effetto delle dimensioni della trama del tipo di carattere o della modalità di importazione del tipo di carattere in Unity.</span><span class="sxs-lookup"><span data-stu-id="b0f48-141">**Disclaimer**: The default value of any font may be effected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="b0f48-142">Questi test sono stati eseguiti in base al tipo di carattere Arial predefinito in Unity e a un altro tipo di carattere importato.</span><span class="sxs-lookup"><span data-stu-id="b0f48-142">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

![Dimensioni del carattere con fattori di ridimensionamento](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[<span data-ttu-id="b0f48-144">Text3DSelawik.mat</span><span class="sxs-lookup"><span data-stu-id="b0f48-144">Text3DSelawik.mat</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

<span data-ttu-id="b0f48-145">Materiale per 3DTextPrefab con supporto dell'occlusione.</span><span class="sxs-lookup"><span data-stu-id="b0f48-145">Material for 3DTextPrefab with occlusion support.</span></span> <span data-ttu-id="b0f48-146">Richiede 3DTextShader.shader</span><span class="sxs-lookup"><span data-stu-id="b0f48-146">Requires 3DTextShader.shader</span></span>

![Materiale del tipo di carattere predefinito e materiale 3DTextSegoeUI](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[<span data-ttu-id="b0f48-148">Text3DShader.shader</span><span class="sxs-lookup"><span data-stu-id="b0f48-148">Text3DShader.shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

<span data-ttu-id="b0f48-149">Shader per 3DTextPrefab con supporto dell'occlusione.</span><span class="sxs-lookup"><span data-stu-id="b0f48-149">Shader for 3DTextPrefab with occlusion support.</span></span>
