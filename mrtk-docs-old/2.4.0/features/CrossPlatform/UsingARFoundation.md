---
title: UsingARFoundation
description: Documentazione per l'uso di ARFoundation in Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, AR core, AR Kit
ms.openlocfilehash: c1d1e9f51304f57e46201972fbb0c419f1f941d7
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782281"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="0f6f3-104">Come configurare MRTK per iOS e Android [sperimentale]</span><span class="sxs-lookup"><span data-stu-id="0f6f3-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="0f6f3-105">Installare i pacchetti necessari</span><span class="sxs-lookup"><span data-stu-id="0f6f3-105">Install required packages</span></span>

1. <span data-ttu-id="0f6f3-106">Scaricare e importare il pacchetto **Microsoft. MixedReality. Toolkit. Unity. Foundation** , da [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) o [NuGet](../../reference-docs/MRTKNuGetPackage.md)</span><span class="sxs-lookup"><span data-stu-id="0f6f3-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or [NuGet](../../reference-docs/MRTKNuGetPackage.md)</span></span>

1. <span data-ttu-id="0f6f3-107">In Gestione pacchetti Unity (UPM) installare i pacchetti seguenti:</span><span class="sxs-lookup"><span data-stu-id="0f6f3-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="0f6f3-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="0f6f3-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="0f6f3-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="0f6f3-109">**Android**</span></span> | <span data-ttu-id="0f6f3-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="0f6f3-110">**iOS**</span></span> | <span data-ttu-id="0f6f3-111">Commenti</span><span class="sxs-lookup"><span data-stu-id="0f6f3-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="0f6f3-112">Fondazione AR</span><span class="sxs-lookup"><span data-stu-id="0f6f3-112">AR Foundation</span></span>  <br/> <span data-ttu-id="0f6f3-113">Versione: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="0f6f3-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="0f6f3-114">Fondazione AR</span><span class="sxs-lookup"><span data-stu-id="0f6f3-114">AR Foundation</span></span>  <br/> <span data-ttu-id="0f6f3-115">Versione: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="0f6f3-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="0f6f3-116">Per Unity 2018,4, questo pacchetto è incluso come anteprima.</span><span class="sxs-lookup"><span data-stu-id="0f6f3-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="0f6f3-117">Per visualizzare il pacchetto: finestra > gestione pacchetti > avanzate > visualizzare i pacchetti di anteprima</span><span class="sxs-lookup"><span data-stu-id="0f6f3-117">To view package: Window > Package Manager > Advanced > Show Preview Packages</span></span>|
    | <span data-ttu-id="0f6f3-118">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="0f6f3-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="0f6f3-119">Versione: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="0f6f3-119">Version: 2.1.2</span></span> | <span data-ttu-id="0f6f3-120">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="0f6f3-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="0f6f3-121">Versione: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="0f6f3-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="0f6f3-122">**Unity 2019.3. x**</span><span class="sxs-lookup"><span data-stu-id="0f6f3-122">**Unity 2019.3.x**</span></span>

    | <span data-ttu-id="0f6f3-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="0f6f3-123">**Android**</span></span> | <span data-ttu-id="0f6f3-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="0f6f3-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="0f6f3-125">Fondazione AR</span><span class="sxs-lookup"><span data-stu-id="0f6f3-125">AR Foundation</span></span>  <br/> <span data-ttu-id="0f6f3-126">Versione: 2.1.4</span><span class="sxs-lookup"><span data-stu-id="0f6f3-126">Version: 2.1.4</span></span> |  <span data-ttu-id="0f6f3-127">Fondazione AR</span><span class="sxs-lookup"><span data-stu-id="0f6f3-127">AR Foundation</span></span>  <br/> <span data-ttu-id="0f6f3-128">Versione: 2.1.4</span><span class="sxs-lookup"><span data-stu-id="0f6f3-128">Version: 2.1.4</span></span> |
    | <span data-ttu-id="0f6f3-129">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="0f6f3-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="0f6f3-130">Versione: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="0f6f3-130">Version: 2.1.2</span></span> | <span data-ttu-id="0f6f3-131">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="0f6f3-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="0f6f3-132">Versione: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="0f6f3-132">Version: 2.1.2</span></span> |

## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="0f6f3-133">Abilitazione del provider di impostazioni della fotocamera AR Unity</span><span class="sxs-lookup"><span data-stu-id="0f6f3-133">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="0f6f3-134">I passaggi seguenti presuppongono l'uso dell'oggetto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="0f6f3-134">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="0f6f3-135">I passaggi necessari per altri registrar di servizi potrebbero essere diversi.</span><span class="sxs-lookup"><span data-stu-id="0f6f3-135">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="0f6f3-136">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="0f6f3-136">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Gerarchia della scena configurata MRTK](../Images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="0f6f3-138">Selezionare **copia e Personalizza** per clonare il profilo MRTK per abilitare la configurazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="0f6f3-138">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Clona profilo MRTK](../Images/CameraSystem/CloneProfileARFoundation.png)

