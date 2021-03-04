---
title: ConfiguringDiagnostics
description: documentazione per configurare la diagnostica in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 9bfcd537b7ee3acc5d760092718fab3f328955f9
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783297"
---
# <a name="configuring-the-diagnostics-system"></a><span data-ttu-id="1b68d-104">Configurazione del sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="1b68d-104">Configuring the diagnostics system</span></span>

## <a name="general-settings"></a><span data-ttu-id="1b68d-105">Impostazioni generali</span><span class="sxs-lookup"><span data-stu-id="1b68d-105">General settings</span></span>

![Impostazioni generali di diagnostica](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a><span data-ttu-id="1b68d-107">Abilita la registrazione dettagliata</span><span class="sxs-lookup"><span data-stu-id="1b68d-107">Enable verbose logging</span></span>

<span data-ttu-id="1b68d-108">Indica se la registrazione MRTK dettagliata verrà abilitata.</span><span class="sxs-lookup"><span data-stu-id="1b68d-108">Indicates whether or not verbose MRTK logging will be enabled.</span></span> <span data-ttu-id="1b68d-109">Il valore predefinito è false, ma può essere attivato per eseguire tracce dettagliate che consentono al team di MRTK di eseguire il debug e l'analisi dei problemi.</span><span class="sxs-lookup"><span data-stu-id="1b68d-109">This defaults to false, but can be turned on to take detailed traces that allow the MRTK team to debug/dig into issues.</span></span> <span data-ttu-id="1b68d-110">Ad esempio, quando si segnala un problema, il fissaggio dei log del lettore Unity (dall'editor o dal lettore) può contribuire a limitare l'origine di bug e problemi.</span><span class="sxs-lookup"><span data-stu-id="1b68d-110">For example, when filing an issue, attaching the Unity player logs (either from the editor or from the player) can help narrow down the source of bugs and issues.</span></span>

<span data-ttu-id="1b68d-111">Si noti che questa opzione è indipendente dall'abilitazione o meno del sistema di diagnostica. viene visualizzato nel sistema di diagnostica perché si tratta di un'opzione di registrazione, ma opera a un livello superiore perché influiscono sulla registrazione nell'intera codebase MRTK.</span><span class="sxs-lookup"><span data-stu-id="1b68d-111">Note that this option is independent of whether or not diagnostics system is enabled - this shows up under the diagnostics system because it's a logging option, but ultimately operates at a higher level because it affects logging across the entire MRTK codebase.</span></span>

### <a name="show-diagnostics"></a><span data-ttu-id="1b68d-112">Visualizza diagnostica</span><span class="sxs-lookup"><span data-stu-id="1b68d-112">Show diagnostics</span></span>

<span data-ttu-id="1b68d-113">Indica se il sistema di diagnostica deve visualizzare o meno le opzioni di diagnostica configurate.</span><span class="sxs-lookup"><span data-stu-id="1b68d-113">Indicates whether or not the diagnostics system is to display the configured diagnostic options.</span></span>

<span data-ttu-id="1b68d-114">Quando questa opzione è disabilitata, tutte le opzioni di diagnostica configurate saranno nascoste.</span><span class="sxs-lookup"><span data-stu-id="1b68d-114">When disabled, all configured diagnostic options will be hidden.</span></span>

## <a name="profiler-settings"></a><span data-ttu-id="1b68d-115">Impostazioni del profiler</span><span class="sxs-lookup"><span data-stu-id="1b68d-115">Profiler settings</span></span>

