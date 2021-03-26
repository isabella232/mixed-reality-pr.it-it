---
title: Sguardo fisso
description: Docummentation sui tipi di sguardo in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sguardo,
ms.openlocfilehash: 7587a89b5784b4e1c2a0d8a858ffa0e84f1e86af
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550941"
---
# <a name="gaze"></a><span data-ttu-id="75b80-104">Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="75b80-104">Gaze</span></span>

<span data-ttu-id="75b80-105">[Sguardi](/windows/mixed-reality/gaze) è un tipo di input che interagisce con il mondo in base alla posizione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="75b80-105">[Gaze](/windows/mixed-reality/gaze) is a form of input that interacts with the world based on where the user is looking.</span></span> <span data-ttu-id="75b80-106">Lo sguardo esiste in due diverse varianti</span><span class="sxs-lookup"><span data-stu-id="75b80-106">Gaze exists in two different flavors</span></span>

## <a name="head-gaze"></a><span data-ttu-id="75b80-107">Puntamento con la testa</span><span class="sxs-lookup"><span data-stu-id="75b80-107">Head gaze</span></span>

<span data-ttu-id="75b80-108">Questo tipo di sguardi è basato sulla direzione che la testa/fotocamera sta osservando.</span><span class="sxs-lookup"><span data-stu-id="75b80-108">This type of gaze is based on the direction that the head/camera is looking at.</span></span> <span data-ttu-id="75b80-109">Il punto di vista del controllo è attivo nei sistemi che non supportano gli sguardi, oppure nei casi in cui l'hardware può supportare gli sguardi, ma il set di [autorizzazioni e l'installazione](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) corretti non sono stati eseguiti.</span><span class="sxs-lookup"><span data-stu-id="75b80-109">Head gaze is active on systems that don't support eye gaze, or in cases where the hardware may support eye gaze, but the right set of [permissions and setup](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) has not been performed.</span></span>

<span data-ttu-id="75b80-110">Lo sguardo a capo è in genere associato alle interazioni di stile HoloLens 1 che coinvolgono l'oggetto, inserendolo al centro del frame olografico e quindi eseguendo il movimento del rubinetto d'aria.</span><span class="sxs-lookup"><span data-stu-id="75b80-110">Head gaze is usually associated with HoloLens 1 style interactions involving looking at object by placing it in the center of the Holographic Frame and then performing the air tap gesture.</span></span>

## <a name="eye-gaze"></a><span data-ttu-id="75b80-111">Tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="75b80-111">Eye gaze</span></span>

<span data-ttu-id="75b80-112">Questo tipo di sguardi è basato sulla posizione in cui si trovano gli occhi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="75b80-112">This type of gaze is based on where the user's eyes are looking.</span></span> <span data-ttu-id="75b80-113">Eye sguardi è presente solo nei sistemi che supportano il rilevamento degli occhi.</span><span class="sxs-lookup"><span data-stu-id="75b80-113">Eye gaze is only present on systems that support eye tracking.</span></span> <span data-ttu-id="75b80-114">Per informazioni dettagliate su come usare gli occhi, vedere la [documentazione relativa a Eye Tracking](eye-tracking/eye-tracking-main.md) .</span><span class="sxs-lookup"><span data-stu-id="75b80-114">See the [eye tracking documentation](eye-tracking/eye-tracking-main.md) for more details on how to use eye gaze.</span></span>

## <a name="gazeprovider"></a><span data-ttu-id="75b80-115">GazeProvider</span><span class="sxs-lookup"><span data-stu-id="75b80-115">GazeProvider</span></span>

<span data-ttu-id="75b80-116">La funzionalità di sguardi (sia Head che Eye) viene fornita da [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider).</span><span class="sxs-lookup"><span data-stu-id="75b80-116">Gaze functionality (both head and eye) is provided by the [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider).</span></span> <span data-ttu-id="75b80-117">Questo provider può essere configurato nella sezione *puntatore* del profilo di sistema di input:</span><span class="sxs-lookup"><span data-stu-id="75b80-117">This provider can be configured in the *Pointer* section of the input system profile:</span></span>

![EntryPoint configurazione sguardo](../images/input/GazeConfigurationEntrypoint.png)

<span data-ttu-id="75b80-119">Analogamente ad altre origini di input, il provider di sguardi interagisce con gli oggetti nella scena tramite l'uso di un puntatore [(vedere questo documento per informazioni sui puntatori)](../../architecture/controllers-pointers-and-focus.md).</span><span class="sxs-lookup"><span data-stu-id="75b80-119">Like other sources of input, the gaze provider interacts with objects in the scene through use of a pointer [(see this document for information on pointers)](../../architecture/controllers-pointers-and-focus.md).</span></span>
<span data-ttu-id="75b80-120">Nel caso del provider di sguardi, il relativo puntatore viene implementato tramite `InternalGazePointer` e non è configurato tramite un profilo.</span><span class="sxs-lookup"><span data-stu-id="75b80-120">In the case of the gaze provider, its pointer is implemented via `InternalGazePointer` and is not configured through a profile.</span></span>

