---
title: Abitare
description: Interazione con l'ora
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: Dwell, Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 18e69f001c8989234d1b75fb713796f079cacbdf
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647800"
---
# <a name="dwell"></a><span data-ttu-id="2da38-104">Abitare</span><span class="sxs-lookup"><span data-stu-id="2da38-104">Dwell</span></span>

![Dwell hero](../images/dwell/MRTK_UX_Dwell.png)

<span data-ttu-id="2da38-106">Il sguardo fisso e l'sguardo fisso sono ottimi negli scenari in cui le mani di una persona sono occupate da altre attività.</span><span class="sxs-lookup"><span data-stu-id="2da38-106">Head-gaze and dwell are great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="2da38-107">Questa funzionalità è utile anche quando la voce non è affidabile al 100% o disponibile a causa di vincoli ambientali o sociali.</span><span class="sxs-lookup"><span data-stu-id="2da38-107">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="2da38-108">Gli esempi di dwell di MRTK illustrano diversi tipi di componenti dell'interfaccia utente con tempi di risposta configurabili e feedback visivo.</span><span class="sxs-lookup"><span data-stu-id="2da38-108">MRTK's dwell examples demonstrate different types of UI components with configurable response time and visual feedback.</span></span>

<span data-ttu-id="2da38-109">Per le [raccomandazioni di progettazione,](/windows/mixed-reality/design/gaze-and-dwell-head) vedere la pagina delle linee guida per lo sguardo fisso e l'sguardo fisso.</span><span class="sxs-lookup"><span data-stu-id="2da38-109">Please see [Head-gaze and dwell guideline](/windows/mixed-reality/design/gaze-and-dwell-head) page for the design recommendations.</span></span>

## <a name="dwell-scripts"></a><span data-ttu-id="2da38-110">Script di dwell</span><span class="sxs-lookup"><span data-stu-id="2da38-110">Dwell scripts</span></span>

- <span data-ttu-id="2da38-111">**DwellHandler:** aggiunge una modalità di inattività alla destinazione dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="2da38-111">**DwellHandler**: Adds a dwell modality to the UI target.</span></span>
- <span data-ttu-id="2da38-112">**DwellStateType:** stati del gestore di dwell.</span><span class="sxs-lookup"><span data-stu-id="2da38-112">**DwellStateType**: The states of the dwell handler.</span></span>
- <span data-ttu-id="2da38-113">**DwellUnityEvent:** evento Unity per un evento di dwell.</span><span class="sxs-lookup"><span data-stu-id="2da38-113">**DwellUnityEvent**: Unity event for a dwell event.</span></span> <span data-ttu-id="2da38-114">Contiene il riferimento al puntatore.</span><span class="sxs-lookup"><span data-stu-id="2da38-114">Contains the pointer reference.</span></span>
- <span data-ttu-id="2da38-115">**BaseDwellPressableButton.cs:** script che attiva l'evento OnClick() nei `Interactable` prefab PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="2da38-115">**BaseDwellPressableButton.cs** : A script that triggers OnClick() event in `Interactable` of PressableButtonHoloLens2 prefabs.</span></span>
- <span data-ttu-id="2da38-116">**ToggleDwellPressableButton.cs:** questo script modifica la proprietà di `_BorderWidth` che usa lo shader standard `dwellVisualImage` MRTK.</span><span class="sxs-lookup"><span data-stu-id="2da38-116">**ToggleDwellPressableButton.cs** : This script modifies `_BorderWidth` property of the `dwellVisualImage` which is using MRTK Standard Shader.</span></span>

