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
# <a name="teleport-hotspot"></a><span data-ttu-id="2ef04-104">Hotspot di teletrasporto</span><span class="sxs-lookup"><span data-stu-id="2ef04-104">Teleport Hotspot</span></span>

<span data-ttu-id="2ef04-105">L'hotspot di teletrasporto è un componente che è possibile aggiungere al gameobject per assicurarsi che l'utente si trova in una determinata posizione e orientamento quando si teletrasporta in tale posizione.</span><span class="sxs-lookup"><span data-stu-id="2ef04-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="2ef04-106">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="2ef04-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="2ef04-107">Come creare un hotspot di teletrasporto</span><span class="sxs-lookup"><span data-stu-id="2ef04-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="2ef04-108">Per creare un hotspot di teletrasporto, aggiungere il componente TeleportHotspot a un oggetto che dispone anche di un componente collisore.</span><span class="sxs-lookup"><span data-stu-id="2ef04-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Componente hotspot di teletrasporto](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="2ef04-110">A questo punto, l'indicatore del puntatore del teletrasporto cambierà colore quando viene indirizzato su un TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="2ef04-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="2ef04-111">Quando l'azione di teletrasporto viene completata sull'hotspot, l'utente si teletrasporterà al centro del TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="2ef04-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="2ef04-112">Se il flag di orientamento dell'override è disattivato, l'orientamento dell'utente corrisponderà a quello dell'area sensibile al teletrasporto.</span><span class="sxs-lookup"><span data-stu-id="2ef04-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Esempio di hotspot di teletrasporto](../images/teleport/TeleportHotspotExample.gif)
