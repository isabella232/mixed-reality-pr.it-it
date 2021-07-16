---
title: Aggiornamento da HoloToolkit
description: Migrazione da HoloLens Toolkit (HTK) a Mixed Reality Toolkit (MRTK).
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, HTK,
ms.openlocfilehash: b54445dc5ca7a6c01c968929e243a1fc4ca2d107
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281757"
---
# <a name="upgrading-from-holotoolkit"></a>Aggiornamento da HoloToolkit

Guida per la migrazione da HoloLens Toolkit (HTK) a Mixed Reality Toolkit (MRTK).

## <a name="controller-and-hand-input"></a>Controller e input manuale

### <a name="setup-and-configuration"></a>Installazione e configurazione

|         Metodi                  | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Tipo                      | Eventi specifici per i pulsanti, con informazioni sul tipo di input quando pertinenti. | Input basato su azione/movimento, passato tramite eventi. |
| Configurazione                     | Posizionare InputManager nella scena. | Abilitare il sistema di input nel profilo [di configurazione e](../configuration/mixed-reality-configuration-guide.md) specificare un tipo di sistema di input concreto. |
| Configurazione             | Configurato in Inspector, in ogni singolo script nella scena. | Configurata tramite il profilo del sistema di input di realtà mista e il profilo correlato, elencati di seguito. |

Profili correlati:

* Profilo di mapping del controller di realtà mista
* Profilo di visualizzazione del controller di realtà mista
* Profilo movimenti di realtà mista
* Profilo azioni input realtà mista
* Profilo regole azione input realtà mista
* Profilo puntatore di realtà mista

[Le impostazioni del](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider) provider di sguardo fisso vengono modificate nell'oggetto Fotocamera principale nella scena.

I componenti di supporto della piattaforma (ad esempio, Windows Mixed Reality Gestione dispositivi) devono essere aggiunti ai provider di dati del servizio corrispondente.

### <a name="interface-and-event-mappings"></a>Mapping di interfacce ed eventi

Alcuni eventi non hanno più eventi univoci e ora contengono [mixedRealityInputAction.](../features/input/input-actions.md) Queste azioni vengono specificate nel profilo Azioni di input e mappate a controller e piattaforme specifici nel profilo di Mapping controller. Gli eventi `OnInputDown` come ora controllano il tipo MixedRealityInputAction.

Sistemi di input correlati:

