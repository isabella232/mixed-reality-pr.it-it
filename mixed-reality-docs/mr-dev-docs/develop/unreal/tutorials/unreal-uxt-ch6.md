---
title: 6. Creazione di pacchetti e distribuzione nel dispositivo o nell'emulatore
description: Parte 6 di 6 in una serie di esercitazioni per la creazione di un'app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 7b706cf2a8685954ed916c825c3617ade190f1e0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "98583650"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="9ce91-104">6. Creazione di pacchetti e distribuzione nel dispositivo o nell'emulatore</span><span class="sxs-lookup"><span data-stu-id="9ce91-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="9ce91-105">Nell'esercitazione precedente hai aggiunto un semplice pulsante che riporta il pezzo degli scacchi nella posizione originale.</span><span class="sxs-lookup"><span data-stu-id="9ce91-105">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="9ce91-106">In questa sezione finale preparerai l'app per l'esecuzione su HoloLens 2 o su un emulatore.</span><span class="sxs-lookup"><span data-stu-id="9ce91-106">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="9ce91-107">Se usi HoloLens 2, puoi trasmettere il flusso dal computer oppure creare un pacchetto dell'app in modo che venga eseguita direttamente sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9ce91-107">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="9ce91-108">Se non hai un dispositivo, creerai un pacchetto dell'app per l'esecuzione nell'emulatore.</span><span class="sxs-lookup"><span data-stu-id="9ce91-108">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="9ce91-109">Alla fine di questa sezione avrai un'app in realtà mista distribuita pronta per l'uso, completa di interazioni e interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="9ce91-109">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="9ce91-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="9ce91-110">Objectives</span></span>

* <span data-ttu-id="9ce91-111">[Solo dispositivo] Streaming a HoloLens 2 con app remota olografica</span><span class="sxs-lookup"><span data-stu-id="9ce91-111">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="9ce91-112">Creazione del pacchetto e distribuzione dell'app in un dispositivo HoloLens 2 o in un emulatore</span><span class="sxs-lookup"><span data-stu-id="9ce91-112">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="9ce91-113">[Solo dispositivo] Streaming</span><span class="sxs-lookup"><span data-stu-id="9ce91-113">[Device Only] Streaming</span></span>

<span data-ttu-id="9ce91-114">[Holographic Remoting](/windows/mixed-reality/add-holographic-remoting) indica lo streaming di dati da un PC o dispositivo UWP autonomo a HoloLens 2, non il cambio di canale.</span><span class="sxs-lookup"><span data-stu-id="9ce91-114">[Holographic Remoting](/windows/mixed-reality/add-holographic-remoting) means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="9ce91-115">Un'app host remota riceve un flusso di dati di input da HoloLens, esegue il rendering del contenuto in una visualizzazione Immersive virtuale e ritrasmette i frame di contenuto a HoloLens tramite Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="9ce91-115">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="9ce91-116">Lo streaming consente di aggiungere visualizzazioni Immersive remote al software per PC desktop esistente e di accedere a più risorse di sistema.</span><span class="sxs-lookup"><span data-stu-id="9ce91-116">Streaming lets you add remote immersive views into existing desktop PC software and has access to more system resources.</span></span>

<span data-ttu-id="9ce91-117">Se usi questa strategia per l'app di scacchi, dovrai eseguire alcuni passaggi:</span><span class="sxs-lookup"><span data-stu-id="9ce91-117">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="9ce91-118">Installa **Holographic Remoting Player** dal Microsoft Store in HoloLens 2 ed esegui l'app.</span><span class="sxs-lookup"><span data-stu-id="9ce91-118">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span> <span data-ttu-id="9ce91-119">Prendere nota dell'indirizzo IP visualizzato nell'app.</span><span class="sxs-lookup"><span data-stu-id="9ce91-119">Note your IP address displayed in the app.</span></span>
    * <span data-ttu-id="9ce91-120">Passare a **Edit > Project Settings** (Modifica > Impostazioni progetto) e verificare che l'opzione **Default RHI** (RHI predefinito) di Windows sia impostata su **Default** (Predefinito) o **D3D11**:</span><span class="sxs-lookup"><span data-stu-id="9ce91-120">Go to **Edit > Project Settings** and sure the Windows **Default RHI** is set to **Default** or **D3D11**:</span></span>

