---
title: Debug gestito con Unity IL2CPP
description: Questo articolo illustra come eseguire un debugger gestito nel progetto Unity IL2CPP UWP.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, debug, il2cpp, HoloLens, cuffie per realtà mista, cuffie con realtà mista di Windows, cuffie per realtà virtuale, UWP
ms.openlocfilehash: 4b21e4888e467e6bd5f1938024a1b8312d8ecbcb
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010242"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="7cad5-104">Debug gestito con Unity IL2CPP</span><span class="sxs-lookup"><span data-stu-id="7cad5-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="7cad5-105">Seguire questa procedura per aggiungere un debugger gestito alla build Unity IL2CPP UWP per HoloLens e HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7cad5-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="7cad5-106">È necessario trovarsi in una rete che supporta il [multicast](https://en.wikipedia.org/wiki/Multicast).</span><span class="sxs-lookup"><span data-stu-id="7cad5-106">You'll need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
2. <span data-ttu-id="7cad5-107">Passare a **UWP Publishing Settings capabilities** e controllare **InternetClientServer** e **PrivateNetworkClientServer**:</span><span class="sxs-lookup"><span data-stu-id="7cad5-107">Go to **UWP Publishing Settings Capabilities** and check **InternetClientServer** and **PrivateNetworkClientServer**:</span></span>

    ![Funzionalità delle impostazioni di pubblicazione UWP](images/il2cpp-debugging-capabilities.png)

3. <span data-ttu-id="7cad5-109">Configurare le impostazioni di compilazione UWP per Unity:</span><span class="sxs-lookup"><span data-stu-id="7cad5-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="7cad5-110">Development Build</span><span class="sxs-lookup"><span data-stu-id="7cad5-110">Development Build</span></span>
    - <span data-ttu-id="7cad5-111">Debug degli script</span><span class="sxs-lookup"><span data-stu-id="7cad5-111">Script Debugging</span></span>
    - <span data-ttu-id="7cad5-112">Attendi debugger gestito (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="7cad5-112">Wait for Managed Debugger (optional)</span></span>

    ![Impostazioni di compilazione UWP](images/il2cpp-debugging-build.png)

4. <span data-ttu-id="7cad5-114">Compilazione in Unity.</span><span class="sxs-lookup"><span data-stu-id="7cad5-114">Build in Unity.</span></span>
5. <span data-ttu-id="7cad5-115">Compilare e distribuire dalla soluzione Visual Studio al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7cad5-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="7cad5-116">È necessario compilare con le configurazioni di **debug** o di **rilascio** .</span><span class="sxs-lookup"><span data-stu-id="7cad5-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="7cad5-117">La configurazione **Master** Disabilita il profiler di Unity ed è in grado di impedire il debug ottimale.</span><span class="sxs-lookup"><span data-stu-id="7cad5-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="7cad5-118">Facoltativamente, verificare la **connessione Internet (client & Server)** e le **Reti Private (client & Server)** nell'elenco delle funzionalità di Package. appxmanifest nella soluzione.</span><span class="sxs-lookup"><span data-stu-id="7cad5-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
6. <span data-ttu-id="7cad5-119">Verificare che il dispositivo sia connesso alla stessa rete del PC e avviare l'app nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7cad5-119">Make sure your device is connected to the same network as your PC and start the app on your device.</span></span>
7. <span data-ttu-id="7cad5-120">Verificare che il dispositivo **non sia** connesso al PC tramite USB.</span><span class="sxs-lookup"><span data-stu-id="7cad5-120">Make sure the device **is not** connected to your PC via USB.</span></span>
8. <span data-ttu-id="7cad5-121">Fare doppio clic su uno degli script in Unity e passare alla soluzione Visual Studio che si apre per visualizzare e modificare.</span><span class="sxs-lookup"><span data-stu-id="7cad5-121">Double-click one of your scripts in Unity and go to the Visual Studio solution that opens to view and edit.</span></span>
9. <span data-ttu-id="7cad5-122">Debug-> connessione del debugger Unity.</span><span class="sxs-lookup"><span data-stu-id="7cad5-122">Debug -> Attach Unity Debugger.</span></span>

    ![Collega debugger Unity](images/il2cpp-debugging-attach.png)

10. <span data-ttu-id="7cad5-124">Selezionare il dispositivo nell'elenco e fare clic su "OK" per connettersi.</span><span class="sxs-lookup"><span data-stu-id="7cad5-124">Select your device in the list and click "OK" to attach.</span></span>

    ![Elenco dei dispositivi](images/il2cpp-debugging-machines.png)
