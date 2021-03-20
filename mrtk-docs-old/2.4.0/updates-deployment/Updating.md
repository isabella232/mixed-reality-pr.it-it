---
title: Aggiornamento
description: Documentazione per la migrazione da una versione precedente di MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: de331582be7b48bffc99ad914f0e648854bae937
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687681"
---
# <a name="updating-the-microsoft-mixed-reality-toolkit"></a><span data-ttu-id="14d80-104">Aggiornamento di Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="14d80-104">Updating the Microsoft Mixed Reality Toolkit</span></span>

- [<span data-ttu-id="14d80-105">Aggiornamento a una nuova versione di MRTK</span><span class="sxs-lookup"><span data-stu-id="14d80-105">Upgrading to a new version of MRTK</span></span>](#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="14d80-106">da 2.3.0 a 2.4.0</span><span class="sxs-lookup"><span data-stu-id="14d80-106">2.3.0 to 2.4.0</span></span>](#updating-230-to-240)
- [<span data-ttu-id="14d80-107">da 2.2.0 a 2.3.0</span><span class="sxs-lookup"><span data-stu-id="14d80-107">2.2.0 to 2.3.0</span></span>](#updating-220-to-230)
- [<span data-ttu-id="14d80-108">da 2.1.0 a 2.2.0</span><span class="sxs-lookup"><span data-stu-id="14d80-108">2.1.0 to 2.2.0</span></span>](#updating-210-to-220)
- [<span data-ttu-id="14d80-109">2.0.0 a 2.1.0</span><span class="sxs-lookup"><span data-stu-id="14d80-109">2.0.0 to 2.1.0</span></span>](#updating-200-to-210)
- [<span data-ttu-id="14d80-110">Da RC2 a 2.0.0</span><span class="sxs-lookup"><span data-stu-id="14d80-110">RC2 to 2.0.0</span></span>](#updating-rc2-to-200)

## <a name="upgrading-to-a-new-version-of-mrtk"></a><span data-ttu-id="14d80-111">Aggiornamento a una nuova versione di MRTK</span><span class="sxs-lookup"><span data-stu-id="14d80-111">Upgrading to a new version of MRTK</span></span>

<span data-ttu-id="14d80-112">La versione 2.4.0 presenta alcune modifiche che potrebbero influisca sui progetti dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="14d80-112">The 2.4.0 release has some changes that may impact application projects.</span></span> <span data-ttu-id="14d80-113">I dettagli delle modifiche di rilievo, incluse le linee guida per la mitigazione, sono disponibili nell'articolo relativo all' [**aggiornamento di 2.3.0 a 2.4.0**](../updates-deployment/Updating.md#updating-230-to-240) .</span><span class="sxs-lookup"><span data-stu-id="14d80-113">Breaking change details, including mitigation guidance, can be found in the [**Updating 2.3.0 to 2.4.0**](../updates-deployment/Updating.md#updating-230-to-240) article.</span></span>

> [!NOTE]
> <span data-ttu-id="14d80-114">Al momento, non è supportata la commutazione tra l'uso di file con estensione file unitypackage Tools e NuGet.</span><span class="sxs-lookup"><span data-stu-id="14d80-114">At this time, it is not supported to switch between using .unitypackage files and NuGet.</span></span>

<span data-ttu-id="14d80-115">A *partire da 2.4.0, è consigliabile eseguire lo strumento di [migrazione](../features/Tools/MigrationWindow.md) dopo aver completato l'aggiornamento di MRTK*\* per correggere automaticamente e aggiornare i componenti deprecati e modificare le modifiche di rilievo.</span><span class="sxs-lookup"><span data-stu-id="14d80-115">*Starting with 2.4.0, it is strongly recommended to run the [migration tool](../features/Tools/MigrationWindow.md) after getting the MRTK update*\* to auto-fix and upgrade from deprecated components and adjust to breaking changes.</span></span> <span data-ttu-id="14d80-116">Lo strumento di migrazione fa parte del pacchetto di **strumenti** .</span><span class="sxs-lookup"><span data-stu-id="14d80-116">The migration tool is part of the **Tools** package.</span></span>

### <a name="unity-asset-unitypackage-files"></a><span data-ttu-id="14d80-117">File di asset Unity (con estensione file unitypackage Tools)</span><span class="sxs-lookup"><span data-stu-id="14d80-117">Unity asset (.unitypackage) files</span></span>

<span data-ttu-id="14d80-118">Per il percorso di aggiornamento più semplice, seguire questa procedura.</span><span class="sxs-lookup"><span data-stu-id="14d80-118">For the smoothest upgrade path, please use the following steps.</span></span>

1. <span data-ttu-id="14d80-119">Salvare una copia del progetto corrente, nel caso in cui si riscontrino eventuali strappi in qualsiasi punto della procedura di aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="14d80-119">Save a copy of your current project, in case you hit any snags at any point in the upgrade steps.</span></span>
1. <span data-ttu-id="14d80-120">Chiudi Unity</span><span class="sxs-lookup"><span data-stu-id="14d80-120">Close Unity</span></span>
1. <span data-ttu-id="14d80-121">All'interno della cartella *assets* eliminare la maggior parte delle cartelle **MixedRealityToolkit** insieme ai relativi file con estensione meta (il progetto potrebbe non avere tutte le cartelle elencate)</span><span class="sxs-lookup"><span data-stu-id="14d80-121">Inside the *Assets* folder, delete most of the **MixedRealityToolkit** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="14d80-122">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="14d80-122">MixedRealityToolkit</span></span>
    - <span data-ttu-id="14d80-123">MixedRealityToolkit. examples</span><span class="sxs-lookup"><span data-stu-id="14d80-123">MixedRealityToolkit.Examples</span></span>
    - <span data-ttu-id="14d80-124">MixedRealityToolkit. Extensions</span><span class="sxs-lookup"><span data-stu-id="14d80-124">MixedRealityToolkit.Extensions</span></span>
    > [!NOTE]
    > <span data-ttu-id="14d80-125">Se sono state installate estensioni aggiuntive, eseguire un backup prima di eliminare le cartelle.</span><span class="sxs-lookup"><span data-stu-id="14d80-125">If additional extensions have been installed, please make a backup prior to deleting these folders.</span></span>
    - <span data-ttu-id="14d80-126">MixedRealityToolkit. Providers</span><span class="sxs-lookup"><span data-stu-id="14d80-126">MixedRealityToolkit.Providers</span></span>
    - <span data-ttu-id="14d80-127">MixedRealityToolkit. SDK</span><span class="sxs-lookup"><span data-stu-id="14d80-127">MixedRealityToolkit.SDK</span></span>
    - <span data-ttu-id="14d80-128">MixedRealityToolkit. Services</span><span class="sxs-lookup"><span data-stu-id="14d80-128">MixedRealityToolkit.Services</span></span>
    - <span data-ttu-id="14d80-129">MixedRealityToolkit. staging</span><span class="sxs-lookup"><span data-stu-id="14d80-129">MixedRealityToolkit.Staging</span></span>
    > [!NOTE]
    > <span data-ttu-id="14d80-130">Il contenuto della cartella MixedRealityToolkit. staging è stato spostato nella cartella MixedRealityToolkit. Providers in MRTK 2.3.0.</span><span class="sxs-lookup"><span data-stu-id="14d80-130">The contents of the MixedRealityToolkit.Staging folder have been moved into the MixedRealityToolkit.Providers folder in MRTK 2.3.0.</span></span>
    - <span data-ttu-id="14d80-131">MixedRealityToolkit. Tools</span><span class="sxs-lookup"><span data-stu-id="14d80-131">MixedRealityToolkit.Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="14d80-132">Non eliminare la cartella **MixedRealityToolkit. generated** o il relativo file con estensione meta.</span><span class="sxs-lookup"><span data-stu-id="14d80-132">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="14d80-133">Elimina la cartella della **libreria**</span><span class="sxs-lookup"><span data-stu-id="14d80-133">Delete the **Library** folder</span></span>
1. <span data-ttu-id="14d80-134">Riaprire il progetto in Unity</span><span class="sxs-lookup"><span data-stu-id="14d80-134">Re-open the project in Unity</span></span>
1. <span data-ttu-id="14d80-135">Importare i nuovi pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="14d80-135">Import the new unity packages</span></span>
    - <span data-ttu-id="14d80-136">Foundation: _importare prima questo pacchetto_</span><span class="sxs-lookup"><span data-stu-id="14d80-136">Foundation - _Import this package first_</span></span>
    - <span data-ttu-id="14d80-137">Strumenti</span><span class="sxs-lookup"><span data-stu-id="14d80-137">Tools</span></span>
    - <span data-ttu-id="14d80-138">Opzionale Estensioni</span><span class="sxs-lookup"><span data-stu-id="14d80-138">(Optional) Extensions</span></span>
    > [!NOTE]
    > <span data-ttu-id="14d80-139">Se sono state installate estensioni aggiuntive, potrebbe essere necessario importarle nuovamente.</span><span class="sxs-lookup"><span data-stu-id="14d80-139">If additional extensions had been installed, they may need to be re-imported.</span></span>
    - <span data-ttu-id="14d80-140">Opzionale Esempi</span><span class="sxs-lookup"><span data-stu-id="14d80-140">(Optional) Examples</span></span>
1. <span data-ttu-id="14d80-141">Chiudere Unity ed eliminare la cartella **Library** .</span><span class="sxs-lookup"><span data-stu-id="14d80-141">Close Unity and delete the **Library** folder.</span></span> <span data-ttu-id="14d80-142">Questo passaggio è necessario per forzare Unity ad aggiornare il database asset e a riconciliare i profili personalizzati esistenti.</span><span class="sxs-lookup"><span data-stu-id="14d80-142">This step is necessary to force Unity to refresh its asset database and reconcile existing custom profiles.</span></span>
1. <span data-ttu-id="14d80-143">Avviare Unity e per ogni scena nel progetto</span><span class="sxs-lookup"><span data-stu-id="14d80-143">Launch Unity, and for each scene in the project</span></span>
    - <span data-ttu-id="14d80-144">Eliminare **MixedRealityToolkit** e **MixedRealityPlayspace**, se presente, dalla gerarchia.</span><span class="sxs-lookup"><span data-stu-id="14d80-144">Delete **MixedRealityToolkit** and **MixedRealityPlayspace**, if present, from the hierarchy.</span></span> <span data-ttu-id="14d80-145">Questa operazione eliminerà la fotocamera principale, ma verrà ricreata nel passaggio successivo.</span><span class="sxs-lookup"><span data-stu-id="14d80-145">This will delete the main camera, but it will be re-created in the next step.</span></span> <span data-ttu-id="14d80-146">Se una qualsiasi proprietà della fotocamera principale è stata modificata manualmente, sarà necessario riapplicarla manualmente una volta creata la nuova fotocamera.</span><span class="sxs-lookup"><span data-stu-id="14d80-146">If any properties of the main camera have been manually changed, these will have to be re-applied manually once the new camera is created.</span></span>
    - <span data-ttu-id="14d80-147">Selezionare **MixedRealityToolkit-> Aggiungi a scena e configura**</span><span class="sxs-lookup"><span data-stu-id="14d80-147">Select **MixedRealityToolkit -> Add to Scene and Configure**</span></span>
    - <span data-ttu-id="14d80-148">Selezionare **MixedRealityToolkit-> Utilities-> aggiornare-> i profili di mapping del controller** (necessario solo una volta). verranno aggiornati tutti i profili di mapping del controller personalizzato con assi e dati aggiornati, lasciando intatte le azioni di input personalizzate assegnate</span><span class="sxs-lookup"><span data-stu-id="14d80-148">Select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (only needs to be done once)       - This will update any custom controller mapping profiles with updated axes and data, while leaving your custom-assigned input actions intact</span></span>
1. <span data-ttu-id="14d80-149">Eseguire lo [strumento di migrazione](../features/Tools/MigrationWindow.md) ed eseguire lo strumento nel *progetto completo* per assicurarsi che tutto il codice venga aggiornato alla versione più recente.</span><span class="sxs-lookup"><span data-stu-id="14d80-149">Run the [migration tool](../features/Tools/MigrationWindow.md) and run the tool on the *Full Project* to ensure that all of your code is updated to the latest.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="14d80-150">Pacchetti NuGet</span><span class="sxs-lookup"><span data-stu-id="14d80-150">NuGet packages</span></span>

<span data-ttu-id="14d80-151">Se il progetto è stato creato usando i [pacchetti NuGet del Toolkit per realtà mista](../reference-docs/MRTKNuGetPackage.md), seguire questa procedura.</span><span class="sxs-lookup"><span data-stu-id="14d80-151">If your project was created using the [Mixed Reality Toolkit NuGet packages](../reference-docs/MRTKNuGetPackage.md), please use the following steps.</span></span>

1. <span data-ttu-id="14d80-152">Selezionare **nuget > Gestisci pacchetti NuGet**</span><span class="sxs-lookup"><span data-stu-id="14d80-152">Select **NuGet > Manage NuGet Packages**</span></span>
1. <span data-ttu-id="14d80-153">Selezionare la scheda **online** e fare clic su **Aggiorna** .</span><span class="sxs-lookup"><span data-stu-id="14d80-153">Select the **Online** tab and click **Refresh**</span></span>
1. <span data-ttu-id="14d80-154">Selezionare la scheda **installato**</span><span class="sxs-lookup"><span data-stu-id="14d80-154">Select the **Installed** tab</span></span>
1. <span data-ttu-id="14d80-155">Fare clic sul pulsante **Aggiorna** per ogni pacchetto installato</span><span class="sxs-lookup"><span data-stu-id="14d80-155">Click the **Update** button for each installed package</span></span>
    - <span data-ttu-id="14d80-156">Microsoft. MixedReality. Toolkit. Foundation</span><span class="sxs-lookup"><span data-stu-id="14d80-156">Microsoft.MixedReality.Toolkit.Foundation</span></span>
    - <span data-ttu-id="14d80-157">Microsoft. MixedReality. Toolkit. Tools</span><span class="sxs-lookup"><span data-stu-id="14d80-157">Microsoft.MixedReality.Toolkit.Tools</span></span>
    - <span data-ttu-id="14d80-158">Microsoft. MixedReality. Toolkit. Extensions</span><span class="sxs-lookup"><span data-stu-id="14d80-158">Microsoft.MixedReality.Toolkit.Extensions</span></span>
    - <span data-ttu-id="14d80-159">Microsoft. MixedReality. Toolkit. examples</span><span class="sxs-lookup"><span data-stu-id="14d80-159">Microsoft.MixedReality.Toolkit.Examples</span></span>
1. <span data-ttu-id="14d80-160">Chiudere e riaprire il progetto in Unity</span><span class="sxs-lookup"><span data-stu-id="14d80-160">Close and re-open the project in Unity</span></span>

## <a name="updating-230-to-240"></a><span data-ttu-id="14d80-161">Aggiornamento di 2.3.0 a 2.4.0</span><span class="sxs-lookup"><span data-stu-id="14d80-161">Updating 2.3.0 to 2.4.0</span></span>

<span data-ttu-id="14d80-162">[Rinomina cartella](#folder-renames-in-240) 
 [Modifiche API](#api-changes-in-240)</span><span class="sxs-lookup"><span data-stu-id="14d80-162">[Folder renames](#folder-renames-in-240)
[API changes](#api-changes-in-240)</span></span>

### <a name="folder-renames-in-240"></a><span data-ttu-id="14d80-163">Ridenominazione della cartella in 2.4.0</span><span class="sxs-lookup"><span data-stu-id="14d80-163">Folder renames in 2.4.0</span></span>

<span data-ttu-id="14d80-164">Le cartelle MixedRealityToolkit sono state rinominate e spostate in una gerarchia comune della versione 2,4.</span><span class="sxs-lookup"><span data-stu-id="14d80-164">The MixedRealityToolkit folders have been renamed and moved into a common hierarchy in version 2.4.</span></span> <span data-ttu-id="14d80-165">Se un'applicazione usa percorsi hardcoded per le risorse MRTK, sarà necessario aggiornarli in base alla tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="14d80-165">If an application uses hard coded paths to MRTK resources, they will need to be updated per the following table.</span></span>

| <span data-ttu-id="14d80-166">Cartella precedente</span><span class="sxs-lookup"><span data-stu-id="14d80-166">Previous Folder</span></span> | <span data-ttu-id="14d80-167">Nuova cartella</span><span class="sxs-lookup"><span data-stu-id="14d80-167">New Folder</span></span> |
| --- | --- |
| <span data-ttu-id="14d80-168">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="14d80-168">MixedRealityToolkit</span></span> | <span data-ttu-id="14d80-169">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="14d80-169">MRTK/Core</span></span> |
| <span data-ttu-id="14d80-170">MixedRealityToolkit. examples</span><span class="sxs-lookup"><span data-stu-id="14d80-170">MixedRealityToolkit.Examples</span></span> | <span data-ttu-id="14d80-171">MRTK/esempi</span><span class="sxs-lookup"><span data-stu-id="14d80-171">MRTK/Examples</span></span> |
| <span data-ttu-id="14d80-172">MixedRealityToolkit. Extensions</span><span class="sxs-lookup"><span data-stu-id="14d80-172">MixedRealityToolkit.Extensions</span></span> | <span data-ttu-id="14d80-173">MRTK/estensioni</span><span class="sxs-lookup"><span data-stu-id="14d80-173">MRTK/Extensions</span></span> |
| <span data-ttu-id="14d80-174">MixedRealityToolkit. Providers</span><span class="sxs-lookup"><span data-stu-id="14d80-174">MixedRealityToolkit.Providers</span></span> | <span data-ttu-id="14d80-175">MRTK/provider</span><span class="sxs-lookup"><span data-stu-id="14d80-175">MRTK/Providers</span></span> |
| <span data-ttu-id="14d80-176">MixedRealityToolkit. SDK</span><span class="sxs-lookup"><span data-stu-id="14d80-176">MixedRealityToolkit.SDK</span></span> | <span data-ttu-id="14d80-177">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="14d80-177">MRTK/SDK</span></span> |
| <span data-ttu-id="14d80-178">MixedRealityToolkit. Services</span><span class="sxs-lookup"><span data-stu-id="14d80-178">MixedRealityToolkit.Services</span></span> | <span data-ttu-id="14d80-179">MRTK/servizi</span><span class="sxs-lookup"><span data-stu-id="14d80-179">MRTK/Services</span></span> |
| <span data-ttu-id="14d80-180">MixedRealityToolkit. test</span><span class="sxs-lookup"><span data-stu-id="14d80-180">MixedRealityToolkit.Tests</span></span> | <span data-ttu-id="14d80-181">MRTK/test</span><span class="sxs-lookup"><span data-stu-id="14d80-181">MRTK/Tests</span></span> |
| <span data-ttu-id="14d80-182">MixedRealityToolkit. Tools</span><span class="sxs-lookup"><span data-stu-id="14d80-182">MixedRealityToolkit.Tools</span></span> | <span data-ttu-id="14d80-183">MRTK/strumenti</span><span class="sxs-lookup"><span data-stu-id="14d80-183">MRTK/Tools</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="14d80-184">`MixedRealityToolkit.Generated`Contiene i file generati dal cliente e rimane invariato.</span><span class="sxs-lookup"><span data-stu-id="14d80-184">The `MixedRealityToolkit.Generated` contains customer generated files and remains unchanged.</span></span>

### <a name="eye-gaze-setup-in-240"></a><span data-ttu-id="14d80-185">Configurazione degli sguardi in 2.4.0</span><span class="sxs-lookup"><span data-stu-id="14d80-185">Eye gaze setup in 2.4.0</span></span>

<span data-ttu-id="14d80-186">Questa versione di MRTK modifica i passaggi necessari per l'installazione di Eye sguardi.</span><span class="sxs-lookup"><span data-stu-id="14d80-186">This version of MRTK modifies the steps required for eye gaze setup.</span></span> <span data-ttu-id="14d80-187">È possibile trovare la casella di controllo _' IsEyeTrackingEnabled '_ nelle impostazioni di sguardi del profilo puntatore di input.</span><span class="sxs-lookup"><span data-stu-id="14d80-187">The _'IsEyeTrackingEnabled'_ checkbox can be found in the gaze settings of the input pointer profile.</span></span> <span data-ttu-id="14d80-188">Se si seleziona questa casella, verrà abilitato lo sguardo basato sull'occhio, anziché lo sguardo predefinito basato sulla testa.</span><span class="sxs-lookup"><span data-stu-id="14d80-188">Checking this box will enable eye based gaze, rather then the default head based gaze.</span></span>

<span data-ttu-id="14d80-189">Per ulteriori informazioni su queste modifiche e istruzioni complete per la configurazione della verifica degli occhi, vedere l'articolo relativo alla [Verifica](../features/EyeTracking/EyeTracking_BasicSetup.md) degli occhi.</span><span class="sxs-lookup"><span data-stu-id="14d80-189">For more information on these changes and complete instructions for eye tracking setup, please see the [eye tracking](../features/EyeTracking/EyeTracking_BasicSetup.md) article.</span></span>

### <a name="api-changes-in-240"></a><span data-ttu-id="14d80-190">Modifiche alle API in 2.4.0</span><span class="sxs-lookup"><span data-stu-id="14d80-190">API changes in 2.4.0</span></span>

<span data-ttu-id="14d80-191">**Classi controller personalizzate**</span><span class="sxs-lookup"><span data-stu-id="14d80-191">**Custom controller classes**</span></span>

<span data-ttu-id="14d80-192">Classi controller personalizzate in precedenza dovevano definire `SetupDefaultInteractions(Handedness)` .</span><span class="sxs-lookup"><span data-stu-id="14d80-192">Custom controller classes previously had to define `SetupDefaultInteractions(Handedness)`.</span></span> <span data-ttu-id="14d80-193">Questo metodo è stato reso obsoleto in 2,4, poiché il parametro di manualità era ridondante con la propria manualità della classe controller.</span><span class="sxs-lookup"><span data-stu-id="14d80-193">This method has been made obsolete in 2.4, as the handedness parameter was redundant with the controller class' own handedness.</span></span> <span data-ttu-id="14d80-194">Il nuovo metodo non dispone di parametri.</span><span class="sxs-lookup"><span data-stu-id="14d80-194">The new method has no parameters.</span></span> <span data-ttu-id="14d80-195">Inoltre, molte classi controller hanno definito questo metodo nello stesso modo ( `AssignControllerMappings(DefaultInteractions);` ), quindi la chiamata completa è stata sottoposta a refactoring in ed è stato `BaseController` eseguito un override facoltativo anziché obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="14d80-195">Additionally, many controller classes defined this the same way (`AssignControllerMappings(DefaultInteractions);`), so the full call has been refactored down into `BaseController` and made an optional override instead of required.</span></span>

<span data-ttu-id="14d80-196">**Proprietà degli sguardi**</span><span class="sxs-lookup"><span data-stu-id="14d80-196">**Eye Gaze properties**</span></span>

<span data-ttu-id="14d80-197">La `UseEyeTracking` proprietà dall' `GazeProvider` implementazione di `IMixedRealityEyeGazeProvider` è stata rinominata in `IsEyeTrackingEnabled` .</span><span class="sxs-lookup"><span data-stu-id="14d80-197">The `UseEyeTracking` property from `GazeProvider` implementation of `IMixedRealityEyeGazeProvider` was renamed to `IsEyeTrackingEnabled`.</span></span>

<span data-ttu-id="14d80-198">Se questa operazione è stata eseguita in precedenza...</span><span class="sxs-lookup"><span data-stu-id="14d80-198">If you did this previously...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

<span data-ttu-id="14d80-199">Esegui ora...</span><span class="sxs-lookup"><span data-stu-id="14d80-199">Do this now...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

<span data-ttu-id="14d80-200">**Proprietà di WindowsApiChecker**</span><span class="sxs-lookup"><span data-stu-id="14d80-200">**WindowsApiChecker properties**</span></span>

<span data-ttu-id="14d80-201">Le proprietà WindowsApiChecker seguenti sono state contrassegnate come obsolete.</span><span class="sxs-lookup"><span data-stu-id="14d80-201">The following WindowsApiChecker properties have been marked as obsolete.</span></span> <span data-ttu-id="14d80-202">Usare `IsMethodAvailable` `IsPropertyAvailable` o `IsTypeAvailable` .</span><span class="sxs-lookup"><span data-stu-id="14d80-202">Please use `IsMethodAvailable`, `IsPropertyAvailable` or `IsTypeAvailable`.</span></span>

- <span data-ttu-id="14d80-203">UniversalApiContractV8_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="14d80-203">UniversalApiContractV8_IsAvailable</span></span>
- <span data-ttu-id="14d80-204">UniversalApiContractV7_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="14d80-204">UniversalApiContractV7_IsAvailable</span></span>
- <span data-ttu-id="14d80-205">UniversalApiContractV6_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="14d80-205">UniversalApiContractV6_IsAvailable</span></span>
- <span data-ttu-id="14d80-206">UniversalApiContractV5_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="14d80-206">UniversalApiContractV5_IsAvailable</span></span>
- <span data-ttu-id="14d80-207">UniversalApiContractV4_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="14d80-207">UniversalApiContractV4_IsAvailable</span></span>
- <span data-ttu-id="14d80-208">UniversalApiContractV3_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="14d80-208">UniversalApiContractV3_IsAvailable</span></span>

<span data-ttu-id="14d80-209">Non sono previsti piani per aggiungere proprietà a WindowsApiChecker per le versioni future del contratto API.</span><span class="sxs-lookup"><span data-stu-id="14d80-209">There are no plans to add properties to WindowsApiChecker for future API contract versions.</span></span>

<span data-ttu-id="14d80-210">**GltfMeshPrimitiveAttributes di sola lettura**</span><span class="sxs-lookup"><span data-stu-id="14d80-210">**GltfMeshPrimitiveAttributes read-only**</span></span>

<span data-ttu-id="14d80-211">Gli attributi primitivi mesh gltf usati per essere impostati, sono ora di sola lettura.</span><span class="sxs-lookup"><span data-stu-id="14d80-211">The gltf mesh primitive attributes used to be settable, they are now read-only.</span></span> <span data-ttu-id="14d80-212">I valori verranno impostati una volta quando vengono deserializzati.</span><span class="sxs-lookup"><span data-stu-id="14d80-212">Their values will be set once when deserialized.</span></span>

### <a name="custom-button-icon-migration"></a><span data-ttu-id="14d80-213">Icona del pulsante personalizzata migrazione</span><span class="sxs-lookup"><span data-stu-id="14d80-213">Custom Button Icon Migration</span></span>

<span data-ttu-id="14d80-214">Nelle icone dei pulsanti personalizzate in precedenza è necessario assegnare un nuovo materiale al renderer quad del pulsante.</span><span class="sxs-lookup"><span data-stu-id="14d80-214">Previously custom button icons required assigning a new material to the button's quad renderer.</span></span> <span data-ttu-id="14d80-215">Questa operazione non è più necessaria e si consiglia di trasferire le trame delle icone personalizzate in un.</span><span class="sxs-lookup"><span data-stu-id="14d80-215">This is no longer necessary and we recommend moving custom icon textures into an IconSet.</span></span> <span data-ttu-id="14d80-216">Vengono conservati i materiali e le icone personalizzati esistenti.</span><span class="sxs-lookup"><span data-stu-id="14d80-216">Existing custom materials and icons are preserved.</span></span> <span data-ttu-id="14d80-217">Tuttavia, saranno meno ottimali fino a quando non vengono aggiornati.</span><span class="sxs-lookup"><span data-stu-id="14d80-217">However they will be less optimal until upgraded.</span></span>
<span data-ttu-id="14d80-218">Per aggiornare gli asset di tutti i pulsanti nel progetto al nuovo formato consigliato, usare ButtonConfigHelperMigrationHandler.</span><span class="sxs-lookup"><span data-stu-id="14d80-218">To upgrade the assets on all buttons in the project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="14d80-219">(Mixed Reality Toolkit-> Utilities-> finestra di migrazione > selezione del gestore della migrazione-> Microsoft. MixedReality. Toolkit. Utilities. ButtonConfigHelperMigrationHandler)</span><span class="sxs-lookup"><span data-stu-id="14d80-219">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

![Finestra di dialogo Aggiorna finestra](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="14d80-221">Se un'icona non viene trovata nel set di icone predefinito durante la migrazione, viene creato un set di icone personalizzato in MixedRealityToolkit. generated/CustomIconSets.</span><span class="sxs-lookup"><span data-stu-id="14d80-221">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="14d80-222">Una finestra di dialogo indicherà che questa operazione è stata eseguita.</span><span class="sxs-lookup"><span data-stu-id="14d80-222">A dialog will indicate that this has taken place.</span></span>

![Notifica dell'icona personalizzata](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a><span data-ttu-id="14d80-224">Aggiornamento di 2.2.0 a 2.3.0</span><span class="sxs-lookup"><span data-stu-id="14d80-224">Updating 2.2.0 to 2.3.0</span></span>

- [<span data-ttu-id="14d80-225">Modifiche all'API</span><span class="sxs-lookup"><span data-stu-id="14d80-225">API changes</span></span>](#api-changes-in-230)

### <a name="api-changes-in-230"></a><span data-ttu-id="14d80-226">Modifiche alle API in 2.3.0</span><span class="sxs-lookup"><span data-stu-id="14d80-226">API changes in 2.3.0</span></span>

<span data-ttu-id="14d80-227">**ControllerPoseSynchronizer**</span><span class="sxs-lookup"><span data-stu-id="14d80-227">**ControllerPoseSynchronizer**</span></span>

<span data-ttu-id="14d80-228">Il campo ControllerPoseSynchronizer. manualità privato è stato contrassegnato come obsoleto.</span><span class="sxs-lookup"><span data-stu-id="14d80-228">The private ControllerPoseSynchronizer.handedness field has been marked as obsolete.</span></span> <span data-ttu-id="14d80-229">Questa operazione dovrebbe avere un effetto minimo sulle applicazioni perché il campo non è visibile all'esterno della relativa classe.</span><span class="sxs-lookup"><span data-stu-id="14d80-229">This should have minimal impact on applications as the field is not visible outside of its class.</span></span>

<span data-ttu-id="14d80-230">Il metodo di impostazione della proprietà ControllerPoseSynchronizer. manualità è stato rimosso ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span><span class="sxs-lookup"><span data-stu-id="14d80-230">The public ControllerPoseSynchronizer.Handedness property's setter has been removed ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span></span>

<span data-ttu-id="14d80-231">**MSBuild per Unity**</span><span class="sxs-lookup"><span data-stu-id="14d80-231">**MSBuild for Unity**</span></span>

<span data-ttu-id="14d80-232">Questa versione di MRTK usa una versione più recente di MSBuild per Unity rispetto alle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="14d80-232">This version of MRTK uses a newer version of MSBuild for Unity than previous releases.</span></span> <span data-ttu-id="14d80-233">Durante il caricamento del progetto, se la versione precedente è elencata nel manifesto di gestione pacchetti Unity, viene visualizzata la finestra di dialogo di configurazione con l'opzione Abilita MSBuild per Unity selezionata.</span><span class="sxs-lookup"><span data-stu-id="14d80-233">During project load, if the older version is listed in the Unity Package Manger manifest, the configuration dialog will appear, with the Enable MSBuild for Unity option checked.</span></span> <span data-ttu-id="14d80-234">L'applicazione eseguirà un aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="14d80-234">Applying will perform an upgrade.</span></span>

<span data-ttu-id="14d80-235">**ScriptingUtilities**</span><span class="sxs-lookup"><span data-stu-id="14d80-235">**ScriptingUtilities**</span></span>

<span data-ttu-id="14d80-236">La classe ScriptingUtilities è stata contrassegnata come obsoleta ed è stata sostituita da ScriptUtilities nell'assembly Microsoft. MixedReality. Toolkit. Editor. Utilities.</span><span class="sxs-lookup"><span data-stu-id="14d80-236">The ScriptingUtilities class has been marked as obsolete and has been replaced by ScriptUtilities, in the Microsoft.MixedReality.Toolkit.Editor.Utilities assembly.</span></span> <span data-ttu-id="14d80-237">La nuova classe perfeziona il comportamento precedente e aggiunge il supporto per la rimozione delle definizioni di scripting.</span><span class="sxs-lookup"><span data-stu-id="14d80-237">The new class refines previous behavior and adds support for removing scripting definitions.</span></span>

<span data-ttu-id="14d80-238">Mentre il codice esistente continuerà a funzionare nella versione 2.3.0, è consigliabile eseguire l'aggiornamento alla nuova classe.</span><span class="sxs-lookup"><span data-stu-id="14d80-238">While existing code will continue to function in version 2.3.0, it is recommended to update to the new class.</span></span>

<span data-ttu-id="14d80-239">**ShellHandRayPointer**</span><span class="sxs-lookup"><span data-stu-id="14d80-239">**ShellHandRayPointer**</span></span>

<span data-ttu-id="14d80-240">I membri lineRendererSelected e lineRendererNoTarget della classe ShellHandRayPointer sono stati sostituiti rispettivamente da lineMaterialSelected e lineMaterialNoTarget ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span><span class="sxs-lookup"><span data-stu-id="14d80-240">The lineRendererSelected and lineRendererNoTarget members of the ShellHandRayPointer class have been replaced by lineMaterialSelected and lineMaterialNoTarget, respectively ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span></span>

<span data-ttu-id="14d80-241">Sostituire lineRendererSelected con lineMaterialSelected e/o lineRendererNoTarget con lineMaterialNoTarget per risolvere gli errori di compilazione.</span><span class="sxs-lookup"><span data-stu-id="14d80-241">Please replace lineRendererSelected with lineMaterialSelected and/or lineRendererNoTarget with lineMaterialNoTarget to resolve compile errors.</span></span>

<span data-ttu-id="14d80-242">**Startupbehavior facendo osservatore spaziale**</span><span class="sxs-lookup"><span data-stu-id="14d80-242">**Spatial observer StartupBehavior**</span></span>

<span data-ttu-id="14d80-243">Gli osservatori spaziali basati sulla `BaseSpatialObserver` classe ora rispettano il valore di startupbehavior facendo quando viene riabilitato ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span><span class="sxs-lookup"><span data-stu-id="14d80-243">Spatial observers built upon the `BaseSpatialObserver` class now honor the value of StartupBehavior when re-enabled ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span></span>

<span data-ttu-id="14d80-244">Non sono necessarie modifiche per sfruttare questa correzione.</span><span class="sxs-lookup"><span data-stu-id="14d80-244">No changes are required to take advantage of this fix.</span></span>

<span data-ttu-id="14d80-245">**Prefabbricati del controllo UX aggiornati per l'uso di PressableButton**</span><span class="sxs-lookup"><span data-stu-id="14d80-245">**UX control prefabs updated to use PressableButton**</span></span>

<span data-ttu-id="14d80-246">I prefabbricati seguenti usano ora il componente PressableButton anziché TouchHandler per l'interazione near ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span><span class="sxs-lookup"><span data-stu-id="14d80-246">The following prefabs are now using the PressableButton component instead of TouchHandler for near interaction ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span></span>

- <span data-ttu-id="14d80-247">AnimationButton</span><span class="sxs-lookup"><span data-stu-id="14d80-247">AnimationButton</span></span>
- <span data-ttu-id="14d80-248">Pulsante</span><span class="sxs-lookup"><span data-stu-id="14d80-248">Button</span></span>
- <span data-ttu-id="14d80-249">ButtonHoloLens1</span><span class="sxs-lookup"><span data-stu-id="14d80-249">ButtonHoloLens1</span></span>
- <span data-ttu-id="14d80-250">ButtonHoloLens1Toggle</span><span class="sxs-lookup"><span data-stu-id="14d80-250">ButtonHoloLens1Toggle</span></span>
- <span data-ttu-id="14d80-251">CheckBox</span><span class="sxs-lookup"><span data-stu-id="14d80-251">CheckBox</span></span>
- <span data-ttu-id="14d80-252">RadialSet</span><span class="sxs-lookup"><span data-stu-id="14d80-252">RadialSet</span></span>
- <span data-ttu-id="14d80-253">ToggleButton</span><span class="sxs-lookup"><span data-stu-id="14d80-253">ToggleButton</span></span>
- <span data-ttu-id="14d80-254">ToggleSwitch</span><span class="sxs-lookup"><span data-stu-id="14d80-254">ToggleSwitch</span></span>
- <span data-ttu-id="14d80-255">UnityUIButton</span><span class="sxs-lookup"><span data-stu-id="14d80-255">UnityUIButton</span></span>
- <span data-ttu-id="14d80-256">UnityUICheckboxButton</span><span class="sxs-lookup"><span data-stu-id="14d80-256">UnityUICheckboxButton</span></span>
- <span data-ttu-id="14d80-257">UnityUIRadialButton</span><span class="sxs-lookup"><span data-stu-id="14d80-257">UnityUIRadialButton</span></span>
- <span data-ttu-id="14d80-258">UnityUIToggleButton</span><span class="sxs-lookup"><span data-stu-id="14d80-258">UnityUIToggleButton</span></span>

<span data-ttu-id="14d80-259">Il codice dell'applicazione può richiedere l'aggiornamento a causa di questa modifica.</span><span class="sxs-lookup"><span data-stu-id="14d80-259">Application code may require updating due to this change.</span></span>

<span data-ttu-id="14d80-260">**Spazio dei nomi WindowsMixedRealityUtilities**</span><span class="sxs-lookup"><span data-stu-id="14d80-260">**WindowsMixedRealityUtilities namespace**</span></span>

<span data-ttu-id="14d80-261">Lo spazio dei nomi di WindowsMixedRealityUtilities è stato modificato da Microsoft. MixedReality. Toolkit. WindowsMixedReality. input a Microsoft. MixedReality. Toolkit. WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span><span class="sxs-lookup"><span data-stu-id="14d80-261">The namespace of WindowsMixedRealityUtilities changed from Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input to Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span></span>

<span data-ttu-id="14d80-262">Aggiornare #using le istruzioni per risolvere gli errori di compilazione.</span><span class="sxs-lookup"><span data-stu-id="14d80-262">Please update #using statements to resolve compile errors.</span></span>

## <a name="updating-210-to-220"></a><span data-ttu-id="14d80-263">Aggiornamento di 2.1.0 a 2.2.0</span><span class="sxs-lookup"><span data-stu-id="14d80-263">Updating 2.1.0 to 2.2.0</span></span>

- [<span data-ttu-id="14d80-264">Modifiche all'API</span><span class="sxs-lookup"><span data-stu-id="14d80-264">API changes</span></span>](#api-changes-in-220)

### <a name="api-changes-in-220"></a><span data-ttu-id="14d80-265">Modifiche alle API in 2.2.0</span><span class="sxs-lookup"><span data-stu-id="14d80-265">API changes in 2.2.0</span></span>

<span data-ttu-id="14d80-266">**IMixedRealityBoundarySystem. Contains**</span><span class="sxs-lookup"><span data-stu-id="14d80-266">**IMixedRealityBoundarySystem.Contains**</span></span>

<span data-ttu-id="14d80-267">Questo metodo ha eseguito in precedenza un'enumerazione sperimentale specifica definita da Unity.</span><span class="sxs-lookup"><span data-stu-id="14d80-267">This method previously took in a specific, Unity-defined experimental enum.</span></span> <span data-ttu-id="14d80-268">Ora accetta un'enumerazione definita da MRTK che è identica all'enumerazione Unity.</span><span class="sxs-lookup"><span data-stu-id="14d80-268">It now takes in an MRTK-defined enum that's identical to the Unity enum.</span></span> <span data-ttu-id="14d80-269">Questa modifica consente di preparare il MRTK per le API limite future di Unity.</span><span class="sxs-lookup"><span data-stu-id="14d80-269">This change helps prepare the MRTK for Unity's future boundary APIs.</span></span>

<span data-ttu-id="14d80-270">**MixedRealityServiceProfileAttribute**</span><span class="sxs-lookup"><span data-stu-id="14d80-270">**MixedRealityServiceProfileAttribute**</span></span>

<span data-ttu-id="14d80-271">Per descrivere meglio i requisiti per il supporto di un profilo, MixedRealityServiceProfileAttribute è stato aggiornato per aggiungere una raccolta facoltativa di tipi esclusi.</span><span class="sxs-lookup"><span data-stu-id="14d80-271">To better describe the requirements for supporting a profile, the MixedRealityServiceProfileAttribute has been updated to add an optional collection of excluded types.</span></span> <span data-ttu-id="14d80-272">Come parte di questa modifica, la proprietà ServiceType è stata modificata dal tipo al tipo [] ed è stata rinominata in RequiredTypes.</span><span class="sxs-lookup"><span data-stu-id="14d80-272">As part of this change, the ServiceType property has been changed from Type to Type[] and been renamed to RequiredTypes.</span></span>

<span data-ttu-id="14d80-273">È stata aggiunta anche una seconda proprietà, ExcludedTypes.</span><span class="sxs-lookup"><span data-stu-id="14d80-273">A second property, ExcludedTypes has also been added.</span></span>

## <a name="updating-200-to-210"></a><span data-ttu-id="14d80-274">Aggiornamento di 2.0.0 a 2.1.0</span><span class="sxs-lookup"><span data-stu-id="14d80-274">Updating 2.0.0 to 2.1.0</span></span>

- [<span data-ttu-id="14d80-275">Modifiche all'API</span><span class="sxs-lookup"><span data-stu-id="14d80-275">API changes</span></span>](#api-changes-in-210)
- [<span data-ttu-id="14d80-276">Modifiche del profilo</span><span class="sxs-lookup"><span data-stu-id="14d80-276">Profile changes</span></span>](#profile-changes-in-210)

### <a name="api-changes-in-210"></a><span data-ttu-id="14d80-277">Modifiche alle API in 2.1.0</span><span class="sxs-lookup"><span data-stu-id="14d80-277">API changes in 2.1.0</span></span>

<span data-ttu-id="14d80-278">**BaseNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="14d80-278">**BaseNearInteractionTouchable**</span></span>

<span data-ttu-id="14d80-279">`BaseNearInteractionTouchable`È stato modificato per contrassegnare il `OnValidate` metodo come virtuale.</span><span class="sxs-lookup"><span data-stu-id="14d80-279">The `BaseNearInteractionTouchable` has been modified to mark the `OnValidate` method as virtual.</span></span> <span data-ttu-id="14d80-280">Le classi che estendono, `BaseNearInteractionTouchable` `NearInteractionTouchableUnityUI` ad esempio, sono state aggiornate per riflettere questa modifica.</span><span class="sxs-lookup"><span data-stu-id="14d80-280">Classes that extend `BaseNearInteractionTouchable` (ex: `NearInteractionTouchableUnityUI`) have been updated to reflect this change.</span></span>

<span data-ttu-id="14d80-281">**ColliderNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="14d80-281">**ColliderNearInteractionTouchable**</span></span>

<span data-ttu-id="14d80-282">La classe `ColliderNearInteractionTouchable` è stata deprecata.</span><span class="sxs-lookup"><span data-stu-id="14d80-282">The `ColliderNearInteractionTouchable` class has been deprecated.</span></span> <span data-ttu-id="14d80-283">Aggiornare i riferimenti al codice da usare `BaseNearInteractionTouchable` .</span><span class="sxs-lookup"><span data-stu-id="14d80-283">Please update code references to use `BaseNearInteractionTouchable`.</span></span>

<span data-ttu-id="14d80-284">**IMixedRealityMouseDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="14d80-284">**IMixedRealityMouseDeviceManager**</span></span>

<span data-ttu-id="14d80-285">**_Aggiunto_**</span><span class="sxs-lookup"><span data-stu-id="14d80-285">**_Added_**</span></span>

<span data-ttu-id="14d80-286">`IMixedRealityMouseDeviceManager` sono state aggiunte `CursorSpeed` le `WheelSpeed` proprietà e.</span><span class="sxs-lookup"><span data-stu-id="14d80-286">`IMixedRealityMouseDeviceManager` has been added `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="14d80-287">Queste proprietà consentono alle applicazioni di specificare un valore moltiplicatore in base al quale verrà ridimensionata rispettivamente la velocità del cursore e della rotellina.</span><span class="sxs-lookup"><span data-stu-id="14d80-287">These properties allow applications to specify a multiplier value by which the speed of the cursor and wheel, respectively will be scaled.</span></span>

<span data-ttu-id="14d80-288">Si tratta di una modifica sostanziale che richiede la modifica delle implementazioni di gestione dispositivi del mouse esistenti.</span><span class="sxs-lookup"><span data-stu-id="14d80-288">This is a breaking change and requires existing mouse device manager implementations to be modified .</span></span>

>[!NOTE]
><span data-ttu-id="14d80-289">Questa modifica non è compatibile con le versioni precedenti della versione 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="14d80-289">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="14d80-290">**_Deprecato_**</span><span class="sxs-lookup"><span data-stu-id="14d80-290">**_Deprecated_**</span></span>

<span data-ttu-id="14d80-291">La `MouseInputProfile` proprietà è stata contrassegnata come obsoleta e verrà rimossa da una versione futura di Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="14d80-291">The `MouseInputProfile` property has been marked as obsolete and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="14d80-292">Si consiglia di non usare più questa proprietà per il codice dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="14d80-292">It is recommended that application code no longer use this property.</span></span>

<span data-ttu-id="14d80-293">**Con cui**</span><span class="sxs-lookup"><span data-stu-id="14d80-293">**Interactable**</span></span>

<span data-ttu-id="14d80-294">I metodi e le proprietà seguenti sono stati deprecati e verranno rimossi da una versione futura di Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="14d80-294">The following methods and properties have been deprecated and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="14d80-295">È consigliabile aggiornare il codice dell'applicazione in base alle linee guida contenute nell'attributo obsolete e visualizzarle nella console di.</span><span class="sxs-lookup"><span data-stu-id="14d80-295">The recommendation is to update application code per the guidance contained in the Obsolete attribute and displayed in the console.</span></span>

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

<span data-ttu-id="14d80-296">**NearInteractionTouchableSurface**</span><span class="sxs-lookup"><span data-stu-id="14d80-296">**NearInteractionTouchableSurface**</span></span>

<span data-ttu-id="14d80-297">La `NearInteractionTouchableSurface` classe è stata aggiunta e ora funge da classe di base per `NearInteractionTouchable` e `NearInteractionTouchableUnityUI` .</span><span class="sxs-lookup"><span data-stu-id="14d80-297">The `NearInteractionTouchableSurface` class has been added and now serves as the base class for `NearInteractionTouchable` and `NearInteractionTouchableUnityUI`.</span></span>

### <a name="profile-changes-in-210"></a><span data-ttu-id="14d80-298">Modifiche del profilo in 2.1.0</span><span class="sxs-lookup"><span data-stu-id="14d80-298">Profile changes in 2.1.0</span></span>

<span data-ttu-id="14d80-299">**Profilo di rilevamento mano**</span><span class="sxs-lookup"><span data-stu-id="14d80-299">**Hand tracking profile**</span></span>

<span data-ttu-id="14d80-300">La mesh mano e le visualizzazioni congiunte dispongono ora di impostazioni distinte per l'editor e il lettore.</span><span class="sxs-lookup"><span data-stu-id="14d80-300">The hand mesh and joint visualizations now have a separate editor and player settings.</span></span> <span data-ttu-id="14d80-301">Il profilo di rilevamento della mano è stato aggiornato per consentire l'impostazione di queste visualizzazioni su; Niente, tutto, editor o lettore.</span><span class="sxs-lookup"><span data-stu-id="14d80-301">The hand tracking profile has been updated to allow for setting these visualizations to; Nothing, Everything, Editor or Player.</span></span>

![Modalità di visualizzazione mano](../features/Images/ReleaseNotes/HandTrackingVisualizationModes.png)

<span data-ttu-id="14d80-303">Potrebbe essere necessario aggiornare i profili di rilevamento mano personalizzati per funzionare correttamente con la versione 2.1.0.</span><span class="sxs-lookup"><span data-stu-id="14d80-303">Custom hand tracking profiles may need to be updated to work correctly with version 2.1.0.</span></span>

>[!NOTE]
><span data-ttu-id="14d80-304">Questa modifica non è compatibile con le versioni precedenti della versione 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="14d80-304">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="14d80-305">**Profilo simulazione di input**</span><span class="sxs-lookup"><span data-stu-id="14d80-305">**Input simulation profile**</span></span>

<span data-ttu-id="14d80-306">Il sistema di simulazione di input è stato aggiornato, che consente di modificare alcune impostazioni nel profilo di simulazione di input.</span><span class="sxs-lookup"><span data-stu-id="14d80-306">The input simulation system has been upgraded, which changes a few settings in the input simulation profile.</span></span> <span data-ttu-id="14d80-307">Non è possibile eseguire la migrazione automatica di alcune modifiche e gli utenti potrebbero rilevare che i profili utilizzano valori predefiniti.</span><span class="sxs-lookup"><span data-stu-id="14d80-307">Some changes can not be migrated automatically and users may find that profiles are using default values.</span></span>

1. <span data-ttu-id="14d80-308">Tutti i binding dei pulsanti del mouse e del KeyCode nel profilo sono stati sostituiti con uno `KeyBinding` struct generico, che archivia il tipo di binding (chiave o mouse), nonché il codice di associazione effettivo (rispettivamente, il numero di tasto del mouse o il prefisso).</span><span class="sxs-lookup"><span data-stu-id="14d80-308">All KeyCode and mouse button bindings in the profile have been replaced with a generic `KeyBinding` struct, which stores the type of binding (key or mouse) as well as the actual binding code (KeyCode or mouse button number respectively).</span></span> <span data-ttu-id="14d80-309">Lo struct dispone di un proprio controllo, che consente la visualizzazione unificata e offre uno strumento di associazione automatica per impostare rapidamente le combinazioni di tasti premendo la rispettiva chiave invece di selezionare da un elenco a discesa di grandi dimensioni.</span><span class="sxs-lookup"><span data-stu-id="14d80-309">The struct has its own inspector, which allows unified display and offers an "auto-bind" tool to quickly set key bindings by pressing the respective key instead of selecting from a huge dropdown list.</span></span>

    - <span data-ttu-id="14d80-310">FastControlKey</span><span class="sxs-lookup"><span data-stu-id="14d80-310">FastControlKey</span></span>
    - <span data-ttu-id="14d80-311">ToggleLeftHandKey</span><span class="sxs-lookup"><span data-stu-id="14d80-311">ToggleLeftHandKey</span></span>
    - <span data-ttu-id="14d80-312">ToggleRightHandKey</span><span class="sxs-lookup"><span data-stu-id="14d80-312">ToggleRightHandKey</span></span>
    - <span data-ttu-id="14d80-313">LeftHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="14d80-313">LeftHandManipulationKey</span></span>
    - <span data-ttu-id="14d80-314">RightHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="14d80-314">RightHandManipulationKey</span></span>

1. <span data-ttu-id="14d80-315">`MouseLookToggle` in precedenza era incluso nell' `MouseLookButton` enum come `InputSimulationMouseButton.Focused` , ora è un'opzione separata.</span><span class="sxs-lookup"><span data-stu-id="14d80-315">`MouseLookToggle` was previously included in the `MouseLookButton` enum as `InputSimulationMouseButton.Focused`, it is now a separate option.</span></span> <span data-ttu-id="14d80-316">Se abilitata, la fotocamera continuerà a ruotare con il mouse dopo aver rilasciato il pulsante, fino a quando non viene premuto il tasto di escape.</span><span class="sxs-lookup"><span data-stu-id="14d80-316">When enabled, the camera will keep rotating with the mouse after releasing the button, until the escape key is pressed.</span></span>
1. <span data-ttu-id="14d80-317">`HandDepthMultiplier` il valore predefinito è stato abbassato da 0,1 a 0,03 per adattare alcune modifiche alla simulazione di input.</span><span class="sxs-lookup"><span data-stu-id="14d80-317">`HandDepthMultiplier` default value has been lowered from 0.1 to 0.03 to accommodate some changes to the input simulation.</span></span> <span data-ttu-id="14d80-318">Se lo scorrimento della fotocamera si sposta troppo rapidamente, provare a ridurre questo valore.</span><span class="sxs-lookup"><span data-stu-id="14d80-318">If the camera moves too fast when scrolling, try lowering this value.</span></span>
1. <span data-ttu-id="14d80-319">Le chiavi per la rotazione delle mani sono state rimosse. la rotazione della mano è ora controllata anche dal mouse.</span><span class="sxs-lookup"><span data-stu-id="14d80-319">Keys for rotating hands have been removed, hand rotation is now controlled by the mouse as well.</span></span> <span data-ttu-id="14d80-320">Tenendo premuto `HandRotateButton` (CTRL) insieme alla chiave di manipolazione a sinistra/destra (LShift/spazio), viene abilitata la rotazione della mano.</span><span class="sxs-lookup"><span data-stu-id="14d80-320">Holding `HandRotateButton` (Ctrl) together with the left/right hand manipulation key (LShift/Space) will enable hand rotation.</span></span>
1. <span data-ttu-id="14d80-321">È stato introdotto un nuovo asse "UpDown" nell'elenco degli assi di input.</span><span class="sxs-lookup"><span data-stu-id="14d80-321">A new axis "UpDown" has been introduced to the input axis list.</span></span> <span data-ttu-id="14d80-322">Questo controlla lo spostamento della fotocamera in verticale e il valore predefinito per le chiavi Q/E, nonché i pulsanti del trigger del controller.</span><span class="sxs-lookup"><span data-stu-id="14d80-322">This controls camera movement in the vertical and defaults to Q/E keys as well as the controller trigger buttons.</span></span>

<span data-ttu-id="14d80-323">Per ulteriori informazioni su queste modifiche, vedere l'articolo relativo al [servizio di simulazione input](../features/InputSimulation/InputSimulationService.md) .</span><span class="sxs-lookup"><span data-stu-id="14d80-323">For more information on these changes, please see the [input simulation service](../features/InputSimulation/InputSimulationService.md) article.</span></span>

<span data-ttu-id="14d80-324">**Profilo provider di dati del mouse**</span><span class="sxs-lookup"><span data-stu-id="14d80-324">**Mouse data provider profile**</span></span>

<span data-ttu-id="14d80-325">Il profilo del provider di dati del mouse è stato aggiornato per esporre le nuove `CursorSpeed` `WheelSpeed` proprietà e.</span><span class="sxs-lookup"><span data-stu-id="14d80-325">The mouse data provider profile has been updated to expose the new `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="14d80-326">Ai profili personalizzati esistenti verranno automaticamente specificati i valori predefiniti.</span><span class="sxs-lookup"><span data-stu-id="14d80-326">Existing custom profiles will automatically have default values provided.</span></span> <span data-ttu-id="14d80-327">Quando il profilo viene salvato, questi nuovi valori saranno resi permanente.</span><span class="sxs-lookup"><span data-stu-id="14d80-327">When the profile is saved, these new values will be persisted.</span></span>

<span data-ttu-id="14d80-328">**Profilo di mapping del controller**</span><span class="sxs-lookup"><span data-stu-id="14d80-328">**Controller mapping profile**</span></span>

<span data-ttu-id="14d80-329">Alcuni assi e tipi di input sono stati aggiornati in 2.1.0, in particolare per la piattaforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="14d80-329">Some axes and input types have been updated in 2.1.0, especially around the OpenVR platform.</span></span> <span data-ttu-id="14d80-330">Quando si esegue l'aggiornamento, assicurarsi di selezionare **MixedRealityToolkit-> Utilities-> i profili di mapping del controller di aggiornamento->** .</span><span class="sxs-lookup"><span data-stu-id="14d80-330">Please be sure to select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** when upgrading.</span></span> <span data-ttu-id="14d80-331">In questo caso i profili di mapping del controller personalizzato vengono aggiornati con gli assi e i dati aggiornati, lasciando intatti le azioni di input personalizzate.</span><span class="sxs-lookup"><span data-stu-id="14d80-331">This will update any custom Controller Mapping Profiles with the updated axes and data, while leaving your custom-assigned input actions intact.</span></span>

## <a name="updating-rc2-to-200"></a><span data-ttu-id="14d80-332">Aggiornamento RC2 alla 2.0.0</span><span class="sxs-lookup"><span data-stu-id="14d80-332">Updating RC2 to 2.0.0</span></span>

<span data-ttu-id="14d80-333">Tra le versioni RC2 e 2.0.0 del Toolkit Microsoft Mixed Reality, sono state apportate modifiche che potrebbero influito sui progetti esistenti.</span><span class="sxs-lookup"><span data-stu-id="14d80-333">Between the RC2 and 2.0.0 releases of the Microsoft Mixed Reality Toolkit, changes were made that may impact existing projects.</span></span> <span data-ttu-id="14d80-334">Questo documento descrive le modifiche e come aggiornare i progetti alla versione 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="14d80-334">This document describes those changes and how to update projects to the 2.0.0 release.</span></span>

- [<span data-ttu-id="14d80-335">Modifiche all'API</span><span class="sxs-lookup"><span data-stu-id="14d80-335">API changes</span></span>](#api-changes-in-200)
- [<span data-ttu-id="14d80-336">Modifiche al nome dell'assembly</span><span class="sxs-lookup"><span data-stu-id="14d80-336">Assembly name changes</span></span>](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a><span data-ttu-id="14d80-337">Modifiche alle API nella 2.0.0</span><span class="sxs-lookup"><span data-stu-id="14d80-337">API changes in 2.0.0</span></span>

<span data-ttu-id="14d80-338">Dalla versione RC2 sono state apportate alcune modifiche alle API, incluse alcune che potrebbero comportare interruzioni dei progetti esistenti.</span><span class="sxs-lookup"><span data-stu-id="14d80-338">Since the release of RC2, there have been a number of API changes including some that may break existing projects.</span></span> <span data-ttu-id="14d80-339">Le sezioni seguenti descrivono le modifiche che si sono verificate tra le versioni RC2 e 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="14d80-339">The following sections describe the changes that have occurred between the RC2 and 2.0.0 releases.</span></span>

<span data-ttu-id="14d80-340">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="14d80-340">**MixedRealityToolkit**</span></span>

<span data-ttu-id="14d80-341">Le seguenti proprietà pubbliche nell'oggetto MixedRealityToolkit sono state deprecate.</span><span class="sxs-lookup"><span data-stu-id="14d80-341">The following public properties on the MixedRealityToolkit object have been deprecated.</span></span>

- <span data-ttu-id="14d80-342">`RegisteredMixedRealityServices` non contiene più la raccolta di servizi e provider di dati delle estensioni registrate.</span><span class="sxs-lookup"><span data-stu-id="14d80-342">`RegisteredMixedRealityServices` no longer contains the collection of registered extensions services and data providers.</span></span>

<span data-ttu-id="14d80-343">Per accedere ai servizi di estensione, utilizzare `MixedRealityServiceRegistry.TryGetService<T>` .</span><span class="sxs-lookup"><span data-stu-id="14d80-343">To access extension services, use `MixedRealityServiceRegistry.TryGetService<T>`.</span></span> <span data-ttu-id="14d80-344">Per accedere ai provider di dati, eseguire il cast dell'istanza del servizio a [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) e utilizzare `GetDataProvider<T>` .</span><span class="sxs-lookup"><span data-stu-id="14d80-344">To access data providers, cast the service instance to [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) and use `GetDataProvider<T>`.</span></span>

<span data-ttu-id="14d80-345">Utilizzare [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) o [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) invece per le seguenti proprietà deprecate</span><span class="sxs-lookup"><span data-stu-id="14d80-345">Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) or [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) instead for the following deprecated properties</span></span>

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

<span data-ttu-id="14d80-346">**CoreServices**</span><span class="sxs-lookup"><span data-stu-id="14d80-346">**CoreServices**</span></span>

<span data-ttu-id="14d80-347">La [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) classe è la sostituzione per le funzioni di accesso di sistema statiche (ad esempio, BoundarySystem) trovate nell' `MixedRealityToolkit` oggetto.</span><span class="sxs-lookup"><span data-stu-id="14d80-347">The [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) class is the replacement for the static system accessors (ex: BoundarySystem) found in the `MixedRealityToolkit` object.</span></span>

>[!IMPORTANT]
><span data-ttu-id="14d80-348">Le `MixedRealityToolkit` funzioni di accesso di sistema sono state deprecate nella versione 2.0.0 e verranno rimosse in una versione futura di MRTK.</span><span class="sxs-lookup"><span data-stu-id="14d80-348">The `MixedRealityToolkit` system accessors have been deprecated in version 2.0.0 and will be removed in a future release of the MRTK.</span></span>

<span data-ttu-id="14d80-349">Nell'esempio di codice seguente vengono illustrati il vecchio e il nuovo modello.</span><span class="sxs-lookup"><span data-stu-id="14d80-349">The following code example illustrates the old and the new pattern.</span></span>

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

<span data-ttu-id="14d80-350">Se si utilizza la nuova classe CoreSystem, il codice dell'applicazione non richiederà l'aggiornamento se si modifica l'applicazione per l'utilizzo di un registrar del servizio diverso (ad esempio, uno dei responsabili del servizio sperimentale).</span><span class="sxs-lookup"><span data-stu-id="14d80-350">Using the new CoreSystem class will ensure that your application code will not need updating if you change the application to use a different service registrar (ex: one of the experimental service managers).</span></span>

<span data-ttu-id="14d80-351">**IMixedRealityRaycastProvider**</span><span class="sxs-lookup"><span data-stu-id="14d80-351">**IMixedRealityRaycastProvider**</span></span>

<span data-ttu-id="14d80-352">Con l'aggiunta di IMixedRealityRaycastProvider, il profilo di configurazione del sistema di input è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="14d80-352">With the addition of the IMixedRealityRaycastProvider, the input system configuration profile was changed.</span></span> <span data-ttu-id="14d80-353">Se si dispone di un profilo personalizzato, è possibile che vengano visualizzati gli errori nell'immagine seguente quando si esegue l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="14d80-353">If you have a custom profile, you may receive the errors in the following image when you run your application.</span></span>

![Selezione del provider Raycast](../features/Images/ReleaseNotes/UnableToRegisterRaycastProvider.png)

<span data-ttu-id="14d80-355">Per risolvere il problema, aggiungere un'istanza di IMixedRealityRaycastProvider al profilo di sistema di input.</span><span class="sxs-lookup"><span data-stu-id="14d80-355">To fix these, please add an IMixedRealityRaycastProvider instance to your input system profile.</span></span>

![Selezione del provider Raycast](../features/Images/ReleaseNotes/SelectRaycastProvider.png)

<span data-ttu-id="14d80-357">**Sistema di eventi**</span><span class="sxs-lookup"><span data-stu-id="14d80-357">**Event System**</span></span>

- <span data-ttu-id="14d80-358">I `IMixedRealityEventSystem` metodi dell'API obsoleti `Register` e `Unregister` sono stati contrassegnati come obsoleti.</span><span class="sxs-lookup"><span data-stu-id="14d80-358">The `IMixedRealityEventSystem` old API methods `Register` and `Unregister` have been marked as obsolete.</span></span> <span data-ttu-id="14d80-359">Sono conservati per la compatibilità con le versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="14d80-359">They are preserved for backwards compatibility.</span></span>
- <span data-ttu-id="14d80-360">`InputSystemGlobalListener` è stato contrassegnato come obsoleto.</span><span class="sxs-lookup"><span data-stu-id="14d80-360">`InputSystemGlobalListener` has been marked as obsolete.</span></span> <span data-ttu-id="14d80-361">La relativa funzionalità non è stata modificata.</span><span class="sxs-lookup"><span data-stu-id="14d80-361">Its functionality has not changed.</span></span>
- <span data-ttu-id="14d80-362">`BaseInputHandler` la classe base è stata modificata da `InputSystemGlobalListener` a `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="14d80-362">`BaseInputHandler` base class has been changed from `InputSystemGlobalListener` to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="14d80-363">Si tratta di una modifica di rilievo per qualsiasi discendente di `BaseInputHandler` .</span><span class="sxs-lookup"><span data-stu-id="14d80-363">This is a breaking change for any descendants of `BaseInputHandler`.</span></span>

<span data-ttu-id="14d80-364">**_Motivazione alla base della modifica_**</span><span class="sxs-lookup"><span data-stu-id="14d80-364">**_Motivation behind the change_**</span></span>

<span data-ttu-id="14d80-365">L'API del sistema di eventi precedente `Register` e `Unregister` potrebbe causare più problemi in fase di esecuzione, Main:</span><span class="sxs-lookup"><span data-stu-id="14d80-365">The old event system API `Register` and `Unregister` could potentially cause multiple issues in runtime, main being:</span></span>

- <span data-ttu-id="14d80-366">Se un componente si registra per gli eventi globali, riceverà gli eventi di input globali di *tutti i* tipi.</span><span class="sxs-lookup"><span data-stu-id="14d80-366">If a component registers for global events, it would receive global input events of *all* types.</span></span>
- <span data-ttu-id="14d80-367">Se uno dei componenti di un oggetto viene registrato per gli eventi di input globali, tutti i componenti di questo oggetto riceveranno gli eventi di input globali di *tutti i* tipi.</span><span class="sxs-lookup"><span data-stu-id="14d80-367">If one of the components on an object registers for global input events, all components on this object will receive global input events of *all* types.</span></span>
- <span data-ttu-id="14d80-368">Se due componenti sullo stesso oggetto si registrano in eventi globali e uno è disabilitato in fase di esecuzione, il secondo arresta la ricezione di eventi globali.</span><span class="sxs-lookup"><span data-stu-id="14d80-368">If two components on the same object register to global events, and then one is disabled in runtime, the second one stops receiving global events.</span></span>

<span data-ttu-id="14d80-369">Nuova API `RegisterHandler` e `UnregisterHandler` :</span><span class="sxs-lookup"><span data-stu-id="14d80-369">New API `RegisterHandler` and `UnregisterHandler`:</span></span>

- <span data-ttu-id="14d80-370">Fornisce un controllo esplicito e granulare su quali eventi di input devono essere ascoltati a livello globale e che devono essere basati su uno stato attivo.</span><span class="sxs-lookup"><span data-stu-id="14d80-370">Provides an explicit and granular control over which input events should be listened to globally and which should be focused-based.</span></span>
- <span data-ttu-id="14d80-371">Consente a più componenti sullo stesso oggetto di restare in ascolto di eventi globali in modo indipendente l'uno dall'altro.</span><span class="sxs-lookup"><span data-stu-id="14d80-371">Allows multiple components on the same object to listen to global events independently on each other.</span></span>

<span data-ttu-id="14d80-372">**_Come eseguire la migrazione_**</span><span class="sxs-lookup"><span data-stu-id="14d80-372">**_How to migrate_**</span></span>

- <span data-ttu-id="14d80-373">Se è stata chiamata l' `Register` / `Unregister` API direttamente prima, sostituire queste chiamate con le chiamate a `RegisterHandler` / `UnregisterHandler` .</span><span class="sxs-lookup"><span data-stu-id="14d80-373">If you have been calling `Register`/`Unregister` API directly before, replace these calls with calls to `RegisterHandler`/`UnregisterHandler`.</span></span> <span data-ttu-id="14d80-374">Usare le interfacce del gestore implementate come parametri generici.</span><span class="sxs-lookup"><span data-stu-id="14d80-374">Use handler interfaces you implement as generic parameters.</span></span> <span data-ttu-id="14d80-375">Se si implementano più interfacce e molte di esse sono in ascolto di eventi di input globali, chiamare `RegisterHandler` più volte.</span><span class="sxs-lookup"><span data-stu-id="14d80-375">If you implement multiple interfaces, and several of them listen to global input events, call `RegisterHandler` multiple times.</span></span>
- <span data-ttu-id="14d80-376">Se è stata ereditata da `InputSystemGlobalListener` , modificare l'ereditarietà in `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="14d80-376">If you have been inheriting from `InputSystemGlobalListener`, change inheritance to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="14d80-377">Implementano `RegisterHandlers` `UnregisterHandlers` metodi astratti e.</span><span class="sxs-lookup"><span data-stu-id="14d80-377">Implement `RegisterHandlers` and `UnregisterHandlers` abstract methods.</span></span> <span data-ttu-id="14d80-378">Nella chiamata di implementazione `inputSystem.RegisterHandler` ( `inputSystem.UnregisterHandler` ) per eseguire la registrazione in tutte le interfacce del gestore per cui si desidera ascoltare gli eventi globali.</span><span class="sxs-lookup"><span data-stu-id="14d80-378">In the implementation call `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) to register on all handler interfaces you want to listen global events for.</span></span>
- <span data-ttu-id="14d80-379">Se è stata ereditata da `BaseInputHandler` , implementare `RegisterHandlers` e i `UnregisterHandlers` metodi astratti (come per `InputSystemGlobalListener` ).</span><span class="sxs-lookup"><span data-stu-id="14d80-379">If you have been inheriting from `BaseInputHandler`, implement `RegisterHandlers` and `UnregisterHandlers` abstract methods (same as for `InputSystemGlobalListener`).</span></span>

<span data-ttu-id="14d80-380">**_Esempi di migrazione_**</span><span class="sxs-lookup"><span data-stu-id="14d80-380">**_Examples of migration_**</span></span>

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

<span data-ttu-id="14d80-381">**Consapevolezza spaziale**</span><span class="sxs-lookup"><span data-stu-id="14d80-381">**Spatial Awareness**</span></span>

<span data-ttu-id="14d80-382">Per le interfacce IMixedRealitySpatialAwarenessSystem e IMixedRealitySpatialAwarenessObserver sono state apportate più modifiche di rilievo, come descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="14d80-382">The IMixedRealitySpatialAwarenessSystem and IMixedRealitySpatialAwarenessObserver interfaces have taken multiple breaking changes as described below.</span></span>

<span data-ttu-id="14d80-383">**_Modifiche_**</span><span class="sxs-lookup"><span data-stu-id="14d80-383">**_Changes_**</span></span>

<span data-ttu-id="14d80-384">I metodi seguenti sono stati rinominati per descrivere meglio l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="14d80-384">The following method(s) have been renamed to better describe their usage.</span></span>

- <span data-ttu-id="14d80-385">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` è stato rinominato in `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` per chiarirne l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="14d80-385">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` has been renamed to `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` to clarify its usage.</span></span>

<span data-ttu-id="14d80-386">**_Aggiornamenti_**</span><span class="sxs-lookup"><span data-stu-id="14d80-386">**_Additions_**</span></span>

<span data-ttu-id="14d80-387">In base ai commenti e suggerimenti dei clienti, è stato aggiunto il supporto per semplificare la rimozione di dati di consapevolezza spaziale osservati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="14d80-387">Based on customer feedback, support for easy removal of previously observed spatial awareness data has been added.</span></span>

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

<span data-ttu-id="14d80-388">**Risolutori**</span><span class="sxs-lookup"><span data-stu-id="14d80-388">**Solvers**</span></span>

<span data-ttu-id="14d80-389">Alcuni componenti del Risolutore e la classe SolverHandler Manager sono stati modificati per correggere diversi bug e per un utilizzo più intuitivo.</span><span class="sxs-lookup"><span data-stu-id="14d80-389">Some solver components and the SolverHandler manager class has changed to fix various bugs and for more intuitive usage.</span></span>

<span data-ttu-id="14d80-390">**_SolverHandler_**</span><span class="sxs-lookup"><span data-stu-id="14d80-390">**_SolverHandler_**</span></span>

- <span data-ttu-id="14d80-391">La classe non si estende più da `ControllerFinder`</span><span class="sxs-lookup"><span data-stu-id="14d80-391">Class no longer extends from `ControllerFinder`</span></span>
- <span data-ttu-id="14d80-392">`TrackedObjectToReference` Proprietà pubblica deprecata ed è stata rinominata in `TrackedTargetType`</span><span class="sxs-lookup"><span data-stu-id="14d80-392">`TrackedObjectToReference` public property deprecated and has been renamed to `TrackedTargetType`</span></span>
- <span data-ttu-id="14d80-393">`TrackedObjectType` depreca i valori Left & right controller.</span><span class="sxs-lookup"><span data-stu-id="14d80-393">`TrackedObjectType` deprecates left & right controller values.</span></span> <span data-ttu-id="14d80-394">Usare invece `MotionController` `HandJoint` i valori o e aggiornare la nuova `TrackedHandedness` proprietà per limitare il rilevamento al controller sinistro o destro</span><span class="sxs-lookup"><span data-stu-id="14d80-394">Instead use `MotionController` or `HandJoint` values and update new `TrackedHandedness` property to limit tracking to left or right controller</span></span>

<span data-ttu-id="14d80-395">**_InBetween_**</span><span class="sxs-lookup"><span data-stu-id="14d80-395">**_InBetween_**</span></span>

- <span data-ttu-id="14d80-396">`TrackedObjectForSecondTransform` Proprietà pubblica deprecata ed è stata rinominata in `SecondTrackedObjectType`</span><span class="sxs-lookup"><span data-stu-id="14d80-396">`TrackedObjectForSecondTransform` public property deprecated and has been renamed to `SecondTrackedObjectType`</span></span>
- <span data-ttu-id="14d80-397">`AttachSecondTransformToNewTrackedObject()` è stato rimosso.</span><span class="sxs-lookup"><span data-stu-id="14d80-397">`AttachSecondTransformToNewTrackedObject()` has been removed.</span></span> <span data-ttu-id="14d80-398">Per aggiornare il Risolutore, modificare le proprietà pubbliche, ad esempio</span><span class="sxs-lookup"><span data-stu-id="14d80-398">To update the solver, modify the public properties (i.e</span></span> <span data-ttu-id="14d80-399">`SecondTrackedObjectType`)</span><span class="sxs-lookup"><span data-stu-id="14d80-399">`SecondTrackedObjectType`)</span></span>

<span data-ttu-id="14d80-400">**_SurfaceMagnetism_**</span><span class="sxs-lookup"><span data-stu-id="14d80-400">**_SurfaceMagnetism_**</span></span>

- <span data-ttu-id="14d80-401">`MaxDistance` Proprietà pubblica deprecata ed è stata rinominata in `MaxRaycastDistance`</span><span class="sxs-lookup"><span data-stu-id="14d80-401">`MaxDistance` public property deprecated and has been renamed to `MaxRaycastDistance`</span></span>
- <span data-ttu-id="14d80-402">`CloseDistance` Proprietà pubblica deprecata ed è stata rinominata in `ClosestDistance`</span><span class="sxs-lookup"><span data-stu-id="14d80-402">`CloseDistance` public property deprecated and has been renamed to `ClosestDistance`</span></span>
- <span data-ttu-id="14d80-403">Il valore predefinito per `RaycastDirectionMode` è ora `TrackedTargetForward` raycasts nella direzione della trasformazione di destinazione rilevata in avanti.</span><span class="sxs-lookup"><span data-stu-id="14d80-403">Default value for `RaycastDirectionMode` is now `TrackedTargetForward` which raycasts in the direction of the tracked target transform forward</span></span>
- <span data-ttu-id="14d80-404">`OrientationMode`i valori enum, `Vertical` e `Full` , sono stati rinominati `TrackedTarget` rispettivamente in e `SurfaceNormal`</span><span class="sxs-lookup"><span data-stu-id="14d80-404">`OrientationMode` enum values, `Vertical` and `Full`, have been renamed to `TrackedTarget` and `SurfaceNormal` respectively</span></span>
- <span data-ttu-id="14d80-405">`KeepOrientationVertical` è stata aggiunta la proprietà Public per controllare se l'orientamento del GameObject associato rimanga verticale</span><span class="sxs-lookup"><span data-stu-id="14d80-405">`KeepOrientationVertical` public property has been added to control whether orientation of associated GameObject remains vertical</span></span>

<span data-ttu-id="14d80-406">**Pulsanti**</span><span class="sxs-lookup"><span data-stu-id="14d80-406">**Buttons**</span></span>

- <span data-ttu-id="14d80-407">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton)`DistanceSpaceMode`la proprietà è ora impostata su `Local` come valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="14d80-407">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) now has `DistanceSpaceMode` property set to `Local` as default.</span></span> <span data-ttu-id="14d80-408">In questo modo è possibile ridimensionare i pulsanti mentre sono ancora stampabili</span><span class="sxs-lookup"><span data-stu-id="14d80-408">This allows buttons to be scaled while still be pressable</span></span>

<span data-ttu-id="14d80-409">**Sfera di ritaglio**</span><span class="sxs-lookup"><span data-stu-id="14d80-409">**Clipping Sphere**</span></span>

<span data-ttu-id="14d80-410">L'interfaccia ClippingSphere è cambiata per eseguire il mirroring delle API trovate in ClippingBox e ClippingPlane.</span><span class="sxs-lookup"><span data-stu-id="14d80-410">The ClippingSphere interface has changed to mirror the APIs found in the ClippingBox and ClippingPlane.</span></span>

<span data-ttu-id="14d80-411">La proprietà RADIUS di ClippingSphere viene ora calcolata in modo implicito in base alla scala di trasformazione.</span><span class="sxs-lookup"><span data-stu-id="14d80-411">The ClippingSphere's Radius property is now implicitly calculated based on the transform scale.</span></span> <span data-ttu-id="14d80-412">Prima che gli sviluppatori dovessero specificare il raggio di ClippingSphere nel controllo.</span><span class="sxs-lookup"><span data-stu-id="14d80-412">Before developers would have to specify the radius of the ClippingSphere in the inspector.</span></span> <span data-ttu-id="14d80-413">Se si vuole modificare il raggio, è sufficiente aggiornare la scala di trasformazione della trasformazione come si farebbe normalmente.</span><span class="sxs-lookup"><span data-stu-id="14d80-413">If you want to change the radius, just update the transform scale of the transform as you normally would.</span></span>

<span data-ttu-id="14d80-414">**NearInteractionTouchable e PokePointer**</span><span class="sxs-lookup"><span data-stu-id="14d80-414">**NearInteractionTouchable and PokePointer**</span></span>

- <span data-ttu-id="14d80-415">NearInteractionTouchable non gestisce più l'area di disegno dell'interfaccia utente di Unity.</span><span class="sxs-lookup"><span data-stu-id="14d80-415">NearInteractionTouchable does not handle Unity UI canvas touching any longer.</span></span> <span data-ttu-id="14d80-416">È necessario usare la classe NearInteractionTouchableUnityUI per l'interfaccia utente di Unity touchables Now.</span><span class="sxs-lookup"><span data-stu-id="14d80-416">The NearInteractionTouchableUnityUI class must be used for Unity UI touchables now.</span></span>
- <span data-ttu-id="14d80-417">ColliderNearInteractionTouchable è la nuova classe di base per touchables in base ai Collider, ovvero ogni oggetto toccabile, ad eccezione di NearInteractionTouchableUnityUI.</span><span class="sxs-lookup"><span data-stu-id="14d80-417">ColliderNearInteractionTouchable is the new base class for touchables based on colliders, i.e. every touchable except NearInteractionTouchableUnityUI.</span></span>
- <span data-ttu-id="14d80-418">BaseNearInteractionTouchable. DistFront è stato spostato e rinominato in PokePointer. TouchableDistance è la distanza e la PokePointer può interagire con touchables.</span><span class="sxs-lookup"><span data-stu-id="14d80-418">BaseNearInteractionTouchable.DistFront has been moved and renamed to PokePointer.TouchableDistance This is the distance and which the PokePointer can interact with touchables.</span></span> <span data-ttu-id="14d80-419">In precedenza ogni modificabile presentava una distanza di interazione massima, ma ora è definita in PokePointer, che consente una migliore ottimizzazione.</span><span class="sxs-lookup"><span data-stu-id="14d80-419">Previously each touchable had its own maximum interaction distance, but now this is defined in the PokePointer which allows better optimization.</span></span>
- <span data-ttu-id="14d80-420">BaseNearInteractionTouchable. DistBack è stato rinominato in PokeThreshold in modo da rendere chiaro che PokeThreshold è la controparte di DebounceThreshold.</span><span class="sxs-lookup"><span data-stu-id="14d80-420">BaseNearInteractionTouchable.DistBack has been renamed to PokeThreshold This makes it clear that PokeThreshold is the counterpart to DebounceThreshold.</span></span> <span data-ttu-id="14d80-421">Un oggetto toccabile viene attivato quando viene superato il valore di PokeThreshold e viene rilasciato quando DebounceThreshold viene attraversato.</span><span class="sxs-lookup"><span data-stu-id="14d80-421">A touchable is activated when the PokeThreshold is crossed, and released when DebounceThreshold is crossed.</span></span>

<span data-ttu-id="14d80-422">**ReadOnlyAttribute**</span><span class="sxs-lookup"><span data-stu-id="14d80-422">**ReadOnlyAttribute**</span></span>

<span data-ttu-id="14d80-423">Lo `Microsoft.MixedReality.Toolkit` spazio dei nomi è stato aggiunto a `ReadOnlyAttribute` , `BeginReadOnlyGroupAttribute` e `EndReadOnlyGroupAttribute` .</span><span class="sxs-lookup"><span data-stu-id="14d80-423">The `Microsoft.MixedReality.Toolkit` namespace has been added to `ReadOnlyAttribute`, `BeginReadOnlyGroupAttribute`, and `EndReadOnlyGroupAttribute`.</span></span>

<span data-ttu-id="14d80-424">**PointerClickHandler**</span><span class="sxs-lookup"><span data-stu-id="14d80-424">**PointerClickHandler**</span></span>

<span data-ttu-id="14d80-425">La classe `PointerClickHandler` è stata deprecata.</span><span class="sxs-lookup"><span data-stu-id="14d80-425">The `PointerClickHandler` class has been deprecated.</span></span> <span data-ttu-id="14d80-426">`PointerHandler`È invece necessario utilizzare l'oggetto, che fornisce la stessa funzionalità.</span><span class="sxs-lookup"><span data-stu-id="14d80-426">The `PointerHandler` should be used instead, it provides the same functionality.</span></span>

<span data-ttu-id="14d80-427">**Supporto di HoloLens Clicker**</span><span class="sxs-lookup"><span data-stu-id="14d80-427">**HoloLens clicker support**</span></span>

<span data-ttu-id="14d80-428">I mapping del controller del clicker HoloLens sono passati a un valore non gestito [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) .</span><span class="sxs-lookup"><span data-stu-id="14d80-428">The HoloLens clicker's controller mappings have changed from being an unhanded [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) to being an unhanded [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand).</span></span> <span data-ttu-id="14d80-429">Per tenere conto di questo problema, viene eseguito un aggiornamento automatico la prima volta che si apre il profilo ControllerMapping.</span><span class="sxs-lookup"><span data-stu-id="14d80-429">To account for this, an automatic updater will run the first time you open your ControllerMapping profile.</span></span> <span data-ttu-id="14d80-430">Aprire i profili personalizzati almeno una volta dopo l'aggiornamento a 2.0.0 per attivare questo passaggio di migrazione una volta.</span><span class="sxs-lookup"><span data-stu-id="14d80-430">Please open any custom profiles at least once after upgrading to 2.0.0 in order to trigger this one-time migration step.</span></span>

<span data-ttu-id="14d80-431">**InteractableHighlight**</span><span class="sxs-lookup"><span data-stu-id="14d80-431">**InteractableHighlight**</span></span>

<span data-ttu-id="14d80-432">La classe `InteractableHighlight` è stata deprecata.</span><span class="sxs-lookup"><span data-stu-id="14d80-432">The `InteractableHighlight` class has been deprecated.</span></span> <span data-ttu-id="14d80-433">In `InteractableOnFocus` alternativa, `FocusInteractableStates` è consigliabile usare la classe e l'asset.</span><span class="sxs-lookup"><span data-stu-id="14d80-433">The `InteractableOnFocus` class and `FocusInteractableStates` asset should be used instead.</span></span> <span data-ttu-id="14d80-434">Per creare un nuovo `Theme` asset per il `InteractableOnFocus` , fare clic con il pulsante destro del mouse nella finestra del progetto e scegliere *Crea*  >    >  *tema interagibile* del Toolkit di realtà mista  >  .</span><span class="sxs-lookup"><span data-stu-id="14d80-434">To create a new `Theme` asset for the `InteractableOnFocus`, right click in the project window and select *Create* > *Mixed Reality Toolkit* > *Interactable* > *Theme*.</span></span>

<span data-ttu-id="14d80-435">**HandInteractionPanZoom**</span><span class="sxs-lookup"><span data-stu-id="14d80-435">**HandInteractionPanZoom**</span></span>

<span data-ttu-id="14d80-436">`HandInteractionPanZoom` è stato spostato nello spazio dei nomi dell'interfaccia utente perché non era un componente di input.</span><span class="sxs-lookup"><span data-stu-id="14d80-436">`HandInteractionPanZoom` has been moved to the UI namespace as it was not an input component.</span></span> <span data-ttu-id="14d80-437">`HandPanEventData` è stato inoltre spostato in questo spazio dei nomi e semplificato per corrispondere ad altri dati degli eventi dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="14d80-437">`HandPanEventData` has also been moved into this namespace, and simplified to correspond with other UI event data.</span></span>

### <a name="assembly-name-changes-in-200"></a><span data-ttu-id="14d80-438">Modifiche al nome dell'assembly in 2.0.0</span><span class="sxs-lookup"><span data-stu-id="14d80-438">Assembly name changes in 2.0.0</span></span>

<span data-ttu-id="14d80-439">Nella versione 2.0.0, tutti i nomi di assembly ufficiali del Toolkit di realtà mista e i file di definizione di assembly (con estensione asmdef) associati sono stati aggiornati per adattarsi al modello seguente.</span><span class="sxs-lookup"><span data-stu-id="14d80-439">In The 2.0.0 release, all of the official Mixed Reality Toolkit assembly names and their associated assembly definition (.asmdef) files have been updated to fit the following pattern.</span></span>

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

<span data-ttu-id="14d80-440">In alcuni casi, sono Stati Uniti più assembly per creare una migliore Unity del rispettivo contenuto.</span><span class="sxs-lookup"><span data-stu-id="14d80-440">In some instances, multiple assemblies have been merged to create better unity of their contents.</span></span> <span data-ttu-id="14d80-441">Se il progetto usa file con estensione asmdef personalizzati, potrebbe essere necessario aggiornare.</span><span class="sxs-lookup"><span data-stu-id="14d80-441">If your project uses custom .asmdef files, they may require updating.</span></span>

<span data-ttu-id="14d80-442">Le tabelle seguenti descrivono il mapping dei nomi di file RC2. asmdef alla versione 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="14d80-442">The following tables describe how the RC2 .asmdef file names map to the 2.0.0 release.</span></span> <span data-ttu-id="14d80-443">Tutti i nomi di assembly corrispondono al nome del file. asmdef.</span><span class="sxs-lookup"><span data-stu-id="14d80-443">All assembly names match the .asmdef file name.</span></span>

<span data-ttu-id="14d80-444">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="14d80-444">**MixedRealityToolkit**</span></span>

| <span data-ttu-id="14d80-445">RC2</span><span class="sxs-lookup"><span data-stu-id="14d80-445">RC2</span></span> | <span data-ttu-id="14d80-446">2.0.0</span><span class="sxs-lookup"><span data-stu-id="14d80-446">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="14d80-447">MixedRealityToolkit.asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-447">MixedRealityToolkit.asmdef</span></span> | <span data-ttu-id="14d80-448">Microsoft. MixedReality. Toolkit. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-448">Microsoft.MixedReality.Toolkit.asmdef</span></span> |
| <span data-ttu-id="14d80-449">MixedRealityToolkit. Core. BuildAndDeploy. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-449">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span></span> | <span data-ttu-id="14d80-450">Microsoft. MixedReality. Toolkit. Editor. BuildAndDeploy. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-450">Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef</span></span> |
| <span data-ttu-id="14d80-451">MixedRealityToolkit. Core. Definitions. Utilities. Editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-451">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="14d80-452">Rimosso, usare Microsoft. MixedReality. Toolkit. Editor. Utilities. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-452">Removed, use Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="14d80-453">MixedRealityToolkit. Core. Extensions. EditorClassExtensions. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-453">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span></span> | <span data-ttu-id="14d80-454">Microsoft. MixedReality. Toolkit. Editor. ClassExtensions. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-454">Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef</span></span>
| <span data-ttu-id="14d80-455">MixedRealityToolkit. Core. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-455">MixedRealityToolkit.Core.Inspectors.asmdef</span></span> | <span data-ttu-id="14d80-456">Microsoft. MixedReality. Toolkit. Editor. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-456">Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef</span></span> |
| <span data-ttu-id="14d80-457">MixedRealityToolkit. Core. Inspectors. ServiceInspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-457">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span></span> | <span data-ttu-id="14d80-458">Microsoft. MixedReality. Toolkit. Editor. ServiceInspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-458">Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef</span></span> |
| <span data-ttu-id="14d80-459">MixedRealityToolkit. Core. UtilitiesAsync. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-459">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span></span> | <span data-ttu-id="14d80-460">Microsoft. MixedReality. Toolkit. Async. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-460">Microsoft.MixedReality.Toolkit.Async.asmdef</span></span> |
| <span data-ttu-id="14d80-461">MixedRealityToolkit. Core. Utilities. Editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-461">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="14d80-462">Microsoft. MixedReality. Toolkit. Editor. Utilities. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-462">Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="14d80-463">MixedRealityToolkit. Utilities. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-463">MixedRealityToolkit.Utilities.Gltf.asmdef</span></span> | <span data-ttu-id="14d80-464">Microsoft. MixedReality. Toolkit. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-464">Microsoft.MixedReality.Toolkit.Gltf.asmdef</span></span> |
| <span data-ttu-id="14d80-465">MixedRealityToolkit. Utilities. Gltf. Importers. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-465">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span></span> | <span data-ttu-id="14d80-466">Microsoft. MixedReality. Toolkit. Gltf. Importers. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-466">Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef</span></span> |

<span data-ttu-id="14d80-467">**MixedRealityToolkit. Providers**</span><span class="sxs-lookup"><span data-stu-id="14d80-467">**MixedRealityToolkit.Providers**</span></span>

| <span data-ttu-id="14d80-468">RC2</span><span class="sxs-lookup"><span data-stu-id="14d80-468">RC2</span></span> | <span data-ttu-id="14d80-469">2.0.0</span><span class="sxs-lookup"><span data-stu-id="14d80-469">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="14d80-470">MixedRealityToolkit. Providers. OpenVR. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-470">MixedRealityToolkit.Providers.OpenVR.asmdef</span></span> | <span data-ttu-id="14d80-471">Microsoft. MixedReality. Toolkit. Providers. OpenVR. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-471">Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef</span></span> |
| <span data-ttu-id="14d80-472">MixedRealityToolkit. Providers. WindowsMixedReality. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-472">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span></span> | <span data-ttu-id="14d80-473">Microsoft. MixedReality. Toolkit. Providers. WindowsMixedReality. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-473">Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef</span></span> |
| <span data-ttu-id="14d80-474">MixedRealityToolkit. Providers. WindowsVoiceInput. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-474">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span></span> | <span data-ttu-id="14d80-475">Microsoft. MixedReality. Toolkit. Providers. WindowsVoiceInput. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-475">Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef</span></span> |

<span data-ttu-id="14d80-476">**MixedRealityToolkit. Services**</span><span class="sxs-lookup"><span data-stu-id="14d80-476">**MixedRealityToolkit.Services**</span></span>

| <span data-ttu-id="14d80-477">RC2</span><span class="sxs-lookup"><span data-stu-id="14d80-477">RC2</span></span> | <span data-ttu-id="14d80-478">2.0.0</span><span class="sxs-lookup"><span data-stu-id="14d80-478">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="14d80-479">MixedRealityToolkit. Services. BoundarySystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-479">MixedRealityToolkit.Services.BoundarySystem.asmdef</span></span> | <span data-ttu-id="14d80-480">Microsoft. MixedReality. Toolkit. Services. BoundarySystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-480">Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef</span></span> |
| <span data-ttu-id="14d80-481">MixedRealityToolkit. Services. CameraSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-481">MixedRealityToolkit.Services.CameraSystem.asmdef</span></span> | <span data-ttu-id="14d80-482">Microsoft. MixedReality. Toolkit. Services. CameraSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-482">Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef</span></span> |
| <span data-ttu-id="14d80-483">MixedRealityToolkit. Services. DiagnosticsSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-483">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span></span> | <span data-ttu-id="14d80-484">Microsoft. MixedReality. Toolkit. Services. DiagnosticsSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-484">Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef</span></span> |
| <span data-ttu-id="14d80-485">MixedRealityToolkit. Services. InputSimulation. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-485">MixedRealityToolkit.Services.InputSimulation.asmdef</span></span> | <span data-ttu-id="14d80-486">Microsoft. MixedReality. Toolkit. Services. InputSimulation. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-486">Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef</span></span> |
| <span data-ttu-id="14d80-487">MixedRealityToolkit. Services. InputSimulation. Editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-487">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span></span> | <span data-ttu-id="14d80-488">Microsoft. MixedReality. Toolkit. Services. InputSimulation. Editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-488">Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef</span></span> |
| <span data-ttu-id="14d80-489">MixedRealityToolkit. Services. InputSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-489">MixedRealityToolkit.Services.InputSystem.asmdef</span></span> | <span data-ttu-id="14d80-490">Microsoft. MixedReality. Toolkit. Services. InputSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-490">Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef</span></span> |
| <span data-ttu-id="14d80-491">MixedRealityToolkit. Services. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-491">MixedRealityToolkit.Services.Inspectors.asmdef</span></span> | <span data-ttu-id="14d80-492">Microsoft. MixedReality. Toolkit. Services. InputSystem. Editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-492">Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef</span></span> |
| <span data-ttu-id="14d80-493">MixedRealityToolkit. Services. SceneSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-493">MixedRealityToolkit.Services.SceneSystem.asmdef</span></span> | <span data-ttu-id="14d80-494">Microsoft. MixedReality. Toolkit. Services. SceneSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-494">Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef</span></span> |
| <span data-ttu-id="14d80-495">MixedRealityToolkit. Services. SpatialAwarenessSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-495">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span></span> | <span data-ttu-id="14d80-496">Microsoft. MixedReality. Toolkit. Services. SpatialAwarenessSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-496">Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef</span></span> |
| <span data-ttu-id="14d80-497">MixedRealityToolkit. Services. TeleportSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-497">MixedRealityToolkit.Services.TeleportSystem.asmdef</span></span> | <span data-ttu-id="14d80-498">Microsoft. MixedReality. Toolkit. Services. TeleportSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-498">Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef</span></span> |

<span data-ttu-id="14d80-499">**MixedRealityToolkit. SDK**</span><span class="sxs-lookup"><span data-stu-id="14d80-499">**MixedRealityToolkit.SDK**</span></span>

| <span data-ttu-id="14d80-500">RC2</span><span class="sxs-lookup"><span data-stu-id="14d80-500">RC2</span></span> | <span data-ttu-id="14d80-501">2.0.0</span><span class="sxs-lookup"><span data-stu-id="14d80-501">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="14d80-502">MixedRealityToolkit. SDK. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-502">MixedRealityToolkit.SDK.asmdef</span></span> | <span data-ttu-id="14d80-503">Microsoft. MixedReality. Toolkit. SDK. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-503">Microsoft.MixedReality.Toolkit.SDK.asmdef</span></span> |
| <span data-ttu-id="14d80-504">MixedRealityToolkit. SDK. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-504">MixedRealityToolkit.SDK.Inspectors.asmdef</span></span> | <span data-ttu-id="14d80-505">Microsoft. MixedReality. Toolkit. SDK. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-505">Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef</span></span> |

<span data-ttu-id="14d80-506">**MixedRealityToolkit. examples**</span><span class="sxs-lookup"><span data-stu-id="14d80-506">**MixedRealityToolkit.Examples**</span></span>

| <span data-ttu-id="14d80-507">RC2</span><span class="sxs-lookup"><span data-stu-id="14d80-507">RC2</span></span> | <span data-ttu-id="14d80-508">2.0.0</span><span class="sxs-lookup"><span data-stu-id="14d80-508">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="14d80-509">MixedRealityToolkit. examples. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-509">MixedRealityToolkit.Examples.asmdef</span></span> | <span data-ttu-id="14d80-510">Microsoft. MixedReality. Toolkit. examples. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-510">Microsoft.MixedReality.Toolkit.Examples.asmdef</span></span> |
| <span data-ttu-id="14d80-511">MixedRealityToolkit. examples. Demos. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-511">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span></span> | <span data-ttu-id="14d80-512">Microsoft. MixedReality. Toolkit. Demos. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-512">Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef</span></span> |
| <span data-ttu-id="14d80-513">MixedRealityToolkit. examples. Demos. StandardShader. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-513">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span></span> | <span data-ttu-id="14d80-514">Microsoft. MixedReality. Toolkit. Demos. StandardShader. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-514">Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef</span></span> |
| <span data-ttu-id="14d80-515">MixedRealityToolkit. examples. Demos. Utilities. InspectorFields. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-515">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span></span> | <span data-ttu-id="14d80-516">Microsoft. MixedReality. Toolkit. Demos. InspectorFields. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-516">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef</span></span> |
| <span data-ttu-id="14d80-517">MixedRealityToolkit. examples. Demos. Utilities. InspectorFields. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-517">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span></span> | <span data-ttu-id="14d80-518">Microsoft. MixedReality. Toolkit. Demos. InspectorFields. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-518">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef</span></span> |
| <span data-ttu-id="14d80-519">MixedRealityToolkit. examples. Demos. UX. Interactables. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-519">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span></span> | <span data-ttu-id="14d80-520">Microsoft. MixedReality. Toolkit. Demos. UX. Interactables. asmdef</span><span class="sxs-lookup"><span data-stu-id="14d80-520">Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef</span></span> |
