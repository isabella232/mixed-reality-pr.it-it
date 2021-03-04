---
title: Framework e Runtime
description: Informazioni correlate a Framework e Runtime in MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: de91dfacb26e9757403d869ae6363289b455cff1
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783794"
---
# <a name="framework-and-runtime"></a>Framework e Runtime

## <a name="changes-to-the-scene"></a>Modifiche alla scena

Per usare il Toolkit, un'istanza dello script MixedRealityToolkit deve trovarsi nella scena.
Per aggiungerne uno, usare l'opzione di menu: Mixed Reality Toolkit-> aggiungere alla scena e configurare. Questa istanza è responsabile della registrazione, dell'aggiornamento e dello strappo dei servizi. È anche la scelta del profilo di configurazione.

Oltre ad aggiungere il GameObject MRTK alla scena, l'opzione di menu consente anche di:

- Aggiungere MixedRealityPlayspace, usato da molti altri componenti di MRTK per ragionare sulle trasformazioni di spazio globale e locale.
- Spostare la fotocamera principale come elemento figlio di MixedRealityPlayspace (e aggiungere anche un input e guardare gli script correlati alla fotocamera principale, che consentono a Power UnityUI e di guardare le funzionalità di input correlate).

## <a name="mixedrealitytoolkit-object-and-runtime"></a>Oggetto MixedRealityToolkit e Runtime

Il MRTK dispone di diversi servizi di base. Una coordinata tra loro; altre sono indipendenti.
Tutti condividono lo stesso ciclo di vita, ovvero startup, registrazione, aggiornamento e teardown, e questo ciclo di vita si differenzia dal ciclo di vita monobehavior di Unity. Questo [post di medie dimensioni](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) illustra alcuni dei retroscena e la motivazione alla base di questo approccio. MRTK dispone di un singolo oggetto che gestisce la durata e il runtime dei servizi.

Questa entità garantisce che:

- all'avvio del gioco, l'individuazione e l'inizializzazione dei servizi vengono eseguite in un ordine predefinito.
- fornisce un meccanismo per la registrazione dei servizi (ad esempio "supporto di questo servizio!") e per altri chiamanti per ottenere i servizi.
- fornisce le chiamate Update ()/LateUpdate () e le invia ai vari servizi, ad esempio tramite UpdateAllServices/LateUpdateAllServices.
