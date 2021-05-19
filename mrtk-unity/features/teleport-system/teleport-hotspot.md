---
title: Hotspot di teletrasporto
description: Documentazione sul componente hotspot di teletrasporto in MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di teletrasporto, hotspot teletrasporto
ms.openlocfilehash: 0cbdad3c038d457109077b742d3f453d63436ae4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144438"
---
# <a name="teleport-hotspot-experimental"></a>Teletrasporto hotspot [sperimentale]

L'hotspot di teletrasporto è un componente che è possibile aggiungere al gameobject per assicurarsi che l'utente si trova in una determinata posizione e orientamento quando si teletrasporta in tale posizione.

## <a name="usage"></a>Utilizzo

### <a name="how-to-create-a-teleport-hotspot"></a>Come creare un hotspot di teletrasporto

Per creare un hotspot di teletrasporto, aggiungere il componente TeleportHotspot a un oggetto che ha anche un componente collisore. 

![Componente Hotspot di teletrasporto](../images/teleport/TeleportHotspotComponent.png)

A questo punto, l'indicatore dell'indicatore di teletrasporto cambierà colore quando viene indirizzato su un TeleportHotspot. Quando l'azione di teletrasporto viene completata sull'hotspot, l'utente si teletrasporterà al centro di TeleportHotspot.

Se il flag di orientamento di sostituzione è disattivato, l'orientamento dell'utente corrisponderà a quello dell'hotspot di teletrasporto.

![Esempio di hotspot di teletrasporto](../images/teleport/TeleportHotspotExample.gif)
