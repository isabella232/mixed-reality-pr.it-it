---
title: WinRT in Unreal
description: Panoramica del plug-in di audio spaziale per Unreal Engine.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicazione remota, realtà mista, sviluppo, Guida introduttiva, funzionalità, nuovo progetto, emulatore, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi, cuffie per realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, WinRT, DLL
ms.openlocfilehash: fd50e5ecd3186fc8852936affbfedc3d5fd4de75
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679810"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="27db0-104">WinRT in Unreal</span><span class="sxs-lookup"><span data-stu-id="27db0-104">WinRT in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="27db0-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="27db0-105">Overview</span></span>

<span data-ttu-id="27db0-106">Nel corso dello sviluppo di HoloLens potrebbe essere necessario scrivere una funzionalità usando WinRT.</span><span class="sxs-lookup"><span data-stu-id="27db0-106">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="27db0-107">Se ad esempio si apre una finestra di dialogo di file in un'applicazione HoloLens, è necessario FileSavePicker nel file di intestazione WinRT/Windows. storage. Pickers. h.</span><span class="sxs-lookup"><span data-stu-id="27db0-107">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span>  <span data-ttu-id="27db0-108">Poiché Unreal non compila in modo nativo il codice WinRT, è il processo di compilare un file binario separato che può essere utilizzato dal sistema di compilazione di Unreal.</span><span class="sxs-lookup"><span data-stu-id="27db0-108">Since Unreal doesn't natively compile WinRT code, it's your job to build a separate binary and that can be consumed by Unreal’s build system.</span></span> <span data-ttu-id="27db0-109">In questa esercitazione verrà illustrata una situazione di questo tipo.</span><span class="sxs-lookup"><span data-stu-id="27db0-109">This tutorial will walk you through just such a scenario.</span></span>

