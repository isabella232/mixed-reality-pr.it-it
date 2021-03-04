---
title: Voce
description: configurazione dell'input vocale in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sintesi vocale,
ms.openlocfilehash: 610516df4e9821c361e87394eb30c9f22389fdd6
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782859"
---
# <a name="speech"></a>Voce

![Menu vicino](../images/input/MRTK_Input_Speech.png)

I provider di input vocale, come l' *input vocale Windows*, non creano alcun controller, ma consentono di definire parole chiave che genereranno eventi di input vocali quando vengono riconosciuti. Il **profilo dei comandi vocali** nel *profilo di sistema di input* è il punto in cui vengono configurate le parole chiave da riconoscere. Per ogni comando è inoltre possibile:

- Selezionare un' **azione di input** a cui eseguire il mapping. In questo modo è possibile, ad esempio, usare la parola chiave *Select* per avere lo stesso effetto di un clic del mouse a sinistra, eseguendo il mapping di entrambi alla stessa azione.
- Specificare un **codice chiave** che produrrà lo stesso evento vocale quando viene premuto.
- Aggiungere una **chiave di localizzazione** che verrà usata nelle app UWP per ottenere la parola chiave localizzata dalle risorse dell'app.

<img src="../images/input/SpeechCommandsProfile.png" width="450px" alt="Speech Commands Profile">

## <a name="handling-speech-input"></a>Gestione dell'input vocale

Lo [**`Speech Input Handler`**](xref:Microsoft.MixedReality.Toolkit.Input.SpeechInputHandler) script può essere aggiunto a un GameObject per gestire i comandi vocali usando [**UnityEvents**](https://docs.unity3d.com/Manual/UnityEvents.html). Mostra automaticamente l'elenco delle parole chiave definite dal profilo dei **comandi vocali**.

<img src="../images/input/SpeechCommands_SpeechInputHandler1.png" width="450px" alt="Speech Input Handler1">

Assegnare l'etichetta facoltativa della descrizione comando **SpeechConfirmationTooltip. prefabbricato** per visualizzare l'etichetta della descrizione comando animata.

<img src="../images/input/SpeechCommands_SpeechInputHandler2.png" alt="Speech Input Handler 2">

In alternativa, gli sviluppatori possono implementare l' [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interfaccia in un componente script personalizzato per [gestire gli eventi di input vocale](InputEvents.md#input-event-interface-example).

## <a name="example-scene"></a>Scena di esempio

La scena **SpeechInputExample** , in `MRTK/Examples/Demos/Input/Scenes/Speech` , Mostra come usare il riconoscimento vocale. È anche possibile ascoltare gli eventi del comando vocale direttamente nello script implementando [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) (vedere la tabella dei [gestori di eventi](InputEvents.md)).

<img src="../images/input/SpeechExampleScene.png" width="750px" alt="Speech Example Scene">
