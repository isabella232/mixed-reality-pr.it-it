---
title: BoundarySystemGettingStarted
description: Pagina di destinazione per il sistema di limiti in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di limiti,
ms.openlocfilehash: 61601b6d426a79a0442cd2115c80030efe50f74c
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688931"
---
# <a name="boundary-system"></a><span data-ttu-id="86970-104">Sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="86970-104">Boundary system</span></span>

<span data-ttu-id="86970-105">Il sistema di limiti fornisce il supporto per la visualizzazione dei componenti limite della realtà virtuale nelle applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="86970-105">The Boundary system provides support for visualizing Virtual Reality boundary components in mixed reality applications.</span></span> <span data-ttu-id="86970-106">I limiti definiscono l'area in cui gli utenti possono spostarsi in modo sicuro mentre indossano una cuffia virtuale.</span><span class="sxs-lookup"><span data-stu-id="86970-106">Boundaries define the area in which users can safely move around while wearing a VR headset.</span></span> <span data-ttu-id="86970-107">I limiti sono un componente importante di un'esperienza di realtà mista per aiutare gli utenti a evitare gli ostacoli non visibili mentre indossano una cuffia virtuale.</span><span class="sxs-lookup"><span data-stu-id="86970-107">Boundaries are an important component of a mixed reality experience to help users avoid unseen obstacles while wearing a VR headset.</span></span>

<span data-ttu-id="86970-108">Molte piattaforme di realtà virtuale forniscono una visualizzazione automatica, ad esempio un contorno bianco sovrapposto al mondo virtuale quando l'utente o il controller si avvicina al limite.</span><span class="sxs-lookup"><span data-stu-id="86970-108">Many Virtual Reality platforms provide an automatic display, for example a white outline superimposed on the virtual world as the user or their controller nears the boundary.</span></span> <span data-ttu-id="86970-109">Il sistema di limiti del Toolkit di realtà mista estende questa funzionalità per consentire la visualizzazione di una struttura dell'area rilevata, un piano di piano e altre funzionalità che possono essere usate per fornire informazioni aggiuntive agli utenti.</span><span class="sxs-lookup"><span data-stu-id="86970-109">The Mixed Reality Toolkit's Boundary System extends this feature to enable the display of an outline of the tracked area, a floor plane and other features that can be used to provide additional information to users.</span></span>

## <a name="getting-started"></a><span data-ttu-id="86970-110">Introduzione</span><span class="sxs-lookup"><span data-stu-id="86970-110">Getting started</span></span>

<span data-ttu-id="86970-111">L'aggiunta del supporto per i limiti richiede due componenti chiave del Toolkit di realtà mista: il sistema di limiti e una piattaforma di realtà virtuale configurata con un limite.</span><span class="sxs-lookup"><span data-stu-id="86970-111">Adding support for boundaries requires two key components of the Mixed Reality Toolkit: the Boundary System and a Virtual Reality platform configured with a boundary.</span></span>

