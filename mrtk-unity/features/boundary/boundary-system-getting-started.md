---
title: Panoramica del sistema di limiti
description: Pagina di destinazione per il sistema di limiti in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di limiti,
ms.openlocfilehash: 405a2d06be5d929d5c276fc8cd7ab36b6b3cf68c
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121359"
---
# <a name="boundary-system"></a><span data-ttu-id="9ed5e-104">Sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="9ed5e-104">Boundary system</span></span>

<span data-ttu-id="9ed5e-105">Il sistema di limiti fornisce il supporto per la visualizzazione dei componenti limite di Realtà virtuale nelle applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-105">The Boundary system provides support for visualizing Virtual Reality boundary components in mixed reality applications.</span></span> <span data-ttu-id="9ed5e-106">I limiti definiscono l'area in cui gli utenti possono spostarsi in modo sicuro mentre si indossano i visori VR.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-106">Boundaries define the area in which users can safely move around while wearing a VR headset.</span></span> <span data-ttu-id="9ed5e-107">I limiti sono un componente importante di un'esperienza di realtà mista per aiutare gli utenti a evitare ostacoli imprevisti durante l'uso di un visore VR.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-107">Boundaries are an important component of a mixed reality experience to help users avoid unseen obstacles while wearing a VR headset.</span></span>

<span data-ttu-id="9ed5e-108">Molte piattaforme di realtà virtuale offrono uno schermo automatico, ad esempio un contorno bianco sovrapposto al mondo virtuale quando l'utente o il controller si avvicina al limite.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-108">Many Virtual Reality platforms provide an automatic display, for example a white outline superimposed on the virtual world as the user or their controller nears the boundary.</span></span> <span data-ttu-id="9ed5e-109">Il sistema di limiti di Mixed Reality Toolkit estende questa funzionalità per consentire la visualizzazione di una struttura dell'area tracciata, di un piano piano e di altre funzionalità che possono essere usate per fornire informazioni aggiuntive agli utenti.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-109">The Mixed Reality Toolkit's Boundary System extends this feature to enable the display of an outline of the tracked area, a floor plane and other features that can be used to provide additional information to users.</span></span>

## <a name="getting-started"></a><span data-ttu-id="9ed5e-110">Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="9ed5e-110">Getting started</span></span>

<span data-ttu-id="9ed5e-111">L'aggiunta del supporto per i limiti richiede due componenti chiave di Mixed Reality Toolkit: il sistema di limiti e una piattaforma di realtà virtuale configurata con un limite.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-111">Adding support for boundaries requires two key components of the Mixed Reality Toolkit: the Boundary System and a Virtual Reality platform configured with a boundary.</span></span>

