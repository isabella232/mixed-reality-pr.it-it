---
title: Uso del profiler visivo
description: documentazione per l'uso di Visual Profiler in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: c3238aed60f6bbf824c74c034ddf506f49f436c7
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121649"
---
# <a name="using-the-visual-profiler"></a><span data-ttu-id="74dee-104">Uso del profiler visivo</span><span class="sxs-lookup"><span data-stu-id="74dee-104">Using the visual profiler</span></span>

<span data-ttu-id="74dee-105">VisualProfiler offre una visualizzazione in-application facile da usare delle prestazioni di un'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="74dee-105">The VisualProfiler provides an easy to use, in-application view of a mixed reality application's performance.</span></span> <span data-ttu-id="74dee-106">Il profiler è supportato in tutte le piattaforme mixed reality toolkit, tra cui:</span><span class="sxs-lookup"><span data-stu-id="74dee-106">The profiler is supported on all Mixed Reality Toolkit platforms, including:</span></span>

- <span data-ttu-id="74dee-107">Microsoft HoloLens (prima generazione)</span><span class="sxs-lookup"><span data-stu-id="74dee-107">Microsoft HoloLens (1st gen)</span></span>
- <span data-ttu-id="74dee-108">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="74dee-108">Microsoft HoloLens 2</span></span>
- <span data-ttu-id="74dee-109">Visori VR immersive di Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="74dee-109">Windows Mixed Reality immersive headsets</span></span>
- <span data-ttu-id="74dee-110">OpenVR</span><span class="sxs-lookup"><span data-stu-id="74dee-110">OpenVR</span></span>

<span data-ttu-id="74dee-111">Durante lo sviluppo di un'applicazione, concentrarsi su più parti della scena quando Visual Profiler visualizza i dati relativi alla visualizzazione corrente.</span><span class="sxs-lookup"><span data-stu-id="74dee-111">While developing an application, focus on multiple parts of the scene as the Visual Profiler displays data relative to the current view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="74dee-112">Concentrare l'attenzione su parti della scena con oggetti complessi, effetti di particelle o attività.</span><span class="sxs-lookup"><span data-stu-id="74dee-112">Focus attention on portions of the scene with complex objects, particle effects or activity.</span></span> <span data-ttu-id="74dee-113">Questi e altri fattori contribuiscono spesso alla riduzione delle prestazioni dell'applicazione e a un'esperienza utente inferiore a quella ideale.</span><span class="sxs-lookup"><span data-stu-id="74dee-113">These and other factors often contribute to reduction in application performance and a less than ideal user experience.</span></span>

## <a name="visual-profiler-interface"></a><span data-ttu-id="74dee-114">Interfaccia del profiler visivo</span><span class="sxs-lookup"><span data-stu-id="74dee-114">Visual profiler interface</span></span>

![Interfaccia di Visual Profiler](../images/diagnostics/VisualProfiler.png)

<span data-ttu-id="74dee-116">L'interfaccia di Visual Profiler include i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="74dee-116">The Visual Profiler interface includes the following components:</span></span>

