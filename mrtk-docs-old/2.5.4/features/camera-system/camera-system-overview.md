---
title: CameraSystemOverview
description: Pagina di destinazione per il sistema della fotocamera in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, fotocamera,
ms.openlocfilehash: e6fbc9a5d67c0069e1afd61089c9d2a0e0d1cecb
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782958"
---
# <a name="camera-system"></a><span data-ttu-id="552b0-104">Sistema fotocamera</span><span class="sxs-lookup"><span data-stu-id="552b0-104">Camera system</span></span>

<span data-ttu-id="552b0-105">Il sistema della fotocamera consente a Microsoft Mixed Reality Toolkit di configurare e ottimizzare la fotocamera dell'applicazione per l'uso in applicazioni con realtà mista.</span><span class="sxs-lookup"><span data-stu-id="552b0-105">The camera system enables the Microsoft Mixed Reality Toolkit to configure and optimize the application's camera for use in mixed reality applications.</span></span> <span data-ttu-id="552b0-106">Utilizzando il sistema di fotocamera, le applicazioni possono essere scritte in modo da supportare sia i dispositivi opachi (ad esempio, la realtà virtuale) che quelli trasparenti (ad esempio, Microsoft HoloLens) senza dover scrivere codice per distinguere tra e adattarsi a ogni tipo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="552b0-106">Using the camera system, applications can be written to support both opaque (ex: virtual reality) and transparent (ex: Microsoft HoloLens) devices without needing to write code to distinguish between, and accommodate for, each type of display.</span></span>

## <a name="enabling-the-camera-system"></a><span data-ttu-id="552b0-107">Abilitazione del sistema della fotocamera</span><span class="sxs-lookup"><span data-stu-id="552b0-107">Enabling the camera system</span></span>

<span data-ttu-id="552b0-108">Il sistema della fotocamera è gestito dall'oggetto MixedRealityToolkit (o da un altro componente di registrazione del servizio).</span><span class="sxs-lookup"><span data-stu-id="552b0-108">The Camera System is managed by the MixedRealityToolkit object (or another service registrar component).</span></span>

<span data-ttu-id="552b0-109">I passaggi seguenti presuppongono l'uso dell'oggetto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="552b0-109">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="552b0-110">I passaggi necessari per altri registrar di servizi potrebbero essere diversi.</span><span class="sxs-lookup"><span data-stu-id="552b0-110">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="552b0-111">Selezionare l'oggetto MixedRealityToolkit nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="552b0-111">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Gerarchia della scena configurata MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="552b0-113">Passare al pannello di controllo nella sezione sistema della fotocamera e verificare che sia selezionata l'opzione **Abilita sistema fotocamera** .</span><span class="sxs-lookup"><span data-stu-id="552b0-113">Navigate the Inspector panel to the camera system section and ensure that **Enable Camera System** is checked.</span></span>

    ![Abilitazione del sistema della fotocamera](../images/camera-system/EnableCameraSystem.png)

