---
title: UsingVisualProfiler
description: documentazione per l'uso di Visual Profiler in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 3ff0a386248b50458788c59666be7e056139f284
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550811"
---
# <a name="using-the-visual-profiler"></a><span data-ttu-id="3706d-104">Uso di Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="3706d-104">Using the visual profiler</span></span>

<span data-ttu-id="3706d-105">Il VisualProfiler offre una visualizzazione di facile utilizzo, in applicazioni, delle prestazioni di un'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="3706d-105">The VisualProfiler provides an easy to use, in-application view of a mixed reality application's performance.</span></span> <span data-ttu-id="3706d-106">Il profiler è supportato in tutte le piattaforme Toolkit per realtà miste, tra cui:</span><span class="sxs-lookup"><span data-stu-id="3706d-106">The profiler is supported on all Mixed Reality Toolkit platforms, including:</span></span>

- <span data-ttu-id="3706d-107">Microsoft HoloLens (1a generazione)</span><span class="sxs-lookup"><span data-stu-id="3706d-107">Microsoft HoloLens (1st gen)</span></span>
- <span data-ttu-id="3706d-108">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3706d-108">Microsoft HoloLens 2</span></span>
- <span data-ttu-id="3706d-109">Visori VR immersive di Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3706d-109">Windows Mixed Reality immersive headsets</span></span>
- <span data-ttu-id="3706d-110">OpenVR</span><span class="sxs-lookup"><span data-stu-id="3706d-110">OpenVR</span></span>

<span data-ttu-id="3706d-111">Durante lo sviluppo di un'applicazione, è possibile concentrarsi su più parti della scena perché Visual Profiler Visualizza i dati relativi alla visualizzazione corrente.</span><span class="sxs-lookup"><span data-stu-id="3706d-111">While developing an application, focus on multiple parts of the scene as the Visual Profiler displays data relative to the current view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3706d-112">Concentrare l'attenzione sulle parti della scena con oggetti complessi, effetti particellari o attività.</span><span class="sxs-lookup"><span data-stu-id="3706d-112">Focus attention on portions of the scene with complex objects, particle effects or activity.</span></span> <span data-ttu-id="3706d-113">Questi e altri fattori spesso contribuiscono a ridurre le prestazioni dell'applicazione e a un'esperienza utente inferiore a quella ideale.</span><span class="sxs-lookup"><span data-stu-id="3706d-113">These and other factors often contribute to reduction in application performance and a less than ideal user experience.</span></span>

## <a name="visual-profiler-interface"></a><span data-ttu-id="3706d-114">Interfaccia di Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="3706d-114">Visual profiler interface</span></span>

![Interfaccia di Visual Profiler](../images/diagnostics/VisualProfiler.png)

<span data-ttu-id="3706d-116">L'interfaccia di Visual Profiler include i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="3706d-116">The Visual Profiler interface includes the following components:</span></span>