## <a name="dwell-profiles"></a><span data-ttu-id="2da38-117">Profili di dwell</span><span class="sxs-lookup"><span data-stu-id="2da38-117">Dwell profiles</span></span>
<span data-ttu-id="2da38-118">I profili di memoria vengono usati dal **gestore di memoria per** configurare le varie soglie.</span><span class="sxs-lookup"><span data-stu-id="2da38-118">Dwell profiles are used by the **Dwell Handler** to configure the various thresholds.</span></span>
- <span data-ttu-id="2da38-119">**ButtonDwellProfile.asset**</span><span class="sxs-lookup"><span data-stu-id="2da38-119">**ButtonDwellProfile.asset**</span></span>
- <span data-ttu-id="2da38-120">**InstandDwellProfile.asset**</span><span class="sxs-lookup"><span data-stu-id="2da38-120">**InstandDwellProfile.asset**</span></span>
- <span data-ttu-id="2da38-121">**DwellProfileWithDecay.asset**</span><span class="sxs-lookup"><span data-stu-id="2da38-121">**DwellProfileWithDecay.asset**</span></span>

## <a name="prefabs"></a><span data-ttu-id="2da38-122">Prefab</span><span class="sxs-lookup"><span data-stu-id="2da38-122">Prefabs</span></span>

<span data-ttu-id="2da38-123">Questi prefab sono varianti dei prefab HoloLens 2 prefab di pulsanti pre-stampabili in stile stile che dispongono di componenti aggiuntivi per supportare le interazioni di sospensione.</span><span class="sxs-lookup"><span data-stu-id="2da38-123">These prefabs are variants of the HoloLens 2 style pressable button prefabs that have additional components to support dwell interactions.</span></span>

- <span data-ttu-id="2da38-124">**PressableButtonHoloLens2_Dwell.prefab**</span><span class="sxs-lookup"><span data-stu-id="2da38-124">**PressableButtonHoloLens2_Dwell.prefab**</span></span>
- <span data-ttu-id="2da38-125">**PressableButtonHoloLens2_32x96_Dwell.prefab**</span><span class="sxs-lookup"><span data-stu-id="2da38-125">**PressableButtonHoloLens2_32x96_Dwell.prefab**</span></span>
- <span data-ttu-id="2da38-126">**PressableButtonHoloLens2ToggleDwell.prefab**</span><span class="sxs-lookup"><span data-stu-id="2da38-126">**PressableButtonHoloLens2ToggleDwell.prefab**</span></span>
- <span data-ttu-id="2da38-127">**PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**</span><span class="sxs-lookup"><span data-stu-id="2da38-127">**PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**</span></span>

<span data-ttu-id="2da38-128">Questi prefab hanno un componente backplate aggiuntivo **QuadDwellVisual** per visualizzare lo stato di input dell'intervallo di tempo.</span><span class="sxs-lookup"><span data-stu-id="2da38-128">These prefabs have an additional backplate component **QuadDwellVisual** to visualize the dwell input state.</span></span> <span data-ttu-id="2da38-129">Ha un **materiale HolographicBackPlateDwellVisual.mat** assegnato.</span><span class="sxs-lookup"><span data-stu-id="2da38-129">It has **HolographicBackPlateDwellVisual.mat** material assigned.</span></span> <span data-ttu-id="2da38-130">**ToggleDwellPressableButton.cs** aggiorna la **proprietà _BorderWidth** dello shader MRTK Standard per visualizzare l'input di dwell.</span><span class="sxs-lookup"><span data-stu-id="2da38-130">**ToggleDwellPressableButton.cs** updates the **_BorderWidth** property of MRTK Standard shader to visualize the dwell input.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a><span data-ttu-id="2da38-131">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="2da38-131">Example scene</span></span>

<span data-ttu-id="2da38-132">È possibile trovare esempi nella `DwellExample` scena.</span><span class="sxs-lookup"><span data-stu-id="2da38-132">You can find examples in the `DwellExample` scene.</span></span> <span data-ttu-id="2da38-133">La scena di esempio mostra sia esempi di interfaccia utente volumetrici che esempi di interfaccia utente unity.</span><span class="sxs-lookup"><span data-stu-id="2da38-133">The example scene shows both volumetric UI examples and Unity UI examples.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a><span data-ttu-id="2da38-134">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="2da38-134">See also</span></span>

- [<span data-ttu-id="2da38-135">**Pulsanti**</span><span class="sxs-lookup"><span data-stu-id="2da38-135">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="2da38-136">**Con interazione**</span><span class="sxs-lookup"><span data-stu-id="2da38-136">**Interactable**</span></span>](interactable.md)
