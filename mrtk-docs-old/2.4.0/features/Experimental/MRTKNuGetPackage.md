---
title: MRTKNuGetPakages
description: Pakages NuGet in MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: f4f4ceb48b9987f6a964879e95a75f8db58c145f
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782762"
---
# <a name="mixed-reality-toolkit-nuget-package"></a><span data-ttu-id="97001-104">Pacchetto NuGet del Toolkit per realtà mista</span><span class="sxs-lookup"><span data-stu-id="97001-104">Mixed Reality Toolkit NuGet package</span></span>

<span data-ttu-id="97001-105">Il Toolkit di realtà mista (MRTK) è ora disponibile come pacchetto NuGet in NuGet.org. Esistono alcune differenze per quanto riguarda l'utilizzo della versione NuGet di MRTK anziché di un file unitypackage Tools, leggere le [considerazioni sui pacchetti NuGet](#nuget-package-considerations) di seguito.</span><span class="sxs-lookup"><span data-stu-id="97001-105">Mixed Reality Toolkit (MRTK) is now available as a NuGet package on NuGet.org. There are some differences when it comes to consuming NuGet version of MRTK as opposed to a .unitypackage, read [NuGet Package Considerations](#nuget-package-considerations) below.</span></span> <span data-ttu-id="97001-106">Se si verificano problemi, archiviare un problema usando questo [modello](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new?assignees=&labels=Bug,Package%20Management%20-%20NuGet&template=bug-report.md&title=).</span><span class="sxs-lookup"><span data-stu-id="97001-106">If any issues are encountered, file an issue using this [template](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new?assignees=&labels=Bug,Package%20Management%20-%20NuGet&template=bug-report.md&title=).</span></span>

> [!NOTE]
> <span data-ttu-id="97001-107">La migrazione dei progetti esistenti per l'utilizzo di MRTK come pacchetto NuGet non è ancora supportata.</span><span class="sxs-lookup"><span data-stu-id="97001-107">Migration of existing projects to consume MRTK as a NuGet package is not yet supported.</span></span> <span data-ttu-id="97001-108">Usare MRTK tramite NuGet solo per i nuovi progetti.</span><span class="sxs-lookup"><span data-stu-id="97001-108">Use MRTK via NuGet only for new projects.</span></span>

## <a name="installing-the-nuget-package"></a><span data-ttu-id="97001-109">Installazione del pacchetto NuGet</span><span class="sxs-lookup"><span data-stu-id="97001-109">Installing the NuGet package</span></span>

<span data-ttu-id="97001-110">Seguire queste istruzioni per aggiungere il Toolkit di realtà mista come pacchetto NuGet al progetto.</span><span class="sxs-lookup"><span data-stu-id="97001-110">Follow these instructions to add the Mixed Reality Toolkit as a NuGet package to your project.</span></span>

1. <span data-ttu-id="97001-111">Scaricare la versione più recente di [NuGetForUnity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) . file unitypackage Tools.</span><span class="sxs-lookup"><span data-stu-id="97001-111">Download the latest [NuGetForUnity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) .unitypackage.</span></span>
    1. <span data-ttu-id="97001-112">Se *NuGetForUnity* è già installato, verificare che sia la versione **2.0.0 o successiva**.</span><span class="sxs-lookup"><span data-stu-id="97001-112">If *NuGetForUnity* is already installed, please ensure it is version **2.0.0 or newer**.</span></span>
