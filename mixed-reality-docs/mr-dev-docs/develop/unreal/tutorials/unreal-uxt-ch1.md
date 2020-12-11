---
title: 1. Guida introduttiva
description: Parte 1 di 6 in una serie di esercitazioni per la creazione di un'app per gli scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 465215efd953c0acb9f2d80a2905ee06963c5f8c
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609722"
---
# <a name="1-getting-started"></a><span data-ttu-id="68f33-104">1. Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="68f33-104">1. Getting started</span></span>

<span data-ttu-id="68f33-105">Indipendentemente dal fatto che l'utente sia alle prime armi o un professionista esperto nell'ambito della realtà mista, questo è il punto di partenza ideale per esplorare [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) e [Unreal Engine](https://www.unrealengine.com/en-US/).</span><span class="sxs-lookup"><span data-stu-id="68f33-105">Whether you're new to mixed reality or a seasoned pro, you're in the right place to start your [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) and [Unreal Engine](https://www.unrealengine.com/en-US/) journey.</span></span> <span data-ttu-id="68f33-106">Questa serie di esercitazioni offre una guida dettagliata su come creare un'app di scacchi interattiva con il [plug-in UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal), che fa parte di [Mixed Reality Toolkit per Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span><span class="sxs-lookup"><span data-stu-id="68f33-106">This tutorial series will give you a step-by-step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="68f33-107">Con il plug-in potrai aggiungere comuni funzionalità UX ai tuoi progetti con codice, progetti ed esempi.</span><span class="sxs-lookup"><span data-stu-id="68f33-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![Schermata finale in viewport](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="68f33-109">Alla fine della serie, l'utente avrà acquisito esperienza pratica su:</span><span class="sxs-lookup"><span data-stu-id="68f33-109">By the end of the series you'll have experience with:</span></span>
* <span data-ttu-id="68f33-110">Avvio di un nuovo progetto</span><span class="sxs-lookup"><span data-stu-id="68f33-110">Starting a new project</span></span>
* <span data-ttu-id="68f33-111">Configurazione per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="68f33-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="68f33-112">Gestione dell'input utente</span><span class="sxs-lookup"><span data-stu-id="68f33-112">Working with user input</span></span>
* <span data-ttu-id="68f33-113">Aggiunta di pulsanti</span><span class="sxs-lookup"><span data-stu-id="68f33-113">Adding buttons</span></span>
* <span data-ttu-id="68f33-114">Riproduzione su un emulatore o dispositivo</span><span class="sxs-lookup"><span data-stu-id="68f33-114">Playing on an emulator or device</span></span>

## <a name="prerequisites"></a><span data-ttu-id="68f33-115">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="68f33-115">Prerequisites</span></span>

<span data-ttu-id="68f33-116">Prima di iniziare, è importante verificare che siano installati gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="68f33-116">Make sure you've installed the following before jumping in:</span></span>
* <span data-ttu-id="68f33-117">Windows 10 1809 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="68f33-117">Windows 10 1809 or later</span></span>
* <span data-ttu-id="68f33-118">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="68f33-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="68f33-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="68f33-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="68f33-120">Dispositivo Microsoft HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) o emulatore</span><span class="sxs-lookup"><span data-stu-id="68f33-120">Microsoft HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="68f33-121">Visual Studio 2019 con i carichi di lavoro seguenti</span><span class="sxs-lookup"><span data-stu-id="68f33-121">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="68f33-122">Installazione di Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="68f33-122">Installing Visual Studio 2019</span></span>

<span data-ttu-id="68f33-123">Assicurarsi, innanzitutto, che la configurazione venga eseguita con tutti i pacchetti di Visual Studio necessari:</span><span class="sxs-lookup"><span data-stu-id="68f33-123">First, make sure your setup with all the required Visual Studio packages:</span></span>
1. <span data-ttu-id="68f33-124">Installa la versione più recente di [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span><span class="sxs-lookup"><span data-stu-id="68f33-124">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
2. <span data-ttu-id="68f33-125">Installa i [carichi di lavoro](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads) seguenti:</span><span class="sxs-lookup"><span data-stu-id="68f33-125">Install the following [workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads):</span></span>
    * <span data-ttu-id="68f33-126">Sviluppo per desktop con C++</span><span class="sxs-lookup"><span data-stu-id="68f33-126">Desktop development with C++</span></span>
    * <span data-ttu-id="68f33-127">Sviluppo per desktop .NET</span><span class="sxs-lookup"><span data-stu-id="68f33-127">.NET desktop development</span></span>
    * <span data-ttu-id="68f33-128">Sviluppo per la piattaforma UWP</span><span class="sxs-lookup"><span data-stu-id="68f33-128">Universal Windows Platform development</span></span>

3. <span data-ttu-id="68f33-129">Installa i [componenti](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components) seguenti:</span><span class="sxs-lookup"><span data-stu-id="68f33-129">Install the following [components](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components):</span></span>
    * <span data-ttu-id="68f33-130">Compilatori, strumenti di compilazione e runtime > MSVC versione 142 - VS 2019 C++ ARM64 Build Tools (versione più recente)</span><span class="sxs-lookup"><span data-stu-id="68f33-130">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="68f33-131">Ecco fatto!</span><span class="sxs-lookup"><span data-stu-id="68f33-131">That's it!</span></span> <span data-ttu-id="68f33-132">Ora è tutto pronto per iniziare il progetto degli scacchi.</span><span class="sxs-lookup"><span data-stu-id="68f33-132">You're all set to move on to starting the chess project.</span></span>

[<span data-ttu-id="68f33-133">Sezione successiva: 2. Inizializzazione del progetto e prima applicazione</span><span class="sxs-lookup"><span data-stu-id="68f33-133">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)