---
ms.openlocfilehash: cc29a6e9d358ba35d1e1ddd336b9df88ba68739b
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/21/2021
ms.locfileid: "98689968"
---
# <a name="426"></a>[<span data-ttu-id="a9eda-101">4.26</span><span class="sxs-lookup"><span data-stu-id="a9eda-101">4.26</span></span>](#tab/426)

## <a name="the-standard-winrt-apis"></a><span data-ttu-id="a9eda-102">API WinRT standard</span><span class="sxs-lookup"><span data-stu-id="a9eda-102">The standard WinRT APIs</span></span>

<span data-ttu-id="a9eda-103">Il modo più comune e più semplice per usare WinRT consiste nel chiamare i metodi di WinSDK.</span><span class="sxs-lookup"><span data-stu-id="a9eda-103">The most common and easiest way to use WinRT is to call methods from WinSDK.</span></span> <span data-ttu-id="a9eda-104">A tale scopo, aprire il file YourModule.Build.cs e aggiungere le righe seguenti:</span><span class="sxs-lookup"><span data-stu-id="a9eda-104">To do so, open YourModule.Build.cs file and add the following lines:</span></span>

```csharp
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // These parameters are mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string[] { "shlwapi.lib", "runtimeobject.lib" });
    PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir,        
                                        "Include", 
                                        Target.WindowsPlatform.WindowsSdkVersion, 
                                        "cppwinrt"));
}
```

<span data-ttu-id="a9eda-105">Successivamente, è necessario aggiungere le intestazioni WinRT seguenti:</span><span class="sxs-lookup"><span data-stu-id="a9eda-105">Next, you need to add the following WinRT headers:</span></span> 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
//Before writing any code, you need to disable common warnings in WinRT headers
#pragma warning(disable : 5205 4265 4268 4946)

#include "Windows/AllowWindowsPlatformTypes.h"
#include "Windows/AllowWindowsPlatformAtomics.h"
#include "Windows/PreWindowsApi.h"

#include <unknwn.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Perception.Spatial.h>
#include <winrt/Windows.Foundation.Collections.h>

