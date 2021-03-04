---
title: HTKToMRTKPortingGuide
description: Migrazione da HTK a MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, HTK,
ms.openlocfilehash: 4c43d3a19e43343d616805566c2a12dcd285bd26
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782128"
---
# <a name="porting-guide"></a>Guida alla conversione

## <a name="controller-and-hand-input"></a>Input del controller e della mano

### <a name="setup-and-configuration"></a>Installazione e configurazione

|         Metodi                  | HTK 2017 |  MRTK V2  |
|---------------------------|----------|-----------|
| Tipo                      | Eventi specifici per i pulsanti, con informazioni sul tipo di input quando pertinente. | Input basato su azione/movimento, passato attraverso gli eventi. |
| Configurazione                     | Posizionare il InputManager nella scena. | Abilitare il sistema di input nel [profilo di configurazione](../configuration/mixed-reality-configuration-guide.md) e specificare un tipo di sistema di input concreto. |
| Configurazione             | Configurato in Inspector, in ogni singolo script nella scena. | Configurato tramite il profilo di sistema di input della realtà mista e il relativo profilo, elencati di seguito. |

Profili correlati:

* Profilo di mapping del controller realtà misto
* Profilo di visualizzazione del controller di realtà misto
* Profilo movimenti realtà mista
* Profilo azioni di input realtà mista
* Profilo delle regole di azione di input realtà mista
* Profilo puntatore realtà mista

Le impostazioni del [provider di sguardi](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider) vengono modificate sull'oggetto fotocamera principale della scena.

I componenti di supporto della piattaforma, ad esempio Gestione dispositivi di realtà mista di Windows, devono essere aggiunti ai provider di dati del servizio corrispondenti.

### <a name="interface-and-event-mappings"></a>Mapping di interfacce ed eventi

Alcuni eventi non hanno più eventi univoci e ora contengono un [MixedRealityInputAction](../features/input/input-actions.md). Queste azioni vengono specificate nel profilo azioni di input e sono mappate a controller e piattaforme specifiche nel profilo di mapping del controller. Gli eventi come `OnInputDown` dovrebbero ora verificare il tipo di MixedRealityInputAction.

Sistemi di input correlati:

