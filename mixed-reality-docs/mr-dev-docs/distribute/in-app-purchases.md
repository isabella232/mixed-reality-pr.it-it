---
title: Acquisti in-app
description: Informazioni su come usare gli acquisti in-app nelle app di realtà mista con visualizzazioni XAML 2D e popup Windows sistema operativo.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: acquisti in-app, hololens, XAML, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale
ms.openlocfilehash: fbb957d1044a5c76c19691b875de8f9513bfc4b49bc4cb0dbb98d045d615f1a4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196149"
---
# <a name="in-app-purchases"></a>Acquisti in-app

Gli acquisti in-app sono supportati in HoloLens, ma è necessario eseguire alcune operazioni per configurarli.

Per usare la funzionalità di acquisto di app, è necessario:
* Creare una visualizzazione XAML [2D da](../design/app-views.md) visualizzare come slate
* Passa a esso per attivare la selezione host, lasciando la visualizzazione immersiva
* Chiamare l'API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Questa API visualizza la finestra popup Windows sistema operativo che mostra il nome, la descrizione e il prezzo dell'acquisto in-app. L'utente può quindi scegliere le opzioni di acquisto. Al termine dell'azione, l'app dovrà presentare l'interfaccia utente, che consente all'utente di tornare alla visualizzazione [immersiva.](../design/app-views.md)

Per le app che hanno come destinazione Windows Mixed Reality visori VR immersive, non è necessario passare manualmente a una visualizzazione XAML prima di chiamare l'API RequestProductPurchaseAsync.