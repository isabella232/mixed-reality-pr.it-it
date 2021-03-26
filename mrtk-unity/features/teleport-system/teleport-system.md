---
title: TeleportSystemOverview
description: Panoramica sull'abilitazione e la disabilitazione del sistema Teleport in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema Teleport,
ms.openlocfilehash: ff24ec720211e02071242f79260bd608fd1a02aa
ms.sourcegitcommit: 4be6f36df9063ccfdce2662e299accc7406b6779
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105555547"
---
# <a name="teleport-system"></a><span data-ttu-id="86df8-104">Sistema Teleport</span><span class="sxs-lookup"><span data-stu-id="86df8-104">Teleport System</span></span>

<span data-ttu-id="86df8-105">Il sistema Teleport è un sottosistema del MRTK che gestisce il Teleporting dell'utente quando l'applicazione usa una visualizzazione opaca.</span><span class="sxs-lookup"><span data-stu-id="86df8-105">The teleport system is a sub-system of the MRTK that handles teleporting the user when the application is using an opaque display.</span></span> <span data-ttu-id="86df8-106">Per le esperienze AR (ad esempio HoloLens), il sistema di teleportazione non è attivo.</span><span class="sxs-lookup"><span data-stu-id="86df8-106">For AR experiences (like HoloLens), the teleportation system is not active.</span></span> <span data-ttu-id="86df8-107">Per esperienze HMD immersive (OpenVR, WMR) è possibile abilitare il sistema Teleport.</span><span class="sxs-lookup"><span data-stu-id="86df8-107">For immersive HMD experiences (OpenVR, WMR) the teleport system can be enabled.</span></span>

## <a name="enabling-and-disabling"></a><span data-ttu-id="86df8-108">Abilitazione e disabilitazione</span><span class="sxs-lookup"><span data-stu-id="86df8-108">Enabling and disabling</span></span>

<span data-ttu-id="86df8-109">Il sistema Teleport può essere abilitato o disabilitato attivando la casella di controllo nel relativo profilo.</span><span class="sxs-lookup"><span data-stu-id="86df8-109">The teleport system can be enabled or disabled by toggling the checkbox in its profile.</span></span>
<span data-ttu-id="86df8-110">Questa operazione può essere eseguita selezionando l'oggetto MixedRealityToolkit nella scena, facendo clic su "Teleport" e quindi attivando la casella di controllo "Enable Teleport System".</span><span class="sxs-lookup"><span data-stu-id="86df8-110">This can be done by selecting the MixedRealityToolkit object in the scene, clicking "Teleport" and then toggling the "Enable Teleport System" checkbox.</span></span>

<span data-ttu-id="86df8-111">Questa operazione può essere eseguita anche in fase di esecuzione:</span><span class="sxs-lookup"><span data-stu-id="86df8-111">This can also be done at runtime:</span></span>

```c#
void DisableTeleportSystem()
{
    CoreServices.TeleportSystem.Disable();
}

void EnableTeleportSystem()
{
    CoreServices.TeleportSystem.Enable();
}
```

## <a name="events"></a><span data-ttu-id="86df8-112">Eventi</span><span class="sxs-lookup"><span data-stu-id="86df8-112">Events</span></span>

<span data-ttu-id="86df8-113">Il sistema Teleport espone gli eventi tramite l' [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interfaccia per fornire segnali quando le azioni Teleport iniziano, terminano o vengono annullate.</span><span class="sxs-lookup"><span data-stu-id="86df8-113">The teleport system exposes events through the [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interface to provide signals on when teleport actions begin, end, or get cancelled.</span></span>
<span data-ttu-id="86df8-114">Per informazioni dettagliate sui meccanismi degli eventi e sul payload associato, vedere la documentazione dell'API collegata.</span><span class="sxs-lookup"><span data-stu-id="86df8-114">See the linked API documentation for more details on the mechanics of the events and their associated payload.</span></span>

## <a name="usage"></a><span data-ttu-id="86df8-115">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="86df8-115">Usage</span></span>

### <a name="how-to-register-for-teleportation-events"></a><span data-ttu-id="86df8-116">Come registrarsi per gli eventi di teleportazione</span><span class="sxs-lookup"><span data-stu-id="86df8-116">How to register for teleportation events</span></span>

<span data-ttu-id="86df8-117">Il codice seguente illustra come creare un monobehavior che resterà in ascolto di eventi di teleportazione.</span><span class="sxs-lookup"><span data-stu-id="86df8-117">The code below shows how to create a MonoBehaviour that will listen for teleportation events.</span></span> <span data-ttu-id="86df8-118">Questo codice presuppone che il sistema Teleport sia abilitato.</span><span class="sxs-lookup"><span data-stu-id="86df8-118">This code assumes that the teleport system is enabled.</span></span>

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Teleport;
using UnityEngine;

public class TeleportHandlerExample : MonoBehaviour, IMixedRealityTeleportHandler
{
    public void OnTeleportCanceled(TeleportEventData eventData)
    {
        Debug.Log("Teleport Cancelled");
    }

    public void OnTeleportCompleted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Completed");
    }

    public void OnTeleportRequest(TeleportEventData eventData)
    {
        Debug.Log("Teleport Request");
    }

    public void OnTeleportStarted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Started");
    }

    void OnEnable()
    {
        // This is the critical call that registers this class for events. Without this
        // class's IMixedRealityTeleportHandler interface will not be called.
        CoreServices.TeleportSystem.RegisterHandler<IMixedRealityTeleportHandler>(this);
    }

    void OnDisable()
    {
        // Unregistering when disabled is important, otherwise this class will continue
        // to receive teleportation events.
        CoreServices.TeleportSystem.UnregisterHandler<IMixedRealityTeleportHandler>(this);
    }
}
```

## <a name="teleporting-on-mrtk"></a><span data-ttu-id="86df8-119">Teleporting su MRTK</span><span class="sxs-lookup"><span data-stu-id="86df8-119">Teleporting on MRTK</span></span>

<span data-ttu-id="86df8-120">Per teletrasportarsi con un controller nei dispositivi MR con configurazioni predefinite, usare levetta.</span><span class="sxs-lookup"><span data-stu-id="86df8-120">To teleport with a controller on MR devices with default configurations, use the thumbstick.</span></span> <span data-ttu-id="86df8-121">Per teletrasportarsi con le mani articolate, creare un gesto con la Palma rivolto verso l'alto con l'indice e il pollice verso l'alto, completando il teletrasporto arricciando il dito dell'indice.</span><span class="sxs-lookup"><span data-stu-id="86df8-121">To teleport with articulated hands, make a gesture with your palm facing up with the index and thumb sticking outwards, completing the teleport by curling the index finger.</span></span> <span data-ttu-id="86df8-122">Per teletrasportarsi con la simulazione di input, vedere la documentazione aggiornata del [servizio di simulazione di input](../input-simulation/input-simulation-service.md).</span><span class="sxs-lookup"><span data-stu-id="86df8-122">To teleport with input simulation, please see our updated [Input Simulation Service documentation](../input-simulation/input-simulation-service.md).</span></span>

  ![Movimento Teleport](../images/teleport/handteleport.gif)