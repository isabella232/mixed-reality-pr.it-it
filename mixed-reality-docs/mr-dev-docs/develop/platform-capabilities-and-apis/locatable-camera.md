---
title: Fotocamera individuabile
description: Informazioni generali sulla HoloLens fotocamera frontale, sul funzionamento e sui profili e le risoluzioni disponibili per gli sviluppatori.
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: fotocamera, hololens, fotocamera a colori, frontale, hololens 2, cv, visione computer, fiducial, marcatori, codice qr, qr, foto, video
ms.openlocfilehash: 33faa4107c6b44041958f422329d8967958a666606a474949184628abcd12544
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217097"
---
# <a name="locatable-camera"></a>Fotocamera individuabile

HoloLens include una fotocamera montata nella parte anteriore del dispositivo, che consente alle app di vedere cosa vede l'utente. Gli sviluppatori hanno accesso e controllo della fotocamera, proprio come per le fotocamere a colori su smartphone, portatili o desktop. Le stesse API universali di Windows [Media Capture](/uwp/api/Windows.Media.Capture.MediaCapture) e Windows Media Foundation che funzionano su dispositivi mobili e desktop HoloLens. Unity [ha eseguito il wrapping di queste API di Windows](../unity/locatable-camera-in-unity.md) per astrarre le funzionalità di utilizzo della fotocamera HoloLens. Le attività di funzionalità includono l'esecuzione di foto e video regolari (con o senza ologrammi) e l'individuazione della posizione e della prospettiva della fotocamera sulla scena.

## <a name="device-camera-information"></a>Informazioni sulla fotocamera del dispositivo

### <a name="hololens-first-generation"></a>HoloLens (prima generazione)

* Correzione della fotocamera con messa a fuoco foto/video (PV) con bilanciamento automatico del bianco, esposizione automatica e pipeline completa di elaborazione delle immagini.
* Il LED della privacy bianca rivolto al mondo si illumina ogni volta che la fotocamera è attiva
* La fotocamera supporta le modalità seguenti (tutte le modalità sono proporzioni 16:9) a 30, 24, 20, 15 e 5 fps:

  |  Video  |  Anteprima  |  Ancora  |  Campo di visualizzazione orizzontale (H-FOV) |  Utilizzo consigliato | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45 deg  |  (modalità predefinita con stabilizzazione video) | 
  |  N/D |  N/D |  2048x1152 |  67 deg |  Immagine con risoluzione massima | 
  |  1408x792 |  1408x792 |  1408x792 |  48 deg |  Overscan (spaziatura interna) risoluzione prima della stabilizzazione video | 
  |  1344x756 |  1344x756 |  1344x756 |  67 deg |  Modalità video FOV di grandi dimensioni con overscan | 
  |  896x504 |  896x504 |  896x504 |  48 deg |  Bassa potenza/modalità a bassa risoluzione per le attività di elaborazione delle immagini | 

### <a name="hololens-2"></a>HoloLens 2