![RHI predefinito](../images/unreal/performance-recommendations-img-09.png)

2.  <span data-ttu-id="9ce91-122">Nell'editor di Unity passare a **Edit > Project Settings** (Modifica > Impostazioni progetto) e selezionare **Enable Remoting** (Abilita comunicazione remota) nella sezione **Holographic Remoting**.</span><span class="sxs-lookup"><span data-stu-id="9ce91-122">Back in the Unreal editor, go to **Edit > Project Settings** and check **Enable Remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="9ce91-123">Riavviare l'editor e immettere l'indirizzo IP del dispositivo (come visualizzato nell'app del lettore Holographic Remoting) e quindi fare clic su **Connect** (Connetti).</span><span class="sxs-lookup"><span data-stu-id="9ce91-123">Restart the editor, then enter your device's IP address (as displayed in the Holographic Remoting Player app), then click **Connect**.</span></span>

<span data-ttu-id="9ce91-124">Dopo esserti connesso, fai clic sulla freccia a discesa a destra del pulsante **Play** (Riproduci) e seleziona **VR Preview** (Anteprima VR).</span><span class="sxs-lookup"><span data-stu-id="9ce91-124">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="9ce91-125">L'app verrà eseguita nella finestra di anteprima VR, che viene trasmessa al visore VR HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9ce91-125">The app will run in the VR Preview window, which is streamed to the HoloLens headset.</span></span>

## <a name="packaging-and-deploying-the-app-via-device-portal"></a><span data-ttu-id="9ce91-126">Creazione del pacchetto e distribuzione dell'app tramite il portale del dispositivo</span><span class="sxs-lookup"><span data-stu-id="9ce91-126">Packaging and deploying the app via device portal</span></span>

