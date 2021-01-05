---
ms.openlocfilehash: 18ccbf3e28eaa2f61157bd9585d633c987e9af48
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2020
ms.locfileid: "97718217"
---
# <a name="426"></a>[4.26](#tab/426)

Per ottenere i dati per i raggi di mano, è necessario usare la funzione Get Motion controller data della sezione precedente. La struttura restituita contiene due parametri che è possibile usare per creare un raggio della mano, la **posizione** e la **rotazione degli obiettivi**. Questi parametri formano un raggio diretto dal gomito. È necessario prenderli e trovare un ologramma a cui punta.

Di seguito è riportato un esempio di come determinare se un raggio di mano raggiunge un widget e imposta un risultato di hit personalizzato:

![Progetto di Get Motion controller data Function](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[4.25](#tab/425)

Per utilizzare i raggi mano nei progetti, cercare le azioni in **HMD realtà mista di Windows**:

![Raggi mano BP](../images/unreal/hand-rays-bp.png)

Per accedere ad essi in C++, includere nella `WindowsMixedRealityFunctionLibrary.h` parte superiore del file di codice chiamante.

### <a name="enum"></a>Enumerazione

È anche possibile accedere ai case di input in **EHMDInputControllerButtons**, che possono essere usati nei progetti:

![Pulsanti del controller di input](../images/unreal/input-controller-buttons.png)

Per l'accesso in C++, usare la `EHMDInputControllerButtons` classe enum:
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

Di seguito è riportata una suddivisione dei due case enum applicabili:

* **Selezionare** l'evento di selezione attivato dall'utente.
    * Attivato in HoloLens 2 da aria-Tap, sguardo e commit, oppure con l' [input vocale](../unreal-voice-input.md) abilitato.
* L' **evento di comprensione** attivato dall'utente.
    * Attivato in HoloLens 2 chiudendo le dita dell'utente su un ologramma.

È possibile accedere allo stato di rilevamento della mesh mano in C++ tramite l' `EHMDTrackingStatus` enumerazione illustrata di seguito:

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

Di seguito è riportata una suddivisione dei due case enum applicabili:

* **NotTracked** : la mano non è visibile
* **Rilevato** : la mano viene rilevata completamente

### <a name="struct"></a>Struct

Lo struct PointerPoseInfo può fornire informazioni sui dati della mano seguenti:

* **Origin** : origine della mano
* **Direzione** : direzione della mano
* Vettore **attivo** della mano
* **Orientamento** -quaternione orientamento
* **Stato di rilevamento** -stato di rilevamento corrente

È possibile accedere allo struct PointerPoseInfo tramite i progetti, come illustrato di seguito:

![Indicatore di posa indicatore BP](../images/unreal/pointer-pose-info-bp.png)

O con C++:

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a>Funzioni

Tutte le funzioni elencate di seguito possono essere chiamate in ogni frame, che consente il monitoraggio continuo.

1. **Get Pointer post info** restituisce informazioni complete sulla direzione del raggio di mano nel frame corrente.

Progetto

![Ottenere le informazioni sulla posa del puntatore](../images/unreal/get-pointer-pose-info.png)

C++:
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **Viene** restituito true se la mano viene afferrata nel frame corrente.

Progetto

![Viene afferrato BP](../images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. **Is Select Pressed** restituisce true se l'utente ha attivato SELECT nel frame corrente.

Progetto

![Seleziona BP premuto](../images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. Il **pulsante è selezionato** restituisce true se l'evento o il pulsante viene attivato nel frame corrente.

Progetto

![Pulsante è selezionato BP](../images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **Ottenere** lo stato di rilevamento del controller restituisce lo stato di rilevamento nel frame corrente.

Progetto

![Ottenere lo stato di rilevamento del controller BP](../images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```