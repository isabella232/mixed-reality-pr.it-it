---
title: 6. Creazione di pacchetti e distribuzione nel dispositivo o nell'emulatore
description: Parte 6 di 6 in una serie di esercitazioni per la creazione di un'app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 7f6f501a5e2cde9fdb6aa3ba1aa973a4ab697fd8
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010547"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="7d8fc-104">6. Creazione di pacchetti e distribuzione nel dispositivo o nell'emulatore</span><span class="sxs-lookup"><span data-stu-id="7d8fc-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="7d8fc-105">Nell'esercitazione precedente hai aggiunto un semplice pulsante che riporta il pezzo degli scacchi nella posizione originale.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-105">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="7d8fc-106">In questa sezione finale preparerai l'app per l'esecuzione su HoloLens 2 o su un emulatore.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-106">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="7d8fc-107">Se usi HoloLens 2, puoi trasmettere il flusso dal computer oppure creare un pacchetto dell'app in modo che venga eseguita direttamente sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-107">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="7d8fc-108">Se non hai un dispositivo, creerai un pacchetto dell'app per l'esecuzione nell'emulatore.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-108">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="7d8fc-109">Alla fine di questa sezione avrai un'app in realtà mista distribuita pronta per l'uso, completa di interazioni e interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-109">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="7d8fc-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="7d8fc-110">Objectives</span></span>

* <span data-ttu-id="7d8fc-111">[Solo dispositivo] Streaming a HoloLens 2 con app remota olografica</span><span class="sxs-lookup"><span data-stu-id="7d8fc-111">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="7d8fc-112">Creazione del pacchetto e distribuzione dell'app in un dispositivo HoloLens 2 o in un emulatore</span><span class="sxs-lookup"><span data-stu-id="7d8fc-112">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="7d8fc-113">[Solo dispositivo] Streaming</span><span class="sxs-lookup"><span data-stu-id="7d8fc-113">[Device Only] Streaming</span></span>

<span data-ttu-id="7d8fc-114">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) indica lo streaming di dati da un PC o dispositivo UWP autonomo a HoloLens 2, non il cambio di canale.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-114">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="7d8fc-115">Un'app host remota riceve un flusso di dati di input da HoloLens, esegue il rendering del contenuto in una visualizzazione Immersive virtuale e ritrasmette i frame di contenuto a HoloLens tramite Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-115">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="7d8fc-116">Lo streaming consente di aggiungere visualizzazioni Immersive remote al software per PC desktop esistente e di accedere a più risorse di sistema.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-116">Streaming lets you add remote immersive views into existing desktop PC software and has access to more system resources.</span></span>

<span data-ttu-id="7d8fc-117">Se usi questa strategia per l'app di scacchi, dovrai eseguire alcuni passaggi:</span><span class="sxs-lookup"><span data-stu-id="7d8fc-117">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="7d8fc-118">Installa **Holographic Remoting Player** dal Microsoft Store in HoloLens 2 ed esegui l'app.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-118">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span> <span data-ttu-id="7d8fc-119">Prendere nota dell'indirizzo IP visualizzato nell'app.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-119">Note your IP address displayed in the app.</span></span>

2.  <span data-ttu-id="7d8fc-120">Nell'editor di Unity passare a **Edit > Project Settings** (Modifica > Impostazioni progetto) e selezionare **Enable Remoting** (Abilita comunicazione remota) nella sezione **Holographic Remoting**.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-120">Back in the Unreal editor, go to **Edit > Project Settings** and check **Enable Remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="7d8fc-121">Riavviare l'editor e immettere l'indirizzo IP del dispositivo (come visualizzato nell'app del lettore Holographic Remoting) e quindi fare clic su **Connect** (Connetti).</span><span class="sxs-lookup"><span data-stu-id="7d8fc-121">Restart the editor, then enter your device's IP address (as displayed in the Holographic Remoting Player app), then click **Connect**.</span></span>

<span data-ttu-id="7d8fc-122">Dopo esserti connesso, fai clic sulla freccia a discesa a destra del pulsante **Play** (Riproduci) e seleziona **VR Preview** (Anteprima VR).</span><span class="sxs-lookup"><span data-stu-id="7d8fc-122">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="7d8fc-123">L'app verrà eseguita nella finestra di anteprima VR, che viene trasmessa al visore VR HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-123">The app will run in the VR Preview window, which is streamed to the HoloLens headset.</span></span>

## <a name="packaging-and-deploying-the-app-via-device-portal"></a><span data-ttu-id="7d8fc-124">Creazione del pacchetto e distribuzione dell'app tramite il portale del dispositivo</span><span class="sxs-lookup"><span data-stu-id="7d8fc-124">Packaging and deploying the app via device portal</span></span>

