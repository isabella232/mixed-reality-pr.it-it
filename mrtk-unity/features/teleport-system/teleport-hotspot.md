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
# <a name="teleport-hotspot-experimental"></a><span data-ttu-id="927f8-104">Teletrasporto hotspot [sperimentale]</span><span class="sxs-lookup"><span data-stu-id="927f8-104">Teleport Hotspot [Experimental]</span></span>

<span data-ttu-id="927f8-105">L'hotspot di teletrasporto è un componente che è possibile aggiungere al gameobject per assicurarsi che l'utente si trova in una determinata posizione e orientamento quando si teletrasporta in tale posizione.</span><span class="sxs-lookup"><span data-stu-id="927f8-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="927f8-106">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="927f8-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="927f8-107">Come creare un hotspot di teletrasporto</span><span class="sxs-lookup"><span data-stu-id="927f8-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="927f8-108">Per creare un hotspot di teletrasporto, aggiungere il componente TeleportHotspot a un oggetto che ha anche un componente collisore.</span><span class="sxs-lookup"><span data-stu-id="927f8-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Componente Hotspot di teletrasporto](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="927f8-110">A questo punto, l'indicatore dell'indicatore di teletrasporto cambierà colore quando viene indirizzato su un TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="927f8-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="927f8-111">Quando l'azione di teletrasporto viene completata sull'hotspot, l'utente si teletrasporterà al centro di TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="927f8-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="927f8-112">Se il flag di orientamento di sostituzione è disattivato, l'orientamento dell'utente corrisponderà a quello dell'hotspot di teletrasporto.</span><span class="sxs-lookup"><span data-stu-id="927f8-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Esempio di hotspot di teletrasporto](../images/teleport/TeleportHotspotExample.gif)
