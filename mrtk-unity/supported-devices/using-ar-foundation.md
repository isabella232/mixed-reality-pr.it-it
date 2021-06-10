---
title: Configurazione MRTK per Android e iOS (ARFoundation)
description: Documentazione per configurare MRTK per Android e iOS (ARFoundation) in Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, AR Core, AR Kit, iOS, IOS, Android, AR Foundation
ms.openlocfilehash: 9f621008db76e3f8e443545b795db442d7c17dda
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345134"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="e16da-104">Come configurare MRTK per iOS e Android [Sperimentale]</span><span class="sxs-lookup"><span data-stu-id="e16da-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="e16da-105">Installare i pacchetti necessari</span><span class="sxs-lookup"><span data-stu-id="e16da-105">Install required packages</span></span>

1. <span data-ttu-id="e16da-106">Scaricare e importare il **pacchetto Microsoft.MixedReality.Toolkit.Unity.Foundation** da [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) o [unity Gestione pacchetti](../configuration/usingupm.md)</span><span class="sxs-lookup"><span data-stu-id="e16da-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="e16da-107">In Unity Gestione pacchetti (UPM) installare i pacchetti seguenti:</span><span class="sxs-lookup"><span data-stu-id="e16da-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="e16da-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="e16da-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="e16da-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="e16da-109">**Android**</span></span> | <span data-ttu-id="e16da-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="e16da-110">**iOS**</span></span> | <span data-ttu-id="e16da-111">Commenti</span><span class="sxs-lookup"><span data-stu-id="e16da-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="e16da-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e16da-112">AR Foundation</span></span>  <br/> <span data-ttu-id="e16da-113">Versione: 1.5.0 - anteprima 6</span><span class="sxs-lookup"><span data-stu-id="e16da-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="e16da-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e16da-114">AR Foundation</span></span>  <br/> <span data-ttu-id="e16da-115">Versione: 1.5.0 - anteprima 6</span><span class="sxs-lookup"><span data-stu-id="e16da-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="e16da-116">Per Unity 2018.4, questo pacchetto è incluso come anteprima.</span><span class="sxs-lookup"><span data-stu-id="e16da-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="e16da-117">Per visualizzare il pacchetto: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="e16da-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="e16da-118">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="e16da-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="e16da-119">Versione: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="e16da-119">Version: 2.1.2</span></span> | <span data-ttu-id="e16da-120">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="e16da-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="e16da-121">Versione: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="e16da-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="e16da-122">**Unity 2019.4.x**</span><span class="sxs-lookup"><span data-stu-id="e16da-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="e16da-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="e16da-123">**Android**</span></span> | <span data-ttu-id="e16da-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="e16da-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="e16da-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e16da-125">AR Foundation</span></span>  <br/> <span data-ttu-id="e16da-126">Versione: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="e16da-126">Version: 2.1.8</span></span> |  <span data-ttu-id="e16da-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e16da-127">AR Foundation</span></span>  <br/> <span data-ttu-id="e16da-128">Versione: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="e16da-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="e16da-129">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="e16da-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="e16da-130">Versione: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="e16da-130">Version: 2.1.11</span></span> | <span data-ttu-id="e16da-131">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="e16da-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="e16da-132">Versione: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="e16da-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="e16da-133">**Unity 2020.1.x (attualmente non supportato formalmente, incluso solo a scopo informativo)**</span><span class="sxs-lookup"><span data-stu-id="e16da-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="e16da-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="e16da-134">**Android**</span></span> | <span data-ttu-id="e16da-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="e16da-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="e16da-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e16da-136">AR Foundation</span></span>  <br/> <span data-ttu-id="e16da-137">Versione: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="e16da-137">Version: 3.1.3</span></span> |  <span data-ttu-id="e16da-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e16da-138">AR Foundation</span></span>  <br/> <span data-ttu-id="e16da-139">Versione: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="e16da-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="e16da-140">Plug-in ARCore XR</span><span class="sxs-lookup"><span data-stu-id="e16da-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="e16da-141">Versione: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="e16da-141">Version: 3.1.4</span></span> | <span data-ttu-id="e16da-142">Plug-in ARKit XR</span><span class="sxs-lookup"><span data-stu-id="e16da-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="e16da-143">Versione: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="e16da-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="e16da-144">Aggiornare le regole di scripting di MRTK UnityAR richiamando la voce di menu: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span><span class="sxs-lookup"><span data-stu-id="e16da-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

    ![Definizione degli script di aggiornamento](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="e16da-146">Abilitazione del provider di impostazioni della fotocamera Unity AR</span><span class="sxs-lookup"><span data-stu-id="e16da-146">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="e16da-147">La procedura seguente presuppone l'uso dell'oggetto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="e16da-147">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="e16da-148">I passaggi necessari per altri registrar del servizio possono essere diversi.</span><span class="sxs-lookup"><span data-stu-id="e16da-148">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="e16da-149">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="e16da-149">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Gerarchia della scena configurata MRTK](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="e16da-151">Selezionare **Copia e personalizza** per clonare il profilo MRTK per abilitare la configurazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="e16da-151">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Clonare il profilo MRTK](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="e16da-153">Selezionare **Clona** accanto al profilo della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="e16da-153">Select **Clone** next to the Camera Profile.</span></span>

    ![Clonare il profilo della fotocamera MRTK](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="e16da-155">Passare al pannello Inspector (Controllo) nella sezione camera system (Sistema fotocamera) ed espandere la **sezione Camera Settings Providers (Provider di impostazioni** fotocamera).</span><span class="sxs-lookup"><span data-stu-id="e16da-155">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Espandere i provider di impostazioni](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="e16da-157">Fare **clic su Add Camera Settings Provider (Aggiungi provider** di impostazioni fotocamera) ed espandere la voce New camera settings **(Nuove impostazioni fotocamera)** appena aggiunta.</span><span class="sxs-lookup"><span data-stu-id="e16da-157">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Espandere il nuovo provider di impostazioni](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="e16da-159">Selezionare il provider di impostazioni fotocamera UNITY AR</span><span class="sxs-lookup"><span data-stu-id="e16da-159">Select the Unity AR Camera Settings provider</span></span>

    ![Selezionare il provider di impostazioni di Unity AR](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="e16da-161">Per altre informazioni sulla configurazione del provider di impostazioni della fotocamera Unity AR: Provider [di impostazioni fotocamera Unity AR.](../features/camera-system/unity-ar-camera-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e16da-161">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e16da-162">Questa installazione controlla (all'avvio dell'applicazione) se i componenti ar Foundation sono nella scena.</span><span class="sxs-lookup"><span data-stu-id="e16da-162">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="e16da-163">In caso contrario, vengono aggiunti automaticamente per farlo funzionare con ARCore e ARKit.</span><span class="sxs-lookup"><span data-stu-id="e16da-163">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="e16da-164">Se è necessario impostare un comportamento specifico, è necessario aggiungere i componenti necessari da soli.</span><span class="sxs-lookup"><span data-stu-id="e16da-164">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="e16da-165">Per altre informazioni sui componenti di AR Foundation e sull'installazione, vedere questa [documentazione.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)</span><span class="sxs-lookup"><span data-stu-id="e16da-165">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="e16da-166">Creazione di una scena per dispositivi Android e iOS</span><span class="sxs-lookup"><span data-stu-id="e16da-166">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="e16da-167">Assicurarsi di aver aggiunto unityAR Camera Settings Provider alla scena.</span><span class="sxs-lookup"><span data-stu-id="e16da-167">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="e16da-168">Passare dalla piattaforma ad Android o iOS nelle impostazioni di compilazione di Unity</span><span class="sxs-lookup"><span data-stu-id="e16da-168">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

1. <span data-ttu-id="e16da-169">Verificare che il provider di gestione plug-in XR associato sia abilitato</span><span class="sxs-lookup"><span data-stu-id="e16da-169">Ensure the associated XR Plug-in management provider is enabled</span></span>

    <span data-ttu-id="e16da-170">Gestione plug-in iOS XR:  ![ Gestione plug-in XR iOS](../features/images/XRManagementiOS.png)</span><span class="sxs-lookup"><span data-stu-id="e16da-170">iOS XR Plug-in Management:  ![XR Plug-in Management iOS](../features/images/XRManagementiOS.png)</span></span>

1. <span data-ttu-id="e16da-171">Compilare ed eseguire la scena</span><span class="sxs-lookup"><span data-stu-id="e16da-171">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="e16da-172">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="e16da-172">See also</span></span>

- [<span data-ttu-id="e16da-173">Impostazioni fotocamera Unity AR</span><span class="sxs-lookup"><span data-stu-id="e16da-173">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
