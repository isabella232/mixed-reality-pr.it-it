---
title: Codici a matrice in Unreal
description: Guida all'uso dei codici a matrice in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, codici a matrice, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 7e39e1d822f0aa623a83678beef24f2c98a18944
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609642"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="5b5c1-104">Codici a matrice in Unreal</span><span class="sxs-lookup"><span data-stu-id="5b5c1-104">QR codes in Unreal</span></span>

<span data-ttu-id="5b5c1-105">HoloLens 2 può individuare i codici a matrice nello spazio globale usando la webcam, eseguendone il rendering come ologrammi nella posizione reale di ciascun codice.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-105">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms at each code's real-world position.</span></span> <span data-ttu-id="5b5c1-106">HoloLens 2 è in grado di eseguire il rendering degli ologrammi nella stessa posizione su più dispositivi per creare un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-106">HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="5b5c1-107">Assicurati di seguire le procedure consigliate per l'aggiunta di codici a matrice alle tue applicazioni:</span><span class="sxs-lookup"><span data-stu-id="5b5c1-107">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="5b5c1-108">Zone silenziose</span><span class="sxs-lookup"><span data-stu-id="5b5c1-108">Quiet zones</span></span>
- <span data-ttu-id="5b5c1-109">Illuminazione e sfondo</span><span class="sxs-lookup"><span data-stu-id="5b5c1-109">Lighting and backdrop</span></span>
- <span data-ttu-id="5b5c1-110">Dimensione, distanza e posizione angolare</span><span class="sxs-lookup"><span data-stu-id="5b5c1-110">Size, distance, and angular position</span></span>

