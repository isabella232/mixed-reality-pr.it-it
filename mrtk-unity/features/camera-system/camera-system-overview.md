---
title: Panoramica del sistema di fotocamera
description: Pagina di destinazione per il sistema di fotocamera in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, fotocamera,
ms.openlocfilehash: e3b7caacaa9baa67fd81f6d32f3fd8c9f123e66d
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121289"
---
# <a name="camera-system"></a><span data-ttu-id="cb690-104">Sistema di fotocamera</span><span class="sxs-lookup"><span data-stu-id="cb690-104">Camera system</span></span>

<span data-ttu-id="cb690-105">Il sistema di fotocamera consente a Microsoft Mixed Reality Toolkit di configurare e ottimizzare la fotocamera dell'applicazione per l'uso in applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="cb690-105">The camera system enables the Microsoft Mixed Reality Toolkit to configure and optimize the application's camera for use in mixed reality applications.</span></span> <span data-ttu-id="cb690-106">Usando il sistema di fotocamera, le applicazioni possono essere scritte per supportare dispositivi opachi (ad esempio, la realtà virtuale) e trasparenti (ad esempio, Microsoft HoloLens) senza dover scrivere codice per distinguere e gestire ogni tipo di schermo.</span><span class="sxs-lookup"><span data-stu-id="cb690-106">Using the camera system, applications can be written to support both opaque (ex: virtual reality) and transparent (ex: Microsoft HoloLens) devices without needing to write code to distinguish between, and accommodate for, each type of display.</span></span>

## <a name="enabling-the-camera-system"></a><span data-ttu-id="cb690-107">Abilitazione del sistema di fotocamera</span><span class="sxs-lookup"><span data-stu-id="cb690-107">Enabling the camera system</span></span>

<span data-ttu-id="cb690-108">Il sistema di fotocamere è gestito dall'oggetto MixedRealityToolkit (o da un altro componente registrar del servizio).</span><span class="sxs-lookup"><span data-stu-id="cb690-108">The Camera System is managed by the MixedRealityToolkit object (or another service registrar component).</span></span>

<span data-ttu-id="cb690-109">La procedura seguente presuppone l'uso dell'oggetto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="cb690-109">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="cb690-110">I passaggi necessari per altri registrar del servizio possono essere diversi.</span><span class="sxs-lookup"><span data-stu-id="cb690-110">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="cb690-111">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="cb690-111">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Gerarchia della scena configurata di MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="cb690-113">Passare al pannello Inspector (Controllo) alla sezione camera system (Sistema fotocamera) e verificare che **l'opzione Enable Camera System (Abilita** sistema fotocamera) sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="cb690-113">Navigate the Inspector panel to the camera system section and ensure that **Enable Camera System** is checked.</span></span>

    ![Abilitazione del sistema di fotocamera](../images/camera-system/EnableCameraSystem.png)

