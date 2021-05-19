---
title: Servizio di rilevamento della perdita
description: Panoramica del servizio LostTracking in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 96090b05c60cfaa6ff5d8c5e1dc7a58cc2658b71
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144526"
---
# <a name="lost-tracking-visualization"></a><span data-ttu-id="340bf-104">Visualizzazione del rilevamento della perdita</span><span class="sxs-lookup"><span data-stu-id="340bf-104">Lost tracking visualization</span></span>

![Rilevamento della perdita](../images/lost-tracking/LostTrackingVisualization.jpg)

<span data-ttu-id="340bf-106">Il servizio di estensione per il rilevamento della perdita fornisce un oggetto visivo animato in stile shell HoloLens per lo stato di rilevamento della perdita.</span><span class="sxs-lookup"><span data-stu-id="340bf-106">Lost Tracking Extension Service provides HoloLens shell style animated visual for the lost tracking state.</span></span>

## <a name="how-to-use-lost-tracking-extensions"></a><span data-ttu-id="340bf-107">Come usare le estensioni per il rilevamento della perdita</span><span class="sxs-lookup"><span data-stu-id="340bf-107">How to use lost tracking extensions</span></span>

<span data-ttu-id="340bf-108">In Profilo MRTK aggiungere **Lost Tracking Service** alle estensioni.</span><span class="sxs-lookup"><span data-stu-id="340bf-108">In MRTK Profile, add **Lost Tracking Service** to the Extensions.</span></span> <span data-ttu-id="340bf-109">Assegnare **DefaultLostTrackingServiceProfile** che include **LostTrackingVisualPrefab.**</span><span class="sxs-lookup"><span data-stu-id="340bf-109">Assign **DefaultLostTrackingServiceProfile** which includes **LostTrackingVisualPrefab**.</span></span>

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
