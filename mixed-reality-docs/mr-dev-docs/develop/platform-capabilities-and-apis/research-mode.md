---
title: Modalità di ricerca HoloLens
description: Usando la modalità di ricerca su HoloLens, un'applicazione può accedere ai flussi dei sensori del dispositivo chiave (profondità, rilevamento dell'ambiente e riflettanza IR).
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Modalità di ricerca, CV, RS4, visione artificiale, ricerca, HoloLens, HoloLens 2
ms.openlocfilehash: 327ee932dce99a2559e406630611dcc3c69a0002
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684965"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="3e587-104">Modalità di ricerca HoloLens</span><span class="sxs-lookup"><span data-stu-id="3e587-104">HoloLens Research Mode</span></span>

<span data-ttu-id="3e587-105">La modalità di ricerca è stata introdotta nella prima generazione HoloLens per consentire l'accesso ai sensori chiave sul dispositivo, in particolare per le applicazioni di ricerca che non sono destinate alla distribuzione.</span><span class="sxs-lookup"><span data-stu-id="3e587-105">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span>  <span data-ttu-id="3e587-106">La modalità di ricerca per HoloLens 2 mantiene le funzionalità di HoloLens 1, aggiungendo l'accesso a flussi aggiuntivi:</span><span class="sxs-lookup"><span data-stu-id="3e587-106">Research Mode for HoloLens 2 retains the capabilities of HoloLens 1, adding access to additional streams:</span></span>

* <span data-ttu-id="3e587-107">**Fotocamere di rilevamento dell'ambiente chiaro visibile** : fotocamere con scalabilità orizzontale usate dal sistema per il rilevamento delle intestazioni e la compilazione della mappa.</span><span class="sxs-lookup"><span data-stu-id="3e587-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="3e587-108">**Depth fotocamera** : funziona in due modalità:</span><span class="sxs-lookup"><span data-stu-id="3e587-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="3e587-109">AHAT, rilevamento a frequenza elevata (45 FPS) usato per il rilevamento manuale.</span><span class="sxs-lookup"><span data-stu-id="3e587-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="3e587-110">In modo diverso rispetto alla prima versione a breve termine, AHAT fornisce lo pseudo-Depth con la fase a capo superiore a 1 contatore.</span><span class="sxs-lookup"><span data-stu-id="3e587-110">Differently from the 1st version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="3e587-111">Rilevamento a lungo termine, a bassa frequenza (1-5 FPS) per un rilevamento approfondito usato dal [mapping spaziale](../../design/spatial-mapping.md)</span><span class="sxs-lookup"><span data-stu-id="3e587-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](../../design/spatial-mapping.md)</span></span>

* <span data-ttu-id="3e587-112">**Due versioni del flusso IR-riflettività** , usate dal HoloLens per calcolare la profondità.</span><span class="sxs-lookup"><span data-stu-id="3e587-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="3e587-113">Queste immagini sono illuminate dall'infrarosso e non sono interessate dalla luce visibile dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="3e587-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="3e587-114">Se si usa un HoloLens 2, è anche possibile accedere agli input aggiuntivi seguenti:</span><span class="sxs-lookup"><span data-stu-id="3e587-114">If you're using a HoloLens 2 you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="3e587-115">**Accelerometro** : usato dal sistema per determinare l'accelerazione lineare lungo gli assi X, Y e Z e la gravità.</span><span class="sxs-lookup"><span data-stu-id="3e587-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="3e587-116">**Gyro** : utilizzato dal sistema per determinare le rotazioni.</span><span class="sxs-lookup"><span data-stu-id="3e587-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="3e587-117">**Magnetometro** : utilizzato dal sistema per stimare l'orientamento assoluto.</span><span class="sxs-lookup"><span data-stu-id="3e587-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e587-118">La modalità di ricerca è attualmente disponibile in anteprima pubblica.</span><span class="sxs-lookup"><span data-stu-id="3e587-118">Research Mode is currently in Public Preview.</span></span> 