1. <span data-ttu-id="97001-113">Importare il pacchetto nel progetto Unity, [istruzioni](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="97001-113">Import the package into the Unity project, [instructions](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span>
1. <span data-ttu-id="97001-114">Nella barra dei menu di Unity fare clic su **NuGet**  >  **Gestisci pacchetti NuGet**.</span><span class="sxs-lookup"><span data-stu-id="97001-114">In the Unity menu bar, click on **NuGet** > **Manage NuGet Packages**.</span></span>

    ![Manage NuGet Packages](../Images/NuGet/ManageNuGetPackages.png)
1. <span data-ttu-id="97001-116">Nella casella di ricerca immettere **Microsoft. MixedReality. Toolkit**.</span><span class="sxs-lookup"><span data-stu-id="97001-116">In the Search box, enter **Microsoft.MixedReality.Toolkit**.</span></span>

    ![Manage NuGet Packages](../Images/NuGet/SearchBox.png)
1. <span data-ttu-id="97001-118">Scegliere il pacchetto MRTK Core:</span><span class="sxs-lookup"><span data-stu-id="97001-118">Choose the MRTK core package:</span></span>
    - <span data-ttu-id="97001-119">**Microsoft. MixedReality. Toolkit. Foundation** : pacchetto principale per MRTK.</span><span class="sxs-lookup"><span data-stu-id="97001-119">**Microsoft.MixedReality.Toolkit.Foundation** – The core package for MRTK.</span></span>
1. <span data-ttu-id="97001-120">Opzionale Scegliere i pacchetti facoltativi MRTK.</span><span class="sxs-lookup"><span data-stu-id="97001-120">(Optional) Choose the MRTK optional packages.</span></span>
    - <span data-ttu-id="97001-121">**Microsoft. MixedReality. Toolkit. examples** : pacchetto che contiene tutti i nostri esempi.</span><span class="sxs-lookup"><span data-stu-id="97001-121">**Microsoft.MixedReality.Toolkit.Examples** – The package that contains all of our examples.</span></span>
    - <span data-ttu-id="97001-122">**Microsoft. MixedReality. Toolkit. Extensions** : pacchetto che contiene i servizi e/o i provider di dati delle estensioni.</span><span class="sxs-lookup"><span data-stu-id="97001-122">**Microsoft.MixedReality.Toolkit.Extensions** – The package that contains extensions services and/or data providers.</span></span>
    - <span data-ttu-id="97001-123">**Microsoft. MixedReality. Toolkit. Tools** : contiene alcuni degli strumenti forniti con MRTK (finestra di compilazione e così via).</span><span class="sxs-lookup"><span data-stu-id="97001-123">**Microsoft.MixedReality.Toolkit.Tools** – Contains some of the tooling that comes with MRTK (Build Window, etc).</span></span>

### <a name="updating-mrtk-nuget-packages"></a><span data-ttu-id="97001-124">Aggiornamento dei pacchetti NuGet MRTK</span><span class="sxs-lookup"><span data-stu-id="97001-124">Updating MRTK NuGet packages</span></span>

<span data-ttu-id="97001-125">I passaggi 1-2 precedenti dovranno essere eseguiti una sola volta per il progetto e l'aggiornamento è un passaggio molto più semplice.</span><span class="sxs-lookup"><span data-stu-id="97001-125">Steps 1-2 above will only need to be done once for the project, and the update is a much simpler step.</span></span> <span data-ttu-id="97001-126">Quando i pacchetti più recenti sono disponibili in NuGet.org (inclusa la versione preliminare), seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="97001-126">Once newer packages are available on NuGet.org (including prerelease), follow these steps:</span></span>

1. <span data-ttu-id="97001-127">Nella barra dei menu di Unity fare clic su **NuGet**  >  **Gestisci pacchetti NuGet**</span><span class="sxs-lookup"><span data-stu-id="97001-127">In the Unity menu bar, click on **NuGet** > **Manage NuGet Packages**</span></span>
1. <span data-ttu-id="97001-128">Passare alla scheda **aggiornamenti** .</span><span class="sxs-lookup"><span data-stu-id="97001-128">Switch to the **Updates** tab.</span></span>
    - <span data-ttu-id="97001-129">Se si desidera ottenere la versione provvisoria più recente, selezionare la casella di controllo **Mostra versione preliminare** .</span><span class="sxs-lookup"><span data-stu-id="97001-129">Check the **Show prerelease** box if you want to get latest prerelease version.</span></span>
1. <span data-ttu-id="97001-130">Aggiornare i pacchetti desiderati.</span><span class="sxs-lookup"><span data-stu-id="97001-130">Update the packages desired.</span></span>

## <a name="nuget-package-considerations"></a><span data-ttu-id="97001-131">Considerazioni sui pacchetti NuGet</span><span class="sxs-lookup"><span data-stu-id="97001-131">NuGet package considerations</span></span>

<span data-ttu-id="97001-132">Il rilascio di MRTK come pacchetto NuGet è un nuovo meccanismo di distribuzione che viene esaminato e ci sono due vantaggi chiave e considerazioni che è necessario apportare quando si sceglie se utilizzare la versione NuGet di MRTK.</span><span class="sxs-lookup"><span data-stu-id="97001-132">The release of MRTK as NuGet package is a new delivery mechanism being explored and there are a couple of key benefits and considerations one must make when choosing whether to consume the NuGet version of MRTK.</span></span>

### <a name="migrating-to-nuget-from-unitypackage-or-source-not-yet-supported"></a><span data-ttu-id="97001-133">Migrazione a NuGet da. file unitypackage Tools o source (non ancora supportata)</span><span class="sxs-lookup"><span data-stu-id="97001-133">Migrating to NuGet from .unitypackage or source (not yet supported)</span></span>

<span data-ttu-id="97001-134">Il pacchetto NuGet è costituito da binari compilati e non da file script separati. gli identificatori degli asset di script C# sono diversi.</span><span class="sxs-lookup"><span data-stu-id="97001-134">NuGet package consists of compiled binaries as opposed to loose script files, and the C# script asset identifiers are different.</span></span> <span data-ttu-id="97001-135">Di conseguenza, gli asset come i prefabbricati nel pacchetto MRTK sono stati aggiornati per fare riferimento allo script compilato appropriato.</span><span class="sxs-lookup"><span data-stu-id="97001-135">As such, the assets like prefabs in the MRTK package have been updated to reference the appropriate compiled script.</span></span> <span data-ttu-id="97001-136">Un progetto che usa la versione con estensione file unitypackage Tools o source di MRTK dovrà ridestinare anche le proprie risorse e anche se è presente codice per questo scenario non è ancora supportato.</span><span class="sxs-lookup"><span data-stu-id="97001-136">A project using the .unitypackage or source version of MRTK will have to re-target its assets as well, and although there is code for it this is not a supported scenario, yet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="97001-137">Non è attualmente supportata la migrazione a NuGet da. file unitypackage Tools o source.</span><span class="sxs-lookup"><span data-stu-id="97001-137">There is no currently supported way of migrating to NuGet from .unitypackage or source.</span></span> <span data-ttu-id="97001-138">Questo cambiamento verrà modificato quando si continua a sviluppare questo meccanismo di recapito.</span><span class="sxs-lookup"><span data-stu-id="97001-138">This will change as we continue development on this delivery mechanism.</span></span>

### <a name="compiled-binaries-nuget-vs-source-files-unitypackage"></a><span data-ttu-id="97001-139">File binari compilati (NuGet) e file di origine (con estensione file unitypackage Tools)</span><span class="sxs-lookup"><span data-stu-id="97001-139">Compiled binaries (NuGet) vs source files (.unitypackage)</span></span>

<span data-ttu-id="97001-140">Poiché il pacchetto NuGet contiene i binari compilati anziché gli script, questo presenta due vantaggi principali:</span><span class="sxs-lookup"><span data-stu-id="97001-140">Since the NuGet package contains the compiled binaries instead of scripts, this has two major advantages:</span></span>

- <span data-ttu-id="97001-141">Tempo di compilazione ridotto</span><span class="sxs-lookup"><span data-stu-id="97001-141">Reduced compilation time</span></span>
- <span data-ttu-id="97001-142">Un numero notevolmente inferiore di file di progetto C# in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="97001-142">Considerably fewer C# project files in Visual Studio</span></span>

### <a name="debugging-mixed-reality-toolkit"></a><span data-ttu-id="97001-143">Debug del Toolkit per realtà mista</span><span class="sxs-lookup"><span data-stu-id="97001-143">Debugging Mixed Reality Toolkit</span></span>

<span data-ttu-id="97001-144">Esistono problemi noti relativi a Unity & Visual Studio Tools per Unity che impediscono il debug di un PDB nel debugger di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="97001-144">There are known issues with Unity & Visual Studio Tools for Unity that prevent a PDB from being easily debugged in Visual Studio Debugger.</span></span> <span data-ttu-id="97001-145">Quindi, anche se il pacchetto viene fornito con PDB e l'origine incorporata, il debug delle dll è possibile solo se è stato compilato localmente (leggere più avanti).</span><span class="sxs-lookup"><span data-stu-id="97001-145">So although the package comes with PDBs and source embedded, debugging the DLLs is possible only if it was locally built (read further).</span></span> <span data-ttu-id="97001-146">Esiste una soluzione alternativa compilata come parte di [MSBuildForUnity](https://github.com/microsoft/MSBuildForUnity/), più aggiornamenti in quel momento.</span><span class="sxs-lookup"><span data-stu-id="97001-146">There is a workaround being built as part of [MSBuildForUnity](https://github.com/microsoft/MSBuildForUnity/), more updates on that later.</span></span>

## <a name="locally-building-the-nuget-package"></a><span data-ttu-id="97001-147">Compilazione locale del pacchetto NuGet</span><span class="sxs-lookup"><span data-stu-id="97001-147">Locally building the NuGet package</span></span>

<span data-ttu-id="97001-148">Con l'origine più recente di MRTK, è possibile compilare il pacchetto NuGet localmente e configurare NuGetForUnity per selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="97001-148">With the latest source from MRTK, you can build the NuGet package locally and configure NuGetForUnity to pick it up.</span></span>

1. <span data-ttu-id="97001-149">Scaricare la versione più recente dell'origine MRTK.</span><span class="sxs-lookup"><span data-stu-id="97001-149">Download the latest MRTK source.</span></span>
1. <span data-ttu-id="97001-150">Eseguire lo `scripts\packaging\createnugetpackages.ps1` script di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="97001-150">Execute the `scripts\packaging\createnugetpackages.ps1` powershell script.</span></span>
    - <span data-ttu-id="97001-151">Specificare il `-UnityDirectory` flag passando la cartella dell'editor dell'installazione di Unity</span><span class="sxs-lookup"><span data-stu-id="97001-151">Specify the `-UnityDirectory` flag by passing the Editor folder of your Unity installation</span></span>
    - <span data-ttu-id="97001-152">Specificare il `-Version` del pacchetto da creare, nel formato x. x. x.</span><span class="sxs-lookup"><span data-stu-id="97001-152">Specify the `-Version` of the package to create, in x.x.x format.</span></span> <span data-ttu-id="97001-153">**Verificare che la versione sia superiore a quella disponibile in NuGet.org**</span><span class="sxs-lookup"><span data-stu-id="97001-153">**Make sure the version is higher than available on NuGet.org**</span></span>
    - <span data-ttu-id="97001-154">**Esempio:** `.\createnugetpackages.ps1 -UnityDirectory "C:\Program Files\Unity\Hub\Editor\2018.4.14f1\Editor" -Version 2.3.2`</span><span class="sxs-lookup"><span data-stu-id="97001-154">**Example:** `.\createnugetpackages.ps1 -UnityDirectory "C:\Program Files\Unity\Hub\Editor\2018.4.14f1\Editor" -Version 2.3.2`</span></span>
1. <span data-ttu-id="97001-155">Una volta completata la compilazione, aprire il progetto di destinazione con i pacchetti NuGet.</span><span class="sxs-lookup"><span data-stu-id="97001-155">After the build succeeds, open the destination project with NuGet packages.</span></span>
    - <span data-ttu-id="97001-156">Fare clic sul menu **modifica**  >  **Preferenze...**</span><span class="sxs-lookup"><span data-stu-id="97001-156">Click on the menu **Edit** > **Preferences...**</span></span>

        ![Modifica la voce di menu preferenze](../Images/NuGet/ProjectPreferences.png)
    - <span data-ttu-id="97001-158">A sinistra, trovare **NuGet per la scheda Unity** .</span><span class="sxs-lookup"><span data-stu-id="97001-158">On the left, find **NuGet for Unity** tab.</span></span>

        ![Modifica la voce di menu preferenze](../Images/NuGet/NuGetForUnityPreferencesTab.png)
    - <span data-ttu-id="97001-160">Premere **Aggiungi nuova origine** e sostituire **source_path** con il `<Path to your Repository>\NuGet\artifacts`</span><span class="sxs-lookup"><span data-stu-id="97001-160">Press **Add New Source** and replace **source_path** with the `<Path to your Repository>\NuGet\artifacts`</span></span>

        ![Modifica la voce di menu preferenze](../Images/NuGet/AddNewSource.png)
    - <span data-ttu-id="97001-162">Nella parte inferiore, fare clic sul pulsante **Salva** .</span><span class="sxs-lookup"><span data-stu-id="97001-162">At the bottom, press the **Save** button.</span></span>

        ![Modifica la voce di menu preferenze](../Images/NuGet/SaveNewSource.png)
1. <span data-ttu-id="97001-164">Se la prima volta che si compila o la versione è stata incrementata, seguire il processo di aggiornamento:</span><span class="sxs-lookup"><span data-stu-id="97001-164">If this your first time building, or the version was incremented, follow the update process:</span></span>
    1. <span data-ttu-id="97001-165">Nella barra dei menu di Unity fare clic su **NuGet**  >  **Gestisci pacchetti NuGet**.</span><span class="sxs-lookup"><span data-stu-id="97001-165">In the Unity menu bar, click on **NuGet** > **Manage NuGet Packages**.</span></span>

        ![Manage NuGet Packages](../Images/NuGet/ManageNuGetPackages.png)
    1. <span data-ttu-id="97001-167">Passare alla scheda **aggiornamenti** .</span><span class="sxs-lookup"><span data-stu-id="97001-167">Switch to the **Updates** tab.</span></span>

        ![Manage NuGet Packages](../Images/NuGet/UpdatesTab.png)
    1. <span data-ttu-id="97001-169">Aggiornare i pacchetti alla versione appena compilata desiderata.</span><span class="sxs-lookup"><span data-stu-id="97001-169">Update the packages to the version you just built desired.</span></span>
1. <span data-ttu-id="97001-170">In caso contrario, è sufficiente eliminare la `Assets\Packages` cartella e consentire a NuGetForUnity di ripristinare i pacchetti.</span><span class="sxs-lookup"><span data-stu-id="97001-170">Otherwise, just delete the `Assets\Packages` folder and let NuGetForUnity restore the packages.</span></span>

## <a name="see-also"></a><span data-ttu-id="97001-171">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="97001-171">See also</span></span>

- [<span data-ttu-id="97001-172">Compilazione e distribuzione di MRTK</span><span class="sxs-lookup"><span data-stu-id="97001-172">Building and Deploying MRTK</span></span>](../../updates-deployment/BuildAndDeploy.md)
- [<span data-ttu-id="97001-173">Contenuto del pacchetto MRTK</span><span class="sxs-lookup"><span data-stu-id="97001-173">MRTK Package Contents</span></span>](MRTK_PackageContents.md)
