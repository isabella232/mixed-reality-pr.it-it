---
title: Modalità ricerca di HoloLens
description: Usando la modalità di ricerca su HoloLens, un'applicazione può accedere ai flussi dei sensori del dispositivo chiave (profondità, rilevamento dell'ambiente e riflettanza IR).
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Modalità di ricerca, CV, RS4, visione artificiale, ricerca, HoloLens, HoloLens 2
ms.openlocfilehash: 6c40ac814a5dacfdbb942aec8200f46157bea161
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530083"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="5edfd-104">Modalità ricerca di HoloLens</span><span class="sxs-lookup"><span data-stu-id="5edfd-104">HoloLens Research Mode</span></span>

<span data-ttu-id="5edfd-105">La modalità di ricerca è stata introdotta nei dispositivi HoloLens (1st Gen) per consentire l'accesso ai sensori chiave, in particolare per le applicazioni di ricerca che non sono destinate alla distribuzione.</span><span class="sxs-lookup"><span data-stu-id="5edfd-105">Research Mode was introduced on HoloLens (1st Gen) devices to give access to key sensors, specifically for research applications that aren't intended for deployment.</span></span>  <span data-ttu-id="5edfd-106">La modalità di ricerca per HoloLens 2 mantiene le funzionalità di HoloLens 1, ma aggiunge l'accesso ai flussi seguenti:</span><span class="sxs-lookup"><span data-stu-id="5edfd-106">Research Mode for HoloLens 2 keeps the capabilities of HoloLens 1 but adds access to the following streams:</span></span>

* <span data-ttu-id="5edfd-107">**Fotocamere di rilevamento dell'ambiente chiaro visibile** : fotocamere con scalabilità orizzontale usate dal sistema per il rilevamento delle intestazioni e la compilazione della mappa.</span><span class="sxs-lookup"><span data-stu-id="5edfd-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="5edfd-108">**Depth fotocamera** : funziona in due modalità:</span><span class="sxs-lookup"><span data-stu-id="5edfd-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="5edfd-109">AHAT, rilevamento a frequenza elevata (45 FPS) usato per il rilevamento manuale.</span><span class="sxs-lookup"><span data-stu-id="5edfd-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="5edfd-110">Diversamente dalla prima modalità di generazione breve, AHAT fornisce la pseudo-profondità con il wrapping della fase oltre 1 contatore.</span><span class="sxs-lookup"><span data-stu-id="5edfd-110">Differently from the first version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="5edfd-111">Rilevamento a lungo termine, a bassa frequenza (1-5 FPS) per un rilevamento approfondito usato dal [mapping spaziale](../../design/spatial-mapping.md)</span><span class="sxs-lookup"><span data-stu-id="5edfd-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](../../design/spatial-mapping.md)</span></span>

* <span data-ttu-id="5edfd-112">**Due versioni del flusso IR-riflettività** , usate dal HoloLens per calcolare la profondità.</span><span class="sxs-lookup"><span data-stu-id="5edfd-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="5edfd-113">Queste immagini sono illuminate dall'infrarosso e non sono interessate dalla luce visibile dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="5edfd-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="5edfd-114">Se si usa un HoloLens 2, è anche possibile accedere agli input aggiuntivi seguenti:</span><span class="sxs-lookup"><span data-stu-id="5edfd-114">If you're using a HoloLens 2, you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="5edfd-115">**Accelerometro** : usato dal sistema per determinare l'accelerazione lineare lungo gli assi X, Y e Z e la gravità.</span><span class="sxs-lookup"><span data-stu-id="5edfd-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y, and Z axes and gravity.</span></span>
* <span data-ttu-id="5edfd-116">**Gyro** : utilizzato dal sistema per determinare le rotazioni.</span><span class="sxs-lookup"><span data-stu-id="5edfd-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="5edfd-117">**Magnetometro** : utilizzato dal sistema per stimare l'orientamento assoluto.</span><span class="sxs-lookup"><span data-stu-id="5edfd-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5edfd-118">La modalità di ricerca è attualmente disponibile in anteprima pubblica.</span><span class="sxs-lookup"><span data-stu-id="5edfd-118">Research Mode is currently in Public Preview.</span></span> 

