---
title: Perdita del rilevamento in Unity
description: Informazioni su come gestire la perdita di rilevamento manuale e predefinita all'interno di un'app di realtà mista Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, rilevamento della perdita, tracciamento dell'immagine di perdita, polling, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale
ms.openlocfilehash: fe11c88bec60042901bd7ebb5c55116da97b6e28f0e44e889ef517a03d67245a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211353"
---
# <a name="tracking-loss-in-unity"></a>Perdita del rilevamento in Unity

Quando il dispositivo non è in grado di individuarsi nel mondo, l'app verifica la perdita. Per impostazione predefinita, Unity sospende il ciclo di aggiornamento e visualizza un'immagine iniziale per l'utente ogni volta che viene perso il rilevamento. Una volta recuperato il rilevamento, l'immagine iniziale viene chiusa e il ciclo di aggiornamento continua.

In alternativa, l'utente può gestire manualmente questa transizione rifiutando esplicitamente l'impostazione. Tutto il contenuto sembra essere bloccato durante la perdita di rilevamento se non viene eseguita alcuna operazione per gestirlo.

## <a name="default-handling"></a>Gestione predefinita

Per impostazione predefinita, il ciclo di aggiornamento e tutti i messaggi e gli eventi si arresteranno per la durata del rilevamento della perdita. Allo stesso tempo, verrà visualizzata un'immagine per l'utente. È possibile personalizzare questa immagine selezionando Edit->Impostazioni->Player (Modifica->Impostazioni->Player), facendo clic su Splash Image (Immagine iniziale) e impostando l'immagine Holographic Tracking Loss (Perdita di tracciamento olografico).

## <a name="manual-handling"></a>Gestione manuale

Per gestire manualmente la perdita di rilevamento, è necessario passare alla scheda Impostazioni di **Edit** Project Impostazioni Player Universal Windows Platform (Modifica impostazioni della piattaforma Universal Windows di  >  **Project Impostazioni**  >  **Player)** Windows Holographic e deselezionare  >    >    >   "On Tracking Loss Pause and Show Image". Successivamente, è necessario gestire il rilevamento delle modifiche con le API specificate di seguito.

**Spazio dei nomi:** *UnityEngine.XR.WSA*<br>
**Tipo:** *WorldManager*

* World Manager espone un evento per rilevare il rilevamento di perdita/perdita *(WorldManager.OnPositionalLocatorStateChanged)* e una proprietà per eseguire una query sullo stato corrente (*WorldManager.state*)
* Quando lo stato di rilevamento non è attivo, la fotocamera non apparirà traslata nel mondo virtuale anche quando l'utente traduce. Gli oggetti non corrisponderanno più ad alcuna posizione fisica e tutti gli oggetti appariranno bloccati.

Quando si gestisce il rilevamento delle modifiche in modo personalizzato, è necessario eseguire il polling della proprietà di stato per ogni frame o gestire *l'evento OnPositionalLocatorStateChanged.*

### <a name="polling"></a>Polling

Lo stato più importante è *PositionalLocatorState.Active,* il che significa che il rilevamento è completamente funzionale. Qualsiasi altro stato comporta solo delta rotazionali per la fotocamera principale. Ad esempio:

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>Gestione dell'evento OnPositionalLocatorStateChanged

Più comodamente, è anche possibile sottoscrivere *OnPositionalLocatorStateChanged* per gestire le transizioni:

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

## <a name="see-also"></a>Vedi anche

* [Gestione della perdita di rilevamento in DirectX](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
