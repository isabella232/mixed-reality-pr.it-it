---
title: Windows Mixed Reality della fotocamera
description: Documentazione per l'Windows Mixed Reality camera in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, fotocamera,
ms.openlocfilehash: 94e00f47dc565af0824ef6acf5c08a9e99d4529f
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145168"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="f6252-104">Windows Mixed Reality provider di impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="f6252-104">Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="f6252-105">Il Windows Mixed Reality delle impostazioni della fotocamera determina il tipo di dispositivo su cui è in esecuzione l'applicazione e applica le impostazioni di configurazione appropriate in base alla visualizzazione (trasparente o opaca).</span><span class="sxs-lookup"><span data-stu-id="f6252-105">The Windows Mixed Reality camera settings provider determines the type of device, upon which the application is running and applies the appropriate configuration settings based on the display (transparent or opaque).</span></span>

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="f6252-106">Abilitazione del provider Windows Mixed Reality impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="f6252-106">Enabling the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="f6252-107">La procedura seguente presuppone l'uso dell'oggetto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="f6252-107">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="f6252-108">I passaggi necessari per altri registrar del servizio possono essere diversi.</span><span class="sxs-lookup"><span data-stu-id="f6252-108">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="f6252-109">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="f6252-109">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="f6252-111">Passare al pannello Inspector (Controllo) nella sezione camera system (Sistema fotocamera) ed espandere la **sezione Camera Settings Providers (Provider di impostazioni fotocamera).**</span><span class="sxs-lookup"><span data-stu-id="f6252-111">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Espandere i provider di impostazioni](../images/camera-system/ExpandProviders.png)

3. <span data-ttu-id="f6252-113">Fare **clic su Add Camera Settings Provider (Aggiungi provider** di impostazioni fotocamera) ed espandere la voce New camera settings **(Nuove impostazioni fotocamera) appena** aggiunta.</span><span class="sxs-lookup"><span data-stu-id="f6252-113">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Espandere il nuovo provider di impostazioni](../images/camera-system/ExpandNewProvider.png)

