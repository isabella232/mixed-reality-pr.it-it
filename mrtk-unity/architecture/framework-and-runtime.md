---
title: Framework e runtime
description: Informazioni correlate al framework e al runtime in MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: a44e5f32cda2803091e27ae1a2c30a1976385a2f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121609"
---
# <a name="framework-and-runtime"></a><span data-ttu-id="10365-104">Framework e runtime</span><span class="sxs-lookup"><span data-stu-id="10365-104">Framework and runtime</span></span>

## <a name="changes-to-the-scene"></a><span data-ttu-id="10365-105">Modifiche alla scena</span><span class="sxs-lookup"><span data-stu-id="10365-105">Changes to the scene</span></span>

<span data-ttu-id="10365-106">Per usare il toolkit, è necessario che nella scena sia presente un'istanza dello script MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="10365-106">To use the toolkit an instance of the MixedRealityToolkit script must be in your scene.</span></span>
<span data-ttu-id="10365-107">Per aggiungerne uno, usa l'opzione di menu Mixed Reality Toolkit -> Aggiungi alla scena e Configura.</span><span class="sxs-lookup"><span data-stu-id="10365-107">To add one use the menu option: Mixed Reality Toolkit -> Add to Scene and Configure.</span></span> <span data-ttu-id="10365-108">Questa istanza è responsabile della registrazione, dell'aggiornamento e della rimozione dei servizi.</span><span class="sxs-lookup"><span data-stu-id="10365-108">This instance is responsible for registering, updating and tearing down services.</span></span> <span data-ttu-id="10365-109">È anche la posizione in cui viene scelto il profilo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="10365-109">It's also where your configuration profile is chosen.</span></span>

<span data-ttu-id="10365-110">Oltre ad aggiungere il GameObject MRTK alla scena, l'opzione di menu:</span><span class="sxs-lookup"><span data-stu-id="10365-110">Apart from adding the MRTK GameObject to the scene the menu option will also:</span></span>

- <span data-ttu-id="10365-111">Aggiungere MixedRealityPlayspace, che viene usato da molti altri componenti MRTK per eseguire trasformazioni di spazio globale e locale.</span><span class="sxs-lookup"><span data-stu-id="10365-111">Add the MixedRealityPlayspace, which is used by many other MRTK components to reason over world and local space transformations.</span></span>
- <span data-ttu-id="10365-112">Sposta la fotocamera principale come elemento figlio di MixedRealityPlayspace (e aggiungendo anche alcuni script correlati all'input e allo sguardo fisso alla fotocamera principale, che consentono di usare UnityUI e la funzionalità di input correlata allo sguardo).</span><span class="sxs-lookup"><span data-stu-id="10365-112">Move the main Camera as a child of the MixedRealityPlayspace (and also adding some input and gaze related scripts to the main Camera, which help power UnityUI and gaze related input functionality).</span></span>

## <a name="mixedrealitytoolkit-object-and-runtime"></a><span data-ttu-id="10365-113">Oggetto MixedRealityToolkit e runtime</span><span class="sxs-lookup"><span data-stu-id="10365-113">MixedRealityToolkit object and runtime</span></span>

<span data-ttu-id="10365-114">MrTK include diversi servizi di base.</span><span class="sxs-lookup"><span data-stu-id="10365-114">The MRTK has several core services.</span></span> <span data-ttu-id="10365-115">Alcuni si coordinano l'uno con l'altro; altri sono indipendenti.</span><span class="sxs-lookup"><span data-stu-id="10365-115">Some coordinate with one another; others are independent.</span></span>
<span data-ttu-id="10365-116">Tutti condividono lo stesso ciclo di vita( avvio, registrazione, aggiornamento e rimozione) e questo ciclo di vita si distingue dal ciclo di vita MonoBehaviour di Unity.</span><span class="sxs-lookup"><span data-stu-id="10365-116">All share the same life cycle - startup, registration, update and teardown - and this life cycle stands apart from Unity's MonoBehaviour life cycle.</span></span> <span data-ttu-id="10365-117">Questo [post medio](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) illustra alcune delle informazioni di base e della motivazione alla base di questo approccio.</span><span class="sxs-lookup"><span data-stu-id="10365-117">This [medium post](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) explains some of the background and motivation behind this approach.</span></span> <span data-ttu-id="10365-118">MRTK ha un singolo oggetto che gestisce la durata e il runtime dei servizi.</span><span class="sxs-lookup"><span data-stu-id="10365-118">MRTK has a single object that manages life and runtime of its services.</span></span>

<span data-ttu-id="10365-119">Questa entità garantisce che:</span><span class="sxs-lookup"><span data-stu-id="10365-119">This entity ensures that:</span></span>

- <span data-ttu-id="10365-120">All'avvio del gioco, l'individuazione e l'inizializzazione dei servizi vengono avviate in un ordine predefinito.</span><span class="sxs-lookup"><span data-stu-id="10365-120">when the game starts, discovery and initialization of services happens in a pre-defined order.</span></span>
- <span data-ttu-id="10365-121">fornisce un meccanismo che consente ai servizi di registrarsi (ad esempio,"Supporto questo servizio!") e per consentire ad altri chiamanti di ottenere informazioni su tali servizi.</span><span class="sxs-lookup"><span data-stu-id="10365-121">it provides a mechanism for services to register themselves (i.e. “I support this service!”) and for other callers to get a hold of those services.</span></span>
- <span data-ttu-id="10365-122">fornisce le chiamate Update()/LateUpdate() e le inoltra ai vari servizi, ad esempio tramite UpdateAllServices/LateUpdateAllServices.</span><span class="sxs-lookup"><span data-stu-id="10365-122">it provides the Update()/LateUpdate() calls and forwards them onto the various services (i.e. via UpdateAllServices/LateUpdateAllServices).</span></span>
