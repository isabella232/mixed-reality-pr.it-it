---
title: Fotocamera video foto in Unity
description: Informazioni su come acquisire una foto in un file o in un Texture2D, come acquisire una foto e interagire con i byte non elaborati e come acquisire un video.
author: keveleigh
ms.author: v-hferrone
ms.date: 03/21/2021
ms.topic: article
keywords: Foto, video, hololens, fotocamera, Unity, locatable, PVC, videocamera video foto, auricolare realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, webcam, acquisizione foto, acquisizione video
ms.openlocfilehash: 1cae796a793036ed59c1d0805df76cb8ac143027
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636213"
---
# <a name="photo-video-camera-in-unity"></a><span data-ttu-id="d0cb6-104">Fotocamera video foto in Unity</span><span class="sxs-lookup"><span data-stu-id="d0cb6-104">Photo Video camera in Unity</span></span>

## <a name="enabling-the-capability-for-camera-access"></a><span data-ttu-id="d0cb6-105">Abilitazione della funzionalità per l'accesso alla fotocamera</span><span class="sxs-lookup"><span data-stu-id="d0cb6-105">Enabling the capability for camera access</span></span>

<span data-ttu-id="d0cb6-106">La funzionalità "WebCam" deve essere dichiarata per l'uso della [fotocamera](../platform-capabilities-and-apis/locatable-camera.md)da parte di un'app.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-106">The "WebCam" capability must be declared for an app to use the [camera](../platform-capabilities-and-apis/locatable-camera.md).</span></span>

1. <span data-ttu-id="d0cb6-107">Nell'editor di Unity passare alle impostazioni del lettore passando alla pagina "Edit > Project Settings > Player"</span><span class="sxs-lookup"><span data-stu-id="d0cb6-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="d0cb6-108">Selezionare la scheda "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="d0cb6-108">Select the "Windows Store" tab</span></span>
3. <span data-ttu-id="d0cb6-109">Nella sezione "impostazioni di pubblicazione > funzionalità" controllare le funzionalità di **Webcam** e **microfono**</span><span class="sxs-lookup"><span data-stu-id="d0cb6-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="d0cb6-110">Con la fotocamera può essere eseguita una sola operazione alla volta.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="d0cb6-111">È possibile controllare la modalità con cui la fotocamera è attualmente disponibile `UnityEngine.XR.WSA.WebCam.Mode` in unity 2018 e versioni precedenti o `UnityEngine.Windows.WebCam.Mode` in unity 2019 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-111">You can check which mode the camera is currently in with `UnityEngine.XR.WSA.WebCam.Mode` in Unity 2018 and earlier or `UnityEngine.Windows.WebCam.Mode` in Unity 2019  and later.</span></span> <span data-ttu-id="d0cb6-112">Le modalità disponibili sono Photo, video o None.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-112">Available modes are photo, video, or none.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="d0cb6-113">Acquisizione foto</span><span class="sxs-lookup"><span data-stu-id="d0cb6-113">Photo capture</span></span>

<span data-ttu-id="d0cb6-114">**Spazio dei nomi (prima di unity 2019):** *UnityEngine. XR. WSA. Webcam*</span><span class="sxs-lookup"><span data-stu-id="d0cb6-114">**Namespace (before Unity 2019):** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="d0cb6-115">**Spazio dei nomi (unity 2019 e versioni successive):** *UnityEngine. Windows. Webcam*</span><span class="sxs-lookup"><span data-stu-id="d0cb6-115">**Namespace (Unity 2019 and later):** *UnityEngine.Windows.WebCam*</span></span><br>
<span data-ttu-id="d0cb6-116">**Tipo:** *fotoacquisizione*</span><span class="sxs-lookup"><span data-stu-id="d0cb6-116">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="d0cb6-117">Il tipo di *acquisizione* di foto consente di scattare fotografie con la fotocamera del video.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-117">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="d0cb6-118">Il modello generale per l'uso di *fotocapture* per scattare una foto è il seguente:</span><span class="sxs-lookup"><span data-stu-id="d0cb6-118">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>

