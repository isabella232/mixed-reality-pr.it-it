---
title: Input vocale in Unreal
description: Informazioni su come configurare e usare l'input vocale, i mapping vocali e il riconoscimento nelle app di realtà mista Unreal per HoloLens 2 dispositivi.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, Unreal, Unreal Engine 4, UE4, HoloLens 2, voce, input vocale, riconoscimento vocale, realtà mista, sviluppo, funzionalità, documentazione, ologrammi, sviluppo di giochi, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 12d0c595b5319da50e119f4a2463e2ca3e07ce449f11d6fd266c5f988d180465
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221012"
---
# <a name="voice-input-in-unreal"></a>Input vocale in Unreal

L'input vocale in Unreal consente di interagire con un ologramma senza dover usare i movimenti della mano ed è supportato solo HoloLens 2. L'input vocale HoloLens 2 è alimentato dallo stesso motore che supporta la voce in tutte le altre app universali Windows, ma Unreal usa un motore più limitato per elaborare l'input vocale. Ciò limita le funzionalità di input vocale in Unreal ai mapping vocali predefiniti, trattati nelle sezioni seguenti. 

## <a name="enabling-speech-recognition"></a>Abilitazione del riconoscimento vocale

Se si usa Windows Mixed Reality plug-in, l'input vocale non richiede api Windows Mixed Reality speciali. è basato sull'API di mapping [dell'input](https://docs.unrealengine.com/Gameplay/Input/index.html) di Unreal Engine 4 esistente. Se si usa OpenXR, è necessario installare anche il [plug-in Microsoft OpenXR.](https://github.com/microsoft/Microsoft-OpenXR-Unreal) 

Per abilitare il riconoscimento vocale in HoloLens:
1. Selezionare **Project Impostazioni > funzionalità > HoloLens > piattaforma e** abilitare **Microfono**. 
2. Abilitato il riconoscimento vocale in **Impostazioni > Privacy > riconoscimento vocale e** selezionare **Inglese.**

> [!NOTE]
> Il riconoscimento vocale funziona sempre nel Windows lingua di visualizzazione configurata nell'app **Impostazioni** predefinita. È consigliabile abilitare anche il riconoscimento vocale **online** per la migliore qualità del servizio.

![Windows Impostazioni di riconoscimento vocale](images/unreal/speech-recognition-settings.png)

3. Verrà visualizzata una finestra di dialogo quando l'applicazione inizia a chiedere se si vuole abilitare il microfono. Se si **seleziona Sì,** l'input vocale viene avviato nell'app.

## <a name="adding-speech-mappings"></a>Aggiunta di mapping voce

La connessione del riconoscimento vocale all'azione è un passaggio importante quando si usa l'input vocale. Questi mapping monitorano l'app per le parole chiave vocali che un utente potrebbe pronunciare e quindi generano un'azione collegata. È possibile trovare i mapping del riconoscimento vocale tramite:
1. Selezionare **Modifica > Project Impostazioni**, scorrere fino alla sezione **Motore** e fare clic su **Input**.

Per aggiungere un nuovo mapping vocale per un comando jump:
1. Selezionare **+** l'icona accanto **a Elementi matrice** e compilare i valori seguenti:
    * **jumpWord per** **Nome azione**
    * **passare alla** parola **chiave Speech**

> [!NOTE]
> Qualsiasi parola o frase breve in inglese può essere usata come parola chiave. 

![Input del motore UE4 Impostazioni](images/unreal/engine-input.png)

I mapping del riconoscimento vocale possono essere usati come componenti di input, ad esempio mapping di azioni o assi, o come nodi del progetto nell'Graph. Ad esempio, è possibile collegare il comando jump per stampare due log diversi a seconda di quando viene pronunciata la parola:

1. Fare doppio clic su un progetto per aprirlo **nell'Graph**.
2. **Fare clic con** il  pulsante destro del mouse e cercare il nome azione del mapping vocale (in questo caso **jumpWord),** quindi premere **INVIO** per aggiungere un nodo Azione di **input** al grafico.
3. Trascinare e rilasciare **il segnaposto** Premuto **nel nodo Stringa** di stampa, come illustrato nell'immagine seguente. È possibile lasciare vuoto **il segnaposto** Rilasciato, che non eseguirà alcun elemento per i mapping di riconoscimento vocale.
 
![Azione semplice per la voce](images/unreal/voice-input-img-03.png)

4. Riprodurre l'app, pronunciare la parola **jump** e guardare la console stampare i log.

Questa è tutta la configurazione necessaria per iniziare ad aggiungere input vocale alle app HoloLens in Unreal. È possibile trovare altre informazioni sul riconoscimento vocale e l'interattività nei collegamenti seguenti e assicurarsi di pensare all'esperienza che si sta creando per gli utenti.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo unreal che è stato previsto, l'attività successiva è esplorare le API e le funzionalità della piattaforma di realtà mista: 

> [!div class="nextstepaction"]
> [Fotocamera HoloLens](unreal-hololens-camera.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Input vocale](../../design/voice-input.md)
* [Sguardo e commit](../../design/gaze-and-commit.md)
* [Interazioni istintive](../../design/interaction-fundamentals.md)

