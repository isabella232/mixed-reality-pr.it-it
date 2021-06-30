---
title: Panoramica del sistema di diagnostica
description: Documentazione per abilitare e disabilitare la diagnostica in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 0de7b904a48453d6021cf7aed5835412c19b7884
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121779"
---
# <a name="diagnostic-system"></a><span data-ttu-id="47922-104">Sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="47922-104">Diagnostic system</span></span>

<span data-ttu-id="47922-105">Mixed Reality Toolkit Diagnostic System fornisce strumenti di diagnostica eseguiti all'interno dell'applicazione per consentire l'analisi dei problemi dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="47922-105">The Mixed Reality Toolkit Diagnostic System provides diagnostic tools that run within the application to enable analysis of application issues.</span></span>

<span data-ttu-id="47922-106">La prima versione del sistema di diagnostica contiene [Visual Profiler](using-visual-profiler.md) per consentire l'analisi dei problemi di prestazioni durante l'uso dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="47922-106">The first release of the Diagnostic System contains the [Visual Profiler](using-visual-profiler.md) to allow for analyzing performance issues while using the application.</span></span>

## <a name="getting-started"></a><span data-ttu-id="47922-107">Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="47922-107">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47922-108">È **_consigliabile che_** il sistema di diagnostica sia abilitato per l'intero ciclo di sviluppo del prodotto e disabilitato come ultima modifica prima di compilare e rilasciare la versione finale.</span><span class="sxs-lookup"><span data-stu-id="47922-108">It is **_highly_** recommended that the Diagnostic System be enabled throughout the entire product development cycle and disabled as the last change prior to building and releasing the final version.</span></span>

<span data-ttu-id="47922-109">Esistono due passaggi chiave per iniziare a usare il sistema di diagnostica.</span><span class="sxs-lookup"><span data-stu-id="47922-109">There are two key steps to start using the Diagnostic System.</span></span>

1. <span data-ttu-id="47922-110">[Abilitare](#enable-diagnostics) il sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="47922-110">[Enable](#enable-diagnostics) the Diagnostic System</span></span>
2. <span data-ttu-id="47922-111">[Configurare le](#configure-diagnostic-options) opzioni di diagnostica</span><span class="sxs-lookup"><span data-stu-id="47922-111">[Configure](#configure-diagnostic-options) diagnostic options</span></span>

### <a name="enable-diagnostics"></a><span data-ttu-id="47922-112">Abilitare la diagnostica</span><span class="sxs-lookup"><span data-stu-id="47922-112">Enable diagnostics</span></span>

<span data-ttu-id="47922-113">Il sistema di diagnostica è gestito dall'oggetto MixedRealityToolkit (o da un altro [componente del registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) del servizio).</span><span class="sxs-lookup"><span data-stu-id="47922-113">The diagnostics system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="47922-114">La procedura seguente presuppone l'uso dell'oggetto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="47922-114">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="47922-115">I passaggi necessari per altri registrar del servizio possono essere diversi.</span><span class="sxs-lookup"><span data-stu-id="47922-115">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="47922-116">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="47922-116">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="47922-118">Passare al pannello Inspector (Controllo) nella sezione Diagnostics System (Sistema di diagnostica) e selezionare Enable (Abilita)</span><span class="sxs-lookup"><span data-stu-id="47922-118">Navigate the Inspector panel to the Diagnostics System section and check Enable</span></span>
1. <span data-ttu-id="47922-119">Selezionare l'implementazione del sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="47922-119">Select the Diagnostics System implementation</span></span>

    ![Selezionare l'implementazione del sistema di diagnostica](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="47922-121">Gli utenti del profilo predefinito `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) avranno il sistema di diagnostica preconfigurato per l'uso [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="47922-121">Users of the default profile, `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles), will have the diagnostics system pre-configured to use the [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) object.</span></span>

### <a name="configure-diagnostic-options"></a><span data-ttu-id="47922-122">Configurare le opzioni di diagnostica</span><span class="sxs-lookup"><span data-stu-id="47922-122">Configure diagnostic options</span></span>

<span data-ttu-id="47922-123">Il sistema di diagnostica usa un profilo di configurazione per specificare i componenti da visualizzare e per configurarne le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="47922-123">The diagnostics system uses a configuration profile to specify which components are to be displayed and to configure their settings.</span></span> <span data-ttu-id="47922-124">Per altre [informazioni relative alle impostazioni dei](configuring-diagnostics.md) componenti disponibili, vedere Configurazione del sistema di diagnostica.</span><span class="sxs-lookup"><span data-stu-id="47922-124">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information pertaining to the available component settings.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47922-125">Sebbene sia possibile usare la modalità di riproduzione di Unity durante lo sviluppo di applicazioni senza richiedere i passaggi di compilazione e distribuzione, è importante valutare i risultati del sistema di diagnostica usando un'applicazione compilata in esecuzione nell'hardware e nella piattaforma di destinazione.</span><span class="sxs-lookup"><span data-stu-id="47922-125">While it is possible to use Unity's Play Mode while developing applications without requiring the build and deploy steps, it is important to evaluate the diagnostics system results using a compiled application running on the target hardware and platform.</span></span>
>
> <span data-ttu-id="47922-126">La diagnostica delle prestazioni, ad esempio [Visual Profiler](using-visual-profiler.md), potrebbe non riflettere in modo accurato le prestazioni effettive dell'applicazione quando viene eseguita dall'editor.</span><span class="sxs-lookup"><span data-stu-id="47922-126">Performance diagnostics, such as the [Visual Profiler](using-visual-profiler.md), may not accurately reflect actual application performance when run from within the editor.</span></span>

## <a name="see-also"></a><span data-ttu-id="47922-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="47922-127">See also</span></span>

- [<span data-ttu-id="47922-128">Documentazione dell'API di diagnostica</span><span class="sxs-lookup"><span data-stu-id="47922-128">Diagnostics API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [<span data-ttu-id="47922-129">Configurazione del sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="47922-129">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)
- [<span data-ttu-id="47922-130">Uso di Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="47922-130">Using the Visual Profiler</span></span>](using-visual-profiler.md)
