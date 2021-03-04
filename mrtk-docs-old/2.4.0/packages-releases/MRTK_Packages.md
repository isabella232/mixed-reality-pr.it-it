---
title: MRTK_Pakages
description: Pakages in MRTK che supportano l'hardware e le piattaforme a realtà mista.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Unity pakage Manager,
ms.openlocfilehash: e55077df9f6415b50b0dd6b614696914c49e702e
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783134"
---
# <a name="mixed-reality-toolkit-packages"></a><span data-ttu-id="21dde-104">Pacchetti Toolkit per realtà mista</span><span class="sxs-lookup"><span data-stu-id="21dde-104">Mixed Reality Toolkit packages</span></span>

<span data-ttu-id="21dde-105">Il Toolkit di realtà mista (MRTK) è una raccolta di pacchetti che consentono lo sviluppo di applicazioni di realtà mista multipiattaforma offrendo supporto per l'hardware e le piattaforme di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="21dde-105">The Mixed Reality Toolkit (MRTK) is a collection of packages that enable cross platform Mixed Reality application development by providing support for Mixed Reality hardware and platforms.</span></span>

<span data-ttu-id="21dde-106">MRTK viene fornito tramite i seguenti pacchetti Unity:</span><span class="sxs-lookup"><span data-stu-id="21dde-106">The MRTK ships via the following Unity packages:</span></span>

