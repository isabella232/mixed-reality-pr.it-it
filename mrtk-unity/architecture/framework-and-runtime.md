---
title: Framework e runtime
description: Informazioni correlate al framework e al runtime in MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: a44e5f32cda2803091e27ae1a2c30a1976385a2f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121609"
---
# <a name="framework-and-runtime"></a>Framework e runtime

## <a name="changes-to-the-scene"></a>Modifiche alla scena

Per usare il toolkit, è necessario che nella scena sia presente un'istanza dello script MixedRealityToolkit.
Per aggiungerne uno, usa l'opzione di menu Mixed Reality Toolkit -> Aggiungi alla scena e Configura. Questa istanza è responsabile della registrazione, dell'aggiornamento e della rimozione dei servizi. È anche la posizione in cui viene scelto il profilo di configurazione.

Oltre ad aggiungere il GameObject MRTK alla scena, l'opzione di menu:

- Aggiungere MixedRealityPlayspace, che viene usato da molti altri componenti MRTK per eseguire trasformazioni di spazio globale e locale.
- Sposta la fotocamera principale come elemento figlio di MixedRealityPlayspace (e aggiungendo anche alcuni script correlati all'input e allo sguardo fisso alla fotocamera principale, che consentono di usare UnityUI e la funzionalità di input correlata allo sguardo).

## <a name="mixedrealitytoolkit-object-and-runtime"></a>Oggetto MixedRealityToolkit e runtime

MrTK include diversi servizi di base. Alcuni si coordinano l'uno con l'altro; altri sono indipendenti.
Tutti condividono lo stesso ciclo di vita( avvio, registrazione, aggiornamento e rimozione) e questo ciclo di vita si distingue dal ciclo di vita MonoBehaviour di Unity. Questo [post medio](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) illustra alcune delle informazioni di base e della motivazione alla base di questo approccio. MRTK ha un singolo oggetto che gestisce la durata e il runtime dei servizi.

Questa entità garantisce che:

- All'avvio del gioco, l'individuazione e l'inizializzazione dei servizi vengono avviate in un ordine predefinito.
- fornisce un meccanismo che consente ai servizi di registrarsi (ad esempio,"Supporto questo servizio!") e per consentire ad altri chiamanti di ottenere informazioni su tali servizi.
- fornisce le chiamate Update()/LateUpdate() e le inoltra ai vari servizi, ad esempio tramite UpdateAllServices/LateUpdateAllServices.
