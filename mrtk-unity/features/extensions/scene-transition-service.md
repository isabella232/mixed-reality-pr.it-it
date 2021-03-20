---
title: SceneTransitionServiceOverview
description: documentazione per la transizione della scena in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, SceneTransition,
ms.openlocfilehash: 546facf53abe38e62176e32e9fb79728e6536d1b
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693168"
---
# <a name="scene-transition-service"></a>Servizio transizione scena

Questa estensione semplifica l'attività di dissolvenza di una scena, la visualizzazione di un indicatore di stato, il caricamento di una scena e la successiva dissolvenza.

Le operazioni di scena sono gestite dal servizio SceneSystem, ma è possibile usare qualsiasi operazione basata su attività per guidare una transizione.

## <a name="enabling-the-extension"></a>Abilitazione dell'estensione

Per abilitare l'estensione, aprire il profilo RegisteredServiceProvider. Fare clic su Registra un nuovo provider di servizi per aggiungere una nuova configurazione. Nel campo tipo di componente selezionare SceneTransitionService. Nel campo profilo di configurazione selezionare il profilo di transizione della scena predefinito incluso nell'estensione.

## <a name="profile-options"></a>Opzioni profilo

### <a name="use-default-progress-indicator"></a>USA indicatore di stato predefinito

Se questa opzione è selezionata, verrà utilizzato il prefabbricato dell'indicatore di stato predefinito quando non viene specificato alcun oggetto indicatore di stato quando si chiama `DoSceneTransition.` se viene specificato un oggetto indicatore di stato, il valore predefinito verrà ignorato.

### <a name="use-fade-color"></a>Usa colore dissolvenza

Se questa opzione è selezionata, il servizio di transizione applicherà una dissolvenza durante la transizione. Questa impostazione può essere modificata in fase di esecuzione tramite la `UseFadeColor` proprietà del servizio.

### <a name="fade-color"></a>Colore dissolvenza

Controlla il colore dell'effetto dissolvenza. Alfa viene ignorato. Questa impostazione può essere modificata in fase di esecuzione prima di una transizione tramite la `FadeColor` proprietà del servizio.

### <a name="fade-targets"></a>Dissolvenza destinazioni

Controlla a quali fotocamere sarà applicato un effetto di dissolvenza. Questa impostazione può essere modificata in fase di esecuzione tramite la `FadeTargets` proprietà del servizio.

Impostazione | Fotocamere di destinazione
--- | --- | ---
Principale | Applica l'effetto dissolvenza alla fotocamera principale.
Interfaccia utente | Applica l'effetto dissolvenza alle fotocamere sul livello dell'interfaccia utente. (Non influisce sull'interfaccia utente sovrapposta)
Tutti | Si applica sia alle fotocamere principali che alle fotocamere dell'interfaccia utente.
Personalizzato | Si applica a un set personalizzato di fotocamere fornite tramite `SetCustomFadeTargetCameras`

### <a name="fade-out-time--fade-in-time"></a>Dissolvenza temporale/dissolvenza nel tempo

Impostazioni predefinite per la durata di una dissolvenza all'immissione o all'uscita da una transizione. Queste impostazioni possono essere modificate in fase di esecuzione tramite le `FadeOutTime` proprietà e del servizio `FadeInTime` .

### <a name="camera-fader-type"></a>Tipo di dissolvenza della fotocamera

`ICameraFader`Classe da usare per l'applicazione di un effetto dissolvenza alle fotocamere. La `CameraFaderQuad` classe predefinita crea un'istanza di un quad con un materiale trasparente davanti alla fotocamera di destinazione vicino al piano di ritaglio. Un altro approccio potrebbe essere quello di usare un sistema di post-effetti.

## <a name="using-the-extension"></a>Uso dell'estensione

Il servizio di transizione viene usato passando le attività che vengono eseguite mentre la fotocamera viene sbiadita.

### <a name="using-scene-system-tasks"></a>Uso delle attività di sistema della scena

Nella maggior parte dei casi si useranno le attività fornite dal servizio SceneSystem:

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

In altri casi è consigliabile eseguire una transizione senza caricare effettivamente una scena:

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

In alternativa, è possibile caricare una scena senza usare il servizio SceneSystem:

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

## <a name="using-the-progress-indicator"></a>Utilizzo dell'indicatore di stato

Un indicatore di stato è qualsiasi elemento che implementa l' `IProgressIndicator` interfaccia. Questo può assumere la forma di una schermata iniziale, un indicatore di caricamento Tagalong 3D o qualsiasi altro elemento che fornisca feedback sull'avanzamento della transizione.

Se `UseDefaultProgressIndicator` viene archiviato nel profilo SceneTransitionService, verrà creata un'istanza di un indicatore di stato all'inizio di una transizione. Per la durata della transizione `Progress` , è possibile accedere alle proprietà e dell'indicatore `Message` tramite i `SetProgressValue` metodi e del servizio `SetProgressMessage` .

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

In alternativa, quando `DoSceneTransition` si chiama è possibile fornire un indicatore di stato personalizzato tramite l' `progressIndicator` argomento facoltativo. Verrà eseguito l'override dell'indicatore di stato predefinito.