* [Cenni preliminari sull'input](../features/input/overview.md)
* [Eventi di input](../features/input/input-events.md)
* [Puntatori di input](../features/input/pointers.md)

| HTK 2017 |  MRTK v2  | Mapping delle azioni |
|----------|-----------|----------------|
| `IControllerInputHandler` | [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mappato al touchpad o alla levetta |
| `IControllerTouchpadHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Mappato al touchpad |
| `IFocusable` | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) | |
| `IGamePadHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IHoldHandler` | [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | Mappato per contenere nel profilo movimenti |
| `IInputClickHandler` | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) |
| `IInputHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Mappato ai pulsanti del controller o al tocco manuale |
| `IManipulationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Mappato alla manipolazione nel profilo movimenti |
| `INavigationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Mappato alla navigazione nel profilo movimenti |
| `IPointerSpecificFocusable` | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) | |
| `ISelectHandler` | [`IMixedRealityInputHandler<float>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mappato alla posizione del trigger |
| `ISourcePositionHandler` | [`IMixedRealityInputHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) o [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mappato alla posizione del puntatore o alla posizione del grip |
| `ISourceRotationHandler` | [`IMixedRealityInputHandler<Quaternion>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) o [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mappato alla posizione del puntatore o alla posizione del grip |
| `ISourceStateHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IXboxControllerHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) E [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mappato ai vari pulsanti e puntini di identificazione personale del controller |

## <a name="camera"></a>Fotocamera

|        Metodi                    | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Configurazione                     | Eliminare MainCamera, aggiungere il prefab MixedRealityCameraParent/MixedRealityCamera/HoloLensCamera alla scena o usare la voce di menu Toolkit > Configura > Applica scena di realtà mista Impostazioni.  | MainCamera con elementi padre in MixedRealityPlayspace via Mixed Reality Toolkit > Aggiungi alla scena e Configura... |
| Configurazione             | Configurazione delle impostazioni della fotocamera eseguita nell'istanza di prefab. | Impostazioni della fotocamera configurate nel [profilo Fotocamera realtà mista.](xref:Microsoft.MixedReality.Toolkit.MixedRealityCameraProfile) |

## <a name="speech"></a>Voce

### <a name="keyword-recognition"></a>Riconoscimento delle parole chiave

|         Metodi                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Configurazione                     | Aggiungere un oggetto SpeechInputSource alla scena. | Il servizio parole chiave (ad esempio, Windows Speech Input Manager) deve essere aggiunto ai provider di dati del sistema di input. |
| Configurazione             | Le parole chiave riconosciute vengono configurate nel controllo SpeechInputSource. | Le parole chiave vengono configurate nel [profilo comandi vocali di realtà mista](../features/input/speech.md). |
| Gestori eventi            | `ISpeechHandler` | [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

### <a name="dictation"></a>Dettatura

|         Metodi                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Configurazione                     | Aggiungere un elemento DictationInputManager alla scena. | Il supporto per la dettatura richiede l'aggiunta del servizio (ad esempio, Windows Gestione input dettatura) ai provider di dati del sistema di input. |
| Gestori eventi            | `IDictationHandler` | `IMixedRealityDictationHandler`[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

## <a name="spatial-awareness--mapping"></a>Consapevolezza spaziale/mapping

### <a name="mesh"></a>Mesh

|         Metodi                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Configurazione                     | Aggiungere il prefab SpatialMapping alla scena. | Abilitare il sistema di consapevolezza spaziale nel profilo di configurazione e aggiungere un osservatore spaziale (ad esempio, Windows Mixed Reality Spatial Mesh Observer) ai provider di dati del sistema di consapevolezza spaziale. |
| Configurazione             | Configurare l'istanza della scena nel controllo . | Configurare le impostazioni nel profilo di ogni osservatore spaziale. |

### <a name="planes"></a>Aerei

|         Metodi                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Configurazione                     | Usare lo `SurfaceMeshesToPlanes` script . | Non ancora implementato. |

### <a name="spatial-understanding"></a>Comprensione spaziale

|       Metodi                      | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Configurazione                     | Aggiungere il prefab SpatialUnderstanding alla scena. | Non ancora implementato. |
| Configurazione             | Configurare l'istanza della scena nel controllo. | Non ancora implementato. |

## <a name="boundary"></a>Limite

|         Metodi                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Configurazione                     | Aggiungere `BoundaryManager` lo script alla scena. | Abilitare il sistema di limiti nel profilo di configurazione. |
| Configurazione             | Configurare l'istanza della scena nel controllo. | Configurare le impostazioni nel profilo Visualizzazione limiti. |

## <a name="sharing"></a>Condivisione

|             Metodi               | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Configurazione                     | Servizio di condivisione: aggiungere il prefab condivisione alla scena. UNet: usare l'esempio SharingWithUNET. | In corso |
| Configurazione             | Configurare le istanze della scena nel controllo. | In corso |

## <a name="ux"></a>Ux

|         Metodi                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Pulsante                     | [Oggetti con interazione](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Button](../features/ux-building-blocks/Button.md) |
| Con interazione                     | [Oggetti con interazione](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Con interazione](../features/ux-building-blocks/Interactable.md) |
| Riquadro             | [Riquadro](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [Riquadro](../features/ux-building-blocks/bounding-box.md) |
| Barra dell'app             | [Barra dell'app](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [Barra dell'app](../features/ux-building-blocks/app-bar.md) |
| Manipolazione di una mano (Grb e Move)   | [HandDraggable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/HandDraggable.cs) | [Gestore di manipolazione](../features/ux-building-blocks/manipulation-handler.md) |
| Manipolazione a due mani (afferrare/spostare/ruotare/ridimensionare)             | [TwoHandManipulatable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/TwoHandManipulatable.cs) | [Gestore di manipolazione](../features/ux-building-blocks/manipulation-handler.md) |
| Tastiera             | [Prefab tastiera]() | [Tastiera di sistema](../features/ux-building-blocks/system-keyboard.md) |
| Descrizione comando             | [Descrizione comando](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_TooltipExample.md) | [Descrizione comando](../features/ux-building-blocks/tooltip.md) |
| Raccolta di oggetti             | [Raccolta di oggetti](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md) | [Raccolta di oggetti](../features/ux-building-blocks/object-collection.md) |
| Solver             | [Solver](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Readme/README_SolverSystem.md) | [Solver](../features/ux-building-blocks/solvers/solver.md) |

## <a name="utilities"></a>Utilità

Alcune utilità sono state riconciliate come duplicati con il sistema risolutore. Se uno degli script necessari non è presente, mettere un problema.

| HTK 2017 |  MRTK v2  |
|----------|-----------|
| Billboard | [`Billboard`](xref:Microsoft.MixedReality.Toolkit.UI.Billboard) |
| Tagalong | [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) o [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) [Risolutore](../features/ux-building-blocks/solvers/Solver.md) |
| FixedAngularSize | [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize)[Risolutore](../features/ux-building-blocks/solvers/solver.md) |
| FpsDisplay | [Sistema di diagnostica](../features/diagnostics/diagnostics-system-getting-started.md) (nel profilo di configurazione) |
| NearFade | Shader standard integrato in [Mixed Reality Toolkit Standard](../features/rendering/mrtk-standard-shader.md) |
