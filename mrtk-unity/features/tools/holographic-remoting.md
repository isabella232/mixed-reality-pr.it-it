---
title: HolographicRemoting
description: Documentazione di comunicazione remota olografica MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: fad990fec79e73d5b5a1224907d1d8772685ffe8
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782332"
---
# <a name="holographic-remoting"></a><span data-ttu-id="a3c63-104">Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="a3c63-104">Holographic Remoting</span></span>

<span data-ttu-id="a3c63-105">La comunicazione remota olografica trasmette contenuto olografico da un PC a Microsoft HoloLens in tempo reale, usando una connessione via cavo Wi-Fi o USB.</span><span class="sxs-lookup"><span data-stu-id="a3c63-105">Holographic remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi or USB cable connection.</span></span> <span data-ttu-id="a3c63-106">Questa funzionalità può aumentare significativamente la produttività degli sviluppatori quando si sviluppano applicazioni di realtà miste.</span><span class="sxs-lookup"><span data-stu-id="a3c63-106">This feature can significantly increase developer productivity when developing mixed reality applications.</span></span>

<span data-ttu-id="a3c63-107">XR SDK come indicato di seguito si riferisce alla [nuova pipeline XR di Unity in unity 2019,3 e versioni successive](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="a3c63-107">XR SDK as mentioned below refers to Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="a3c63-108">Vedere [qui](../../configuration/getting-started-with-mrtk-and-xrsdk.md) per altre informazioni sull'uso di XR SDK con MRTK.</span><span class="sxs-lookup"><span data-stu-id="a3c63-108">See [here](../../configuration/getting-started-with-mrtk-and-xrsdk.md) for more information on using XR SDK with MRTK.</span></span> <span data-ttu-id="a3c63-109">La versione precedente di XR si riferisce alla pipeline XR esistente inclusa in Unity 2018, deprecata in Unity 2019,3 ed è stata rimossa in Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="a3c63-109">Legacy XR refers to the existing XR pipeline that is included in Unity 2018, deprecated in Unity 2019.3 and removed in Unity 2020.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="a3c63-110">Configurazione iniziale</span><span class="sxs-lookup"><span data-stu-id="a3c63-110">Initial setup</span></span>

<span data-ttu-id="a3c63-111">Per abilitare la comunicazione remota a una HoloLens, è importante assicurarsi che il progetto usi i componenti .NET Remoting più recenti.</span><span class="sxs-lookup"><span data-stu-id="a3c63-111">To enable remoting to a HoloLens, it is important to ensure that the project is using the latest remoting components.</span></span>

1. <span data-ttu-id="a3c63-112">Apri **finestra > gestione pacchetti**</span><span class="sxs-lookup"><span data-stu-id="a3c63-112">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="a3c63-113">Se si usa la versione precedente di XR: verificare che sia installata la versione più recente del pacchetto di **realtà mista di Windows** .</span><span class="sxs-lookup"><span data-stu-id="a3c63-113">If using legacy XR: Verify that latest version of the **Windows Mixed Reality** package is installed.</span></span>
    - <span data-ttu-id="a3c63-114">Se si usa XR SDK: verificare che sia installata la versione più recente del pacchetto di plug-in **Windows XR** .</span><span class="sxs-lookup"><span data-stu-id="a3c63-114">If using XR SDK: Verify that latest version of the **Windows XR Plugin** package is installed.</span></span>
1. <span data-ttu-id="a3c63-115">Verificare che nell'HoloLens sia installata la versione più recente dell'applicazione di comunicazione remota olografica tramite il Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="a3c63-115">Ensure the latest Holographic Remoting application is installed, on the HoloLens, via the Microsoft Store.</span></span>

<span data-ttu-id="a3c63-116">Continuare con [le istruzioni di installazione legacy XR](#legacy-xr-setup-instructions) o [le istruzioni di installazione di XR SDK](#xr-sdk-setup-instructions) a seconda della pipeline usata nel progetto.</span><span class="sxs-lookup"><span data-stu-id="a3c63-116">Please continue to [Legacy XR setup instructions](#legacy-xr-setup-instructions) or [XR SDK setup instructions](#xr-sdk-setup-instructions) depending on which pipeline is used in the project.</span></span>

## <a name="legacy-xr-setup-instructions"></a><span data-ttu-id="a3c63-117">Istruzioni per l'installazione di XR legacy</span><span class="sxs-lookup"><span data-stu-id="a3c63-117">Legacy XR setup instructions</span></span>

<span data-ttu-id="a3c63-118">Le istruzioni seguenti sono valide solo per la comunicazione remota con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a3c63-118">The instructions below only apply to remoting with HoloLens 2.</span></span> <span data-ttu-id="a3c63-119">Se si esegue solo la comunicazione remota con HoloLens (1a generazione), passare alla [connessione a HoloLens con Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span><span class="sxs-lookup"><span data-stu-id="a3c63-119">If you only perform remoting with HoloLens (1st Gen), skip to [Connecting to the HoloLens with Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span></span>

<span data-ttu-id="a3c63-120">Quando si usa HoloLens 2, è stato aggiunto il supporto per i dati di rilevamento a mano e a occhio articolato per la comunicazione remota in MRTK.</span><span class="sxs-lookup"><span data-stu-id="a3c63-120">When using a HoloLens 2, support for remoting articulated hand and eye tracking data has been added to MRTK.</span></span> <span data-ttu-id="a3c63-121">Per abilitare queste funzionalità, seguire i passaggi descritti in [importare DotNetWinRT nel progetto](#import-dotnetwinrt-into-the-project).</span><span class="sxs-lookup"><span data-stu-id="a3c63-121">To enable these features, please follow the steps documented in [Import DotNetWinRT into the project](#import-dotnetwinrt-into-the-project).</span></span>

<span data-ttu-id="a3c63-122">Una volta importato, il passaggio successivo consiste nel selezionare le utilità del **Toolkit di realtà misto**  >    >  Windows configurazione controllo della **realtà mista**  >  .</span><span class="sxs-lookup"><span data-stu-id="a3c63-122">Once imported, the next step is to select **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration**.</span></span> <span data-ttu-id="a3c63-123">Questo passaggio aggiunge una definizione di script che Abilita la dipendenza DotNetWinRT.</span><span class="sxs-lookup"><span data-stu-id="a3c63-123">This step adds a scripting define that enables the DotNetWinRT dependency.</span></span>

> [!NOTE]
> <span data-ttu-id="a3c63-124">Quando si usa Unity 2019,4 e versioni successive, non è necessario eseguire l'utilità check Configuration.</span><span class="sxs-lookup"><span data-stu-id="a3c63-124">When using Unity 2019.4 and newer, it is not necessary to run the Check Configuration utility.</span></span>

<span data-ttu-id="a3c63-125">Per abilitare il rilevamento dei giunti della mano e del rilevamento degli occhi, seguire i passaggi descritti nell' **importazione di servizi remoti HoloLens 2 tramite l'importazione dei pacchetti Unity** e le sezioni correlate.</span><span class="sxs-lookup"><span data-stu-id="a3c63-125">To enable tracking of hand joints and eye tracking, follow the steps in the **Debugging HoloLens 2 remoting via Unity package import** and related sections.</span></span>

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a><span data-ttu-id="a3c63-126">Debug di HoloLens 2 Remoting tramite l'importazione di pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="a3c63-126">Debugging HoloLens 2 remoting via Unity package import</span></span>

<span data-ttu-id="a3c63-127">Se HoloLens 2 e la verifica degli occhi non funzionano sulla comunicazione remota, esistono alcuni punti comuni di potenziali problemi.</span><span class="sxs-lookup"><span data-stu-id="a3c63-127">If HoloLens 2 hand joints and eye tracking aren't working over remoting, there are a few common points of potential issues.</span></span> <span data-ttu-id="a3c63-128">Questi elementi sono elencati di seguito nell'ordine in cui devono essere controllati.</span><span class="sxs-lookup"><span data-stu-id="a3c63-128">They're listed below in the order they should be checked.</span></span>

<span data-ttu-id="a3c63-129">Questi problemi sono particolarmente rilevanti quando vengono eseguiti in **unity 2019,3** o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="a3c63-129">These issues are particularly relevant when running on **Unity 2019.3** or later.</span></span>

#### <a name="import-dotnetwinrt-into-the-project"></a><span data-ttu-id="a3c63-130">Importa DotNetWinRT nel progetto</span><span class="sxs-lookup"><span data-stu-id="a3c63-130">Import DotNetWinRT into the project</span></span>

1. <span data-ttu-id="a3c63-131">Scaricare lo [strumento per la funzionalità di realtà mista](https://aka.ms/MRFeatureTool)</span><span class="sxs-lookup"><span data-stu-id="a3c63-131">Download the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool)</span></span>

1. <span data-ttu-id="a3c63-132">Nella visualizzazione **funzionalità di individuazione** selezionare *proiezioni WinRT realtà mista*</span><span class="sxs-lookup"><span data-stu-id="a3c63-132">In the **Discover features** view, select *Mixed Reality WinRT Projections*</span></span>

    ![Selezionare il pacchetto DotNetWinRT](../images/tools/remoting/SelectDotNetWinRT.png)

1. <span data-ttu-id="a3c63-134">Fare clic su **Ottieni funzionalità** e continuare a [importare il pacchetto](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span><span class="sxs-lookup"><span data-stu-id="a3c63-134">Click **Get Features** and continue to [import the package](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span></span>

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a><span data-ttu-id="a3c63-135">DOTNETWINRT_PRESENT definire scritte in Impostazioni lettore</span><span class="sxs-lookup"><span data-stu-id="a3c63-135">DOTNETWINRT_PRESENT define written into player settings</span></span>

> [!NOTE]
> <span data-ttu-id="a3c63-136">Quando si usa Unity 2019,4 e versioni successive, la DOTNETWINRT_PRESENT define è contenuta nei file. asmdef appropriati e non nelle impostazioni del lettore Unity.</span><span class="sxs-lookup"><span data-stu-id="a3c63-136">When using Unity 2019.4 and newer, the DOTNETWINRT_PRESENT define is contained within the appropriate .asmdef files and not the Unity Player Settings.</span></span> <span data-ttu-id="a3c63-137">Il passaggio controlla configurazione non è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="a3c63-137">The Check Configuration step is not required.</span></span>

<span data-ttu-id="a3c63-138">A partire da MRTK versione 2.5.0, per motivi di prestazioni, questo #define non viene più impostato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a3c63-138">Beginning with MRTK version 2.5.0, for performance reasons, this #define is no longer automatically set.</span></span> <span data-ttu-id="a3c63-139">Per abilitare questo flag, usare la voce di menu configurazione di Microsoft Mixed **reality Toolkit**  >  **Utilities**  >    >   .</span><span class="sxs-lookup"><span data-stu-id="a3c63-139">To enable this flag, please use the **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration** menu item.</span></span>

> [!Note]
> <span data-ttu-id="a3c63-140">L'elemento di configurazione check non visualizza una conferma.</span><span class="sxs-lookup"><span data-stu-id="a3c63-140">The Check Configuration item does not display a confirmation.</span></span> <span data-ttu-id="a3c63-141">Per confermare che la definizione è stata impostata, passare alle impostazioni del lettore Unity.</span><span class="sxs-lookup"><span data-stu-id="a3c63-141">To confirm that the define has been set, please navigate to the Unity Player Settings.</span></span> <span data-ttu-id="a3c63-142">Da qui, nella scheda UWP, controllare le altre impostazioni per i simboli di definizione dello scripting.</span><span class="sxs-lookup"><span data-stu-id="a3c63-142">From there, under the UWP tab, check under Other Settings for the Scripting Define Symbols.</span></span> <span data-ttu-id="a3c63-143">Assicurarsi che DOTNETWINRT_PRESENT sia scritto correttamente in tale elenco.</span><span class="sxs-lookup"><span data-stu-id="a3c63-143">Make sure DOTNETWINRT_PRESENT is properly written in that list.</span></span> <span data-ttu-id="a3c63-144">Questa operazione è stata completata.</span><span class="sxs-lookup"><span data-stu-id="a3c63-144">If that's there, this step succeeded.</span></span>

![DotNetWinRT presente](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a><span data-ttu-id="a3c63-146">Rimozione del supporto per servizi remoti specifici di HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a3c63-146">Removing HoloLens 2-specific remoting support</span></span>

<span data-ttu-id="a3c63-147">Se si verificano conflitti o altri problemi causati dalla presenza dell'adattatore DotNetWinRT, contattare [una delle risorse della Guida](../../welcome-to-mrtk.md#getting-help).</span><span class="sxs-lookup"><span data-stu-id="a3c63-147">If you're running into conflicts or other issues due to the presence of the DotNetWinRT adapter, please [reach out on one of our help resources](../../welcome-to-mrtk.md#getting-help).</span></span>

## <a name="xr-sdk-setup-instructions"></a><span data-ttu-id="a3c63-148">Istruzioni di installazione di XR SDK</span><span class="sxs-lookup"><span data-stu-id="a3c63-148">XR SDK setup instructions</span></span>

<span data-ttu-id="a3c63-149">Seguire le [istruzioni di configurazione della realtà mista di Windows nella pagina Introduzione a MRTK e XR SDK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) e assicurarsi di eseguire il passaggio necessario per la comunicazione remota HoloLens in-Editor.</span><span class="sxs-lookup"><span data-stu-id="a3c63-149">Follow the [Windows Mixed Reality setup instructions on the Getting started with MRTK and XR SDK page](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) and make sure to perform the step required for in-editor HoloLens Remoting.</span></span>

## <a name="connecting-to-the-hololens-with-wi-fi"></a><span data-ttu-id="a3c63-150">Connessione a HoloLens con Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="a3c63-150">Connecting to the HoloLens with Wi-Fi</span></span>

<span data-ttu-id="a3c63-151">Una volta configurato il progetto, è possibile stabilire una connessione a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a3c63-151">Once the project has been configured, a connection can be established to the HoloLens.</span></span>

1. <span data-ttu-id="a3c63-152">In **File > impostazioni di compilazione** assicurarsi che il tipo di compilazione del progetto sia impostato su **piattaforma UWP (Universal Windows Platform)**</span><span class="sxs-lookup"><span data-stu-id="a3c63-152">In **File > Build Settings**, ensure that the project build type is set to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="a3c63-153">In HoloLens avviare l'applicazione di **comunicazione remota olografica** .</span><span class="sxs-lookup"><span data-stu-id="a3c63-153">On the HoloLens, launch the **Holographic Remoting** application.</span></span>
1. <span data-ttu-id="a3c63-154">In Unity selezionare la **finestra > XR > emulazione olografica (se si usa il plug-in Legacy XR)/Windows XR plug-in (se si usa XR SDK)**.</span><span class="sxs-lookup"><span data-stu-id="a3c63-154">In Unity, select **Window > XR > Holographic Emulation (if using legacy XR) / Windows XR Plugin Remoting (if using XR SDK)**.</span></span>

    ![Avviare l'emulazione olografica](../images/tools/remoting/StartHolographicEmulation.png)

1. <span data-ttu-id="a3c63-156">Impostare la **modalità di emulazione** su da **remoto a dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="a3c63-156">Set **Emulation Mode** to **Remote to Device**.</span></span>

    ![Impostare la modalità di emulazione](../images/tools/remoting/SelectEmulationMode.png)

1. <span data-ttu-id="a3c63-158">(**_Si applica solo a una versione precedente di XR_**) Selezionare la **versione del dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="a3c63-158">(**_Only applies to legacy XR_**) Select the **Device Version**.</span></span>

    ![Selezionare la versione del dispositivo](../images/tools/remoting/SelectDeviceVersion.png)

1. <span data-ttu-id="a3c63-160">Usando l'indirizzo IP visualizzato dall'applicazione del lettore di comunicazione remota olografico, impostare il campo **computer remoto** .</span><span class="sxs-lookup"><span data-stu-id="a3c63-160">Using the IP Address displayed by the Holographic Remoting Player application, set the **Remote Machine** field.</span></span>

    ![Immettere l'indirizzo IP](../images/tools/remoting/EnterIPAddress.png)

1. <span data-ttu-id="a3c63-162">Fare clic su **Connect** (Connetti).</span><span class="sxs-lookup"><span data-stu-id="a3c63-162">Click **Connect**.</span></span>

> [!NOTE]
> <span data-ttu-id="a3c63-163">Se non è possibile connettersi, assicurarsi che HoloLens 2 non sia collegato al PC e riavviare Unity.</span><span class="sxs-lookup"><span data-stu-id="a3c63-163">If you cannot connect, make sure your HoloLens 2 is not plugged in to your PC and restart Unity.</span></span>

## <a name="connecting-to-the-hololens-with-usb-cable"></a><span data-ttu-id="a3c63-164">Connessione a HoloLens con cavo USB</span><span class="sxs-lookup"><span data-stu-id="a3c63-164">Connecting to the HoloLens with USB cable</span></span>

<span data-ttu-id="a3c63-165">La connessione via cavo USB garantisce maggiore qualità e stabilità di rendering.</span><span class="sxs-lookup"><span data-stu-id="a3c63-165">USB cable connection gives better rendering quality and stability.</span></span> <span data-ttu-id="a3c63-166">Per usare la connessione via cavo USB, disconnettersi da HoloLens da Wi-Fi nelle impostazioni di HoloLens e avviare l'app lettore remoto olografico.</span><span class="sxs-lookup"><span data-stu-id="a3c63-166">To use USB cable connection, disconnect from the HoloLens from Wi-Fi in HoloLens's Settings and launch Holographic Remoting Player app.</span></span> <span data-ttu-id="a3c63-167">Verrà visualizzato un indirizzo IP che inizia con 169.</span><span class="sxs-lookup"><span data-stu-id="a3c63-167">It will display an IP address that starts with 169.</span></span> <span data-ttu-id="a3c63-168">Usare questo indirizzo IP nell'impostazione di emulazione olografica di Unity per connettersi.</span><span class="sxs-lookup"><span data-stu-id="a3c63-168">Use this IP address in Unity's Holographic Emulation setting to connect.</span></span> <span data-ttu-id="a3c63-169">Quando l'indirizzo IP per il cavo USB è stato identificato, è possibile connettere il HoloLens a Wi-Fi nuovamente.</span><span class="sxs-lookup"><span data-stu-id="a3c63-169">Once the IP address for USB cable has been identified, it is safe to connect the HoloLens to Wi-Fi again.</span></span>

## <a name="starting-a-remoting-session"></a><span data-ttu-id="a3c63-170">Avvio di una sessione remota</span><span class="sxs-lookup"><span data-stu-id="a3c63-170">Starting a remoting session</span></span>

<span data-ttu-id="a3c63-171">Con Unity connected to the HoloLens, immettere Play Mode nell'editor.</span><span class="sxs-lookup"><span data-stu-id="a3c63-171">With Unity connected to the HoloLens, enter play mode in the editor.</span></span>

<span data-ttu-id="a3c63-172">Al termine della sessione, uscire dalla modalità di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="a3c63-172">When the session is complete, exit play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="a3c63-173">Si è verificato un problema noto con alcune versioni di Unity in cui l'editor potrebbe bloccarsi dopo l'immissione della modalità di riproduzione durante una sessione remota.</span><span class="sxs-lookup"><span data-stu-id="a3c63-173">There is a known issue with some versions of Unity where the editor may hang upon entering play mode during a remoting session.</span></span> <span data-ttu-id="a3c63-174">Questo problema può manifestarsi se la finestra olografica è aperta quando il progetto viene caricato.</span><span class="sxs-lookup"><span data-stu-id="a3c63-174">This issue may manifest if the Holographic window is open when the project is loaded.</span></span> <span data-ttu-id="a3c63-175">Per evitare che il problema si verifichi, chiudere sempre la finestra di dialogo olografica prima di uscire da Unity.</span><span class="sxs-lookup"><span data-stu-id="a3c63-175">To ensure this issue does not occur, always close the Holographic dialog prior to exiting Unity.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3c63-176">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="a3c63-176">See also</span></span>

- [<span data-ttu-id="a3c63-177">Limitazioni e risoluzione dei problemi di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="a3c63-177">Holographic Remoting troubleshooting and limitations</span></span>](https://docs.microsoft.com/windows/mixed-reality/holographic-remoting-troubleshooting)
- [<span data-ttu-id="a3c63-178">Condizioni di licenza del software Microsoft olografico Remoting</span><span class="sxs-lookup"><span data-stu-id="a3c63-178">Microsoft Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
