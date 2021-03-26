---
title: TeleportHotspot
description: Documentazione sul componente hotspot Teleport in MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema Teleport, hotspot Teleport
ms.openlocfilehash: 986105dd771c38b1e26fd9f86df90224110591a4
ms.sourcegitcommit: 4be6f36df9063ccfdce2662e299accc7406b6779
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105582963"
---
# <a name="teleport-hotspot-experimental"></a>Hotspot Teleport [sperimentale]

L'hotspot Teleport è un componente che è possibile aggiungere alla GameObject per garantire che l'utente si trovi in una posizione e un orientamento specifici quando si teletrasportano in tale posizione.

## <a name="usage"></a>Utilizzo

### <a name="how-to-create-a-teleport-hotspot"></a>Come creare un hotspot Teleport

Per creare un hotspot Teleport, aggiungere il componente TeleportHotspot a un oggetto che dispone anche di un componente Collider. 

![Componente hotspot Teleport](../images/teleport/TeleportHotspotComponent.png)

A questo punto, l'indicatore del puntatore a Teleport cambierà il colore quando viene indirizzato su un TeleportHotspot. Quando l'azione Teleport viene completata sull'hotspot, l'utente si teletrasporta al centro della TeleportHotspot.

Se il flag di orientamento di sostituzione è disconnesso, l'orientamento dell'utente corrisponderà a quello dell'hotspot Teleport.

![Esempio di hotspot Teleport](../images/teleport/TeleportHotspotExample.gif)