* Fotocamera foto/video con messa a fuoco automatica con bilanciamento del bianco automatico, esposizione automatica e pipeline completa di elaborazione delle immagini.
* Il LED della privacy bianca rivolto al mondo si illumina ogni volta che la fotocamera è attiva.
* HoloLens 2 supporta profili di fotocamera diversi. Informazioni su come [individuare e selezionare le funzionalità della fotocamera.](/windows/uwp/audio-video-camera/camera-profiles)
* La fotocamera supporta i profili e le risoluzioni seguenti (tutte le modalità video sono proporzioni 16:9):
  
  | Profilo                                         | Video     | Anteprima   | Ancora     | Frequenze fotogrammi | Campo di visualizzazione orizzontale (H-FOV) | Utilizzo consigliato                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Legacy,0 BalancedVideoAndPhoto,100             | 2272x1278 | 2272x1278 |           | 15.30       | 64.69                            | Registrazione video di alta qualità                |
  | Legacy,0 BalancedVideoAndPhoto,100             | 896x504   | 896x504   |           | 15.30       | 64.69                            | Flusso di anteprima per l'acquisizione di foto di alta qualità |
  | Legacy,0 BalancedVideoAndPhoto,100             |           |           | 3904x2196 |             | 64.69                            | Acquisizione di foto di alta qualità                  |
  | BalancedVideoAndPhoto, 120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15.30       | 64.69                            | Scenari di lunga durata                     |
  | BalancedVideoAndPhoto, 120                       | 1504x846  | 1504x846  |           | 15.30       | 64.69                            | Scenari di lunga durata                     |
  | Videoconferenza,100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15,30,60    | 64.69                            | Videoconferenza, scenari di lunga durata |
  | Videoconferenza,100                           | 1504x846  | 1504x846  |           | 5,15,30,60  | 64.69                            | Videoconferenza, scenari di lunga durata |
  | Videoconferenza,100 BalancedVideoAndPhoto,120 | 1920x1080 | 1920x1080 | 1920x1080 | 15,30       | 64.69                            | Videoconferenza, scenari di lunga durata |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1280x720  | 1280x720  | 1280x720  | 15,30       | 64.69                            | Videoconferenza, scenari di lunga durata |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1128x636  |           |           | 15,30       | 64.69                            | Videoconferenza, scenari di lunga durata |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 960x540   |           |           | 15,30       | 64.69                            | Videoconferenza, scenari di lunga durata |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 760x428   |           |           | 15,30       | 64.69                            | Videoconferenza, scenari di lunga durata |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 640x360   |           |           | 15,30       | 64.69                            | Videoconferenza, scenari di lunga durata |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 500x282   |           |           | 15,30       | 64.69                            | Videoconferenza, scenari di lunga durata |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 424x240   |           |           | 15,30       | 64.69                            | Videoconferenza, scenari di lunga durata |

