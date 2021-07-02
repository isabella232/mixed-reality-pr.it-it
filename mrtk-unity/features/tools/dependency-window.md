---
title: Finestra Dipendenze
description: Documentazione sull'utilizzo della finestra delle dipendenze in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 590476add6904f76081630c4416184bea9f694ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176665"
---
# <a name="dependency-window"></a><span data-ttu-id="87ed2-104">Finestra Dipendenze</span><span class="sxs-lookup"><span data-stu-id="87ed2-104">Dependency window</span></span>

<span data-ttu-id="87ed2-105">In Unity è spesso difficile capire quali asset vengono usati e cosa vi fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="87ed2-105">In Unity, it is often difficult to gleam which assets are being used, and what is referencing them.</span></span> <span data-ttu-id="87ed2-106">L'opzione "Trova riferimenti nella scena" è molto utile quando si è interessati solo alla scena corrente, ma per quanto riguarda l'intero progetto Unity?</span><span class="sxs-lookup"><span data-stu-id="87ed2-106">The "Find References in Scene" option works great when you are only concerned with the current scene, but what about your entire Unity project?</span></span> <span data-ttu-id="87ed2-107">È qui che la **finestra Delle dipendenze** (Assets/MRTK/Tools/DependencyWindow) può essere utile.</span><span class="sxs-lookup"><span data-stu-id="87ed2-107">This is where the **Dependency Window** (Assets/MRTK/Tools/DependencyWindow) can be useful.</span></span>

<span data-ttu-id="87ed2-108">Nella finestra Dipendenza viene visualizzato il modo in cui gli asset fanno riferimento e dipendono l'uno dall'altro.</span><span class="sxs-lookup"><span data-stu-id="87ed2-108">The Dependency Window displays how assets reference and depend on each other.</span></span> <span data-ttu-id="87ed2-109">Le dipendenze vengono calcolate analizzando i GUID all'interno dei file YAML del progetto (si noti che le dipendenze da script a script non vengono considerate).</span><span class="sxs-lookup"><span data-stu-id="87ed2-109">Dependencies are calculated by parsing guids within project YAML files (note, script to script dependencies are not considered).</span></span>

## <a name="usage"></a><span data-ttu-id="87ed2-110">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="87ed2-110">Usage</span></span>

<span data-ttu-id="87ed2-111">Per aprire la finestra, selezionare **Mixed Reality** Toolkit Utilities Dependency Window che aprirà la finestra e inizierà automaticamente a compilare il grafico delle  >    >    >   dipendenze del progetto.</span><span class="sxs-lookup"><span data-stu-id="87ed2-111">To open the window, select **Mixed Reality** > **Toolkit** > **Utilities** > **Dependency Window** which will open the window and automatically begin building your project's dependency graph.</span></span> <span data-ttu-id="87ed2-112">Dopo aver compilato il grafico delle dipendenze, è possibile selezionare gli asset nella scheda del progetto per esaminarne le dipendenze.</span><span class="sxs-lookup"><span data-stu-id="87ed2-112">Once the dependency graph is built, you can select assets in the project tab to inspect their dependencies.</span></span>

![Finestra Dipendenze](../images/dependency-window/MRTK_Dependency_Window.png)

<span data-ttu-id="87ed2-114">Nella finestra viene visualizzato un elenco di asset da cui dipende l'asset attualmente selezionato e un elenco gerarchico di asset che dipendono da esso.</span><span class="sxs-lookup"><span data-stu-id="87ed2-114">The window displays a list of assets that the currently selected asset depends on, and a hierarchical list of assets that depend on it.</span></span> <span data-ttu-id="87ed2-115">Se non dipende dall'asset attualmente selezionato, è possibile eliminarlo dal progetto (si noti che alcuni asset vengono caricati a livello di codice tramite API come Shader.Find() e potrebbero non essere intercettate dal rilevamento delle dipendenze).</span><span class="sxs-lookup"><span data-stu-id="87ed2-115">If nothing depends on the currently selected asset, you can consider deleting it from your project (note that some assets are loaded programmatically via APIs like Shader.Find() and may not be caught by the dependency tracker).</span></span>

<span data-ttu-id="87ed2-116">La finestra può anche visualizzare solo un elenco di tutti gli asset a cui non fanno riferimento altri asset e che possono essere considerati per l'eliminazione:</span><span class="sxs-lookup"><span data-stu-id="87ed2-116">The window can also display just a list of all assets which are not referenced by any other assets and could be considered for deletion:</span></span>

![Finestra delle dipendenze che mostra gli asset senza riferimenti](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> <span data-ttu-id="87ed2-118">Se gli asset vengono modificati, aggiunti o rimossi mentre la finestra delle dipendenze è in uso, è consigliabile aggiornare il grafico delle dipendenze per i risultati più "aggiornati".</span><span class="sxs-lookup"><span data-stu-id="87ed2-118">If assets are modified, added, or removed while the dependency window is in use, it is advised to refresh the dependency graph for the most "up to date" results.</span></span>
