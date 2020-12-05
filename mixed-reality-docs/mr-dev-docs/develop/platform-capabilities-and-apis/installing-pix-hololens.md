---
title: Installazione di PIX per HoloLens 2
description: Informazioni su come installare PIX per i dispositivi HoloLens 2.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIX, acquisizione, cuffia a realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 4554600414784b2644006e6e891f16f8ce3a79f5
ms.sourcegitcommit: 924f8c1ceb93c378f800cf88d82944cf80f092bc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96615363"
---
# <a name="installing-pix-for-hololens-2"></a><span data-ttu-id="bbea2-104">Installazione di PIX per HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bbea2-104">Installing PIX for HoloLens 2</span></span>

<span data-ttu-id="bbea2-105">[Pix](https://devblogs.microsoft.com/pix) è uno strumento di ottimizzazione e debug delle prestazioni per le applicazioni DirectX 12 in Windows.</span><span class="sxs-lookup"><span data-stu-id="bbea2-105">[PIX](https://devblogs.microsoft.com/pix) is a performance tuning and debugging tool for DirectX 12 applications on Windows.</span></span> 

## <a name="setup"></a><span data-ttu-id="bbea2-106">Configurazione</span><span class="sxs-lookup"><span data-stu-id="bbea2-106">Setup</span></span>

1. <span data-ttu-id="bbea2-107">Scaricare la [versione]( https://devblogs.microsoft.com/pix/download) più recente di pix dal PC host e connettere HoloLens 2 al PC tramite un cavo USB.</span><span class="sxs-lookup"><span data-stu-id="bbea2-107">Grab the latest PIX [release]( https://devblogs.microsoft.com/pix/download) from your host PC and connect your HoloLens 2 to your PC via a USB cable.</span></span>

2. <span data-ttu-id="bbea2-108">Se il HoloLens 2 si trova in una [Build di Windows Insider](https://insider.windows.com) o ha una configurazione che interrompe Pix,  [riavviare il dispositivo](https://docs.microsoft.com/hololens/hololens-recovery) per cancellare tutti i dati.</span><span class="sxs-lookup"><span data-stu-id="bbea2-108">If your HoloLens 2 is on a [Windows Insider build](https://insider.windows.com) or has a configuration that breaks PIX,  [re-flash your device](https://docs.microsoft.com/hololens/hololens-recovery) to erase all data.</span></span>

3. <span data-ttu-id="bbea2-109">Abilitare la **modalità sviluppatore** e il portale per i **dispositivi**:</span><span class="sxs-lookup"><span data-stu-id="bbea2-109">Enable **Developer Mode** and **Device Portal**:</span></span>

* <span data-ttu-id="bbea2-110">Apri **Impostazioni** dalla shell:</span><span class="sxs-lookup"><span data-stu-id="bbea2-110">Open **Settings** from Shell:</span></span>

![Screenshot del menu HoloLens con il pulsante Impostazioni evidenziato](images/pix-img-01.jpg)

* <span data-ttu-id="bbea2-112">Selezionare **aggiorna & sicurezza**:</span><span class="sxs-lookup"><span data-stu-id="bbea2-112">Select **Update & Security**:</span></span>

![Screenshot della finestra Impostazioni aperta in HoloLens con il pulsante Aggiorna e sicurezza evidenziato](images/pix-img-02.jpg)

* <span data-ttu-id="bbea2-114">Fare clic **per gli sviluppatori**:</span><span class="sxs-lookup"><span data-stu-id="bbea2-114">Click **For Developers**:</span></span>

![Screenshot della finestra sicurezza e aggiornamenti Apri con per gli sviluppatori pulsante evidenziato](images/pix-img-03.jpg)

* <span data-ttu-id="bbea2-116">Attivare **Usa funzionalità** per gli sviluppatori e **abilitare il portale** per i dispositivi</span><span class="sxs-lookup"><span data-stu-id="bbea2-116">Turn on **Use Developer Features** and **Enable Device Portal**</span></span>

![Screenshot della finestra per sviluppatori aprire in impostazioni con il pulsante Abilita il portale del dispositivo evidenziato](images/pix-img-04.jpg)

![Screenshot della finestra per sviluppatori aperta in impostazioni con l'opzione Usa sviluppo funzionalità evidenziata](images/pix-img-05.jpg)

* <span data-ttu-id="bbea2-119">Con il dispositivo ancora connesso, sveglio e con l'utente connesso, avviare Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bbea2-119">With the device still connected, awake, and with the user logged in, launch Visual Studio.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bbea2-120">Verificare che il dispositivo non sia in modalità standby o in stato di sospensione.</span><span class="sxs-lookup"><span data-stu-id="bbea2-120">Make sure your device isn't in standby mode or asleep.</span></span> <span data-ttu-id="bbea2-121">In caso di problemi con questo passaggio, fare riferimento alle istruzioni del portale per i [dispositivi Windows](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span><span class="sxs-lookup"><span data-stu-id="bbea2-121">If you're having trouble with this step, refer to the [Windows Device Portal instructions](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span></span>

## <a name="preparing-for-deployment"></a><span data-ttu-id="bbea2-122">Preparazione per la distribuzione</span><span class="sxs-lookup"><span data-stu-id="bbea2-122">Preparing for deployment</span></span>

1. <span data-ttu-id="bbea2-123">In Visual Studio impostare **arm64** come piattaforma e **dispositivo** come dispositivo:</span><span class="sxs-lookup"><span data-stu-id="bbea2-123">In Visual Studio, set **ARM64** as the platform and **Device** as the device:</span></span>

![Screenshot della soluzione Visual Studio con impostazioni della piattaforma e del dispositivo evidenziate](images/pix-img-06.png)

2. <span data-ttu-id="bbea2-125">Quando Visual Studio richiede un **pin** dal dispositivo:</span><span class="sxs-lookup"><span data-stu-id="bbea2-125">When Visual Studio prompts you for a **PIN** from the device:</span></span>

![Screenshot del popup di Visual Studio che richiede PIN](images/pix-img-07.png)

* <span data-ttu-id="bbea2-127">Selezionare **le impostazioni** dalla shell</span><span class="sxs-lookup"><span data-stu-id="bbea2-127">Select **Settings** from Shell</span></span>
* <span data-ttu-id="bbea2-128">Selezionare **aggiorna & sicurezza**</span><span class="sxs-lookup"><span data-stu-id="bbea2-128">Select **Update & Security**</span></span>
* <span data-ttu-id="bbea2-129">Fare clic **per gli sviluppatori** e premere associa in **Individuazione dispositivo**</span><span class="sxs-lookup"><span data-stu-id="bbea2-129">Click **For Developers** and press Pair under **Device Discovery**</span></span> 

![Screenshot della finestra per sviluppatori aperta in impostazioni con individuazione dispositivo evidenziata](images/pix-img-08.jpg)

![Screenshot del popup del dispositivo a pagamento con il codice di registrazione evidenziato](images/pix-img-09.jpg)

* <span data-ttu-id="bbea2-132">Immettere il numero di PIN generato in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bbea2-132">Enter the generated PIN number in Visual Studio</span></span>

3. <span data-ttu-id="bbea2-133">In Visual Studio l'app verrà distribuita nel HoloLens 2 connesso, operazione che può richiedere alcuni minuti a seconda dell'app.</span><span class="sxs-lookup"><span data-stu-id="bbea2-133">Visual Studio will deploy the app to the connected HoloLens 2, which may take a few minutes depending on the app.</span></span>

## <a name="launching-pix"></a><span data-ttu-id="bbea2-134">Avvio di PIX</span><span class="sxs-lookup"><span data-stu-id="bbea2-134">Launching PIX</span></span>

<span data-ttu-id="bbea2-135">Per prima cosa, usare il portale del dispositivo per verificare che l'app non sia in esecuzione nel HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="bbea2-135">First, use Device Portal to verify the app is not running on the HoloLens 2.</span></span> <span data-ttu-id="bbea2-136">Avviare quindi PIX, connettersi al dispositivo e fare clic su **Home**:</span><span class="sxs-lookup"><span data-stu-id="bbea2-136">Then, launch PIX, connect to your device, and click **Home**:</span></span>

![Screenshot della schermata iniziale dell'applicazione PIX](images/pix-img-10.png)

* <span data-ttu-id="bbea2-138">Selezionare **Connetti** dal menu a sinistra:</span><span class="sxs-lookup"><span data-stu-id="bbea2-138">Select **Connect** from the left-side menu:</span></span>

![Screenshot del menu a sinistra dell'applicazione PIX con il pulsante Connetti evidenziato](images/pix-img-11.png)

2. <span data-ttu-id="bbea2-140">Nella scheda **computer** fare clic su **Aggiungi** e immettere le credenziali seguenti:</span><span class="sxs-lookup"><span data-stu-id="bbea2-140">From the **Computer** tab, click **Add** and enter the following credentials:</span></span>
    * <span data-ttu-id="bbea2-141">Alias: a discrezione dell'utente</span><span class="sxs-lookup"><span data-stu-id="bbea2-141">Alias: Up to user’s discretion</span></span>
    * <span data-ttu-id="bbea2-142">Nome host o indirizzo IP: 127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="bbea2-142">Host Name or IP Address: 127.0.0.1</span></span>

3. <span data-ttu-id="bbea2-143">Fare clic su **Connetti** nella parte inferiore destra della scheda **computer** :</span><span class="sxs-lookup"><span data-stu-id="bbea2-143">Click **Connect** in the lower-right of the **Computer** tab:</span></span>

![Screenshot della finestra di connessione all'applicazione PIX con alias, nome host, indirizzo IP e pulsante Aggiungi evidenziato](images/pix-img-12.png)

> [!NOTE]
> <span data-ttu-id="bbea2-145">La prima connessione è sempre più lenta perché i file binari vengono copiati.</span><span class="sxs-lookup"><span data-stu-id="bbea2-145">The first connection is always slower because binaries are being copied.</span></span>

4. <span data-ttu-id="bbea2-146">Quando PIX si è connesso a HoloLens 2, trovare l'app nella sezione **selezionare il processo di destinazione** nella scheda Avvia UWP e fare clic su **Avvia**:</span><span class="sxs-lookup"><span data-stu-id="bbea2-146">When PIX has connected to the HoloLens 2, find your app in the **Select Target Process** section in the Launch UWP tab, and click **Launch**:</span></span>

![Screenshot dell'applicazione PIX con la finestra selezione processo di destinazione e il pulsante Avvia evidenziato](images/pix-img-13.png)

## <a name="gpu-captured"></a><span data-ttu-id="bbea2-148">GPU acquisita</span><span class="sxs-lookup"><span data-stu-id="bbea2-148">GPU captured</span></span>

1. <span data-ttu-id="bbea2-149">Avviare l'acquisizione della GPU facendo clic su **Photo** nella sezione **acquisizione GPU** :</span><span class="sxs-lookup"><span data-stu-id="bbea2-149">Start the GPU capture by clicking **Photo** in the **GPU Capture** section:</span></span>

![Screenshot dell'applicazione PIX con il pannello di connessione PC aperto con l'acquisizione GPU evidenziato](images/pix-img-14.png)

2. <span data-ttu-id="bbea2-151">Aprire l'acquisizione per l'analisi facendo clic sullo screenshot generato nel pannello **acquisizione GPU** :</span><span class="sxs-lookup"><span data-stu-id="bbea2-151">Open the capture for analysis by clicking on the generated screen shot in the **GPU Capture** panel:</span></span>

![Screenshot dell'applicazione PIX con la sezione acquisizione GPU aperta con il pannello di acquisizione GPU evidenziato](images/pix-img-15.png)

3. <span data-ttu-id="bbea2-153">Premere **Start** per avviare l'analisi:</span><span class="sxs-lookup"><span data-stu-id="bbea2-153">Press **Start** to begin the analysis:</span></span>

![Screenshot dell'applicazione PIX con il pulsante Start evidenziato](images/pix-img-16.png)

> [!IMPORTANT]
> <span data-ttu-id="bbea2-155">Se si raccolgono dati di temporizzazione dopo aver eseguito un'acquisizione GPU, sarà necessario riavviare l'auricolare.</span><span class="sxs-lookup"><span data-stu-id="bbea2-155">If you collect timing data after taking a GPU capture, you'll be required to reboot the headset.</span></span> <span data-ttu-id="bbea2-156">Si tratta di un riavvio unico del dispositivo ed è necessario per la raccolta dei dati di temporizzazione.</span><span class="sxs-lookup"><span data-stu-id="bbea2-156">This is a one-time restart of the device and is required for timing data collection.</span></span>

<span data-ttu-id="bbea2-157">PIX è ora pronto per l'uso.</span><span class="sxs-lookup"><span data-stu-id="bbea2-157">PIX is now ready for use!</span></span>

## <a name="see-also"></a><span data-ttu-id="bbea2-158">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bbea2-158">See also</span></span>
* [<span data-ttu-id="bbea2-159">Home page di PIX</span><span class="sxs-lookup"><span data-stu-id="bbea2-159">PIX homepage</span></span>](https://devblogs.microsoft.com/pix)