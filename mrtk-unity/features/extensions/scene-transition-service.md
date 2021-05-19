---
title: Panoramica del servizio di transizione della scena
description: documentazione per la transizione di scena in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, SceneTransition,
ms.openlocfilehash: 5ea76b572b3cddc097e8266d3c31f152b63a13aa
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144280"
---
# <a name="scene-transition-service"></a><span data-ttu-id="b1f2d-104">Servizio di transizione della scena</span><span class="sxs-lookup"><span data-stu-id="b1f2d-104">Scene transition service</span></span>

<span data-ttu-id="b1f2d-105">Questa estensione semplifica l'attività di dissolversi di una scena, visualizzare un indicatore di stato, caricare una scena e quindi tornare indietro.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-105">This extension simplifies the business of fading out a scene, displaying a progress indicator, loading a scene, then fading back in.</span></span>

<span data-ttu-id="b1f2d-106">Le operazioni della scena sono guidate dal servizio SceneSystem, ma qualsiasi operazione basata su attività può essere usata per guidare una transizione.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-106">Scene operations are driven by the SceneSystem service, but any Task-based operation can be used to drive a transition.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="b1f2d-107">Abilitazione dell'estensione</span><span class="sxs-lookup"><span data-stu-id="b1f2d-107">Enabling the extension</span></span>

<span data-ttu-id="b1f2d-108">Per abilitare l'estensione, aprire il profilo RegisteredServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="b1f2d-109">Fare clic su Registra un nuovo provider di servizi per aggiungere una nuova configurazione.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-109">Click Register a new Service Provider to add a new configuration.</span></span> <span data-ttu-id="b1f2d-110">Nel campo Tipo di componente selezionare SceneTransitionService.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-110">In the Component Type field, select SceneTransitionService.</span></span> <span data-ttu-id="b1f2d-111">Nel campo Profilo di configurazione selezionare il profilo di transizione della scena predefinito incluso nell'estensione.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-111">In the Configuration Profile field, select the default scene transition profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="b1f2d-112">Opzioni del profilo</span><span class="sxs-lookup"><span data-stu-id="b1f2d-112">Profile options</span></span>

### <a name="use-default-progress-indicator"></a><span data-ttu-id="b1f2d-113">Usare l'indicatore di stato predefinito</span><span class="sxs-lookup"><span data-stu-id="b1f2d-113">Use default progress indicator</span></span>

<span data-ttu-id="b1f2d-114">Se selezionata, il prefab dell'indicatore di stato predefinito verrà usato quando non viene fornito alcun oggetto indicatore di stato quando si chiama Se viene fornito un oggetto indicatore di stato, il valore predefinito `DoSceneTransition.` verrà ignorato.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-114">If checked, the default progress indicator prefab will be used when no progress indicator object is provided when calling `DoSceneTransition.` If a progress indicator object is provided, the default will be ignored.</span></span>

### <a name="use-fade-color"></a><span data-ttu-id="b1f2d-115">Usare il colore di dissolvenza</span><span class="sxs-lookup"><span data-stu-id="b1f2d-115">Use fade color</span></span>

<span data-ttu-id="b1f2d-116">Se l'opzione è selezionata, il servizio di transizione applierà una dissolvenza durante la transizione.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-116">If checked, the transition service will apply a fade during your transition.</span></span> <span data-ttu-id="b1f2d-117">Questa impostazione può essere modificata in fase di esecuzione tramite la proprietà del `UseFadeColor` servizio.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-117">This setting can be changed at runtime via the service's `UseFadeColor` property.</span></span>

### <a name="fade-color"></a><span data-ttu-id="b1f2d-118">Colore dissolvenza</span><span class="sxs-lookup"><span data-stu-id="b1f2d-118">Fade color</span></span>

<span data-ttu-id="b1f2d-119">Controlla il colore dell'effetto di dissolvenza.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-119">Controls the color of the fade effect.</span></span> <span data-ttu-id="b1f2d-120">Alpha viene ignorato.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-120">Alpha is ignored.</span></span> <span data-ttu-id="b1f2d-121">Questa impostazione può essere modificata in fase di esecuzione prima di una transizione tramite la proprietà del `FadeColor` servizio.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-121">This setting can be changed at runtime prior to a transition via the service's `FadeColor` property.</span></span>

### <a name="fade-targets"></a><span data-ttu-id="b1f2d-122">Destinazioni di dissolvenza</span><span class="sxs-lookup"><span data-stu-id="b1f2d-122">Fade targets</span></span>

<span data-ttu-id="b1f2d-123">Controlla le fotocamere a cui verrà applicato un effetto di dissolvenza.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-123">Controls which cameras will have a fade effect applied to them.</span></span> <span data-ttu-id="b1f2d-124">Questa impostazione può essere modificata in fase di esecuzione tramite la proprietà del `FadeTargets` servizio.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-124">This setting can be changed at runtime via the service's `FadeTargets` property.</span></span>