3. <span data-ttu-id="cb690-115">Selezionare l'implementazione del sistema di fotocamera.</span><span class="sxs-lookup"><span data-stu-id="cb690-115">Select the camera system implementation.</span></span> <span data-ttu-id="cb690-116">L'implementazione predefinita della classe fornita da MRTK è `MixedRealityCameraSystem` .</span><span class="sxs-lookup"><span data-stu-id="cb690-116">The default class implementation provided by the MRTK is the `MixedRealityCameraSystem`.</span></span>

    ![Selezionare l'implementazione del sistema di fotocamera](../images/camera-system/SelectCameraSystemType.png)

4. <span data-ttu-id="cb690-118">Selezionare il profilo di configurazione desiderato</span><span class="sxs-lookup"><span data-stu-id="cb690-118">Select the desired configuration profile</span></span>

    ![Selezionare il profilo del sistema di fotocamera](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a><span data-ttu-id="cb690-120">Configurazione del sistema di fotocamera</span><span class="sxs-lookup"><span data-stu-id="cb690-120">Configuring the camera system</span></span>

### <a name="settings-providers"></a><span data-ttu-id="cb690-121">Provider di impostazioni</span><span class="sxs-lookup"><span data-stu-id="cb690-121">Settings providers</span></span>

![Provider di impostazioni della fotocamera](../images/camera-system/CameraSettingsProviders.png)

<span data-ttu-id="cb690-123">I provider di impostazioni della fotocamera abilitano la configurazione specifica della piattaforma della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="cb690-123">Camera setting providers enable platform specific configuration of the camera.</span></span> <span data-ttu-id="cb690-124">Queste impostazioni possono includere passaggi di configurazione personalizzati e/o componenti.</span><span class="sxs-lookup"><span data-stu-id="cb690-124">These settings may include custom configuration steps and/or components.</span></span>

<span data-ttu-id="cb690-125">I provider possono essere aggiunti facendo clic sul **pulsante Add Camera Settings Provider (Aggiungi provider di impostazioni** fotocamera).</span><span class="sxs-lookup"><span data-stu-id="cb690-125">Providers can be added by clicking the **Add Camera Settings Provider** button.</span></span> <span data-ttu-id="cb690-126">Possono essere rimossi facendo clic **-** sul pulsante a destra del nome del provider.</span><span class="sxs-lookup"><span data-stu-id="cb690-126">They can be removed by clicking the **-** button to the right of the provider's name.</span></span>

> [!Note]
> <span data-ttu-id="cb690-127">Non tutte le piattaforme richiedono un provider di impostazioni della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="cb690-127">Not all platforms will require a camera settings provider.</span></span> <span data-ttu-id="cb690-128">Se non sono presenti provider compatibili con la piattaforma in cui è in esecuzione l'applicazione, Microsoft Mixed Reality Toolkit applierà le impostazioni predefinite di base.</span><span class="sxs-lookup"><span data-stu-id="cb690-128">If there are no providers that are compatible with the platform on which the application is running, the Microsoft Mixed Reality Toolkit will apply basic defaults.</span></span>

### <a name="display-settings"></a><span data-ttu-id="cb690-129">Impostazioni schermo</span><span class="sxs-lookup"><span data-stu-id="cb690-129">Display settings</span></span>

![Impostazioni di visualizzazione della fotocamera](../images/camera-system/CameraDisplaySettings.png)

<span data-ttu-id="cb690-131">Le impostazioni di visualizzazione vengono specificate sia per gli schermi opachi (ad esempio, virtual reality) che per i display trasparenti (ad esempio, Microsoft HoloLens).</span><span class="sxs-lookup"><span data-stu-id="cb690-131">Display settings are specified for both opaque (ex: Virtual Reality) and transparent (ex: Microsoft HoloLens) displays.</span></span> <span data-ttu-id="cb690-132">La fotocamera viene configurata, in fase di esecuzione, usando queste impostazioni.</span><span class="sxs-lookup"><span data-stu-id="cb690-132">The camera is configured, at run time, using these settings.</span></span>

<span data-ttu-id="cb690-133">**Near Clip**</span><span class="sxs-lookup"><span data-stu-id="cb690-133">**Near Clip**</span></span>

<span data-ttu-id="cb690-134">Il piano di ritaglio vicino è il più vicino, in metri, che un oggetto virtuale può essere alla fotocamera ed essere ancora sottoposto a rendering.</span><span class="sxs-lookup"><span data-stu-id="cb690-134">The near clip plane is the closest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="cb690-135">Per il massimo comfort dell'utente, è consigliabile rendere questo valore maggiore di zero.</span><span class="sxs-lookup"><span data-stu-id="cb690-135">For greatest user comfort, it is recommended to make this value greater than zero.</span></span> <span data-ttu-id="cb690-136">L'immagine precedente contiene valori che si sono trovati a proprio agio in un'ampia gamma di dispositivi.</span><span class="sxs-lookup"><span data-stu-id="cb690-136">The previous image contains values that have been found to be comfortable on a variety of devices.</span></span>

<span data-ttu-id="cb690-137">**Far Clip**</span><span class="sxs-lookup"><span data-stu-id="cb690-137">**Far Clip**</span></span>

<span data-ttu-id="cb690-138">Il piano di ritaglio lontano è il più lontano, in metri, in cui un oggetto virtuale può essere sulla fotocamera ed essere ancora sottoposto a rendering.</span><span class="sxs-lookup"><span data-stu-id="cb690-138">The far clip plane is the furthest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="cb690-139">Per i dispositivi trasparenti, è consigliabile che questo valore sia relativamente vicino per non superare e troppo lo spazio reale e interrompere le qualità immersive dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="cb690-139">For transparent devices, it is recommended that this value be relatively close as not to overly exceed the real world space and break the application's immersive qualities.</span></span>

<span data-ttu-id="cb690-140">**Cancella flag**</span><span class="sxs-lookup"><span data-stu-id="cb690-140">**Clear Flags**</span></span>

<span data-ttu-id="cb690-141">Il valore dei flag di cancellazione indica come viene cancellata la visualizzazione mentre viene disegnata.</span><span class="sxs-lookup"><span data-stu-id="cb690-141">The clear flags value indicates how the display is cleared as it is drawn.</span></span> <span data-ttu-id="cb690-142">Per le esperienze di realtà virtuale, questo valore è spesso impostato su Skybox.</span><span class="sxs-lookup"><span data-stu-id="cb690-142">For virtual reality experiences, this value is most often set to Skybox.</span></span> <span data-ttu-id="cb690-143">Per gli schermi trasparenti, è consigliabile impostare questa opzione su Colore.</span><span class="sxs-lookup"><span data-stu-id="cb690-143">For transparent displays, it is recommended to set this to Color.</span></span>

<span data-ttu-id="cb690-144">**Colore di sfondo**</span><span class="sxs-lookup"><span data-stu-id="cb690-144">**Background Color**</span></span>

<span data-ttu-id="cb690-145">Se i flag di cancellazione non sono impostati su Skybox, verrà visualizzata la proprietà del colore di sfondo.</span><span class="sxs-lookup"><span data-stu-id="cb690-145">If the clear flags are not set to Skybox, the background color property will be displayed.</span></span>

<span data-ttu-id="cb690-146">**Impostazioni di qualità**</span><span class="sxs-lookup"><span data-stu-id="cb690-146">**Quality Settings**</span></span>

<span data-ttu-id="cb690-147">Il valore delle impostazioni di qualità indica la qualità grafica che Unity deve usare quando esegue il rendering della scena.</span><span class="sxs-lookup"><span data-stu-id="cb690-147">The quality settings value indicates the graphics quality that Unity should use when it renders the scene.</span></span> <span data-ttu-id="cb690-148">Il livello di qualità è un'impostazione a livello di progetto e non è specifico di alcuna fotocamera.</span><span class="sxs-lookup"><span data-stu-id="cb690-148">The quality level is a project level setting and is not specific to any one camera.</span></span> <span data-ttu-id="cb690-149">Per altre informazioni, vedere [l'articolo Sulla](https://docs.unity3d.com/Manual/class-QualitySettings.html) qualità nella documentazione di Unity.</span><span class="sxs-lookup"><span data-stu-id="cb690-149">For more information, please see the [Quality](https://docs.unity3d.com/Manual/class-QualitySettings.html) article in Unity's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb690-150">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cb690-150">See also</span></span>

- [<span data-ttu-id="cb690-151">Documentazione dell'API Camera System</span><span class="sxs-lookup"><span data-stu-id="cb690-151">Camera System API Documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [<span data-ttu-id="cb690-152">Creazione di un provider di impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="cb690-152">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
