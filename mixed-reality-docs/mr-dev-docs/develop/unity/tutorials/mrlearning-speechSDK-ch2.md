---
title: Aggiunta di una modalità offline per la traduzione locale da voce a testo
description: In questo corso viene illustrato come aggiungere la modalità offline per la conversione locale della voce in testo scritto in applicazioni di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure, riconoscimento vocale, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: db495d6cdfa99721e68b4004535a5411bde9b17d
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010081"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a>2. Aggiunta di una modalità offline per la conversione locale della voce in testo scritto

In questa esercitazione aggiungerai la possibilità di eseguire comandi con il riconoscimento vocale di Azure, che consentirà di eseguire un evento in base alla parola o alla frase definita.

## <a name="objectives"></a>Obiettivi

* Imparare a usare il riconoscimento vocale di Azure per eseguire comandi

## <a name="instructions"></a>Istruzioni

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom** e quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Wake Word Recognizer (Script)** (Riconoscimento parola di attivazione Lunarcom - Script) all'oggetto Lunarcom e configuralo come indicato di seguito:

* Nel campo **Wake Word** (Parola di attivazione) immetti una frase appropriata, ad esempio _Activate Terminal_.
* Nel campo **Dismiss Word** (Parola di eliminazione) immetti una frase appropriata, ad esempio _Dismiss Terminal_.

![Editor di Unity con il componente Lunarcom Wake Word Recognizer (Script) evidenziato](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> Il componente Lunarcom Wake Word Recognizer (Script) (Riconoscimento parola di attivazione Lunarcom - Script) non fa parte di MRTK. È stato fornito con gli asset dell'esercitazione.

Se ora attivi la modalità gioco, come nell'esercitazione precedente, il pannello del terminale viene abilitato per impostazione predefinita. Tuttavia, puoi ora disabilitarlo pronunciando la parola di eliminazione **Dismiss terminal**:

![Editor di Unity in modalità di riproduzione con la funzionalità di riconoscimento vocale in uso](images/mrlearning-speech/tutorial2-section1-step1-2.png)

Puoi anche riabilitarlo pronunciando la parola di attivazione **Activate terminal**:

![Editor di Unity in modalità di riproduzione con il terminale attivo](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> Poiché l'applicazione deve connettersi ad Azure, assicurati che il computer o il dispositivo sia connesso a Internet.

> [!TIP]
> Se si prevede di non essere spesso in grado di connettersi ad Azure, è possibile implementare i comandi vocali anche con MRTK seguendo le istruzioni contenute in [Uso dei comandi vocali](mr-learning-base-09.md).

## <a name="congratulations"></a>Lezione completata

Hai implementato i comandi vocali basati su Azure. Esegui l'applicazione nel dispositivo per verificare che la funzionalità venga eseguita correttamente.

Nell'esercitazione successiva apprenderai come tradurre il parlato con la traduzione vocale di Azure.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 3. Aggiunta del componente di traduzione vocale di Servizi cognitivi di Azure](mrlearning-speechSDK-ch3.md)
