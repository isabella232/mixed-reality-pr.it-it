---
title: Aggiunta del componente di traduzione vocale di Servizi cognitivi di Azure
description: In questo corso viene illustrato come aggiungere la traduzione vocale di Servizi cognitivi di Azure in applicazioni di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure, riconoscimento vocale, Windows 10, traduzione vocale
ms.localizationpriority: high
ms.openlocfilehash: bcc966b63f4c3e5bb9e6d6a38dc7f0312b288402
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590143"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="a4bc0-104">3. Aggiunta del componente di traduzione vocale di Servizi cognitivi di Azure</span><span class="sxs-lookup"><span data-stu-id="a4bc0-104">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="a4bc0-105">In questa esercitazione aggiungerai a un progetto la traduzione vocale in modo da poter tradurre e trascrivere il parlato in tre lingue diverse.</span><span class="sxs-lookup"><span data-stu-id="a4bc0-105">In this tutorial, you will add speech translation to your project which will allow you to translate and transcribed your speech into three different languages.</span></span>

## <a name="objectives"></a><span data-ttu-id="a4bc0-106">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="a4bc0-106">Objectives</span></span>

* <span data-ttu-id="a4bc0-107">Ottenere informazioni su come integrare la traduzione vocale di Azure</span><span class="sxs-lookup"><span data-stu-id="a4bc0-107">Learn how to integrate Azure speech translation</span></span>

## <a name="instructions"></a><span data-ttu-id="a4bc0-108">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="a4bc0-108">Instructions</span></span>

<span data-ttu-id="a4bc0-109">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Translation Recognizer (Script)** (Riconoscimento traduzione Lunarcom - Script) all'oggetto Lunarcom e configuralo come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="a4bc0-109">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Translation Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="a4bc0-110">Modifica l'impostazione di **Target Language** (Lingua di destinazione) impostando la lingua desiderata, ad esempio _German_ (Tedesco)</span><span class="sxs-lookup"><span data-stu-id="a4bc0-110">Change the **Target Language** to a language of your choosing, for example, _German_</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="a4bc0-112">Il componente Lunarcom Translation Recognizer (Script) (Riconoscimento traduzione Lunarcom - Script) non fa parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="a4bc0-112">The Lunarcom Translation Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="a4bc0-113">È stato fornito con gli asset dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="a4bc0-113">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="a4bc0-114">Se attivi la modalità di gioco, puoi testare la traduzione vocale selezionando prima il pulsante satellite.</span><span class="sxs-lookup"><span data-stu-id="a4bc0-114">If you now enter Game mode, you can test the speech translation by first pressing the satellite button.</span></span> <span data-ttu-id="a4bc0-115">Supponendo quindi che il computer disponga di un microfono, quando pronunci una frase, questa verrà tradotta nella lingua scelta e trascritta nel pannello del terminale:</span><span class="sxs-lookup"><span data-stu-id="a4bc0-115">Then, assuming your computer has a microphone, when you say something, your speech will be translated into the chosen language and transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="a4bc0-117">Poiché l'applicazione deve connettersi ad Azure, assicurati che il computer o il dispositivo sia connesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="a4bc0-117">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="a4bc0-118">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="a4bc0-118">Congratulations</span></span>

<span data-ttu-id="a4bc0-119">Il progetto ora è in grado di tradurre correttamente in lingue diverse le parole che pronunci.</span><span class="sxs-lookup"><span data-stu-id="a4bc0-119">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="a4bc0-120">Esegui l'applicazione sul dispositivo per verificare che la funzionalità venga eseguita correttamente.</span><span class="sxs-lookup"><span data-stu-id="a4bc0-120">Run the application on your device to ensure the feature is working properly.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a4bc0-121">Esercitazione successiva: 4. Configurazione di finalità e comprensione del linguaggio naturale</span><span class="sxs-lookup"><span data-stu-id="a4bc0-121">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
