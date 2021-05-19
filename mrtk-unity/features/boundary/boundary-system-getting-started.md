---
title: Sistema di limiti Attività iniziali
description: Pagina di destinazione per il sistema di limiti in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di limiti,
ms.openlocfilehash: 2858b770fb49a44d1e2d704e8d3a81affe74d272
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144730"
---
# <a name="boundary-system"></a><span data-ttu-id="2777b-104">Sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="2777b-104">Boundary system</span></span>

<span data-ttu-id="2777b-105">Il sistema Boundary fornisce il supporto per la visualizzazione dei componenti limite della realtà virtuale nelle applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="2777b-105">The Boundary system provides support for visualizing Virtual Reality boundary components in mixed reality applications.</span></span> <span data-ttu-id="2777b-106">I limiti definiscono l'area in cui gli utenti possono spostarsi in modo sicuro mentre indossano un visore VR.</span><span class="sxs-lookup"><span data-stu-id="2777b-106">Boundaries define the area in which users can safely move around while wearing a VR headset.</span></span> <span data-ttu-id="2777b-107">I limiti sono un componente importante di un'esperienza di realtà mista per aiutare gli utenti a evitare ostacoli nonvisibile mentre indossano un visore VR.</span><span class="sxs-lookup"><span data-stu-id="2777b-107">Boundaries are an important component of a mixed reality experience to help users avoid unseen obstacles while wearing a VR headset.</span></span>

<span data-ttu-id="2777b-108">Molte piattaforme di realtà virtuale offrono una visualizzazione automatica, ad esempio un contorno bianco sovrapposto al mondo virtuale quando l'utente o il controller si avvicina al limite.</span><span class="sxs-lookup"><span data-stu-id="2777b-108">Many Virtual Reality platforms provide an automatic display, for example a white outline superimposed on the virtual world as the user or their controller nears the boundary.</span></span> <span data-ttu-id="2777b-109">Mixed Reality Toolkit's Boundary System estende questa funzionalità per consentire la visualizzazione di un contorno dell'area tracciata, di un piano terra e di altre funzionalità che possono essere usate per fornire informazioni aggiuntive agli utenti.</span><span class="sxs-lookup"><span data-stu-id="2777b-109">The Mixed Reality Toolkit's Boundary System extends this feature to enable the display of an outline of the tracked area, a floor plane and other features that can be used to provide additional information to users.</span></span>

## <a name="getting-started"></a><span data-ttu-id="2777b-110">Per iniziare</span><span class="sxs-lookup"><span data-stu-id="2777b-110">Getting started</span></span>

<span data-ttu-id="2777b-111">L'aggiunta del supporto per i limiti richiede due componenti chiave di Mixed Reality Toolkit: il sistema di limiti e una piattaforma di realtà virtuale configurata con un limite.</span><span class="sxs-lookup"><span data-stu-id="2777b-111">Adding support for boundaries requires two key components of the Mixed Reality Toolkit: the Boundary System and a Virtual Reality platform configured with a boundary.</span></span>

