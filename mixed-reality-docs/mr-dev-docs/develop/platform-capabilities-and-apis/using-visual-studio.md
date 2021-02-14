---
title: Uso di Visual Studio per la distribuzione e il debug
description: Informazioni su come compilare, sottoporre a debug e distribuire app per HoloLens e Windows Mixed Reality con Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, realtà mista, debug, distribuzione
ms.openlocfilehash: 2ab89311163a48ee3c14511446a1498ce883a232
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496094"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="46e32-104">Uso di Visual Studio per la distribuzione e il debug</span><span class="sxs-lookup"><span data-stu-id="46e32-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="46e32-105">Indipendentemente dal fatto che venga usato DirectX o Unity per lo sviluppo di un'app di realtà mista, Visual Studio rimane lo strumento ideale per il debug e la distribuzione.</span><span class="sxs-lookup"><span data-stu-id="46e32-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="46e32-106">In questa sezione imparerai a eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="46e32-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="46e32-107">Distribuire applicazioni nel visore VR immersive di HoloLens o Windows Mixed Reality tramite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="46e32-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="46e32-108">Usare l'emulatore HoloLens incorporato in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="46e32-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="46e32-109">Eseguire il debug di app di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="46e32-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="46e32-110">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="46e32-110">Prerequisites</span></span>

