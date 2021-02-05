---
title: Introduzione alle esercitazioni sulle funzionalità multiutente
description: In questo corso viene illustrato come implementare esperienze multiutente condivise in un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, funzionalità multiutente, Photon, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure
ms.localizationpriority: high
ms.openlocfilehash: 7f9164540b6d887dcb43bfd6bfa2cc074ee05ce2
ms.sourcegitcommit: d9f87635c87627adba7db37834e4627c149f9a28
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/05/2021
ms.locfileid: "99570224"
---
# <a name="1-introduction-to-the-multi-user-capabilities-tutorials"></a><span data-ttu-id="ab618-104">1. Introduzione alle esercitazioni sulle funzionalità multiutente</span><span class="sxs-lookup"><span data-stu-id="ab618-104">1. Introduction to the Multi-user capabilities tutorials</span></span>

<span data-ttu-id="ab618-105">Esercitazioni sulle funzionalità multiutente</span><span class="sxs-lookup"><span data-stu-id="ab618-105">Welcome to the Multi-User Capabilities tutorials!</span></span> <span data-ttu-id="ab618-106">Con questa serie di esercitazioni si apprenderanno le nozioni di base per la creazione di un'esperienza multiutente usando <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span><span class="sxs-lookup"><span data-stu-id="ab618-106">Through this tutorial series, you will learn the fundamentals of building a multi-user experience using <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span></span> <span data-ttu-id="ab618-107">PUN è una delle diverse opzioni di rete disponibili per gli sviluppatori di realtà mista per creare esperienze condivise.</span><span class="sxs-lookup"><span data-stu-id="ab618-107">PUN is one of several networking options available to mixed reality developers to create shared experiences.</span></span>

<span data-ttu-id="ab618-108">Esercitazioni di questa serie:</span><span class="sxs-lookup"><span data-stu-id="ab618-108">Tutorials in this series:</span></span>

* [<span data-ttu-id="ab618-109">Configurazione di Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="ab618-109">Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
* [<span data-ttu-id="ab618-110">Connessione di più utenti</span><span class="sxs-lookup"><span data-stu-id="ab618-110">Connecting multiple users</span></span>](mr-learning-sharing-03.md)
* [<span data-ttu-id="ab618-111">Condivisione dei movimenti di oggetti con più utenti</span><span class="sxs-lookup"><span data-stu-id="ab618-111">Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
* [<span data-ttu-id="ab618-112">Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa</span><span class="sxs-lookup"><span data-stu-id="ab618-112">Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)

## <a name="objectives"></a><span data-ttu-id="ab618-113">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="ab618-113">Objectives</span></span>

* <span data-ttu-id="ab618-114">Imparare a creare un'app PUN e a connettere il progetto Unity all'app</span><span class="sxs-lookup"><span data-stu-id="ab618-114">Learn how to create a PUN app and connect your Unity project to it</span></span>
* <span data-ttu-id="ab618-115">Imparare a connettere più utenti in un'esperienza condivisa</span><span class="sxs-lookup"><span data-stu-id="ab618-115">Learn how to connect multiple users in a shared experience</span></span>
* <span data-ttu-id="ab618-116">Imparare a condividere i movimenti degli oggetti con altri utenti</span><span class="sxs-lookup"><span data-stu-id="ab618-116">Learn how to share the object movements with other users</span></span>
* <span data-ttu-id="ab618-117">Imparare a ottenere l'allineamento spaziale tra più dispositivi</span><span class="sxs-lookup"><span data-stu-id="ab618-117">Learn how to achieve spatial alignment between multiple devices</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ab618-118">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="ab618-118">Prerequisites</span></span>

* <span data-ttu-id="ab618-119">Un computer Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="ab618-119">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="ab618-120">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="ab618-120">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="ab618-121">Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="ab618-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="ab618-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019 LTS installato e il modulo di supporto per la compilazione UWP (Universal Windows Platform) aggiunto</span><span class="sxs-lookup"><span data-stu-id="ab618-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="ab618-123">Completamento della sezione [Creare una risorsa di Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) dell'esercitazione [Avvio rapido: Creare un'app HoloLens in Unity che usa Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="ab618-123">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="ab618-124">Completamento della serie di [esercitazioni introduttive](mr-learning-base-01.md) o di esperienze di base precedenti con Unity e MRTK</span><span class="sxs-lookup"><span data-stu-id="ab618-124">Completed the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="ab618-125">Completamento della serie di [esercitazioni sugli Ancoraggi nello spazio di Azure](mr-learning-asa-01.md) o di esperienze precedenti sulla creazione di un account di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="ab618-125">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or prior experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="ab618-126">Se è prevista la distribuzione in Android e HoloLens</span><span class="sxs-lookup"><span data-stu-id="ab618-126">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="ab618-127">Un dispositivo Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">con le opzioni di sviluppo abilitate</a> e <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">supportato da ARCore</a> con connessione USB a un computer con Windows o macOS</span><span class="sxs-lookup"><span data-stu-id="ab618-127">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="ab618-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub Unity</a> con unity 2019 LTS installato e aggiunta del modulo di supporto Build Android</span><span class="sxs-lookup"><span data-stu-id="ab618-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Android Build Support module added</span></span>
* <span data-ttu-id="ab618-129">Se è prevista la distribuzione in iOS e HoloLens</span><span class="sxs-lookup"><span data-stu-id="ab618-129">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="ab618-130">Un computer macOS con la versione più recente di <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> e <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installata</span><span class="sxs-lookup"><span data-stu-id="ab618-130">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="ab618-131">Un dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatibile con ARKit</a> con connessione USB al computer macOS</span><span class="sxs-lookup"><span data-stu-id="ab618-131">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="ab618-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub Unity</a> con unity 2019 LTS installato e il modulo di supporto Build iOS aggiunto</span><span class="sxs-lookup"><span data-stu-id="ab618-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="ab618-133">La versione consigliata del Toolkit per la realtà mista per questa serie di esercitazioni è MRTK 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="ab618-133">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.5.3.</span></span>

> [!CAUTION]
> <span data-ttu-id="ab618-134">La versione consigliata di Unity per questa serie di esercitazioni è Unity 2019 LTS, che sostituisce tutti i requisiti di versione di Unity indicati nei prerequisiti collegati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="ab618-134">The recommended Unity version for this tutorial series is Unity 2019 LTS This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ab618-135">Esercitazione successiva: 2. Configurazione di Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="ab618-135">Next Tutorial: 2. Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
