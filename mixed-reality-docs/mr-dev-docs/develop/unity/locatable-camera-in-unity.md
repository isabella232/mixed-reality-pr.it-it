---
title: Fotocamera con foto in Unity
description: Informazioni su come acquisire una foto in un file o in un oggetto Texture2D, come acquisire una foto e interagire con i byte non elaborati e come acquisire un video.
author: keveleigh
ms.author: v-hferrone
ms.date: 03/21/2021
ms.topic: article
keywords: foto, video, hololens, fotocamera, unity, localizzatore, PVC, fotocamera, visore di realtà mista, visore di realtà mista windows, visore di realtà virtuale, webcam, acquisizione di foto, acquisizione video
ms.openlocfilehash: 4fdf895e6b2b7ed1fc051b45b07ce49052f8a95587178caddfc71a0cfd364eee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193505"
---
# <a name="photo-video-camera-in-unity"></a>Fotocamera con foto in Unity

## <a name="enabling-the-capability-for-camera-access"></a>Abilitazione della funzionalità per l'accesso alla fotocamera

La funzionalità "WebCam" deve essere dichiarata perché un'app usi la [fotocamera](../platform-capabilities-and-apis/locatable-camera.md).

1. Nell'editor unity passare alle impostazioni del lettore passando alla pagina "Modifica > Project Impostazioni > lettore"
2. Selezionare la scheda "Windows Store"
3. Nella sezione "Funzionalità di Impostazioni > pubblicazione" controllare le **funzionalità WebCam** e **microfono**

Con la fotocamera è possibile eseguire una sola operazione alla volta. È possibile controllare la modalità in cui si trova attualmente la fotocamera in Unity 2018 e versioni precedenti o `UnityEngine.XR.WSA.WebCam.Mode` `UnityEngine.Windows.WebCam.Mode` in Unity 2019 e versioni successive. Le modalità disponibili sono foto, video o nessuna.

## <a name="photo-capture"></a>Acquisizione di foto

**Spazio dei nomi (prima di Unity 2019):** *UnityEngine.XR.WSA.WebCam*<br>
**Spazio dei nomi (Unity 2019 e versioni successive):** *UnityEngine.Windows. WebCam*<br>
**Tipo:** *PhotoCapture*

Il *tipo PhotoCapture* consente di scattare foto con la fotocamera. Il modello generale per *l'uso di PhotoCapture* per scattare una foto è il seguente:

1. Creare un *oggetto PhotoCapture*
2. Creare un *oggetto CameraParameters* con le impostazioni desiderate
3. Avviare la modalità foto tramite *StartPhotoModeAsync*
4. Scattare la foto desiderata
    * (facoltativo) Interagire con tale immagine
5. Arrestare la modalità foto e pulire le risorse

### <a name="common-set-up-for-photocapture"></a>Configurazione comune per PhotoCapture

Per tutti e tre gli usi, iniziare con gli stessi primi tre passaggi precedenti

Iniziare creando un *oggetto PhotoCapture*

```cs
private void Start()
{
    PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
}
```

Archiviare quindi l'oggetto, impostare i parametri e avviare la modalità foto

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

