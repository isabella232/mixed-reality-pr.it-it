---
title: LostTrackingService
description: Panoramica sul servizio LostTracking in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 775e7cd9cffad1deeb5fe5a10b3fb80d5a26b091
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782869"
---
# <a name="lost-tracking-visualization"></a><span data-ttu-id="9a25e-104">Visualizzazione di rilevamento persa</span><span class="sxs-lookup"><span data-stu-id="9a25e-104">Lost tracking visualization</span></span>

![Rilevamento perso](images/lost-tracking/LostTrackingVisualization.jpg)

<span data-ttu-id="9a25e-106">Il servizio di estensione rilevamento perso fornisce l'oggetto visivo animato in stile shell HoloLens per lo stato di rilevamento perso.</span><span class="sxs-lookup"><span data-stu-id="9a25e-106">Lost Tracking Extension Service provides HoloLens shell style animated visual for the lost tracking state.</span></span>

## <a name="how-to-use-lost-tracking-extensions"></a><span data-ttu-id="9a25e-107">Come usare le estensioni di rilevamento perdute</span><span class="sxs-lookup"><span data-stu-id="9a25e-107">How to use lost tracking extensions</span></span>

<span data-ttu-id="9a25e-108">In profilo MRTK aggiungere il **servizio di rilevamento perso** alle estensioni.</span><span class="sxs-lookup"><span data-stu-id="9a25e-108">In MRTK Profile, add **Lost Tracking Service** to the Extensions.</span></span> <span data-ttu-id="9a25e-109">Assegnare **DefaultLostTrackingServiceProfile** che include **LostTrackingVisualPrefab**.</span><span class="sxs-lookup"><span data-stu-id="9a25e-109">Assign **DefaultLostTrackingServiceProfile** which includes **LostTrackingVisualPrefab**.</span></span>

<img src="images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extensions">
