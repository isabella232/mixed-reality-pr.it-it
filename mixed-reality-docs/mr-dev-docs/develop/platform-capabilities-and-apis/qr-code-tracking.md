---
title: Rilevamento di codici a matrice
description: Informazioni su come rilevare i codici a matrice, aggiungere funzionalità di webcam e gestire i sistemi di coordinate nelle app di realtà mista in HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: VR, LBE, location based Entertainment, VR Arcade, Arcade, immersive, QR, QR code, hololens2
ms.openlocfilehash: 08ed651deaab0c230142f45b93858f41ee300323
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583139"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="d02de-104">Rilevamento di codici a matrice</span><span class="sxs-lookup"><span data-stu-id="d02de-104">QR code tracking</span></span>

<span data-ttu-id="d02de-105">HoloLens 2 è in grado di rilevare i codici a matrice nell'ambiente attorno al visore VR, stabilendo un sistema di coordinate nella posizione reale di ciascun codice.</span><span class="sxs-lookup"><span data-stu-id="d02de-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

## <a name="device-support"></a><span data-ttu-id="d02de-106">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="d02de-106">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d02de-107">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="d02de-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="d02de-108"><a href="/hololens/hololens1-hardware">HoloLens (prima generazione)</a></span><span class="sxs-lookup"><span data-stu-id="d02de-108"><a href="/hololens/hololens1-hardware">HoloLens (first gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="d02de-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d02de-109">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="d02de-110"><a href="../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="d02de-110"><a href="../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="d02de-111">Rilevamento del codice a matrice</span><span class="sxs-lookup"><span data-stu-id="d02de-111">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="d02de-112">️</span><span class="sxs-lookup"><span data-stu-id="d02de-112">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d02de-113">✔️</span><span class="sxs-lookup"><span data-stu-id="d02de-113">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="d02de-114">✔️</span><span class="sxs-lookup"><span data-stu-id="d02de-114">✔️</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="d02de-115">Il rilevamento del codice a matrice con auricolari a realtà mista di Windows su PC desktop è supportato in Windows 10 versione 2004 e successive.</span><span class="sxs-lookup"><span data-stu-id="d02de-115">QR code tracking with immersive Windows Mixed Reality headsets on desktop PCs is supported on Windows 10 Version 2004 and higher.</span></span> <span data-ttu-id="d02de-116">Usare l'API Microsoft. MixedReality. QRCodeWatcher. non supportata () per determinare se la funzionalità è supportata nel dispositivo corrente.</span><span class="sxs-lookup"><span data-stu-id="d02de-116">Use the Microsoft.MixedReality.QRCodeWatcher.IsSupported() API to determine whether the feature is supported on the current device.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="d02de-117">Recupero del pacchetto QR</span><span class="sxs-lookup"><span data-stu-id="d02de-117">Getting the QR package</span></span>

