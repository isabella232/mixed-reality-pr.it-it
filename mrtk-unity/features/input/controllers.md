---
title: Controllers
description: Come usare i controller in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, controller,
ms.openlocfilehash: c92ad099d770cc52467918053af02e7bebab928d
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850337"
---
# <a name="controllers"></a><span data-ttu-id="b05f4-104">Controllers</span><span class="sxs-lookup"><span data-stu-id="b05f4-104">Controllers</span></span>

<span data-ttu-id="b05f4-105">I controller vengono creati ed distrutti automaticamente dai [**provider di input**](input-providers.md).</span><span class="sxs-lookup"><span data-stu-id="b05f4-105">Controllers are created and destroyed automatically by [**input providers**](input-providers.md).</span></span> <span data-ttu-id="b05f4-106">Ogni tipo di controller ha un numero di *input* fisici definiti da un tipo di asse *,* indicando il tipo di dati del valore di input (Digitale, Asse singolo, Asse doppio, Sei Dof, ...) e un tipo di *input* (Pressione pulsante, Trigger, Levetta thumb, Puntatore spaziale, ...) che descrive l'origine dell'input.</span><span class="sxs-lookup"><span data-stu-id="b05f4-106">Each controller type has a number of *physical inputs* defined by an *axis type*, telling us the data type of the input value (Digital, Single Axis, Dual Axis, Six Dof, ...), and an *input type* (Button Press, Trigger, Thumb Stick, Spatial Pointer, ...) describing the origin of the input.</span></span> <span data-ttu-id="b05f4-107">Gli input fisici vengono mappati alle azioni di *input* tramite nel profilo di mapping dell'input del **controller,** nel profilo del sistema di *input* nel componente Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="b05f4-107">Physical inputs are mapped to *input actions* via in the **Controller Input Mapping Profile**, under the *Input System Profile* in the Mixed Reality Toolkit component.</span></span>

<span data-ttu-id="b05f4-108">MRTK rileverà automaticamente i controller WMR e li visualizza quando viene installato il pacchetto [**Microsoft.MixedReality.Input.**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="b05f4-108">MRTK will automatically detect WMR controllers and display them when the [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) package is installed.</span></span> <span data-ttu-id="b05f4-109">I modelli controller verranno visualizzati nell'editor solo quando si usa la pipeline OpenXR.</span><span class="sxs-lookup"><span data-stu-id="b05f4-109">Controllers models will only show up in the editor when using the OpenXR pipeline.</span></span> <span data-ttu-id="b05f4-110">Per visualizzare i modelli di controller Oculus, seguire le istruzioni [per la distribuzione di Oculus Quest](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="b05f4-110">To visualize Oculus controller models, follow the [Oculus Quest deployment instructions](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)</span></span>

![Mapping dell'input del controller](../images/input/ControllerInputMapping.png)