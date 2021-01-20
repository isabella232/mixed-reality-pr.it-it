---
title: Installazione PIX per HoloLens 2
description: Informazioni su come installare PIX per i dispositivi HoloLens 2.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIX, acquisizione, cuffia a realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 29cb741cd986fbb98dabb1faf2051450fd0286c3
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583089"
---
# <a name="installing-pix-for-hololens-2"></a><span data-ttu-id="96cc6-104">Installazione PIX per HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="96cc6-104">Installing PIX for HoloLens 2</span></span>

<span data-ttu-id="96cc6-105">[Pix](https://devblogs.microsoft.com/pix) è uno strumento di ottimizzazione e debug delle prestazioni per le applicazioni DirectX 12 in Windows.</span><span class="sxs-lookup"><span data-stu-id="96cc6-105">[PIX](https://devblogs.microsoft.com/pix) is a performance tuning and debugging tool for DirectX 12 applications on Windows.</span></span> 

## <a name="setup"></a><span data-ttu-id="96cc6-106">Configurazione</span><span class="sxs-lookup"><span data-stu-id="96cc6-106">Setup</span></span>

1. <span data-ttu-id="96cc6-107">Scaricare la [versione]( https://devblogs.microsoft.com/pix/download) più recente di pix dal PC host e connettere HoloLens 2 al PC tramite un cavo USB.</span><span class="sxs-lookup"><span data-stu-id="96cc6-107">Grab the latest PIX [release]( https://devblogs.microsoft.com/pix/download) from your host PC and connect your HoloLens 2 to your PC via a USB cable.</span></span>

2. <span data-ttu-id="96cc6-108">Se il HoloLens 2 si trova in una [Build di Windows Insider](https://insider.windows.com) o ha una configurazione che interrompe Pix,  [relampeggiare il dispositivo](/hololens/hololens-recovery) per cancellare tutti i dati.</span><span class="sxs-lookup"><span data-stu-id="96cc6-108">If your HoloLens 2 is on a [Windows Insider build](https://insider.windows.com) or has a configuration that breaks PIX,  [reflash your device](/hololens/hololens-recovery) to erase all data.</span></span>

3. <span data-ttu-id="96cc6-109">Abilitare la **modalità sviluppatore** e il portale per i **dispositivi**:</span><span class="sxs-lookup"><span data-stu-id="96cc6-109">Enable **Developer Mode** and **Device Portal**:</span></span>

* <span data-ttu-id="96cc6-110">Aprire **le impostazioni** dalla Home realtà mista:</span><span class="sxs-lookup"><span data-stu-id="96cc6-110">Open **Settings** from Mixed Reality Home:</span></span>

![Screenshot del menu HoloLens con il pulsante Impostazioni evidenziato](images/pix-img-01.jpg)

* <span data-ttu-id="96cc6-112">Selezionare **aggiorna & sicurezza**:</span><span class="sxs-lookup"><span data-stu-id="96cc6-112">Select **Update & Security**:</span></span>

![Screenshot della finestra Impostazioni aperta in HoloLens con il pulsante Aggiorna e sicurezza evidenziato](images/pix-img-02.jpg)

* <span data-ttu-id="96cc6-114">Seleziona **per gli sviluppatori**:</span><span class="sxs-lookup"><span data-stu-id="96cc6-114">Select **For Developers**:</span></span>

![Screenshot della finestra sicurezza e aggiornamenti Apri con per gli sviluppatori pulsante evidenziato](images/pix-img-03.jpg)

* <span data-ttu-id="96cc6-116">Attivare **Usa funzionalità** per gli sviluppatori e **abilitare il portale** per i dispositivi</span><span class="sxs-lookup"><span data-stu-id="96cc6-116">Turn on **Use Developer Features** and **Enable Device Portal**</span></span>

![Screenshot della finestra per sviluppatori aprire in impostazioni con il pulsante Abilita il portale del dispositivo evidenziato](images/pix-img-04.jpg)

![Screenshot della finestra per sviluppatori aperta in impostazioni con l'opzione Usa sviluppo funzionalità evidenziata](images/pix-img-05.jpg)

* <span data-ttu-id="96cc6-119">Con il dispositivo ancora connesso, sveglio e con l'utente connesso, avviare Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="96cc6-119">With the device still connected, awake, and with the user logged in, launch Visual Studio.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96cc6-120">Verificare che il dispositivo non sia in modalità standby o in stato di sospensione.</span><span class="sxs-lookup"><span data-stu-id="96cc6-120">Make sure your device isn't in standby mode or asleep.</span></span> <span data-ttu-id="96cc6-121">In caso di problemi con questo passaggio, fare riferimento alle istruzioni del portale per i [dispositivi Windows](./using-the-windows-device-portal.md).</span><span class="sxs-lookup"><span data-stu-id="96cc6-121">If you're having trouble with this step, refer to the [Windows Device Portal instructions](./using-the-windows-device-portal.md).</span></span>

## <a name="preparing-for-deployment"></a><span data-ttu-id="96cc6-122">Preparazione per la distribuzione</span><span class="sxs-lookup"><span data-stu-id="96cc6-122">Preparing for deployment</span></span>

1. <span data-ttu-id="96cc6-123">In Visual Studio impostare **arm64** come piattaforma e **dispositivo** come dispositivo:</span><span class="sxs-lookup"><span data-stu-id="96cc6-123">In Visual Studio, set **ARM64** as the platform and **Device** as the device:</span></span>

![Screenshot della soluzione Visual Studio con impostazioni della piattaforma e del dispositivo evidenziate](images/pix-img-06.png)

2. <span data-ttu-id="96cc6-125">Quando Visual Studio richiede un **pin** dal dispositivo:</span><span class="sxs-lookup"><span data-stu-id="96cc6-125">When Visual Studio prompts you for a **PIN** from the device:</span></span>

![Screenshot del popup di Visual Studio che richiede PIN](images/pix-img-07.png)

* <span data-ttu-id="96cc6-127">Selezionare **le impostazioni** dalla shell</span><span class="sxs-lookup"><span data-stu-id="96cc6-127">Select **Settings** from Shell</span></span>
* <span data-ttu-id="96cc6-128">Selezionare **aggiorna & sicurezza**</span><span class="sxs-lookup"><span data-stu-id="96cc6-128">Select **Update & Security**</span></span>
* <span data-ttu-id="96cc6-129">Selezionare **per gli sviluppatori** e premere associa in **Individuazione dispositivo**</span><span class="sxs-lookup"><span data-stu-id="96cc6-129">Select **For Developers** and press Pair under **Device Discovery**</span></span> 

![Screenshot della finestra per sviluppatori aperta in impostazioni con individuazione dispositivo evidenziata](images/pix-img-08.jpg)

![Screenshot del popup del dispositivo a pagamento con il codice di registrazione evidenziato](images/pix-img-09.jpg)

* <span data-ttu-id="96cc6-132">Immettere il numero di PIN generato in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="96cc6-132">Enter the generated PIN number in Visual Studio</span></span>

3. <span data-ttu-id="96cc6-133">In Visual Studio l'app verrà distribuita nel HoloLens 2 connesso, operazione che può richiedere alcuni minuti a seconda dell'app.</span><span class="sxs-lookup"><span data-stu-id="96cc6-133">Visual Studio will deploy the app to the connected HoloLens 2, which may take a few minutes depending on the app.</span></span>

## <a name="launching-pix"></a><span data-ttu-id="96cc6-134">Avvio di PIX</span><span class="sxs-lookup"><span data-stu-id="96cc6-134">Launching PIX</span></span>

<span data-ttu-id="96cc6-135">Per prima cosa, usare il portale del dispositivo per verificare che l'app non sia in esecuzione nel HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="96cc6-135">First, use Device Portal to verify the app isn't running on the HoloLens 2.</span></span> <span data-ttu-id="96cc6-136">Avviare quindi PIX, connettersi al dispositivo e selezionare **Home**:</span><span class="sxs-lookup"><span data-stu-id="96cc6-136">Then, launch PIX, connect to your device, and select **Home**:</span></span>

![Screenshot della schermata iniziale dell'applicazione PIX](images/pix-img-10.png)

* <span data-ttu-id="96cc6-138">Selezionare **Connetti** dal menu a sinistra:</span><span class="sxs-lookup"><span data-stu-id="96cc6-138">Select **Connect** from the left-side menu:</span></span>

![Screenshot del menu a sinistra dell'applicazione PIX con il pulsante Connetti evidenziato](images/pix-img-11.png)

2. <span data-ttu-id="96cc6-140">Nella scheda **computer** selezionare **Aggiungi** e immettere le credenziali seguenti:</span><span class="sxs-lookup"><span data-stu-id="96cc6-140">From the **Computer** tab, select **Add**, and enter the following credentials:</span></span>
    * <span data-ttu-id="96cc6-141">Alias: a discrezione dell'utente</span><span class="sxs-lookup"><span data-stu-id="96cc6-141">Alias: Up to user’s discretion</span></span>
    * <span data-ttu-id="96cc6-142">Nome host o indirizzo IP: 127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="96cc6-142">Host Name or IP Address: 127.0.0.1</span></span>

3. <span data-ttu-id="96cc6-143">Selezionare **Connetti** in basso a destra nella scheda **computer** :</span><span class="sxs-lookup"><span data-stu-id="96cc6-143">Select **Connect** in the lower right of the **Computer** tab:</span></span>

![Screenshot della finestra di connessione all'applicazione PIX con alias, nome host, indirizzo IP e pulsante Aggiungi evidenziato](images/pix-img-12.png)

> [!NOTE]
> <span data-ttu-id="96cc6-145">La prima connessione è sempre più lenta perché i file binari vengono copiati.</span><span class="sxs-lookup"><span data-stu-id="96cc6-145">The first connection is always slower because binaries are being copied.</span></span>

4. <span data-ttu-id="96cc6-146">Quando PIX si è connesso a HoloLens 2, trovare l'app nella sezione **selezionare il processo di destinazione** nella scheda Avvia UWP e selezionare **Avvia**:</span><span class="sxs-lookup"><span data-stu-id="96cc6-146">When PIX has connected to the HoloLens 2, find your app in the **Select Target Process** section in the Launch UWP tab, and select **Launch**:</span></span>

![Screenshot dell'applicazione PIX con la finestra selezione processo di destinazione e il pulsante Avvia evidenziato](images/pix-img-13.png)

## <a name="gpu-captured"></a><span data-ttu-id="96cc6-148">GPU acquisita</span><span class="sxs-lookup"><span data-stu-id="96cc6-148">GPU captured</span></span>

1. <span data-ttu-id="96cc6-149">Avviare l'acquisizione della GPU facendo clic su **Photo** nella sezione **acquisizione GPU** :</span><span class="sxs-lookup"><span data-stu-id="96cc6-149">Start the GPU capture by clicking **Photo** in the **GPU Capture** section:</span></span>

![Screenshot dell'applicazione PIX con il pannello di connessione PC aperto con l'acquisizione GPU evidenziato](images/pix-img-14.png)

2. <span data-ttu-id="96cc6-151">Aprire l'acquisizione per l'analisi facendo clic sullo screenshot generato nel pannello **acquisizione GPU** :</span><span class="sxs-lookup"><span data-stu-id="96cc6-151">Open the capture for analysis by clicking on the generated screenshot in the **GPU Capture** panel:</span></span>

![Screenshot dell'applicazione PIX con la sezione acquisizione GPU aperta con il pannello di acquisizione GPU evidenziato](images/pix-img-15.png)

3. <span data-ttu-id="96cc6-153">Premere **Start** per avviare l'analisi:</span><span class="sxs-lookup"><span data-stu-id="96cc6-153">Press **Start** to begin the analysis:</span></span>

![Screenshot dell'applicazione PIX con il pulsante Start evidenziato](images/pix-img-16.png)

> [!IMPORTANT]
> <span data-ttu-id="96cc6-155">Se si raccolgono dati di temporizzazione dopo aver eseguito un'acquisizione GPU, sarà necessario riavviare l'auricolare.</span><span class="sxs-lookup"><span data-stu-id="96cc6-155">If you collect timing data after taking a GPU capture, you'll be required to reboot the headset.</span></span> <span data-ttu-id="96cc6-156">Si tratta di un riavvio unico del dispositivo ed è necessario per la raccolta dei dati di temporizzazione.</span><span class="sxs-lookup"><span data-stu-id="96cc6-156">This is a one-time restart of the device and is required for timing data collection.</span></span>

<span data-ttu-id="96cc6-157">PIX è ora pronto per l'uso.</span><span class="sxs-lookup"><span data-stu-id="96cc6-157">PIX is now ready for use!</span></span>

## <a name="see-also"></a><span data-ttu-id="96cc6-158">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="96cc6-158">See also</span></span>
* [<span data-ttu-id="96cc6-159">Home page di PIX</span><span class="sxs-lookup"><span data-stu-id="96cc6-159">PIX homepage</span></span>](https://devblogs.microsoft.com/pix)