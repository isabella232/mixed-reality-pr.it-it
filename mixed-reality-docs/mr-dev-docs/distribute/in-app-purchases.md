---
title: Acquisti in-app
description: Informazioni su come usare gli acquisti in-app nelle app per realtà mista con visualizzazioni XAML 2D e un popup del sistema operativo Windows azionario.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: acquisti in-app, hololens, XAML, cuffie per realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: dfc5a0cfcc7a4d63147a753c8892d65dfae5e495
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582953"
---
# <a name="in-app-purchases"></a><span data-ttu-id="5079e-104">Acquisti in-app</span><span class="sxs-lookup"><span data-stu-id="5079e-104">In-app purchases</span></span>

<span data-ttu-id="5079e-105">Gli acquisti in-app sono supportati in HoloLens, ma è necessario configurarli.</span><span class="sxs-lookup"><span data-stu-id="5079e-105">In-app purchases are supported in HoloLens, but there's some work to set them up.</span></span>

<span data-ttu-id="5079e-106">Per usare la funzionalità di acquisto di app, è necessario:</span><span class="sxs-lookup"><span data-stu-id="5079e-106">To use the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="5079e-107">Creare una [visualizzazione 2D](../design/app-views.md) XAML da visualizzare come ardesia</span><span class="sxs-lookup"><span data-stu-id="5079e-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="5079e-108">Passare ad esso per attivare la selezione host, che lascia la visualizzazione immersiva</span><span class="sxs-lookup"><span data-stu-id="5079e-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="5079e-109">Chiamare l'API: await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="5079e-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="5079e-110">Questa API visualizzerà il popup del sistema operativo Windows azionario che mostra il nome, la descrizione e il prezzo dell'acquisto in-app.</span><span class="sxs-lookup"><span data-stu-id="5079e-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="5079e-111">L'utente può quindi scegliere le opzioni di acquisto.</span><span class="sxs-lookup"><span data-stu-id="5079e-111">The user can then choose purchase options.</span></span> <span data-ttu-id="5079e-112">Al termine dell'azione, l'app dovrà presentare l'interfaccia utente, che consente all'utente di tornare alla [visualizzazione immersiva](../design/app-views.md).</span><span class="sxs-lookup"><span data-stu-id="5079e-112">Once the action is completed, the app will need to present UI, which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="5079e-113">Per le app destinate a auricolari di Windows a realtà mista basate su desktop, non è necessario passare manualmente a una visualizzazione XAML prima di chiamare l'API RequestProductPurchaseAsync.</span><span class="sxs-lookup"><span data-stu-id="5079e-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it isn't required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>