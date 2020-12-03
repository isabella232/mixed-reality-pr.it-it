---
ms.openlocfilehash: 5952cf94ba07a6d92903050a2a813cc911d4d70f
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354678"
---
# <a name="425"></a>[<span data-ttu-id="0cac1-101">4.25</span><span class="sxs-lookup"><span data-stu-id="0cac1-101">4.25</span></span>](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="0cac1-102">Eseguire il rendering dalla fotocamera/videocamera per MRC</span><span class="sxs-lookup"><span data-stu-id="0cac1-102">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="0cac1-103">Questa operazione richiede **Unreal Engine 4.25** o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="0cac1-103">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="0cac1-104">Il sistema e i registratori MRC personalizzati creano acquisizioni in realtà mista combinando la fotocamera/videocamera con ologrammi sottoposti a rendering dall'app immersiva.</span><span class="sxs-lookup"><span data-stu-id="0cac1-104">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="0cac1-105">Per impostazione predefinita, l'acquisizione in realtà mista usa l'output olografico dell'occhio destro.</span><span class="sxs-lookup"><span data-stu-id="0cac1-105">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="0cac1-106">Se un'app immersiva sceglie di [eseguire il rendering dalla fotocamera/videocamera](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), verrà usata quest'ultima.</span><span class="sxs-lookup"><span data-stu-id="0cac1-106">If an immersive app chooses to [render from the PV Camera](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="0cac1-107">Ciò migliora il mapping tra il mondo reale e gli ologrammi nel video MRC.</span><span class="sxs-lookup"><span data-stu-id="0cac1-107">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="0cac1-108">Per acconsentire esplicitamente al rendering dalla fotocamera/videocamera:</span><span class="sxs-lookup"><span data-stu-id="0cac1-108">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="0cac1-109">Chiama **SetEnabledMixedRealityCamera** e **ResizeMixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="0cac1-109">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="0cac1-110">Usa i valori **Size X** (Dimensione X) e **Size Y** (Dimensione Y) per impostare le dimensioni video.</span><span class="sxs-lookup"><span data-stu-id="0cac1-110">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Terza fotocamera](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="0cac1-112">Unreal gestirà quindi le richieste da MRC per eseguire il rendering dal punto di vista della fotocamera/videocamera.</span><span class="sxs-lookup"><span data-stu-id="0cac1-112">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="0cac1-113">Solo quando viene attivata [Aquisizione realtà mista](../../../mixed-reality-capture.md) all'app verrà chiesto di eseguire il rendering dal punto di vista della fotocamera/videocamera.</span><span class="sxs-lookup"><span data-stu-id="0cac1-113">Only when [Mixed Reality Capture](../../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="0cac1-114">Uso della fotocamera/videocamera</span><span class="sxs-lookup"><span data-stu-id="0cac1-114">Using the PV Camera</span></span>