<span data-ttu-id="75b80-121">È possibile sostituire il GazeProvider di magazzino con un'implementazione alternativa modificando il *tipo di provider di sguardi* per fare riferimento a una classe diversa che implementa [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) e [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).</span><span class="sxs-lookup"><span data-stu-id="75b80-121">It is possible to replace the stock GazeProvider with an alternate implementation by changing *Gaze Provider Type* to reference a different class that implements [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) and [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).</span></span>
<span data-ttu-id="75b80-122">È in genere consigliabile usare il GazeProvider di magazzino (e i problemi di archiviazione durante la ricerca dei bug) perché la riimplementazione di GazeProvider non è semplice.</span><span class="sxs-lookup"><span data-stu-id="75b80-122">It's generally recommended to use the stock GazeProvider (and filing issues in when finding bugs) as re-implementing the GazeProvider is non-trivial.</span></span>

### <a name="alternative-platform-provided-gaze-poses"></a><span data-ttu-id="75b80-123">Pose mirate della piattaforma alternative</span><span class="sxs-lookup"><span data-stu-id="75b80-123">Alternative platform-provided gaze poses</span></span>

<span data-ttu-id="75b80-124">Per impostazione predefinita, MRTK GazeProvider usa il centro del frame della fotocamera come origine dello sguardo.</span><span class="sxs-lookup"><span data-stu-id="75b80-124">By default, the MRTK GazeProvider uses the center of the camera's frame as the gaze origin.</span></span> <span data-ttu-id="75b80-125">Alcune piattaforme, ad esempio la realtà mista di Windows in HoloLens 2, forniscono uno sguardo definito in modo alternativo.</span><span class="sxs-lookup"><span data-stu-id="75b80-125">Some platforms, like Windows Mixed Reality on HoloLens 2, provide an alternatively defined gaze pose.</span></span> <span data-ttu-id="75b80-126">Questa operazione viene gestita tramite l' `Use Head Gaze Override` impostazione nelle impostazioni di sguardi.</span><span class="sxs-lookup"><span data-stu-id="75b80-126">This is managed via the `Use Head Gaze Override` setting in the gaze settings.</span></span> <span data-ttu-id="75b80-127">Quando è abilitata, verrà usato l'override di sguardi alternativi.</span><span class="sxs-lookup"><span data-stu-id="75b80-127">When enabled, the alternative gaze override will be used.</span></span> <span data-ttu-id="75b80-128">Se questa opzione è disabilitata, verrà utilizzata l'origine di frame Center predefinita.</span><span class="sxs-lookup"><span data-stu-id="75b80-128">When disabled, the default frame center origin will be used.</span></span> <span data-ttu-id="75b80-129">In particolare, per HoloLens 2, l'angolo dello sguardo verrà generato da diversi gradi per tenere conto del comfort degli utenti nell'uso della loro testa per la destinazione.</span><span class="sxs-lookup"><span data-stu-id="75b80-129">Specifically, for HoloLens 2, the gaze angle will be raised several degrees to account for user comfort in using their head for targeting.</span></span>

## <a name="usage"></a><span data-ttu-id="75b80-130">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="75b80-130">Usage</span></span>

### <a name="how-get-the-current-gaze-target"></a><span data-ttu-id="75b80-131">Come ottenere la destinazione dello sguardo corrente</span><span class="sxs-lookup"><span data-stu-id="75b80-131">How get the current gaze target</span></span>

<span data-ttu-id="75b80-132">In questo esempio viene illustrato come ottenere l'oggetto Game corrente di destinazione dello sguardo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="75b80-132">This sample shows how to get the current game object that is targeted by the user gaze.</span></span>

```c#
void LogCurrentGazeTarget()
{
    if (CoreServices.InputSystem.GazeProvider.GazeTarget)
    {
        Debug.Log("User gaze is currently over game object: "
            + CoreServices.InputSystem.GazeProvider.GazeTarget)
    }
}
```

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a><span data-ttu-id="75b80-133">Come ottenere la direzione e l'origine dello sguardo corrente</span><span class="sxs-lookup"><span data-stu-id="75b80-133">How to get the current gaze direction and origin</span></span>

<span data-ttu-id="75b80-134">In questo esempio viene illustrato come ottenere l'oggetto Vector3 che rappresenta la direzione dello sguardo dell'utente e l'origine (il punto da cui la direzione sta per essere).</span><span class="sxs-lookup"><span data-stu-id="75b80-134">This sample shows how to get the Vector3 representing the direction of the user gaze and the origin (the point from which the direction is going).</span></span>

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```