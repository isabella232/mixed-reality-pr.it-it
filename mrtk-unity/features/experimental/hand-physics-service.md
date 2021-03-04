---
title: HandPhysicsExtensionService
description: Descrizione servizi di estensione della fisica della mano.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 86c94d5f036f4f0919f53049a90d70b3ec8018e0
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781965"
---
# <a name="hand-physics-extension-services"></a>Servizi di estensione della fisica della mano

Il servizio di fisica della mano Abilita gli eventi di collisione corpo rigidi e le interazioni con le mani articolate.

## <a name="getting-started-with-hand-physics-extension-service"></a>Introduzione al servizio di estensione della fisica della mano

Aggiungere il servizio di fisica della mano all'elenco dei servizi di estensione e usare il profilo predefinito.

Una volta abilitata, usare qualsiasi proprietà del trigger di Collider per ricevere eventi di collisione da tutte le 10 cifre (e le palme se sono abilitate).

### <a name="prerequisites"></a>Prerequisiti

- Abilitazione del servizio di estensione
- Assegnare un prefabbricato appropriato al giunto dito/Palm.

## <a name="recommendations"></a>Consigli

Quando il servizio viene impostato per impostazione predefinita sul livello "predefinito", è consigliabile usare un livello separato per gli oggetti HandPhysics. In caso contrario, potrebbero verificarsi collisioni indesiderate e/o raycasts non accurati.
