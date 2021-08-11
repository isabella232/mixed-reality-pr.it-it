---
ms.openlocfilehash: 555360092a65b80a1298eb779736b29360f8c6e13bd1834994f316043843b47a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198382"
---
# <a name="426"></a>[4.26](#tab/426)

## <a name="the-standard-winrt-apis"></a>API WinRT standard

Il modo più comune e semplice per usare WinRT è chiamare i metodi da WinSDK. A tale scopo, aprire il file YourModule.Build.cs e aggiungere le righe seguenti:

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

Successivamente, devi aggiungere le intestazioni WinRT seguenti: 

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

Il codice WinRT può essere compilato solo nelle piattaforme Win64 e HoloLens, quindi l'istruzione if impedisce che le librerie WinRT vengano incluse in altre piattaforme. unknwn.h è stato aggiunto per avere l'interfaccia IUnknown. 


## <a name="winrt-from-a-nuget-package"></a>WinRT da un pacchetto NuGet

È un po' più complicato se devi aggiungere un pacchetto NuGet con supporto WinRT. In questo caso, Visual Studio può eseguire praticamente tutti i processi, ma il sistema di compilazione Unreal non lo può fare. Fortunatamente, non è troppo difficile. Di seguito è riportato un esempio di come scaricare il pacchetto Microsoft.MixedReality.QR. È possibile sostituirlo con un altro. Assicurarsi semplicemente di non perdere il file winmd e copiare la DLL corretta. 

Windows Le DLL SDK della sezione precedente vengono gestite dal sistema operativo. NuGet dll del modulo devono essere gestite dal codice nel modulo. È consigliabile aggiungere codice per scaricarli, copiarli nella cartella binaries e caricarli nella memoria del processo all'avvio del modulo.

