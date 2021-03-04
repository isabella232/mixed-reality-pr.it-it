---
title: SpatialObjectMeshObserver
description: Documentazione sull'osservatore mesh spaziale in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: ab95878b62d4ee805e0445833db5e900425c912e
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782418"
---
# <a name="configuring-mesh-observers-for-the-editor"></a><span data-ttu-id="852df-104">Configurazione degli osservatori mesh per l'editor</span><span class="sxs-lookup"><span data-stu-id="852df-104">Configuring mesh observers for the editor</span></span>

<span data-ttu-id="852df-105">Un modo pratico per fornire i dati di rete dell'ambiente nell'editor di Unity consiste nell'usare la [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe.</span><span class="sxs-lookup"><span data-stu-id="852df-105">A convenient way to provide environment mesh data in the Unity editor is to use the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class.</span></span> <span data-ttu-id="852df-106">L' *osservatore mesh di oggetti spaziali* è un provider di dati solo editor per il [sistema di riconoscimento spaziale](SpatialAwarenessGettingStarted.md) che consente di importare i dati del modello 3D per rappresentare una mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="852df-106">The *Spatial Object Mesh Observer* is an editor-only data provider for the [Spatial Awareness system](SpatialAwarenessGettingStarted.md) that enables importing 3D model data to represent a spatial mesh.</span></span> <span data-ttu-id="852df-107">Un uso comune dell' *osservatore mesh di oggetti spaziali* consiste nell'importare i dati analizzati tramite un HoloLens Microsoft per testare il modo in cui un'esperienza si adatta a diversi ambienti da Unity.</span><span class="sxs-lookup"><span data-stu-id="852df-107">One common use of the *Spatial Object Mesh Observer* is to import data scanned via a Microsoft HoloLens to test how an experience adapts to different environments from within Unity.</span></span>

## <a name="getting-started"></a><span data-ttu-id="852df-108">Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="852df-108">Getting started</span></span>

<span data-ttu-id="852df-109">In questa guida viene illustrata la configurazione di un *Observer mesh di oggetti spaziali*.</span><span class="sxs-lookup"><span data-stu-id="852df-109">This guide will walk through setting up a *Spatial Object Mesh Observer*.</span></span> <span data-ttu-id="852df-110">Per abilitare questa funzionalità, è necessario eseguire tre passaggi principali.</span><span class="sxs-lookup"><span data-stu-id="852df-110">There are three key steps to enable this feature.</span></span>

