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
# <a name="progress-indicators"></a><span data-ttu-id="7688c-104">Indicatori di stato</span><span class="sxs-lookup"><span data-stu-id="7688c-104">Progress Indicators</span></span>

![Indicatori di stato](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a><span data-ttu-id="7688c-106">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="7688c-106">Example scene</span></span>

<span data-ttu-id="7688c-107">Esempi di come usare gli indicatori di stato sono disponibili nella `ProgressIndicatorExamples` scena.</span><span class="sxs-lookup"><span data-stu-id="7688c-107">Examples of how to use progress indicators can be found in the `ProgressIndicatorExamples` scene.</span></span> <span data-ttu-id="7688c-108">Questa scena illustra ognuno dei prefab dell'indicatore di stato inclusi nell'SDK.</span><span class="sxs-lookup"><span data-stu-id="7688c-108">This scene demonstrates each of the progress indicator prefabs included in the SDK.</span></span> <span data-ttu-id="7688c-109">Illustra anche come usare gli indicatori di stato in combinazione con alcune attività asincrone comuni, ad esempio il caricamento della scena.</span><span class="sxs-lookup"><span data-stu-id="7688c-109">It also demonstrates how to use progress indicators in conjunction with some common asynchronous tasks like scene loading.</span></span>

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a><span data-ttu-id="7688c-110">Esempio: Aprire, aggiornare & chiudere un indicatore di stato</span><span class="sxs-lookup"><span data-stu-id="7688c-110">Example: Open, update & close a progress indicator</span></span>

<span data-ttu-id="7688c-111">Gli indicatori di stato implementano [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) l'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="7688c-111">Progress indicators implement the [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span></span> <span data-ttu-id="7688c-112">Questa interfaccia può essere recuperata da un GameObject usando `GetComponent` .</span><span class="sxs-lookup"><span data-stu-id="7688c-112">This interface can be retrieved from a GameObject using `GetComponent`.</span></span>

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

<span data-ttu-id="7688c-113">I `IProgressIndicator.OpenAsync()` metodi e `IProgressIndicator.CloseAsync()` restituiscono [Attività](xref:System.Threading.Tasks.Task).</span><span class="sxs-lookup"><span data-stu-id="7688c-113">The `IProgressIndicator.OpenAsync()` and `IProgressIndicator.CloseAsync()` methods return [Tasks](xref:System.Threading.Tasks.Task).</span></span> <span data-ttu-id="7688c-114">È consigliabile attendere queste attività in un metodo asincrono.</span><span class="sxs-lookup"><span data-stu-id="7688c-114">We recommend awaiting these Tasks in an async method.</span></span>

<span data-ttu-id="7688c-115">I prefab predefiniti dell'indicatore di stato di MRTK devono essere inattivi quando vengono posizionati in una scena.</span><span class="sxs-lookup"><span data-stu-id="7688c-115">The MRTK's default progress indicator prefabs should be inactive when placed in a scene.</span></span> <span data-ttu-id="7688c-116">Quando i `IProgressIndicator.OpenAsync()` relativi metodi vengono chiamati, gli indicatori di stato attivano e disattivano automaticamente gli oggetti di gioco.</span><span class="sxs-lookup"><span data-stu-id="7688c-116">When their `IProgressIndicator.OpenAsync()` methods are called the progress indicators will activate and deactivate their gameobjects automatically.</span></span> <span data-ttu-id="7688c-117">Questo modello non è un requisito dell'interfaccia IProgressIndicator.</span><span class="sxs-lookup"><span data-stu-id="7688c-117">(This pattern is not a requirement of the IProgressIndicator interface.)</span></span>

<span data-ttu-id="7688c-118">Impostare la proprietà `Progress` dell'indicatore su un valore compreso tra 0 e 1 per aggiornarne lo stato visualizzato.</span><span class="sxs-lookup"><span data-stu-id="7688c-118">Set the indicator's `Progress` property to a value from 0-1 to update its displayed progress.</span></span> <span data-ttu-id="7688c-119">Impostare la `Message` proprietà per aggiornare il messaggio visualizzato.</span><span class="sxs-lookup"><span data-stu-id="7688c-119">Set its `Message` property to update its displayed message.</span></span> <span data-ttu-id="7688c-120">Implementazioni diverse possono visualizzare questo contenuto in modi diversi.</span><span class="sxs-lookup"><span data-stu-id="7688c-120">Different implementations may display this content in different ways.</span></span>

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

## <a name="indicator-states"></a><span data-ttu-id="7688c-121">Stati dell'indicatore</span><span class="sxs-lookup"><span data-stu-id="7688c-121">Indicator states</span></span>

<span data-ttu-id="7688c-122">La proprietà di un `State` indicatore determina le operazioni valide.</span><span class="sxs-lookup"><span data-stu-id="7688c-122">An indicator's `State` property determines which operations are valid.</span></span> <span data-ttu-id="7688c-123">Se si chiama un metodo non valido, l'indicatore segnala in genere un errore e non esegue alcuna azione.</span><span class="sxs-lookup"><span data-stu-id="7688c-123">Calling an invalid method will typically cause the indicator to report an error and take no action.</span></span>

<span data-ttu-id="7688c-124">Stato</span><span class="sxs-lookup"><span data-stu-id="7688c-124">State</span></span> | <span data-ttu-id="7688c-125">Operazioni valide</span><span class="sxs-lookup"><span data-stu-id="7688c-125">Valid Operations</span></span>
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

<span data-ttu-id="7688c-126">`AwaitTransitionAsync()` può essere usato per assicurarsi che un indicatore sia completamente aperto o chiuso prima di usarlo.</span><span class="sxs-lookup"><span data-stu-id="7688c-126">`AwaitTransitionAsync()` can be used to be sure an indicator is fully opened or closed before using it.</span></span>

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
