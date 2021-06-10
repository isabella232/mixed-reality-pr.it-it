---
title: Holographic Remoting
description: Documentazione di Holographic Remoting MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 196bbb7027389ea75ddc577e4efc397ca779d550
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647179"
---
# <a name="holographic-remoting"></a><span data-ttu-id="b47bb-104">Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="b47bb-104">Holographic Remoting</span></span>

<span data-ttu-id="b47bb-105">Holographic Remoting streaming il contenuto olografico da un PC al Microsoft HoloLens in tempo reale, usando una connessione Wi-Fi o un cavo USB.</span><span class="sxs-lookup"><span data-stu-id="b47bb-105">Holographic remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi or USB cable connection.</span></span> <span data-ttu-id="b47bb-106">Questa funzionalità può aumentare significativamente la produttività degli sviluppatori quando si sviluppano applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b47bb-106">This feature can significantly increase developer productivity when developing mixed reality applications.</span></span>

<span data-ttu-id="b47bb-107">XR SDK come indicato di seguito fa riferimento alla nuova [pipeline XR di Unity in Unity 2019.3 e versioni seguenti.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)</span><span class="sxs-lookup"><span data-stu-id="b47bb-107">XR SDK as mentioned below refers to Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="b47bb-108">Per [altre](../../configuration/getting-started-with-mrtk-and-xrsdk.md) informazioni sull'uso di XR SDK con MRTK, vedere qui.</span><span class="sxs-lookup"><span data-stu-id="b47bb-108">See [here](../../configuration/getting-started-with-mrtk-and-xrsdk.md) for more information on using XR SDK with MRTK.</span></span> <span data-ttu-id="b47bb-109">XR legacy fa riferimento alla pipeline XR esistente inclusa in Unity 2018, deprecata in Unity 2019.3 e rimossa in Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="b47bb-109">Legacy XR refers to the existing XR pipeline that is included in Unity 2018, deprecated in Unity 2019.3 and removed in Unity 2020.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="b47bb-110">Configurazione iniziale</span><span class="sxs-lookup"><span data-stu-id="b47bb-110">Initial setup</span></span>

<span data-ttu-id="b47bb-111">Per abilitare la comunicazione remota con HoloLens, è importante assicurarsi che il progetto utilizzi i componenti remoti più recenti.</span><span class="sxs-lookup"><span data-stu-id="b47bb-111">To enable remoting to a HoloLens, it is important to ensure that the project is using the latest remoting components.</span></span>

1. <span data-ttu-id="b47bb-112">Apri **finestra > Gestione pacchetti**</span><span class="sxs-lookup"><span data-stu-id="b47bb-112">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="b47bb-113">Se si usa XR legacy: verificare che sia installata la versione più **recente Windows Mixed Reality** pacchetto.</span><span class="sxs-lookup"><span data-stu-id="b47bb-113">If using legacy XR: Verify that latest version of the **Windows Mixed Reality** package is installed.</span></span>
    - <span data-ttu-id="b47bb-114">Se si usa XR SDK: verificare che sia installata la versione più recente del pacchetto **windows XR Plugin.**</span><span class="sxs-lookup"><span data-stu-id="b47bb-114">If using XR SDK: Verify that latest version of the **Windows XR Plugin** package is installed.</span></span>
1. <span data-ttu-id="b47bb-115">Verificare che l'applicazione Holographic Remoting più recente sia installata in HoloLens tramite il Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="b47bb-115">Ensure the latest Holographic Remoting application is installed, on the HoloLens, via the Microsoft Store.</span></span>

