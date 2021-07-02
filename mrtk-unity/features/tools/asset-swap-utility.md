---
title: Utilità di scambio di asset
description: Documentazione sull'uso dell'utilità di scambio di asset in MRTK per Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
ms.openlocfilehash: 50ef252913575988b5f377dd9ff92f9e9ade3a72
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176161"
---
# <a name="asset-swap-utility"></a><span data-ttu-id="37da0-104">Utilità di scambio di asset</span><span class="sxs-lookup"><span data-stu-id="37da0-104">Asset swap utility</span></span>

<span data-ttu-id="37da0-105">Trovare e sostituire è onnipresente quando si lavora negli strumenti di creazione di testo e contenuto.</span><span class="sxs-lookup"><span data-stu-id="37da0-105">Find and replace is ubiquitous when working in text and content creation tools.</span></span> <span data-ttu-id="37da0-106">Quando è necessario scambiare molti asset all'interno di una scena unity, è qui che l'oggetto [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) e l'editor [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) possono dare una mano.</span><span class="sxs-lookup"><span data-stu-id="37da0-106">When you need to swap many assets within a Unity scene this is where the [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) and editor can lend a hand.</span></span> <span data-ttu-id="37da0-107">L'utilità è inclusa nel `Microsoft.MixedReality.Toolkit.Unity.Tools` pacchetto.</span><span class="sxs-lookup"><span data-stu-id="37da0-107">The utility is included with the `Microsoft.MixedReality.Toolkit.Unity.Tools` package.</span></span>

<span data-ttu-id="37da0-108">Salva tutte le azioni di ricerca e sostituzione come ScriptableObject in modo che sia trivalo scambiare avanti e indietro o salvare i "temi" di scambio per un `AssetSwapUtility` uso futuro.</span><span class="sxs-lookup"><span data-stu-id="37da0-108">The `AssetSwapUtility` saves all find and replace actions as a ScriptableObject so that it is trival to swap back and forth or save swap "themes" for future use.</span></span>

## <a name="swapping-assets"></a><span data-ttu-id="37da0-109">Scambio di asset</span><span class="sxs-lookup"><span data-stu-id="37da0-109">Swapping assets</span></span>

<span data-ttu-id="37da0-110">Lo scambio di asset è semplice dopo aver creato un `AssetSwapCollection` oggetto .</span><span class="sxs-lookup"><span data-stu-id="37da0-110">Swapping assets is easy once you have created a `AssetSwapCollection`.</span></span> <span data-ttu-id="37da0-111">Di seguito viene illustrato l'uso scambiando due cubi rossi con due sfera blu in una scena.</span><span class="sxs-lookup"><span data-stu-id="37da0-111">Let's demonstrate use by swapping two red cubes with two blue spheres in a scene.</span></span> <span data-ttu-id="37da0-112">Aggiungere prima di tutto due cubi rossi alla scena che usano il cubo Unity predefinito e il `MRTK_Standard_Red` materiale.</span><span class="sxs-lookup"><span data-stu-id="37da0-112">First add two red cubes to your scene that use the default Unity cube and the `MRTK_Standard_Red` material.</span></span>

<span data-ttu-id="37da0-113">Per creare un `AssetSwapCollection` , passare a Mixed Reality Toolkit > Utilities > Asset Swap **Collection**.</span><span class="sxs-lookup"><span data-stu-id="37da0-113">To create an `AssetSwapCollection`, navigate to **Mixed Reality Toolkit > Utilities > Create Asset Swap Collection**.</span></span> <span data-ttu-id="37da0-114">Con `AssetSwapCollection` l'opzione selezionata, compilare le proprietà come illustrato nell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="37da0-114">With the `AssetSwapCollection` selected fill out the properties as seen in the below image:</span></span>

![Raccolta di scambio di asset nell'editor di Unity](images/asset-swap-img-01.png)

<span data-ttu-id="37da0-116">Selezionare quindi "Blue Spheres" nell'elenco a discesa "Tema selezionato" e premere "Applica".</span><span class="sxs-lookup"><span data-stu-id="37da0-116">Next select "Blue Spheres" from the "Selected Theme" dropdown and hit "Apply."</span></span> <span data-ttu-id="37da0-117">Tutti i cubi rossi all'interno della scena devono essere sostituiti con le sfera blu.</span><span class="sxs-lookup"><span data-stu-id="37da0-117">All red cubes within your scene should be replaced with blue spheres.</span></span>

![Raccolta di scambio di asset nell'editor di Unity con il tema selezionato evidenziato](images/asset-swap-img-02.png)

<span data-ttu-id="37da0-119">In questo esempio è stata eseguita una sostituzione completa della scena, ma è possibile sostituire parti della scena modificando la "modalità di selezione".</span><span class="sxs-lookup"><span data-stu-id="37da0-119">In this example we performed a full scene replacement but you may replace portions of your scene by changing the "Selection Mode."</span></span> <span data-ttu-id="37da0-120">È anche possibile tornare ai cubi rossi selezionando "Cubi rossi" nell'elenco a discesa "Tema selezionato" e premendo di nuovo "Applica".</span><span class="sxs-lookup"><span data-stu-id="37da0-120">You may also swap back to red cubes by selecting "Red Cubes" from the "Selected Theme" dropdown and hitting "Apply" again.</span></span>

> [!NOTE]
> <span data-ttu-id="37da0-121">È possibile scambiare qualsiasi tipo di asset, ad esempio file audio, tipi di carattere, prefab e così via. Eseguirà alcuni controlli di integrità per assicurarsi di passare `AssetSwapUtility` a tipi simili.</span><span class="sxs-lookup"><span data-stu-id="37da0-121">It's possible to swap any asset type such as audio files, fonts, prefabs, etc. The `AssetSwapUtility` will perform a few sanity checks to ensure you are swapping to similar types.</span></span>
