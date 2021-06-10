---
title: Uso di Visual Studio per la distribuzione e il debug
description: Informazioni su come compilare, sottoporre a debug e distribuire app per HoloLens e Windows Mixed Reality con Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, realtà mista, debug, distribuzione
ms.openlocfilehash: 5510646c058f683babff5e9e34dd296f88cd06c3
ms.sourcegitcommit: b4bdac2c4d7315902712ce74fd909fb8383d4bfd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110543227"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="c20e0-104">Uso di Visual Studio per la distribuzione e il debug</span><span class="sxs-lookup"><span data-stu-id="c20e0-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="c20e0-105">Indipendentemente dal fatto che venga usato DirectX o Unity per lo sviluppo di un'app di realtà mista, Visual Studio rimane lo strumento ideale per il debug e la distribuzione.</span><span class="sxs-lookup"><span data-stu-id="c20e0-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="c20e0-106">In questa sezione imparerai a eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="c20e0-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="c20e0-107">Distribuire applicazioni nel visore VR immersive di HoloLens o Windows Mixed Reality tramite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c20e0-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="c20e0-108">Usare l'emulatore HoloLens incorporato in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c20e0-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="c20e0-109">Eseguire il debug di app di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="c20e0-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c20e0-110">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="c20e0-110">Prerequisites</span></span>

