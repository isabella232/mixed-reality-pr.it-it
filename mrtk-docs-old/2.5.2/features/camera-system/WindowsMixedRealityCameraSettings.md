---
title: WindowsMixedRealityCameraSettings
description: Documentazione per usare la fotocamera di realtà mista di Windows in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, fotocamera,
ms.openlocfilehash: a2459cef55e6c98532ded3d2709ba69e750fa267
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783810"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="5887c-104">Provider di impostazioni della fotocamera per la realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="5887c-104">Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="5887c-105">Il provider di impostazioni della camera di realtà mista di Windows determina il tipo di dispositivo su cui l'applicazione è in esecuzione e applica le impostazioni di configurazione appropriate in base allo schermo (trasparente o opaco).</span><span class="sxs-lookup"><span data-stu-id="5887c-105">The Windows Mixed Reality camera settings provider determines the type of device, upon which the application is running and applies the appropriate configuration settings based on the display (transparent or opaque).</span></span>

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="5887c-106">Abilitazione del provider di impostazioni della camera di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="5887c-106">Enabling the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="5887c-107">I passaggi seguenti presuppongono l'uso dell'oggetto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="5887c-107">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="5887c-108">I passaggi necessari per altri registrar di servizi potrebbero essere diversi.</span><span class="sxs-lookup"><span data-stu-id="5887c-108">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="5887c-109">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="5887c-109">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="5887c-111">Passare al pannello di controllo nella sezione sistema della fotocamera ed espandere la sezione **provider impostazioni fotocamera** .</span><span class="sxs-lookup"><span data-stu-id="5887c-111">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Espandi provider di impostazioni](../images/camera-system/ExpandProviders.png)

3. <span data-ttu-id="5887c-113">Fare clic su **Aggiungi provider di impostazioni della fotocamera** ed espandere la nuova voce di **impostazioni della fotocamera** appena aggiunta.</span><span class="sxs-lookup"><span data-stu-id="5887c-113">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Espandi nuovo provider di impostazioni](../images/camera-system/ExpandNewProvider.png)

