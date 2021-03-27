---
title: Configurazione della fotocamera in Unity
description: Informazioni su come configurare e usare la fotocamera principale di Unity per lo sviluppo di realtà mista di Windows per eseguire il rendering olografico.
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, rendering olografico, olografico, immersivo, punto di messa a fuoco, buffer di profondità, solo orientamento, posizionale, opaco, trasparente, clip, auricolare realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: d3f69c6cf1889587b23b68259f22b34b89b925a4
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636304"
---
# <a name="camera-setup-in-unity"></a><span data-ttu-id="394f6-104">Configurazione della fotocamera in Unity</span><span class="sxs-lookup"><span data-stu-id="394f6-104">Camera setup in Unity</span></span>

<span data-ttu-id="394f6-105">Quando si usa una cuffia a realtà mista, diventa il centro del mondo olografico.</span><span class="sxs-lookup"><span data-stu-id="394f6-105">When you wear a mixed reality headset, it becomes the center of your holographic world.</span></span> <span data-ttu-id="394f6-106">Il componente della [fotocamera](https://docs.unity3d.com/Manual/class-Camera.html) Unity gestirà automaticamente il rendering stereoscopico e seguirà lo spostamento e la rotazione del titolo.</span><span class="sxs-lookup"><span data-stu-id="394f6-106">The Unity [Camera](https://docs.unity3d.com/Manual/class-Camera.html) component will automatically handle stereoscopic rendering and follow your head movement and rotation.</span></span> <span data-ttu-id="394f6-107">Tuttavia, per ottimizzare completamente la qualità visiva e la [stabilità dell'ologramma](../platform-capabilities-and-apis/hologram-stability.md), è necessario impostare le impostazioni della fotocamera descritte di seguito.</span><span class="sxs-lookup"><span data-stu-id="394f6-107">However, to fully optimize visual quality and [hologram stability](../platform-capabilities-and-apis/hologram-stability.md), you should set the camera settings described below.</span></span>

## <a name="hololens-vs-vr-immersive-headsets"></a><span data-ttu-id="394f6-108">Cuffie immersive HoloLens vs VR</span><span class="sxs-lookup"><span data-stu-id="394f6-108">HoloLens vs VR immersive headsets</span></span>

<span data-ttu-id="394f6-109">Le impostazioni predefinite nel componente della fotocamera Unity sono per le applicazioni 3D tradizionali, che richiedono uno sfondo SKYBOX, perché non hanno un mondo reale.</span><span class="sxs-lookup"><span data-stu-id="394f6-109">The default settings on the Unity Camera component are for traditional 3D applications, which need a skybox-like background as they don't have a real world.</span></span>

* <span data-ttu-id="394f6-110">Quando si esegue un' **[auricolare immersiva](../../discover/immersive-headset-hardware-details.md)**, si esegue il rendering di tutti gli elementi che l'utente vede, quindi è probabile che si desideri proteggere skybox.</span><span class="sxs-lookup"><span data-stu-id="394f6-110">When running on an **[immersive headset](../../discover/immersive-headset-hardware-details.md)**, you're rendering everything the user sees, and so you'll likely want to keep the skybox.</span></span>
* <span data-ttu-id="394f6-111">Tuttavia, quando si esegue un **auricolare olografico** come [HoloLens](/hololens/hololens2-hardware), il mondo reale dovrebbe apparire dietro tutto il rendering della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="394f6-111">However, when running on a **holographic headset** like [HoloLens](/hololens/hololens2-hardware), the real world should appear behind everything the camera renders.</span></span> <span data-ttu-id="394f6-112">Impostare lo sfondo della fotocamera come trasparente (in HoloLens, il nero viene visualizzato come trasparente) invece di una trama skybox:</span><span class="sxs-lookup"><span data-stu-id="394f6-112">Set the camera background to be transparent (in HoloLens, black renders as transparent) instead of a Skybox texture:</span></span>
    1. <span data-ttu-id="394f6-113">Selezionare la fotocamera principale nel pannello gerarchia</span><span class="sxs-lookup"><span data-stu-id="394f6-113">Select the Main Camera in the Hierarchy panel</span></span>
    2. <span data-ttu-id="394f6-114">Nel pannello Inspector trovare il componente della fotocamera e modificare l'elenco a discesa Clear Flags da skybox a Solid Color.</span><span class="sxs-lookup"><span data-stu-id="394f6-114">In the Inspector panel, find the Camera component and change the Clear Flags dropdown from Skybox to Solid Color</span></span>
    3. <span data-ttu-id="394f6-115">Selezionare la selezione dei colori di sfondo e modificare i valori di RGBA in (0, 0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="394f6-115">Select the Background color picker and change the RGBA values to (0, 0, 0, 0)</span></span>
        1. <span data-ttu-id="394f6-116">Se si imposta questa opzione dal codice, è possibile usare Unity [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)</span><span class="sxs-lookup"><span data-stu-id="394f6-116">If setting this from code, you can use Unity's [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)</span></span>

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a><span data-ttu-id="394f6-117">Impostazione della fotocamera</span><span class="sxs-lookup"><span data-stu-id="394f6-117">Camera setup</span></span>

<span data-ttu-id="394f6-118">Indipendentemente dal tipo di esperienza che si sta sviluppando, la fotocamera principale è sempre il componente di rendering stereo primario collegato alla visualizzazione a capo del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="394f6-118">Whatever kind of experience you're developing, the Main Camera is always the primary stereo rendering component attached to your device's head-mounted display.</span></span> <span data-ttu-id="394f6-119">Il layout dell'app sarà più semplice se si immagina la posizione iniziale dell'utente come (X: 0, Y: 0, Z: 0).</span><span class="sxs-lookup"><span data-stu-id="394f6-119">It'll be easier to lay out your app if you imagine the starting position of the user as (X: 0, Y: 0, Z: 0).</span></span> <span data-ttu-id="394f6-120">Poiché la fotocamera principale tiene traccia del movimento della testa dell'utente, è possibile impostare la posizione iniziale dell'utente impostando la posizione iniziale della fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="394f6-120">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

<span data-ttu-id="394f6-121">La scelta centrale da fare è se si sta sviluppando per auricolari HoloLens o VR immersivi.</span><span class="sxs-lookup"><span data-stu-id="394f6-121">The central choice you need to make is whether you're developing for HoloLens or VR immersive headsets.</span></span> <span data-ttu-id="394f6-122">Una volta ottenuta questa procedura, passare a qualsiasi sezione di configurazione.</span><span class="sxs-lookup"><span data-stu-id="394f6-122">Once you've got that, skip to whichever setup section applies.</span></span>

### <a name="hololens-camera-setup"></a><span data-ttu-id="394f6-123">Installazione della fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="394f6-123">HoloLens camera setup</span></span>

<span data-ttu-id="394f6-124">Per le app HoloLens, è necessario usare ancoraggi per tutti gli oggetti che si desidera bloccare nell'ambiente della scena.</span><span class="sxs-lookup"><span data-stu-id="394f6-124">For HoloLens apps, you need to use anchors for any objects you want to lock to the scene environment.</span></span> <span data-ttu-id="394f6-125">Si consiglia di usare uno spazio non vincolato per ottimizzare la stabilità e creare ancoraggi in più chat room.</span><span class="sxs-lookup"><span data-stu-id="394f6-125">We recommend using unbounded space to maximize stability and create anchors in multiple rooms.</span></span>

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a><span data-ttu-id="394f6-126">Configurazione della fotocamera VR</span><span class="sxs-lookup"><span data-stu-id="394f6-126">VR camera setup</span></span>

<span data-ttu-id="394f6-127">La realtà mista di Windows supporta le app in un'ampia gamma di [scale di esperienza](../../design/coordinate-systems.md#mixed-reality-experience-scales), da app di solo orientamento e scalabilità verticale fino ad app a scalabilità.</span><span class="sxs-lookup"><span data-stu-id="394f6-127">Windows Mixed Reality supports apps across a wide range of [experience scales](../../design/coordinate-systems.md#mixed-reality-experience-scales), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="394f6-128">In HoloLens è possibile proseguire e creare app su scala mondiale che consentono agli utenti di superare i 5 metri, esplorando un'intera superficie di un edificio e oltre.</span><span class="sxs-lookup"><span data-stu-id="394f6-128">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="394f6-129">Il primo passaggio per creare un'esperienza di realtà mista in Unity consiste nel determinare quale [scalabilità dell'esperienza](../../design/coordinate-systems.md) sarà destinata all'app:</span><span class="sxs-lookup"><span data-stu-id="394f6-129">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](../../design/coordinate-systems.md) your app will target:</span></span>

* [<span data-ttu-id="394f6-130">Orientamento o scalabilità a sedere</span><span class="sxs-lookup"><span data-stu-id="394f6-130">Orientation or seated-scale</span></span>](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [<span data-ttu-id="394f6-131">Scalabilità in piedi o in locale</span><span class="sxs-lookup"><span data-stu-id="394f6-131">Standing or room-scale</span></span>](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [<span data-ttu-id="394f6-132">Scalabilità globale</span><span class="sxs-lookup"><span data-stu-id="394f6-132">World-scale</span></span>](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a><span data-ttu-id="394f6-133">Esperienze su scala o in piedi</span><span class="sxs-lookup"><span data-stu-id="394f6-133">Room-scale or standing experiences</span></span>

> [!NOTE]
> <span data-ttu-id="394f6-134">Se si sta compilando per HL2, è consigliabile creare un'esperienza a livello di occhio oppure prendere in considerazione l'uso della [comprensione della scena](../platform-capabilities-and-apis/scene-understanding-sdk.md) per ragionare sul pavimento della scena.</span><span class="sxs-lookup"><span data-stu-id="394f6-134">If you're building for HL2, we recommend creating an eye-level experience, or consider using [Scene Understanding](../platform-capabilities-and-apis/scene-understanding-sdk.md) to reason about the floor of your scene.</span></span>

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a><span data-ttu-id="394f6-135">Esperienze di seduta</span><span class="sxs-lookup"><span data-stu-id="394f6-135">Seated experiences</span></span>

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a><span data-ttu-id="394f6-136">Impostazione dello sfondo della fotocamera</span><span class="sxs-lookup"><span data-stu-id="394f6-136">Setting up the camera background</span></span>

<span data-ttu-id="394f6-137">Se si usa MRTK, lo sfondo della fotocamera viene configurato e gestito automaticamente.</span><span class="sxs-lookup"><span data-stu-id="394f6-137">If you're using MRTK, the camera's background is automatically configured and managed.</span></span> <span data-ttu-id="394f6-138">Per i progetti di XR SDK o legacy WSA, è consigliabile impostare lo sfondo della fotocamera su nero a tinta unita in HoloLens e mantenere Skybox per VR.</span><span class="sxs-lookup"><span data-stu-id="394f6-138">For XR SDK or Legacy WSA projects, we recommend setting the camera's background to solid black on HoloLens and keeping the skybox for VR.</span></span>

## <a name="using-multiple-cameras"></a><span data-ttu-id="394f6-139">Uso di più fotocamere</span><span class="sxs-lookup"><span data-stu-id="394f6-139">Using multiple cameras</span></span>

<span data-ttu-id="394f6-140">Quando nella scena sono presenti più componenti della fotocamera, Unity sa quale fotocamera usare per il rendering stereoscopico in base a quale GameObject ha il tag MainCamera.</span><span class="sxs-lookup"><span data-stu-id="394f6-140">When there are multiple Camera components in the scene, Unity knows which camera to use for stereoscopic rendering based on which GameObject has the MainCamera tag.</span></span> <span data-ttu-id="394f6-141">Nella versione precedente di XR, usa questo tag anche per sincronizzare il rilevamento Head.</span><span class="sxs-lookup"><span data-stu-id="394f6-141">In legacy XR, it also uses this tag to sync head tracking.</span></span> <span data-ttu-id="394f6-142">In XR SDK il rilevamento Head è gestito da uno script TrackedPoseDriver collegato alla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="394f6-142">In XR SDK, head tracking is driven by a TrackedPoseDriver script attached to the camera.</span></span>

## <a name="sharing-depth-buffers"></a><span data-ttu-id="394f6-143">Condivisione di buffer di profondità</span><span class="sxs-lookup"><span data-stu-id="394f6-143">Sharing depth buffers</span></span>

<span data-ttu-id="394f6-144">La condivisione del buffer di profondità dell'app in Windows ogni frame offrirà all'app uno dei due aumenti di stabilità dell'ologramma, in base al tipo di auricolare per cui si esegue il rendering:</span><span class="sxs-lookup"><span data-stu-id="394f6-144">Sharing your app's depth buffer to Windows each frame will give your app one of two boosts in hologram stability, based on the type of headset you're rendering for:</span></span>

* <span data-ttu-id="394f6-145">Gli **auricolari VR immersivi** possono gestire la riproiezione posizionale quando viene fornito un buffer di profondità, regolando gli ologrammi per la stima errata nella posizione e nell'orientamento.</span><span class="sxs-lookup"><span data-stu-id="394f6-145">**VR immersive headsets** can take care of positional reprojection when a depth buffer is provided, adjusting your holograms for misprediction in both position and orientation.</span></span>
* <span data-ttu-id="394f6-146">Gli **auricolari HoloLens** hanno metodi diversi.</span><span class="sxs-lookup"><span data-stu-id="394f6-146">**HoloLens headsets** have a few different methods.</span></span> <span data-ttu-id="394f6-147">HoloLens 1 seleziona automaticamente un [punto di interesse](focus-point-in-unity.md) quando viene fornito un buffer di profondità, ottimizzando la stabilità dell'ologramma lungo il piano che interseca la maggior parte del contenuto.</span><span class="sxs-lookup"><span data-stu-id="394f6-147">HoloLens 1 will automatically select a [focus point](focus-point-in-unity.md) when a depth buffer is provided, optimizing hologram stability along the plane that intersects the most content.</span></span> <span data-ttu-id="394f6-148">HoloLens 2 stabilizza il contenuto usando [LSR di profondità (vedere la sezione Osservazioni)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).</span><span class="sxs-lookup"><span data-stu-id="394f6-148">HoloLens 2 will stabilize content using [Depth LSR (see Remarks)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).</span></span>

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a><span data-ttu-id="394f6-149">Uso di piani di ritaglio</span><span class="sxs-lookup"><span data-stu-id="394f6-149">Using clipping planes</span></span>

<span data-ttu-id="394f6-150">Il rendering del contenuto troppo vicino all'utente può risultare scomodo in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="394f6-150">Rendering content too close to the user can be uncomfortable in mixed reality.</span></span> <span data-ttu-id="394f6-151">È possibile regolare i [piani di ritaglio vicini e lontani](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) sul componente della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="394f6-151">You can adjust the [near and far clip planes](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) on the Camera component.</span></span>

1. <span data-ttu-id="394f6-152">Selezionare la **fotocamera principale** nel pannello **gerarchia**</span><span class="sxs-lookup"><span data-stu-id="394f6-152">Select the **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="394f6-153">Nel pannello **Inspector** trovare i **piani di ritaglio** dei componenti della **fotocamera** e modificare la casella di testo **near** da **0,3** a **0,85**.</span><span class="sxs-lookup"><span data-stu-id="394f6-153">In the **Inspector** panel, find the **Camera** component **Clipping Planes** and change the **Near** textbox from **0.3** to **0.85**.</span></span> <span data-ttu-id="394f6-154">Il rendering del contenuto ancora più vicino può causare disagi da parte dell'utente e deve essere evitato in base alle [linee guida di rendering](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).</span><span class="sxs-lookup"><span data-stu-id="394f6-154">Content rendered even closer can lead to user discomfort and should be avoided per the [render distance guidelines](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).</span></span>

## <a name="recentering-the-camera"></a><span data-ttu-id="394f6-155">Ricentrare la fotocamera</span><span class="sxs-lookup"><span data-stu-id="394f6-155">Recentering the camera</span></span>

<span data-ttu-id="394f6-156">Se si sta creando un' [esperienza a scalabilità verticale](../../design/coordinate-systems.md), è possibile ricentrare l'origine del mondo di Unity nella posizione Head corrente dell'utente chiamando **[XR. Metodo InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** nel metodo legacy XR o **[XRInputSubsystem. TRYRECENTER](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** in XR SDK.</span><span class="sxs-lookup"><span data-stu-id="394f6-156">If you're building a [seated-scale experience](../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method in legacy XR or the **[XRInputSubsystem.TryRecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** method in XR SDK.</span></span>

## <a name="teleportation"></a><span data-ttu-id="394f6-157">Teletrasporto</span><span class="sxs-lookup"><span data-stu-id="394f6-157">Teleportation</span></span>

<span data-ttu-id="394f6-158">Questa funzionalità è in genere riservata per le esperienze di VR:</span><span class="sxs-lookup"><span data-stu-id="394f6-158">This feature is typically reserved for VR experiences:</span></span>

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a><span data-ttu-id="394f6-159">Modalità di riproiezione</span><span class="sxs-lookup"><span data-stu-id="394f6-159">Reprojection modes</span></span>

<span data-ttu-id="394f6-160">Sia HoloLens che le cuffie immersive riproiettano ogni frame di cui l'app esegue il rendering per adattarsi a qualsiasi stima errata della posizione effettiva dell'utente quando vengono emessi i fotoni.</span><span class="sxs-lookup"><span data-stu-id="394f6-160">Both HoloLens and immersive headsets will reproject each frame your app renders to adjust for any misprediction of the user's actual head position when photons are emitted.</span></span>

<span data-ttu-id="394f6-161">Per impostazione predefinita:</span><span class="sxs-lookup"><span data-stu-id="394f6-161">By default:</span></span>

* <span data-ttu-id="394f6-162">Gli **auricolari immersivi VR** si occupano della riproiezione posizionale se l'app fornisce un buffer di profondità per un determinato frame.</span><span class="sxs-lookup"><span data-stu-id="394f6-162">**VR immersive headsets** will take care of positional reprojection if the app provides a depth buffer for a given frame.</span></span> <span data-ttu-id="394f6-163">Gli auricolari immersivi configureranno anche gli ologrammi in modo da ottenere una stima errata nella posizione e nell'orientamento.</span><span class="sxs-lookup"><span data-stu-id="394f6-163">Immersive headsets will also adjust your holograms for misprediction in both position and orientation.</span></span> <span data-ttu-id="394f6-164">Se non viene fornito un buffer di profondità, il sistema correggerà solo le stime errate all'orientamento.</span><span class="sxs-lookup"><span data-stu-id="394f6-164">If a depth buffer isn't provided, the system will only correct mispredictions in orientation.</span></span>
* <span data-ttu-id="394f6-165">Gli **auricolari olografici** come HoloLens 2 si occupano della riproiezione posizionale, indipendentemente dal fatto che l'app fornisca il buffer di profondità.</span><span class="sxs-lookup"><span data-stu-id="394f6-165">**Holographic headsets** like HoloLens 2 will take care of positional reprojection whether the app provides its depth buffer or not.</span></span> <span data-ttu-id="394f6-166">La riproiezione posizionale è possibile senza buffer di profondità su HoloLens perché il rendering è spesso di tipo sparse con uno sfondo stabile fornito dal mondo reale.</span><span class="sxs-lookup"><span data-stu-id="394f6-166">Positional reprojection is possible without depth buffers on HoloLens as rendering is often sparse with a stable background provided by the real world.</span></span>

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="394f6-167">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="394f6-167">Next Development Checkpoint</span></span>

<span data-ttu-id="394f6-168">Se si sta seguendo il percorso di sviluppo di Unity, si sta per esplorare i blocchi predefiniti di MRTK core.</span><span class="sxs-lookup"><span data-stu-id="394f6-168">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="394f6-169">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="394f6-169">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="394f6-170">Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="394f6-170">Gaze</span></span>](gaze-in-unity.md)

<span data-ttu-id="394f6-171">In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="394f6-171">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="394f6-172">Esperienze condivise</span><span class="sxs-lookup"><span data-stu-id="394f6-172">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="394f6-173">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="394f6-173">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="394f6-174">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="394f6-174">See also</span></span>

* [<span data-ttu-id="394f6-175">Stabilità degli ologrammi</span><span class="sxs-lookup"><span data-stu-id="394f6-175">Hologram stability</span></span>](../platform-capabilities-and-apis/hologram-stability.md)
* [<span data-ttu-id="394f6-176">Scale Experience</span><span class="sxs-lookup"><span data-stu-id="394f6-176">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="394f6-177">Fase spaziale</span><span class="sxs-lookup"><span data-stu-id="394f6-177">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="394f6-178">Perdita del rilevamento in Unity</span><span class="sxs-lookup"><span data-stu-id="394f6-178">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="394f6-179">Ancoraggi nello spazio</span><span class="sxs-lookup"><span data-stu-id="394f6-179">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="394f6-180">Persistenza in Unity</span><span class="sxs-lookup"><span data-stu-id="394f6-180">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="394f6-181">Esperienze condivise in Unity</span><span class="sxs-lookup"><span data-stu-id="394f6-181">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="394f6-182">Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="394f6-182">Azure Spatial Anchors</span></span>](/azure/spatial-anchors)
* [<span data-ttu-id="394f6-183">Azure Spatial Anchors SDK per Unity</span><span class="sxs-lookup"><span data-stu-id="394f6-183">Azure Spatial Anchors SDK for Unity</span></span>](/dotnet/api/Microsoft.Azure.SpatialAnchors)