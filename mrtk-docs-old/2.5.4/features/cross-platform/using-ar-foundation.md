---
title: UsingARFoundation
description: Documentazione per l'uso di ARFoundation in Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, AR core, AR Kit
ms.openlocfilehash: 4a0e57fa3f8b00ac9867689b9c8fe49a560dbe11
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683054"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="77c62-104">Come configurare MRTK per iOS e Android [sperimentale]</span><span class="sxs-lookup"><span data-stu-id="77c62-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="77c62-105">Installare i pacchetti necessari</span><span class="sxs-lookup"><span data-stu-id="77c62-105">Install required packages</span></span>

1. <span data-ttu-id="77c62-106">Scaricare e importare il pacchetto **Microsoft. MixedReality. Toolkit. Unity. Foundation** , da [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) o da [Gestione pacchetti Unity](../../configuration/usingupm.md)</span><span class="sxs-lookup"><span data-stu-id="77c62-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="77c62-107">In Gestione pacchetti Unity (UPM) installare i pacchetti seguenti:</span><span class="sxs-lookup"><span data-stu-id="77c62-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="77c62-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="77c62-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="77c62-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="77c62-109">**Android**</span></span> | <span data-ttu-id="77c62-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="77c62-110">**iOS**</span></span> | <span data-ttu-id="77c62-111">Commenti</span><span class="sxs-lookup"><span data-stu-id="77c62-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="77c62-112">Fondazione AR</span><span class="sxs-lookup"><span data-stu-id="77c62-112">AR Foundation</span></span>  <br/> <span data-ttu-id="77c62-113">Versione: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="77c62-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="77c62-114">Fondazione AR</span><span class="sxs-lookup"><span data-stu-id="77c62-114">AR Foundation</span></span>  <br/> <span data-ttu-id="77c62-115">Versione: 1.5.0-Preview 6</span><span class="sxs-lookup"><span data-stu-id="77c62-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="77c62-116">Per Unity 2018,4, questo pacchetto è incluso come anteprima.</span><span class="sxs-lookup"><span data-stu-id="77c62-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="77c62-117">Per visualizzare il pacchetto: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="77c62-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="77c62-118">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="77c62-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="77c62-119">Versione: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="77c62-119">Version: 2.1.2</span></span> | <span data-ttu-id="77c62-120">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="77c62-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="77c62-121">Versione: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="77c62-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="77c62-122">**Unity 2019.4. x**</span><span class="sxs-lookup"><span data-stu-id="77c62-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="77c62-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="77c62-123">**Android**</span></span> | <span data-ttu-id="77c62-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="77c62-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="77c62-125">Fondazione AR</span><span class="sxs-lookup"><span data-stu-id="77c62-125">AR Foundation</span></span>  <br/> <span data-ttu-id="77c62-126">Versione: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="77c62-126">Version: 2.1.8</span></span> |  <span data-ttu-id="77c62-127">Fondazione AR</span><span class="sxs-lookup"><span data-stu-id="77c62-127">AR Foundation</span></span>  <br/> <span data-ttu-id="77c62-128">Versione: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="77c62-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="77c62-129">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="77c62-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="77c62-130">Versione: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="77c62-130">Version: 2.1.11</span></span> | <span data-ttu-id="77c62-131">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="77c62-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="77c62-132">Versione: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="77c62-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="77c62-133">**Unity 2020.1. x (attualmente non supportato formalmente, incluso solo a scopo informativo)**</span><span class="sxs-lookup"><span data-stu-id="77c62-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="77c62-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="77c62-134">**Android**</span></span> | <span data-ttu-id="77c62-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="77c62-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="77c62-136">Fondazione AR</span><span class="sxs-lookup"><span data-stu-id="77c62-136">AR Foundation</span></span>  <br/> <span data-ttu-id="77c62-137">Versione: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="77c62-137">Version: 3.1.3</span></span> |  <span data-ttu-id="77c62-138">Fondazione AR</span><span class="sxs-lookup"><span data-stu-id="77c62-138">AR Foundation</span></span>  <br/> <span data-ttu-id="77c62-139">Versione: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="77c62-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="77c62-140">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="77c62-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="77c62-141">Versione: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="77c62-141">Version: 3.1.4</span></span> | <span data-ttu-id="77c62-142">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="77c62-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="77c62-143">Versione: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="77c62-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="77c62-144">Aggiornare le definizioni di script di MRTK Unity richiamando la voce di menu: **mixed reality Toolkit > Utilities > unity > Update scripting definisce**</span><span class="sxs-lookup"><span data-stu-id="77c62-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="77c62-145">Abilitazione del provider di impostazioni della fotocamera AR Unity</span><span class="sxs-lookup"><span data-stu-id="77c62-145">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="77c62-146">I passaggi seguenti presuppongono l'uso dell'oggetto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="77c62-146">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="77c62-147">I passaggi necessari per altri registrar di servizi potrebbero essere diversi.</span><span class="sxs-lookup"><span data-stu-id="77c62-147">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="77c62-148">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="77c62-148">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="77c62-150">Selezionare **copia e Personalizza** per clonare il profilo MRTK per abilitare la configurazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="77c62-150">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Clona profilo MRTK](../images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="77c62-152">Selezionare **Clone** accanto al profilo della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="77c62-152">Select **Clone** next to the Camera Profile.</span></span>

    ![Clona profilo della fotocamera MRTK](../images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="77c62-154">Passare al pannello di controllo nella sezione sistema della fotocamera ed espandere la sezione **provider impostazioni fotocamera** .</span><span class="sxs-lookup"><span data-stu-id="77c62-154">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Espandi provider di impostazioni](../images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="77c62-156">Fare clic su **Aggiungi provider di impostazioni della fotocamera** ed espandere la nuova voce di **impostazioni della fotocamera** appena aggiunta.</span><span class="sxs-lookup"><span data-stu-id="77c62-156">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Espandi nuovo provider di impostazioni](../images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="77c62-158">Selezionare il provider di impostazioni della fotocamera AR Unity</span><span class="sxs-lookup"><span data-stu-id="77c62-158">Select the Unity AR Camera Settings provider</span></span>

    ![Selezionare il provider di impostazioni AR Unity](../images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="77c62-160">Per altre informazioni sulla configurazione del provider di impostazioni della fotocamera AR Unity: [Unity AR camera Provider Settings](../camera-system/unity-ar-camera-settings.md).</span><span class="sxs-lookup"><span data-stu-id="77c62-160">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="77c62-161">Questa installazione controlla (all'avvio dell'applicazione) se i componenti di AR Foundation si trovano nella scena.</span><span class="sxs-lookup"><span data-stu-id="77c62-161">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="77c62-162">In caso contrario, vengono aggiunti automaticamente per fare in modo che funzioni con ARCore e ARKit.</span><span class="sxs-lookup"><span data-stu-id="77c62-162">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="77c62-163">Se è necessario impostare un comportamento specifico, è necessario aggiungere i componenti necessari da soli.</span><span class="sxs-lookup"><span data-stu-id="77c62-163">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="77c62-164">Per ulteriori informazioni sui componenti e sull'installazione di AR Foundation, consultare la [documentazione](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span><span class="sxs-lookup"><span data-stu-id="77c62-164">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="77c62-165">Creazione di una scena per dispositivi Android e iOS</span><span class="sxs-lookup"><span data-stu-id="77c62-165">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="77c62-166">Assicurarsi di aver aggiunto il provider di impostazioni della fotocamera Unity alla scena.</span><span class="sxs-lookup"><span data-stu-id="77c62-166">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="77c62-167">Passa alla piattaforma Android o iOS nelle impostazioni di compilazione Unity</span><span class="sxs-lookup"><span data-stu-id="77c62-167">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

    <span data-ttu-id="77c62-168">Quando si passa alla piattaforma, viene visualizzata la finestra di configurazione del progetto MRTK con le impostazioni per la piattaforma scelta.</span><span class="sxs-lookup"><span data-stu-id="77c62-168">When you switch the platform you should see the MRTK Project Configurator Window with settings for your chosen platform.</span></span>  <span data-ttu-id="77c62-169">Fare clic su Applica per abilitare le impostazioni specifiche della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="77c62-169">Click Apply to enable platform specific settings.</span></span>

    <span data-ttu-id="77c62-170">Impostazioni di configurazione del progetto iOS</span><span class="sxs-lookup"><span data-stu-id="77c62-170">iOS Project Configurator Settings</span></span>

    ![strumento di configurazione del progetto iOS](../images/camera-system/MRTKProjectConfigurator.png)

1. <span data-ttu-id="77c62-172">Non sono previsti passaggi aggiuntivi dopo il passaggio alla piattaforma per Android.</span><span class="sxs-lookup"><span data-stu-id="77c62-172">There are no additional steps after switching the platform for Android.</span></span>

1. <span data-ttu-id="77c62-173">Se la piattaforma è iOS, modificare > impostazioni progetto > lettore > altre impostazioni, sotto l'intestazione Ottimizzazione, **deselezionare** Rimuovi codice motore</span><span class="sxs-lookup"><span data-stu-id="77c62-173">If the platform is iOS, Edit > Project Settings > Player > Other Settings, under the Optimization header, **uncheck** Strip Engine Code</span></span>

    ![Impostazioni iOS](../images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > <span data-ttu-id="77c62-175">Deselezionando il codice del motore di striping si tratta della soluzione a breve termine per un errore in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span><span class="sxs-lookup"><span data-stu-id="77c62-175">Unchecking Strip Engine Code is the short term solution to an error in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span></span>  <span data-ttu-id="77c62-176">Stiamo lavorando a una soluzione a lungo termine.</span><span class="sxs-lookup"><span data-stu-id="77c62-176">We are working on a long term solution.</span></span>

1. <span data-ttu-id="77c62-177">Compilare ed eseguire la scena</span><span class="sxs-lookup"><span data-stu-id="77c62-177">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="77c62-178">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="77c62-178">See also</span></span>

- [<span data-ttu-id="77c62-179">Impostazioni della fotocamera AR Unity</span><span class="sxs-lookup"><span data-stu-id="77c62-179">Unity AR Camera Settings</span></span>](../camera-system/unity-ar-camera-settings.md)