1. <span data-ttu-id="86970-112">[Abilitare](#enable-boundary-system) il sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="86970-112">[Enable](#enable-boundary-system) the boundary system</span></span>
2. <span data-ttu-id="86970-113">[Configurare](#configure-boundary-visualization) la visualizzazione dei limiti</span><span class="sxs-lookup"><span data-stu-id="86970-113">[Configure](#configure-boundary-visualization) the boundary visualization</span></span>
3. <span data-ttu-id="86970-114">[Compila e Distribuisci](#build-and-deploy) in una piattaforma VR con un limite configurato</span><span class="sxs-lookup"><span data-stu-id="86970-114">[Build and deploy](#build-and-deploy) to a VR platform with a configured boundary</span></span>

## <a name="enable-boundary-system"></a><span data-ttu-id="86970-115">Abilita sistema limite</span><span class="sxs-lookup"><span data-stu-id="86970-115">Enable boundary system</span></span>

<span data-ttu-id="86970-116">Il sistema di limiti è gestito dall'oggetto MixedRealityToolkit (o da un altro componente di [registrazione del servizio](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).</span><span class="sxs-lookup"><span data-stu-id="86970-116">The Boundary System is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="86970-117">I passaggi seguenti presuppongono l'uso dell'oggetto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="86970-117">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="86970-118">I passaggi necessari per altri registrar di servizi potrebbero essere diversi.</span><span class="sxs-lookup"><span data-stu-id="86970-118">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="86970-119">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="86970-119">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Gerarchia della scena configurata MRTK](../Images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="86970-121">Passare al pannello di controllo nella sezione del sistema di limiti e selezionare Abilita.</span><span class="sxs-lookup"><span data-stu-id="86970-121">Navigate the Inspector panel to the Boundary System section and check Enable</span></span>

    ![Abilitare il sistema di limiti](../Images/Boundary/MRTKConfig_Boundary.png)

1. <span data-ttu-id="86970-123">Selezionare l'implementazione del sistema di limiti.</span><span class="sxs-lookup"><span data-stu-id="86970-123">Select the Boundary System implementation.</span></span> <span data-ttu-id="86970-124">L'implementazione della classe predefinita fornita da MRTK è [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="86970-124">The default class implementation provided by the MRTK is the [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

    ![Selezionare l'implementazione del sistema di limiti](../Images/Boundary/BoundarySelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="86970-126">Tutte le implementazioni del sistema limite devono estendere [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="86970-126">All Boundary System implementation must extend the [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span></span>

## <a name="configure-boundary-visualization"></a><span data-ttu-id="86970-127">Configurare la visualizzazione limite</span><span class="sxs-lookup"><span data-stu-id="86970-127">Configure boundary visualization</span></span>

<span data-ttu-id="86970-128">Il [sistema di limiti USA un profilo di configurazione](ConfiguringBoundaryVisualization.md) per specificare quali componenti limite devono essere visualizzati e per configurarne l'aspetto.</span><span class="sxs-lookup"><span data-stu-id="86970-128">The [Boundary System uses a configuration profile](ConfiguringBoundaryVisualization.md) to specify which boundary components are to be displayed and to configure their appearance.</span></span>

![Opzioni di visualizzazione limite](../Images/Boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> <span data-ttu-id="86970-130">Gli utenti del profilo predefinito, `DefaultMixedRealityBoundaryVisualizationProfile` (assets/MRTK/SDK/Profiles) avranno il sistema di limiti preconfigurato per visualizzare un piano di piano, l'area di riproduzione e l'area rilevata.</span><span class="sxs-lookup"><span data-stu-id="86970-130">Users of the default profile, `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/MRTK/SDK/Profiles) will have the boundary system pre-configured to display a floor plane, the play area and the tracked area.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="86970-131">Eseguire la compilazione e la distribuzione</span><span class="sxs-lookup"><span data-stu-id="86970-131">Build and deploy</span></span>

<span data-ttu-id="86970-132">Una volta configurato il sistema di limiti con le opzioni di visualizzazione desiderate, è possibile compilare il progetto distribuito nella piattaforma di destinazione.</span><span class="sxs-lookup"><span data-stu-id="86970-132">Once the boundary system is configured with the desired visualization options, the project can be built deployed to the target platform.</span></span>

> [!NOTE]
> <span data-ttu-id="86970-133">La modalità di riproduzione Unity consente la visualizzazione all'interno dell'editor del limite configurato.</span><span class="sxs-lookup"><span data-stu-id="86970-133">Unity Play Mode enables in-editor visualization of the configured boundary.</span></span> <span data-ttu-id="86970-134">Questa funzionalità consente lo sviluppo e i test rapidi senza richiedere la fase di compilazione e distribuzione.</span><span class="sxs-lookup"><span data-stu-id="86970-134">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="86970-135">Assicurarsi di eseguire test di accettazione finali usando una versione compilata e distribuita dell'applicazione, in esecuzione nell'hardware e nella piattaforma di destinazione.</span><span class="sxs-lookup"><span data-stu-id="86970-135">Be sure to do final acceptance testing using an built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="accessing-boundary-system-via-code"></a><span data-ttu-id="86970-136">Accesso al sistema di limiti tramite codice</span><span class="sxs-lookup"><span data-stu-id="86970-136">Accessing boundary system via code</span></span>

<span data-ttu-id="86970-137">Se abilitata e configurata, è possibile accedere al sistema di limiti tramite la classe helper statica CoreServices.</span><span class="sxs-lookup"><span data-stu-id="86970-137">If enabled and configured, the Boundary System can be accessed via the CoreServices static helper class.</span></span> <span data-ttu-id="86970-138">Il riferimento può quindi essere usato per modificare dinamicamente i parametri limite e accedere a GameObject correlati gestiti dal sistema.</span><span class="sxs-lookup"><span data-stu-id="86970-138">The reference can then be used to dynamically change the Boundary parameters and access related GameObjects managed by the system.</span></span>

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a><span data-ttu-id="86970-139">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="86970-139">See also</span></span>

- [<span data-ttu-id="86970-140">Documentazione dell'API limite</span><span class="sxs-lookup"><span data-stu-id="86970-140">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="86970-141">Configurazione della visualizzazione dei limiti</span><span class="sxs-lookup"><span data-stu-id="86970-141">Configuring the Boundary Visualization</span></span>](ConfiguringBoundaryVisualization.md)