4. <span data-ttu-id="f6252-115">Selezionare il provider Windows Mixed Reality impostazioni fotocamera</span><span class="sxs-lookup"><span data-stu-id="f6252-115">Select the Windows Mixed Reality Camera Settings provider</span></span>

    ![Selezionare Windows Mixed Reality provider di impostazioni](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> <span data-ttu-id="f6252-117">Quando si usano i profili predefiniti di Microsoft Mixed Reality Toolkit, il provider Windows Mixed Reality impostazioni della fotocamera sarà già abilitato e configurato.</span><span class="sxs-lookup"><span data-stu-id="f6252-117">When using the Microsoft Mixed Reality Toolkit default profiles, the Windows Mixed Reality camera settings provider will already be enabled and configured.</span></span>

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="f6252-118">Configurazione del provider Windows Mixed Reality impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="f6252-118">Configuring the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="f6252-119">Anche Windows Mixed Reality impostazioni della fotocamera supporta un profilo.</span><span class="sxs-lookup"><span data-stu-id="f6252-119">The Windows Mixed Reality Camera Settings also supports a profile.</span></span> <span data-ttu-id="f6252-120">Questo profilo offre le opzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f6252-120">This profile provides the following options:</span></span>

![Windows Mixed Reality delle impostazioni della fotocamera](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a><span data-ttu-id="f6252-122">Eseguire il rendering dell'acquisizione di realtà mista dalla foto/videocamere</span><span class="sxs-lookup"><span data-stu-id="f6252-122">Render mixed reality capture from the photo/video camera</span></span>

<span data-ttu-id="f6252-123">Con questa impostazione su HoloLens 2, è possibile abilitare l'allineamento degli ologrammi nelle acquisizioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="f6252-123">With this setting on HoloLens 2, you can enable hologram alignment in your mixed reality captures.</span></span> <span data-ttu-id="f6252-124">Se abilitata, la piattaforma fornirà un'ulteriore holographicCamera all'app quando viene scattata una foto o un video di acquisizione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="f6252-124">If enabled, the platform will provide an additional HolographicCamera to the app when a mixed reality capture photo or video is taken.</span></span> <span data-ttu-id="f6252-125">Questa holographicCamera fornisce matrici di visualizzazione corrispondenti alla posizione della foto/videocamera e fornisce matrici di proiezione usando il campo di visualizzazione foto/videocamera.</span><span class="sxs-lookup"><span data-stu-id="f6252-125">This HolographicCamera provides view matrices corresponding to the photo/video camera location, and it provides projection matrices using the photo/video camera field of view.</span></span> <span data-ttu-id="f6252-126">In questo modo gli ologrammi, ad esempio le mesh a mano, rimarranno visibilmente allineati nell'output video.</span><span class="sxs-lookup"><span data-stu-id="f6252-126">This will ensure that holograms, such as hand meshes, remain visibly aligned in the video output.</span></span>

### <a name="hololens-2-reprojection-method"></a><span data-ttu-id="f6252-127">HoloLens 2 metodo di riprogettazione</span><span class="sxs-lookup"><span data-stu-id="f6252-127">HoloLens 2 reprojection method</span></span>

<span data-ttu-id="f6252-128">Imposta il metodo iniziale per la HoloLens 2 di progetto.</span><span class="sxs-lookup"><span data-stu-id="f6252-128">Sets the initial method for HoloLens 2 reprojection.</span></span> <span data-ttu-id="f6252-129">Per impostazione predefinita, è consigliabile usare la riproiezione della profondità, in quanto tutte le parti della scena verranno stabilizzate in modo indipendente in base alla distanza dall'utente.</span><span class="sxs-lookup"><span data-stu-id="f6252-129">The default recommendation is to use depth reprojection, as all parts of the scene will be independently stabilized based on their distance from the user.</span></span> <span data-ttu-id="f6252-130">Se gli ologrammi appaiono ancora instabili, provare a verificare che tutti gli oggetti hanno inviato correttamente la profondità al buffer di profondità.</span><span class="sxs-lookup"><span data-stu-id="f6252-130">If holograms still appear unstable, try ensuring all objects have properly submitted their depth to the depth buffer.</span></span> <span data-ttu-id="f6252-131">A volte si tratta di un'impostazione shader.</span><span class="sxs-lookup"><span data-stu-id="f6252-131">This is sometimes a shader setting.</span></span> <span data-ttu-id="f6252-132">Se la profondità sembra essere inviata correttamente e l'instabilità è ancora presente, provare a stabilizzare automaticamente, che usa il buffer di profondità per calcolare un piano di stabilizzazione.</span><span class="sxs-lookup"><span data-stu-id="f6252-132">If depth appears to be properly submitted and instability is still present, try autoplanar stabilization, which uses the depth buffer to calculate a stabilization plane.</span></span> <span data-ttu-id="f6252-133">Se un'app non è in grado di inviare dati di profondità sufficienti perché una di queste opzioni sia utilizzabile, la riproiezione planare viene fornita come fallback.</span><span class="sxs-lookup"><span data-stu-id="f6252-133">If an app is unable to submit enough depth data for either of those options to be usable, planar reprojection is provided as a fallback.</span></span> <span data-ttu-id="f6252-134">Questo metodo sarà basato sui dati del punto di attivazione forniti da un'app tramite [SetFocusPointForFrame.](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html)</span><span class="sxs-lookup"><span data-stu-id="f6252-134">This method will be based on an app's provided focus point data via [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).</span></span>

<span data-ttu-id="f6252-135">Per aggiornare il metodo di riprogettazione in fase di esecuzione, accedere all'oggetto `WindowsMixedRealityReprojectionUpdater` simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="f6252-135">To update the reprojection method at runtime, access the `WindowsMixedRealityReprojectionUpdater` like so:</span></span>

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

<span data-ttu-id="f6252-136">Questa operazione deve essere aggiornata una sola volta e il valore viene riutilizzato per tutti i fotogrammi successivi.</span><span class="sxs-lookup"><span data-stu-id="f6252-136">This only needs to be updated once and the value is reused for all subsequent frames.</span></span> <span data-ttu-id="f6252-137">Se il metodo verrà aggiornato di frequente, è consigliabile memorizzare nella cache il risultato anziché `EnsureComponent` chiamarlo spesso.</span><span class="sxs-lookup"><span data-stu-id="f6252-137">If the method will be updated frequently, it's recommended to cache the result of `EnsureComponent` instead of calling it often.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6252-138">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="f6252-138">See also</span></span>

- [<span data-ttu-id="f6252-139">Panoramica del sistema di fotocamera</span><span class="sxs-lookup"><span data-stu-id="f6252-139">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="f6252-140">Creazione di un provider di impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="f6252-140">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
- [<span data-ttu-id="f6252-141">Rendering Acquisizione realtà mista dalla fotocamera PV</span><span class="sxs-lookup"><span data-stu-id="f6252-141">Rendering Mixed Reality Capture from the PV camera</span></span>](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [<span data-ttu-id="f6252-142">Riprogettazione olografica</span><span class="sxs-lookup"><span data-stu-id="f6252-142">Holographic reprojection</span></span>](/windows/mixed-reality/hologram-stability#reprojection)