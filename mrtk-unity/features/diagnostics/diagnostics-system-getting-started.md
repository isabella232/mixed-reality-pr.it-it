---
title: DiagnosticsSystemGettingStarted
description: documentazione per abilitare e disabilitare la diagnostica in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: ff8ee7bc50da66477544677d57b8d7c75bf0a1cd
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681334"
---
# <a name="diagnostic-system"></a><span data-ttu-id="4a6ab-104">Sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="4a6ab-104">Diagnostic system</span></span>

<span data-ttu-id="4a6ab-105">Il sistema di diagnostica del Toolkit di realtà mista fornisce strumenti di diagnostica che vengono eseguiti all'interno dell'applicazione per consentire l'analisi dei problemi dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="4a6ab-105">The Mixed Reality Toolkit Diagnostic System provides diagnostic tools that run within the application to enable analysis of application issues.</span></span>

<span data-ttu-id="4a6ab-106">Il primo rilascio del sistema di diagnostica contiene il [Profiler visivo](using-visual-profiler.md) che consente di analizzare i problemi di prestazioni durante l'uso dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="4a6ab-106">The first release of the Diagnostic System contains the [Visual Profiler](using-visual-profiler.md) to allow for analyzing performance issues while using the application.</span></span>

## <a name="getting-started"></a><span data-ttu-id="4a6ab-107">Introduzione</span><span class="sxs-lookup"><span data-stu-id="4a6ab-107">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a6ab-108">È consigliabile **_che_** il sistema di diagnostica sia abilitato nell'intero ciclo di sviluppo del prodotto e sia disabilitato come Ultima modifica prima della compilazione e del rilascio della versione finale.</span><span class="sxs-lookup"><span data-stu-id="4a6ab-108">It is **_highly_** recommended that the Diagnostic System be enabled throughout the entire product development cycle and disabled as the last change prior to building and releasing the final version.</span></span>

<span data-ttu-id="4a6ab-109">Per iniziare a usare il sistema di diagnostica, è necessario eseguire due passaggi principali.</span><span class="sxs-lookup"><span data-stu-id="4a6ab-109">There are two key steps to start using the Diagnostic System.</span></span>

1. <span data-ttu-id="4a6ab-110">[Abilitare](#enable-diagnostics) il sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="4a6ab-110">[Enable](#enable-diagnostics) the Diagnostic System</span></span>
2. <span data-ttu-id="4a6ab-111">[Configurare](#configure-diagnostic-options) le opzioni di diagnostica</span><span class="sxs-lookup"><span data-stu-id="4a6ab-111">[Configure](#configure-diagnostic-options) diagnostic options</span></span>

### <a name="enable-diagnostics"></a><span data-ttu-id="4a6ab-112">Abilitare la diagnostica</span><span class="sxs-lookup"><span data-stu-id="4a6ab-112">Enable diagnostics</span></span>

<span data-ttu-id="4a6ab-113">Il sistema di diagnostica è gestito dall'oggetto MixedRealityToolkit (o da un altro componente di [registrazione del servizio](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).</span><span class="sxs-lookup"><span data-stu-id="4a6ab-113">The diagnostics system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="4a6ab-114">I passaggi seguenti presuppongono l'uso dell'oggetto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="4a6ab-114">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="4a6ab-115">I passaggi necessari per altri registrar di servizi potrebbero essere diversi.</span><span class="sxs-lookup"><span data-stu-id="4a6ab-115">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="4a6ab-116">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="4a6ab-116">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="4a6ab-118">Passare al pannello di controllo nella sezione del sistema di diagnostica e selezionare Abilita.</span><span class="sxs-lookup"><span data-stu-id="4a6ab-118">Navigate the Inspector panel to the Diagnostics System section and check Enable</span></span>
1. <span data-ttu-id="4a6ab-119">Selezionare l'implementazione del sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="4a6ab-119">Select the Diagnostics System implementation</span></span>

    ![Selezionare l'implementazione del sistema di diagnostica](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="4a6ab-121">Gli utenti del profilo predefinito, `DefaultMixedRealityToolkitConfigurationProfile` (assets/MRTK/SDK/Profiles), avranno il sistema di diagnostica preconfigurato per l'uso dell' [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) oggetto.</span><span class="sxs-lookup"><span data-stu-id="4a6ab-121">Users of the default profile, `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles), will have the diagnostics system pre-configured to use the [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) object.</span></span>

### <a name="configure-diagnostic-options"></a><span data-ttu-id="4a6ab-122">Configurare le opzioni di diagnostica</span><span class="sxs-lookup"><span data-stu-id="4a6ab-122">Configure diagnostic options</span></span>

<span data-ttu-id="4a6ab-123">Il sistema di diagnostica utilizza un profilo di configurazione per specificare i componenti da visualizzare e per configurarne le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="4a6ab-123">The diagnostics system uses a configuration profile to specify which components are to be displayed and to configure their settings.</span></span> <span data-ttu-id="4a6ab-124">Per ulteriori informazioni relative alle impostazioni del componente disponibili, vedere [configurazione del sistema di diagnostica](configuring-diagnostics.md) .</span><span class="sxs-lookup"><span data-stu-id="4a6ab-124">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information pertaining to the available component settings.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a6ab-125">Sebbene sia possibile usare la modalità di riproduzione di Unity durante lo sviluppo di applicazioni senza la necessità di eseguire la procedura di compilazione e distribuzione, è importante valutare i risultati del sistema di diagnostica usando un'applicazione compilata in esecuzione nell'hardware e nella piattaforma di destinazione.</span><span class="sxs-lookup"><span data-stu-id="4a6ab-125">While it is possible to use Unity's Play Mode while developing applications without requiring the build and deploy steps, it is important to evaluate the diagnostics system results using a compiled application running on the target hardware and platform.</span></span>
>
> <span data-ttu-id="4a6ab-126">La diagnostica delle prestazioni, ad esempio il [Profiler visuale](using-visual-profiler.md), potrebbe non riflettere accuratamente le prestazioni effettive delle applicazioni quando vengono eseguite dall'interno dell'editor.</span><span class="sxs-lookup"><span data-stu-id="4a6ab-126">Performance diagnostics, such as the [Visual Profiler](using-visual-profiler.md), may not accurately reflect actual application performance when run from within the editor.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a6ab-127">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="4a6ab-127">See also</span></span>

- [<span data-ttu-id="4a6ab-128">Documentazione dell'API di diagnostica</span><span class="sxs-lookup"><span data-stu-id="4a6ab-128">Diagnostics API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [<span data-ttu-id="4a6ab-129">Configurazione del sistema di diagnostica</span><span class="sxs-lookup"><span data-stu-id="4a6ab-129">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)
- [<span data-ttu-id="4a6ab-130">Uso di Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="4a6ab-130">Using the Visual Profiler</span></span>](using-visual-profiler.md)
