---
title: ConfiguringDiagnostics
description: documentazione per configurare la diagnostica in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: bc84ab193d3c3233f2930dc955d8293af578348b
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688161"
---
# <a name="configuring-the-diagnostics-system"></a><span data-ttu-id="b8dcf-104">Configurazione del sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="b8dcf-104">Configuring the diagnostics system</span></span>

## <a name="general-settings"></a><span data-ttu-id="b8dcf-105">Impostazioni generali</span><span class="sxs-lookup"><span data-stu-id="b8dcf-105">General settings</span></span>

![Impostazioni generali di diagnostica](../Images/Diagnostics/DiagnosticsGeneralSettings.png)

### <a name="show-diagnostics"></a><span data-ttu-id="b8dcf-107">Visualizza diagnostica</span><span class="sxs-lookup"><span data-stu-id="b8dcf-107">Show diagnostics</span></span>

<span data-ttu-id="b8dcf-108">Indica se il sistema di diagnostica deve visualizzare o meno le opzioni di diagnostica configurate.</span><span class="sxs-lookup"><span data-stu-id="b8dcf-108">Indicates whether or not the diagnostics system is to display the configured diagnostic options.</span></span>

<span data-ttu-id="b8dcf-109">Quando questa opzione è disabilitata, tutte le opzioni di diagnostica configurate saranno nascoste.</span><span class="sxs-lookup"><span data-stu-id="b8dcf-109">When disabled, all configured diagnostic options will be hidden.</span></span>

## <a name="profiler-settings"></a><span data-ttu-id="b8dcf-110">Impostazioni del profiler</span><span class="sxs-lookup"><span data-stu-id="b8dcf-110">Profiler settings</span></span>

![Impostazioni del profiler di diagnostica](../Images/Diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a><span data-ttu-id="b8dcf-112">Mostra Profiler</span><span class="sxs-lookup"><span data-stu-id="b8dcf-112">Show profiler</span></span>

<span data-ttu-id="b8dcf-113">Indica se il profiler deve essere visualizzato o meno.</span><span class="sxs-lookup"><span data-stu-id="b8dcf-113">Indicates whether or not the Visual Profiler is to be displayed.</span></span>

### <a name="frame-sample-rate"></a><span data-ttu-id="b8dcf-114">Frequenza di campionamento frame</span><span class="sxs-lookup"><span data-stu-id="b8dcf-114">Frame sample rate</span></span>

<span data-ttu-id="b8dcf-115">Quantità di tempo, in secondi, per la raccolta dei frame per il calcolo della frequenza dei fotogrammi.</span><span class="sxs-lookup"><span data-stu-id="b8dcf-115">The amount of time, in seconds to collect frames for frame rate calculation.</span></span> <span data-ttu-id="b8dcf-116">L'intervallo è compreso tra 0 e 5 secondi.</span><span class="sxs-lookup"><span data-stu-id="b8dcf-116">The range is 0 to 5 seconds.</span></span>

### <a name="window-anchor"></a><span data-ttu-id="b8dcf-117">Ancoraggio finestra</span><span class="sxs-lookup"><span data-stu-id="b8dcf-117">Window anchor</span></span>

<span data-ttu-id="b8dcf-118">A quale parte della porta di visualizzazione deve essere ancorata la finestra del profiler.</span><span class="sxs-lookup"><span data-stu-id="b8dcf-118">To what portion of the view port should the profiler window be anchored.</span></span> <span data-ttu-id="b8dcf-119">Il valore predefinito è il centro inferiore.</span><span class="sxs-lookup"><span data-stu-id="b8dcf-119">The default value is Lower Center.</span></span>

### <a name="window-offset"></a><span data-ttu-id="b8dcf-120">Offset finestra</span><span class="sxs-lookup"><span data-stu-id="b8dcf-120">Window offset</span></span>

<span data-ttu-id="b8dcf-121">Offset, dal centro della porta di visualizzazione, per inserire Visual Profiler.</span><span class="sxs-lookup"><span data-stu-id="b8dcf-121">The offset, from the center of the view port, to place the Visual Profiler.</span></span> <span data-ttu-id="b8dcf-122">L'offset sarà nella direzione della proprietà di *ancoraggio della finestra* .</span><span class="sxs-lookup"><span data-stu-id="b8dcf-122">The offset will be in the direction of the *Window Anchor* property.</span></span>

### <a name="window-scale"></a><span data-ttu-id="b8dcf-123">Scala della finestra</span><span class="sxs-lookup"><span data-stu-id="b8dcf-123">Window scale</span></span>

<span data-ttu-id="b8dcf-124">Moltiplicatore dimensioni applicato alla finestra del profiler.</span><span class="sxs-lookup"><span data-stu-id="b8dcf-124">Size multiplier applied to the profiler window.</span></span> <span data-ttu-id="b8dcf-125">Se ad esempio si imposta il valore su 2, le dimensioni della finestra vengono raddoppiate.</span><span class="sxs-lookup"><span data-stu-id="b8dcf-125">For example, setting the value to 2 will double the window size.</span></span>

### <a name="window-follow-speed"></a><span data-ttu-id="b8dcf-126">Velocità di completamento finestra</span><span class="sxs-lookup"><span data-stu-id="b8dcf-126">Window follow speed</span></span>

<span data-ttu-id="b8dcf-127">Velocità di spostamento della finestra del profiler per mantenere la visibilità all'interno della porta di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="b8dcf-127">The speed at which to move the profiler window to maintain visibility within the view port.</span></span>

## <a name="programmatically-controlling-the-diagnostics-system"></a><span data-ttu-id="b8dcf-128">Controllo a livello di codice del sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="b8dcf-128">Programmatically controlling the diagnostics system</span></span>

<span data-ttu-id="b8dcf-129">È anche possibile impostare la visibilità del sistema di diagnostica e del profiler in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="b8dcf-129">It's also possible to toggle the visibility of the diagnostics system and the profiler at runtime.</span></span> <span data-ttu-id="b8dcf-130">Il codice seguente, ad esempio, nasconde il sistema di diagnostica e il profiler.</span><span class="sxs-lookup"><span data-stu-id="b8dcf-130">For example, the code below will hide the diagnostics system and profiler.</span></span>

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a><span data-ttu-id="b8dcf-131">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="b8dcf-131">See also</span></span>

- [<span data-ttu-id="b8dcf-132">Sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="b8dcf-132">Diagnostics System</span></span>](DiagnosticsSystemGettingStarted.md)
- [<span data-ttu-id="b8dcf-133">Uso di Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="b8dcf-133">Using the Visual Profiler</span></span>](UsingVisualProfiler.md)