#include "Windows/PostWindowsApi.h"
#include "Windows/HideWindowsPlatformAtomics.h"
#include "Windows/HideWindowsPlatformTypes.h"
#endif
```

<span data-ttu-id="a9eda-106">Il codice WinRT può essere compilato solo nelle piattaforme Win64 e HoloLens, quindi l'istruzione If impedisce l'inclusione di librerie WinRT su altre piattaforme.</span><span class="sxs-lookup"><span data-stu-id="a9eda-106">WinRT code can only be compiled in the Win64 and HoloLens platforms, so the if statement prevents WinRT libraries from being included on other platforms.</span></span> <span data-ttu-id="a9eda-107">Unknwn. h è stato aggiunto per avere l'interfaccia IUnknown.</span><span class="sxs-lookup"><span data-stu-id="a9eda-107">unknwn.h was added for having the IUnknown interface.</span></span> 


## <a name="winrt-from-a-nuget-package"></a><span data-ttu-id="a9eda-108">WinRT da un pacchetto NuGet</span><span class="sxs-lookup"><span data-stu-id="a9eda-108">WinRT from a NuGet package</span></span>

<span data-ttu-id="a9eda-109">È un po' più complesso se è necessario aggiungere un pacchetto NuGet con supporto per WinRT.</span><span class="sxs-lookup"><span data-stu-id="a9eda-109">It’s a little more complicated if you need to add a NuGet package with WinRT support.</span></span> <span data-ttu-id="a9eda-110">In questo caso, Visual Studio può eseguire praticamente tutti i processi, ma il sistema di compilazione non reale non può.</span><span class="sxs-lookup"><span data-stu-id="a9eda-110">In this case, Visual Studio can do practically all job for you, but the Unreal build system can’t.</span></span> <span data-ttu-id="a9eda-111">Fortunatamente, non è troppo difficile.</span><span class="sxs-lookup"><span data-stu-id="a9eda-111">Luckily, it’s not too difficult.</span></span> <span data-ttu-id="a9eda-112">Di seguito è riportato un esempio di come è possibile scaricare il pacchetto Microsoft. MixedReality. QR.</span><span class="sxs-lookup"><span data-stu-id="a9eda-112">Below is an example of how you would go about downloading the Microsoft.MixedReality.QR package.</span></span> <span data-ttu-id="a9eda-113">È possibile sostituirlo con un altro, ma assicurarsi di non perdere il file WinMD e copiare la DLL corretta.</span><span class="sxs-lookup"><span data-stu-id="a9eda-113">You can replace it with another, just make sure you don’t lose the winmd file and copy the correct dll.</span></span> 

<span data-ttu-id="a9eda-114">Windows SDK dll della sezione precedente sono gestite dal sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="a9eda-114">Windows SDK dlls from the previous section are handled by the OS.</span></span> <span data-ttu-id="a9eda-115">Le DLL di NuGet devono essere gestite dal codice nel modulo.</span><span class="sxs-lookup"><span data-stu-id="a9eda-115">NuGet’s dlls must be managed by the code in your module.</span></span> <span data-ttu-id="a9eda-116">Si consiglia di aggiungere il codice per scaricarli, copiarli nella cartella dei file binari e caricarli nella memoria del processo all'avvio del modulo.</span><span class="sxs-lookup"><span data-stu-id="a9eda-116">We recommend adding code to download them, copying into binaries folder, and load into the process memory at the module startup.</span></span>

<span data-ttu-id="a9eda-117">Al primo passaggio, è necessario aggiungere un packages.config ( https://docs.microsoft.com/nuget/reference/packages-config) nella cartella radice del modulo.</span><span class="sxs-lookup"><span data-stu-id="a9eda-117">At the first step, you should add a packages.config (https://docs.microsoft.com/nuget/reference/packages-config) into the root folder of your module.</span></span> <span data-ttu-id="a9eda-118">È necessario aggiungere tutti i pacchetti che si desidera scaricare, incluse tutte le relative dipendenze.</span><span class="sxs-lookup"><span data-stu-id="a9eda-118">There you should add all packages you want to download, including all their dependencies.</span></span> <span data-ttu-id="a9eda-119">Qui ho aggiunto Microsoft. MixedReality. QR come payload primario e altri due come dipendenze.</span><span class="sxs-lookup"><span data-stu-id="a9eda-119">Here I added Microsoft.MixedReality.QR as a primary payload and two others as dependencies to it.</span></span> <span data-ttu-id="a9eda-120">Il formato del file è uguale a quello di Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="a9eda-120">The format of that file is same as in Visual Studio:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

<span data-ttu-id="a9eda-121">È ora possibile scaricare NuGet, i pacchetti necessari o fare riferimento alla [documentazione](/nuget/consume-packages/install-use-packages-nuget-cli)di NuGet.</span><span class="sxs-lookup"><span data-stu-id="a9eda-121">Now you can download the NuGet, the required packages, or refer to the NuGet [documentation](/nuget/consume-packages/install-use-packages-nuget-cli).</span></span>

<span data-ttu-id="a9eda-122">Aprire YourModule.Build.cs e aggiungere il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="a9eda-122">Open YourModule.Build.cs and add the following code:</span></span>

```csharp
// WinRT with Nuget support
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string [] { "shlwapi.lib", "runtimeobject.lib" });

    // prepare everything for nuget
    string MyModuleName = GetType().Name;
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

    PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    ExternalDependencies.Add("packages.config");

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if (!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
            // we aren't focusing on a specific nuget version, we can use any of them but the latest one is preferable
            myWebClient.DownloadFile(@"https://dist.nuget.org/win-x86-commandline/latest/nuget.exe", NugetExe);
        }
    }

    // run nuget to update the packages
    {
        var StartInfo = new System.Diagnostics.ProcessStartInfo(NugetExe, string.Format("install \"{0}\" -OutputDirectory \"{1}\"", Path.Combine(ModuleDirectory, "packages.config"), NugetFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get nuget packages.  See log for details.");
        }
    }

    // get list of the installed packages, that's needed because the code should get particular versions of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] { '\r', '\n' });

    // winmd files of the packages
    List<string> WinMDFiles = new List<string>();

    // WinRT lib for some job
    string QRPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        string WinMDFile = Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd");
        SafeCopy(WinMDFile, Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())),
            Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        //add winmd file to the list for further processing using cppwinrt.exe
        WinMDFiles.Add(WinMDFile);
    }

    if (Target.Platform == UnrealTargetPlatform.Win64)
    {
        // Microsoft.VCRTForwarders.140 is needed to run WinRT dlls in Win64 platforms
        string VCRTForwardersPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
        if (!string.IsNullOrEmpty(VCRTForwardersPackage))
        {
            string VCRTForwardersName = VCRTForwardersPackage.Replace(" ", ".");
            foreach (var Dll in Directory.EnumerateFiles(Path.Combine(NugetFolder, VCRTForwardersName, "runtimes/win10-x64/native/release"), "*_app.dll"))
            {
                string newDll = Path.Combine(BinariesFolder, Path.GetFileName(Dll));
                SafeCopy(Dll, newDll);
                RuntimeDependencies.Add(newDll);
            }
        }
    }

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if (!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach (var winmd in WinMDFiles)
        {
            WinMDFilesStringbuilder.Append(" -input \"");
            WinMDFilesStringbuilder.Append(winmd);
            WinMDFilesStringbuilder.Append("\"");
        }

        // generate winrt headers and add them into include paths
        var StartInfo = new System.Diagnostics.ProcessStartInfo(CppWinRTExe, string.Format("{0} -input \"{1}\" -output \"{2}\"", WinMDFilesStringbuilder, Target.WindowsPlatform.WindowsSdkVersion, CppWinRTFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get generate WinRT headers.  See log for details.");
        }

        PrivateIncludePaths.Add(CppWinRTFolder);
    }
    else
    {
        // fall back to default WinSDK headers if no winrt package in our list
        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
    }
}
```

<span data-ttu-id="a9eda-123">È necessario definire il metodo SafeCopy come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="a9eda-123">You'll need to define the SafeCopy method as follows:</span></span>

```csharp
private void SafeCopy(string source, string destination)
{
    if(!File.Exists(source))
    {
        Log.TraceError("Class {0} can't find {1} file for copying", this.GetType().Name, source);
        return;
    }

    try
    {
        File.Copy(source, destination, true);
    }
    catch(IOException ex)
    {
        Log.TraceWarning("Failed to copy {0} to {1} with exception: {2}", source, destination, ex.Message);
        if (!File.Exists(destination))
        {
            Log.TraceError("Destination file {0} does not exist", destination);
            return;
        }

        Log.TraceWarning("Destination file {0} already existed and is probably in use.  The old file will be used for the runtime dependency.  This may happen when packaging a Win64 exe from the editor.", destination);
    }
}
```

<span data-ttu-id="a9eda-124">È necessario caricare manualmente le dll NuGet nella memoria del processo Win32. si consiglia di aggiungere il caricamento manuale nel metodo di avvio del modulo:</span><span class="sxs-lookup"><span data-stu-id="a9eda-124">NuGet DLLs needs to load into your Win32 process memory manually; we recommend adding manual loading into the startup method of your module:</span></span>

```cpp
void StartupModule() override
{
#if PLATFORM_WINDOWS
    const FString LibrariesDir = FPaths::ProjectPluginsDir() / "MyModule" / THIRDPARTY_BINARY_SUBFOLDER;
    FPlatformProcess::PushDllDirectory(*LibrariesDir);

    const FString DllName = "Microsoft.MixedReality.QR.dll";
    if (!FPlatformProcess::GetDllHandle(*DllName))
    {
        UE_LOG(LogHMD, Warning, TEXT("Dll \'%s\' can't be loaded from \'%s\'"), *DllName, *LibrariesDir);
    }

    FPlatformProcess::PopDllDirectory(*LibrariesDir);
#endif
}
```

<span data-ttu-id="a9eda-125">Infine, è possibile includere le intestazioni WinRT nel codice, come descritto nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="a9eda-125">Finally, you can include WinRT headers into your code as described in the previous section.</span></span>

# <a name="425"></a>[<span data-ttu-id="a9eda-126">4.25</span><span class="sxs-lookup"><span data-stu-id="a9eda-126">4.25</span></span>](#tab/425)

<span data-ttu-id="a9eda-127">Unreal non compila in modo nativo il codice WinRT nella versione 4,25, quindi è il processo di creare un file binario separato che può essere utilizzato dal sistema di compilazione di Unreal.</span><span class="sxs-lookup"><span data-stu-id="a9eda-127">Unreal doesn't natively compile WinRT code in version 4.25, so it's your job to build a separate binary that Unreal’s build system can consume.</span></span> 

## <a name="objectives"></a><span data-ttu-id="a9eda-128">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="a9eda-128">Objectives</span></span>

- <span data-ttu-id="a9eda-129">Crea una DLL di Windows universale che apre un FileSaveDialogue</span><span class="sxs-lookup"><span data-stu-id="a9eda-129">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="a9eda-130">Collegare la DLL a un progetto di gioco Unreal</span><span class="sxs-lookup"><span data-stu-id="a9eda-130">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="a9eda-131">Salvare un file in HoloLens da un progetto Unreal usando la nuova DLL</span><span class="sxs-lookup"><span data-stu-id="a9eda-131">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="a9eda-132">Introduzione</span><span class="sxs-lookup"><span data-stu-id="a9eda-132">Getting started</span></span>

1. <span data-ttu-id="a9eda-133">Verificare che siano installati tutti [gli strumenti necessari](../tutorials/unreal-uxt-ch1.md)</span><span class="sxs-lookup"><span data-stu-id="a9eda-133">Check that you have all [required tools](../tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="a9eda-134">[Creare un nuovo progetto irreale](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) e denominarlo **Consumewinrt**</span><span class="sxs-lookup"><span data-stu-id="a9eda-134">[Create a new Unreal project](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="a9eda-135">Abilitare i [plug](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) -in richiesti per lo sviluppo di HoloLens</span><span class="sxs-lookup"><span data-stu-id="a9eda-135">Enable the [required plugins](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="a9eda-136">[Installazione per la distribuzione](../tutorials/unreal-uxt-ch6.md) in un dispositivo o in un emulatore</span><span class="sxs-lookup"><span data-stu-id="a9eda-136">[Setup for deployment](../tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="a9eda-137">Creazione di una DLL WinRT</span><span class="sxs-lookup"><span data-stu-id="a9eda-137">Creating a WinRT DLL</span></span> 

1. <span data-ttu-id="a9eda-138">Aprire un nuovo progetto di Visual Studio e creare un progetto **dll (Windows universale)** nella stessa directory del file **uproject** del gioco non reale.</span><span class="sxs-lookup"><span data-stu-id="a9eda-138">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory as the Unreal game’s **uproject** file.</span></span> 

![Creazione di una DLL](../images/unreal-winrt-img-01.png)

2. <span data-ttu-id="a9eda-140">Denominare il progetto **HoloLensWinrtDLL** e impostare il percorso come sottodirectory **thirdparty** sul file uproject del gioco Unreal.</span><span class="sxs-lookup"><span data-stu-id="a9eda-140">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="a9eda-141">Selezionare **posiziona soluzione e progetto nella stessa directory** per semplificare la ricerca dei percorsi in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="a9eda-141">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![Configurazione della DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="a9eda-143">Al termine della compilazione del nuovo progetto, prestare particolare attenzione ai file di intestazione e cpp vuoti, denominati rispettivamente **HoloLensWinrtDLL. cpp** e **HoloLensWinrtDLL. h** .</span><span class="sxs-lookup"><span data-stu-id="a9eda-143">After the new project compiles, pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="a9eda-144">L'intestazione è il file di inclusione che usa la DLL in Unreal, mentre la CPP conserva il corpo di tutte le funzioni esportate e include il codice WinRT che Unreal non sarebbe altrimenti in grado di compilare.</span><span class="sxs-lookup"><span data-stu-id="a9eda-144">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="a9eda-145">Prima di aggiungere il codice, è necessario aggiornare le proprietà del progetto per assicurarsi che il codice WinRT necessario possa essere compilato:</span><span class="sxs-lookup"><span data-stu-id="a9eda-145">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="a9eda-146">Fare clic con il pulsante destro del mouse sul progetto HoloLensWinrtDLL e scegliere **Proprietà** .</span><span class="sxs-lookup"><span data-stu-id="a9eda-146">Right-click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="a9eda-147">Modificare l'elenco a discesa **configurazione** in **tutte le configurazioni** e l'elenco a discesa **piattaforma** su **tutte le piattaforme**</span><span class="sxs-lookup"><span data-stu-id="a9eda-147">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="a9eda-148">In **proprietà di configurazione> C/C++> tutte le opzioni**:</span><span class="sxs-lookup"><span data-stu-id="a9eda-148">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="a9eda-149">Aggiungere **await** a **Opzioni aggiuntive** per assicurarsi che sia possibile attendere le attività asincrone</span><span class="sxs-lookup"><span data-stu-id="a9eda-149">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="a9eda-150">Modificare lo standard del **linguaggio c++** allo **standard ISO c++ 17 (/STD: c++ 17)** per includere qualsiasi codice WinRT</span><span class="sxs-lookup"><span data-stu-id="a9eda-150">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![Aggiornamento delle proprietà del progetto](../images/unreal-winrt-img-03.png)

<span data-ttu-id="a9eda-152">Il progetto è pronto per aggiornare l'origine della DLL con il codice WinRT che apre una finestra di dialogo di file e salva un file nel disco HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a9eda-152">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="a9eda-153">Aggiunta del codice DLL</span><span class="sxs-lookup"><span data-stu-id="a9eda-153">Adding the DLL code</span></span>

1. <span data-ttu-id="a9eda-154">Aprire **HoloLensWinrtDLL. h** e aggiungere una funzione di DLL esportata per l'utilizzo di Unreal:</span><span class="sxs-lookup"><span data-stu-id="a9eda-154">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="a9eda-155">Aprire **HoloLensWinrtDLL. cpp** e aggiungere tutte le intestazioni che la classe utilizzerà:</span><span class="sxs-lookup"><span data-stu-id="a9eda-155">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> <span data-ttu-id="a9eda-156">Tutto il codice WinRT viene archiviato in **HoloLensWinrtDLL. cpp,** quindi Unreal non tenta di includere codice WinRT quando fa riferimento all'intestazione.</span><span class="sxs-lookup"><span data-stu-id="a9eda-156">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="a9eda-157">Sempre in **HoloLensWinrtDLL. cpp** aggiungere un corpo della funzione per OpenFileDialogue () e tutto il codice supportato:</span><span class="sxs-lookup"><span data-stu-id="a9eda-157">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="a9eda-158">Aggiungere una classe SaveGameManager a **HoloLensWinrtDLL. cpp** per gestire la finestra di dialogo del file e salvare il file:</span><span class="sxs-lookup"><span data-stu-id="a9eda-158">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullptr);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. <span data-ttu-id="a9eda-159">Compilare la soluzione per la **versione > arm64** per compilare la dll nella directory figlio arm64/Release/HoloLensWinrtDLL dalla soluzione dll.</span><span class="sxs-lookup"><span data-stu-id="a9eda-159">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="a9eda-160">Aggiunta del file binario WinRT a Unreal</span><span class="sxs-lookup"><span data-stu-id="a9eda-160">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="a9eda-161">Per il collegamento e l'uso di una DLL in Unreal è necessario un progetto C++.</span><span class="sxs-lookup"><span data-stu-id="a9eda-161">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="a9eda-162">Se si usa un progetto Blueprint, è possibile convertirlo facilmente in un progetto C++ aggiungendo una classe C++:</span><span class="sxs-lookup"><span data-stu-id="a9eda-162">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="a9eda-163">Nell'editor Unreal aprire **File > nuova classe C++...**</span><span class="sxs-lookup"><span data-stu-id="a9eda-163">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="a9eda-164">e creare un nuovo **attore** denominato **WinrtActor** per eseguire il codice nella dll:</span><span class="sxs-lookup"><span data-stu-id="a9eda-164">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![Creazione di un nuovo attore](../images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="a9eda-166">È stata ora creata una soluzione nella stessa directory del file uproject insieme a un nuovo script di compilazione denominato source/ConsumeWinRT/ConsumeWinRT. Build. cs.</span><span class="sxs-lookup"><span data-stu-id="a9eda-166">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="a9eda-167">Aprire la soluzione, cercare la cartella **Games/ConsumeWinRT/source/ConsumeWinRT** e aprire **ConsumeWinRT.Build.cs**:</span><span class="sxs-lookup"><span data-stu-id="a9eda-167">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![Apertura del file ConsumeWinRT.build.cs](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="a9eda-169">Collegamento della DLL</span><span class="sxs-lookup"><span data-stu-id="a9eda-169">Linking the DLL</span></span>
1. <span data-ttu-id="a9eda-170">In **ConsumeWinRT.Build.cs** aggiungere una proprietà per trovare il percorso di inclusione per la dll (la directory contenente HoloLensWinrtDLL. h).</span><span class="sxs-lookup"><span data-stu-id="a9eda-170">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="a9eda-171">La DLL si trova in una directory figlio del percorso di inclusione, quindi questa proprietà verrà usata come dir radice binaria:</span><span class="sxs-lookup"><span data-stu-id="a9eda-171">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

```cs
using System.IO;

