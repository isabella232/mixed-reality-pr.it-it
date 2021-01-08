---
title: Sguardo fisso e attesa
description: Ottenere una panoramica generale del modello di input occhi e Head per le applicazioni di realtà miste.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realtà mista, sguardo, abitazione, interazione, progettazione, rilevamento degli occhi, rilevamento Head, auricolare in realtà mista, auricolare di realtà mista di Windows, headset di realtà virtuale, HoloLens, MRTK, Toolkit di realtà mista
ms.openlocfilehash: 2daeea996251b1220ee4753567b42117fbb2126c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007641"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="4cf0e-104">Sguardo fisso e attesa</span><span class="sxs-lookup"><span data-stu-id="4cf0e-104">Gaze and dwell</span></span>

<span data-ttu-id="4cf0e-105">Quando le mani sono occupate con gli attrezzi e le parti, i movimenti possono risultare difficili o addirittura impossibili.</span><span class="sxs-lookup"><span data-stu-id="4cf0e-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>
<span data-ttu-id="4cf0e-106">I comandi vocali possono anche essere inaffidabili in determinati contesti, ad esempio in condizioni troppo potenti.</span><span class="sxs-lookup"><span data-stu-id="4cf0e-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span>
<span data-ttu-id="4cf0e-107">Sguardi e abitazioni offre un meccanismo familiare e facile da gestire per l'esecuzione di attività di Head-up e hands-free in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4cf0e-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span>
<span data-ttu-id="4cf0e-108">Inoltre, lo sguardo e l'abitazione sono un ottimo fallback, indipendente dall'interferenza del rumore o dai vincoli di silenzio nell'ambiente operativo.</span><span class="sxs-lookup"><span data-stu-id="4cf0e-108">Additionally, gaze and dwell is a great fallback, which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="4cf0e-109">Si distinguono due varianti di _sguardo e dimora_, ovvero lo [sguardo](gaze-and-dwell-head.md) e l'abitato e lo [sguardo e l'abitazione](gaze-and-dwell-eyes.md).</span><span class="sxs-lookup"><span data-stu-id="4cf0e-109">We distinguish two variants of _gaze and dwell_: [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="4cf0e-110">Scenari</span><span class="sxs-lookup"><span data-stu-id="4cf0e-110">Scenarios</span></span>

<span data-ttu-id="4cf0e-111">Lo sguardo e la permanenza si adattano a scenari in cui le mani di una persona sono occupate da altre attività e la voce non è del 100% affidabile o disponibile a causa di vincoli ambientali o sociali.</span><span class="sxs-lookup"><span data-stu-id="4cf0e-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="4cf0e-112">Un buon esempio di questo tipo di situazioni è dato da una persona che indossa un dispositivo HoloLens per la sovrimpressione di informazioni di riferimento mentre ripara il motore di un'automobile.</span><span class="sxs-lookup"><span data-stu-id="4cf0e-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span>
<span data-ttu-id="4cf0e-113">Le sue mani sono occupate con gli attrezzi o devono sostenere il corpo mentre la persona si protende sul vano motore.</span><span class="sxs-lookup"><span data-stu-id="4cf0e-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span>
<span data-ttu-id="4cf0e-114">L'autofficina è rumorosa a causa dei colpi e del ronzio costanti degli attrezzi da lavoro, quindi l'uso dei comandi vocali risulterebbe particolarmente difficoltoso.</span><span class="sxs-lookup"><span data-stu-id="4cf0e-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span>
<span data-ttu-id="4cf0e-115">Lo sguardo e l'abitazione consentono all'utente che usa HoloLens di esplorare in modo sicuro il materiale di riferimento senza interrompere il flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="4cf0e-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span>

## <a name="device-support"></a><span data-ttu-id="4cf0e-116">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="4cf0e-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4cf0e-117"><strong>Modello di input</strong></span><span class="sxs-lookup"><span data-stu-id="4cf0e-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="4cf0e-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="4cf0e-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="4cf0e-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="4cf0e-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="4cf0e-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="4cf0e-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4cf0e-121">Puntamento con la testa e attesa</span><span class="sxs-lookup"><span data-stu-id="4cf0e-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="4cf0e-122">✔️ Consigliato</span><span class="sxs-lookup"><span data-stu-id="4cf0e-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="4cf0e-123">✔️ Consigliato</span><span class="sxs-lookup"><span data-stu-id="4cf0e-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="4cf0e-124">✔️ Consigliato</span><span class="sxs-lookup"><span data-stu-id="4cf0e-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4cf0e-125">Sguardo fisso e attesa</span><span class="sxs-lookup"><span data-stu-id="4cf0e-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="4cf0e-126">❌ Non disponibile</span><span class="sxs-lookup"><span data-stu-id="4cf0e-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="4cf0e-127">✔️ Consigliata</span><span class="sxs-lookup"><span data-stu-id="4cf0e-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="4cf0e-128">❌ Non disponibile</span><span class="sxs-lookup"><span data-stu-id="4cf0e-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a><span data-ttu-id="4cf0e-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4cf0e-129">See also</span></span>

* [<span data-ttu-id="4cf0e-130">Interazione basata sullo sguardo</span><span class="sxs-lookup"><span data-stu-id="4cf0e-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="4cf0e-131">Tracciamento oculare in HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4cf0e-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="4cf0e-132">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="4cf0e-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="4cf0e-133">Mani - Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="4cf0e-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="4cf0e-134">Mani - Movimenti</span><span class="sxs-lookup"><span data-stu-id="4cf0e-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="4cf0e-135">Mani - Puntamento e commit</span><span class="sxs-lookup"><span data-stu-id="4cf0e-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="4cf0e-136">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="4cf0e-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="4cf0e-137">Input vocale</span><span class="sxs-lookup"><span data-stu-id="4cf0e-137">Voice input</span></span>](voice-input.md)