Nel primo passaggio è necessario aggiungere un packages.config ( https://docs.microsoft.com/nuget/reference/packages-config) nella cartella radice del modulo. In questa pagina è necessario aggiungere tutti i pacchetti da scaricare, incluse tutte le relative dipendenze. Qui è stato aggiunto Microsoft.MixedReality.QR come payload primario e altri due come dipendenze. Il formato del file è identico a quello in Visual Studio:

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

È ora possibile scaricare il NuGet, i pacchetti necessari o fare riferimento alla documentazione NuGet [.](/nuget/consume-packages/install-use-packages-nuget-cli)

Aprire YourModule.Build.cs e aggiungere il codice seguente:

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

È necessario definire il metodo SafeCopy come segue:

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

NuGet Le DLL devono essere caricate manualmente nella memoria del processo Win32. È consigliabile aggiungere il caricamento manuale nel metodo di avvio del modulo:

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

Infine, puoi includere le intestazioni WinRT nel codice come descritto nella sezione precedente.

# <a name="425"></a>[4.25](#tab/425)

Unreal non compila in modo nativo il codice WinRT nella versione 4.25, quindi è compito dell'utente creare un file binario separato che può essere utilizzato dal sistema di compilazione di Unreal. 

## <a name="objectives"></a>Obiettivi

- Creare una DLL Windows universale che apre un fileSaveDialogue
- Collegare la DLL a un progetto di gioco Unreal
- Salvare un file nel HoloLens da un progetto Unreal usando la nuova DLL

## <a name="getting-started"></a>Guida introduttiva

1. Verificare che siano installati tutti [gli strumenti](../tutorials/unreal-uxt-ch1.md) necessari
2. [Creare un nuovo progetto Unreal e](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) denoziarlo **Consumewinrt**
3. Abilitare i [plug-in necessari per](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) HoloLens sviluppo
4. [Configurazione per la distribuzione](../tutorials/unreal-uxt-ch6.md) in un dispositivo o un emulatore

## <a name="creating-a-winrt-dll"></a>Creazione di una DLL WinRT 

1. Aprire un nuovo Visual Studio e creare un progetto **DLL (Universal Windows)** nella stessa directory del file **uproject** del gioco Unreal. 

![Creazione di una DLL](../images/unreal-winrt-img-01.png)

2. Assegnare al progetto **il nome HoloLensWinrtDLL** e impostare il percorso come sottodirectory **ThirdParty** sul file uproject del gioco Unreal. 
    * Selezionare **Inserisci soluzione e progetto nella stessa directory per semplificare** la ricerca dei percorsi in un secondo momento. 

![Configurazione della DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> Dopo la compilazione del nuovo progetto, prestare particolare attenzione ai file cpp e di intestazione vuoti, denominati **rispettivamente HoloLensWinrtDLL.cpp** e **HoloLensWinrtDLL.h.** L'intestazione è il file di inclusione che usa la DLL in Unreal, mentre il cpp contiene il corpo di qualsiasi funzione esportata e include qualsiasi codice WinRT che Unreal altrimenti non sarebbe in grado di compilare. 

3. Prima di aggiungere codice, devi aggiornare le proprietà del progetto per assicurarti che il codice WinRT necessario possa essere compilato: 
    * Fare clic con il pulsante destro del mouse sul progetto HoloLensWinrtDLL e selezionare **proprietà**  
    * Modificare **l'elenco a** discesa Configurazione **in Tutte le configurazioni** e l'elenco a discesa **Piattaforma** in Tutte **le piattaforme**  
    * In **Proprietà di configurazione> C/C++> tutte le opzioni:**
        * Aggiungere **await** ad **Altre opzioni** per assicurarsi che sia possibile attendere le attività asincrone  
        * Modificare **lo standard del linguaggio C++** in **ISO C++17 Standard (/std:c++17)** per includere qualsiasi codice WinRT

![Aggiornamento delle proprietà del progetto](../images/unreal-winrt-img-03.png)

Il progetto è pronto per aggiornare l'origine della DLL con il codice WinRT che apre una finestra di dialogo file e salva un file nel HoloLens disco.  

## <a name="adding-the-dll-code"></a>Aggiunta del codice DLL

1. Aprire **HoloLensWinrtDLL.h** e aggiungere una funzione esportata dll per l'uso da parte di Unreal: 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. Aprire **HoloLensWinrtDLL.cpp** e aggiungere tutte le intestazioni che verranno usate dalla classe:  

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
> Tutto il codice WinRT viene archiviato in **HoloLensWinrtDLL.cpp,** quindi Unreal non prova a includere codice WinRT quando fa riferimento all'intestazione. 

3. Sempre in **HoloLensWinrtDLL.cpp** aggiungere un corpo della funzione per OpenFileDialogue() e tutto il codice supportato: 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. Aggiungi una classe SaveGameManager **a HoloLensWinrtDLL.cpp** per gestire la finestra di dialogo del file e salvare il file: 

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

5. Compilare la soluzione **per release > ARM64** per compilare la DLL nella directory figlio ARM64/Release/HoloLensWinrtDLL dalla soluzione DLL. 

## <a name="adding-the-winrt-binary-to-unreal"></a>Aggiunta del file binario WinRT a Unreal 
Il collegamento e l'uso di una DLL in Unreal richiedono un progetto C++. Se si usa un progetto Blueprint, è possibile convertirlo facilmente in un progetto C++ aggiungendo una classe C++:  

1. Nell'editor Unreal aprire **File > Nuova classe C++...** e creare un nuovo **attore** denominato **WinrtActor** per eseguire il codice nella DLL: 

![Creazione di un nuovo attore](../images/unreal-winrt-img-04.png)

> [!NOTE]
> È stata creata una soluzione nella stessa directory del file uproject insieme a un nuovo script di compilazione denominato Source/ConsumeWinRT/ConsumeWinRT.Build.cs.

2. Aprire la soluzione, cercare la **cartella Games/ConsumeWinRT/Source/ConsumeWinRT** e **aprire ConsumeWinRT.build.cs:**

![Apertura del file ConsumeWinRT.build.cs](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>Collegamento della DLL
1. In **ConsumeWinRT.build.cs** aggiungi una proprietà per trovare il percorso di inclusione per la DLL (la directory contenente HoloLensWinrtDLL.h). La DLL si trova in una directory figlio del percorso di inclusione, quindi questa proprietà verrà usata come dir radice binaria:

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

2. Nel costruttore della classe aggiungere il codice seguente per aggiornare il percorso di inclusione, collegare la nuova libreria e ritardare il caricamento e copiare la DLL nel percorso appx in pacchetto:

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

3. Aprire **WinrtActor.h** e aggiungere una definizione di funzione, che verrà chiamata da un progetto: 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. Aprire **WinrtActor.cpp e** aggiornare BeginPlay per caricare la DLL: 

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
> La DLL deve essere caricata prima di chiamare una delle relative funzioni.

### <a name="building-the-game"></a>Compilazione del gioco
1. Compilare la soluzione di gioco per avviare l'editor Unreal aperto al progetto di gioco: 
    * Nella scheda **Place Actors (Inserisci** attori) cercare il **nuovo WinrtActor** e trascinarlo nella scena 
    * Aprire il progetto di livello per eseguire la funzione chiamabile del progetto in **WinrtActor** 

![Posizionamento di WinrtActor nella scena](../images/unreal-winrt-img-06.png)

2. In **World Outliner (Delineatore mondo)** trova **WindrtActor** rilasciato in precedenza nella scena e trascinalo nel progetto level: 

![Trascinamento di WinrtActor nel progetto di livello](../images/unreal-winrt-img-07.png)

3. Nel progetto a livello trascinare il nodo di output da WinrtActor, cercare Open File Dialog (Apri finestra di dialogo **file)** e quindi instradare il nodo da qualsiasi input utente.  In questo caso, open file dialog viene chiamato da un evento vocale: 

![Configurazione dei nodi nel progetto a livello](../images/unreal-winrt-img-08.png)

4. [Creare un pacchetto di questo gioco HoloLens,](../tutorials/unreal-uxt-ch6.md)distribuirlo ed eseguirlo.  

Quando Unreal chiama OpenFileDialogue, viene visualizzata una finestra di dialogo file HoloLens richiesta di un nome .txt file.  Dopo aver salvato il file, passare alla scheda **Esplora file** nel portale dei dispositivi per visualizzare il contenuto "Hello WinRT". 

## <a name="summary"></a>Riepilogo 

Si consiglia di usare questa esercitazione come punto di partenza per l'utilizzo di codice WinRT in Unreal quando è necessario salvare i file nel disco HoloLens usando la stessa finestra di dialogo dei file Windows.  Lo stesso processo si applica all'esportazione di funzioni aggiuntive dall'intestazione HoloLensWinrtDLL e usata in Unreal.  Prestare particolare attenzione al codice DLL che attende il codice WinRT asincrono in un thread MTA in background, evitando il deadlock del thread del gioco Unreal.