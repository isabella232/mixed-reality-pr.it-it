---
title: Framework e Runtime
description: Informazioni correlate a Framework e Runtime in MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: de91dfacb26e9757403d869ae6363289b455cff1
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782346"
---
# <a name="framework-and-runtime"></a><span data-ttu-id="e2a0b-104">Framework e Runtime</span><span class="sxs-lookup"><span data-stu-id="e2a0b-104">Framework and runtime</span></span>

## <a name="changes-to-the-scene"></a><span data-ttu-id="e2a0b-105">Modifiche alla scena</span><span class="sxs-lookup"><span data-stu-id="e2a0b-105">Changes to the scene</span></span>

<span data-ttu-id="e2a0b-106">Per usare il Toolkit, un'istanza dello script MixedRealityToolkit deve trovarsi nella scena.</span><span class="sxs-lookup"><span data-stu-id="e2a0b-106">To use the toolkit an instance of the MixedRealityToolkit script must be in your scene.</span></span>
<span data-ttu-id="e2a0b-107">Per aggiungerne uno, usare l'opzione di menu: Mixed Reality Toolkit-> aggiungere alla scena e configurare.</span><span class="sxs-lookup"><span data-stu-id="e2a0b-107">To add one use the menu option: Mixed Reality Toolkit -> Add to Scene and Configure.</span></span> <span data-ttu-id="e2a0b-108">Questa istanza è responsabile della registrazione, dell'aggiornamento e dello strappo dei servizi.</span><span class="sxs-lookup"><span data-stu-id="e2a0b-108">This instance is responsible for registering, updating and tearing down services.</span></span> <span data-ttu-id="e2a0b-109">È anche la scelta del profilo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="e2a0b-109">It's also where your configuration profile is chosen.</span></span>

<span data-ttu-id="e2a0b-110">Oltre ad aggiungere il GameObject MRTK alla scena, l'opzione di menu consente anche di:</span><span class="sxs-lookup"><span data-stu-id="e2a0b-110">Apart from adding the MRTK GameObject to the scene the menu option will also:</span></span>

- <span data-ttu-id="e2a0b-111">Aggiungere MixedRealityPlayspace, usato da molti altri componenti di MRTK per ragionare sulle trasformazioni di spazio globale e locale.</span><span class="sxs-lookup"><span data-stu-id="e2a0b-111">Add the MixedRealityPlayspace, which is used by many other MRTK components to reason over world and local space transformations.</span></span>
- <span data-ttu-id="e2a0b-112">Spostare la fotocamera principale come elemento figlio di MixedRealityPlayspace (e aggiungere anche un input e guardare gli script correlati alla fotocamera principale, che consentono a Power UnityUI e di guardare le funzionalità di input correlate).</span><span class="sxs-lookup"><span data-stu-id="e2a0b-112">Move the main Camera as a child of the MixedRealityPlayspace (and also adding some input and gaze related scripts to the main Camera, which help power UnityUI and gaze related input functionality).</span></span>

## <a name="mixedrealitytoolkit-object-and-runtime"></a><span data-ttu-id="e2a0b-113">Oggetto MixedRealityToolkit e Runtime</span><span class="sxs-lookup"><span data-stu-id="e2a0b-113">MixedRealityToolkit object and runtime</span></span>

<span data-ttu-id="e2a0b-114">Il MRTK dispone di diversi servizi di base.</span><span class="sxs-lookup"><span data-stu-id="e2a0b-114">The MRTK has several core services.</span></span> <span data-ttu-id="e2a0b-115">Una coordinata tra loro; altre sono indipendenti.</span><span class="sxs-lookup"><span data-stu-id="e2a0b-115">Some coordinate with one another; others are independent.</span></span>
<span data-ttu-id="e2a0b-116">Tutti condividono lo stesso ciclo di vita, ovvero startup, registrazione, aggiornamento e teardown, e questo ciclo di vita si differenzia dal ciclo di vita monobehavior di Unity.</span><span class="sxs-lookup"><span data-stu-id="e2a0b-116">All share the same life cycle - startup, registration, update and teardown - and this life cycle stands apart from Unity's MonoBehaviour life cycle.</span></span> <span data-ttu-id="e2a0b-117">Questo [post di medie dimensioni](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) illustra alcuni dei retroscena e la motivazione alla base di questo approccio.</span><span class="sxs-lookup"><span data-stu-id="e2a0b-117">This [medium post](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) explains some of the background and motivation behind this approach.</span></span> <span data-ttu-id="e2a0b-118">MRTK dispone di un singolo oggetto che gestisce la durata e il runtime dei servizi.</span><span class="sxs-lookup"><span data-stu-id="e2a0b-118">MRTK has a single object that manages life and runtime of its services.</span></span>

<span data-ttu-id="e2a0b-119">Questa entità garantisce che:</span><span class="sxs-lookup"><span data-stu-id="e2a0b-119">This entity ensures that:</span></span>

- <span data-ttu-id="e2a0b-120">all'avvio del gioco, l'individuazione e l'inizializzazione dei servizi vengono eseguite in un ordine predefinito.</span><span class="sxs-lookup"><span data-stu-id="e2a0b-120">when the game starts, discovery and initialization of services happens in a pre-defined order.</span></span>
- <span data-ttu-id="e2a0b-121">fornisce un meccanismo per la registrazione dei servizi (ad esempio "supporto di questo servizio!") e per altri chiamanti per ottenere i servizi.</span><span class="sxs-lookup"><span data-stu-id="e2a0b-121">it provides a mechanism for services to register themselves (i.e. “I support this service!”) and for other callers to get a hold of those services.</span></span>
- <span data-ttu-id="e2a0b-122">fornisce le chiamate Update ()/LateUpdate () e le invia ai vari servizi, ad esempio tramite UpdateAllServices/LateUpdateAllServices.</span><span class="sxs-lookup"><span data-stu-id="e2a0b-122">it provides the Update()/LateUpdate() calls and forwards them onto the various services (i.e. via UpdateAllServices/LateUpdateAllServices).</span></span>
