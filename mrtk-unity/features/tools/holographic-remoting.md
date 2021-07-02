---
title: Holographic Remoting
description: Documentazione di Holographic Remoting MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 0fbde863185a9f51b53192a338e9403dc79248db
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176646"
---
# <a name="holographic-remoting"></a><span data-ttu-id="23c46-104">Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="23c46-104">Holographic remoting</span></span>

<span data-ttu-id="23c46-105">Holographic Remoting streaming il contenuto olografico da un PC al Microsoft HoloLens in tempo reale, usando una Wi-Fi o un cavo USB.</span><span class="sxs-lookup"><span data-stu-id="23c46-105">Holographic remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi or USB cable connection.</span></span> <span data-ttu-id="23c46-106">Questa funzionalità può aumentare significativamente la produttività degli sviluppatori quando si sviluppano applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="23c46-106">This feature can significantly increase developer productivity when developing mixed reality applications.</span></span>

<span data-ttu-id="23c46-107">XR SDK come indicato di seguito fa riferimento alla nuova [pipeline XR di Unity in Unity 2019.3 e versioni seguenti.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)</span><span class="sxs-lookup"><span data-stu-id="23c46-107">XR SDK as mentioned below refers to Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="23c46-108">Per [altre](../../configuration/getting-started-with-mrtk-and-xrsdk.md) informazioni sull'uso di XR SDK con MRTK, vedere qui.</span><span class="sxs-lookup"><span data-stu-id="23c46-108">See [here](../../configuration/getting-started-with-mrtk-and-xrsdk.md) for more information on using XR SDK with MRTK.</span></span> <span data-ttu-id="23c46-109">XR legacy fa riferimento alla pipeline XR esistente inclusa in Unity 2018, deprecata in Unity 2019.3 e rimossa in Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="23c46-109">Legacy XR refers to the existing XR pipeline that is included in Unity 2018, deprecated in Unity 2019.3 and removed in Unity 2020.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="23c46-110">Configurazione iniziale</span><span class="sxs-lookup"><span data-stu-id="23c46-110">Initial setup</span></span>

<span data-ttu-id="23c46-111">Per abilitare la comunicazione remota a HoloLens, è importante assicurarsi che il progetto utilizzi i componenti remoti più recenti.</span><span class="sxs-lookup"><span data-stu-id="23c46-111">To enable remoting to a HoloLens, it is important to ensure that the project is using the latest remoting components.</span></span>

1. <span data-ttu-id="23c46-112">Apri **finestra > Gestione pacchetti**</span><span class="sxs-lookup"><span data-stu-id="23c46-112">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="23c46-113">Se si usa XR legacy: verificare che sia installata la versione più recente **Windows Mixed Reality** pacchetto.</span><span class="sxs-lookup"><span data-stu-id="23c46-113">If using legacy XR: Verify that latest version of the **Windows Mixed Reality** package is installed.</span></span>
    - <span data-ttu-id="23c46-114">Se si usa XR SDK: verificare che sia installata la versione più **recente Windows pacchetto plug-in XR.**</span><span class="sxs-lookup"><span data-stu-id="23c46-114">If using XR SDK: Verify that latest version of the **Windows XR Plugin** package is installed.</span></span>
1. <span data-ttu-id="23c46-115">Verificare che l'applicazione Holographic Remoting più recente sia installata nel HoloLens, tramite il Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="23c46-115">Ensure the latest Holographic Remoting application is installed, on the HoloLens, via the Microsoft Store.</span></span>

