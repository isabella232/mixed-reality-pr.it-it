---
ms.openlocfilehash: e79b14c19a452b5b78c6f8cf7ea24bd65bfa0eaa
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98605305"
---
# <a name="426"></a>[4.26](#tab/426) 

## <a name="pv-camera-feed-setup"></a>Impostazione del feed della fotocamera/videocamera

> [!IMPORTANT]
> La fotocamera/videocamera è implementata nei plug-in Windows Mixed Reality e OpenXR. OpenXR, tuttavia, richiede l'installazione del [plug-in Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal). Inoltre, OpenXR presenta una limitazione corrente per cui la fotocamera può funzionare con l'interfaccia RHI DirectX11. Questa limitazione verrà eliminata in una successiva versione di Unreal. 

- In **Project Settings > HoloLens** (Impostazioni progetto) abilitare la funzionalità **Webcam**:

![Screenshot delle impostazioni di progetto HoloLens con la proprietà Webcam evidenziata](../images/unreal-pvc-img-01.png)

- Creare un nuovo attore denominato "CamCapture" e aggiungere un piano per il rendering del feed della fotocamera:

![Screenshot di un attore con un piano aggiunto](../images/unreal-pvc-img-02.png)

- Aggiungere l'attore alla scena, creare un nuovo materiale denominato CamTextureMaterial con un parametro di oggetto trama e un esempio di trama.  Inviare i dati RGB della trama al colore emissivo di output:

![Progetto di un materiale e un esempio di trama](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a>Rendering del feed della fotocamera/videocamera

- Nel progetto CamCapture attivare la fotocamera/videocamera:

![Progetto della funzione Toggle ARCapture con la fotocamera/videocamera attivata](../images/unreal-pvc-img-04.png)

- Creare un'istanza del materiale dinamico da CamTextureMaterial e assegnare questo materiale al piano dell'attore:

![Progetto della funzione Create Dynamic Material Instance](../images/unreal-pvc-img-05.png)

- Ottenere la trama dal feed della fotocamera e, se è valida, assegnarla al materiale dinamico.  Se la trama non è valida, avviare un timer e riprovare dopo il timeout:

![Progetto della trama del feed della fotocamera assegnata al materiale dinamico](../images/unreal-pvc-img-06.png)

- Infine, ridimensionare il piano in base alle proporzioni dell'immagine della fotocamera:

![Progetto del piano ridimensionato rispetto alle proporzioni delle immagini della fotocamera](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a>Trovare le posizioni della fotocamera nello spazio globale

La fotocamera in HoloLens 2 presenta uno scostamento verticale rispetto al rilevamento della testa operato dal dispositivo.  Per tenere in considerazione questo scostamento, sono disponibili alcune funzioni per individuare la fotocamera nello spazio globale.

GetPVCameraToWorldTransform ottiene la trasformazione nello spazio globale della fotocamera/videocamera e viene posizionata sull'obiettivo della fotocamera:

![Progetto della funzione Get PVCamera to World Transform](../images/unreal-pvc-img-08.png)

GetWorldSpaceRayFromCameraPoint esegue il cast di un raggio dall'obiettivo della fotocamera alla scena nello spazio globale di Unreal per trovare un contenuto di pixel presente nel frame della fotocamera:

![Progetto di Get World Space Ray from Camera Point](../images/unreal-pvc-img-09.png)

GetPVCameraIntrinsics restituisce i valori intrinseci della fotocamera, che possono essere usati quando si esegue l'elaborazione della visione artificiale su un frame della fotocamera:

![Progetto delle funzioni di Get PVCamera Intrinsics](../images/unreal-pvc-img-10.png)

Per trovare un elemento presente nello spazio globale in corrispondenza di una particolare coordinata del pixel, usare una traccia lineare con il raggio dello spazio globale:

![Progetto del raggio dello spazio globale usato per individuare un elemento presente nello spazio globale in corrispondenza di una particolare coordinata](../images/unreal-pvc-img-11.png)

A questo punto viene eseguito il cast di un raggio di 2 metri dall'obiettivo della fotocamera alla posizione dello spazio della fotocamera con uno scostamento di 1/4 dalla parte superiore sinistra del frame.  Usare quindi il risultato ottenuto per eseguire il rendering di un elemento nel punto in cui è presente l'oggetto nello spazio globale:

![Progetto del cast di un raggio di 2 metri dall'obiettivo della fotocamera alla posizione dello spazio della fotocamera con uno scostamento di 1/4 dalla parte superiore sinistra del frame](../images/unreal-pvc-img-12.png)

Quando si usa il mapping spaziale, la posizione ottenuta corrisponde alla superficie visualizzata dalla fotocamera.

## <a name="rendering-the-pv-camera-feed-in-c"></a>Rendering del feed della fotocamera/videocamera in C++

- Creare un nuovo attore C++ denominato CamCapture
- Nel file build.cs del progetto aggiungere "AugmentedReality" all'elenco PublicDependencyModuleNames:

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

- In CamCapture.h includere ARBlueprintLibrary.h

```cpp
#include "ARBlueprintLibrary.h"
```

- È anche necessario aggiungere variabili locali per la mesh e il materiale:

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- In CamCapture.cpp aggiornare il costruttore per aggiungere una mesh statica alla scena:

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

In BeginPlay creare un'istanza di materiale dinamico dal materiale della fotocamera del progetto, applicarla al componente della mesh statica e avviare la fotocamera HoloLens. 
 
Per ottenere la stringa per CameraMatPath, nell'editor fare clic con il pulsante destro del mouse su CamTextureMaterial nel browser del contenuto e selezionare "Copy Reference" (Copia riferimento).

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

In Tick ottenere la trama dalla fotocamera, impostarla sul parametro della trama nel materiale CamTextureMaterial e ridimensionare il componente della mesh statica in base alle proporzioni del frame della fotocamera:

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

# <a name="425"></a>[4.25](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a>Eseguire il rendering dalla fotocamera/videocamera per MRC

> [!NOTE]
> Questa operazione richiede **Unreal Engine 4.25** o versioni successive.

Il sistema e i registratori MRC personalizzati creano acquisizioni in realtà mista combinando la fotocamera/videocamera con ologrammi sottoposti a rendering dall'app.

Per impostazione predefinita, l'acquisizione in realtà mista usa l'output olografico dell'occhio destro. Se un'app immersiva sceglie di [eseguire il rendering dalla fotocamera/videocamera](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), verrà usata quest'ultima. Il rendering dalla fotocamera/videocamera migliora il mapping tra il mondo reale e gli ologrammi nel video MRC.

Per acconsentire esplicitamente al rendering dalla fotocamera/videocamera:

1. Chiama **SetEnabledMixedRealityCamera** e **ResizeMixedRealityCamera**.
    * Usa i valori **Size X** (Dimensione X) e **Size Y** (Dimensione Y) per impostare le dimensioni video.

![Terza fotocamera](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

Unreal gestirà quindi le richieste da MRC per eseguire il rendering dal punto di vista della fotocamera/videocamera.

> [!NOTE]
> Solo quando viene attivata [Aquisizione realtà mista](/hololens/holographic-photos-and-videos) all'app verrà chiesto di eseguire il rendering dal punto di vista della fotocamera/videocamera.

## <a name="using-the-pv-camera"></a>Uso della fotocamera/videocamera

La texture della webcam può essere recuperata nel gioco in fase di runtime, ma deve essere abilitata in **Edit > Project Settings** (Modifica > Impostazioni progetto) nell'editor:
1. Passa a **Platforms > HoloLens > Capabilities** (Piattaforme > HoloLens > Funzionalità) e seleziona **Webcam**.
    * Usa la funzione **StartCameraCapture** per usare la webcam in fase di runtime e la funzione **StopCameraCapture** per arrestare la registrazione.

![Avvio e arresto della fotocamera](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>Rendering di un'immagine
Per eseguire il rendering dell'immagine della fotocamera:
1. Crea un'istanza materiale dinamica basata su un materiale nel progetto, denominato **PVCamMat** nello screenshot seguente.  
2. Imposta l'istanza materiale dinamica su una variabile **Material Instance Dynamic Object Reference** (Riferimento all'oggetto dinamico istanza materiale).  
3. Imposta il materiale dell'oggetto nella scena che eseguirà il rendering del feed della fotocamera su questa nuova istanza materiale dinamica.
    * Avvia un timer che verrà usato per associare l'immagine della fotocamera al materiale.

![Rendering della fotocamera](../images/unreal-camera-render.PNG)

4. Crea una nuova funzione per questo timer, in questo caso **MaterialTimer**, e chiama **GetARCameraImage** per ottenere la texture dalla webcam.  
5. Se la texture è valida, imposta un parametro di texture nello shader sull'immagine.  In alternativa, avvia di nuovo il timer del materiale.

![Acquisire texture dalla webcam](../images/unreal-camera-texture.PNG)

5. Assicurarsi che il materiale includa un parametro corrispondente al nome in **SetTextureParameterValue** associato a una voce di colore. In mancanza di questo parametro, l'immagine della fotocamera non potrà essere visualizzata correttamente.

![Texture della fotocamera](../images/unreal-camera-material.PNG)