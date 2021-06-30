---
title: Windows Mixed Reality della fotocamera
description: Documentazione per usare le Windows Mixed Reality della fotocamera in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, fotocamera,
ms.openlocfilehash: 49b178b7ebd1fbcdaab9648baeaa6abfa9e885ea
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121639"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="2474e-104">Windows Mixed Reality provider di impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="2474e-104">Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="2474e-105">Il provider Windows Mixed Reality impostazioni della fotocamera determina il tipo di dispositivo su cui è in esecuzione l'applicazione e applica le impostazioni di configurazione appropriate in base alla visualizzazione (trasparente o opaca).</span><span class="sxs-lookup"><span data-stu-id="2474e-105">The Windows Mixed Reality camera settings provider determines the type of device, upon which the application is running and applies the appropriate configuration settings based on the display (transparent or opaque).</span></span>

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="2474e-106">Abilitazione del provider Windows Mixed Reality impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="2474e-106">Enabling the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="2474e-107">La procedura seguente presuppone l'uso dell'oggetto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="2474e-107">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="2474e-108">I passaggi necessari per altri registrar del servizio possono essere diversi.</span><span class="sxs-lookup"><span data-stu-id="2474e-108">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="2474e-109">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="2474e-109">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Gerarchia della scena configurata da MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="2474e-111">Passare al pannello Inspector (Controllo) alla sezione camera system (Sistema fotocamera) ed espandere la **sezione Camera Settings Providers (Provider di impostazioni** fotocamera).</span><span class="sxs-lookup"><span data-stu-id="2474e-111">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Espandere i provider di impostazioni](../images/camera-system/ExpandProviders.png)

3. <span data-ttu-id="2474e-113">Fare **clic su Add Camera Settings Provider (Aggiungi provider** di impostazioni fotocamera) ed espandere la voce New camera settings **(Nuove impostazioni fotocamera) appena** aggiunta.</span><span class="sxs-lookup"><span data-stu-id="2474e-113">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Espandere il nuovo provider di impostazioni](../images/camera-system/ExpandNewProvider.png)