1. <span data-ttu-id="2777b-112">[Abilitare](#enable-boundary-system) il sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="2777b-112">[Enable](#enable-boundary-system) the boundary system</span></span>
2. <span data-ttu-id="2777b-113">[Configurare la](#configure-boundary-visualization) visualizzazione dei limiti</span><span class="sxs-lookup"><span data-stu-id="2777b-113">[Configure](#configure-boundary-visualization) the boundary visualization</span></span>
3. <span data-ttu-id="2777b-114">[Compilare e distribuire](#build-and-deploy) in una piattaforma VR con un limite configurato</span><span class="sxs-lookup"><span data-stu-id="2777b-114">[Build and deploy](#build-and-deploy) to a VR platform with a configured boundary</span></span>

## <a name="enable-boundary-system"></a><span data-ttu-id="2777b-115">Abilitare il sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="2777b-115">Enable boundary system</span></span>

<span data-ttu-id="2777b-116">Il sistema di limiti è gestito dall'oggetto MixedRealityToolkit (o da un altro [componente del registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) del servizio).</span><span class="sxs-lookup"><span data-stu-id="2777b-116">The Boundary System is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="2777b-117">La procedura seguente presuppone l'uso dell'oggetto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="2777b-117">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="2777b-118">I passaggi necessari per altri registrar del servizio possono essere diversi.</span><span class="sxs-lookup"><span data-stu-id="2777b-118">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="2777b-119">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="2777b-119">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="2777b-121">Passare al pannello Inspector (Controllo) nella sezione Boundary System (Sistema limite) e selezionare Enable (Abilita)</span><span class="sxs-lookup"><span data-stu-id="2777b-121">Navigate the Inspector panel to the Boundary System section and check Enable</span></span>

    ![Abilitare il sistema di limiti](../images/boundary/MRTKConfig_Boundary.png)

1. <span data-ttu-id="2777b-123">Selezionare l'implementazione del sistema di limiti.</span><span class="sxs-lookup"><span data-stu-id="2777b-123">Select the Boundary System implementation.</span></span> <span data-ttu-id="2777b-124">L'implementazione predefinita della classe fornita da MRTK è [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="2777b-124">The default class implementation provided by the MRTK is the [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

    ![Selezionare l'implementazione del sistema di limiti](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="2777b-126">Tutte le implementazioni del sistema di limiti devono estendere [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="2777b-126">All Boundary System implementation must extend the [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span></span>

## <a name="configure-boundary-visualization"></a><span data-ttu-id="2777b-127">Configurare la visualizzazione dei limiti</span><span class="sxs-lookup"><span data-stu-id="2777b-127">Configure boundary visualization</span></span>

<span data-ttu-id="2777b-128">Il [sistema di limiti usa un profilo di](configuring-boundary-visualization.md) configurazione per specificare quali componenti limite devono essere visualizzati e per configurarne l'aspetto.</span><span class="sxs-lookup"><span data-stu-id="2777b-128">The [Boundary System uses a configuration profile](configuring-boundary-visualization.md) to specify which boundary components are to be displayed and to configure their appearance.</span></span>

![Opzioni di visualizzazione dei limiti](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> <span data-ttu-id="2777b-130">Gli utenti del profilo predefinito (Assets/MRTK/SDK/Profiles) avranno il sistema di limiti preconfigurato per visualizzare un piano piano, l'area di riproduzione e `DefaultMixedRealityBoundaryVisualizationProfile` l'area tracciata.</span><span class="sxs-lookup"><span data-stu-id="2777b-130">Users of the default profile, `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/MRTK/SDK/Profiles) will have the boundary system pre-configured to display a floor plane, the play area and the tracked area.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="2777b-131">Eseguire la compilazione e la distribuzione</span><span class="sxs-lookup"><span data-stu-id="2777b-131">Build and deploy</span></span>

<span data-ttu-id="2777b-132">Dopo aver configurato il sistema di limiti con le opzioni di visualizzazione desiderate, il progetto può essere compilato nella piattaforma di destinazione.</span><span class="sxs-lookup"><span data-stu-id="2777b-132">Once the boundary system is configured with the desired visualization options, the project can be built deployed to the target platform.</span></span>

> [!NOTE]
> <span data-ttu-id="2777b-133">La modalità di riproduzione Unity consente la visualizzazione nell'editor del limite configurato.</span><span class="sxs-lookup"><span data-stu-id="2777b-133">Unity Play Mode enables in-editor visualization of the configured boundary.</span></span> <span data-ttu-id="2777b-134">Questa funzionalità consente lo sviluppo e il test rapidi senza richiedere il passaggio di compilazione e distribuzione.</span><span class="sxs-lookup"><span data-stu-id="2777b-134">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="2777b-135">Assicurarsi di eseguire il test di accettazione finale usando una versione compilata e distribuita dell'applicazione, in esecuzione nell'hardware e nella piattaforma di destinazione.</span><span class="sxs-lookup"><span data-stu-id="2777b-135">Be sure to do final acceptance testing using an built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="accessing-boundary-system-via-code"></a><span data-ttu-id="2777b-136">Accesso al sistema di limiti tramite codice</span><span class="sxs-lookup"><span data-stu-id="2777b-136">Accessing boundary system via code</span></span>

<span data-ttu-id="2777b-137">Se abilitata e configurata, è possibile accedere al sistema di limiti tramite la classe helper statica CoreServices.</span><span class="sxs-lookup"><span data-stu-id="2777b-137">If enabled and configured, the Boundary System can be accessed via the CoreServices static helper class.</span></span> <span data-ttu-id="2777b-138">Il riferimento può quindi essere usato per modificare dinamicamente i parametri Boundary e accedere ai GameObject correlati gestiti dal sistema.</span><span class="sxs-lookup"><span data-stu-id="2777b-138">The reference can then be used to dynamically change the Boundary parameters and access related GameObjects managed by the system.</span></span>

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a><span data-ttu-id="2777b-139">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="2777b-139">See also</span></span>

- [<span data-ttu-id="2777b-140">Documentazione dell'API Limite</span><span class="sxs-lookup"><span data-stu-id="2777b-140">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="2777b-141">Configurazione della visualizzazione dei limiti</span><span class="sxs-lookup"><span data-stu-id="2777b-141">Configuring the Boundary Visualization</span></span>](configuring-boundary-visualization.md)
