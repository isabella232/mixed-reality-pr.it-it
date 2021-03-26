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
# <a name="teleport-hotspot-experimental"></a><span data-ttu-id="74826-104">Hotspot Teleport [sperimentale]</span><span class="sxs-lookup"><span data-stu-id="74826-104">Teleport Hotspot [Experimental]</span></span>

<span data-ttu-id="74826-105">L'hotspot Teleport è un componente che è possibile aggiungere alla GameObject per garantire che l'utente si trovi in una posizione e un orientamento specifici quando si teletrasportano in tale posizione.</span><span class="sxs-lookup"><span data-stu-id="74826-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="74826-106">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="74826-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="74826-107">Come creare un hotspot Teleport</span><span class="sxs-lookup"><span data-stu-id="74826-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="74826-108">Per creare un hotspot Teleport, aggiungere il componente TeleportHotspot a un oggetto che dispone anche di un componente Collider.</span><span class="sxs-lookup"><span data-stu-id="74826-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Componente hotspot Teleport](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="74826-110">A questo punto, l'indicatore del puntatore a Teleport cambierà il colore quando viene indirizzato su un TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="74826-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="74826-111">Quando l'azione Teleport viene completata sull'hotspot, l'utente si teletrasporta al centro della TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="74826-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="74826-112">Se il flag di orientamento di sostituzione è disconnesso, l'orientamento dell'utente corrisponderà a quello dell'hotspot Teleport.</span><span class="sxs-lookup"><span data-stu-id="74826-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Esempio di hotspot Teleport](../images/teleport/TeleportHotspotExample.gif)
