---
title: TeleportSystemOverview
description: Panoramica sull'abilitazione e la disabilitazione del sistema Teleport in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema Teleport,
ms.openlocfilehash: 872ae21b36dff81af144752c175ed80ff0e6c245
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782994"
---
# <a name="teleport-system"></a><span data-ttu-id="42963-104">Sistema Teleport</span><span class="sxs-lookup"><span data-stu-id="42963-104">Teleport system</span></span>

<span data-ttu-id="42963-105">Il sistema Teleport è un sottosistema del MRTK che gestisce il Teleporting dell'utente quando l'applicazione usa una visualizzazione opaca.</span><span class="sxs-lookup"><span data-stu-id="42963-105">The teleport system is a sub-system of the MRTK that handles teleporting the user when the application is using an opaque display.</span></span> <span data-ttu-id="42963-106">Per le esperienze AR (ad esempio HoloLens), il sistema di teleportazione non è attivo.</span><span class="sxs-lookup"><span data-stu-id="42963-106">For AR experiences (like HoloLens), the teleportation system is not active.</span></span> <span data-ttu-id="42963-107">Per esperienze HMD immersive (OpenVR, WMR) è possibile abilitare il sistema Teleport.</span><span class="sxs-lookup"><span data-stu-id="42963-107">For immersive HMD experiences (OpenVR, WMR) the teleport system can be enabled.</span></span>

## <a name="enabling-and-disabling"></a><span data-ttu-id="42963-108">Abilitazione e disabilitazione</span><span class="sxs-lookup"><span data-stu-id="42963-108">Enabling and disabling</span></span>

<span data-ttu-id="42963-109">Il sistema Teleport può essere abilitato o disabilitato attivando la casella di controllo nel relativo profilo.</span><span class="sxs-lookup"><span data-stu-id="42963-109">The teleport system can be enabled or disabled by toggling the checkbox in its profile.</span></span>
<span data-ttu-id="42963-110">Questa operazione può essere eseguita selezionando l'oggetto MixedRealityToolkit nella scena, facendo clic su "Teleport" e quindi attivando la casella di controllo "Enable Teleport System".</span><span class="sxs-lookup"><span data-stu-id="42963-110">This can be done by selecting the MixedRealityToolkit object in the scene, clicking "Teleport" and then toggling the "Enable Teleport System" checkbox.</span></span>

<span data-ttu-id="42963-111">Questa operazione può essere eseguita anche in fase di esecuzione:</span><span class="sxs-lookup"><span data-stu-id="42963-111">This can also be done at runtime:</span></span>

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

## <a name="events"></a><span data-ttu-id="42963-112">Eventi</span><span class="sxs-lookup"><span data-stu-id="42963-112">Events</span></span>

<span data-ttu-id="42963-113">Il sistema Teleport espone gli eventi tramite l' [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interfaccia per fornire segnali quando le azioni Teleport iniziano, terminano o vengono annullate.</span><span class="sxs-lookup"><span data-stu-id="42963-113">The teleport system exposes events through the [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interface to provide signals on when teleport actions begin, end, or get cancelled.</span></span>
<span data-ttu-id="42963-114">Per informazioni dettagliate sui meccanismi degli eventi e sul payload associato, vedere la documentazione dell'API collegata.</span><span class="sxs-lookup"><span data-stu-id="42963-114">See the linked API documentation for more details on the mechanics of the events and their associated payload.</span></span>

## <a name="usage"></a><span data-ttu-id="42963-115">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="42963-115">Usage</span></span>

### <a name="how-to-register-for-teleportation-events"></a><span data-ttu-id="42963-116">Come registrarsi per gli eventi di teleportazione</span><span class="sxs-lookup"><span data-stu-id="42963-116">How to register for teleportation events</span></span>

<span data-ttu-id="42963-117">Il codice seguente illustra come creare un monobehavior che resterà in ascolto di eventi di teleportazione.</span><span class="sxs-lookup"><span data-stu-id="42963-117">The code below shows how to create a MonoBehaviour that will listen for teleportation events.</span></span> <span data-ttu-id="42963-118">Questo codice presuppone che il sistema Teleport sia abilitato.</span><span class="sxs-lookup"><span data-stu-id="42963-118">This code assumes that the teleport system is enabled.</span></span>

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
