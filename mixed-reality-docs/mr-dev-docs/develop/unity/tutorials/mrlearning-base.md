---
title: Esercitazioni introduttive - 1 Panoramica e obiettivi
description: Questo corso illustra come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 777203d0051c22b0f249db7d377ab08f92c089b7
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91701588"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="5dc6e-105">1. Panoramica e obiettivi</span><span class="sxs-lookup"><span data-stu-id="5dc6e-105">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="5dc6e-106">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="5dc6e-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="5dc6e-107"><strong>Corso</strong></span><span class="sxs-lookup"><span data-stu-id="5dc6e-107"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="5dc6e-108"><a href="../../../hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="5dc6e-108"><a href="../../../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="5dc6e-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="5dc6e-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="5dc6e-110"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="5dc6e-110"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="5dc6e-111">✔️</span><span class="sxs-lookup"><span data-stu-id="5dc6e-111">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="5dc6e-112">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="5dc6e-112">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5dc6e-113">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="5dc6e-113">Prerequisites</span></span>

* <span data-ttu-id="5dc6e-114">Un PC Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="5dc6e-114">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="5dc6e-115">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="5dc6e-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="5dc6e-116">Alcune funzionalità di programmazione C# di base</span><span class="sxs-lookup"><span data-stu-id="5dc6e-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="5dc6e-117">Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="5dc6e-117">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="5dc6e-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X installato e il modulo di supporto delle compilazioni UWP (Universal Windows Platform) aggiunto</span><span class="sxs-lookup"><span data-stu-id="5dc6e-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5dc6e-119">La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="5dc6e-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="5dc6e-120">Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="5dc6e-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="5dc6e-121">Lezione successiva: 2. Inizializzazione del progetto e prima applicazione</span><span class="sxs-lookup"><span data-stu-id="5dc6e-121">Next lesson: 2. Initializing your project and first application</span></span>](../../../mrlearning-base-ch1.md)