1. <span data-ttu-id="d0cb6-119">Creare un oggetto di *acquisizione*</span><span class="sxs-lookup"><span data-stu-id="d0cb6-119">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="d0cb6-120">Creare un oggetto *CameraParameters* con le impostazioni desiderate</span><span class="sxs-lookup"><span data-stu-id="d0cb6-120">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="d0cb6-121">Avviare la modalità foto tramite *StartPhotoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="d0cb6-121">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="d0cb6-122">Scattare la foto desiderata</span><span class="sxs-lookup"><span data-stu-id="d0cb6-122">Take the photo you want</span></span>
    * <span data-ttu-id="d0cb6-123">opzionale Interagire con l'immagine</span><span class="sxs-lookup"><span data-stu-id="d0cb6-123">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="d0cb6-124">Arrestare la modalità foto e pulire le risorse</span><span class="sxs-lookup"><span data-stu-id="d0cb6-124">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="d0cb6-125">Configurazione comune per l'acquisizione di fotorileva</span><span class="sxs-lookup"><span data-stu-id="d0cb6-125">Common set-up for PhotoCapture</span></span>

<span data-ttu-id="d0cb6-126">Per tutti e tre gli usi, iniziare con gli stessi primi tre passaggi precedenti</span><span class="sxs-lookup"><span data-stu-id="d0cb6-126">For all three uses, start with the same first three steps above</span></span>

<span data-ttu-id="d0cb6-127">Iniziare creando un oggetto di *acquisizione*</span><span class="sxs-lookup"><span data-stu-id="d0cb6-127">Start by creating a *PhotoCapture* object</span></span>

```cs
private void Start()
{
    PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
}
```

<span data-ttu-id="d0cb6-128">Quindi, archiviare l'oggetto, impostare i parametri e avviare la modalità foto</span><span class="sxs-lookup"><span data-stu-id="d0cb6-128">Next, store your object, set your parameters, and start Photo Mode</span></span>

```cs
private PhotoCapture photoCaptureObject = null;

void OnPhotoCaptureCreated(PhotoCapture captureObject)
{
    photoCaptureObject = captureObject;

    Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

    CameraParameters c = new CameraParameters();
    c.hologramOpacity = 0.0f;
    c.cameraResolutionWidth = cameraResolution.width;
    c.cameraResolutionHeight = cameraResolution.height;
    c.pixelFormat = CapturePixelFormat.BGRA32;

    captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
}
```

<span data-ttu-id="d0cb6-129">Alla fine, si userà anche lo stesso codice di pulizia presentato qui</span><span class="sxs-lookup"><span data-stu-id="d0cb6-129">In the end, you'll also use the same clean-up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
{
    photoCaptureObject.Dispose();
    photoCaptureObject = null;
}
```

<span data-ttu-id="d0cb6-130">Dopo questa procedura, è possibile scegliere il tipo di foto da acquisire.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-130">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="d0cb6-131">Acquisire una foto in un file</span><span class="sxs-lookup"><span data-stu-id="d0cb6-131">Capture a photo to a file</span></span>

<span data-ttu-id="d0cb6-132">L'operazione più semplice consiste nell'acquisire una foto direttamente in un file.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-132">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="d0cb6-133">La foto può essere salvata come JPG o PNG.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-133">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="d0cb6-134">Se la modalità Photo è stata avviata correttamente, scattare una foto e archiviarla sul disco</span><span class="sxs-lookup"><span data-stu-id="d0cb6-134">If you successfully started photo mode, take a photo and store it on disk</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
        string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

        photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
    }
    else
    {
        Debug.LogError("Unable to start photo mode!");
    }
}
```

