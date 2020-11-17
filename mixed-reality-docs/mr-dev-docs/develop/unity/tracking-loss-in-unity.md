---
title: Perdita del rilevamento in Unity
description: Gestione della perdita di rilevamento all'interno di un'app Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, perdita di rilevamento, immagine della perdita del rilevamento, polling, auricolare a realtà mista, auricolare di realtà mista di Windows, auricolare di realtà virtuale
ms.openlocfilehash: 52b81069e6b9f94a2a6a4fb552be4234cf43d1f0
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678420"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="5e73c-104">Perdita del rilevamento in Unity</span><span class="sxs-lookup"><span data-stu-id="5e73c-104">Tracking loss in Unity</span></span>

<span data-ttu-id="5e73c-105">Quando il dispositivo non è in grado di trovarsi nel mondo, l'app riscontra una "perdita di rilevamento".</span><span class="sxs-lookup"><span data-stu-id="5e73c-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="5e73c-106">Per impostazione predefinita, Unity sospende il ciclo di aggiornamento e visualizza un'immagine iniziale per l'utente.</span><span class="sxs-lookup"><span data-stu-id="5e73c-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="5e73c-107">Quando il rilevamento viene recuperato, l'immagine iniziale viene interrotta e il ciclo di aggiornamento continua.</span><span class="sxs-lookup"><span data-stu-id="5e73c-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="5e73c-108">In alternativa, l'utente può gestire manualmente questa transizione scegliendo l'impostazione.</span><span class="sxs-lookup"><span data-stu-id="5e73c-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="5e73c-109">Se non viene eseguita alcuna operazione per la gestione, tutto il contenuto sembrerà bloccato nel corpo durante la perdita del rilevamento.</span><span class="sxs-lookup"><span data-stu-id="5e73c-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="5e73c-110">Gestione predefinita</span><span class="sxs-lookup"><span data-stu-id="5e73c-110">Default Handling</span></span>

<span data-ttu-id="5e73c-111">Per impostazione predefinita, il ciclo di aggiornamento dell'app, nonché tutti i messaggi e gli eventi, si arresteranno per la durata della perdita del rilevamento.</span><span class="sxs-lookup"><span data-stu-id="5e73c-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="5e73c-112">Allo stesso tempo, all'utente verrà visualizzata un'immagine.</span><span class="sxs-lookup"><span data-stu-id="5e73c-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="5e73c-113">È possibile personalizzare questa immagine scegliendo Modifica->impostazioni->Player, facendo clic su immagine iniziale e impostando l'immagine della perdita del rilevamento olografico.</span><span class="sxs-lookup"><span data-stu-id="5e73c-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="5e73c-114">Gestione manuale</span><span class="sxs-lookup"><span data-stu-id="5e73c-114">Manual Handling</span></span>

<span data-ttu-id="5e73c-115">Per gestire manualmente la perdita del rilevamento, è necessario passare a **modifica**  >  **Impostazioni progetto**  >  **Player**  >  **piattaforma UWP (Universal Windows Platform) impostazioni**  >  **immagine schermata iniziale**  >  **Windows olografico** e deselezionare "in rilevamento perdita sospensione e Mostra immagine".</span><span class="sxs-lookup"><span data-stu-id="5e73c-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="5e73c-116">Successivamente, è necessario gestire le modifiche di rilevamento con le API specificate di seguito.</span><span class="sxs-lookup"><span data-stu-id="5e73c-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="5e73c-117">**Spazio dei nomi:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="5e73c-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="5e73c-118">**Tipo:** *WorldManager*</span><span class="sxs-lookup"><span data-stu-id="5e73c-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="5e73c-119">World Manager espone un evento per rilevare il rilevamento perso/acquisito (*WorldManager. OnPositionalLocatorStateChanged*) e una proprietà per eseguire una query sullo stato corrente (*WorldManager. state*)</span><span class="sxs-lookup"><span data-stu-id="5e73c-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="5e73c-120">Quando lo stato di rilevamento non è attivo, la fotocamera non sembra tradursi nel mondo virtuale, anche quando l'utente si traduce.</span><span class="sxs-lookup"><span data-stu-id="5e73c-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="5e73c-121">Ciò significa che gli oggetti non corrisponderanno più a una posizione fisica e tutti verranno visualizzati corpo bloccati.</span><span class="sxs-lookup"><span data-stu-id="5e73c-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="5e73c-122">Quando si gestiscono le modifiche di rilevamento, è necessario eseguire il polling per la proprietà di stato ogni frame o gestire l'evento *OnPositionalLocatorStateChanged* .</span><span class="sxs-lookup"><span data-stu-id="5e73c-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="5e73c-123">Polling</span><span class="sxs-lookup"><span data-stu-id="5e73c-123">Polling</span></span>

<span data-ttu-id="5e73c-124">Lo stato più importante è *PositionalLocatorState. Active* , che significa che il rilevamento è completamente funzionante.</span><span class="sxs-lookup"><span data-stu-id="5e73c-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="5e73c-125">Qualsiasi altro stato comporterà solo Delta rotazionali alla fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="5e73c-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="5e73c-126">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="5e73c-126">For example:</span></span>

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="5e73c-127">Gestione dell'evento OnPositionalLocatorStateChanged</span><span class="sxs-lookup"><span data-stu-id="5e73c-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="5e73c-128">In alternativa, è anche possibile eseguire la sottoscrizione a *OnPositionalLocatorStateChanged* per gestire le transizioni:</span><span class="sxs-lookup"><span data-stu-id="5e73c-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a><span data-ttu-id="5e73c-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5e73c-129">See also</span></span>
* [<span data-ttu-id="5e73c-130">Gestione della perdita di rilevamento in DirectX</span><span class="sxs-lookup"><span data-stu-id="5e73c-130">Handling tracking loss in DirectX</span></span>](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
