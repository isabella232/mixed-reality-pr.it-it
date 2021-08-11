---
title: Voce
description: configurazione dell'input vocale in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, voce,
ms.openlocfilehash: 00de7854bcb68703fbfd5566b7d502f08ac34efc1ac9434a2c86274f07b6342d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207813"
---
# <a name="speech"></a>Voce

![Menu vicino](../images/input/MRTK_Input_Speech.png)

I provider di input vocale, *Windows* input vocale, non creano controller, ma consentono invece di definire parole chiave che generano eventi di input vocale quando vengono riconosciuti. Il **profilo Comandi vocali nel** profilo del sistema di *input* consente di configurare le parole chiave da riconoscere. Per ogni comando è anche possibile:

- Selezionare **un'azione di input** a cui eseguire il mapping. In questo modo, ad esempio, è possibile usare la parola chiave *Select* per ottenere lo stesso effetto di un clic con il pulsante sinistro del mouse, tramite il mapping di entrambi alla stessa azione.
- Specificare un **codice tasto che** produrrà lo stesso evento vocale quando viene premuto.
- Aggiungere una **chiave di localizzazione che** verrà usata nelle app UWP per ottenere la parola chiave localizzata dalle risorse dell'app.

<img src="../images/input/SpeechCommandsProfile.png" width="450px" alt="Speech Commands profile">

## <a name="handling-speech-input"></a>Gestione dell'input vocale

Lo [**`Speech Input Handler`**](xref:Microsoft.MixedReality.Toolkit.Input.SpeechInputHandler) script può essere aggiunto a un GameObject per gestire i comandi vocali usando [**UnityEvents.**](https://docs.unity3d.com/Manual/UnityEvents.html) Mostra automaticamente l'elenco delle parole chiave definite dal profilo **Comandi vocali**.

<img src="../images/input/SpeechCommands_SpeechInputHandler1.png" width="450px" alt="Speech Input handler">

Assegnare **speechConfirmationTooltip.prefab facoltativo** per visualizzare l'etichetta della descrizione comando di conferma animata al riconoscimento.

<img src="../images/input/SpeechCommands_SpeechInputHandler2.png" alt="Sppech input handler 2">

In alternativa, gli sviluppatori possono implementare [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) l'interfaccia in un componente script personalizzato per [gestire gli eventi di input vocale.](input-events.md#input-event-interface-example)

## <a name="example-scene"></a>Scena di esempio

La **scena SpeechInputExample,** in `MRTK/Examples/Demos/Input/Scenes/Speech` , mostra come usare il riconoscimento vocale. È anche possibile ascoltare gli eventi dei comandi vocali direttamente nel proprio script implementando [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) (vedere la tabella dei [gestori eventi](input-events.md)).

<img src="../images/input/SpeechExampleScene.png" width="750px" alt="Speech Example scene">
