---
title: HandPhysicsExtensionService
description: Descrizione servizi di estensione della fisica della mano.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: f958f964fcfd4880770dad3952ce69621c7dd931
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685614"
---
# <a name="hand-physics-extension-services"></a><span data-ttu-id="c9fcc-104">Servizi di estensione della fisica della mano</span><span class="sxs-lookup"><span data-stu-id="c9fcc-104">Hand physics extension services</span></span>

<span data-ttu-id="c9fcc-105">Il servizio di fisica della mano Abilita gli eventi di collisione corpo rigidi e le interazioni con le mani articolate.</span><span class="sxs-lookup"><span data-stu-id="c9fcc-105">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="getting-started-with-hand-physics-extension-service"></a><span data-ttu-id="c9fcc-106">Introduzione al servizio di estensione della fisica della mano</span><span class="sxs-lookup"><span data-stu-id="c9fcc-106">Getting started with hand physics extension service</span></span>

<span data-ttu-id="c9fcc-107">Aggiungere il servizio di fisica della mano all'elenco dei servizi di estensione e usare il profilo predefinito.</span><span class="sxs-lookup"><span data-stu-id="c9fcc-107">Add the hand physics service to the list of extension services and use the default profile.</span></span>

<span data-ttu-id="c9fcc-108">Una volta abilitata, usare qualsiasi proprietà del trigger di Collider per ricevere eventi di collisione da tutte le 10 cifre (e le palme se sono abilitate).</span><span class="sxs-lookup"><span data-stu-id="c9fcc-108">Once enabled, use any collider's IsTrigger property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c9fcc-109">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="c9fcc-109">Prerequisites</span></span>

- <span data-ttu-id="c9fcc-110">Abilitazione del servizio di estensione</span><span class="sxs-lookup"><span data-stu-id="c9fcc-110">Enabled the extension service</span></span>
- <span data-ttu-id="c9fcc-111">Assegnare un prefabbricato appropriato al giunto dito/Palm.</span><span class="sxs-lookup"><span data-stu-id="c9fcc-111">Assign an appropriate prefab to the finger/palm joint.</span></span>

## <a name="recommendations"></a><span data-ttu-id="c9fcc-112">Consigli</span><span class="sxs-lookup"><span data-stu-id="c9fcc-112">Recommendations</span></span>

<span data-ttu-id="c9fcc-113">Quando il servizio viene impostato per impostazione predefinita sul livello "predefinito", è consigliabile usare un livello separato per gli oggetti HandPhysics.</span><span class="sxs-lookup"><span data-stu-id="c9fcc-113">While the service defaults to the "default" layer, it is recommended to use a separate layer for HandPhysics objects.</span></span> <span data-ttu-id="c9fcc-114">In caso contrario, potrebbero verificarsi collisioni indesiderate e/o raycasts non accurati.</span><span class="sxs-lookup"><span data-stu-id="c9fcc-114">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>
