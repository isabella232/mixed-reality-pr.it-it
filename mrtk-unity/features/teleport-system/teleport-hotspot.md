---
title: Hotspot di teletrasporto
description: Documentazione sul componente hotspot teletrasporto in MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, sistema di teletrasporto, hotspot teletrasporto
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 2d6160570b43ca931d46f4ec04c604b53b18d731
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647045"
---
# <a name="teleport-hotspot"></a>Hotspot di teletrasporto

L'hotspot di teletrasporto è un componente che è possibile aggiungere al gameobject per assicurarsi che l'utente si trova in una determinata posizione e orientamento quando si teletrasporta in tale posizione.

## <a name="usage"></a>Utilizzo

### <a name="how-to-create-a-teleport-hotspot"></a>Come creare un hotspot di teletrasporto

Per creare un hotspot di teletrasporto, aggiungere il componente TeleportHotspot a un oggetto che dispone anche di un componente collisore. 

![Componente hotspot di teletrasporto](../images/teleport/TeleportHotspotComponent.png)

A questo punto, l'indicatore del puntatore del teletrasporto cambierà colore quando viene indirizzato su un TeleportHotspot. Quando l'azione di teletrasporto viene completata sull'hotspot, l'utente si teletrasporterà al centro del TeleportHotspot.

Se il flag di orientamento dell'override è disattivato, l'orientamento dell'utente corrisponderà a quello dell'area sensibile al teletrasporto.

![Esempio di hotspot di teletrasporto](../images/teleport/TeleportHotspotExample.gif)
