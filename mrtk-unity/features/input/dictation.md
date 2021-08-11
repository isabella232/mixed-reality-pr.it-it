---
title: Dettatura
description: Documentazione su come registrare clip audio e ottenere una trascrizione in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 14061197031282dcc9dd20a141101b65ee92ca2376bdc009fa8790076681a970
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220008"
---
# <a name="dictation"></a>Dettatura

La dettatura consente agli utenti di registrare clip audio e ottenere una trascrizione. Per usarlo, assicurarsi che un sistema di dettatura sia registrato nel profilo *del sistema di input*. **Windows dictation Input Provider** è il sistema di dettatura predefinito, ma è possibile creare sistemi di dettatura alternativi implementando [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) .

## <a name="requirements"></a>Requisiti

Il sistema di dettatura usa [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) di Unity, che a sua Windows api di riconoscimento vocale sottostanti per la gestione della dettatura. Si noti che ciò implica che questa funzionalità è presente solo nelle Windows basate su client.

L'utilizzo del sistema di dettatura richiede entrambe le funzionalità dell'applicazione "Client Internet" e "Microfono" nella sezione [PlayerSettings - Capabilities (Impostazioni - Funzionalità).](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities)
Vedere [Windows Mixed Reality documentazione per](/windows/mixed-reality/voice-input-in-unity#dictation) altri dettagli sull'input vocale in Unity.

## <a name="configuration"></a>Configurazione

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

Dopo aver configurato un servizio di dettatura, è possibile usare lo script per avviare e arrestare la registrazione delle sessioni e ottenere i risultati della trascrizione [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) tramite UnityEvents.

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- **L'ipotesi di** dettatura viene generata mentre l'utente parla con trascrizioni approssimative e iniziali dell'audio acquisito fino a questo momento.
- **Il risultato della dettatura** viene generato alla fine di ogni frase (ad esempio quando l'utente viene sospeso) con la trascrizione finale dell'audio acquisito fino a questo momento.
- **La dettatura completa** viene generata alla fine della sessione di registrazione con la trascrizione finale completa dell'audio.
- **L'errore di** dettatura viene generato per segnalare errori nel servizio di dettatura. La trascrizione in questo caso contiene una descrizione dell'errore.

## <a name="example-scene"></a>Scena di esempio

**La scena di dettatura** in `MRTK/Examples/Demos/Input/Scenes/Dictation` mostra lo script in `DictationHandler` uso. Se è necessario un maggiore controllo, è possibile estendere questo script o creare un'implementazione di per [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) ricevere direttamente gli eventi di dettatura.

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
