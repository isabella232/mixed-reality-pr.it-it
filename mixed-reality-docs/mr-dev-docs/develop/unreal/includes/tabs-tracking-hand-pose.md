---
ms.openlocfilehash: ec1246085989b4b157504e9b8551694d6116e6f08789fa669200e5425ef75cc6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187418"
---
# <a name="426"></a>[4.26](#tab/426)

La gerarchia è descritta `EHandKeypoint` dall'enumerazione :

![Immagine delle opzioni di bluprint del punto chiave a mano](../images/hand-keypoint-bp.png)

È possibile ottenere tutti questi dati dalle mani di un utente usando la **funzione Get Motion Controller Data** . Tale funzione restituisce una **struttura XRMotionControllerData.** Di seguito è riportato uno script blueprint di esempio che analizza la struttura XRMotionControllerData per ottenere le posizioni delle giunzioni delle mani e disegna un sistema di coordinate di debug in corrispondenza della posizione di ogni giunzione.

![Progetto della funzione get gaze data connessa alla traccia linea in base alla funzione del canale](../images/unreal-hand-tracking-img-03.png)

È importante verificare se la struttura è valida e che si tratta di una mano. In caso contrario, è possibile ottenere un comportamento non definito nell'accesso a posizioni, rotazioni e matrici di raggi.

# <a name="425"></a>[4.25](#tab/425)

`EWMRHandKeypoint`L'enumerazione descrive la gerarchia dell'osso della mano. È possibile trovare ogni punto chiave della mano elencato nei progetti:

![Punto chiave mano BP](../images/hand-keypoint-bp.png)

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

È possibile trovare i valori numerici per ogni case di enumerazione nel [Windows. Tabella Perception.People.HandJointKind.](/uwp/api/windows.perception.people.handjointkind)

### <a name="supporting-hand-tracking"></a>Supporto del rilevamento manuale

È possibile usare il tracciamento manuale in Blueprints aggiungendo **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:

![Rilevamento della mano BP](../images/unreal/hand-tracking-bp.png)

Questa funzione restituisce `true` se il tracciamento manuale è supportato nel dispositivo e `false` se il tracciamento manuale non è disponibile.

![Supporta il rilevamento delle mani BP](../images/unreal/supports-hand-tracking-bp.png)

C++:

Includere `WindowsMixedRealityHandTrackingFunctionLibrary.h`.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>Ottenere il rilevamento delle mani

È possibile usare **GetHandJointTransform** per restituire dati spaziali dalla mano. I dati aggiornano ogni frame, ma se ci si trova all'interno di un frame, i valori restituiti vengono memorizzati nella cache. Non è consigliabile avere una logica pesante in questa funzione per motivi di prestazioni.

![Get Hand Joint Transform](../images/unreal/get-hand-joint-transform.png)

C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Ecco una suddivisione dei parametri di funzione di GetHandJointTransform:

* **Mano:** può essere l'utente a sinistra o a destra.
* **Punto chiave:** l'osso della mano.
* **Trasforma:** coordinate e orientamento della base dell'osso. È possibile richiedere la base dell'osso successivo per ottenere i dati di trasformazione per la fine di un osso. Un osso di punta speciale restituisce la fine della distal.
* **Raggio: raggio della base dell'osso.
* **Valore restituito: true se l'osso viene tracciato da questo fotogramma, false se l'osso non viene tracciato.