<span data-ttu-id="d0cb6-135">Dopo aver acquisito la foto su disco, uscire dalla modalità foto e quindi pulire gli oggetti</span><span class="sxs-lookup"><span data-stu-id="d0cb6-135">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        Debug.Log("Saved Photo to disk!");
        photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
    }
    else
    {
        Debug.Log("Failed to save Photo to disk");
    }
}
```

### <a name="capture-a-photo-to-a-texture2d-with-location"></a><span data-ttu-id="d0cb6-136">Acquisisci una foto in una Texture2D con percorso</span><span class="sxs-lookup"><span data-stu-id="d0cb6-136">Capture a photo to a Texture2D with location</span></span>

<span data-ttu-id="d0cb6-137">Quando si acquisiscono dati in un Texture2D, il processo è simile all'acquisizione su disco.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-137">When capturing data to a Texture2D, the process is similar to capturing to disk.</span></span>

<span data-ttu-id="d0cb6-138">Seguire il processo di configurazione precedente.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-138">Follow the setup process above.</span></span>

<span data-ttu-id="d0cb6-139">In *OnPhotoModeStarted* acquisire un frame in memoria.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-139">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
    }
    else
    {
        Debug.LogError("Unable to start photo mode!");
    }
}
```

<span data-ttu-id="d0cb6-140">Si applicherà quindi il risultato a una trama e si userà il codice di pulizia comune riportato sopra.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-140">You'll then apply your result to a texture and use the common clean-up code above.</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
{
    if (result.success)
    {
        // Create our Texture2D for use and set the correct resolution
        Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
        Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
        // Copy the raw image data into our target texture
        photoCaptureFrame.UploadImageDataToTexture(targetTexture);
        // Do as we wish with the texture such as apply it to a material, etc.
    }
    // Clean up
    photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
}
```

#### <a name="locatable-camera"></a><span data-ttu-id="d0cb6-141">Fotocamera individuabile</span><span class="sxs-lookup"><span data-stu-id="d0cb6-141">Locatable camera</span></span>

<span data-ttu-id="d0cb6-142">Per inserire questa trama nella scena e visualizzarla usando le matrici della fotocamera locatable, aggiungere il codice seguente a *OnCapturedPhotoToMemory* nel `result.success` controllo:</span><span class="sxs-lookup"><span data-stu-id="d0cb6-142">To place this texture in the scene and display it using the locatable camera matrices, add the following code to *OnCapturedPhotoToMemory* in the `result.success` check:</span></span>

```cs
if (photoCaptureFrame.hasLocationData)
{
    photoCaptureFrame.TryGetCameraToWorldMatrix(out Matrix4x4 cameraToWorldMatrix);

    Vector3 position = cameraToWorldMatrix.GetColumn(3) - cameraToWorldMatrix.GetColumn(2);
    Quaternion rotation = Quaternion.LookRotation(-cameraToWorldMatrix.GetColumn(2), cameraToWorldMatrix.GetColumn(1));

    photoCaptureFrame.TryGetProjectionMatrix(Camera.main.nearClipPlane, Camera.main.farClipPlane, out Matrix4x4 projectionMatrix);
}
```

<span data-ttu-id="d0cb6-143">[Unity ha fornito il codice di esempio](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) per applicare la matrice di proiezione a uno shader specifico nei forum.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-143">[Unity has provided sample code](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) for applying the projection matrix to a specific shader on their forums.</span></span>

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="d0cb6-144">Acquisisci una foto e interagisci con i byte non elaborati</span><span class="sxs-lookup"><span data-stu-id="d0cb6-144">Capture a photo and interact with the raw bytes</span></span>

<span data-ttu-id="d0cb6-145">Per interagire con i byte non elaborati di un frame in memoria, seguire gli stessi passaggi di installazione indicati in precedenza e *OnPhotoModeStarted* come per acquisire una foto in un Texture2D.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-145">To interact with the raw bytes of an in memory frame, follow the same setup steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="d0cb6-146">La differenza si trova in *OnCapturedPhotoToMemory* , in cui è possibile ottenere i byte non elaborati e interagire con essi.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-146">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="d0cb6-147">In questo esempio verrà creato un *elenco <Color>* che verrà ulteriormente elaborato o applicato a una trama tramite *sepixels ()*</span><span class="sxs-lookup"><span data-stu-id="d0cb6-147">In this example, you'll create a *List<Color>* to be further processed or applied to a texture via *SetPixels()*</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
{
    if (result.success)
    {
        List<byte> imageBufferList = new List<byte>();
        // Copy the raw IMFMediaBuffer data into our empty byte list.
        photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

        // In this example, we captured the image using the BGRA32 format.
        // So our stride will be 4 since we have a byte for each rgba channel.
        // The raw image data will also be flipped so we access our pixel data
        // in the reverse order.
        int stride = 4;
        float denominator = 1.0f / 255.0f;
        List<Color> colorArray = new List<Color>();
        for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
        {
            float a = (int)(imageBufferList[i - 0]) * denominator;
            float r = (int)(imageBufferList[i - 1]) * denominator;
            float g = (int)(imageBufferList[i - 2]) * denominator;
            float b = (int)(imageBufferList[i - 3]) * denominator;

            colorArray.Add(new Color(r, g, b, a));
        }
        // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
    }
    photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
}
```

