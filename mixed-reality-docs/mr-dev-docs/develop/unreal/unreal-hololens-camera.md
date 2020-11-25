---
title: Fotocamera/videocamera HoloLens in Unreal
description: Guida all'uso della fotocamera/videocamera HoloLens in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, videocamera, fotocamera, MRC, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 975853a7b39c4d8790adb1f48160d7e4fdf6c19a
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679040"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="814d0-104">Fotocamera/videocamera HoloLens in Unreal</span><span class="sxs-lookup"><span data-stu-id="814d0-104">HoloLens Photo/Video Camera in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="814d0-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="814d0-105">Overview</span></span>

<span data-ttu-id="814d0-106">HoloLens dispone di una fotocamera/videocamera che viene usata per l'acquisizione in realtà mista (MRC) e può essere usata da un'app per accedere agli oggetti visivi reali.</span><span class="sxs-lookup"><span data-stu-id="814d0-106">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="814d0-107">La fotocamera/videocamera non è supportata con Holographic Remoting, ma per simulare la funzionalità della fotocamera/videocamera di HoloLens è possibile usare una webcam collegata al PC.</span><span class="sxs-lookup"><span data-stu-id="814d0-107">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="814d0-108">Eseguire il rendering dalla fotocamera/videocamera per MRC</span><span class="sxs-lookup"><span data-stu-id="814d0-108">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="814d0-109">Questa operazione richiede **Unreal Engine 4.25** o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="814d0-109">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="814d0-110">Il sistema e i registratori MRC personalizzati creano acquisizioni in realtà mista combinando la fotocamera/videocamera con ologrammi sottoposti a rendering dall'app immersiva.</span><span class="sxs-lookup"><span data-stu-id="814d0-110">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="814d0-111">Per impostazione predefinita, l'acquisizione in realtà mista usa l'output olografico dell'occhio destro.</span><span class="sxs-lookup"><span data-stu-id="814d0-111">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="814d0-112">Se un'app immersiva sceglie di [eseguire il rendering dalla fotocamera/videocamera](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), verrà usata quest'ultima.</span><span class="sxs-lookup"><span data-stu-id="814d0-112">If an immersive app chooses to [render from the PV Camera](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="814d0-113">Ciò migliora il mapping tra il mondo reale e gli ologrammi nel video MRC.</span><span class="sxs-lookup"><span data-stu-id="814d0-113">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="814d0-114">Per acconsentire esplicitamente al rendering dalla fotocamera/videocamera:</span><span class="sxs-lookup"><span data-stu-id="814d0-114">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="814d0-115">Chiama **SetEnabledMixedRealityCamera** e **ResizeMixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="814d0-115">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="814d0-116">Usa i valori **Size X** (Dimensione X) e **Size Y** (Dimensione Y) per impostare le dimensioni video.</span><span class="sxs-lookup"><span data-stu-id="814d0-116">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Terza fotocamera](../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="814d0-118">Unreal gestirà quindi le richieste da MRC per eseguire il rendering dal punto di vista della fotocamera/videocamera.</span><span class="sxs-lookup"><span data-stu-id="814d0-118">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="814d0-119">Solo quando viene attivata [Aquisizione realtà mista](../../mixed-reality-capture.md) all'app verrà chiesto di eseguire il rendering dal punto di vista della fotocamera/videocamera.</span><span class="sxs-lookup"><span data-stu-id="814d0-119">Only when [Mixed Reality Capture](../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="814d0-120">Uso della fotocamera/videocamera</span><span class="sxs-lookup"><span data-stu-id="814d0-120">Using the PV Camera</span></span>

<span data-ttu-id="814d0-121">La texture della webcam può essere recuperata nel gioco in fase di runtime, ma deve essere abilitata in **Edit > Project Settings** (Modifica > Impostazioni progetto) nell'editor:</span><span class="sxs-lookup"><span data-stu-id="814d0-121">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="814d0-122">Passa a **Platforms > HoloLens > Capabilities** (Piattaforme > HoloLens > Funzionalità) e seleziona **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="814d0-122">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="814d0-123">Usa la funzione **StartCameraCapture** per usare la webcam in fase di runtime e la funzione **StopCameraCapture** per arrestare la registrazione.</span><span class="sxs-lookup"><span data-stu-id="814d0-123">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Avvio e arresto della fotocamera](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="814d0-125">Rendering di un'immagine</span><span class="sxs-lookup"><span data-stu-id="814d0-125">Rendering an image</span></span>
<span data-ttu-id="814d0-126">Per eseguire il rendering dell'immagine della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="814d0-126">To render the camera image:</span></span>
1. <span data-ttu-id="814d0-127">Crea un'istanza materiale dinamica basata su un materiale nel progetto, denominato **PVCamMat** nello screenshot seguente.</span><span class="sxs-lookup"><span data-stu-id="814d0-127">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="814d0-128">Imposta l'istanza materiale dinamica su una variabile **Material Instance Dynamic Object Reference** (Riferimento all'oggetto dinamico istanza materiale).</span><span class="sxs-lookup"><span data-stu-id="814d0-128">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="814d0-129">Imposta il materiale dell'oggetto nella scena che eseguirà il rendering del feed della fotocamera su questa nuova istanza materiale dinamica.</span><span class="sxs-lookup"><span data-stu-id="814d0-129">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="814d0-130">Avvia un timer che verrà usato per associare l'immagine della fotocamera al materiale.</span><span class="sxs-lookup"><span data-stu-id="814d0-130">Start a timer that will be used to bind the camera image to the material.</span></span>

![Rendering della fotocamera](images/unreal-camera-render.PNG)

4. <span data-ttu-id="814d0-132">Crea una nuova funzione per questo timer, in questo caso **MaterialTimer**, e chiama **GetARCameraImage** per ottenere la texture dalla webcam.</span><span class="sxs-lookup"><span data-stu-id="814d0-132">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="814d0-133">Se la texture è valida, imposta un parametro di texture nello shader sull'immagine.</span><span class="sxs-lookup"><span data-stu-id="814d0-133">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="814d0-134">In alternativa, avvia di nuovo il timer del materiale.</span><span class="sxs-lookup"><span data-stu-id="814d0-134">Otherwise, start the material timer again.</span></span>

![Acquisire texture dalla webcam](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="814d0-136">Assicurati che il materiale includa un parametro corrispondente al nome in **SetTextureParameterValue** associato a una voce di colore.</span><span class="sxs-lookup"><span data-stu-id="814d0-136">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="814d0-137">In mancanza di questo parametro, l'immagine della fotocamera non potrà essere visualizzata correttamente.</span><span class="sxs-lookup"><span data-stu-id="814d0-137">Without this, the camera image can't be properly displayed.</span></span>

![Texture della fotocamera](images/unreal-camera-material.PNG)

## <a name="next-development-checkpoint"></a><span data-ttu-id="814d0-139">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="814d0-139">Next Development Checkpoint</span></span>

<span data-ttu-id="814d0-140">Se si sta seguendo il percorso di checkpoint per lo sviluppo con Unreal che abbiamo delineato, si stanno esplorando le API e le funzionalità della piattaforma di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="814d0-140">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="814d0-141">Da qui è possibile passare all'argomento successivo:</span><span class="sxs-lookup"><span data-stu-id="814d0-141">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="814d0-142">Codici QR</span><span class="sxs-lookup"><span data-stu-id="814d0-142">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="814d0-143">In alternativa, passare direttamente alla distribuzione dell'app in un dispositivo o emulatore:</span><span class="sxs-lookup"><span data-stu-id="814d0-143">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="814d0-144">Distribuzione nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="814d0-144">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="814d0-145">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="814d0-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="814d0-146">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="814d0-146">See also</span></span>
* [<span data-ttu-id="814d0-147">Fotocamera individuabile</span><span class="sxs-lookup"><span data-stu-id="814d0-147">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="814d0-148">Acquisizione realtà mista per sviluppatori</span><span class="sxs-lookup"><span data-stu-id="814d0-148">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
