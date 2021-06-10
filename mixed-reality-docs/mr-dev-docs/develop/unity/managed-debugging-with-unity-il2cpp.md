---
title: Debug gestito con Unity
description: Questo articolo illustra come eseguire un debugger gestito nel progetto UWP Unity IL2CPP.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity, visual studio, debug, il2cpp, HoloLens, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale, UWP
ms.openlocfilehash: 8e3967971220fa453f4e60639bd08f2554a8dd7e
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547082"
---
# <a name="managed-debugging-with-unity"></a><span data-ttu-id="19d5b-104">Debug gestito con Unity</span><span class="sxs-lookup"><span data-stu-id="19d5b-104">Managed debugging with Unity</span></span>

<span data-ttu-id="19d5b-105">Seguire questa procedura per collegare un debugger gestito alla build UWP di Unity IL2CPP per HoloLens e HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="19d5b-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="19d5b-106">È necessario essere in una rete che supporta [multicast](https://en.wikipedia.org/wiki/Multicast).</span><span class="sxs-lookup"><span data-stu-id="19d5b-106">You'll need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
2. <span data-ttu-id="19d5b-107">Passare a **Funzionalità delle impostazioni di pubblicazione UWP** e controllare **InternetClientServer** e **PrivateNetworkClientServer:**</span><span class="sxs-lookup"><span data-stu-id="19d5b-107">Go to **UWP Publishing Settings Capabilities** and check **InternetClientServer** and **PrivateNetworkClientServer**:</span></span>

    ![Funzionalità delle impostazioni di pubblicazione UWP](images/il2cpp-debugging-capabilities.png)

3. <span data-ttu-id="19d5b-109">Configurare le impostazioni di compilazione UWP di Unity:</span><span class="sxs-lookup"><span data-stu-id="19d5b-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="19d5b-110">Development Build</span><span class="sxs-lookup"><span data-stu-id="19d5b-110">Development Build</span></span>
    - <span data-ttu-id="19d5b-111">Debug degli script</span><span class="sxs-lookup"><span data-stu-id="19d5b-111">Script Debugging</span></span>
    - <span data-ttu-id="19d5b-112">Attendere il debugger gestito (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="19d5b-112">Wait for Managed Debugger (optional)</span></span>

    ![Impostazioni di compilazione UWP](images/il2cpp-debugging-build.png)

4. <span data-ttu-id="19d5b-114">Compilare in Unity.</span><span class="sxs-lookup"><span data-stu-id="19d5b-114">Build in Unity.</span></span>
5. <span data-ttu-id="19d5b-115">Compilare e distribuire dalla soluzione Visual Studio nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="19d5b-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="19d5b-116">È consigliabile eseguire la compilazione con **le configurazioni debug** **o versione.**</span><span class="sxs-lookup"><span data-stu-id="19d5b-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="19d5b-117">La **configurazione Master** disabilita il profiler Unity e può impedire il debug ottimale.</span><span class="sxs-lookup"><span data-stu-id="19d5b-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="19d5b-118">Facoltativamente, verificare **Internet (Client & Server)** e Reti private **(Client & Server)** nell'elenco delle funzionalità in Package.appxmanifest nella soluzione.</span><span class="sxs-lookup"><span data-stu-id="19d5b-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
6. <span data-ttu-id="19d5b-119">Assicurarsi che il dispositivo sia connesso alla stessa rete del PC e avviare l'app nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="19d5b-119">Make sure your device is connected to the same network as your PC and start the app on your device.</span></span>
7. <span data-ttu-id="19d5b-120">Assicurarsi che il **dispositivo non sia** connesso al PC tramite USB.</span><span class="sxs-lookup"><span data-stu-id="19d5b-120">Make sure the device **is not** connected to your PC via USB.</span></span>
8. <span data-ttu-id="19d5b-121">Fare doppio clic su uno degli script in Unity e passare alla soluzione Visual Studio visualizzata per visualizzarla e modificarla.</span><span class="sxs-lookup"><span data-stu-id="19d5b-121">Double-click one of your scripts in Unity and go to the Visual Studio solution that opens to view and edit.</span></span>
9. <span data-ttu-id="19d5b-122">Debug -> collegare il debugger unity.</span><span class="sxs-lookup"><span data-stu-id="19d5b-122">Debug -> Attach Unity Debugger.</span></span>

    ![Collega debugger Unity](images/il2cpp-debugging-attach.png)

10. <span data-ttu-id="19d5b-124">Selezionare il dispositivo nell'elenco e fare clic su "OK" per collegarsi.</span><span class="sxs-lookup"><span data-stu-id="19d5b-124">Select your device in the list and click "OK" to attach.</span></span>

    ![Elenco dei dispositivi](images/il2cpp-debugging-machines.png)
