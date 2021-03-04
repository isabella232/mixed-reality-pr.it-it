---
title: README_HandMenu
description: Scena di esempio del menu a mano in MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, HandMenu,
ms.openlocfilehash: 353e1d9c01e29437574f9b9fc6fc23cba6d892d0
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782505"
---
# <a name="hand-menu"></a>Menu a mano

![Esempio di UX menu a mano](Images/Solver/MRTK_UX_HandMenu.png)

I menu a mano consentono agli utenti di visualizzare rapidamente l'interfaccia utente collegata manualmente per le funzioni usate di frequente. Per evitare l'attivazione di false durante l'interazione con altri oggetti, il menu a mano fornisce opzioni come ' Richiedi mano piatta ' è usa lo sguardo di attivazione '. È consigliabile usare queste opzioni per impedire l'attivazione indesiderata.

## <a name="hand-menu-examples"></a>Esempi di menu a mano

La scena **HandMenuExamples. Unity** si trova nella ``MRTK/Examples/Demos/HandTracking/Scenes`` cartella. Quando è in esecuzione, la scena attiverà solo il tipo di menu attualmente selezionato.
<br/><img src="Images/HandMenu/MRTK_HandMenu_ExampleScene.png" width="600px" alt="Example Scene">

È possibile trovare questi prefabbricati di menu della mano in ``MRTK/Examples/Demos/HandTracking/Prefabs`` cartella.

### <a name="handmenu_small_hideonhanddrop-and-handmenu_medium_hideonhanddrop"></a>HandMenu_Small_HideOnHandDrop e HandMenu_Medium_HideOnHandDrop

Questi due esempi attivano e disattivano semplicemente l'oggetto MenuContent per visualizzare e nascondere il menu in **OnFirstHandDetected ()** e l'evento **OnLastHandLost ()** .
<br/><img src="Images/HandMenu/MRTK_HandMenu_Example1.png" width="600" alt="Example 1">
<br/><img src="Images/HandMenu/MRTK_HandMenu_Example2.png" width="600" alt="Example 2">

### <a name="handmenu_large_worldlock_on_grabandpull"></a>HandMenu_Large_WorldLock_On_GrabAndPull

Per i menu più complessi che richiedono tempi di interazione più lunghi, è consigliabile bloccare il menu in modo globale. In questo esempio, l'utente può eseguire il pull e il pull in un blocco globale del menu, oltre ad attivare e disattivare gli eventi MenuContent in **OnFirstHandDetected ()** e **OnLastHandLost ()** .
<br/><img src="Images/HandMenu/MRTK_HandMenu_Example3.png" width="600" alt="Example 3">

Il backplating `ManipulationHandler` lo rende afferrabile e mobile. All'evento di **manipolazione avviata** , **SolverHandler. UpdateSolvers** viene disattivato per bloccare il menu in modo globale. Inoltre, viene visualizzato il **pulsante Chiudi** per consentire all'utente di chiudere il menu al termine dell'attività. All'evento di **modifica terminata** , chiama **HandConstraintPalmUp. StartWorldLockReattachCheckCoroutine** per consentire all'utente di riportare il menu tramite la generazione e l'analisi del Palm.
<br/><img src="Images/HandMenu/MRTK_HandMenu_Example4.png" width="600" alt="Example 4">

Il pulsante **Chiudi** riattiva **SolverHandler. UpdateSolvers** e nasconde il **MenuContent**.
<br/><img src="Images/HandMenu/MRTK_HandMenu_Example5.png" alt="Example 5">

### <a name="handmenu_large_autoworldlock_on_handdrop"></a>HandMenu_Large_AutoWorldLock_On_HandDrop

Questo esempio è simile a HandMenu_Large_WorldLock_On_GrabAndPull. L'unica differenza è che il menu verrà automaticamente bloccato a mano. Questa operazione viene eseguita semplicemente non nascondendo l'evento MenuContent in **OnLastHandLost ()** . Il comportamento di pull & è uguale a quello HandMenu_Large_WorldLock_On_GrabAndPull esempio.

## <a name="scripts"></a>Script

Il [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) comportamento fornisce un risolutore che vincola l'oggetto rilevato a un'area sicura per il contenuto vincolato della mano, ad esempio l'interfaccia utente, i menu e così via. Le aree sicure sono considerate aree che non si intersecano con la mano. Viene inoltre inclusa una classe derivata di [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) chiamata [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) per illustrare un comportamento comune di attivazione dell'oggetto rilevato del Risolutore quando il Palm è rivolte all'utente.