4. <span data-ttu-id="5887c-115">Selezionare il provider di impostazioni della fotocamera per la realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="5887c-115">Select the Windows Mixed Reality Camera Settings provider</span></span>

    ![Selezionare il provider di impostazioni della realtà mista di Windows](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> <span data-ttu-id="5887c-117">Quando si usano i profili predefiniti di Microsoft Mixed Reality Toolkit, il provider di impostazioni della fotocamera di realtà mista di Windows verrà già abilitato e configurato.</span><span class="sxs-lookup"><span data-stu-id="5887c-117">When using the Microsoft Mixed Reality Toolkit default profiles, the Windows Mixed Reality camera settings provider will already be enabled and configured.</span></span>

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="5887c-118">Configurazione del provider di impostazioni della fotocamera per la realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="5887c-118">Configuring the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="5887c-119">Le impostazioni della fotocamera per la realtà mista di Windows supportano anche un profilo.</span><span class="sxs-lookup"><span data-stu-id="5887c-119">The Windows Mixed Reality Camera Settings also supports a profile.</span></span> <span data-ttu-id="5887c-120">Questo profilo offre le opzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="5887c-120">This profile provides the following options:</span></span>

![Configurazione delle impostazioni della fotocamera per la realtà mista di Windows](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a><span data-ttu-id="5887c-122">Rendering dell'acquisizione di realtà mista dalla fotocamera foto/video</span><span class="sxs-lookup"><span data-stu-id="5887c-122">Render mixed reality capture from the photo/video camera</span></span>

<span data-ttu-id="5887c-123">Con questa impostazione in HoloLens 2 è possibile abilitare l'allineamento degli ologrammi nelle acquisizioni della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="5887c-123">With this setting on HoloLens 2, you can enable hologram alignment in your mixed reality captures.</span></span> <span data-ttu-id="5887c-124">Se abilitata, la piattaforma fornirà un HolographicCamera aggiuntivo all'app quando viene eseguita una foto o un video di acquisizione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="5887c-124">If enabled, the platform will provide an additional HolographicCamera to the app when a mixed reality capture photo or video is taken.</span></span> <span data-ttu-id="5887c-125">Questo HolographicCamera fornisce le matrici di visualizzazione corrispondenti al percorso della fotocamera foto/video e fornisce matrici di proiezione usando il campo foto/video della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="5887c-125">This HolographicCamera provides view matrices corresponding to the photo/video camera location, and it provides projection matrices using the photo/video camera field of view.</span></span> <span data-ttu-id="5887c-126">In questo modo si garantisce che gli ologrammi, ad esempio le maglie della mano, rimangano allineati in modo visibile nell'output del video.</span><span class="sxs-lookup"><span data-stu-id="5887c-126">This will ensure that holograms, such as hand meshes, remain visibly aligned in the video output.</span></span>

### <a name="hololens-2-reprojection-method"></a><span data-ttu-id="5887c-127">Metodo di riproiezione HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5887c-127">HoloLens 2 reprojection method</span></span>

<span data-ttu-id="5887c-128">Imposta il metodo iniziale per la riproiezione HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5887c-128">Sets the initial method for HoloLens 2 reprojection.</span></span> <span data-ttu-id="5887c-129">L'indicazione predefinita prevede l'uso della riproiezione di profondità, in quanto tutte le parti della scena verranno stabilizzate in modo indipendente in base alla distanza dall'utente.</span><span class="sxs-lookup"><span data-stu-id="5887c-129">The default recommendation is to use depth reprojection, as all parts of the scene will be independently stabilized based on their distance from the user.</span></span> <span data-ttu-id="5887c-130">Se gli ologrammi sembrano ancora instabili, provare a verificare che tutti gli oggetti abbiano inviato correttamente la profondità al buffer di profondità.</span><span class="sxs-lookup"><span data-stu-id="5887c-130">If holograms still appear unstable, try ensuring all objects have properly submitted their depth to the depth buffer.</span></span> <span data-ttu-id="5887c-131">Questa è talvolta un'impostazione dello shader.</span><span class="sxs-lookup"><span data-stu-id="5887c-131">This is sometimes a shader setting.</span></span> <span data-ttu-id="5887c-132">Se la profondità sembra essere inviata correttamente e l'instabilità è ancora presente, provare la stabilizzazione autoplanal, che usa il buffer di profondità per calcolare un piano di stabilizzazione.</span><span class="sxs-lookup"><span data-stu-id="5887c-132">If depth appears to be properly submitted and instability is still present, try autoplanar stabilization, which uses the depth buffer to calculate a stabilization plane.</span></span> <span data-ttu-id="5887c-133">Se un'app non è in grado di inviare dati di profondità sufficienti per una di queste opzioni, la riproiezione piana viene fornita come fallback.</span><span class="sxs-lookup"><span data-stu-id="5887c-133">If an app is unable to submit enough depth data for either of those options to be usable, planar reprojection is provided as a fallback.</span></span> <span data-ttu-id="5887c-134">Questo metodo sarà basato sui dati del punto di interesse forniti da un'app tramite [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).</span><span class="sxs-lookup"><span data-stu-id="5887c-134">This method will be based on an app's provided focus point data via [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).</span></span>

<span data-ttu-id="5887c-135">Per aggiornare il metodo di riproiezione in fase di esecuzione, accedere a nel `WindowsMixedRealityReprojectionUpdater` modo seguente:</span><span class="sxs-lookup"><span data-stu-id="5887c-135">To update the reprojection method at runtime, access the `WindowsMixedRealityReprojectionUpdater` like so:</span></span>

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

<span data-ttu-id="5887c-136">Questa operazione deve essere aggiornata solo una volta e il valore viene riutilizzato per tutti i frame successivi.</span><span class="sxs-lookup"><span data-stu-id="5887c-136">This only needs to be updated once and the value is reused for all subsequent frames.</span></span> <span data-ttu-id="5887c-137">Se il metodo verrà aggiornato di frequente, è consigliabile memorizzare nella cache il risultato di `EnsureComponent` invece di chiamarlo spesso.</span><span class="sxs-lookup"><span data-stu-id="5887c-137">If the method will be updated frequently, it's recommended to cache the result of `EnsureComponent` instead of calling it often.</span></span>

## <a name="see-also"></a><span data-ttu-id="5887c-138">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="5887c-138">See also</span></span>

- [<span data-ttu-id="5887c-139">Panoramica del sistema di fotocamere</span><span class="sxs-lookup"><span data-stu-id="5887c-139">Camera System Overview</span></span>](CameraSystemOverview.md)
- [<span data-ttu-id="5887c-140">Creazione di un provider di impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="5887c-140">Creating a Camera Settings Provider</span></span>](CreateSettingsProvider.md)
- [<span data-ttu-id="5887c-141">Rendering dell'acquisizione di realtà mista dalla fotocamera PV</span><span class="sxs-lookup"><span data-stu-id="5887c-141">Rendering Mixed Reality Capture from the PV camera</span></span>](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [<span data-ttu-id="5887c-142">Riproiezione olografica</span><span class="sxs-lookup"><span data-stu-id="5887c-142">Holographic reprojection</span></span>](https://docs.microsoft.com/windows/mixed-reality/hologram-stability#reprojection)
