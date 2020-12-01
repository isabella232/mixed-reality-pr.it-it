---
ms.openlocfilehash: fd44d63ad502b6807c6aa18ce6fc63493fc254dc
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354444"
---
# <a name="425"></a>[<span data-ttu-id="cd9c8-101">4.25</span><span class="sxs-lookup"><span data-stu-id="cd9c8-101">4.25</span></span>](#tab/425)

<span data-ttu-id="cd9c8-102">Unreal non compila in modo nativo il codice WinRT nella versione 4,25, quindi è il processo di compilare un file binario separato che può essere utilizzato dal sistema di compilazione di Unreal.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-102">Unreal doesn't natively compile WinRT code in version 4.25, so it's your job to build a separate binary and that can be consumed by Unreal’s build system.</span></span> <span data-ttu-id="cd9c8-103">In questa esercitazione verrà illustrata una situazione di questo tipo.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-103">This tutorial will walk you through just such a scenario.</span></span>

## <a name="objectives"></a><span data-ttu-id="cd9c8-104">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="cd9c8-104">Objectives</span></span>
- <span data-ttu-id="cd9c8-105">Crea una DLL di Windows universale che apre un FileSaveDialogue</span><span class="sxs-lookup"><span data-stu-id="cd9c8-105">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="cd9c8-106">Collegare la DLL a un progetto di gioco Unreal</span><span class="sxs-lookup"><span data-stu-id="cd9c8-106">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="cd9c8-107">Salvare un file in HoloLens da un progetto Unreal usando la nuova DLL</span><span class="sxs-lookup"><span data-stu-id="cd9c8-107">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="cd9c8-108">Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="cd9c8-108">Getting started</span></span>
1. <span data-ttu-id="cd9c8-109">Verificare che siano installati tutti [gli strumenti necessari](../tutorials/unreal-uxt-ch1.md)</span><span class="sxs-lookup"><span data-stu-id="cd9c8-109">Check that you have all [required tools](../tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="cd9c8-110">[Creare un nuovo progetto irreale](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) e denominarlo **Consumewinrt**</span><span class="sxs-lookup"><span data-stu-id="cd9c8-110">[Create a new Unreal project](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="cd9c8-111">Abilitare i [plug](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) -in richiesti per lo sviluppo di HoloLens</span><span class="sxs-lookup"><span data-stu-id="cd9c8-111">Enable the [required plugins](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="cd9c8-112">[Installazione per la distribuzione](../tutorials/unreal-uxt-ch6.md) in un dispositivo o in un emulatore</span><span class="sxs-lookup"><span data-stu-id="cd9c8-112">[Setup for deployment](../tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="cd9c8-113">Creazione di una DLL WinRT</span><span class="sxs-lookup"><span data-stu-id="cd9c8-113">Creating a WinRT DLL</span></span> 
1. <span data-ttu-id="cd9c8-114">Aprire un nuovo progetto di Visual Studio e creare un progetto **dll (Windows universale)** nella stessa directory del file **uproject** del gioco Unreal.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-114">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory to the Unreal game’s **uproject** file.</span></span> 

![Creazione di una DLL](../images/unreal-winrt-img-01.png)

2. <span data-ttu-id="cd9c8-116">Denominare il progetto **HoloLensWinrtDLL** e impostare il percorso come sottodirectory **thirdparty** sul file uproject del gioco Unreal.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-116">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="cd9c8-117">Selezionare **posiziona soluzione e progetto nella stessa directory** per semplificare la ricerca dei percorsi in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-117">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![Configurazione della DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="cd9c8-119">Al termine della compilazione del nuovo progetto, è opportuno prestare particolare attenzione ai file di intestazione e cpp vuoti, denominati rispettivamente **HoloLensWinrtDLL. cpp** e **HoloLensWinrtDLL. h** .</span><span class="sxs-lookup"><span data-stu-id="cd9c8-119">After the new project compiles, you want to pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="cd9c8-120">L'intestazione è il file di inclusione che usa la DLL in Unreal, mentre la CPP conserva il corpo di tutte le funzioni esportate e include il codice WinRT che Unreal non sarebbe altrimenti in grado di compilare.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-120">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="cd9c8-121">Prima di aggiungere il codice, è necessario aggiornare le proprietà del progetto per assicurarsi che il codice WinRT necessario possa essere compilato:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-121">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="cd9c8-122">Fare clic con il pulsante destro del mouse sul progetto HoloLensWinrtDLL e scegliere **Proprietà** .</span><span class="sxs-lookup"><span data-stu-id="cd9c8-122">Right click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="cd9c8-123">Modificare l'elenco a discesa **configurazione** in **tutte le configurazioni** e l'elenco a discesa **piattaforma** su **tutte le piattaforme**</span><span class="sxs-lookup"><span data-stu-id="cd9c8-123">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="cd9c8-124">In **proprietà di configurazione> C/C++> tutte le opzioni**:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-124">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="cd9c8-125">Aggiungere **await** a **Opzioni aggiuntive** per assicurarsi che sia possibile attendere le attività asincrone</span><span class="sxs-lookup"><span data-stu-id="cd9c8-125">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="cd9c8-126">Modificare lo standard del **linguaggio c++** allo **standard ISO c++ 17 (/STD: c++ 17)** per includere qualsiasi codice WinRT</span><span class="sxs-lookup"><span data-stu-id="cd9c8-126">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![Aggiornamento delle proprietà del progetto](../images/unreal-winrt-img-03.png)

<span data-ttu-id="cd9c8-128">Il progetto è pronto per aggiornare l'origine della DLL con il codice WinRT che apre una finestra di dialogo di file e salva un file nel disco HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-128">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="cd9c8-129">Aggiunta del codice DLL</span><span class="sxs-lookup"><span data-stu-id="cd9c8-129">Adding the DLL code</span></span>
1. <span data-ttu-id="cd9c8-130">Aprire **HoloLensWinrtDLL. h** e aggiungere una funzione di DLL esportata per l'utilizzo di Unreal:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-130">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="cd9c8-131">Aprire **HoloLensWinrtDLL. cpp** e aggiungere tutte le intestazioni che la classe utilizzerà:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-131">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

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
> <span data-ttu-id="cd9c8-132">Tutto il codice WinRT viene archiviato in **HoloLensWinrtDLL. cpp,** quindi Unreal non tenta di includere codice WinRT quando fa riferimento all'intestazione.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-132">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="cd9c8-133">Sempre in **HoloLensWinrtDLL. cpp** aggiungere un corpo della funzione per OpenFileDialogue () e tutto il codice supportato:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-133">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="cd9c8-134">Aggiungere una classe SaveGameManager a **HoloLensWinrtDLL. cpp** per gestire la finestra di dialogo del file e salvare il file:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-134">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

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

5. <span data-ttu-id="cd9c8-135">Compilare la soluzione per la **versione > arm64** per compilare la dll nella directory figlio arm64/Release/HoloLensWinrtDLL dalla soluzione dll.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-135">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="cd9c8-136">Aggiunta del file binario WinRT a Unreal</span><span class="sxs-lookup"><span data-stu-id="cd9c8-136">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="cd9c8-137">Per il collegamento e l'uso di una DLL in Unreal è necessario un progetto C++.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-137">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="cd9c8-138">Se si usa un progetto Blueprint, è possibile convertirlo facilmente in un progetto C++ aggiungendo una classe C++:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-138">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="cd9c8-139">Nell'editor Unreal aprire **File > nuova classe C++...**</span><span class="sxs-lookup"><span data-stu-id="cd9c8-139">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="cd9c8-140">e creare un nuovo **attore** denominato **WinrtActor** per eseguire il codice nella dll:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-140">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![Creazione di un nuovo attore](../images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="cd9c8-142">È stata ora creata una soluzione nella stessa directory del file uproject insieme a un nuovo script di compilazione denominato source/ConsumeWinRT/ConsumeWinRT. Build. cs.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-142">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="cd9c8-143">Aprire la soluzione, cercare la cartella **Games/ConsumeWinRT/source/ConsumeWinRT** e aprire **ConsumeWinRT.Build.cs**:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-143">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![Apertura del file ConsumeWinRT.build.cs](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="cd9c8-145">Collegamento della DLL</span><span class="sxs-lookup"><span data-stu-id="cd9c8-145">Linking the DLL</span></span>
1. <span data-ttu-id="cd9c8-146">In **ConsumeWinRT.Build.cs** aggiungere una proprietà per trovare il percorso di inclusione per la dll (la directory contenente HoloLensWinrtDLL. h).</span><span class="sxs-lookup"><span data-stu-id="cd9c8-146">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="cd9c8-147">La DLL si trova in una directory figlio del percorso di inclusione, quindi questa proprietà verrà usata come dir radice binaria:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-147">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

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

2. <span data-ttu-id="cd9c8-148">Nel costruttore della classe aggiungere il codice seguente per aggiornare il percorso di inclusione, collegare il nuovo lib e ritardare il caricamento e copiare la DLL nel percorso appx in pacchetto:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-148">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

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

3. <span data-ttu-id="cd9c8-149">Aprire **WinrtActor. h** e aggiungere una definizione di funzione, una che chiamerà da un progetto:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-149">Open **WinrtActor.h** and add one function definition, one that a blueprint will call:</span></span> 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. <span data-ttu-id="cd9c8-150">Aprire **WinrtActor. cpp** e aggiornare BeginPlay per caricare la dll:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-150">Open **WinrtActor.cpp** and update BeginPlay to load the DLL:</span></span> 

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
> <span data-ttu-id="cd9c8-151">Prima di chiamare le funzioni, è necessario caricare la DLL.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-151">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="cd9c8-152">Compilazione del gioco</span><span class="sxs-lookup"><span data-stu-id="cd9c8-152">Building the game</span></span>
1. <span data-ttu-id="cd9c8-153">Compilare la soluzione di gioco per avviare l'editor non reale aperto al progetto di gioco:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-153">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="cd9c8-154">Nella scheda **posiziona gli attori** cercare il nuovo **WinrtActor** e trascinarlo nella scena</span><span class="sxs-lookup"><span data-stu-id="cd9c8-154">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="cd9c8-155">Aprire il progetto level per eseguire la funzione Blueprint Callable nella **WinrtActor**</span><span class="sxs-lookup"><span data-stu-id="cd9c8-155">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![Inserimento del WinrtActor nella scena](../images/unreal-winrt-img-06.png)

2. <span data-ttu-id="cd9c8-157">Nel **mondo**, trovare i **WindrtActor** precedentemente rilasciati nella scena e trascinarli nel progetto di livello:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-157">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![Trascinamento del WinrtActor nel progetto di livello](../images/unreal-winrt-img-07.png)

3. <span data-ttu-id="cd9c8-159">Nel progetto Level trascinare il nodo output da WinrtActor, cercare **Apri file Dialog**, quindi indirizzare il nodo da qualsiasi input utente.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-159">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="cd9c8-160">In questo caso, la finestra di dialogo Apri file viene chiamata da un evento vocale:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-160">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![Configurazione dei nodi nel progetto di livello](../images/unreal-winrt-img-08.png)

4. <span data-ttu-id="cd9c8-162">Creare [il pacchetto del gioco per HoloLens](../tutorials/unreal-uxt-ch6.md), distribuirlo ed eseguirlo.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-162">[Package this game for HoloLens](../tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="cd9c8-163">Quando Unreal chiama OpenFileDialogue, viene aperta una finestra di dialogo di file nella richiesta di HoloLens di un nome di file con estensione txt.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-163">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="cd9c8-164">Dopo aver salvato il file, passare alla scheda **Esplora file** nel portale del dispositivo per visualizzare il contenuto "Hello WinRT".</span><span class="sxs-lookup"><span data-stu-id="cd9c8-164">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="cd9c8-165">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="cd9c8-165">Summary</span></span> 

<span data-ttu-id="cd9c8-166">Si consiglia di usare il codice in questa esercitazione come punto di partenza per l'utilizzo del codice WinRT in Unreal.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-166">We encourage you to use the code in this tutorial as a starting point for consuming WinRT code in Unreal.</span></span>  <span data-ttu-id="cd9c8-167">Consente agli utenti di salvare i file nel disco HoloLens usando la stessa finestra di dialogo del file di Windows.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-167">It allows users to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="cd9c8-168">Seguire lo stesso processo per esportare eventuali funzioni aggiuntive dall'intestazione HoloLensWinrtDLL e usate in Unreal.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-168">Follow the same process to export any additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="cd9c8-169">Si noti il codice DLL che attende il codice WinRT asincrono in un thread in background MTA, che evita il deadlock del thread del gioco non reale.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-169">Note the DLL code that waits on any async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

# <a name="426"></a>[<span data-ttu-id="cd9c8-170">4,26</span><span class="sxs-lookup"><span data-stu-id="cd9c8-170">4.26</span></span>](#tab/426)

## <a name="the-standard-winrt-apis"></a><span data-ttu-id="cd9c8-171">API WinRT standard</span><span class="sxs-lookup"><span data-stu-id="cd9c8-171">The standard WinRT APIs</span></span>

<span data-ttu-id="cd9c8-172">Il modo più comune e più semplice per usare WinRT consiste nel chiamare i metodi di WinSDK.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-172">The most common and easiest way to use WinRT is to call methods from WinSDK.</span></span> <span data-ttu-id="cd9c8-173">A tale scopo, aprire il file YourModule.Build.cs e aggiungere le righe seguenti:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-173">To do so, open YourModule.Build.cs file and add the following lines:</span></span>

```cpp
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

<span data-ttu-id="cd9c8-174">Successivamente, è necessario aggiungere le intestazioni WinRT seguenti:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-174">Next, you need to add the following WinRT headers:</span></span> 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
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

<span data-ttu-id="cd9c8-175">Il codice WinRT può essere compilato solo nelle piattaforme Win64 e HoloLens, quindi l'istruzione If impedisce l'inclusione di librerie WinRT su altre piattaforme.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-175">WinRT code can only be compiled in the Win64 and HoloLens platforms, so the if statement prevents WinRT libraries from being included on other platforms.</span></span> <span data-ttu-id="cd9c8-176">Unknwn. h è stato aggiunto per avere l'interfaccia IUnknown.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-176">unknwn.h was added for having the IUnknown interface.</span></span> 

<span data-ttu-id="cd9c8-177">Prima di scrivere codice, è necessario disabilitare gli avvisi comuni nelle intestazioni WinRT usando:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-177">Before writing any code, you need to disable common warnings in WinRT headers by using:</span></span>

```cpp
#pragma warning(disable : 5205 4265)
```

## <a name="winrt-from-a-nuget-package"></a><span data-ttu-id="cd9c8-178">WinRT da un pacchetto NuGet</span><span class="sxs-lookup"><span data-stu-id="cd9c8-178">WinRT from a NuGet package</span></span>

<span data-ttu-id="cd9c8-179">È un po' più complesso se è necessario aggiungere un pacchetto NuGet con supporto per WinRT.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-179">It’s a little more complicated if you need to add a nuget package with WinRT support.</span></span> <span data-ttu-id="cd9c8-180">In questo caso, Visual Studio può eseguire praticamente tutti i processi, ma il sistema di compilazione non reale non può.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-180">In this case, Visual Studio can do practically all job for you, but the Unreal build system can’t.</span></span> <span data-ttu-id="cd9c8-181">Fortunatamente, non è troppo difficile.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-181">Luckily, it’s not too difficult.</span></span> <span data-ttu-id="cd9c8-182">Di seguito è riportato un esempio di come è possibile scaricare il pacchetto Microsoft. MixedReality. QR.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-182">Below is an example of how you would go about downloading the Microsoft.MixedReality.QR package.</span></span> <span data-ttu-id="cd9c8-183">È possibile sostituirlo con un altro, ma assicurarsi di non perdere il file WinMD e copiare la DLL corretta.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-183">You can replace it with another, just make sure that you don’t lose the winmd file and copy the correct dll.</span></span> 

<span data-ttu-id="cd9c8-184">Windows SDK dll della sezione precedente sono gestite dal sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-184">Windows SDK dlls from the previous section are handled by the OS.</span></span> <span data-ttu-id="cd9c8-185">Le DLL di NuGet devono essere gestite dal codice nel modulo.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-185">Nuget’s dlls must be managed by the code in your module.</span></span> <span data-ttu-id="cd9c8-186">È necessario aggiungere il codice per scaricarli, copiarli nella cartella dei file binari e caricarli nella memoria del processo all'avvio del modulo.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-186">You should add code to download them, copy into binaries folder and load into the process memory at the module startup.</span></span>

<span data-ttu-id="cd9c8-187">Al primo passaggio, è necessario aggiungere un packages.config ( https://docs.microsoft.com/nuget/reference/packages-config) nella cartella radice del modulo.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-187">At the first step, you should add a packages.config (https://docs.microsoft.com/nuget/reference/packages-config) into the root folder of your module.</span></span> <span data-ttu-id="cd9c8-188">È necessario aggiungere tutti i pacchetti che si desidera scaricare, incluse tutte le relative dipendenze.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-188">There you should add all packages you want to download, including all their dependencies.</span></span> <span data-ttu-id="cd9c8-189">Qui ho aggiunto Microsoft. MixedReality. QR come payload primario e altri due come dipendenze.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-189">Here I added Microsoft.MixedReality.QR as a primary payload and two others as dependencies to it.</span></span> <span data-ttu-id="cd9c8-190">Il formato del file è uguale a quello di Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-190">The format of that file is same as in Visual Studio:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

<span data-ttu-id="cd9c8-191">È ora possibile scaricare NuGet, i pacchetti necessari o fare riferimento alla [documentazione](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli)di NuGet.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-191">Now you can download the NuGet, the required packages, or refer to the NuGet [documentation](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli).</span></span>

<span data-ttu-id="cd9c8-192">Aprire YourModule.Build.cs e aggiungere il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-192">Open YourModule.Build.cs and add the following code:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    string MyModuleName = GetType().Name;

    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.Add("shlwapi.lib");
    PublicSystemLibraries.Add("runtimeobject.lib");

    // prepare everything for nuget
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

            PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if(!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
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
            
    // get list of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] {'\r', '\n' });

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if(!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // search all downloaded packages for winmd files
        string[] WinMDFiles = Directory.GetFiles(NugetFolder, "*.winmd", SearchOption.AllDirectories);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach(var winmd in WinMDFiles)
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
        // fall to default WinSDK headers
                        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
            }

    // WinRT lib for some job
    string QRPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        SafeCopy(Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd"), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));
    }

    if(Target.Platform == UnrealTargetPlatform.Win64)
    {
        // Microsoft.VCRTForwarders.140 is needed to run WinRT dlls in Win64 platforms
        string VCRTForwardersPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
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
```

<span data-ttu-id="cd9c8-193">È necessario definire il metodo SafeCopy come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-193">You'll need to define the SafeCopy method as follows:</span></span>

```cpp
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

<span data-ttu-id="cd9c8-194">Le dll NuGet devono essere caricate manualmente nella memoria del processo Win32.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-194">Nuget DLLs needs to load into your Win32 process memory manually.</span></span> <span data-ttu-id="cd9c8-195">È necessario aggiungere il caricamento manuale nel metodo di avvio del modulo:</span><span class="sxs-lookup"><span data-stu-id="cd9c8-195">You should add manual loading into the startup method of your module:</span></span>

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

<span data-ttu-id="cd9c8-196">Infine, è possibile includere le intestazioni WinRT nel codice, come descritto nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="cd9c8-196">Finally, you can include WinRT headers into your code as described in the previous section.</span></span>