Alla fine, si userà anche lo stesso codice di pulizia presentato qui

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
{
    photoCaptureObject.Dispose();
    photoCaptureObject = null;
}
```

Dopo questi passaggi, è possibile scegliere il tipo di foto da acquisire.

### <a name="capture-a-photo-to-a-file"></a>Acquisire una foto in un file

L'operazione più semplice è acquisire una foto direttamente in un file. La foto può essere salvata come JPG o PNG.

Se la modalità foto è stata avviata correttamente, scattare una foto e archiviarla su disco

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

Dopo aver acquisito la foto su disco, uscire dalla modalità foto e quindi pulire gli oggetti

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

### <a name="capture-a-photo-to-a-texture2d-with-location"></a>Acquisire una foto in un oggetto Texture2D con posizione

Quando si acquisisce dati in un oggetto Texture2D, il processo è simile all'acquisizione su disco.

Seguire il processo di configurazione precedente.

In *OnPhotoModeStarted* acquisire un frame in memoria.

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

Si applierà quindi il risultato a una trama e si userà il codice di pulizia comune precedente.

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

#### <a name="locatable-camera"></a>Fotocamera individuabile

Per inserire questa trama nella scena e visualizzarla usando le matrici di fotocamera localizzate, aggiungere il codice seguente a *OnCapturedPhotoToMemory* nel `result.success` controllo :

```cs
if (photoCaptureFrame.hasLocationData)
{
    photoCaptureFrame.TryGetCameraToWorldMatrix(out Matrix4x4 cameraToWorldMatrix);

    Vector3 position = cameraToWorldMatrix.GetColumn(3) - cameraToWorldMatrix.GetColumn(2);
    Quaternion rotation = Quaternion.LookRotation(-cameraToWorldMatrix.GetColumn(2), cameraToWorldMatrix.GetColumn(1));

    photoCaptureFrame.TryGetProjectionMatrix(Camera.main.nearClipPlane, Camera.main.farClipPlane, out Matrix4x4 projectionMatrix);
}
```

[Unity ha fornito codice di esempio](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) per l'applicazione della matrice di proiezione a uno shader specifico nei forum.

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Acquisire una foto e interagire con i byte non elaborati

Per interagire con i byte non elaborati di un frame in memoria, seguire la stessa procedura di configurazione descritta in precedenza e *OnPhotoModeStarted* come nell'acquisizione di una foto in un oggetto Texture2D. La differenza è in *OnCapturedPhotoToMemory* in cui è possibile ottenere i byte non elaborati e interagire con essi.

In questo esempio si creerà un *elenco <Color>* da elaborare ulteriormente o applicare a una trama tramite *SetPixels()*

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

## <a name="video-capture"></a>Acquisizione video

**Spazio dei nomi (prima di Unity 2019):** *UnityEngine.XR.WSA.WebCam*<br>
**Spazio dei nomi (Unity 2019 e versioni successive):** *UnityEngine.Windows. WebCam*<br>
**Tipo:** *VideoCapture*

*VideoCapture* funziona in modo simile a *PhotoCapture.* Le uniche due differenze sono che è necessario specificare un valore FpS (Frames Per Second) ed è possibile salvare direttamente su disco solo come .mp4 file. La procedura per usare *VideoCapture* è la seguente:

1. Creare un *oggetto VideoCapture*
2. Creare un *oggetto CameraParameters* con le impostazioni desiderate
3. Avviare la modalità video *tramite StartVideoModeAsync*
4. Avviare la registrazione di video
5. Arrestare la registrazione di video
6. Arrestare la modalità video ed eliminare le risorse

Per iniziare, creare *l'oggetto VideoCapture* *VideoCapture m_VideoCapture = null;*

```cs
void Start ()
{
    VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
}
```

Configurare quindi i parametri desiderati per la registrazione e l'avvio.

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

Una volta avviata, iniziare la registrazione

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

Dopo l'avvio della registrazione, è possibile aggiornare l'interfaccia utente o i comportamenti per abilitare l'arresto. Qui è sufficiente eseguire la registrazione.

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Started Recording Video!");
    // We will stop the video from recording via other input such as a timer or a tap, etc.
}
```

In un secondo momento, si vorrà arrestare la registrazione usando un timer o un input utente, ad esempio.

```cs
// The user has indicated to stop recording
void StopRecordingVideo()
{
    m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
}
```

Una volta arrestata la registrazione, arrestare la modalità video e pulire le risorse.

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

## <a name="troubleshooting"></a>Risoluzione dei problemi

* Non sono disponibili soluzioni
  * Verificare che **la funzionalità WebCam** sia specificata nel progetto.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di checkpoint di sviluppo unity che è stato previsto, si sta esplorando le API e le funzionalità della piattaforma di realtà mista. Da qui, è possibile passare all'argomento successivo:

> [!div class="nextstepaction"]
> [Punto di interesse](focus-point-in-unity.md)

In alternativa, passare direttamente alla distribuzione dell'app in un dispositivo o emulatore:

> [!div class="nextstepaction"]
> [Distribuire in HoloLens o Windows Mixed Reality visori immersive](../platform-capabilities-and-apis/using-visual-studio.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#3-advanced-features) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche

* [Fotocamera individuabile](../platform-capabilities-and-apis/locatable-camera.md)