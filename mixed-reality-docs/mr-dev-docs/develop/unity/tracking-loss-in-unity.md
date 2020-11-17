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
# <a name="tracking-loss-in-unity"></a>Perdita del rilevamento in Unity

Quando il dispositivo non è in grado di trovarsi nel mondo, l'app riscontra una "perdita di rilevamento". Per impostazione predefinita, Unity sospende il ciclo di aggiornamento e visualizza un'immagine iniziale per l'utente. Quando il rilevamento viene recuperato, l'immagine iniziale viene interrotta e il ciclo di aggiornamento continua.

In alternativa, l'utente può gestire manualmente questa transizione scegliendo l'impostazione. Se non viene eseguita alcuna operazione per la gestione, tutto il contenuto sembrerà bloccato nel corpo durante la perdita del rilevamento.

## <a name="default-handling"></a>Gestione predefinita

Per impostazione predefinita, il ciclo di aggiornamento dell'app, nonché tutti i messaggi e gli eventi, si arresteranno per la durata della perdita del rilevamento. Allo stesso tempo, all'utente verrà visualizzata un'immagine. È possibile personalizzare questa immagine scegliendo Modifica->impostazioni->Player, facendo clic su immagine iniziale e impostando l'immagine della perdita del rilevamento olografico.

## <a name="manual-handling"></a>Gestione manuale

Per gestire manualmente la perdita del rilevamento, è necessario passare a **modifica**  >  **Impostazioni progetto**  >  **Player**  >  **piattaforma UWP (Universal Windows Platform) impostazioni**  >  **immagine schermata iniziale**  >  **Windows olografico** e deselezionare "in rilevamento perdita sospensione e Mostra immagine". Successivamente, è necessario gestire le modifiche di rilevamento con le API specificate di seguito.

**Spazio dei nomi:** *UnityEngine. XR. WSA*<br>
**Tipo:** *WorldManager*

* World Manager espone un evento per rilevare il rilevamento perso/acquisito (*WorldManager. OnPositionalLocatorStateChanged*) e una proprietà per eseguire una query sullo stato corrente (*WorldManager. state*)
* Quando lo stato di rilevamento non è attivo, la fotocamera non sembra tradursi nel mondo virtuale, anche quando l'utente si traduce. Ciò significa che gli oggetti non corrisponderanno più a una posizione fisica e tutti verranno visualizzati corpo bloccati.

Quando si gestiscono le modifiche di rilevamento, è necessario eseguire il polling per la proprietà di stato ogni frame o gestire l'evento *OnPositionalLocatorStateChanged* .

### <a name="polling"></a>Polling

Lo stato più importante è *PositionalLocatorState. Active* , che significa che il rilevamento è completamente funzionante. Qualsiasi altro stato comporterà solo Delta rotazionali alla fotocamera principale. Ad esempio:

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

In alternativa, è anche possibile eseguire la sottoscrizione a *OnPositionalLocatorStateChanged* per gestire le transizioni:

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

## <a name="see-also"></a>Vedere anche
* [Gestione della perdita di rilevamento in DirectX](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
