---
title: ProgressIndicator
description: Panoramica dell'indicatore di stato in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 252bd3d406e797ed219fade0438869e5253d5e5f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689106"
---
# <a name="progress-indicators"></a><span data-ttu-id="9fff8-104">Indicatori di stato</span><span class="sxs-lookup"><span data-stu-id="9fff8-104">Progress Indicators</span></span>

![Indicatori di stato](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a><span data-ttu-id="9fff8-106">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="9fff8-106">Example scene</span></span>

<span data-ttu-id="9fff8-107">Esempi di come usare gli indicatori di stato sono disponibili nella `ProgressIndicatorExamples` scena.</span><span class="sxs-lookup"><span data-stu-id="9fff8-107">Examples of how to use progress indicators can be found in the `ProgressIndicatorExamples` scene.</span></span> <span data-ttu-id="9fff8-108">In questa scena viene illustrato ogni prefabbricato indicatore di stato incluso nell'SDK.</span><span class="sxs-lookup"><span data-stu-id="9fff8-108">This scene demonstrates each of the progress indicator prefabs included in the SDK.</span></span>

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a><span data-ttu-id="9fff8-109">Esempio: apertura, aggiornamento & chiusura di un indicatore di stato</span><span class="sxs-lookup"><span data-stu-id="9fff8-109">Example: Open, update & close a progress indicator</span></span>

<span data-ttu-id="9fff8-110">Gli indicatori di stato implementano l' [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="9fff8-110">Progress indicators implement the [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span></span> <span data-ttu-id="9fff8-111">Questa interfaccia può essere recuperata da un GameObject usando `GetComponent` .</span><span class="sxs-lookup"><span data-stu-id="9fff8-111">This interface can be retrieved from a GameObject using `GetComponent`.</span></span>

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

<span data-ttu-id="9fff8-112">I `IProgressIndicator.OpenAsync()` `IProgressIndicator.CloseAsync()` metodi e restituiscono [attività](xref:System.Threading.Tasks.Task).</span><span class="sxs-lookup"><span data-stu-id="9fff8-112">The `IProgressIndicator.OpenAsync()` and `IProgressIndicator.CloseAsync()` methods return [Tasks](xref:System.Threading.Tasks.Task).</span></span> <span data-ttu-id="9fff8-113">Si consiglia di attendere queste attività in un metodo asincrono.</span><span class="sxs-lookup"><span data-stu-id="9fff8-113">We recommend awaiting these Tasks in an async method.</span></span>

<span data-ttu-id="9fff8-114">Impostare la proprietà dell'indicatore `Progress` su un valore compreso tra 0-1 per aggiornare lo stato di avanzamento visualizzato.</span><span class="sxs-lookup"><span data-stu-id="9fff8-114">Set the indicator's `Progress` property to a value from 0-1 to update its displayed progress.</span></span> <span data-ttu-id="9fff8-115">Impostarne la `Message` proprietà per aggiornare il messaggio visualizzato.</span><span class="sxs-lookup"><span data-stu-id="9fff8-115">Set its `Message` property to update its displayed message.</span></span> <span data-ttu-id="9fff8-116">Implementazioni diverse possono visualizzare questo contenuto in modi diversi.</span><span class="sxs-lookup"><span data-stu-id="9fff8-116">Different implementations may display this content in different ways.</span></span>

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

## <a name="indicator-states"></a><span data-ttu-id="9fff8-117">Stati indicatore</span><span class="sxs-lookup"><span data-stu-id="9fff8-117">Indicator states</span></span>

<span data-ttu-id="9fff8-118">La proprietà di un indicatore `State` determina quali operazioni sono valide.</span><span class="sxs-lookup"><span data-stu-id="9fff8-118">An indicator's `State` property determines which operations are valid.</span></span> <span data-ttu-id="9fff8-119">La chiamata a un metodo non valido genererà l'indicatore per segnalare un errore e non eseguire alcuna azione.</span><span class="sxs-lookup"><span data-stu-id="9fff8-119">Calling an invalid method will typically cause the indicator to report an error and take no action.</span></span>

<span data-ttu-id="9fff8-120">State</span><span class="sxs-lookup"><span data-stu-id="9fff8-120">State</span></span> | <span data-ttu-id="9fff8-121">Operazioni valide</span><span class="sxs-lookup"><span data-stu-id="9fff8-121">Valid Operations</span></span>
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

<span data-ttu-id="9fff8-122">`AwaitTransitionAsync()` può essere usato per assicurarsi che un indicatore sia completamente aperto o chiuso prima di usarlo.</span><span class="sxs-lookup"><span data-stu-id="9fff8-122">`AwaitTransitionAsync()` can be used to be sure an indicator is fully opened or closed before using it.</span></span>

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