<span data-ttu-id="d02de-118">È possibile scaricare il pacchetto NuGet per il rilevamento del codice QR [qui](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span><span class="sxs-lookup"><span data-stu-id="d02de-118">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="d02de-119">Rilevamento di codici QR</span><span class="sxs-lookup"><span data-stu-id="d02de-119">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="d02de-120">Aggiunta della funzionalità webcam</span><span class="sxs-lookup"><span data-stu-id="d02de-120">Adding the webcam capability</span></span>

<span data-ttu-id="d02de-121">È necessario aggiungere la funzionalità `webcam` al manifesto per rilevare i codici QR.</span><span class="sxs-lookup"><span data-stu-id="d02de-121">You'll need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="d02de-122">Questa funzionalità è necessaria perché i dati nei codici rilevati nell'ambiente dell'utente possono contenere informazioni riservate.</span><span class="sxs-lookup"><span data-stu-id="d02de-122">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="d02de-123">È possibile richiedere l'autorizzazione chiamando `QRCodeWatcher.RequestAccessAsync()` :</span><span class="sxs-lookup"><span data-stu-id="d02de-123">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="d02de-124">_C#_</span><span class="sxs-lookup"><span data-stu-id="d02de-124">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="d02de-125">_C++_</span><span class="sxs-lookup"><span data-stu-id="d02de-125">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="d02de-126">Prima di creare un oggetto QRCodeWatcher, è necessario richiedere l'autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="d02de-126">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="d02de-127">Sebbene il rilevamento del codice a matrice richieda la `webcam` funzionalità, il rilevamento si verifica usando le fotocamere di rilevamento del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d02de-127">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="d02de-128">Questo fornisce un rilevamento più ampio FOV e una migliore durata della batteria rispetto al rilevamento con la fotocamera Photo/video (PV) del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d02de-128">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="d02de-129">Rilevamento di codici QR in Unity</span><span class="sxs-lookup"><span data-stu-id="d02de-129">Detecting QR codes in Unity</span></span>

<span data-ttu-id="d02de-130">È possibile usare l'API di rilevamento del codice a matrice in Unity senza importare MRTK installando il pacchetto NuGet usando [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span><span class="sxs-lookup"><span data-stu-id="d02de-130">You can use the QR code detection API in Unity without importing MRTK by installing the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span> <span data-ttu-id="d02de-131">Per avere un'idea del funzionamento, scaricare l' [app Unity di esempio](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span><span class="sxs-lookup"><span data-stu-id="d02de-131">If you want to get a feel for how it works, download the [sample Unity app](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span></span> <span data-ttu-id="d02de-132">L'app di esempio include esempi per la visualizzazione di un quadrato olografico su codici QR e dati associati, ad esempio GUID, dimensioni fisiche, timestamp e dati decodificati.</span><span class="sxs-lookup"><span data-stu-id="d02de-132">The sample app has examples for displaying a holographic square over QR codes and associated data such as GUID, physical size, timestamp, and decoded data.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="d02de-133">Rilevamento di codici QR in C++</span><span class="sxs-lookup"><span data-stu-id="d02de-133">Detecting QR codes in C++</span></span>

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

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="d02de-134">Recupero del sistema di coordinate per un codice a matrice</span><span class="sxs-lookup"><span data-stu-id="d02de-134">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="d02de-135">Ogni codice QR rilevato espone un [sistema di coordinate spaziali](../../design/coordinate-systems.md) allineato al codice a matrice nell'angolo superiore sinistro del quadrato di rilevamento rapido in alto a sinistra:</span><span class="sxs-lookup"><span data-stu-id="d02de-135">Each detected QR code exposes a [spatial coordinate system](../../design/coordinate-systems.md) aligned with the QR code at the top-left corner of the fast detection square in the top left:</span></span>  

![Sistema di coordinate del codice a matrice](images/Qr-coordinatesystem.png) 

<span data-ttu-id="d02de-137">Quando si usa direttamente il QR SDK, l'asse Z punta alla carta (non mostrata): quando viene convertito in coordinate Unity, l'asse Z punta all'esterno della carta ed è a sinistra.</span><span class="sxs-lookup"><span data-stu-id="d02de-137">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="d02de-138">Il SpatialCoordinateSystem del codice a matrice viene allineato come illustrato.</span><span class="sxs-lookup"><span data-stu-id="d02de-138">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="d02de-139">È possibile ottenere il sistema di coordinate dalla piattaforma chiamando <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a> e passando il SpatialGraphNodeId del codice.</span><span class="sxs-lookup"><span data-stu-id="d02de-139">You can get the coordinate system from the platform by calling <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

<span data-ttu-id="d02de-140">Nel codice C++ riportato di seguito viene illustrato come creare un rettangolo e posizionarlo utilizzando il sistema di coordinate del codice a matrice:</span><span class="sxs-lookup"><span data-stu-id="d02de-140">The C++ code below shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

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

<span data-ttu-id="d02de-141">È possibile utilizzare le dimensioni fisiche per creare il rettangolo QR:</span><span class="sxs-lookup"><span data-stu-id="d02de-141">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="d02de-142">Il sistema di coordinate può essere usato per creare il codice a matrice o per alleghire gli ologrammi al percorso:</span><span class="sxs-lookup"><span data-stu-id="d02de-142">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="d02de-143">Il *QRCodeAddedHandler* potrebbe avere un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="d02de-143">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="d02de-144">Procedure consigliate per il rilevamento del codice a matrice</span><span class="sxs-lookup"><span data-stu-id="d02de-144">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="d02de-145">Zone tranquille intorno ai codici QR</span><span class="sxs-lookup"><span data-stu-id="d02de-145">Quiet zones around QR Codes</span></span>

<span data-ttu-id="d02de-146">Per la lettura corretta, i codici a matrice richiedono un margine intorno a tutti i lati del codice.</span><span class="sxs-lookup"><span data-stu-id="d02de-146">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="d02de-147">Questo margine non deve contenere contenuto stampato e deve essere costituito da quattro moduli (un singolo quadrato nero nel codice).</span><span class="sxs-lookup"><span data-stu-id="d02de-147">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="d02de-148">La [specifica QR](https://www.qrcode.com/en/howto/code.html) contiene altre informazioni sulle zone tranquile.</span><span class="sxs-lookup"><span data-stu-id="d02de-148">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="d02de-149">Illuminazione e sfondo</span><span class="sxs-lookup"><span data-stu-id="d02de-149">Lighting and backdrop</span></span>
<span data-ttu-id="d02de-150">La qualità del rilevamento del codice a matrice è soggetta a variazioni di illuminazione e sfondo.</span><span class="sxs-lookup"><span data-stu-id="d02de-150">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="d02de-151">In una scena con illuminazione luminosa stampare un codice nero su uno sfondo grigio.</span><span class="sxs-lookup"><span data-stu-id="d02de-151">In a scene with bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="d02de-152">In caso contrario, stampare un codice a matrice nero su uno sfondo bianco.</span><span class="sxs-lookup"><span data-stu-id="d02de-152">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="d02de-153">Se lo sfondo del codice è scuro, provare a usare un codice nero in grigio se la frequenza di rilevamento è bassa.</span><span class="sxs-lookup"><span data-stu-id="d02de-153">If the backdrop to the code is dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="d02de-154">Se lo sfondo è relativamente chiaro, un codice normale dovrebbe funzionare correttamente.</span><span class="sxs-lookup"><span data-stu-id="d02de-154">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="d02de-155">Dimensioni dei codici QR</span><span class="sxs-lookup"><span data-stu-id="d02de-155">Size of QR codes</span></span>
<span data-ttu-id="d02de-156">I dispositivi di realtà mista di Windows non funzionano con codici a matrice con lati inferiori a 5 cm.</span><span class="sxs-lookup"><span data-stu-id="d02de-156">Windows Mixed Reality devices don't work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="d02de-157">Per i codici QR compresi tra 5 cm e 10 cm di lunghezza, è necessario essere abbastanza vicini per rilevare il codice.</span><span class="sxs-lookup"><span data-stu-id="d02de-157">For QR codes between 5 cm and 10-cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="d02de-158">Sarà inoltre necessario più tempo per rilevare i codici in questa dimensione.</span><span class="sxs-lookup"><span data-stu-id="d02de-158">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="d02de-159">Il tempo esatto per rilevare i codici dipende non solo dalle dimensioni dei codici a matrice, ma da quanto manca il codice.</span><span class="sxs-lookup"><span data-stu-id="d02de-159">The exact time to detect codes depends not only on the size of the QR codes, but how far you're away from the code.</span></span> <span data-ttu-id="d02de-160">Lo spostamento più vicino al codice consente di compensare i problemi con le dimensioni.</span><span class="sxs-lookup"><span data-stu-id="d02de-160">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="d02de-161">Posizione angolare e distanza dal codice a matrice</span><span class="sxs-lookup"><span data-stu-id="d02de-161">Distance and angular position from the QR code</span></span>
<span data-ttu-id="d02de-162">Le videocamere di rilevamento possono rilevare solo un certo livello di dettaglio.</span><span class="sxs-lookup"><span data-stu-id="d02de-162">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="d02de-163">Per i codici piccoli, < 10 cm lungo i lati, è necessario essere abbastanza vicini.</span><span class="sxs-lookup"><span data-stu-id="d02de-163">For small codes - < 10 cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="d02de-164">Per un codice a matrice di versione 1 variabile da 10 cm a 25 cm di larghezza, la distanza di rilevamento minima varia da 0,15 metri a 0,5 metri.</span><span class="sxs-lookup"><span data-stu-id="d02de-164">For a version 1 QR code varying from 10 cm to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="d02de-165">La distanza di rilevamento per le dimensioni aumenta in modo lineare.</span><span class="sxs-lookup"><span data-stu-id="d02de-165">The detection distance for size increases linearly.</span></span> 

<span data-ttu-id="d02de-166">Il rilevamento a matrice funziona con un intervallo di angoli + = 45 deg per garantire la corretta risoluzione per il rilevamento del codice.</span><span class="sxs-lookup"><span data-stu-id="d02de-166">QR detection works with a range of angles += 45 deg to ensure we have proper resolution to detect the code.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="d02de-167">Codici QR con logo</span><span class="sxs-lookup"><span data-stu-id="d02de-167">QR codes with logos</span></span>
<span data-ttu-id="d02de-168">I codici QR con logo non sono stati testati e non sono attualmente supportati.</span><span class="sxs-lookup"><span data-stu-id="d02de-168">QR codes with logos haven't been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="d02de-169">Gestione dei dati del codice QR</span><span class="sxs-lookup"><span data-stu-id="d02de-169">Managing QR code data</span></span>
<span data-ttu-id="d02de-170">I dispositivi di realtà mista Windows rilevano codici QR a livello di sistema nel driver.</span><span class="sxs-lookup"><span data-stu-id="d02de-170">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="d02de-171">Quando il dispositivo viene riavviato, i codici QR rilevati vengono eliminati e verranno rilevati nuovamente come nuovi oggetti la volta successiva.</span><span class="sxs-lookup"><span data-stu-id="d02de-171">When the device is rebooted, the detected QR codes are gone and will be redetected as new objects next time.</span></span>

<span data-ttu-id="d02de-172">Si consiglia di configurare l'app in modo da ignorare i codici QR precedenti a un timestamp specifico.</span><span class="sxs-lookup"><span data-stu-id="d02de-172">We recommend configuring your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="d02de-173">Attualmente, l'API non supporta la cancellazione della cronologia del codice QR.</span><span class="sxs-lookup"><span data-stu-id="d02de-173">Currently, the API doesn't support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="d02de-174">Posizionamento del codice a matrice in uno spazio</span><span class="sxs-lookup"><span data-stu-id="d02de-174">QR code placement in a space</span></span>
<span data-ttu-id="d02de-175">Per consigli su dove e come collocare i codici QR, vedere [considerazioni sull'ambiente per HoloLens](/hololens/hololens-environment-considerations).</span><span class="sxs-lookup"><span data-stu-id="d02de-175">For recommendations on where and how to place QR codes, refer to [Environment considerations for HoloLens](/hololens/hololens-environment-considerations).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="d02de-176">Riferimento all'API QR</span><span class="sxs-lookup"><span data-stu-id="d02de-176">QR API reference</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d02de-177">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d02de-177">See also</span></span>
* [<span data-ttu-id="d02de-178">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="d02de-178">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* <span data-ttu-id="d02de-179"><a href="/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello spazio di Azure</a></span><span class="sxs-lookup"><span data-stu-id="d02de-179"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>