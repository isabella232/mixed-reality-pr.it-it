---
title: Configurazione della diagnostica
description: Documentazione per configurare la diagnostica in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 211ee2ed06ba9b13bd90169bcc7ee50da4594034
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121799"
---
# <a name="configuring-the-diagnostics-system"></a><span data-ttu-id="2cbd1-104">Configurazione del sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="2cbd1-104">Configuring the diagnostics system</span></span>

## <a name="general-settings"></a><span data-ttu-id="2cbd1-105">Impostazioni generali</span><span class="sxs-lookup"><span data-stu-id="2cbd1-105">General settings</span></span>

![Impostazioni generali di diagnostica](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a><span data-ttu-id="2cbd1-107">Abilita la registrazione dettagliata</span><span class="sxs-lookup"><span data-stu-id="2cbd1-107">Enable verbose logging</span></span>

<span data-ttu-id="2cbd1-108">Indica se la registrazione MRTK dettagliata verrà abilitata o meno.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-108">Indicates whether or not verbose MRTK logging will be enabled.</span></span> <span data-ttu-id="2cbd1-109">Questa impostazione predefinita è false, ma può essere attivata per eseguire tracce dettagliate che consentono al team MRTK di eseguire il debug o di risolvere i problemi.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-109">This defaults to false, but can be turned on to take detailed traces that allow the MRTK team to debug/dig into issues.</span></span> <span data-ttu-id="2cbd1-110">Ad esempio, quando si registra un problema, collegare i log del giocatore unity (dall'editor o dal lettore) può aiutare a restringere l'origine di bug e problemi.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-110">For example, when filing an issue, attaching the Unity player logs (either from the editor or from the player) can help narrow down the source of bugs and issues.</span></span>

<span data-ttu-id="2cbd1-111">Si noti che questa opzione è indipendente dal fatto che il sistema di diagnostica sia abilitato o meno. Questa opzione viene visualizzata nel sistema di diagnostica perché è un'opzione di registrazione, ma funziona a un livello superiore perché influisce sulla registrazione nell'intera codebase MRTK.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-111">Note that this option is independent of whether or not diagnostics system is enabled - this shows up under the diagnostics system because it's a logging option, but ultimately operates at a higher level because it affects logging across the entire MRTK codebase.</span></span>

### <a name="show-diagnostics"></a><span data-ttu-id="2cbd1-112">Visualizza diagnostica</span><span class="sxs-lookup"><span data-stu-id="2cbd1-112">Show diagnostics</span></span>

<span data-ttu-id="2cbd1-113">Indica se il sistema di diagnostica deve visualizzare le opzioni di diagnostica configurate.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-113">Indicates whether or not the diagnostics system is to display the configured diagnostic options.</span></span>

<span data-ttu-id="2cbd1-114">Se disabilitata, tutte le opzioni di diagnostica configurate verranno nascoste.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-114">When disabled, all configured diagnostic options will be hidden.</span></span>

## <a name="profiler-settings"></a><span data-ttu-id="2cbd1-115">Impostazioni del profiler</span><span class="sxs-lookup"><span data-stu-id="2cbd1-115">Profiler settings</span></span>

![Impostazioni del profiler di diagnostica](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a><span data-ttu-id="2cbd1-117">Mostra profiler</span><span class="sxs-lookup"><span data-stu-id="2cbd1-117">Show profiler</span></span>

<span data-ttu-id="2cbd1-118">Indica se visual profiler deve essere visualizzato o meno.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-118">Indicates whether or not the Visual Profiler is to be displayed.</span></span>

### <a name="frame-sample-rate"></a><span data-ttu-id="2cbd1-119">Frequenza di campionamento dei fotogrammi</span><span class="sxs-lookup"><span data-stu-id="2cbd1-119">Frame sample rate</span></span>

<span data-ttu-id="2cbd1-120">Quantità di tempo, in secondi, per raccogliere i fotogrammi per il calcolo della frequenza dei fotogrammi.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-120">The amount of time, in seconds to collect frames for frame rate calculation.</span></span> <span data-ttu-id="2cbd1-121">L'intervallo è compreso tra 0 e 5 secondi.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-121">The range is 0 to 5 seconds.</span></span>

### <a name="window-anchor"></a><span data-ttu-id="2cbd1-122">Ancoraggio finestra</span><span class="sxs-lookup"><span data-stu-id="2cbd1-122">Window anchor</span></span>

<span data-ttu-id="2cbd1-123">A quale parte della porta di visualizzazione deve essere ancorata la finestra del profiler.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-123">To what portion of the view port should the profiler window be anchored.</span></span> <span data-ttu-id="2cbd1-124">Il valore predefinito è Centro inferiore.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-124">The default value is Lower Center.</span></span>

### <a name="window-offset"></a><span data-ttu-id="2cbd1-125">Offset della finestra</span><span class="sxs-lookup"><span data-stu-id="2cbd1-125">Window offset</span></span>

<span data-ttu-id="2cbd1-126">Offset, dal centro della porta di visualizzazione, per posizionare Visual Profiler.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-126">The offset, from the center of the view port, to place the Visual Profiler.</span></span> <span data-ttu-id="2cbd1-127">L'offset sarà nella direzione della proprietà *Ancoraggio* finestra.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-127">The offset will be in the direction of the *Window Anchor* property.</span></span>

### <a name="window-scale"></a><span data-ttu-id="2cbd1-128">Scalabilità della finestra</span><span class="sxs-lookup"><span data-stu-id="2cbd1-128">Window scale</span></span>

<span data-ttu-id="2cbd1-129">Moltiplicatore di dimensioni applicato alla finestra del profiler.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-129">Size multiplier applied to the profiler window.</span></span> <span data-ttu-id="2cbd1-130">Ad esempio, l'impostazione del valore su 2 raddoppierà le dimensioni della finestra.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-130">For example, setting the value to 2 will double the window size.</span></span>

### <a name="window-follow-speed"></a><span data-ttu-id="2cbd1-131">Velocità di follow della finestra</span><span class="sxs-lookup"><span data-stu-id="2cbd1-131">Window follow speed</span></span>

<span data-ttu-id="2cbd1-132">Velocità alla quale spostare la finestra del profiler per mantenere la visibilità all'interno della porta di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-132">The speed at which to move the profiler window to maintain visibility within the view port.</span></span>

## <a name="programmatically-controlling-the-diagnostics-system"></a><span data-ttu-id="2cbd1-133">Controllo del sistema di diagnostica a livello di codice</span><span class="sxs-lookup"><span data-stu-id="2cbd1-133">Programmatically controlling the diagnostics system</span></span>

<span data-ttu-id="2cbd1-134">È anche possibile attivare o disattivare la visibilità del sistema di diagnostica e del profiler in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-134">It's also possible to toggle the visibility of the diagnostics system and the profiler at runtime.</span></span> <span data-ttu-id="2cbd1-135">Ad esempio, il codice seguente nasconderà il sistema di diagnostica e il profiler.</span><span class="sxs-lookup"><span data-stu-id="2cbd1-135">For example, the code below will hide the diagnostics system and profiler.</span></span>

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a><span data-ttu-id="2cbd1-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2cbd1-136">See also</span></span>

- [<span data-ttu-id="2cbd1-137">Sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="2cbd1-137">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="2cbd1-138">Uso di Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="2cbd1-138">Using the Visual Profiler</span></span>](using-visual-profiler.md)
