---
title: Sguardo fisso
description: Docummentation sui tipi di sguardo fisso in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sguardo,
ms.openlocfilehash: 95dad85ca8154d35f73906b53019d3a52ced546f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176911"
---
# <a name="gaze"></a><span data-ttu-id="f3713-104">Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="f3713-104">Gaze</span></span>

<span data-ttu-id="f3713-105">[Lo](/windows/mixed-reality/gaze) sguardo fisso è una forma di input che interagisce con il mondo in base alla posizione in cui l'utente sta cercando.</span><span class="sxs-lookup"><span data-stu-id="f3713-105">[Gaze](/windows/mixed-reality/gaze) is a form of input that interacts with the world based on where the user is looking.</span></span> <span data-ttu-id="f3713-106">Lo sguardo è presente in due diverse versioni</span><span class="sxs-lookup"><span data-stu-id="f3713-106">Gaze exists in two different flavors</span></span>

## <a name="head-gaze"></a><span data-ttu-id="f3713-107">Puntamento con la testa</span><span class="sxs-lookup"><span data-stu-id="f3713-107">Head gaze</span></span>

<span data-ttu-id="f3713-108">Questo tipo di sguardo è basato sulla direzione che la testa/fotocamera sta osservando.</span><span class="sxs-lookup"><span data-stu-id="f3713-108">This type of gaze is based on the direction that the head/camera is looking at.</span></span> <span data-ttu-id="f3713-109">Lo sguardo con la testa è attivo nei sistemi che non supportano lo sguardo fisso o nei casi in cui l'hardware può supportare lo sguardo fisso, ma non è stato eseguito il set di autorizzazioni e la configurazione corrette. [](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist)</span><span class="sxs-lookup"><span data-stu-id="f3713-109">Head gaze is active on systems that don't support eye gaze, or in cases where the hardware may support eye gaze, but the right set of [permissions and setup](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) has not been performed.</span></span>

<span data-ttu-id="f3713-110">Lo sguardo della testa è in genere associato HoloLens interazioni di stile 1 che implicano la visualizzazione dell'oggetto posizionarlo al centro del frame olografico e quindi eseguire il movimento del tocco dell'aria.</span><span class="sxs-lookup"><span data-stu-id="f3713-110">Head gaze is usually associated with HoloLens 1 style interactions involving looking at object by placing it in the center of the Holographic Frame and then performing the air tap gesture.</span></span>

## <a name="eye-gaze"></a><span data-ttu-id="f3713-111">Tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="f3713-111">Eye gaze</span></span>

<span data-ttu-id="f3713-112">Questo tipo di sguardo si basa sul punto in cui gli occhi dell'utente guardano.</span><span class="sxs-lookup"><span data-stu-id="f3713-112">This type of gaze is based on where the user's eyes are looking.</span></span> <span data-ttu-id="f3713-113">Lo sguardo fisso è presente solo nei sistemi che supportano il tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="f3713-113">Eye gaze is only present on systems that support eye tracking.</span></span> <span data-ttu-id="f3713-114">Per altri [dettagli su come](eye-tracking/eye-tracking-main.md) usare lo sguardo fisso, vedere la documentazione relativa al tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="f3713-114">See the [eye tracking documentation](eye-tracking/eye-tracking-main.md) for more details on how to use eye gaze.</span></span>

## <a name="gazeprovider"></a><span data-ttu-id="f3713-115">GazeProvider</span><span class="sxs-lookup"><span data-stu-id="f3713-115">GazeProvider</span></span>

<span data-ttu-id="f3713-116">La funzionalità dello sguardo (testa e occhio) viene fornita da [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider).</span><span class="sxs-lookup"><span data-stu-id="f3713-116">Gaze functionality (both head and eye) is provided by the [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider).</span></span> <span data-ttu-id="f3713-117">Questo provider può essere configurato nella sezione *Puntatore* del profilo di sistema di input:</span><span class="sxs-lookup"><span data-stu-id="f3713-117">This provider can be configured in the *Pointer* section of the input system profile:</span></span>

![Punto di ingresso di configurazione dello sguardo fisso](../images/input/GazeConfigurationEntrypoint.png)

<span data-ttu-id="f3713-119">Analogamente ad altre origini di input, il provider dello sguardo fisso interagisce con gli oggetti nella scena tramite l'uso di un puntatore (vedere questo documento per [informazioni sui puntatori).](../../architecture/controllers-pointers-and-focus.md)</span><span class="sxs-lookup"><span data-stu-id="f3713-119">Like other sources of input, the gaze provider interacts with objects in the scene through use of a pointer [(see this document for information on pointers)](../../architecture/controllers-pointers-and-focus.md).</span></span>
<span data-ttu-id="f3713-120">Nel caso del provider di sguardo fisso, il relativo puntatore viene implementato tramite `InternalGazePointer` e non viene configurato tramite un profilo.</span><span class="sxs-lookup"><span data-stu-id="f3713-120">In the case of the gaze provider, its pointer is implemented via `InternalGazePointer` and is not configured through a profile.</span></span>

