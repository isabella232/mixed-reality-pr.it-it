---
title: Introduzione alle esercitazioni su Ancoraggi nello spazio di Azure
description: In questo corso viene illustrato come implementare Ancoraggi nello spazio di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure, ios, android, Windows 10, ARCore, macOS, Android Build Support, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 613aa50e1cfaadcf245b719d5a846f35e9e6159e
ms.sourcegitcommit: 7a8fa3257a13635ddad77d963e49440f62c19774
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2021
ms.locfileid: "101883366"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a><span data-ttu-id="d50c6-104">1. Introduzione alle esercitazioni su Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="d50c6-104">1. Introduction to the Azure Spatial Anchors tutorials</span></span>

<span data-ttu-id="d50c6-105">Esercitazioni su Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="d50c6-105">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="d50c6-106">Con questa serie di esercitazioni si apprenderanno le nozioni di base di <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a> (ASA) e le procedure per ancorare un'esperienza di realtà mista completa al mondo reale.</span><span class="sxs-lookup"><span data-stu-id="d50c6-106">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="d50c6-107">Si apprenderà anche come distribuire il progetto in Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="d50c6-107">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="d50c6-108">Esercitazioni di questa serie:</span><span class="sxs-lookup"><span data-stu-id="d50c6-108">Tutorials in this series:</span></span>

1. <span data-ttu-id="d50c6-109">[Introduzione](mr-learning-asa-01.md) (l'esercitazione corrente)</span><span class="sxs-lookup"><span data-stu-id="d50c6-109">[Introduction](mr-learning-asa-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="d50c6-110">Introduzione ad Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="d50c6-110">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="d50c6-111">Salvataggio, recupero e condivisione di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="d50c6-111">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="d50c6-112">Visualizzazione del feedback su Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="d50c6-112">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="d50c6-113">Ancoraggi nello spazio di Azure per Android e iOS</span><span class="sxs-lookup"><span data-stu-id="d50c6-113">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="d50c6-114">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="d50c6-114">Objectives</span></span>

* <span data-ttu-id="d50c6-115">Imparare a creare ancoraggi nello spazio e recuperarli da Azure</span><span class="sxs-lookup"><span data-stu-id="d50c6-115">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="d50c6-116">Imparare a ottenere l'allineamento spaziale tra le sessioni dell'app</span><span class="sxs-lookup"><span data-stu-id="d50c6-116">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="d50c6-117">Imparare a ottenere l'allineamento spaziale tra più dispositivi</span><span class="sxs-lookup"><span data-stu-id="d50c6-117">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="d50c6-118">Imparare a preparare, creare e distribuire il progetto in Android e iOS</span><span class="sxs-lookup"><span data-stu-id="d50c6-118">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d50c6-119">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="d50c6-119">Prerequisites</span></span>

* <span data-ttu-id="d50c6-120">Un computer Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="d50c6-120">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="d50c6-121">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="d50c6-121">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="d50c6-122">Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="d50c6-122">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="d50c6-123"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019 LTS installato e il modulo di supporto per la compilazione UWP (Universal Windows Platform) aggiunto</span><span class="sxs-lookup"><span data-stu-id="d50c6-123"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="d50c6-124">Completamento della sezione [Creare una risorsa di Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) dell'esercitazione [Avvio rapido: Creare un'app HoloLens in Unity che usa Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="d50c6-124">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="d50c6-125">Completamento della serie di [esercitazioni introduttive](mr-learning-base-01.md) o di esperienze di base precedenti con Unity e MRTK</span><span class="sxs-lookup"><span data-stu-id="d50c6-125">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="d50c6-126">Se è prevista la distribuzione in Android e HoloLens</span><span class="sxs-lookup"><span data-stu-id="d50c6-126">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="d50c6-127">Un dispositivo Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">con le opzioni di sviluppo abilitate</a> e <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">supportato da ARCore</a> con connessione USB a un computer con Windows o macOS</span><span class="sxs-lookup"><span data-stu-id="d50c6-127">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="d50c6-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub Unity</a> con unity 2019 LTS installato e aggiunta del modulo di supporto Build Android</span><span class="sxs-lookup"><span data-stu-id="d50c6-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Android Build Support module added</span></span>
* <span data-ttu-id="d50c6-129">Se è prevista la distribuzione in iOS e HoloLens</span><span class="sxs-lookup"><span data-stu-id="d50c6-129">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="d50c6-130">Un computer macOS con la versione più recente di <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> e <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installata</span><span class="sxs-lookup"><span data-stu-id="d50c6-130">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="d50c6-131">Un dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatibile con ARKit</a> con connessione USB al computer macOS</span><span class="sxs-lookup"><span data-stu-id="d50c6-131">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="d50c6-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub Unity</a> con unity 2019 LTS installato e il modulo di supporto Build iOS aggiunto</span><span class="sxs-lookup"><span data-stu-id="d50c6-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="d50c6-133">La versione consigliata del Toolkit per la realtà mista per questa serie di esercitazioni è MRTK 2,6.</span><span class="sxs-lookup"><span data-stu-id="d50c6-133">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.6.</span></span>

> [!CAUTION]
> <span data-ttu-id="d50c6-134">La versione consigliata di Unity per questa serie di esercitazioni è Unity 2019 LTS, che sostituisce tutti i requisiti di versione di Unity indicati nei prerequisiti collegati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="d50c6-134">The recommended Unity version for this tutorial series is Unity 2019 LTS This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d50c6-135">Esercitazione successiva: 2. Introduzione ad Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="d50c6-135">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
