---
title: HolographicRemoting
description: Documentazione di comunicazione remota olografica MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: f8631db428464c1381d4940a71908c45a6d4ad9d
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783256"
---
# <a name="holographic-remoting"></a><span data-ttu-id="862ad-104">Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="862ad-104">Holographic Remoting</span></span>

<span data-ttu-id="862ad-105">La comunicazione remota olografica trasmette contenuto olografico da un PC a Microsoft HoloLens in tempo reale, usando una connessione via cavo Wi-Fi o USB.</span><span class="sxs-lookup"><span data-stu-id="862ad-105">Holographic remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi or USB cable connection.</span></span> <span data-ttu-id="862ad-106">Questa funzionalità può aumentare significativamente la produttività degli sviluppatori quando si sviluppano applicazioni di realtà miste.</span><span class="sxs-lookup"><span data-stu-id="862ad-106">This feature can significantly increase developer productivity when developing mixed reality applications.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="862ad-107">Configurazione iniziale</span><span class="sxs-lookup"><span data-stu-id="862ad-107">Initial setup</span></span>

<span data-ttu-id="862ad-108">Per abilitare la comunicazione remota a una HoloLens, è importante assicurarsi che il progetto usi i componenti .NET Remoting più recenti.</span><span class="sxs-lookup"><span data-stu-id="862ad-108">To enable remoting to a HoloLens, it is important to ensure that the project is using the latest remoting components.</span></span>

1. <span data-ttu-id="862ad-109">Apri **finestra > gestione pacchetti**</span><span class="sxs-lookup"><span data-stu-id="862ad-109">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="862ad-110">Verificare che sia installata la versione più recente del pacchetto di **realtà mista di Windows** .</span><span class="sxs-lookup"><span data-stu-id="862ad-110">Verify that latest version of the **Windows Mixed Reality** package is installed.</span></span>
1. <span data-ttu-id="862ad-111">Verificare che nell'HoloLens sia installata la versione più recente dell'applicazione di comunicazione remota olografica tramite il Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="862ad-111">Ensure the latest Holographic Remoting application is installed, on the HoloLens, via the Microsoft Store.</span></span>

### <a name="hololens-2"></a><span data-ttu-id="862ad-112">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="862ad-112">HoloLens 2</span></span>

<span data-ttu-id="862ad-113">Quando si usa HoloLens 2, è stato aggiunto il supporto per i dati di rilevamento a mano e a occhio articolato per la comunicazione remota in MRTK.</span><span class="sxs-lookup"><span data-stu-id="862ad-113">When using a HoloLens 2, support for remoting articulated hand and eye tracking data has been added to MRTK.</span></span> <span data-ttu-id="862ad-114">Per abilitare queste funzionalità, configurare il progetto seguendo questa procedura.</span><span class="sxs-lookup"><span data-stu-id="862ad-114">To enable these features, configure the project using the following steps.</span></span>

1. <span data-ttu-id="862ad-115">Eseguire l'utilità MRTK Configurator (**mixed reality Toolkit > Utilities > configurare il progetto Unity**)</span><span class="sxs-lookup"><span data-stu-id="862ad-115">Run the MRTK Configurator Utility (**Mixed Reality Toolkit > Utilities > Configure Unity Project**)</span></span>
1. <span data-ttu-id="862ad-116">Espandi **modifiche configurazioni**</span><span class="sxs-lookup"><span data-stu-id="862ad-116">Expand **Modify Configurations**</span></span>

    ![MRTK Configurator](../Images/Tools/Remoting/EnableMSBuildForUnity.png)

1. <span data-ttu-id="862ad-118">Assicurarsi che sia selezionata l'opzione **Abilita MSBuild per Unity**</span><span class="sxs-lookup"><span data-stu-id="862ad-118">Ensure that **Enable MSBuild for Unity** is selected</span></span>
1. <span data-ttu-id="862ad-119">Fare clic su **Applica**.</span><span class="sxs-lookup"><span data-stu-id="862ad-119">Click **Apply**</span></span>

