---
title: TeleportSystemOverview
description: Panoramica sull'abilitazione e la disabilitazione del sistema Teleport in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema Teleport,
ms.openlocfilehash: 2dfccc009510183f6c6b60d46ef4df312d2dc046
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104686871"
---
# <a name="teleport-system"></a>Sistema Teleport

Il sistema Teleport è un sottosistema del MRTK che gestisce il Teleporting dell'utente quando l'applicazione usa una visualizzazione opaca. Per le esperienze AR (ad esempio HoloLens), il sistema di teleportazione non è attivo. Per esperienze HMD immersive (OpenVR, WMR) è possibile abilitare il sistema Teleport.

## <a name="enabling-and-disabling"></a>Abilitazione e disabilitazione

Il sistema Teleport può essere abilitato o disabilitato attivando la casella di controllo nel relativo profilo.
Questa operazione può essere eseguita selezionando l'oggetto MixedRealityToolkit nella scena, facendo clic su "Teleport" e quindi attivando la casella di controllo "Enable Teleport System".

Questa operazione può essere eseguita anche in fase di esecuzione:

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

## <a name="events"></a>Eventi

Il sistema Teleport espone gli eventi tramite l' [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interfaccia per fornire segnali quando le azioni Teleport iniziano, terminano o vengono annullate.
Per informazioni dettagliate sui meccanismi degli eventi e sul payload associato, vedere la documentazione dell'API collegata.

## <a name="usage"></a>Utilizzo

### <a name="how-to-register-for-teleportation-events"></a>Come registrarsi per gli eventi di teleportazione

Il codice seguente illustra come creare un monobehavior che resterà in ascolto di eventi di teleportazione. Questo codice presuppone che il sistema Teleport sia abilitato.

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
