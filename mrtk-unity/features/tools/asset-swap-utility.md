---
title: Utilità di scambio asset
description: Documentazione sull'uso di asset swap Utility in MRTK per Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
ms.openlocfilehash: f052cb5e758ca1a9376c4344657478c2fd9ff2b3
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104696048"
---
# <a name="asset-swap-utility"></a><span data-ttu-id="336ed-104">Utilità di scambio asset</span><span class="sxs-lookup"><span data-stu-id="336ed-104">Asset swap utility</span></span>

<span data-ttu-id="336ed-105">Trova e Sostituisci è onnipresente quando si lavora con gli strumenti di creazione di testo e di contenuto.</span><span class="sxs-lookup"><span data-stu-id="336ed-105">Find and replace is ubiquitous when working in text and content creation tools.</span></span> <span data-ttu-id="336ed-106">Quando è necessario scambiare molti asset in una scena Unity, questo è il punto in cui il [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) di [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) e l'editor possono dare una mano.</span><span class="sxs-lookup"><span data-stu-id="336ed-106">When you need to swap many assets within a Unity scene this is where the [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) and editor can lend a hand.</span></span> <span data-ttu-id="336ed-107">L'utilità è inclusa nel `Microsoft.MixedReality.Toolkit.Unity.Tools` pacchetto.</span><span class="sxs-lookup"><span data-stu-id="336ed-107">The utility is included with the `Microsoft.MixedReality.Toolkit.Unity.Tools` package.</span></span>

<span data-ttu-id="336ed-108">`AssetSwapUtility`Salva tutte le azioni di ricerca e sostituzione come ScriptableObject, in modo che sia trival eseguire lo swap avanti e indietro o salvare i "temi" per un uso futuro.</span><span class="sxs-lookup"><span data-stu-id="336ed-108">The `AssetSwapUtility` saves all find and replace actions as a ScriptableObject so that it is trival to swap back and forth or save swap "themes" for future use.</span></span>

## <a name="swapping-assets"></a><span data-ttu-id="336ed-109">Scambio di asset</span><span class="sxs-lookup"><span data-stu-id="336ed-109">Swapping assets</span></span>

<span data-ttu-id="336ed-110">Lo scambio di risorse è facile dopo aver creato un `AssetSwapCollection` .</span><span class="sxs-lookup"><span data-stu-id="336ed-110">Swapping assets is easy once you have created a `AssetSwapCollection`.</span></span> <span data-ttu-id="336ed-111">Per illustrare l'uso, è necessario scambiare due cubi rossi con due sfere blu in una scena.</span><span class="sxs-lookup"><span data-stu-id="336ed-111">Let's demonstrate use by swapping two red cubes with two blue spheres in a scene.</span></span> <span data-ttu-id="336ed-112">Aggiungere prima due cubi rossi alla scena che usano il cubo Unity predefinito e il `MRTK_Standard_Red` materiale.</span><span class="sxs-lookup"><span data-stu-id="336ed-112">First add two red cubes to your scene that use the default Unity cube and the `MRTK_Standard_Red` material.</span></span>

<span data-ttu-id="336ed-113">Per creare un `AssetSwapCollection` , passare a **mixed reality Toolkit > Utilities > create asset swap Collection**.</span><span class="sxs-lookup"><span data-stu-id="336ed-113">To create an `AssetSwapCollection`, navigate to **Mixed Reality Toolkit > Utilities > Create Asset Swap Collection**.</span></span> <span data-ttu-id="336ed-114">Con l' `AssetSwapCollection` opzione selezionato compila le proprietà come illustrato nell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="336ed-114">With the `AssetSwapCollection` selected fill out the properties as seen in the below image:</span></span>

![Raccolta asset swap nell'editor di Unity](images/asset-swap-img-01.png)

<span data-ttu-id="336ed-116">Selezionare quindi "sfere blu" dall'elenco a discesa "tema selezionato" e fare clic su "applica".</span><span class="sxs-lookup"><span data-stu-id="336ed-116">Next select "Blue Spheres" from the "Selected Theme" dropdown and hit "Apply."</span></span> <span data-ttu-id="336ed-117">Tutti i cubi rossi nella scena devono essere sostituiti con sfere blu.</span><span class="sxs-lookup"><span data-stu-id="336ed-117">All red cubes within your scene should be replaced with blue spheres.</span></span>

![Raccolta asset swap nell'editor di Unity con tema selezionato evidenziato](images/asset-swap-img-02.png)

<span data-ttu-id="336ed-119">In questo esempio è stata eseguita una sostituzione completa della scena, ma è possibile sostituire parti della scena modificando la "modalità di selezione".</span><span class="sxs-lookup"><span data-stu-id="336ed-119">In this example we performed a full scene replacement but you may replace portions of your scene by changing the "Selection Mode."</span></span> <span data-ttu-id="336ed-120">È anche possibile eseguire lo swapping ai cubi rossi selezionando "cubi rossi" dall'elenco a discesa "tema selezionato" e ripetendo "Apply".</span><span class="sxs-lookup"><span data-stu-id="336ed-120">You may also swap back to red cubes by selecting "Red Cubes" from the "Selected Theme" dropdown and hitting "Apply" again.</span></span>

> [!NOTE]
> <span data-ttu-id="336ed-121">È possibile scambiare qualsiasi tipo di asset, ad esempio file audio, tipi di carattere, prefabbricati e così via. Il eseguirà `AssetSwapUtility` alcuni controlli di integrità per assicurarsi di eseguire lo scambio a tipi simili.</span><span class="sxs-lookup"><span data-stu-id="336ed-121">It's possible to swap any asset type such as audio files, fonts, prefabs, etc. The `AssetSwapUtility` will perform a few sanity checks to ensure you are swapping to similar types.</span></span>