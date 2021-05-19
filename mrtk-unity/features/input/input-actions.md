---
title: Azioni di input
description: Documentazione per creare azioni di input in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, InputActions,
ms.openlocfilehash: 071d4bc8bb4193a3d60cb53852c192ae975d79df
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144149"
---
# <a name="input-actions"></a>Azioni di input

[**Le azioni di**](input-actions.md) input sono astrazioni su input non elaborati che consentono di isolare la logica dell'applicazione dalle origini di input specifiche che producono un input. Può essere utile, ad esempio,  definire un'azione Select e mapparla al pulsante sinistro del mouse, un pulsante in un gamepad e un trigger in un controller DOF 6. È quindi possibile fare in modo che la logica dell'applicazione sia in ascolto per selezionare gli eventi di azione di *input* invece di dover tenere presenti tutti i diversi input che possono generarli.

## <a name="creating-an-input-action"></a>Creazione di un'azione di input

Le azioni di input vengono configurate nel profilo azioni di **input**, all'interno del profilo di sistema di *input* nel componente Mixed Reality Toolkit, specificando un nome per l'azione e il tipo di input (*Vincolo* asse ) a cui è possibile eseguire il mapping:

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

Questi sono i valori usati più di frequente per **Vincolo asse**:

Vincolo dell'asse | Descrizione
--- | ---
Digitale | Input on/off come un pulsante binario in un gamepad o mouse.
Asse singolo | Input analogo a un singolo asse, ad esempio un trigger analogo in un gamepad.
Doppio asse | Input analogo a doppio asse, ad esempio una levetta.
Sei Dof | Pose 3D con traslazione e rotazione come quella prodotta da 6 controller DOF.

È possibile trovare l'elenco completo in [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) .

## <a name="mapping-input-to-actions"></a>Mapping dell'input alle azioni

Il modo in cui si esegue il mapping di un input a e l'azione dipende dal tipo di origine di input:

### <a name="controller-input"></a>Input del controller

Passare al profilo **di mapping dell'input del controller** in Profilo di sistema di *input*. È presente un elenco di tutti i controller supportati:

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

Selezionare quello che si vuole configurare e verrà visualizzata una finestra di dialogo con tutti gli input del controller, consentendo di impostare un'azione per ognuno di essi:

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a>Input vocale

In **Profilo comandi vocali**, in Profilo di sistema *di input*, è disponibile l'elenco dei comandi vocali attualmente definiti. Per eseguire il mapping di uno di essi a un'azione, è sufficiente selezionarla *nell'elenco a* discesa Azione.

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a>Input movimento

Il **profilo movimenti**, in Profilo di sistema di *input*, contiene tutti i movimenti definiti. È possibile eseguire il mapping di ognuno di essi a un'azione selezionandola *nell'elenco a* discesa Azione.

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a>Gestione delle azioni di input

> [!WARNING]
> Attualmente è possibile gestire solo *le azioni* di input di tipo Digitale usando i metodi descritti in questa sezione. Per altri tipi di azione, sarà invece necessario gestire direttamente gli eventi per gli input corrispondenti. Ad esempio, per gestire un'azione DOF 6 mappata agli input del controller, è necessario usare [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) con T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .

Il modo più semplice per gestire le azioni di input è usare lo [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script. In questo modo è possibile definire l'azione che si vuole ascoltare e rispondere agli eventi di avvio e fine dell'azione usando gli eventi unity.

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

Se si vuole un maggiore controllo, è possibile implementare [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) l'interfaccia direttamente nello script. Per altri [**dettagli sulla**](input-events.md) gestione degli eventi tramite le interfacce del gestore, vedere la sezione Eventi di input.

## <a name="examples"></a>Esempio

Vedere per una scena di esempio che illustra come creare un'azione, mapparla al controller, alla voce e agli input dei movimenti e usarla per ruotare un `MRTK/Examples/Demos/Input/Scenes/InputActions` oggetto nel comando.

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