3. <span data-ttu-id="552b0-115">Selezionare l'implementazione del sistema della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="552b0-115">Select the camera system implementation.</span></span> <span data-ttu-id="552b0-116">L'implementazione della classe predefinita fornita da MRTK è `MixedRealityCameraSystem` .</span><span class="sxs-lookup"><span data-stu-id="552b0-116">The default class implementation provided by the MRTK is the `MixedRealityCameraSystem`.</span></span>

    ![Selezionare l'implementazione del sistema della fotocamera](../images/camera-system/SelectCameraSystemType.png)

4. <span data-ttu-id="552b0-118">Selezionare il profilo di configurazione desiderato</span><span class="sxs-lookup"><span data-stu-id="552b0-118">Select the desired configuration profile</span></span>

    ![Seleziona profilo di sistema della fotocamera](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a><span data-ttu-id="552b0-120">Configurazione del sistema della fotocamera</span><span class="sxs-lookup"><span data-stu-id="552b0-120">Configuring the camera system</span></span>

### <a name="settings-providers"></a><span data-ttu-id="552b0-121">Provider di impostazioni</span><span class="sxs-lookup"><span data-stu-id="552b0-121">Settings providers</span></span>

![Provider di impostazioni della fotocamera](../images/camera-system/CameraSettingsProviders.png)

<span data-ttu-id="552b0-123">I provider di impostazioni della fotocamera abilitano la configurazione specifica della piattaforma della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="552b0-123">Camera setting providers enable platform specific configuration of the camera.</span></span> <span data-ttu-id="552b0-124">Queste impostazioni possono includere passaggi di configurazione personalizzati e/o componenti.</span><span class="sxs-lookup"><span data-stu-id="552b0-124">These settings may include custom configuration steps and/or components.</span></span>

<span data-ttu-id="552b0-125">È possibile aggiungere i provider facendo clic sul pulsante **Aggiungi provider impostazioni fotocamera** .</span><span class="sxs-lookup"><span data-stu-id="552b0-125">Providers can be added by clicking the **Add Camera Settings Provider** button.</span></span> <span data-ttu-id="552b0-126">È possibile rimuoverli facendo clic sul **-** pulsante a destra del nome del provider.</span><span class="sxs-lookup"><span data-stu-id="552b0-126">They can be removed by clicking the **-** button to the right of the provider's name.</span></span>

> [!Note]
> <span data-ttu-id="552b0-127">Non tutte le piattaforme richiedono un provider di impostazioni della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="552b0-127">Not all platforms will require a camera settings provider.</span></span> <span data-ttu-id="552b0-128">Se non sono presenti provider compatibili con la piattaforma in cui è in esecuzione l'applicazione, Microsoft Mixed Reality Toolkit applica le impostazioni predefinite di base.</span><span class="sxs-lookup"><span data-stu-id="552b0-128">If there are no providers that are compatible with the platform on which the application is running, the Microsoft Mixed Reality Toolkit will apply basic defaults.</span></span>

### <a name="display-settings"></a><span data-ttu-id="552b0-129">Impostazioni schermo</span><span class="sxs-lookup"><span data-stu-id="552b0-129">Display settings</span></span>

![Impostazioni di visualizzazione della fotocamera](../images/camera-system/CameraDisplaySettings.png)

<span data-ttu-id="552b0-131">Le impostazioni di visualizzazione vengono specificate per le visualizzazioni opache (ad esempio, realtà virtuale) e trasparenti (ad esempio: Microsoft HoloLens).</span><span class="sxs-lookup"><span data-stu-id="552b0-131">Display settings are specified for both opaque (ex: Virtual Reality) and transparent (ex: Microsoft HoloLens) displays.</span></span> <span data-ttu-id="552b0-132">La fotocamera viene configurata, in fase di esecuzione, usando queste impostazioni.</span><span class="sxs-lookup"><span data-stu-id="552b0-132">The camera is configured, at run time, using these settings.</span></span>

<span data-ttu-id="552b0-133">**Near clip**</span><span class="sxs-lookup"><span data-stu-id="552b0-133">**Near Clip**</span></span>

<span data-ttu-id="552b0-134">Il piano di ritaglio vicino è il più vicino, in metri, che un oggetto virtuale può essere alla fotocamera ed è ancora sottoposto a rendering.</span><span class="sxs-lookup"><span data-stu-id="552b0-134">The near clip plane is the closest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="552b0-135">Per ottenere la massima comodità per gli utenti, è consigliabile fare in modo che questo valore sia maggiore di zero.</span><span class="sxs-lookup"><span data-stu-id="552b0-135">For greatest user comfort, it is recommended to make this value greater than zero.</span></span> <span data-ttu-id="552b0-136">Nell'immagine precedente sono contenuti i valori che sono stati rilevati per essere comodi in un'ampia gamma di dispositivi.</span><span class="sxs-lookup"><span data-stu-id="552b0-136">The previous image contains values that have been found to be comfortable on a variety of devices.</span></span>

<span data-ttu-id="552b0-137">**Clip lontano**</span><span class="sxs-lookup"><span data-stu-id="552b0-137">**Far Clip**</span></span>

<span data-ttu-id="552b0-138">Il piano di ritaglio è il più lontano, in metri, che un oggetto virtuale può essere alla fotocamera ed è ancora sottoposto a rendering.</span><span class="sxs-lookup"><span data-stu-id="552b0-138">The far clip plane is the furthest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="552b0-139">Per i dispositivi trasparenti, è consigliabile che questo valore sia relativamente vicino a non superare eccessivamente lo spazio reale e suddividere le qualità immersive dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="552b0-139">For transparent devices, it is recommended that this value be relatively close as not to overly exceed the real world space and break the application's immersive qualities.</span></span>

<span data-ttu-id="552b0-140">**Cancella flag**</span><span class="sxs-lookup"><span data-stu-id="552b0-140">**Clear Flags**</span></span>

<span data-ttu-id="552b0-141">Il valore Clear Flags indica il modo in cui la visualizzazione viene cancellata mentre viene disegnata.</span><span class="sxs-lookup"><span data-stu-id="552b0-141">The clear flags value indicates how the display is cleared as it is drawn.</span></span> <span data-ttu-id="552b0-142">Per le esperienze di realtà virtuale, questo valore viene spesso impostato su skybox.</span><span class="sxs-lookup"><span data-stu-id="552b0-142">For virtual reality experiences, this value is most often set to Skybox.</span></span> <span data-ttu-id="552b0-143">Per le visualizzazioni trasparenti, è consigliabile impostare questa proprietà su Color.</span><span class="sxs-lookup"><span data-stu-id="552b0-143">For transparent displays, it is recommended to set this to Color.</span></span>

<span data-ttu-id="552b0-144">**Colore di sfondo**</span><span class="sxs-lookup"><span data-stu-id="552b0-144">**Background Color**</span></span>

<span data-ttu-id="552b0-145">Se i flag Clear non sono impostati su SKYBOX, verrà visualizzata la proprietà del colore di sfondo.</span><span class="sxs-lookup"><span data-stu-id="552b0-145">If the clear flags are not set to Skybox, the background color property will be displayed.</span></span>

<span data-ttu-id="552b0-146">**Impostazioni qualità**</span><span class="sxs-lookup"><span data-stu-id="552b0-146">**Quality Settings**</span></span>

<span data-ttu-id="552b0-147">Il valore delle impostazioni di qualità indica la qualità grafica che Unity deve usare quando esegue il rendering della scena.</span><span class="sxs-lookup"><span data-stu-id="552b0-147">The quality settings value indicates the graphics quality that Unity should use when it renders the scene.</span></span> <span data-ttu-id="552b0-148">Il livello di qualità è un'impostazione a livello di progetto e non è specifico di una fotocamera.</span><span class="sxs-lookup"><span data-stu-id="552b0-148">The quality level is a project level setting and is not specific to any one camera.</span></span> <span data-ttu-id="552b0-149">Per altre informazioni, vedere l'articolo relativo alla [qualità](https://docs.unity3d.com/Manual/class-QualitySettings.html) nella documentazione di Unity.</span><span class="sxs-lookup"><span data-stu-id="552b0-149">For more information, please see the [Quality](https://docs.unity3d.com/Manual/class-QualitySettings.html) article in Unity's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="552b0-150">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="552b0-150">See also</span></span>

- [<span data-ttu-id="552b0-151">Documentazione dell'API di sistema per fotocamere</span><span class="sxs-lookup"><span data-stu-id="552b0-151">Camera System API Documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [<span data-ttu-id="552b0-152">Creazione di un provider di impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="552b0-152">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
