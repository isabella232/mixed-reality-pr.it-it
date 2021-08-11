---
title: Tracciamento oculare e mano articolato in Unity
description: Informazioni sui due modi principali per intervenire sullo sguardo in Unity, i movimenti della mano e i controller di movimento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: movimenti, controller di movimento, unità, sguardo, input, visore di realtà mista, visore di realtà mista windows, visore per realtà virtuale, MRTK, realtà mista Toolkit
ms.openlocfilehash: 005b817574e6d3600b9c43e443432203418b58a2258e2938614cc549ab7539c2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223837"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Tracciamento oculare e mano articolato in Unity

HoloLens 2 ha introdotto alcune funzionalità nuove ed interessanti, ad esempio la mano articolata e il tracciamento oculare.

Il modo più semplice per sfruttare la nuova funzionalità in Unity è tramite MRTK. Sono anche disponibili alcune scene di esempio per iniziare.

* [Introduzione a Articulated Hand in MRTK](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
* [Introduzione al tracciamento oculare in MRTK](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>Blocchi predefiniti che supportano mani, occhi e altri in MRTK

MRTK v2 offre un set di controlli dell'interfaccia utente e blocchi predefiniti che consentono di accelerare lo sviluppo.

|  [ ![ Pulsante](images/MRTK_Button_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) [](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) | [ ![ Rettangolo di selezione del](images/MRTK_BoundingBox_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) rettangolo di [selezione](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) | [ ![ Gestore di manipolazione del](images/MRTK_Manipulation_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) gestore di [manipolazione](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) |
|:--- | :--- | :--- |
| Un controllo pulsante, che supporta vari metodi di input, tra cui la mano articolata di HoloLens2 | Interfaccia utente standard per la modifica di oggetti nello spazio 3D | Script per la modifica di oggetti con una o due mani |
|  [ ![ Slate](images/MRTK_Slate_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) [Slate](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) | [ ![ Tastiera di sistema tastiera](images/MRTK_SystemKeyboard_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) di [sistema](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) | [ ![ Interactable](images/InteractableExamples.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) [Interactable](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) |
| Piano di stile 2D, che supporta lo scorrimento con input manuale articolato | Script di esempio dell'uso della tastiera di sistema in Unity  | Uno script per rendere gli oggetti intervienibili con gli stati di visualizzazione e il supporto del tema |
|  [ ![ Risolutore](images/MRTK_Solver_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) [di risolutore](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) | [ ![ Raccolta di oggetti della](images/MRTK_ObjectCollection_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) raccolta di [oggetti](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) | [ ![ Descrizione](images/MRTK_Tooltip_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) [comando](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) |
| Vari comportamenti di posizionamento degli oggetti, ad esempio tag-along, blocco del corpo, dimensioni di visualizzazione costanti e magnetismo della superficie | Script per il lay out di una matrice di oggetti in una forma tridimensionale | Interfaccia utente delle annotazioni con sistema flessibile di ancoraggio/pivot, che può essere usato per etichettare controller di movimento e oggetti. |
|  [ ![ Barra dell'app Barra](images/MRTK_AppBar_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) [delle app](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) | [ ![ Puntatori](images/MRTK_Pointer_Main.png)](/windows/mixed-reality/mrtk-unity/features/input/pointers) [puntatori](/windows/mixed-reality/mrtk-unity/features/input/pointers) | [ ![ Visualizzazione della punta delle dita](images/MRTK_FingertipVisualization_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) [Visualizzazione punta del dito](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) |
| Interfaccia utente per l'attivazione manuale di Bounding Box | Informazioni sui vari tipi di puntatori | Convenienza visiva sulla punta delle dita, che migliora la confidenza per l'interazione diretta |
|  [ ![ Tracciamento oculare: Tracciamento oculare](images/mrtk_et_targetselect.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) [selezione destinazione: Selezione destinazione](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) | [ ![ Tracciamento oculare: Tracciamento](images/mrtk_et_navigation.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) [oculare di navigazione: Navigazione](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) |
| Combinare occhi, voce e input manuale per selezionare rapidamente e senza sforzo gli ologrammi nella scena | Informazioni su come scorrere automaticamente il testo o ingrandire il contenuto con stato attivo in base a ciò che si sta esaminando| Esempi per la registrazione, il caricamento e la visualizzazione di ciò che gli utenti hanno visto nell'app |

## <a name="example-scenes"></a>Scene di esempio

Esplorare i vari tipi di interazioni e controlli dell'interfaccia utente di MRTK in [questa scena di esempio.](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)

Altre scene di esempio sono disponibili nella Toolkit GitHub Di realtà [mista](https://github.com/Microsoft/MixedRealityToolkit-Unity) nella **cartella Assets/MixedRealityToolkit.Examples/Demos.**

[![Scena di esempio](images/MRTK_Examples.png)](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity che è stato previsto, si stanno esplorando i blocchi predefiniti principali di MRTK. Da qui è possibile passare al blocco predefinito successivo:

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