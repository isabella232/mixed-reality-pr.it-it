---
title: Acquisti in-app
description: Gli acquisti in-app sono supportati nelle app per realtà mista, ma è necessario configurarli.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: acquisti in-app, hololens
ms.openlocfilehash: 7174fe555322216b7e547055aaaf7879c01d8f23
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684845"
---
# <a name="in-app-purchases"></a>Acquisti in-app

Gli acquisti in-app sono supportati in HoloLens, ma è necessario configurarli.

Per sfruttare le funzionalità di acquisto di app, è necessario:
* Creare una [visualizzazione 2D](../design/app-views.md) XAML da visualizzare come ardesia
* Passare ad esso per attivare la selezione host, che lascia la visualizzazione immersiva
* Chiamare l'API: await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Questa API visualizzerà il popup del sistema operativo Windows azionario che mostra il nome, la descrizione e il prezzo dell'acquisto in-app. L'utente può quindi scegliere le opzioni di acquisto. Al termine dell'azione, l'app deve presentare l'interfaccia utente che consente all'utente di tornare alla [visualizzazione immersiva](../design/app-views.md).

Per le app destinate a auricolari di Windows a realtà mista basate su desktop, non è necessario passare manualmente a una visualizzazione XAML prima di chiamare l'API RequestProductPurchaseAsync.
