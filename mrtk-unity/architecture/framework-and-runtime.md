---
title: Framework e runtime
description: Informazioni correlate al framework e al runtime in MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: f2391ab0c67880c8902092be6fcecefcf30f008c7f31ea76879d399e35e1491b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212672"
---
# <a name="framework-and-runtime"></a>Framework e runtime

## <a name="changes-to-the-scene"></a>Modifiche alla scena

Per usare il toolkit, è necessario che nella scena sia presente un'istanza dello script MixedRealityToolkit.
Per aggiungerne uno, usare l'opzione di menu: Realtà mista Toolkit -> Aggiungi a scena e Configura. Questa istanza è responsabile della registrazione, dell'aggiornamento e dell'operazione di rimozione dei servizi. È anche la posizione in cui viene scelto il profilo di configurazione.

Oltre ad aggiungere MRTK GameObject alla scena, l'opzione di menu include anche:

- Aggiungere MixedRealityPlayspace, usato da molti altri componenti MRTK per eseguire trasformazioni dello spazio globale e locale.
- Spostare la fotocamera principale come figlio di MixedRealityPlayspace (e aggiungere anche alcuni script correlati all'input e allo sguardo alla fotocamera principale, che consentono di alimentare UnityUI e la funzionalità di input correlata allo sguardo).

## <a name="mixedrealitytoolkit-object-and-runtime"></a>Oggetto MixedRealityToolkit e runtime

MrTK ha diversi servizi di base. Alcune si coordinano tra loro; altri sono indipendenti.
Tutti condividono lo stesso ciclo di vita, ad esempio avvio, registrazione, aggiornamento e teardown, e questo ciclo di vita si distingue dal ciclo di vita MonoBehaviour di Unity. Questo [post medio illustra](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) alcune delle informazioni di base e della motivazione alla base di questo approccio. MRTK ha un singolo oggetto che gestisce la durata e il runtime dei servizi.

Questa entità garantisce che:

- all'avvio del gioco, l'individuazione e l'inizializzazione dei servizi avviene in un ordine predefinito.
- fornisce un meccanismo che consente ai servizi di registrarsi (ad esempio"Supporto questo servizio!") e per altri chiamanti di ottenere informazioni su tali servizi.
- fornisce le chiamate Update()/LateUpdate() e le inoltra ai vari servizi, ad esempio tramite UpdateAllServices/LateUpdateAllServices.