4. <span data-ttu-id="2474e-115">Selezionare il provider Windows Mixed Reality impostazioni fotocamera</span><span class="sxs-lookup"><span data-stu-id="2474e-115">Select the Windows Mixed Reality Camera Settings provider</span></span>

    ![Selezionare Windows Mixed Reality provider di impostazioni](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> <span data-ttu-id="2474e-117">Quando si usano i profili predefiniti di Microsoft Mixed Reality Toolkit, il provider Windows Mixed Reality impostazioni della fotocamera sarà già abilitato e configurato.</span><span class="sxs-lookup"><span data-stu-id="2474e-117">When using the Microsoft Mixed Reality Toolkit default profiles, the Windows Mixed Reality camera settings provider will already be enabled and configured.</span></span>

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="2474e-118">Configurazione del provider Windows Mixed Reality impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="2474e-118">Configuring the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="2474e-119">Il Windows Mixed Reality impostazioni della fotocamera supporta anche un profilo.</span><span class="sxs-lookup"><span data-stu-id="2474e-119">The Windows Mixed Reality Camera Settings also supports a profile.</span></span> <span data-ttu-id="2474e-120">Questo profilo offre le opzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="2474e-120">This profile provides the following options:</span></span>

![Windows Mixed Reality delle impostazioni della fotocamera](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a><span data-ttu-id="2474e-122">Eseguire il rendering dell'acquisizione di realtà mista dalla fotocamera/videocamere</span><span class="sxs-lookup"><span data-stu-id="2474e-122">Render mixed reality capture from the photo/video camera</span></span>

<span data-ttu-id="2474e-123">Con questa impostazione attivata HoloLens 2, è possibile abilitare l'allineamento degli ologrammi nelle acquisizioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="2474e-123">With this setting on HoloLens 2, you can enable hologram alignment in your mixed reality captures.</span></span> <span data-ttu-id="2474e-124">Se abilitata, la piattaforma fornirà all'app un altro dispositivo HolographicCamera quando viene eseguita una foto o un video di acquisizione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="2474e-124">If enabled, the platform will provide an additional HolographicCamera to the app when a mixed reality capture photo or video is taken.</span></span> <span data-ttu-id="2474e-125">Questa holographicCamera fornisce matrici di visualizzazione corrispondenti alla posizione della fotocamera/videocamere e le matrici di proiezione che usano il campo di visualizzazione foto/videocamera.</span><span class="sxs-lookup"><span data-stu-id="2474e-125">This HolographicCamera provides view matrices corresponding to the photo/video camera location, and it provides projection matrices using the photo/video camera field of view.</span></span> <span data-ttu-id="2474e-126">In questo modo gli ologrammi, ad esempio le mesh delle mani, rimangono visibilmente allineati nell'output video.</span><span class="sxs-lookup"><span data-stu-id="2474e-126">This will ensure that holograms, such as hand meshes, remain visibly aligned in the video output.</span></span>

### <a name="hololens-2-reprojection-method"></a><span data-ttu-id="2474e-127">HoloLens 2 di nuovo progetto</span><span class="sxs-lookup"><span data-stu-id="2474e-127">HoloLens 2 reprojection method</span></span>

<span data-ttu-id="2474e-128">Imposta il metodo iniziale per la HoloLens 2 di progetto.</span><span class="sxs-lookup"><span data-stu-id="2474e-128">Sets the initial method for HoloLens 2 reprojection.</span></span> <span data-ttu-id="2474e-129">Per impostazione predefinita, è consigliabile usare la riproiezione della profondità, perché tutte le parti della scena verranno stabilizzate in modo indipendente in base alla distanza dall'utente.</span><span class="sxs-lookup"><span data-stu-id="2474e-129">The default recommendation is to use depth reprojection, as all parts of the scene will be independently stabilized based on their distance from the user.</span></span> <span data-ttu-id="2474e-130">Se gli ologrammi appaiono ancora instabili, provare a verificare che tutti gli oggetti hanno inviato correttamente la profondità al buffer di profondità.</span><span class="sxs-lookup"><span data-stu-id="2474e-130">If holograms still appear unstable, try ensuring all objects have properly submitted their depth to the depth buffer.</span></span> <span data-ttu-id="2474e-131">A volte si tratta di un'impostazione shader.</span><span class="sxs-lookup"><span data-stu-id="2474e-131">This is sometimes a shader setting.</span></span> <span data-ttu-id="2474e-132">Se la profondità sembra essere inviata correttamente e l'instabilità è ancora presente, provare la stabilizzazione autoplanare, che usa il buffer di profondità per calcolare un piano di stabilizzazione.</span><span class="sxs-lookup"><span data-stu-id="2474e-132">If depth appears to be properly submitted and instability is still present, try autoplanar stabilization, which uses the depth buffer to calculate a stabilization plane.</span></span> <span data-ttu-id="2474e-133">Se un'app non è in grado di inviare dati di profondità sufficienti perché una di queste opzioni sia utilizzabile, viene fornita una nuovaproiezione planare come fallback.</span><span class="sxs-lookup"><span data-stu-id="2474e-133">If an app is unable to submit enough depth data for either of those options to be usable, planar reprojection is provided as a fallback.</span></span> <span data-ttu-id="2474e-134">Questo metodo sarà basato sui dati del punto di attivazione forniti da un'app [tramite SetFocusPointForFrame.](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html)</span><span class="sxs-lookup"><span data-stu-id="2474e-134">This method will be based on an app's provided focus point data via [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).</span></span>

<span data-ttu-id="2474e-135">Per aggiornare il metodo di riestrazione in fase di esecuzione, accedere a `WindowsMixedRealityReprojectionUpdater` come in questo modo:</span><span class="sxs-lookup"><span data-stu-id="2474e-135">To update the reprojection method at runtime, access the `WindowsMixedRealityReprojectionUpdater` like so:</span></span>

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

<span data-ttu-id="2474e-136">Questa operazione deve essere aggiornata una sola volta e il valore viene riutilizzato per tutti i fotogrammi successivi.</span><span class="sxs-lookup"><span data-stu-id="2474e-136">This only needs to be updated once and the value is reused for all subsequent frames.</span></span> <span data-ttu-id="2474e-137">Se il metodo verrà aggiornato di frequente, è consigliabile memorizzare nella cache il risultato anziché `EnsureComponent` chiamarlo spesso.</span><span class="sxs-lookup"><span data-stu-id="2474e-137">If the method will be updated frequently, it's recommended to cache the result of `EnsureComponent` instead of calling it often.</span></span>

## <a name="see-also"></a><span data-ttu-id="2474e-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2474e-138">See also</span></span>

- [<span data-ttu-id="2474e-139">Panoramica del sistema di fotocamera</span><span class="sxs-lookup"><span data-stu-id="2474e-139">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="2474e-140">Creazione di un provider di impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="2474e-140">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
- [<span data-ttu-id="2474e-141">Rendering Acquisizione realtà mista dalla fotocamera PV</span><span class="sxs-lookup"><span data-stu-id="2474e-141">Rendering Mixed Reality Capture from the PV camera</span></span>](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [<span data-ttu-id="2474e-142">Reproiezione olografica</span><span class="sxs-lookup"><span data-stu-id="2474e-142">Holographic reprojection</span></span>](/windows/mixed-reality/hologram-stability#reprojection)