1. <span data-ttu-id="46e32-111">Per le istruzioni di installazione, vedi [Installare gli strumenti](../../develop/install-the-tools.md#installation-checklist).</span><span class="sxs-lookup"><span data-stu-id="46e32-111">See [Install the Tools](../../develop/install-the-tools.md#installation-checklist) for installation instructions.</span></span>
2. <span data-ttu-id="46e32-112">Crea un progetto di app di Windows universale in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="46e32-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="46e32-113">Per HoloLens (prima generazione), usa Visual Studio 2017 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="46e32-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="46e32-114">Per HoloLens 2, usare Visual Studio 2019 16.2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="46e32-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="46e32-115">C# e C++ sono supportati.</span><span class="sxs-lookup"><span data-stu-id="46e32-115">C# and C++ are supported.</span></span> <span data-ttu-id="46e32-116">In alternativa, segui le istruzioni per [creare un'app in Unity](../../develop/unity/tutorials/holograms-100.md).</span><span class="sxs-lookup"><span data-stu-id="46e32-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="46e32-117">Abilitazione della modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="46e32-117">Enabling Developer Mode</span></span>

<span data-ttu-id="46e32-118">Per iniziare, abilita **Modalità sviluppatore** sul tuo dispositivo per consentire a Visual Studio di connettersi.</span><span class="sxs-lookup"><span data-stu-id="46e32-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="46e32-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="46e32-119">HoloLens</span></span>

1. <span data-ttu-id="46e32-120">Accendi HoloLens e il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="46e32-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="46e32-121">Usare il [gesto Start](../../design/system-gesture.md) per avviare il menu principale.</span><span class="sxs-lookup"><span data-stu-id="46e32-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="46e32-122">Seleziona il riquadro **Impostazioni** per avviare l'app nell'ambiente in uso.</span><span class="sxs-lookup"><span data-stu-id="46e32-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="46e32-123">Scegli la voce di menu **Aggiorna**.</span><span class="sxs-lookup"><span data-stu-id="46e32-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="46e32-124">Scegli la voce di menu **Per gli sviluppatori**.</span><span class="sxs-lookup"><span data-stu-id="46e32-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="46e32-125">Abilitare **Modalità sviluppatore** per distribuire le app da Visual Studio al dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="46e32-125">Enable **Developer Mode** to deploy apps from Visual Studio to your HoloLens.</span></span>
7. <span data-ttu-id="46e32-126">Facoltativo: scorrere verso il basso e abilitare anche il **Portale di dispositivi**, che consente di connettersi al [Portale di dispositivi di Windows](using-the-windows-device-portal.md) in HoloLens da un Web browser.</span><span class="sxs-lookup"><span data-stu-id="46e32-126">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="46e32-127">PC Windows</span><span class="sxs-lookup"><span data-stu-id="46e32-127">Windows PC</span></span>

<span data-ttu-id="46e32-128">Se si usa un visore VR di Windows Mixed Reality connesso al PC, è necessario abilitare **Modalità sviluppatore** nel PC.</span><span class="sxs-lookup"><span data-stu-id="46e32-128">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="46e32-129">Vai a **Impostazioni**</span><span class="sxs-lookup"><span data-stu-id="46e32-129">Go to **Settings**</span></span>
2. <span data-ttu-id="46e32-130">Seleziona **Aggiornamento e sicurezza**</span><span class="sxs-lookup"><span data-stu-id="46e32-130">Select **Update and Security**</span></span>
3. <span data-ttu-id="46e32-131">Seleziona **Per gli sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="46e32-131">Select **For developers**</span></span>
4. <span data-ttu-id="46e32-132">Abilitare **Modalità sviluppatore**, leggere la dichiarazione di non responsabilità relativa all'impostazione scelta e quindi selezionare Sì per accettare la modifica.</span><span class="sxs-lookup"><span data-stu-id="46e32-132">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-a-hololens-app-over-wi-fi"></a><span data-ttu-id="46e32-133">Distribuzione di un'app HoloLens tramite Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="46e32-133">Deploying a HoloLens app over Wi-Fi</span></span> 

<span data-ttu-id="46e32-134">Configurare il progetto di Visual Studio con le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="46e32-134">Configure your Visual Studio project with the following properties:</span></span>

1. <span data-ttu-id="46e32-135">Selezionare le opzioni di compilazione delle app</span><span class="sxs-lookup"><span data-stu-id="46e32-135">Select your apps compilation options</span></span>
    * <span data-ttu-id="46e32-136">Per i progetti Unity, scegliere **versione** o **Master**</span><span class="sxs-lookup"><span data-stu-id="46e32-136">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="46e32-137">Per tutti gli altri progetti, scegliere **versione**</span><span class="sxs-lookup"><span data-stu-id="46e32-137">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="46e32-138">È possibile trovare definizioni complete per ogni opzione di compilazione nell' [esportazione e nella compilazione di soluzioni di Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="46e32-138">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="46e32-139">Selezionare la configurazione della build in base al dispositivo</span><span class="sxs-lookup"><span data-stu-id="46e32-139">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="46e32-140">Seleziona **Computer remoto** nel menu a discesa delle destinazioni di distribuzione</span><span class="sxs-lookup"><span data-stu-id="46e32-140">Select **Remote Machine** in the deployment target drop-down menu</span></span>

![Destinazione di distribuzione computer remoto in Visual Studio](images/remotemachinesetting_arm64.png)

<span data-ttu-id="46e32-142">Successivamente, è necessario impostare la connessione remota.</span><span class="sxs-lookup"><span data-stu-id="46e32-142">Next, you need to set your remote connection.</span></span> <span data-ttu-id="46e32-143">Per i progetti C++ e JavaScript, vai a **Progetto > Proprietà > Proprietà di configurazione > Debug**.</span><span class="sxs-lookup"><span data-stu-id="46e32-143">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="46e32-144">Se si sta lavorando in un progetto C#, viene visualizzata automaticamente una finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="46e32-144">If you're working in a C# project, a dialog should automatically appear.</span></span>

> [!NOTE]
> <span data-ttu-id="46e32-145">Se la finestra di dialogo connessione remota non viene visualizzata nel progetto C#, è possibile aprirla manualmente da **proprietà > debug**.</span><span class="sxs-lookup"><span data-stu-id="46e32-145">If the remote connection dialog doesn't appear in your C# project, you can open it manually from **Properties > Debug**.</span></span>

1. <span data-ttu-id="46e32-146">Immetti l'indirizzo IP del tuo dispositivo nel campo **Indirizzo** o **Nome computer**.</span><span class="sxs-lookup"><span data-stu-id="46e32-146">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> 
    * <span data-ttu-id="46e32-147">È possibile trovare l'indirizzo IP nella HoloLens in **impostazioni > rete & Internet > opzioni avanzate**</span><span class="sxs-lookup"><span data-stu-id="46e32-147">You can find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**</span></span>
    * <span data-ttu-id="46e32-148">Si consiglia sempre di immettere manualmente l'indirizzo IP anziché a seconda della funzionalità di rilevamento automatico</span><span class="sxs-lookup"><span data-stu-id="46e32-148">We always recommend manually entering your IP address rather than depending on the Auto Detected feature</span></span>

2. <span data-ttu-id="46e32-149">Impostare la **modalità di autenticazione** su **universale (protocollo non crittografato)**</span><span class="sxs-lookup"><span data-stu-id="46e32-149">Set the **Authentication Mode** to **Universal (Unencrypted protocol)**</span></span>

  ![Finestra di dialogo connessione remota in Visual Studio](images/remotedeploy.png)

3. <span data-ttu-id="46e32-151">Crea, Distribuisci ed Esegui il debug dell'app in base alle tue esigenze</span><span class="sxs-lookup"><span data-stu-id="46e32-151">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="46e32-152">Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug</span><span class="sxs-lookup"><span data-stu-id="46e32-152">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="46e32-153">Selezionare **compila > Distribuisci** per compilare e distribuire senza debug</span><span class="sxs-lookup"><span data-stu-id="46e32-153">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Avvia senza eseguire debug in Visual Studio](images/deploywithdebugging.png)

4. <span data-ttu-id="46e32-155">La prima volta che viene distribuita un'app in HoloLens dal PC, verrà chiesto di specificare un PIN.</span><span class="sxs-lookup"><span data-stu-id="46e32-155">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="46e32-156">Segui le istruzioni riportate di seguito in **Associazione del dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="46e32-156">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-a-hololens-app-over-usb"></a><span data-ttu-id="46e32-157">Distribuzione di un'app HoloLens su USB</span><span class="sxs-lookup"><span data-stu-id="46e32-157">Deploying a HoloLens app over USB</span></span> 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="46e32-158">Selezionare le opzioni di compilazione delle app</span><span class="sxs-lookup"><span data-stu-id="46e32-158">Select your apps compilation options</span></span>
    * <span data-ttu-id="46e32-159">Per i progetti Unity, scegliere **versione** o **Master**</span><span class="sxs-lookup"><span data-stu-id="46e32-159">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="46e32-160">Per tutti gli altri progetti, scegliere **versione**</span><span class="sxs-lookup"><span data-stu-id="46e32-160">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="46e32-161">È possibile trovare definizioni complete per ogni opzione di compilazione nell' [esportazione e nella compilazione di soluzioni di Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="46e32-161">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="46e32-162">Selezionare la configurazione della build in base al dispositivo</span><span class="sxs-lookup"><span data-stu-id="46e32-162">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="46e32-163">Seleziona **Dispositivo** nel menu a discesa delle destinazioni di distribuzione</span><span class="sxs-lookup"><span data-stu-id="46e32-163">Select **Device** in the deployment target drop-down menu</span></span>

![Distribuzione dispositivi in Visual Studio](images/buildsettingsusbdeploy_arm64.png)

4. <span data-ttu-id="46e32-165">Crea, Distribuisci ed Esegui il debug dell'app in base alle tue esigenze</span><span class="sxs-lookup"><span data-stu-id="46e32-165">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="46e32-166">Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug</span><span class="sxs-lookup"><span data-stu-id="46e32-166">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="46e32-167">Selezionare **compila > Distribuisci** per compilare e distribuire senza debug</span><span class="sxs-lookup"><span data-stu-id="46e32-167">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Avvia senza eseguire debug in Visual Studio](images/deploywithdebugging.png)</br>

5. <span data-ttu-id="46e32-169">La prima volta che viene distribuita un'app in HoloLens dal PC, verrà chiesto di specificare un PIN.</span><span class="sxs-lookup"><span data-stu-id="46e32-169">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="46e32-170">Segui le istruzioni riportate di seguito in **Associazione del dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="46e32-170">Follow the **Pairing your device** instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="46e32-171">Se si osserva un tempo di ritardo notevole con la distribuzione delle app su USB, è consigliabile usare le [istruzioni del computer remoto](#deploying-a-hololens-app-over-wi-fi) nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="46e32-171">If you're seeing considerable lag time with your apps deployment over USB, we recommend using the [remote machine instructions](#deploying-a-hololens-app-over-wi-fi) in the previous section.</span></span>

## <a name="deploying-an-app-to-the-hololens-emulator"></a><span data-ttu-id="46e32-172">Distribuzione di un'app nell'emulatore di HoloLens</span><span class="sxs-lookup"><span data-stu-id="46e32-172">Deploying an app to the HoloLens Emulator</span></span>

1. <span data-ttu-id="46e32-173">Assicurarsi **[di aver installato l'emulatore HoloLens 2 o HoloLens (1st Gen)](../install-the-tools.md#installation-checklist)**</span><span class="sxs-lookup"><span data-stu-id="46e32-173">Make sure you've **[installed either the HoloLens 2 or HoloLens (1st gen) Emulator](../install-the-tools.md#installation-checklist)**</span></span>
2. <span data-ttu-id="46e32-174">Selezionare la configurazione della build e l'emulatore in base al dispositivo</span><span class="sxs-lookup"><span data-stu-id="46e32-174">Select your build configuration and emulator based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="46e32-175">Crea, Distribuisci ed Esegui il debug dell'app in base alle tue esigenze</span><span class="sxs-lookup"><span data-stu-id="46e32-175">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="46e32-176">Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug</span><span class="sxs-lookup"><span data-stu-id="46e32-176">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="46e32-177">Selezionare **compila > Distribuisci** per compilare e distribuire senza debuggingg</span><span class="sxs-lookup"><span data-stu-id="46e32-177">Select **Build > Deploy** to build and deploy without debuggingg</span></span>

![Avvia senza eseguire debug in Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a><span data-ttu-id="46e32-179">Distribuzione di un'app VR nel PC locale</span><span class="sxs-lookup"><span data-stu-id="46e32-179">Deploying a VR app to your Local PC</span></span> 

<span data-ttu-id="46e32-180">Per usare un visore VR immersive di Windows Mixed Reality che si connette al PC o al [simulatore di realtà mista](using-the-windows-mixed-reality-simulator.md):</span><span class="sxs-lookup"><span data-stu-id="46e32-180">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="46e32-181">Seleziona una configurazione di build **x86** o **x64** per l'app</span><span class="sxs-lookup"><span data-stu-id="46e32-181">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="46e32-182">Seleziona **Computer locale** nel menu a discesa delle destinazioni di distribuzione</span><span class="sxs-lookup"><span data-stu-id="46e32-182">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="46e32-183">Crea, Distribuisci ed Esegui il debug dell'app in base alle tue esigenze</span><span class="sxs-lookup"><span data-stu-id="46e32-183">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="46e32-184">Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug</span><span class="sxs-lookup"><span data-stu-id="46e32-184">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="46e32-185">Selezionare **compila > Distribuisci** per compilare e distribuire senza debug</span><span class="sxs-lookup"><span data-stu-id="46e32-185">Select **Build > Deploy** to build and deploy without debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="46e32-186">Associazione del dispositivo</span><span class="sxs-lookup"><span data-stu-id="46e32-186">Pairing your device</span></span>

<span data-ttu-id="46e32-187">La prima volta che viene distribuita un'app da Visual Studio al dispositivo HoloLens, verrà chiesto di specificare un PIN.</span><span class="sxs-lookup"><span data-stu-id="46e32-187">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="46e32-188">In HoloLens generare un PIN avviando l'app Settings, passare a **Update > For Developers** (Aggiorna > Per gli sviluppatori) e toccare **Pair** (Associa).</span><span class="sxs-lookup"><span data-stu-id="46e32-188">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="46e32-189">Quando il PIN viene visualizzato in HoloLens, digitarlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="46e32-189">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="46e32-190">Al termine dell'associazione, tocca **Fine** su HoloLens per chiudere la finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="46e32-190">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="46e32-191">Il PC è ora associato a HoloLens ed è possibile distribuire le app automaticamente.</span><span class="sxs-lookup"><span data-stu-id="46e32-191">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="46e32-192">Ripetere questi passaggi per tutti i PC usati per distribuire app in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="46e32-192">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="46e32-193">Per dissociare HoloLens da tutti i computer associati:</span><span class="sxs-lookup"><span data-stu-id="46e32-193">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="46e32-194">Avviare l'app **Settings**, passare a **Update > For Developers** (Aggiorna > Per sviluppatori) e toccare **Clear** (Cancella).</span><span class="sxs-lookup"><span data-stu-id="46e32-194">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="46e32-195">Debugger grafica per HoloLens (prima generazione)</span><span class="sxs-lookup"><span data-stu-id="46e32-195">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="46e32-196">Gli strumenti di Diagnostica della grafica di Visual Studio sono utili per la scrittura e l'ottimizzazione di un'app olografica.</span><span class="sxs-lookup"><span data-stu-id="46e32-196">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="46e32-197">Per informazioni dettagliate, vedi [Diagnostica della grafica di Visual Studio su MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics).</span><span class="sxs-lookup"><span data-stu-id="46e32-197">See [Visual Studio Graphics Diagnostics on MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) for full details.</span></span>

<span data-ttu-id="46e32-198">**Per avviare Debugger grafica**</span><span class="sxs-lookup"><span data-stu-id="46e32-198">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="46e32-199">Segui le istruzioni riportate sopra per specificare come destinazione un dispositivo o un emulatore</span><span class="sxs-lookup"><span data-stu-id="46e32-199">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="46e32-200">Vai a **Debug > Grafica > Avvia diagnostica**</span><span class="sxs-lookup"><span data-stu-id="46e32-200">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="46e32-201">La prima volta che viene avviata la diagnostica con un dispositivo HoloLens, è possibile che venga restituito un errore di accesso negato.</span><span class="sxs-lookup"><span data-stu-id="46e32-201">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="46e32-202">Riavviare il dispositivo HoloLens per rendere effettive le autorizzazioni aggiornate e riprovare.</span><span class="sxs-lookup"><span data-stu-id="46e32-202">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="46e32-203">Profilatura</span><span class="sxs-lookup"><span data-stu-id="46e32-203">Profiling</span></span>

<span data-ttu-id="46e32-204">Gli strumenti di profilatura di Visual Studio consentono di analizzare le prestazioni e l'uso delle risorse dell'app.</span><span class="sxs-lookup"><span data-stu-id="46e32-204">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="46e32-205">Sono inclusi strumenti per ottimizzare l'uso di CPU, memoria, grafica e rete.</span><span class="sxs-lookup"><span data-stu-id="46e32-205">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="46e32-206">Per i dettagli completi, vedi [Eseguire strumenti di diagnostica senza debug in MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools).</span><span class="sxs-lookup"><span data-stu-id="46e32-206">See [Run diagnostic tools without debugging on MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) for full details.</span></span>

<span data-ttu-id="46e32-207">**Per avviare gli strumenti di profilatura con HoloLens**</span><span class="sxs-lookup"><span data-stu-id="46e32-207">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="46e32-208">Segui le istruzioni riportate sopra per specificare come destinazione un dispositivo o un emulatore</span><span class="sxs-lookup"><span data-stu-id="46e32-208">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="46e32-209">Vai a **Debug > Avvia strumenti di diagnostica senza debug**</span><span class="sxs-lookup"><span data-stu-id="46e32-209">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="46e32-210">Seleziona gli strumenti che vuoi usare</span><span class="sxs-lookup"><span data-stu-id="46e32-210">Select the tools you want to use</span></span>
4. <span data-ttu-id="46e32-211">Selezionare **Avvia**.</span><span class="sxs-lookup"><span data-stu-id="46e32-211">Select **Start**</span></span>
5. <span data-ttu-id="46e32-212">La prima volta che viene avviata la diagnostica senza debug con un dispositivo HoloLens, è possibile che venga restituito un errore di accesso negato.</span><span class="sxs-lookup"><span data-stu-id="46e32-212">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="46e32-213">Riavviare il dispositivo HoloLens per rendere effettive le autorizzazioni aggiornate e riprovare.</span><span class="sxs-lookup"><span data-stu-id="46e32-213">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="46e32-214">Debug di un'app installata o in esecuzione</span><span class="sxs-lookup"><span data-stu-id="46e32-214">Debugging an installed or running app</span></span>

<span data-ttu-id="46e32-215">È possibile usare Visual Studio per eseguire il debug di un'app di Windows universale installata senza distribuzione da un progetto di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="46e32-215">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="46e32-216">Questa opzione è utile se si vuole eseguire il debug di un pacchetto dell'app installato o di un'app già in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="46e32-216">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="46e32-217">Vai a **Debug -> Altre destinazioni debug -> Debug del pacchetto dell'app installato**</span><span class="sxs-lookup"><span data-stu-id="46e32-217">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="46e32-218">Seleziona la destinazione **Computer remoto** per HoloLens o **Computer locale** per i visori VR immersive.</span><span class="sxs-lookup"><span data-stu-id="46e32-218">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="46e32-219">Immetti l'**indirizzo IP** del dispositivo</span><span class="sxs-lookup"><span data-stu-id="46e32-219">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="46e32-220">Scegli la modalità di autenticazione **Universale**</span><span class="sxs-lookup"><span data-stu-id="46e32-220">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="46e32-221">La finestra mostra le app in esecuzione e inattive.</span><span class="sxs-lookup"><span data-stu-id="46e32-221">The window shows both running and inactive apps.</span></span> <span data-ttu-id="46e32-222">Seleziona quella di cui vuoi eseguire il debug.</span><span class="sxs-lookup"><span data-stu-id="46e32-222">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="46e32-223">Scegli il tipo di codice di cui eseguire il debug (gestito, nativo, misto)</span><span class="sxs-lookup"><span data-stu-id="46e32-223">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="46e32-224">Selezionare **Associa** o **Avvia**.</span><span class="sxs-lookup"><span data-stu-id="46e32-224">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="46e32-225">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="46e32-225">Next Development Checkpoint</span></span>

<span data-ttu-id="46e32-226">Se si segue il percorso di checkpoint per lo sviluppo con Unity che è stato delineato, ci si trova nella fase di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="46e32-226">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="46e32-227">Da qui, è possibile passare all'argomento successivo:</span><span class="sxs-lookup"><span data-stu-id="46e32-227">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="46e32-228">Distribuzione nell'emulatore HoloLens</span><span class="sxs-lookup"><span data-stu-id="46e32-228">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="46e32-229">In alternativa, passare direttamente all'aggiunta di servizi avanzati:</span><span class="sxs-lookup"><span data-stu-id="46e32-229">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="46e32-230">Servizi avanzati</span><span class="sxs-lookup"><span data-stu-id="46e32-230">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="46e32-231">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="46e32-231">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="46e32-232">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="46e32-232">See also</span></span>
* [<span data-ttu-id="46e32-233">Installare gli strumenti</span><span class="sxs-lookup"><span data-stu-id="46e32-233">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="46e32-234">Uso dell'emulatore HoloLens</span><span class="sxs-lookup"><span data-stu-id="46e32-234">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="46e32-235">Distribuzione e debug delle app UWP (Universal Windows Platform)</span><span class="sxs-lookup"><span data-stu-id="46e32-235">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [<span data-ttu-id="46e32-236">Abilitare il dispositivo per lo sviluppo</span><span class="sxs-lookup"><span data-stu-id="46e32-236">Enable your device for development</span></span>](/windows/uwp/get-started/enable-your-device-for-development)