<span data-ttu-id="3e587-119">![Schermata dell'app modalità di ricerca](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="3e587-119">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="3e587-120">*Acquisizione di realtà mista di un'applicazione di test che visualizza gli otto flussi di sensori disponibili in modalità ricerca*</span><span class="sxs-lookup"><span data-stu-id="3e587-120">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="3e587-121">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="3e587-121">Usage</span></span>

<span data-ttu-id="3e587-122">La modalità di ricerca è progettata per ricercatori accademici e industriali che esplorano nuove idee nei campi di Visione artificiale e robotica.</span><span class="sxs-lookup"><span data-stu-id="3e587-122">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="3e587-123">Non è destinata alle applicazioni distribuite in ambienti aziendali o disponibili tramite il Microsoft Store o altri canali di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="3e587-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="3e587-124">Inoltre, Microsoft non garantisce che la modalità di ricerca o la funzionalità equivalente verrà supportata negli aggiornamenti futuri dell'hardware o del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="3e587-124">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="3e587-125">Tuttavia, ciò non impedisce di usarlo per sviluppare e testare nuove idee.</span><span class="sxs-lookup"><span data-stu-id="3e587-125">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="3e587-126">Sicurezza e prestazioni</span><span class="sxs-lookup"><span data-stu-id="3e587-126">Security and performance</span></span>

<span data-ttu-id="3e587-127">Tenere presente che l'abilitazione della modalità di ricerca usa più potenza della batteria rispetto all'uso di HoloLens 2 in condizioni normali.</span><span class="sxs-lookup"><span data-stu-id="3e587-127">Be aware that enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="3e587-128">Questo vale anche se l'applicazione che usa le funzionalità della modalità di ricerca non è in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="3e587-128">This is true even if the application using the Research Mode features is not running.</span></span>  <span data-ttu-id="3e587-129">L'abilitazione di questa modalità può anche ridurre la sicurezza complessiva del dispositivo perché le applicazioni possono usare i dati del sensore in modo errato.</span><span class="sxs-lookup"><span data-stu-id="3e587-129">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="3e587-130">Altre informazioni sulla sicurezza del dispositivo sono disponibili nelle [domande frequenti sulla sicurezza di HoloLens](https://docs.microsoft.com/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="3e587-130">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="3e587-131">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="3e587-131">Device support</span></span>
<table><span data-ttu-id="3e587-132">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="3e587-132">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="3e587-133"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="3e587-133"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="3e587-134"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="3e587-134"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="3e587-135"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="3e587-135"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="3e587-136">Fotocamere di rilevamento Head</span><span class="sxs-lookup"><span data-stu-id="3e587-136">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="3e587-137">✔️</span><span class="sxs-lookup"><span data-stu-id="3e587-137">✔️</span></span></td>
        <td><span data-ttu-id="3e587-138">✔️</span><span class="sxs-lookup"><span data-stu-id="3e587-138">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3e587-139">Profondità & fotocamera IR</span><span class="sxs-lookup"><span data-stu-id="3e587-139">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="3e587-140">✔️</span><span class="sxs-lookup"><span data-stu-id="3e587-140">✔️</span></span></td>
        <td><span data-ttu-id="3e587-141">✔️</span><span class="sxs-lookup"><span data-stu-id="3e587-141">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3e587-142">Accelerometro</span><span class="sxs-lookup"><span data-stu-id="3e587-142">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="3e587-143">✔️</span><span class="sxs-lookup"><span data-stu-id="3e587-143">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3e587-144">Giroscopio</span><span class="sxs-lookup"><span data-stu-id="3e587-144">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="3e587-145">✔️</span><span class="sxs-lookup"><span data-stu-id="3e587-145">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3e587-146">Magnetometro</span><span class="sxs-lookup"><span data-stu-id="3e587-146">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="3e587-147">✔️</span><span class="sxs-lookup"><span data-stu-id="3e587-147">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-1st-gen-and-hololens-2"></a><span data-ttu-id="3e587-148">Abilitazione della modalità di ricerca (HoloLens 1 gen e HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="3e587-148">Enabling Research Mode (HoloLens 1st Gen and HoloLens 2)</span></span>

<span data-ttu-id="3e587-149">La modalità di ricerca è un'estensione della modalità sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="3e587-149">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="3e587-150">Prima di iniziare, è necessario abilitare le funzionalità di sviluppo del dispositivo per accedere alle impostazioni della modalità di ricerca:</span><span class="sxs-lookup"><span data-stu-id="3e587-150">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="3e587-151">Aprire il **menu Start > impostazioni** e selezionare **aggiornamenti** .</span><span class="sxs-lookup"><span data-stu-id="3e587-151">Open **Start Menu > Settings** and select **Updates** .</span></span>
* <span data-ttu-id="3e587-152">Selezionare **per gli sviluppatori** e abilitare la **modalità sviluppatore** .</span><span class="sxs-lookup"><span data-stu-id="3e587-152">Select **For Developers** and enable **Developer Mode** .</span></span>
* <span data-ttu-id="3e587-153">Scorri verso il basso e abilita **Portale dispositivi** .</span><span class="sxs-lookup"><span data-stu-id="3e587-153">Scroll down and enable **Device Portal** .</span></span>

<span data-ttu-id="3e587-154">Una volta abilitate le funzionalità per gli sviluppatori, [connettersi al portale del dispositivo](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) per abilitare le funzionalità della modalità di ricerca:</span><span class="sxs-lookup"><span data-stu-id="3e587-154">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="3e587-155">Passare alla **modalità di ricerca di System >** nel **portale del dispositivo** .</span><span class="sxs-lookup"><span data-stu-id="3e587-155">Go to **System > Research Mode** in the **Device Portal** .</span></span>
* <span data-ttu-id="3e587-156">Selezionare **Consenti accesso al flusso del sensore** .</span><span class="sxs-lookup"><span data-stu-id="3e587-156">Select **Allow access to sensor stream** .</span></span>
* <span data-ttu-id="3e587-157">Riavviare il dispositivo dalla voce del menu **Power** nella parte superiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="3e587-157">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="3e587-158">Dopo aver riavviato il dispositivo, le applicazioni caricate tramite il **portale** per i dispositivi possono accedere ai flussi della modalità di ricerca.</span><span class="sxs-lookup"><span data-stu-id="3e587-158">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="3e587-159">![Scheda modalità ricerca del portale per dispositivi HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="3e587-159">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="3e587-160">*Finestra modalità di ricerca nel portale per dispositivi HoloLens*</span><span class="sxs-lookup"><span data-stu-id="3e587-160">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e587-161">La modalità di ricerca per HoloLens 2 è disponibile a partire dalla Build 19041,1356.</span><span class="sxs-lookup"><span data-stu-id="3e587-161">Research Mode for HoloLens 2 is available beginning with build 19041.1356.</span></span> <span data-ttu-id="3e587-162">Se è necessario accedere a una build precedente, iscriversi al programma di [Anteprima di insider](https://docs.microsoft.com/hololens/hololens-insider) .</span><span class="sxs-lookup"><span data-stu-id="3e587-162">If you need access in an earlier build, sign up for our [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) program.</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="3e587-163">Uso dei dati dei sensori nelle app</span><span class="sxs-lookup"><span data-stu-id="3e587-163">Using sensor data in your apps</span></span>

<span data-ttu-id="3e587-164">Le applicazioni possono accedere ai dati del flusso dei sensori nello stesso modo in cui si accede ai flussi della fotocamera e della foto tramite [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span><span class="sxs-lookup"><span data-stu-id="3e587-164">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="3e587-165">Tutte le API che funzionano per lo sviluppo di HoloLens sono disponibili anche in modalità ricerca.</span><span class="sxs-lookup"><span data-stu-id="3e587-165">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="3e587-166">In particolare, l'applicazione conosce esattamente dove HoloLens si trova nello spazio 6DoF a ogni tempo di acquisizione del fotogramma del sensore.</span><span class="sxs-lookup"><span data-stu-id="3e587-166">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="3e587-167">È possibile trovare applicazioni di esempio sull'accesso ai vari flussi della modalità di ricerca, usando le [funzioni intrinseche ed estrinseche](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)e registrando i flussi nei rispettivi repository in modalità di ricerca:</span><span class="sxs-lookup"><span data-stu-id="3e587-167">You can find sample applications on accessing the various Research Mode streams, using the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and recording streams in the respective Research Mode repos:</span></span>
* [<span data-ttu-id="3e587-168">HoloLens (prima generazione)</span><span class="sxs-lookup"><span data-stu-id="3e587-168">HoloLens (1st gen)</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="3e587-169">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3e587-169">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a><span data-ttu-id="3e587-170">Supporto</span><span class="sxs-lookup"><span data-stu-id="3e587-170">Support</span></span>

<span data-ttu-id="3e587-171">Per HoloLens (1st Gen), usare lo strumento di [registrazione dei problemi](https://github.com/Microsoft/HololensForCV/issues) nel repository HoloLensForCV per inviare commenti e suggerimenti e rilevare i problemi noti.</span><span class="sxs-lookup"><span data-stu-id="3e587-171">For HoloLens (1st gen), please use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

<span data-ttu-id="3e587-172">Per HoloLens 2, usare lo strumento di [registrazione dei problemi](https://github.com/microsoft/HoloLens2ForCV/issues) nel repository HoloLens2ForCV per inviare commenti e suggerimenti e rilevare i problemi noti.</span><span class="sxs-lookup"><span data-stu-id="3e587-172">For HoloLens 2, please use the [issue tracker](https://github.com/microsoft/HoloLens2ForCV/issues) in the HoloLens2ForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e587-173">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3e587-173">See also</span></span>

* [<span data-ttu-id="3e587-174">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="3e587-174">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="3e587-175">Repository GitHub HoloLensForCV</span><span class="sxs-lookup"><span data-stu-id="3e587-175">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="3e587-176">Repository GitHub HoloLens2ForCV</span><span class="sxs-lookup"><span data-stu-id="3e587-176">HoloLens2ForCV GitHub repo</span></span>](https://github.com/microsoft/HoloLens2ForCV)
* [<span data-ttu-id="3e587-177">Avviare il Portale di dispositivi di Windows</span><span class="sxs-lookup"><span data-stu-id="3e587-177">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