<span data-ttu-id="5edfd-119">![Schermata dell'app modalità di ricerca](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="5edfd-119">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="5edfd-120">*Acquisizione di realtà mista di un'applicazione di test che visualizza gli otto flussi di sensori disponibili in modalità ricerca*</span><span class="sxs-lookup"><span data-stu-id="5edfd-120">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="5edfd-121">Uso</span><span class="sxs-lookup"><span data-stu-id="5edfd-121">Usage</span></span>

<span data-ttu-id="5edfd-122">La modalità di ricerca è progettata per ricercatori accademici e industriali che esplorano nuove idee nei campi di Visione artificiale e robotica.</span><span class="sxs-lookup"><span data-stu-id="5edfd-122">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="5edfd-123">Non è destinata alle applicazioni distribuite in ambienti aziendali o disponibili tramite il Microsoft Store o altri canali di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="5edfd-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="5edfd-124">Inoltre, Microsoft non garantisce che la modalità di ricerca o la funzionalità equivalente verrà supportata negli aggiornamenti futuri dell'hardware o del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="5edfd-124">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="5edfd-125">Tuttavia, non è possibile impedirne l'uso per sviluppare e testare nuove idee.</span><span class="sxs-lookup"><span data-stu-id="5edfd-125">However, don't let that stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="5edfd-126">Sicurezza e prestazioni</span><span class="sxs-lookup"><span data-stu-id="5edfd-126">Security and performance</span></span>

<span data-ttu-id="5edfd-127">L'abilitazione della modalità di ricerca usa più potenza della batteria rispetto all'uso di HoloLens 2 in condizioni normali, anche se l'applicazione che usa le funzionalità della modalità di ricerca non è in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="5edfd-127">Enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions, even if the application using the Research Mode features isn't running.</span></span>  <span data-ttu-id="5edfd-128">L'abilitazione di questa modalità può anche ridurre la sicurezza complessiva del dispositivo perché le applicazioni possono usare i dati del sensore in modo errato.</span><span class="sxs-lookup"><span data-stu-id="5edfd-128">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="5edfd-129">Altre informazioni sulla sicurezza del dispositivo sono disponibili nelle [domande frequenti sulla sicurezza di HoloLens](https://docs.microsoft.com/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="5edfd-129">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="5edfd-130">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="5edfd-130">Device support</span></span>
<table><span data-ttu-id="5edfd-131">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="5edfd-131">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="5edfd-132"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="5edfd-132"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="5edfd-133"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1a generazione</strong></a></span><span class="sxs-lookup"><span data-stu-id="5edfd-133"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens first Gen</strong></a></span></span></td>
        <td><span data-ttu-id="5edfd-134"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="5edfd-134"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="5edfd-135">Fotocamere di rilevamento Head</span><span class="sxs-lookup"><span data-stu-id="5edfd-135">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="5edfd-136">✔️</span><span class="sxs-lookup"><span data-stu-id="5edfd-136">✔️</span></span></td>
        <td><span data-ttu-id="5edfd-137">✔️</span><span class="sxs-lookup"><span data-stu-id="5edfd-137">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="5edfd-138">Profondità & fotocamera IR</span><span class="sxs-lookup"><span data-stu-id="5edfd-138">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="5edfd-139">✔️</span><span class="sxs-lookup"><span data-stu-id="5edfd-139">✔️</span></span></td>
        <td><span data-ttu-id="5edfd-140">✔️</span><span class="sxs-lookup"><span data-stu-id="5edfd-140">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="5edfd-141">Accelerometro</span><span class="sxs-lookup"><span data-stu-id="5edfd-141">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="5edfd-142">✔️</span><span class="sxs-lookup"><span data-stu-id="5edfd-142">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="5edfd-143">Giroscopio</span><span class="sxs-lookup"><span data-stu-id="5edfd-143">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="5edfd-144">✔️</span><span class="sxs-lookup"><span data-stu-id="5edfd-144">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="5edfd-145">Magnetometro</span><span class="sxs-lookup"><span data-stu-id="5edfd-145">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="5edfd-146">✔️</span><span class="sxs-lookup"><span data-stu-id="5edfd-146">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a><span data-ttu-id="5edfd-147">Abilitazione della modalità di ricerca (HoloLens First Gen and HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="5edfd-147">Enabling Research Mode (HoloLens first Gen and HoloLens 2)</span></span>

<span data-ttu-id="5edfd-148">La modalità di ricerca è un'estensione della modalità sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="5edfd-148">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="5edfd-149">Prima di iniziare, è necessario abilitare le funzionalità di sviluppo del dispositivo per accedere alle impostazioni della modalità di ricerca:</span><span class="sxs-lookup"><span data-stu-id="5edfd-149">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="5edfd-150">Aprire il **menu Start > impostazioni** e selezionare **aggiornamenti**.</span><span class="sxs-lookup"><span data-stu-id="5edfd-150">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="5edfd-151">Selezionare **per gli sviluppatori** e abilitare la **modalità sviluppatore**.</span><span class="sxs-lookup"><span data-stu-id="5edfd-151">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="5edfd-152">Scorri verso il basso e abilita **Portale dispositivi**.</span><span class="sxs-lookup"><span data-stu-id="5edfd-152">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="5edfd-153">Una volta abilitate le funzionalità per gli sviluppatori, [connettersi al portale del dispositivo](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) per abilitare le funzionalità della modalità di ricerca:</span><span class="sxs-lookup"><span data-stu-id="5edfd-153">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="5edfd-154">Passare alla **modalità di ricerca di System >** nel **portale del dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="5edfd-154">Go to **System > Research Mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="5edfd-155">Selezionare **Consenti accesso al flusso del sensore**.</span><span class="sxs-lookup"><span data-stu-id="5edfd-155">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="5edfd-156">Riavviare il dispositivo dalla voce del menu **Power** nella parte superiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="5edfd-156">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="5edfd-157">Dopo aver riavviato il dispositivo, le applicazioni caricate tramite il **portale** per i dispositivi possono accedere ai flussi della modalità di ricerca.</span><span class="sxs-lookup"><span data-stu-id="5edfd-157">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="5edfd-158">![Scheda modalità ricerca del portale per dispositivi HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="5edfd-158">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="5edfd-159">*Finestra modalità di ricerca nel portale per dispositivi HoloLens*</span><span class="sxs-lookup"><span data-stu-id="5edfd-159">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5edfd-160">La modalità di ricerca per HoloLens 2 è disponibile a partire dalla Build 19041,1356.</span><span class="sxs-lookup"><span data-stu-id="5edfd-160">Research Mode for HoloLens 2 is available beginning with build 19041.1356.</span></span> <span data-ttu-id="5edfd-161">Se è necessario accedere a una build precedente, iscriversi al programma di [Anteprima di insider](https://docs.microsoft.com/hololens/hololens-insider) .</span><span class="sxs-lookup"><span data-stu-id="5edfd-161">If you need access in an earlier build, sign up for our [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) program.</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="5edfd-162">Uso dei dati dei sensori nelle app</span><span class="sxs-lookup"><span data-stu-id="5edfd-162">Using sensor data in your apps</span></span>

<span data-ttu-id="5edfd-163">Le applicazioni possono accedere ai dati del flusso dei sensori nello stesso modo in cui [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) accede ai flussi della fotocamera e della foto.</span><span class="sxs-lookup"><span data-stu-id="5edfd-163">Applications can access the sensor stream data in the same way that [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) accesses photo and video camera streams.</span></span> 

<span data-ttu-id="5edfd-164">Tutte le API che funzionano per lo sviluppo di HoloLens sono disponibili anche in modalità ricerca.</span><span class="sxs-lookup"><span data-stu-id="5edfd-164">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="5edfd-165">In particolare, l'applicazione conosce esattamente dove HoloLens si trova nello spazio 6DoF a ogni tempo di acquisizione del fotogramma del sensore.</span><span class="sxs-lookup"><span data-stu-id="5edfd-165">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="5edfd-166">Sono disponibili applicazioni di esempio che illustrano l'accesso al flusso in modalità ricerca, usando le [funzioni intrinseche ed estrinseche](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)e i flussi di registrazione:</span><span class="sxs-lookup"><span data-stu-id="5edfd-166">We have sample applications showing Research Mode stream access, using the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and recording streams:</span></span>
* [<span data-ttu-id="5edfd-167">HoloLens (prima generazione)</span><span class="sxs-lookup"><span data-stu-id="5edfd-167">HoloLens (first gen)</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="5edfd-168">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5edfd-168">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a><span data-ttu-id="5edfd-169">Supporto</span><span class="sxs-lookup"><span data-stu-id="5edfd-169">Support</span></span>

<span data-ttu-id="5edfd-170">Per HoloLens (First Gen), usare lo strumento di [registrazione dei problemi](https://github.com/Microsoft/HololensForCV/issues) nel repository HoloLensForCV per inviare commenti e suggerimenti e rilevare i problemi noti.</span><span class="sxs-lookup"><span data-stu-id="5edfd-170">For HoloLens (first gen), use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

<span data-ttu-id="5edfd-171">Per HoloLens 2, usare lo strumento di [registrazione dei problemi](https://github.com/microsoft/HoloLens2ForCV/issues) nel repository HoloLens2ForCV per inviare commenti e suggerimenti e per tenere traccia dei problemi noti.</span><span class="sxs-lookup"><span data-stu-id="5edfd-171">For HoloLens 2, use the [issue tracker](https://github.com/microsoft/HoloLens2ForCV/issues) in the HoloLens2ForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="5edfd-172">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5edfd-172">See also</span></span>

* [<span data-ttu-id="5edfd-173">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="5edfd-173">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="5edfd-174">Repository GitHub HoloLensForCV</span><span class="sxs-lookup"><span data-stu-id="5edfd-174">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="5edfd-175">Repository GitHub HoloLens2ForCV</span><span class="sxs-lookup"><span data-stu-id="5edfd-175">HoloLens2ForCV GitHub repo</span></span>](https://github.com/microsoft/HoloLens2ForCV)
* [<span data-ttu-id="5edfd-176">Avviare il Portale di dispositivi di Windows</span><span class="sxs-lookup"><span data-stu-id="5edfd-176">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
