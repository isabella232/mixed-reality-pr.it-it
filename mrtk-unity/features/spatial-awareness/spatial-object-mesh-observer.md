---
title: Osservatore mesh oggetto spaziale
description: Documentazione su Spatial Mesh Observer in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 51963fca4fa76340089b84e400f2882763977f72
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144454"
---
# <a name="configuring-mesh-observers-for-the-editor"></a><span data-ttu-id="fb43c-104">Configurazione degli osservatori mesh per l'editor</span><span class="sxs-lookup"><span data-stu-id="fb43c-104">Configuring mesh observers for the editor</span></span>

<span data-ttu-id="fb43c-105">Un modo pratico per fornire i dati della mesh dell'ambiente nell'editor di Unity è usare la [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe .</span><span class="sxs-lookup"><span data-stu-id="fb43c-105">A convenient way to provide environment mesh data in the Unity editor is to use the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class.</span></span> <span data-ttu-id="fb43c-106">*Spatial Object Mesh Observer è* un provider di dati solo editor per il sistema [di](spatial-awareness-getting-started.md) consapevolezza spaziale che consente di importare dati del modello 3D per rappresentare una mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="fb43c-106">The *Spatial Object Mesh Observer* is an editor-only data provider for the [Spatial Awareness system](spatial-awareness-getting-started.md) that enables importing 3D model data to represent a spatial mesh.</span></span> <span data-ttu-id="fb43c-107">Un uso comune di *Spatial Object Mesh Observer* è quello di importare i dati analizzati tramite un Microsoft HoloLens per testare come un'esperienza si adatta a ambienti diversi dall'interno di Unity.</span><span class="sxs-lookup"><span data-stu-id="fb43c-107">One common use of the *Spatial Object Mesh Observer* is to import data scanned via a Microsoft HoloLens to test how an experience adapts to different environments from within Unity.</span></span>

## <a name="getting-started"></a><span data-ttu-id="fb43c-108">Per iniziare</span><span class="sxs-lookup"><span data-stu-id="fb43c-108">Getting started</span></span>

<span data-ttu-id="fb43c-109">In questa guida verrà illustrata la configurazione di *un osservatore spatial object mesh*.</span><span class="sxs-lookup"><span data-stu-id="fb43c-109">This guide will walk through setting up a *Spatial Object Mesh Observer*.</span></span> <span data-ttu-id="fb43c-110">Per abilitare questa funzionalità, è necessario eseguire tre passaggi chiave.</span><span class="sxs-lookup"><span data-stu-id="fb43c-110">There are three key steps to enable this feature.</span></span>

1. <span data-ttu-id="fb43c-111">Aggiungere un *osservatore di mesh di oggetti spaziali* al profilo di sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="fb43c-111">Add a *Spatial Object Mesh Observer* to the Spatial Awareness system profile</span></span>
1. <span data-ttu-id="fb43c-112">Impostare l'oggetto Dati mesh dell'ambiente</span><span class="sxs-lookup"><span data-stu-id="fb43c-112">Set the Environment Mesh Data object</span></span>
1. [<span data-ttu-id="fb43c-113">Configurare le altre proprietà del profilo di Mesh Observer</span><span class="sxs-lookup"><span data-stu-id="fb43c-113">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a><span data-ttu-id="fb43c-114">Configurare un profilo *osservatore mesh di oggetti spaziali*</span><span class="sxs-lookup"><span data-stu-id="fb43c-114">Set up a *spatial object mesh observer* profile</span></span>

1. <span data-ttu-id="fb43c-115">Selezionare il profilo di *configurazione di Mixed Reality Toolkit* desiderato o selezionare l'oggetto Mixed Reality *Toolkit* nella scena</span><span class="sxs-lookup"><span data-stu-id="fb43c-115">Select the desired *Mixed Reality Toolkit* configuration profile or select the *Mixed Reality Toolkit* object in scene</span></span>
1. <span data-ttu-id="fb43c-116">Aprire o espandere la *scheda Sistema di consapevolezza* spaziale</span><span class="sxs-lookup"><span data-stu-id="fb43c-116">Open or expand the *Spatial Awareness System* tab</span></span>
1. <span data-ttu-id="fb43c-117">Fare clic sul *pulsante "Aggiungi osservatore spaziale"*</span><span class="sxs-lookup"><span data-stu-id="fb43c-117">Click on *"Add Spatial Observer"* button</span></span>

    ![Aggiungere un osservatore spaziale](../images/spatial-awareness/AddObserver.png)

1. <span data-ttu-id="fb43c-119">Selezionare il *tipo SpatialObjectMeshObserver*</span><span class="sxs-lookup"><span data-stu-id="fb43c-119">Select the *SpatialObjectMeshObserver* type</span></span>

    ![Selezionare l'osservatore mesh di oggetti spaziali](../images/spatial-awareness/SelectObjectObserver.png)

1. <span data-ttu-id="fb43c-121">Selezionare *l'oggetto mesh spaziale desiderato.*</span><span class="sxs-lookup"><span data-stu-id="fb43c-121">Select the desired *Spatial Mesh Object*.</span></span> <span data-ttu-id="fb43c-122">Per impostazione predefinita, l'osservatore è configurato con un modello di esempio.</span><span class="sxs-lookup"><span data-stu-id="fb43c-122">By default, the observer is configured with an example model.</span></span> <span data-ttu-id="fb43c-123">Questo modello è stato creato usando un Microsoft HoloLens ma è possibile creare un nuovo [oggetto mesh di analisi](#acquiring-environment-scans).</span><span class="sxs-lookup"><span data-stu-id="fb43c-123">This model was created using a Microsoft HoloLens but it is possible to [create a new scan mesh object](#acquiring-environment-scans).</span></span>
1. [<span data-ttu-id="fb43c-124">Configurare il resto delle proprietà del profilo osservatore mesh</span><span class="sxs-lookup"><span data-stu-id="fb43c-124">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

    ![Selezionare l'oggetto Mesh](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a><span data-ttu-id="fb43c-126">Note sul profilo osservatore della mesh di oggetti spaziali</span><span class="sxs-lookup"><span data-stu-id="fb43c-126">Spatial object mesh observer profile notes</span></span>

<span data-ttu-id="fb43c-127">Poiché *Spatial Object Mesh Observer* carica i dati da un modello 3D, non rispetta alcune delle impostazioni dell'osservatore mesh standard descritte di seguito.</span><span class="sxs-lookup"><span data-stu-id="fb43c-127">Since the *Spatial Object Mesh Observer* loads data from a 3D model, it does not honor some of the standard mesh observer settings which are outlined below.</span></span>

<span data-ttu-id="fb43c-128">**Intervallo di aggiornamento**</span><span class="sxs-lookup"><span data-stu-id="fb43c-128">**Update Interval**</span></span>

<span data-ttu-id="fb43c-129">Spatial  *Object Mesh Observer* invia tutte le mesh a un'applicazione quando viene caricato il modello.</span><span class="sxs-lookup"><span data-stu-id="fb43c-129">The  *Spatial Object Mesh Observer* sends all meshes to an application when the model is loaded.</span></span> <span data-ttu-id="fb43c-130">Non simula i delta di tempo tra gli aggiornamenti.</span><span class="sxs-lookup"><span data-stu-id="fb43c-130">It does not simulate time deltas between updates.</span></span> <span data-ttu-id="fb43c-131">Un'applicazione può ricevere nuovamente gli eventi mesh chiamando [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) e [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .</span><span class="sxs-lookup"><span data-stu-id="fb43c-131">An application can re-receive the mesh events by calling [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) and [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume).</span></span>

<span data-ttu-id="fb43c-132">**Is Stationary Observer**</span><span class="sxs-lookup"><span data-stu-id="fb43c-132">**Is Stationary Observer**</span></span>

<span data-ttu-id="fb43c-133">Spatial *Object Mesh Observer* considera tutti gli oggetti mesh 3D stazionari e ignora l'origine.</span><span class="sxs-lookup"><span data-stu-id="fb43c-133">The *Spatial Object Mesh Observer* considers all 3D mesh objects to be stationary and disregards origin.</span></span>

<span data-ttu-id="fb43c-134">**Forma ed extent dell'osservatore**</span><span class="sxs-lookup"><span data-stu-id="fb43c-134">**Observer Shape and Extents**</span></span>

<span data-ttu-id="fb43c-135">Spatial  *Object Mesh Observer* invia l'intera mesh 3D all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="fb43c-135">The  *Spatial Object Mesh Observer* sends the entire 3D mesh to the application.</span></span> <span data-ttu-id="fb43c-136">La forma e gli extent dell'osservatore non vengono considerati.</span><span class="sxs-lookup"><span data-stu-id="fb43c-136">Observer shape and extents are not considered.</span></span>

<span data-ttu-id="fb43c-137">**Livello di dettaglio e triangoli/contatore cubico**</span><span class="sxs-lookup"><span data-stu-id="fb43c-137">**Level of Detail and Triangles / Cubic Meter**</span></span>

<span data-ttu-id="fb43c-138">Observer non tenta di trovare gli ID modello 3D durante l'invio delle mesh all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="fb43c-138">The Observer does not attempt to find 3D model LODs when sending the meshes to the application.</span></span>

## <a name="acquiring-environment-scans"></a><span data-ttu-id="fb43c-139">Acquisizione di analisi dell'ambiente</span><span class="sxs-lookup"><span data-stu-id="fb43c-139">Acquiring environment scans</span></span>

<span data-ttu-id="fb43c-140">Questa sezione descrive informazioni aggiuntive per creare e raccogliere file *oggetto mesh* spaziale da usare con Spatial Object *Mesh Observer.*</span><span class="sxs-lookup"><span data-stu-id="fb43c-140">This section outlines additional information to create and gather *Spatial Mesh Object* files for use with the *Spatial Object Mesh Observer*.</span></span>

### <a name="windows-device-portal"></a><span data-ttu-id="fb43c-141">Portale di dispositivi di Windows</span><span class="sxs-lookup"><span data-stu-id="fb43c-141">Windows Device Portal</span></span>

<span data-ttu-id="fb43c-142">Il [Portale di dispositivi di Windows](/windows/mixed-reality/using-the-windows-device-portal) può essere usato per scaricare la mesh spaziale, come file obj, da un Microsoft HoloLens dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fb43c-142">The [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) can be used to download the spatial mesh, as a .obj file, from a Microsoft HoloLens device.</span></span>

1. <span data-ttu-id="fb43c-143">Eseguire l'analisi semplicemente a piedi e visualizzare l'ambiente desiderato con un holoLens</span><span class="sxs-lookup"><span data-stu-id="fb43c-143">Scan by simply walking and viewing the desired environment with a HoloLens</span></span>
1. <span data-ttu-id="fb43c-144">Connettersi a HoloLens usando il Portale di dispositivi di Windows</span><span class="sxs-lookup"><span data-stu-id="fb43c-144">Connect to the HoloLens using the Windows Device Portal</span></span>
1. <span data-ttu-id="fb43c-145">Passare alla *pagina Visualizzazione 3D*</span><span class="sxs-lookup"><span data-stu-id="fb43c-145">Navigate to the *3D View* page</span></span>
1. <span data-ttu-id="fb43c-146">Fare clic *sul pulsante* Aggiorna nella *sezione Mapping* spaziale</span><span class="sxs-lookup"><span data-stu-id="fb43c-146">Click the *Update* button under *Spatial Mapping* section</span></span>
1. <span data-ttu-id="fb43c-147">Fare clic *sul pulsante* Salva nella *sezione Mapping* spaziale per salvare il file obj nel PC</span><span class="sxs-lookup"><span data-stu-id="fb43c-147">Click the *Save* button under *Spatial Mapping* section to save the obj file to PC</span></span>

> [!NOTE]
> <span data-ttu-id="fb43c-148">**File con estensione room di HoloToolkit**</span><span class="sxs-lookup"><span data-stu-id="fb43c-148">**HoloToolkit .room files**</span></span>
>
> <span data-ttu-id="fb43c-149">Molti sviluppatori hanno usato in precedenza HoloToolkit per analizzare gli ambienti e creare file con estensione room.</span><span class="sxs-lookup"><span data-stu-id="fb43c-149">Many developers will have previously used HoloToolkit to scan environments and create .room files.</span></span> <span data-ttu-id="fb43c-150">Mixed Reality Toolkit supporta ora l'importazione di questi file come GameObject in Unity e li usa come *oggetti mesh spaziali* nell'osservatore.</span><span class="sxs-lookup"><span data-stu-id="fb43c-150">The Mixed Reality Toolkit now supports importing these files as GameObjects in Unity and use them as *Spatial Mesh Objects* in the observer.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb43c-151">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="fb43c-151">See also</span></span>

- [<span data-ttu-id="fb43c-152">Profili</span><span class="sxs-lookup"><span data-stu-id="fb43c-152">Profiles</span></span>](../profiles/profiles.md)
- [<span data-ttu-id="fb43c-153">Guida alla configurazione del profilo di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="fb43c-153">Mixed Reality Toolkit Profile configuration guide</span></span>](../../configuration/mixed-reality-configuration-guide.md)
- [<span data-ttu-id="fb43c-154">Introduzione alla consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="fb43c-154">Spatial Awareness Getting started</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="fb43c-155">Configurazione degli osservatori mesh nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="fb43c-155">Configuring Mesh Observers on Device</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="fb43c-156">Configurazione degli osservatori mesh tramite codice</span><span class="sxs-lookup"><span data-stu-id="fb43c-156">Configuring Mesh Observers via code</span></span>](usage-guide.md)
- [<span data-ttu-id="fb43c-157">Avviare il Portale di dispositivi di Windows</span><span class="sxs-lookup"><span data-stu-id="fb43c-157">Using the Windows Device Portal</span></span>](/windows/mixed-reality/using-the-windows-device-portal)