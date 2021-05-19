---
title: Consapevolezza spaziale
description: descrive la consapevolezza spaziale in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 776033dbb4736ccaa44cdb683c4fce284758a51c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144467"
---
# <a name="spatial-awareness"></a><span data-ttu-id="8411c-104">Consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="8411c-104">Spatial Awareness</span></span>

![Consapevolezza spaziale](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

<span data-ttu-id="8411c-106">Il sistema di consapevolezza spaziale offre consapevolezza ambientale reale nelle applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="8411c-106">The Spatial Awareness system provides real-world environmental awareness in mixed reality applications.</span></span> <span data-ttu-id="8411c-107">Se introdotta in Microsoft HoloLens, la consapevolezza spaziale ha fornito una raccolta di mesh, che rappresentano la geometria dell'ambiente, che ha consentito interazioni accattivanti tra ologrammi e il mondo reale.</span><span class="sxs-lookup"><span data-stu-id="8411c-107">When introduced on Microsoft HoloLens, Spatial Awareness provided a collection of meshes, representing the geometry of the environment, which allowed for compelling interactions between holograms and the real-world.</span></span>

> [!NOTE]
> <span data-ttu-id="8411c-108">Al momento, Mixed Reality Toolkit non include algoritmi spatial understanding come originariamente in pacchetto in HoloToolkit.</span><span class="sxs-lookup"><span data-stu-id="8411c-108">At this time, the Mixed Reality Toolkit does not ship with Spatial Understanding algorithms as originally packaged in the HoloToolkit.</span></span> <span data-ttu-id="8411c-109">La comprensione spaziale comporta in genere la trasformazione dei dati della mesh spaziale per creare dati mesh semplificati e/o raggruppati, ad esempio piani, pareti, piani, controsoffi e così via.</span><span class="sxs-lookup"><span data-stu-id="8411c-109">Spatial Understanding generally involves transforming Spatial Mesh data to create simplified and/or grouped Mesh data such as planes, walls, floors, ceilings, etc.</span></span>

## <a name="getting-started"></a><span data-ttu-id="8411c-110">Per iniziare</span><span class="sxs-lookup"><span data-stu-id="8411c-110">Getting started</span></span>

<span data-ttu-id="8411c-111">L'aggiunta del supporto per la consapevolezza spaziale richiede due componenti chiave di Mixed Reality Toolkit: il sistema di consapevolezza spaziale e un provider di piattaforma supportato.</span><span class="sxs-lookup"><span data-stu-id="8411c-111">Adding support for Spatial Awareness requires two key components of the Mixed Reality Toolkit: the Spatial Awareness system and a supported platform provider.</span></span>

1. <span data-ttu-id="8411c-112">[Abilitare](#enable-the-spatial-awareness-system) il sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="8411c-112">[Enable](#enable-the-spatial-awareness-system) the Spatial Awareness system</span></span>
2. <span data-ttu-id="8411c-113">[Registrare](#register-observers) [e configurare](configuring-spatial-awareness-mesh-observer.md) uno o più osservatori spaziali per fornire dati mesh</span><span class="sxs-lookup"><span data-stu-id="8411c-113">[Register](#register-observers) and [configure](configuring-spatial-awareness-mesh-observer.md) one or more spatial observers to provide mesh data</span></span>
3. <span data-ttu-id="8411c-114">[Compilare e distribuire](#build-and-deploy) in una piattaforma che supporta la consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="8411c-114">[Build and deploy](#build-and-deploy) to a platform that supports Spatial Awareness</span></span>

### <a name="enable-the-spatial-awareness-system"></a><span data-ttu-id="8411c-115">Abilitare il sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="8411c-115">Enable the spatial awareness system</span></span>

<span data-ttu-id="8411c-116">Il sistema di consapevolezza spaziale è gestito dall'oggetto MixedRealityToolkit (o da un altro [componente registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) del servizio).</span><span class="sxs-lookup"><span data-stu-id="8411c-116">The Spatial Awareness system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span> <span data-ttu-id="8411c-117">Seguire questa procedura per abilitare o disabilitare il *sistema di* consapevolezza spaziale nel *profilo MixedRealityToolkit.*</span><span class="sxs-lookup"><span data-stu-id="8411c-117">Follow the steps below to enable or disable the *Spatial Awareness system* in the *MixedRealityToolkit* profile.</span></span>

<span data-ttu-id="8411c-118">Mixed Reality Toolkit viene fornito con alcuni profili preconfigurati predefiniti.</span><span class="sxs-lookup"><span data-stu-id="8411c-118">The Mixed Reality Toolkit ships with a few default pre-configured profiles.</span></span> <span data-ttu-id="8411c-119">Per alcuni di questi il sistema di consapevolezza spaziale è abilitato o disabilitato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="8411c-119">Some of these have the Spatial Awareness system enabled OR disabled by default.</span></span> <span data-ttu-id="8411c-120">Lo scopo di questa pre-configurazione, in particolare per quando è disabilitato, è evitare il sovraccarico visivo dovuto al calcolo e al rendering delle mesh.</span><span class="sxs-lookup"><span data-stu-id="8411c-120">The intent of this pre-configuration, particularly for when disabled, is to avoid the visual overhead of calculating and rendering the meshes.</span></span>

| <span data-ttu-id="8411c-121">Profilo</span><span class="sxs-lookup"><span data-stu-id="8411c-121">Profile</span></span> | <span data-ttu-id="8411c-122">Sistema abilitato per impostazione predefinita</span><span class="sxs-lookup"><span data-stu-id="8411c-122">System Enabled by Default</span></span> |
| --- | --- |
| <span data-ttu-id="8411c-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span><span class="sxs-lookup"><span data-stu-id="8411c-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span></span> | <span data-ttu-id="8411c-124">Falso</span><span class="sxs-lookup"><span data-stu-id="8411c-124">False</span></span> |
| <span data-ttu-id="8411c-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span><span class="sxs-lookup"><span data-stu-id="8411c-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span></span> | <span data-ttu-id="8411c-126">Falso</span><span class="sxs-lookup"><span data-stu-id="8411c-126">False</span></span> |
| <span data-ttu-id="8411c-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)</span><span class="sxs-lookup"><span data-stu-id="8411c-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)</span></span> | <span data-ttu-id="8411c-128">Vero</span><span class="sxs-lookup"><span data-stu-id="8411c-128">True</span></span> |

1. <span data-ttu-id="8411c-129">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena da aprire nel pannello inspector.</span><span class="sxs-lookup"><span data-stu-id="8411c-129">Select the MixedRealityToolkit object in the scene hierarchy to open in the Inspector Panel.</span></span>

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="8411c-131">Passare alla sezione *Sistema di consapevolezza spaziale* e selezionare Abilita sistema di *consapevolezza spaziale*</span><span class="sxs-lookup"><span data-stu-id="8411c-131">Navigate to the *Spatial Awareness System* section and check *Enable Spatial Awareness System*</span></span>

    ![Abilitare la consapevolezza spaziale](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. <span data-ttu-id="8411c-133">Selezionare il tipo di implementazione del sistema Spatial Awareness desiderato.</span><span class="sxs-lookup"><span data-stu-id="8411c-133">Select the desired Spatial Awareness system implementation type.</span></span> <span data-ttu-id="8411c-134">è [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) il valore predefinito fornito.</span><span class="sxs-lookup"><span data-stu-id="8411c-134">The [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) is the default provided.</span></span>

    ![Selezionare l'implementazione del sistema di consapevolezza spaziale](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a><span data-ttu-id="8411c-136">Registrare gli osservatori</span><span class="sxs-lookup"><span data-stu-id="8411c-136">Register observers</span></span>

<span data-ttu-id="8411c-137">I servizi in Mixed Reality Toolkit possono avere provider di dati [che](../../architecture/systems-extensions-providers.md) integrano il servizio principale con dati specifici della piattaforma e controlli di implementazione.</span><span class="sxs-lookup"><span data-stu-id="8411c-137">Services in the Mixed Reality Toolkit can have [Data Provider services](../../architecture/systems-extensions-providers.md) that supplement the main service with platform specific data and implementation controls.</span></span> <span data-ttu-id="8411c-138">Un esempio è il sistema di [](../input/input-providers.md) input di realtà mista che dispone di più provider di dati per ottenere il controller e altre informazioni di input correlate da varie API specifiche della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="8411c-138">An example of this is the Mixed Reality Input System which has [multiple data providers](../input/input-providers.md) to get controller and other related input information from various platform-specific APIs.</span></span>

<span data-ttu-id="8411c-139">Il sistema di consapevolezza spaziale è simile perché i provider di dati forniscono al sistema dati mesh sul mondo reale.</span><span class="sxs-lookup"><span data-stu-id="8411c-139">The Spatial Awareness system is similar in that data providers supply the system with mesh data about the real-world.</span></span> <span data-ttu-id="8411c-140">Nel profilo Di consapevolezza spaziale deve essere registrato almeno un osservatore spaziale.</span><span class="sxs-lookup"><span data-stu-id="8411c-140">The Spatial Awareness profile must have at least one Spatial Observer registered.</span></span> <span data-ttu-id="8411c-141">Gli osservatori spaziali sono in genere componenti specifici della piattaforma che fungono da provider per la visualizzazione di vari tipi di dati mesh da un endpoint specifico della piattaforma (ad esempio</span><span class="sxs-lookup"><span data-stu-id="8411c-141">Spatial Observers are generally platform specific components that act as the provider for surfacing various types of mesh data from a platform specific endpoint (i.e</span></span> <span data-ttu-id="8411c-142">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="8411c-142">HoloLens).</span></span>

1. <span data-ttu-id="8411c-143">Aprire o espandere il profilo *Sistema di consapevolezza spaziale*</span><span class="sxs-lookup"><span data-stu-id="8411c-143">Open or expand the *Spatial Awareness System profile*</span></span>

    ![Profilo di sistema per la consapevolezza spaziale](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. <span data-ttu-id="8411c-145">Fare clic sul *pulsante "Aggiungi osservatore spaziale"*</span><span class="sxs-lookup"><span data-stu-id="8411c-145">Click the *"Add Spatial Observer"* button</span></span>
1. <span data-ttu-id="8411c-146">Selezionare il tipo di *implementazione osservatore spaziale desiderato*</span><span class="sxs-lookup"><span data-stu-id="8411c-146">Select the desired *Spatial Observer implementation type*</span></span>

    ![Selezionare l'implementazione dell'osservatore spaziale](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. <span data-ttu-id="8411c-148">[Modificare le proprietà di configurazione nell'osservatore](configuring-spatial-awareness-mesh-observer.md) in base alle esigenze</span><span class="sxs-lookup"><span data-stu-id="8411c-148">[Modify configuration properties on the observer](configuring-spatial-awareness-mesh-observer.md) as necessary</span></span>

> [!NOTE]
> <span data-ttu-id="8411c-149">Gli utenti di `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) avranno il sistema spatial awareness preconfigurato per la piattaforma Windows Mixed Reality che usa la [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) classe .</span><span class="sxs-lookup"><span data-stu-id="8411c-149">Users of the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) will have the Spatial Awareness system pre-configured for the Windows Mixed Reality platform which uses the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="8411c-150">Eseguire la compilazione e la distribuzione</span><span class="sxs-lookup"><span data-stu-id="8411c-150">Build and deploy</span></span>

<span data-ttu-id="8411c-151">Dopo aver configurato il sistema di riconoscimento spaziale con gli osservatori desiderati, il progetto può essere compilato e distribuito nella piattaforma di destinazione.</span><span class="sxs-lookup"><span data-stu-id="8411c-151">Once the Spatial Awareness system is configured with the desired observer(s), the project can be built and deployed to the target platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8411c-152">Se la piattaforma Windows Mixed Reality destinazione (ad esempio, HoloLens), è importante assicurarsi che la funzionalità [Percezione](/windows/mixed-reality/spatial-mapping-in-unity) spaziale sia abilitata per usare il sistema di consapevolezza spaziale nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8411c-152">If targeting the Windows Mixed Reality platform (ex: HoloLens), it is important to ensure the [Spatial Perception capability](/windows/mixed-reality/spatial-mapping-in-unity) is enabled in order to use the Spatial Awareness system on device.</span></span>

> [!WARNING]
> <span data-ttu-id="8411c-153">Alcune piattaforme, tra cui Microsoft HoloLens, forniscono il supporto per l'esecuzione remota dall'interno di Unity.</span><span class="sxs-lookup"><span data-stu-id="8411c-153">Some platforms, including Microsoft HoloLens, provide support for remote execution from within Unity.</span></span> <span data-ttu-id="8411c-154">Questa funzionalità consente di sviluppare e testare rapidamente senza richiedere il passaggio di compilazione e distribuzione.</span><span class="sxs-lookup"><span data-stu-id="8411c-154">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="8411c-155">Assicurarsi di eseguire il test di accettazione finale usando una versione compilata e distribuita dell'applicazione, in esecuzione nell'hardware e nella piattaforma di destinazione.</span><span class="sxs-lookup"><span data-stu-id="8411c-155">Be sure to do final acceptance testing using a built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8411c-156">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="8411c-156">Next steps</span></span>

<span data-ttu-id="8411c-157">Dopo aver seguito le procedure precedenti per abilitare il sistema di riconoscimento spaziale, il sistema può essere configurato e controllato in modo più dettagliato.</span><span class="sxs-lookup"><span data-stu-id="8411c-157">After following the procedures above to enable the Spatial Awareness system, the system can be configured and controlled in more detail.</span></span>

<span data-ttu-id="8411c-158">Informazioni per la configurazione degli osservatori in Inspector:</span><span class="sxs-lookup"><span data-stu-id="8411c-158">Information for configuring observers in inspector:</span></span>

- [<span data-ttu-id="8411c-159">Configurazione di Observers per l'utilizzo del dispositivo</span><span class="sxs-lookup"><span data-stu-id="8411c-159">Configuring Observers for on device usage</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="8411c-160">Configurazione di Observers per l'utilizzo nell'editor</span><span class="sxs-lookup"><span data-stu-id="8411c-160">Configuring Observers for in-editor usage</span></span>](spatial-object-mesh-observer.md)

<span data-ttu-id="8411c-161">Informazioni per il controllo e l'estensione degli osservatori tramite codice:</span><span class="sxs-lookup"><span data-stu-id="8411c-161">Information for controlling and extending observers via code:</span></span>

- [<span data-ttu-id="8411c-162">Configurazione degli osservatori tramite codice</span><span class="sxs-lookup"><span data-stu-id="8411c-162">Configuring Observers via Code</span></span>](usage-guide.md)
- [<span data-ttu-id="8411c-163">Creazione di un osservatore personalizzato</span><span class="sxs-lookup"><span data-stu-id="8411c-163">Creating a custom Observer</span></span>](create-data-provider.md)

## <a name="see-also"></a><span data-ttu-id="8411c-164">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="8411c-164">See also</span></span>

- [<span data-ttu-id="8411c-165">Documentazione dell'API Spatial Awareness</span><span class="sxs-lookup"><span data-stu-id="8411c-165">Spatial Awareness API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [<span data-ttu-id="8411c-166">Panoramica del mapping spaziale WMR</span><span class="sxs-lookup"><span data-stu-id="8411c-166">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/spatial-mapping)
- [<span data-ttu-id="8411c-167">Mapping spaziale in Unity WMR</span><span class="sxs-lookup"><span data-stu-id="8411c-167">Spatial Mapping in Unity WMR</span></span>](/windows/mixed-reality/spatial-mapping-in-unity)