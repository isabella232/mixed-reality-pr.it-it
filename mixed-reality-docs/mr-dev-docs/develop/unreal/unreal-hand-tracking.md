---
title: Tracciamento mano in Unreal
description: Spiega come usare il rilevamento manuale in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realtà mista di Windows, verifica della mano, Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, sviluppo di giochi
ms.openlocfilehash: 5bc120f802c2160282befd1ce6cb8025be21cbaa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683081"
---
# <a name="hand-tracking-in-unreal"></a>Tracciamento mano in Unreal

## <a name="overview"></a>Panoramica

Il sistema di rilevamento manuale usa le palme e le dita di una persona come input. È possibile ottenere la posizione e la rotazione di ogni dito, l'intero Palm e persino i movimenti di mano da usare nel codice. 

## <a name="hand-pose"></a>Hand Pose

Hand Pose consente di tenere traccia delle mani e delle dita dell'utente attivo e di usarla come input, a cui è possibile accedere tramite progetti e C++. È possibile trovare dettagli più tecnici nell'API [Windows. Perception. people. HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) di Unreal. L'API Unreal invia i dati come sistema di coordinate, con segni di selezione sincronizzati con il motore irreale.

### <a name="understanding-the-bone-hierarchy"></a>Informazioni sulla gerarchia ossea

L' `EWMRHandKeypoint` enumerazione descrive la gerarchia ossea della mano. È possibile trovare ogni punto di riferimento della mano elencato nei progetti:

![BP punto di riferimento della mano](images/hand-keypoint-bp.png)

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

È possibile trovare i valori numerici per ogni case enum nella tabella [Windows. Perception. people. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) . Nell'immagine seguente viene illustrato l'intero layout di creazione della mano con i case enum corrispondenti:

