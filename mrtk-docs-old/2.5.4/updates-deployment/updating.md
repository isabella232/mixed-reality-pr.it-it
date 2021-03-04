---
title: Aggiornamento
description: Documentazione per la migrazione da una versione precedente di MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: dfd764062827d85fe87aab26e7b0b53772bb3814
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781932"
---
# <a name="updating-the-microsoft-mixed-reality-toolkit"></a><span data-ttu-id="53da9-104">Aggiornamento di Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="53da9-104">Updating the Microsoft Mixed Reality Toolkit</span></span>

- [<span data-ttu-id="53da9-105">Aggiornamento a una nuova versione di MRTK</span><span class="sxs-lookup"><span data-stu-id="53da9-105">Upgrading to a new version of MRTK</span></span>](#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="53da9-106">da 2.3.0 a 2.4.0</span><span class="sxs-lookup"><span data-stu-id="53da9-106">2.3.0 to 2.4.0</span></span>](#updating-230-to-240)
- [<span data-ttu-id="53da9-107">da 2.2.0 a 2.3.0</span><span class="sxs-lookup"><span data-stu-id="53da9-107">2.2.0 to 2.3.0</span></span>](#updating-220-to-230)
- [<span data-ttu-id="53da9-108">da 2.1.0 a 2.2.0</span><span class="sxs-lookup"><span data-stu-id="53da9-108">2.1.0 to 2.2.0</span></span>](#updating-210-to-220)
- [<span data-ttu-id="53da9-109">2.0.0 a 2.1.0</span><span class="sxs-lookup"><span data-stu-id="53da9-109">2.0.0 to 2.1.0</span></span>](#updating-200-to-210)
- [<span data-ttu-id="53da9-110">Da RC2 a 2.0.0</span><span class="sxs-lookup"><span data-stu-id="53da9-110">RC2 to 2.0.0</span></span>](#updating-rc2-to-200)

## <a name="upgrading-to-a-new-version-of-mrtk"></a><span data-ttu-id="53da9-111">Aggiornamento a una nuova versione di MRTK</span><span class="sxs-lookup"><span data-stu-id="53da9-111">Upgrading to a new version of MRTK</span></span>

<span data-ttu-id="53da9-112">*Si consiglia vivamente di eseguire lo [strumento di migrazione](../features/tools/migration-window.md) dopo aver ricevuto l'aggiornamento di MRTK per la* correzione automatica e l'aggiornamento dai componenti deprecati e la modifica delle modifiche di rilievo.</span><span class="sxs-lookup"><span data-stu-id="53da9-112">*It is strongly recommended to run the [migration tool](../features/tools/migration-window.md) after getting the MRTK update* to auto-fix and upgrade from deprecated components and adjust to breaking changes.</span></span> <span data-ttu-id="53da9-113">Lo strumento di migrazione fa parte del pacchetto di **strumenti** .</span><span class="sxs-lookup"><span data-stu-id="53da9-113">The migration tool is part of the **Tools** package.</span></span>

<span data-ttu-id="53da9-114">Le istruzioni seguenti descrivono il percorso di aggiornamento da 2.4.0 a 2.5.0.</span><span class="sxs-lookup"><span data-stu-id="53da9-114">The instructions below describe the 2.4.0 to 2.5.0 upgrade path.</span></span> <span data-ttu-id="53da9-115">Se il progetto si trova in 2.3.0 o versioni precedenti, leggere le modifiche [tra le versioni](#updating-230-to-240) per comprendere il percorso di aggiornamento o leggere le [istruzioni](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) della versione precedente per eseguire un aggiornamento versione per versione.</span><span class="sxs-lookup"><span data-stu-id="53da9-115">If your project is on 2.3.0 or earlier, read on to the changes [between versions](#updating-230-to-240) to understand the upgrade path, or read the previous [release's instructions](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) to do a version-by-version upgrade.</span></span>

### <a name="unity-asset-unitypackage-files"></a><span data-ttu-id="53da9-116">File di asset Unity (con estensione file unitypackage Tools)</span><span class="sxs-lookup"><span data-stu-id="53da9-116">Unity asset (.unitypackage) files</span></span>

<span data-ttu-id="53da9-117">Per il percorso di aggiornamento più semplice, seguire questa procedura.</span><span class="sxs-lookup"><span data-stu-id="53da9-117">For the smoothest upgrade path, please use the following steps.</span></span>

1. <span data-ttu-id="53da9-118">Salvare una copia del progetto corrente, nel caso in cui si riscontrino eventuali strappi in qualsiasi punto della procedura di aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="53da9-118">Save a copy of your current project, in case you hit any snags at any point in the upgrade steps.</span></span>
1. <span data-ttu-id="53da9-119">Chiudi Unity</span><span class="sxs-lookup"><span data-stu-id="53da9-119">Close Unity</span></span>
1. <span data-ttu-id="53da9-120">All'interno della cartella *assets* , eliminare le cartelle **MRTK** seguenti, insieme ai relativi file con estensione meta (il progetto potrebbe non avere tutte le cartelle elencate)</span><span class="sxs-lookup"><span data-stu-id="53da9-120">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="53da9-121">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="53da9-121">MRTK/Core</span></span>
    - <span data-ttu-id="53da9-122">MRTK/esempi</span><span class="sxs-lookup"><span data-stu-id="53da9-122">MRTK/Examples</span></span>
    - <span data-ttu-id="53da9-123">MRTK/estensioni</span><span class="sxs-lookup"><span data-stu-id="53da9-123">MRTK/Extensions</span></span>
    > [!NOTE]
    > <span data-ttu-id="53da9-124">Se sono state installate estensioni aggiuntive, eseguire un backup prima di eliminare le cartelle.</span><span class="sxs-lookup"><span data-stu-id="53da9-124">If additional extensions have been installed, please make a backup prior to deleting these folders.</span></span>
    - <span data-ttu-id="53da9-125">MRTK/provider</span><span class="sxs-lookup"><span data-stu-id="53da9-125">MRTK/Providers</span></span>
    - <span data-ttu-id="53da9-126">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="53da9-126">MRTK/SDK</span></span>
    - <span data-ttu-id="53da9-127">MRTK/servizi</span><span class="sxs-lookup"><span data-stu-id="53da9-127">MRTK/Services</span></span>
    - <span data-ttu-id="53da9-128">MRTK/strumenti</span><span class="sxs-lookup"><span data-stu-id="53da9-128">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="53da9-129">Non eliminare la cartella **MixedRealityToolkit. generated** o il relativo file con estensione meta.</span><span class="sxs-lookup"><span data-stu-id="53da9-129">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="53da9-130">Elimina la cartella della **libreria**</span><span class="sxs-lookup"><span data-stu-id="53da9-130">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="53da9-131">Alcuni strumenti di Unity, ad esempio Unity collab, salvano le informazioni di configurazione nella cartella della libreria.</span><span class="sxs-lookup"><span data-stu-id="53da9-131">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="53da9-132">Se si usa uno strumento che consente di eseguire questa operazione, copiare prima di tutto la cartella dei dati dello strumento dalla libreria prima di eliminarla, quindi ripristinarla dopo la rigenerazione della libreria.</span><span class="sxs-lookup"><span data-stu-id="53da9-132">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="53da9-133">Riaprire il progetto in Unity</span><span class="sxs-lookup"><span data-stu-id="53da9-133">Re-open the project in Unity</span></span>
1. <span data-ttu-id="53da9-134">Importare i nuovi pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="53da9-134">Import the new unity packages</span></span>
    - <span data-ttu-id="53da9-135">Foundation: _importare prima questo pacchetto_</span><span class="sxs-lookup"><span data-stu-id="53da9-135">Foundation - _Import this package first_</span></span>
    - <span data-ttu-id="53da9-136">Strumenti</span><span class="sxs-lookup"><span data-stu-id="53da9-136">Tools</span></span>
    - <span data-ttu-id="53da9-137">Opzionale Estensioni</span><span class="sxs-lookup"><span data-stu-id="53da9-137">(Optional) Extensions</span></span>
    > [!NOTE]
    > <span data-ttu-id="53da9-138">Se sono state installate estensioni aggiuntive, potrebbe essere necessario importarle nuovamente.</span><span class="sxs-lookup"><span data-stu-id="53da9-138">If additional extensions had been installed, they may need to be re-imported.</span></span>
    - <span data-ttu-id="53da9-139">Opzionale Esempi</span><span class="sxs-lookup"><span data-stu-id="53da9-139">(Optional) Examples</span></span>
1. <span data-ttu-id="53da9-140">Chiudere Unity ed eliminare la cartella **Library** (per prima cosa leggere la nota riportata di seguito).</span><span class="sxs-lookup"><span data-stu-id="53da9-140">Close Unity and delete the **Library** folder (read the note below first!).</span></span> <span data-ttu-id="53da9-141">Questo passaggio è necessario per forzare Unity ad aggiornare il database asset e a riconciliare i profili personalizzati esistenti.</span><span class="sxs-lookup"><span data-stu-id="53da9-141">This step is necessary to force Unity to refresh its asset database and reconcile existing custom profiles.</span></span>
1. <span data-ttu-id="53da9-142">Avviare Unity e per ogni scena nel progetto</span><span class="sxs-lookup"><span data-stu-id="53da9-142">Launch Unity, and for each scene in the project</span></span>
    - <span data-ttu-id="53da9-143">Eliminare **MixedRealityToolkit** e **MixedRealityPlayspace**, se presente, dalla gerarchia.</span><span class="sxs-lookup"><span data-stu-id="53da9-143">Delete **MixedRealityToolkit** and **MixedRealityPlayspace**, if present, from the hierarchy.</span></span> <span data-ttu-id="53da9-144">Questa operazione eliminerà la fotocamera principale, ma verrà ricreata nel passaggio successivo.</span><span class="sxs-lookup"><span data-stu-id="53da9-144">This will delete the main camera, but it will be re-created in the next step.</span></span> <span data-ttu-id="53da9-145">Se una qualsiasi proprietà della fotocamera principale è stata modificata manualmente, sarà necessario riapplicarla manualmente una volta creata la nuova fotocamera.</span><span class="sxs-lookup"><span data-stu-id="53da9-145">If any properties of the main camera have been manually changed, these will have to be re-applied manually once the new camera is created.</span></span>
    - <span data-ttu-id="53da9-146">Selezionare **MixedRealityToolkit-> Aggiungi a scena e configura**</span><span class="sxs-lookup"><span data-stu-id="53da9-146">Select **MixedRealityToolkit -> Add to Scene and Configure**</span></span>
    - <span data-ttu-id="53da9-147">Selezionare **MixedRealityToolkit-> Utilities-> aggiornare-> i profili di mapping del controller** (necessario solo una volta). verranno aggiornati tutti i profili di mapping del controller personalizzato con assi e dati aggiornati, lasciando intatte le azioni di input personalizzate assegnate</span><span class="sxs-lookup"><span data-stu-id="53da9-147">Select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (only needs to be done once)       - This will update any custom controller mapping profiles with updated axes and data, while leaving your custom-assigned input actions intact</span></span>
1. <span data-ttu-id="53da9-148">Eseguire lo [strumento di migrazione](../features/tools/migration-window.md) ed eseguire lo strumento nel *progetto completo* per assicurarsi che tutto il codice venga aggiornato alla versione più recente.</span><span class="sxs-lookup"><span data-stu-id="53da9-148">Run the [migration tool](../features/tools/migration-window.md) and run the tool on the *Full Project* to ensure that all of your code is updated to the latest.</span></span>
   <span data-ttu-id="53da9-149">La finestra migrazione contiene diversi gestori della migrazione, ognuno dei quali deve essere eseguito autonomamente.</span><span class="sxs-lookup"><span data-stu-id="53da9-149">The migration window contains a number of different migration handlers, which must each be run on their own.</span></span> <span data-ttu-id="53da9-150">Questo passaggio include:</span><span class="sxs-lookup"><span data-stu-id="53da9-150">This step involves:</span></span>
   - <span data-ttu-id="53da9-151">Selezionare il primo gestore della migrazione dall'elenco a discesa di **selezione del gestore della migrazione** .</span><span class="sxs-lookup"><span data-stu-id="53da9-151">Select the first migration handler from the **Migration Handler Selection** dropdown.</span></span>
   - <span data-ttu-id="53da9-152">Fare clic sul pulsante "progetto completo".</span><span class="sxs-lookup"><span data-stu-id="53da9-152">Click the "Full Project" button.</span></span>
   - <span data-ttu-id="53da9-153">Fare clic sul pulsante "Aggiungi progetto completo per la migrazione". l'intero progetto verrà analizzato per la migrazione degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="53da9-153">Click the "Add full project for migration" button (this will scan the entire project for objects to migrate).</span></span>
   - <span data-ttu-id="53da9-154">Fare clic sul pulsante "migrate", che deve essere abilitato se sono stati trovati oggetti migrabili.</span><span class="sxs-lookup"><span data-stu-id="53da9-154">Click the "Migrate" button which should be enabled if any migrateable objects were found.</span></span>
   - <span data-ttu-id="53da9-155">Ripetere i tre passaggi precedenti per ogni gestore della migrazione all'interno dell'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="53da9-155">Repeat the previous three steps for each of the migration handlers within the dropdown.</span></span>
     <span data-ttu-id="53da9-156">(Vedere [questo problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) che riguarda il lavoro che è possibile eseguire per semplificare questo processo di migrazione in una versione futura)</span><span class="sxs-lookup"><span data-stu-id="53da9-156">(See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) which covers work that can be done to simplify this migration process in a future release)</span></span>

## <a name="updating-230-to-240"></a><span data-ttu-id="53da9-157">Aggiornamento di 2.3.0 a 2.4.0</span><span class="sxs-lookup"><span data-stu-id="53da9-157">Updating 2.3.0 to 2.4.0</span></span>

<span data-ttu-id="53da9-158">[Rinomina cartella](#folder-renames-in-240) 
 [Modifiche API](#api-changes-in-240)</span><span class="sxs-lookup"><span data-stu-id="53da9-158">[Folder renames](#folder-renames-in-240)
[API changes](#api-changes-in-240)</span></span>

### <a name="folder-renames-in-240"></a><span data-ttu-id="53da9-159">Ridenominazione della cartella in 2.4.0</span><span class="sxs-lookup"><span data-stu-id="53da9-159">Folder renames in 2.4.0</span></span>

<span data-ttu-id="53da9-160">Le cartelle MixedRealityToolkit sono state rinominate e spostate in una gerarchia comune della versione 2,4.</span><span class="sxs-lookup"><span data-stu-id="53da9-160">The MixedRealityToolkit folders have been renamed and moved into a common hierarchy in version 2.4.</span></span> <span data-ttu-id="53da9-161">Se un'applicazione usa percorsi hardcoded per le risorse MRTK, sarà necessario aggiornarli in base alla tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="53da9-161">If an application uses hard coded paths to MRTK resources, they will need to be updated per the following table.</span></span>

| <span data-ttu-id="53da9-162">Cartella precedente</span><span class="sxs-lookup"><span data-stu-id="53da9-162">Previous Folder</span></span> | <span data-ttu-id="53da9-163">Nuova cartella</span><span class="sxs-lookup"><span data-stu-id="53da9-163">New Folder</span></span> |
| --- | --- |
| <span data-ttu-id="53da9-164">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="53da9-164">MixedRealityToolkit</span></span> | <span data-ttu-id="53da9-165">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="53da9-165">MRTK/Core</span></span> |
| <span data-ttu-id="53da9-166">MixedRealityToolkit. examples</span><span class="sxs-lookup"><span data-stu-id="53da9-166">MixedRealityToolkit.Examples</span></span> | <span data-ttu-id="53da9-167">MRTK/esempi</span><span class="sxs-lookup"><span data-stu-id="53da9-167">MRTK/Examples</span></span> |
| <span data-ttu-id="53da9-168">MixedRealityToolkit. Extensions</span><span class="sxs-lookup"><span data-stu-id="53da9-168">MixedRealityToolkit.Extensions</span></span> | <span data-ttu-id="53da9-169">MRTK/estensioni</span><span class="sxs-lookup"><span data-stu-id="53da9-169">MRTK/Extensions</span></span> |
| <span data-ttu-id="53da9-170">MixedRealityToolkit. Providers</span><span class="sxs-lookup"><span data-stu-id="53da9-170">MixedRealityToolkit.Providers</span></span> | <span data-ttu-id="53da9-171">MRTK/provider</span><span class="sxs-lookup"><span data-stu-id="53da9-171">MRTK/Providers</span></span> |
| <span data-ttu-id="53da9-172">MixedRealityToolkit. SDK</span><span class="sxs-lookup"><span data-stu-id="53da9-172">MixedRealityToolkit.SDK</span></span> | <span data-ttu-id="53da9-173">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="53da9-173">MRTK/SDK</span></span> |
| <span data-ttu-id="53da9-174">MixedRealityToolkit. Services</span><span class="sxs-lookup"><span data-stu-id="53da9-174">MixedRealityToolkit.Services</span></span> | <span data-ttu-id="53da9-175">MRTK/servizi</span><span class="sxs-lookup"><span data-stu-id="53da9-175">MRTK/Services</span></span> |
| <span data-ttu-id="53da9-176">MixedRealityToolkit. test</span><span class="sxs-lookup"><span data-stu-id="53da9-176">MixedRealityToolkit.Tests</span></span> | <span data-ttu-id="53da9-177">MRTK/test</span><span class="sxs-lookup"><span data-stu-id="53da9-177">MRTK/Tests</span></span> |
| <span data-ttu-id="53da9-178">MixedRealityToolkit. Tools</span><span class="sxs-lookup"><span data-stu-id="53da9-178">MixedRealityToolkit.Tools</span></span> | <span data-ttu-id="53da9-179">MRTK/strumenti</span><span class="sxs-lookup"><span data-stu-id="53da9-179">MRTK/Tools</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="53da9-180">`MixedRealityToolkit.Generated`Contiene i file generati dal cliente e rimane invariato.</span><span class="sxs-lookup"><span data-stu-id="53da9-180">The `MixedRealityToolkit.Generated` contains customer generated files and remains unchanged.</span></span>

### <a name="eye-gaze-setup-in-240"></a><span data-ttu-id="53da9-181">Configurazione degli sguardi in 2.4.0</span><span class="sxs-lookup"><span data-stu-id="53da9-181">Eye gaze setup in 2.4.0</span></span>

<span data-ttu-id="53da9-182">Questa versione di MRTK modifica i passaggi necessari per l'installazione di Eye sguardi.</span><span class="sxs-lookup"><span data-stu-id="53da9-182">This version of MRTK modifies the steps required for eye gaze setup.</span></span> <span data-ttu-id="53da9-183">È possibile trovare la casella di controllo _' IsEyeTrackingEnabled '_ nelle impostazioni di sguardi del profilo puntatore di input.</span><span class="sxs-lookup"><span data-stu-id="53da9-183">The _'IsEyeTrackingEnabled'_ checkbox can be found in the gaze settings of the input pointer profile.</span></span> <span data-ttu-id="53da9-184">Se si seleziona questa casella, verrà abilitato lo sguardo basato sull'occhio, anziché lo sguardo predefinito basato sulla testa.</span><span class="sxs-lookup"><span data-stu-id="53da9-184">Checking this box will enable eye based gaze, rather then the default head based gaze.</span></span>

<span data-ttu-id="53da9-185">Per ulteriori informazioni su queste modifiche e istruzioni complete per la configurazione della verifica degli occhi, vedere l'articolo relativo alla [Verifica](../features/eye-tracking/eye-tracking-basic-setup.md) degli occhi.</span><span class="sxs-lookup"><span data-stu-id="53da9-185">For more information on these changes and complete instructions for eye tracking setup, please see the [eye tracking](../features/eye-tracking/eye-tracking-basic-setup.md) article.</span></span>

### <a name="eye-gaze-pointer-behavior-in-240"></a><span data-ttu-id="53da9-186">Comportamento del puntatore a sguardi oculari in 2.4.0</span><span class="sxs-lookup"><span data-stu-id="53da9-186">Eye gaze pointer behavior in 2.4.0</span></span>

<span data-ttu-id="53da9-187">Il comportamento dell'indicatore di misura predefinito per gli occhi è stato modificato in modo da corrispondere al comportamento predefinito del puntatore.</span><span class="sxs-lookup"><span data-stu-id="53da9-187">The eye gaze default pointer behavior have been modified to match the head gaze default pointer behavior.</span></span> <span data-ttu-id="53da9-188">Quando viene rilevata una mano, un puntatore a sguardi occhi verrà eliminato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="53da9-188">An eye gaze pointer will automatically be suppressed once a hand is detected.</span></span> <span data-ttu-id="53da9-189">Il puntatore a sguardi occhi diventerà nuovamente visibile dopo aver detto "Select".</span><span class="sxs-lookup"><span data-stu-id="53da9-189">The eye gaze pointer will become visible again after saying "Select".</span></span>

<span data-ttu-id="53da9-190">Per informazioni dettagliate sulle configurazioni dello sguardo e della mano, vedere l'articolo relativo [agli occhi e alle mani](../features/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) .</span><span class="sxs-lookup"><span data-stu-id="53da9-190">Details about gaze and hand setups can be found in the [eyes and hands](../features/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) article.</span></span>

### <a name="api-changes-in-240"></a><span data-ttu-id="53da9-191">Modifiche alle API in 2.4.0</span><span class="sxs-lookup"><span data-stu-id="53da9-191">API changes in 2.4.0</span></span>

<span data-ttu-id="53da9-192">**Classi controller personalizzate**</span><span class="sxs-lookup"><span data-stu-id="53da9-192">**Custom controller classes**</span></span>

<span data-ttu-id="53da9-193">Classi controller personalizzate in precedenza dovevano definire `SetupDefaultInteractions(Handedness)` .</span><span class="sxs-lookup"><span data-stu-id="53da9-193">Custom controller classes previously had to define `SetupDefaultInteractions(Handedness)`.</span></span> <span data-ttu-id="53da9-194">Questo metodo è stato reso obsoleto in 2,4, poiché il parametro di manualità era ridondante con la propria manualità della classe controller.</span><span class="sxs-lookup"><span data-stu-id="53da9-194">This method has been made obsolete in 2.4, as the handedness parameter was redundant with the controller class' own handedness.</span></span> <span data-ttu-id="53da9-195">Il nuovo metodo non dispone di parametri.</span><span class="sxs-lookup"><span data-stu-id="53da9-195">The new method has no parameters.</span></span> <span data-ttu-id="53da9-196">Inoltre, molte classi controller hanno definito questo metodo nello stesso modo ( `AssignControllerMappings(DefaultInteractions);` ), quindi la chiamata completa è stata sottoposta a refactoring in ed è stato `BaseController` eseguito un override facoltativo anziché obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="53da9-196">Additionally, many controller classes defined this the same way (`AssignControllerMappings(DefaultInteractions);`), so the full call has been refactored down into `BaseController` and made an optional override instead of required.</span></span>

<span data-ttu-id="53da9-197">**Proprietà degli sguardi**</span><span class="sxs-lookup"><span data-stu-id="53da9-197">**Eye Gaze properties**</span></span>

<span data-ttu-id="53da9-198">La `UseEyeTracking` proprietà dall' `GazeProvider` implementazione di `IMixedRealityEyeGazeProvider` è stata rinominata in `IsEyeTrackingEnabled` .</span><span class="sxs-lookup"><span data-stu-id="53da9-198">The `UseEyeTracking` property from `GazeProvider` implementation of `IMixedRealityEyeGazeProvider` was renamed to `IsEyeTrackingEnabled`.</span></span>

<span data-ttu-id="53da9-199">Se questa operazione è stata eseguita in precedenza...</span><span class="sxs-lookup"><span data-stu-id="53da9-199">If you did this previously...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

<span data-ttu-id="53da9-200">Esegui ora...</span><span class="sxs-lookup"><span data-stu-id="53da9-200">Do this now...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

<span data-ttu-id="53da9-201">**Proprietà di WindowsApiChecker**</span><span class="sxs-lookup"><span data-stu-id="53da9-201">**WindowsApiChecker properties**</span></span>

<span data-ttu-id="53da9-202">Le proprietà WindowsApiChecker seguenti sono state contrassegnate come obsolete.</span><span class="sxs-lookup"><span data-stu-id="53da9-202">The following WindowsApiChecker properties have been marked as obsolete.</span></span> <span data-ttu-id="53da9-203">Usare `IsMethodAvailable` `IsPropertyAvailable` o `IsTypeAvailable` .</span><span class="sxs-lookup"><span data-stu-id="53da9-203">Please use `IsMethodAvailable`, `IsPropertyAvailable` or `IsTypeAvailable`.</span></span>

- <span data-ttu-id="53da9-204">UniversalApiContractV8_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="53da9-204">UniversalApiContractV8_IsAvailable</span></span>
- <span data-ttu-id="53da9-205">UniversalApiContractV7_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="53da9-205">UniversalApiContractV7_IsAvailable</span></span>
- <span data-ttu-id="53da9-206">UniversalApiContractV6_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="53da9-206">UniversalApiContractV6_IsAvailable</span></span>
- <span data-ttu-id="53da9-207">UniversalApiContractV5_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="53da9-207">UniversalApiContractV5_IsAvailable</span></span>
- <span data-ttu-id="53da9-208">UniversalApiContractV4_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="53da9-208">UniversalApiContractV4_IsAvailable</span></span>
- <span data-ttu-id="53da9-209">UniversalApiContractV3_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="53da9-209">UniversalApiContractV3_IsAvailable</span></span>

<span data-ttu-id="53da9-210">Non sono previsti piani per aggiungere proprietà a WindowsApiChecker per le versioni future del contratto API.</span><span class="sxs-lookup"><span data-stu-id="53da9-210">There are no plans to add properties to WindowsApiChecker for future API contract versions.</span></span>

<span data-ttu-id="53da9-211">**GltfMeshPrimitiveAttributes di sola lettura**</span><span class="sxs-lookup"><span data-stu-id="53da9-211">**GltfMeshPrimitiveAttributes read-only**</span></span>

<span data-ttu-id="53da9-212">Gli attributi primitivi mesh gltf usati per essere impostati, sono ora di sola lettura.</span><span class="sxs-lookup"><span data-stu-id="53da9-212">The gltf mesh primitive attributes used to be settable, they are now read-only.</span></span> <span data-ttu-id="53da9-213">I valori verranno impostati una volta quando vengono deserializzati.</span><span class="sxs-lookup"><span data-stu-id="53da9-213">Their values will be set once when deserialized.</span></span>

### <a name="custom-button-icon-migration"></a><span data-ttu-id="53da9-214">Icona del pulsante personalizzata migrazione</span><span class="sxs-lookup"><span data-stu-id="53da9-214">Custom Button Icon Migration</span></span>

<span data-ttu-id="53da9-215">Nelle icone dei pulsanti personalizzate in precedenza è necessario assegnare un nuovo materiale al renderer quad del pulsante.</span><span class="sxs-lookup"><span data-stu-id="53da9-215">Previously custom button icons required assigning a new material to the button's quad renderer.</span></span> <span data-ttu-id="53da9-216">Questa operazione non è più necessaria e si consiglia di trasferire le trame delle icone personalizzate in un.</span><span class="sxs-lookup"><span data-stu-id="53da9-216">This is no longer necessary and we recommend moving custom icon textures into an IconSet.</span></span> <span data-ttu-id="53da9-217">Vengono conservati i materiali e le icone personalizzati esistenti.</span><span class="sxs-lookup"><span data-stu-id="53da9-217">Existing custom materials and icons are preserved.</span></span> <span data-ttu-id="53da9-218">Tuttavia, saranno meno ottimali fino a quando non vengono aggiornati.</span><span class="sxs-lookup"><span data-stu-id="53da9-218">However they will be less optimal until upgraded.</span></span>
<span data-ttu-id="53da9-219">Per aggiornare gli asset di tutti i pulsanti nel progetto al nuovo formato consigliato, usare ButtonConfigHelperMigrationHandler.</span><span class="sxs-lookup"><span data-stu-id="53da9-219">To upgrade the assets on all buttons in the project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="53da9-220">(Mixed Reality Toolkit-> Utilities-> finestra di migrazione > selezione del gestore della migrazione-> Microsoft. MixedReality. Toolkit. Utilities. ButtonConfigHelperMigrationHandler)</span><span class="sxs-lookup"><span data-stu-id="53da9-220">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

![Finestra di dialogo Aggiorna finestra](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="53da9-222">Se un'icona non viene trovata nel set di icone predefinito durante la migrazione, viene creato un set di icone personalizzato in MixedRealityToolkit. generated/CustomIconSets.</span><span class="sxs-lookup"><span data-stu-id="53da9-222">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="53da9-223">Una finestra di dialogo indicherà che questa operazione è stata eseguita.</span><span class="sxs-lookup"><span data-stu-id="53da9-223">A dialog will indicate that this has taken place.</span></span>

![Notifica dell'icona personalizzata](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a><span data-ttu-id="53da9-225">Aggiornamento di 2.2.0 a 2.3.0</span><span class="sxs-lookup"><span data-stu-id="53da9-225">Updating 2.2.0 to 2.3.0</span></span>

- [<span data-ttu-id="53da9-226">Modifiche all'API</span><span class="sxs-lookup"><span data-stu-id="53da9-226">API changes</span></span>](#api-changes-in-230)

### <a name="api-changes-in-230"></a><span data-ttu-id="53da9-227">Modifiche alle API in 2.3.0</span><span class="sxs-lookup"><span data-stu-id="53da9-227">API changes in 2.3.0</span></span>

<span data-ttu-id="53da9-228">**ControllerPoseSynchronizer**</span><span class="sxs-lookup"><span data-stu-id="53da9-228">**ControllerPoseSynchronizer**</span></span>

<span data-ttu-id="53da9-229">Il campo ControllerPoseSynchronizer. manualità privato è stato contrassegnato come obsoleto.</span><span class="sxs-lookup"><span data-stu-id="53da9-229">The private ControllerPoseSynchronizer.handedness field has been marked as obsolete.</span></span> <span data-ttu-id="53da9-230">Questa operazione dovrebbe avere un effetto minimo sulle applicazioni perché il campo non è visibile all'esterno della relativa classe.</span><span class="sxs-lookup"><span data-stu-id="53da9-230">This should have minimal impact on applications as the field is not visible outside of its class.</span></span>

<span data-ttu-id="53da9-231">Il metodo di impostazione della proprietà ControllerPoseSynchronizer. manualità è stato rimosso ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span><span class="sxs-lookup"><span data-stu-id="53da9-231">The public ControllerPoseSynchronizer.Handedness property's setter has been removed ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span></span>

<span data-ttu-id="53da9-232">**MSBuild per Unity**</span><span class="sxs-lookup"><span data-stu-id="53da9-232">**MSBuild for Unity**</span></span>

<span data-ttu-id="53da9-233">Questa versione di MRTK usa una versione più recente di MSBuild per Unity rispetto alle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="53da9-233">This version of MRTK uses a newer version of MSBuild for Unity than previous releases.</span></span> <span data-ttu-id="53da9-234">Durante il caricamento del progetto, se la versione precedente è elencata nel manifesto di gestione pacchetti Unity, viene visualizzata la finestra di dialogo di configurazione con l'opzione Abilita MSBuild per Unity selezionata.</span><span class="sxs-lookup"><span data-stu-id="53da9-234">During project load, if the older version is listed in the Unity Package Manger manifest, the configuration dialog will appear, with the Enable MSBuild for Unity option checked.</span></span> <span data-ttu-id="53da9-235">L'applicazione eseguirà un aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="53da9-235">Applying will perform an upgrade.</span></span>

<span data-ttu-id="53da9-236">**ScriptingUtilities**</span><span class="sxs-lookup"><span data-stu-id="53da9-236">**ScriptingUtilities**</span></span>

<span data-ttu-id="53da9-237">La classe ScriptingUtilities è stata contrassegnata come obsoleta ed è stata sostituita da ScriptUtilities nell'assembly Microsoft. MixedReality. Toolkit. Editor. Utilities.</span><span class="sxs-lookup"><span data-stu-id="53da9-237">The ScriptingUtilities class has been marked as obsolete and has been replaced by ScriptUtilities, in the Microsoft.MixedReality.Toolkit.Editor.Utilities assembly.</span></span> <span data-ttu-id="53da9-238">La nuova classe perfeziona il comportamento precedente e aggiunge il supporto per la rimozione delle definizioni di scripting.</span><span class="sxs-lookup"><span data-stu-id="53da9-238">The new class refines previous behavior and adds support for removing scripting definitions.</span></span>

<span data-ttu-id="53da9-239">Mentre il codice esistente continuerà a funzionare nella versione 2.3.0, è consigliabile eseguire l'aggiornamento alla nuova classe.</span><span class="sxs-lookup"><span data-stu-id="53da9-239">While existing code will continue to function in version 2.3.0, it is recommended to update to the new class.</span></span>

<span data-ttu-id="53da9-240">**ShellHandRayPointer**</span><span class="sxs-lookup"><span data-stu-id="53da9-240">**ShellHandRayPointer**</span></span>

<span data-ttu-id="53da9-241">I membri lineRendererSelected e lineRendererNoTarget della classe ShellHandRayPointer sono stati sostituiti rispettivamente da lineMaterialSelected e lineMaterialNoTarget ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span><span class="sxs-lookup"><span data-stu-id="53da9-241">The lineRendererSelected and lineRendererNoTarget members of the ShellHandRayPointer class have been replaced by lineMaterialSelected and lineMaterialNoTarget, respectively ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span></span>

<span data-ttu-id="53da9-242">Sostituire lineRendererSelected con lineMaterialSelected e/o lineRendererNoTarget con lineMaterialNoTarget per risolvere gli errori di compilazione.</span><span class="sxs-lookup"><span data-stu-id="53da9-242">Please replace lineRendererSelected with lineMaterialSelected and/or lineRendererNoTarget with lineMaterialNoTarget to resolve compile errors.</span></span>

<span data-ttu-id="53da9-243">**Startupbehavior facendo osservatore spaziale**</span><span class="sxs-lookup"><span data-stu-id="53da9-243">**Spatial observer StartupBehavior**</span></span>

<span data-ttu-id="53da9-244">Gli osservatori spaziali basati sulla `BaseSpatialObserver` classe ora rispettano il valore di startupbehavior facendo quando viene riabilitato ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span><span class="sxs-lookup"><span data-stu-id="53da9-244">Spatial observers built upon the `BaseSpatialObserver` class now honor the value of StartupBehavior when re-enabled ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span></span>

<span data-ttu-id="53da9-245">Non sono necessarie modifiche per sfruttare questa correzione.</span><span class="sxs-lookup"><span data-stu-id="53da9-245">No changes are required to take advantage of this fix.</span></span>

<span data-ttu-id="53da9-246">**Prefabbricati del controllo UX aggiornati per l'uso di PressableButton**</span><span class="sxs-lookup"><span data-stu-id="53da9-246">**UX control prefabs updated to use PressableButton**</span></span>

<span data-ttu-id="53da9-247">I prefabbricati seguenti usano ora il componente PressableButton anziché TouchHandler per l'interazione near ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span><span class="sxs-lookup"><span data-stu-id="53da9-247">The following prefabs are now using the PressableButton component instead of TouchHandler for near interaction ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span></span>

- <span data-ttu-id="53da9-248">AnimationButton</span><span class="sxs-lookup"><span data-stu-id="53da9-248">AnimationButton</span></span>
- <span data-ttu-id="53da9-249">Pulsante</span><span class="sxs-lookup"><span data-stu-id="53da9-249">Button</span></span>
- <span data-ttu-id="53da9-250">ButtonHoloLens1</span><span class="sxs-lookup"><span data-stu-id="53da9-250">ButtonHoloLens1</span></span>
- <span data-ttu-id="53da9-251">ButtonHoloLens1Toggle</span><span class="sxs-lookup"><span data-stu-id="53da9-251">ButtonHoloLens1Toggle</span></span>
- <span data-ttu-id="53da9-252">CheckBox</span><span class="sxs-lookup"><span data-stu-id="53da9-252">CheckBox</span></span>
- <span data-ttu-id="53da9-253">RadialSet</span><span class="sxs-lookup"><span data-stu-id="53da9-253">RadialSet</span></span>
- <span data-ttu-id="53da9-254">ToggleButton</span><span class="sxs-lookup"><span data-stu-id="53da9-254">ToggleButton</span></span>
- <span data-ttu-id="53da9-255">ToggleSwitch</span><span class="sxs-lookup"><span data-stu-id="53da9-255">ToggleSwitch</span></span>
- <span data-ttu-id="53da9-256">UnityUIButton</span><span class="sxs-lookup"><span data-stu-id="53da9-256">UnityUIButton</span></span>
- <span data-ttu-id="53da9-257">UnityUICheckboxButton</span><span class="sxs-lookup"><span data-stu-id="53da9-257">UnityUICheckboxButton</span></span>
- <span data-ttu-id="53da9-258">UnityUIRadialButton</span><span class="sxs-lookup"><span data-stu-id="53da9-258">UnityUIRadialButton</span></span>
- <span data-ttu-id="53da9-259">UnityUIToggleButton</span><span class="sxs-lookup"><span data-stu-id="53da9-259">UnityUIToggleButton</span></span>

<span data-ttu-id="53da9-260">Il codice dell'applicazione può richiedere l'aggiornamento a causa di questa modifica.</span><span class="sxs-lookup"><span data-stu-id="53da9-260">Application code may require updating due to this change.</span></span>

<span data-ttu-id="53da9-261">**Spazio dei nomi WindowsMixedRealityUtilities**</span><span class="sxs-lookup"><span data-stu-id="53da9-261">**WindowsMixedRealityUtilities namespace**</span></span>

<span data-ttu-id="53da9-262">Lo spazio dei nomi di WindowsMixedRealityUtilities è stato modificato da Microsoft. MixedReality. Toolkit. WindowsMixedReality. input a Microsoft. MixedReality. Toolkit. WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span><span class="sxs-lookup"><span data-stu-id="53da9-262">The namespace of WindowsMixedRealityUtilities changed from Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input to Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span></span>

<span data-ttu-id="53da9-263">Aggiornare #using le istruzioni per risolvere gli errori di compilazione.</span><span class="sxs-lookup"><span data-stu-id="53da9-263">Please update #using statements to resolve compile errors.</span></span>

## <a name="updating-210-to-220"></a><span data-ttu-id="53da9-264">Aggiornamento di 2.1.0 a 2.2.0</span><span class="sxs-lookup"><span data-stu-id="53da9-264">Updating 2.1.0 to 2.2.0</span></span>

- [<span data-ttu-id="53da9-265">Modifiche all'API</span><span class="sxs-lookup"><span data-stu-id="53da9-265">API changes</span></span>](#api-changes-in-220)

### <a name="api-changes-in-220"></a><span data-ttu-id="53da9-266">Modifiche alle API in 2.2.0</span><span class="sxs-lookup"><span data-stu-id="53da9-266">API changes in 2.2.0</span></span>

<span data-ttu-id="53da9-267">**IMixedRealityBoundarySystem. Contains**</span><span class="sxs-lookup"><span data-stu-id="53da9-267">**IMixedRealityBoundarySystem.Contains**</span></span>

<span data-ttu-id="53da9-268">Questo metodo ha eseguito in precedenza un'enumerazione sperimentale specifica definita da Unity.</span><span class="sxs-lookup"><span data-stu-id="53da9-268">This method previously took in a specific, Unity-defined experimental enum.</span></span> <span data-ttu-id="53da9-269">Ora accetta un'enumerazione definita da MRTK che è identica all'enumerazione Unity.</span><span class="sxs-lookup"><span data-stu-id="53da9-269">It now takes in an MRTK-defined enum that's identical to the Unity enum.</span></span> <span data-ttu-id="53da9-270">Questa modifica consente di preparare il MRTK per le API limite future di Unity.</span><span class="sxs-lookup"><span data-stu-id="53da9-270">This change helps prepare the MRTK for Unity's future boundary APIs.</span></span>

<span data-ttu-id="53da9-271">**MixedRealityServiceProfileAttribute**</span><span class="sxs-lookup"><span data-stu-id="53da9-271">**MixedRealityServiceProfileAttribute**</span></span>

<span data-ttu-id="53da9-272">Per descrivere meglio i requisiti per il supporto di un profilo, MixedRealityServiceProfileAttribute è stato aggiornato per aggiungere una raccolta facoltativa di tipi esclusi.</span><span class="sxs-lookup"><span data-stu-id="53da9-272">To better describe the requirements for supporting a profile, the MixedRealityServiceProfileAttribute has been updated to add an optional collection of excluded types.</span></span> <span data-ttu-id="53da9-273">Come parte di questa modifica, la proprietà ServiceType è stata modificata dal tipo al tipo [] ed è stata rinominata in RequiredTypes.</span><span class="sxs-lookup"><span data-stu-id="53da9-273">As part of this change, the ServiceType property has been changed from Type to Type[] and been renamed to RequiredTypes.</span></span>

<span data-ttu-id="53da9-274">È stata aggiunta anche una seconda proprietà, ExcludedTypes.</span><span class="sxs-lookup"><span data-stu-id="53da9-274">A second property, ExcludedTypes has also been added.</span></span>

## <a name="updating-200-to-210"></a><span data-ttu-id="53da9-275">Aggiornamento di 2.0.0 a 2.1.0</span><span class="sxs-lookup"><span data-stu-id="53da9-275">Updating 2.0.0 to 2.1.0</span></span>

- [<span data-ttu-id="53da9-276">Modifiche all'API</span><span class="sxs-lookup"><span data-stu-id="53da9-276">API changes</span></span>](#api-changes-in-210)
- [<span data-ttu-id="53da9-277">Modifiche del profilo</span><span class="sxs-lookup"><span data-stu-id="53da9-277">Profile changes</span></span>](#profile-changes-in-210)

### <a name="api-changes-in-210"></a><span data-ttu-id="53da9-278">Modifiche alle API in 2.1.0</span><span class="sxs-lookup"><span data-stu-id="53da9-278">API changes in 2.1.0</span></span>

<span data-ttu-id="53da9-279">**BaseNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="53da9-279">**BaseNearInteractionTouchable**</span></span>

<span data-ttu-id="53da9-280">`BaseNearInteractionTouchable`È stato modificato per contrassegnare il `OnValidate` metodo come virtuale.</span><span class="sxs-lookup"><span data-stu-id="53da9-280">The `BaseNearInteractionTouchable` has been modified to mark the `OnValidate` method as virtual.</span></span> <span data-ttu-id="53da9-281">Le classi che estendono, `BaseNearInteractionTouchable` `NearInteractionTouchableUnityUI` ad esempio, sono state aggiornate per riflettere questa modifica.</span><span class="sxs-lookup"><span data-stu-id="53da9-281">Classes that extend `BaseNearInteractionTouchable` (ex: `NearInteractionTouchableUnityUI`) have been updated to reflect this change.</span></span>

<span data-ttu-id="53da9-282">**ColliderNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="53da9-282">**ColliderNearInteractionTouchable**</span></span>

<span data-ttu-id="53da9-283">La classe `ColliderNearInteractionTouchable` è stata deprecata.</span><span class="sxs-lookup"><span data-stu-id="53da9-283">The `ColliderNearInteractionTouchable` class has been deprecated.</span></span> <span data-ttu-id="53da9-284">Aggiornare i riferimenti al codice da usare `BaseNearInteractionTouchable` .</span><span class="sxs-lookup"><span data-stu-id="53da9-284">Please update code references to use `BaseNearInteractionTouchable`.</span></span>

<span data-ttu-id="53da9-285">**IMixedRealityMouseDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="53da9-285">**IMixedRealityMouseDeviceManager**</span></span>

<span data-ttu-id="53da9-286">**_Aggiunto_**</span><span class="sxs-lookup"><span data-stu-id="53da9-286">**_Added_**</span></span>

<span data-ttu-id="53da9-287">`IMixedRealityMouseDeviceManager` sono state aggiunte `CursorSpeed` le `WheelSpeed` proprietà e.</span><span class="sxs-lookup"><span data-stu-id="53da9-287">`IMixedRealityMouseDeviceManager` has been added `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="53da9-288">Queste proprietà consentono alle applicazioni di specificare un valore moltiplicatore in base al quale verrà ridimensionata rispettivamente la velocità del cursore e della rotellina.</span><span class="sxs-lookup"><span data-stu-id="53da9-288">These properties allow applications to specify a multiplier value by which the speed of the cursor and wheel, respectively will be scaled.</span></span>

<span data-ttu-id="53da9-289">Si tratta di una modifica sostanziale che richiede la modifica delle implementazioni di gestione dispositivi del mouse esistenti.</span><span class="sxs-lookup"><span data-stu-id="53da9-289">This is a breaking change and requires existing mouse device manager implementations to be modified .</span></span>

>[!NOTE]
><span data-ttu-id="53da9-290">Questa modifica non è compatibile con le versioni precedenti della versione 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="53da9-290">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="53da9-291">**_Deprecato_**</span><span class="sxs-lookup"><span data-stu-id="53da9-291">**_Deprecated_**</span></span>

<span data-ttu-id="53da9-292">La `MouseInputProfile` proprietà è stata contrassegnata come obsoleta e verrà rimossa da una versione futura di Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="53da9-292">The `MouseInputProfile` property has been marked as obsolete and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="53da9-293">Si consiglia di non usare più questa proprietà per il codice dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="53da9-293">It is recommended that application code no longer use this property.</span></span>

<span data-ttu-id="53da9-294">**Con cui**</span><span class="sxs-lookup"><span data-stu-id="53da9-294">**Interactable**</span></span>

<span data-ttu-id="53da9-295">I metodi e le proprietà seguenti sono stati deprecati e verranno rimossi da una versione futura di Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="53da9-295">The following methods and properties have been deprecated and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="53da9-296">È consigliabile aggiornare il codice dell'applicazione in base alle linee guida contenute nell'attributo obsolete e visualizzarle nella console di.</span><span class="sxs-lookup"><span data-stu-id="53da9-296">The recommendation is to update application code per the guidance contained in the Obsolete attribute and displayed in the console.</span></span>

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

<span data-ttu-id="53da9-297">**NearInteractionTouchableSurface**</span><span class="sxs-lookup"><span data-stu-id="53da9-297">**NearInteractionTouchableSurface**</span></span>

<span data-ttu-id="53da9-298">La `NearInteractionTouchableSurface` classe è stata aggiunta e ora funge da classe di base per `NearInteractionTouchable` e `NearInteractionTouchableUnityUI` .</span><span class="sxs-lookup"><span data-stu-id="53da9-298">The `NearInteractionTouchableSurface` class has been added and now serves as the base class for `NearInteractionTouchable` and `NearInteractionTouchableUnityUI`.</span></span>

### <a name="profile-changes-in-210"></a><span data-ttu-id="53da9-299">Modifiche del profilo in 2.1.0</span><span class="sxs-lookup"><span data-stu-id="53da9-299">Profile changes in 2.1.0</span></span>

<span data-ttu-id="53da9-300">**Profilo di rilevamento mano**</span><span class="sxs-lookup"><span data-stu-id="53da9-300">**Hand tracking profile**</span></span>

<span data-ttu-id="53da9-301">La mesh mano e le visualizzazioni congiunte dispongono ora di impostazioni distinte per l'editor e il lettore.</span><span class="sxs-lookup"><span data-stu-id="53da9-301">The hand mesh and joint visualizations now have a separate editor and player settings.</span></span> <span data-ttu-id="53da9-302">Il profilo di rilevamento della mano è stato aggiornato per consentire l'impostazione di queste visualizzazioni su; Niente, tutto, editor o lettore.</span><span class="sxs-lookup"><span data-stu-id="53da9-302">The hand tracking profile has been updated to allow for setting these visualizations to; Nothing, Everything, Editor or Player.</span></span>

![Modalità di visualizzazione mano](../features/images/release-notes/HandTrackingVisualizationModes.png)

<span data-ttu-id="53da9-304">Potrebbe essere necessario aggiornare i profili di rilevamento mano personalizzati per funzionare correttamente con la versione 2.1.0.</span><span class="sxs-lookup"><span data-stu-id="53da9-304">Custom hand tracking profiles may need to be updated to work correctly with version 2.1.0.</span></span>

>[!NOTE]
><span data-ttu-id="53da9-305">Questa modifica non è compatibile con le versioni precedenti della versione 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="53da9-305">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="53da9-306">**Profilo simulazione di input**</span><span class="sxs-lookup"><span data-stu-id="53da9-306">**Input simulation profile**</span></span>

<span data-ttu-id="53da9-307">Il sistema di simulazione di input è stato aggiornato, che consente di modificare alcune impostazioni nel profilo di simulazione di input.</span><span class="sxs-lookup"><span data-stu-id="53da9-307">The input simulation system has been upgraded, which changes a few settings in the input simulation profile.</span></span> <span data-ttu-id="53da9-308">Non è possibile eseguire la migrazione automatica di alcune modifiche e gli utenti potrebbero rilevare che i profili utilizzano valori predefiniti.</span><span class="sxs-lookup"><span data-stu-id="53da9-308">Some changes can not be migrated automatically and users may find that profiles are using default values.</span></span>

1. <span data-ttu-id="53da9-309">Tutti i binding dei pulsanti del mouse e del KeyCode nel profilo sono stati sostituiti con uno `KeyBinding` struct generico, che archivia il tipo di binding (chiave o mouse), nonché il codice di associazione effettivo (rispettivamente, il numero di tasto del mouse o il prefisso).</span><span class="sxs-lookup"><span data-stu-id="53da9-309">All KeyCode and mouse button bindings in the profile have been replaced with a generic `KeyBinding` struct, which stores the type of binding (key or mouse) as well as the actual binding code (KeyCode or mouse button number respectively).</span></span> <span data-ttu-id="53da9-310">Lo struct dispone di un proprio controllo, che consente la visualizzazione unificata e offre uno strumento di associazione automatica per impostare rapidamente le combinazioni di tasti premendo la rispettiva chiave invece di selezionare da un elenco a discesa di grandi dimensioni.</span><span class="sxs-lookup"><span data-stu-id="53da9-310">The struct has its own inspector, which allows unified display and offers an "auto-bind" tool to quickly set key bindings by pressing the respective key instead of selecting from a huge dropdown list.</span></span>

    - <span data-ttu-id="53da9-311">FastControlKey</span><span class="sxs-lookup"><span data-stu-id="53da9-311">FastControlKey</span></span>
    - <span data-ttu-id="53da9-312">ToggleLeftHandKey</span><span class="sxs-lookup"><span data-stu-id="53da9-312">ToggleLeftHandKey</span></span>
    - <span data-ttu-id="53da9-313">ToggleRightHandKey</span><span class="sxs-lookup"><span data-stu-id="53da9-313">ToggleRightHandKey</span></span>
    - <span data-ttu-id="53da9-314">LeftHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="53da9-314">LeftHandManipulationKey</span></span>
    - <span data-ttu-id="53da9-315">RightHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="53da9-315">RightHandManipulationKey</span></span>

1. <span data-ttu-id="53da9-316">`MouseLookToggle` in precedenza era incluso nell' `MouseLookButton` enum come `InputSimulationMouseButton.Focused` , ora è un'opzione separata.</span><span class="sxs-lookup"><span data-stu-id="53da9-316">`MouseLookToggle` was previously included in the `MouseLookButton` enum as `InputSimulationMouseButton.Focused`, it is now a separate option.</span></span> <span data-ttu-id="53da9-317">Se abilitata, la fotocamera continuerà a ruotare con il mouse dopo aver rilasciato il pulsante, fino a quando non viene premuto il tasto di escape.</span><span class="sxs-lookup"><span data-stu-id="53da9-317">When enabled, the camera will keep rotating with the mouse after releasing the button, until the escape key is pressed.</span></span>
1. <span data-ttu-id="53da9-318">`HandDepthMultiplier` il valore predefinito è stato abbassato da 0,1 a 0,03 per adattare alcune modifiche alla simulazione di input.</span><span class="sxs-lookup"><span data-stu-id="53da9-318">`HandDepthMultiplier` default value has been lowered from 0.1 to 0.03 to accommodate some changes to the input simulation.</span></span> <span data-ttu-id="53da9-319">Se lo scorrimento della fotocamera si sposta troppo rapidamente, provare a ridurre questo valore.</span><span class="sxs-lookup"><span data-stu-id="53da9-319">If the camera moves too fast when scrolling, try lowering this value.</span></span>
1. <span data-ttu-id="53da9-320">Le chiavi per la rotazione delle mani sono state rimosse. la rotazione della mano è ora controllata anche dal mouse.</span><span class="sxs-lookup"><span data-stu-id="53da9-320">Keys for rotating hands have been removed, hand rotation is now controlled by the mouse as well.</span></span> <span data-ttu-id="53da9-321">Tenendo premuto `HandRotateButton` (CTRL) insieme alla chiave di manipolazione a sinistra/destra (LShift/spazio), viene abilitata la rotazione della mano.</span><span class="sxs-lookup"><span data-stu-id="53da9-321">Holding `HandRotateButton` (Ctrl) together with the left/right hand manipulation key (LShift/Space) will enable hand rotation.</span></span>
1. <span data-ttu-id="53da9-322">È stato introdotto un nuovo asse "UpDown" nell'elenco degli assi di input.</span><span class="sxs-lookup"><span data-stu-id="53da9-322">A new axis "UpDown" has been introduced to the input axis list.</span></span> <span data-ttu-id="53da9-323">Questo controlla lo spostamento della fotocamera in verticale e il valore predefinito per le chiavi Q/E, nonché i pulsanti del trigger del controller.</span><span class="sxs-lookup"><span data-stu-id="53da9-323">This controls camera movement in the vertical and defaults to Q/E keys as well as the controller trigger buttons.</span></span>

<span data-ttu-id="53da9-324">Per ulteriori informazioni su queste modifiche, vedere l'articolo relativo al [servizio di simulazione input](../features/input-simulation/input-simulation-service.md) .</span><span class="sxs-lookup"><span data-stu-id="53da9-324">For more information on these changes, please see the [input simulation service](../features/input-simulation/input-simulation-service.md) article.</span></span>

<span data-ttu-id="53da9-325">**Profilo provider di dati del mouse**</span><span class="sxs-lookup"><span data-stu-id="53da9-325">**Mouse data provider profile**</span></span>

<span data-ttu-id="53da9-326">Il profilo del provider di dati del mouse è stato aggiornato per esporre le nuove `CursorSpeed` `WheelSpeed` proprietà e.</span><span class="sxs-lookup"><span data-stu-id="53da9-326">The mouse data provider profile has been updated to expose the new `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="53da9-327">Ai profili personalizzati esistenti verranno automaticamente specificati i valori predefiniti.</span><span class="sxs-lookup"><span data-stu-id="53da9-327">Existing custom profiles will automatically have default values provided.</span></span> <span data-ttu-id="53da9-328">Quando il profilo viene salvato, questi nuovi valori saranno resi permanente.</span><span class="sxs-lookup"><span data-stu-id="53da9-328">When the profile is saved, these new values will be persisted.</span></span>

<span data-ttu-id="53da9-329">**Profilo di mapping del controller**</span><span class="sxs-lookup"><span data-stu-id="53da9-329">**Controller mapping profile**</span></span>

<span data-ttu-id="53da9-330">Alcuni assi e tipi di input sono stati aggiornati in 2.1.0, in particolare per la piattaforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="53da9-330">Some axes and input types have been updated in 2.1.0, especially around the OpenVR platform.</span></span> <span data-ttu-id="53da9-331">Quando si esegue l'aggiornamento, assicurarsi di selezionare **MixedRealityToolkit-> Utilities-> i profili di mapping del controller di aggiornamento->** .</span><span class="sxs-lookup"><span data-stu-id="53da9-331">Please be sure to select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** when upgrading.</span></span> <span data-ttu-id="53da9-332">In questo caso i profili di mapping del controller personalizzato vengono aggiornati con gli assi e i dati aggiornati, lasciando intatti le azioni di input personalizzate.</span><span class="sxs-lookup"><span data-stu-id="53da9-332">This will update any custom Controller Mapping Profiles with the updated axes and data, while leaving your custom-assigned input actions intact.</span></span>

## <a name="updating-rc2-to-200"></a><span data-ttu-id="53da9-333">Aggiornamento RC2 alla 2.0.0</span><span class="sxs-lookup"><span data-stu-id="53da9-333">Updating RC2 to 2.0.0</span></span>

<span data-ttu-id="53da9-334">Tra le versioni RC2 e 2.0.0 del Toolkit Microsoft Mixed Reality, sono state apportate modifiche che potrebbero influito sui progetti esistenti.</span><span class="sxs-lookup"><span data-stu-id="53da9-334">Between the RC2 and 2.0.0 releases of the Microsoft Mixed Reality Toolkit, changes were made that may impact existing projects.</span></span> <span data-ttu-id="53da9-335">Questo documento descrive le modifiche e come aggiornare i progetti alla versione 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="53da9-335">This document describes those changes and how to update projects to the 2.0.0 release.</span></span>

- [<span data-ttu-id="53da9-336">Modifiche all'API</span><span class="sxs-lookup"><span data-stu-id="53da9-336">API changes</span></span>](#api-changes-in-200)
- [<span data-ttu-id="53da9-337">Modifiche al nome dell'assembly</span><span class="sxs-lookup"><span data-stu-id="53da9-337">Assembly name changes</span></span>](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a><span data-ttu-id="53da9-338">Modifiche alle API nella 2.0.0</span><span class="sxs-lookup"><span data-stu-id="53da9-338">API changes in 2.0.0</span></span>

<span data-ttu-id="53da9-339">Dalla versione RC2 sono state apportate alcune modifiche alle API, incluse alcune che potrebbero comportare interruzioni dei progetti esistenti.</span><span class="sxs-lookup"><span data-stu-id="53da9-339">Since the release of RC2, there have been a number of API changes including some that may break existing projects.</span></span> <span data-ttu-id="53da9-340">Le sezioni seguenti descrivono le modifiche che si sono verificate tra le versioni RC2 e 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="53da9-340">The following sections describe the changes that have occurred between the RC2 and 2.0.0 releases.</span></span>

<span data-ttu-id="53da9-341">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="53da9-341">**MixedRealityToolkit**</span></span>

<span data-ttu-id="53da9-342">Le seguenti proprietà pubbliche nell'oggetto MixedRealityToolkit sono state deprecate.</span><span class="sxs-lookup"><span data-stu-id="53da9-342">The following public properties on the MixedRealityToolkit object have been deprecated.</span></span>

- <span data-ttu-id="53da9-343">`RegisteredMixedRealityServices` non contiene più la raccolta di servizi e provider di dati delle estensioni registrate.</span><span class="sxs-lookup"><span data-stu-id="53da9-343">`RegisteredMixedRealityServices` no longer contains the collection of registered extensions services and data providers.</span></span>

<span data-ttu-id="53da9-344">Per accedere ai servizi di estensione, utilizzare `MixedRealityServiceRegistry.TryGetService<T>` .</span><span class="sxs-lookup"><span data-stu-id="53da9-344">To access extension services, use `MixedRealityServiceRegistry.TryGetService<T>`.</span></span> <span data-ttu-id="53da9-345">Per accedere ai provider di dati, eseguire il cast dell'istanza del servizio a [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) e utilizzare `GetDataProvider<T>` .</span><span class="sxs-lookup"><span data-stu-id="53da9-345">To access data providers, cast the service instance to [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) and use `GetDataProvider<T>`.</span></span>

<span data-ttu-id="53da9-346">Utilizzare [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) o [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) invece per le seguenti proprietà deprecate</span><span class="sxs-lookup"><span data-stu-id="53da9-346">Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) or [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) instead for the following deprecated properties</span></span>

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

<span data-ttu-id="53da9-347">**CoreServices**</span><span class="sxs-lookup"><span data-stu-id="53da9-347">**CoreServices**</span></span>

<span data-ttu-id="53da9-348">La [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) classe è la sostituzione per le funzioni di accesso di sistema statiche (ad esempio, BoundarySystem) trovate nell' `MixedRealityToolkit` oggetto.</span><span class="sxs-lookup"><span data-stu-id="53da9-348">The [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) class is the replacement for the static system accessors (ex: BoundarySystem) found in the `MixedRealityToolkit` object.</span></span>

>[!IMPORTANT]
><span data-ttu-id="53da9-349">Le `MixedRealityToolkit` funzioni di accesso di sistema sono state deprecate nella versione 2.0.0 e verranno rimosse in una versione futura di MRTK.</span><span class="sxs-lookup"><span data-stu-id="53da9-349">The `MixedRealityToolkit` system accessors have been deprecated in version 2.0.0 and will be removed in a future release of the MRTK.</span></span>

<span data-ttu-id="53da9-350">Nell'esempio di codice seguente vengono illustrati il vecchio e il nuovo modello.</span><span class="sxs-lookup"><span data-stu-id="53da9-350">The following code example illustrates the old and the new pattern.</span></span>

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

<span data-ttu-id="53da9-351">Se si utilizza la nuova classe CoreSystem, il codice dell'applicazione non richiederà l'aggiornamento se si modifica l'applicazione per l'utilizzo di un registrar del servizio diverso (ad esempio, uno dei responsabili del servizio sperimentale).</span><span class="sxs-lookup"><span data-stu-id="53da9-351">Using the new CoreSystem class will ensure that your application code will not need updating if you change the application to use a different service registrar (ex: one of the experimental service managers).</span></span>

<span data-ttu-id="53da9-352">**IMixedRealityRaycastProvider**</span><span class="sxs-lookup"><span data-stu-id="53da9-352">**IMixedRealityRaycastProvider**</span></span>

<span data-ttu-id="53da9-353">Con l'aggiunta di IMixedRealityRaycastProvider, il profilo di configurazione del sistema di input è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="53da9-353">With the addition of the IMixedRealityRaycastProvider, the input system configuration profile was changed.</span></span> <span data-ttu-id="53da9-354">Se si dispone di un profilo personalizzato, è possibile che vengano visualizzati gli errori nell'immagine seguente quando si esegue l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="53da9-354">If you have a custom profile, you may receive the errors in the following image when you run your application.</span></span>

![Selezione del provider Raycast 1](../features/images/release-notes/UnableToRegisterRaycastProvider.png)

<span data-ttu-id="53da9-356">Per risolvere il problema, aggiungere un'istanza di IMixedRealityRaycastProvider al profilo di sistema di input.</span><span class="sxs-lookup"><span data-stu-id="53da9-356">To fix these, please add an IMixedRealityRaycastProvider instance to your input system profile.</span></span>

![Selezione del provider Raycast 2](../features/images/release-notes/SelectRaycastProvider.png)

<span data-ttu-id="53da9-358">**Sistema di eventi**</span><span class="sxs-lookup"><span data-stu-id="53da9-358">**Event System**</span></span>

- <span data-ttu-id="53da9-359">I `IMixedRealityEventSystem` metodi dell'API obsoleti `Register` e `Unregister` sono stati contrassegnati come obsoleti.</span><span class="sxs-lookup"><span data-stu-id="53da9-359">The `IMixedRealityEventSystem` old API methods `Register` and `Unregister` have been marked as obsolete.</span></span> <span data-ttu-id="53da9-360">Sono conservati per la compatibilità con le versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="53da9-360">They are preserved for backwards compatibility.</span></span>
- <span data-ttu-id="53da9-361">`InputSystemGlobalListener` è stato contrassegnato come obsoleto.</span><span class="sxs-lookup"><span data-stu-id="53da9-361">`InputSystemGlobalListener` has been marked as obsolete.</span></span> <span data-ttu-id="53da9-362">La relativa funzionalità non è stata modificata.</span><span class="sxs-lookup"><span data-stu-id="53da9-362">Its functionality has not changed.</span></span>
- <span data-ttu-id="53da9-363">`BaseInputHandler` la classe base è stata modificata da `InputSystemGlobalListener` a `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="53da9-363">`BaseInputHandler` base class has been changed from `InputSystemGlobalListener` to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="53da9-364">Si tratta di una modifica di rilievo per qualsiasi discendente di `BaseInputHandler` .</span><span class="sxs-lookup"><span data-stu-id="53da9-364">This is a breaking change for any descendants of `BaseInputHandler`.</span></span>

<span data-ttu-id="53da9-365">**_Motivazione alla base della modifica_**</span><span class="sxs-lookup"><span data-stu-id="53da9-365">**_Motivation behind the change_**</span></span>

<span data-ttu-id="53da9-366">L'API del sistema di eventi precedente `Register` e `Unregister` potrebbe causare più problemi in fase di esecuzione, Main:</span><span class="sxs-lookup"><span data-stu-id="53da9-366">The old event system API `Register` and `Unregister` could potentially cause multiple issues in runtime, main being:</span></span>

- <span data-ttu-id="53da9-367">Se un componente si registra per gli eventi globali, riceverà gli eventi di input globali di *tutti i* tipi.</span><span class="sxs-lookup"><span data-stu-id="53da9-367">If a component registers for global events, it would receive global input events of *all* types.</span></span>
- <span data-ttu-id="53da9-368">Se uno dei componenti di un oggetto viene registrato per gli eventi di input globali, tutti i componenti di questo oggetto riceveranno gli eventi di input globali di *tutti i* tipi.</span><span class="sxs-lookup"><span data-stu-id="53da9-368">If one of the components on an object registers for global input events, all components on this object will receive global input events of *all* types.</span></span>
- <span data-ttu-id="53da9-369">Se due componenti sullo stesso oggetto si registrano in eventi globali e uno è disabilitato in fase di esecuzione, il secondo arresta la ricezione di eventi globali.</span><span class="sxs-lookup"><span data-stu-id="53da9-369">If two components on the same object register to global events, and then one is disabled in runtime, the second one stops receiving global events.</span></span>

<span data-ttu-id="53da9-370">Nuova API `RegisterHandler` e `UnregisterHandler` :</span><span class="sxs-lookup"><span data-stu-id="53da9-370">New API `RegisterHandler` and `UnregisterHandler`:</span></span>

- <span data-ttu-id="53da9-371">Fornisce un controllo esplicito e granulare su quali eventi di input devono essere ascoltati a livello globale e che devono essere basati su uno stato attivo.</span><span class="sxs-lookup"><span data-stu-id="53da9-371">Provides an explicit and granular control over which input events should be listened to globally and which should be focused-based.</span></span>
- <span data-ttu-id="53da9-372">Consente a più componenti sullo stesso oggetto di restare in ascolto di eventi globali in modo indipendente l'uno dall'altro.</span><span class="sxs-lookup"><span data-stu-id="53da9-372">Allows multiple components on the same object to listen to global events independently on each other.</span></span>

<span data-ttu-id="53da9-373">**_Come eseguire la migrazione_**</span><span class="sxs-lookup"><span data-stu-id="53da9-373">**_How to migrate_**</span></span>

- <span data-ttu-id="53da9-374">Se è stata chiamata l' `Register` / `Unregister` API direttamente prima, sostituire queste chiamate con le chiamate a `RegisterHandler` / `UnregisterHandler` .</span><span class="sxs-lookup"><span data-stu-id="53da9-374">If you have been calling `Register`/`Unregister` API directly before, replace these calls with calls to `RegisterHandler`/`UnregisterHandler`.</span></span> <span data-ttu-id="53da9-375">Usare le interfacce del gestore implementate come parametri generici.</span><span class="sxs-lookup"><span data-stu-id="53da9-375">Use handler interfaces you implement as generic parameters.</span></span> <span data-ttu-id="53da9-376">Se si implementano più interfacce e molte di esse sono in ascolto di eventi di input globali, chiamare `RegisterHandler` più volte.</span><span class="sxs-lookup"><span data-stu-id="53da9-376">If you implement multiple interfaces, and several of them listen to global input events, call `RegisterHandler` multiple times.</span></span>
- <span data-ttu-id="53da9-377">Se è stata ereditata da `InputSystemGlobalListener` , modificare l'ereditarietà in `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="53da9-377">If you have been inheriting from `InputSystemGlobalListener`, change inheritance to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="53da9-378">Implementano `RegisterHandlers` `UnregisterHandlers` metodi astratti e.</span><span class="sxs-lookup"><span data-stu-id="53da9-378">Implement `RegisterHandlers` and `UnregisterHandlers` abstract methods.</span></span> <span data-ttu-id="53da9-379">Nella chiamata di implementazione `inputSystem.RegisterHandler` ( `inputSystem.UnregisterHandler` ) per eseguire la registrazione in tutte le interfacce del gestore per cui si desidera ascoltare gli eventi globali.</span><span class="sxs-lookup"><span data-stu-id="53da9-379">In the implementation call `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) to register on all handler interfaces you want to listen global events for.</span></span>
- <span data-ttu-id="53da9-380">Se è stata ereditata da `BaseInputHandler` , implementare `RegisterHandlers` e i `UnregisterHandlers` metodi astratti (come per `InputSystemGlobalListener` ).</span><span class="sxs-lookup"><span data-stu-id="53da9-380">If you have been inheriting from `BaseInputHandler`, implement `RegisterHandlers` and `UnregisterHandlers` abstract methods (same as for `InputSystemGlobalListener`).</span></span>

<span data-ttu-id="53da9-381">**_Esempi di migrazione_**</span><span class="sxs-lookup"><span data-stu-id="53da9-381">**_Examples of migration_**</span></span>

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

<span data-ttu-id="53da9-382">**Consapevolezza spaziale**</span><span class="sxs-lookup"><span data-stu-id="53da9-382">**Spatial Awareness**</span></span>

<span data-ttu-id="53da9-383">Per le interfacce IMixedRealitySpatialAwarenessSystem e IMixedRealitySpatialAwarenessObserver sono state apportate più modifiche di rilievo, come descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="53da9-383">The IMixedRealitySpatialAwarenessSystem and IMixedRealitySpatialAwarenessObserver interfaces have taken multiple breaking changes as described below.</span></span>

<span data-ttu-id="53da9-384">**_Modifiche_**</span><span class="sxs-lookup"><span data-stu-id="53da9-384">**_Changes_**</span></span>

<span data-ttu-id="53da9-385">I metodi seguenti sono stati rinominati per descrivere meglio l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="53da9-385">The following method(s) have been renamed to better describe their usage.</span></span>

- <span data-ttu-id="53da9-386">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` è stato rinominato in `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` per chiarirne l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="53da9-386">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` has been renamed to `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` to clarify its usage.</span></span>

<span data-ttu-id="53da9-387">**_Aggiornamenti_**</span><span class="sxs-lookup"><span data-stu-id="53da9-387">**_Additions_**</span></span>

<span data-ttu-id="53da9-388">In base ai commenti e suggerimenti dei clienti, è stato aggiunto il supporto per semplificare la rimozione di dati di consapevolezza spaziale osservati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="53da9-388">Based on customer feedback, support for easy removal of previously observed spatial awareness data has been added.</span></span>

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

<span data-ttu-id="53da9-389">**Risolutori**</span><span class="sxs-lookup"><span data-stu-id="53da9-389">**Solvers**</span></span>

<span data-ttu-id="53da9-390">Alcuni componenti del Risolutore e la classe SolverHandler Manager sono stati modificati per correggere diversi bug e per un utilizzo più intuitivo.</span><span class="sxs-lookup"><span data-stu-id="53da9-390">Some solver components and the SolverHandler manager class has changed to fix various bugs and for more intuitive usage.</span></span>

<span data-ttu-id="53da9-391">**_SolverHandler_**</span><span class="sxs-lookup"><span data-stu-id="53da9-391">**_SolverHandler_**</span></span>

- <span data-ttu-id="53da9-392">La classe non si estende più da `ControllerFinder`</span><span class="sxs-lookup"><span data-stu-id="53da9-392">Class no longer extends from `ControllerFinder`</span></span>
- <span data-ttu-id="53da9-393">`TrackedObjectToReference` Proprietà pubblica deprecata ed è stata rinominata in `TrackedTargetType`</span><span class="sxs-lookup"><span data-stu-id="53da9-393">`TrackedObjectToReference` public property deprecated and has been renamed to `TrackedTargetType`</span></span>
- <span data-ttu-id="53da9-394">`TrackedObjectType` depreca i valori Left & right controller.</span><span class="sxs-lookup"><span data-stu-id="53da9-394">`TrackedObjectType` deprecates left & right controller values.</span></span> <span data-ttu-id="53da9-395">Usare invece `MotionController` `HandJoint` i valori o e aggiornare la nuova `TrackedHandedness` proprietà per limitare il rilevamento al controller sinistro o destro</span><span class="sxs-lookup"><span data-stu-id="53da9-395">Instead use `MotionController` or `HandJoint` values and update new `TrackedHandedness` property to limit tracking to left or right controller</span></span>

<span data-ttu-id="53da9-396">**_InBetween_**</span><span class="sxs-lookup"><span data-stu-id="53da9-396">**_InBetween_**</span></span>

- <span data-ttu-id="53da9-397">`TrackedObjectForSecondTransform` Proprietà pubblica deprecata ed è stata rinominata in `SecondTrackedObjectType`</span><span class="sxs-lookup"><span data-stu-id="53da9-397">`TrackedObjectForSecondTransform` public property deprecated and has been renamed to `SecondTrackedObjectType`</span></span>
- <span data-ttu-id="53da9-398">`AttachSecondTransformToNewTrackedObject()` è stato rimosso.</span><span class="sxs-lookup"><span data-stu-id="53da9-398">`AttachSecondTransformToNewTrackedObject()` has been removed.</span></span> <span data-ttu-id="53da9-399">Per aggiornare il Risolutore, modificare le proprietà pubbliche, ad esempio</span><span class="sxs-lookup"><span data-stu-id="53da9-399">To update the solver, modify the public properties (i.e</span></span> <span data-ttu-id="53da9-400">`SecondTrackedObjectType`)</span><span class="sxs-lookup"><span data-stu-id="53da9-400">`SecondTrackedObjectType`)</span></span>

<span data-ttu-id="53da9-401">**_SurfaceMagnetism_**</span><span class="sxs-lookup"><span data-stu-id="53da9-401">**_SurfaceMagnetism_**</span></span>

- <span data-ttu-id="53da9-402">`MaxDistance` Proprietà pubblica deprecata ed è stata rinominata in `MaxRaycastDistance`</span><span class="sxs-lookup"><span data-stu-id="53da9-402">`MaxDistance` public property deprecated and has been renamed to `MaxRaycastDistance`</span></span>
- <span data-ttu-id="53da9-403">`CloseDistance` Proprietà pubblica deprecata ed è stata rinominata in `ClosestDistance`</span><span class="sxs-lookup"><span data-stu-id="53da9-403">`CloseDistance` public property deprecated and has been renamed to `ClosestDistance`</span></span>
- <span data-ttu-id="53da9-404">Il valore predefinito per `RaycastDirectionMode` è ora `TrackedTargetForward` raycasts nella direzione della trasformazione di destinazione rilevata in avanti.</span><span class="sxs-lookup"><span data-stu-id="53da9-404">Default value for `RaycastDirectionMode` is now `TrackedTargetForward` which raycasts in the direction of the tracked target transform forward</span></span>
- <span data-ttu-id="53da9-405">`OrientationMode`i valori enum, `Vertical` e `Full` , sono stati rinominati `TrackedTarget` rispettivamente in e `SurfaceNormal`</span><span class="sxs-lookup"><span data-stu-id="53da9-405">`OrientationMode` enum values, `Vertical` and `Full`, have been renamed to `TrackedTarget` and `SurfaceNormal` respectively</span></span>
- <span data-ttu-id="53da9-406">`KeepOrientationVertical` è stata aggiunta la proprietà Public per controllare se l'orientamento del GameObject associato rimanga verticale</span><span class="sxs-lookup"><span data-stu-id="53da9-406">`KeepOrientationVertical` public property has been added to control whether orientation of associated GameObject remains vertical</span></span>

<span data-ttu-id="53da9-407">**Pulsanti**</span><span class="sxs-lookup"><span data-stu-id="53da9-407">**Buttons**</span></span>

- <span data-ttu-id="53da9-408">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton)`DistanceSpaceMode`la proprietà è ora impostata su `Local` come valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="53da9-408">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) now has `DistanceSpaceMode` property set to `Local` as default.</span></span> <span data-ttu-id="53da9-409">In questo modo è possibile ridimensionare i pulsanti mentre sono ancora stampabili</span><span class="sxs-lookup"><span data-stu-id="53da9-409">This allows buttons to be scaled while still be pressable</span></span>

<span data-ttu-id="53da9-410">**Sfera di ritaglio**</span><span class="sxs-lookup"><span data-stu-id="53da9-410">**Clipping Sphere**</span></span>

<span data-ttu-id="53da9-411">L'interfaccia ClippingSphere è cambiata per eseguire il mirroring delle API trovate in ClippingBox e ClippingPlane.</span><span class="sxs-lookup"><span data-stu-id="53da9-411">The ClippingSphere interface has changed to mirror the APIs found in the ClippingBox and ClippingPlane.</span></span>

<span data-ttu-id="53da9-412">La proprietà RADIUS di ClippingSphere viene ora calcolata in modo implicito in base alla scala di trasformazione.</span><span class="sxs-lookup"><span data-stu-id="53da9-412">The ClippingSphere's Radius property is now implicitly calculated based on the transform scale.</span></span> <span data-ttu-id="53da9-413">Prima che gli sviluppatori dovessero specificare il raggio di ClippingSphere nel controllo.</span><span class="sxs-lookup"><span data-stu-id="53da9-413">Before developers would have to specify the radius of the ClippingSphere in the inspector.</span></span> <span data-ttu-id="53da9-414">Se si vuole modificare il raggio, è sufficiente aggiornare la scala di trasformazione della trasformazione come si farebbe normalmente.</span><span class="sxs-lookup"><span data-stu-id="53da9-414">If you want to change the radius, just update the transform scale of the transform as you normally would.</span></span>

<span data-ttu-id="53da9-415">**NearInteractionTouchable e PokePointer**</span><span class="sxs-lookup"><span data-stu-id="53da9-415">**NearInteractionTouchable and PokePointer**</span></span>

- <span data-ttu-id="53da9-416">NearInteractionTouchable non gestisce più l'area di disegno dell'interfaccia utente di Unity.</span><span class="sxs-lookup"><span data-stu-id="53da9-416">NearInteractionTouchable does not handle Unity UI canvas touching any longer.</span></span> <span data-ttu-id="53da9-417">È necessario usare la classe NearInteractionTouchableUnityUI per l'interfaccia utente di Unity touchables Now.</span><span class="sxs-lookup"><span data-stu-id="53da9-417">The NearInteractionTouchableUnityUI class must be used for Unity UI touchables now.</span></span>
- <span data-ttu-id="53da9-418">ColliderNearInteractionTouchable è la nuova classe di base per touchables in base ai Collider, ovvero ogni oggetto toccabile, ad eccezione di NearInteractionTouchableUnityUI.</span><span class="sxs-lookup"><span data-stu-id="53da9-418">ColliderNearInteractionTouchable is the new base class for touchables based on colliders, i.e. every touchable except NearInteractionTouchableUnityUI.</span></span>
- <span data-ttu-id="53da9-419">BaseNearInteractionTouchable. DistFront è stato spostato e rinominato in PokePointer. TouchableDistance è la distanza e la PokePointer può interagire con touchables.</span><span class="sxs-lookup"><span data-stu-id="53da9-419">BaseNearInteractionTouchable.DistFront has been moved and renamed to PokePointer.TouchableDistance This is the distance and which the PokePointer can interact with touchables.</span></span> <span data-ttu-id="53da9-420">In precedenza ogni modificabile presentava una distanza di interazione massima, ma ora è definita in PokePointer, che consente una migliore ottimizzazione.</span><span class="sxs-lookup"><span data-stu-id="53da9-420">Previously each touchable had its own maximum interaction distance, but now this is defined in the PokePointer which allows better optimization.</span></span>
- <span data-ttu-id="53da9-421">BaseNearInteractionTouchable. DistBack è stato rinominato in PokeThreshold in modo da rendere chiaro che PokeThreshold è la controparte di DebounceThreshold.</span><span class="sxs-lookup"><span data-stu-id="53da9-421">BaseNearInteractionTouchable.DistBack has been renamed to PokeThreshold This makes it clear that PokeThreshold is the counterpart to DebounceThreshold.</span></span> <span data-ttu-id="53da9-422">Un oggetto toccabile viene attivato quando viene superato il valore di PokeThreshold e viene rilasciato quando DebounceThreshold viene attraversato.</span><span class="sxs-lookup"><span data-stu-id="53da9-422">A touchable is activated when the PokeThreshold is crossed, and released when DebounceThreshold is crossed.</span></span>

<span data-ttu-id="53da9-423">**ReadOnlyAttribute**</span><span class="sxs-lookup"><span data-stu-id="53da9-423">**ReadOnlyAttribute**</span></span>

<span data-ttu-id="53da9-424">Lo `Microsoft.MixedReality.Toolkit` spazio dei nomi è stato aggiunto a `ReadOnlyAttribute` , `BeginReadOnlyGroupAttribute` e `EndReadOnlyGroupAttribute` .</span><span class="sxs-lookup"><span data-stu-id="53da9-424">The `Microsoft.MixedReality.Toolkit` namespace has been added to `ReadOnlyAttribute`, `BeginReadOnlyGroupAttribute`, and `EndReadOnlyGroupAttribute`.</span></span>

<span data-ttu-id="53da9-425">**PointerClickHandler**</span><span class="sxs-lookup"><span data-stu-id="53da9-425">**PointerClickHandler**</span></span>

<span data-ttu-id="53da9-426">La classe `PointerClickHandler` è stata deprecata.</span><span class="sxs-lookup"><span data-stu-id="53da9-426">The `PointerClickHandler` class has been deprecated.</span></span> <span data-ttu-id="53da9-427">`PointerHandler`È invece necessario utilizzare l'oggetto, che fornisce la stessa funzionalità.</span><span class="sxs-lookup"><span data-stu-id="53da9-427">The `PointerHandler` should be used instead, it provides the same functionality.</span></span>

<span data-ttu-id="53da9-428">**Supporto di HoloLens Clicker**</span><span class="sxs-lookup"><span data-stu-id="53da9-428">**HoloLens clicker support**</span></span>

<span data-ttu-id="53da9-429">I mapping del controller del clicker HoloLens sono passati a un valore non gestito [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) .</span><span class="sxs-lookup"><span data-stu-id="53da9-429">The HoloLens clicker's controller mappings have changed from being an unhanded [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) to being an unhanded [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand).</span></span> <span data-ttu-id="53da9-430">Per tenere conto di questo problema, viene eseguito un aggiornamento automatico la prima volta che si apre il profilo ControllerMapping.</span><span class="sxs-lookup"><span data-stu-id="53da9-430">To account for this, an automatic updater will run the first time you open your ControllerMapping profile.</span></span> <span data-ttu-id="53da9-431">Aprire i profili personalizzati almeno una volta dopo l'aggiornamento a 2.0.0 per attivare questo passaggio di migrazione una volta.</span><span class="sxs-lookup"><span data-stu-id="53da9-431">Please open any custom profiles at least once after upgrading to 2.0.0 in order to trigger this one-time migration step.</span></span>

<span data-ttu-id="53da9-432">**InteractableHighlight**</span><span class="sxs-lookup"><span data-stu-id="53da9-432">**InteractableHighlight**</span></span>

<span data-ttu-id="53da9-433">La classe `InteractableHighlight` è stata deprecata.</span><span class="sxs-lookup"><span data-stu-id="53da9-433">The `InteractableHighlight` class has been deprecated.</span></span> <span data-ttu-id="53da9-434">In `InteractableOnFocus` alternativa, `FocusInteractableStates` è consigliabile usare la classe e l'asset.</span><span class="sxs-lookup"><span data-stu-id="53da9-434">The `InteractableOnFocus` class and `FocusInteractableStates` asset should be used instead.</span></span> <span data-ttu-id="53da9-435">Per creare un nuovo `Theme` asset per il `InteractableOnFocus` , fare clic con il pulsante destro del mouse nella finestra del progetto e scegliere *Crea*  >    >  *tema interagibile* del Toolkit di realtà mista  >  .</span><span class="sxs-lookup"><span data-stu-id="53da9-435">To create a new `Theme` asset for the `InteractableOnFocus`, right click in the project window and select *Create* > *Mixed Reality Toolkit* > *Interactable* > *Theme*.</span></span>

<span data-ttu-id="53da9-436">**HandInteractionPanZoom**</span><span class="sxs-lookup"><span data-stu-id="53da9-436">**HandInteractionPanZoom**</span></span>

<span data-ttu-id="53da9-437">`HandInteractionPanZoom` è stato spostato nello spazio dei nomi dell'interfaccia utente perché non era un componente di input.</span><span class="sxs-lookup"><span data-stu-id="53da9-437">`HandInteractionPanZoom` has been moved to the UI namespace as it was not an input component.</span></span> <span data-ttu-id="53da9-438">`HandPanEventData` è stato inoltre spostato in questo spazio dei nomi e semplificato per corrispondere ad altri dati degli eventi dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="53da9-438">`HandPanEventData` has also been moved into this namespace, and simplified to correspond with other UI event data.</span></span>

### <a name="assembly-name-changes-in-200"></a><span data-ttu-id="53da9-439">Modifiche al nome dell'assembly in 2.0.0</span><span class="sxs-lookup"><span data-stu-id="53da9-439">Assembly name changes in 2.0.0</span></span>

<span data-ttu-id="53da9-440">Nella versione 2.0.0, tutti i nomi di assembly ufficiali del Toolkit di realtà mista e i file di definizione di assembly (con estensione asmdef) associati sono stati aggiornati per adattarsi al modello seguente.</span><span class="sxs-lookup"><span data-stu-id="53da9-440">In The 2.0.0 release, all of the official Mixed Reality Toolkit assembly names and their associated assembly definition (.asmdef) files have been updated to fit the following pattern.</span></span>

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

<span data-ttu-id="53da9-441">In alcuni casi, sono Stati Uniti più assembly per creare una migliore Unity del rispettivo contenuto.</span><span class="sxs-lookup"><span data-stu-id="53da9-441">In some instances, multiple assemblies have been merged to create better unity of their contents.</span></span> <span data-ttu-id="53da9-442">Se il progetto usa file con estensione asmdef personalizzati, potrebbe essere necessario aggiornare.</span><span class="sxs-lookup"><span data-stu-id="53da9-442">If your project uses custom .asmdef files, they may require updating.</span></span>

<span data-ttu-id="53da9-443">Le tabelle seguenti descrivono il mapping dei nomi di file RC2. asmdef alla versione 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="53da9-443">The following tables describe how the RC2 .asmdef file names map to the 2.0.0 release.</span></span> <span data-ttu-id="53da9-444">Tutti i nomi di assembly corrispondono al nome del file. asmdef.</span><span class="sxs-lookup"><span data-stu-id="53da9-444">All assembly names match the .asmdef file name.</span></span>

<span data-ttu-id="53da9-445">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="53da9-445">**MixedRealityToolkit**</span></span>

| <span data-ttu-id="53da9-446">RC2</span><span class="sxs-lookup"><span data-stu-id="53da9-446">RC2</span></span> | <span data-ttu-id="53da9-447">2.0.0</span><span class="sxs-lookup"><span data-stu-id="53da9-447">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="53da9-448">MixedRealityToolkit.asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-448">MixedRealityToolkit.asmdef</span></span> | <span data-ttu-id="53da9-449">Microsoft. MixedReality. Toolkit. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-449">Microsoft.MixedReality.Toolkit.asmdef</span></span> |
| <span data-ttu-id="53da9-450">MixedRealityToolkit. Core. BuildAndDeploy. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-450">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span></span> | <span data-ttu-id="53da9-451">Microsoft. MixedReality. Toolkit. Editor. BuildAndDeploy. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-451">Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef</span></span> |
| <span data-ttu-id="53da9-452">MixedRealityToolkit. Core. Definitions. Utilities. Editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-452">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="53da9-453">Rimosso, usare Microsoft. MixedReality. Toolkit. Editor. Utilities. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-453">Removed, use Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="53da9-454">MixedRealityToolkit. Core. Extensions. EditorClassExtensions. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-454">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span></span> | <span data-ttu-id="53da9-455">Microsoft. MixedReality. Toolkit. Editor. ClassExtensions. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-455">Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef</span></span>
| <span data-ttu-id="53da9-456">MixedRealityToolkit. Core. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-456">MixedRealityToolkit.Core.Inspectors.asmdef</span></span> | <span data-ttu-id="53da9-457">Microsoft. MixedReality. Toolkit. Editor. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-457">Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef</span></span> |
| <span data-ttu-id="53da9-458">MixedRealityToolkit. Core. Inspectors. ServiceInspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-458">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span></span> | <span data-ttu-id="53da9-459">Microsoft. MixedReality. Toolkit. Editor. ServiceInspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-459">Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef</span></span> |
| <span data-ttu-id="53da9-460">MixedRealityToolkit. Core. UtilitiesAsync. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-460">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span></span> | <span data-ttu-id="53da9-461">Microsoft. MixedReality. Toolkit. Async. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-461">Microsoft.MixedReality.Toolkit.Async.asmdef</span></span> |
| <span data-ttu-id="53da9-462">MixedRealityToolkit. Core. Utilities. Editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-462">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="53da9-463">Microsoft. MixedReality. Toolkit. Editor. Utilities. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-463">Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="53da9-464">MixedRealityToolkit. Utilities. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-464">MixedRealityToolkit.Utilities.Gltf.asmdef</span></span> | <span data-ttu-id="53da9-465">Microsoft. MixedReality. Toolkit. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-465">Microsoft.MixedReality.Toolkit.Gltf.asmdef</span></span> |
| <span data-ttu-id="53da9-466">MixedRealityToolkit. Utilities. Gltf. Importers. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-466">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span></span> | <span data-ttu-id="53da9-467">Microsoft. MixedReality. Toolkit. Gltf. Importers. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-467">Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef</span></span> |

<span data-ttu-id="53da9-468">**MixedRealityToolkit. Providers**</span><span class="sxs-lookup"><span data-stu-id="53da9-468">**MixedRealityToolkit.Providers**</span></span>

| <span data-ttu-id="53da9-469">RC2</span><span class="sxs-lookup"><span data-stu-id="53da9-469">RC2</span></span> | <span data-ttu-id="53da9-470">2.0.0</span><span class="sxs-lookup"><span data-stu-id="53da9-470">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="53da9-471">MixedRealityToolkit. Providers. OpenVR. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-471">MixedRealityToolkit.Providers.OpenVR.asmdef</span></span> | <span data-ttu-id="53da9-472">Microsoft. MixedReality. Toolkit. Providers. OpenVR. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-472">Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef</span></span> |
| <span data-ttu-id="53da9-473">MixedRealityToolkit. Providers. WindowsMixedReality. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-473">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span></span> | <span data-ttu-id="53da9-474">Microsoft. MixedReality. Toolkit. Providers. WindowsMixedReality. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-474">Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef</span></span> |
| <span data-ttu-id="53da9-475">MixedRealityToolkit. Providers. WindowsVoiceInput. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-475">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span></span> | <span data-ttu-id="53da9-476">Microsoft. MixedReality. Toolkit. Providers. WindowsVoiceInput. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-476">Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef</span></span> |

<span data-ttu-id="53da9-477">**MixedRealityToolkit. Services**</span><span class="sxs-lookup"><span data-stu-id="53da9-477">**MixedRealityToolkit.Services**</span></span>

| <span data-ttu-id="53da9-478">RC2</span><span class="sxs-lookup"><span data-stu-id="53da9-478">RC2</span></span> | <span data-ttu-id="53da9-479">2.0.0</span><span class="sxs-lookup"><span data-stu-id="53da9-479">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="53da9-480">MixedRealityToolkit. Services. BoundarySystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-480">MixedRealityToolkit.Services.BoundarySystem.asmdef</span></span> | <span data-ttu-id="53da9-481">Microsoft. MixedReality. Toolkit. Services. BoundarySystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-481">Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef</span></span> |
| <span data-ttu-id="53da9-482">MixedRealityToolkit. Services. CameraSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-482">MixedRealityToolkit.Services.CameraSystem.asmdef</span></span> | <span data-ttu-id="53da9-483">Microsoft. MixedReality. Toolkit. Services. CameraSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-483">Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef</span></span> |
| <span data-ttu-id="53da9-484">MixedRealityToolkit. Services. DiagnosticsSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-484">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span></span> | <span data-ttu-id="53da9-485">Microsoft. MixedReality. Toolkit. Services. DiagnosticsSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-485">Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef</span></span> |
| <span data-ttu-id="53da9-486">MixedRealityToolkit. Services. InputSimulation. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-486">MixedRealityToolkit.Services.InputSimulation.asmdef</span></span> | <span data-ttu-id="53da9-487">Microsoft. MixedReality. Toolkit. Services. InputSimulation. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-487">Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef</span></span> |
| <span data-ttu-id="53da9-488">MixedRealityToolkit. Services. InputSimulation. Editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-488">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span></span> | <span data-ttu-id="53da9-489">Microsoft. MixedReality. Toolkit. Services. InputSimulation. Editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-489">Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef</span></span> |
| <span data-ttu-id="53da9-490">MixedRealityToolkit. Services. InputSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-490">MixedRealityToolkit.Services.InputSystem.asmdef</span></span> | <span data-ttu-id="53da9-491">Microsoft. MixedReality. Toolkit. Services. InputSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-491">Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef</span></span> |
| <span data-ttu-id="53da9-492">MixedRealityToolkit. Services. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-492">MixedRealityToolkit.Services.Inspectors.asmdef</span></span> | <span data-ttu-id="53da9-493">Microsoft. MixedReality. Toolkit. Services. InputSystem. Editor. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-493">Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef</span></span> |
| <span data-ttu-id="53da9-494">MixedRealityToolkit. Services. SceneSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-494">MixedRealityToolkit.Services.SceneSystem.asmdef</span></span> | <span data-ttu-id="53da9-495">Microsoft. MixedReality. Toolkit. Services. SceneSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-495">Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef</span></span> |
| <span data-ttu-id="53da9-496">MixedRealityToolkit. Services. SpatialAwarenessSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-496">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span></span> | <span data-ttu-id="53da9-497">Microsoft. MixedReality. Toolkit. Services. SpatialAwarenessSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-497">Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef</span></span> |
| <span data-ttu-id="53da9-498">MixedRealityToolkit. Services. TeleportSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-498">MixedRealityToolkit.Services.TeleportSystem.asmdef</span></span> | <span data-ttu-id="53da9-499">Microsoft. MixedReality. Toolkit. Services. TeleportSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-499">Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef</span></span> |

<span data-ttu-id="53da9-500">**MixedRealityToolkit. SDK**</span><span class="sxs-lookup"><span data-stu-id="53da9-500">**MixedRealityToolkit.SDK**</span></span>

| <span data-ttu-id="53da9-501">RC2</span><span class="sxs-lookup"><span data-stu-id="53da9-501">RC2</span></span> | <span data-ttu-id="53da9-502">2.0.0</span><span class="sxs-lookup"><span data-stu-id="53da9-502">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="53da9-503">MixedRealityToolkit. SDK. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-503">MixedRealityToolkit.SDK.asmdef</span></span> | <span data-ttu-id="53da9-504">Microsoft. MixedReality. Toolkit. SDK. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-504">Microsoft.MixedReality.Toolkit.SDK.asmdef</span></span> |
| <span data-ttu-id="53da9-505">MixedRealityToolkit. SDK. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-505">MixedRealityToolkit.SDK.Inspectors.asmdef</span></span> | <span data-ttu-id="53da9-506">Microsoft. MixedReality. Toolkit. SDK. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-506">Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef</span></span> |

<span data-ttu-id="53da9-507">**MixedRealityToolkit. examples**</span><span class="sxs-lookup"><span data-stu-id="53da9-507">**MixedRealityToolkit.Examples**</span></span>

| <span data-ttu-id="53da9-508">RC2</span><span class="sxs-lookup"><span data-stu-id="53da9-508">RC2</span></span> | <span data-ttu-id="53da9-509">2.0.0</span><span class="sxs-lookup"><span data-stu-id="53da9-509">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="53da9-510">MixedRealityToolkit. examples. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-510">MixedRealityToolkit.Examples.asmdef</span></span> | <span data-ttu-id="53da9-511">Microsoft. MixedReality. Toolkit. examples. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-511">Microsoft.MixedReality.Toolkit.Examples.asmdef</span></span> |
| <span data-ttu-id="53da9-512">MixedRealityToolkit. examples. Demos. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-512">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span></span> | <span data-ttu-id="53da9-513">Microsoft. MixedReality. Toolkit. Demos. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-513">Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef</span></span> |
| <span data-ttu-id="53da9-514">MixedRealityToolkit. examples. Demos. StandardShader. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-514">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span></span> | <span data-ttu-id="53da9-515">Microsoft. MixedReality. Toolkit. Demos. StandardShader. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-515">Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef</span></span> |
| <span data-ttu-id="53da9-516">MixedRealityToolkit. examples. Demos. Utilities. InspectorFields. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-516">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span></span> | <span data-ttu-id="53da9-517">Microsoft. MixedReality. Toolkit. Demos. InspectorFields. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-517">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef</span></span> |
| <span data-ttu-id="53da9-518">MixedRealityToolkit. examples. Demos. Utilities. InspectorFields. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-518">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span></span> | <span data-ttu-id="53da9-519">Microsoft. MixedReality. Toolkit. Demos. InspectorFields. Inspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-519">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef</span></span> |
| <span data-ttu-id="53da9-520">MixedRealityToolkit. examples. Demos. UX. Interactables. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-520">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span></span> | <span data-ttu-id="53da9-521">Microsoft. MixedReality. Toolkit. Demos. UX. Interactables. asmdef</span><span class="sxs-lookup"><span data-stu-id="53da9-521">Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef</span></span> |
