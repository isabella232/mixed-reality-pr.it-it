---
ms.openlocfilehash: 21c29b2c8d540378259200cc834f7a36065f8ab3
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581104"
---
# <a name="426"></a>[4.26](#tab/426)

La gerarchia è descritta da `EHandKeypoint` enum:

![Immagine delle opzioni di Bluprint del punto di riferimento della mano](../images/hand-keypoint-bp.png)

È possibile ottenere tutti questi dati dalle mani di un utente usando la funzione **Get Motion controller data** . Questa funzione restituisce una struttura **XRMotionControllerData** . Di seguito è riportato uno script di progetto di esempio che analizza la struttura XRMotionControllerData per ottenere le posizioni congiunte della mano e disegna un sistema di coordinate di debug in corrispondenza della posizione di ogni joint.

![Progetto di Get sguardi data Function connesso a line Trace by Channel Function](../images/unreal-hand-tracking-img-03.png)

È importante controllare se la struttura è valida e se è una mano. In caso contrario, è possibile ottenere un comportamento non definito nell'accesso a posizioni, rotazioni e matrici di raggi.

# <a name="425"></a>[4.25](#tab/425)

L' `EWMRHandKeypoint` enumerazione descrive la gerarchia ossea della mano. È possibile trovare ogni punto di riferimento della mano elencato nei progetti:

![BP punto di riferimento della mano](../images/hand-keypoint-bp.png)

L'enumerazione C++ completa è elencata di seguito:
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

È possibile trovare i valori numerici per ogni case enum nella tabella [Windows. Perception. people. HandJointKind](/uwp/api/windows.perception.people.handjointkind) .

### <a name="supporting-hand-tracking"></a>Supporto del rilevamento della mano

È possibile usare il rilevamento manuale nei progetti, aggiungendo supporto per il **rilevamento** manuale **> realtà mista di Windows**:

![Verifica della mano BP](../images/unreal/hand-tracking-bp.png)

Questa funzione restituisce `true` se il rilevamento manuale è supportato nel dispositivo e `false` se il rilevamento manuale non è disponibile.

![Supporta la verifica della mano BP](../images/unreal/supports-hand-tracking-bp.png)

C++:

Includere `WindowsMixedRealityHandTrackingFunctionLibrary.h`.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>Recupero del rilevamento della mano

È possibile utilizzare **GetHandJointTransform** per restituire i dati spaziali dalla mano. I dati vengono aggiornati ogni frame, ma se ci si trova all'interno di un frame i valori restituiti vengono memorizzati nella cache. Per motivi di prestazioni, non è consigliabile usare una logica intensa in questa funzione.

![Ottenere la trasformazione congiunta della mano](../images/unreal/get-hand-joint-transform.png)

C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Ecco una suddivisione dei parametri della funzione di GetHandJointTransform:

* **Hand** : può essere il lato sinistro o destro dell'utente.
* **Punto di riferimento** : l'osso della mano.
* **Transform** : coordinate e orientamento della base dell'osso. È possibile richiedere la base dell'osso successivo per ottenere i dati di trasformazione per la fine di un osso. Un osso Tip speciale fornisce la fine del valore distali.
* * * RADIUS: raggio della base dell'osso.
* * * Valore restituito: true se l'osso rileva il frame, false se l'osso non viene rilevato.