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
# <a name="gaze-input"></a><span data-ttu-id="90c71-104">Input sguardo</span><span class="sxs-lookup"><span data-stu-id="90c71-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="90c71-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="90c71-105">Overview</span></span>

<span data-ttu-id="90c71-106">Il [plug-in realtà mista di Windows](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) non fornisce funzioni predefinite per l'input di sguardi, ma HoloLens 2 supporta la verifica degli occhi.</span><span class="sxs-lookup"><span data-stu-id="90c71-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="90c71-107">Le funzionalità di rilevamento effettive vengono fornite dalle API di visualizzazione e **rilevamento degli occhi** **montate** da Unreal e includono:</span><span class="sxs-lookup"><span data-stu-id="90c71-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="90c71-108">Informazioni sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="90c71-108">Device information</span></span>
- <span data-ttu-id="90c71-109">Sensori di rilevamento</span><span class="sxs-lookup"><span data-stu-id="90c71-109">Tracking sensors</span></span>
- <span data-ttu-id="90c71-110">Orientamento e posizione</span><span class="sxs-lookup"><span data-stu-id="90c71-110">Orientation and position</span></span>
- <span data-ttu-id="90c71-111">Riquadri di ritaglio</span><span class="sxs-lookup"><span data-stu-id="90c71-111">Clipping panes</span></span>
- <span data-ttu-id="90c71-112">Informazioni sugli sguardi e sui dati di rilevamento</span><span class="sxs-lookup"><span data-stu-id="90c71-112">Gaze data and tracking information</span></span>

<span data-ttu-id="90c71-113">È possibile trovare l'elenco completo delle funzionalità disponibili nella documentazione di [visualizzazione](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) e [rilevamento degli occhi](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) di Unreal.</span><span class="sxs-lookup"><span data-stu-id="90c71-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span>

<span data-ttu-id="90c71-114">Oltre alle API Unreal, consultare la documentazione relativa all' [interazione basata sull'occhio](../../design/eye-gaze-interaction.md) per HoloLens 2 e leggere le informazioni sul funzionamento del [monitoraggio degli occhi in HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) .</span><span class="sxs-lookup"><span data-stu-id="90c71-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](../../design/eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="90c71-115">Il rilevamento degli occhi è supportato solo in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="90c71-115">Eye tracking is only supported on HoloLens 2.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="90c71-116">Abilitazione del rilevamento degli occhi</span><span class="sxs-lookup"><span data-stu-id="90c71-116">Enabling eye tracking</span></span>
<span data-ttu-id="90c71-117">È necessario abilitare l'input dello sguardo nelle impostazioni del progetto HoloLens prima di poter usare le API non reali.</span><span class="sxs-lookup"><span data-stu-id="90c71-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="90c71-118">All'avvio dell'applicazione verrà visualizzata una richiesta di consenso visualizzata nella schermata seguente.</span><span class="sxs-lookup"><span data-stu-id="90c71-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="90c71-119">Selezionare **Sì** per impostare l'autorizzazione e ottenere l'accesso a sguardi input.</span><span class="sxs-lookup"><span data-stu-id="90c71-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="90c71-120">Se è necessario modificare questa impostazione in qualsiasi momento, è possibile trovarla nell'app **Impostazioni** .</span><span class="sxs-lookup"><span data-stu-id="90c71-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![Autorizzazioni di input per gli occhi](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="90c71-122">HoloLens Eye Tracking in Unreal ha solo un singolo raggio di sguardi per entrambi gli occhi anziché i due raggi necessari per il rilevamento stereoscopico, che non è supportato.</span><span class="sxs-lookup"><span data-stu-id="90c71-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="90c71-123">Questa è tutta la configurazione necessaria per iniziare ad aggiungere l'input dello sguardo alle app HoloLens 2 in modo irreale.</span><span class="sxs-lookup"><span data-stu-id="90c71-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="90c71-124">Altre informazioni sull'input di sguardi e sul modo in cui influiscono sugli utenti in realtà mista sono disponibili nei collegamenti seguenti.</span><span class="sxs-lookup"><span data-stu-id="90c71-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="90c71-125">Quando si compilano esperienze interattive, tenere presente quanto prima.</span><span class="sxs-lookup"><span data-stu-id="90c71-125">Be sure to think about these when building your interactive experiences.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="90c71-126">Checkpoint di sviluppo successivo</span><span class="sxs-lookup"><span data-stu-id="90c71-126">Next Development Checkpoint</span></span>

<span data-ttu-id="90c71-127">Se si segue il percorso di checkpoint dello sviluppo non reale, si sta per esplorare i blocchi predefiniti di MRTK core.</span><span class="sxs-lookup"><span data-stu-id="90c71-127">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="90c71-128">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="90c71-128">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="90c71-129">Tracciamento mano</span><span class="sxs-lookup"><span data-stu-id="90c71-129">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="90c71-130">In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="90c71-130">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="90c71-131">Fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="90c71-131">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="90c71-132">È sempre possibile tornare ai checkpoint di [sviluppo non reali](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="90c71-132">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="90c71-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="90c71-133">See also</span></span>
* [<span data-ttu-id="90c71-134">Calibrazione</span><span class="sxs-lookup"><span data-stu-id="90c71-134">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="90c71-135">Comodità</span><span class="sxs-lookup"><span data-stu-id="90c71-135">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="90c71-136">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="90c71-136">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="90c71-137">Input vocale</span><span class="sxs-lookup"><span data-stu-id="90c71-137">Voice input</span></span>](../../out-of-scope/voice-design.md)
