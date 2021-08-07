---
ms.openlocfilehash: fb8b5b509ef83e2a4f9d978dbf0faebbf3e0be1d10d6697f16cfb9366d7a2edb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187421"
---
# <a name="426"></a>[4.26](#tab/426)

Per ottenere i dati per i raggi della mano, è consigliabile usare la funzione Get Motion Controller Data della sezione precedente. La struttura restituita contiene due parametri che è possibile usare per creare un raggio della mano, la **posizione dell'obiettivo** e la **rotazione dell'obiettivo.** Questi parametri formano un raggio diretto dal gomito. È consigliabile prenderli e trovare un ologramma a cui punta.

Di seguito è riportato un esempio per determinare se un raggio della mano raggiunge un widget e impostare un risultato di hit personalizzato:

![Progetto della funzione get motion controller data](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[4.25](#tab/425)

Per usare Hand Rays in Blueprints, cercare le azioni in Windows Mixed Reality **HMD:**

![Bp dei raggi della mano](../images/unreal/hand-rays-bp.png)

Per accedervi in C++, includere `WindowsMixedRealityFunctionLibrary.h` all'inizio del file di codice chiamante.

### <a name="enum"></a>Enumerazione

È anche possibile accedere ai case di input in **EHMDInputControllerButtons,** che possono essere usati in Blueprints:

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

Di seguito è riportata una suddivisione dei due case di enumerazione applicabili:

* **Selezionare** - Evento Select attivato dall'utente.
    * Attivato in HoloLens 2 tramite tocco, sguardo e commit o pronunciando "Seleziona" con [l'input vocale](../unreal-voice-input.md) abilitato.
* **Afferra -** Evento Di afferrare attivato dall'utente.
    * Attivato in HoloLens 2 chiudendo le dita dell'utente su un ologramma.

È possibile accedere allo stato di rilevamento della mesh della mano in C++ tramite `EHMDTrackingStatus` l'enumerazione illustrata di seguito:

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

Di seguito è riportata una suddivisione dei due case di enumerazione applicabili:

* **NotTracked** : la mano non è visibile
* **Tracciato :** la mano è completamente tracciata

### <a name="struct"></a>Struct

Lo struct PointerPoseInfo può fornire informazioni sui dati della mano seguenti:

* **Origine:** origine della mano
* **Direzione** : direzione della mano
* **Up** : vettore up della mano
* **Orientamento** : quaternione di orientamento
* **Stato rilevamento** : stato di rilevamento corrente

È possibile accedere alla struttura PointerPoseInfo tramite Blueprints, come illustrato di seguito:

![Informazioni sulla posizione del puntatore BP](../images/unreal/pointer-pose-info-bp.png)

Oppure con C++:

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

1. **Ottieni informazioni sulla posizione del** puntatore restituisce informazioni complete sulla direzione del raggio della mano nel fotogramma corrente.

Progetto:

![Ottenere informazioni sulla posizione del puntatore](../images/unreal/get-pointer-pose-info.png)

C++:
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **Se Afferrato** restituisce true, se la mano viene afferrata nel frame corrente.

Progetto:

![È afferrato BP](../images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. **Se Seleziona premuto** restituisce true se l'utente ha attivato Seleziona nel frame corrente.

Progetto:

![È selezionato premuto BP](../images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. **Is Button Clicked** restituisce true se l'evento o il pulsante viene attivato nel frame corrente.

Progetto:

![È stato fatto clic sul pulsante BP](../images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **Get Controller Tracking Status** (Ottieni stato rilevamento controller) restituisce lo stato di rilevamento nel frame corrente.

Progetto:

![Ottenere lo stato di rilevamento del controller BP](../images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```