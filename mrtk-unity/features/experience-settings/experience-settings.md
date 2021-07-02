---
title: Impostazioni dell'esperienza
description: Documentazione sulle diverse impostazioni dell'esperienza per MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: ab3a449b064d4a1c8f2bf76154f7a25c688693e1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177353"
---
# <a name="experience-settings"></a><span data-ttu-id="eb47e-104">Impostazioni dell'esperienza</span><span class="sxs-lookup"><span data-stu-id="eb47e-104">Experience settings</span></span>

<span data-ttu-id="eb47e-105">Una delle sfide della creazione dell'interfaccia utente per la realtà mista è l'allineamento tra esperienze diverse.</span><span class="sxs-lookup"><span data-stu-id="eb47e-105">One of the challenges of creating UI for Mixed Reality is aligning across different experiences.</span></span> <span data-ttu-id="eb47e-106">Con MRTK, è possibile impostare e per la scena. Il comportamento seguente verrà configurato in modo appropriato per `Target Experience Scale` `Content Offset` la scala di destinazione.</span><span class="sxs-lookup"><span data-stu-id="eb47e-106">With MRTK, you can set the `Target Experience Scale` and the `Content Offset` for your scene, will configue the following to behave appropriately for the target scale.</span></span>

- <span data-ttu-id="eb47e-107">Contenuto della scena di realtà mista</span><span class="sxs-lookup"><span data-stu-id="eb47e-107">Mixed Reality Scene Content</span></span>
- <span data-ttu-id="eb47e-108">Sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="eb47e-108">Boundary System</span></span>

  ![Esperienza Impostazioni nel profilo di configurazione di MRTK](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a><span data-ttu-id="eb47e-110">Scalabilità dell'esperienza di destinazione</span><span class="sxs-lookup"><span data-stu-id="eb47e-110">Target Experience Scale</span></span>

<span data-ttu-id="eb47e-111">La **scalabilità dell'esperienza** di destinazione specifica l'ambiente per cui è progettata l'esperienza.</span><span class="sxs-lookup"><span data-stu-id="eb47e-111">The **Target Experience Scale** specifies the environment for which the experience is designed.</span></span> <span data-ttu-id="eb47e-112">Può assumere i valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="eb47e-112">It can take on the following values.</span></span>

* <span data-ttu-id="eb47e-113">*OrientationOnly:* esperienza che usa solo l'orientamento del visore VR ed è allineata alla gravità.</span><span class="sxs-lookup"><span data-stu-id="eb47e-113">*OrientationOnly* - An experience which utilizes only the headset orientation and is gravity aligned.</span></span> <span data-ttu-id="eb47e-114">L'origine del sistema di coordinate si trova al livello della testa.</span><span class="sxs-lookup"><span data-stu-id="eb47e-114">The coordinate system origin is at head level.</span></span>
* <span data-ttu-id="eb47e-115">*Seated :* un'esperienza progettata per l'uso da posti a parte.</span><span class="sxs-lookup"><span data-stu-id="eb47e-115">*Seated* - An experience designed for seated use.</span></span> <span data-ttu-id="eb47e-116">L'origine del sistema di coordinate è a livello di piano.</span><span class="sxs-lookup"><span data-stu-id="eb47e-116">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="eb47e-117">*In piedi:* un'esperienza progettata per l'uso permanente.</span><span class="sxs-lookup"><span data-stu-id="eb47e-117">*Standing* - An experience designed for stationary standing use.</span></span> <span data-ttu-id="eb47e-118">L'origine del sistema di coordinate è a livello di piano.</span><span class="sxs-lookup"><span data-stu-id="eb47e-118">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="eb47e-119">*Room:* esperienza progettata per supportare lo spostamento in una stanza.</span><span class="sxs-lookup"><span data-stu-id="eb47e-119">*Room* - An experience designed to support movement throughout a room.</span></span> <span data-ttu-id="eb47e-120">L'origine del sistema di coordinate è a livello di piano.</span><span class="sxs-lookup"><span data-stu-id="eb47e-120">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="eb47e-121">*Mondo:* un'esperienza progettata per usare e spostarsi nel mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="eb47e-121">*World* - An experience designed to utilize and move through the physical world.</span></span> <span data-ttu-id="eb47e-122">L'origine del sistema di coordinate si trova al livello della testa.</span><span class="sxs-lookup"><span data-stu-id="eb47e-122">The coordinate system origin is at head level.</span></span>

## <a name="content-offset"></a><span data-ttu-id="eb47e-123">Offset del contenuto</span><span class="sxs-lookup"><span data-stu-id="eb47e-123">Content Offset</span></span>

<span data-ttu-id="eb47e-124">Questo parametro specifica l'altezza al [](scene-content.md) di sopra del piano per eseguire l'offset del contenuto della scena di realtà mista quando Tipo di **allineamento** è impostato su Allinea con **scala dell'esperienza**</span><span class="sxs-lookup"><span data-stu-id="eb47e-124">This parameter specifies the height above the floor to offset [Mixed Reality Scene Content](scene-content.md) when **Alignment Type** is set to **Align with Experience Scale**</span></span>