<span data-ttu-id="f3713-121">È possibile sostituire lo stock GazeProvider con un'implementazione alternativa modificando il tipo di *provider gaze* in modo da fare riferimento a una classe diversa che implementa [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) e [IMixedRealityEyeGazeProvider.](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider)</span><span class="sxs-lookup"><span data-stu-id="f3713-121">It is possible to replace the stock GazeProvider with an alternate implementation by changing *Gaze Provider Type* to reference a different class that implements [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) and [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).</span></span>
<span data-ttu-id="f3713-122">È in genere consigliabile usare lo stock GazeProvider (e i problemi di archiviazione in durante la ricerca di bug) perché la ri-implementazione di GazeProvider non è semplice.</span><span class="sxs-lookup"><span data-stu-id="f3713-122">It's generally recommended to use the stock GazeProvider (and filing issues in when finding bugs) as re-implementing the GazeProvider is non-trivial.</span></span>

### <a name="alternative-platform-provided-gaze-poses"></a><span data-ttu-id="f3713-123">Posizioni di sguardo alternative fornite dalla piattaforma</span><span class="sxs-lookup"><span data-stu-id="f3713-123">Alternative platform-provided gaze poses</span></span>

<span data-ttu-id="f3713-124">Per impostazione predefinita, MRTK GazeProvider usa il centro della cornice della fotocamera come origine dello sguardo.</span><span class="sxs-lookup"><span data-stu-id="f3713-124">By default, the MRTK GazeProvider uses the center of the camera's frame as the gaze origin.</span></span> <span data-ttu-id="f3713-125">Alcune piattaforme, ad esempio Windows Mixed Reality su HoloLens 2, forniscono una posizione dello sguardo fisso definita in alternativa.</span><span class="sxs-lookup"><span data-stu-id="f3713-125">Some platforms, like Windows Mixed Reality on HoloLens 2, provide an alternatively defined gaze pose.</span></span> <span data-ttu-id="f3713-126">Questa operazione viene gestita tramite `Use Head Gaze Override` l'impostazione nelle impostazioni dello sguardo.</span><span class="sxs-lookup"><span data-stu-id="f3713-126">This is managed via the `Use Head Gaze Override` setting in the gaze settings.</span></span> <span data-ttu-id="f3713-127">Se abilitata, verrà usata la sostituzione dello sguardo alternativo.</span><span class="sxs-lookup"><span data-stu-id="f3713-127">When enabled, the alternative gaze override will be used.</span></span> <span data-ttu-id="f3713-128">Se disabilitata, verrà usata l'origine predefinita del centro frame.</span><span class="sxs-lookup"><span data-stu-id="f3713-128">When disabled, the default frame center origin will be used.</span></span> <span data-ttu-id="f3713-129">In particolare, per HoloLens 2, l'angolo dello sguardo fisso verrà aumentato di diversi gradi per motivi di comfort dell'utente nell'uso della testa per il targeting.</span><span class="sxs-lookup"><span data-stu-id="f3713-129">Specifically, for HoloLens 2, the gaze angle will be raised several degrees to account for user comfort in using their head for targeting.</span></span>

## <a name="usage"></a><span data-ttu-id="f3713-130">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="f3713-130">Usage</span></span>

### <a name="how-get-the-current-gaze-target"></a><span data-ttu-id="f3713-131">Come ottenere la destinazione dello sguardo corrente</span><span class="sxs-lookup"><span data-stu-id="f3713-131">How get the current gaze target</span></span>

<span data-ttu-id="f3713-132">Questo esempio illustra come ottenere l'oggetto di gioco corrente destinato dallo sguardo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="f3713-132">This sample shows how to get the current game object that is targeted by the user gaze.</span></span>

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

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a><span data-ttu-id="f3713-133">Come ottenere la direzione e l'origine dello sguardo corrente</span><span class="sxs-lookup"><span data-stu-id="f3713-133">How to get the current gaze direction and origin</span></span>

<span data-ttu-id="f3713-134">Questo esempio illustra come ottenere Vector3 che rappresenta la direzione dello sguardo dell'utente e l'origine (il punto da cui sta andando la direzione).</span><span class="sxs-lookup"><span data-stu-id="f3713-134">This sample shows how to get the Vector3 representing the direction of the user gaze and the origin (the point from which the direction is going).</span></span>

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
