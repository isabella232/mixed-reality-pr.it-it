---
title: ProgressIndicator
description: Panoramica dell'indicatore di stato in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 9170a376812901cb063038a5513d4fbf79ad0a28
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110124"
---
# <a name="progress-indicators"></a>Indicatori di stato

![Indicatori di stato](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a>Scena di esempio

Esempi di come usare gli indicatori di stato sono disponibili nella `ProgressIndicatorExamples` scena. Questa scena illustra ognuno dei prefab dell'indicatore di stato inclusi nell'SDK. Illustra anche come usare gli indicatori di stato in combinazione con alcune attività asincrone comuni, ad esempio il caricamento della scena.

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a>Esempio: Aprire, aggiornare & chiudere un indicatore di stato

Gli indicatori di stato implementano [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) l'interfaccia . Questa interfaccia può essere recuperata da un GameObject usando `GetComponent` .

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

I `IProgressIndicator.OpenAsync()` metodi e `IProgressIndicator.CloseAsync()` restituiscono [Attività](xref:System.Threading.Tasks.Task). È consigliabile attendere queste attività in un metodo asincrono.

I prefab predefiniti dell'indicatore di stato di MRTK devono essere inattivi quando vengono posizionati in una scena. Quando i `IProgressIndicator.OpenAsync()` relativi metodi vengono chiamati, gli indicatori di stato attivano e disattivano automaticamente gli oggetti di gioco. Questo modello non è un requisito dell'interfaccia IProgressIndicator.

Impostare la proprietà `Progress` dell'indicatore su un valore compreso tra 0 e 1 per aggiornarne lo stato visualizzato. Impostare la `Message` proprietà per aggiornare il messaggio visualizzato. Implementazioni diverse possono visualizzare questo contenuto in modi diversi.

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

## <a name="indicator-states"></a>Stati dell'indicatore

La proprietà di un `State` indicatore determina le operazioni valide. Se si chiama un metodo non valido, l'indicatore segnala in genere un errore e non esegue alcuna azione.

Stato | Operazioni valide
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
