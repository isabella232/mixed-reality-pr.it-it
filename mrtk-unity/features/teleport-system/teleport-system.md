---
title: Sistema di teletrasporto
description: Panoramica sull'abilitazione e la disabilitazione del sistema di teletrasporto in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di teletrasporto,
ms.openlocfilehash: 7a49b1fea36eb1809c57abee4cede1216c07d5bf
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176179"
---
# <a name="teleport-system"></a><span data-ttu-id="50f07-104">Sistema di teletrasporto</span><span class="sxs-lookup"><span data-stu-id="50f07-104">Teleport system</span></span>

<span data-ttu-id="50f07-105">Il sistema di teletrasporto è un sottosistema di MRTK che gestisce il teletrasporto dell'utente quando l'applicazione usa uno schermo opaco.</span><span class="sxs-lookup"><span data-stu-id="50f07-105">The teleport system is a sub-system of the MRTK that handles teleporting the user when the application is using an opaque display.</span></span> <span data-ttu-id="50f07-106">Per le esperienze ar (ad HoloLens), il sistema di teletrasporto non è attivo.</span><span class="sxs-lookup"><span data-stu-id="50f07-106">For AR experiences (like HoloLens), the teleportation system is not active.</span></span> <span data-ttu-id="50f07-107">Per esperienze HMD immersive (OpenVR, WMR) è possibile abilitato il sistema di teletrasporto.</span><span class="sxs-lookup"><span data-stu-id="50f07-107">For immersive HMD experiences (OpenVR, WMR) the teleport system can be enabled.</span></span>

## <a name="enabling-and-disabling"></a><span data-ttu-id="50f07-108">Abilitazione e disabilitazione</span><span class="sxs-lookup"><span data-stu-id="50f07-108">Enabling and disabling</span></span>

<span data-ttu-id="50f07-109">Il sistema di teletrasporto può essere abilitato o disabilitato attivando o disattivando la casella di controllo nel profilo.</span><span class="sxs-lookup"><span data-stu-id="50f07-109">The teleport system can be enabled or disabled by toggling the checkbox in its profile.</span></span>
<span data-ttu-id="50f07-110">A tale scopo, selezionare l'oggetto MixedRealityToolkit nella scena, fare clic su "Teleport" e quindi attivare o disattivare la casella di controllo "Enable Teleport System" (Abilita sistema di teletrasporto).</span><span class="sxs-lookup"><span data-stu-id="50f07-110">This can be done by selecting the MixedRealityToolkit object in the scene, clicking "Teleport" and then toggling the "Enable Teleport System" checkbox.</span></span>

<span data-ttu-id="50f07-111">Questa operazione può essere eseguita anche in fase di esecuzione:</span><span class="sxs-lookup"><span data-stu-id="50f07-111">This can also be done at runtime:</span></span>

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

## <a name="events"></a><span data-ttu-id="50f07-112">Eventi</span><span class="sxs-lookup"><span data-stu-id="50f07-112">Events</span></span>

<span data-ttu-id="50f07-113">Il sistema di teletrasporto espone gli eventi tramite l'interfaccia per fornire segnali quando le azioni di [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) teletrasporto iniziano, terminano o vengono annullate.</span><span class="sxs-lookup"><span data-stu-id="50f07-113">The teleport system exposes events through the [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interface to provide signals on when teleport actions begin, end, or get cancelled.</span></span>
<span data-ttu-id="50f07-114">Per altri dettagli sui meccanismi degli eventi e sul payload associato, vedere la documentazione dell'API collegata.</span><span class="sxs-lookup"><span data-stu-id="50f07-114">See the linked API documentation for more details on the mechanics of the events and their associated payload.</span></span>

## <a name="usage"></a><span data-ttu-id="50f07-115">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="50f07-115">Usage</span></span>

### <a name="how-to-register-for-teleportation-events"></a><span data-ttu-id="50f07-116">Come registrarsi per gli eventi di teletrasporto</span><span class="sxs-lookup"><span data-stu-id="50f07-116">How to register for teleportation events</span></span>

<span data-ttu-id="50f07-117">Il codice seguente illustra come creare un oggetto MonoBehaviour che sarà in ascolto degli eventi di teletrasporto.</span><span class="sxs-lookup"><span data-stu-id="50f07-117">The code below shows how to create a MonoBehaviour that will listen for teleportation events.</span></span> <span data-ttu-id="50f07-118">Questo codice presuppone che il sistema di teletrasporto sia abilitato.</span><span class="sxs-lookup"><span data-stu-id="50f07-118">This code assumes that the teleport system is enabled.</span></span>

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

## <a name="teleporting-on-mrtk"></a><span data-ttu-id="50f07-119">Teletrasporto su MRTK</span><span class="sxs-lookup"><span data-stu-id="50f07-119">Teleporting on MRTK</span></span>

<span data-ttu-id="50f07-120">Per teletrasportare con un controller nei dispositivi MR con configurazioni predefinite, usare la levetta.</span><span class="sxs-lookup"><span data-stu-id="50f07-120">To teleport with a controller on MR devices with default configurations, use the thumbstick.</span></span> <span data-ttu-id="50f07-121">Per teletrasportarti con le mani articolate, fai un movimento con il palmo rivolto verso l'alto con l'indice e il pollice che si fiocchi verso l'esterno, completando il teletrasporto arricciando il dito indice.</span><span class="sxs-lookup"><span data-stu-id="50f07-121">To teleport with articulated hands, make a gesture with your palm facing up with the index and thumb sticking outwards, completing the teleport by curling the index finger.</span></span> <span data-ttu-id="50f07-122">Per teletrasportare con la simulazione di input, vedere la documentazione aggiornata del [servizio di simulazione input.](../input-simulation/input-simulation-service.md)</span><span class="sxs-lookup"><span data-stu-id="50f07-122">To teleport with input simulation, please see our updated [Input Simulation Service documentation](../input-simulation/input-simulation-service.md).</span></span>

  ![Movimento di teletrasporto](../images/teleport/handteleport.gif)
