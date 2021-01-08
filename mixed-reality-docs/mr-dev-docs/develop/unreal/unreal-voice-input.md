---
title: Input vocale in Unreal
description: Informazioni su come configurare e usare l'input vocale, i mapping vocale e il riconoscimento in app Real realtà mista per i dispositivi HoloLens 2.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realtà mista di Windows, Unreal, Unreal Engine 4, UE4, HoloLens 2, Voice, input vocale, riconoscimento vocale, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, sviluppo di giochi, cuffie per realtà mista, cuffia di realtà mista di Windows, Headset della realtà virtuale
ms.openlocfilehash: c7ac523258dc44aa261470aea8cdf21f32c915b2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010071"
---
# <a name="voice-input-in-unreal"></a>Input vocale in Unreal

L'input vocale in Unreal consente di interagire con un ologramma senza dover usare i movimenti della mano ed è supportato solo HoloLens 2. L'input vocale in HoloLens 2 è alimentato dallo stesso motore che supporta la sintesi vocale in tutte le altre app di Windows universale, ma Unreal usa un motore più limitato per elaborare l'input vocale. In questo modo è possibile limitare le funzionalità di input vocali in Unreal ai mapping di riconoscimento vocale predefiniti, descritte nelle sezioni seguenti. 

## <a name="enabling-speech-recognition"></a>Abilitazione del riconoscimento vocale

Per abilitare il riconoscimento vocale in HoloLens:
1. Selezionare **Impostazioni progetto > piattaforma > funzionalità di > HoloLens** e abilitare il **microfono**. 
2. Il riconoscimento vocale è stato abilitato in **impostazioni > Privacy > vocale** e selezionare **inglese**.

> [!NOTE]
> Il riconoscimento vocale funziona sempre nella lingua di visualizzazione di Windows configurata nell'app **Impostazioni** . È inoltre consigliabile abilitare il **riconoscimento vocale online** per la qualità del servizio migliore.

![Impostazioni di riconoscimento vocale Windows](images/unreal/speech-recognition-settings.png)

3. Una finestra di dialogo viene visualizzata quando l'applicazione inizia per la prima volta a richiedere se si vuole abilitare il microfono. Se **si seleziona Sì** , viene avviato l'input vocale nell'app.

L'input vocale non richiede alcuna API della realtà mista di Windows speciale; si basa sull'API di mapping di [input](https://docs.unrealengine.com/Gameplay/Input/index.html) Unreal Engine 4 esistente. 

## <a name="adding-speech-mappings"></a>Aggiunta di mapping vocale

La connessione vocale all'azione è un passaggio importante quando si usa l'input vocale. Questi mapping monitorano l'app per le parole chiave vocali che un utente potrebbe pronunciare, quindi avviare un'azione collegata. È possibile trovare mapping vocale per:
1. Selezionare **modifica > impostazioni progetto**, scorrere fino alla sezione **motore** e fare clic su **input**.

Per aggiungere un nuovo mapping vocale per un comando Jump:
1. Selezionare l' **+** icona accanto agli **elementi della matrice** e compilare i valori seguenti:
    * **jumpWord** per **nome azione**
    * **passa** alla **parola chiave Speech**

> [!NOTE]
> Tutte le parole o le frasi brevi possono essere utilizzate come parola chiave. 

![Impostazioni di input del motore UE4](images/unreal/engine-input.png)

I mapping vocale possono essere usati come componenti di input come mapping di azioni o assi o come nodi del progetto nel grafico eventi. Ad esempio, è possibile collegare il comando Jump per stampare due log diversi a seconda del momento in cui viene pronunciata la parola:

1. Fare doppio clic su un progetto per aprirlo nel **grafico eventi**.
2. **Fare clic con il pulsante destro del mouse** e cercare il **nome dell'azione** del mapping vocale (in questo caso **JumpWord**), quindi premere **invio** per aggiungere un nodo **azione di input** al grafico.
3. Trascinare e rilasciare il pin **premuto** nel nodo della **stringa di stampa** come illustrato nell'immagine seguente. È possibile lasciare vuoto il pin **rilasciato** e non eseguire alcuna operazione per i mapping vocale.
 
![Azione semplice per la voce](images/unreal/voice-input-img-03.png)

4. Riprodurre l'app, pronunciare il Word **Jump** e guardare la console per stampare i log.

Questa è tutta la configurazione necessaria per iniziare ad aggiungere input voce alle app HoloLens in Unreal. È possibile trovare altre informazioni sulla voce e sull'interattività nei collegamenti seguenti e assicurarsi di considerare l'esperienza che si sta creando per gli utenti.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo non reale, si sta per iniziare a esplorare le funzionalità e le API della piattaforma di realtà mista: 

> [!div class="nextstepaction"]
> [Fotocamera HoloLens](unreal-hololens-camera.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Input vocale](../../design/voice-input.md)
* [Sguardo e commit](../../design/gaze-and-commit.md)
* [Interazioni istintive](../../design/interaction-fundamentals.md)

