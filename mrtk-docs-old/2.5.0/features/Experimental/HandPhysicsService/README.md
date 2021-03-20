---
title: README_HandPhysicsExtensionService
description: Descrizione servizi di estensione della fisica della mano.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: db5ef8ca5a6b3e30a796071eb7a0a389e66eae37
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104691818"
---
# <a name="hand-physics-extension-service"></a><span data-ttu-id="76545-104">Servizio di estensione fisica della mano</span><span class="sxs-lookup"><span data-stu-id="76545-104">Hand physics extension service</span></span>

![Servizio di estensione fisica della mano](../../Images/HandPhysics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="76545-106">Il servizio di fisica della mano Abilita gli eventi di collisione corpo rigidi e le interazioni con le mani articolate.</span><span class="sxs-lookup"><span data-stu-id="76545-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="getting-started-with-hand-physics-extension-service"></a><span data-ttu-id="76545-107">Introduzione al servizio di estensione della fisica della mano</span><span class="sxs-lookup"><span data-stu-id="76545-107">Getting started with hand physics extension service</span></span>

<span data-ttu-id="76545-108">Aggiungere il servizio di fisica della mano all'elenco dei servizi di estensione e usare il profilo predefinito.</span><span class="sxs-lookup"><span data-stu-id="76545-108">Add the hand physics service to the list of extension services and use the default profile.</span></span>

<span data-ttu-id="76545-109">Una volta abilitata, usare qualsiasi proprietà del trigger di Collider per ricevere eventi di collisione da tutte le 10 cifre (e le palme se sono abilitate).</span><span class="sxs-lookup"><span data-stu-id="76545-109">Once enabled, use any collider's IsTrigger property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>

### <a name="prerequisites"></a><span data-ttu-id="76545-110">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="76545-110">Prerequisites</span></span>

- <span data-ttu-id="76545-111">Abilitazione del servizio di estensione</span><span class="sxs-lookup"><span data-stu-id="76545-111">Enabled the extension service</span></span>
- <span data-ttu-id="76545-112">Assegnare un prefabbricato appropriato al giunto dito/Palm.</span><span class="sxs-lookup"><span data-stu-id="76545-112">Assign an appropriate prefab to the finger/palm joint.</span></span>

## <a name="recommendations"></a><span data-ttu-id="76545-113">Consigli</span><span class="sxs-lookup"><span data-stu-id="76545-113">Recommendations</span></span>

<span data-ttu-id="76545-114">Quando il servizio viene impostato per impostazione predefinita sul livello "predefinito", è consigliabile usare un livello separato per gli oggetti HandPhysics.</span><span class="sxs-lookup"><span data-stu-id="76545-114">While the service defaults to the "default" layer, it is recommended to use a separate layer for HandPhysics objects.</span></span> <span data-ttu-id="76545-115">In caso contrario, potrebbero verificarsi collisioni indesiderate e/o raycasts non accurati.</span><span class="sxs-lookup"><span data-stu-id="76545-115">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>