>[!NOTE]
><span data-ttu-id="7d8fc-125">Se è la prima volta esegui il packaging di un'app Unreal per HoloLens, dovrai scaricare i file di supporto dall'utilità di avvio Epic.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-125">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span>
>- <span data-ttu-id="7d8fc-126">Passare a **Preferenze editor > Generale > Codice sorgente > Editor codice sorgente** e verificare che Visual Studio 2019 sia selezionato.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-126">Go to **Editor Preferences > General > Source Code > Source Code Editor** and check that Visual Studio 2019 is selected.</span></span>
>- <span data-ttu-id="7d8fc-127">Passa alla scheda **Library** (Libreria) nel launcher di Epic Games, seleziona la freccia a discesa accanto a **Launch** (Avvia) e fai clic su **Options** (Opzioni).</span><span class="sxs-lookup"><span data-stu-id="7d8fc-127">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span>
>- <span data-ttu-id="7d8fc-128">In **Target Platforms** (Piattaforme di destinazione) seleziona **HoloLens 2** e fai clic su **Apply** (Applica).</span><span class="sxs-lookup"><span data-stu-id="7d8fc-128">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
><span data-ttu-id="7d8fc-129">![Modificare la piattaforma di destinazione nelle impostazioni del progetto](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="7d8fc-129">![Change target platform in project settings](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="7d8fc-130">Passa a **Edit > Project Settings** (Modifica > Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="7d8fc-130">Go to **Edit > Project Settings**.</span></span>
    * <span data-ttu-id="7d8fc-131">Aggiungi un nome progetto in **Project > Description > About > Project Name** (Progetto > Descrizione > Informazioni -> Nome progetto).</span><span class="sxs-lookup"><span data-stu-id="7d8fc-131">Add a project name under **Project > Description > About > Project Name**.</span></span>
    * <span data-ttu-id="7d8fc-132">Aggiungi **CN=NomeSocietà** in **Project > Description > Publisher > Company Distinguished Name** (Progetto > Descrizione > Autore > Nome distinto società).</span><span class="sxs-lookup"><span data-stu-id="7d8fc-132">Add **CN=YourCompanyName** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>
    * <span data-ttu-id="7d8fc-133">Selezionare **Start in VR** (Avvia in VR) in **Project > Description > Settings** (Progetto > Descrizione > Impostazioni).</span><span class="sxs-lookup"><span data-stu-id="7d8fc-133">Select **Start in VR** under **Project > Description > Settings**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d8fc-134">Se lasci vuoto uno di questi campi, viene generato un errore quando tenti di generare un nuovo certificato nel passaggio 3.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-134">Leaving either of these fields blank will result in an error when you try and generate a new certificate in step 3.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d8fc-135">Il nome dell'autore deve essere nel [formato LADPv3 Distinguished Names](https://www.ietf.org/rfc/rfc2253.txt).</span><span class="sxs-lookup"><span data-stu-id="7d8fc-135">The publisher's name must be in [LADPv3 Distinguished Names Format](https://www.ietf.org/rfc/rfc2253.txt).</span></span> <span data-ttu-id="7d8fc-136">Se il nome dell'autore non è valido, viene visualizzato un errore che indica che la chiave di firma non è stata trovata</span><span class="sxs-lookup"><span data-stu-id="7d8fc-136">A malformed publisher's name leads to the "Signing key not found.</span></span> <span data-ttu-id="7d8fc-137">e che non è stato possibile firmare digitalmente l'app</span><span class="sxs-lookup"><span data-stu-id="7d8fc-137">The app could not be digitally signed."</span></span> <span data-ttu-id="7d8fc-138">durante la creazione del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-138">error upon packaging.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d8fc-139">Se non si seleziona l'opzione "Start in VR" (Avvia in VR), l'applicazione tenterà l'avvio in una finestra.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-139">Not selecting "Start in VR" will lead your application trying to start in a slate</span></span>

![Impostazioni del progetto - Descrizione](images/unreal-uxt/6-cn-new.PNG)

2.  <span data-ttu-id="7d8fc-141">Abilita **Build for HoloLens Emulation** (Build per emulazione HoloLens) e/o **Build for HoloLens Device** (Build per dispositivo HoloLens) in **Platforms > HoloLens** (Piattaforme > HoloLens).</span><span class="sxs-lookup"><span data-stu-id="7d8fc-141">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="7d8fc-142">Fai clic su **Generate new** (Genera nuovo) nella sezione **Packaging** (Pacchetto), accanto a **Signing Certificate** (Certificato di firma).</span><span class="sxs-lookup"><span data-stu-id="7d8fc-142">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d8fc-143">Se usi un certificato già generato, il nome dell'autore del certificato deve corrispondere al nome dell'autore dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-143">If you're using an already generated certificate, then the certificate's publisher name must be the same as the application's publisher name.</span></span> <span data-ttu-id="7d8fc-144">In caso contrario, viene visualizzato un errore che indica che la chiave di firma non è stata trovata</span><span class="sxs-lookup"><span data-stu-id="7d8fc-144">Otherwise it leads to the "Signing key not found.</span></span> <span data-ttu-id="7d8fc-145">e che non è stato possibile firmare digitalmente l'app</span><span class="sxs-lookup"><span data-stu-id="7d8fc-145">The app could not be digitally signed."</span></span> <span data-ttu-id="7d8fc-146">errore.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-146">error.</span></span>

![Impostazioni di progetto - Piattaforme - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. <span data-ttu-id="7d8fc-148">Fai clic su **None** (Nessuno) a scopo di test quando ti viene chiesto di creare una password di chiave privata.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-148">Click **None** for testing purposes when you're prompted to create a Private Key Password.</span></span>

![Generazione di un nuovo certificato](images/unreal-uxt/6-private-key-testing.png)

5. <span data-ttu-id="7d8fc-150">Passa a **File > Package Project** (File > Crea pacchetto progetto) e seleziona **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-150">Go to **File > Package Project** and select **HoloLens**.</span></span>
    * <span data-ttu-id="7d8fc-151">Crea una nuova cartella in cui salvare il pacchetto e fare clic su **Select Folder** (Seleziona cartella).</span><span class="sxs-lookup"><span data-stu-id="7d8fc-151">Create a new folder to save your package in and click **Select Folder**.</span></span>

6.  <span data-ttu-id="7d8fc-152">Dopo avere creato il pacchetto dell'app, apri il [Portale di dispositivi di Windows](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal), passa a **Views > Apps** (Viste > App) e trova la sezione **Deploy apps** (Distribuzione app).</span><span class="sxs-lookup"><span data-stu-id="7d8fc-152">Open the [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

7.  <span data-ttu-id="7d8fc-153">Fai clic su **Sfoglia** (Sfoglia), passa al file **ChessApp.appxbundle** e fai clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-153">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span>

    * <span data-ttu-id="7d8fc-154">Se si installa l'app sul dispositivo per la prima volta, selezionare la casella accanto a **Allow me to select framework packages** (Consenti di selezionare i pacchetti del framework).</span><span class="sxs-lookup"><span data-stu-id="7d8fc-154">Check the box next to **Allow me to select framework packages** if you're installing the app on your device for the first time.</span></span>
    * <span data-ttu-id="7d8fc-155">Nella finestra di dialogo successiva includere i file **VCLibs** e **appx**, **arm64** per il dispositivo e **x64** per l'emulatore.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-155">In the next dialogue, include the appropriate **VCLibs** and **appx** files, **arm64** for device and **x64** for emulator.</span></span> <span data-ttu-id="7d8fc-156">Sono disponibili in **HoloLens** all'interno della cartella in cui è stato salvato il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-156">You can find the files under **HoloLens** inside the folder where you saved your package.</span></span>

8.  <span data-ttu-id="7d8fc-157">Fai clic su **Install** (Installa).</span><span class="sxs-lookup"><span data-stu-id="7d8fc-157">Click **Install**</span></span>
    * <span data-ttu-id="7d8fc-158">È ora possibile passare a **All Apps** (Tutte le app) e toccare l'app installata per eseguirla. In alternativa, avviare l'app direttamente dal **Portale di dispositivi di Windows**.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-158">You can now go to **All Apps** and tap the newly installed app to run it, or start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="7d8fc-159">A questo punto,</span><span class="sxs-lookup"><span data-stu-id="7d8fc-159">Congratulations!</span></span> <span data-ttu-id="7d8fc-160">la tua applicazione in realtà mista HoloLens è completa e pronta per l'uso.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-160">Your HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="7d8fc-161">Sono, tuttavia, necessarie altre operazioni.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-161">However, you're not at the end of the road.</span></span> <span data-ttu-id="7d8fc-162">MRTK include molte funzionalità autonome che puoi aggiungere ai progetti, ad esempio il mapping spaziale, lo sguardo e l'input vocale e persino codici a matrice.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-162">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="7d8fc-163">Per altre informazioni su queste funzionalità, consulta la [Panoramica sullo sviluppo con Unreal](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span><span class="sxs-lookup"><span data-stu-id="7d8fc-163">More information on these features can be found in the [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="7d8fc-164">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="7d8fc-164">Next Development Checkpoint</span></span>

<span data-ttu-id="7d8fc-165">Se si segue il percorso delineato per lo sviluppo con Unreal, tenere presente che si stanno esplorando i blocchi predefiniti fondamentali di MRTK.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-165">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="7d8fc-166">Da qui, è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="7d8fc-166">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7d8fc-167">Input sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="7d8fc-167">Gaze input</span></span>](../unreal-gaze-input.md)

<span data-ttu-id="7d8fc-168">In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="7d8fc-168">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7d8fc-169">Fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="7d8fc-169">HoloLens camera</span></span>](../unreal-hololens-camera.md)

<span data-ttu-id="7d8fc-170">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](../unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="7d8fc-170">You can always go back to the [Unreal development checkpoints](../unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>