1. <span data-ttu-id="0f6f3-140">Selezionare **Clone** accanto al profilo della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="0f6f3-140">Select **Clone** next to the Camera Profile.</span></span>

    ![Clona profilo della fotocamera MRTK](../Images/CameraSystem/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="0f6f3-142">Passare al pannello di controllo nella sezione sistema della fotocamera ed espandere la sezione **provider impostazioni fotocamera** .</span><span class="sxs-lookup"><span data-stu-id="0f6f3-142">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Espandi provider di impostazioni](../Images/CameraSystem/ExpandProviders.png)

1. <span data-ttu-id="0f6f3-144">Fare clic su **Aggiungi provider di impostazioni della fotocamera** ed espandere la nuova voce di **impostazioni della fotocamera** appena aggiunta.</span><span class="sxs-lookup"><span data-stu-id="0f6f3-144">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Espandi nuovo provider di impostazioni](../Images/CameraSystem/ExpandNewProvider.png)

1. <span data-ttu-id="0f6f3-146">Selezionare il provider di impostazioni della fotocamera AR Unity</span><span class="sxs-lookup"><span data-stu-id="0f6f3-146">Select the Unity AR Camera Settings provider</span></span>

    ![Selezionare il provider di impostazioni AR Unity](../Images/CameraSystem/SelectUnityArSettings.png)

    <span data-ttu-id="0f6f3-148">Per altre informazioni sulla configurazione del provider di impostazioni della fotocamera AR Unity: [Unity AR camera Provider Settings](../CameraSystem/UnityArCameraSettings.md).</span><span class="sxs-lookup"><span data-stu-id="0f6f3-148">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../CameraSystem/UnityArCameraSettings.md).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="0f6f3-149">Creazione di una scena per dispositivi Android e iOS</span><span class="sxs-lookup"><span data-stu-id="0f6f3-149">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="0f6f3-150">Assicurarsi di aver aggiunto il provider di impostazioni della fotocamera Unity alla scena.</span><span class="sxs-lookup"><span data-stu-id="0f6f3-150">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="0f6f3-151">Passa alla piattaforma Android o iOS nelle impostazioni di compilazione Unity</span><span class="sxs-lookup"><span data-stu-id="0f6f3-151">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

    <span data-ttu-id="0f6f3-152">Quando si passa alla piattaforma, viene visualizzata la finestra di configurazione del progetto MRTK con le impostazioni per la piattaforma scelta.</span><span class="sxs-lookup"><span data-stu-id="0f6f3-152">When you switch the platform you should see the MRTK Project Configurator Window with settings for your chosen platform.</span></span>  <span data-ttu-id="0f6f3-153">Fare clic su Applica per abilitare le impostazioni specifiche della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="0f6f3-153">Click Apply to enable platform specific settings.</span></span>

    <span data-ttu-id="0f6f3-154">Impostazioni di configurazione del progetto iOS</span><span class="sxs-lookup"><span data-stu-id="0f6f3-154">iOS Project Configurator Settings</span></span>

    ![strumento di configurazione del progetto iOS](../Images/CameraSystem/MRTKProjectConfigurator.png)

1. <span data-ttu-id="0f6f3-156">Non sono previsti passaggi aggiuntivi dopo il passaggio alla piattaforma per Android.</span><span class="sxs-lookup"><span data-stu-id="0f6f3-156">There are no additional steps after switching the platform for Android.</span></span>

1. <span data-ttu-id="0f6f3-157">Se la piattaforma è iOS, modificare > impostazioni progetto > lettore > altre impostazioni, sotto l'intestazione Ottimizzazione, **deselezionare** Rimuovi codice motore</span><span class="sxs-lookup"><span data-stu-id="0f6f3-157">If the platform is iOS, Edit > Project Settings > Player > Other Settings, under the Optimization header, **uncheck** Strip Engine Code</span></span>

    ![Impostazioni iOS](../Images/CameraSystem/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > <span data-ttu-id="0f6f3-159">Deselezionando il codice del motore di striping si tratta della soluzione a breve termine per un errore in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span><span class="sxs-lookup"><span data-stu-id="0f6f3-159">Unchecking Strip Engine Code is the short term solution to an error in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span></span>  <span data-ttu-id="0f6f3-160">Stiamo lavorando a una soluzione a lungo termine.</span><span class="sxs-lookup"><span data-stu-id="0f6f3-160">We are working on a long term solution.</span></span>

1. <span data-ttu-id="0f6f3-161">Compilare ed eseguire la scena</span><span class="sxs-lookup"><span data-stu-id="0f6f3-161">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="0f6f3-162">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="0f6f3-162">See also</span></span>

- [<span data-ttu-id="0f6f3-163">Impostazioni della fotocamera AR Unity</span><span class="sxs-lookup"><span data-stu-id="0f6f3-163">Unity AR Camera Settings</span></span>](../CameraSystem/UnityArCameraSettings.md)