<span data-ttu-id="862ad-120">Quando si usa **unity 2019,3** e versioni successive, l' **Abilitazione di MSBuild per Unity** non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="862ad-120">When using **Unity 2019.3** and later the **Enable MSBuild for Unity** is not available.</span></span> <span data-ttu-id="862ad-121">per abilitare la comunicazione remota olografica, attenersi alle procedure riportate di seguito.</span><span class="sxs-lookup"><span data-stu-id="862ad-121">please follow the below procedures to enable holographic remoting.</span></span>

1. <span data-ttu-id="862ad-122">Eseguire l'utilità MRTK Configurator (**mixed reality Toolkit > Utilities > configurare il progetto Unity**)</span><span class="sxs-lookup"><span data-stu-id="862ad-122">Run the MRTK Configurator Utility (**Mixed Reality Toolkit > Utilities > Configure Unity Project**)</span></span>
1. <span data-ttu-id="862ad-123">Impostare la piattaforma di destinazione in **File > impostazioni di compilazione** su **piattaforma UWP (Universal Windows Platform)**</span><span class="sxs-lookup"><span data-stu-id="862ad-123">Set the target platform in **File > Build Settings** to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="862ad-124">Fare clic su **Applica**.</span><span class="sxs-lookup"><span data-stu-id="862ad-124">Click **Apply**</span></span>
1. <span data-ttu-id="862ad-125">Apri **finestra > gestione pacchetti**</span><span class="sxs-lookup"><span data-stu-id="862ad-125">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="862ad-126">Verificare che il **plug-in Windows XR** non sia installato se il progetto non usa [XR SDK](../../configuration/GettingStartedWithMRTKAndXRSDK.md), perché il pacchetto di **realtà mista di Windows** legacy non funzionerà insieme a esso.</span><span class="sxs-lookup"><span data-stu-id="862ad-126">Ensure that the **Windows XR Plugin** is not installed if the project isn't using [XR SDK](../../configuration/GettingStartedWithMRTKAndXRSDK.md), as the legacy **Windows Mixed Reality** package will not function alongside it</span></span>
1. <span data-ttu-id="862ad-127">Apri **Impostazioni progetto modifica > > lettore**</span><span class="sxs-lookup"><span data-stu-id="862ad-127">Open **Edit > Project Settings > Player**</span></span>

    ![SDK di realtà mista di Windows](../Images/Tools/Remoting/WindowsMixedRealitySDK.png)

1. <span data-ttu-id="862ad-129">Verificare che sia selezionata l'opzione **realtà virtuale supportata** e che la **realtà mista di Windows** venga aggiunta agli **SDK di realtà virtuale**</span><span class="sxs-lookup"><span data-stu-id="862ad-129">Ensure that **Virtual Reality Supported** is selected and that **Windows Mixed Reality** is added to the **Virtual Reality SDKs**</span></span>

<span data-ttu-id="862ad-130">Per abilitare il rilevamento dei giunti della mano e del rilevamento degli occhi, seguire i passaggi descritti nell' **importazione di servizi remoti HoloLens 2 tramite l'importazione dei pacchetti Unity** e le sezioni correlate.</span><span class="sxs-lookup"><span data-stu-id="862ad-130">To enable tracking of hand joints and eye tracking, follow the steps in the **Debugging HoloLens 2 remoting via Unity package import** and related sections.</span></span>

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a><span data-ttu-id="862ad-131">Debug di HoloLens 2 Remoting tramite l'importazione di pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="862ad-131">Debugging HoloLens 2 remoting via Unity package import</span></span>

