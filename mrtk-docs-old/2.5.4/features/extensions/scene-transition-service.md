---
title: SceneTransitionServiceOverview
description: documentazione per la transizione di scena in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, SceneTransition,
ms.openlocfilehash: a1db05143808224186757c63a9554d50c72875e4cbb7ab8a4f1ec2c4338f963b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115222772"
---
# <a name="scene-transition-service"></a>Servizio di transizione della scena

Questa estensione semplifica l'attività di dissolversi di una scena, visualizzare un indicatore di stato, caricare una scena e quindi tornare indietro.

Le operazioni della scena sono guidate dal servizio SceneSystem, ma qualsiasi operazione basata su attività può essere usata per guidare una transizione.

## <a name="enabling-the-extension"></a>Abilitazione dell'estensione

Per abilitare l'estensione, aprire il profilo RegisteredServiceProvider. Fare clic su Registra un nuovo provider di servizi per aggiungere una nuova configurazione. Nel campo Tipo di componente selezionare SceneTransitionService. Nel campo Profilo di configurazione selezionare il profilo di transizione della scena predefinito incluso nell'estensione.

## <a name="profile-options"></a>Opzioni del profilo

### <a name="use-default-progress-indicator"></a>Usare l'indicatore di stato predefinito

Se selezionata, il prefab dell'indicatore di stato predefinito verrà usato quando non viene fornito alcun oggetto indicatore di stato quando si chiama Se viene fornito un oggetto indicatore di stato, il valore predefinito `DoSceneTransition.` verrà ignorato.

### <a name="use-fade-color"></a>Usare il colore di dissolvenza

Se l'opzione è selezionata, il servizio di transizione applierà una dissolvenza durante la transizione. Questa impostazione può essere modificata in fase di esecuzione tramite la proprietà del `UseFadeColor` servizio.

### <a name="fade-color"></a>Colore dissolvenza

Controlla il colore dell'effetto dissolvenza. Alpha viene ignorato. Questa impostazione può essere modificata in fase di esecuzione prima di una transizione tramite la proprietà del `FadeColor` servizio.

### <a name="fade-targets"></a>Destinazioni di dissolvenza

Controlla le fotocamere a cui verrà applicato un effetto di dissolvenza. Questa impostazione può essere modificata in fase di esecuzione tramite la proprietà del `FadeTargets` servizio.

Impostazione | Fotocamere di destinazione
--- | --- | ---
Principale | Applica l'effetto dissolvenza alla fotocamera principale.
Interfaccia utente | Applica l'effetto dissolvenza alle fotocamere nel livello dell'interfaccia utente. (Non influisce sull'interfaccia utente di sovrapposizione)
Tutti | Si applica alle fotocamere principali e all'interfaccia utente.
Personalizzato | Si applica a un set personalizzato di fotocamere fornite tramite `SetCustomFadeTargetCameras`

### <a name="fade-out-time--fade-in-time"></a>Dissolvenza temporale/dissolvenza nel tempo

Impostazioni predefinite per la durata di una dissolvenza all'ingresso/uscita da una transizione. Queste impostazioni possono essere modificate in fase di esecuzione tramite le proprietà `FadeOutTime` e del `FadeInTime` servizio.

### <a name="camera-fader-type"></a>Tipo di camera fader

Classe `ICameraFader` da usare per applicare un effetto di dissolvenza alle fotocamere. La classe predefinita crea un'istanza di un quad con un materiale trasparente davanti alla fotocamera `CameraFaderQuad` di destinazione vicino al piano di ritaglio. Un altro approccio potrebbe consistere nell'usare un sistema di post-effetti.

## <a name="using-the-extension"></a>Uso dell'estensione

È possibile usare il servizio di transizione passando Le attività eseguite mentre la fotocamera è sfumare.

### <a name="using-scene-system-tasks"></a>Uso delle attività di sistema della scena

Nella maggior parte dei casi si usano le attività fornite dal servizio SceneSystem:

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

### <a name="using-custom-tasks"></a>Uso di attività personalizzate

In altri casi può essere necessario eseguire una transizione senza caricare effettivamente una scena:

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

Oppure è possibile caricare una scena senza usare il servizio SceneSystem:

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

### <a name="using-multiple-tasks"></a>Uso di più attività

È anche possibile specificare più attività, che verranno eseguite nell'ordine seguente:

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

## <a name="using-the-progress-indicator"></a>Uso dell'indicatore di stato

Un indicatore di stato è qualsiasi elemento che implementa `IProgressIndicator` l'interfaccia . Può assumere la forma di una schermata iniziale, di un indicatore di caricamento 3D tagalong o di qualsiasi altro elemento che fornisce feedback sullo stato di avanzamento della transizione.

Se `UseDefaultProgressIndicator` è selezionata nel profilo SceneTransitionService, all'inizio di una transizione verrà creata un'istanza di un indicatore di stato. Per la durata della transizione è possibile accedere alle proprietà e di questo indicatore `Progress` tramite i metodi e del `Message` `SetProgressValue` `SetProgressMessage` servizio.

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

In alternativa, quando si chiama `DoSceneTransition` è possibile fornire un indicatore di stato personalizzato tramite l'argomento `progressIndicator` facoltativo. Verrà eseguito l'override dell'indicatore di stato predefinito.
