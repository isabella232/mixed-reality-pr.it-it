---
title: Menu a mano
description: Scena di esempio del menu a mano in MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, HandMenu,
ms.openlocfilehash: 9bb0276c048912b4f463dd93d3303c9a3af8fe29
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177519"
---
# <a name="hand-menu"></a>Menu a mano

![Esempio di esperienza utente del menu a mano](../images/solver/MRTK_UX_HandMenu.png)

I menu a mano consentono agli utenti di visualizzare rapidamente l'interfaccia utente collegata a mano per le funzioni usate di frequente. Per evitare una falsa attivazione durante l'interazione con altri oggetti, il menu a forma di mano offre opzioni come "Richiedi mano piatta" e "Usa attivazione dello sguardo fisso". È consigliabile usare queste opzioni per impedire l'attivazione indesiderata.

## <a name="hand-menu-examples"></a>Esempi di menu a mano

**La scena HandMenuExamples.unity** si trova nella ``MRTK/Examples/Demos/HandTracking/Scenes`` cartella . Quando è in esecuzione, la scena attiverà solo il tipo di menu attualmente selezionato.
<br/><img src="../images/hand-menu/MRTK_HandMenu_ExampleScene.png" width="600px" alt="HandMenu_ExampleScene">

Questi prefab del menu a mano sono disponibili nella ``MRTK/Examples/Demos/HandTracking/Prefabs`` cartella .

### <a name="handmenu_small_hideonhanddrop-and-handmenu_medium_hideonhanddrop"></a>HandMenu_Small_HideOnHandDrop e HandMenu_Medium_HideOnHandDrop

Questi due esempi semplicemente attivano e disattivano l'oggetto MenuContent per visualizzare e nascondere il menu negli eventi **OnFirstHandDetected()** e **OnLastHandLost().**
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example1.png" width="600" alt="HandMenu_ExampleScene 1">
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example2.png" width="600" alt="HandMenu_ExampleScene 2">

### <a name="handmenu_large_worldlock_on_grabandpull"></a>HandMenu_Large_WorldLock_On_GrabAndPull

Per i menu più complessi che richiedono più tempo di interazione, è consigliabile bloccare il menu. In questo esempio l'utente può afferrare e tirare per bloccare il menu, oltre ad attivare e disattivare menuContent negli eventi **OnFirstHandDetected()** e **OnLastHandLost().**
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example3.png" width="600" alt="HandMenu_ExampleScene 3">

Il backplate `ManipulationHandler` lo rende afferrabile e mobile. **In caso di evento Manipulation Started,** **SolverHandler.UpdateSolvers** viene disattivato per bloccare il menu. Viene inoltre visualizzato il pulsante **Chiudi per** consentire all'utente di chiudere il menu al termine dell'attività. **Nell'evento Manipulation Ended** chiama **HandConstraintPalmUp.StartWorldLockReattachCheckCoroutine** per consentire all'utente di riportare il menu a portata di mano alzando e osservando il palmo.
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example4.png" width="600" alt="HandMenu_ExampleScene 4">

**Il** pulsante Chiudi riattiva **SolverHandler.UpdateSolvers** e nasconde **MenuContent.**
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example5.png" alt="HandMenu_ExampleScene 5">

### <a name="handmenu_large_autoworldlock_on_handdrop"></a>HandMenu_Large_AutoWorldLock_On_HandDrop

Questo esempio è simile a HandMenu_Large_WorldLock_On_GrabAndPull. L'unica differenza è che il menu verrà automaticamente bloccato a portata di mano. Questa operazione viene eseguita semplicemente non nascondendo l'evento MenuContent **onLastHandLost().** Il & pull è identico a quello HandMenu_Large_WorldLock_On_GrabAndPull esempio.

## <a name="scripts"></a>Script

Il comportamento fornisce un risolutore che vincola l'oggetto tracciato in un'area sicura per il contenuto vincolato a mano ,ad esempio l'interfaccia utente [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) della mano, i menu e così via. Cassaforte aree sono considerate aree che non si intersecano con la mano. È inclusa anche una classe derivata di chiamata per illustrare un comportamento comune di attivazione dell'oggetto tracciato del risolutore quando il [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) palmo è rivolto verso l'utente.

