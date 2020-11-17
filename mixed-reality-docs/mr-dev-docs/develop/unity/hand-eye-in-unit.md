---
title: Rilevamento mano e occhio articolato in Unity
description: Ci sono due modi principali per agire sullo sguardo in Unity, movimenti della mano e controller di movimento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: movimenti, controller di movimento, Unity, sguardo, input, cuffie per realtà mista, cuffie di realtà mista di Windows, cuffie per realtà virtuale, MRTK, Toolkit di realtà mista
ms.openlocfilehash: 244d1ef27d9aa68d971fa8372bda301fccab0704
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677590"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Rilevamento mano e occhio articolato in Unity

HoloLens 2 ha introdotto alcune nuove e interessanti funzionalità, ad esempio la traccia articolata e il rilevamento degli occhi.

Il modo più semplice per sfruttare la nuova funzionalità in Unity è tramite MRTK V2. Sono inoltre disponibili alcune scene di esempio utili per iniziare.

* [Inizia a usare MRTK V2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/HandTracking.html)
* [Introduzione a Eye Tracking in MRTK V2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk-v2"></a>Blocchi predefiniti che supportano Hands, Eyes e others in MRTK V2

MRTK v2 fornisce un set di controlli dell'interfaccia utente e blocchi predefiniti che consentono di accelerare lo sviluppo.

|  [Pulsante](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) [ ![ pulsante](images/MRTK_Button_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) | Rettangolo di [delimitazione del](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) rettangolo di [ ![ delimitazione](images/MRTK_BoundingBox_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) | [Gestore manipolazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) [ ![ gestione](images/MRTK_Manipulation_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) manipolazione |
|:--- | :--- | :--- |
| Controllo Button che supporta vari metodi di input, tra cui la mano articolata HoloLens2's | Interfaccia utente standard per la modifica di oggetti nello spazio 3D | Script per la modifica di oggetti con una o due mani |
|  [ ![ Ardesia ardesia](images/MRTK_Slate_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) [Slate](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) | [Tastiera sistema](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) [ ![ tastiera](images/MRTK_SystemKeyboard_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) sistema | [ ![ Interazione](images/InteractableExamples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) interactabile [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) |
| piano di stile 2D che supporta lo scorrimento con l'input della mano articolata | Script di esempio di uso della tastiera di sistema in Unity  | Uno script per rendere gli oggetti interagiscono con gli stati visivi e il supporto dei temi |
|  [Risolutore](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) [ ![ Risolutore](images/MRTK_Solver_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) | [Raccolta oggetti](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) [ ![ raccolta oggetti](images/MRTK_ObjectCollection_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) | [Descrizione comando](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) [ ![ Descrizione comando](images/MRTK_Tooltip_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) |
| Vari comportamenti di posizionamento degli oggetti, ad esempio tag-along, blocco del corpo, dimensioni della visualizzazione costante e magnetismo della superficie | Script per il layout di una matrice di oggetti in una forma tridimensionale | Interfaccia utente dell'annotazione con sistema di ancoraggio/pivot flessibile, che può essere usata per etichettare i controller di movimento e l'oggetto. |
|  [Barra dell'app](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) [ ![ barra dell'app](images/MRTK_AppBar_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) | [ ![ Puntatori puntatori](images/MRTK_Pointer_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html) [Pointers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html) | [Visualizzazione a portata](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) di mano [ ![ visualizzazione a mano](images/MRTK_FingertipVisualization_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) |
| Interfaccia utente per l'attivazione manuale del riquadro delimitatore | Informazioni sui diversi tipi di puntatori | Offerta visiva a portata di mano, che migliora la confidenza per l'interazione diretta |
|  [ ![ Rilevamento degli occhi: rilevamento occhi selezione destinazione](images/mrtk_et_targetselect.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) [: selezione destinazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) | [ ![ Rilevamento degli occhi:](images/mrtk_et_navigation.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) esplorazione [degli occhi: navigazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) | [ ![ Verifica degli occhi:](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) [monitoraggio degli occhi della mappa termica: mappa termica](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| Combina gli occhi, l'input voce e la mano per selezionare gli ologrammi in modo rapido e semplice nella tua scena | Informazioni su come scorrere automaticamente il testo o ingrandire in modo scorrevole il contenuto con lo stato attivo in base a ciò che si sta esaminando| Esempi per la registrazione, il caricamento e la visualizzazione delle informazioni visualizzate dall'utente nell'app |

## <a name="example-scenes"></a>Scene di esempio

Esplorare i diversi tipi di interazioni e i controlli dell'interfaccia utente di MRTK in [questa scena di esempio](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html).

È possibile trovare altre scene di esempio nel [Toolkit di realtà mista GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity) in **assets/MixedRealityToolkit. examples/Demos** cartella.

[![Scena di esempio](images/MRTK_Examples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di checkpoint per lo sviluppo con Unity che abbiamo delineato, si stanno esplorando i blocchi predefiniti fondamentali in MRTK. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Mapping spaziale](spatial-mapping-in-unity.md)

In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche

* [Interazione basata sullo sguardo](../../design/eye-gaze-interaction.md)
* [Tracciamento oculare in HoloLens 2](../../design/eye-tracking.md)
* [Sguardo e commit](../../design/gaze-and-commit.md)
* [Mani - Manipolazione diretta](../../design/direct-manipulation.md)
* [Mani - Movimenti](../../design/gaze-and-commit.md#composite-gestures)
* [Mani - Puntamento e commit](../../design/point-and-commit.md)
* [Interazioni istintive](../../design/interaction-fundamentals.md)
* [Controller del movimento](../../design/motion-controllers.md)
* [UnityEngine. XR. WSA. input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