## <a name="video-capture"></a><span data-ttu-id="d0cb6-148">Acquisizione video</span><span class="sxs-lookup"><span data-stu-id="d0cb6-148">Video capture</span></span>

<span data-ttu-id="d0cb6-149">**Spazio dei nomi (prima di unity 2019):** *UnityEngine. XR. WSA. Webcam*</span><span class="sxs-lookup"><span data-stu-id="d0cb6-149">**Namespace (before Unity 2019):** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="d0cb6-150">**Spazio dei nomi (unity 2019 e versioni successive):** *UnityEngine. Windows. Webcam*</span><span class="sxs-lookup"><span data-stu-id="d0cb6-150">**Namespace (Unity 2019 and later):** *UnityEngine.Windows.WebCam*</span></span><br>
<span data-ttu-id="d0cb6-151">**Tipo:** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="d0cb6-151">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="d0cb6-152">*VideoCapture* funziona in modo analogo alla *fotoacquisizione*.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-152">*VideoCapture* functions similarly to *PhotoCapture*.</span></span> <span data-ttu-id="d0cb6-153">Le uniche due differenze sono che è necessario specificare un valore per i frame al secondo (FPS) ed è possibile salvare direttamente sul disco come file con estensione MP4.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-153">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as a .mp4 file.</span></span> <span data-ttu-id="d0cb6-154">I passaggi per usare *VideoCapture* sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="d0cb6-154">The steps to use *VideoCapture* are as follows:</span></span>

