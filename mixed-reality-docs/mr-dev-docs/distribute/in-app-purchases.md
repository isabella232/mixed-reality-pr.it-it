---
title: Acquisti in-app
description: Gli acquisti in-app sono supportati nelle app per realtà mista, ma è necessario configurarli.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: acquisti in-app, hololens, XAML, cuffie per realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 905c1be72bf2a3d6fa167cab68a4cb71e6538acc
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757781"
---
# <a name="in-app-purchases"></a><span data-ttu-id="e724d-104">Acquisti in-app</span><span class="sxs-lookup"><span data-stu-id="e724d-104">In-app purchases</span></span>

<span data-ttu-id="e724d-105">Gli acquisti in-app sono supportati in HoloLens, ma è necessario configurarli.</span><span class="sxs-lookup"><span data-stu-id="e724d-105">In-app purchases are supported in HoloLens, but there's some work to set them up.</span></span>

<span data-ttu-id="e724d-106">Per usare la funzionalità di acquisto di app, è necessario:</span><span class="sxs-lookup"><span data-stu-id="e724d-106">To use the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="e724d-107">Creare una [visualizzazione 2D](../design/app-views.md) XAML da visualizzare come ardesia</span><span class="sxs-lookup"><span data-stu-id="e724d-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="e724d-108">Passare ad esso per attivare la selezione host, che lascia la visualizzazione immersiva</span><span class="sxs-lookup"><span data-stu-id="e724d-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="e724d-109">Chiamare l'API: await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="e724d-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="e724d-110">Questa API visualizzerà il popup del sistema operativo Windows azionario che mostra il nome, la descrizione e il prezzo dell'acquisto in-app.</span><span class="sxs-lookup"><span data-stu-id="e724d-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="e724d-111">L'utente può quindi scegliere le opzioni di acquisto.</span><span class="sxs-lookup"><span data-stu-id="e724d-111">The user can then choose purchase options.</span></span> <span data-ttu-id="e724d-112">Al termine dell'azione, l'app dovrà presentare l'interfaccia utente, che consente all'utente di tornare alla [visualizzazione immersiva](../design/app-views.md).</span><span class="sxs-lookup"><span data-stu-id="e724d-112">Once the action is completed, the app will need to present UI, which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="e724d-113">Per le app destinate a auricolari di Windows a realtà mista basate su desktop, non è necessario passare manualmente a una visualizzazione XAML prima di chiamare l'API RequestProductPurchaseAsync.</span><span class="sxs-lookup"><span data-stu-id="e724d-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it isn't required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