Per documentazione aggiuntiva, vedere le descrizioni comando disponibili [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) per ogni proprietà. Alcune proprietà sono definite in modo più dettagliato di seguito.

<img src="../images/solver/MRTK_Solver_HandConstraintPalmUp.png" width="450" alt="HandMenu_ExampleScene Palm up">

* **Cassaforte zona sicura:** la zona sicura specifica dove vincolare il contenuto. È consigliabile inserire il contenuto sul lato Ulnar per evitare sovrapposizioni con la mano e migliorare la qualità dell'interazione. Cassaforte le zone vengono calcolate prendendo l'orientamento delle mani proiettate in un piano ortogonale verso la visualizzazione della fotocamera e il raycasting su un rettangolo di selezione intorno alle mani. Cassaforte sono definite per l'utilizzo con [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) ma anche con altri tipi di controller. È consigliabile esplorare ciò che ogni zona sicura rappresenta in diversi tipi di controller.

* **Seguire la mano fino alla fotocamera rivolta verso l'alto** Con questo oggetto attivo, il risolutore seguirà la rotazione manuale fino a quando il menu non è sufficientemente allineato allo sguardo, a quel punto si trova di fronte alla fotocamera. Ciò funziona modificando SolverRotationBehavior in HandConstraintSolver, da LookAtTrackedObject a LookAtMainCamera man mano che l'angolo gazeAlignment con il risolutore varia.

<img src="../images/solver/MRTK_Solver_HandConstraintSafeZones.png" width="450" alt="HandMenu Safe Zones">

* **Eventi di attivazione:** attiva [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) attualmente quattro eventi di attivazione. Questi eventi possono essere usati in molte combinazioni diverse per creare comportamenti univoci, vedere la scena [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) HandBasedMenuExample in per esempi `MRTK/Examples/Demos/HandTracking/Scenes/` di questi comportamenti.

  * *OnHandActivate:* viene attivato quando una mano soddisfa il metodo IsHandActive.
  * *OnHandDeactivate:* viene attivato quando il metodo IsHandActive non è più soddisfatto.
  * *OnFirstHandDetected:* si verifica quando lo stato di rilevamento della mano cambia da nessuna mano nella visualizzazione alla prima mano nella visualizzazione.
  * *OnLastHandLost:* si verifica quando lo stato di rilevamento della mano cambia da almeno una mano nella visualizzazione a nessuna mano nella visualizzazione.

* Logica di **attivazione/disattivazione** del risolutore: attualmente è consigliabile attivare e disattivare la logica tramite l'uso del valore [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) UpdateSolver di SolverHandler, anziché disabilitando/abilitando l'oggetto. Questa operazione può essere visualizzata nella scena di esempio tramite gli hook basati sull'editor attivati dopo gli eventi ManipulationHandler "OnManipulationStarted/Ended" del menu associato.

  * Arresto della logica del vincolo di *mano:* quando si tenta di impostare l'arresto dell'oggetto vincolato alla mano (oltre a non eseguire la logica di attivazione/disattivazione), impostare UpdateSolver su False anziché disabilitare HandConstraintPalmUp.
    * Se si vuole abilitare la logica di ricottacco basata su sguardo fisso (o anche non basato su sguardo), questa operazione viene seguita chiamando la funzione HandConstraintPalmUp.StartWorldLockReattachCheckCoroutine(). Verrà attivata una coroutine che continua a verificare se i criteri "IsValidController" sono soddisfatti e imposta UpdateSolver su True una volta che è (o l'oggetto è disabilitato)
  * *Avvio* della logica di vincolo della mano: quando si tenta di impostare l'oggetto con vincoli di mano per iniziare di nuovo a seguire la mano (a seconda che soddisfi i criteri di attivazione), impostare UpdateSolver di SolverHandler su true.

* **Logica di** ricollegare: attualmente è in grado di ricollegare automaticamente l'oggetto di destinazione al punto tracciato, indipendentemente dal fatto che UpdateSolver di SolverHandler sia o meno [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) True. Questa operazione viene eseguita chiamando la funzione StartWorldLockReattachCheckCoroutine() di HandConstraintPalmUp, dopo che è stata bloccata in tutto il mondo (che in questo caso sta effettivamente impostando UpdateSolver di SolverHandler su False).

## <a name="see-also"></a>Vedere anche

* [Button](button.md)
* [Menu vicino](near-menu.md)
