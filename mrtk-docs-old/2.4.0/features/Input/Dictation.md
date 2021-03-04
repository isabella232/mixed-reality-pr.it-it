---
title: Dettatura
description: Docummentation su come registrare clip audio e ottenere una trascrizione in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 933283dd504ebc90b83c0039e069afcb428759ad
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781855"
---
# <a name="dictation"></a>Dettatura

La dettatura consente agli utenti di registrare clip audio e ottenere una trascrizione. Per usarlo, verificare che nel *profilo di sistema di input* sia registrato un sistema di dettatura. Il **provider di input di dettatura di Windows** è il sistema di dettatura fornito in modalità predefinita, ma è possibile creare sistemi di dettatura alternativi [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) .

## <a name="requirements"></a>Requisiti

Il sistema di dettatura USA [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) di Unity, che a sua volta usa le API di riconoscimento vocale di Windows sottostanti per gestire la dettatura. Si noti che questo implica che questa funzionalità è presente solo nelle piattaforme basate su Windows.

L'utilizzo del sistema di dettatura richiede le funzionalità dell'applicazione "client Internet" e "microfono" nella [sezione PlayerSettings-capabilities](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).
Vedere la [documentazione di realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/voice-input-in-unity#dictation) per altri dettagli sull'input vocale in Unity.

## <a name="configuration"></a>Configurazione

<img src="../Images/Input/DictationDataProvider.png" width="80%" class="center" alt="Dictation Data Provider">

Dopo aver configurato un servizio di dettatura, è possibile usare lo [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) script per avviare e arrestare la registrazione delle sessioni e ottenere i risultati della trascrizione tramite UnityEvents.

<img src="../Images/Input/DictationHandler.png" width="80%" class="center" alt="Dictation Handler">

- L' **ipotesi di dettatura** viene generata quando l'utente parla con trascrizioni iniziali e approssimative dell'audio acquisite finora.
- Il **risultato della dettatura** viene generato alla fine di ogni frase, ad esempio quando l'utente esegue la sospensione, con la trascrizione finale dell'audio acquisita finora.
- La **Dettatura completa** viene generata alla fine della sessione di registrazione con la trascrizione finale completa dell'audio.
- L' **errore di dettatura** viene generato per segnalare gli errori nel servizio di dettatura. La trascrizione in questo caso contiene una descrizione dell'errore.

## <a name="example-scene"></a>Scena di esempio

La scena di **Dettatura** in `MRTK/Examples/Demos/Input/Scenes/Dictation` Mostra lo `DictationHandler` script in uso. Se è necessario un maggiore controllo, è possibile estendere questo script o creare un'implementazione personalizzata [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) per ricevere direttamente gli eventi di dettatura.

<img src="../Images/Input/DictationDemo.png" width="80%" class="center" alt="Dictation Demo">
