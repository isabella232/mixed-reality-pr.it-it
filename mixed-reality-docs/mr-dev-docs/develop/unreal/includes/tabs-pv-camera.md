---
ms.openlocfilehash: e79b14c19a452b5b78c6f8cf7ea24bd65bfa0eaa
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98605305"
---
# <a name="426"></a>[<span data-ttu-id="d6620-101">4.26</span><span class="sxs-lookup"><span data-stu-id="d6620-101">4.26</span></span>](#tab/426) 

## <a name="pv-camera-feed-setup"></a><span data-ttu-id="d6620-102">Impostazione del feed della fotocamera/videocamera</span><span class="sxs-lookup"><span data-stu-id="d6620-102">PV Camera Feed Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6620-103">La fotocamera/videocamera è implementata nei plug-in Windows Mixed Reality e OpenXR.</span><span class="sxs-lookup"><span data-stu-id="d6620-103">PV camera is implemented in both Windows Mixed Reality and OpenXR plugins.</span></span> <span data-ttu-id="d6620-104">OpenXR, tuttavia, richiede l'installazione del [plug-in Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="d6620-104">However OpenXR needs [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) to be installed.</span></span> <span data-ttu-id="d6620-105">Inoltre, OpenXR presenta una limitazione corrente per cui la fotocamera può funzionare con l'interfaccia RHI DirectX11.</span><span class="sxs-lookup"><span data-stu-id="d6620-105">Also OpenXR has current limitation, camera can work with DirectX11 RHI.</span></span> <span data-ttu-id="d6620-106">Questa limitazione verrà eliminata in una successiva versione di Unreal.</span><span class="sxs-lookup"><span data-stu-id="d6620-106">This limitation will be fixed in a further Unreal version.</span></span> 

- <span data-ttu-id="d6620-107">In **Project Settings > HoloLens** (Impostazioni progetto) abilitare la funzionalità **Webcam**:</span><span class="sxs-lookup"><span data-stu-id="d6620-107">In **Project Settings > HoloLens**, enable the **Webcam** capability:</span></span>

![Screenshot delle impostazioni di progetto HoloLens con la proprietà Webcam evidenziata](../images/unreal-pvc-img-01.png)

- <span data-ttu-id="d6620-109">Creare un nuovo attore denominato "CamCapture" e aggiungere un piano per il rendering del feed della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="d6620-109">Create a new actor called “CamCapture” and add a plane to render the camera feed:</span></span>

![Screenshot di un attore con un piano aggiunto](../images/unreal-pvc-img-02.png)

- <span data-ttu-id="d6620-111">Aggiungere l'attore alla scena, creare un nuovo materiale denominato CamTextureMaterial con un parametro di oggetto trama e un esempio di trama.</span><span class="sxs-lookup"><span data-stu-id="d6620-111">Add the actor to your scene, create a new material called CamTextureMaterial with a Texture Object Parameter, and a texture sample.</span></span>  <span data-ttu-id="d6620-112">Inviare i dati RGB della trama al colore emissivo di output:</span><span class="sxs-lookup"><span data-stu-id="d6620-112">Send the texture’s rgb data to the output emissive color:</span></span>