<span data-ttu-id="b1f2d-125">Impostazione</span><span class="sxs-lookup"><span data-stu-id="b1f2d-125">Setting</span></span> | <span data-ttu-id="b1f2d-126">Fotocamere di destinazione</span><span class="sxs-lookup"><span data-stu-id="b1f2d-126">Targeted Cameras</span></span>
--- | --- | ---
<span data-ttu-id="b1f2d-127">Principale</span><span class="sxs-lookup"><span data-stu-id="b1f2d-127">Main</span></span> | <span data-ttu-id="b1f2d-128">Applica l'effetto dissolvenza alla fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-128">Applies fade effect to the main camera.</span></span>
<span data-ttu-id="b1f2d-129">Interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="b1f2d-129">UI</span></span> | <span data-ttu-id="b1f2d-130">Applica l'effetto dissolvenza alle fotocamere nel livello dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-130">Applies fade effect to cameras on the UI layer.</span></span> <span data-ttu-id="b1f2d-131">(Non influisce sull'interfaccia utente di sovrapposizione)</span><span class="sxs-lookup"><span data-stu-id="b1f2d-131">(Does not affect overlay UI)</span></span>
<span data-ttu-id="b1f2d-132">Tutti</span><span class="sxs-lookup"><span data-stu-id="b1f2d-132">All</span></span> | <span data-ttu-id="b1f2d-133">Si applica sia alle fotocamere principali che alle fotocamere dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-133">Applies to both main and UI cameras.</span></span>
<span data-ttu-id="b1f2d-134">Personalizzato</span><span class="sxs-lookup"><span data-stu-id="b1f2d-134">Custom</span></span> | <span data-ttu-id="b1f2d-135">Si applica a un set personalizzato di fotocamere fornite tramite `SetCustomFadeTargetCameras`</span><span class="sxs-lookup"><span data-stu-id="b1f2d-135">Applies to a custom set of cameras provided via `SetCustomFadeTargetCameras`</span></span>

### <a name="fade-out-time--fade-in-time"></a><span data-ttu-id="b1f2d-136">Dissolvenza temporale/dissolvenza nel tempo</span><span class="sxs-lookup"><span data-stu-id="b1f2d-136">Fade out time / fade in time</span></span>

<span data-ttu-id="b1f2d-137">Impostazioni predefinite per la durata di una dissolvenza all'ingresso/uscita da una transizione.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-137">Default settings for the duration of a fade on entering / exiting a transition.</span></span> <span data-ttu-id="b1f2d-138">Queste impostazioni possono essere modificate in fase di esecuzione tramite le proprietà `FadeOutTime` e del `FadeInTime` servizio.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-138">These settings can be changed at runtime via the service's `FadeOutTime` and `FadeInTime` properties.</span></span>

### <a name="camera-fader-type"></a><span data-ttu-id="b1f2d-139">Tipo di fader della fotocamera</span><span class="sxs-lookup"><span data-stu-id="b1f2d-139">Camera fader type</span></span>

<span data-ttu-id="b1f2d-140">Classe `ICameraFader` da usare per applicare un effetto di dissolvenza alle fotocamere.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-140">Which `ICameraFader` class to use for applying a fade effect to cameras.</span></span> <span data-ttu-id="b1f2d-141">La classe predefinita crea un'istanza di un quad con un materiale trasparente davanti alla fotocamera `CameraFaderQuad` di destinazione vicino al piano di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-141">The default `CameraFaderQuad` class instantiates a quad with a transparent material in front of the target camera close to the clip plane.</span></span> <span data-ttu-id="b1f2d-142">Un altro approccio potrebbe consistere nell'usare un sistema di post-effetti.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-142">Another approach might be to use a post effects system.</span></span>

## <a name="using-the-extension"></a><span data-ttu-id="b1f2d-143">Uso dell'estensione</span><span class="sxs-lookup"><span data-stu-id="b1f2d-143">Using the extension</span></span>

<span data-ttu-id="b1f2d-144">È possibile usare il servizio di transizione passando Le attività eseguite mentre la fotocamera è sfumare.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-144">You use the transition service by passing Tasks that are run while the camera is faded out.</span></span>

### <a name="using-scene-system-tasks"></a><span data-ttu-id="b1f2d-145">Uso delle attività di sistema della scena</span><span class="sxs-lookup"><span data-stu-id="b1f2d-145">Using scene system tasks</span></span>

<span data-ttu-id="b1f2d-146">Nella maggior parte dei casi si usano le attività fornite dal servizio SceneSystem:</span><span class="sxs-lookup"><span data-stu-id="b1f2d-146">In most cases you will be using Tasks supplied by the SceneSystem service:</span></span>

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Runs LoadContent task
    // Fades back in
    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}
```

### <a name="using-custom-tasks"></a><span data-ttu-id="b1f2d-147">Uso di attività personalizzate</span><span class="sxs-lookup"><span data-stu-id="b1f2d-147">Using custom tasks</span></span>

<span data-ttu-id="b1f2d-148">In altri casi può essere necessario eseguire una transizione senza caricare effettivamente una scena:</span><span class="sxs-lookup"><span data-stu-id="b1f2d-148">In other cases you may want to perform a transition without actually loading a scene:</span></span>

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Resets scene
    // Fades back in
    await transition.DoSceneTransition(
            () => ResetScene()
        );
}

private async Task ResetScene()
{
    // Go through all enemies in the current scene and move them back to starting positions
}
```

