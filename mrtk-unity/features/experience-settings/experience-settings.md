---
title: ExperienceSettings
description: Documentazione sulle diverse impostazioni dell'esperienza per MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 1c93e2ee703eb5dad43bb51236b9991d17e1d58d
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647835"
---
# <a name="experience-settings"></a><span data-ttu-id="dad86-104">Impostazioni dell'esperienza</span><span class="sxs-lookup"><span data-stu-id="dad86-104">Experience Settings</span></span>

<span data-ttu-id="dad86-105">Una delle sfide della creazione dell'interfaccia utente per la realtà mista è l'allineamento tra esperienze diverse.</span><span class="sxs-lookup"><span data-stu-id="dad86-105">One of the challenges of creating UI for Mixed Reality is aligning across different experiences.</span></span> <span data-ttu-id="dad86-106">Con MRTK è possibile impostare e per la scena in modo che il comportamento seguente si comporti in modo appropriato `Target Experience Scale` per la scala di `Content Offset` destinazione.</span><span class="sxs-lookup"><span data-stu-id="dad86-106">With MRTK, you can set the `Target Experience Scale` and the `Content Offset` for your scene, will configue the following to behave appropriately for the target scale.</span></span>

- <span data-ttu-id="dad86-107">Contenuto della scena di realtà mista</span><span class="sxs-lookup"><span data-stu-id="dad86-107">Mixed Reality Scene Content</span></span>
- <span data-ttu-id="dad86-108">Sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="dad86-108">Boundary System</span></span>

  ![Impostazioni dell'esperienza nel profilo di configurazione MRTK](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a><span data-ttu-id="dad86-110">Scalabilità dell'esperienza di destinazione</span><span class="sxs-lookup"><span data-stu-id="dad86-110">Target Experience Scale</span></span>

<span data-ttu-id="dad86-111">La **scalabilità dell'esperienza di** destinazione specifica l'ambiente per cui è progettata l'esperienza.</span><span class="sxs-lookup"><span data-stu-id="dad86-111">The **Target Experience Scale** specifies the environment for which the experience is designed.</span></span> <span data-ttu-id="dad86-112">Può assumere i valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="dad86-112">It can take on the following values.</span></span>

* <span data-ttu-id="dad86-113">*OrientationOnly:* esperienza che usa solo l'orientamento del visore ed è allineata alla gravità.</span><span class="sxs-lookup"><span data-stu-id="dad86-113">*OrientationOnly* - An experience which utilizes only the headset orientation and is gravity aligned.</span></span> <span data-ttu-id="dad86-114">L'origine del sistema di coordinate è a livello di testa.</span><span class="sxs-lookup"><span data-stu-id="dad86-114">The coordinate system origin is at head level.</span></span>
* <span data-ttu-id="dad86-115">*Seduti:* un'esperienza progettata per l'uso da seduti.</span><span class="sxs-lookup"><span data-stu-id="dad86-115">*Seated* - An experience designed for seated use.</span></span> <span data-ttu-id="dad86-116">L'origine del sistema di coordinate è a livello di piano.</span><span class="sxs-lookup"><span data-stu-id="dad86-116">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="dad86-117">*In piedi:* un'esperienza progettata per l'uso in posizione stazionaria.</span><span class="sxs-lookup"><span data-stu-id="dad86-117">*Standing* - An experience designed for stationary standing use.</span></span> <span data-ttu-id="dad86-118">L'origine del sistema di coordinate è a livello di piano.</span><span class="sxs-lookup"><span data-stu-id="dad86-118">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="dad86-119">*Room:* un'esperienza progettata per supportare lo spostamento in una stanza.</span><span class="sxs-lookup"><span data-stu-id="dad86-119">*Room* - An experience designed to support movement throughout a room.</span></span> <span data-ttu-id="dad86-120">L'origine del sistema di coordinate è a livello di piano.</span><span class="sxs-lookup"><span data-stu-id="dad86-120">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="dad86-121">*Mondo:* un'esperienza progettata per usare e spostarsi nel mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="dad86-121">*World* - An experience designed to utilize and move through the physical world.</span></span> <span data-ttu-id="dad86-122">L'origine del sistema di coordinate è a livello di testa.</span><span class="sxs-lookup"><span data-stu-id="dad86-122">The coordinate system origin is at head level.</span></span>

## <a name="content-offset"></a><span data-ttu-id="dad86-123">Offset del contenuto</span><span class="sxs-lookup"><span data-stu-id="dad86-123">Content Offset</span></span>

<span data-ttu-id="dad86-124">Questo parametro specifica l'altezza sopra [](scene-content.md) il pavimento per compensare il contenuto della scena di realtà mista quando **Tipo** di allineamento è impostato su Allinea con **scala esperienza**</span><span class="sxs-lookup"><span data-stu-id="dad86-124">This parameter specifies the height above the floor to offset [Mixed Reality Scene Content](scene-content.md) when **Alignment Type** is set to **Align with Experience Scale**</span></span>