---
title: Dettatura
description: Documentazione su come registrare clip audio e ottenere una trascrizione in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 520a667cc4b41f5e8f4373a7c901eb2458cd2d17
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176471"
---
# <a name="dictation"></a>Dettatura

La dettatura consente agli utenti di registrare clip audio e ottenere una trascrizione. Per usarlo, assicurarsi che un sistema di dettatura sia registrato nel profilo *di sistema di input*. **Windows provider di input** di dettatura è il sistema di dettatura fornito in modo predefinito, ma è possibile creare sistemi di dettatura alternativi implementando [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) .

## <a name="requirements"></a>Requisiti

Il sistema di dettatura usa [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) di Unity, che usa a sua Windows api vocali sottostanti per la gestione della dettatura. Si noti che ciò implica che questa funzionalità è presente solo nelle Windows basate su dispositivi mobili.

L'utilizzo del sistema di dettatura richiede sia le funzionalità dell'applicazione "Internet Client" che "Microfono" nella sezione [PlayerSettings - Capabilities](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).
Per [altri dettagli sull'input](/windows/mixed-reality/voice-input-in-unity#dictation) vocale in Unity, vedere la documentazione di Windows Mixed Reality.

## <a name="configuration"></a>Configurazione

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

Dopo aver configurato un servizio di dettatura, è possibile usare lo script per avviare e arrestare la registrazione delle sessioni e ottenere i risultati della trascrizione [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) tramite UnityEvents.

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- **L'ipotesi di dettatura** viene generata quando l'utente parla con trascrizioni approssimative e iniziali dell'audio acquisito finora.
- **Il risultato della dettatura** viene generato alla fine di ogni frase ,ad esempio quando l'utente viene sospeso, con la trascrizione finale dell'audio acquisito finora.
- **La dettatura completa** viene generata alla fine della sessione di registrazione con la trascrizione finale completa dell'audio.
- **L'errore di** dettatura viene generato per informare degli errori nel servizio di dettatura. La trascrizione in questo caso contiene una descrizione dell'errore.

## <a name="example-scene"></a>Scena di esempio

**La scena di dettatura** in `MRTK/Examples/Demos/Input/Scenes/Dictation` mostra lo script in `DictationHandler` uso. Se è necessario un maggiore controllo, è possibile estendere questo script o creare un'implementazione propria per ricevere direttamente gli [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) eventi di dettatura.

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
