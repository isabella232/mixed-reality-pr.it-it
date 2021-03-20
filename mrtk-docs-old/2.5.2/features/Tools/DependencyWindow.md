---
title: DependencyWindow
description: Documentazione sull'utilizzo della finestra di dipendenza in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: c53989151123f61988160b74fa876b907264bdd4
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104691238"
---
# <a name="dependency-window"></a><span data-ttu-id="b94d9-104">Finestra dipendenze</span><span class="sxs-lookup"><span data-stu-id="b94d9-104">Dependency window</span></span>

<span data-ttu-id="b94d9-105">In Unity, spesso è difficile brillare quali asset vengono usati e quali sono i riferimenti.</span><span class="sxs-lookup"><span data-stu-id="b94d9-105">In Unity, it is often difficult to gleam which assets are being used, and what is referencing them.</span></span> <span data-ttu-id="b94d9-106">L'opzione "trova riferimenti in scena" è molto interessante quando si è interessati solo alla scena corrente, ma all'intero progetto Unity?</span><span class="sxs-lookup"><span data-stu-id="b94d9-106">The "Find References in Scene" option works great when you are only concerned with the current scene, but what about your entire Unity project?</span></span> <span data-ttu-id="b94d9-107">Questo è il punto in cui la **finestra di dipendenza** (assets/MRTK/Tools/DependencyWindow) può essere utile.</span><span class="sxs-lookup"><span data-stu-id="b94d9-107">This is where the **Dependency Window** (Assets/MRTK/Tools/DependencyWindow) can be useful.</span></span>

<span data-ttu-id="b94d9-108">Nella finestra dipendenza viene visualizzato il modo in cui gli asset fanno riferimento e dipendono tra loro.</span><span class="sxs-lookup"><span data-stu-id="b94d9-108">The Dependency Window displays how assets reference and depend on each other.</span></span> <span data-ttu-id="b94d9-109">Le dipendenze vengono calcolate analizzando i GUID all'interno dei file YAML del progetto. Nota: le dipendenze di script per script non vengono considerate.</span><span class="sxs-lookup"><span data-stu-id="b94d9-109">Dependencies are calculated by parsing guids within project YAML files (note, script to script dependencies are not considered).</span></span>

## <a name="usage"></a><span data-ttu-id="b94d9-110">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="b94d9-110">Usage</span></span>

<span data-ttu-id="b94d9-111">Per aprire la finestra, selezionare *mixed reality Toolkit->Utilities->finestra delle dipendenze* che apre la finestra e inizia automaticamente a compilare il grafico delle dipendenze del progetto.</span><span class="sxs-lookup"><span data-stu-id="b94d9-111">To open the window, select *Mixed Reality Toolkit->Utilities->Dependency Window* which will open the window and automatically begin building your project's dependency graph.</span></span> <span data-ttu-id="b94d9-112">Una volta compilato il grafico delle dipendenze, è possibile selezionare Asset nella scheda progetto per esaminarne le dipendenze.</span><span class="sxs-lookup"><span data-stu-id="b94d9-112">Once the dependency graph is built, you can select assets in the project tab to inspect their dependencies.</span></span>

![Finestra dipendenze](../images/dependency-window/MRTK_Dependency_Window.png)

<span data-ttu-id="b94d9-114">La finestra Visualizza un elenco di asset da cui dipende l'asset attualmente selezionato e un elenco gerarchico di asset che dipendono da esso.</span><span class="sxs-lookup"><span data-stu-id="b94d9-114">The window displays a list of assets that the currently selected asset depends on, and a hierarchical list of assets that depend on it.</span></span> <span data-ttu-id="b94d9-115">Se non dipende dall'asset attualmente selezionato, è possibile eliminarlo dal progetto (si noti che alcune risorse vengono caricate a livello di codice tramite API come shader. Find () e che potrebbero non essere rilevate dallo strumento di rilevamento delle dipendenze.</span><span class="sxs-lookup"><span data-stu-id="b94d9-115">If nothing depends on the currently selected asset, you can consider deleting it from your project (note that some assets are loaded programmatically via APIs like Shader.Find() and may not be caught by the dependency tracker).</span></span>

<span data-ttu-id="b94d9-116">La finestra può anche visualizzare solo un elenco di tutti gli asset a cui non viene fatto riferimento da altri asset e che potrebbero essere presi in considerazione per l'eliminazione:</span><span class="sxs-lookup"><span data-stu-id="b94d9-116">The window can also display just a list of all assets which are not referenced by any other assets and could be considered for deletion:</span></span>

![Finestra di dipendenza che Mostra risorse senza riferimenti](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> <span data-ttu-id="b94d9-118">Se le risorse vengono modificate, aggiunte o rimosse mentre è in uso la finestra di dipendenza, è consigliabile aggiornare il grafico delle dipendenze per i risultati più aggiornati.</span><span class="sxs-lookup"><span data-stu-id="b94d9-118">If assets are modified, added, or removed while the dependency window is in use, it is advised to refresh the dependency graph for the most "up to date" results.</span></span>
