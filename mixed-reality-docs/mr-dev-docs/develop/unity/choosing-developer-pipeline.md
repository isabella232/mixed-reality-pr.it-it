---
title: Scelta della pipeline di sviluppo
description: Rimanere aggiornati sulle raccomandazioni più recenti sulla pipeline di sviluppo unity per lo sviluppo di applicazioni HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale, unity
ms.openlocfilehash: b7896c2426ff9adb1133e86a5e3204bff1249ebc
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394555"
---
# <a name="choosing-your-developer-pipeline"></a><span data-ttu-id="64193-104">Scelta della pipeline di sviluppo</span><span class="sxs-lookup"><span data-stu-id="64193-104">Choosing your developer pipeline</span></span>

![Banner con logo di Unity](../images/unity_logo_banner.png)<br>

<span data-ttu-id="64193-106">Anche se attualmente è consigliabile installare **Unity 2019.4 LTS** e usare XR incorporato legacy per lo sviluppo di realtà mista, è possibile compilare app anche con altre configurazioni di Unity.</span><span class="sxs-lookup"><span data-stu-id="64193-106">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="mixed-reality-toolkit-recommended"></a><span data-ttu-id="64193-107">Mixed Reality Toolkit (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="64193-107">Mixed Reality Toolkit (Recommended)</span></span>

<span data-ttu-id="64193-108">La configurazione di Unity consigliata di Microsoft per HoloLens 2 è Mixed Reality Toolkit...</span><span class="sxs-lookup"><span data-stu-id="64193-108">Microsoft’s current recommended Unity configuration for HoloLens 2 is the Mixed Reality Toolkit...</span></span>

### <a name="install-the-mixed-reality-feature-tool"></a><span data-ttu-id="64193-109">Installare lo strumento di funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="64193-109">Install the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="64193-110">Lo [strumento funzionalità realtà mista](welcome-to-mr-feature-tool.md) è un nuovo modo per consentire agli sviluppatori di individuare e aggiungere pacchetti di funzionalità di realtà mista nei progetti Unity.</span><span class="sxs-lookup"><span data-stu-id="64193-110">The [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) is a new way for developers to discover and add Mixed Reality feature packages into Unity projects.</span></span> 

<span data-ttu-id="64193-111">È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="64193-111">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="64193-112">Dopo aver convalidato i pacchetti desiderati, lo strumento per la funzionalità di realtà mista li scaricherà nel progetto di propria scelta.</span><span class="sxs-lookup"><span data-stu-id="64193-112">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

### <a name="importing-the-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="64193-113">Importazione di Mixed Reality Toolkit per Unity</span><span class="sxs-lookup"><span data-stu-id="64193-113">Importing the Mixed Reality Toolkit for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="64193-115">[Mixed Reality Toolkit](mrtk-getting-started.md) (MRTK) è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="64193-115">[Mixed Reality Toolkit](mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> 

* <span data-ttu-id="64193-116">Installare il pacchetto Mixed Reality Toolkit seguendo le istruzioni di installazione e [utilizzo](welcome-to-mr-feature-tool.md#system-requirements) e selezionando il **pacchetto Mixed Reality Toolkit Foundation.**</span><span class="sxs-lookup"><span data-stu-id="64193-116">Install the Mixed Reality Toolkit package by following the [installation and usage instructions](welcome-to-mr-feature-tool.md#system-requirements) and selecting the **Mixed Reality Toolkit Foundation** package.</span></span>

<span data-ttu-id="64193-117">È consigliabile completare la sezione introduttiva nei percorsi di [sviluppo di HoloLens](unity-development-overview.md#1-getting-started) o [VR](unity-development-wmr-overview.md#1-getting-started) curati.</span><span class="sxs-lookup"><span data-stu-id="64193-117">We recommend completing the getting started section in our curated [HoloLens](unity-development-overview.md#1-getting-started) or [VR](unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="64193-118">Se si sta già seguendo il percorso di sviluppo con Unity per HoloLens, completare i rimanenti passaggi di configurazione elencati di seguito e proseguire con le [esercitazioni introduttive su HoloLens 2](tutorials/mr-learning-base-01.md).</span><span class="sxs-lookup"><span data-stu-id="64193-118">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="64193-119">Si noti che le istruzioni di installazione sono destinate alla più recente combinazione stabile di versioni di MRTK e Unity, ovvero **MRTK 2.6.1** e **Unity 2019.4 LTS.**</span><span class="sxs-lookup"><span data-stu-id="64193-119">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.6.1** and **Unity 2019.4 LTS**.</span></span>

> [!NOTE]
> <span data-ttu-id="64193-120">Se non si vuole usare MRTK per Unity, è necessario creare uno script di tutte le interazioni [e i comportamenti manualmente.](configure-unity-project.md)</span><span class="sxs-lookup"><span data-stu-id="64193-120">If you don't want to use MRTK for Unity, you'll need to [script all interactions and behaviors yourself](configure-unity-project.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="64193-121"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Banner di Unity](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="64193-121"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="64193-122">**Mixed Reality Toolkit-Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="64193-122">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

## <a name="manual"></a><span data-ttu-id="64193-123">Manuale</span><span class="sxs-lookup"><span data-stu-id="64193-123">Manual</span></span> 

<span data-ttu-id="64193-124">Tbd...</span><span class="sxs-lookup"><span data-stu-id="64193-124">TBD...</span></span>