---
title: Configurazione del progetto Unreal
description: Informazioni su come configurare il progetto con la versione più recente di Unreal Engine e dello strumento di funzionalità di realtà mista.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, realtà mista, sviluppo, funzionalità, nuovo progetto, emulatore, documentazione, guide, ologrammi, sviluppo di giochi, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale
ms.openlocfilehash: 8201e97ed35d11404928c1dfe94ad9b7e626e51b
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394643"
---
# <a name="setting-up-your-unreal-project"></a><span data-ttu-id="e9a75-104">Configurazione del progetto Unreal</span><span class="sxs-lookup"><span data-stu-id="e9a75-104">Setting up your Unreal project</span></span>

<span data-ttu-id="e9a75-105">È consigliabile installare [Unreal Engine versione 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) o versione successiva per sfruttare appieno il supporto di HoloLens incorporato.</span><span class="sxs-lookup"><span data-stu-id="e9a75-105">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

<span data-ttu-id="e9a75-106">Passare alla scheda **Library (Libreria)** nell'utilità di avvio di Epic Games, selezionare la freccia a discesa accanto **a Launch (Avvia)** e fare clic su **Options (Opzioni).**</span><span class="sxs-lookup"><span data-stu-id="e9a75-106">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** and click **Options**.</span></span> <span data-ttu-id="e9a75-107">In **Target Platforms** (Piattaforme di destinazione) seleziona **HoloLens 2** e fai clic su **Apply** (Applica).</span><span class="sxs-lookup"><span data-stu-id="e9a75-107">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
<span data-ttu-id="e9a75-108">![Opzione di installazione Unreal HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)</span><span class="sxs-lookup"><span data-stu-id="e9a75-108">![Unreal Install Option HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)</span></span>

## <a name="import-mixed-reality-toolkit-for-unreal"></a><span data-ttu-id="e9a75-109">Importare Mixed Reality Toolkit per Unreal</span><span class="sxs-lookup"><span data-stu-id="e9a75-109">Import Mixed Reality Toolkit for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="e9a75-111">Mixed Reality Toolkit (MRTK) è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="e9a75-111">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="e9a75-112">MRTK offre un sistema di input multipiattaforma, componenti di base e blocchi predefiniti comuni per le interazioni spaziali.</span><span class="sxs-lookup"><span data-stu-id="e9a75-112">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="e9a75-113">Il toolkit permette di accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, ai visori VR immersive di Windows Mixed Reality e alla piattaforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="e9a75-113">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="e9a75-114">Per l'installazione, è consigliabile completare la [sezione introduttiva](unreal-development-overview.md#1-getting-started) del nostro [percorso di sviluppo con Unreal](unreal-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e9a75-114">For installation, we recommend completing the [Getting Started section](unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](unreal-development-overview.md).</span></span> <span data-ttu-id="e9a75-115">Se si sta già seguendo il percorso di sviluppo con Unreal, completare il resto dei passaggi di configurazione elencati di seguito e proseguire con le [esercitazioni introduttive su HoloLens 2](tutorials/unreal-uxt-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="e9a75-115">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="e9a75-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Immagine del logo di Unity](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="e9a75-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="e9a75-117">**Mixed Reality Toolkit-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="e9a75-117">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="e9a75-118">Se non si vuole usare MRTK per Unreal, sarà necessario creare personalmente script per tutti i comportamenti e le interazioni.</span><span class="sxs-lookup"><span data-stu-id="e9a75-118">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>