- [<span data-ttu-id="21dde-107">Foundation</span><span class="sxs-lookup"><span data-stu-id="21dde-107">Foundation</span></span>](#foundation-package)
- [<span data-ttu-id="21dde-108">Estensioni</span><span class="sxs-lookup"><span data-stu-id="21dde-108">Extensions</span></span>](#extensions-package)
- [<span data-ttu-id="21dde-109">esempi</span><span class="sxs-lookup"><span data-stu-id="21dde-109">Examples</span></span>](#examples-package)
- [<span data-ttu-id="21dde-110">Strumenti</span><span class="sxs-lookup"><span data-stu-id="21dde-110">Tools</span></span>](#tools-package)

<span data-ttu-id="21dde-111">Questi pacchetti vengono rilasciati e supportati da Microsoft dal codice sorgente nel ramo [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) su GitHub.</span><span class="sxs-lookup"><span data-stu-id="21dde-111">These packages are released and supported by Microsoft from source code in the [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) branch on GitHub.</span></span>

## <a name="foundation-package"></a><span data-ttu-id="21dde-112">Pacchetto di base</span><span class="sxs-lookup"><span data-stu-id="21dde-112">Foundation package</span></span>

<span data-ttu-id="21dde-113">Mixed Reality Toolkit Foundation è il set di codice che consente all'applicazione di sfruttare le funzionalità comuni nelle piattaforme di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="21dde-113">The Mixed Reality Toolkit Foundation is the set of code that enables your application to leverage common functionality across Mixed Reality Platforms.</span></span>

<img src="../features//Images/Input/MRTK_Package_Foundation.png" width="350px" alt="Pakage Foundation" style="display:block;">  
<span data-ttu-id="21dde-114"><sup>Pacchetto di MRTK Foundation</sup></span><span class="sxs-lookup"><span data-stu-id="21dde-114"><sup>MRTK Foundation Package</sup></span></span>

<span data-ttu-id="21dde-115">MRTK Foundation è costituito da:</span><span class="sxs-lookup"><span data-stu-id="21dde-115">The MRTK Foundation is comprised of:</span></span>

- <span data-ttu-id="21dde-116">**Pacchetto principale**</span><span class="sxs-lookup"><span data-stu-id="21dde-116">**Core Package**</span></span>

<span data-ttu-id="21dde-117">Il pacchetto principale contiene le definizioni per tutte le interfacce comuni, le classi e i tipi di dati utilizzati da tutti gli altri componenti.</span><span class="sxs-lookup"><span data-stu-id="21dde-117">The Core Package contains the definitions for all of the common interfaces, classes and data types that are used by all other components.</span></span> <span data-ttu-id="21dde-118">Si consiglia vivamente alle applicazioni di accedere ai componenti di MRTK esclusivamente tramite le interfacce definite per consentire il massimo livello di compatibilità tra le piattaforme.</span><span class="sxs-lookup"><span data-stu-id="21dde-118">It is highly recommended that applications access MRTK components exclusively through the defined interfaces to enable the highest level of compatibility across platforms.</span></span>

- <span data-ttu-id="21dde-119">**Provider di piattaforma**</span><span class="sxs-lookup"><span data-stu-id="21dde-119">**Platform Providers**</span></span>

<span data-ttu-id="21dde-120">I pacchetti del provider della piattaforma MRTK sono i componenti che consentono al Toolkit di realtà misto di usare la funzionalità di piattaforma e hardware di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="21dde-120">The MRTK Platform Provider packages are the components that enable the Mixed Reality Toolkit to target Mixed Reality hardware and platform functionality.</span></span>

<span data-ttu-id="21dde-121">Le piattaforme supportate includono:</span><span class="sxs-lookup"><span data-stu-id="21dde-121">Supported platforms include:</span></span>

- <span data-ttu-id="21dde-122">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="21dde-122">Windows Mixed Reality</span></span>
- <span data-ttu-id="21dde-123">OpenVR</span><span class="sxs-lookup"><span data-stu-id="21dde-123">OpenVR</span></span>
- <span data-ttu-id="21dde-124">Windows Voice</span><span class="sxs-lookup"><span data-stu-id="21dde-124">Windows Voice</span></span>

- <span data-ttu-id="21dde-125">**Servizi di sistema**</span><span class="sxs-lookup"><span data-stu-id="21dde-125">**System Services**</span></span>

<span data-ttu-id="21dde-126">I servizi di base forniscono le implementazioni predefinite per le interfacce del servizio di sistema, definite nel pacchetto principale.</span><span class="sxs-lookup"><span data-stu-id="21dde-126">Core services provide the default implementations for the system service interfaces, defined in the core package.</span></span>

<span data-ttu-id="21dde-127">MRTK Foundation include i servizi di sistema seguenti:</span><span class="sxs-lookup"><span data-stu-id="21dde-127">The MRTK foundation includes the following system services:</span></span>

- [<span data-ttu-id="21dde-128">Sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="21dde-128">Boundary System</span></span>](../features/Boundary/BoundarySystemGettingStarted.md)
- [<span data-ttu-id="21dde-129">Sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="21dde-129">Diagnostic System</span></span>](../features/Diagnostics/DiagnosticsSystemGettingStarted.md)
- [<span data-ttu-id="21dde-130">Sistema di input</span><span class="sxs-lookup"><span data-stu-id="21dde-130">Input System</span></span>](../features/Input/Overview.md)
- [<span data-ttu-id="21dde-131">Sistema di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="21dde-131">Spatial Awareness System</span></span>](../features/SpatialAwareness/SpatialAwarenessGettingStarted.md)
- [<span data-ttu-id="21dde-132">Sistema Teleport</span><span class="sxs-lookup"><span data-stu-id="21dde-132">Teleport System</span></span>](../features/TeleportSystem/Overview.md)

- <span data-ttu-id="21dde-133">**Asset funzionalità**</span><span class="sxs-lookup"><span data-stu-id="21dde-133">**Feature Assets**</span></span>

<span data-ttu-id="21dde-134">Gli asset di funzionalità sono raccolte di funzionalità correlate fornite come asset Unity e script, inclusi i controlli dell'interfaccia utente, gli asset standard e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="21dde-134">Feature Assets are collections of related functionality delivered as Unity assets and scripts including user interface controls, Standard assets, and more.</span></span>

## <a name="extensions-package"></a><span data-ttu-id="21dde-135">Pacchetto di estensioni</span><span class="sxs-lookup"><span data-stu-id="21dde-135">Extensions package</span></span>

<span data-ttu-id="21dde-136">Il pacchetto di estensioni contiene servizi e componenti aggiuntivi che estendono le funzionalità del pacchetto di base.</span><span class="sxs-lookup"><span data-stu-id="21dde-136">The extensions package contains additional services and components that extend the functionality of the foundation package.</span></span>

- [<span data-ttu-id="21dde-137">Servizio transizione scena</span><span class="sxs-lookup"><span data-stu-id="21dde-137">Scene Transition Service</span></span>](../features/Extensions/SceneTransitionService/SceneTransitionServiceOverview.md)

## <a name="examples-package"></a><span data-ttu-id="21dde-138">Pacchetto di esempi</span><span class="sxs-lookup"><span data-stu-id="21dde-138">Examples package</span></span>

<span data-ttu-id="21dde-139">Il pacchetto degli esempi contiene demo, script di esempio e scene di esempio che esercitano le funzionalità del pacchetto di base.</span><span class="sxs-lookup"><span data-stu-id="21dde-139">The examples package contains demos, sample scripts, and sample scenes that exercise functionality in the foundation package.</span></span> <span data-ttu-id="21dde-140">Questo pacchetto contiene la [scena HandInteractionExample](../features/README_HandInteractionExamples.md) (illustrata di seguito) che contiene oggetti di esempio che rispondono a diversi tipi di input della mano (articolati e non articolati).</span><span class="sxs-lookup"><span data-stu-id="21dde-140">This package contains the [HandInteractionExample scene](../features/README_HandInteractionExamples.md) (pictured below) which contains sample objects that respond to various types of hand input (articulated and non-articulated).</span></span>

![Scena HandInteractionExample](../features/Images/MRTK_Examples.png)

<span data-ttu-id="21dde-142">Questo pacchetto contiene anche le demo di rilevamento degli occhi, [documentate qui](../features/EyeTracking/EyeTracking_ExamplesOverview.md)</span><span class="sxs-lookup"><span data-stu-id="21dde-142">This package also contains eye tracking demos, which are [documented here](../features/EyeTracking/EyeTracking_ExamplesOverview.md)</span></span>

<span data-ttu-id="21dde-143">Più in generale, tutte le nuove funzionalità di MRTK devono contenere un esempio corrispondente nel pacchetto degli esempi, approssimativamente seguendo la stessa struttura di cartelle e la stessa posizione.</span><span class="sxs-lookup"><span data-stu-id="21dde-143">More generally, any new feature in the MRTK should contain a corresponding example in the examples package, roughly following the same folder structure and location.</span></span>

## <a name="tools-package"></a><span data-ttu-id="21dde-144">Pacchetto strumenti</span><span class="sxs-lookup"><span data-stu-id="21dde-144">Tools package</span></span>

<span data-ttu-id="21dde-145">Il pacchetto Tools contiene strumenti utili per la creazione di esperienze di realtà miste il cui codice non verrà fornito come parte di un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="21dde-145">The tools package contains tools that are useful for creating mixed reality experiences whose code will ultimately not ship as part of an application.</span></span>

- [<span data-ttu-id="21dde-146">Finestra dipendenze</span><span class="sxs-lookup"><span data-stu-id="21dde-146">Dependency Window</span></span>](../features/Tools/DependencyWindow.md)
- [<span data-ttu-id="21dde-147">Creazione guidata servizio di estensione</span><span class="sxs-lookup"><span data-stu-id="21dde-147">Extension Service Creation Wizard</span></span>](../features/Tools/ExtensionServiceCreationWizard.md)
- [<span data-ttu-id="21dde-148">Ottimizza finestra</span><span class="sxs-lookup"><span data-stu-id="21dde-148">Optimize Window</span></span>](../features/Tools/OptimizeWindow.md)
- [<span data-ttu-id="21dde-149">Utilità screenshot</span><span class="sxs-lookup"><span data-stu-id="21dde-149">Screenshot Utility</span></span>](../features/Tools/ScreenshotUtility.md)

## <a name="see-also"></a><span data-ttu-id="21dde-150">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="21dde-150">See also</span></span>

- [<span data-ttu-id="21dde-151">Panoramica dell'architettura</span><span class="sxs-lookup"><span data-stu-id="21dde-151">Architecture Overview</span></span>](../Architecture/Overview.md)
- [<span data-ttu-id="21dde-152">Sistemi, servizi di estensione e provider di dati</span><span class="sxs-lookup"><span data-stu-id="21dde-152">Systems, Extension Services and Data Providers</span></span>](../Architecture/SystemsExtensionsProviders.md)
