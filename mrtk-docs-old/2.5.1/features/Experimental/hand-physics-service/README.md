---
title: README_HandPhysicsExtensionService
description: Descrizione servizi di estensione della fisica della mano.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 73e7cb358c9690ffc7cb8fac8a46c7b0f2fc2a58
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682614"
---
# <a name="hand-physics-extension-service"></a>Servizio di estensione fisica della mano

![Servizio di estensione fisica della mano](../../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

Il servizio di fisica della mano Abilita gli eventi di collisione corpo rigidi e le interazioni con le mani articolate.

## <a name="getting-started-with-hand-physics-extension-service"></a>Introduzione al servizio di estensione della fisica della mano

Aggiungere il servizio di fisica della mano all'elenco dei servizi di estensione e usare il profilo predefinito.

Una volta abilitata, usare qualsiasi proprietà del trigger di Collider per ricevere eventi di collisione da tutte le 10 cifre (e le palme se sono abilitate).

### <a name="prerequisites"></a>Prerequisiti

- Abilitazione del servizio di estensione
- Assegnare un prefabbricato appropriato al giunto dito/Palm.

## <a name="recommendations"></a>Consigli

Quando il servizio viene impostato per impostazione predefinita sul livello "predefinito", è consigliabile usare un livello separato per gli oggetti HandPhysics. In caso contrario, potrebbero verificarsi collisioni indesiderate e/o raycasts non accurati.