* [Cenni preliminari sull'input](../features/input/overview.md)
* [Eventi di input](../features/input/input-events.md)
* [Puntatori di input](../features/input/pointers.md)

| HTK 2017 |  MRTK V2  | Mapping delle azioni |
|----------|-----------|----------------|
| `IControllerInputHandler` | [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mappato al touchpad o levetta |
| `IControllerTouchpadHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Mappato al touchpad |
| `IFocusable` | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) | |
| `IGamePadHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IHoldHandler` | [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | Mappata per l'attesa nel profilo movimenti |
| `IInputClickHandler` | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) |
| `IInputHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Mappato ai pulsanti o al tocco della mano del controller |
| `IManipulationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Mappato alla manipolazione nel profilo movimenti |
| `INavigationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Mappato alla navigazione nel profilo movimenti |
| `IPointerSpecificFocusable` | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) | |
| `ISelectHandler` | [`IMixedRealityInputHandler<float>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mappata alla posizione del trigger |
| `ISourcePositionHandler` | [`IMixedRealityInputHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) o [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mappata alla posizione del puntatore o alla posizione del grip |
| `ISourceRotationHandler` | [`IMixedRealityInputHandler<Quaternion>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) o [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mappata alla posizione del puntatore o alla posizione del grip |
| `ISourceStateHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IXboxControllerHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) e [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mappato ai vari pulsanti del controller e ThumbSticks |

## <a name="camera"></a>Fotocamera

|        Metodi                    | HTK 2017 |  MRTK V2  |
|---------------------------|----------|-----------|
| Configurazione                     | Eliminare MainCamera, aggiungere MixedRealityCameraParent/MixedRealityCamera/HoloLensCamera prefabbricate alla scena **o** usare il Toolkit di realtà mista > configurare > applicare la voce di menu delle impostazioni della scena della realtà mista. | MainCamera padre in MixedRealityPlayspace tramite il Toolkit di realtà mista > Aggiungi alla scena e configura... |
| Configurazione             | Configurazione delle impostazioni della fotocamera eseguita nell'istanza prefabbricata. | Impostazioni della fotocamera configurate nel profilo della fotocamera per la [realtà mista](xref:Microsoft.MixedReality.Toolkit.MixedRealityCameraProfile). |

## <a name="speech"></a>Voce

### <a name="keyword-recognition"></a>Riconoscimento parole chiave

|         Metodi                   | HTK 2017 |  MRTK V2  |
|---------------------------|----------|-----------|
| Configurazione                     | Aggiungere un SpeechInputSource alla scena. | Il servizio parole chiave (ad esempio, Windows Speech input Manager) deve essere aggiunto ai provider di dati del sistema di input. |
| Configurazione             | Le parole chiave riconosciute vengono configurate nel controllo di SpeechInputSource. | Le parole chiave sono configurate nel [profilo dei comandi vocali di realtà mista](../features/input/speech.md). |
| Gestori eventi            | `ISpeechHandler` | [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

### <a name="dictation"></a>Dettatura

|         Metodi                   | HTK 2017 |  MRTK V2  |
|---------------------------|----------|-----------|
| Configurazione                     | Aggiungere un DictationInputManager alla scena. | Il supporto per la dettatura richiede che il servizio (ad esempio, gestione input di dettatura di Windows) venga aggiunto ai provider di dati del sistema di input. |
| Gestori eventi            | `IDictationHandler` | `IMixedRealityDictationHandler`[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

## <a name="spatial-awareness--mapping"></a>Riconoscimento spaziale/mapping

### <a name="mesh"></a>Mesh

|         Metodi                   | HTK 2017 |  MRTK V2  |
|---------------------------|----------|-----------|
| Configurazione                     | Aggiungere la prefabbricazione SpatialMapping alla scena. | Abilitare il sistema di riconoscimento spaziale nel profilo di configurazione e aggiungere un osservatore spaziale (ad esempio, l'osservatore della rete spaziale a realtà mista di Windows) ai provider di dati del sistema di sensibilizzazione spaziale. |
| Configurazione             | Configurare l'istanza della scena nel controllo. | Configurare le impostazioni nel profilo di ogni osservatore spaziale. |

### <a name="planes"></a>Aerei

|         Metodi                   | HTK 2017 |  MRTK V2  |
|---------------------------|----------|-----------|
| Configurazione                     | Usare lo `SurfaceMeshesToPlanes` script. | Non ancora implementato. |

### <a name="spatial-understanding"></a>Conoscenza spaziale

|       Metodi                      | HTK 2017 |  MRTK V2  |
|---------------------------|----------|-----------|
| Configurazione                     | Aggiungere la prefabbricazione SpatialUnderstanding alla scena. | Non ancora implementato. |
| Configurazione             | Configurare l'istanza della scena nel controllo. | Non ancora implementato. |

## <a name="boundary"></a>Limite

|         Metodi                   | HTK 2017 |  MRTK V2  |
|---------------------------|----------|-----------|
| Configurazione                     | Aggiungere lo `BoundaryManager` script alla scena. | Abilitare il sistema di limiti nel profilo di configurazione. |
| Configurazione             | Configurare l'istanza della scena nel controllo. | Configurare le impostazioni nel profilo di visualizzazione limite. |

## <a name="sharing"></a>Condivisione

|             Metodi               | HTK 2017 |  MRTK V2  |
|---------------------------|----------|-----------|
| Configurazione                     | Servizio di condivisione: aggiungere la precostruzione della condivisione alla scena. UNet: usare l'esempio SharingWithUNET. | In corso |
| Configurazione             | Configurare le istanze della scena nel controllo. | In corso |

## <a name="ux"></a>UX

|         Metodi                   | HTK 2017 |  MRTK V2  |
|---------------------------|----------|-----------|
| Pulsante                     | [Oggetti interagibili](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Button](../features/ux-building-blocks/Button.md) |
| Con cui                     | [Oggetti interagibili](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Con cui](../features/ux-building-blocks/Interactable.md) |
| Riquadro             | [Rettangolo di delimitazione](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [Rettangolo di delimitazione](../features/ux-building-blocks/bounding-box.md) |
| Barra dell'app             | [Barra dell'app](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [Barra dell'app](../features/ux-building-blocks/app-bar.md) |
| Manipolazione a mano singola (GRB e Move)   | [HandDraggable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/HandDraggable.cs) | [Gestore di manipolazione](../features/ux-building-blocks/manipulation-handler.md) |
| Manipolazione a due mani (recupero/spostamento/rotazione/scala)             | [TwoHandManipulatable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/TwoHandManipulatable.cs) | [Gestore di manipolazione](../features/ux-building-blocks/manipulation-handler.md) |
| Tastiera             | [Prefabbricato tastiera]() | [Tastiera di sistema](../features/ux-building-blocks/system-keyboard.md) |
| Descrizione comando             | [Descrizione comando](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_TooltipExample.md) | [Descrizione comando](../features/ux-building-blocks/tooltip.md) |
| Raccolta di oggetti             | [Raccolta di oggetti](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md) | [Raccolta di oggetti](../features/ux-building-blocks/object-collection.md) |
| Solver             | [Solver](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Readme/README_SolverSystem.md) | [Solver](../features/ux-building-blocks/solvers/solver.md) |

## <a name="utilities"></a>Utilità

Alcune utilità sono state riconciliate come duplicati con il sistema di risoluzione. Se uno degli script necessari risulta mancante, inviare un problema.

| HTK 2017 |  MRTK V2  |
|----------|-----------|
| Billboard | [`Billboard`](xref:Microsoft.MixedReality.Toolkit.UI.Billboard) |
| Tagalong | [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) o [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) [Risolutore](../features/ux-building-blocks/solvers/Solver.md) |
| FixedAngularSize | [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize)[Risolutore](../features/ux-building-blocks/solvers/solver.md) |
| FpsDisplay | [Sistema di diagnostica](../features/diagnostics/diagnostics-system-getting-started.md) (nel profilo di configurazione) |
| NearFade | Shader incorporato a [mixed reality Toolkit standard](../features/rendering/mrtk-standard-shader.md) |
