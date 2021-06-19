---
title: Creare un'applicazione Holographic Remoting per PC
description: In questo corso viene illustrato come creare un'applicazione per PC per usare in remoto un'esperienza di realtà mista da PC a HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, holographic remoting per PC, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: ca0efe13acac4408a05ab89eb98b508e9993c5a4
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392540"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="4c878-104">2. Creazione di un'applicazione Holographic Remoting per PC</span><span class="sxs-lookup"><span data-stu-id="4c878-104">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="4c878-105">In questa esercitazione si apprenderà come creare un'app Holographic Remoting per PC e connettere HoloLens 2 in qualsiasi momento, offrendo un modo per visualizzare il contenuto 3D in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="4c878-105">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="4c878-106">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="4c878-106">Objectives</span></span>

* <span data-ttu-id="4c878-107">Configurare Unity per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="4c878-107">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="4c878-108">Imparare a compilare e distribuire l'applicazione con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4c878-108">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="4c878-109">Sviluppare un'applicazione Holographic Remoting e connetterla a HoloLens</span><span class="sxs-lookup"><span data-stu-id="4c878-109">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="4c878-110">Configurazione delle funzionalità</span><span class="sxs-lookup"><span data-stu-id="4c878-110">Configuring the capabilities</span></span>

<span data-ttu-id="4c878-111">Nella finestra **Impostazioni progetto** espandere Impostazioni di pubblicazione **,** scorrere verso il basso fino alla sezione Funzionalità e selezionare la casella di controllo funzionalità visualizzata di seguito oltre alle funzionalità esistenti.</span><span class="sxs-lookup"><span data-stu-id="4c878-111">In the **Project Settings** window, expand the **Publishing Settings**, scroll down to the Capabilities section and select the below-shown capability checkbox in addition to the existing capabilities.</span></span>

* <span data-ttu-id="4c878-112">Client e server Internet</span><span class="sxs-lookup"><span data-stu-id="4c878-112">Internet Clint server</span></span>
* <span data-ttu-id="4c878-113">Client e server di rete privata</span><span class="sxs-lookup"><span data-stu-id="4c878-113">Private Network Client Server</span></span>

![abilitazione delle funzionalità](images/mrlearning-pc-holographic-remoting/tutorial2-section0-step1-1.png)

[!INCLUDE[](includes/configuring-scene-for-holographic-remoting.md)]

## <a name="build-your-application-to-pc"></a><span data-ttu-id="4c878-115">Compilare l'applicazione nel PC</span><span class="sxs-lookup"><span data-stu-id="4c878-115">Build your application to PC</span></span>

<span data-ttu-id="4c878-116">L'app Holographic Remoting è ora pronta per la compilazione nel PC.</span><span class="sxs-lookup"><span data-stu-id="4c878-116">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="4c878-117">Attenersi ai passaggi seguenti e apportare queste modifiche per compilare l'applicazione nel PC.</span><span class="sxs-lookup"><span data-stu-id="4c878-117">Follow the below steps and make these changes to build this application on to your PC.</span></span>

[!INCLUDE[](includes/build-your-application-to-pc.md)]

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="4c878-118">Test di un'applicazione remota Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="4c878-118">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="4c878-119">Per connettere l'applicazione PC a HoloLens 2, seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="4c878-119">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="4c878-120">1. Installare l'applicazione Remoting Player nel dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4c878-120">1. Install the Remoting Player application on HoloLens 2 device</span></span>

* <span data-ttu-id="4c878-121">In HoloLens 2 visitare l'app dello Store e cercare "**Remoting Player**".</span><span class="sxs-lookup"><span data-stu-id="4c878-121">On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="4c878-122">Selezionare l'app **Remoting Player**.</span><span class="sxs-lookup"><span data-stu-id="4c878-122">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="4c878-123">Toccare **Install** (Installa) per scaricare e installare l'app.</span><span class="sxs-lookup"><span data-stu-id="4c878-123">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="4c878-124">2. Connettere l'app del PC Holographic Remoting a Remoting Player</span><span class="sxs-lookup"><span data-stu-id="4c878-124">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="4c878-125">Avviare **Remoting Player** in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4c878-125">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="4c878-126">Prendere nota dell'**indirizzo IP** di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4c878-126">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="4c878-127">Verrà visualizzato come ologramma da **Remoting Player** non appena viene avviato.</span><span class="sxs-lookup"><span data-stu-id="4c878-127">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="4c878-128">Aprire l'applicazione Holographic Remoting per PC nel PC in uso.</span><span class="sxs-lookup"><span data-stu-id="4c878-128">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="4c878-129">Una volta avviata l'applicazione, immettere l'**indirizzo IP** e fare clic sul pulsante **Connect** (Connetti) per connettersi.</span><span class="sxs-lookup"><span data-stu-id="4c878-129">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="4c878-130">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="4c878-130">Congratulations</span></span>

<span data-ttu-id="4c878-131">In questa esercitazione si è appreso come creare un'app remota Holographic Remoting e connetterla a HoloLens 2 in qualsiasi momento, offrendo un modo per visualizzare il contenuto 3D in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="4c878-131">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="4c878-132">Dopo aver connesso HoloLens all'applicazione PC Holographic Remoting, si noterà che l'esperienza di realtà mista è in streaming nel dispositivo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4c878-132">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>
