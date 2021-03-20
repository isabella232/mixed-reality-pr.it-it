---
title: LostTrackingService
description: Panoramica sul servizio LostTracking in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 1465f1fe934e55f8bd8a5ce6d680e438e436380a
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693548"
---
# <a name="lost-tracking-visualization"></a><span data-ttu-id="15c95-104">Visualizzazione di rilevamento persa</span><span class="sxs-lookup"><span data-stu-id="15c95-104">Lost tracking visualization</span></span>

![Rilevamento perso](images/lost-tracking/LostTrackingVisualization.jpg)

<span data-ttu-id="15c95-106">Il servizio di estensione rilevamento perso fornisce l'oggetto visivo animato in stile shell HoloLens per lo stato di rilevamento perso.</span><span class="sxs-lookup"><span data-stu-id="15c95-106">Lost Tracking Extension Service provides HoloLens shell style animated visual for the lost tracking state.</span></span>

## <a name="how-to-use-lost-tracking-extensions"></a><span data-ttu-id="15c95-107">Come usare le estensioni di rilevamento perdute</span><span class="sxs-lookup"><span data-stu-id="15c95-107">How to use lost tracking extensions</span></span>

<span data-ttu-id="15c95-108">In profilo MRTK aggiungere il **servizio di rilevamento perso** alle estensioni.</span><span class="sxs-lookup"><span data-stu-id="15c95-108">In MRTK Profile, add **Lost Tracking Service** to the Extensions.</span></span> <span data-ttu-id="15c95-109">Assegnare **DefaultLostTrackingServiceProfile** che include **LostTrackingVisualPrefab**.</span><span class="sxs-lookup"><span data-stu-id="15c95-109">Assign **DefaultLostTrackingServiceProfile** which includes **LostTrackingVisualPrefab**.</span></span>

<img src="images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
