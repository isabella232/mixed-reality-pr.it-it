---
title: Distribuire nel dispositivo in Unreal
description: Guida alla distribuzione di un dispositivo in Unreal a HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, distribuzione su dispositivo, PC, documentazione, auricolare realtà mista, headset di realtà mista di Windows, auricolare della realtà virtuale
appliesto:
- HoloLens 2
ms.openlocfilehash: 390bd1a9f1bc643efb1a342421e8c96574e74334
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925903"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="d5d2a-104">Distribuire nel dispositivo in Unreal</span><span class="sxs-lookup"><span data-stu-id="d5d2a-104">Deploy to device in Unreal</span></span>

<span data-ttu-id="d5d2a-105">Esistono due modi per distribuire un'applicazione Unreal in HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="d5d2a-105">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="d5d2a-106">Direttamente dall'editor non reale</span><span class="sxs-lookup"><span data-stu-id="d5d2a-106">Directly from the Unreal editor</span></span>
* <span data-ttu-id="d5d2a-107">Come pacchetto caricato tramite il portale del dispositivo</span><span class="sxs-lookup"><span data-stu-id="d5d2a-107">As a package uploaded via the device portal</span></span>

<span data-ttu-id="d5d2a-108">Per entrambe le opzioni è necessario configurare il HoloLens per l'uso del portale per lo sviluppo del [dispositivo](../platform-capabilities-and-apis/using-the-windows-device-portal.md) .</span><span class="sxs-lookup"><span data-stu-id="d5d2a-108">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="d5d2a-109">Distribuzione nel dispositivo da un editor non reale</span><span class="sxs-lookup"><span data-stu-id="d5d2a-109">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="d5d2a-110">Selezionare la freccia a discesa accanto al pulsante **Avvia** .</span><span class="sxs-lookup"><span data-stu-id="d5d2a-110">Select the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="d5d2a-111">Inizialmente, l'opzione del dispositivo HoloLens sarà disabilitata.</span><span class="sxs-lookup"><span data-stu-id="d5d2a-111">Initially, the HoloLens device option will be grayed out.</span></span>

![Opzioni menu a discesa Avvia](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="d5d2a-113">Aprire il **Device Manager** e notare che il HoloLens non verrà visualizzato automaticamente nell'elenco dei dispositivi.</span><span class="sxs-lookup"><span data-stu-id="d5d2a-113">Open the **Device Manager** and note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="d5d2a-114">Espandere la sezione **aggiungere un dispositivo** non in elenco.</span><span class="sxs-lookup"><span data-stu-id="d5d2a-114">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="d5d2a-115">Selezionare **HoloLens** come **piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="d5d2a-115">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="d5d2a-116">Immettere le informazioni sull'indirizzo IP e sulla porta dei dispositivi separati da due punti come identificatore del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d5d2a-116">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="d5d2a-117">Ad esempio, "127.0.0.1:10080" (quando si è connessi tramite USB).</span><span class="sxs-lookup"><span data-stu-id="d5d2a-117">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="d5d2a-118">Usare le credenziali del nome utente e della password del portale del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d5d2a-118">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="d5d2a-119">Premere **Aggiungi** e chiudere Gestione dispositivi.</span><span class="sxs-lookup"><span data-stu-id="d5d2a-119">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="d5d2a-120">Se si verifica un errore, ad esempio un indirizzo errato o le credenziali dell'utente, verrà stampato un messaggio nel log di output.</span><span class="sxs-lookup"><span data-stu-id="d5d2a-120">If there's an error, such as wrong address or user credentials, a message will print to the Output Log.</span></span>

![Aggiunta di un dispositivo non in elenco](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="d5d2a-122">Selezionare di nuovo la freccia a discesa accanto al pulsante **Launch (avvia** ). questa volta dovrebbe essere visualizzato il dispositivo HoloLens appena aggiunto.</span><span class="sxs-lookup"><span data-stu-id="d5d2a-122">Select the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="d5d2a-123">Selezionare il dispositivo HoloLens da compilare e distribuire in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d5d2a-123">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="d5d2a-124">La compilazione per il dispositivo può comportare la ricompilazione degli shader (soprattutto alla prima esecuzione). questa operazione può richiedere alcuni minuti.</span><span class="sxs-lookup"><span data-stu-id="d5d2a-124">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="d5d2a-125">Non lasciare che il dispositivo vada a dormire fino a quando l'app non è in esecuzione (potrebbe essere necessario investirla).</span><span class="sxs-lookup"><span data-stu-id="d5d2a-125">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="d5d2a-126">In caso contrario, la compilazione dello shader non riuscirà.</span><span class="sxs-lookup"><span data-stu-id="d5d2a-126">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="d5d2a-127">Distribuzione nel dispositivo tramite il portale del dispositivo</span><span class="sxs-lookup"><span data-stu-id="d5d2a-127">Deploying to device via device portal</span></span>

<span data-ttu-id="d5d2a-128">Per istruzioni dettagliate sulla creazione di pacchetti e sulla distribuzione di un'app, vedere la [serie di esercitazioni su Unreal](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span><span class="sxs-lookup"><span data-stu-id="d5d2a-128">You can find detailed instructions on packaging and deploying an app in the [Unreal tutorial series](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="d5d2a-129">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="d5d2a-129">Next Development Checkpoint</span></span>

<span data-ttu-id="d5d2a-130">Se si sta seguendo il percorso di sviluppo non reale, si è in fase di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="d5d2a-130">If you're following the Unreal development journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="d5d2a-131">Da qui è possibile continuare ad aggiungere servizi avanzati:</span><span class="sxs-lookup"><span data-stu-id="d5d2a-131">From here, you can continue to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d5d2a-132">Servizi avanzati</span><span class="sxs-lookup"><span data-stu-id="d5d2a-132">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="d5d2a-133">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="d5d2a-133">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) at any time.</span></span>