<span data-ttu-id="0cac1-115">La texture della webcam può essere recuperata nel gioco in fase di runtime, ma deve essere abilitata in **Edit > Project Settings** (Modifica > Impostazioni progetto) nell'editor:</span><span class="sxs-lookup"><span data-stu-id="0cac1-115">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="0cac1-116">Passa a **Platforms > HoloLens > Capabilities** (Piattaforme > HoloLens > Funzionalità) e seleziona **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="0cac1-116">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="0cac1-117">Usa la funzione **StartCameraCapture** per usare la webcam in fase di runtime e la funzione **StopCameraCapture** per arrestare la registrazione.</span><span class="sxs-lookup"><span data-stu-id="0cac1-117">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Avvio e arresto della fotocamera](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="0cac1-119">Rendering di un'immagine</span><span class="sxs-lookup"><span data-stu-id="0cac1-119">Rendering an image</span></span>
<span data-ttu-id="0cac1-120">Per eseguire il rendering dell'immagine della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="0cac1-120">To render the camera image:</span></span>
1. <span data-ttu-id="0cac1-121">Crea un'istanza materiale dinamica basata su un materiale nel progetto, denominato **PVCamMat** nello screenshot seguente.</span><span class="sxs-lookup"><span data-stu-id="0cac1-121">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="0cac1-122">Imposta l'istanza materiale dinamica su una variabile **Material Instance Dynamic Object Reference** (Riferimento all'oggetto dinamico istanza materiale).</span><span class="sxs-lookup"><span data-stu-id="0cac1-122">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="0cac1-123">Imposta il materiale dell'oggetto nella scena che eseguirà il rendering del feed della fotocamera su questa nuova istanza materiale dinamica.</span><span class="sxs-lookup"><span data-stu-id="0cac1-123">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="0cac1-124">Avvia un timer che verrà usato per associare l'immagine della fotocamera al materiale.</span><span class="sxs-lookup"><span data-stu-id="0cac1-124">Start a timer that will be used to bind the camera image to the material.</span></span>

![Rendering della fotocamera](../images/unreal-camera-render.PNG)

4. <span data-ttu-id="0cac1-126">Crea una nuova funzione per questo timer, in questo caso **MaterialTimer**, e chiama **GetARCameraImage** per ottenere la texture dalla webcam.</span><span class="sxs-lookup"><span data-stu-id="0cac1-126">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="0cac1-127">Se la texture è valida, imposta un parametro di texture nello shader sull'immagine.</span><span class="sxs-lookup"><span data-stu-id="0cac1-127">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="0cac1-128">In alternativa, avvia di nuovo il timer del materiale.</span><span class="sxs-lookup"><span data-stu-id="0cac1-128">Otherwise, start the material timer again.</span></span>

![Acquisire texture dalla webcam](../images/unreal-camera-texture.PNG)

5. <span data-ttu-id="0cac1-130">Assicurati che il materiale includa un parametro corrispondente al nome in **SetTextureParameterValue** associato a una voce di colore.</span><span class="sxs-lookup"><span data-stu-id="0cac1-130">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="0cac1-131">In mancanza di questo parametro, l'immagine della fotocamera non potrà essere visualizzata correttamente.</span><span class="sxs-lookup"><span data-stu-id="0cac1-131">Without this, the camera image can't be properly displayed.</span></span>

![Texture della fotocamera](../images/unreal-camera-material.PNG)

# <a name="426"></a>[<span data-ttu-id="0cac1-133">4.26</span><span class="sxs-lookup"><span data-stu-id="0cac1-133">4.26</span></span>](#tab/426) 

## <a name="pv-camera-feed-setup"></a><span data-ttu-id="0cac1-134">Impostazione del feed della fotocamera/videocamera</span><span class="sxs-lookup"><span data-stu-id="0cac1-134">PV Camera Feed Setup</span></span>

- <span data-ttu-id="0cac1-135">In **Project Settings > HoloLens** (Impostazioni progetto) abilitare la funzionalità **Webcam**:</span><span class="sxs-lookup"><span data-stu-id="0cac1-135">In **Project Settings > HoloLens**, enable the **Webcam** capability:</span></span>

![Screenshot delle impostazioni di progetto HoloLens con la proprietà Webcam evidenziata](../images/unreal-pvc-img-01.png)

- <span data-ttu-id="0cac1-137">Creare un nuovo attore denominato "CamCapture" e aggiungere un piano per il rendering del feed della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="0cac1-137">Create a new actor called “CamCapture” and add a plane to render the camera feed:</span></span>

![Screenshot di un attore con un piano aggiunto](../images/unreal-pvc-img-02.png)

- <span data-ttu-id="0cac1-139">Aggiungere l'attore alla scena, creare un nuovo materiale denominato CamTextureMaterial con un parametro di oggetto trama e un esempio di trama.</span><span class="sxs-lookup"><span data-stu-id="0cac1-139">Add the actor to your scene, create a new material called CamTextureMaterial with a Texture Object Parameter, and a texture sample.</span></span>  <span data-ttu-id="0cac1-140">Inviare i dati RGB della trama al colore emissivo di output:</span><span class="sxs-lookup"><span data-stu-id="0cac1-140">Send the texture’s rgb data to the output emissive color:</span></span>

![Progetto di un materiale e un esempio di trama](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a><span data-ttu-id="0cac1-142">Rendering del feed della fotocamera/videocamera</span><span class="sxs-lookup"><span data-stu-id="0cac1-142">Rendering the PV Camera Feed</span></span>

- <span data-ttu-id="0cac1-143">Nel progetto CamCapture attivare la fotocamera/videocamera:</span><span class="sxs-lookup"><span data-stu-id="0cac1-143">In the CamCapture blueprint, turn the PV Camera on:</span></span>

![Progetto della funzione Toggle ARCapture con la fotocamera/videocamera attivata](../images/unreal-pvc-img-04.png)

- <span data-ttu-id="0cac1-145">Creare un'istanza del materiale dinamico da CamTextureMaterial e assegnare questo materiale al piano dell'attore:</span><span class="sxs-lookup"><span data-stu-id="0cac1-145">Create a dynamic material instance from CamTextureMaterial and assign this material to the actor’s plane:</span></span>

![Progetto della funzione Create Dynamic Material Instance](../images/unreal-pvc-img-05.png)

- <span data-ttu-id="0cac1-147">Ottenere la trama dal feed della fotocamera e, se è valida, assegnarla al materiale dinamico.</span><span class="sxs-lookup"><span data-stu-id="0cac1-147">Get the texture from the camera feed and assign it to the dynamic material if it is valid.</span></span>  <span data-ttu-id="0cac1-148">Se la trama non è valida, avviare un timer e riprovare dopo il timeout:</span><span class="sxs-lookup"><span data-stu-id="0cac1-148">If the texture is not valid, start a timer and try again after the timeout:</span></span>

![Progetto della trama del feed della fotocamera assegnata al materiale dinamico](../images/unreal-pvc-img-06.png)

- <span data-ttu-id="0cac1-150">Infine, ridimensionare il piano in base alle proporzioni dell'immagine della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="0cac1-150">Finally, scale the plane by the camera image’s aspect ratio:</span></span>

![Progetto del piano ridimensionato rispetto alle proporzioni delle immagini della fotocamera](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a><span data-ttu-id="0cac1-152">Trovare le posizioni della fotocamera nello spazio globale</span><span class="sxs-lookup"><span data-stu-id="0cac1-152">Find Camera Positions in World Space</span></span>

<span data-ttu-id="0cac1-153">La fotocamera in HoloLens 2 presenta uno scostamento verticale rispetto al rilevamento della testa operato dal dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cac1-153">The camera on the HoloLens 2 is offset vertically from the device’s head tracking.</span></span>  <span data-ttu-id="0cac1-154">Per tenere in considerazione questo aspetto, sono disponibili alcune funzioni per individuare la fotocamera nello spazio globale.</span><span class="sxs-lookup"><span data-stu-id="0cac1-154">To account for this, a few functions exist to locate the camera in world space.</span></span>

<span data-ttu-id="0cac1-155">GetPVCameraToWorldTransform ottiene la trasformazione della fotocamera/videocamera nello spazio globale.</span><span class="sxs-lookup"><span data-stu-id="0cac1-155">GetPVCameraToWorldTransform gets the transform in world space of the PVCamera.</span></span>  <span data-ttu-id="0cac1-156">Tale trasformazione verrà posizionata sull'obiettivo della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="0cac1-156">This will be positioned on the camera lens:</span></span>

![Progetto della funzione Get PVCamera to World Transform](../images/unreal-pvc-img-08.png)

<span data-ttu-id="0cac1-158">GetWorldSpaceRayFromCameraPoint esegue il cast di un raggio dall'obiettivo dalla fotocamera alla scena nello spazio globale di Unreal per trovare un elemento presente in un particolare pixel del frame della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="0cac1-158">GetWorldSpaceRayFromCameraPoint casts a ray from the camera lens into the scene in Unreal world space to find what is on a particular pixel in the camera frame:</span></span>

![Progetto di Get World Space Ray from Camera Point](../images/unreal-pvc-img-09.png)

<span data-ttu-id="0cac1-160">GetPVCameraIntrinsics restituisce i valori intrinseci della fotocamera, che possono essere usati quando si esegue l'elaborazione della visione artificiale su un frame della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="0cac1-160">GetPVCameraIntrinsics returns the camera intrinsic values, which can be used when doing computer vision processing on a camera frame:</span></span>

![Progetto delle funzioni di Get PVCamera Intrinsics](../images/unreal-pvc-img-10.png)

<span data-ttu-id="0cac1-162">Per trovare un elemento presente nello spazio globale in corrispondenza di una particolare coordinata del pixel, è possibile usare una traccia lineare con il raggio dello spazio globale:</span><span class="sxs-lookup"><span data-stu-id="0cac1-162">To find what exists in world space at a particular pixel coordinate, you can use a line trace with the world space ray:</span></span>

![Progetto del raggio dello spazio globale usato per individuare un elemento presente nello spazio globale in corrispondenza di una particolare coordinata](../images/unreal-pvc-img-11.png)

<span data-ttu-id="0cac1-164">A questo punto viene eseguito il cast di un raggio di 2 metri dall'obiettivo della fotocamera alla posizione dello spazio della fotocamera con uno scostamento di 1/4 dalla parte superiore sinistra del frame.</span><span class="sxs-lookup"><span data-stu-id="0cac1-164">Here we cast a 2-meter ray from the camera lens to the camera-space position ¼ from the top left of the frame.</span></span>  <span data-ttu-id="0cac1-165">Usare quindi il risultato ottenuto per eseguire il rendering di un elemento nel punto in cui è presente l'oggetto nello spazio globale:</span><span class="sxs-lookup"><span data-stu-id="0cac1-165">Then use the hit result to render something where the object exists in world space:</span></span>

![Progetto del cast di un raggio di 2 metri dall'obiettivo della fotocamera alla posizione dello spazio della fotocamera con uno scostamento di 1/4 dalla parte superiore sinistra del frame](../images/unreal-pvc-img-12.png)

<span data-ttu-id="0cac1-167">Quando si usa il mapping spaziale, la posizione ottenuta corrisponde alla superficie visualizzata dalla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="0cac1-167">When using spatial mapping, this hit position will match the surface that the camera is seeing.</span></span>

## <a name="rendering-the-pv-camera-feed-in-c"></a><span data-ttu-id="0cac1-168">Rendering del feed della fotocamera/videocamera in C++</span><span class="sxs-lookup"><span data-stu-id="0cac1-168">Rendering the PV Camera Feed in C++</span></span>

- <span data-ttu-id="0cac1-169">Creare un nuovo attore C++ denominato CamCapture</span><span class="sxs-lookup"><span data-stu-id="0cac1-169">Create a new C++ actor called CamCapture</span></span>
- <span data-ttu-id="0cac1-170">Nel file build.cs del progetto aggiungere "AugmentedReality" all'elenco PublicDependencyModuleNames:</span><span class="sxs-lookup"><span data-stu-id="0cac1-170">In the project’s build.cs, add “AugmentedReality” to the PublicDependencyModuleNames list:</span></span>

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

- <span data-ttu-id="0cac1-171">In CamCapture.h includere ARBlueprintLibrary.h</span><span class="sxs-lookup"><span data-stu-id="0cac1-171">In CamCapture.h, include ARBlueprintLibrary.h</span></span>

```cpp
#include "ARBlueprintLibrary.h"
```

- <span data-ttu-id="0cac1-172">È anche necessario aggiungere variabili locali per la mesh e il materiale:</span><span class="sxs-lookup"><span data-stu-id="0cac1-172">You also need to add local variables for the mesh and material:</span></span>

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- <span data-ttu-id="0cac1-173">In CamCapture.cpp aggiornare il costruttore per aggiungere una mesh statica alla scena:</span><span class="sxs-lookup"><span data-stu-id="0cac1-173">In CamCapture.cpp, update the constructor to add a static mesh to the scene:</span></span>

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

<span data-ttu-id="0cac1-174">In BeginPlay creare un'istanza di materiale dinamico dal materiale della fotocamera del progetto, applicarla al componente della mesh statica e avviare la fotocamera HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0cac1-174">In BeginPlay create a dynamic material instance from the project’s camera material, apply it to the static mesh component, and start the HoloLens camera.</span></span> 
 
<span data-ttu-id="0cac1-175">Nell'editor fare clic con il pulsante destro del mouse su CamTextureMaterial nel browser del contenuto e selezionare "Copy Reference" (Copia riferimento) per ottenere la stringa per CameraMatPath.</span><span class="sxs-lookup"><span data-stu-id="0cac1-175">In the editor, right click on the CamTextureMaterial in the content browser and select “Copy Reference” to get the string for CameraMatPath.</span></span>

```cpp
void ACamCapture::BeginPlay()
{
    Super::BeginPlay();

    // Create a dynamic material instance from the game's camera material.
    // Right-click on a material in the project and select "Copy Reference" to get this string.
    FString CameraMatPath("Material'/Game/Materials/CamTextureMaterial.CamTextureMaterial'");
    UMaterial* BaseMateriall = (UMaterial*)StaticLoadObject(UMaterial::StaticClass(), nullptr, *CameraMatPath, nullptr, LOAD_None, nullptr);
    DynamicMaterial = UMaterialInstanceDynamic::Create(BaseMaterial, this);

    // Use the dynamic material instance when rendering the camera mesh.
    StaticMeshComponent->SetMaterial(0, DynamicMaterial);

    // Start the webcam.
    UARBlueprintLibrary::ToggleARCapture(true, EARCaptureType::Camera);
}
```

<span data-ttu-id="0cac1-176">In Tick ottenere la trama dalla fotocamera, impostarla sul parametro della trama nel materiale CamTextureMaterial e ridimensionare il componente della mesh statica in base alle proporzioni del frame della fotocamera:</span><span class="sxs-lookup"><span data-stu-id="0cac1-176">In Tick get the texture from the camera, set it to the texture parameter in the CamTextureMaterial material, and scale the static mesh component by the camera frame’s aspect ratio:</span></span>

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