1. <span data-ttu-id="852df-111">Aggiungere un *Observer mesh di oggetti spaziali* al profilo del sistema di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="852df-111">Add a *Spatial Object Mesh Observer* to the Spatial Awareness system profile</span></span>
1. <span data-ttu-id="852df-112">Impostare l'oggetto dati mesh ambiente</span><span class="sxs-lookup"><span data-stu-id="852df-112">Set the Environment Mesh Data object</span></span>
1. [<span data-ttu-id="852df-113">Configurare il resto delle proprietà del profilo osservatore mesh</span><span class="sxs-lookup"><span data-stu-id="852df-113">Configure rest of the Mesh Observer profile properties</span></span>](ConfiguringSpatialAwarenessMeshObserver.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a><span data-ttu-id="852df-114">Configurare un profilo *osservatore mesh oggetto spaziale*</span><span class="sxs-lookup"><span data-stu-id="852df-114">Set up a *spatial object mesh observer* profile</span></span>

1. <span data-ttu-id="852df-115">Selezionare il profilo di configurazione del *Toolkit di realtà mista* desiderato o selezionare l'oggetto del *Toolkit di realtà mista* in scena</span><span class="sxs-lookup"><span data-stu-id="852df-115">Select the desired *Mixed Reality Toolkit* configuration profile or select the *Mixed Reality Toolkit* object in scene</span></span>
1. <span data-ttu-id="852df-116">Aprire o espandere la scheda *sistema di riconoscimento spaziale*</span><span class="sxs-lookup"><span data-stu-id="852df-116">Open or expand the *Spatial Awareness System* tab</span></span>
1. <span data-ttu-id="852df-117">Fai clic sul pulsante *"Aggiungi osservatore spaziale"*</span><span class="sxs-lookup"><span data-stu-id="852df-117">Click on *"Add Spatial Observer"* button</span></span>

    ![Aggiungi osservatore spaziale](../images/spatial-awareness/AddObserver.png)

1. <span data-ttu-id="852df-119">Selezionare il tipo di *SpatialObjectMeshObserver*</span><span class="sxs-lookup"><span data-stu-id="852df-119">Select the *SpatialObjectMeshObserver* type</span></span>

    ![Seleziona osservatore mesh oggetto spaziale](../images/spatial-awareness/SelectObjectObserver.png)

1. <span data-ttu-id="852df-121">Selezionare l' *oggetto mesh spaziale* desiderato.</span><span class="sxs-lookup"><span data-stu-id="852df-121">Select the desired *Spatial Mesh Object*.</span></span> <span data-ttu-id="852df-122">Per impostazione predefinita, l'Observer viene configurato con un modello di esempio.</span><span class="sxs-lookup"><span data-stu-id="852df-122">By default, the observer is configured with an example model.</span></span> <span data-ttu-id="852df-123">Questo modello è stato creato usando un HoloLens Microsoft, ma è possibile [creare un nuovo oggetto mesh di analisi](#acquiring-environment-scans).</span><span class="sxs-lookup"><span data-stu-id="852df-123">This model was created using a Microsoft HoloLens but it is possible to [create a new scan mesh object](#acquiring-environment-scans).</span></span>
1. [<span data-ttu-id="852df-124">Configurare il resto delle proprietà del profilo osservatore mesh</span><span class="sxs-lookup"><span data-stu-id="852df-124">Configure rest of the Mesh Observer profile properties</span></span>](ConfiguringSpatialAwarenessMeshObserver.md)

    ![Selezionare l'oggetto mesh](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a><span data-ttu-id="852df-126">Note del profilo osservatore mesh oggetto spaziale</span><span class="sxs-lookup"><span data-stu-id="852df-126">Spatial object mesh observer profile notes</span></span>

<span data-ttu-id="852df-127">Poiché l' *osservatore mesh di oggetti spaziali* carica i dati da un modello 3D, non rispetta alcune delle impostazioni standard dell'Observer mesh descritte di seguito.</span><span class="sxs-lookup"><span data-stu-id="852df-127">Since the *Spatial Object Mesh Observer* loads data from a 3D model, it does not honor some of the standard mesh observer settings which are outlined below.</span></span>

<span data-ttu-id="852df-128">**Intervallo di aggiornamento**</span><span class="sxs-lookup"><span data-stu-id="852df-128">**Update Interval**</span></span>

<span data-ttu-id="852df-129">L'  *osservatore mesh di oggetti spaziali* Invia tutte le mesh a un'applicazione quando il modello viene caricato.</span><span class="sxs-lookup"><span data-stu-id="852df-129">The  *Spatial Object Mesh Observer* sends all meshes to an application when the model is loaded.</span></span> <span data-ttu-id="852df-130">Non simula i Delta temporali tra gli aggiornamenti.</span><span class="sxs-lookup"><span data-stu-id="852df-130">It does not simulate time deltas between updates.</span></span> <span data-ttu-id="852df-131">Un'applicazione può ricevere nuovamente gli eventi mesh chiamando [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) e [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .</span><span class="sxs-lookup"><span data-stu-id="852df-131">An application can re-receive the mesh events by calling [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) and [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume).</span></span>

<span data-ttu-id="852df-132">**Osservatore stazionario**</span><span class="sxs-lookup"><span data-stu-id="852df-132">**Is Stationary Observer**</span></span>

<span data-ttu-id="852df-133">L' *osservatore mesh oggetto spaziale* considera tutti gli oggetti mesh 3D come stazionari e non considera l'origine.</span><span class="sxs-lookup"><span data-stu-id="852df-133">The *Spatial Object Mesh Observer* considers all 3D mesh objects to be stationary and disregards origin.</span></span>

<span data-ttu-id="852df-134">**Forma ed extent dell'Observer**</span><span class="sxs-lookup"><span data-stu-id="852df-134">**Observer Shape and Extents**</span></span>

<span data-ttu-id="852df-135">L'  *osservatore mesh di oggetti spaziali* invia l'intera mesh 3D all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="852df-135">The  *Spatial Object Mesh Observer* sends the entire 3D mesh to the application.</span></span> <span data-ttu-id="852df-136">Gli extent e la forma Observer non vengono considerati.</span><span class="sxs-lookup"><span data-stu-id="852df-136">Observer shape and extents are not considered.</span></span>

<span data-ttu-id="852df-137">**Livello di dettaglio e triangoli/misuratore cubico**</span><span class="sxs-lookup"><span data-stu-id="852df-137">**Level of Detail and Triangles / Cubic Meter**</span></span>

<span data-ttu-id="852df-138">L'Observer non tenta di trovare il modello 3D LODs quando invia le mesh all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="852df-138">The Observer does not attempt to find 3D model LODs when sending the meshes to the application.</span></span>

## <a name="acquiring-environment-scans"></a><span data-ttu-id="852df-139">Acquisizione di analisi dell'ambiente</span><span class="sxs-lookup"><span data-stu-id="852df-139">Acquiring environment scans</span></span>

<span data-ttu-id="852df-140">In questa sezione vengono descritte informazioni aggiuntive per la creazione e la raccolta di file di *oggetti mesh spaziali* da utilizzare con l' *osservatore mesh di oggetti spaziali*.</span><span class="sxs-lookup"><span data-stu-id="852df-140">This section outlines additional information to create and gather *Spatial Mesh Object* files for use with the *Spatial Object Mesh Observer*.</span></span>

### <a name="windows-device-portal"></a><span data-ttu-id="852df-141">Portale di dispositivi di Windows</span><span class="sxs-lookup"><span data-stu-id="852df-141">Windows Device Portal</span></span>

<span data-ttu-id="852df-142">Il [portale per dispositivi Windows](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) può essere usato per scaricare la mesh spaziale, come file con estensione obj, da un dispositivo HoloLens Microsoft.</span><span class="sxs-lookup"><span data-stu-id="852df-142">The [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) can be used to download the spatial mesh, as a .obj file, from a Microsoft HoloLens device.</span></span>

1. <span data-ttu-id="852df-143">Eseguire un'analisi semplicemente e visualizzare l'ambiente desiderato con un HoloLens</span><span class="sxs-lookup"><span data-stu-id="852df-143">Scan by simply walking and viewing the desired environment with a HoloLens</span></span>
1. <span data-ttu-id="852df-144">Connettersi a HoloLens tramite il portale del dispositivo Windows</span><span class="sxs-lookup"><span data-stu-id="852df-144">Connect to the HoloLens using the Windows Device Portal</span></span>
1. <span data-ttu-id="852df-145">Passa alla pagina della *visualizzazione 3D*</span><span class="sxs-lookup"><span data-stu-id="852df-145">Navigate to the *3D View* page</span></span>
1. <span data-ttu-id="852df-146">Fare clic sul pulsante *Aggiorna* in sezione *mapping spaziale*</span><span class="sxs-lookup"><span data-stu-id="852df-146">Click the *Update* button under *Spatial Mapping* section</span></span>
1. <span data-ttu-id="852df-147">Fare clic sul pulsante *Salva* nella sezione *mapping spaziale* per salvare il file obj sul PC</span><span class="sxs-lookup"><span data-stu-id="852df-147">Click the *Save* button under *Spatial Mapping* section to save the obj file to PC</span></span>

> [!NOTE]
> <span data-ttu-id="852df-148">**File HoloToolkit. room**</span><span class="sxs-lookup"><span data-stu-id="852df-148">**HoloToolkit .room files**</span></span>
>
> <span data-ttu-id="852df-149">Molti sviluppatori utilizzeranno in precedenza HoloToolkit per analizzare gli ambienti e creare file con estensione room.</span><span class="sxs-lookup"><span data-stu-id="852df-149">Many developers will have previously used HoloToolkit to scan environments and create .room files.</span></span> <span data-ttu-id="852df-150">Il Toolkit di realtà mista supporta ora l'importazione di questi file come GameObject in Unity e li usa come *oggetti mesh spaziali* nell'Observer.</span><span class="sxs-lookup"><span data-stu-id="852df-150">The Mixed Reality Toolkit now supports importing these files as GameObjects in Unity and use them as *Spatial Mesh Objects* in the observer.</span></span>

## <a name="see-also"></a><span data-ttu-id="852df-151">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="852df-151">See also</span></span>

- [<span data-ttu-id="852df-152">Profili</span><span class="sxs-lookup"><span data-stu-id="852df-152">Profiles</span></span>](../profiles/Profiles.md)
- [<span data-ttu-id="852df-153">Guida alla configurazione del profilo del Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="852df-153">Mixed Reality Toolkit Profile configuration guide</span></span>](../../configuration/MixedRealityConfigurationGuide.md)
- [<span data-ttu-id="852df-154">Introduzione a consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="852df-154">Spatial Awareness Getting started</span></span>](SpatialAwarenessGettingStarted.md)
- [<span data-ttu-id="852df-155">Configurazione degli osservatori mesh nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="852df-155">Configuring Mesh Observers on Device</span></span>](ConfiguringSpatialAwarenessMeshObserver.md)
- [<span data-ttu-id="852df-156">Configurazione di osservatori mesh tramite codice</span><span class="sxs-lookup"><span data-stu-id="852df-156">Configuring Mesh Observers via code</span></span>](UsageGuide.md)
- [<span data-ttu-id="852df-157">Avviare il Portale di dispositivi di Windows</span><span class="sxs-lookup"><span data-stu-id="852df-157">Using the Windows Device Portal</span></span>](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal)
