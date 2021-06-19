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
# <a name="qr-code-tracking"></a><span data-ttu-id="4eba6-104">Rilevamento di codici a matrice</span><span class="sxs-lookup"><span data-stu-id="4eba6-104">QR code tracking</span></span>

<span data-ttu-id="4eba6-105">HoloLens 2 è in grado di rilevare i codici a matrice nell'ambiente attorno al visore VR, stabilendo un sistema di coordinate nella posizione reale di ciascun codice.</span><span class="sxs-lookup"><span data-stu-id="4eba6-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="4eba6-106">Dopo aver abilitato la webcam del dispositivo, sarà possibile riconoscere i codici a barre nelle versioni più recenti dei progetti Unreal o Unity.</span><span class="sxs-lookup"><span data-stu-id="4eba6-106">Once you enable your device's webcam, you'll be able to recognize QR codes in the latest versions of your Unreal or Unity projects.</span></span> <span data-ttu-id="4eba6-107">Prima di andare in produzione, è consigliabile seguire [le procedure](#best-practices-for-qr-code-detection) consigliate riportate alla fine dell'articolo.</span><span class="sxs-lookup"><span data-stu-id="4eba6-107">Before going to production, we recommend following the [best practices](#best-practices-for-qr-code-detection) we've laid at the end of the article.</span></span>

## <a name="device-support"></a><span data-ttu-id="4eba6-108">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="4eba6-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4eba6-109">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="4eba6-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="4eba6-110"><a href="/hololens/hololens1-hardware">HoloLens (prima generazione)</a></span><span class="sxs-lookup"><span data-stu-id="4eba6-110"><a href="/hololens/hololens1-hardware">HoloLens (first gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="4eba6-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4eba6-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="4eba6-112"><a href="../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="4eba6-112"><a href="../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="4eba6-113">Rilevamento del codice a qr</span><span class="sxs-lookup"><span data-stu-id="4eba6-113">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="4eba6-114">️</span><span class="sxs-lookup"><span data-stu-id="4eba6-114">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="4eba6-115">✔️</span><span class="sxs-lookup"><span data-stu-id="4eba6-115">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="4eba6-116">✔️</span><span class="sxs-lookup"><span data-stu-id="4eba6-116">✔️</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="4eba6-117">Il rilevamento del codice a Windows Mixed Reality con visori vr immersive nei PC desktop è supportato Windows 10 versione 2004 e successive.</span><span class="sxs-lookup"><span data-stu-id="4eba6-117">QR code tracking with immersive Windows Mixed Reality headsets on desktop PCs is supported on Windows 10 Version 2004 and higher.</span></span> <span data-ttu-id="4eba6-118">Usare l'API Microsoft.MixedReality.QRCodeWatcher.IsSupported() per determinare se la funzionalità è supportata nel dispositivo corrente.</span><span class="sxs-lookup"><span data-stu-id="4eba6-118">Use the Microsoft.MixedReality.QRCodeWatcher.IsSupported() API to determine whether the feature is supported on the current device.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="4eba6-119">Recupero del pacchetto A QR</span><span class="sxs-lookup"><span data-stu-id="4eba6-119">Getting the QR package</span></span>

<span data-ttu-id="4eba6-120">È possibile scaricare il pacchetto NuGet per il rilevamento del codice a qr [qui.](https://nuget.org/Packages/Microsoft.MixedReality.QR)</span><span class="sxs-lookup"><span data-stu-id="4eba6-120">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="using-openxr"></a><span data-ttu-id="4eba6-121">Uso di OpenXR</span><span class="sxs-lookup"><span data-stu-id="4eba6-121">Using OpenXR</span></span>

<span data-ttu-id="4eba6-122">Quando si usa il plug-in OpenXR, afferrare [ `SpatialGraphNodeId` l'oggetto dall'API AR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) e usare `Microsoft.MixedReality.OpenXR.SpatialGraphNode` l'API per individuare il codice a qr.</span><span class="sxs-lookup"><span data-stu-id="4eba6-122">When using the OpenXR plugin, grab the [`SpatialGraphNodeId` from the QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) and use the `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API to locate the QR code.</span></span>

<span data-ttu-id="4eba6-123">Per riferimento, è stato creato un progetto di esempio di rilevamento a livello di codice [in GitHub](https://github.com/yl-msft/QRTracking) con una spiegazione più dettagliata dell'utilizzo per l'API . [ `SpatialGraphNode` ](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)</span><span class="sxs-lookup"><span data-stu-id="4eba6-123">For reference, we have a [QR tracking sample project on GitHub](https://github.com/yl-msft/QRTracking) with more a detailed usage explanation for the [`SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="4eba6-124">Rilevamento dei codici a barre</span><span class="sxs-lookup"><span data-stu-id="4eba6-124">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="4eba6-125">Aggiunta della funzionalità webcam</span><span class="sxs-lookup"><span data-stu-id="4eba6-125">Adding the webcam capability</span></span>

<span data-ttu-id="4eba6-126">È necessario aggiungere la funzionalità al manifesto per `webcam` rilevare i codici a barre.</span><span class="sxs-lookup"><span data-stu-id="4eba6-126">You'll need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="4eba6-127">Questa funzionalità è necessaria perché i dati all'interno dei codici rilevati nell'ambiente dell'utente possono contenere informazioni riservate.</span><span class="sxs-lookup"><span data-stu-id="4eba6-127">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="4eba6-128">L'autorizzazione può essere richiesta chiamando `QRCodeWatcher.RequestAccessAsync()` :</span><span class="sxs-lookup"><span data-stu-id="4eba6-128">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="4eba6-129">_C#:_</span><span class="sxs-lookup"><span data-stu-id="4eba6-129">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="4eba6-130">_C++:_</span><span class="sxs-lookup"><span data-stu-id="4eba6-130">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="4eba6-131">L'autorizzazione deve essere richiesta prima di costruire un oggetto QRCodeWatcher.</span><span class="sxs-lookup"><span data-stu-id="4eba6-131">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="4eba6-132">Anche se il rilevamento del codice a qr richiede la funzionalità , il rilevamento viene eseguito `webcam` usando le telecamere di rilevamento del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4eba6-132">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="4eba6-133">Ciò offre un FOV di rilevamento più ampio e una maggiore durata della batteria rispetto al rilevamento con la fotocamera foto/video (PV) del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4eba6-133">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="4eba6-134">Rilevamento dei codici a barre in Unity</span><span class="sxs-lookup"><span data-stu-id="4eba6-134">Detecting QR codes in Unity</span></span>

<span data-ttu-id="4eba6-135">È possibile usare l'API di rilevamento del codice A/QR in Unity senza importare MRTK installando il pacchetto NuGet usando [NuGet per Unity.](https://github.com/GlitchEnzo/NuGetForUnity)</span><span class="sxs-lookup"><span data-stu-id="4eba6-135">You can use the QR code detection API in Unity without importing MRTK by installing the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span> <span data-ttu-id="4eba6-136">Per avere un'immagine del funzionamento, scaricare [l'app Unity di esempio.](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes)</span><span class="sxs-lookup"><span data-stu-id="4eba6-136">If you want to get a feel for how it works, download the [sample Unity app](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span></span> <span data-ttu-id="4eba6-137">L'app di esempio include esempi per la visualizzazione di un quadrato olografico sui codici a barre e i dati associati, ad esempio GUID, dimensioni fisiche, timestamp e dati decodificati.</span><span class="sxs-lookup"><span data-stu-id="4eba6-137">The sample app has examples for displaying a holographic square over QR codes and associated data such as GUID, physical size, timestamp, and decoded data.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="4eba6-138">Rilevamento dei codici a barre in C++</span><span class="sxs-lookup"><span data-stu-id="4eba6-138">Detecting QR codes in C++</span></span>

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

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="4eba6-139">Recupero del sistema di coordinate per un codice A/A</span><span class="sxs-lookup"><span data-stu-id="4eba6-139">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="4eba6-140">Ogni codice AR rilevato espone un sistema di [coordinate](../../design/coordinate-systems.md) spaziali allineato con il codice A QR nell'angolo superiore sinistro del quadrato di rilevamento rapido in alto a sinistra:</span><span class="sxs-lookup"><span data-stu-id="4eba6-140">Each detected QR code exposes a [spatial coordinate system](../../design/coordinate-systems.md) aligned with the QR code at the top-left corner of the fast detection square in the top left:</span></span>  

![Sistema di coordinate del codice AR](images/Qr-coordinatesystem.png) 

<span data-ttu-id="4eba6-142">Quando si usa direttamente QR SDK, l'asse Z punta alla carta (non visualizzata): quando viene convertito in coordinate unity, l'asse Z punta fuori dalla carta e viene mancino.</span><span class="sxs-lookup"><span data-stu-id="4eba6-142">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="4eba6-143">SpatialCoordinateSystem di un codice a qr viene allineato come illustrato.</span><span class="sxs-lookup"><span data-stu-id="4eba6-143">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="4eba6-144">È possibile ottenere il sistema di coordinate dalla piattaforma chiamando <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> e passando SpatialGraphNodeId del codice.</span><span class="sxs-lookup"><span data-stu-id="4eba6-144">You can get the coordinate system from the platform by calling <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

<span data-ttu-id="4eba6-145">Il codice C++ seguente illustra come creare un rettangolo e posizionarlo usando il sistema di coordinate del codice ARI:</span><span class="sxs-lookup"><span data-stu-id="4eba6-145">The C++ code below shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

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

<span data-ttu-id="4eba6-146">È possibile usare le dimensioni fisiche per creare il rettangolo A/A:</span><span class="sxs-lookup"><span data-stu-id="4eba6-146">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="4eba6-147">Il sistema di coordinate può essere usato per disegnare il codice a qr o collegare ologrammi alla posizione:</span><span class="sxs-lookup"><span data-stu-id="4eba6-147">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="4eba6-148">Nel complesso, *il QRCodeAddedHandler* può avere un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="4eba6-148">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="4eba6-149">Procedure consigliate per il rilevamento del codice a esecuzione automatica</span><span class="sxs-lookup"><span data-stu-id="4eba6-149">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="4eba6-150">Zone non sicure intorno ai codici a barre</span><span class="sxs-lookup"><span data-stu-id="4eba6-150">Quiet zones around QR Codes</span></span>

<span data-ttu-id="4eba6-151">Per essere letti correttamente, i codici A QR richiedono un margine su tutti i lati del codice.</span><span class="sxs-lookup"><span data-stu-id="4eba6-151">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="4eba6-152">Questo margine non deve contenere contenuto stampato e deve essere di quattro moduli (un singolo quadrato nero nel codice).</span><span class="sxs-lookup"><span data-stu-id="4eba6-152">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="4eba6-153">La [specifica QR contiene](https://www.qrcode.com/en/howto/code.html) altre informazioni sulle zone non sicure.</span><span class="sxs-lookup"><span data-stu-id="4eba6-153">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="4eba6-154">Illuminazione e sfondo</span><span class="sxs-lookup"><span data-stu-id="4eba6-154">Lighting and backdrop</span></span>
<span data-ttu-id="4eba6-155">La qualità di rilevamento del codice AR è soggetta a illuminazione e sfondo variabili.</span><span class="sxs-lookup"><span data-stu-id="4eba6-155">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="4eba6-156">In una scena con illuminazione brillante, stampare un codice nero su uno sfondo grigio.</span><span class="sxs-lookup"><span data-stu-id="4eba6-156">In a scene with bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="4eba6-157">In caso contrario, stampare un codice a qr nero su uno sfondo bianco.</span><span class="sxs-lookup"><span data-stu-id="4eba6-157">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="4eba6-158">Se il contesto per il codice è scuro, provare un codice nero su grigio se la frequenza di rilevamento è bassa.</span><span class="sxs-lookup"><span data-stu-id="4eba6-158">If the backdrop to the code is dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="4eba6-159">Se il contesto è relativamente leggero, un codice normale dovrebbe funzionare correttamente.</span><span class="sxs-lookup"><span data-stu-id="4eba6-159">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="4eba6-160">Dimensioni dei codici a barre</span><span class="sxs-lookup"><span data-stu-id="4eba6-160">Size of QR codes</span></span>
<span data-ttu-id="4eba6-161">Windows Mixed Reality i dispositivi non funzionano con i codici a barre con lati inferiori a 5 cm ciascuno.</span><span class="sxs-lookup"><span data-stu-id="4eba6-161">Windows Mixed Reality devices don't work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="4eba6-162">Per i codici a lungo periodo di lunghezza compresi tra 5 cm e 10 cm, è necessario essere abbastanza vicini per rilevare il codice.</span><span class="sxs-lookup"><span data-stu-id="4eba6-162">For QR codes between 5 cm and 10-cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="4eba6-163">Sarà anche necessario più tempo per rilevare i codici a queste dimensioni.</span><span class="sxs-lookup"><span data-stu-id="4eba6-163">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="4eba6-164">L'ora esatta per rilevare i codici dipende non solo dalle dimensioni dei codici a lungo periodo, ma anche dalla distanza dal codice.</span><span class="sxs-lookup"><span data-stu-id="4eba6-164">The exact time to detect codes depends not only on the size of the QR codes, but how far you're away from the code.</span></span> <span data-ttu-id="4eba6-165">L'avvicinamento al codice consente di compensare i problemi relativi alle dimensioni.</span><span class="sxs-lookup"><span data-stu-id="4eba6-165">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="4eba6-166">Distanza e posizione angolare dal codice ARI</span><span class="sxs-lookup"><span data-stu-id="4eba6-166">Distance and angular position from the QR code</span></span>
<span data-ttu-id="4eba6-167">Le telecamere di rilevamento possono rilevare solo un determinato livello di dettaglio.</span><span class="sxs-lookup"><span data-stu-id="4eba6-167">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="4eba6-168">Per i codici di piccole < 10 cm lungo i lati, è necessario essere abbastanza vicini.</span><span class="sxs-lookup"><span data-stu-id="4eba6-168">For small codes - < 10 cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="4eba6-169">Per un codice AQR versione 1 che varia da 10 cm a 25 cm di larghezza, la distanza minima di rilevamento varia da 0,15 metri a 0,5 metri.</span><span class="sxs-lookup"><span data-stu-id="4eba6-169">For a version 1 QR code varying from 10 cm to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="4eba6-170">La distanza di rilevamento per le dimensioni aumenta in modo lineare, ma dipende anche dalla versione AQR o dalle dimensioni del modulo.</span><span class="sxs-lookup"><span data-stu-id="4eba6-170">The detection distance for size increases linearly, but also depends on QR version or module size.</span></span> <span data-ttu-id="4eba6-171">Più alta è la versione, più piccoli sono i moduli, che possono essere rilevati solo da una posizione più vicina.</span><span class="sxs-lookup"><span data-stu-id="4eba6-171">The higher the version, the smaller the modules, which can only be detected from a closer position.</span></span> <span data-ttu-id="4eba6-172">È anche possibile provare i micro codici a lungo termine se si vuole che la distanza di rilevamento sia più lunga.</span><span class="sxs-lookup"><span data-stu-id="4eba6-172">You can also try micro QR codes if you want the distance of detection to be longer.</span></span> <span data-ttu-id="4eba6-173">Il rilevamento a lungo raggio funziona con un intervallo di angoli += 45 gradi per garantire la risoluzione appropriata per rilevare il codice.</span><span class="sxs-lookup"><span data-stu-id="4eba6-173">QR detection works with a range of angles += 45 deg to ensure we have proper resolution to detect the code.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4eba6-174">Assicurarsi sempre di avere un contrasto sufficiente e un bordo appropriato.</span><span class="sxs-lookup"><span data-stu-id="4eba6-174">Always make sure you have enough contrast and a proper border.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="4eba6-175">Codici a qr con logo</span><span class="sxs-lookup"><span data-stu-id="4eba6-175">QR codes with logos</span></span>
<span data-ttu-id="4eba6-176">I codici a barre con logo non sono stati testati e non sono attualmente supportati.</span><span class="sxs-lookup"><span data-stu-id="4eba6-176">QR codes with logos haven't been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="4eba6-177">Gestione dei dati del codice a qr</span><span class="sxs-lookup"><span data-stu-id="4eba6-177">Managing QR code data</span></span>
<span data-ttu-id="4eba6-178">Windows Mixed Reality i dispositivi rilevano i codici a barre a livello di sistema nel driver.</span><span class="sxs-lookup"><span data-stu-id="4eba6-178">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="4eba6-179">Quando il dispositivo viene riavviato, i codici a lungo termine rilevati non sono più disponibili e verranno nuovamente rilevati come nuovi oggetti la volta successiva.</span><span class="sxs-lookup"><span data-stu-id="4eba6-179">When the device is rebooted, the detected QR codes are gone and will be redetected as new objects next time.</span></span>

<span data-ttu-id="4eba6-180">È consigliabile configurare l'app per ignorare i codici A QR precedenti a un timestamp specifico.</span><span class="sxs-lookup"><span data-stu-id="4eba6-180">We recommend configuring your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="4eba6-181">Attualmente, l'API non supporta la cancellazione della cronologia del codice AR.</span><span class="sxs-lookup"><span data-stu-id="4eba6-181">Currently, the API doesn't support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="4eba6-182">Posizionamento del codice a qr in uno spazio</span><span class="sxs-lookup"><span data-stu-id="4eba6-182">QR code placement in a space</span></span>
<span data-ttu-id="4eba6-183">Per consigli su dove e come inserire i codici a barre, vedere [Considerazioni sull'ambiente per HoloLens.](/hololens/hololens-environment-considerations)</span><span class="sxs-lookup"><span data-stu-id="4eba6-183">For recommendations on where and how to place QR codes, refer to [Environment considerations for HoloLens](/hololens/hololens-environment-considerations).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="4eba6-184">Informazioni di riferimento sulle API di domande e risposte</span><span class="sxs-lookup"><span data-stu-id="4eba6-184">QR API reference</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4eba6-185">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="4eba6-185">See also</span></span>
* [<span data-ttu-id="4eba6-186">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="4eba6-186">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* <span data-ttu-id="4eba6-187"><a href="/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello spazio di Azure</a></span><span class="sxs-lookup"><span data-stu-id="4eba6-187"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>