- [<span data-ttu-id="3706d-117">Frequenza fotogrammi</span><span class="sxs-lookup"><span data-stu-id="3706d-117">Frame Rate</span></span>](#frame-rate)
- [<span data-ttu-id="3706d-118">Tempo frame</span><span class="sxs-lookup"><span data-stu-id="3706d-118">Frame Time</span></span>](#frame-time)
- [<span data-ttu-id="3706d-119">Grafico frame</span><span class="sxs-lookup"><span data-stu-id="3706d-119">Frame Graph</span></span>](#frame-graph)
- [<span data-ttu-id="3706d-120">Utilizzo memoria</span><span class="sxs-lookup"><span data-stu-id="3706d-120">Memory Utilization</span></span>](#memory-utilization)

### <a name="frame-rate"></a><span data-ttu-id="3706d-121">Frequenza dei fotogrammi</span><span class="sxs-lookup"><span data-stu-id="3706d-121">Frame rate</span></span>

<span data-ttu-id="3706d-122">Nell'angolo superiore sinistro dell'interfaccia è la frequenza dei fotogrammi, misurata in fotogrammi al secondo.</span><span class="sxs-lookup"><span data-stu-id="3706d-122">In the upper-left corner of the interface is the frame rate, measured in frames per second.</span></span> <span data-ttu-id="3706d-123">Per ottimizzare l'esperienza utente e la comodità, questo valore dovrebbe essere il più elevato possibile.</span><span class="sxs-lookup"><span data-stu-id="3706d-123">For the best user experience and comfort, this value should be as high as possible.</span></span>

<span data-ttu-id="3706d-124">La piattaforma e la configurazione hardware specifiche giocheranno un ruolo significativo nella frequenza massima ottenibile di frame.</span><span class="sxs-lookup"><span data-stu-id="3706d-124">The specific platform and hardware configuration will play a significant role in the maximum achievable frame rate.</span></span> <span data-ttu-id="3706d-125">Alcuni valori di destinazione comuni includono:</span><span class="sxs-lookup"><span data-stu-id="3706d-125">Some common target values include:</span></span>

- <span data-ttu-id="3706d-126">Microsoft HoloLens: 60</span><span class="sxs-lookup"><span data-stu-id="3706d-126">Microsoft HoloLens: 60</span></span>
- <span data-ttu-id="3706d-127">Realtà mista di Windows Ultra: 90</span><span class="sxs-lookup"><span data-stu-id="3706d-127">Windows Mixed Reality Ultra: 90</span></span>

> [!NOTE]
> <span data-ttu-id="3706d-128">A causa della [limitazione delle richieste di frequenza dei fotogrammi in HoloLens quando è attiva la fase MRC predefinita](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), il Profiler visivo si nasconde mentre vengono acquisiti video e foto.</span><span class="sxs-lookup"><span data-stu-id="3706d-128">Due to [frame rate throttling on HoloLens when default MRC is active](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), the visual profiler hides itself while videos and photos are captured.</span></span> <span data-ttu-id="3706d-129">È possibile eseguire l'override di questa impostazione nel profilo di sistema di diagnostica.</span><span class="sxs-lookup"><span data-stu-id="3706d-129">This setting can be overridden in the diagnostics system profile.</span></span>

### <a name="frame-time"></a><span data-ttu-id="3706d-130">Durata fotogramma</span><span class="sxs-lookup"><span data-stu-id="3706d-130">Frame time</span></span>

<span data-ttu-id="3706d-131">A destra della frequenza dei fotogrammi è il tempo di frame, in millisecondi, dedicato alla CPU.</span><span class="sxs-lookup"><span data-stu-id="3706d-131">To the right of the frame rate is the frame time, in milliseconds, spent on the CPU.</span></span> <span data-ttu-id="3706d-132">Per ottenere le frequenze dei frame di destinazione citate in precedenza, un'applicazione può dedicare la quantità di tempo seguente per frame:</span><span class="sxs-lookup"><span data-stu-id="3706d-132">To achieve the target frame rates mentioned previously, an application can spend the following amount of time per frame:</span></span>

- <span data-ttu-id="3706d-133">60 fps: 16,6 ms</span><span class="sxs-lookup"><span data-stu-id="3706d-133">60 fps: 16.6 ms</span></span>
- <span data-ttu-id="3706d-134">90 fps: 11,1 ms</span><span class="sxs-lookup"><span data-stu-id="3706d-134">90 fps: 11.1 ms</span></span>

<span data-ttu-id="3706d-135">Il tempo GPU è pianificato per essere aggiunto in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="3706d-135">GPU time is planned to be added in a future release.</span></span>

### <a name="frame-graph"></a><span data-ttu-id="3706d-136">Grafico frame</span><span class="sxs-lookup"><span data-stu-id="3706d-136">Frame graph</span></span>

<span data-ttu-id="3706d-137">Il grafico frame fornisce una visualizzazione grafica della cronologia della frequenza dei fotogrammi dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="3706d-137">The frame graph provides a graphical display of the application frame rate history.</span></span>

![Grafico frame mancanti di Visual Profiler](../images/diagnostics/VisualProfilerMissedFrames.png)

<span data-ttu-id="3706d-139">Quando si usa l'applicazione, cercare i frame mancanti che indicano che l'applicazione non sta raggiungendo la frequenza dei fotogrammi di destinazione e potrebbe richiedere un lavoro di ottimizzazione.</span><span class="sxs-lookup"><span data-stu-id="3706d-139">When using the application, look for missed frames which indicate that the application is not hitting its target frame rate and may need optimization work.</span></span>

### <a name="memory-utilization"></a><span data-ttu-id="3706d-140">Utilizzo della memoria</span><span class="sxs-lookup"><span data-stu-id="3706d-140">Memory utilization</span></span>

<span data-ttu-id="3706d-141">La visualizzazione utilizzo memoria consente di comprendere facilmente il modo in cui la visualizzazione corrente influisca sul consumo di memoria di un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="3706d-141">The memory utilization display allows for easy understanding of how the current view is impacting an application's memory consumption.</span></span>

![Grafico della memoria di Visual Profiler](../images/diagnostics/VisualProfilerMemory.png)

<span data-ttu-id="3706d-143">Quando si usa l'applicazione, cercare l'utilizzo totale della memoria.</span><span class="sxs-lookup"><span data-stu-id="3706d-143">When using the application, look for total memory usage.</span></span> <span data-ttu-id="3706d-144">Gli indicatori chiave sono vicini al limite di memoria e a modifiche rapide nell'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="3706d-144">Key indicators include nearing the memory limit and rapid changes in usage.</span></span>

## <a name="customizing-the-visual-profiler"></a><span data-ttu-id="3706d-145">Personalizzazione di Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="3706d-145">Customizing the visual profiler</span></span>

<span data-ttu-id="3706d-146">L'aspetto e il comportamento di Visual Profiler sono personalizzabili tramite il profilo di sistema di diagnostica.</span><span class="sxs-lookup"><span data-stu-id="3706d-146">The Visual Profiler's appearance and behavior are customizable via the diagnostics system profile.</span></span> <span data-ttu-id="3706d-147">Per ulteriori informazioni, vedere [configurazione del sistema di diagnostica](configuring-diagnostics.md) .</span><span class="sxs-lookup"><span data-stu-id="3706d-147">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="3706d-148">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="3706d-148">See also</span></span>

- [<span data-ttu-id="3706d-149">Sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="3706d-149">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="3706d-150">Configurazione del sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="3706d-150">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)