<span data-ttu-id="23c46-116">Continuare con le [istruzioni di installazione legacy di XR](#legacy-xr-setup-instructions) o [XR SDK](#xr-sdk-setup-instructions) a seconda della pipeline usata nel progetto.</span><span class="sxs-lookup"><span data-stu-id="23c46-116">Please continue to [Legacy XR setup instructions](#legacy-xr-setup-instructions) or [XR SDK setup instructions](#xr-sdk-setup-instructions) depending on which pipeline is used in the project.</span></span>

## <a name="legacy-xr-setup-instructions"></a><span data-ttu-id="23c46-117">Istruzioni di configurazione di XR legacy</span><span class="sxs-lookup"><span data-stu-id="23c46-117">Legacy XR setup instructions</span></span>

<span data-ttu-id="23c46-118">Le istruzioni seguenti si applicano solo alla comunicazione remota con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="23c46-118">The instructions below only apply to remoting with HoloLens 2.</span></span> <span data-ttu-id="23c46-119">Se si esegue la comunicazione remota solo con HoloLens (prima generazione), passare a Connessione al HoloLens [con Wi-Fi.](#connecting-to-the-hololens-with-wi-fi)</span><span class="sxs-lookup"><span data-stu-id="23c46-119">If you only perform remoting with HoloLens (1st Gen), skip to [Connecting to the HoloLens with Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span></span>

<span data-ttu-id="23c46-120">Quando si usa un HoloLens 2, a MRTK è stato aggiunto il supporto per i dati di tracciamento oculare e mano articolati remoti.</span><span class="sxs-lookup"><span data-stu-id="23c46-120">When using a HoloLens 2, support for remoting articulated hand and eye tracking data has been added to MRTK.</span></span> <span data-ttu-id="23c46-121">Per abilitare queste funzionalità, seguire i passaggi documentati in [Importare DotNetWinRT nel progetto](#import-dotnetwinrt-into-the-project).</span><span class="sxs-lookup"><span data-stu-id="23c46-121">To enable these features, please follow the steps documented in [Import DotNetWinRT into the project](#import-dotnetwinrt-into-the-project).</span></span>

<span data-ttu-id="23c46-122">Dopo l'importazione, il passaggio successivo consiste nel selezionare **Mixed Reality**  >  **Toolkit**  >  **Utilities**  >  **Windows Mixed Reality**  >  **Check Configuration (Controlla configurazione).**</span><span class="sxs-lookup"><span data-stu-id="23c46-122">Once imported, the next step is to select **Mixed Reality** > **Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration**.</span></span> <span data-ttu-id="23c46-123">Questo passaggio aggiunge una definizione di scripting che abilita la dipendenza DotNetWinRT.</span><span class="sxs-lookup"><span data-stu-id="23c46-123">This step adds a scripting define that enables the DotNetWinRT dependency.</span></span>

> [!NOTE]
> <span data-ttu-id="23c46-124">Quando si usa Unity 2019.4 e versione più recente, non è necessario eseguire l'utilità Controlla configurazione.</span><span class="sxs-lookup"><span data-stu-id="23c46-124">When using Unity 2019.4 and newer, it is not necessary to run the Check Configuration utility.</span></span>

<span data-ttu-id="23c46-125">Per abilitare il tracciamento delle giunzioni delle mani e il tracciamento oculare, seguire i passaggi nelle sezioni Debug **HoloLens 2 remoto tramite l'importazione** di pacchetti Unity e le sezioni correlate.</span><span class="sxs-lookup"><span data-stu-id="23c46-125">To enable tracking of hand joints and eye tracking, follow the steps in the **Debugging HoloLens 2 remoting via Unity package import** and related sections.</span></span>

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a><span data-ttu-id="23c46-126">Debug di HoloLens 2 remota tramite l'importazione di pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="23c46-126">Debugging HoloLens 2 remoting via Unity package import</span></span>

<span data-ttu-id="23c46-127">Se HoloLens 2 le giunzioni delle mani e il tracciamento oculare non funzionano con la comunicazione remota, esistono alcuni punti comuni di potenziali problemi.</span><span class="sxs-lookup"><span data-stu-id="23c46-127">If HoloLens 2 hand joints and eye tracking aren't working over remoting, there are a few common points of potential issues.</span></span> <span data-ttu-id="23c46-128">Sono elencati di seguito nell'ordine in cui devono essere controllati.</span><span class="sxs-lookup"><span data-stu-id="23c46-128">They're listed below in the order they should be checked.</span></span>

<span data-ttu-id="23c46-129">Questi problemi sono particolarmente rilevanti quando vengono eseguiti **in Unity 2019.3** o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="23c46-129">These issues are particularly relevant when running on **Unity 2019.3** or later.</span></span>

#### <a name="import-dotnetwinrt-into-the-project"></a><span data-ttu-id="23c46-130">Importare DotNetWinRT nel progetto</span><span class="sxs-lookup"><span data-stu-id="23c46-130">Import DotNetWinRT into the project</span></span>

1. <span data-ttu-id="23c46-131">Scaricare lo strumento [di funzionalità di realtà mista](https://aka.ms/MRFeatureTool)</span><span class="sxs-lookup"><span data-stu-id="23c46-131">Download the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool)</span></span>

1. <span data-ttu-id="23c46-132">Nella visualizzazione **Individua funzionalità** selezionare Mixed *Reality WinRT Projections (Proiezioni WinRT di realtà mista)*</span><span class="sxs-lookup"><span data-stu-id="23c46-132">In the **Discover features** view, select *Mixed Reality WinRT Projections*</span></span>

    ![Selezionare il pacchetto DotNetWinRT](../images/tools/remoting/SelectDotNetWinRT.png)

1. <span data-ttu-id="23c46-134">Fare **clic su Ottieni** funzionalità e continuare a [importare il pacchetto](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span><span class="sxs-lookup"><span data-stu-id="23c46-134">Click **Get Features** and continue to [import the package](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span></span>

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a><span data-ttu-id="23c46-135">DOTNETWINRT_PRESENT definite scritte nelle impostazioni del lettore</span><span class="sxs-lookup"><span data-stu-id="23c46-135">DOTNETWINRT_PRESENT define written into player settings</span></span>

> [!NOTE]
> <span data-ttu-id="23c46-136">Quando si usa Unity 2019.4 e versione più recente, la definizione DOTNETWINRT_PRESENT è contenuta all'interno dei file asmdef appropriati e non del lettore Unity Impostazioni.</span><span class="sxs-lookup"><span data-stu-id="23c46-136">When using Unity 2019.4 and newer, the DOTNETWINRT_PRESENT define is contained within the appropriate .asmdef files and not the Unity Player Settings.</span></span> <span data-ttu-id="23c46-137">Il passaggio Controlla configurazione non è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="23c46-137">The Check Configuration step is not required.</span></span>

<span data-ttu-id="23c46-138">A partire da MRTK versione 2.5.0, per motivi di prestazioni, questa #define non viene più impostata automaticamente.</span><span class="sxs-lookup"><span data-stu-id="23c46-138">Beginning with MRTK version 2.5.0, for performance reasons, this #define is no longer automatically set.</span></span> <span data-ttu-id="23c46-139">Per abilitare questo flag, usare la voce di menu **Mixed Reality Toolkit**  >  **Utilities**  >  **Windows Mixed Reality** Check Configuration  >  **(Controlla** configurazione).</span><span class="sxs-lookup"><span data-stu-id="23c46-139">To enable this flag, please use the **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration** menu item.</span></span>

> [!Note]
> <span data-ttu-id="23c46-140">L'elemento Controlla configurazione non visualizza una conferma.</span><span class="sxs-lookup"><span data-stu-id="23c46-140">The Check Configuration item does not display a confirmation.</span></span> <span data-ttu-id="23c46-141">Per verificare che la definizione sia stata impostata, passare alla pagina Unity Player Impostazioni.</span><span class="sxs-lookup"><span data-stu-id="23c46-141">To confirm that the define has been set, please navigate to the Unity Player Settings.</span></span> <span data-ttu-id="23c46-142">Da qui, nella scheda UWP, controllare in Altri Impostazioni i simboli di definizione dello scripting.</span><span class="sxs-lookup"><span data-stu-id="23c46-142">From there, under the UWP tab, check under Other Settings for the Scripting Define Symbols.</span></span> <span data-ttu-id="23c46-143">Assicurarsi che DOTNETWINRT_PRESENT sia scritto correttamente nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="23c46-143">Make sure DOTNETWINRT_PRESENT is properly written in that list.</span></span> <span data-ttu-id="23c46-144">Se è presente, questo passaggio ha avuto esito positivo.</span><span class="sxs-lookup"><span data-stu-id="23c46-144">If that's there, this step succeeded.</span></span>

![DotNetWinRT presente](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a><span data-ttu-id="23c46-146">Rimozione del HoloLens 2 remoto specifico per l'utente</span><span class="sxs-lookup"><span data-stu-id="23c46-146">Removing HoloLens 2-specific remoting support</span></span>

<span data-ttu-id="23c46-147">Se si verificano conflitti o altri problemi a causa della presenza dell'adattatore DotNetWinRT, contattare una delle [risorse della Guida.](../../index.md#getting-help)</span><span class="sxs-lookup"><span data-stu-id="23c46-147">If you're running into conflicts or other issues due to the presence of the DotNetWinRT adapter, please [reach out on one of our help resources](../../index.md#getting-help).</span></span>

## <a name="xr-sdk-setup-instructions"></a><span data-ttu-id="23c46-148">Istruzioni di installazione di XR SDK</span><span class="sxs-lookup"><span data-stu-id="23c46-148">XR SDK setup instructions</span></span>

<span data-ttu-id="23c46-149">Seguire le Windows Mixed Reality di configurazione nella pagina Getting [started with MRTK and XR SDK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) (Introduzione a MRTK e XR SDK) e assicurarsi di eseguire il passaggio necessario per la comunicazione remota nell'editor HoloLens remota.</span><span class="sxs-lookup"><span data-stu-id="23c46-149">Follow the [Windows Mixed Reality setup instructions on the Getting started with MRTK and XR SDK page](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) and make sure to perform the step required for in-editor HoloLens Remoting.</span></span>

## <a name="connecting-to-the-hololens-with-wi-fi"></a><span data-ttu-id="23c46-150">Connessione al HoloLens con Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="23c46-150">Connecting to the HoloLens with Wi-Fi</span></span>

<span data-ttu-id="23c46-151">Dopo aver configurato il progetto, è possibile stabilire una connessione al HoloLens.</span><span class="sxs-lookup"><span data-stu-id="23c46-151">Once the project has been configured, a connection can be established to the HoloLens.</span></span>

1. <span data-ttu-id="23c46-152">In **Compilazione > file Impostazioni** assicurarsi che il tipo di compilazione del progetto sia impostato su Universal Windows **Platform**</span><span class="sxs-lookup"><span data-stu-id="23c46-152">In **File > Build Settings**, ensure that the project build type is set to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="23c46-153">Nel HoloLens avviare **l'applicazione Holographic Remoting.**</span><span class="sxs-lookup"><span data-stu-id="23c46-153">On the HoloLens, launch the **Holographic Remoting** application.</span></span>
1. <span data-ttu-id="23c46-154">In Unity selezionare **Window > XR > Holographic Emulation (se si usa XR legacy) /Windows XR Plugin Remoting (se si usa XR SDK).**</span><span class="sxs-lookup"><span data-stu-id="23c46-154">In Unity, select **Window > XR > Holographic Emulation (if using legacy XR) / Windows XR Plugin Remoting (if using XR SDK)**.</span></span>

    ![Avviare l'emulazione olografica](../images/tools/remoting/StartHolographicEmulation.png)

1. <span data-ttu-id="23c46-156">Impostare **Modalità di emulazione** **su Remoto su Dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="23c46-156">Set **Emulation Mode** to **Remote to Device**.</span></span>

    ![Impostare la modalità di emulazione](../images/tools/remoting/SelectEmulationMode.png)

1. <span data-ttu-id="23c46-158">(**_si applica solo a XR legacy)_** Selezionare la **versione del dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="23c46-158">(**_Only applies to legacy XR_**) Select the **Device Version**.</span></span>

    ![Selezionare la versione del dispositivo](../images/tools/remoting/SelectDeviceVersion.png)

1. <span data-ttu-id="23c46-160">Usando l'indirizzo IP visualizzato dall'applicazione Holographic Remoting Player, impostare il **campo Computer** remoto.</span><span class="sxs-lookup"><span data-stu-id="23c46-160">Using the IP Address displayed by the Holographic Remoting Player application, set the **Remote Machine** field.</span></span>

    ![Immettere l'indirizzo IP](../images/tools/remoting/EnterIPAddress.png)

1. <span data-ttu-id="23c46-162">Fare clic su **Connetti**.</span><span class="sxs-lookup"><span data-stu-id="23c46-162">Click **Connect**.</span></span>

> [!NOTE]
> <span data-ttu-id="23c46-163">Se non è possibile connettersi, assicurarsi che HoloLens 2 dispositivo non sia collegato al PC e riavviare Unity.</span><span class="sxs-lookup"><span data-stu-id="23c46-163">If you cannot connect, make sure your HoloLens 2 is not plugged in to your PC and restart Unity.</span></span>

## <a name="connecting-to-the-hololens-with-usb-cable"></a><span data-ttu-id="23c46-164">Connessione al dispositivo HoloLens cavo USB</span><span class="sxs-lookup"><span data-stu-id="23c46-164">Connecting to the HoloLens with USB cable</span></span>

<span data-ttu-id="23c46-165">La connessione tramite cavo USB offre una qualità e una stabilità di rendering migliori.</span><span class="sxs-lookup"><span data-stu-id="23c46-165">USB cable connection gives better rendering quality and stability.</span></span> <span data-ttu-id="23c46-166">Per usare la connessione tramite cavo USB, disconnettersi dal HoloLens da Wi-Fi nel Impostazioni di HoloLens e avviare l'app Holographic Remoting Player.</span><span class="sxs-lookup"><span data-stu-id="23c46-166">To use USB cable connection, disconnect from the HoloLens from Wi-Fi in HoloLens's Settings and launch Holographic Remoting Player app.</span></span> <span data-ttu-id="23c46-167">Verrà visualizzato un indirizzo IP che inizia con 169.</span><span class="sxs-lookup"><span data-stu-id="23c46-167">It will display an IP address that starts with 169.</span></span> <span data-ttu-id="23c46-168">Usare questo indirizzo IP nell'impostazione Holographic Emulation (Emulazione olografica) di Unity per connettersi.</span><span class="sxs-lookup"><span data-stu-id="23c46-168">Use this IP address in Unity's Holographic Emulation setting to connect.</span></span> <span data-ttu-id="23c46-169">Dopo aver identificato l'indirizzo IP per il cavo USB, è possibile connettere nuovamente il HoloLens alla Wi-Fi usb.</span><span class="sxs-lookup"><span data-stu-id="23c46-169">Once the IP address for USB cable has been identified, it is safe to connect the HoloLens to Wi-Fi again.</span></span>

## <a name="starting-a-remoting-session"></a><span data-ttu-id="23c46-170">Avvio di una sessione remota</span><span class="sxs-lookup"><span data-stu-id="23c46-170">Starting a remoting session</span></span>

<span data-ttu-id="23c46-171">Con Unity connesso al HoloLens, accedere alla modalità di riproduzione nell'editor.</span><span class="sxs-lookup"><span data-stu-id="23c46-171">With Unity connected to the HoloLens, enter play mode in the editor.</span></span>

<span data-ttu-id="23c46-172">Al termine della sessione, uscire dalla modalità di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="23c46-172">When the session is complete, exit play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="23c46-173">Esiste un problema noto con alcune versioni di Unity a causa del quale l'editor potrebbe bloccarsi quando entra in modalità di riproduzione durante una sessione remota.</span><span class="sxs-lookup"><span data-stu-id="23c46-173">There is a known issue with some versions of Unity where the editor may hang upon entering play mode during a remoting session.</span></span> <span data-ttu-id="23c46-174">Questo problema può manifestarsi se la finestra olografica è aperta quando viene caricato il progetto.</span><span class="sxs-lookup"><span data-stu-id="23c46-174">This issue may manifest if the Holographic window is open when the project is loaded.</span></span> <span data-ttu-id="23c46-175">Per assicurarsi che questo problema non si verifichi, chiudere sempre la finestra di dialogo olografica prima di uscire da Unity.</span><span class="sxs-lookup"><span data-stu-id="23c46-175">To ensure this issue does not occur, always close the Holographic dialog prior to exiting Unity.</span></span>

## <a name="see-also"></a><span data-ttu-id="23c46-176">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="23c46-176">See also</span></span>

- [<span data-ttu-id="23c46-177">Risoluzione dei problemi e limitazioni di Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="23c46-177">Holographic Remoting troubleshooting and limitations</span></span>](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [<span data-ttu-id="23c46-178">Condizioni di licenza software di Microsoft Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="23c46-178">Microsoft Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