1. <span data-ttu-id="d0cb6-155">Creare un oggetto *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="d0cb6-155">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="d0cb6-156">Creare un oggetto *CameraParameters* con le impostazioni desiderate</span><span class="sxs-lookup"><span data-stu-id="d0cb6-156">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="d0cb6-157">Avviare la modalità video tramite *StartVideoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="d0cb6-157">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="d0cb6-158">Avviare la registrazione del video</span><span class="sxs-lookup"><span data-stu-id="d0cb6-158">Start recording video</span></span>
5. <span data-ttu-id="d0cb6-159">Interrompi registrazione video</span><span class="sxs-lookup"><span data-stu-id="d0cb6-159">Stop recording video</span></span>
6. <span data-ttu-id="d0cb6-160">Arrestare la modalità video e pulire le risorse</span><span class="sxs-lookup"><span data-stu-id="d0cb6-160">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="d0cb6-161">Per iniziare, creare l'oggetto *VideoCapture* *VideoCapture m_VideoCapture = null;*</span><span class="sxs-lookup"><span data-stu-id="d0cb6-161">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
{
    VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
}
```

<span data-ttu-id="d0cb6-162">Successivamente, impostare i parametri da usare per la registrazione e avviare.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-162">Next, set up the parameters you'll want for the recording and start.</span></span>

```cs
void OnVideoCaptureCreated(VideoCapture videoCapture)
{
    if (videoCapture != null)
    {
        m_VideoCapture = videoCapture;

        Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
        float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

        CameraParameters cameraParameters = new CameraParameters();
        cameraParameters.hologramOpacity = 0.0f;
        cameraParameters.frameRate = cameraFramerate;
        cameraParameters.cameraResolutionWidth = cameraResolution.width;
        cameraParameters.cameraResolutionHeight = cameraResolution.height;
        cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

        m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                            VideoCapture.AudioState.None,
                                            OnStartedVideoCaptureMode);
    }
    else
    {
        Debug.LogError("Failed to create VideoCapture Instance!");
    }
}
```

<span data-ttu-id="d0cb6-163">Una volta avviata, iniziare la registrazione</span><span class="sxs-lookup"><span data-stu-id="d0cb6-163">Once started, begin the recording</span></span>

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
{
    if (result.success)
    {
        string filename = string.Format("MyVideo_{0}.mp4", Time.time);
        string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

        m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
    }
}
```

<span data-ttu-id="d0cb6-164">Dopo l'avvio della registrazione, è possibile aggiornare l'interfaccia utente o i comportamenti per consentire l'arresto.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-164">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="d0cb6-165">Qui è sufficiente eseguire il log.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-165">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Started Recording Video!");
    // We will stop the video from recording via other input such as a timer or a tap, etc.
}
```

<span data-ttu-id="d0cb6-166">In un secondo momento, è necessario arrestare la registrazione usando un timer o un input utente, ad esempio.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-166">At a later point, you'll want to stop the recording using a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
void StopRecordingVideo()
{
    m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
}
```

<span data-ttu-id="d0cb6-167">Dopo che la registrazione è stata interrotta, arrestare la modalità video e pulire le risorse.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-167">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Stopped Recording Video!");
    m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
}

void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
{
    m_VideoCapture.Dispose();
    m_VideoCapture = null;
}
```

## <a name="troubleshooting"></a><span data-ttu-id="d0cb6-168">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="d0cb6-168">Troubleshooting</span></span>

* <span data-ttu-id="d0cb6-169">Non sono disponibili risoluzioni</span><span class="sxs-lookup"><span data-stu-id="d0cb6-169">No resolutions are available</span></span>
  * <span data-ttu-id="d0cb6-170">Verificare che la funzionalità **Webcam** sia specificata nel progetto.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-170">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="d0cb6-171">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="d0cb6-171">Next Development Checkpoint</span></span>

<span data-ttu-id="d0cb6-172">Se si segue il percorso di checkpoint per lo sviluppo di Unity, è possibile esplorare le funzionalità e le API della piattaforma per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-172">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="d0cb6-173">Da qui, è possibile passare all'argomento successivo:</span><span class="sxs-lookup"><span data-stu-id="d0cb6-173">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d0cb6-174">Punto di interesse</span><span class="sxs-lookup"><span data-stu-id="d0cb6-174">Focus point</span></span>](focus-point-in-unity.md)

<span data-ttu-id="d0cb6-175">In alternativa, passare direttamente alla distribuzione dell'app in un dispositivo o emulatore:</span><span class="sxs-lookup"><span data-stu-id="d0cb6-175">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d0cb6-176">Eseguire la distribuzione in HoloLens o in modalità mista di Windows per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="d0cb6-176">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="d0cb6-177">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#3-advanced-features) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="d0cb6-177">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0cb6-178">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d0cb6-178">See Also</span></span>

* [<span data-ttu-id="d0cb6-179">Fotocamera individuabile</span><span class="sxs-lookup"><span data-stu-id="d0cb6-179">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)