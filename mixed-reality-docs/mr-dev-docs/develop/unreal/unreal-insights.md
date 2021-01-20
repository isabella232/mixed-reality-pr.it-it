---
title: Profilatura con Unreal Insights
description: Informazioni su come usare Unreal Insights in HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal Engine 4, UE4, HoloLens, HoloLens 2, sviluppo, profling, Unreal Insights, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi, cuffie per realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: b41d36679adfb35b5cc3561b8d5e7734654e7fb5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580829"
---
# <a name="profiling-with-unreal-insights"></a><span data-ttu-id="c65d8-104">Profilatura con Unreal Insights</span><span class="sxs-lookup"><span data-stu-id="c65d8-104">Profiling with Unreal Insights</span></span> 

<span data-ttu-id="c65d8-105">[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) è un sistema di profilatura che raccoglie, analizza e Visualizza i dati da Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="c65d8-105">[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) is a profiling system that collects, analyzes, and visualizes data from Unreal Engine.</span></span> <span data-ttu-id="c65d8-106">Il sistema di profilatura consente di individuare i colli di bottiglia e le aree di ottimizzazione in cui le prestazioni delle app possono usare un Boost.</span><span class="sxs-lookup"><span data-stu-id="c65d8-106">The profiling system can help you find optimization bottlenecks and areas where you apps performance could use a boost.</span></span> <span data-ttu-id="c65d8-107">In genere, si abilitano le informazioni dettagliate non reali direttamente dall'editor, ma per HoloLens 2 è necessario usare la riga di comando.</span><span class="sxs-lookup"><span data-stu-id="c65d8-107">Normally, you enable Unreal Insights right from the editor, but for HoloLens 2 you'll need to use the command line.</span></span>  

## <a name="setup"></a><span data-ttu-id="c65d8-108">Configurazione</span><span class="sxs-lookup"><span data-stu-id="c65d8-108">Setup</span></span>

<span data-ttu-id="c65d8-109">Unreal consente di creare e configurare un "profilo personalizzato" nell'utilità di avvio HoloLens con i parametri della riga di comando che abilitano le informazioni non reali.</span><span class="sxs-lookup"><span data-stu-id="c65d8-109">Unreal lets you to create and configure a "Custom Profile" in the HoloLens launcher with the command line parameters that enable Unreal Insights.</span></span>

1.  <span data-ttu-id="c65d8-110">Individuare l'indirizzo IP del computer utilizzando il comando **ipconfig** al prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="c65d8-110">Find the IP address of your computer using the **ipconfig** command on the command prompt.</span></span> <span data-ttu-id="c65d8-111">L'indirizzo IP è l'indirizzo IPv4 elencato da ipconfig.</span><span class="sxs-lookup"><span data-stu-id="c65d8-111">The IP address is the IPv4 address listed by ipconfig.</span></span> <span data-ttu-id="c65d8-112">Tenere presente questo aspetto per un momento successivo quando si impostano i parametri della riga di comando.</span><span class="sxs-lookup"><span data-stu-id="c65d8-112">Keep this in mind for later when you set Command Line Parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c65d8-113">Se si è protetti da una VPN, potrebbe essere necessario specificare l'indirizzo IP fornito tramite la VPN.</span><span class="sxs-lookup"><span data-stu-id="c65d8-113">If you're behind a VPN, you may need to provide the IP address provided via the VPN instead.</span></span>

![Screenshot dei risultati della riga di comando per il comando ipconfig](images/unreal-insights-img-01.png)

2.  <span data-ttu-id="c65d8-115">Passare alla parte superiore del pannello Unreal Engine e aprire **Device Manager** sotto il pulsante **Launch (avvia** ):</span><span class="sxs-lookup"><span data-stu-id="c65d8-115">Go to the top of the Unreal Engine panel and open **Device Manager** under the **Launch** button:</span></span>

![Screenshot delle opzioni di avvio con gestione dispositivi evidenziato](images/unreal-insights-img-02.png)

3.  <span data-ttu-id="c65d8-117">Nella Device Manager selezionare **Aggiungi un dispositivo** non in elenco:</span><span class="sxs-lookup"><span data-stu-id="c65d8-117">In the Device Manager, select **Add an Unlisted Device**:</span></span>

![Screenshot di gestione dispositivi aperto in Unreal Engine](images/unreal-insights-img-03.png)

4. <span data-ttu-id="c65d8-119">Fare clic su **selezionare una piattaforma** e scegliere **HoloLens**:</span><span class="sxs-lookup"><span data-stu-id="c65d8-119">Click **Select a platform** and choose **HoloLens**:</span></span>

