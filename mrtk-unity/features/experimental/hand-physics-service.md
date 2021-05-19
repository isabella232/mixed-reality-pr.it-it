---
title: Servizio di estensione fisica della mano
description: Descrizione Dei servizi di estensione di Fisica della mano.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 401a9d31ed3fbbe0c3e02cb95ffebb024f882fd9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143435"
---
# <a name="hand-physics-extension-services"></a>Servizi di estensione per la fisica della mano

Il servizio di fisica della mano consente eventi rigidi di collisione del corpo e interazioni con mani articolate.

## <a name="getting-started-with-hand-physics-extension-service"></a>Introduzione al servizio di estensione della fisica della mano

Aggiungere il servizio di fisica della mano all'elenco dei servizi di estensione e usare il profilo predefinito.

Una volta abilitata, usare la proprietà IsTrigger di qualsiasi collisore per ricevere eventi di collisione da tutte e 10 cifre (e palmi se abilitati).

### <a name="prerequisites"></a>Prerequisiti

- Abilitato il servizio di estensione
- Assegnare un prefab appropriato all'giunzione di dito/palmo.

## <a name="recommendations"></a>Consigli

Anche se il livello predefinito del servizio è "predefinito", è consigliabile usare un livello separato per gli oggetti HandPhysics. In caso contrario, potrebbero verificarsi collisioni indesiderate e/o raycast non accurati.