<span data-ttu-id="b1f2d-149">Oppure è possibile caricare una scena senza usare il servizio SceneSystem:</span><span class="sxs-lookup"><span data-stu-id="b1f2d-149">Or you may want to load a scene without using the SceneSystem service:</span></span>

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Loads scene using Unity's scene manager
    // Fades back in
    await transition.DoSceneTransition(
            () => LoadScene("TestScene1")
        );
}

private async Task LoadScene(string sceneName)
{
    AsyncOperation asyncOp = SceneManager.LoadSceneAsync(sceneName, LoadSceneMode.Additive);
    while (!asyncOp.isDone)
    {
        await Task.Yield();
    }
}
```

### <a name="using-multiple-tasks"></a><span data-ttu-id="b1f2d-150">Uso di più attività</span><span class="sxs-lookup"><span data-stu-id="b1f2d-150">Using multiple tasks</span></span>

<span data-ttu-id="b1f2d-151">È anche possibile specificare più attività, che verranno eseguite in ordine:</span><span class="sxs-lookup"><span data-stu-id="b1f2d-151">You can also supply multiple tasks, which will be executed in order:</span></span>

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Sets time scale to 0
    // Fades out audio to 0
    // Loads TestScene1
    // Fades in audio to 1
    // Sets time scale to 1
    // Fades back in
    await transition.DoSceneTransition(
            () => SetTimescale(0f),
            () => FadeAudio(0f, 1f),
            () => sceneSystem.LoadContent("TestScene1"),
            () => FadeAudio(1f, 1f),
            () => SetTimescale(1f)
        );
}

private async Task SetTimescale(float targetTime)
{
    Time.timeScale = targetTime;
    await Task.Yield();
}

private async Task FadeAudio(float targetVolume, float duration)
{
    float startTime = Time.realtimeSinceStartup;
    float startVolume = AudioListener.volume;
    while (Time.realtimeSinceStartup < startTime + duration)
    {
        AudioListener.volume = Mathf.Lerp(startVolume, targetVolume, Time.realtimeSinceStartup - startTime / duration);
        await Task.Yield();
       }
       AudioListener.volume = targetVolume;
}
```

## <a name="using-the-progress-indicator"></a><span data-ttu-id="b1f2d-152">Uso dell'indicatore di stato</span><span class="sxs-lookup"><span data-stu-id="b1f2d-152">Using the progress indicator</span></span>

<span data-ttu-id="b1f2d-153">Un indicatore di stato è qualsiasi elemento che implementa `IProgressIndicator` l'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="b1f2d-153">A progress indicator is anything that implements the `IProgressIndicator` interface.</span></span> <span data-ttu-id="b1f2d-154">Può assumere la forma di una schermata iniziale, un indicatore di caricamento 3D tagalong o qualsiasi altro elemento che fornisce commenti e suggerimenti sullo stato di avanzamento della transizione.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-154">This can take the form of a splash screen, a 3D tagalong loading indicator, or anything else that provides feedback about transition progress.</span></span>

<span data-ttu-id="b1f2d-155">Se `UseDefaultProgressIndicator` è selezionato nel profilo SceneTransitionService, verrà creata un'istanza di un indicatore di stato all'inizio di una transizione.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-155">If `UseDefaultProgressIndicator` is checked in the SceneTransitionService profile, a progress indicator will be instantiated when a transition begins.</span></span> <span data-ttu-id="b1f2d-156">Per la durata della transizione, è possibile accedere alle proprietà e di questo indicatore `Progress` tramite i metodi e del `Message` `SetProgressValue` `SetProgressMessage` servizio.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-156">For the duration of the transition this indicator's `Progress` and `Message` properties can be accessed via that service's `SetProgressValue` and `SetProgressMessage` methods.</span></span>

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    ListenToSceneTransition(sceneSystem, transition);

    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}

private async void ListenToSceneTransition(IMixedRealitySceneSystem sceneSystem, ISceneTransitionService transition)
{
    transition.SetProgressMessage("Starting transition...");

    while (transition.TransitionInProgress)
    {
        if (sceneSystem.SceneOperationInProgress)
        {
            transition.SetProgressMessage("Loading scene...");
            transition.SetProgressValue(sceneSystem.SceneOperationProgress);
        }
        else
        {
            transition.SetProgressMessage("Finished loading scene...");
            transition.SetProgressValue(1);
        }

        await Task.Yield();
    }
}
```

<span data-ttu-id="b1f2d-157">In alternativa, quando si chiama `DoSceneTransition` è possibile fornire un indicatore di stato personalizzato tramite l'argomento `progressIndicator` facoltativo .</span><span class="sxs-lookup"><span data-stu-id="b1f2d-157">Alternatively, when calling `DoSceneTransition` you can supply your own progress indicator via the optional `progressIndicator` argument.</span></span> <span data-ttu-id="b1f2d-158">Verrà eseguito l'override dell'indicatore di stato predefinito.</span><span class="sxs-lookup"><span data-stu-id="b1f2d-158">This will override the default progress indicator.</span></span>