![Screenshot dell'elenco a discesa Aggiungi dispositivo non in elenco con HoloLens evidenziato](images/unreal-insights-img-04.png)

5.  <span data-ttu-id="c65d8-121">Se si usa IPoverUSB, immettere 127.0.0.1:10080 come identificatore del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c65d8-121">If you're using IPoverUSB, enter 127.0.0.1:10080 as the Device Identifier.</span></span> <span data-ttu-id="c65d8-122">Immettere l'utente e la password di HoloLens nei rispettivi campi e compilare il **nome visualizzato** come desiderato.</span><span class="sxs-lookup"><span data-stu-id="c65d8-122">Enter your HoloLens user and password in their respective fields and fill **Display Name** as you wish.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c65d8-123">L'identificatore del dispositivo è l'indirizzo IP del HoloLens, non del computer che esegue informazioni dettagliate non reali trovate nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="c65d8-123">The Device Identifier is the IP address of the HoloLens, NOT of the computer running Unreal Insights you found in step 1.</span></span>

![Schermata dei dettagli del dispositivo HoloLens in gestione dispositivi](images/unreal-insights-img-05.png)

6.  <span data-ttu-id="c65d8-125">Selezionare **Aggiungi** per visualizzare il HoloLens nell'elenco dei dispositivi di gestione dispositivi:</span><span class="sxs-lookup"><span data-stu-id="c65d8-125">Select **Add** and your HoloLens should appear in the device list of the device manager:</span></span>

![Screenshot di HoloLens aggiunto all'elenco dei dispositivi](images/unreal-insights-img-06.png)

## <a name="launch"></a><span data-ttu-id="c65d8-127">Launch</span><span class="sxs-lookup"><span data-stu-id="c65d8-127">Launch</span></span>

1. <span data-ttu-id="c65d8-128">Aprire **avvio progetto** dal pannello UE4 sotto il pulsante **Launch (avvia** ):</span><span class="sxs-lookup"><span data-stu-id="c65d8-128">Open **Project Launcher** from the UE4 panel under the **Launch** button:</span></span>

![Screenshot delle opzioni di avvio con avvio del progetto evidenziato](images/unreal-insights-img-07.png)

2. <span data-ttu-id="c65d8-130">Selezionare il **+** pulsante per creare un profilo personalizzato in **profili di avvio personalizzati**.</span><span class="sxs-lookup"><span data-stu-id="c65d8-130">Select the **+** button to create a custom profile under **Custom Launch Profiles**.</span></span> <span data-ttu-id="c65d8-131">Una volta creato, è sempre possibile modificare il profilo in un secondo momento:</span><span class="sxs-lookup"><span data-stu-id="c65d8-131">Once created, you can always edit this profile later:</span></span>

![Screenshot dell'utilità di avvio del progetto con profili di avvio personalizzati evidenziati](images/unreal-insights-img-08.png)

3. <span data-ttu-id="c65d8-133">Selezionare il pulsante **modifica profilo** nel profilo di avvio personalizzato di HoloLens e configurare:</span><span class="sxs-lookup"><span data-stu-id="c65d8-133">Select **edit profile** button on the HoloLens custom launch profile and configure:</span></span>
    * <span data-ttu-id="c65d8-134">Selezionare **Cook** to **by the book** per abilitare la copia nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="c65d8-134">Select **Cook** to **By the Book** to enable copying to device</span></span>
    * <span data-ttu-id="c65d8-135">È possibile scegliere di archiviare l'archivio **?** nella sezione **Archivio** per mantenere il. appxbundle generato anziché eliminare per risparmiare spazio su disco.</span><span class="sxs-lookup"><span data-stu-id="c65d8-135">You may want to check **Do you wish to archive?** in the **Archive** section to retain the generated .appxbundle rather than deleting to save disk space.</span></span> <span data-ttu-id="c65d8-136">Specificare un percorso per il appxbundle e passare a una build di sviluppo, se si desidera</span><span class="sxs-lookup"><span data-stu-id="c65d8-136">Specify a location for the .appxbundle and switch to a development build if you wish</span></span>

![Screenshot delle opzioni di Cook nella configurazione del profilo con Cook by the book e HoloLens evidenziato](images/unreal-insights-img-09.png)

4. <span data-ttu-id="c65d8-138">Impostare la **modalità di distribuzione della compilazione** per la **copia nel dispositivo** per attivare la sezione **Launch** dell'interfaccia utente:</span><span class="sxs-lookup"><span data-stu-id="c65d8-138">Set **How would you like to deploy the build?** to **Copy to device** to activate the **Launch** section of the UI:</span></span>

![Screenshot dell'utilità di avvio del progetto con opzioni di distribuzione con copia nel dispositivo evidenziato](images/unreal-insights-img-10.png)

5. <span data-ttu-id="c65d8-140">Impostare **parametri della riga di comando aggiuntivi** nella sezione **Launch** .</span><span class="sxs-lookup"><span data-stu-id="c65d8-140">Set **Additional Command Line Parameters** in the **Launch** section.</span></span> <span data-ttu-id="c65d8-141">I parametri verranno scritti in un file di ue4commandline.txt, inclusi nel bundle e usati all'avvio.</span><span class="sxs-lookup"><span data-stu-id="c65d8-141">The parameters will be written into a ue4commandline.txt file, packaged into the bundle, and used at launch.</span></span> 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * <span data-ttu-id="c65d8-142">Provare a eseguire queste operazioni per i principianti: **-tracehost = IP_OF_YOUR_PC-trace = log, Bookmark, frame, CPU, GPU, LoadTime, file, NET**</span><span class="sxs-lookup"><span data-stu-id="c65d8-142">Try these for starters: **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame,CPU,GPU,LoadTime,File,Net**</span></span>
    * <span data-ttu-id="c65d8-143">È possibile trovare un elenco completo dei parametri di avvio disponibili nella [documentazione di riferimento di Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).</span><span class="sxs-lookup"><span data-stu-id="c65d8-143">You can find a complete list of available launch parameters in the [Unreal Insights reference documentation](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).</span></span>

> [!NOTE]
> <span data-ttu-id="c65d8-144">"IP_OF_YOUR_PC" è l'indirizzo IP trovato nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="c65d8-144">"IP_OF_YOUR_PC" is the IP address we found in step 1.</span></span> <span data-ttu-id="c65d8-145">Si tratta dell'indirizzo IP del computer che esegue Unreal Insights, non dell'indirizzo IP del HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c65d8-145">This is the IP address of the computer running Unreal Insights, NOT the IP address of the HoloLens.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c65d8-146">Il numero di tracce può essere molto rapido.</span><span class="sxs-lookup"><span data-stu-id="c65d8-146">Traces can get large very quickly.</span></span> <span data-ttu-id="c65d8-147">Abilitare solo i canali necessari per ridurre le dimensioni della traccia.</span><span class="sxs-lookup"><span data-stu-id="c65d8-147">Enable only those channels you need to keep trace size low.</span></span>

![Screenshot delle opzioni di configurazione di avvio](images/unreal-insights-img-11.png)

6. <span data-ttu-id="c65d8-149">Avviare informazioni dettagliate non reali prima dell'avvio dell'app. in caso contrario, le informazioni dettagliate non saranno in grado di inizializzare in modo appropriato prima dell'app:</span><span class="sxs-lookup"><span data-stu-id="c65d8-149">Launch Unreal Insights BEFORE app launch, otherwise Unreal Insights wont be able to initialize appropriately before the app:</span></span>
    * <span data-ttu-id="c65d8-150">Il file eseguibile di Unreal Insights viene archiviato nella cartella del motore dei binari, in genere come segue: "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"</span><span class="sxs-lookup"><span data-stu-id="c65d8-150">The Unreal Insights executable is stored in the binaries engine folder, usually as follows: "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"</span></span>

![Screenshot del file eseguibile di Unreal Insights in esecuzione](images/unreal-insights-img-12.png)

6.  <span data-ttu-id="c65d8-152">Selezionare **indietro** per tornare alla radice della finestra di dialogo di **avvio del progetto**</span><span class="sxs-lookup"><span data-stu-id="c65d8-152">Select **Back** to return to the root of the **Project Launcher** dialog</span></span>
7.  <span data-ttu-id="c65d8-153">Nell'editor fare clic su **Launch (avvia** ) nel profilo di avvio personalizzato</span><span class="sxs-lookup"><span data-stu-id="c65d8-153">Back in the editor, Click **Launch** on your custom launch profile</span></span>

![Screenshot dei profili di avvio personalizzati](images/unreal-insights-img-13.png)

8.  <span data-ttu-id="c65d8-155">È possibile osservare il pacchetto del progetto, installarlo nel dispositivo e avviare</span><span class="sxs-lookup"><span data-stu-id="c65d8-155">Watch as your project is packaged up, installed on your device, and launched</span></span>

## <a name="profiling"></a><span data-ttu-id="c65d8-156">Profilatura</span><span class="sxs-lookup"><span data-stu-id="c65d8-156">Profiling</span></span>

<span data-ttu-id="c65d8-157">Per avviare la profilatura, selezionare la connessione in **tempo** reale al dispositivo per avviare la profilatura.</span><span class="sxs-lookup"><span data-stu-id="c65d8-157">Back in Unreal Insights, select the **Live** connection to your device to start profiling</span></span>

<span data-ttu-id="c65d8-158">Il profilo personalizzato è condiviso tra i progetti.</span><span class="sxs-lookup"><span data-stu-id="c65d8-158">The custom profile is shared between projects.</span></span> <span data-ttu-id="c65d8-159">Da questo punto in poi, è possibile usare il profilo personalizzato creato anziché eseguire questa operazione ogni volta.</span><span class="sxs-lookup"><span data-stu-id="c65d8-159">From here on out, you can use the custom profile you created instead of having to do this every time.</span></span> <span data-ttu-id="c65d8-160">È necessario ricreare la connessione al dispositivo ogni volta che si avvia Unreal con i passaggi da 3 a 6 nella [sezione relativa all'installazione](#setup).</span><span class="sxs-lookup"><span data-stu-id="c65d8-160">You only need to recreate the connection to the device every time you start Unreal with steps 3 to 6 in the [setup section](#setup).</span></span>

## <a name="see-also"></a><span data-ttu-id="c65d8-161">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c65d8-161">See also</span></span>
* [<span data-ttu-id="c65d8-162">Documentazione di Unreal Insights</span><span class="sxs-lookup"><span data-stu-id="c65d8-162">Unreal Insights documentation</span></span>](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

