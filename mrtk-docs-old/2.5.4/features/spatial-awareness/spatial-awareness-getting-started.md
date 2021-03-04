---
title: SpatialAwareness
description: descrive la conoscenza spaziale in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 7a27f5eb63150b2521ea3471f50c2bbdeb886d90
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782747"
---
# <a name="spatial-awareness"></a><span data-ttu-id="cb3f9-104">Consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="cb3f9-104">Spatial Awareness</span></span>

![Consapevolezza spaziale](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

<span data-ttu-id="cb3f9-106">Il sistema di riconoscimento spaziale fornisce una reale consapevolezza ambientale nelle applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-106">The Spatial Awareness system provides real-world environmental awareness in mixed reality applications.</span></span> <span data-ttu-id="cb3f9-107">Quando introdotta in Microsoft HoloLens, la consapevolezza spaziale ha fornito una raccolta di mesh, che rappresenta la geometria dell'ambiente, che consentiva di interagire in modo interessante tra gli ologrammi e il mondo reale.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-107">When introduced on Microsoft HoloLens, Spatial Awareness provided a collection of meshes, representing the geometry of the environment, which allowed for compelling interactions between holograms and the real-world.</span></span>

> [!NOTE]
> <span data-ttu-id="cb3f9-108">A questo punto, il Toolkit di realtà mista non viene fornito con gli algoritmi di comprensione spaziale come originariamente confezionato in HoloToolkit.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-108">At this time, the Mixed Reality Toolkit does not ship with Spatial Understanding algorithms as originally packaged in the HoloToolkit.</span></span> <span data-ttu-id="cb3f9-109">La comprensione spaziale comporta in genere la trasformazione dei dati di rete spaziale per creare dati di mesh semplificati e/o raggruppati, ad esempio piani, muri, piani, soffitti e così via.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-109">Spatial Understanding generally involves transforming Spatial Mesh data to create simplified and/or grouped Mesh data such as planes, walls, floors, ceilings, etc.</span></span>

## <a name="getting-started"></a><span data-ttu-id="cb3f9-110">Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="cb3f9-110">Getting started</span></span>

<span data-ttu-id="cb3f9-111">L'aggiunta del supporto per la consapevolezza spaziale richiede due componenti chiave del Toolkit di realtà mista: il sistema di riconoscimento spaziale e un provider di piattaforme supportato.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-111">Adding support for Spatial Awareness requires two key components of the Mixed Reality Toolkit: the Spatial Awareness system and a supported platform provider.</span></span>

1. <span data-ttu-id="cb3f9-112">[Abilitare](#enable-the-spatial-awareness-system) il sistema di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="cb3f9-112">[Enable](#enable-the-spatial-awareness-system) the Spatial Awareness system</span></span>
2. <span data-ttu-id="cb3f9-113">[Registrare](#register-observers) e [configurare](configuring-spatial-awareness-mesh-observer.md) uno o più osservatori spaziali per fornire dati mesh</span><span class="sxs-lookup"><span data-stu-id="cb3f9-113">[Register](#register-observers) and [configure](configuring-spatial-awareness-mesh-observer.md) one or more spatial observers to provide mesh data</span></span>
3. <span data-ttu-id="cb3f9-114">[Compila e Distribuisci](#build-and-deploy) in una piattaforma che supporta la consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="cb3f9-114">[Build and deploy](#build-and-deploy) to a platform that supports Spatial Awareness</span></span>

### <a name="enable-the-spatial-awareness-system"></a><span data-ttu-id="cb3f9-115">Abilitare il sistema di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="cb3f9-115">Enable the spatial awareness system</span></span>

<span data-ttu-id="cb3f9-116">Il sistema di riconoscimento spaziale è gestito dall'oggetto MixedRealityToolkit (o da un altro componente di [registrazione del servizio](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).</span><span class="sxs-lookup"><span data-stu-id="cb3f9-116">The Spatial Awareness system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span> <span data-ttu-id="cb3f9-117">Attenersi alla procedura seguente per abilitare o disabilitare il *sistema di riconoscimento spaziale* nel profilo *MixedRealityToolkit* .</span><span class="sxs-lookup"><span data-stu-id="cb3f9-117">Follow the steps below to enable or disable the *Spatial Awareness system* in the *MixedRealityToolkit* profile.</span></span>

<span data-ttu-id="cb3f9-118">Il Toolkit di realtà misto viene fornito con alcuni profili preconfigurati predefiniti.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-118">The Mixed Reality Toolkit ships with a few default pre-configured profiles.</span></span> <span data-ttu-id="cb3f9-119">Per alcune di queste funzionalità il sistema di riconoscimento spaziale è abilitato o disabilitato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-119">Some of these have the Spatial Awareness system enabled OR disabled by default.</span></span> <span data-ttu-id="cb3f9-120">Lo scopo di questa pre-configurazione, in particolare per i casi in cui è disabilitato, è quello di evitare il sovraccarico visivo del calcolo e del rendering dei mesh.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-120">The intent of this pre-configuration, particularly for when disabled, is to avoid the visual overhead of calculating and rendering the meshes.</span></span>

| <span data-ttu-id="cb3f9-121">Profilo</span><span class="sxs-lookup"><span data-stu-id="cb3f9-121">Profile</span></span> | <span data-ttu-id="cb3f9-122">Sistema abilitato per impostazione predefinita</span><span class="sxs-lookup"><span data-stu-id="cb3f9-122">System Enabled by Default</span></span> |
| --- | --- |
| <span data-ttu-id="cb3f9-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span><span class="sxs-lookup"><span data-stu-id="cb3f9-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span></span> | <span data-ttu-id="cb3f9-124">Falso</span><span class="sxs-lookup"><span data-stu-id="cb3f9-124">False</span></span> |
| <span data-ttu-id="cb3f9-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span><span class="sxs-lookup"><span data-stu-id="cb3f9-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span></span> | <span data-ttu-id="cb3f9-126">Falso</span><span class="sxs-lookup"><span data-stu-id="cb3f9-126">False</span></span> |
| <span data-ttu-id="cb3f9-127">`DefaultMixedRealityToolkitConfigurationProfile` (Asset/MRTK/SDK/profili)</span><span class="sxs-lookup"><span data-stu-id="cb3f9-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)</span></span> | <span data-ttu-id="cb3f9-128">Vero</span><span class="sxs-lookup"><span data-stu-id="cb3f9-128">True</span></span> |

1. <span data-ttu-id="cb3f9-129">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena per aprirlo nel pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-129">Select the MixedRealityToolkit object in the scene hierarchy to open in the Inspector Panel.</span></span>

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="cb3f9-131">Passare alla sezione *sistema di riconoscimento spaziale* e selezionare *Abilita sistema di riconoscimento spaziale*</span><span class="sxs-lookup"><span data-stu-id="cb3f9-131">Navigate to the *Spatial Awareness System* section and check *Enable Spatial Awareness System*</span></span>

    ![Abilita consapevolezza spaziale](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. <span data-ttu-id="cb3f9-133">Selezionare il tipo di implementazione del sistema di riconoscimento spaziale desiderato.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-133">Select the desired Spatial Awareness system implementation type.</span></span> <span data-ttu-id="cb3f9-134">[`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem)È il valore predefinito specificato.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-134">The [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) is the default provided.</span></span>

    ![Selezionare l'implementazione del sistema di riconoscimento spaziale](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a><span data-ttu-id="cb3f9-136">Registrare gli osservatori</span><span class="sxs-lookup"><span data-stu-id="cb3f9-136">Register observers</span></span>

<span data-ttu-id="cb3f9-137">I servizi nel Toolkit per la realtà mista possono avere [provider di dati Servizi](../../architecture/systems-extensions-providers.md) che integrano il servizio principale con i controlli di implementazione e i dati specifici della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-137">Services in the Mixed Reality Toolkit can have [Data Provider services](../../architecture/systems-extensions-providers.md) that supplement the main service with platform specific data and implementation controls.</span></span> <span data-ttu-id="cb3f9-138">Un esempio è il sistema di input della realtà mista che dispone di [più provider di dati](../input/input-providers.md) per ottenere il controller e altre informazioni di input correlate da diverse API specifiche della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-138">An example of this is the Mixed Reality Input System which has [multiple data providers](../input/input-providers.md) to get controller and other related input information from various platform-specific APIs.</span></span>

<span data-ttu-id="cb3f9-139">Il sistema di riconoscimento spaziale è simile in quanto i provider di dati forniscono al sistema i dati di rete sul mondo reale.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-139">The Spatial Awareness system is similar in that data providers supply the system with mesh data about the real-world.</span></span> <span data-ttu-id="cb3f9-140">Il profilo di riconoscimento spaziale deve avere almeno un osservatore spaziale registrato.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-140">The Spatial Awareness profile must have at least one Spatial Observer registered.</span></span> <span data-ttu-id="cb3f9-141">Gli osservatori spaziali sono in genere componenti specifici della piattaforma che fungono da provider per l'emersione di diversi tipi di dati mesh da un endpoint specifico della piattaforma (ad esempio</span><span class="sxs-lookup"><span data-stu-id="cb3f9-141">Spatial Observers are generally platform specific components that act as the provider for surfacing various types of mesh data from a platform specific endpoint (i.e</span></span> <span data-ttu-id="cb3f9-142">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="cb3f9-142">HoloLens).</span></span>

1. <span data-ttu-id="cb3f9-143">Aprire o espandere il *profilo di sistema di riconoscimento spaziale*</span><span class="sxs-lookup"><span data-stu-id="cb3f9-143">Open or expand the *Spatial Awareness System profile*</span></span>

    ![Profilo del sistema di riconoscimento spaziale](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. <span data-ttu-id="cb3f9-145">Fai clic sul pulsante *"Aggiungi osservatore spaziale"*</span><span class="sxs-lookup"><span data-stu-id="cb3f9-145">Click the *"Add Spatial Observer"* button</span></span>
1. <span data-ttu-id="cb3f9-146">Selezionare il *tipo di implementazione dell'osservatore spaziale* desiderato</span><span class="sxs-lookup"><span data-stu-id="cb3f9-146">Select the desired *Spatial Observer implementation type*</span></span>

    ![Selezionare l'implementazione dell'osservatore spaziale](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. <span data-ttu-id="cb3f9-148">[Modificare le proprietà di configurazione nell'Observer](configuring-spatial-awareness-mesh-observer.md) se necessario</span><span class="sxs-lookup"><span data-stu-id="cb3f9-148">[Modify configuration properties on the observer](configuring-spatial-awareness-mesh-observer.md) as necessary</span></span>

> [!NOTE]
> <span data-ttu-id="cb3f9-149">Gli utenti di `DefaultMixedRealityToolkitConfigurationProfile` (assets/MRTK/SDK/Profiles) avranno il sistema di riconoscimento spaziale preconfigurato per la piattaforma di realtà mista di Windows che usa la [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) classe.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-149">Users of the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) will have the Spatial Awareness system pre-configured for the Windows Mixed Reality platform which uses the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="cb3f9-150">Eseguire la compilazione e la distribuzione</span><span class="sxs-lookup"><span data-stu-id="cb3f9-150">Build and deploy</span></span>

<span data-ttu-id="cb3f9-151">Quando il sistema di riconoscimento spaziale viene configurato con gli osservatori desiderati, il progetto può essere compilato e distribuito nella piattaforma di destinazione.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-151">Once the Spatial Awareness system is configured with the desired observer(s), the project can be built and deployed to the target platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb3f9-152">Se la destinazione è la piattaforma di realtà mista di Windows (ad esempio, HoloLens), è importante assicurarsi che la [funzionalità di percezione spaziale](https://docs.microsoft.com/windows/mixed-reality/spatial-mapping-in-unity) sia abilitata per poter usare il sistema di riconoscimento spaziale sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-152">If targeting the Windows Mixed Reality platform (ex: HoloLens), it is important to ensure the [Spatial Perception capability](https://docs.microsoft.com/windows/mixed-reality/spatial-mapping-in-unity) is enabled in order to use the Spatial Awareness system on device.</span></span>

> [!WARNING]
> <span data-ttu-id="cb3f9-153">Alcune piattaforme, tra cui Microsoft HoloLens, forniscono supporto per l'esecuzione remota dall'interno di Unity.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-153">Some platforms, including Microsoft HoloLens, provide support for remote execution from within Unity.</span></span> <span data-ttu-id="cb3f9-154">Questa funzionalità consente lo sviluppo e i test rapidi senza richiedere la fase di compilazione e distribuzione.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-154">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="cb3f9-155">Assicurarsi di eseguire test di accettazione finali usando una versione compilata e distribuita dell'applicazione, in esecuzione nell'hardware e nella piattaforma di destinazione.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-155">Be sure to do final acceptance testing using a built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cb3f9-156">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="cb3f9-156">Next steps</span></span>

<span data-ttu-id="cb3f9-157">Dopo aver seguito le procedure riportate sopra per abilitare il sistema di riconoscimento spaziale, il sistema può essere configurato e controllato in modo più dettagliato.</span><span class="sxs-lookup"><span data-stu-id="cb3f9-157">After following the procedures above to enable the Spatial Awareness system, the system can be configured and controlled in more detail.</span></span>

<span data-ttu-id="cb3f9-158">Informazioni per la configurazione degli osservatori in Inspector:</span><span class="sxs-lookup"><span data-stu-id="cb3f9-158">Information for configuring observers in inspector:</span></span>

- [<span data-ttu-id="cb3f9-159">Configurazione degli Observer per l'utilizzo del dispositivo</span><span class="sxs-lookup"><span data-stu-id="cb3f9-159">Configuring Observers for on device usage</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="cb3f9-160">Configurazione degli osservatori per l'utilizzo in-Editor</span><span class="sxs-lookup"><span data-stu-id="cb3f9-160">Configuring Observers for in-editor usage</span></span>](spatial-object-mesh-observer.md)

<span data-ttu-id="cb3f9-161">Informazioni per il controllo e l'estensione degli osservatori tramite codice:</span><span class="sxs-lookup"><span data-stu-id="cb3f9-161">Information for controlling and extending observers via code:</span></span>

- [<span data-ttu-id="cb3f9-162">Configurazione di osservatori tramite codice</span><span class="sxs-lookup"><span data-stu-id="cb3f9-162">Configuring Observers via Code</span></span>](usage-guide.md)
- [<span data-ttu-id="cb3f9-163">Creazione di un Observer personalizzato</span><span class="sxs-lookup"><span data-stu-id="cb3f9-163">Creating a custom Observer</span></span>](create-data-provider.md)

## <a name="see-also"></a><span data-ttu-id="cb3f9-164">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="cb3f9-164">See also</span></span>

- [<span data-ttu-id="cb3f9-165">Documentazione dell'API di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="cb3f9-165">Spatial Awareness API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [<span data-ttu-id="cb3f9-166">Panoramica del mapping spaziale WMR</span><span class="sxs-lookup"><span data-stu-id="cb3f9-166">Spatial Mapping Overview WMR</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-mapping)
- [<span data-ttu-id="cb3f9-167">Mapping spaziale in Unity WMR</span><span class="sxs-lookup"><span data-stu-id="cb3f9-167">Spatial Mapping in Unity WMR</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-mapping-in-unity)
