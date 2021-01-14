---
title: Aggiunta del componente di traduzione vocale di Servizi cognitivi di Azure
description: In questo corso viene illustrato come aggiungere la traduzione vocale di Servizi cognitivi di Azure in applicazioni di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure, riconoscimento vocale, Windows 10, traduzione vocale
ms.localizationpriority: high
ms.openlocfilehash: 3c647ca841e51b707aae4171b31b0b045c79fb03
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009881"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. Aggiunta del componente di traduzione vocale di Servizi cognitivi di Azure

In questa esercitazione aggiungerai a un progetto la traduzione vocale in modo da poter tradurre e trascrivere il parlato in tre lingue diverse.

## <a name="objectives"></a>Obiettivi

* Ottenere informazioni su come integrare la traduzione vocale di Azure

## <a name="instructions"></a>Istruzioni

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Translation Recognizer (Script)** (Riconoscimento traduzione Lunarcom - Script) all'oggetto Lunarcom e configuralo come indicato di seguito:

* Modifica l'impostazione di **Target Language** (Lingua di destinazione) impostando la lingua desiderata, ad esempio _German_ (Tedesco)

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> Il componente Lunarcom Translation Recognizer (Script) (Riconoscimento traduzione Lunarcom - Script) non fa parte di MRTK. È stato fornito con gli asset dell'esercitazione.

Se attivi la modalità di gioco, puoi testare la traduzione vocale selezionando prima il pulsante satellite. Supponendo quindi che il computer disponga di un microfono, quando pronunci una frase, questa verrà tradotta nella lingua scelta e trascritta nel pannello del terminale:

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> Poiché l'applicazione deve connettersi ad Azure, assicurati che il computer o il dispositivo sia connesso a Internet.

## <a name="congratulations"></a>Lezione completata

Il progetto ora è in grado di tradurre correttamente in lingue diverse le parole che pronunci. Esegui l'applicazione sul dispositivo per verificare che la funzionalità venga eseguita correttamente.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 4. Configurazione di finalità e comprensione del linguaggio naturale](mrlearning-speechSDK-ch4.md)
