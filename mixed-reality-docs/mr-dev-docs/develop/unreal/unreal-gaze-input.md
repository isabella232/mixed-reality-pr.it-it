---
title: Input di sguardi in Unreal
description: Esercitazione sulla configurazione dell'input di sguardi per HoloLens e Unreal Engine
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, HoloLens 2, rilevamento degli occhi, input di sguardi, visualizzazione montata su schermo, Unreal Engine, auricolare realtà mista, auricolare della realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 2ea55e3c53275f6150ca7f2def10d71634119e2e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679050"
---
# <a name="gaze-input"></a><span data-ttu-id="2a17e-104">Input sguardo</span><span class="sxs-lookup"><span data-stu-id="2a17e-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="2a17e-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="2a17e-105">Overview</span></span>

<span data-ttu-id="2a17e-106">Il [plug-in realtà mista di Windows](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) non fornisce funzioni predefinite per l'input di sguardi, ma HoloLens 2 supporta la verifica degli occhi.</span><span class="sxs-lookup"><span data-stu-id="2a17e-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="2a17e-107">Le funzionalità di rilevamento effettive vengono fornite dalle API di visualizzazione e **rilevamento degli occhi** **montate** da Unreal e includono:</span><span class="sxs-lookup"><span data-stu-id="2a17e-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="2a17e-108">Informazioni sul dispositivo</span><span class="sxs-lookup"><span data-stu-id="2a17e-108">Device information</span></span>
- <span data-ttu-id="2a17e-109">Sensori di rilevamento</span><span class="sxs-lookup"><span data-stu-id="2a17e-109">Tracking sensors</span></span>
- <span data-ttu-id="2a17e-110">Orientamento e posizione</span><span class="sxs-lookup"><span data-stu-id="2a17e-110">Orientation and position</span></span>
- <span data-ttu-id="2a17e-111">Riquadri di ritaglio</span><span class="sxs-lookup"><span data-stu-id="2a17e-111">Clipping panes</span></span>
- <span data-ttu-id="2a17e-112">Informazioni sugli sguardi e sui dati di rilevamento</span><span class="sxs-lookup"><span data-stu-id="2a17e-112">Gaze data and tracking information</span></span>

<span data-ttu-id="2a17e-113">È possibile trovare l'elenco completo delle funzionalità disponibili nella documentazione di [visualizzazione](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) e [rilevamento degli occhi](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) di Unreal.</span><span class="sxs-lookup"><span data-stu-id="2a17e-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span>

<span data-ttu-id="2a17e-114">Oltre alle API Unreal, consultare la documentazione relativa all' [interazione basata sull'occhio](../../design/eye-gaze-interaction.md) per HoloLens 2 e leggere le informazioni sul funzionamento del [monitoraggio degli occhi in HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) .</span><span class="sxs-lookup"><span data-stu-id="2a17e-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](../../design/eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2a17e-115">Il rilevamento degli occhi è supportato solo in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2a17e-115">Eye tracking is only supported on HoloLens 2.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="2a17e-116">Abilitazione del rilevamento degli occhi</span><span class="sxs-lookup"><span data-stu-id="2a17e-116">Enabling eye tracking</span></span>
<span data-ttu-id="2a17e-117">È necessario abilitare l'input dello sguardo nelle impostazioni del progetto HoloLens prima di poter usare le API non reali.</span><span class="sxs-lookup"><span data-stu-id="2a17e-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="2a17e-118">All'avvio dell'applicazione verrà visualizzata una richiesta di consenso visualizzata nella schermata seguente.</span><span class="sxs-lookup"><span data-stu-id="2a17e-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="2a17e-119">Selezionare **Sì** per impostare l'autorizzazione e ottenere l'accesso a sguardi input.</span><span class="sxs-lookup"><span data-stu-id="2a17e-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="2a17e-120">Se è necessario modificare questa impostazione in qualsiasi momento, è possibile trovarla nell'app **Impostazioni** .</span><span class="sxs-lookup"><span data-stu-id="2a17e-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![Autorizzazioni di input per gli occhi](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="2a17e-122">HoloLens Eye Tracking in Unreal ha solo un singolo raggio di sguardi per entrambi gli occhi anziché i due raggi necessari per il rilevamento stereoscopico, che non è supportato.</span><span class="sxs-lookup"><span data-stu-id="2a17e-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="2a17e-123">Questa è tutta la configurazione necessaria per iniziare ad aggiungere l'input dello sguardo alle app HoloLens 2 in modo irreale.</span><span class="sxs-lookup"><span data-stu-id="2a17e-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="2a17e-124">Altre informazioni sull'input di sguardi e sul modo in cui influiscono sugli utenti in realtà mista sono disponibili nei collegamenti seguenti.</span><span class="sxs-lookup"><span data-stu-id="2a17e-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="2a17e-125">Quando si compilano esperienze interattive, tenere presente quanto prima.</span><span class="sxs-lookup"><span data-stu-id="2a17e-125">Be sure to think about these when building your interactive experiences.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="2a17e-126">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="2a17e-126">Next Development Checkpoint</span></span>

<span data-ttu-id="2a17e-127">Se si segue il percorso di checkpoint per lo sviluppo con Unreal che è stato delineato, si stanno esplorando i blocchi predefiniti fondamentali di MRTK.</span><span class="sxs-lookup"><span data-stu-id="2a17e-127">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="2a17e-128">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="2a17e-128">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="2a17e-129">Tracciamento mano</span><span class="sxs-lookup"><span data-stu-id="2a17e-129">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="2a17e-130">In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="2a17e-130">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2a17e-131">Fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="2a17e-131">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="2a17e-132">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="2a17e-132">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a17e-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2a17e-133">See also</span></span>
* [<span data-ttu-id="2a17e-134">Calibrazione</span><span class="sxs-lookup"><span data-stu-id="2a17e-134">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="2a17e-135">Comodità</span><span class="sxs-lookup"><span data-stu-id="2a17e-135">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="2a17e-136">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="2a17e-136">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="2a17e-137">Input vocale</span><span class="sxs-lookup"><span data-stu-id="2a17e-137">Voice input</span></span>](../../out-of-scope/voice-design.md)