>[!NOTE]
><span data-ttu-id="9ce91-127">Se è la prima volta esegui il packaging di un'app Unreal per HoloLens, dovrai scaricare i file di supporto dall'utilità di avvio Epic.</span><span class="sxs-lookup"><span data-stu-id="9ce91-127">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span>
>- <span data-ttu-id="9ce91-128">Passare a **Preferenze editor > Generale > Codice sorgente > Editor codice sorgente** e verificare che Visual Studio 2019 sia selezionato.</span><span class="sxs-lookup"><span data-stu-id="9ce91-128">Go to **Editor Preferences > General > Source Code > Source Code Editor** and check that Visual Studio 2019 is selected.</span></span>
>- <span data-ttu-id="9ce91-129">Passa alla scheda **Library** (Libreria) nel launcher di Epic Games, seleziona la freccia a discesa accanto a **Launch** (Avvia) e fai clic su **Options** (Opzioni).</span><span class="sxs-lookup"><span data-stu-id="9ce91-129">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span>
>- <span data-ttu-id="9ce91-130">In **Target Platforms** (Piattaforme di destinazione) seleziona **HoloLens 2** e fai clic su **Apply** (Applica).</span><span class="sxs-lookup"><span data-stu-id="9ce91-130">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
><span data-ttu-id="9ce91-131">![Modificare la piattaforma di destinazione nelle impostazioni del progetto](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="9ce91-131">![Change target platform in project settings](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="9ce91-132">Passa a **Edit > Project Settings** (Modifica > Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="9ce91-132">Go to **Edit > Project Settings**.</span></span>
    * <span data-ttu-id="9ce91-133">Aggiungi un nome progetto in **Project > Description > About > Project Name** (Progetto > Descrizione > Informazioni -> Nome progetto).</span><span class="sxs-lookup"><span data-stu-id="9ce91-133">Add a project name under **Project > Description > About > Project Name**.</span></span>
    * <span data-ttu-id="9ce91-134">Aggiungi **CN=NomeSocietà** in **Project > Description > Publisher > Company Distinguished Name** (Progetto > Descrizione > Autore > Nome distinto società).</span><span class="sxs-lookup"><span data-stu-id="9ce91-134">Add **CN=YourCompanyName** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>
    * <span data-ttu-id="9ce91-135">Selezionare **Start in VR** (Avvia in VR) in **Project > Description > Settings** (Progetto > Descrizione > Impostazioni).</span><span class="sxs-lookup"><span data-stu-id="9ce91-135">Select **Start in VR** under **Project > Description > Settings**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ce91-136">Se lasci vuoto uno di questi campi, viene generato un errore quando tenti di generare un nuovo certificato nel passaggio 3.</span><span class="sxs-lookup"><span data-stu-id="9ce91-136">Leaving either of these fields blank will result in an error when you try and generate a new certificate in step 3.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ce91-137">Il nome dell'autore deve essere nel [formato LADPv3 Distinguished Names](https://www.ietf.org/rfc/rfc2253.txt).</span><span class="sxs-lookup"><span data-stu-id="9ce91-137">The publisher's name must be in [LADPv3 Distinguished Names Format](https://www.ietf.org/rfc/rfc2253.txt).</span></span> <span data-ttu-id="9ce91-138">Se il nome dell'autore non è valido, viene visualizzato un errore che indica che la chiave di firma non è stata trovata</span><span class="sxs-lookup"><span data-stu-id="9ce91-138">A malformed publisher's name leads to the "Signing key not found.</span></span> <span data-ttu-id="9ce91-139">e che non è stato possibile firmare digitalmente l'app</span><span class="sxs-lookup"><span data-stu-id="9ce91-139">The app could not be digitally signed."</span></span> <span data-ttu-id="9ce91-140">durante la creazione del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="9ce91-140">error upon packaging.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ce91-141">Se non si seleziona l'opzione "Start in VR" (Avvia in VR), l'applicazione tenterà l'avvio in una finestra.</span><span class="sxs-lookup"><span data-stu-id="9ce91-141">Not selecting "Start in VR" will lead your application trying to start in a slate</span></span>

![Impostazioni del progetto - Descrizione](images/unreal-uxt/6-cn-new.PNG)

2.  <span data-ttu-id="9ce91-143">Abilita **Build for HoloLens Emulation** (Build per emulazione HoloLens) e/o **Build for HoloLens Device** (Build per dispositivo HoloLens) in **Platforms > HoloLens** (Piattaforme > HoloLens).</span><span class="sxs-lookup"><span data-stu-id="9ce91-143">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="9ce91-144">Fai clic su **Generate new** (Genera nuovo) nella sezione **Packaging** (Pacchetto), accanto a **Signing Certificate** (Certificato di firma).</span><span class="sxs-lookup"><span data-stu-id="9ce91-144">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ce91-145">Se usi un certificato già generato, il nome dell'autore del certificato deve corrispondere al nome dell'autore dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="9ce91-145">If you're using an already generated certificate, then the certificate's publisher name must be the same as the application's publisher name.</span></span> <span data-ttu-id="9ce91-146">In caso contrario, viene visualizzato un errore che indica che la chiave di firma non è stata trovata</span><span class="sxs-lookup"><span data-stu-id="9ce91-146">Otherwise it leads to the "Signing key not found.</span></span> <span data-ttu-id="9ce91-147">e che non è stato possibile firmare digitalmente l'app</span><span class="sxs-lookup"><span data-stu-id="9ce91-147">The app could not be digitally signed."</span></span> <span data-ttu-id="9ce91-148">errore.</span><span class="sxs-lookup"><span data-stu-id="9ce91-148">error.</span></span>

![Impostazioni di progetto - Piattaforme - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. <span data-ttu-id="9ce91-150">Fai clic su **None** (Nessuno) a scopo di test quando ti viene chiesto di creare una password di chiave privata.</span><span class="sxs-lookup"><span data-stu-id="9ce91-150">Click **None** for testing purposes when you're prompted to create a Private Key Password.</span></span>

![Generazione di un nuovo certificato](images/unreal-uxt/6-private-key-testing.png)

5. <span data-ttu-id="9ce91-152">Passa a **File > Package Project** (File > Crea pacchetto progetto) e seleziona **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="9ce91-152">Go to **File > Package Project** and select **HoloLens**.</span></span>
    * <span data-ttu-id="9ce91-153">Crea una nuova cartella in cui salvare il pacchetto e fare clic su **Select Folder** (Seleziona cartella).</span><span class="sxs-lookup"><span data-stu-id="9ce91-153">Create a new folder to save your package in and click **Select Folder**.</span></span>

6.  <span data-ttu-id="9ce91-154">Dopo avere creato il pacchetto dell'app, apri il [Portale di dispositivi di Windows](/windows/mixed-reality/using-the-windows-device-portal), passa a **Views > Apps** (Viste > App) e trova la sezione **Deploy apps** (Distribuzione app).</span><span class="sxs-lookup"><span data-stu-id="9ce91-154">Open the [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

7.  <span data-ttu-id="9ce91-155">Fai clic su **Sfoglia** (Sfoglia), passa al file **ChessApp.appxbundle** e fai clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="9ce91-155">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span>

    * <span data-ttu-id="9ce91-156">Se si installa l'app sul dispositivo per la prima volta, selezionare la casella accanto a **Allow me to select framework packages** (Consenti di selezionare i pacchetti del framework).</span><span class="sxs-lookup"><span data-stu-id="9ce91-156">Check the box next to **Allow me to select framework packages** if you're installing the app on your device for the first time.</span></span>
    * <span data-ttu-id="9ce91-157">Nella finestra di dialogo successiva includere i file **VCLibs** e **appx**, **arm64** per il dispositivo e **x64** per l'emulatore.</span><span class="sxs-lookup"><span data-stu-id="9ce91-157">In the next dialogue, include the appropriate **VCLibs** and **appx** files, **arm64** for device and **x64** for emulator.</span></span> <span data-ttu-id="9ce91-158">Sono disponibili in **HoloLens** all'interno della cartella in cui è stato salvato il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="9ce91-158">You can find the files under **HoloLens** inside the folder where you saved your package.</span></span>

8.  <span data-ttu-id="9ce91-159">Fai clic su **Install** (Installa).</span><span class="sxs-lookup"><span data-stu-id="9ce91-159">Click **Install**</span></span>
    * <span data-ttu-id="9ce91-160">È ora possibile passare a **All Apps** (Tutte le app) e toccare l'app installata per eseguirla. In alternativa, avviare l'app direttamente dal **Portale di dispositivi di Windows**.</span><span class="sxs-lookup"><span data-stu-id="9ce91-160">You can now go to **All Apps** and tap the newly installed app to run it, or start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="9ce91-161">A questo punto,</span><span class="sxs-lookup"><span data-stu-id="9ce91-161">Congratulations!</span></span> <span data-ttu-id="9ce91-162">la tua applicazione in realtà mista HoloLens è completa e pronta per l'uso.</span><span class="sxs-lookup"><span data-stu-id="9ce91-162">Your HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="9ce91-163">Sono, tuttavia, necessarie altre operazioni.</span><span class="sxs-lookup"><span data-stu-id="9ce91-163">However, you're not at the end of the road.</span></span> <span data-ttu-id="9ce91-164">MRTK include molte funzionalità autonome che puoi aggiungere ai progetti, ad esempio il mapping spaziale, lo sguardo e l'input vocale e persino codici a matrice.</span><span class="sxs-lookup"><span data-stu-id="9ce91-164">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="9ce91-165">Per altre informazioni su queste funzionalità, consulta la [Panoramica sullo sviluppo con Unreal](/windows/mixed-reality/unreal-development-overview).</span><span class="sxs-lookup"><span data-stu-id="9ce91-165">More information on these features can be found in the [Unreal development overview](/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="9ce91-166">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="9ce91-166">Next Development Checkpoint</span></span>

<span data-ttu-id="9ce91-167">Se si segue il percorso delineato per lo sviluppo con Unreal, tenere presente che si stanno esplorando i blocchi predefiniti fondamentali di MRTK.</span><span class="sxs-lookup"><span data-stu-id="9ce91-167">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="9ce91-168">Da qui, è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="9ce91-168">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9ce91-169">Input sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="9ce91-169">Gaze input</span></span>](../unreal-gaze-input.md)

<span data-ttu-id="9ce91-170">In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="9ce91-170">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9ce91-171">Fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="9ce91-171">HoloLens camera</span></span>](../unreal-hololens-camera.md)

<span data-ttu-id="9ce91-172">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](../unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="9ce91-172">You can always go back to the [Unreal development checkpoints](../unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>