<span data-ttu-id="5b5c1-111">Presta particolare attenzione alle [considerazioni sull'ambiente](../../environment-considerations-for-hololens.md) quando vengono inseriti codici a matrice nell'app.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-111">Pay special attention to the [environment considerations](../../environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="5b5c1-112">Per altre informazioni su questi argomenti e per istruzioni su come scaricare il pacchetto NuGet necessario, vedi il documento principale [Rilevamento di codici a matrice](../platform-capabilities-and-apis/qr-code-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="5b5c1-112">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) document.</span></span>

> [!CAUTION]
> <span data-ttu-id="5b5c1-113">I codici a matrice sono l'unico tipo di immagini che possono essere rilevate da HoloLens automaticamente. Il modulo **UARTrackedImage** di Unreal non è supportato in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-113">QR codes are the only type of images that can be tracked by HoloLens out of the box - Unreal's **UARTrackedImage** module isn't supported on HoloLens.</span></span> <span data-ttu-id="5b5c1-114">Se è necessario rilevare immagini personalizzate, è possibile accedere alla [webcam](unreal-hololens-camera.md) del dispositivo ed elaborare le immagini usando una libreria di riconoscimento immagini di terze parti.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-114">If you need to track custom images, you can access the device's [webcam](unreal-hololens-camera.md) and process images using a third party image recognition library.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="5b5c1-115">Abilitazione del rilevamento di codici a matrice</span><span class="sxs-lookup"><span data-stu-id="5b5c1-115">Enabling QR detection</span></span>
<span data-ttu-id="5b5c1-116">Dato che HoloLens 2 deve usare la webcam per visualizzare i codici a matrice, è necessario abilitarla nelle impostazioni del progetto:</span><span class="sxs-lookup"><span data-stu-id="5b5c1-116">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="5b5c1-117">Aprire **Edit > Project Settings** (Modifica > Impostazioni progetto), scorrere fino alla sezione **Platforms** (Piattaforme) e selezionare **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-117">Open **Edit > Project Settings**, scroll to the **Platforms** section, and select **HoloLens**.</span></span>
    + <span data-ttu-id="5b5c1-118">Espandi la sezione **Capabilities** (Funzionalità) e seleziona **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-118">Expand the **Capabilities** section and check **Webcam**.</span></span>  
- <span data-ttu-id="5b5c1-119">Devi anche acconsentire esplicitamente al rilevamento dei codici a matrice [aggiungendo un asset ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="5b5c1-119">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a><span data-ttu-id="5b5c1-120">Configurazione di un codice a matrice rilevato</span><span class="sxs-lookup"><span data-stu-id="5b5c1-120">Setting up a tracked QR code</span></span>

<span data-ttu-id="5b5c1-121">I codici a matrice vengono esposti tramite il sistema di geometria rilevata AR di Unreal come immagine rilevata.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-121">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="5b5c1-122">Per procedere, è necessario:</span><span class="sxs-lookup"><span data-stu-id="5b5c1-122">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="5b5c1-123">Creare un attore di progetto e aggiungere un componente **ARTrackableNotify**:</span><span class="sxs-lookup"><span data-stu-id="5b5c1-123">Create an Actor Blueprint and add an **ARTrackableNotify** component:</span></span>

![Codice a matrice - AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="5b5c1-125">Selezionare **ARTrackableNotify** ed espandere la sezione **Events** (Eventi) nel pannello **Details** (Dettagli):</span><span class="sxs-lookup"><span data-stu-id="5b5c1-125">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel:</span></span>

![Eventi dei codici a matrice](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="5b5c1-127">Fare clic su **+** accanto a **On Add Tracked Geometry** (All'aggiunta della geometria rilevata) per aggiungere il nodo in Event Graph (Grafico eventi).</span><span class="sxs-lookup"><span data-stu-id="5b5c1-127">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="5b5c1-128">L'elenco completo degli eventi è disponibile nell'API del componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="5b5c1-128">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span>

![Aggiungere il nodo a On Add Tracked Geometry (All'aggiunta della geometria rilevata)](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a><span data-ttu-id="5b5c1-130">Uso di un codice a matrice rilevato</span><span class="sxs-lookup"><span data-stu-id="5b5c1-130">Using a tracked QR code</span></span>
<span data-ttu-id="5b5c1-131">Il grafico degli eventi nell'immagine seguente mostra l'evento **OnUpdateTrackedImage** usato per eseguire il rendering di un punto al centro di un codice a matrice e stamparne i dati.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-131">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span>

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

<span data-ttu-id="5b5c1-132">Ecco cosa accade:</span><span class="sxs-lookup"><span data-stu-id="5b5c1-132">Here's what's going on:</span></span>
1. <span data-ttu-id="5b5c1-133">Prima di tutto, viene eseguito il cast dell'immagine rilevata in un codice **ARTrackedQRCode** per verificare che l'immagine aggiornata corrente sia un codice a matrice.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-133">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="5b5c1-134">I dati codificati vengono recuperati dalla variabile **QRCode**.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-134">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="5b5c1-135">È possibile ottenere la parte superiore sinistra del codice a matrice dalla posizione di **GetLocalToWorldTransform** e le dimensioni con **GetEstimateSize**.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-135">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span>

<span data-ttu-id="5b5c1-136">È anche possibile [ottenere il sistema di coordinate per un codice a matrice](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) nel codice.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-136">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="5b5c1-137">Ricerca dell'ID univoco</span><span class="sxs-lookup"><span data-stu-id="5b5c1-137">Finding the unique ID</span></span>
<span data-ttu-id="5b5c1-138">Ogni codice a matrice ha un ID GUID univoco. Per trovarlo:</span><span class="sxs-lookup"><span data-stu-id="5b5c1-138">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="5b5c1-139">Trascina e rilascia il segnaposto **As ARTracked QRCode** e cerca **Get Unique ID** (Ottieni ID univoco).</span><span class="sxs-lookup"><span data-stu-id="5b5c1-139">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![GUID dei codici a matrice](images/unreal-qr-guid.PNG)

<span data-ttu-id="5b5c1-141">Le operazioni sui codici a matrice sono piuttosto complesse, quindi ci sono diversi aspetti da approfondire.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-141">There's a lot going on behind the scenes with QR codes, so you're not at the end of the road.</span></span> <span data-ttu-id="5b5c1-142">I collegamenti riportati di seguito consentono di accedere a informazioni più dettagliate a questo proposito.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-142">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="5b5c1-143">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="5b5c1-143">Next Development Checkpoint</span></span>

<span data-ttu-id="5b5c1-144">Se si sta seguendo il percorso di checkpoint per lo sviluppo con Unreal che abbiamo delineato, si stanno esplorando le API e le funzionalità della piattaforma di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-144">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="5b5c1-145">Da qui è possibile passare all'argomento successivo:</span><span class="sxs-lookup"><span data-stu-id="5b5c1-145">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5b5c1-146">WinRT</span><span class="sxs-lookup"><span data-stu-id="5b5c1-146">WinRT</span></span>](unreal-winRT.md)

<span data-ttu-id="5b5c1-147">In alternativa, passare direttamente alla distribuzione dell'app in un dispositivo o emulatore:</span><span class="sxs-lookup"><span data-stu-id="5b5c1-147">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5b5c1-148">Distribuzione nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="5b5c1-148">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="5b5c1-149">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="5b5c1-149">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b5c1-150">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5b5c1-150">See also</span></span>
* [<span data-ttu-id="5b5c1-151">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="5b5c1-151">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="5b5c1-152">Ologrammi</span><span class="sxs-lookup"><span data-stu-id="5b5c1-152">Holograms</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="5b5c1-153">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="5b5c1-153">Coordinate systems</span></span>](../../design/coordinate-systems.md)
