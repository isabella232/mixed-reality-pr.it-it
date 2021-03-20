---
title: ProgressIndicator
description: Panoramica dell'indicatore di stato in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: ff047a2185cf93d41163176a07c0f5ef7b745b26
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104686781"
---
# <a name="progress-indicators"></a>Indicatori di stato

![Indicatori di stato](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a>Scena di esempio

Esempi di come usare gli indicatori di stato sono disponibili nella `ProgressIndicatorExamples` scena. In questa scena viene illustrato ogni prefabbricato indicatore di stato incluso nell'SDK.

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator">

## <a name="example-open-update--close-a-progress-indicator"></a>Esempio: apertura, aggiornamento & chiusura di un indicatore di stato

Gli indicatori di stato implementano l' [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interfaccia. Questa interfaccia può essere recuperata da un GameObject usando `GetComponent` .

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

I `IProgressIndicator.OpenAsync()` `IProgressIndicator.CloseAsync()` metodi e restituiscono [attività](xref:System.Threading.Tasks.Task). Si consiglia di attendere queste attività in un metodo asincrono.

Impostare la proprietà dell'indicatore `Progress` su un valore compreso tra 0-1 per aggiornare lo stato di avanzamento visualizzato. Impostarne la `Message` proprietà per aggiornare il messaggio visualizzato. Implementazioni diverse possono visualizzare questo contenuto in modi diversi.

```c#
private async void OpenProgressIndicator()
{
    await indicator.OpenAsync();

    float progress = 0;
    while (progress < 1)
    {
        progress += Time.deltaTime;
        indicator.Message = "Loading...";
        indicator.Progress = progress;
        await Task.Yield();
    }

    await indicator.CloseAsync();
}
```

## <a name="indicator-states"></a>Stati indicatore

La proprietà di un indicatore `State` determina quali operazioni sono valide. La chiamata a un metodo non valido genererà l'indicatore per segnalare un errore e non eseguire alcuna azione.

State | Operazioni valide
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

`AwaitTransitionAsync()` può essere usato per assicurarsi che un indicatore sia completamente aperto o chiuso prima di usarlo.

```c#
private async void ToggleIndicator(IProgressIndicator indicator)
{
    await indicator.AwaitTransitionAsync();

    switch (indicator.State)
    {
        case ProgressIndicatorState.Closed:
            await indicator.OpenAsync();
            break;

        case ProgressIndicatorState.Open:
            await indicator.CloseAsync();
            break;
        }
    }
```
