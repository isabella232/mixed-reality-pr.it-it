---
title: Introduzione alle esercitazioni di MRTK
description: Questo corso illustra come usare Mixed Reality Toolkit (MRTK) per creare un'applicazione di realtà mista da zero.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, risolutori, tracciamento oculare, comandi vocali
ms.localizationpriority: high
ms.openlocfilehash: 0af75341aa1c90f38ac679dd1ff2db6ab2796839
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403342"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a><span data-ttu-id="b1a2a-104">1. Introduzione alle esercitazioni di MRTK</span><span class="sxs-lookup"><span data-stu-id="b1a2a-104">1. Introduction to the MRTK tutorials</span></span>

<span data-ttu-id="b1a2a-105">Serie di esercitazioni introduttive</span><span class="sxs-lookup"><span data-stu-id="b1a2a-105">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="b1a2a-106">Nel corso di queste esercitazioni, verranno fornite informazioni su Mixed Reality Toolkit (MRTK) e alcune delle funzionalità che offre.</span><span class="sxs-lookup"><span data-stu-id="b1a2a-106">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="b1a2a-107">Sarà anche possibile creare un'esperienza di realtà mista in cui l'utente può esplorare un ologramma modellato in base a Mars Curiosity Rover della NASA.</span><span class="sxs-lookup"><span data-stu-id="b1a2a-107">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="b1a2a-108">Al termine di questa serie, si disporrà di una solida conoscenza di MRTK e dell'utilizzo di questo strumento per accelerare il processo di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="b1a2a-108">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="b1a2a-109">Le esercitazioni di questa serie sono sequenziali, consultarle quindi nell'ordine corretto:</span><span class="sxs-lookup"><span data-stu-id="b1a2a-109">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. <span data-ttu-id="b1a2a-110">[Introduzione](mr-learning-base-01.md) (l'esercitazione corrente)</span><span class="sxs-lookup"><span data-stu-id="b1a2a-110">[Introduction](mr-learning-base-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="b1a2a-111">Inizializzazione del progetto e distribuzione della prima applicazione</span><span class="sxs-lookup"><span data-stu-id="b1a2a-111">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="b1a2a-112">Configurazione dei profili di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="b1a2a-112">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="b1a2a-113">Posizionamento degli oggetti nella scena</span><span class="sxs-lookup"><span data-stu-id="b1a2a-113">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="b1a2a-114">Creazione di contenuto dinamico tramite risolutori</span><span class="sxs-lookup"><span data-stu-id="b1a2a-114">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="b1a2a-115">Creazione delle interfacce utente</span><span class="sxs-lookup"><span data-stu-id="b1a2a-115">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="b1a2a-116">Interazione con oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="b1a2a-116">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="b1a2a-117">Uso del tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="b1a2a-117">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="b1a2a-118">Uso dei comandi vocali</span><span class="sxs-lookup"><span data-stu-id="b1a2a-118">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="b1a2a-119">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="b1a2a-119">Objectives</span></span>

* <span data-ttu-id="b1a2a-120">Imparare a configurare Unity per MRTK</span><span class="sxs-lookup"><span data-stu-id="b1a2a-120">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="b1a2a-121">Imparare a compilare e distribuire nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="b1a2a-121">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="b1a2a-122">Imparare a usare alcune delle funzionalità chiave di MRTK</span><span class="sxs-lookup"><span data-stu-id="b1a2a-122">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="b1a2a-123">Creare un'esperienza di realtà mista completa</span><span class="sxs-lookup"><span data-stu-id="b1a2a-123">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b1a2a-124">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="b1a2a-124">Prerequisites</span></span>

* <span data-ttu-id="b1a2a-125">Un PC Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="b1a2a-125">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="b1a2a-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="b1a2a-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="b1a2a-127">Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="b1a2a-127">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>

* <span data-ttu-id="b1a2a-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020 LTS (attualmente 2020.3.x) o Unity 2019 LTS (attualmente 2019.4.x) installato e il modulo piattaforma UWP (Universal Windows Platform) Build Support aggiunto</span><span class="sxs-lookup"><span data-stu-id="b1a2a-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020 LTS(currently 2020.3.x) or Unity 2019 LTS (currently 2019.4.x)  installed and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="b1a2a-129">Quando si installa Unity, assicurarsi di controllare i componenti seguenti in **"Piattaforme".**</span><span class="sxs-lookup"><span data-stu-id="b1a2a-129">When installing Unity, please make sure to check following components under **'Platforms'**.</span></span>

* <span data-ttu-id="b1a2a-130">**piattaforma UWP (Universal Windows Platform) di compilazione**</span><span class="sxs-lookup"><span data-stu-id="b1a2a-130">**Universal Windows Platform Build Support**</span></span>
* <span data-ttu-id="b1a2a-131">**Supporto per la compilazione di Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="b1a2a-131">**Windows Build Support (IL2CPP)**</span></span>

![Opzione supporto piattaforma UWP (Universal Windows Platform) compilazione di Unity](../../../develop/images/Unity_Install_Option_UWP.png)

<span data-ttu-id="b1a2a-133">Se Unity è stato installato senza queste opzioni, è possibile aggiungerlo tramite il menu **"Aggiungi moduli"** in Unity Hub.</span><span class="sxs-lookup"><span data-stu-id="b1a2a-133">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub.</span></span>

![Opzione Unity Windows Build Support (Supporto per la compilazione di Windows in Unity)](../../../develop/images/Unity_Install_Option_UWP2.png)

> [!Important]
> <span data-ttu-id="b1a2a-135">La versione consigliata di MRTK per questa serie di esercitazioni è MRTK 2.7.</span><span class="sxs-lookup"><span data-stu-id="b1a2a-135">The recommended MRTK version for this tutorial series is MRTK 2.7.</span></span>

> [!Important]
> <span data-ttu-id="b1a2a-136">Questa serie di esercitazioni supporta Unity 2020 LTS (attualmente 2020.3.x) se si usa Open XR o Windows XR Plugin e anche Unity 2019 LTS (attualmente 2019.4.x) se si usa WSA legacy o Windows XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="b1a2a-136">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="b1a2a-137">Questa istruzione sostituisce gli eventuali requisiti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="b1a2a-137">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b1a2a-138">Esercitazione successiva: 2. Inizializzazione del progetto e distribuzione della prima applicazione</span><span class="sxs-lookup"><span data-stu-id="b1a2a-138">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