> [!NOTE]
> I clienti possono [sfruttare l'acquisizione](/hololens/holographic-photos-and-videos) di realtà mista per scattare video o foto dell'app, tra cui ologrammi e stabilizzazione video.
>
>Gli sviluppatori devono tenere presenti alcune considerazioni quando creano l'app se si vuole che l'aspetto sia il più possibile positivo quando un cliente acquisisce contenuto. È anche possibile abilitare (e personalizzare) l'acquisizione di realtà mista direttamente dall'app. Per altre informazioni, [vedere Mixed Reality Capture per sviluppatori.](mixed-reality-capture-for-developers.md)

## <a name="locating-the-device-camera-in-the-world"></a>Individuazione della fotocamera del dispositivo nel mondo

Quando HoloLens foto e video, i fotogrammi acquisiti includono la posizione della fotocamera nel mondo e il modello di obiettivo della fotocamera. In questo modo le applicazioni possono pensare alla posizione della fotocamera nel mondo reale per scenari di creazione di immagini aumentate. Gli sviluppatori possono implementare in modo creative i propri scenari usando le librerie di elaborazione delle immagini preferite o visione personalizzata.

La "fotocamera" altrove HoloLens documentazione può fare riferimento alla "fotocamera del gioco virtuale" (il frustum a cui l'app esegue il rendering). Se non diversamente specificato, la "fotocamera" in questa pagina fa riferimento alla fotocamera a colori RGB reale.

### <a name="using-unity"></a>Uso di Unity

Per passare da "CameraIntrinsics" e "CameraCoordinateSystem" al sistema di coordinate dell'applicazione o del mondo, seguire le istruzioni nell'articolo Fotocamera localizzata [in Unity.](../unity/locatable-camera-in-unity.md)  CameraToWorldMatrix viene fornito automaticamente dalla classe PhotoCaptureFrame e quindi non è necessario preoccuparsi delle trasformazioni CameraCoordinateSystem illustrate di seguito.

### <a name="using-mediaframereference"></a>Uso di MediaFrameReference

Queste istruzioni si applicano se si usa la classe [MediaFrameReference](/uwp/api/windows.media.capture.frames.mediaframereference) per leggere i fotogrammi dell'immagine dalla fotocamera.

Ogni fotogramma dell'immagine (foto o video) include [un spatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) rooted nella fotocamera al momento dell'acquisizione, accessibile tramite la proprietà [CoordinateSystem](/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) di [MediaFrameReference.](/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference) Ogni fotogramma contiene una descrizione del modello di obiettivo della fotocamera, disponibile nella [proprietà CameraIntrinsics.](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) Insieme, queste trasformazioni definiscono per ogni pixel un raggio nello spazio 3D che rappresenta il percorso tracciato dai fotoni che hanno prodotto il pixel. Questi raggi possono essere correlati ad altri contenuti nell'app ottenendo la trasformazione dal sistema di coordinate del [](../../design/coordinate-systems.md#stationary-frame-of-reference)fotogramma a un altro sistema di coordinate(ad esempio, da un fotogramma di riferimento zionario). 

Ogni frame di immagine offre quanto segue:
* Dati pixel (in formato RGB/NV12/JPEG/e così via)
* [SpatialCoordinateSystem dalla](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) posizione di acquisizione
* Classe [CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) contenente la modalità obiettivo della fotocamera

[L'esempio HolographicFaceTracking](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) illustra il modo piuttosto semplice per eseguire una query per la trasformazione tra il sistema di coordinate della fotocamera e i sistemi di coordinate dell'applicazione.

### <a name="using-media-foundation"></a>Uso di Media Foundation

Se si usa Media Foundation direttamente per leggere i fotogrammi dell'immagine dalla fotocamera, è possibile usare l'attributo [MFSampleExtension_CameraExtrinsics](/windows/win32/medfound/mfsampleextension-cameraextrinsics) di ogni fotogramma e l'attributo [MFSampleExtension_PinholeCameraIntrinsics](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) per individuare i fotogrammi della fotocamera relativi agli altri sistemi di coordinate dell'applicazione, come illustrato in questo codice di esempio:

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```

### <a name="distortion-error"></a>Errore di distorsione

In HoloLens, i flussi video e di immagini non vengono formattati nella pipeline di elaborazione delle immagini del sistema prima che i fotogrammi siano resi disponibili per l'applicazione (il flusso di anteprima contiene i fotogrammi distorti originali). Poiché vengono rese disponibili solo le funzionalità CameraIntrinsics, le applicazioni devono presupporre che i fotogrammi immagine rappresentino una fotocamera perfetta.

In HoloLens (prima generazione), la funzione undistortion nel processore di immagini può comunque lasciare un errore fino a 10 pixel quando si usa CameraIntrinsics nei metadati dei fotogrammi. In molti casi d'uso, questo errore non è importante, ma se si allineano ologrammi a poster/marcatori reali, ad esempio, e si nota un offset di <10 px (circa 11 mm per gli ologrammi posizionati a 2 metri di distanza), questo errore di distorsione potrebbe essere la causa. 

## <a name="locatable-camera-usage-scenarios"></a>Scenari di utilizzo delle fotocamere localizzate

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Visualizzare una foto o un video nel mondo in cui è stato acquisito

I fotogrammi della fotocamera del dispositivo hanno una trasformazione "Camera To World", che può essere usata per mostrare esattamente dove si trova il dispositivo quando è stata eseguita l'immagine. Ad esempio, è possibile posizionare una piccola icona olografica in questa posizione (CameraToWorld.MultiplyPoint(Vector3.zero)) e persino disegnare una piccola freccia nella direzione verso cui era rivolta la fotocamera (CameraToWorld.MultiplyVector(Vector3.forward)).

### <a name="tag--pattern--poster--object-tracking"></a>Tag/Pattern/Poster/Object Tracking

Molte applicazioni di realtà mista usano un'immagine o un modello visivo riconoscibile per creare un punto tracciabile nello spazio. Viene quindi usato per eseguire il rendering di oggetti relativi a tale punto o per creare una posizione nota. Alcuni usi di HoloLens includono la ricerca di un oggetto reale contrassegnato con fiduciali (ad esempio un monitor TV con un codice a codici a chiave), l'inserimento di ologrammi su fiduciali e l'associazione visiva con dispositivi non HoloLens come tablet che sono stati impostati per comunicare con HoloLens tramite Wi-Fi.

Sono necessari alcuni elementi per riconoscere un modello visivo e posizionare un oggetto nello spazio del mondo delle applicazioni:
1. Toolkit di riconoscimento di modelli di immagine, ad esempio codice a matrice, tag AR, ricerca di visi, tracciatori di cerchi, OCR e così via.
2. Raccogliere fotogrammi immagine in fase di esecuzione e passarli al livello di riconoscimento
3. Annullare il progetto delle posizioni delle immagini in posizioni del mondo o probabilmente raggi del mondo. 
4. Posizionare i modelli virtuali in queste località del mondo

Alcuni collegamenti importanti per l'elaborazione di immagini:
* [OpenCV](https://opencv.org/)
* [Tag di domande e risposte](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](https://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

Mantenere una frequenza dei fotogrammi dell'applicazione interattiva è fondamentale, soprattutto quando si gestiscono algoritmi di riconoscimento delle immagini a esecuzione elevata. Per questo motivo, in genere viene usato il modello seguente:
1. Thread principale: gestisce l'oggetto fotocamera
2. Thread principale: richiede nuovi frame (asincroni)
3. Thread principale: passare nuovi frame al thread di rilevamento
4. Thread di rilevamento: elabora l'immagine per raccogliere i punti chiave
5. Thread principale: sposta il modello virtuale in modo che corrisponda ai punti chiave trovati
6. Thread principale: ripetere dal passaggio 2

Alcuni sistemi di marcatori di immagine forniscono solo una posizione a singolo pixel (altri forniscono la trasformazione completa, nel qual caso questa sezione non sarà necessaria), che equivale a un raggio di possibili posizioni. Per raggiungere una singola posizione 3D, è quindi possibile sfruttare più raggi e trovare il risultato finale in base all'intersezione approssimativa. A tale scopo è necessario:
1. Ottenere un ciclo per raccogliere più immagini della fotocamera
2. Trovare i punti caratteristiche associati e i relativi raggi del mondo
3. Quando si dispone di un dizionario di funzionalità, ognuna con più raggi del mondo, è possibile usare il codice seguente per risolvere l'intersezione di tali raggi:

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

Dati due o più percorsi di tag monitorati, è possibile posizionare una scena modellata in base allo scenario corrente dell'utente. Se non si può presupporre la gravità, sono necessarie tre posizioni di tag. In molti casi, si usa una combinazione di colori in cui le sfera bianca rappresentano le posizioni dei tag tracciati in tempo reale e le aree blu rappresentano le posizioni dei tag modellate. Ciò consente all'utente di misurare visivamente la qualità dell'allineamento. Si presuppone la configurazione seguente in tutte le applicazioni:
* Due o più posizioni di tag modellate
* Uno "spazio di calibrazione", che nella scena è l'elemento padre dei tag
* Identificatore della funzionalità della fotocamera
* Comportamento, che sposta lo spazio di calibrazione per allineare i tag modellati con i tag in tempo reale (è importante spostare lo spazio padre, non i marcatori modellati stessi, perché altre si connettono alle posizioni relative a essi).

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Rilevare o identificare oggetti/visi reali con tag stazionari o in movimento usando LED o altre librerie di riconoscimento

Esempi:
* Robot industriali con LED (o codici a qr per oggetti in movimento più lento)
* Identificare e riconoscere gli oggetti nella stanza
* Identificare e riconoscere le persone nella stanza, ad esempio posizionando schede di contatto olografiche sui visi

## <a name="see-also"></a>Vedi anche
* [Esempio di fotocamera localizzata](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Fotocamera individuabile in Unity](../unity/locatable-camera-in-unity.md)
* [Acquisizione in realtà mista (MRC, Mixed Reality Capture)](/hololens/holographic-photos-and-videos)
* [Acquisizione realtà mista per sviluppatori](mixed-reality-capture-for-developers.md)
* [Introduzione all'acquisizione di supporti](/windows/uwp/audio-video-camera/)
* [Esempio di rilevamento del viso olografico](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)