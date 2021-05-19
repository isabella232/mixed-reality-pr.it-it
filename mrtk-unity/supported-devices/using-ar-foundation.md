---
title: Uso di AR Foundation
description: Documentazione per l'uso di ARFoundation in Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, AR Core, AR Kit
ms.openlocfilehash: 1c39950e8b64968e182ddc551ef344dee42060e9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143939"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="d1c7a-104">Come configurare MRTK per iOS e Android [sperimentale]</span><span class="sxs-lookup"><span data-stu-id="d1c7a-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="d1c7a-105">Installare i pacchetti necessari</span><span class="sxs-lookup"><span data-stu-id="d1c7a-105">Install required packages</span></span>

1. <span data-ttu-id="d1c7a-106">Scaricare e importare **il pacchetto Microsoft.MixedReality.Toolkit.Unity.Foundation** da [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) o [dal](../configuration/usingupm.md) Gestione pacchetti</span><span class="sxs-lookup"><span data-stu-id="d1c7a-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="d1c7a-107">In Unity Gestione pacchetti (UPM) installare i pacchetti seguenti:</span><span class="sxs-lookup"><span data-stu-id="d1c7a-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="d1c7a-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="d1c7a-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="d1c7a-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="d1c7a-109">**Android**</span></span> | <span data-ttu-id="d1c7a-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="d1c7a-110">**iOS**</span></span> | <span data-ttu-id="d1c7a-111">Commenti</span><span class="sxs-lookup"><span data-stu-id="d1c7a-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="d1c7a-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="d1c7a-112">AR Foundation</span></span>  <br/> <span data-ttu-id="d1c7a-113">Versione: 1.5.0 - anteprima 6</span><span class="sxs-lookup"><span data-stu-id="d1c7a-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="d1c7a-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="d1c7a-114">AR Foundation</span></span>  <br/> <span data-ttu-id="d1c7a-115">Versione: 1.5.0 - anteprima 6</span><span class="sxs-lookup"><span data-stu-id="d1c7a-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="d1c7a-116">Per Unity 2018.4, questo pacchetto è incluso come anteprima.</span><span class="sxs-lookup"><span data-stu-id="d1c7a-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="d1c7a-117">Per visualizzare il pacchetto: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="d1c7a-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="d1c7a-118">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="d1c7a-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="d1c7a-119">Versione: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="d1c7a-119">Version: 2.1.2</span></span> | <span data-ttu-id="d1c7a-120">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="d1c7a-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="d1c7a-121">Versione: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="d1c7a-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="d1c7a-122">**Unity 2019.4.x**</span><span class="sxs-lookup"><span data-stu-id="d1c7a-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="d1c7a-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="d1c7a-123">**Android**</span></span> | <span data-ttu-id="d1c7a-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="d1c7a-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="d1c7a-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="d1c7a-125">AR Foundation</span></span>  <br/> <span data-ttu-id="d1c7a-126">Versione: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="d1c7a-126">Version: 2.1.8</span></span> |  <span data-ttu-id="d1c7a-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="d1c7a-127">AR Foundation</span></span>  <br/> <span data-ttu-id="d1c7a-128">Versione: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="d1c7a-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="d1c7a-129">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="d1c7a-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="d1c7a-130">Versione: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="d1c7a-130">Version: 2.1.11</span></span> | <span data-ttu-id="d1c7a-131">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="d1c7a-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="d1c7a-132">Versione: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="d1c7a-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="d1c7a-133">**Unity 2020.1.x (attualmente non supportato formalmente, incluso solo a scopo informativo)**</span><span class="sxs-lookup"><span data-stu-id="d1c7a-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="d1c7a-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="d1c7a-134">**Android**</span></span> | <span data-ttu-id="d1c7a-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="d1c7a-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="d1c7a-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="d1c7a-136">AR Foundation</span></span>  <br/> <span data-ttu-id="d1c7a-137">Versione: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="d1c7a-137">Version: 3.1.3</span></span> |  <span data-ttu-id="d1c7a-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="d1c7a-138">AR Foundation</span></span>  <br/> <span data-ttu-id="d1c7a-139">Versione: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="d1c7a-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="d1c7a-140">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="d1c7a-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="d1c7a-141">Versione: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="d1c7a-141">Version: 3.1.4</span></span> | <span data-ttu-id="d1c7a-142">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="d1c7a-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="d1c7a-143">Versione: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="d1c7a-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="d1c7a-144">Aggiornare le regole di scripting di MRTK UnityAR richiamando la voce di menu: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span><span class="sxs-lookup"><span data-stu-id="d1c7a-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="d1c7a-145">Abilitazione del provider di impostazioni della fotocamera Unity AR</span><span class="sxs-lookup"><span data-stu-id="d1c7a-145">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="d1c7a-146">La procedura seguente presuppone l'uso dell'oggetto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="d1c7a-146">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="d1c7a-147">I passaggi necessari per altri registrar del servizio possono essere diversi.</span><span class="sxs-lookup"><span data-stu-id="d1c7a-147">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="d1c7a-148">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="d1c7a-148">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Gerarchia della scena configurata MRTK](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="d1c7a-150">Selezionare **Copia e personalizza** per clonare il profilo MRTK per abilitare la configurazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="d1c7a-150">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Clonare il profilo MRTK](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="d1c7a-152">Selezionare **Clona** accanto al profilo della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="d1c7a-152">Select **Clone** next to the Camera Profile.</span></span>

    ![Clonare il profilo della fotocamera MRTK](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="d1c7a-154">Passare al pannello Inspector (Controllo) nella sezione camera system (Sistema fotocamera) ed espandere la **sezione Camera Settings Providers (Provider di impostazioni** fotocamera).</span><span class="sxs-lookup"><span data-stu-id="d1c7a-154">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Espandere i provider di impostazioni](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="d1c7a-156">Fare **clic su Add Camera Settings Provider (Aggiungi provider** di impostazioni fotocamera) ed espandere la voce New camera settings **(Nuove impostazioni fotocamera)** appena aggiunta.</span><span class="sxs-lookup"><span data-stu-id="d1c7a-156">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Espandere il nuovo provider di impostazioni](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="d1c7a-158">Selezionare il provider di impostazioni fotocamera UNITY AR</span><span class="sxs-lookup"><span data-stu-id="d1c7a-158">Select the Unity AR Camera Settings provider</span></span>

    ![Selezionare il provider di impostazioni di Unity AR](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="d1c7a-160">Per altre informazioni sulla configurazione del provider di impostazioni della fotocamera Unity AR: Provider [di impostazioni fotocamera Unity AR.](../features/camera-system/unity-ar-camera-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d1c7a-160">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d1c7a-161">Questa installazione controlla (all'avvio dell'applicazione) se i componenti ar Foundation sono nella scena.</span><span class="sxs-lookup"><span data-stu-id="d1c7a-161">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="d1c7a-162">In caso contrario, vengono aggiunti automaticamente per farlo funzionare con ARCore e ARKit.</span><span class="sxs-lookup"><span data-stu-id="d1c7a-162">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="d1c7a-163">Se è necessario impostare un comportamento specifico, è necessario aggiungere i componenti necessari da soli.</span><span class="sxs-lookup"><span data-stu-id="d1c7a-163">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="d1c7a-164">Per altre informazioni sui componenti di AR Foundation e sull'installazione, vedere questa [documentazione.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)</span><span class="sxs-lookup"><span data-stu-id="d1c7a-164">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="d1c7a-165">Creazione di una scena per dispositivi Android e iOS</span><span class="sxs-lookup"><span data-stu-id="d1c7a-165">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="d1c7a-166">Assicurarsi di aver aggiunto unityAR Camera Settings Provider alla scena.</span><span class="sxs-lookup"><span data-stu-id="d1c7a-166">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="d1c7a-167">Passare dalla piattaforma ad Android o iOS nelle impostazioni di compilazione di Unity</span><span class="sxs-lookup"><span data-stu-id="d1c7a-167">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

    <span data-ttu-id="d1c7a-168">Quando si cambia piattaforma, verrà visualizzata la finestra del configuratore di progetto MRTK con le impostazioni per la piattaforma scelta.</span><span class="sxs-lookup"><span data-stu-id="d1c7a-168">When you switch the platform you should see the MRTK Project Configurator Window with settings for your chosen platform.</span></span>  <span data-ttu-id="d1c7a-169">Fare clic su Applica per abilitare le impostazioni specifiche della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="d1c7a-169">Click Apply to enable platform specific settings.</span></span>

    <span data-ttu-id="d1c7a-170">Impostazioni del configuratore di progetti iOS</span><span class="sxs-lookup"><span data-stu-id="d1c7a-170">iOS Project Configurator Settings</span></span>

    ![Configuratore di progetti iOS](../features/images/camera-system/MRTKProjectConfigurator.png)

1. <span data-ttu-id="d1c7a-172">Non sono necessari passaggi aggiuntivi dopo il passaggio della piattaforma per Android.</span><span class="sxs-lookup"><span data-stu-id="d1c7a-172">There are no additional steps after switching the platform for Android.</span></span>

1. <span data-ttu-id="d1c7a-173">Se la piattaforma è iOS, modificare > impostazioni del progetto > Player > Altre impostazioni, sotto l'intestazione Ottimizzazione **deselezionare** Strip Engine Code (Strip Engine Code)</span><span class="sxs-lookup"><span data-stu-id="d1c7a-173">If the platform is iOS, Edit > Project Settings > Player > Other Settings, under the Optimization header, **uncheck** Strip Engine Code</span></span>

    ![Impostazioni iOS](../features/images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > <span data-ttu-id="d1c7a-175">Deselezionare Strip Engine Code è la soluzione a breve termine per un errore in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span><span class="sxs-lookup"><span data-stu-id="d1c7a-175">Unchecking Strip Engine Code is the short term solution to an error in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span></span>  <span data-ttu-id="d1c7a-176">Stiamo lavorando a una soluzione a lungo termine.</span><span class="sxs-lookup"><span data-stu-id="d1c7a-176">We are working on a long term solution.</span></span>

1. <span data-ttu-id="d1c7a-177">Compilare ed eseguire la scena</span><span class="sxs-lookup"><span data-stu-id="d1c7a-177">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="d1c7a-178">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="d1c7a-178">See also</span></span>

- [<span data-ttu-id="d1c7a-179">Impostazioni della fotocamera unity AR</span><span class="sxs-lookup"><span data-stu-id="d1c7a-179">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
