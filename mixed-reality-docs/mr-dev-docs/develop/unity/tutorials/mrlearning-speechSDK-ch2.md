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
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="f21cc-104">2. Aggiunta di una modalità offline per la conversione locale della voce in testo scritto</span><span class="sxs-lookup"><span data-stu-id="f21cc-104">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="f21cc-105">In questa esercitazione aggiungerai la possibilità di eseguire comandi con il riconoscimento vocale di Azure, che consentirà di eseguire un evento in base alla parola o alla frase definita.</span><span class="sxs-lookup"><span data-stu-id="f21cc-105">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="f21cc-106">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f21cc-106">Objectives</span></span>

* <span data-ttu-id="f21cc-107">Imparare a usare il riconoscimento vocale di Azure per eseguire comandi</span><span class="sxs-lookup"><span data-stu-id="f21cc-107">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="f21cc-108">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="f21cc-108">Instructions</span></span>

<span data-ttu-id="f21cc-109">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom** e quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Wake Word Recognizer (Script)** (Riconoscimento parola di attivazione Lunarcom - Script) all'oggetto Lunarcom e configuralo come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f21cc-109">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="f21cc-110">Nel campo **Wake Word** (Parola di attivazione) immetti una frase appropriata, ad esempio _Activate Terminal_.</span><span class="sxs-lookup"><span data-stu-id="f21cc-110">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="f21cc-111">Nel campo **Dismiss Word** (Parola di eliminazione) immetti una frase appropriata, ad esempio _Dismiss Terminal_.</span><span class="sxs-lookup"><span data-stu-id="f21cc-111">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![Editor di Unity con il componente Lunarcom Wake Word Recognizer (Script) evidenziato](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="f21cc-113">Il componente Lunarcom Wake Word Recognizer (Script) (Riconoscimento parola di attivazione Lunarcom - Script) non fa parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="f21cc-113">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="f21cc-114">È stato fornito con gli asset dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="f21cc-114">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="f21cc-115">Se ora attivi la modalità gioco, come nell'esercitazione precedente, il pannello del terminale viene abilitato per impostazione predefinita. Tuttavia, puoi ora disabilitarlo pronunciando la parola di eliminazione **Dismiss terminal**:</span><span class="sxs-lookup"><span data-stu-id="f21cc-115">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![Editor di Unity in modalità di riproduzione con la funzionalità di riconoscimento vocale in uso](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="f21cc-117">Puoi anche riabilitarlo pronunciando la parola di attivazione **Activate terminal**:</span><span class="sxs-lookup"><span data-stu-id="f21cc-117">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![Editor di Unity in modalità di riproduzione con il terminale attivo](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="f21cc-119">Poiché l'applicazione deve connettersi ad Azure, assicurati che il computer o il dispositivo sia connesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="f21cc-119">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="f21cc-120">Se si prevede di non essere spesso in grado di connettersi ad Azure, è possibile implementare i comandi vocali anche con MRTK seguendo le istruzioni contenute in [Uso dei comandi vocali](mr-learning-base-09.md).</span><span class="sxs-lookup"><span data-stu-id="f21cc-120">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Using speech commands](mr-learning-base-09.md) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f21cc-121">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="f21cc-121">Congratulations</span></span>

<span data-ttu-id="f21cc-122">Hai implementato i comandi vocali basati su Azure.</span><span class="sxs-lookup"><span data-stu-id="f21cc-122">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="f21cc-123">Esegui l'applicazione nel dispositivo per verificare che la funzionalità venga eseguita correttamente.</span><span class="sxs-lookup"><span data-stu-id="f21cc-123">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="f21cc-124">Nell'esercitazione successiva apprenderai come tradurre il parlato con la traduzione vocale di Azure.</span><span class="sxs-lookup"><span data-stu-id="f21cc-124">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f21cc-125">Esercitazione successiva: 3. Aggiunta del componente di traduzione vocale di Servizi cognitivi di Azure</span><span class="sxs-lookup"><span data-stu-id="f21cc-125">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
