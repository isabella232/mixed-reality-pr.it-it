---
title: UsingARFoundation
description: Documentazione per l'uso di ARFoundation in Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, AR core, AR Kit
ms.openlocfilehash: a4f3df71d0d1b5abf3f2f70bb01daebe08c740ee
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782698"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="23679-104">Come configurare MRTK per iOS e Android [sperimentale]</span><span class="sxs-lookup"><span data-stu-id="23679-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="23679-105">Installare i pacchetti necessari</span><span class="sxs-lookup"><span data-stu-id="23679-105">Install required packages</span></span>

1. <span data-ttu-id="23679-106">Scaricare e importare il pacchetto **Microsoft. MixedReality. Toolkit. Unity. Foundation** , da [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) o da [Gestione pacchetti Unity](../../configuration/usingupm.md)</span><span class="sxs-lookup"><span data-stu-id="23679-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="23679-107">In Gestione pacchetti Unity (UPM) installare i pacchetti seguenti:</span><span class="sxs-lookup"><span data-stu-id="23679-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="23679-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="23679-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="23679-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="23679-109">**Android**</span></span> | <span data-ttu-id="23679-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="23679-110">**iOS**</span></span> | <span data-ttu-id="23679-111">Commenti</span><span class="sxs-lookup"><span data-stu-id="23679-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="23679-112">Fondazione AR</span><span class="sxs-lookup"><span data-stu-id="23679-112">AR Foundation</span></span>  <br/> <span data-ttu-id="23679-113">Versione: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="23679-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="23679-114">Fondazione AR</span><span class="sxs-lookup"><span data-stu-id="23679-114">AR Foundation</span></span>  <br/> <span data-ttu-id="23679-115">Versione: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="23679-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="23679-116">Per Unity 2018,4, questo pacchetto è incluso come anteprima.</span><span class="sxs-lookup"><span data-stu-id="23679-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="23679-117">Per visualizzare il pacchetto: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="23679-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="23679-118">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="23679-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="23679-119">Versione: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="23679-119">Version: 2.1.2</span></span> | <span data-ttu-id="23679-120">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="23679-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="23679-121">Versione: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="23679-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="23679-122">**Unity 2019.4. x**</span><span class="sxs-lookup"><span data-stu-id="23679-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="23679-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="23679-123">**Android**</span></span> | <span data-ttu-id="23679-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="23679-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="23679-125">Fondazione AR</span><span class="sxs-lookup"><span data-stu-id="23679-125">AR Foundation</span></span>  <br/> <span data-ttu-id="23679-126">Versione: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="23679-126">Version: 2.1.8</span></span> |  <span data-ttu-id="23679-127">Fondazione AR</span><span class="sxs-lookup"><span data-stu-id="23679-127">AR Foundation</span></span>  <br/> <span data-ttu-id="23679-128">Versione: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="23679-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="23679-129">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="23679-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="23679-130">Versione: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="23679-130">Version: 2.1.11</span></span> | <span data-ttu-id="23679-131">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="23679-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="23679-132">Versione: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="23679-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="23679-133">**Unity 2020.1. x (attualmente non supportato formalmente, incluso solo a scopo informativo)**</span><span class="sxs-lookup"><span data-stu-id="23679-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="23679-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="23679-134">**Android**</span></span> | <span data-ttu-id="23679-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="23679-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="23679-136">Fondazione AR</span><span class="sxs-lookup"><span data-stu-id="23679-136">AR Foundation</span></span>  <br/> <span data-ttu-id="23679-137">Versione: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="23679-137">Version: 3.1.3</span></span> |  <span data-ttu-id="23679-138">Fondazione AR</span><span class="sxs-lookup"><span data-stu-id="23679-138">AR Foundation</span></span>  <br/> <span data-ttu-id="23679-139">Versione: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="23679-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="23679-140">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="23679-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="23679-141">Versione: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="23679-141">Version: 3.1.4</span></span> | <span data-ttu-id="23679-142">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="23679-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="23679-143">Versione: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="23679-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="23679-144">Aggiornare le definizioni di script di MRTK Unity richiamando la voce di menu: **mixed reality Toolkit > Utilities > unity > Update scripting definisce**</span><span class="sxs-lookup"><span data-stu-id="23679-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="23679-145">Abilitazione del provider di impostazioni della fotocamera AR Unity</span><span class="sxs-lookup"><span data-stu-id="23679-145">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="23679-146">I passaggi seguenti presuppongono l'uso dell'oggetto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="23679-146">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="23679-147">I passaggi necessari per altri registrar di servizi potrebbero essere diversi.</span><span class="sxs-lookup"><span data-stu-id="23679-147">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="23679-148">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="23679-148">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Gerarchia della scena configurata MRTK](../Images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="23679-150">Selezionare **copia e Personalizza** per clonare il profilo MRTK per abilitare la configurazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="23679-150">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Clona profilo MRTK](../Images/CameraSystem/CloneProfileARFoundation.png)