public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirdParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. <span data-ttu-id="a9eda-172">Nel costruttore della classe aggiungere il codice seguente per aggiornare il percorso di inclusione, collegare il nuovo lib e ritardare il caricamento e copiare la DLL nel percorso appx in pacchetto:</span><span class="sxs-lookup"><span data-stu-id="a9eda-172">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. <span data-ttu-id="a9eda-173">Aprire **WinrtActor. h** e aggiungere una definizione di funzione, una che chiamerà da un progetto:</span><span class="sxs-lookup"><span data-stu-id="a9eda-173">Open **WinrtActor.h** and add one function definition, one that a blueprint will call:</span></span> 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. <span data-ttu-id="a9eda-174">Aprire **WinrtActor. cpp** e aggiornare BeginPlay per caricare la dll:</span><span class="sxs-lookup"><span data-stu-id="a9eda-174">Open **WinrtActor.cpp** and update BeginPlay to load the DLL:</span></span> 

```cpp
void AWinrtActor::BeginPlay()
{
    Super::BeginPlay();

    // Gets path to DLL location
    const FString BinDir = FPaths::ProjectDir() / 
        "ThirdParty" / "HoloLensWinrtDLL" / 
        "arm64" / "Release" / "HoloLensWinrtDLL";

    // Loads DLL into application
    void * dllHandle = FPlatformProcess::GetDllHandle(
        *(BinDir / "HoloLensWinrtDLL.dll"));
}

void AWinrtActor::OpenFileDialogue()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> <span data-ttu-id="a9eda-175">Prima di chiamare le funzioni, è necessario caricare la DLL.</span><span class="sxs-lookup"><span data-stu-id="a9eda-175">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="a9eda-176">Compilazione del gioco</span><span class="sxs-lookup"><span data-stu-id="a9eda-176">Building the game</span></span>
1. <span data-ttu-id="a9eda-177">Compilare la soluzione di gioco per avviare l'editor non reale aperto al progetto di gioco:</span><span class="sxs-lookup"><span data-stu-id="a9eda-177">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="a9eda-178">Nella scheda **posiziona gli attori** cercare il nuovo **WinrtActor** e trascinarlo nella scena</span><span class="sxs-lookup"><span data-stu-id="a9eda-178">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="a9eda-179">Aprire il progetto level per eseguire la funzione Blueprint Callable nella **WinrtActor**</span><span class="sxs-lookup"><span data-stu-id="a9eda-179">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![Inserimento del WinrtActor nella scena](../images/unreal-winrt-img-06.png)

2. <span data-ttu-id="a9eda-181">Nel **mondo**, trovare i **WindrtActor** precedentemente rilasciati nella scena e trascinarli nel progetto di livello:</span><span class="sxs-lookup"><span data-stu-id="a9eda-181">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![Trascinamento del WinrtActor nel progetto di livello](../images/unreal-winrt-img-07.png)

3. <span data-ttu-id="a9eda-183">Nel progetto Level trascinare il nodo output da WinrtActor, cercare **Apri file Dialog**, quindi indirizzare il nodo da qualsiasi input utente.</span><span class="sxs-lookup"><span data-stu-id="a9eda-183">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="a9eda-184">In questo caso, la finestra di dialogo Apri file viene chiamata da un evento vocale:</span><span class="sxs-lookup"><span data-stu-id="a9eda-184">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![Configurazione dei nodi nel progetto di livello](../images/unreal-winrt-img-08.png)

4. <span data-ttu-id="a9eda-186">Creare [il pacchetto del gioco per HoloLens](../tutorials/unreal-uxt-ch6.md), distribuirlo ed eseguirlo.</span><span class="sxs-lookup"><span data-stu-id="a9eda-186">[Package this game for HoloLens](../tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="a9eda-187">Quando Unreal chiama OpenFileDialogue, viene aperta una finestra di dialogo di file nella richiesta di HoloLens di un nome di file con estensione txt.</span><span class="sxs-lookup"><span data-stu-id="a9eda-187">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="a9eda-188">Dopo aver salvato il file, passare alla scheda **Esplora file** nel portale del dispositivo per visualizzare il contenuto "Hello WinRT".</span><span class="sxs-lookup"><span data-stu-id="a9eda-188">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="a9eda-189">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="a9eda-189">Summary</span></span> 

<span data-ttu-id="a9eda-190">Si consiglia di usare questa esercitazione come punto di partenza per l'utilizzo del codice WinRT in Unreal quando è necessario salvare i file nel disco HoloLens usando la stessa finestra di dialogo di Windows.</span><span class="sxs-lookup"><span data-stu-id="a9eda-190">We encourage you to use this tutorial as a starting point for consuming WinRT code in Unreal when you need to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="a9eda-191">Lo stesso processo si applica all'esportazione di funzioni aggiuntive dall'intestazione HoloLensWinrtDLL e usate in Unreal.</span><span class="sxs-lookup"><span data-stu-id="a9eda-191">The same process applies to exporting additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="a9eda-192">Prestare particolare attenzione al codice DLL che attende il codice WinRT asincrono in un thread MTA in background, evitando il deadlock del thread del gioco non reale.</span><span class="sxs-lookup"><span data-stu-id="a9eda-192">Pay special attention to the DLL code that waits on async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span>