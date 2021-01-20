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
# <a name="in-app-purchases"></a>Acquisti in-app

Gli acquisti in-app sono supportati in HoloLens, ma è necessario configurarli.

Per usare la funzionalità di acquisto di app, è necessario:
* Creare una [visualizzazione 2D](../design/app-views.md) XAML da visualizzare come ardesia
* Passare ad esso per attivare la selezione host, che lascia la visualizzazione immersiva
* Chiamare l'API: await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Questa API visualizzerà il popup del sistema operativo Windows azionario che mostra il nome, la descrizione e il prezzo dell'acquisto in-app. L'utente può quindi scegliere le opzioni di acquisto. Al termine dell'azione, l'app dovrà presentare l'interfaccia utente, che consente all'utente di tornare alla [visualizzazione immersiva](../design/app-views.md).

Per le app destinate a auricolari di Windows a realtà mista basate su desktop, non è necessario passare manualmente a una visualizzazione XAML prima di chiamare l'API RequestProductPurchaseAsync.