<span data-ttu-id="b47bb-116">Continuare con le [istruzioni di installazione legacy di XR](#legacy-xr-setup-instructions) o [XR SDK](#xr-sdk-setup-instructions) a seconda della pipeline usata nel progetto.</span><span class="sxs-lookup"><span data-stu-id="b47bb-116">Please continue to [Legacy XR setup instructions](#legacy-xr-setup-instructions) or [XR SDK setup instructions](#xr-sdk-setup-instructions) depending on which pipeline is used in the project.</span></span>

## <a name="legacy-xr-setup-instructions"></a><span data-ttu-id="b47bb-117">Istruzioni di configurazione di XR legacy</span><span class="sxs-lookup"><span data-stu-id="b47bb-117">Legacy XR setup instructions</span></span>

<span data-ttu-id="b47bb-118">Le istruzioni seguenti si applicano solo alla comunicazione remota con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b47bb-118">The instructions below only apply to remoting with HoloLens 2.</span></span> <span data-ttu-id="b47bb-119">Se esegui la comunicazione remota solo con HoloLens (prima generazione), passa a Connecting [to the HoloLens with Wi-Fi (Connessione a HoloLens con Wi-Fi).](#connecting-to-the-hololens-with-wi-fi)</span><span class="sxs-lookup"><span data-stu-id="b47bb-119">If you only perform remoting with HoloLens (1st Gen), skip to [Connecting to the HoloLens with Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span></span>

<span data-ttu-id="b47bb-120">Quando si usa un HoloLens 2, a MRTK è stato aggiunto il supporto per i dati di tracciamento oculare e mano articolati remoti.</span><span class="sxs-lookup"><span data-stu-id="b47bb-120">When using a HoloLens 2, support for remoting articulated hand and eye tracking data has been added to MRTK.</span></span> <span data-ttu-id="b47bb-121">Per abilitare queste funzionalità, seguire i passaggi documentati in [Importare DotNetWinRT nel progetto](#import-dotnetwinrt-into-the-project).</span><span class="sxs-lookup"><span data-stu-id="b47bb-121">To enable these features, please follow the steps documented in [Import DotNetWinRT into the project](#import-dotnetwinrt-into-the-project).</span></span>

<span data-ttu-id="b47bb-122">Dopo l'importazione, il passaggio successivo consiste nel selezionare **Mixed Reality**  >  **Toolkit**  >  **Utilities**  >  **Windows Mixed Reality**  >  **Check Configuration (Controlla configurazione).**</span><span class="sxs-lookup"><span data-stu-id="b47bb-122">Once imported, the next step is to select **Mixed Reality** > **Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration**.</span></span> <span data-ttu-id="b47bb-123">Questo passaggio aggiunge una definizione di scripting che abilita la dipendenza DotNetWinRT.</span><span class="sxs-lookup"><span data-stu-id="b47bb-123">This step adds a scripting define that enables the DotNetWinRT dependency.</span></span>

> [!NOTE]
> <span data-ttu-id="b47bb-124">Quando si usa Unity 2019.4 e versione più recente, non è necessario eseguire l'utilità Controlla configurazione.</span><span class="sxs-lookup"><span data-stu-id="b47bb-124">When using Unity 2019.4 and newer, it is not necessary to run the Check Configuration utility.</span></span>

<span data-ttu-id="b47bb-125">Per abilitare il tracciamento delle giunzioni delle mani e il tracciamento oculare, seguire la procedura descritta nelle sezioni Debug **HoloLens 2 remoto** tramite l'importazione di pacchetti Unity e le sezioni correlate.</span><span class="sxs-lookup"><span data-stu-id="b47bb-125">To enable tracking of hand joints and eye tracking, follow the steps in the **Debugging HoloLens 2 remoting via Unity package import** and related sections.</span></span>

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a><span data-ttu-id="b47bb-126">Debug di HoloLens 2 remota tramite l'importazione di pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="b47bb-126">Debugging HoloLens 2 remoting via Unity package import</span></span>

<span data-ttu-id="b47bb-127">Se HoloLens 2 mani e il tracciamento oculare non funzionano con la comunicazione remota, esistono alcuni punti comuni di potenziali problemi.</span><span class="sxs-lookup"><span data-stu-id="b47bb-127">If HoloLens 2 hand joints and eye tracking aren't working over remoting, there are a few common points of potential issues.</span></span> <span data-ttu-id="b47bb-128">Sono elencati di seguito nell'ordine in cui devono essere controllati.</span><span class="sxs-lookup"><span data-stu-id="b47bb-128">They're listed below in the order they should be checked.</span></span>

<span data-ttu-id="b47bb-129">Questi problemi sono particolarmente rilevanti quando vengono eseguiti **in Unity 2019.3** o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="b47bb-129">These issues are particularly relevant when running on **Unity 2019.3** or later.</span></span>

#### <a name="import-dotnetwinrt-into-the-project"></a><span data-ttu-id="b47bb-130">Importare DotNetWinRT nel progetto</span><span class="sxs-lookup"><span data-stu-id="b47bb-130">Import DotNetWinRT into the project</span></span>

1. <span data-ttu-id="b47bb-131">Scaricare lo strumento [di funzionalità di realtà mista](https://aka.ms/MRFeatureTool)</span><span class="sxs-lookup"><span data-stu-id="b47bb-131">Download the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool)</span></span>

1. <span data-ttu-id="b47bb-132">Nella visualizzazione **Individua funzionalità** selezionare Mixed *Reality WinRT Projections (Proiezioni WinRT di realtà mista)*</span><span class="sxs-lookup"><span data-stu-id="b47bb-132">In the **Discover features** view, select *Mixed Reality WinRT Projections*</span></span>

    ![Selezionare il pacchetto DotNetWinRT](../images/tools/remoting/SelectDotNetWinRT.png)

1. <span data-ttu-id="b47bb-134">Fare **clic su Ottieni** funzionalità e continuare a [importare il pacchetto](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span><span class="sxs-lookup"><span data-stu-id="b47bb-134">Click **Get Features** and continue to [import the package](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span></span>

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a><span data-ttu-id="b47bb-135">DOTNETWINRT_PRESENT definite scritte nelle impostazioni del lettore</span><span class="sxs-lookup"><span data-stu-id="b47bb-135">DOTNETWINRT_PRESENT define written into player settings</span></span>

> [!NOTE]
> <span data-ttu-id="b47bb-136">Quando si usa Unity 2019.4 e versione più recente, il DOTNETWINRT_PRESENT definito è contenuto nei file asmdef appropriati e non nelle impostazioni del lettore Unity.</span><span class="sxs-lookup"><span data-stu-id="b47bb-136">When using Unity 2019.4 and newer, the DOTNETWINRT_PRESENT define is contained within the appropriate .asmdef files and not the Unity Player Settings.</span></span> <span data-ttu-id="b47bb-137">Il passaggio Controlla configurazione non è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="b47bb-137">The Check Configuration step is not required.</span></span>

<span data-ttu-id="b47bb-138">A partire da MRTK versione 2.5.0, per motivi di prestazioni, questo #define non viene più impostato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b47bb-138">Beginning with MRTK version 2.5.0, for performance reasons, this #define is no longer automatically set.</span></span> <span data-ttu-id="b47bb-139">Per abilitare questo flag, usa la voce di menu **Mixed Reality Toolkit**  >  **Utilities**  >  **Windows Mixed Reality** Check Configuration  >  **(Controlla** configurazione).</span><span class="sxs-lookup"><span data-stu-id="b47bb-139">To enable this flag, please use the **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration** menu item.</span></span>

> [!Note]
> <span data-ttu-id="b47bb-140">L'elemento Controlla configurazione non visualizza una conferma.</span><span class="sxs-lookup"><span data-stu-id="b47bb-140">The Check Configuration item does not display a confirmation.</span></span> <span data-ttu-id="b47bb-141">Per verificare che la definizione sia stata impostata, passare a Unity Player Settings (Impostazioni lettore Unity).</span><span class="sxs-lookup"><span data-stu-id="b47bb-141">To confirm that the define has been set, please navigate to the Unity Player Settings.</span></span> <span data-ttu-id="b47bb-142">Da qui, nella scheda UWP, controllare in Altre impostazioni per i simboli di definizione dello scripting.</span><span class="sxs-lookup"><span data-stu-id="b47bb-142">From there, under the UWP tab, check under Other Settings for the Scripting Define Symbols.</span></span> <span data-ttu-id="b47bb-143">Assicurarsi che DOTNETWINRT_PRESENT sia scritto correttamente nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="b47bb-143">Make sure DOTNETWINRT_PRESENT is properly written in that list.</span></span> <span data-ttu-id="b47bb-144">Se è presente, questo passaggio ha avuto esito positivo.</span><span class="sxs-lookup"><span data-stu-id="b47bb-144">If that's there, this step succeeded.</span></span>

![DotNetWinRT presente](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a><span data-ttu-id="b47bb-146">Rimozione del HoloLens 2 remoto specifico del servizio</span><span class="sxs-lookup"><span data-stu-id="b47bb-146">Removing HoloLens 2-specific remoting support</span></span>

<span data-ttu-id="b47bb-147">Se si verificano conflitti o altri problemi a causa della presenza dell'adapter DotNetWinRT, contattare una delle [risorse della Guida.](../../index.md#getting-help)</span><span class="sxs-lookup"><span data-stu-id="b47bb-147">If you're running into conflicts or other issues due to the presence of the DotNetWinRT adapter, please [reach out on one of our help resources](../../index.md#getting-help).</span></span>

## <a name="xr-sdk-setup-instructions"></a><span data-ttu-id="b47bb-148">Istruzioni di installazione di XR SDK</span><span class="sxs-lookup"><span data-stu-id="b47bb-148">XR SDK setup instructions</span></span>

<span data-ttu-id="b47bb-149">Seguire le Windows Mixed Reality di configurazione nella pagina [Getting started with MRTK and XR SDK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) (Introduzione a MRTK e XR SDK) e assicurarsi di eseguire il passaggio necessario per holoLens Remoting nell'editor.</span><span class="sxs-lookup"><span data-stu-id="b47bb-149">Follow the [Windows Mixed Reality setup instructions on the Getting started with MRTK and XR SDK page](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) and make sure to perform the step required for in-editor HoloLens Remoting.</span></span>

## <a name="connecting-to-the-hololens-with-wi-fi"></a><span data-ttu-id="b47bb-150">Connessione a HoloLens con Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="b47bb-150">Connecting to the HoloLens with Wi-Fi</span></span>

<span data-ttu-id="b47bb-151">Dopo aver configurato il progetto, è possibile stabilire una connessione a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b47bb-151">Once the project has been configured, a connection can be established to the HoloLens.</span></span>

1. <span data-ttu-id="b47bb-152">In **Impostazioni > file** assicurarsi che il tipo di compilazione del progetto sia impostato su **piattaforma UWP (Universal Windows Platform)**</span><span class="sxs-lookup"><span data-stu-id="b47bb-152">In **File > Build Settings**, ensure that the project build type is set to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="b47bb-153">In HoloLens avviare **l'applicazione Holographic Remoting.**</span><span class="sxs-lookup"><span data-stu-id="b47bb-153">On the HoloLens, launch the **Holographic Remoting** application.</span></span>
1. <span data-ttu-id="b47bb-154">In Unity selezionare **Window > XR > Holographic Emulation (se si usa XR legacy) /Windows XR Plugin Remoting (se si usa XR SDK).**</span><span class="sxs-lookup"><span data-stu-id="b47bb-154">In Unity, select **Window > XR > Holographic Emulation (if using legacy XR) / Windows XR Plugin Remoting (if using XR SDK)**.</span></span>

    ![Avviare l'emulazione olografica](../images/tools/remoting/StartHolographicEmulation.png)

1. <span data-ttu-id="b47bb-156">Impostare **Modalità di emulazione** **su Remoto su Dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="b47bb-156">Set **Emulation Mode** to **Remote to Device**.</span></span>

    ![Impostare la modalità di emulazione](../images/tools/remoting/SelectEmulationMode.png)

1. <span data-ttu-id="b47bb-158">(**_si applica solo a XR legacy)_** Selezionare La **versione del dispositivo.**</span><span class="sxs-lookup"><span data-stu-id="b47bb-158">(**_Only applies to legacy XR_**) Select the **Device Version**.</span></span>

    ![Selezionare la versione del dispositivo](../images/tools/remoting/SelectDeviceVersion.png)

1. <span data-ttu-id="b47bb-160">Usando l'indirizzo IP visualizzato dall'applicazione Holographic Remoting Player, impostare il **campo Computer** remoto.</span><span class="sxs-lookup"><span data-stu-id="b47bb-160">Using the IP Address displayed by the Holographic Remoting Player application, set the **Remote Machine** field.</span></span>

    ![Immettere l'indirizzo IP](../images/tools/remoting/EnterIPAddress.png)

1. <span data-ttu-id="b47bb-162">Fare clic su **Connetti**.</span><span class="sxs-lookup"><span data-stu-id="b47bb-162">Click **Connect**.</span></span>

> [!NOTE]
> <span data-ttu-id="b47bb-163">Se non è possibile connettersi, assicurarsi che HoloLens 2 dispositivo non sia collegato al PC e riavviare Unity.</span><span class="sxs-lookup"><span data-stu-id="b47bb-163">If you cannot connect, make sure your HoloLens 2 is not plugged in to your PC and restart Unity.</span></span>

## <a name="connecting-to-the-hololens-with-usb-cable"></a><span data-ttu-id="b47bb-164">Connessione a HoloLens con cavo USB</span><span class="sxs-lookup"><span data-stu-id="b47bb-164">Connecting to the HoloLens with USB cable</span></span>

<span data-ttu-id="b47bb-165">La connessione tramite cavo USB offre una qualità e una stabilità di rendering migliori.</span><span class="sxs-lookup"><span data-stu-id="b47bb-165">USB cable connection gives better rendering quality and stability.</span></span> <span data-ttu-id="b47bb-166">Per usare la connessione tramite cavo USB, disconnettiti da HoloLens Wi-Fi in Impostazioni di HoloLens e avvia l'app Holographic Remoting Player.</span><span class="sxs-lookup"><span data-stu-id="b47bb-166">To use USB cable connection, disconnect from the HoloLens from Wi-Fi in HoloLens's Settings and launch Holographic Remoting Player app.</span></span> <span data-ttu-id="b47bb-167">Verrà visualizzato un indirizzo IP che inizia con 169.</span><span class="sxs-lookup"><span data-stu-id="b47bb-167">It will display an IP address that starts with 169.</span></span> <span data-ttu-id="b47bb-168">Usare questo indirizzo IP nell'impostazione Holographic Emulation (Emulazione olografica) di Unity per connettersi.</span><span class="sxs-lookup"><span data-stu-id="b47bb-168">Use this IP address in Unity's Holographic Emulation setting to connect.</span></span> <span data-ttu-id="b47bb-169">Dopo aver identificato l'indirizzo IP per il cavo USB, è possibile connettere di nuovo HoloLens Wi-Fi dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b47bb-169">Once the IP address for USB cable has been identified, it is safe to connect the HoloLens to Wi-Fi again.</span></span>

## <a name="starting-a-remoting-session"></a><span data-ttu-id="b47bb-170">Avvio di una sessione remota</span><span class="sxs-lookup"><span data-stu-id="b47bb-170">Starting a remoting session</span></span>

<span data-ttu-id="b47bb-171">Con Unity connesso a HoloLens, entra in modalità di riproduzione nell'editor.</span><span class="sxs-lookup"><span data-stu-id="b47bb-171">With Unity connected to the HoloLens, enter play mode in the editor.</span></span>

<span data-ttu-id="b47bb-172">Al termine della sessione, uscire dalla modalità di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="b47bb-172">When the session is complete, exit play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="b47bb-173">Esiste un problema noto con alcune versioni di Unity a causa del quale l'editor potrebbe bloccarsi quando entra in modalità di riproduzione durante una sessione remota.</span><span class="sxs-lookup"><span data-stu-id="b47bb-173">There is a known issue with some versions of Unity where the editor may hang upon entering play mode during a remoting session.</span></span> <span data-ttu-id="b47bb-174">Questo problema può manifestarsi se la finestra olografica è aperta quando viene caricato il progetto.</span><span class="sxs-lookup"><span data-stu-id="b47bb-174">This issue may manifest if the Holographic window is open when the project is loaded.</span></span> <span data-ttu-id="b47bb-175">Per assicurarsi che questo problema non si verifichi, chiudere sempre la finestra di dialogo olografica prima di uscire da Unity.</span><span class="sxs-lookup"><span data-stu-id="b47bb-175">To ensure this issue does not occur, always close the Holographic dialog prior to exiting Unity.</span></span>

## <a name="see-also"></a><span data-ttu-id="b47bb-176">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="b47bb-176">See also</span></span>

- [<span data-ttu-id="b47bb-177">Risoluzione dei problemi e limitazioni di Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="b47bb-177">Holographic Remoting troubleshooting and limitations</span></span>](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [<span data-ttu-id="b47bb-178">Condizioni di licenza software di Microsoft Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="b47bb-178">Microsoft Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)