![Scheletro mano](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a>Supporto del rilevamento della mano

È possibile usare il rilevamento manuale nei progetti, aggiungendo supporto per il **rilevamento** manuale **> realtà mista di Windows** :

![Verifica della mano BP](images/unreal/hand-tracking-bp.png)

Questa funzione restituisce `true` se il rilevamento manuale è supportato nel dispositivo e `false` se il rilevamento manuale non è disponibile.

![Supporta la verifica della mano BP](images/unreal/supports-hand-tracking-bp.png)

C++: 

Includere `WindowsMixedRealityHandTrackingFunctionLibrary.h`.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>Recupero del rilevamento della mano
È possibile utilizzare **GetHandJointTransform** per restituire i dati spaziali dalla mano. I dati vengono aggiornati ogni frame, ma se ci si trova all'interno di un frame i valori restituiti vengono memorizzati nella cache. Per motivi di prestazioni, non è consigliabile usare una logica intensa in questa funzione. 

![Ottenere la trasformazione congiunta della mano](images/unreal/get-hand-joint-transform.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Suddivisione parametri funzione:

* **Hand** : è il lato sinistro o destro dell'utente
* **Punto di riferimento** : l'osso della mano. 
* **Transform** : coordinate e orientamento della base dell'osso. È possibile richiedere la base dell'osso successivo per ottenere i dati di trasformazione per la fine di un osso. Un osso Tip speciale fornisce la fine del valore distali. 
* **RADIUS** : raggio della base dell'osso.
* **Valore restituito** : true se l'osso rileva il frame, false se l'osso non viene rilevato.

## <a name="hand-live-link-animation"></a>Animazione collegamento dinamico
Le pose della mano vengono esposte all'animazione usando il plug-in [Live link](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).

Se sono abilitati i plug-in della realtà mista di Windows e dei collegamenti dinamici: 
1. Selezionare **finestra > collegamento Live** per aprire la finestra dell'editor di collegamento Live. 
2. Fare clic su **origine** e abilitare l' **origine rilevamento a mano della realtà mista di Windows**

![Origine collegamento dinamico](images/unreal/live-link-source.png)
 
Dopo aver abilitato l'origine e aperto un asset di animazione, espandere la sezione **animazione** nella scheda della **scena anteprima** . vedere anche opzioni aggiuntive (i dettagli sono disponibili nella documentazione del collegamento Live di Unreal, perché il plug-in è in versione beta, il processo potrebbe cambiare in seguito).

![Animazione collegamento dinamico](images/unreal/live-link-animation.png)
 
La gerarchia di animazione della mano è identica a quella di `EWMRHandKeypoint` . L'animazione può essere ridestinata usando **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** :

![Animazione collegamento dinamico 2](images/unreal/live-link-animation2.png)
 
Può anche essere sottoclassato nell'Editor:

![Modifica del mapping di Live link](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a>Accesso ai dati della rete a mano

![Mesh mano](images/unreal/hand-mesh.png)

Prima di poter accedere ai dati della mesh a mano, è necessario:
- Selezionare l'asset **ARSessionConfig** , espandere impostazioni **AR-> Impostazioni mapping del mondo** e selezionare **genera dati mesh da geometria rilevata** . 

Di seguito sono riportati i parametri di mesh predefiniti:

1.  Usare i dati mesh per l'occlusione
2.  Genera collisione per i dati mesh
3.  Genera la mesh NAV per i dati mesh
4.  Eseguire il rendering dei dati mesh nel parametro wireframe-debug che mostra la mesh generata

Questi valori di parametro vengono usati come il mapping spaziale mesh e le impostazioni predefinite mesh a mano. È possibile modificarli in qualsiasi momento in progetti o codice per qualsiasi mesh.

### <a name="c-api-reference"></a>Informazioni di riferimento sulle API C++ 
Usare `EEARObjectClassification` per trovare i valori della mesh mano in tutti gli oggetti rilevabili.
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

I delegati seguenti vengono chiamati quando il sistema rileva qualsiasi oggetto rilevabile, inclusa una mesh mano. 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

Assicurarsi che i gestori del delegato seguano la firma della funzione seguente:

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

È possibile accedere ai dati mesh tramite  `UARTrackedGeometry::GetUnderlyingMesh` :

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a>Riferimento all'API Blueprint

Per lavorare con le mesh mano nei progetti:
1. Aggiungere un componente **ARTrackableNotify** a un attore del progetto

![Notifica ARTrackable](images/unreal/ar-trackable-notify.png)
 
2. Passare al pannello dei **Dettagli** ed espandere la sezione **eventi** . 

![Notifica ARTrackable 2](images/unreal/ar-trackable-notify2.png)
 
3. Sovrascrivi in Aggiungi/Aggiorna/Rimuovi geometria rilevata con i nodi seguenti nel grafico eventi:

![In ARTrackable notifica](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>Raggi mano

È possibile usare un raggio di mano come un dispositivo di puntamento sia in C++ che nei progetti, che espone l'API [Windows. UI. input. Spatial. SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) .

È importante ricordare che, poiché i risultati di tutte le funzioni cambiano ogni frame, sono tutti resi richiamabili. Per ulteriori informazioni sulle funzioni pure e non pure o chiamabili, vedere il progetto GUID utente sulle [funzioni](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)

Per utilizzare i raggi mano nei progetti, cercare le azioni in **HMD realtà mista di Windows** :

![Raggi mano BP](images/unreal/hand-rays-bp.png)
 
Per accedere ad essi in C++, includere nella `WindowsMixedRealityFunctionLibrary.h` parte superiore del file di codice chiamante.

### <a name="enum"></a>Enumerazione
È anche possibile accedere ai case di input in **EHMDInputControllerButtons** , che possono essere usati nei progetti:

![Pulsanti del controller di input](images/unreal/input-controller-buttons.png)

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
    * L'evento può essere attivato in HoloLens 2 tramite il tocco di aria, lo sguardo e il commit oppure "Select" con l' [input vocale](unreal-voice-input.md) abilitato. 
* L' **evento di comprensione** attivato dall'utente. 
    * Questo evento può essere attivato in HoloLens 2 chiudendo le dita dell'utente su un ologramma. 

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

È possibile accedere a questo con i progetti, come illustrato di seguito:

![Indicatore di posa indicatore BP](images/unreal/pointer-pose-info-bp.png)

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

![Ottenere le informazioni sulla posa del puntatore](images/unreal/get-pointer-pose-info.png)

C++: 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **Viene** restituito true se la mano viene afferrata nel frame corrente.

Progetto

![Viene afferrato BP](images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. **Is Select Pressed** restituisce true se l'utente ha attivato SELECT nel frame corrente.

Progetto

![Seleziona BP premuto](images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. Il **pulsante è selezionato** restituisce true se l'evento o il pulsante viene attivato nel frame corrente.

Progetto

![Pulsante è selezionato BP](images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **Ottenere** lo stato di rilevamento del controller restituisce lo stato di rilevamento nel frame corrente.

Progetto

![Ottenere lo stato di rilevamento del controller BP](images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a>Movimenti

Hololens 2 consente di tenere traccia dei movimenti spaziali, il che significa che è possibile acquisire tali movimenti come input. Per ulteriori informazioni sui movimenti, vedere il documento [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) .

È possibile trovare la funzione Blueprint in **input spaziale di realtà mista di Windows** e la funzione C++ aggiungendo `WindowsMixedRealitySpatialInputFunctionLibrary.h` nel file di codice chiamante.

![Acquisisci movimenti](images/unreal/capture-gestures.png)

### <a name="enum"></a>Enumerazione
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
Progetto 

![Tipo di movimento](images/unreal/gesture-type.png)

C++:
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a>Funzione
È possibile abilitare e disabilitare l'acquisizione di movimenti con la `CaptureGestures` funzione. Quando un movimento abilitato genera eventi di input, la funzione restituisce `true` se l'acquisizione del movimento riesce e `false` se si verifica un errore.

Progetto

![Movimenti di acquisizione BP](images/unreal/capture-gestures-bp.png)

C++:
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

Di seguito sono riportati gli eventi chiave che è possibile trovare in progetti e C++: ![ eventi chiave](images/unreal/key-events.png)

![Eventi chiave 2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

## <a name="next-development-checkpoint"></a>Checkpoint di sviluppo successivo

Se si segue il percorso di checkpoint dello sviluppo non reale, si sta per esplorare i blocchi predefiniti di MRTK core. Da qui è possibile passare al blocco predefinito successivo: 

> [!div class="nextstepaction"]
> [Ancoraggi nello spazio locali](unreal-spatial-anchors.md)

In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Fotocamera HoloLens](unreal-hololens-camera.md)

È sempre possibile tornare ai checkpoint di [sviluppo non reali](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.