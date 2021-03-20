---
title: SceneSystemGettingStarted
description: Pagina di destinazione per il sistema di scena con MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: adffe6a30c9154bbf5be2ca3cc783e53da4e6868
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681174"
---
# <a name="scene-system-overview"></a><span data-ttu-id="da51a-104">Panoramica del sistema di scena</span><span class="sxs-lookup"><span data-stu-id="da51a-104">Scene system overview</span></span>

## <a name="when-to-use-the-scene-system"></a><span data-ttu-id="da51a-105">Quando usare il sistema di scena</span><span class="sxs-lookup"><span data-stu-id="da51a-105">When to use the scene system</span></span>

<span data-ttu-id="da51a-106">Se il progetto è costituito da un'unica scena, probabilmente il sistema della scena non è necessario.</span><span class="sxs-lookup"><span data-stu-id="da51a-106">If your project consists of a single scene, the Scene System probably isn't necessary.</span></span> <span data-ttu-id="da51a-107">È particolarmente utile quando si verificano una o più delle condizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="da51a-107">It is most useful when one or more of the following are true:</span></span>

- <span data-ttu-id="da51a-108">Il progetto include più scene.</span><span class="sxs-lookup"><span data-stu-id="da51a-108">Your project has multiple scenes.</span></span>
- <span data-ttu-id="da51a-109">Si viene usati per il caricamento di una singola scena, ma non è come il modo in cui viene distrutta l'istanza di MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="da51a-109">You're used to single scene loading, but you don't like the way it destroys the MixedRealityToolkit instance.</span></span>
- <span data-ttu-id="da51a-110">Si vuole un modo semplice per caricare additivamente più scene per costruire la propria esperienza.</span><span class="sxs-lookup"><span data-stu-id="da51a-110">You want a simple way to additively load multiple scenes to construct your experience.</span></span>
- <span data-ttu-id="da51a-111">Si vuole un modo semplice per tenere traccia delle operazioni di caricamento in corso o un modo semplice per controllare l'attivazione della scena per più scene caricate contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="da51a-111">You want a simple way to keep track of load operations in progress or a simple way to control scene activation for multiple scenes being loaded at once.</span></span>
- <span data-ttu-id="da51a-112">Si vuole rendere l'illuminazione coerente e prevedibile in tutte le scene.</span><span class="sxs-lookup"><span data-stu-id="da51a-112">You want to keep lighting consistent and predictable across all your scenes.</span></span>

## <a name="how-to-use-the-scene-system"></a><span data-ttu-id="da51a-113">Come usare il sistema di scena</span><span class="sxs-lookup"><span data-stu-id="da51a-113">How to use the scene system</span></span>

- [<span data-ttu-id="da51a-114">Tipi di scena</span><span class="sxs-lookup"><span data-stu-id="da51a-114">Scene Types</span></span>](SceneSystemSceneTypes.md)
- [<span data-ttu-id="da51a-115">Caricamento della scena del contenuto</span><span class="sxs-lookup"><span data-stu-id="da51a-115">Content Scene Loading</span></span>](SceneSystemContentLoading.md)
- [<span data-ttu-id="da51a-116">Monitoraggio del caricamento del contenuto</span><span class="sxs-lookup"><span data-stu-id="da51a-116">Monitoring Content Loading</span></span>](SceneSystemLoadProgress.md)
- [<span data-ttu-id="da51a-117">Caricamento della scena di illuminazione</span><span class="sxs-lookup"><span data-stu-id="da51a-117">Lighting Scene Loading</span></span>](SceneSystemLightingScenes.md)

## <a name="editor-settings"></a><span data-ttu-id="da51a-118">Impostazioni editor</span><span class="sxs-lookup"><span data-stu-id="da51a-118">Editor settings</span></span>

<span data-ttu-id="da51a-119">Per impostazione predefinita, il sistema di scena impone diversi comportamenti nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="da51a-119">By default, the Scene System enforces several behaviors in the Unity editor.</span></span> <span data-ttu-id="da51a-120">Se uno di questi comportamenti è elevato, è possibile disabilitarli nella sezione **Impostazioni editor** del profilo di sistema della scena.</span><span class="sxs-lookup"><span data-stu-id="da51a-120">If you find any of these behaviors heavy-handed, they can be disabled in the **Editor Settings** section of your Scene System profile.</span></span>

- <span data-ttu-id="da51a-121">`Editor Manage Build Settings:` Se true, il servizio aggiornerà automaticamente le impostazioni di compilazione, assicurando l'aggiunta di tutte le scene di gestione, illuminazione e contenuto.</span><span class="sxs-lookup"><span data-stu-id="da51a-121">`Editor Manage Build Settings:` If true, the service will update your build settings automatically, ensuring that all manager, lighting and content scenes are added.</span></span> <span data-ttu-id="da51a-122">Disabilitare questa impostazione se si desidera il controllo totale sulle impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="da51a-122">Disable this if you want total control over build settings.</span></span>

- <span data-ttu-id="da51a-123">`Editor Enforce Scene Order:` Se true, il servizio assicurerà che la scena del Manager venga visualizzata per prima nella gerarchia della scena, seguita dall'illuminazione e quindi dal contenuto.</span><span class="sxs-lookup"><span data-stu-id="da51a-123">`Editor Enforce Scene Order:` If true, the service will ensure that the manager scene is displayed first in scene hierarchy, followed by lighting and then content.</span></span> <span data-ttu-id="da51a-124">Disabilitare questa proprietà se si desidera il controllo totale sulla gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="da51a-124">Disable this if you want total control over scene hierarchy.</span></span>

- <span data-ttu-id="da51a-125">`Editor Manage Loaded Scenes:` Se true, il servizio assicurerà che il responsabile, il contenuto e le scene di illuminazione siano sempre caricati.</span><span class="sxs-lookup"><span data-stu-id="da51a-125">`Editor Manage Loaded Scenes:` If true, the service will ensure that the manager, content and lighting scenes are always loaded.</span></span> <span data-ttu-id="da51a-126">Disabilitare se si desidera il controllo totale sulle scene caricate nell'editor.</span><span class="sxs-lookup"><span data-stu-id="da51a-126">Disable if you want total control over which scenes are loaded in editor.</span></span>

- <span data-ttu-id="da51a-127">`Editor Enforce Lighting Scene Types:` Se true, il servizio garantirà che solo i componenti correlati all'illuminazione definiti in `PermittedLightingSceneComponentTypes` siano consentiti nelle scene di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="da51a-127">`Editor Enforce Lighting Scene Types:` If true, the service will ensure that only the lighting-related components defined in `PermittedLightingSceneComponentTypes` are allowed in lighting scenes.</span></span> <span data-ttu-id="da51a-128">Disabilitare se si desidera il controllo totale sul contenuto delle scene di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="da51a-128">Disable if you want total control over the content of lighting scenes.</span></span>

![Impostazioni dell'editor di sistema della scena](../Images/SceneSystem/MRTK_SceneSystemProfileEditorSettings.PNG)
