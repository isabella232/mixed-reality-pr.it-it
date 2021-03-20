---
title: Panoramica e obiettivi dell'esercitazione
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: b7e04a03f01beb1438f6f723c3938d05a60c9131
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "98581160"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="aee29-104">1. Panoramica e obiettivi</span><span class="sxs-lookup"><span data-stu-id="aee29-104">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="aee29-105">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="aee29-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="aee29-106"><strong>Corso</strong></span><span class="sxs-lookup"><span data-stu-id="aee29-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="aee29-107"><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="aee29-107"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="aee29-108"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="aee29-108"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="aee29-109"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="aee29-109"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="aee29-110">✔️</span><span class="sxs-lookup"><span data-stu-id="aee29-110">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="aee29-111">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="aee29-111">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="aee29-112">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="aee29-112">Prerequisites</span></span>

* <span data-ttu-id="aee29-113">Un PC Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="aee29-113">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="aee29-114">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="aee29-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="aee29-115">Alcune funzionalità di programmazione C# di base</span><span class="sxs-lookup"><span data-stu-id="aee29-115">Some basic C# programming ability</span></span>
* <span data-ttu-id="aee29-116">Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="aee29-116">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="aee29-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X installato e il modulo di supporto delle compilazioni UWP (Universal Windows Platform) aggiunto</span><span class="sxs-lookup"><span data-stu-id="aee29-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aee29-118">La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="aee29-118">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="aee29-119">Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="aee29-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="aee29-120">Lezione successiva: 2. Inizializzazione del progetto e prima applicazione</span><span class="sxs-lookup"><span data-stu-id="aee29-120">Next lesson: 2. Initializing your project and first application</span></span>](./mr-learning-base-02.md)