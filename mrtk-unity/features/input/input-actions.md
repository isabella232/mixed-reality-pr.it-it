---
title: Azioni di input
description: Documentazione per creare azioni di input in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, InputActions,
ms.openlocfilehash: cf6ce2af304ee1cd706d0111d66a97018113fb09
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176808"
---
# <a name="input-actions"></a>Azioni di input

[**Le azioni di**](input-actions.md) input sono astrazioni su input non elaborati che consentono di isolare la logica dell'applicazione dalle origini di input specifiche che producono un input. Può essere utile, ad esempio, definire un'azione *Select* e mapparla al pulsante sinistro del mouse, un pulsante in un game pad e un trigger in un controller DOF 6. È quindi possibile fare in modo che la logica dell'applicazione sia in ascolto degli eventi Select *input* action invece di dover conoscere tutti i diversi input che possono generarlo.

## <a name="creating-an-input-action"></a>Creazione di un'azione di input

Le azioni di input vengono configurate  nel profilo azioni di input all'interno del profilo del sistema di input nel componente Toolkit realtà mista, specificando un nome per l'azione e il tipo di input (*Vincolo* asse ) a cui è possibile eseguire il mapping:

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

Questi sono i valori usati più di frequente per **Il vincolo dell'asse:**

Vincolo dell'asse | Descrizione
--- | ---
Digitale | Input on/off come un pulsante binario in un game pad o mouse.
Asse singolo | Input analogo a un asse singolo come un trigger analogico in un game pad.
Asse doppio | Input analogo a doppio asse, ad esempio una levetta.
Sei Dof | Posizione 3D con traslazione e rotazione come quella prodotta da 6 controller DOF.

È possibile trovare l'elenco completo in [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) .

## <a name="mapping-input-to-actions"></a>Mapping dell'input alle azioni

Il modo in cui si esegue il mapping di un input a un'azione e dipende dal tipo di origine di input:

### <a name="controller-input"></a>Input del controller

Passare a Profilo **mapping input controller** in Profilo sistema di *input*. Qui è possibile trovare un elenco di tutti i controller supportati:

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

Selezionare quella che si vuole configurare e verrà visualizzata una finestra di dialogo con tutti gli input del controller, consentendo di impostare un'azione per ognuno di essi:

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a>Input vocale

In **Speech Command Profile (Profilo** comando vocale) in *Input System Profile (Profilo* sistema di input) è disponibile l'elenco dei comandi vocali attualmente definiti. Per eseguire il mapping di uno di essi a un'azione, è sufficiente selezionarla *nell'elenco a discesa* Azione.

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a>Input del movimento

Il **profilo Movimenti,** in *Profilo sistema di input,* contiene tutti i movimenti definiti. È possibile eseguire il mapping di ognuno di essi a un'azione selezionandola *nell'elenco a discesa* Azione.

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a>Gestione delle azioni di input

> [!WARNING]
> Attualmente solo le azioni di input *di tipo* Digitale possono essere gestite usando i metodi descritti in questa sezione. Per altri tipi di azione, sarà invece necessario gestire direttamente gli eventi per gli input corrispondenti. Ad esempio, per gestire un'azione 6 DOF mappata agli input del controller, è necessario usare [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) con T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .

Il modo più semplice per gestire le azioni di input è usare lo [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script. In questo modo è possibile definire l'azione su cui si vuole restare in ascolto e reagire agli eventi avviati e terminati tramite eventi unity.

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

Se si vuole un maggiore controllo, è possibile implementare [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) l'interfaccia direttamente nello script. Per altri [**dettagli sulla**](input-events.md) gestione degli eventi tramite le interfacce del gestore, vedere la sezione Eventi di input.

## <a name="examples"></a>Esempio

Vedere per una scena di esempio che illustra come creare un'azione, mapparla al controller, input vocali e movimenti e usarla per ruotare `MRTK/Examples/Demos/Input/Scenes/InputActions` un oggetto al comando.

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
