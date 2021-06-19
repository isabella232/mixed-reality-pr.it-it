---
title: Rilevamento di codici a matrice
description: Informazioni su come rilevare i codici A/A, aggiungere funzionalità di webcam e gestire i sistemi di coordinate nelle app di realtà mista HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: vr, lbe, location based entertainment, vr sala giochi, sala giochi, immersive, qr, codice qr, hololens2
ms.openlocfilehash: 9d3a5d9696fbf875b2e6a890ed837efc055a9e6e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394335"
---
# <a name="qr-code-tracking"></a>Rilevamento di codici a matrice

HoloLens 2 è in grado di rilevare i codici a matrice nell'ambiente attorno al visore VR, stabilendo un sistema di coordinate nella posizione reale di ciascun codice. Dopo aver abilitato la webcam del dispositivo, sarà possibile riconoscere i codici a barre nelle versioni più recenti dei progetti Unreal o Unity. Prima di andare in produzione, è consigliabile seguire [le procedure](#best-practices-for-qr-code-detection) consigliate riportate alla fine dell'articolo.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens (prima generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> Rilevamento del codice a qr</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>

>[!NOTE]
>Il rilevamento del codice a Windows Mixed Reality con visori vr immersive nei PC desktop è supportato Windows 10 versione 2004 e successive. Usare l'API Microsoft.MixedReality.QRCodeWatcher.IsSupported() per determinare se la funzionalità è supportata nel dispositivo corrente.

## <a name="getting-the-qr-package"></a>Recupero del pacchetto A QR

È possibile scaricare il pacchetto NuGet per il rilevamento del codice a qr [qui.](https://nuget.org/Packages/Microsoft.MixedReality.QR)

## <a name="using-openxr"></a>Uso di OpenXR

Quando si usa il plug-in OpenXR, afferrare [ `SpatialGraphNodeId` l'oggetto dall'API AR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) e usare `Microsoft.MixedReality.OpenXR.SpatialGraphNode` l'API per individuare il codice a qr.

Per riferimento, è stato creato un progetto di esempio di rilevamento a livello di codice [in GitHub](https://github.com/yl-msft/QRTracking) con una spiegazione più dettagliata dell'utilizzo per l'API . [ `SpatialGraphNode` ](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)

## <a name="detecting-qr-codes"></a>Rilevamento dei codici a barre

### <a name="adding-the-webcam-capability"></a>Aggiunta della funzionalità webcam

È necessario aggiungere la funzionalità al manifesto per `webcam` rilevare i codici a barre. Questa funzionalità è necessaria perché i dati all'interno dei codici rilevati nell'ambiente dell'utente possono contenere informazioni riservate.

L'autorizzazione può essere richiesta chiamando `QRCodeWatcher.RequestAccessAsync()` :

_C#:_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++:_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

L'autorizzazione deve essere richiesta prima di costruire un oggetto QRCodeWatcher.

Anche se il rilevamento del codice a qr richiede la funzionalità , il rilevamento viene eseguito `webcam` usando le telecamere di rilevamento del dispositivo. Ciò offre un FOV di rilevamento più ampio e una maggiore durata della batteria rispetto al rilevamento con la fotocamera foto/video (PV) del dispositivo.

### <a name="detecting-qr-codes-in-unity"></a>Rilevamento dei codici a barre in Unity

È possibile usare l'API di rilevamento del codice A/QR in Unity senza importare MRTK installando il pacchetto NuGet usando [NuGet per Unity.](https://github.com/GlitchEnzo/NuGetForUnity) Per avere un'immagine del funzionamento, scaricare [l'app Unity di esempio.](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) L'app di esempio include esempi per la visualizzazione di un quadrato olografico sui codici a barre e i dati associati, ad esempio GUID, dimensioni fisiche, timestamp e dati decodificati.

### <a name="detecting-qr-codes-in-c"></a>Rilevamento dei codici a barre in C++

```cpp
using namespace winrt::Windows::Foundation;
using namespace winrt::Microsoft::MixedReality::QR;

class QRListHelper
{
public:
    QRListHelper(MyApplication& app) :
        m_app(app)
    {}

    IAsyncAction SetUpQRCodes()
    {
        if (QRCodeWatcher::IsSupported())
        {
            QRCodeWatcherAccessStatus status = co_await QRCodeWatcher::RequestAccessAsync();
            InitializeQR(status);
        }
    }

private:
    void OnAddedQRCode(const IInspectable&, const QRCodeAddedEventArgs& args)
    {
        m_app.OnAddedQRCode(args);
    }

    void OnUpdatedQRCode(const IInspectable&, const QRCodeUpdatedEventArgs& args)
    {
        m_app.OnUpdatedQRCode(args);
    }

    void OnEnumerationComplete(const IInspectable&, const IInspectable&)
    {
        m_app.OnEnumerationComplete();
    }

    MyApplication& m_app;
    QRCodeWatcher m_qrWatcher{ nullptr };

    void InitializeQR(QRCodeWatcherAccessStatus status)
    {
        if (status == QRCodeWatcherAccessStatus::Allowed)
        {
            m_qrWatcher = QRCodeWatcher();
            m_qrWatcher.Added({ this, &QRListHelper::OnAddedQRCode });
            m_qrWatcher.Updated({ this, &QRListHelper::OnUpdatedQRCode });
            m_qrWatcher.EnumerationCompleted({ this, &QRListHelper::OnEnumerationComplete });
            m_qrWatcher.Start();
        }
        else
        {
            // Permission denied by system or user
            // Handle the failures
        }
    }
};
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>Recupero del sistema di coordinate per un codice A/A

Ogni codice AR rilevato espone un sistema di [coordinate](../../design/coordinate-systems.md) spaziali allineato con il codice A QR nell'angolo superiore sinistro del quadrato di rilevamento rapido in alto a sinistra:  

![Sistema di coordinate del codice AR](images/Qr-coordinatesystem.png) 

Quando si usa direttamente QR SDK, l'asse Z punta alla carta (non visualizzata): quando viene convertito in coordinate unity, l'asse Z punta fuori dalla carta e viene mancino.

SpatialCoordinateSystem di un codice a qr viene allineato come illustrato. È possibile ottenere il sistema di coordinate dalla piattaforma chiamando <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> e passando SpatialGraphNodeId del codice.

Il codice C++ seguente illustra come creare un rettangolo e posizionarlo usando il sistema di coordinate del codice ARI:

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> MyApplication::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

È possibile usare le dimensioni fisiche per creare il rettangolo A/A:

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

Il sistema di coordinate può essere usato per disegnare il codice a qr o collegare ologrammi alla posizione:

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

Nel complesso, *il QRCodeAddedHandler* può avere un aspetto simile al seguente:

```cpp
void MyApplication::OnAddedQRCode(const QRCodeAddedEventArgs& args)
{
    QRCode code = args.Code();
    std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength());
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            qrVertices,
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a>Procedure consigliate per il rilevamento del codice a esecuzione automatica

### <a name="quiet-zones-around-qr-codes"></a>Zone non sicure intorno ai codici a barre

Per essere letti correttamente, i codici A QR richiedono un margine su tutti i lati del codice. Questo margine non deve contenere contenuto stampato e deve essere di quattro moduli (un singolo quadrato nero nel codice). 

La [specifica QR contiene](https://www.qrcode.com/en/howto/code.html) altre informazioni sulle zone non sicure.

### <a name="lighting-and-backdrop"></a>Illuminazione e sfondo
La qualità di rilevamento del codice AR è soggetta a illuminazione e sfondo variabili. 

In una scena con illuminazione brillante, stampare un codice nero su uno sfondo grigio. In caso contrario, stampare un codice a qr nero su uno sfondo bianco.

Se il contesto per il codice è scuro, provare un codice nero su grigio se la frequenza di rilevamento è bassa. Se il contesto è relativamente leggero, un codice normale dovrebbe funzionare correttamente.

### <a name="size-of-qr-codes"></a>Dimensioni dei codici a barre
Windows Mixed Reality i dispositivi non funzionano con i codici a barre con lati inferiori a 5 cm ciascuno.

Per i codici a lungo periodo di lunghezza compresi tra 5 cm e 10 cm, è necessario essere abbastanza vicini per rilevare il codice. Sarà anche necessario più tempo per rilevare i codici a queste dimensioni. 

L'ora esatta per rilevare i codici dipende non solo dalle dimensioni dei codici a lungo periodo, ma anche dalla distanza dal codice. L'avvicinamento al codice consente di compensare i problemi relativi alle dimensioni.

### <a name="distance-and-angular-position-from-the-qr-code"></a>Distanza e posizione angolare dal codice ARI
Le telecamere di rilevamento possono rilevare solo un determinato livello di dettaglio. Per i codici di piccole < 10 cm lungo i lati, è necessario essere abbastanza vicini. Per un codice AQR versione 1 che varia da 10 cm a 25 cm di larghezza, la distanza minima di rilevamento varia da 0,15 metri a 0,5 metri. 

La distanza di rilevamento per le dimensioni aumenta in modo lineare, ma dipende anche dalla versione AQR o dalle dimensioni del modulo. Più alta è la versione, più piccoli sono i moduli, che possono essere rilevati solo da una posizione più vicina. È anche possibile provare i micro codici a lungo termine se si vuole che la distanza di rilevamento sia più lunga. Il rilevamento a lungo raggio funziona con un intervallo di angoli += 45 gradi per garantire la risoluzione appropriata per rilevare il codice.

> [!IMPORTANT]
> Assicurarsi sempre di avere un contrasto sufficiente e un bordo appropriato.

### <a name="qr-codes-with-logos"></a>Codici a qr con logo
I codici a barre con logo non sono stati testati e non sono attualmente supportati.

### <a name="managing-qr-code-data"></a>Gestione dei dati del codice a qr
Windows Mixed Reality i dispositivi rilevano i codici a barre a livello di sistema nel driver. Quando il dispositivo viene riavviato, i codici a lungo termine rilevati non sono più disponibili e verranno nuovamente rilevati come nuovi oggetti la volta successiva.

È consigliabile configurare l'app per ignorare i codici A QR precedenti a un timestamp specifico. Attualmente, l'API non supporta la cancellazione della cronologia del codice AR.

### <a name="qr-code-placement-in-a-space"></a>Posizionamento del codice a qr in uno spazio
Per consigli su dove e come inserire i codici a barre, vedere [Considerazioni sull'ambiente per HoloLens.](/hololens/hololens-environment-considerations)

## <a name="qr-api-reference"></a>Informazioni di riferimento sulle API di domande e risposte

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and M1 to M4 are Micro QR code formats 1-4.
        /// </summary>
        public QRVersion Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum QRVersion
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a>Vedi anche
* [Sistemi di coordinate](../../design/coordinate-systems.md)
* <a href="/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello spazio di Azure</a>