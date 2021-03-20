---
title: EyeTracking_Main
description: Pagina di destinazione del rilevamento degli occhi in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: 71dcdb119ce6e2d340392afe840f9eaea3efeb48
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687271"
---
# <a name="eye-tracking-in-the-mixed-reality-toolkit"></a><span data-ttu-id="7bab5-104">Rilevamento degli occhi nel Toolkit per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="7bab5-104">Eye tracking in the Mixed Reality Toolkit</span></span>

![Rilevamento degli occhi in MRTK](../images/eye-tracking/mrtk_et_compilation.png)

<span data-ttu-id="7bab5-106">_HoloLens 2_ offre un nuovo input entusiasmante e potente: rilevamento degli occhi!</span><span class="sxs-lookup"><span data-stu-id="7bab5-106">_HoloLens 2_ offers an exciting and powerful new input: Eye tracking!</span></span>
<span data-ttu-id="7bab5-107">Il rilevamento degli occhi consente agli utenti di interagire in modo rapido e semplice con gli ologrammi attraverso la visualizzazione e può rendere il sistema più intelligente identificando meglio l'intenzione di un utente.</span><span class="sxs-lookup"><span data-stu-id="7bab5-107">Eye tracking enables users to quickly and effortlessly engage with holograms across their view and can make your system smarter by better identifying a user's intention.</span></span> <span data-ttu-id="7bab5-108">Per altri dettagli, vedere la documentazione di Microsoft Mixed Reality [sulla gestione degli occhi su HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) , ad esempio la spiegazione di potenti applicazioni e linee guida di progettazione per il rilevamento degli occhi in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="7bab5-108">Check out Microsoft's Mixed Reality [documentation on eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) for more details, such as explaining powerful applications and design guidelines for eye tracking in mixed reality.</span></span>

<span data-ttu-id="7bab5-109">Nuovo per la verifica degli occhi?</span><span class="sxs-lookup"><span data-stu-id="7bab5-109">New to eye tracking?</span></span> <span data-ttu-id="7bab5-110">non è un problema.</span><span class="sxs-lookup"><span data-stu-id="7bab5-110">No problem!</span></span> <span data-ttu-id="7bab5-111">Sono disponibili numerosi video, esercitazioni ed esempi per iniziare a usare il Toolkit per la [realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span><span class="sxs-lookup"><span data-stu-id="7bab5-111">There are a number of videos, tutorials and samples to get you started in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)!</span></span>
<span data-ttu-id="7bab5-112">È consigliabile iniziare esaminando alcuni degli esempi di monitoraggio degli occhi esistenti che illustrano le procedure consigliate per le interazioni basate sull'occhio.</span><span class="sxs-lookup"><span data-stu-id="7bab5-112">It is recommended to start by exploring some of the existing eye tracking samples that demonstrate best practices for eye-based interactions.</span></span> <span data-ttu-id="7bab5-113">È quindi possibile usare questi esempi per estrarre le parti che sembrano rilevanti per l'utente nell'app.</span><span class="sxs-lookup"><span data-stu-id="7bab5-113">You can then use these samples to pull the parts that seem relevant to you into your app.</span></span> <span data-ttu-id="7bab5-114">Infine, viene descritto come configurare una nuova scena con i componenti di base per tenere traccia degli occhi in funzione nell'app.</span><span class="sxs-lookup"><span data-stu-id="7bab5-114">Finally, we also describe how to set up a fresh scene with the core components to get eye tracking working in your app.</span></span>

1. [<span data-ttu-id="7bab5-115">Esempi di rilevamento degli occhi di MRTK</span><span class="sxs-lookup"><span data-stu-id="7bab5-115">MRTK eye tracking samples</span></span>](EyeTracking_ExamplesOverview.md)

2. [<span data-ttu-id="7bab5-116">Configurazione di MRTK Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="7bab5-116">MRTK eye tracking setup</span></span>](EyeTracking_BasicSetup.md)

3. [<span data-ttu-id="7bab5-117">Accesso ai dati di rilevamento degli occhi tramite codice</span><span class="sxs-lookup"><span data-stu-id="7bab5-117">Accessing eye tracking data via Code</span></span>](EyeTracking_EyeGazeProvider.md)

4. [<span data-ttu-id="7bab5-118">Convalidare la calibrazione del rilevamento degli occhi sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="7bab5-118">Validate eye tracking calibration on device</span></span>](EyeTracking_IsUserCalibrated.md)

## <a name="see-also"></a><span data-ttu-id="7bab5-119">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="7bab5-119">See also</span></span>

- [<span data-ttu-id="7bab5-120">Configurazione di MRTK Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="7bab5-120">MRTK Eye Tracking setup</span></span>](EyeTracking_BasicSetup.md)
- [<span data-ttu-id="7bab5-121">MRTK la verifica degli occhi tramite codice</span><span class="sxs-lookup"><span data-stu-id="7bab5-121">MRTK Eye Tracking via Code</span></span>](EyeTracking_EyeGazeProvider.md)
- [<span data-ttu-id="7bab5-122">Calibrazione di MRTK Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="7bab5-122">MRTK Eye Tracking Calibration</span></span>](EyeTracking_IsUserCalibrated.md)
- [<span data-ttu-id="7bab5-123">Documentazione di HoloLens 2 Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="7bab5-123">HoloLens 2 Eye Tracking Documentation</span></span>](https://docs.microsoft.com/windows/mixed-reality/eye-tracking)
