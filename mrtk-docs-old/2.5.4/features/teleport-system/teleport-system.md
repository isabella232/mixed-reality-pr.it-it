---
title: TeleportSystemOverview
description: Panoramica sull'abilitazione e la disabilitazione del sistema teletrasporto in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di teletrasporto,
ms.openlocfilehash: ee56f62d6e0206249db62d8e7e93cf97cdf8bcc40c35ec0284ebae319870f8ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197641"
---
# <a name="teleport-system"></a>Sistema di teletrasporto

Il sistema di teletrasporto è un sottosistema di MRTK che gestisce il teletrasporto dell'utente quando l'applicazione usa uno schermo opaco. Per le esperienze ar (HoloLens), il sistema di teletrasporto non è attivo. Per esperienze HMD immersive (OpenVR, WMR) è possibile abilitato il sistema di teletrasporto.

## <a name="enabling-and-disabling"></a>Abilitazione e disabilitazione

Il sistema di teletrasporto può essere abilitato o disabilitato attivando la casella di controllo nel relativo profilo.
A tale scopo, selezionare l'oggetto MixedRealityToolkit nella scena, fare clic su "Teletrasporto" e quindi selezionare la casella di controllo "Abilita teletrasporto".

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

Il sistema di teletrasporto espone gli eventi tramite l'interfaccia per fornire segnali quando le azioni di [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) teletrasporto iniziano, terminano o vengono annullate.
Per altri dettagli sui meccanismi degli eventi e sul payload associato, vedere la documentazione dell'API collegata.

## <a name="usage"></a>Utilizzo

### <a name="how-to-register-for-teleportation-events"></a>Come registrarsi per gli eventi di teletrasporto

Il codice seguente illustra come creare un oggetto MonoBehaviour che sarà in ascolto degli eventi di teletrasporto. Questo codice presuppone che il sistema di teletrasporto sia abilitato.

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