![Impostazioni del profiler di diagnostica](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a><span data-ttu-id="1b68d-117">Mostra Profiler</span><span class="sxs-lookup"><span data-stu-id="1b68d-117">Show profiler</span></span>

<span data-ttu-id="1b68d-118">Indica se il profiler deve essere visualizzato o meno.</span><span class="sxs-lookup"><span data-stu-id="1b68d-118">Indicates whether or not the Visual Profiler is to be displayed.</span></span>

### <a name="frame-sample-rate"></a><span data-ttu-id="1b68d-119">Frequenza di campionamento frame</span><span class="sxs-lookup"><span data-stu-id="1b68d-119">Frame sample rate</span></span>

<span data-ttu-id="1b68d-120">Quantità di tempo, in secondi, per la raccolta dei frame per il calcolo della frequenza dei fotogrammi.</span><span class="sxs-lookup"><span data-stu-id="1b68d-120">The amount of time, in seconds to collect frames for frame rate calculation.</span></span> <span data-ttu-id="1b68d-121">L'intervallo è compreso tra 0 e 5 secondi.</span><span class="sxs-lookup"><span data-stu-id="1b68d-121">The range is 0 to 5 seconds.</span></span>

### <a name="window-anchor"></a><span data-ttu-id="1b68d-122">Ancoraggio finestra</span><span class="sxs-lookup"><span data-stu-id="1b68d-122">Window anchor</span></span>

<span data-ttu-id="1b68d-123">A quale parte della porta di visualizzazione deve essere ancorata la finestra del profiler.</span><span class="sxs-lookup"><span data-stu-id="1b68d-123">To what portion of the view port should the profiler window be anchored.</span></span> <span data-ttu-id="1b68d-124">Il valore predefinito è il centro inferiore.</span><span class="sxs-lookup"><span data-stu-id="1b68d-124">The default value is Lower Center.</span></span>

### <a name="window-offset"></a><span data-ttu-id="1b68d-125">Offset finestra</span><span class="sxs-lookup"><span data-stu-id="1b68d-125">Window offset</span></span>

<span data-ttu-id="1b68d-126">Offset, dal centro della porta di visualizzazione, per inserire Visual Profiler.</span><span class="sxs-lookup"><span data-stu-id="1b68d-126">The offset, from the center of the view port, to place the Visual Profiler.</span></span> <span data-ttu-id="1b68d-127">L'offset sarà nella direzione della proprietà di *ancoraggio della finestra* .</span><span class="sxs-lookup"><span data-stu-id="1b68d-127">The offset will be in the direction of the *Window Anchor* property.</span></span>

### <a name="window-scale"></a><span data-ttu-id="1b68d-128">Scala della finestra</span><span class="sxs-lookup"><span data-stu-id="1b68d-128">Window scale</span></span>

<span data-ttu-id="1b68d-129">Moltiplicatore dimensioni applicato alla finestra del profiler.</span><span class="sxs-lookup"><span data-stu-id="1b68d-129">Size multiplier applied to the profiler window.</span></span> <span data-ttu-id="1b68d-130">Se ad esempio si imposta il valore su 2, le dimensioni della finestra vengono raddoppiate.</span><span class="sxs-lookup"><span data-stu-id="1b68d-130">For example, setting the value to 2 will double the window size.</span></span>

### <a name="window-follow-speed"></a><span data-ttu-id="1b68d-131">Velocità di completamento finestra</span><span class="sxs-lookup"><span data-stu-id="1b68d-131">Window follow speed</span></span>

<span data-ttu-id="1b68d-132">Velocità di spostamento della finestra del profiler per mantenere la visibilità all'interno della porta di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1b68d-132">The speed at which to move the profiler window to maintain visibility within the view port.</span></span>

## <a name="programmatically-controlling-the-diagnostics-system"></a><span data-ttu-id="1b68d-133">Controllo a livello di codice del sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="1b68d-133">Programmatically controlling the diagnostics system</span></span>

<span data-ttu-id="1b68d-134">È anche possibile impostare la visibilità del sistema di diagnostica e del profiler in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="1b68d-134">It's also possible to toggle the visibility of the diagnostics system and the profiler at runtime.</span></span> <span data-ttu-id="1b68d-135">Il codice seguente, ad esempio, nasconde il sistema di diagnostica e il profiler.</span><span class="sxs-lookup"><span data-stu-id="1b68d-135">For example, the code below will hide the diagnostics system and profiler.</span></span>

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a><span data-ttu-id="1b68d-136">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="1b68d-136">See also</span></span>

- [<span data-ttu-id="1b68d-137">Sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="1b68d-137">Diagnostics System</span></span>](DiagnosticsSystemGettingStarted.md)
- [<span data-ttu-id="1b68d-138">Uso di Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="1b68d-138">Using the Visual Profiler</span></span>](UsingVisualProfiler.md)
