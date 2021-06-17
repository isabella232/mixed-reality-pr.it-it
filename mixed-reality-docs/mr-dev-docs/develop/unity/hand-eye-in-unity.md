---
title: Tracciamento oculare e mano articolata in Unity
description: Informazioni sui due modi principali per intervenire sullo sguardo fisso in Unity, sui movimenti della mano e sui controller del movimento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: movimenti, controller del movimento, unity, sguardo fisso, input, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 2daa02a0681fe4f3da24fa32379e10877750af7e
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110223"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Tracciamento oculare e mano articolata in Unity

HoloLens 2 ha introdotto alcune funzionalità nuove e interessanti, ad esempio la mano articolata e il tracciamento oculare.

Il modo più semplice per sfruttare la nuova funzionalità in Unity è tramite MRTK. Sono disponibili anche alcune scene di esempio per iniziare.

* [Introduzione a Articulated Hand in MRTK](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
* [Introduzione al tracciamento oculare in MRTK](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>Blocchi predefiniti che supportano mani, occhi e altri elementi in MRTK

MRTK v2 offre un set di controlli dell'interfaccia utente e blocchi predefiniti che consentono di accelerare lo sviluppo.

|  [ ![ Pulsante](images/MRTK_Button_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) [Pulsante](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) | [ ![ Rettangolo di selezione del](images/MRTK_BoundingBox_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) rettangolo di [selezione](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) | [ ![ Gestore di manipolazione del](images/MRTK_Manipulation_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) gestore di [manipolazione](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) |
|:--- | :--- | :--- |
| Un controllo pulsante, che supporta vari metodi di input, tra cui la mano articolata di HoloLens2 | Interfaccia utente standard per la modifica di oggetti nello spazio 3D | Script per la manipolazione di oggetti con una o due mani |
|  [ ![ Slate](images/MRTK_Slate_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) [Slate](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) | [ ![ Tastiera di sistema tastiera](images/MRTK_SystemKeyboard_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) di [sistema](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) | [ ![ Interactable](images/InteractableExamples.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) [Interactable](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) |
| Piano di stile 2D, che supporta lo scorrimento con input della mano articolato | Script di esempio dell'uso della tastiera di sistema in Unity  | Uno script per rendere gli oggetti intervienibili con gli stati di visualizzazione e il supporto del tema |
|  [ ![ Risolutore](images/MRTK_Solver_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) [di risolutore](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) | [ ![ Raccolta di oggetti Raccolta](images/MRTK_ObjectCollection_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) [oggetti](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) | [ ![ Descrizione comando](images/MRTK_Tooltip_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) [](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) |
| Vari comportamenti di posizionamento degli oggetti, ad esempio tag lungo, blocco del corpo, dimensioni della visualizzazione costanti e magnetismo della superficie | Script per la creazione di una matrice di oggetti in una forma tridimensionale | Interfaccia utente di annotazione con sistema di ancoraggio/pivot flessibile, che può essere usato per etichettare controller del movimento e oggetti. |
|  [ ![ Barra dell'app barra](images/MRTK_AppBar_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) [dell'app](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) | [ ![ Puntatori](images/MRTK_Pointer_Main.png)](/windows/mixed-reality/mrtk-unity/features/input/pointers) [](/windows/mixed-reality/mrtk-unity/features/input/pointers) | [ ![ Visualizzazione punta del dito](images/MRTK_FingertipVisualization_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) [Visualizzazione punta del dito](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) |
| Interfaccia utente per l'attivazione manuale del rettangolo di selezione | Informazioni sui vari tipi di puntatori | L'affordance visivo sulla punta del dito, che migliora la confidenza per l'interazione diretta |
|  [ ![ Tracciamento oculare: Selezione della destinazione](images/mrtk_et_targetselect.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) [Tracciamento oculare: selezione della destinazione](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) | [ ![ Tracciamento oculare: navigazione](images/mrtk_et_navigation.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) [tracciamento oculare: navigazione](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) |
| Combina occhi, voce e input delle mani per selezionare in modo semplice e rapido gli ologrammi nella scena | Informazioni su come scorrere automaticamente il testo o ingrandire il contenuto con lo stato attivo in base a ciò che si sta esaminando| Esempi per la registrazione, il caricamento e la visualizzazione di ciò che gli utenti hanno visto nell'app |

## <a name="example-scenes"></a>Scene di esempio

Esplora i vari tipi di interazioni e controlli dell'interfaccia utente di MRTK in [questa scena di esempio.](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)

È possibile trovare altre scene di esempio in [GitHub di Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) nella cartella **Assets/MixedRealityToolkit.Examples/Demos.**

[![Scena di esempio](images/MRTK_Examples.png)](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity che è stato strutturato, si stanno esplorando i blocchi predefiniti principali di MRTK. Da qui è possibile passare al blocco predefinito successivo:

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
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)