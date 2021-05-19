---
title: Panoramica del sistema di teletrasporto
description: Panoramica sull'abilitazione e la disabilitazione del sistema di teletrasporto in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di teletrasporto,
ms.openlocfilehash: a44ad1827597dd0b27bc88a9420a3b251f934afd
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144142"
---
# <a name="teleport-system"></a>Sistema di teletrasporto

Il sistema di teletrasporto è un sottosistema di MRTK che gestisce il teletrasporto dell'utente quando l'applicazione usa uno schermo opaco. Per le esperienze AR (ad esempio HoloLens), il sistema di teletrasporto non è attivo. Per esperienze HMD immersive (OpenVR, WMR) è possibile abilitato il sistema di teletrasporto.

## <a name="enabling-and-disabling"></a>Abilitazione e disabilitazione

Il sistema di teletrasporto può essere abilitato o disabilitato attivando o disattivando la casella di controllo nel profilo.
A tale scopo, selezionare l'oggetto MixedRealityToolkit nella scena, fare clic su "Teleport" e quindi attivare o disattivare la casella di controllo "Enable Teleport System" (Abilita sistema di teletrasporto).

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

## <a name="teleporting-on-mrtk"></a>Teletrasporto su MRTK

Per teletrasportare con un controller nei dispositivi MR con configurazioni predefinite, usare la levetta. Per teletrasportarti con le mani articolate, fai un movimento con il palmo rivolto verso l'alto con l'indice e il pollice che si fiocchi verso l'esterno, completando il teletrasporto arricciando il dito indice. Per teletrasportare con la simulazione di input, vedere la documentazione aggiornata del [servizio di simulazione input](../input-simulation/input-simulation-service.md).

  ![Movimento di teletrasporto](../images/teleport/handteleport.gif)