- [<span data-ttu-id="74dee-117">Frequenza dei fotogrammi</span><span class="sxs-lookup"><span data-stu-id="74dee-117">Frame Rate</span></span>](#frame-rate)
- [<span data-ttu-id="74dee-118">Tempo dell'intervallo</span><span class="sxs-lookup"><span data-stu-id="74dee-118">Frame Time</span></span>](#frame-time)
- [<span data-ttu-id="74dee-119">Grafico dei frame</span><span class="sxs-lookup"><span data-stu-id="74dee-119">Frame Graph</span></span>](#frame-graph)
- [<span data-ttu-id="74dee-120">Utilizzo della memoria</span><span class="sxs-lookup"><span data-stu-id="74dee-120">Memory Utilization</span></span>](#memory-utilization)

### <a name="frame-rate"></a><span data-ttu-id="74dee-121">Frequenza dei fotogrammi</span><span class="sxs-lookup"><span data-stu-id="74dee-121">Frame rate</span></span>

<span data-ttu-id="74dee-122">Nell'angolo superiore sinistro dell'interfaccia è presente la frequenza dei fotogrammi, misurata in fotogrammi al secondo.</span><span class="sxs-lookup"><span data-stu-id="74dee-122">In the upper-left corner of the interface is the frame rate, measured in frames per second.</span></span> <span data-ttu-id="74dee-123">Per la migliore esperienza utente e il massimo comfort, questo valore deve essere il più alto possibile.</span><span class="sxs-lookup"><span data-stu-id="74dee-123">For the best user experience and comfort, this value should be as high as possible.</span></span>

<span data-ttu-id="74dee-124">La piattaforma e la configurazione hardware specifiche avranno un ruolo significativo nella frequenza dei fotogrammi massima ottenibile.</span><span class="sxs-lookup"><span data-stu-id="74dee-124">The specific platform and hardware configuration will play a significant role in the maximum achievable frame rate.</span></span> <span data-ttu-id="74dee-125">Alcuni valori di destinazione comuni includono:</span><span class="sxs-lookup"><span data-stu-id="74dee-125">Some common target values include:</span></span>

- <span data-ttu-id="74dee-126">Microsoft HoloLens: 60</span><span class="sxs-lookup"><span data-stu-id="74dee-126">Microsoft HoloLens: 60</span></span>
- <span data-ttu-id="74dee-127">Windows Mixed Reality Ultra: 90</span><span class="sxs-lookup"><span data-stu-id="74dee-127">Windows Mixed Reality Ultra: 90</span></span>

> [!NOTE]
> <span data-ttu-id="74dee-128">A causa della limitazione della frequenza dei fotogrammi in [HoloLens](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)quando mrC predefinito è attivo, il profiler visivo si nasconde mentre vengono acquisiti video e foto.</span><span class="sxs-lookup"><span data-stu-id="74dee-128">Due to [frame rate throttling on HoloLens when default MRC is active](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), the visual profiler hides itself while videos and photos are captured.</span></span> <span data-ttu-id="74dee-129">Questa impostazione può essere sostituita nel profilo del sistema di diagnostica.</span><span class="sxs-lookup"><span data-stu-id="74dee-129">This setting can be overridden in the diagnostics system profile.</span></span>

### <a name="frame-time"></a><span data-ttu-id="74dee-130">Durata fotogramma</span><span class="sxs-lookup"><span data-stu-id="74dee-130">Frame time</span></span>

<span data-ttu-id="74dee-131">A destra della frequenza dei fotogrammi si trova il tempo in millisecondi impiegato per la CPU.</span><span class="sxs-lookup"><span data-stu-id="74dee-131">To the right of the frame rate is the frame time, in milliseconds, spent on the CPU.</span></span> <span data-ttu-id="74dee-132">Per ottenere la frequenza dei fotogrammi di destinazione indicata in precedenza, un'applicazione può impiegare la quantità di tempo seguente per fotogramma:</span><span class="sxs-lookup"><span data-stu-id="74dee-132">To achieve the target frame rates mentioned previously, an application can spend the following amount of time per frame:</span></span>

- <span data-ttu-id="74dee-133">60 fps: 16,6 ms</span><span class="sxs-lookup"><span data-stu-id="74dee-133">60 fps: 16.6 ms</span></span>
- <span data-ttu-id="74dee-134">90 fps: 11,1 ms</span><span class="sxs-lookup"><span data-stu-id="74dee-134">90 fps: 11.1 ms</span></span>

<span data-ttu-id="74dee-135">È previsto che l'ora della GPU verrà aggiunta in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="74dee-135">GPU time is planned to be added in a future release.</span></span>

### <a name="frame-graph"></a><span data-ttu-id="74dee-136">Grafico dei frame</span><span class="sxs-lookup"><span data-stu-id="74dee-136">Frame graph</span></span>

<span data-ttu-id="74dee-137">Il grafico dei frame offre una visualizzazione grafica della cronologia della frequenza dei fotogrammi dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="74dee-137">The frame graph provides a graphical display of the application frame rate history.</span></span>

![Grafico dei fotogrammi persi di Visual Profiler](../images/diagnostics/VisualProfilerMissedFrames.png)

<span data-ttu-id="74dee-139">Quando si usa l'applicazione, cercare i fotogrammi persi che indicano che l'applicazione non sta per raggiungere la frequenza dei fotogrammi di destinazione e potrebbe richiedere operazioni di ottimizzazione.</span><span class="sxs-lookup"><span data-stu-id="74dee-139">When using the application, look for missed frames which indicate that the application is not hitting its target frame rate and may need optimization work.</span></span>

### <a name="memory-utilization"></a><span data-ttu-id="74dee-140">Utilizzo della memoria</span><span class="sxs-lookup"><span data-stu-id="74dee-140">Memory utilization</span></span>

<span data-ttu-id="74dee-141">La visualizzazione dell'utilizzo della memoria consente di comprendere facilmente l'impatto della visualizzazione corrente sul consumo di memoria di un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="74dee-141">The memory utilization display allows for easy understanding of how the current view is impacting an application's memory consumption.</span></span>

![Grafico della memoria di Visual Profiler](../images/diagnostics/VisualProfilerMemory.png)

<span data-ttu-id="74dee-143">Quando si usa l'applicazione, cercare l'utilizzo totale della memoria.</span><span class="sxs-lookup"><span data-stu-id="74dee-143">When using the application, look for total memory usage.</span></span> <span data-ttu-id="74dee-144">Gli indicatori chiave includono il prossimità del limite di memoria e modifiche rapide nell'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="74dee-144">Key indicators include nearing the memory limit and rapid changes in usage.</span></span>

## <a name="customizing-the-visual-profiler"></a><span data-ttu-id="74dee-145">Personalizzazione del profiler visivo</span><span class="sxs-lookup"><span data-stu-id="74dee-145">Customizing the visual profiler</span></span>

<span data-ttu-id="74dee-146">L'aspetto e il comportamento di Visual Profiler sono personalizzabili tramite il profilo del sistema di diagnostica.</span><span class="sxs-lookup"><span data-stu-id="74dee-146">The Visual Profiler's appearance and behavior are customizable via the diagnostics system profile.</span></span> <span data-ttu-id="74dee-147">Per altre [informazioni, vedere Configurazione del sistema](configuring-diagnostics.md) di diagnostica.</span><span class="sxs-lookup"><span data-stu-id="74dee-147">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="74dee-148">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="74dee-148">See also</span></span>

- [<span data-ttu-id="74dee-149">Sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="74dee-149">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="74dee-150">Configurazione del sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="74dee-150">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)