1. <span data-ttu-id="9ed5e-112">[Abilitare](#enable-boundary-system) il sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="9ed5e-112">[Enable](#enable-boundary-system) the boundary system</span></span>
2. <span data-ttu-id="9ed5e-113">[Configurare la](#configure-boundary-visualization) visualizzazione dei limiti</span><span class="sxs-lookup"><span data-stu-id="9ed5e-113">[Configure](#configure-boundary-visualization) the boundary visualization</span></span>
3. <span data-ttu-id="9ed5e-114">[Compilare e distribuire](#build-and-deploy) in una piattaforma di realtà virtuale con un limite configurato</span><span class="sxs-lookup"><span data-stu-id="9ed5e-114">[Build and deploy](#build-and-deploy) to a VR platform with a configured boundary</span></span>

## <a name="enable-boundary-system"></a><span data-ttu-id="9ed5e-115">Abilitare il sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="9ed5e-115">Enable boundary system</span></span>

<span data-ttu-id="9ed5e-116">Il sistema di limiti è gestito dall'oggetto MixedRealityToolkit (o da un altro [componente registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) del servizio).</span><span class="sxs-lookup"><span data-stu-id="9ed5e-116">The Boundary System is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="9ed5e-117">La procedura seguente presuppone l'uso dell'oggetto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-117">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="9ed5e-118">I passaggi necessari per altri registrar del servizio possono essere diversi.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-118">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="9ed5e-119">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-119">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Gerarchia della scena configurata da MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="9ed5e-121">Passare al pannello Inspector (Controllo) nella sezione Boundary System (Sistema limite) e selezionare Enable (Abilita)</span><span class="sxs-lookup"><span data-stu-id="9ed5e-121">Navigate the Inspector panel to the Boundary System section and check Enable</span></span>

    ![Abilitare il sistema di limiti](../images/boundary/MRTKConfig_Boundary.png)

1. <span data-ttu-id="9ed5e-123">Selezionare l'implementazione del sistema di limiti.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-123">Select the Boundary System implementation.</span></span> <span data-ttu-id="9ed5e-124">L'implementazione predefinita della classe fornita da MRTK è [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="9ed5e-124">The default class implementation provided by the MRTK is the [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

    ![Selezionare l'implementazione del sistema di limiti](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="9ed5e-126">Tutte le implementazioni del sistema di limiti devono estendere [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="9ed5e-126">All Boundary System implementation must extend the [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span></span>

## <a name="configure-boundary-visualization"></a><span data-ttu-id="9ed5e-127">Configurare la visualizzazione dei limiti</span><span class="sxs-lookup"><span data-stu-id="9ed5e-127">Configure boundary visualization</span></span>

<span data-ttu-id="9ed5e-128">Il [sistema di limiti usa un profilo di](configuring-boundary-visualization.md) configurazione per specificare i componenti limite da visualizzare e per configurarne l'aspetto.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-128">The [Boundary System uses a configuration profile](configuring-boundary-visualization.md) to specify which boundary components are to be displayed and to configure their appearance.</span></span>

![Opzioni di visualizzazione dei limiti](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> <span data-ttu-id="9ed5e-130">Gli utenti del profilo predefinito (Assets/MRTK/SDK/Profiles) avranno il sistema di limiti preconfigurato per visualizzare un piano piano, l'area di riproduzione e `DefaultMixedRealityBoundaryVisualizationProfile` l'area tracciata.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-130">Users of the default profile, `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/MRTK/SDK/Profiles) will have the boundary system pre-configured to display a floor plane, the play area and the tracked area.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="9ed5e-131">Eseguire la compilazione e la distribuzione</span><span class="sxs-lookup"><span data-stu-id="9ed5e-131">Build and deploy</span></span>

<span data-ttu-id="9ed5e-132">Dopo aver configurato il sistema di limiti con le opzioni di visualizzazione desiderate, il progetto può essere compilato nella piattaforma di destinazione.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-132">Once the boundary system is configured with the desired visualization options, the project can be built deployed to the target platform.</span></span>

> [!NOTE]
> <span data-ttu-id="9ed5e-133">La modalità di riproduzione Unity consente la visualizzazione nell'editor del limite configurato.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-133">Unity Play Mode enables in-editor visualization of the configured boundary.</span></span> <span data-ttu-id="9ed5e-134">Questa funzionalità consente lo sviluppo e il test rapidi senza richiedere il passaggio di compilazione e distribuzione.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-134">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="9ed5e-135">Assicurarsi di eseguire il test di accettazione finale usando una versione compilata e distribuita dell'applicazione, in esecuzione nell'hardware e nella piattaforma di destinazione.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-135">Be sure to do final acceptance testing using an built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="accessing-boundary-system-via-code"></a><span data-ttu-id="9ed5e-136">Accesso al sistema di limiti tramite codice</span><span class="sxs-lookup"><span data-stu-id="9ed5e-136">Accessing boundary system via code</span></span>

<span data-ttu-id="9ed5e-137">Se abilitata e configurata, è possibile accedere al sistema di limiti tramite la classe helper statica CoreServices.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-137">If enabled and configured, the Boundary System can be accessed via the CoreServices static helper class.</span></span> <span data-ttu-id="9ed5e-138">Il riferimento può quindi essere usato per modificare dinamicamente i parametri boundary e accedere ai GameObject correlati gestiti dal sistema.</span><span class="sxs-lookup"><span data-stu-id="9ed5e-138">The reference can then be used to dynamically change the Boundary parameters and access related GameObjects managed by the system.</span></span>

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a><span data-ttu-id="9ed5e-139">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9ed5e-139">See also</span></span>

- [<span data-ttu-id="9ed5e-140">Documentazione dell'API Limite</span><span class="sxs-lookup"><span data-stu-id="9ed5e-140">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="9ed5e-141">Configurazione della visualizzazione dei limiti</span><span class="sxs-lookup"><span data-stu-id="9ed5e-141">Configuring the Boundary Visualization</span></span>](configuring-boundary-visualization.md)
