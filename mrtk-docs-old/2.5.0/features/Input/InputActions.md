---
title: InputActions
description: Documentazione per creare azioni di input in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, InputActions,
ms.openlocfilehash: e21290e62b7104fbb062f45891369e0f9642d1df
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695498"
---
# <a name="input-actions"></a>Azioni di input

Le [**azioni di input**](InputActions.md) sono astrazioni rispetto a input non elaborati per semplificare l'isolamento della logica dell'applicazione dalle origini di input specifiche che producono un input. Può essere utile, ad esempio, definire un'azione *Select* ed eseguirne il mapping con il pulsante sinistro del mouse, un pulsante in un gamepad e un trigger in un controller 6 DOF. È quindi possibile fare in modo che la logica dell'applicazione attenda gli eventi di azione *Select* input anziché tenere presente tutti i diversi input in grado di produrli.

## <a name="creating-an-input-action"></a>Creazione di un'azione di input

Le azioni di input vengono configurate nel **profilo azioni** di input, all'interno del *profilo del sistema di input* nel componente Toolkit di realtà mista, specificando un nome per l'azione e il tipo di input (vincolo dell'*asse*) a cui è possibile eseguire il mapping:

<img src="../Images/Input/InputActions.png" style="max-width:100%;" alt="Input Action image">

Questi sono i valori usati più di frequente per il **vincolo AXIS**:

Vincolo asse | Descrizione
--- | ---
Digitale | Input on/off come un pulsante binario in un gamepad o mouse.
Asse singolo | Input analogico a asse singolo come un trigger analogico in un gamepad.
Asse doppio | Input analogico a doppio asse come un levetta.
Sei DOF | 3D pose con conversione e rotazione come quella prodotta da 6 controller DOF.

È possibile trovare l'elenco completo in [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) .

## <a name="mapping-input-to-actions"></a>Mapping dell'input alle azioni

Il modo in cui si esegue il mapping di un input a un'azione dipende dal tipo di origine di input:

### <a name="controller-input"></a>Input del controller

Passare al **profilo di mapping di input del controller**, sotto il profilo di sistema di *input*. Qui sarà disponibile un elenco di tutti i controller supportati:

<img src="../Images/Input/ControllerInputMappingProfile.PNG" style="max-width:100%;" alt="Input maping profile 1">

Selezionare quello che si desidera configurare e verrà visualizzata una finestra di dialogo con tutti gli input del controller, consentendo di impostare un'azione per ognuno di essi:

<img src="../Images/Input/InputActionAssignment.PNG" style="max-width:100%;" alt="Input Action Assignment">

### <a name="speech-input"></a>Input vocale

Nel **profilo del comando vocale**, sotto il *profilo di sistema di input*, è disponibile l'elenco dei comandi vocali attualmente definiti. Per eseguire il mapping di uno di essi a un'azione, è sufficiente selezionarlo nell'elenco a discesa *azione* .

<img src="../Images/Input/SpeechCommandsProfile.png" style="max-width:100%;" alt="Speech command Profile">

### <a name="gesture-input"></a>Input movimento

Il **profilo movimenti**, sotto il *profilo di sistema di input*, contiene tutti i movimenti definiti. È possibile eseguire il mapping di ognuna di esse a un'azione selezionandola nell'elenco a discesa *azione* .

<img src="../Images/Input/GestureProfile.png" style="max-width:100%;" alt="Gesture Profile">

## <a name="handling-input-actions"></a>Gestione delle azioni di input

> [!WARNING]
> Attualmente solo le azioni di input di tipo *digitale* possono essere gestite usando i metodi descritti in questa sezione. Per gli altri tipi di azione, sarà necessario gestire direttamente gli eventi per gli input corrispondenti. Ad esempio, per gestire un'azione 6 DOF mappata agli input del controller, è necessario usare [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) con T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .

Il modo più semplice per gestire le azioni di input consiste nell'usare lo [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script. In questo modo è possibile definire l'azione che si vuole ascoltare e rispondere agli eventi avviati e terminati con gli eventi di Unity.

<img src="../Images/Input/InputActionHandler.PNG" style="max-width:100%;" alt="Input Action handler">

Se si desidera un maggiore controllo, è possibile implementare l' [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interfaccia direttamente nello script. Per ulteriori informazioni sulla gestione degli eventi tramite interfacce del gestore, vedere la sezione [**eventi di input**](InputEvents.md) .

## <a name="examples"></a>Esempio

Vedere `MRTK/Examples/Demos/Input/Scenes/InputActions` per una scena di esempio che illustra come creare un'azione, eseguirne il mapping agli input del controller, del riconoscimento vocale e del movimento e usarla per ruotare un oggetto in un comando.

<img src="../Images/Input/InputActionsExample.PNG" style="max-width:100%;" alt="Input Action Example">