1. <span data-ttu-id="23679-152">Selezionare **Clone** accanto al profilo della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="23679-152">Select **Clone** next to the Camera Profile.</span></span>

    ![Clona profilo della fotocamera MRTK](../Images/CameraSystem/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="23679-154">Passare al pannello di controllo nella sezione sistema della fotocamera ed espandere la sezione **provider impostazioni fotocamera** .</span><span class="sxs-lookup"><span data-stu-id="23679-154">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Espandi provider di impostazioni](../Images/CameraSystem/ExpandProviders.png)

1. <span data-ttu-id="23679-156">Fare clic su **Aggiungi provider di impostazioni della fotocamera** ed espandere la nuova voce di **impostazioni della fotocamera** appena aggiunta.</span><span class="sxs-lookup"><span data-stu-id="23679-156">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Espandi nuovo provider di impostazioni](../Images/CameraSystem/ExpandNewProvider.png)

1. <span data-ttu-id="23679-158">Selezionare il provider di impostazioni della fotocamera AR Unity</span><span class="sxs-lookup"><span data-stu-id="23679-158">Select the Unity AR Camera Settings provider</span></span>

    ![Selezionare il provider di impostazioni AR Unity](../Images/CameraSystem/SelectUnityArSettings.png)

    <span data-ttu-id="23679-160">Per altre informazioni sulla configurazione del provider di impostazioni della fotocamera AR Unity: [Unity AR camera Provider Settings](../CameraSystem/UnityArCameraSettings.md).</span><span class="sxs-lookup"><span data-stu-id="23679-160">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../CameraSystem/UnityArCameraSettings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="23679-161">Questa installazione controlla (all'avvio dell'applicazione) se i componenti di AR Foundation si trovano nella scena.</span><span class="sxs-lookup"><span data-stu-id="23679-161">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="23679-162">In caso contrario, vengono aggiunti automaticamente per fare in modo che funzioni con ARCore e ARKit.</span><span class="sxs-lookup"><span data-stu-id="23679-162">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="23679-163">Se è necessario impostare un comportamento specifico, è necessario aggiungere i componenti necessari da soli.</span><span class="sxs-lookup"><span data-stu-id="23679-163">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="23679-164">Per ulteriori informazioni sui componenti e sull'installazione di AR Foundation, consultare la [documentazione](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span><span class="sxs-lookup"><span data-stu-id="23679-164">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="23679-165">Creazione di una scena per dispositivi Android e iOS</span><span class="sxs-lookup"><span data-stu-id="23679-165">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="23679-166">Assicurarsi di aver aggiunto il provider di impostazioni della fotocamera Unity alla scena.</span><span class="sxs-lookup"><span data-stu-id="23679-166">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="23679-167">Passa alla piattaforma Android o iOS nelle impostazioni di compilazione Unity</span><span class="sxs-lookup"><span data-stu-id="23679-167">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

    <span data-ttu-id="23679-168">Quando si passa alla piattaforma, viene visualizzata la finestra di configurazione del progetto MRTK con le impostazioni per la piattaforma scelta.</span><span class="sxs-lookup"><span data-stu-id="23679-168">When you switch the platform you should see the MRTK Project Configurator Window with settings for your chosen platform.</span></span>  <span data-ttu-id="23679-169">Fare clic su Applica per abilitare le impostazioni specifiche della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="23679-169">Click Apply to enable platform specific settings.</span></span>

    <span data-ttu-id="23679-170">Impostazioni di configurazione del progetto iOS</span><span class="sxs-lookup"><span data-stu-id="23679-170">iOS Project Configurator Settings</span></span>

    ![strumento di configurazione del progetto iOS](../Images/CameraSystem/MRTKProjectConfigurator.png)

1. <span data-ttu-id="23679-172">Non sono previsti passaggi aggiuntivi dopo il passaggio alla piattaforma per Android.</span><span class="sxs-lookup"><span data-stu-id="23679-172">There are no additional steps after switching the platform for Android.</span></span>

1. <span data-ttu-id="23679-173">Se la piattaforma è iOS, modificare > impostazioni progetto > lettore > altre impostazioni, sotto l'intestazione Ottimizzazione, **deselezionare** Rimuovi codice motore</span><span class="sxs-lookup"><span data-stu-id="23679-173">If the platform is iOS, Edit > Project Settings > Player > Other Settings, under the Optimization header, **uncheck** Strip Engine Code</span></span>

    ![Impostazioni iOS](../Images/CameraSystem/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > <span data-ttu-id="23679-175">Deselezionando il codice del motore di striping si tratta della soluzione a breve termine per un errore in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span><span class="sxs-lookup"><span data-stu-id="23679-175">Unchecking Strip Engine Code is the short term solution to an error in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span></span>  <span data-ttu-id="23679-176">Stiamo lavorando a una soluzione a lungo termine.</span><span class="sxs-lookup"><span data-stu-id="23679-176">We are working on a long term solution.</span></span>

1. <span data-ttu-id="23679-177">Compilare ed eseguire la scena</span><span class="sxs-lookup"><span data-stu-id="23679-177">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="23679-178">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="23679-178">See also</span></span>

- [<span data-ttu-id="23679-179">Impostazioni della fotocamera AR Unity</span><span class="sxs-lookup"><span data-stu-id="23679-179">Unity AR Camera Settings</span></span>](../CameraSystem/UnityArCameraSettings.md)
