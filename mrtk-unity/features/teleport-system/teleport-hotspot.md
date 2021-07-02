---
title: Hotspot di teletrasporto
description: Documentazione sul componente hotspot di teletrasporto in MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di teletrasporto, hotspot di teletrasporto
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 01ae900800c4a13ca7bafc3391ff51b752a95ae0
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176202"
---
# <a name="teleport-hotspot"></a>Hotspot di teletrasporto

L'hotspot di teletrasporto è un componente che è possibile aggiungere al gameobject per assicurarsi che l'utente si trova in una determinata posizione e orientamento quando si teletrasporta in tale posizione.

## <a name="usage"></a>Utilizzo

### <a name="how-to-create-a-teleport-hotspot"></a>Come creare un hotspot di teletrasporto

Per creare un hotspot di teletrasporto, aggiungere il componente TeleportHotspot a un oggetto che ha anche un componente collisore. 

![Componente Hotspot di teletrasporto](../images/teleport/TeleportHotspotComponent.png)

A questo punto, l'indicatore dell'indicatore di teletrasporto cambierà colore quando viene indirizzato su un TeleportHotspot. Quando l'azione di teletrasporto viene completata sull'hotspot, l'utente si teletrasporterà al centro di TeleportHotspot.

Se il flag di orientamento di sostituzione è disattivato, l'orientamento dell'utente corrisponderà a quello dell'hotspot di teletrasporto.

![Esempio di hotspot di teletrasporto](../images/teleport/TeleportHotspotExample.gif)
