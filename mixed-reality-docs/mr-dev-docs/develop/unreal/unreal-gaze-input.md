---
title: Input di sguardi in Unreal
description: Esercitazione sulla configurazione dell'input di sguardi per HoloLens e Unreal Engine
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, HoloLens 2, rilevamento degli occhi, input dello sguardo, visualizzazione montata a capo, Unreal Engine
ms.openlocfilehash: 477fbdc9c7ddb3b4e890e62150651d9227d4c19e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684860"
---
# <a name="gaze-input"></a>Input sguardo

## <a name="overview"></a>Panoramica

Il [plug-in realtà mista di Windows](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) non fornisce funzioni predefinite per l'input di sguardi, ma HoloLens 2 supporta la verifica degli occhi. Le funzionalità di rilevamento effettive vengono fornite dalle API di visualizzazione e **rilevamento degli occhi** **montate** da Unreal e includono:

- Informazioni sul dispositivo
- Sensori di rilevamento
- Orientamento e posizione
- Riquadri di ritaglio
- Informazioni sugli sguardi e sui dati di rilevamento

È possibile trovare l'elenco completo delle funzionalità disponibili nella documentazione di [visualizzazione](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) e [rilevamento degli occhi](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) di Unreal.

Oltre alle API Unreal, consultare la documentazione relativa all' [interazione basata sull'occhio](../../design/eye-gaze-interaction.md) per HoloLens 2 e leggere le informazioni sul funzionamento del [monitoraggio degli occhi in HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) .

> [!IMPORTANT]
> Il rilevamento degli occhi è supportato solo in HoloLens 2.

## <a name="enabling-eye-tracking"></a>Abilitazione del rilevamento degli occhi
È necessario abilitare l'input dello sguardo nelle impostazioni del progetto HoloLens prima di poter usare le API non reali. All'avvio dell'applicazione verrà visualizzata una richiesta di consenso visualizzata nella schermata seguente.

- Selezionare **Sì** per impostare l'autorizzazione e ottenere l'accesso a sguardi input. Se è necessario modificare questa impostazione in qualsiasi momento, è possibile trovarla nell'app **Impostazioni** .

![Autorizzazioni di input per gli occhi](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> HoloLens Eye Tracking in Unreal ha solo un singolo raggio di sguardi per entrambi gli occhi anziché i due raggi necessari per il rilevamento stereoscopico, che non è supportato.

Questa è tutta la configurazione necessaria per iniziare ad aggiungere l'input dello sguardo alle app HoloLens 2 in modo irreale. Altre informazioni sull'input di sguardi e sul modo in cui influiscono sugli utenti in realtà mista sono disponibili nei collegamenti seguenti. Quando si compilano esperienze interattive, tenere presente quanto prima.

## <a name="next-development-checkpoint"></a>Checkpoint di sviluppo successivo

Se si segue il percorso di checkpoint dello sviluppo non reale, si sta per esplorare i blocchi predefiniti di MRTK core. Da qui è possibile passare al blocco predefinito successivo: 

> [!div class="nextstepaction"]
> [Tracciamento mano](unreal-hand-tracking.md)

In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Fotocamera HoloLens](unreal-hololens-camera.md)

È sempre possibile tornare ai checkpoint di [sviluppo non reali](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Calibrazione](../../calibration.md)
* [Comodità](../../design/comfort.md)
* [Sguardo e commit](../../design/gaze-and-commit.md)
* [Input vocale](../../out-of-scope/voice-design.md)