## <a name="objectives"></a><span data-ttu-id="27db0-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="27db0-110">Objectives</span></span>
- <span data-ttu-id="27db0-111">Crea una DLL di Windows universale che apre un FileSaveDialogue</span><span class="sxs-lookup"><span data-stu-id="27db0-111">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="27db0-112">Collegare la DLL a un progetto di gioco Unreal</span><span class="sxs-lookup"><span data-stu-id="27db0-112">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="27db0-113">Salvare un file in HoloLens da un progetto Unreal usando la nuova DLL</span><span class="sxs-lookup"><span data-stu-id="27db0-113">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="27db0-114">Introduzione</span><span class="sxs-lookup"><span data-stu-id="27db0-114">Getting started</span></span>
1. <span data-ttu-id="27db0-115">Verificare che siano installati tutti [gli strumenti necessari](tutorials/unreal-uxt-ch1.md)</span><span class="sxs-lookup"><span data-stu-id="27db0-115">Check that you have all [required tools](tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="27db0-116">[Creare un nuovo progetto irreale](tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) e denominarlo **Consumewinrt**</span><span class="sxs-lookup"><span data-stu-id="27db0-116">[Create a new Unreal project](tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="27db0-117">Abilitare i [plug](tutorials/unreal-uxt-ch2.md#enabling-required-plugins) -in richiesti per lo sviluppo di HoloLens</span><span class="sxs-lookup"><span data-stu-id="27db0-117">Enable the [required plugins](tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="27db0-118">[Installazione per la distribuzione](tutorials/unreal-uxt-ch6.md) in un dispositivo o in un emulatore</span><span class="sxs-lookup"><span data-stu-id="27db0-118">[Setup for deployment](tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="27db0-119">Creazione di una DLL WinRT</span><span class="sxs-lookup"><span data-stu-id="27db0-119">Creating a WinRT DLL</span></span> 
1. <span data-ttu-id="27db0-120">Aprire un nuovo progetto di Visual Studio e creare un progetto **dll (Windows universale)** nella stessa directory del file **uproject** del gioco Unreal.</span><span class="sxs-lookup"><span data-stu-id="27db0-120">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory to the Unreal game’s **uproject** file.</span></span> 

![Creazione di una DLL](images/unreal-winrt-img-01.png)

2. <span data-ttu-id="27db0-122">Denominare il progetto **HoloLensWinrtDLL** e impostare il percorso come sottodirectory **thirdparty** sul file uproject del gioco Unreal.</span><span class="sxs-lookup"><span data-stu-id="27db0-122">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="27db0-123">Selezionare **posiziona soluzione e progetto nella stessa directory** per semplificare la ricerca dei percorsi in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="27db0-123">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![Configurazione della DLL](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="27db0-125">Al termine della compilazione del nuovo progetto, è opportuno prestare particolare attenzione ai file di intestazione e cpp vuoti, denominati rispettivamente **HoloLensWinrtDLL. cpp** e **HoloLensWinrtDLL. h** .</span><span class="sxs-lookup"><span data-stu-id="27db0-125">After the new project compiles, you want to pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="27db0-126">L'intestazione è il file di inclusione che usa la DLL in Unreal, mentre la CPP conserva il corpo di tutte le funzioni esportate e include il codice WinRT che Unreal non sarebbe altrimenti in grado di compilare.</span><span class="sxs-lookup"><span data-stu-id="27db0-126">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="27db0-127">Prima di aggiungere il codice, è necessario aggiornare le proprietà del progetto per assicurarsi che il codice WinRT necessario possa essere compilato:</span><span class="sxs-lookup"><span data-stu-id="27db0-127">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="27db0-128">Fare clic con il pulsante destro del mouse sul progetto HoloLensWinrtDLL e scegliere **Proprietà** .</span><span class="sxs-lookup"><span data-stu-id="27db0-128">Right click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="27db0-129">Modificare l'elenco a discesa **configurazione** in **tutte le configurazioni** e l'elenco a discesa **piattaforma** su **tutte le piattaforme**</span><span class="sxs-lookup"><span data-stu-id="27db0-129">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="27db0-130">In **proprietà di configurazione> C/C++> tutte le opzioni**:</span><span class="sxs-lookup"><span data-stu-id="27db0-130">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="27db0-131">Aggiungere **await** a **Opzioni aggiuntive** per assicurarsi che sia possibile attendere le attività asincrone</span><span class="sxs-lookup"><span data-stu-id="27db0-131">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="27db0-132">Modificare lo standard del **linguaggio c++** allo **standard ISO c++ 17 (/STD: c++ 17)** per includere qualsiasi codice WinRT</span><span class="sxs-lookup"><span data-stu-id="27db0-132">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![Aggiornamento delle proprietà del progetto](images/unreal-winrt-img-03.png)

<span data-ttu-id="27db0-134">Il progetto è pronto per aggiornare l'origine della DLL con il codice WinRT che apre una finestra di dialogo di file e salva un file nel disco HoloLens.</span><span class="sxs-lookup"><span data-stu-id="27db0-134">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="27db0-135">Aggiunta del codice DLL</span><span class="sxs-lookup"><span data-stu-id="27db0-135">Adding the DLL code</span></span>
1. <span data-ttu-id="27db0-136">Aprire **HoloLensWinrtDLL. h** e aggiungere una funzione di DLL esportata per l'utilizzo di Unreal:</span><span class="sxs-lookup"><span data-stu-id="27db0-136">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="27db0-137">Aprire **HoloLensWinrtDLL. cpp** e aggiungere tutte le intestazioni che la classe utilizzerà:</span><span class="sxs-lookup"><span data-stu-id="27db0-137">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

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
> <span data-ttu-id="27db0-138">Tutto il codice WinRT viene archiviato in **HoloLensWinrtDLL. cpp,** quindi Unreal non tenta di includere codice WinRT quando fa riferimento all'intestazione.</span><span class="sxs-lookup"><span data-stu-id="27db0-138">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="27db0-139">Sempre in **HoloLensWinrtDLL. cpp** aggiungere un corpo della funzione per OpenFileDialogue () e tutto il codice supportato:</span><span class="sxs-lookup"><span data-stu-id="27db0-139">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="27db0-140">Aggiungere una classe SaveGameManager a **HoloLensWinrtDLL. cpp** per gestire la finestra di dialogo del file e salvare il file:</span><span class="sxs-lookup"><span data-stu-id="27db0-140">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

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

5. <span data-ttu-id="27db0-141">Compilare la soluzione per la **versione > arm64** per compilare la dll nella directory figlio arm64/Release/HoloLensWinrtDLL dalla soluzione dll.</span><span class="sxs-lookup"><span data-stu-id="27db0-141">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="27db0-142">Aggiunta del file binario WinRT a Unreal</span><span class="sxs-lookup"><span data-stu-id="27db0-142">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="27db0-143">Per il collegamento e l'uso di una DLL in Unreal è necessario un progetto C++.</span><span class="sxs-lookup"><span data-stu-id="27db0-143">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="27db0-144">Se si usa un progetto Blueprint, è possibile convertirlo facilmente in un progetto C++ aggiungendo una classe C++:</span><span class="sxs-lookup"><span data-stu-id="27db0-144">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="27db0-145">Nell'editor Unreal aprire **File > nuova classe C++...**</span><span class="sxs-lookup"><span data-stu-id="27db0-145">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="27db0-146">e creare un nuovo **attore** denominato **WinrtActor** per eseguire il codice nella dll:</span><span class="sxs-lookup"><span data-stu-id="27db0-146">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![Creazione di un nuovo attore](images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="27db0-148">È stata ora creata una soluzione nella stessa directory del file uproject insieme a un nuovo script di compilazione denominato source/ConsumeWinRT/ConsumeWinRT. Build. cs.</span><span class="sxs-lookup"><span data-stu-id="27db0-148">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="27db0-149">Aprire la soluzione, cercare la cartella **Games/ConsumeWinRT/source/ConsumeWinRT** e aprire **ConsumeWinRT.Build.cs**:</span><span class="sxs-lookup"><span data-stu-id="27db0-149">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![Apertura del file ConsumeWinRT.build.cs](images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="27db0-151">Collegamento della DLL</span><span class="sxs-lookup"><span data-stu-id="27db0-151">Linking the DLL</span></span>
1. <span data-ttu-id="27db0-152">In **ConsumeWinRT.Build.cs** aggiungere una proprietà per trovare il percorso di inclusione per la dll (la directory contenente HoloLensWinrtDLL. h).</span><span class="sxs-lookup"><span data-stu-id="27db0-152">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="27db0-153">La DLL si trova in una directory figlio del percorso di inclusione, quindi questa proprietà verrà usata come dir radice binaria:</span><span class="sxs-lookup"><span data-stu-id="27db0-153">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

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

2. <span data-ttu-id="27db0-154">Nel costruttore della classe aggiungere il codice seguente per aggiornare il percorso di inclusione, collegare il nuovo lib e ritardare il caricamento e copiare la DLL nel percorso appx in pacchetto:</span><span class="sxs-lookup"><span data-stu-id="27db0-154">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

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

3. <span data-ttu-id="27db0-155">Aprire **WinrtActor. h** e aggiungere una definizione di funzione, una che chiamerà da un progetto:</span><span class="sxs-lookup"><span data-stu-id="27db0-155">Open **WinrtActor.h** and add one function definition, one that a blueprint will call:</span></span> 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. <span data-ttu-id="27db0-156">Aprire **WinrtActor. cpp** e aggiornare BeginPlay per caricare la dll:</span><span class="sxs-lookup"><span data-stu-id="27db0-156">Open **WinrtActor.cpp** and update BeginPlay to load the DLL:</span></span> 

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
> <span data-ttu-id="27db0-157">Prima di chiamare le funzioni, è necessario caricare la DLL.</span><span class="sxs-lookup"><span data-stu-id="27db0-157">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="27db0-158">Compilazione del gioco</span><span class="sxs-lookup"><span data-stu-id="27db0-158">Building the game</span></span>
1. <span data-ttu-id="27db0-159">Compilare la soluzione di gioco per avviare l'editor non reale aperto al progetto di gioco:</span><span class="sxs-lookup"><span data-stu-id="27db0-159">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="27db0-160">Nella scheda **posiziona gli attori** cercare il nuovo **WinrtActor** e trascinarlo nella scena</span><span class="sxs-lookup"><span data-stu-id="27db0-160">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="27db0-161">Aprire il progetto level per eseguire la funzione Blueprint Callable nella **WinrtActor**</span><span class="sxs-lookup"><span data-stu-id="27db0-161">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![Inserimento del WinrtActor nella scena](images/unreal-winrt-img-06.png)

2. <span data-ttu-id="27db0-163">Nel **mondo**, trovare i **WindrtActor** precedentemente rilasciati nella scena e trascinarli nel progetto di livello:</span><span class="sxs-lookup"><span data-stu-id="27db0-163">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![Trascinamento del WinrtActor nel progetto di livello](images/unreal-winrt-img-07.png)

3. <span data-ttu-id="27db0-165">Nel progetto Level trascinare il nodo output da WinrtActor, cercare **Apri file Dialog**, quindi indirizzare il nodo da qualsiasi input utente.</span><span class="sxs-lookup"><span data-stu-id="27db0-165">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="27db0-166">In questo caso, la finestra di dialogo Apri file viene chiamata da un evento vocale:</span><span class="sxs-lookup"><span data-stu-id="27db0-166">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![Configurazione dei nodi nel progetto di livello](images/unreal-winrt-img-08.png)

4. <span data-ttu-id="27db0-168">Creare [il pacchetto del gioco per HoloLens](tutorials/unreal-uxt-ch6.md), distribuirlo ed eseguirlo.</span><span class="sxs-lookup"><span data-stu-id="27db0-168">[Package this game for HoloLens](tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="27db0-169">Quando Unreal chiama OpenFileDialogue, viene aperta una finestra di dialogo di file nella richiesta di HoloLens di un nome di file con estensione txt.</span><span class="sxs-lookup"><span data-stu-id="27db0-169">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="27db0-170">Dopo aver salvato il file, passare alla scheda **Esplora file** nel portale del dispositivo per visualizzare il contenuto "Hello WinRT".</span><span class="sxs-lookup"><span data-stu-id="27db0-170">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="27db0-171">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="27db0-171">Summary</span></span> 

<span data-ttu-id="27db0-172">Si consiglia di usare il codice in questa esercitazione come punto di partenza per l'utilizzo del codice WinRT in Unreal.</span><span class="sxs-lookup"><span data-stu-id="27db0-172">We encourage you to use the code in this tutorial as a starting point for consuming WinRT code in Unreal.</span></span>  <span data-ttu-id="27db0-173">Consente agli utenti di salvare i file nel disco HoloLens usando la stessa finestra di dialogo del file di Windows.</span><span class="sxs-lookup"><span data-stu-id="27db0-173">It allows users to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="27db0-174">Seguire lo stesso processo per esportare eventuali funzioni aggiuntive dall'intestazione HoloLensWinrtDLL e usate in Unreal.</span><span class="sxs-lookup"><span data-stu-id="27db0-174">Follow the same process to export any additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="27db0-175">Si noti il codice DLL che attende il codice WinRT asincrono in un thread in background MTA, che evita il deadlock del thread del gioco non reale.</span><span class="sxs-lookup"><span data-stu-id="27db0-175">Note the DLL code that waits on any async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

## <a name="next-development-checkpoint"></a><span data-ttu-id="27db0-176">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="27db0-176">Next Development Checkpoint</span></span>

<span data-ttu-id="27db0-177">Se si sta seguendo il percorso di checkpoint per lo sviluppo con Unreal che abbiamo delineato, si stanno esplorando le API e le funzionalità della piattaforma di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="27db0-177">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="27db0-178">Da qui è possibile passare a qualsiasi [argomento](unreal-development-overview.md#3-platform-capabilities-and-apis) o passare direttamente alla distribuzione dell'app in un dispositivo o in un emulatore.</span><span class="sxs-lookup"><span data-stu-id="27db0-178">From here, you can proceed to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="27db0-179">Distribuzione nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="27db0-179">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="27db0-180">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="27db0-180">See also</span></span>
* [<span data-ttu-id="27db0-181">API C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="27db0-181">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="27db0-182">Classe FileSavePicker</span><span class="sxs-lookup"><span data-stu-id="27db0-182">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="27db0-183">Librerie di terze parti non reali</span><span class="sxs-lookup"><span data-stu-id="27db0-183">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
