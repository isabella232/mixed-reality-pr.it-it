---
title: Debug gestito con Unity
description: Questo articolo illustra come eseguire un debugger gestito nel progetto UWP Unity IL2CPP.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity, visual studio, debug, il2cpp, HoloLens, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, UWP
ms.openlocfilehash: 48f5fbd4b2ac217a3f840117595aa36fb3d7c10e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394505"
---
# <a name="managed-debugging-with-unity"></a><span data-ttu-id="6e710-104">Debug gestito con Unity</span><span class="sxs-lookup"><span data-stu-id="6e710-104">Managed debugging with Unity</span></span>

<span data-ttu-id="6e710-105">Segui questa procedura per collegare un debugger gestito alla build UWP unity IL2CPP per HoloLens e HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6e710-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="6e710-106">È necessario essere in una rete che supporta il [multicast.](https://en.wikipedia.org/wiki/Multicast)</span><span class="sxs-lookup"><span data-stu-id="6e710-106">You'll need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
2. <span data-ttu-id="6e710-107">Passare a **Funzionalità delle impostazioni di pubblicazione UWP** e selezionare **InternetClientServer** e **PrivateNetworkClientServer:**</span><span class="sxs-lookup"><span data-stu-id="6e710-107">Go to **UWP Publishing Settings Capabilities** and check **InternetClientServer** and **PrivateNetworkClientServer**:</span></span>

    ![Funzionalità delle impostazioni di pubblicazione UWP](images/il2cpp-debugging-capabilities.png)

3. <span data-ttu-id="6e710-109">Configurare le impostazioni di compilazione UWP di Unity:</span><span class="sxs-lookup"><span data-stu-id="6e710-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="6e710-110">Development Build</span><span class="sxs-lookup"><span data-stu-id="6e710-110">Development Build</span></span>
    - <span data-ttu-id="6e710-111">Debug degli script</span><span class="sxs-lookup"><span data-stu-id="6e710-111">Script Debugging</span></span>
    - <span data-ttu-id="6e710-112">Attendere il debugger gestito (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="6e710-112">Wait for Managed Debugger (optional)</span></span>

    ![Impostazioni di compilazione UWP](images/il2cpp-debugging-build.png)

4. <span data-ttu-id="6e710-114">Compilare in Unity.</span><span class="sxs-lookup"><span data-stu-id="6e710-114">Build in Unity.</span></span>
5. <span data-ttu-id="6e710-115">Compilare e distribuire dalla Visual Studio al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6e710-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="6e710-116">È consigliabile eseguire la compilazione con **le configurazioni Debug** **o** Release.</span><span class="sxs-lookup"><span data-stu-id="6e710-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="6e710-117">La **configurazione master** disabilita il profiler Unity e può impedire il debug ottimale.</span><span class="sxs-lookup"><span data-stu-id="6e710-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="6e710-118">Facoltativamente, verificare **Internet (Client & Server)** e Reti private **(Client & Server)** nell'elenco delle funzionalità in Package.appxmanifest nella soluzione.</span><span class="sxs-lookup"><span data-stu-id="6e710-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
6. <span data-ttu-id="6e710-119">Assicurarsi che il dispositivo sia connesso alla stessa rete del PC e avviare l'app nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6e710-119">Make sure your device is connected to the same network as your PC and start the app on your device.</span></span>
7. <span data-ttu-id="6e710-120">Assicurarsi che il **dispositivo non sia** connesso al PC tramite USB.</span><span class="sxs-lookup"><span data-stu-id="6e710-120">Make sure the device **is not** connected to your PC via USB.</span></span>
8. <span data-ttu-id="6e710-121">Fare doppio clic su uno degli script in Unity e passare alla Visual Studio che si apre per visualizzarlo e modificarlo.</span><span class="sxs-lookup"><span data-stu-id="6e710-121">Double-click one of your scripts in Unity and go to the Visual Studio solution that opens to view and edit.</span></span>
9. <span data-ttu-id="6e710-122">Debug -> Collegare il debugger unity.</span><span class="sxs-lookup"><span data-stu-id="6e710-122">Debug -> Attach Unity Debugger.</span></span>

    ![Collega debugger Unity](images/il2cpp-debugging-attach.png)

10. <span data-ttu-id="6e710-124">Selezionare il dispositivo nell'elenco e fare clic su "OK" per collegarsi.</span><span class="sxs-lookup"><span data-stu-id="6e710-124">Select your device in the list and click "OK" to attach.</span></span>

    ![Elenco dei dispositivi](images/il2cpp-debugging-machines.png)

## <a name="see-also"></a><span data-ttu-id="6e710-126">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="6e710-126">See also</span></span> 

* [<span data-ttu-id="6e710-127">Debug C#</span><span class="sxs-lookup"><span data-stu-id="6e710-127">C# debugging</span></span>](/visualstudio/get-started/csharp/tutorial-debugger)