Per ulteriori informazioni, vedere le descrizioni comandi disponibili per ogni [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) Proprietà. Alcune proprietà sono definite in modo più dettagliato di seguito.

<img src="Images/Solver/MRTK_Solver_HandConstraintPalmUp.png" width="450" alt="Hand Constraint palm up">

* **Area sicura**: l'area sicura specifica il punto in cui vincolare il contenuto. È consigliabile posizionare il contenuto sul lato ulnare per evitare sovrapposizioni con la mano e una migliore qualità di interazione. Le zone sicure vengono calcolate impostando l'orientamento delle mani proiettato in un piano ortogonale alla visualizzazione della fotocamera e Raycasting in base a un rettangolo di delimitazione delle mani. Le zone sicure sono definite per funzionare con [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) ma anche con altri tipi di controller. Si consiglia di esaminare il significato di ogni zona sicura su diversi tipi di controller.

* **Segui manualmente fino alla videocamera** Con questo attivo, il Risolutore seguirà la rotazione della mano fino a quando il menu non sarà sufficientemente allineato con lo sguardo, a quel punto la fotocamera. Questa operazione può essere eseguita modificando SolverRotationBehavior in HandConstraintSolver, da LookAtTrackedObject a LookAtMainCamera come l'angolo GazeAlignment con il Risolutore varia.

<img src="Images/Solver/MRTK_Solver_HandConstraintSafeZones.png" width="450" alt="Hand constraint safe zones">

* **Eventi di attivazione**: attualmente [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) Attiva quattro eventi di attivazione. Questi eventi possono essere usati in molte combinazioni diverse per creare comportamenti univoci [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) `MRTK/Examples/Demos/HandTracking/Scenes/` . per esempi di questi comportamenti, vedere la scena HandBasedMenuExample in.

  * *OnHandActivate*: viene attivato quando una mano soddisfa il metodo IsHandActive.
  * *OnHandDeactivate*: viene attivato quando il metodo IsHandActive non è più soddisfatto.
  * *OnFirstHandDetected*: si verifica quando lo stato di rilevamento della mano passa da nessuna mano alla visualizzazione, fino alla prima mano nella visualizzazione.
  * *OnLastHandLost*: si verifica in seguito alla modifica dello stato di rilevamento della mano da almeno una mano nella visualizzazione.

* **Logica di attivazione/disattivazione del Risolutore**: attualmente la raccomandazione per l'attivazione e la disattivazione della [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) logica consiste nell'usare il valore UpdateSolver di SolverHandler, invece di disabilitare o abilitare l'oggetto. Questo può essere visualizzato nella scena di esempio tramite gli hook basati su Editor attivati dopo gli eventi ManipulationHandler "OnManipulationStarted/ended" del menu associato.

  * *Arresto della logica del vincolo di mano*: quando si tenta di impostare l'oggetto vincolato della mano su Stop (oltre a non eseguire la logica di attivazione/disattivazione), impostare UpdateSolver su false anziché disabilitare HandConstraintPalmUp.
    * Se si vuole abilitare la logica di riassociazione basata sullo sguardo (o anche senza sguardo), questo viene seguito chiamando la funzione HandConstraintPalmUp. StartWorldLockReattachCheckCoroutine (). Verrà attivata una coroutine che continua a controllare se i criteri "IsValidController" sono soddisfatti e imposterà UpdateSolver su true una volta (oppure l'oggetto è disabilitato)
  * *Avvio della logica del vincolo di mano*: quando si tenta di impostare l'oggetto vincolato Hand per iniziare a seguire di nuovo la mano (a seconda che soddisfi i criteri di attivazione), impostare UpdateSolver di SolverHandler su true.

* **Logica di riconnessione**: attualmente [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) è in grado di allineare automaticamente l'oggetto di destinazione al punto di rilevamento, indipendentemente dal fatto che il UpdateSolver di SolverHandler sia true o meno. Questa operazione viene eseguita tramite la chiamata della funzione StartWorldLockReattachCheckCoroutine () di HandConstraintPalmUp, dopo che è stata bloccata in modo globale, in questo caso l'impostazione del UpdateSolver di SolverHandler su false.

## <a name="see-also"></a>Vedi anche

* [Button](README_Button.md)
* [Menu vicino](README_NearMenu.md)
