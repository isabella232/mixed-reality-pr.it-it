---
title: Strumento di utilizzo delle funzionalità di input
description: Strumento InputFeatureUsage della documentazione in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 0f2d3d3eb07d8b631f3f11a8b497a22a028a2f24
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145012"
---
# <a name="inputfeatureusage-tool"></a><span data-ttu-id="416e6-104">Strumento InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="416e6-104">InputFeatureUsage tool</span></span>

<span data-ttu-id="416e6-105">Lo strumento InputFeatureUsage è uno strumento di runtime (nel dispositivo o nell'editor) che consente agli sviluppatori di determinare rapidamente l'input UnityFeatureUsages disponibile per un'origine di input rilevata (ad esempio controller di movimento o mano articolata).</span><span class="sxs-lookup"><span data-stu-id="416e6-105">The InputFeatureUsage tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the available Unity InputFeatureUsages for a detected input source (ex: motion controller or articulated hand).</span></span>

> [!NOTE]
> <span data-ttu-id="416e6-106">Questa scena funziona solo in Unity 2019.3 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="416e6-106">This scene only works on Unity 2019.3 or later.</span></span>

<span data-ttu-id="416e6-107">Questo strumento è molto utile quando si sviluppa il supporto per un nuovo controller hardware.</span><span class="sxs-lookup"><span data-stu-id="416e6-107">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="416e6-108">Può anche essere utile per confermare un sospetto problema di mapping dei controlli nella classe di supporto per un controller esistente.</span><span class="sxs-lookup"><span data-stu-id="416e6-108">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![Strumento InputFeatureUsage](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a><span data-ttu-id="416e6-110">Uso dello strumento InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="416e6-110">Using the InputFeatureUsage tool</span></span>

<span data-ttu-id="416e6-111">Per iniziare a usare lo strumento InputFeatureUsage, passare a **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** e aprire la **scena InputFeatureUsageTool.**</span><span class="sxs-lookup"><span data-stu-id="416e6-111">To get started with the InputFeatureUsage tool, navigate to **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** and open the **InputFeatureUsageTool** scene.</span></span> <span data-ttu-id="416e6-112">Dopo aver caricato la scena, il progetto può essere eseguito nell'editor, usando la modalità di riproduzione o compilato ed eseguito in un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="416e6-112">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="416e6-113">Per esaminare i mapping di Unity per un controller:</span><span class="sxs-lookup"><span data-stu-id="416e6-113">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="416e6-114">Connettere il controller</span><span class="sxs-lookup"><span data-stu-id="416e6-114">Connect the controller</span></span>
- <span data-ttu-id="416e6-115">Premere ogni pulsante e spostare ogni asse</span><span class="sxs-lookup"><span data-stu-id="416e6-115">Press each button and move each axis</span></span>
- <span data-ttu-id="416e6-116">Si notino gli utilizzi delle funzionalità nella visualizzazione</span><span class="sxs-lookup"><span data-stu-id="416e6-116">Note the feature usages in the display</span></span>
- <span data-ttu-id="416e6-117">Aggiornare i mapping dei controlli nel provider di dati del sistema di input per il controller</span><span class="sxs-lookup"><span data-stu-id="416e6-117">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="416e6-118">Lo strumento InputFeatureUsage non usa i componenti di Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="416e6-118">The InputFeatureUsage tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="416e6-119">Comunica direttamente con Unity per determinare e visualizzare gli utilizzi delle funzionalità.</span><span class="sxs-lookup"><span data-stu-id="416e6-119">It directly communicates with Unity to determine and display the feature usages.</span></span>

### <a name="panels"></a><span data-ttu-id="416e6-120">Pannelli</span><span class="sxs-lookup"><span data-stu-id="416e6-120">Panels</span></span>

<span data-ttu-id="416e6-121">I pannelli visualizzano lo stato corrente di tutte le inputFeatureUsages segnalate in tutte le origini di input unity rilevate.</span><span class="sxs-lookup"><span data-stu-id="416e6-121">The panels display the current state of all reported InputFeatureUsages on all detected Unity input sources.</span></span>

<span data-ttu-id="416e6-122">Il pannello più piccolo nella parte superiore elenca i nomi di tutte le origini rilevate.</span><span class="sxs-lookup"><span data-stu-id="416e6-122">The smaller panel along the top lists the names of all detected sources.</span></span>

## <a name="see-also"></a><span data-ttu-id="416e6-123">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="416e6-123">See also</span></span>

- [<span data-ttu-id="416e6-124">Creazione di un provider di dati del sistema di input</span><span class="sxs-lookup"><span data-stu-id="416e6-124">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="416e6-125">Strumento di mapping del controller</span><span class="sxs-lookup"><span data-stu-id="416e6-125">Controller mapping tool</span></span>](controller-mapping-tool.md)
