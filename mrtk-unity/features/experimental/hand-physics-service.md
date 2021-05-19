---
title: Servizio di estensione fisica della mano
description: Descrizione Dei servizi di estensione di Fisica della mano.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 401a9d31ed3fbbe0c3e02cb95ffebb024f882fd9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143435"
---
# <a name="hand-physics-extension-services"></a><span data-ttu-id="4862f-104">Servizi di estensione per la fisica della mano</span><span class="sxs-lookup"><span data-stu-id="4862f-104">Hand physics extension services</span></span>

<span data-ttu-id="4862f-105">Il servizio di fisica della mano consente eventi rigidi di collisione del corpo e interazioni con mani articolate.</span><span class="sxs-lookup"><span data-stu-id="4862f-105">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="getting-started-with-hand-physics-extension-service"></a><span data-ttu-id="4862f-106">Introduzione al servizio di estensione della fisica della mano</span><span class="sxs-lookup"><span data-stu-id="4862f-106">Getting started with hand physics extension service</span></span>

<span data-ttu-id="4862f-107">Aggiungere il servizio di fisica della mano all'elenco dei servizi di estensione e usare il profilo predefinito.</span><span class="sxs-lookup"><span data-stu-id="4862f-107">Add the hand physics service to the list of extension services and use the default profile.</span></span>

<span data-ttu-id="4862f-108">Una volta abilitata, usare la proprietà IsTrigger di qualsiasi collisore per ricevere eventi di collisione da tutte e 10 cifre (e palmi se abilitati).</span><span class="sxs-lookup"><span data-stu-id="4862f-108">Once enabled, use any collider's IsTrigger property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>

### <a name="prerequisites"></a><span data-ttu-id="4862f-109">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="4862f-109">Prerequisites</span></span>

- <span data-ttu-id="4862f-110">Abilitato il servizio di estensione</span><span class="sxs-lookup"><span data-stu-id="4862f-110">Enabled the extension service</span></span>
- <span data-ttu-id="4862f-111">Assegnare un prefab appropriato all'giunzione di dito/palmo.</span><span class="sxs-lookup"><span data-stu-id="4862f-111">Assign an appropriate prefab to the finger/palm joint.</span></span>

## <a name="recommendations"></a><span data-ttu-id="4862f-112">Consigli</span><span class="sxs-lookup"><span data-stu-id="4862f-112">Recommendations</span></span>

<span data-ttu-id="4862f-113">Anche se il livello predefinito del servizio è "predefinito", è consigliabile usare un livello separato per gli oggetti HandPhysics.</span><span class="sxs-lookup"><span data-stu-id="4862f-113">While the service defaults to the "default" layer, it is recommended to use a separate layer for HandPhysics objects.</span></span> <span data-ttu-id="4862f-114">In caso contrario, potrebbero verificarsi collisioni indesiderate e/o raycast non accurati.</span><span class="sxs-lookup"><span data-stu-id="4862f-114">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>