![Progetto di un materiale e un esempio di trama](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a><span data-ttu-id="d6620-114">Rendering del feed della fotocamera/videocamera</span><span class="sxs-lookup"><span data-stu-id="d6620-114">Rendering the PV Camera Feed</span></span>

- <span data-ttu-id="d6620-115">Nel progetto CamCapture attivare la fotocamera/videocamera:</span><span class="sxs-lookup"><span data-stu-id="d6620-115">In the CamCapture blueprint, turn on the PV Camera:</span></span>

![Progetto della funzione Toggle ARCapture con la fotocamera/videocamera attivata](../images/unreal-pvc-img-04.png)

- <span data-ttu-id="d6620-117">Creare un'istanza del materiale dinamico da CamTextureMaterial e assegnare questo materiale al piano dell'attore:</span><span class="sxs-lookup"><span data-stu-id="d6620-117">Create a dynamic material instance from CamTextureMaterial and assign this material to the actor’s plane:</span></span>

![Progetto della funzione Create Dynamic Material Instance](../images/unreal-pvc-img-05.png)

- <span data-ttu-id="d6620-119">Ottenere la trama dal feed della fotocamera e, se è valida, assegnarla al materiale dinamico.</span><span class="sxs-lookup"><span data-stu-id="d6620-119">Get the texture from the camera feed and assign it to the dynamic material if it's valid.</span></span>  <span data-ttu-id="d6620-120">Se la trama non è valida, avviare un timer e riprovare dopo il timeout:</span><span class="sxs-lookup"><span data-stu-id="d6620-120">If the texture isn't valid, start a timer and try again after the timeout:</span></span>

![Progetto della trama del feed della fotocamera assegnata al materiale dinamico](../images/unreal-pvc-img-06.png)

- <span data-ttu-id="d6620-122">Infine, ridimensionare il piano in base alle proporzioni dell'immagine della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="d6620-122">Finally, scale the plane by the camera image’s aspect ratio:</span></span>

![Progetto del piano ridimensionato rispetto alle proporzioni delle immagini della fotocamera](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a><span data-ttu-id="d6620-124">Trovare le posizioni della fotocamera nello spazio globale</span><span class="sxs-lookup"><span data-stu-id="d6620-124">Find Camera Positions in World Space</span></span>

<span data-ttu-id="d6620-125">La fotocamera in HoloLens 2 presenta uno scostamento verticale rispetto al rilevamento della testa operato dal dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d6620-125">The camera on the HoloLens 2 is offset vertically from the device’s head tracking.</span></span>  <span data-ttu-id="d6620-126">Per tenere in considerazione questo scostamento, sono disponibili alcune funzioni per individuare la fotocamera nello spazio globale.</span><span class="sxs-lookup"><span data-stu-id="d6620-126">A few functions exist to locate the camera in world space to account for the offset.</span></span>

<span data-ttu-id="d6620-127">GetPVCameraToWorldTransform ottiene la trasformazione nello spazio globale della fotocamera/videocamera e viene posizionata sull'obiettivo della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="d6620-127">GetPVCameraToWorldTransform gets the transform in world space of the PV Camera and will be positioned on the camera lens:</span></span>

![Progetto della funzione Get PVCamera to World Transform](../images/unreal-pvc-img-08.png)

<span data-ttu-id="d6620-129">GetWorldSpaceRayFromCameraPoint esegue il cast di un raggio dall'obiettivo della fotocamera alla scena nello spazio globale di Unreal per trovare un contenuto di pixel presente nel frame della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="d6620-129">GetWorldSpaceRayFromCameraPoint casts a ray from the camera lens into the scene in Unreal world space to find a pixel's content in the camera frame:</span></span>

![Progetto di Get World Space Ray from Camera Point](../images/unreal-pvc-img-09.png)

<span data-ttu-id="d6620-131">GetPVCameraIntrinsics restituisce i valori intrinseci della fotocamera, che possono essere usati quando si esegue l'elaborazione della visione artificiale su un frame della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="d6620-131">GetPVCameraIntrinsics returns the camera intrinsic values, which can be used when doing computer vision processing on a camera frame:</span></span>

![Progetto delle funzioni di Get PVCamera Intrinsics](../images/unreal-pvc-img-10.png)

<span data-ttu-id="d6620-133">Per trovare un elemento presente nello spazio globale in corrispondenza di una particolare coordinata del pixel, usare una traccia lineare con il raggio dello spazio globale:</span><span class="sxs-lookup"><span data-stu-id="d6620-133">To find what exists in world space at a particular pixel coordinate, use a line trace with the world space ray:</span></span>

![Progetto del raggio dello spazio globale usato per individuare un elemento presente nello spazio globale in corrispondenza di una particolare coordinata](../images/unreal-pvc-img-11.png)

<span data-ttu-id="d6620-135">A questo punto viene eseguito il cast di un raggio di 2 metri dall'obiettivo della fotocamera alla posizione dello spazio della fotocamera con uno scostamento di 1/4 dalla parte superiore sinistra del frame.</span><span class="sxs-lookup"><span data-stu-id="d6620-135">Here we cast a 2-meter ray from the camera lens to the camera-space position ¼ from the top left of the frame.</span></span>  <span data-ttu-id="d6620-136">Usare quindi il risultato ottenuto per eseguire il rendering di un elemento nel punto in cui è presente l'oggetto nello spazio globale:</span><span class="sxs-lookup"><span data-stu-id="d6620-136">Then use the hit result to render something where the object exists in world space:</span></span>

![Progetto del cast di un raggio di 2 metri dall'obiettivo della fotocamera alla posizione dello spazio della fotocamera con uno scostamento di 1/4 dalla parte superiore sinistra del frame](../images/unreal-pvc-img-12.png)

<span data-ttu-id="d6620-138">Quando si usa il mapping spaziale, la posizione ottenuta corrisponde alla superficie visualizzata dalla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="d6620-138">When using spatial mapping, this hit position will match the surface that the camera is seeing.</span></span>

## <a name="rendering-the-pv-camera-feed-in-c"></a><span data-ttu-id="d6620-139">Rendering del feed della fotocamera/videocamera in C++</span><span class="sxs-lookup"><span data-stu-id="d6620-139">Rendering the PV Camera Feed in C++</span></span>

- <span data-ttu-id="d6620-140">Creare un nuovo attore C++ denominato CamCapture</span><span class="sxs-lookup"><span data-stu-id="d6620-140">Create a new C++ actor called CamCapture</span></span>
- <span data-ttu-id="d6620-141">Nel file build.cs del progetto aggiungere "AugmentedReality" all'elenco PublicDependencyModuleNames:</span><span class="sxs-lookup"><span data-stu-id="d6620-141">In the project’s build.cs, add “AugmentedReality” to the PublicDependencyModuleNames list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "AugmentedReality"
});
```

- <span data-ttu-id="d6620-142">In CamCapture.h includere ARBlueprintLibrary.h</span><span class="sxs-lookup"><span data-stu-id="d6620-142">In CamCapture.h, include ARBlueprintLibrary.h</span></span>

```cpp
#include "ARBlueprintLibrary.h"
```

- <span data-ttu-id="d6620-143">È anche necessario aggiungere variabili locali per la mesh e il materiale:</span><span class="sxs-lookup"><span data-stu-id="d6620-143">You also need to add local variables for the mesh and material:</span></span>

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- <span data-ttu-id="d6620-144">In CamCapture.cpp aggiornare il costruttore per aggiungere una mesh statica alla scena:</span><span class="sxs-lookup"><span data-stu-id="d6620-144">In CamCapture.cpp, update the constructor to add a static mesh to the scene:</span></span>

```cpp
ACamCapture::ACamCapture()
{
    PrimaryActorTick.bCanEverTick = true;

    // Load a mesh from the engine to render the camera feed to.
    StaticMesh = LoadObject<UStaticMesh>(nullptr, TEXT("/Engine/EngineMeshes/Cube.Cube"), nullptr, LOAD_None, nullptr);

    // Create a static mesh component to render the static mesh
    StaticMeshComponent = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("CameraPlane"));
    StaticMeshComponent->SetStaticMesh(StaticMesh);

    // Scale and add to the scene
    StaticMeshComponent->SetWorldScale3D(FVector(0.1f, 1, 1));
    this->SetRootComponent(StaticMeshComponent);
}
```

<span data-ttu-id="d6620-145">In BeginPlay creare un'istanza di materiale dinamico dal materiale della fotocamera del progetto, applicarla al componente della mesh statica e avviare la fotocamera HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d6620-145">In BeginPlay create a dynamic material instance from the project’s camera material, apply it to the static mesh component, and start the HoloLens camera.</span></span> 
 
<span data-ttu-id="d6620-146">Per ottenere la stringa per CameraMatPath, nell'editor fare clic con il pulsante destro del mouse su CamTextureMaterial nel browser del contenuto e selezionare "Copy Reference" (Copia riferimento).</span><span class="sxs-lookup"><span data-stu-id="d6620-146">In the editor, right-click on the CamTextureMaterial in the content browser and select “Copy Reference” to get the string for CameraMatPath.</span></span>

```cpp
void ACamCapture::BeginPlay()
{
    Super::BeginPlay();

    // Create a dynamic material instance from the game's camera material.
    // Right-click on a material in the project and select "Copy Reference" to get this string.
    FString CameraMatPath("Material'/Game/Materials/CamTextureMaterial.CamTextureMaterial'");
    UMaterial* BaseMaterial = (UMaterial*)StaticLoadObject(UMaterial::StaticClass(), nullptr, *CameraMatPath, nullptr, LOAD_None, nullptr);
    DynamicMaterial = UMaterialInstanceDynamic::Create(BaseMaterial, this);

    // Use the dynamic material instance when rendering the camera mesh.
    StaticMeshComponent->SetMaterial(0, DynamicMaterial);

    // Start the webcam.
    UARBlueprintLibrary::ToggleARCapture(true, EARCaptureType::Camera);
}
```

<span data-ttu-id="d6620-147">In Tick ottenere la trama dalla fotocamera, impostarla sul parametro della trama nel materiale CamTextureMaterial e ridimensionare il componente della mesh statica in base alle proporzioni del frame della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="d6620-147">In Tick get the texture from the camera, set it to the texture parameter in the CamTextureMaterial material, and scale the static mesh component by the camera frame’s aspect ratio:</span></span>

```cpp
void ACamCapture::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    // Dynamic material instance only needs to be set once.
    if(IsTextureParamSet)
    {
        return;
    }

    // Get the texture from the camera.
    UARTexture* ARTexture = UARBlueprintLibrary::GetARTexture(EARTextureType::CameraImage);
    if(ARTexture != nullptr)
    {
        // Set the shader's texture parameter (named "Param") to the camera image.
        DynamicMaterial->SetTextureParameterValue("Param", ARTexture);
        IsTextureParamSet = true;

        // Get the camera instrincs
        FARCameraIntrinsics Intrinsics;
        UARBlueprintLibrary::GetCameraIntrinsics(Intrinsics);

        // Scale the camera mesh by the aspect ratio.
        float R = (float)Intrinsics.ImageResolution.X / (float)Intrinsics.ImageResolution.Y;
        StaticMeshComponent->SetWorldScale3D(FVector(0.1f, R, 1));
    }
}
```

# <a name="425"></a>[<span data-ttu-id="d6620-148">4.25</span><span class="sxs-lookup"><span data-stu-id="d6620-148">4.25</span></span>](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="d6620-149">Eseguire il rendering dalla fotocamera/videocamera per MRC</span><span class="sxs-lookup"><span data-stu-id="d6620-149">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="d6620-150">Questa operazione richiede **Unreal Engine 4.25** o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="d6620-150">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="d6620-151">Il sistema e i registratori MRC personalizzati creano acquisizioni in realtà mista combinando la fotocamera/videocamera con ologrammi sottoposti a rendering dall'app.</span><span class="sxs-lookup"><span data-stu-id="d6620-151">The system and custom MRC recorders create mixed reality captures by combining the PV Camera with holograms rendered by the app.</span></span>

<span data-ttu-id="d6620-152">Per impostazione predefinita, l'acquisizione in realtà mista usa l'output olografico dell'occhio destro.</span><span class="sxs-lookup"><span data-stu-id="d6620-152">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="d6620-153">Se un'app immersiva sceglie di [eseguire il rendering dalla fotocamera/videocamera](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), verrà usata quest'ultima.</span><span class="sxs-lookup"><span data-stu-id="d6620-153">If an immersive app chooses to [render from the PV Camera](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), then that will be used instead.</span></span> <span data-ttu-id="d6620-154">Il rendering dalla fotocamera/videocamera migliora il mapping tra il mondo reale e gli ologrammi nel video MRC.</span><span class="sxs-lookup"><span data-stu-id="d6620-154">Rendering from the PV Camera improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="d6620-155">Per acconsentire esplicitamente al rendering dalla fotocamera/videocamera:</span><span class="sxs-lookup"><span data-stu-id="d6620-155">To opt in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="d6620-156">Chiama **SetEnabledMixedRealityCamera** e **ResizeMixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="d6620-156">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="d6620-157">Usa i valori **Size X** (Dimensione X) e **Size Y** (Dimensione Y) per impostare le dimensioni video.</span><span class="sxs-lookup"><span data-stu-id="d6620-157">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Terza fotocamera](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="d6620-159">Unreal gestirà quindi le richieste da MRC per eseguire il rendering dal punto di vista della fotocamera/videocamera.</span><span class="sxs-lookup"><span data-stu-id="d6620-159">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="d6620-160">Solo quando viene attivata [Aquisizione realtà mista](/hololens/holographic-photos-and-videos) all'app verrà chiesto di eseguire il rendering dal punto di vista della fotocamera/videocamera.</span><span class="sxs-lookup"><span data-stu-id="d6620-160">Only when [Mixed Reality Capture](/hololens/holographic-photos-and-videos) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="d6620-161">Uso della fotocamera/videocamera</span><span class="sxs-lookup"><span data-stu-id="d6620-161">Using the PV Camera</span></span>

<span data-ttu-id="d6620-162">La texture della webcam può essere recuperata nel gioco in fase di runtime, ma deve essere abilitata in **Edit > Project Settings** (Modifica > Impostazioni progetto) nell'editor:</span><span class="sxs-lookup"><span data-stu-id="d6620-162">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="d6620-163">Passa a **Platforms > HoloLens > Capabilities** (Piattaforme > HoloLens > Funzionalità) e seleziona **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="d6620-163">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="d6620-164">Usa la funzione **StartCameraCapture** per usare la webcam in fase di runtime e la funzione **StopCameraCapture** per arrestare la registrazione.</span><span class="sxs-lookup"><span data-stu-id="d6620-164">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Avvio e arresto della fotocamera](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="d6620-166">Rendering di un'immagine</span><span class="sxs-lookup"><span data-stu-id="d6620-166">Rendering an image</span></span>
<span data-ttu-id="d6620-167">Per eseguire il rendering dell'immagine della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="d6620-167">To render the camera image:</span></span>
1. <span data-ttu-id="d6620-168">Crea un'istanza materiale dinamica basata su un materiale nel progetto, denominato **PVCamMat** nello screenshot seguente.</span><span class="sxs-lookup"><span data-stu-id="d6620-168">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="d6620-169">Imposta l'istanza materiale dinamica su una variabile **Material Instance Dynamic Object Reference** (Riferimento all'oggetto dinamico istanza materiale).</span><span class="sxs-lookup"><span data-stu-id="d6620-169">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="d6620-170">Imposta il materiale dell'oggetto nella scena che eseguirà il rendering del feed della fotocamera su questa nuova istanza materiale dinamica.</span><span class="sxs-lookup"><span data-stu-id="d6620-170">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="d6620-171">Avvia un timer che verrà usato per associare l'immagine della fotocamera al materiale.</span><span class="sxs-lookup"><span data-stu-id="d6620-171">Start a timer that will be used to bind the camera image to the material.</span></span>

![Rendering della fotocamera](../images/unreal-camera-render.PNG)

4. <span data-ttu-id="d6620-173">Crea una nuova funzione per questo timer, in questo caso **MaterialTimer**, e chiama **GetARCameraImage** per ottenere la texture dalla webcam.</span><span class="sxs-lookup"><span data-stu-id="d6620-173">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="d6620-174">Se la texture è valida, imposta un parametro di texture nello shader sull'immagine.</span><span class="sxs-lookup"><span data-stu-id="d6620-174">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="d6620-175">In alternativa, avvia di nuovo il timer del materiale.</span><span class="sxs-lookup"><span data-stu-id="d6620-175">Otherwise, start the material timer again.</span></span>

![Acquisire texture dalla webcam](../images/unreal-camera-texture.PNG)

5. <span data-ttu-id="d6620-177">Assicurarsi che il materiale includa un parametro corrispondente al nome in **SetTextureParameterValue** associato a una voce di colore.</span><span class="sxs-lookup"><span data-stu-id="d6620-177">Make sure the material has a parameter that matches the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="d6620-178">In mancanza di questo parametro, l'immagine della fotocamera non potrà essere visualizzata correttamente.</span><span class="sxs-lookup"><span data-stu-id="d6620-178">Without the parameter, the camera image can't be displayed properly.</span></span>

![Texture della fotocamera](../images/unreal-camera-material.PNG)