<span data-ttu-id="862ad-132">Se HoloLens 2 e la verifica degli occhi non funzionano sulla comunicazione remota, esistono alcuni punti comuni di potenziali problemi.</span><span class="sxs-lookup"><span data-stu-id="862ad-132">If HoloLens 2 hand joints and eye tracking aren't working over remoting, there are a few common points of potential issues.</span></span> <span data-ttu-id="862ad-133">Questi elementi sono elencati di seguito nell'ordine in cui devono essere controllati.</span><span class="sxs-lookup"><span data-stu-id="862ad-133">They're listed below in the order they should be checked.</span></span>

<span data-ttu-id="862ad-134">Questi problemi sono particolarmente rilevanti quando vengono eseguiti in **unity 2019,3** o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="862ad-134">These issues are particularly relevant when running on **Unity 2019.3** or later.</span></span>

#### <a name="msbuildforunity-package-import-via-writing-into-the-packagemanifest"></a><span data-ttu-id="862ad-135">Importazione del pacchetto MSBuildForUnity tramite la scrittura nel file Package. manifest</span><span class="sxs-lookup"><span data-stu-id="862ad-135">MSBuildForUnity package import via writing into the package.manifest</span></span>

> [!Note]
> <span data-ttu-id="862ad-136">Si è verificato un problema noto che impedisce a MSBuild per Unity di funzionare correttamente in alcune versioni di Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="862ad-136">There is a known issue that prevents MSBuild for Unity from functioning properly on some versions of Unity 2019.</span></span> <span data-ttu-id="862ad-137">Per evitare questo problema, MRTK non supporta MSBuild per Unity in Unity 2019,3.</span><span class="sxs-lookup"><span data-stu-id="862ad-137">To avoid this issue, the MRTK does not support MSBuild for Unity on Unity 2019.3.</span></span>
>
> <span data-ttu-id="862ad-138">Per acquisire il pacchetto NuGet necessario quando si esegue in Unity 2019,3, vedere le [istruzioni di installazione manuale](#manual-dotnetadapter-installation).</span><span class="sxs-lookup"><span data-stu-id="862ad-138">To acquire the required NuGet package when running on Unity 2019.3, please refer to the [manual installation instructions](#manual-dotnetadapter-installation).</span></span>

<span data-ttu-id="862ad-139">Il modo migliore per verificare è aprire Gestione pacchetti > finestra e assicurarsi che MSBuild per Unity venga visualizzato nell'elenco dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="862ad-139">The best way to check is to open Window -> Package Manager and make sure MSBuild for Unity shows up in the packages list.</span></span> <span data-ttu-id="862ad-140">Se è presente, si supponga che questo passaggio sia riuscito.</span><span class="sxs-lookup"><span data-stu-id="862ad-140">If it's there, assume this step succeeded.</span></span> <span data-ttu-id="862ad-141">Se non è presente, provare a eseguire il Toolkit di realtà mista-> Utilities-> configurare Unity e ripetere i passaggi precedenti per l'esecuzione di MRTK Configurator.</span><span class="sxs-lookup"><span data-stu-id="862ad-141">If it's not there, try running Mixed Reality Toolkit -> Utilities -> Configure Unity and repeat the steps above for running the MRTK Configurator.</span></span>

![Gestione pacchetti MSB4U](../Images/Tools/Remoting/MSB4UPackageManager.png)

#### <a name="dotnetwinrt-nuget-package-resolution"></a><span data-ttu-id="862ad-143">Risoluzione del pacchetto NuGet DotNetWinRT</span><span class="sxs-lookup"><span data-stu-id="862ad-143">DotNetWinRT NuGet package resolution</span></span>

<span data-ttu-id="862ad-144">Il modo migliore per verificare la ricerca consiste nel cercare DotNetWinRT.dll nella cartella assets.</span><span class="sxs-lookup"><span data-stu-id="862ad-144">The best way to check is to search the Assets folder for DotNetWinRT.dll.</span></span> <span data-ttu-id="862ad-145">Se il problema persiste, passare alla cartella Asset nella visualizzazione del progetto e selezionare `[ProjectName].Dependencies.msb4u.csproj` .</span><span class="sxs-lookup"><span data-stu-id="862ad-145">If this doesn't exist, navigate to the Assets folder in the Project view and select `[ProjectName].Dependencies.msb4u.csproj`.</span></span> <span data-ttu-id="862ad-146">Supponendo che la parte 1 abbia avuto esito positivo, deve essere presente un controllo personalizzato con pulsanti Compila, ricompila e Pulisci.</span><span class="sxs-lookup"><span data-stu-id="862ad-146">Assuming part 1 did succeed, there should be a custom inspector with Build, Rebuild, and Clean buttons.</span></span> <span data-ttu-id="862ad-147">Provare a fare clic su Compila o Ricompila, quindi eseguire di nuovo la ricerca DotNetWinRT.dll.</span><span class="sxs-lookup"><span data-stu-id="862ad-147">Try clicking Build or Rebuild, and then re-search for DotNetWinRT.dll.</span></span> <span data-ttu-id="862ad-148">Se la DLL esiste ora, il passaggio è riuscito.</span><span class="sxs-lookup"><span data-stu-id="862ad-148">If that DLL now exists, this step succeeded.</span></span>

![Controllo DotNetAdapter](../Images/Tools/Remoting/DotNetAdapterInspector.png)

#### <a name="dotnetadaptercsproj-missing"></a><span data-ttu-id="862ad-150">DotNetAdapter. csproj mancante</span><span class="sxs-lookup"><span data-stu-id="862ad-150">DotNetAdapter.csproj missing</span></span>

<span data-ttu-id="862ad-151">Se il passaggio precedente non riesce, è opportuno verificare che nel progetto sia presente il csproj appropriato.</span><span class="sxs-lookup"><span data-stu-id="862ad-151">If the previous step didn't succeed, it's good to double check that the appropriate csproj exists in your project.</span></span> <span data-ttu-id="862ad-152">Controllare in MRTK/Providers/WindowsMixedReality/Shared/DotNetAdapter e verificare che sia presente DotNetAdapter. csproj.</span><span class="sxs-lookup"><span data-stu-id="862ad-152">Check under MRTK / Providers / WindowsMixedReality / Shared / DotNetAdapter and check that DotNetAdapter.csproj exists.</span></span> <span data-ttu-id="862ad-153">Un caso comune in cui questo file potrebbe non esistere è se il file con estensione gitignore ignora i file csproj ed è stato eseguito il commit dei file MRTK in un repository remoto.</span><span class="sxs-lookup"><span data-stu-id="862ad-153">One common case where this file might not exist is if your .gitignore ignores csproj files and you've committed the MRTK files to a remote repo.</span></span> <span data-ttu-id="862ad-154">In tal caso, assicurarsi di forzare l'aggiunta di DotNetAdapter. csproj con `git add -f [path/to]/DotNetAdapter.csproj` per assicurarsi che venga eseguito il commit e la clonazione per tutti gli altri collaboratori o computer.</span><span class="sxs-lookup"><span data-stu-id="862ad-154">In this case, please make sure you force add DotNetAdapter.csproj with `git add -f [path/to]/DotNetAdapter.csproj` to make sure it gets committed and cloned for all other collaborators or computers.</span></span>

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a><span data-ttu-id="862ad-155">`DOTNETWINRT_PRESENT` #define scritte in Impostazioni lettore</span><span class="sxs-lookup"><span data-stu-id="862ad-155">`DOTNETWINRT_PRESENT` #define written into player settings</span></span>

<span data-ttu-id="862ad-156">Passare alle impostazioni del lettore Unity.</span><span class="sxs-lookup"><span data-stu-id="862ad-156">Navigate to the Unity Player Settings.</span></span> <span data-ttu-id="862ad-157">Da qui, nella scheda UWP, controllare le altre impostazioni per i simboli di definizione dello scripting.</span><span class="sxs-lookup"><span data-stu-id="862ad-157">From there, under the UWP tab, check under Other Settings for the Scripting Define Symbols.</span></span> <span data-ttu-id="862ad-158">Assicurarsi che DOTNETWINRT_PRESENT sia scritto correttamente in tale elenco.</span><span class="sxs-lookup"><span data-stu-id="862ad-158">Make sure DOTNETWINRT_PRESENT is properly written in that list.</span></span> <span data-ttu-id="862ad-159">Questa operazione è stata completata.</span><span class="sxs-lookup"><span data-stu-id="862ad-159">If that's there, this step succeeded.</span></span>

![DotNetWinRT presente](../Images/Tools/Remoting/DotNetWinRTPresent.png)

#### <a name="failure-to-find-dotnetexe"></a><span data-ttu-id="862ad-161">Impossibile trovare dotnet.exe</span><span class="sxs-lookup"><span data-stu-id="862ad-161">Failure to find dotnet.exe</span></span>

<span data-ttu-id="862ad-162">MSBuild per Unity dipende da dotnet.exe esistente nel percorso di sistema. dotnet.exe devono essere installati e presenti nella variabile di ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="862ad-162">MSBuild for Unity depends on dotnet.exe existing in the system path - dotnet.exe must both be installed and present in the PATH environment variable.</span></span> <span data-ttu-id="862ad-163">Se nessuno di questi requisiti è true, questo errore può essere manifesto nella console di Unity:</span><span class="sxs-lookup"><span data-stu-id="862ad-163">If neither of those requirements are true, this error may manifest in the Unity console:</span></span>

```cmd
Win32Exception: ApplicationName='dotnet', CommandLine='msbuild DotNetAdapter.csproj -restore  -v:minimal -p:NuGetInteractive=true  -t:Build -p:Configuration=Release -nologo', CurrentDirectory='C:\src\Assets\MRTK\Providers\WindowsMixedReality\Shared\DotNetAdapter', Native error= The system cannot find the file specified.
```

<span data-ttu-id="862ad-164">La soluzione consiste nel verificare che gli strumenti di [interfaccia della riga di comando di .NET Core siano installati](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x) e riavviare il sistema per forzare l'esecuzione di un percorso di sistema aggiornato per tutte le app.</span><span class="sxs-lookup"><span data-stu-id="862ad-164">The solution to this is to ensure that the [.NET Core CLI tools are installed](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x) and reboot the system to force all apps to get a refreshed system path.</span></span>

<span data-ttu-id="862ad-165">Se le giunzioni di mano sulla comunicazione remota continuano a non funzionare dopo aver eseguito i passaggi precedenti, potrebbe essersi verificato un problema di configurazione nei profili per le giunzioni di mano generale sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="862ad-165">If hand joints over remoting are still not working after following the above steps, there might be something misconfigured in the profiles for general hand joints on-device.</span></span> <span data-ttu-id="862ad-166">In tal caso, contattare [una delle risorse della Guida](../../WelcomeToMRTK.md#getting-help).</span><span class="sxs-lookup"><span data-stu-id="862ad-166">In that case, please [reach out on one of our help resources](../../WelcomeToMRTK.md#getting-help).</span></span>

#### <a name="manual-dotnetadapter-installation"></a><span data-ttu-id="862ad-167">Installazione manuale di DotNetAdapter</span><span class="sxs-lookup"><span data-stu-id="862ad-167">Manual DotNetAdapter installation</span></span>

<span data-ttu-id="862ad-168">Nel caso in cui l'installazione di DotNetAdapter non possa essere eseguita tramite MSBuild per Unity, è possibile eseguire i passaggi seguenti.</span><span class="sxs-lookup"><span data-stu-id="862ad-168">In the event that the installation of the DotNetAdapter cannot be performed via MSBuild for Unity, the following steps can be performed.</span></span>

> [!Important]
> <span data-ttu-id="862ad-169">L'uso di MSBuild per Unity e di un altro client NuGet nello stesso progetto non è supportato e può causare potenziali problemi di risoluzione delle dipendenze.</span><span class="sxs-lookup"><span data-stu-id="862ad-169">Using both MSBuild for Unity and another NuGet client within the same project is not supported and can result in potential dependency resolution issues.</span></span>

1. <span data-ttu-id="862ad-170">Installare un client NuGet</span><span class="sxs-lookup"><span data-stu-id="862ad-170">Install a NuGet client</span></span>

    > [!Note]
    > <span data-ttu-id="862ad-171">Le istruzioni seguenti presuppongono l'uso di [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases)</span><span class="sxs-lookup"><span data-stu-id="862ad-171">The following instructions presume use of [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases)</span></span>

1. <span data-ttu-id="862ad-172">Passare all'interfaccia utente del client NuGet</span><span class="sxs-lookup"><span data-stu-id="862ad-172">Navigate to the NuGet client UI</span></span>

    ![Avviare l'interfaccia utente di NuGet](../Images/Tools/Remoting/LaunchNuGetForUnity.png)

1. <span data-ttu-id="862ad-174">Individuare il `Microsoft.Windows.MixedReality.DotNetWinRT` pacchetto</span><span class="sxs-lookup"><span data-stu-id="862ad-174">Locate the `Microsoft.Windows.MixedReality.DotNetWinRT` package</span></span>

    ![Individua pacchetto](../Images/Tools/Remoting/LocateDotNetWinRT.png)

1. <span data-ttu-id="862ad-176">Selezionare Installa</span><span class="sxs-lookup"><span data-stu-id="862ad-176">Select Install</span></span>

### <a name="removing-hololens-2-specific-remoting-support"></a><span data-ttu-id="862ad-177">Rimozione del supporto per servizi remoti specifici di HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="862ad-177">Removing HoloLens 2-specific remoting support</span></span>

<span data-ttu-id="862ad-178">Se si verificano conflitti o altri problemi causati dalla presenza dell'adattatore DotNetWinRT, contattare [una delle risorse della Guida](../../WelcomeToMRTK.md#getting-help).</span><span class="sxs-lookup"><span data-stu-id="862ad-178">If you're running into conflicts or other issues due to the presence of the DotNetWinRT adapter, please [reach out on one of our help resources](../../WelcomeToMRTK.md#getting-help).</span></span>

<span data-ttu-id="862ad-179">È anche possibile rimuovere temporaneamente l'adapter per aggirare il problema tramite i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="862ad-179">You can also temporarily remove the adapter to workaround your issue via the following steps:</span></span>

1. <span data-ttu-id="862ad-180">In Unity passare a Window-> Package Manager e disinstallare MSBuild for Unity.</span><span class="sxs-lookup"><span data-stu-id="862ad-180">In Unity, go to Window -> Package Manager and uninstall MSBuild for Unity.</span></span>
1. <span data-ttu-id="862ad-181">Cercare DotNetWinRT.dll nell'elenco asset in Unity ed eliminare la DLL o eliminare i plug-in (MRTK 2,2 o versioni precedenti) o le dipendenze (MRTK 2,3 o versione successiva) che contengono alcuni livelli.</span><span class="sxs-lookup"><span data-stu-id="862ad-181">Search for DotNetWinRT.dll in your assets list in Unity and either delete the DLL or delete the Plugins (MRTK 2.2 or earlier) or Dependencies (MRTK 2.3 or later) folder that contains it a few levels up.</span></span> <span data-ttu-id="862ad-182">Questo dovrebbe rimuovere questi spazi dei nomi in conflitto, mantenendo MRTK.</span><span class="sxs-lookup"><span data-stu-id="862ad-182">That should remove these conflicting namespaces, while keeping MRTK around.</span></span>
1. <span data-ttu-id="862ad-183">Opzionale Passare a MRTK/Providers/WindowsMixedReality/Shared/DotNetAdapter in Esplora file (non la visualizzazione asset di Unity) ed eliminare le `.bin` `.obj` cartelle e.</span><span class="sxs-lookup"><span data-stu-id="862ad-183">(Optional) Navigate to MRTK / Providers / WindowsMixedReality / Shared / DotNetAdapter in your file explorer (not Unity's Assets view) and delete the `.bin` and `.obj` folders.</span></span> <span data-ttu-id="862ad-184">In questo modo viene rimossa la cache locale dei pacchetti NuGet ripristinati per DotNetWinRT.</span><span class="sxs-lookup"><span data-stu-id="862ad-184">This removes the local cache of NuGet restored packages for DotNetWinRT.</span></span>
1. <span data-ttu-id="862ad-185">Se si esegue di nuovo lo strumento di configurazione di MRTK, assicurarsi di non abilitare di nuovo MSBuild per Unity.</span><span class="sxs-lookup"><span data-stu-id="862ad-185">If you run the MRTK Configurator again, make sure you don't re-enable MSBuild for Unity.</span></span>

## <a name="connecting-to-the-hololens-with-wi-fi"></a><span data-ttu-id="862ad-186">Connessione a HoloLens con Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="862ad-186">Connecting to the HoloLens with Wi-Fi</span></span>

<span data-ttu-id="862ad-187">Una volta configurato il progetto, è possibile stabilire una connessione a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="862ad-187">Once the project has been configured, a connection can be established to the HoloLens.</span></span>

1. <span data-ttu-id="862ad-188">In **File > impostazioni di compilazione** assicurarsi che il tipo di compilazione del progetto sia impostato su **piattaforma UWP (Universal Windows Platform)**</span><span class="sxs-lookup"><span data-stu-id="862ad-188">In **File > Build Settings**, ensure that the project build type is set to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="862ad-189">In HoloLens avviare l'applicazione di **comunicazione remota olografica** .</span><span class="sxs-lookup"><span data-stu-id="862ad-189">On the HoloLens, launch the **Holographic Remoting** application.</span></span>
1. <span data-ttu-id="862ad-190">In Unity selezionare **Window > XR > emulazione olografica**.</span><span class="sxs-lookup"><span data-stu-id="862ad-190">In Unity, select **Window > XR > Holographic Emulation**.</span></span>

    ![Avviare l'emulazione olografica](../Images/Tools/Remoting/StartHolographicEmulation.png)

1. <span data-ttu-id="862ad-192">Impostare la **modalità di emulazione** su da **remoto a dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="862ad-192">Set **Emulation Mode** to **Remote to Device**.</span></span>

    ![Impostare la modalità di emulazione](../Images/Tools/Remoting/SelectEmulationMode.png)

1. <span data-ttu-id="862ad-194">Selezionare la **versione del dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="862ad-194">Select the **Device Version**.</span></span>

    ![Selezionare la versione del dispositivo](../Images/Tools/Remoting/SelectDeviceVersion.png)

1. <span data-ttu-id="862ad-196">Usando l'indirizzo IP visualizzato dall'applicazione del lettore di comunicazione remota olografico, impostare il campo **computer remoto** .</span><span class="sxs-lookup"><span data-stu-id="862ad-196">Using the IP Address displayed by the Holographic Remoting Player application, set the **Remote Machine** field.</span></span>

    ![Immettere l'indirizzo IP](../Images/Tools/Remoting/EnterIPAddress.png)

1. <span data-ttu-id="862ad-198">Fare clic su **Connect** (Connetti).</span><span class="sxs-lookup"><span data-stu-id="862ad-198">Click **Connect**.</span></span>

> [!NOTE]
> <span data-ttu-id="862ad-199">Se non è possibile connettersi, assicurarsi che HoloLens 2 non sia collegato al PC e riavviare Unity.</span><span class="sxs-lookup"><span data-stu-id="862ad-199">If you cannot connect, make sure your HoloLens 2 is not plugged in to your PC and restart Unity.</span></span>

## <a name="connecting-to-the-hololens-with-usb-cable"></a><span data-ttu-id="862ad-200">Connessione a HoloLens con cavo USB</span><span class="sxs-lookup"><span data-stu-id="862ad-200">Connecting to the HoloLens with USB cable</span></span>

<span data-ttu-id="862ad-201">La connessione via cavo USB garantisce maggiore qualità e stabilità di rendering.</span><span class="sxs-lookup"><span data-stu-id="862ad-201">USB cable connection gives better rendering quality and stability.</span></span> <span data-ttu-id="862ad-202">Per usare la connessione via cavo USB, disconnettersi da HoloLens da Wi-Fi nelle impostazioni di HoloLens e avviare l'app lettore remoto olografico.</span><span class="sxs-lookup"><span data-stu-id="862ad-202">To use USB cable connection, disconnect from the HoloLens from Wi-Fi in HoloLens's Settings and launch Holographic Remoting Player app.</span></span> <span data-ttu-id="862ad-203">Verrà visualizzato un indirizzo IP che inizia con 169.</span><span class="sxs-lookup"><span data-stu-id="862ad-203">It will display an IP address that starts with 169.</span></span> <span data-ttu-id="862ad-204">Usare questo indirizzo IP nell'impostazione di emulazione olografica di Unity per connettersi.</span><span class="sxs-lookup"><span data-stu-id="862ad-204">Use this IP address in Unity's Holographic Emulation setting to connect.</span></span> <span data-ttu-id="862ad-205">Quando l'indirizzo IP per il cavo USB è stato identificato, è possibile connettere il HoloLens a Wi-Fi nuovamente.</span><span class="sxs-lookup"><span data-stu-id="862ad-205">Once the IP address for USB cable has been identified, it is safe to connect the HoloLens to Wi-Fi again.</span></span>

## <a name="starting-a-remoting-session"></a><span data-ttu-id="862ad-206">Avvio di una sessione remota</span><span class="sxs-lookup"><span data-stu-id="862ad-206">Starting a remoting session</span></span>

<span data-ttu-id="862ad-207">Con Unity connected to the HoloLens, immettere Play Mode nell'editor.</span><span class="sxs-lookup"><span data-stu-id="862ad-207">With Unity connected to the HoloLens, enter play mode in the editor.</span></span>

<span data-ttu-id="862ad-208">Al termine della sessione, uscire dalla modalità di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="862ad-208">When the session is complete, exit play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="862ad-209">Si è verificato un problema noto con alcune versioni di Unity in cui l'editor potrebbe bloccarsi dopo l'immissione della modalità di riproduzione durante una sessione remota.</span><span class="sxs-lookup"><span data-stu-id="862ad-209">There is a known issue with some versions of Unity where the editor may hang upon entering play mode during a remoting session.</span></span> <span data-ttu-id="862ad-210">Questo problema può manifestarsi se la finestra olografica è aperta quando il progetto viene caricato.</span><span class="sxs-lookup"><span data-stu-id="862ad-210">This issue may manifest if the Holographic window is open when the project is loaded.</span></span> <span data-ttu-id="862ad-211">Per evitare che il problema si verifichi, chiudere sempre la finestra di dialogo olografica prima di uscire da Unity.</span><span class="sxs-lookup"><span data-stu-id="862ad-211">To ensure this issue does not occur, always close the Holographic dialog prior to exiting Unity.</span></span>

## <a name="see-also"></a><span data-ttu-id="862ad-212">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="862ad-212">See also</span></span>

- [<span data-ttu-id="862ad-213">Limitazioni e risoluzione dei problemi di comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="862ad-213">Holographic Remoting troubleshooting and limitations</span></span>](https://docs.microsoft.com/windows/mixed-reality/holographic-remoting-troubleshooting)
- [<span data-ttu-id="862ad-214">Condizioni di licenza del software Microsoft olografico Remoting</span><span class="sxs-lookup"><span data-stu-id="862ad-214">Microsoft Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