1. <span data-ttu-id="c20e0-111">Per le istruzioni di installazione, vedi [Installare gli strumenti](../../develop/install-the-tools.md#installation-checklist).</span><span class="sxs-lookup"><span data-stu-id="c20e0-111">See [Install the Tools](../../develop/install-the-tools.md#installation-checklist) for installation instructions.</span></span>
2. <span data-ttu-id="c20e0-112">Crea un progetto di app di Windows universale in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c20e0-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="c20e0-113">Per HoloLens (prima generazione), usa Visual Studio 2017 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="c20e0-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="c20e0-114">Per HoloLens 2, usare Visual Studio 2019 16.2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="c20e0-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="c20e0-115">C# e C++ sono supportati.</span><span class="sxs-lookup"><span data-stu-id="c20e0-115">C# and C++ are supported.</span></span> <span data-ttu-id="c20e0-116">In alternativa, segui le istruzioni per [creare un'app in Unity](../../develop/unity/tutorials/holograms-100.md).</span><span class="sxs-lookup"><span data-stu-id="c20e0-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="c20e0-117">Abilitazione della modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="c20e0-117">Enabling Developer Mode</span></span>

<span data-ttu-id="c20e0-118">Per iniziare, abilita **Modalità sviluppatore** sul tuo dispositivo per consentire a Visual Studio di connettersi.</span><span class="sxs-lookup"><span data-stu-id="c20e0-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="c20e0-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="c20e0-119">HoloLens</span></span>

1. <span data-ttu-id="c20e0-120">Accendi HoloLens e il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c20e0-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="c20e0-121">Usare il [gesto Start](../../design/system-gesture.md) per avviare il menu principale.</span><span class="sxs-lookup"><span data-stu-id="c20e0-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="c20e0-122">Seleziona il riquadro **Impostazioni** per avviare l'app nell'ambiente in uso.</span><span class="sxs-lookup"><span data-stu-id="c20e0-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="c20e0-123">Scegli la voce di menu **Aggiorna**.</span><span class="sxs-lookup"><span data-stu-id="c20e0-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="c20e0-124">Scegli la voce di menu **Per gli sviluppatori**.</span><span class="sxs-lookup"><span data-stu-id="c20e0-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="c20e0-125">Abilitare **Usa le funzionalità per sviluppatori** per distribuire le app Visual Studio in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c20e0-125">Enable **Use developer features** to deploy apps from Visual Studio to your HoloLens.</span></span> <span data-ttu-id="c20e0-126">Se il dispositivo esegue Windows Holographic versione 21H1 o successiva, abilitare anche **Individuazione dispositivi**.</span><span class="sxs-lookup"><span data-stu-id="c20e0-126">If your device is running Windows Holographic version 21H1 or newer, also enable **Device discovery**.</span></span>
7. <span data-ttu-id="c20e0-127">Facoltativo: scorrere verso il basso e abilitare anche il **Portale di dispositivi**, che consente di connettersi al [Portale di dispositivi di Windows](using-the-windows-device-portal.md) in HoloLens da un Web browser.</span><span class="sxs-lookup"><span data-stu-id="c20e0-127">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="c20e0-128">PC Windows</span><span class="sxs-lookup"><span data-stu-id="c20e0-128">Windows PC</span></span>

<span data-ttu-id="c20e0-129">Se si usa un visore VR di Windows Mixed Reality connesso al PC, è necessario abilitare **Modalità sviluppatore** nel PC.</span><span class="sxs-lookup"><span data-stu-id="c20e0-129">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="c20e0-130">Vai a **Impostazioni**</span><span class="sxs-lookup"><span data-stu-id="c20e0-130">Go to **Settings**</span></span>
2. <span data-ttu-id="c20e0-131">Seleziona **Aggiornamento e sicurezza**</span><span class="sxs-lookup"><span data-stu-id="c20e0-131">Select **Update and Security**</span></span>
3. <span data-ttu-id="c20e0-132">Seleziona **Per gli sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="c20e0-132">Select **For developers**</span></span>
4. <span data-ttu-id="c20e0-133">Abilitare **Modalità sviluppatore**, leggere la dichiarazione di non responsabilità relativa all'impostazione scelta e quindi selezionare Sì per accettare la modifica.</span><span class="sxs-lookup"><span data-stu-id="c20e0-133">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-a-hololens-app-over-wi-fi"></a><span data-ttu-id="c20e0-134">Distribuzione di un'app HoloLens Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="c20e0-134">Deploying a HoloLens app over Wi-Fi</span></span> 

<span data-ttu-id="c20e0-135">Configurare il Visual Studio progetto con le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="c20e0-135">Configure your Visual Studio project with the following properties:</span></span>

1. <span data-ttu-id="c20e0-136">Selezionare le opzioni di compilazione delle app</span><span class="sxs-lookup"><span data-stu-id="c20e0-136">Select your apps compilation options</span></span>
    * <span data-ttu-id="c20e0-137">Per i progetti Unity scegliere **Versione o** **Master**</span><span class="sxs-lookup"><span data-stu-id="c20e0-137">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="c20e0-138">Per tutti gli altri progetti, scegliere **Versione**</span><span class="sxs-lookup"><span data-stu-id="c20e0-138">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="c20e0-139">È possibile trovare definizioni complete per ogni opzione di compilazione nell'esportazione e nella [Visual Studio soluzioni](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="c20e0-139">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="c20e0-140">Selezionare la configurazione di compilazione in base al dispositivo</span><span class="sxs-lookup"><span data-stu-id="c20e0-140">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="c20e0-141">Seleziona **Computer remoto** nel menu a discesa delle destinazioni di distribuzione</span><span class="sxs-lookup"><span data-stu-id="c20e0-141">Select **Remote Machine** in the deployment target drop-down menu</span></span>

![Destinazione di distribuzione computer remoto in Visual Studio](images/remotemachinesetting_arm64.png)

<span data-ttu-id="c20e0-143">Successivamente, è necessario impostare la connessione remota.</span><span class="sxs-lookup"><span data-stu-id="c20e0-143">Next, you need to set your remote connection.</span></span> <span data-ttu-id="c20e0-144">Per i progetti C++ e JavaScript, vai a **Progetto > Proprietà > Proprietà di configurazione > Debug**.</span><span class="sxs-lookup"><span data-stu-id="c20e0-144">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="c20e0-145">Se si lavora in un progetto C#, verrà visualizzata automaticamente una finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="c20e0-145">If you're working in a C# project, a dialog should automatically appear.</span></span>

> [!NOTE]
> <span data-ttu-id="c20e0-146">Se la finestra di dialogo di connessione remota non viene visualizzata nel progetto C#, è possibile aprirla manualmente da **Proprietà > Debug**.</span><span class="sxs-lookup"><span data-stu-id="c20e0-146">If the remote connection dialog doesn't appear in your C# project, you can open it manually from **Properties > Debug**.</span></span>

1. <span data-ttu-id="c20e0-147">Immetti l'indirizzo IP del tuo dispositivo nel campo **Indirizzo** o **Nome computer**.</span><span class="sxs-lookup"><span data-stu-id="c20e0-147">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> 
    * <span data-ttu-id="c20e0-148">È possibile trovare l'indirizzo IP in HoloLens in Impostazioni **> rete & Internet > opzioni avanzate**</span><span class="sxs-lookup"><span data-stu-id="c20e0-148">You can find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**</span></span>
    * <span data-ttu-id="c20e0-149">È sempre consigliabile immettere manualmente l'indirizzo IP anziché a seconda della funzionalità Rilevata automaticamente</span><span class="sxs-lookup"><span data-stu-id="c20e0-149">We always recommend manually entering your IP address rather than depending on the Auto Detected feature</span></span>

2. <span data-ttu-id="c20e0-150">Impostare la **modalità di autenticazione** su Universale **(protocollo non crittografato)**</span><span class="sxs-lookup"><span data-stu-id="c20e0-150">Set the **Authentication Mode** to **Universal (Unencrypted protocol)**</span></span>

  ![Finestra di dialogo connessione remota in Visual Studio](images/remotedeploy.png)

3. <span data-ttu-id="c20e0-152">Compilare, distribuire ed eseguire il debug dell'app in base alle esigenze</span><span class="sxs-lookup"><span data-stu-id="c20e0-152">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="c20e0-153">Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug</span><span class="sxs-lookup"><span data-stu-id="c20e0-153">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="c20e0-154">Selezionare **Compila > Distribuisci** per compilare e distribuire senza eseguire il debug</span><span class="sxs-lookup"><span data-stu-id="c20e0-154">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Avvia senza eseguire debug in Visual Studio](images/deploywithdebugging.png)

4. <span data-ttu-id="c20e0-156">La prima volta che viene distribuita un'app in HoloLens dal PC, verrà chiesto di specificare un PIN.</span><span class="sxs-lookup"><span data-stu-id="c20e0-156">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="c20e0-157">Segui le istruzioni riportate di seguito in **Associazione del dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="c20e0-157">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-a-hololens-app-over-usb"></a><span data-ttu-id="c20e0-158">Distribuzione di un'app HoloLens tramite USB</span><span class="sxs-lookup"><span data-stu-id="c20e0-158">Deploying a HoloLens app over USB</span></span> 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="c20e0-159">Selezionare le opzioni di compilazione delle app</span><span class="sxs-lookup"><span data-stu-id="c20e0-159">Select your apps compilation options</span></span>
    * <span data-ttu-id="c20e0-160">Per i progetti Unity scegliere **Versione o** **Master**</span><span class="sxs-lookup"><span data-stu-id="c20e0-160">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="c20e0-161">Per tutti gli altri progetti, scegliere **Versione**</span><span class="sxs-lookup"><span data-stu-id="c20e0-161">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="c20e0-162">È possibile trovare definizioni complete per ogni opzione di compilazione nell'esportazione e nella [Visual Studio soluzioni](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="c20e0-162">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="c20e0-163">Selezionare la configurazione di compilazione in base al dispositivo</span><span class="sxs-lookup"><span data-stu-id="c20e0-163">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="c20e0-164">Seleziona **Dispositivo** nel menu a discesa delle destinazioni di distribuzione</span><span class="sxs-lookup"><span data-stu-id="c20e0-164">Select **Device** in the deployment target drop-down menu</span></span>

![Distribuzione dispositivi in Visual Studio](images/buildsettingsusbdeploy_arm64.png)

4. <span data-ttu-id="c20e0-166">Compilare, distribuire ed eseguire il debug dell'app in base alle esigenze</span><span class="sxs-lookup"><span data-stu-id="c20e0-166">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="c20e0-167">Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug</span><span class="sxs-lookup"><span data-stu-id="c20e0-167">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="c20e0-168">Selezionare **Compila > Distribuisci** per compilare e distribuire senza eseguire il debug</span><span class="sxs-lookup"><span data-stu-id="c20e0-168">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Avvia senza eseguire debug in Visual Studio](images/deploywithdebugging.png)</br>

5. <span data-ttu-id="c20e0-170">La prima volta che viene distribuita un'app in HoloLens dal PC, verrà chiesto di specificare un PIN.</span><span class="sxs-lookup"><span data-stu-id="c20e0-170">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="c20e0-171">Segui le istruzioni riportate di seguito in **Associazione del dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="c20e0-171">Follow the **Pairing your device** instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="c20e0-172">Se si verifica un ritardo notevole con la distribuzione delle app tramite USB, è consigliabile usare le istruzioni del [computer](#deploying-a-hololens-app-over-wi-fi) remoto nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="c20e0-172">If you're seeing considerable lag time with your apps deployment over USB, we recommend using the [remote machine instructions](#deploying-a-hololens-app-over-wi-fi) in the previous section.</span></span>

## <a name="deploying-an-app-to-the-hololens-emulator"></a><span data-ttu-id="c20e0-173">Distribuzione di un'app nell'emulatore HoloLens</span><span class="sxs-lookup"><span data-stu-id="c20e0-173">Deploying an app to the HoloLens Emulator</span></span>

1. <span data-ttu-id="c20e0-174">Assicurarsi di aver installato **[l'emulatore HoloLens 2 o HoloLens (prima generazione)](../install-the-tools.md#installation-checklist)**</span><span class="sxs-lookup"><span data-stu-id="c20e0-174">Make sure you've **[installed either the HoloLens 2 or HoloLens (1st gen) Emulator](../install-the-tools.md#installation-checklist)**</span></span>
2. <span data-ttu-id="c20e0-175">Selezionare la configurazione di compilazione e l'emulatore in base al dispositivo</span><span class="sxs-lookup"><span data-stu-id="c20e0-175">Select your build configuration and emulator based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="c20e0-176">Compilare, distribuire ed eseguire il debug dell'app in base alle esigenze</span><span class="sxs-lookup"><span data-stu-id="c20e0-176">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="c20e0-177">Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug</span><span class="sxs-lookup"><span data-stu-id="c20e0-177">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="c20e0-178">Selezionare **Compila > Distribuisci** per compilare e distribuire senza eseguire il debugg</span><span class="sxs-lookup"><span data-stu-id="c20e0-178">Select **Build > Deploy** to build and deploy without debuggingg</span></span>

![Avvia senza eseguire debug in Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a><span data-ttu-id="c20e0-180">Distribuzione di un'app VR nel PC locale</span><span class="sxs-lookup"><span data-stu-id="c20e0-180">Deploying a VR app to your Local PC</span></span> 

<span data-ttu-id="c20e0-181">Per usare un visore VR immersive di Windows Mixed Reality che si connette al PC o al [simulatore di realtà mista](using-the-windows-mixed-reality-simulator.md):</span><span class="sxs-lookup"><span data-stu-id="c20e0-181">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="c20e0-182">Seleziona una configurazione di build **x86** o **x64** per l'app</span><span class="sxs-lookup"><span data-stu-id="c20e0-182">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="c20e0-183">Seleziona **Computer locale** nel menu a discesa delle destinazioni di distribuzione</span><span class="sxs-lookup"><span data-stu-id="c20e0-183">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="c20e0-184">Compilare, distribuire ed eseguire il debug dell'app in base alle esigenze</span><span class="sxs-lookup"><span data-stu-id="c20e0-184">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="c20e0-185">Seleziona **Debug > Avvia debug** per distribuire l'app e avviare il debug</span><span class="sxs-lookup"><span data-stu-id="c20e0-185">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="c20e0-186">Selezionare **Compila > Distribuisci** per compilare e distribuire senza eseguire il debug</span><span class="sxs-lookup"><span data-stu-id="c20e0-186">Select **Build > Deploy** to build and deploy without debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="c20e0-187">Associazione del dispositivo</span><span class="sxs-lookup"><span data-stu-id="c20e0-187">Pairing your device</span></span>

<span data-ttu-id="c20e0-188">La prima volta che viene distribuita un'app da Visual Studio al dispositivo HoloLens, verrà chiesto di specificare un PIN.</span><span class="sxs-lookup"><span data-stu-id="c20e0-188">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="c20e0-189">In HoloLens generare un PIN avviando l'app Settings, passare a **Update > For Developers** (Aggiorna > Per gli sviluppatori) e toccare **Pair** (Associa).</span><span class="sxs-lookup"><span data-stu-id="c20e0-189">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="c20e0-190">Quando il PIN viene visualizzato in HoloLens, digitarlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c20e0-190">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="c20e0-191">Al termine dell'associazione, tocca **Fine** su HoloLens per chiudere la finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="c20e0-191">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="c20e0-192">Il PC è ora associato a HoloLens ed è possibile distribuire le app automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c20e0-192">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="c20e0-193">Ripetere questi passaggi per tutti i PC usati per distribuire app in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c20e0-193">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="c20e0-194">Per dissociare HoloLens da tutti i computer associati:</span><span class="sxs-lookup"><span data-stu-id="c20e0-194">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="c20e0-195">Avviare l'app **Settings**, passare a **Update > For Developers** (Aggiorna > Per sviluppatori) e toccare **Clear** (Cancella).</span><span class="sxs-lookup"><span data-stu-id="c20e0-195">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="c20e0-196">Debugger grafica per HoloLens (prima generazione)</span><span class="sxs-lookup"><span data-stu-id="c20e0-196">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="c20e0-197">Gli strumenti di Diagnostica della grafica di Visual Studio sono utili per la scrittura e l'ottimizzazione di un'app olografica.</span><span class="sxs-lookup"><span data-stu-id="c20e0-197">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="c20e0-198">Per informazioni dettagliate, vedi [Diagnostica della grafica di Visual Studio su MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics).</span><span class="sxs-lookup"><span data-stu-id="c20e0-198">See [Visual Studio Graphics Diagnostics on MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) for full details.</span></span>

<span data-ttu-id="c20e0-199">**Per avviare Debugger grafica**</span><span class="sxs-lookup"><span data-stu-id="c20e0-199">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="c20e0-200">Segui le istruzioni riportate sopra per specificare come destinazione un dispositivo o un emulatore</span><span class="sxs-lookup"><span data-stu-id="c20e0-200">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="c20e0-201">Vai a **Debug > Grafica > Avvia diagnostica**</span><span class="sxs-lookup"><span data-stu-id="c20e0-201">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="c20e0-202">La prima volta che viene avviata la diagnostica con un dispositivo HoloLens, è possibile che venga restituito un errore di accesso negato.</span><span class="sxs-lookup"><span data-stu-id="c20e0-202">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="c20e0-203">Riavviare il dispositivo HoloLens per rendere effettive le autorizzazioni aggiornate e riprovare.</span><span class="sxs-lookup"><span data-stu-id="c20e0-203">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="c20e0-204">Profilatura</span><span class="sxs-lookup"><span data-stu-id="c20e0-204">Profiling</span></span>

<span data-ttu-id="c20e0-205">Gli strumenti di profilatura di Visual Studio consentono di analizzare le prestazioni e l'uso delle risorse dell'app.</span><span class="sxs-lookup"><span data-stu-id="c20e0-205">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="c20e0-206">Sono inclusi strumenti per ottimizzare l'uso di CPU, memoria, grafica e rete.</span><span class="sxs-lookup"><span data-stu-id="c20e0-206">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="c20e0-207">Per i dettagli completi, vedi [Eseguire strumenti di diagnostica senza debug in MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools).</span><span class="sxs-lookup"><span data-stu-id="c20e0-207">See [Run diagnostic tools without debugging on MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) for full details.</span></span>

<span data-ttu-id="c20e0-208">**Per avviare gli strumenti di profilatura con HoloLens**</span><span class="sxs-lookup"><span data-stu-id="c20e0-208">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="c20e0-209">Segui le istruzioni riportate sopra per specificare come destinazione un dispositivo o un emulatore</span><span class="sxs-lookup"><span data-stu-id="c20e0-209">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="c20e0-210">Vai a **Debug > Avvia strumenti di diagnostica senza debug**</span><span class="sxs-lookup"><span data-stu-id="c20e0-210">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="c20e0-211">Seleziona gli strumenti che vuoi usare</span><span class="sxs-lookup"><span data-stu-id="c20e0-211">Select the tools you want to use</span></span>
4. <span data-ttu-id="c20e0-212">Selezionare **Avvia**.</span><span class="sxs-lookup"><span data-stu-id="c20e0-212">Select **Start**</span></span>
5. <span data-ttu-id="c20e0-213">La prima volta che viene avviata la diagnostica senza debug con un dispositivo HoloLens, è possibile che venga restituito un errore di accesso negato.</span><span class="sxs-lookup"><span data-stu-id="c20e0-213">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="c20e0-214">Riavviare il dispositivo HoloLens per rendere effettive le autorizzazioni aggiornate e riprovare.</span><span class="sxs-lookup"><span data-stu-id="c20e0-214">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="c20e0-215">Debug di un'app installata o in esecuzione</span><span class="sxs-lookup"><span data-stu-id="c20e0-215">Debugging an installed or running app</span></span>

<span data-ttu-id="c20e0-216">È possibile usare Visual Studio per eseguire il debug di un'app di Windows universale installata senza distribuzione da un progetto di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c20e0-216">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="c20e0-217">Questa opzione è utile se si vuole eseguire il debug di un pacchetto dell'app installato o di un'app già in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="c20e0-217">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="c20e0-218">Vai a **Debug -> Altre destinazioni debug -> Debug del pacchetto dell'app installato**</span><span class="sxs-lookup"><span data-stu-id="c20e0-218">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="c20e0-219">Seleziona la destinazione **Computer remoto** per HoloLens o **Computer locale** per i visori VR immersive.</span><span class="sxs-lookup"><span data-stu-id="c20e0-219">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="c20e0-220">Immetti l'**indirizzo IP** del dispositivo</span><span class="sxs-lookup"><span data-stu-id="c20e0-220">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="c20e0-221">Scegli la modalità di autenticazione **Universale**</span><span class="sxs-lookup"><span data-stu-id="c20e0-221">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="c20e0-222">La finestra mostra le app in esecuzione e inattive.</span><span class="sxs-lookup"><span data-stu-id="c20e0-222">The window shows both running and inactive apps.</span></span> <span data-ttu-id="c20e0-223">Seleziona quella di cui vuoi eseguire il debug.</span><span class="sxs-lookup"><span data-stu-id="c20e0-223">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="c20e0-224">Scegli il tipo di codice di cui eseguire il debug (gestito, nativo, misto)</span><span class="sxs-lookup"><span data-stu-id="c20e0-224">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="c20e0-225">Selezionare **Associa** o **Avvia**.</span><span class="sxs-lookup"><span data-stu-id="c20e0-225">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="c20e0-226">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="c20e0-226">Next Development Checkpoint</span></span>

<span data-ttu-id="c20e0-227">Se si segue il percorso di checkpoint per lo sviluppo con Unity che è stato delineato, ci si trova nella fase di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="c20e0-227">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="c20e0-228">Da qui, è possibile passare all'argomento successivo:</span><span class="sxs-lookup"><span data-stu-id="c20e0-228">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c20e0-229">Distribuzione nell'emulatore HoloLens</span><span class="sxs-lookup"><span data-stu-id="c20e0-229">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="c20e0-230">In alternativa, passare direttamente all'aggiunta di servizi avanzati:</span><span class="sxs-lookup"><span data-stu-id="c20e0-230">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c20e0-231">Servizi avanzati</span><span class="sxs-lookup"><span data-stu-id="c20e0-231">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="c20e0-232">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="c20e0-232">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="c20e0-233">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c20e0-233">See also</span></span>
* [<span data-ttu-id="c20e0-234">Installare gli strumenti</span><span class="sxs-lookup"><span data-stu-id="c20e0-234">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="c20e0-235">Uso dell'emulatore HoloLens</span><span class="sxs-lookup"><span data-stu-id="c20e0-235">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="c20e0-236">Distribuzione e debug delle app UWP (Universal Windows Platform)</span><span class="sxs-lookup"><span data-stu-id="c20e0-236">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [<span data-ttu-id="c20e0-237">Abilitare il dispositivo per lo sviluppo</span><span class="sxs-lookup"><span data-stu-id="c20e0-237">Enable your device for development</span></span>](/windows/uwp/get-started/enable-your-device-for-development)
