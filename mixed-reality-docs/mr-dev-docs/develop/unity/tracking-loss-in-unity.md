---
title: Perdita del rilevamento in Unity
description: Informazioni su come gestire la perdita di rilevamento manuale e predefinita in un'app per realtà mista Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, perdita di rilevamento, immagine della perdita del rilevamento, polling, auricolare a realtà mista, auricolare di realtà mista di Windows, auricolare di realtà virtuale
ms.openlocfilehash: 39ce4e079886b27ed35c419a3b3913c6700e0d32
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009851"
---
# <a name="tracking-loss-in-unity"></a>Perdita del rilevamento in Unity

Quando il dispositivo non è in grado di trovarsi nel mondo, l'app riscontra una "perdita di rilevamento". Per impostazione predefinita, Unity sospende il ciclo di aggiornamento e visualizza un'immagine iniziale per l'utente in qualsiasi momento in cui il rilevamento viene perso. Dopo che il rilevamento è stato recuperato, l'immagine iniziale viene rilasciata e il ciclo di aggiornamento continua.

In alternativa, l'utente può gestire manualmente questa transizione scegliendo l'impostazione. Se non viene eseguita alcuna operazione per la gestione, tutto il contenuto sembrerà bloccato nel corpo durante la perdita del rilevamento.

## <a name="default-handling"></a>Gestione predefinita

Il ciclo di aggiornamento e tutti i messaggi e gli eventi si arresteranno per la durata della perdita del rilevamento per impostazione predefinita. Allo stesso tempo, all'utente verrà visualizzata un'immagine. È possibile personalizzare questa immagine scegliendo Modifica->impostazioni->Player, facendo clic su immagine iniziale e impostando l'immagine della perdita del rilevamento olografico.

## <a name="manual-handling"></a>Gestione manuale

Per gestire manualmente la perdita del rilevamento, è necessario passare a **modifica**  >  **Impostazioni progetto**  >  **Player**  >  **piattaforma UWP (Universal Windows Platform) impostazioni**  >  **immagine schermata iniziale**  >  **Windows olografico** e deselezionare "in rilevamento perdita sospensione e Mostra immagine". Successivamente, è necessario gestire le modifiche di rilevamento con le API specificate di seguito.

**Spazio dei nomi:** *UnityEngine. XR. WSA*<br>
**Tipo:** *WorldManager*

* World Manager espone un evento per rilevare il rilevamento perso/acquisito (*WorldManager. OnPositionalLocatorStateChanged*) e una proprietà per eseguire una query sullo stato corrente (*WorldManager. state*)
* Quando lo stato di rilevamento non è attivo, la fotocamera non sembra tradursi nel mondo virtuale anche quando l'utente si traduce. Gli oggetti non corrisponderanno più a una posizione fisica e tutti verranno visualizzati corpo bloccati.

Quando si gestiscono le modifiche di rilevamento autonomamente, è necessario eseguire il polling per la proprietà state di ogni frame o gestire l'evento *OnPositionalLocatorStateChanged* .

### <a name="polling"></a>Polling

Lo stato più importante è *PositionalLocatorState. Active*, che significa che il rilevamento è completamente funzionante. Qualsiasi altro stato comporterà solo Delta rotazionali alla fotocamera principale. Ad esempio:

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

Più facilmente, è anche possibile sottoscrivere *OnPositionalLocatorStateChanged* per gestire le transizioni:

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
