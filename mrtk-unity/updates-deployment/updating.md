---
title: Aggiornamento
description: Documentazione per eseguire la migrazione da una versione precedente di MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 97f45328bc8f9b811e815da0240138790db699c6
ms.sourcegitcommit: 0b09536c16f6802acc120a973d720aec7e30f617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2021
ms.locfileid: "107742237"
---
# <a name="updating-the-microsoft-mixed-reality-toolkit"></a><span data-ttu-id="fb52b-104">Aggiornamento di Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="fb52b-104">Updating the Microsoft Mixed Reality Toolkit</span></span>

- [<span data-ttu-id="fb52b-105">Aggiornamento a una nuova versione di MRTK</span><span class="sxs-lookup"><span data-stu-id="fb52b-105">Upgrading to a new version of MRTK</span></span>](#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="fb52b-106">Da 2.3.0 a 2.4.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-106">2.3.0 to 2.4.0</span></span>](#updating-230-to-240)
- [<span data-ttu-id="fb52b-107">Da 2.2.0 a 2.3.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-107">2.2.0 to 2.3.0</span></span>](#updating-220-to-230)
- [<span data-ttu-id="fb52b-108">Da 2.1.0 a 2.2.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-108">2.1.0 to 2.2.0</span></span>](#updating-210-to-220)
- [<span data-ttu-id="fb52b-109">Da 2.0.0 a 2.1.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-109">2.0.0 to 2.1.0</span></span>](#updating-200-to-210)
- [<span data-ttu-id="fb52b-110">Da RC2 a 2.0.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-110">RC2 to 2.0.0</span></span>](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a><span data-ttu-id="fb52b-111">Ricerca della versione corrente</span><span class="sxs-lookup"><span data-stu-id="fb52b-111">Finding the current version</span></span> 

<span data-ttu-id="fb52b-112">Seguire queste istruzioni per determinare la versione di MRTK attualmente in uso:</span><span class="sxs-lookup"><span data-stu-id="fb52b-112">Follow these instructions to figure out which version of the MRTK you're currently using:</span></span>

1. <span data-ttu-id="fb52b-113">Aprire il progetto MRTK in Unity</span><span class="sxs-lookup"><span data-stu-id="fb52b-113">Open your MRTK project in Unity</span></span>
2. <span data-ttu-id="fb52b-114">Passare alla cartella "MixedRealityToolkit" nella finestra del progetto</span><span class="sxs-lookup"><span data-stu-id="fb52b-114">Navigate to the "MixedRealityToolkit" folder in your Project window</span></span>
3. <span data-ttu-id="fb52b-115">Aprire il file denominato "Version"</span><span class="sxs-lookup"><span data-stu-id="fb52b-115">Open the file called "Version"</span></span>

<span data-ttu-id="fb52b-116">Se il file e la cartella precedenti non esistono, si è in una versione più recente di MRTK.</span><span class="sxs-lookup"><span data-stu-id="fb52b-116">If the file and folder above doesn't exist, you're on a newer version of the MRTK.</span></span> <span data-ttu-id="fb52b-117">In tal caso, provare a eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="fb52b-117">In that case, try the following:</span></span>

1. <span data-ttu-id="fb52b-118">Passare alla cartella "Mixed Reality Toolkit Foundation"</span><span class="sxs-lookup"><span data-stu-id="fb52b-118">Navigate to the "Mixed Reality Toolkit Foundation" folder</span></span>
2. <span data-ttu-id="fb52b-119">Fare clic sul pulsante "package.js" per visualizzare un'anteprima in Unity o aprirlo con un editor di testo</span><span class="sxs-lookup"><span data-stu-id="fb52b-119">Click on the "package.json" to see a preview in Unity or open it with a text editor</span></span>
3. <span data-ttu-id="fb52b-120">Cercare la riga con la parola "version:"</span><span class="sxs-lookup"><span data-stu-id="fb52b-120">Look for the line with the word "version:"</span></span> 

## <a name="upgrading-to-a-new-version-of-mrtk"></a><span data-ttu-id="fb52b-121">Aggiornamento a una nuova versione di MRTK</span><span class="sxs-lookup"><span data-stu-id="fb52b-121">Upgrading to a new version of MRTK</span></span>

<span data-ttu-id="fb52b-122">*È consigliabile eseguire [](../features/tools/migration-window.md) lo* strumento di migrazione dopo aver eseguito l'aggiornamento MRTK per la correzione automatica e l'aggiornamento da componenti deprecati e dopo aver apportato modifiche di rilievo.</span><span class="sxs-lookup"><span data-stu-id="fb52b-122">*It is strongly recommended to run the [migration tool](../features/tools/migration-window.md) after getting the MRTK update* to auto-fix and upgrade from deprecated components and adjust to breaking changes.</span></span> <span data-ttu-id="fb52b-123">Lo strumento di migrazione fa parte del **pacchetto** Tools.</span><span class="sxs-lookup"><span data-stu-id="fb52b-123">The migration tool is part of the **Tools** package.</span></span>

<span data-ttu-id="fb52b-124">Le istruzioni seguenti descrivono il percorso di aggiornamento da 2.4.0 a 2.5.0.</span><span class="sxs-lookup"><span data-stu-id="fb52b-124">The instructions below describe the 2.4.0 to 2.5.0 upgrade path.</span></span> <span data-ttu-id="fb52b-125">Se il progetto è nella versione 2.3.0 [](#updating-230-to-240) o precedente, leggere le modifiche tra [](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) le versioni per comprendere il percorso di aggiornamento o leggere le istruzioni della versione precedente per eseguire un aggiornamento versione per versione.</span><span class="sxs-lookup"><span data-stu-id="fb52b-125">If your project is on 2.3.0 or earlier, read on to the changes [between versions](#updating-230-to-240) to understand the upgrade path, or read the previous [release's instructions](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) to do a version-by-version upgrade.</span></span>

### <a name="mixed-reality-feature-tool"></a><span data-ttu-id="fb52b-126">Strumento per la funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="fb52b-126">Mixed Reality Feature Tool</span></span>
<span data-ttu-id="fb52b-127">Il modo più semplice per aggiornare MRTK a una versione più recente di MRTK è usare [mixed reality feature tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) per scaricare i pacchetti più recenti e caricarli direttamente nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="fb52b-127">The easiest way to upgrade MRTK to a newer version MRTK is by using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) to download the latest packages and load them directly to your Unity project.</span></span>

<span data-ttu-id="fb52b-128">Se il progetto usava in precedenza file di asset Unity (con estensione unitypackage), vedere [queste istruzioni.](#switching-from-unity-asset-files-to-mixed-reality-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="fb52b-128">If the project previously used Unity asset (.unitypackage) files, please see [these instructions](#switching-from-unity-asset-files-to-mixed-reality-feature-tool).</span></span> 

### <a name="unity-asset-unitypackage-files"></a><span data-ttu-id="fb52b-129">File di asset Unity (con estensione unitypackage)</span><span class="sxs-lookup"><span data-stu-id="fb52b-129">Unity asset (.unitypackage) files</span></span>

<span data-ttu-id="fb52b-130">Un altro percorso di aggiornamento è scaricare manualmente i pacchetti DIRTK Unity e applicarli al progetto.</span><span class="sxs-lookup"><span data-stu-id="fb52b-130">Another upgrade path is to manually download MRTK Unity packages and apply them to your project.</span></span> <span data-ttu-id="fb52b-131">Vedere la procedura seguente,</span><span class="sxs-lookup"><span data-stu-id="fb52b-131">See the steps below,</span></span>

1. <span data-ttu-id="fb52b-132">Salvare una copia del progetto corrente, nel caso in cui si sbatta in qualsiasi punto della procedura di aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="fb52b-132">Save a copy of your current project, in case you hit any snags at any point in the upgrade steps.</span></span>
1. <span data-ttu-id="fb52b-133">Chiudere Unity</span><span class="sxs-lookup"><span data-stu-id="fb52b-133">Close Unity</span></span>
1. <span data-ttu-id="fb52b-134">*All'interno della cartella Assets* eliminare le cartelle **MRTK** seguenti, insieme ai relativi file con estensione meta (il progetto potrebbe non avere tutte le cartelle elencate)</span><span class="sxs-lookup"><span data-stu-id="fb52b-134">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="fb52b-135">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="fb52b-135">MRTK/Core</span></span>
    - <span data-ttu-id="fb52b-136">MRTK/Esempi</span><span class="sxs-lookup"><span data-stu-id="fb52b-136">MRTK/Examples</span></span>
    - <span data-ttu-id="fb52b-137">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="fb52b-137">MRTK/Extensions</span></span>
    - <span data-ttu-id="fb52b-138">MRTK/Providers</span><span class="sxs-lookup"><span data-stu-id="fb52b-138">MRTK/Providers</span></span>
    - <span data-ttu-id="fb52b-139">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="fb52b-139">MRTK/SDK</span></span>
    - <span data-ttu-id="fb52b-140">MRTK/Services</span><span class="sxs-lookup"><span data-stu-id="fb52b-140">MRTK/Services</span></span>
    - <span data-ttu-id="fb52b-141">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="fb52b-141">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="fb52b-142">Se sono state apportate modifiche agli shader MRTK, creare un backup locale prima di eliminare la cartella MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="fb52b-142">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="fb52b-143">MRTK/Strumenti</span><span class="sxs-lookup"><span data-stu-id="fb52b-143">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="fb52b-144">NON eliminare la **cartella MixedRealityToolkit.Generated** o il relativo file con estensione meta.</span><span class="sxs-lookup"><span data-stu-id="fb52b-144">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="fb52b-145">Eliminare la **cartella** Library</span><span class="sxs-lookup"><span data-stu-id="fb52b-145">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="fb52b-146">Alcuni strumenti unity, ad esempio Unity Collab, salvano le informazioni di configurazione nella cartella Library.</span><span class="sxs-lookup"><span data-stu-id="fb52b-146">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="fb52b-147">Se si usa uno strumento che esegue questa operazione, copiare prima di eliminare la cartella dati dello strumento dalla libreria, quindi ripristinarla dopo la rigenerazione della libreria.</span><span class="sxs-lookup"><span data-stu-id="fb52b-147">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="fb52b-148">Aprire nuovamente il progetto in Unity</span><span class="sxs-lookup"><span data-stu-id="fb52b-148">Re-open the project in Unity</span></span>
1. <span data-ttu-id="fb52b-149">Importare i nuovi pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="fb52b-149">Import the new unity packages</span></span>
    - <span data-ttu-id="fb52b-150">Foundation- _Importare prima questo pacchetto_</span><span class="sxs-lookup"><span data-stu-id="fb52b-150">Foundation - _Import this package first_</span></span>
    - <span data-ttu-id="fb52b-151">Strumenti</span><span class="sxs-lookup"><span data-stu-id="fb52b-151">Tools</span></span>
    - <span data-ttu-id="fb52b-152">(Facoltativo) Estensioni</span><span class="sxs-lookup"><span data-stu-id="fb52b-152">(Optional) Extensions</span></span>
    > [!NOTE]
    > <span data-ttu-id="fb52b-153">Se sono state installate estensioni aggiuntive, potrebbe essere necessario importare nuovamente tali estensioni.</span><span class="sxs-lookup"><span data-stu-id="fb52b-153">If additional extensions had been installed, they may need to be re-imported.</span></span>
    - <span data-ttu-id="fb52b-154">(Facoltativo) Esempi</span><span class="sxs-lookup"><span data-stu-id="fb52b-154">(Optional) Examples</span></span>
1. <span data-ttu-id="fb52b-155">Chiudere Unity ed eliminare la **cartella Library** (leggere prima la nota seguente).</span><span class="sxs-lookup"><span data-stu-id="fb52b-155">Close Unity and delete the **Library** folder (read the note below first!).</span></span> <span data-ttu-id="fb52b-156">Questo passaggio è necessario per forzare Unity ad aggiornare il database degli asset e riconciliare i profili personalizzati esistenti.</span><span class="sxs-lookup"><span data-stu-id="fb52b-156">This step is necessary to force Unity to refresh its asset database and reconcile existing custom profiles.</span></span>
1. <span data-ttu-id="fb52b-157">Avviare Unity e per ogni scena nel progetto</span><span class="sxs-lookup"><span data-stu-id="fb52b-157">Launch Unity, and for each scene in the project</span></span>
    - <span data-ttu-id="fb52b-158">Eliminare **MixedRealityToolkit** e **MixedRealityPlayspace,** se presenti, dalla gerarchia.</span><span class="sxs-lookup"><span data-stu-id="fb52b-158">Delete **MixedRealityToolkit** and **MixedRealityPlayspace**, if present, from the hierarchy.</span></span> <span data-ttu-id="fb52b-159">Questa operazione eliminerà la fotocamera principale, ma verrà ri-creata nel passaggio successivo.</span><span class="sxs-lookup"><span data-stu-id="fb52b-159">This will delete the main camera, but it will be re-created in the next step.</span></span> <span data-ttu-id="fb52b-160">Se le proprietà della fotocamera principale sono state modificate manualmente, sarà necessario applicarne di nuovo manualmente una volta creata la nuova fotocamera.</span><span class="sxs-lookup"><span data-stu-id="fb52b-160">If any properties of the main camera have been manually changed, these will have to be re-applied manually once the new camera is created.</span></span>
    - <span data-ttu-id="fb52b-161">Selezionare **MixedRealityToolkit -> Aggiungi alla scena e configura**</span><span class="sxs-lookup"><span data-stu-id="fb52b-161">Select **MixedRealityToolkit -> Add to Scene and Configure**</span></span>
    - <span data-ttu-id="fb52b-162">Selezionare **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (Profili di mapping del controller di >- Questa operazione deve essere eseguita una sola volta) - In questo modo tutti i profili di mapping dei controller personalizzati verranno aggiornati con gli assi e i dati aggiornati, lasciando intatte le azioni di input assegnate dall'utente</span><span class="sxs-lookup"><span data-stu-id="fb52b-162">Select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (only needs to be done once)       - This will update any custom controller mapping profiles with updated axes and data, while leaving your custom-assigned input actions intact</span></span>
1. <span data-ttu-id="fb52b-163">Eseguire lo [strumento di migrazione](../features/tools/migration-window.md) ed eseguire lo strumento nel progetto *completo* per assicurarsi che tutto il codice sia aggiornato alla versione più recente.</span><span class="sxs-lookup"><span data-stu-id="fb52b-163">Run the [migration tool](../features/tools/migration-window.md) and run the tool on the *Full Project* to ensure that all of your code is updated to the latest.</span></span>
   <span data-ttu-id="fb52b-164">La finestra di migrazione contiene diversi gestori di migrazione, ognuno dei quali deve essere eseguito per conto proprio.</span><span class="sxs-lookup"><span data-stu-id="fb52b-164">The migration window contains a number of different migration handlers, which must each be run on their own.</span></span> <span data-ttu-id="fb52b-165">Questo passaggio comporta:</span><span class="sxs-lookup"><span data-stu-id="fb52b-165">This step involves:</span></span>
   - <span data-ttu-id="fb52b-166">Selezionare il primo gestore di migrazione dall'elenco **a discesa Selezione gestore** migrazione.</span><span class="sxs-lookup"><span data-stu-id="fb52b-166">Select the first migration handler from the **Migration Handler Selection** dropdown.</span></span>
   - <span data-ttu-id="fb52b-167">Fare clic sul pulsante "Progetto completo".</span><span class="sxs-lookup"><span data-stu-id="fb52b-167">Click the "Full Project" button.</span></span>
   - <span data-ttu-id="fb52b-168">Fare clic sul pulsante "Aggiungi progetto completo per la migrazione" per analizzare l'intero progetto per trovare gli oggetti di cui eseguire la migrazione.</span><span class="sxs-lookup"><span data-stu-id="fb52b-168">Click the "Add full project for migration" button (this will scan the entire project for objects to migrate).</span></span>
   - <span data-ttu-id="fb52b-169">Fare clic sul pulsante "Migrate" (Esegui migrazione) che deve essere abilitato se sono stati trovati oggetti di cui è possibile eseguire la migrazione.</span><span class="sxs-lookup"><span data-stu-id="fb52b-169">Click the "Migrate" button which should be enabled if any migrateable objects were found.</span></span>
   - <span data-ttu-id="fb52b-170">Ripetere i tre passaggi precedenti per ognuno dei gestori di migrazione nell'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="fb52b-170">Repeat the previous three steps for each of the migration handlers within the dropdown.</span></span>
     <span data-ttu-id="fb52b-171">Vedere questo [problema che](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) illustra le operazioni che è possibile eseguire per semplificare questo processo di migrazione in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="fb52b-171">(See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) which covers work that can be done to simplify this migration process in a future release)</span></span>

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a><span data-ttu-id="fb52b-172">Passaggio dai file di asset di Unity a Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="fb52b-172">Switching from Unity asset files to Mixed Reality Feature Tool</span></span>

<span data-ttu-id="fb52b-173">Il passaggio dai file di asset unity ai pacchetti dello strumento di funzionalità di realtà mista offre una serie di vantaggi:</span><span class="sxs-lookup"><span data-stu-id="fb52b-173">Switching from Unity asset files to Mixed Reality Feature Tool packages brings a number of benefits:</span></span>

- <span data-ttu-id="fb52b-174">Aggiornamento più semplice</span><span class="sxs-lookup"><span data-stu-id="fb52b-174">Easier updating</span></span>
- <span data-ttu-id="fb52b-175">Tempi di compilazione più rapidi</span><span class="sxs-lookup"><span data-stu-id="fb52b-175">Faster compile times</span></span>
- <span data-ttu-id="fb52b-176">Meno progetti nella soluzione Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fb52b-176">Fewer projects in the Visual Studio solution</span></span>

<span data-ttu-id="fb52b-177">Il passaggio all'uso di Mixed Reality Feature Tool richiede un set di passaggi manuali una sola volta.</span><span class="sxs-lookup"><span data-stu-id="fb52b-177">Changing to using the Mixed Reality Feature Tool requires a one-time set of manual steps.</span></span>

1. <span data-ttu-id="fb52b-178">Salvare una copia del progetto corrente.</span><span class="sxs-lookup"><span data-stu-id="fb52b-178">Save a copy of your current project.</span></span>
1. <span data-ttu-id="fb52b-179">Chiudere Unity</span><span class="sxs-lookup"><span data-stu-id="fb52b-179">Close Unity</span></span>
1. <span data-ttu-id="fb52b-180">*All'interno della cartella Assets* eliminare le cartelle **MRTK** seguenti, insieme ai relativi file con estensione meta (il progetto potrebbe non avere tutte le cartelle elencate)</span><span class="sxs-lookup"><span data-stu-id="fb52b-180">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="fb52b-181">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="fb52b-181">MRTK/Core</span></span>
    - <span data-ttu-id="fb52b-182">MRTK/Esempi</span><span class="sxs-lookup"><span data-stu-id="fb52b-182">MRTK/Examples</span></span>
    - <span data-ttu-id="fb52b-183">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="fb52b-183">MRTK/Extensions</span></span>
    - <span data-ttu-id="fb52b-184">MRTK/Providers</span><span class="sxs-lookup"><span data-stu-id="fb52b-184">MRTK/Providers</span></span>
    - <span data-ttu-id="fb52b-185">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="fb52b-185">MRTK/SDK</span></span>
    - <span data-ttu-id="fb52b-186">MRTK/Services</span><span class="sxs-lookup"><span data-stu-id="fb52b-186">MRTK/Services</span></span>
    - <span data-ttu-id="fb52b-187">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="fb52b-187">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="fb52b-188">Se sono state apportate modifiche agli shader MRTK, creare un backup locale prima di eliminare la cartella MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="fb52b-188">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="fb52b-189">MRTK/Strumenti</span><span class="sxs-lookup"><span data-stu-id="fb52b-189">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="fb52b-190">NON eliminare la **cartella MixedRealityToolkit.Generated** o il relativo file con estensione meta.</span><span class="sxs-lookup"><span data-stu-id="fb52b-190">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="fb52b-191">Eliminare la **cartella** Library</span><span class="sxs-lookup"><span data-stu-id="fb52b-191">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="fb52b-192">Alcuni strumenti unity, ad esempio Unity Collab, salvano le informazioni di configurazione nella cartella Library.</span><span class="sxs-lookup"><span data-stu-id="fb52b-192">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="fb52b-193">Se si usa uno strumento che esegue questa operazione, copiare prima di eliminare la cartella dei dati dello strumento dalla libreria, quindi ripristinarla dopo la rigenerazione della libreria.</span><span class="sxs-lookup"><span data-stu-id="fb52b-193">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="fb52b-194">Aprire nuovamente il progetto in Unity</span><span class="sxs-lookup"><span data-stu-id="fb52b-194">Re-open the project in Unity</span></span>

<span data-ttu-id="fb52b-195">Dopo aver eseguito i passaggi precedenti, esegui [Mixed Reality Feature Tool](#mixed-reality-feature-tool) e importa la versione desiderata di Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="fb52b-195">Once the previous steps have been performed, run the [Mixed Reality Feature Tool](#mixed-reality-feature-tool) and import the desired version of the Mixed Reality Toolkit.</span></span>

## <a name="updating-230-to-240"></a><span data-ttu-id="fb52b-196">Aggiornamento dalla versione 2.3.0 alla versione 2.4.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-196">Updating 2.3.0 to 2.4.0</span></span>

<span data-ttu-id="fb52b-197">[Ridenominazione delle cartelle](#folder-renames-in-240) 
 [Modifiche all'API](#api-changes-in-240)</span><span class="sxs-lookup"><span data-stu-id="fb52b-197">[Folder renames](#folder-renames-in-240)
[API changes](#api-changes-in-240)</span></span>

### <a name="folder-renames-in-240"></a><span data-ttu-id="fb52b-198">Ridenominazione delle cartelle nella versione 2.4.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-198">Folder renames in 2.4.0</span></span>

<span data-ttu-id="fb52b-199">Le cartelle MixedRealityToolkit sono state rinominate e spostate in una gerarchia comune nella versione 2.4.</span><span class="sxs-lookup"><span data-stu-id="fb52b-199">The MixedRealityToolkit folders have been renamed and moved into a common hierarchy in version 2.4.</span></span> <span data-ttu-id="fb52b-200">Se un'applicazione usa percorsi hard coded per le risorse MRTK, dovrà essere aggiornata in base alla tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="fb52b-200">If an application uses hard coded paths to MRTK resources, they will need to be updated per the following table.</span></span>

| <span data-ttu-id="fb52b-201">Cartella precedente</span><span class="sxs-lookup"><span data-stu-id="fb52b-201">Previous Folder</span></span> | <span data-ttu-id="fb52b-202">Nuova cartella</span><span class="sxs-lookup"><span data-stu-id="fb52b-202">New Folder</span></span> |
| --- | --- |
| <span data-ttu-id="fb52b-203">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="fb52b-203">MixedRealityToolkit</span></span> | <span data-ttu-id="fb52b-204">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="fb52b-204">MRTK/Core</span></span> |
| <span data-ttu-id="fb52b-205">MixedRealityToolkit.Examples</span><span class="sxs-lookup"><span data-stu-id="fb52b-205">MixedRealityToolkit.Examples</span></span> | <span data-ttu-id="fb52b-206">MRTK/Esempi</span><span class="sxs-lookup"><span data-stu-id="fb52b-206">MRTK/Examples</span></span> |
| <span data-ttu-id="fb52b-207">MixedRealityToolkit.Extensions</span><span class="sxs-lookup"><span data-stu-id="fb52b-207">MixedRealityToolkit.Extensions</span></span> | <span data-ttu-id="fb52b-208">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="fb52b-208">MRTK/Extensions</span></span> |
| <span data-ttu-id="fb52b-209">MixedRealityToolkit.Providers</span><span class="sxs-lookup"><span data-stu-id="fb52b-209">MixedRealityToolkit.Providers</span></span> | <span data-ttu-id="fb52b-210">MRTK/Providers</span><span class="sxs-lookup"><span data-stu-id="fb52b-210">MRTK/Providers</span></span> |
| <span data-ttu-id="fb52b-211">MixedRealityToolkit.SDK</span><span class="sxs-lookup"><span data-stu-id="fb52b-211">MixedRealityToolkit.SDK</span></span> | <span data-ttu-id="fb52b-212">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="fb52b-212">MRTK/SDK</span></span> |
| <span data-ttu-id="fb52b-213">MixedRealityToolkit.Services</span><span class="sxs-lookup"><span data-stu-id="fb52b-213">MixedRealityToolkit.Services</span></span> | <span data-ttu-id="fb52b-214">MRTK/Services</span><span class="sxs-lookup"><span data-stu-id="fb52b-214">MRTK/Services</span></span> |
| <span data-ttu-id="fb52b-215">MixedRealityToolkit.Tests</span><span class="sxs-lookup"><span data-stu-id="fb52b-215">MixedRealityToolkit.Tests</span></span> | <span data-ttu-id="fb52b-216">MRTK/Tests</span><span class="sxs-lookup"><span data-stu-id="fb52b-216">MRTK/Tests</span></span> |
| <span data-ttu-id="fb52b-217">MixedRealityToolkit.Tools</span><span class="sxs-lookup"><span data-stu-id="fb52b-217">MixedRealityToolkit.Tools</span></span> | <span data-ttu-id="fb52b-218">MRTK/Tools</span><span class="sxs-lookup"><span data-stu-id="fb52b-218">MRTK/Tools</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="fb52b-219">Contiene `MixedRealityToolkit.Generated` i file generati dal cliente e rimane invariato.</span><span class="sxs-lookup"><span data-stu-id="fb52b-219">The `MixedRealityToolkit.Generated` contains customer generated files and remains unchanged.</span></span>

### <a name="eye-gaze-setup-in-240"></a><span data-ttu-id="fb52b-220">Configurazione dello sguardo fisso nella versione 2.4.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-220">Eye gaze setup in 2.4.0</span></span>

<span data-ttu-id="fb52b-221">Questa versione di MRTK modifica i passaggi necessari per la configurazione dello sguardo fisso.</span><span class="sxs-lookup"><span data-stu-id="fb52b-221">This version of MRTK modifies the steps required for eye gaze setup.</span></span> <span data-ttu-id="fb52b-222">La _casella di controllo "IsEyeTrackingEnabled"_ è disponibile nelle impostazioni dello sguardo del profilo puntatore di input.</span><span class="sxs-lookup"><span data-stu-id="fb52b-222">The _'IsEyeTrackingEnabled'_ checkbox can be found in the gaze settings of the input pointer profile.</span></span> <span data-ttu-id="fb52b-223">Se si seleziona questa casella, lo sguardo basato sull'occhio verrà abilitato, anziché lo sguardo predefinito basato sulla testa.</span><span class="sxs-lookup"><span data-stu-id="fb52b-223">Checking this box will enable eye based gaze, rather then the default head based gaze.</span></span>

<span data-ttu-id="fb52b-224">Per altre informazioni su queste modifiche e istruzioni complete per la configurazione del tracciamento oculare, vedere l'articolo [sul tracciamento](../features/input/eye-tracking/eye-tracking-basic-setup.md) oculare.</span><span class="sxs-lookup"><span data-stu-id="fb52b-224">For more information on these changes and complete instructions for eye tracking setup, please see the [eye tracking](../features/input/eye-tracking/eye-tracking-basic-setup.md) article.</span></span>

### <a name="eye-gaze-pointer-behavior-in-240"></a><span data-ttu-id="fb52b-225">Comportamento del puntatore dello sguardo fisso nella versione 2.4.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-225">Eye gaze pointer behavior in 2.4.0</span></span>

<span data-ttu-id="fb52b-226">Il comportamento del puntatore predefinito dello sguardo fisso è stato modificato in modo che corrisponda al comportamento predefinito del puntatore dello sguardo con la testa.</span><span class="sxs-lookup"><span data-stu-id="fb52b-226">The eye gaze default pointer behavior have been modified to match the head gaze default pointer behavior.</span></span> <span data-ttu-id="fb52b-227">Un puntatore dello sguardo fisso verrà automaticamente eliminato quando viene rilevata una mano.</span><span class="sxs-lookup"><span data-stu-id="fb52b-227">An eye gaze pointer will automatically be suppressed once a hand is detected.</span></span> <span data-ttu-id="fb52b-228">Il puntatore dello sguardo fisso diventerà nuovamente visibile dopo aver detto "Seleziona".</span><span class="sxs-lookup"><span data-stu-id="fb52b-228">The eye gaze pointer will become visible again after saying "Select".</span></span>

<span data-ttu-id="fb52b-229">Informazioni dettagliate sulle configurazioni di sguardo fisso e mano sono disponibili [nell'articolo occhi e](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) mani.</span><span class="sxs-lookup"><span data-stu-id="fb52b-229">Details about gaze and hand setups can be found in the [eyes and hands](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) article.</span></span>

### <a name="api-changes-in-240"></a><span data-ttu-id="fb52b-230">Modifiche all'API nella versione 2.4.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-230">API changes in 2.4.0</span></span>

<span data-ttu-id="fb52b-231">**Classi controller personalizzate**</span><span class="sxs-lookup"><span data-stu-id="fb52b-231">**Custom controller classes**</span></span>

<span data-ttu-id="fb52b-232">Le classi controller personalizzate in precedenza dovevano definire `SetupDefaultInteractions(Handedness)` .</span><span class="sxs-lookup"><span data-stu-id="fb52b-232">Custom controller classes previously had to define `SetupDefaultInteractions(Handedness)`.</span></span> <span data-ttu-id="fb52b-233">Questo metodo è stato reso obsoleto nella versione 2.4, perché il parametro handedness era ridondante con il proprio mani della classe controller.</span><span class="sxs-lookup"><span data-stu-id="fb52b-233">This method has been made obsolete in 2.4, as the handedness parameter was redundant with the controller class' own handedness.</span></span> <span data-ttu-id="fb52b-234">Il nuovo metodo non ha parametri.</span><span class="sxs-lookup"><span data-stu-id="fb52b-234">The new method has no parameters.</span></span> <span data-ttu-id="fb52b-235">Inoltre, molte classi controller hanno definito questa operazione nello stesso modo ( ), quindi la chiamata completa è stata sottoposta a refactoring in ed è stato eseguito un override facoltativo `AssignControllerMappings(DefaultInteractions);` `BaseController` anziché obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="fb52b-235">Additionally, many controller classes defined this the same way (`AssignControllerMappings(DefaultInteractions);`), so the full call has been refactored down into `BaseController` and made an optional override instead of required.</span></span>

<span data-ttu-id="fb52b-236">**Proprietà dello sguardo fisso**</span><span class="sxs-lookup"><span data-stu-id="fb52b-236">**Eye Gaze properties**</span></span>

<span data-ttu-id="fb52b-237">La `UseEyeTracking` proprietà `GazeProvider` dall'implementazione `IMixedRealityEyeGazeProvider` di è stata rinominata in `IsEyeTrackingEnabled` .</span><span class="sxs-lookup"><span data-stu-id="fb52b-237">The `UseEyeTracking` property from `GazeProvider` implementation of `IMixedRealityEyeGazeProvider` was renamed to `IsEyeTrackingEnabled`.</span></span>

<span data-ttu-id="fb52b-238">Se è stato fatto in precedenza...</span><span class="sxs-lookup"><span data-stu-id="fb52b-238">If you did this previously...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

<span data-ttu-id="fb52b-239">Eseguire questa operazione ora...</span><span class="sxs-lookup"><span data-stu-id="fb52b-239">Do this now...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

<span data-ttu-id="fb52b-240">**Proprietà di WindowsApiChecker**</span><span class="sxs-lookup"><span data-stu-id="fb52b-240">**WindowsApiChecker properties**</span></span>

<span data-ttu-id="fb52b-241">Le proprietà WindowsApiChecker seguenti sono state contrassegnate come obsolete.</span><span class="sxs-lookup"><span data-stu-id="fb52b-241">The following WindowsApiChecker properties have been marked as obsolete.</span></span> <span data-ttu-id="fb52b-242">Usare `IsMethodAvailable` o `IsPropertyAvailable` `IsTypeAvailable` .</span><span class="sxs-lookup"><span data-stu-id="fb52b-242">Please use `IsMethodAvailable`, `IsPropertyAvailable` or `IsTypeAvailable`.</span></span>

- <span data-ttu-id="fb52b-243">UniversalApiContractV8_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="fb52b-243">UniversalApiContractV8_IsAvailable</span></span>
- <span data-ttu-id="fb52b-244">UniversalApiContractV7_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="fb52b-244">UniversalApiContractV7_IsAvailable</span></span>
- <span data-ttu-id="fb52b-245">UniversalApiContractV6_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="fb52b-245">UniversalApiContractV6_IsAvailable</span></span>
- <span data-ttu-id="fb52b-246">UniversalApiContractV5_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="fb52b-246">UniversalApiContractV5_IsAvailable</span></span>
- <span data-ttu-id="fb52b-247">UniversalApiContractV4_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="fb52b-247">UniversalApiContractV4_IsAvailable</span></span>
- <span data-ttu-id="fb52b-248">UniversalApiContractV3_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="fb52b-248">UniversalApiContractV3_IsAvailable</span></span>

<span data-ttu-id="fb52b-249">Non sono in programma di aggiungere proprietà a WindowsApiChecker per le versioni future del contratto API.</span><span class="sxs-lookup"><span data-stu-id="fb52b-249">There are no plans to add properties to WindowsApiChecker for future API contract versions.</span></span>

<span data-ttu-id="fb52b-250">**GltfMeshPrimitiveAttributes di sola lettura**</span><span class="sxs-lookup"><span data-stu-id="fb52b-250">**GltfMeshPrimitiveAttributes read-only**</span></span>

<span data-ttu-id="fb52b-251">Gli attributi primitivi della mesh gltf usati per essere impostati sono ora di sola lettura.</span><span class="sxs-lookup"><span data-stu-id="fb52b-251">The gltf mesh primitive attributes used to be settable, they are now read-only.</span></span> <span data-ttu-id="fb52b-252">I relativi valori verranno impostati una sola volta durante la deserializzazione.</span><span class="sxs-lookup"><span data-stu-id="fb52b-252">Their values will be set once when deserialized.</span></span>

### <a name="custom-button-icon-migration"></a><span data-ttu-id="fb52b-253">Migrazione dell'icona del pulsante personalizzato</span><span class="sxs-lookup"><span data-stu-id="fb52b-253">Custom Button Icon Migration</span></span>

<span data-ttu-id="fb52b-254">Le icone dei pulsanti personalizzate in precedenza richiedeva l'assegnazione di un nuovo materiale al renderer quad del pulsante.</span><span class="sxs-lookup"><span data-stu-id="fb52b-254">Previously custom button icons required assigning a new material to the button's quad renderer.</span></span> <span data-ttu-id="fb52b-255">Questa operazione non è più necessaria ed è consigliabile spostare trame di icone personalizzate in un oggetto IconSet.</span><span class="sxs-lookup"><span data-stu-id="fb52b-255">This is no longer necessary and we recommend moving custom icon textures into an IconSet.</span></span> <span data-ttu-id="fb52b-256">Le icone e i materiali personalizzati esistenti vengono mantenuti.</span><span class="sxs-lookup"><span data-stu-id="fb52b-256">Existing custom materials and icons are preserved.</span></span> <span data-ttu-id="fb52b-257">Saranno tuttavia meno ottimali fino all'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="fb52b-257">However they will be less optimal until upgraded.</span></span>
<span data-ttu-id="fb52b-258">Per aggiornare gli asset in tutti i pulsanti del progetto al nuovo formato consigliato, usare ButtonConfigHelperMigrationHandler.</span><span class="sxs-lookup"><span data-stu-id="fb52b-258">To upgrade the assets on all buttons in the project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="fb52b-259">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span><span class="sxs-lookup"><span data-stu-id="fb52b-259">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

![Finestra di dialogo Aggiorna](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="fb52b-261">Se non viene trovata un'icona nel set di icone predefinito durante la migrazione, verrà creato un set di icone personalizzato in MixedRealityToolkit.Generated/CustomIconSets.</span><span class="sxs-lookup"><span data-stu-id="fb52b-261">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="fb52b-262">Una finestra di dialogo indicherà che l'operazione è stata eseguita.</span><span class="sxs-lookup"><span data-stu-id="fb52b-262">A dialog will indicate that this has taken place.</span></span>

![Notifica dell'icona personalizzata](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a><span data-ttu-id="fb52b-264">Aggiornamento da 2.2.0 a 2.3.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-264">Updating 2.2.0 to 2.3.0</span></span>

- [<span data-ttu-id="fb52b-265">Modifiche all'API</span><span class="sxs-lookup"><span data-stu-id="fb52b-265">API changes</span></span>](#api-changes-in-230)

### <a name="api-changes-in-230"></a><span data-ttu-id="fb52b-266">Modifiche dell'API nella versione 2.3.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-266">API changes in 2.3.0</span></span>

<span data-ttu-id="fb52b-267">**ControllerPoseSynchronizer**</span><span class="sxs-lookup"><span data-stu-id="fb52b-267">**ControllerPoseSynchronizer**</span></span>

<span data-ttu-id="fb52b-268">Il campo ControllerPoseSynchronizer.handedness privato è stato contrassegnato come obsoleto.</span><span class="sxs-lookup"><span data-stu-id="fb52b-268">The private ControllerPoseSynchronizer.handedness field has been marked as obsolete.</span></span> <span data-ttu-id="fb52b-269">Questo dovrebbe avere un impatto minimo sulle applicazioni perché il campo non è visibile all'esterno della relativa classe.</span><span class="sxs-lookup"><span data-stu-id="fb52b-269">This should have minimal impact on applications as the field is not visible outside of its class.</span></span>

<span data-ttu-id="fb52b-270">Il setter pubblico della proprietà ControllerPoseSynchronizer.Handedness è stato rimosso ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span><span class="sxs-lookup"><span data-stu-id="fb52b-270">The public ControllerPoseSynchronizer.Handedness property's setter has been removed ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span></span>

<span data-ttu-id="fb52b-271">**MSBuild per Unity**</span><span class="sxs-lookup"><span data-stu-id="fb52b-271">**MSBuild for Unity**</span></span>

<span data-ttu-id="fb52b-272">Questa versione di MRTK usa una versione più recente di MSBuild per Unity rispetto alle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="fb52b-272">This version of MRTK uses a newer version of MSBuild for Unity than previous releases.</span></span> <span data-ttu-id="fb52b-273">Durante il caricamento del progetto, se la versione precedente è elencata nel manifesto di Gestione pacchetti Unity, verrà visualizzata la finestra di dialogo di configurazione con l'opzione Abilita MSBuild per Unity selezionata.</span><span class="sxs-lookup"><span data-stu-id="fb52b-273">During project load, if the older version is listed in the Unity Package Manger manifest, the configuration dialog will appear, with the Enable MSBuild for Unity option checked.</span></span> <span data-ttu-id="fb52b-274">L'applicazione eseguirà un aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="fb52b-274">Applying will perform an upgrade.</span></span>

<span data-ttu-id="fb52b-275">**ScriptingUtilities**</span><span class="sxs-lookup"><span data-stu-id="fb52b-275">**ScriptingUtilities**</span></span>

<span data-ttu-id="fb52b-276">La classe ScriptingUtilities è stata contrassegnata come obsoleta ed è stata sostituita da ScriptUtilities nell'assembly Microsoft.MixedReality.Toolkit.Editor.Utilities.</span><span class="sxs-lookup"><span data-stu-id="fb52b-276">The ScriptingUtilities class has been marked as obsolete and has been replaced by ScriptUtilities, in the Microsoft.MixedReality.Toolkit.Editor.Utilities assembly.</span></span> <span data-ttu-id="fb52b-277">La nuova classe perfeziona il comportamento precedente e aggiunge il supporto per la rimozione delle definizioni di scripting.</span><span class="sxs-lookup"><span data-stu-id="fb52b-277">The new class refines previous behavior and adds support for removing scripting definitions.</span></span>

<span data-ttu-id="fb52b-278">Anche se il codice esistente continuerà a funzionare nella versione 2.3.0, è consigliabile eseguire l'aggiornamento alla nuova classe .</span><span class="sxs-lookup"><span data-stu-id="fb52b-278">While existing code will continue to function in version 2.3.0, it is recommended to update to the new class.</span></span>

<span data-ttu-id="fb52b-279">**ShellHandRayPointer**</span><span class="sxs-lookup"><span data-stu-id="fb52b-279">**ShellHandRayPointer**</span></span>

<span data-ttu-id="fb52b-280">I membri lineRendererSelected e lineRendererNoTarget della classe ShellHandRayPointer sono stati sostituiti rispettivamente da lineMaterialSelected e lineMaterialNoTarget ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span><span class="sxs-lookup"><span data-stu-id="fb52b-280">The lineRendererSelected and lineRendererNoTarget members of the ShellHandRayPointer class have been replaced by lineMaterialSelected and lineMaterialNoTarget, respectively ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span></span>

<span data-ttu-id="fb52b-281">Sostituire lineRendererSelected con lineMaterialSelected e/o lineRendererNoTarget con lineMaterialNoTarget per risolvere gli errori di compilazione.</span><span class="sxs-lookup"><span data-stu-id="fb52b-281">Please replace lineRendererSelected with lineMaterialSelected and/or lineRendererNoTarget with lineMaterialNoTarget to resolve compile errors.</span></span>

<span data-ttu-id="fb52b-282">**StartupBehavior dell'osservatore spaziale**</span><span class="sxs-lookup"><span data-stu-id="fb52b-282">**Spatial observer StartupBehavior**</span></span>

<span data-ttu-id="fb52b-283">Gli osservatori spaziali compilati sulla classe ora rispettano il valore di `BaseSpatialObserver` StartupBehavior quando vengono ri abilitati ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span><span class="sxs-lookup"><span data-stu-id="fb52b-283">Spatial observers built upon the `BaseSpatialObserver` class now honor the value of StartupBehavior when re-enabled ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span></span>

<span data-ttu-id="fb52b-284">Non sono necessarie modifiche per sfruttare i vantaggi di questa correzione.</span><span class="sxs-lookup"><span data-stu-id="fb52b-284">No changes are required to take advantage of this fix.</span></span>

<span data-ttu-id="fb52b-285">**Prefab di controllo UX aggiornati per l'uso di PressableButton**</span><span class="sxs-lookup"><span data-stu-id="fb52b-285">**UX control prefabs updated to use PressableButton**</span></span>

<span data-ttu-id="fb52b-286">I prefab seguenti usano ora il componente PressableButton invece di TouchHandler per l'interazione da vicino ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span><span class="sxs-lookup"><span data-stu-id="fb52b-286">The following prefabs are now using the PressableButton component instead of TouchHandler for near interaction ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span></span>

- <span data-ttu-id="fb52b-287">AnimationButton</span><span class="sxs-lookup"><span data-stu-id="fb52b-287">AnimationButton</span></span>
- <span data-ttu-id="fb52b-288">Pulsante</span><span class="sxs-lookup"><span data-stu-id="fb52b-288">Button</span></span>
- <span data-ttu-id="fb52b-289">ButtonHoloLens1</span><span class="sxs-lookup"><span data-stu-id="fb52b-289">ButtonHoloLens1</span></span>
- <span data-ttu-id="fb52b-290">ButtonHoloLens1Toggle</span><span class="sxs-lookup"><span data-stu-id="fb52b-290">ButtonHoloLens1Toggle</span></span>
- <span data-ttu-id="fb52b-291">CheckBox</span><span class="sxs-lookup"><span data-stu-id="fb52b-291">CheckBox</span></span>
- <span data-ttu-id="fb52b-292">RadialSet</span><span class="sxs-lookup"><span data-stu-id="fb52b-292">RadialSet</span></span>
- <span data-ttu-id="fb52b-293">ToggleButton</span><span class="sxs-lookup"><span data-stu-id="fb52b-293">ToggleButton</span></span>
- <span data-ttu-id="fb52b-294">ToggleSwitch</span><span class="sxs-lookup"><span data-stu-id="fb52b-294">ToggleSwitch</span></span>
- <span data-ttu-id="fb52b-295">UnityUIButton</span><span class="sxs-lookup"><span data-stu-id="fb52b-295">UnityUIButton</span></span>
- <span data-ttu-id="fb52b-296">UnityUICheckboxButton</span><span class="sxs-lookup"><span data-stu-id="fb52b-296">UnityUICheckboxButton</span></span>
- <span data-ttu-id="fb52b-297">UnityUIRadialButton</span><span class="sxs-lookup"><span data-stu-id="fb52b-297">UnityUIRadialButton</span></span>
- <span data-ttu-id="fb52b-298">UnityUIToggleButton</span><span class="sxs-lookup"><span data-stu-id="fb52b-298">UnityUIToggleButton</span></span>

<span data-ttu-id="fb52b-299">Il codice dell'applicazione potrebbe richiedere l'aggiornamento a causa di questa modifica.</span><span class="sxs-lookup"><span data-stu-id="fb52b-299">Application code may require updating due to this change.</span></span>

<span data-ttu-id="fb52b-300">**Spazio dei nomi WindowsMixedRealityUtilities**</span><span class="sxs-lookup"><span data-stu-id="fb52b-300">**WindowsMixedRealityUtilities namespace**</span></span>

<span data-ttu-id="fb52b-301">Lo spazio dei nomi di WindowsMixedRealityUtilities è stato modificato da Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input a Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span><span class="sxs-lookup"><span data-stu-id="fb52b-301">The namespace of WindowsMixedRealityUtilities changed from Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input to Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span></span>

<span data-ttu-id="fb52b-302">Aggiornare le #using per risolvere gli errori di compilazione.</span><span class="sxs-lookup"><span data-stu-id="fb52b-302">Please update #using statements to resolve compile errors.</span></span>

## <a name="updating-210-to-220"></a><span data-ttu-id="fb52b-303">Aggiornamento da 2.1.0 a 2.2.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-303">Updating 2.1.0 to 2.2.0</span></span>

- [<span data-ttu-id="fb52b-304">Modifiche all'API</span><span class="sxs-lookup"><span data-stu-id="fb52b-304">API changes</span></span>](#api-changes-in-220)

### <a name="api-changes-in-220"></a><span data-ttu-id="fb52b-305">Modifiche dell'API nella versione 2.2.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-305">API changes in 2.2.0</span></span>

<span data-ttu-id="fb52b-306">**IMixedRealityBoundarySystem.Contains**</span><span class="sxs-lookup"><span data-stu-id="fb52b-306">**IMixedRealityBoundarySystem.Contains**</span></span>

<span data-ttu-id="fb52b-307">Questo metodo in precedenza ha preso in un'enumerazione sperimentale specifica, definita da Unity.</span><span class="sxs-lookup"><span data-stu-id="fb52b-307">This method previously took in a specific, Unity-defined experimental enum.</span></span> <span data-ttu-id="fb52b-308">Accetta ora un'enumerazione definita da MRTK identica all'enumerazione Unity.</span><span class="sxs-lookup"><span data-stu-id="fb52b-308">It now takes in an MRTK-defined enum that's identical to the Unity enum.</span></span> <span data-ttu-id="fb52b-309">Questa modifica consente di preparare MRTK per le API limite future di Unity.</span><span class="sxs-lookup"><span data-stu-id="fb52b-309">This change helps prepare the MRTK for Unity's future boundary APIs.</span></span>

<span data-ttu-id="fb52b-310">**MixedRealityServiceProfileAttribute**</span><span class="sxs-lookup"><span data-stu-id="fb52b-310">**MixedRealityServiceProfileAttribute**</span></span>

<span data-ttu-id="fb52b-311">Per descrivere meglio i requisiti per il supporto di un profilo, MixedRealityServiceProfileAttribute è stato aggiornato per aggiungere una raccolta facoltativa di tipi esclusi.</span><span class="sxs-lookup"><span data-stu-id="fb52b-311">To better describe the requirements for supporting a profile, the MixedRealityServiceProfileAttribute has been updated to add an optional collection of excluded types.</span></span> <span data-ttu-id="fb52b-312">Come parte di questa modifica, la proprietà ServiceType è stata modificata da Type a Type[] ed è stata rinominata RequiredTypes.</span><span class="sxs-lookup"><span data-stu-id="fb52b-312">As part of this change, the ServiceType property has been changed from Type to Type[] and been renamed to RequiredTypes.</span></span>

<span data-ttu-id="fb52b-313">È stata aggiunta anche una seconda proprietà, ExcludedTypes.</span><span class="sxs-lookup"><span data-stu-id="fb52b-313">A second property, ExcludedTypes has also been added.</span></span>

## <a name="updating-200-to-210"></a><span data-ttu-id="fb52b-314">Aggiornamento dalla versione 2.0.0 alla versione 2.1.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-314">Updating 2.0.0 to 2.1.0</span></span>

- [<span data-ttu-id="fb52b-315">Modifiche all'API</span><span class="sxs-lookup"><span data-stu-id="fb52b-315">API changes</span></span>](#api-changes-in-210)
- [<span data-ttu-id="fb52b-316">Modifiche del profilo</span><span class="sxs-lookup"><span data-stu-id="fb52b-316">Profile changes</span></span>](#profile-changes-in-210)

### <a name="api-changes-in-210"></a><span data-ttu-id="fb52b-317">Modifiche all'API nella versione 2.1.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-317">API changes in 2.1.0</span></span>

<span data-ttu-id="fb52b-318">**BaseNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="fb52b-318">**BaseNearInteractionTouchable**</span></span>

<span data-ttu-id="fb52b-319">È `BaseNearInteractionTouchable` stato modificato per contrassegnare il metodo come `OnValidate` virtuale.</span><span class="sxs-lookup"><span data-stu-id="fb52b-319">The `BaseNearInteractionTouchable` has been modified to mark the `OnValidate` method as virtual.</span></span> <span data-ttu-id="fb52b-320">Le classi che `BaseNearInteractionTouchable` estendono (ad `NearInteractionTouchableUnityUI` esempio) sono state aggiornate per riflettere questa modifica.</span><span class="sxs-lookup"><span data-stu-id="fb52b-320">Classes that extend `BaseNearInteractionTouchable` (ex: `NearInteractionTouchableUnityUI`) have been updated to reflect this change.</span></span>

<span data-ttu-id="fb52b-321">**ColliderNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="fb52b-321">**ColliderNearInteractionTouchable**</span></span>

<span data-ttu-id="fb52b-322">La classe `ColliderNearInteractionTouchable` è stata deprecata.</span><span class="sxs-lookup"><span data-stu-id="fb52b-322">The `ColliderNearInteractionTouchable` class has been deprecated.</span></span> <span data-ttu-id="fb52b-323">Aggiornare i riferimenti al codice per usare `BaseNearInteractionTouchable` .</span><span class="sxs-lookup"><span data-stu-id="fb52b-323">Please update code references to use `BaseNearInteractionTouchable`.</span></span>

<span data-ttu-id="fb52b-324">**IMixedRealityMouseDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="fb52b-324">**IMixedRealityMouseDeviceManager**</span></span>

<span data-ttu-id="fb52b-325">**_Aggiunto_**</span><span class="sxs-lookup"><span data-stu-id="fb52b-325">**_Added_**</span></span>

<span data-ttu-id="fb52b-326">`IMixedRealityMouseDeviceManager` sono state aggiunte `CursorSpeed` le proprietà `WheelSpeed` e .</span><span class="sxs-lookup"><span data-stu-id="fb52b-326">`IMixedRealityMouseDeviceManager` has been added `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="fb52b-327">Queste proprietà consentono alle applicazioni di specificare un valore moltiplicatore in base al quale verrà ridimensionata rispettivamente la velocità del cursore e della rotellina.</span><span class="sxs-lookup"><span data-stu-id="fb52b-327">These properties allow applications to specify a multiplier value by which the speed of the cursor and wheel, respectively will be scaled.</span></span>

<span data-ttu-id="fb52b-328">Si tratta di una modifica di rilievo e richiede che le implementazioni esistenti di Gestione dispositivi mouse siano modificate.</span><span class="sxs-lookup"><span data-stu-id="fb52b-328">This is a breaking change and requires existing mouse device manager implementations to be modified .</span></span>

>[!NOTE]
><span data-ttu-id="fb52b-329">Questa modifica non è compatibile con la versione 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="fb52b-329">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="fb52b-330">**_Deprecato_**</span><span class="sxs-lookup"><span data-stu-id="fb52b-330">**_Deprecated_**</span></span>

<span data-ttu-id="fb52b-331">La `MouseInputProfile` proprietà è stata contrassegnata come obsoleta e verrà rimossa da una versione futura di Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="fb52b-331">The `MouseInputProfile` property has been marked as obsolete and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="fb52b-332">È consigliabile che il codice dell'applicazione non usi più questa proprietà.</span><span class="sxs-lookup"><span data-stu-id="fb52b-332">It is recommended that application code no longer use this property.</span></span>

<span data-ttu-id="fb52b-333">**Con interazione**</span><span class="sxs-lookup"><span data-stu-id="fb52b-333">**Interactable**</span></span>

<span data-ttu-id="fb52b-334">I metodi e le proprietà seguenti sono stati deprecati e verranno rimossi da una versione futura di Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="fb52b-334">The following methods and properties have been deprecated and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="fb52b-335">È consigliabile aggiornare il codice dell'applicazione in base alle indicazioni contenute nell'attributo Obsolete e visualizzato nella console.</span><span class="sxs-lookup"><span data-stu-id="fb52b-335">The recommendation is to update application code per the guidance contained in the Obsolete attribute and displayed in the console.</span></span>

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

<span data-ttu-id="fb52b-336">**NearInteractionTouchableSurface**</span><span class="sxs-lookup"><span data-stu-id="fb52b-336">**NearInteractionTouchableSurface**</span></span>

<span data-ttu-id="fb52b-337">La `NearInteractionTouchableSurface` classe è stata aggiunta e ora funge da classe di base per e `NearInteractionTouchable` `NearInteractionTouchableUnityUI` .</span><span class="sxs-lookup"><span data-stu-id="fb52b-337">The `NearInteractionTouchableSurface` class has been added and now serves as the base class for `NearInteractionTouchable` and `NearInteractionTouchableUnityUI`.</span></span>

### <a name="profile-changes-in-210"></a><span data-ttu-id="fb52b-338">Modifiche del profilo nella versione 2.1.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-338">Profile changes in 2.1.0</span></span>

<span data-ttu-id="fb52b-339">**Profilo di tracciamento manuale**</span><span class="sxs-lookup"><span data-stu-id="fb52b-339">**Hand tracking profile**</span></span>

<span data-ttu-id="fb52b-340">La mesh a mano e le visualizzazioni congiunte hanno ora un editor e le impostazioni del giocatore separati.</span><span class="sxs-lookup"><span data-stu-id="fb52b-340">The hand mesh and joint visualizations now have a separate editor and player settings.</span></span> <span data-ttu-id="fb52b-341">Il profilo di rilevamento manuale è stato aggiornato per consentire l'impostazione di queste visualizzazioni su . Nothing, Everything, Editor o Player.</span><span class="sxs-lookup"><span data-stu-id="fb52b-341">The hand tracking profile has been updated to allow for setting these visualizations to; Nothing, Everything, Editor or Player.</span></span>

![Modalità di visualizzazione manuale](../release-notes/images/HandTrackingVisualizationModes.png)

<span data-ttu-id="fb52b-343">Per il corretto funzionamento con la versione 2.1.0 potrebbe essere necessario aggiornare i profili di tracciamento manuale personalizzati.</span><span class="sxs-lookup"><span data-stu-id="fb52b-343">Custom hand tracking profiles may need to be updated to work correctly with version 2.1.0.</span></span>

>[!NOTE]
><span data-ttu-id="fb52b-344">Questa modifica non è compatibile con la versione 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="fb52b-344">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="fb52b-345">**Profilo di simulazione di input**</span><span class="sxs-lookup"><span data-stu-id="fb52b-345">**Input simulation profile**</span></span>

<span data-ttu-id="fb52b-346">Il sistema di simulazione dell'input è stato aggiornato, che modifica alcune impostazioni nel profilo di simulazione di input.</span><span class="sxs-lookup"><span data-stu-id="fb52b-346">The input simulation system has been upgraded, which changes a few settings in the input simulation profile.</span></span> <span data-ttu-id="fb52b-347">Non è possibile eseguire automaticamente la migrazione di alcune modifiche e gli utenti potrebbero scoprire che i profili usano valori predefiniti.</span><span class="sxs-lookup"><span data-stu-id="fb52b-347">Some changes can not be migrated automatically and users may find that profiles are using default values.</span></span>

1. <span data-ttu-id="fb52b-348">Tutte le associazioni keyCode e del pulsante del mouse nel profilo sono state sostituite con uno struct generico, che archivia il tipo di associazione (tasto o mouse) e il codice di associazione effettivo (KeyCode o il numero del pulsante del `KeyBinding` mouse rispettivamente).</span><span class="sxs-lookup"><span data-stu-id="fb52b-348">All KeyCode and mouse button bindings in the profile have been replaced with a generic `KeyBinding` struct, which stores the type of binding (key or mouse) as well as the actual binding code (KeyCode or mouse button number respectively).</span></span> <span data-ttu-id="fb52b-349">Lo struct ha un proprio controllo, che consente la visualizzazione unificata e offre uno strumento di "associazione automatica" per impostare rapidamente le associazioni di tasti premendo il rispettivo tasto invece di selezionare da un elenco a discesa enorme.</span><span class="sxs-lookup"><span data-stu-id="fb52b-349">The struct has its own inspector, which allows unified display and offers an "auto-bind" tool to quickly set key bindings by pressing the respective key instead of selecting from a huge dropdown list.</span></span>

    - <span data-ttu-id="fb52b-350">FastControlKey</span><span class="sxs-lookup"><span data-stu-id="fb52b-350">FastControlKey</span></span>
    - <span data-ttu-id="fb52b-351">ToggleLeftHandKey</span><span class="sxs-lookup"><span data-stu-id="fb52b-351">ToggleLeftHandKey</span></span>
    - <span data-ttu-id="fb52b-352">ToggleRightHandKey</span><span class="sxs-lookup"><span data-stu-id="fb52b-352">ToggleRightHandKey</span></span>
    - <span data-ttu-id="fb52b-353">LeftHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="fb52b-353">LeftHandManipulationKey</span></span>
    - <span data-ttu-id="fb52b-354">RightHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="fb52b-354">RightHandManipulationKey</span></span>

1. <span data-ttu-id="fb52b-355">`MouseLookToggle` in precedenza era incluso `MouseLookButton` nell'enumerazione `InputSimulationMouseButton.Focused` come , ora è un'opzione separata.</span><span class="sxs-lookup"><span data-stu-id="fb52b-355">`MouseLookToggle` was previously included in the `MouseLookButton` enum as `InputSimulationMouseButton.Focused`, it is now a separate option.</span></span> <span data-ttu-id="fb52b-356">Se abilitata, la fotocamera continuerà a ruotare con il mouse dopo il rilascio del pulsante, fino a quando non viene premuto il tasto di escape.</span><span class="sxs-lookup"><span data-stu-id="fb52b-356">When enabled, the camera will keep rotating with the mouse after releasing the button, until the escape key is pressed.</span></span>
1. <span data-ttu-id="fb52b-357">`HandDepthMultiplier` il valore predefinito è stato abbassato da 0,1 a 0,03 per contenere alcune modifiche alla simulazione di input.</span><span class="sxs-lookup"><span data-stu-id="fb52b-357">`HandDepthMultiplier` default value has been lowered from 0.1 to 0.03 to accommodate some changes to the input simulation.</span></span> <span data-ttu-id="fb52b-358">Se la fotocamera si sposta troppo velocemente durante lo scorrimento, provare ad abbassare questo valore.</span><span class="sxs-lookup"><span data-stu-id="fb52b-358">If the camera moves too fast when scrolling, try lowering this value.</span></span>
1. <span data-ttu-id="fb52b-359">Le chiavi per ruotare le mani sono state rimosse, la rotazione delle mani è ora controllata anche dal mouse.</span><span class="sxs-lookup"><span data-stu-id="fb52b-359">Keys for rotating hands have been removed, hand rotation is now controlled by the mouse as well.</span></span> <span data-ttu-id="fb52b-360">Tenendo premuto (CTRL) insieme al tasto di manipolazione della mano `HandRotateButton` sinistra/destra (LShift/Space) verrà abilitata la rotazione della mano.</span><span class="sxs-lookup"><span data-stu-id="fb52b-360">Holding `HandRotateButton` (Ctrl) together with the left/right hand manipulation key (LShift/Space) will enable hand rotation.</span></span>
1. <span data-ttu-id="fb52b-361">È stato introdotto un nuovo asse "UpDown" nell'elenco degli assi di input.</span><span class="sxs-lookup"><span data-stu-id="fb52b-361">A new axis "UpDown" has been introduced to the input axis list.</span></span> <span data-ttu-id="fb52b-362">Questo controllo controlla lo spostamento della fotocamera in verticale e per impostazione predefinita vengono visualizzati i tasti Q/E, nonché i pulsanti del trigger del controller.</span><span class="sxs-lookup"><span data-stu-id="fb52b-362">This controls camera movement in the vertical and defaults to Q/E keys as well as the controller trigger buttons.</span></span>

<span data-ttu-id="fb52b-363">Per altre informazioni su queste modifiche, vedere l'articolo sul servizio [di simulazione dell'input.](../features/input-simulation/input-simulation-service.md)</span><span class="sxs-lookup"><span data-stu-id="fb52b-363">For more information on these changes, please see the [input simulation service](../features/input-simulation/input-simulation-service.md) article.</span></span>

<span data-ttu-id="fb52b-364">**Profilo del provider di dati mouse**</span><span class="sxs-lookup"><span data-stu-id="fb52b-364">**Mouse data provider profile**</span></span>

<span data-ttu-id="fb52b-365">Il profilo del provider di dati del mouse è stato aggiornato per esporre le nuove `CursorSpeed` proprietà `WheelSpeed` e .</span><span class="sxs-lookup"><span data-stu-id="fb52b-365">The mouse data provider profile has been updated to expose the new `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="fb52b-366">Per i profili personalizzati esistenti verranno forniti automaticamente i valori predefiniti.</span><span class="sxs-lookup"><span data-stu-id="fb52b-366">Existing custom profiles will automatically have default values provided.</span></span> <span data-ttu-id="fb52b-367">Quando il profilo viene salvato, questi nuovi valori verranno salvati in modo permanente.</span><span class="sxs-lookup"><span data-stu-id="fb52b-367">When the profile is saved, these new values will be persisted.</span></span>

<span data-ttu-id="fb52b-368">**Profilo di mapping del controller**</span><span class="sxs-lookup"><span data-stu-id="fb52b-368">**Controller mapping profile**</span></span>

<span data-ttu-id="fb52b-369">Alcuni assi e tipi di input sono stati aggiornati nella versione 2.1.0, in particolare per quanto riguarda la piattaforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="fb52b-369">Some axes and input types have been updated in 2.1.0, especially around the OpenVR platform.</span></span> <span data-ttu-id="fb52b-370">Assicurarsi di selezionare **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** durante l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="fb52b-370">Please be sure to select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** when upgrading.</span></span> <span data-ttu-id="fb52b-371">In questo modo, tutti i profili di mapping del controller personalizzati verranno aggiornati con gli assi e i dati aggiornati, lasciando intatte le azioni di input assegnate dall'utente.</span><span class="sxs-lookup"><span data-stu-id="fb52b-371">This will update any custom Controller Mapping Profiles with the updated axes and data, while leaving your custom-assigned input actions intact.</span></span>

## <a name="updating-rc2-to-200"></a><span data-ttu-id="fb52b-372">Aggiornamento da RC2 a 2.0.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-372">Updating RC2 to 2.0.0</span></span>

<span data-ttu-id="fb52b-373">Tra le versioni RC2 e 2.0.0 di Microsoft Mixed Reality Toolkit sono state apportate modifiche che potrebbero influire sui progetti esistenti.</span><span class="sxs-lookup"><span data-stu-id="fb52b-373">Between the RC2 and 2.0.0 releases of the Microsoft Mixed Reality Toolkit, changes were made that may impact existing projects.</span></span> <span data-ttu-id="fb52b-374">Questo documento descrive queste modifiche e come aggiornare i progetti alla versione 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="fb52b-374">This document describes those changes and how to update projects to the 2.0.0 release.</span></span>

- [<span data-ttu-id="fb52b-375">Modifiche all'API</span><span class="sxs-lookup"><span data-stu-id="fb52b-375">API changes</span></span>](#api-changes-in-200)
- [<span data-ttu-id="fb52b-376">Modifiche al nome dell'assembly</span><span class="sxs-lookup"><span data-stu-id="fb52b-376">Assembly name changes</span></span>](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a><span data-ttu-id="fb52b-377">Modifiche dell'API nella versione 2.0.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-377">API changes in 2.0.0</span></span>

<span data-ttu-id="fb52b-378">Dopo il rilascio di RC2, sono state apportate alcune modifiche all'API, tra cui alcune che potrebbero interrompere i progetti esistenti.</span><span class="sxs-lookup"><span data-stu-id="fb52b-378">Since the release of RC2, there have been a number of API changes including some that may break existing projects.</span></span> <span data-ttu-id="fb52b-379">Le sezioni seguenti descrivono le modifiche apportate tra le versioni RC2 e 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="fb52b-379">The following sections describe the changes that have occurred between the RC2 and 2.0.0 releases.</span></span>

<span data-ttu-id="fb52b-380">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="fb52b-380">**MixedRealityToolkit**</span></span>

<span data-ttu-id="fb52b-381">Le proprietà pubbliche seguenti nell'oggetto MixedRealityToolkit sono state deprecate.</span><span class="sxs-lookup"><span data-stu-id="fb52b-381">The following public properties on the MixedRealityToolkit object have been deprecated.</span></span>

- <span data-ttu-id="fb52b-382">`RegisteredMixedRealityServices` non contiene più la raccolta di servizi di estensioni registrati e provider di dati.</span><span class="sxs-lookup"><span data-stu-id="fb52b-382">`RegisteredMixedRealityServices` no longer contains the collection of registered extensions services and data providers.</span></span>

<span data-ttu-id="fb52b-383">Per accedere ai servizi di estensione, usare `MixedRealityServiceRegistry.TryGetService<T>` .</span><span class="sxs-lookup"><span data-stu-id="fb52b-383">To access extension services, use `MixedRealityServiceRegistry.TryGetService<T>`.</span></span> <span data-ttu-id="fb52b-384">Per accedere ai provider di dati, eseguire il cast dell'istanza del servizio [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) a e usare `GetDataProvider<T>` .</span><span class="sxs-lookup"><span data-stu-id="fb52b-384">To access data providers, cast the service instance to [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) and use `GetDataProvider<T>`.</span></span>

<span data-ttu-id="fb52b-385">Usare [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) o invece per le proprietà [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) deprecate seguenti</span><span class="sxs-lookup"><span data-stu-id="fb52b-385">Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) or [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) instead for the following deprecated properties</span></span>

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

<span data-ttu-id="fb52b-386">**CoreServices**</span><span class="sxs-lookup"><span data-stu-id="fb52b-386">**CoreServices**</span></span>

<span data-ttu-id="fb52b-387">La classe è la sostituzione delle funzioni di accesso di sistema [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) statiche (ad esempio BoundarySystem) trovate `MixedRealityToolkit` nell'oggetto .</span><span class="sxs-lookup"><span data-stu-id="fb52b-387">The [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) class is the replacement for the static system accessors (ex: BoundarySystem) found in the `MixedRealityToolkit` object.</span></span>

>[!IMPORTANT]
><span data-ttu-id="fb52b-388">Le `MixedRealityToolkit` funzioni di accesso di sistema sono state deprecate nella versione 2.0.0 e verranno rimosse in una versione futura di MRTK.</span><span class="sxs-lookup"><span data-stu-id="fb52b-388">The `MixedRealityToolkit` system accessors have been deprecated in version 2.0.0 and will be removed in a future release of the MRTK.</span></span>

<span data-ttu-id="fb52b-389">L'esempio di codice seguente illustra il modello precedente e il nuovo modello.</span><span class="sxs-lookup"><span data-stu-id="fb52b-389">The following code example illustrates the old and the new pattern.</span></span>

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

<span data-ttu-id="fb52b-390">L'uso della nuova classe CoreSystem garantisce che il codice dell'applicazione non dovrà essere aggiornato se si modifica l'applicazione in modo da usare un registrar del servizio diverso(ad esempio, uno dei gestori di servizi sperimentali).</span><span class="sxs-lookup"><span data-stu-id="fb52b-390">Using the new CoreSystem class will ensure that your application code will not need updating if you change the application to use a different service registrar (ex: one of the experimental service managers).</span></span>

<span data-ttu-id="fb52b-391">**IMixedRealityRaycastProvider**</span><span class="sxs-lookup"><span data-stu-id="fb52b-391">**IMixedRealityRaycastProvider**</span></span>

<span data-ttu-id="fb52b-392">Con l'aggiunta di IMixedRealityRaycastProvider, il profilo di configurazione del sistema di input è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="fb52b-392">With the addition of the IMixedRealityRaycastProvider, the input system configuration profile was changed.</span></span> <span data-ttu-id="fb52b-393">Se si dispone di un profilo personalizzato, è possibile che si ricevano gli errori nell'immagine seguente quando si esegue l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="fb52b-393">If you have a custom profile, you may receive the errors in the following image when you run your application.</span></span>

![Selezione del provider Raycast 1](../release-notes/images/UnableToRegisterRaycastProvider.png)

<span data-ttu-id="fb52b-395">Per risolvere questi problemi, aggiungere un'istanza di IMixedRealityRaycastProvider al profilo di sistema di input.</span><span class="sxs-lookup"><span data-stu-id="fb52b-395">To fix these, please add an IMixedRealityRaycastProvider instance to your input system profile.</span></span>

![Selezione del provider Raycast 2](../release-notes/images/SelectRaycastProvider.png)

<span data-ttu-id="fb52b-397">**Sistema di eventi**</span><span class="sxs-lookup"><span data-stu-id="fb52b-397">**Event System**</span></span>

- <span data-ttu-id="fb52b-398">I `IMixedRealityEventSystem` metodi API obsoleti e sono stati `Register` `Unregister` contrassegnati come obsoleti.</span><span class="sxs-lookup"><span data-stu-id="fb52b-398">The `IMixedRealityEventSystem` old API methods `Register` and `Unregister` have been marked as obsolete.</span></span> <span data-ttu-id="fb52b-399">Vengono mantenuti per compatibilità con le versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="fb52b-399">They are preserved for backwards compatibility.</span></span>
- <span data-ttu-id="fb52b-400">`InputSystemGlobalListener` è stato contrassegnato come obsoleto.</span><span class="sxs-lookup"><span data-stu-id="fb52b-400">`InputSystemGlobalListener` has been marked as obsolete.</span></span> <span data-ttu-id="fb52b-401">La funzionalità non è stata modificata.</span><span class="sxs-lookup"><span data-stu-id="fb52b-401">Its functionality has not changed.</span></span>
- <span data-ttu-id="fb52b-402">`BaseInputHandler` La classe base è stata modificata da `InputSystemGlobalListener` a `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="fb52b-402">`BaseInputHandler` base class has been changed from `InputSystemGlobalListener` to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="fb52b-403">Si tratta di una modifica di rilievo per tutti i discendenti di `BaseInputHandler` .</span><span class="sxs-lookup"><span data-stu-id="fb52b-403">This is a breaking change for any descendants of `BaseInputHandler`.</span></span>

<span data-ttu-id="fb52b-404">**_Motivazione alla base della modifica_**</span><span class="sxs-lookup"><span data-stu-id="fb52b-404">**_Motivation behind the change_**</span></span>

<span data-ttu-id="fb52b-405">L'API del sistema di `Register` eventi precedente e potrebbe potenzialmente causare più problemi in fase di `Unregister` esecuzione, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="fb52b-405">The old event system API `Register` and `Unregister` could potentially cause multiple issues in runtime, main being:</span></span>

- <span data-ttu-id="fb52b-406">Se un componente si registra per eventi globali, riceverà eventi di input globali di *tutti i* tipi.</span><span class="sxs-lookup"><span data-stu-id="fb52b-406">If a component registers for global events, it would receive global input events of *all* types.</span></span>
- <span data-ttu-id="fb52b-407">Se uno dei componenti di un oggetto viene registrato per gli eventi di input globali, tutti i componenti in questo oggetto riceveranno eventi di input globali di *tutti i* tipi.</span><span class="sxs-lookup"><span data-stu-id="fb52b-407">If one of the components on an object registers for global input events, all components on this object will receive global input events of *all* types.</span></span>
- <span data-ttu-id="fb52b-408">Se due componenti nello stesso oggetto vengono registrati in eventi globali e uno viene disabilitato in fase di esecuzione, il secondo smette di ricevere eventi globali.</span><span class="sxs-lookup"><span data-stu-id="fb52b-408">If two components on the same object register to global events, and then one is disabled in runtime, the second one stops receiving global events.</span></span>

<span data-ttu-id="fb52b-409">Nuova API `RegisterHandler` e `UnregisterHandler` :</span><span class="sxs-lookup"><span data-stu-id="fb52b-409">New API `RegisterHandler` and `UnregisterHandler`:</span></span>

- <span data-ttu-id="fb52b-410">Fornisce un controllo esplicito e granulare su quali eventi di input devono essere in ascolto a livello globale e su quali devono essere basati su stato attivo.</span><span class="sxs-lookup"><span data-stu-id="fb52b-410">Provides an explicit and granular control over which input events should be listened to globally and which should be focused-based.</span></span>
- <span data-ttu-id="fb52b-411">Consente a più componenti nello stesso oggetto di restare in ascolto di eventi globali in modo indipendente l'uno sull'altro.</span><span class="sxs-lookup"><span data-stu-id="fb52b-411">Allows multiple components on the same object to listen to global events independently on each other.</span></span>

<span data-ttu-id="fb52b-412">**_Come eseguire la migrazione_**</span><span class="sxs-lookup"><span data-stu-id="fb52b-412">**_How to migrate_**</span></span>

- <span data-ttu-id="fb52b-413">Se l'API è stata `Register` / `Unregister` chiamata direttamente in precedenza, sostituire queste chiamate con chiamate a `RegisterHandler` / `UnregisterHandler` .</span><span class="sxs-lookup"><span data-stu-id="fb52b-413">If you have been calling `Register`/`Unregister` API directly before, replace these calls with calls to `RegisterHandler`/`UnregisterHandler`.</span></span> <span data-ttu-id="fb52b-414">Usare le interfacce del gestore implementate come parametri generici.</span><span class="sxs-lookup"><span data-stu-id="fb52b-414">Use handler interfaces you implement as generic parameters.</span></span> <span data-ttu-id="fb52b-415">Se si implementano più interfacce e molte di esse sono in ascolto di eventi di input globali, chiamare `RegisterHandler` più volte.</span><span class="sxs-lookup"><span data-stu-id="fb52b-415">If you implement multiple interfaces, and several of them listen to global input events, call `RegisterHandler` multiple times.</span></span>
- <span data-ttu-id="fb52b-416">Se si eredita da , modificare `InputSystemGlobalListener` l'ereditarietà in `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="fb52b-416">If you have been inheriting from `InputSystemGlobalListener`, change inheritance to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="fb52b-417">Implementare `RegisterHandlers` e `UnregisterHandlers` astrarre i metodi.</span><span class="sxs-lookup"><span data-stu-id="fb52b-417">Implement `RegisterHandlers` and `UnregisterHandlers` abstract methods.</span></span> <span data-ttu-id="fb52b-418">Nella chiamata di implementazione ( ) per eseguire la registrazione in tutte le interfacce del gestore per cui si vogliono restare in ascolto `inputSystem.RegisterHandler` `inputSystem.UnregisterHandler` degli eventi globali.</span><span class="sxs-lookup"><span data-stu-id="fb52b-418">In the implementation call `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) to register on all handler interfaces you want to listen global events for.</span></span>
- <span data-ttu-id="fb52b-419">Se si eredita da `BaseInputHandler` , implementare e `RegisterHandlers` `UnregisterHandlers` astrarre i metodi (come per `InputSystemGlobalListener` ).</span><span class="sxs-lookup"><span data-stu-id="fb52b-419">If you have been inheriting from `BaseInputHandler`, implement `RegisterHandlers` and `UnregisterHandlers` abstract methods (same as for `InputSystemGlobalListener`).</span></span>

<span data-ttu-id="fb52b-420">**_Esempi di migrazione_**</span><span class="sxs-lookup"><span data-stu-id="fb52b-420">**_Examples of migration_**</span></span>

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

<span data-ttu-id="fb52b-421">**Consapevolezza spaziale**</span><span class="sxs-lookup"><span data-stu-id="fb52b-421">**Spatial Awareness**</span></span>

<span data-ttu-id="fb52b-422">Le interfacce IMixedRealitySpatialAwarenessSystem e IMixedRealitySpatialAwarenessObserver hanno apportato più modifiche di rilievo, come descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="fb52b-422">The IMixedRealitySpatialAwarenessSystem and IMixedRealitySpatialAwarenessObserver interfaces have taken multiple breaking changes as described below.</span></span>

<span data-ttu-id="fb52b-423">**_Modifiche_**</span><span class="sxs-lookup"><span data-stu-id="fb52b-423">**_Changes_**</span></span>

<span data-ttu-id="fb52b-424">I metodi seguenti sono stati rinominati per descriverne meglio l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="fb52b-424">The following method(s) have been renamed to better describe their usage.</span></span>

- <span data-ttu-id="fb52b-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` è stato rinominato in per `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` chiarirne l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="fb52b-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` has been renamed to `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` to clarify its usage.</span></span>

<span data-ttu-id="fb52b-426">**_Aggiornamenti_**</span><span class="sxs-lookup"><span data-stu-id="fb52b-426">**_Additions_**</span></span>

<span data-ttu-id="fb52b-427">In base ai commenti e suggerimenti dei clienti, è stato aggiunto il supporto per la rimozione semplice dei dati di consapevolezza spaziale osservati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="fb52b-427">Based on customer feedback, support for easy removal of previously observed spatial awareness data has been added.</span></span>

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

<span data-ttu-id="fb52b-428">**Risolutori**</span><span class="sxs-lookup"><span data-stu-id="fb52b-428">**Solvers**</span></span>

<span data-ttu-id="fb52b-429">Alcuni componenti del risolutore e la classe di gestione SolverHandler sono stati modificati per correggere vari bug e per un utilizzo più intuitivo.</span><span class="sxs-lookup"><span data-stu-id="fb52b-429">Some solver components and the SolverHandler manager class has changed to fix various bugs and for more intuitive usage.</span></span>

<span data-ttu-id="fb52b-430">**_SolverHandler_**</span><span class="sxs-lookup"><span data-stu-id="fb52b-430">**_SolverHandler_**</span></span>

- <span data-ttu-id="fb52b-431">La classe non si estende più da `ControllerFinder`</span><span class="sxs-lookup"><span data-stu-id="fb52b-431">Class no longer extends from `ControllerFinder`</span></span>
- <span data-ttu-id="fb52b-432">`TrackedObjectToReference` proprietà pubblica deprecata ed è stata rinominata in `TrackedTargetType`</span><span class="sxs-lookup"><span data-stu-id="fb52b-432">`TrackedObjectToReference` public property deprecated and has been renamed to `TrackedTargetType`</span></span>
- <span data-ttu-id="fb52b-433">`TrackedObjectType` deprecazione dei & a destra del controller.</span><span class="sxs-lookup"><span data-stu-id="fb52b-433">`TrackedObjectType` deprecates left & right controller values.</span></span> <span data-ttu-id="fb52b-434">Usare invece `MotionController` i valori o e aggiornare la nuova proprietà per limitare il rilevamento al controller sinistro o `HandJoint` `TrackedHandedness` destro</span><span class="sxs-lookup"><span data-stu-id="fb52b-434">Instead use `MotionController` or `HandJoint` values and update new `TrackedHandedness` property to limit tracking to left or right controller</span></span>

<span data-ttu-id="fb52b-435">**_Inbetween_**</span><span class="sxs-lookup"><span data-stu-id="fb52b-435">**_InBetween_**</span></span>

- <span data-ttu-id="fb52b-436">`TrackedObjectForSecondTransform` proprietà pubblica deprecata ed è stata rinominata in `SecondTrackedObjectType`</span><span class="sxs-lookup"><span data-stu-id="fb52b-436">`TrackedObjectForSecondTransform` public property deprecated and has been renamed to `SecondTrackedObjectType`</span></span>
- <span data-ttu-id="fb52b-437">`AttachSecondTransformToNewTrackedObject()` è stato rimosso.</span><span class="sxs-lookup"><span data-stu-id="fb52b-437">`AttachSecondTransformToNewTrackedObject()` has been removed.</span></span> <span data-ttu-id="fb52b-438">Per aggiornare il risolutore, modificare le proprietà pubbliche, ad esempio</span><span class="sxs-lookup"><span data-stu-id="fb52b-438">To update the solver, modify the public properties (i.e</span></span> <span data-ttu-id="fb52b-439">`SecondTrackedObjectType`)</span><span class="sxs-lookup"><span data-stu-id="fb52b-439">`SecondTrackedObjectType`)</span></span>

<span data-ttu-id="fb52b-440">**_SurfaceMagnetism_**</span><span class="sxs-lookup"><span data-stu-id="fb52b-440">**_SurfaceMagnetism_**</span></span>

- <span data-ttu-id="fb52b-441">`MaxDistance` la proprietà public è deprecata ed è stata rinominata in `MaxRaycastDistance`</span><span class="sxs-lookup"><span data-stu-id="fb52b-441">`MaxDistance` public property deprecated and has been renamed to `MaxRaycastDistance`</span></span>
- <span data-ttu-id="fb52b-442">`CloseDistance` la proprietà public è deprecata ed è stata rinominata in `ClosestDistance`</span><span class="sxs-lookup"><span data-stu-id="fb52b-442">`CloseDistance` public property deprecated and has been renamed to `ClosestDistance`</span></span>
- <span data-ttu-id="fb52b-443">Il valore predefinito per è ora il raycast nella direzione della trasformazione `RaycastDirectionMode` della destinazione `TrackedTargetForward` rilevata in avanti</span><span class="sxs-lookup"><span data-stu-id="fb52b-443">Default value for `RaycastDirectionMode` is now `TrackedTargetForward` which raycasts in the direction of the tracked target transform forward</span></span>
- <span data-ttu-id="fb52b-444">`OrientationMode`I valori enum `Vertical` e `Full` sono stati rinominati `TrackedTarget` rispettivamente in e `SurfaceNormal`</span><span class="sxs-lookup"><span data-stu-id="fb52b-444">`OrientationMode` enum values, `Vertical` and `Full`, have been renamed to `TrackedTarget` and `SurfaceNormal` respectively</span></span>
- <span data-ttu-id="fb52b-445">`KeepOrientationVertical` È stata aggiunta la proprietà public per controllare se l'orientamento del GameObject associato rimane verticale</span><span class="sxs-lookup"><span data-stu-id="fb52b-445">`KeepOrientationVertical` public property has been added to control whether orientation of associated GameObject remains vertical</span></span>

<span data-ttu-id="fb52b-446">**Pulsanti**</span><span class="sxs-lookup"><span data-stu-id="fb52b-446">**Buttons**</span></span>

- <span data-ttu-id="fb52b-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) ora ha `DistanceSpaceMode` la proprietà impostata `Local` su come predefinita.</span><span class="sxs-lookup"><span data-stu-id="fb52b-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) now has `DistanceSpaceMode` property set to `Local` as default.</span></span> <span data-ttu-id="fb52b-448">In questo modo i pulsanti possono essere ridimensionati mentre sono ancora a pressione</span><span class="sxs-lookup"><span data-stu-id="fb52b-448">This allows buttons to be scaled while still be pressable</span></span>

<span data-ttu-id="fb52b-449">**Sfera di ritaglio**</span><span class="sxs-lookup"><span data-stu-id="fb52b-449">**Clipping Sphere**</span></span>

<span data-ttu-id="fb52b-450">L'interfaccia ClippingSphere è stata modificata per rispecchiare le API presenti in ClippingBox e ClippingPlane.</span><span class="sxs-lookup"><span data-stu-id="fb52b-450">The ClippingSphere interface has changed to mirror the APIs found in the ClippingBox and ClippingPlane.</span></span>

<span data-ttu-id="fb52b-451">La proprietà Radius di ClippingSphere viene ora calcolata in modo implicito in base alla scala della trasformazione.</span><span class="sxs-lookup"><span data-stu-id="fb52b-451">The ClippingSphere's Radius property is now implicitly calculated based on the transform scale.</span></span> <span data-ttu-id="fb52b-452">Prima che gli sviluppatori devono specificare il raggio di ClippingSphere nel controllo.</span><span class="sxs-lookup"><span data-stu-id="fb52b-452">Before developers would have to specify the radius of the ClippingSphere in the inspector.</span></span> <span data-ttu-id="fb52b-453">Se si vuole modificare il raggio, è sufficiente aggiornare la scala di trasformazione della trasformazione come di consueto.</span><span class="sxs-lookup"><span data-stu-id="fb52b-453">If you want to change the radius, just update the transform scale of the transform as you normally would.</span></span>

<span data-ttu-id="fb52b-454">**NearInteractionTouchable e PokePointer**</span><span class="sxs-lookup"><span data-stu-id="fb52b-454">**NearInteractionTouchable and PokePointer**</span></span>

- <span data-ttu-id="fb52b-455">NearInteractionTouchable non gestisce più il tocco dell'area di disegno dell'interfaccia utente di Unity.</span><span class="sxs-lookup"><span data-stu-id="fb52b-455">NearInteractionTouchable does not handle Unity UI canvas touching any longer.</span></span> <span data-ttu-id="fb52b-456">La classe NearInteractionTouchableUnityUI deve essere ora usata per i touchable dell'interfaccia utente di Unity.</span><span class="sxs-lookup"><span data-stu-id="fb52b-456">The NearInteractionTouchableUnityUI class must be used for Unity UI touchables now.</span></span>
- <span data-ttu-id="fb52b-457">ColliderNearInteractionTouchable è la nuova classe di base per i collisori touchable, ad eccezione di NearInteractionTouchableUnityUI.</span><span class="sxs-lookup"><span data-stu-id="fb52b-457">ColliderNearInteractionTouchable is the new base class for touchables based on colliders, i.e. every touchable except NearInteractionTouchableUnityUI.</span></span>
- <span data-ttu-id="fb52b-458">BaseNearInteractionTouchable.DistFront è stato spostato e rinominato in PokePointer.TouchableDistance Si tratta della distanza e della quale PokePointer può interagire con i dispositivi toccabili.</span><span class="sxs-lookup"><span data-stu-id="fb52b-458">BaseNearInteractionTouchable.DistFront has been moved and renamed to PokePointer.TouchableDistance This is the distance and which the PokePointer can interact with touchables.</span></span> <span data-ttu-id="fb52b-459">In precedenza ogni toccabile aveva la propria distanza massima di interazione, ma ora è definita in PokePointer, che consente una migliore ottimizzazione.</span><span class="sxs-lookup"><span data-stu-id="fb52b-459">Previously each touchable had its own maximum interaction distance, but now this is defined in the PokePointer which allows better optimization.</span></span>
- <span data-ttu-id="fb52b-460">BaseNearInteractionTouchable.DistBack è stato rinominato in PokeThreshold. In questo modo è chiaro che PokeThreshold è la controparte di DebounceThreshold.</span><span class="sxs-lookup"><span data-stu-id="fb52b-460">BaseNearInteractionTouchable.DistBack has been renamed to PokeThreshold This makes it clear that PokeThreshold is the counterpart to DebounceThreshold.</span></span> <span data-ttu-id="fb52b-461">Un oggetto toccabile viene attivato quando PokeThreshold viene incrociato e rilasciato quando DebounceThreshold viene incrociato.</span><span class="sxs-lookup"><span data-stu-id="fb52b-461">A touchable is activated when the PokeThreshold is crossed, and released when DebounceThreshold is crossed.</span></span>

<span data-ttu-id="fb52b-462">**ReadOnlyAttribute**</span><span class="sxs-lookup"><span data-stu-id="fb52b-462">**ReadOnlyAttribute**</span></span>

<span data-ttu-id="fb52b-463">Lo `Microsoft.MixedReality.Toolkit` spazio dei nomi è stato aggiunto a , e `ReadOnlyAttribute` `BeginReadOnlyGroupAttribute` `EndReadOnlyGroupAttribute` .</span><span class="sxs-lookup"><span data-stu-id="fb52b-463">The `Microsoft.MixedReality.Toolkit` namespace has been added to `ReadOnlyAttribute`, `BeginReadOnlyGroupAttribute`, and `EndReadOnlyGroupAttribute`.</span></span>

<span data-ttu-id="fb52b-464">**PointerClickHandler**</span><span class="sxs-lookup"><span data-stu-id="fb52b-464">**PointerClickHandler**</span></span>

<span data-ttu-id="fb52b-465">La classe `PointerClickHandler` è stata deprecata.</span><span class="sxs-lookup"><span data-stu-id="fb52b-465">The `PointerClickHandler` class has been deprecated.</span></span> <span data-ttu-id="fb52b-466">`PointerHandler`L'oggetto deve essere invece usato e fornisce la stessa funzionalità.</span><span class="sxs-lookup"><span data-stu-id="fb52b-466">The `PointerHandler` should be used instead, it provides the same functionality.</span></span>

<span data-ttu-id="fb52b-467">**Supporto del clicker HoloLens**</span><span class="sxs-lookup"><span data-stu-id="fb52b-467">**HoloLens clicker support**</span></span>

<span data-ttu-id="fb52b-468">I mapping del controller del clicker HoloLens sono stati modificati da non mano a non [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) mano. [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand)</span><span class="sxs-lookup"><span data-stu-id="fb52b-468">The HoloLens clicker's controller mappings have changed from being an unhanded [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) to being an unhanded [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand).</span></span> <span data-ttu-id="fb52b-469">A tale scopo, un programma di aggiornamento automatico verrà eseguito la prima volta che si apre il profilo ControllerMapping.</span><span class="sxs-lookup"><span data-stu-id="fb52b-469">To account for this, an automatic updater will run the first time you open your ControllerMapping profile.</span></span> <span data-ttu-id="fb52b-470">Aprire i profili personalizzati almeno una volta dopo l'aggiornamento alla versione 2.0.0 per attivare questo passaggio di migrazione una sola volta.</span><span class="sxs-lookup"><span data-stu-id="fb52b-470">Please open any custom profiles at least once after upgrading to 2.0.0 in order to trigger this one-time migration step.</span></span>

<span data-ttu-id="fb52b-471">**InteractableHighlight**</span><span class="sxs-lookup"><span data-stu-id="fb52b-471">**InteractableHighlight**</span></span>

<span data-ttu-id="fb52b-472">La classe `InteractableHighlight` è stata deprecata.</span><span class="sxs-lookup"><span data-stu-id="fb52b-472">The `InteractableHighlight` class has been deprecated.</span></span> <span data-ttu-id="fb52b-473">In `InteractableOnFocus` alternativa, `FocusInteractableStates` è necessario usare la classe e l'asset.</span><span class="sxs-lookup"><span data-stu-id="fb52b-473">The `InteractableOnFocus` class and `FocusInteractableStates` asset should be used instead.</span></span> <span data-ttu-id="fb52b-474">Per creare un nuovo asset per , fare clic con il pulsante destro del mouse nella finestra `Theme` del progetto e scegliere Crea `InteractableOnFocus` *tema*  >  interagiscibile di Mixed Reality  >    >  Toolkit.</span><span class="sxs-lookup"><span data-stu-id="fb52b-474">To create a new `Theme` asset for the `InteractableOnFocus`, right click in the project window and select *Create* > *Mixed Reality Toolkit* > *Interactable* > *Theme*.</span></span>

<span data-ttu-id="fb52b-475">**HandInteractionPanZoom**</span><span class="sxs-lookup"><span data-stu-id="fb52b-475">**HandInteractionPanZoom**</span></span>

<span data-ttu-id="fb52b-476">`HandInteractionPanZoom` è stato spostato nello spazio dei nomi dell'interfaccia utente perché non era un componente di input.</span><span class="sxs-lookup"><span data-stu-id="fb52b-476">`HandInteractionPanZoom` has been moved to the UI namespace as it was not an input component.</span></span> <span data-ttu-id="fb52b-477">`HandPanEventData` è stato anche spostato in questo spazio dei nomi e semplificato in modo da corrispondere ad altri dati dell'evento dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="fb52b-477">`HandPanEventData` has also been moved into this namespace, and simplified to correspond with other UI event data.</span></span>

### <a name="assembly-name-changes-in-200"></a><span data-ttu-id="fb52b-478">Modifiche al nome dell'assembly nella versione 2.0.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-478">Assembly name changes in 2.0.0</span></span>

<span data-ttu-id="fb52b-479">Nella versione 2.0.0 tutti i nomi di assembly ufficiali di Mixed Reality Toolkit e i relativi file di definizione dell'assembly (asmdef) associati sono stati aggiornati in base al modello seguente.</span><span class="sxs-lookup"><span data-stu-id="fb52b-479">In The 2.0.0 release, all of the official Mixed Reality Toolkit assembly names and their associated assembly definition (.asmdef) files have been updated to fit the following pattern.</span></span>

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

<span data-ttu-id="fb52b-480">In alcuni casi, sono stati uniti più assembly per creare una migliore unità del contenuto.</span><span class="sxs-lookup"><span data-stu-id="fb52b-480">In some instances, multiple assemblies have been merged to create better unity of their contents.</span></span> <span data-ttu-id="fb52b-481">Se il progetto usa file asmdef personalizzati, potrebbe essere necessario aggiornarsi.</span><span class="sxs-lookup"><span data-stu-id="fb52b-481">If your project uses custom .asmdef files, they may require updating.</span></span>

<span data-ttu-id="fb52b-482">Le tabelle seguenti descrivono il mapping dei nomi di file con estensione asmdef RC2 alla versione 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="fb52b-482">The following tables describe how the RC2 .asmdef file names map to the 2.0.0 release.</span></span> <span data-ttu-id="fb52b-483">Tutti i nomi degli assembly corrispondono al nome del file asmdef.</span><span class="sxs-lookup"><span data-stu-id="fb52b-483">All assembly names match the .asmdef file name.</span></span>

<span data-ttu-id="fb52b-484">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="fb52b-484">**MixedRealityToolkit**</span></span>

| <span data-ttu-id="fb52b-485">RC2</span><span class="sxs-lookup"><span data-stu-id="fb52b-485">RC2</span></span> | <span data-ttu-id="fb52b-486">2.0.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-486">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="fb52b-487">MixedRealityToolkit.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-487">MixedRealityToolkit.asmdef</span></span> | <span data-ttu-id="fb52b-488">Microsoft.MixedReality.Toolkit.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-488">Microsoft.MixedReality.Toolkit.asmdef</span></span> |
| <span data-ttu-id="fb52b-489">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-489">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span></span> | <span data-ttu-id="fb52b-490">Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-490">Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef</span></span> |
| <span data-ttu-id="fb52b-491">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-491">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="fb52b-492">Rimosso, usare Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-492">Removed, use Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="fb52b-493">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-493">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span></span> | <span data-ttu-id="fb52b-494">Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-494">Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef</span></span>
| <span data-ttu-id="fb52b-495">MixedRealityToolkit.Core.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-495">MixedRealityToolkit.Core.Inspectors.asmdef</span></span> | <span data-ttu-id="fb52b-496">Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-496">Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef</span></span> |
| <span data-ttu-id="fb52b-497">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-497">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span></span> | <span data-ttu-id="fb52b-498">Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-498">Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef</span></span> |
| <span data-ttu-id="fb52b-499">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-499">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span></span> | <span data-ttu-id="fb52b-500">Microsoft.MixedReality.Toolkit.Async.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-500">Microsoft.MixedReality.Toolkit.Async.asmdef</span></span> |
| <span data-ttu-id="fb52b-501">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-501">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="fb52b-502">Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-502">Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="fb52b-503">MixedRealityToolkit.Utilities.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-503">MixedRealityToolkit.Utilities.Gltf.asmdef</span></span> | <span data-ttu-id="fb52b-504">Microsoft.MixedReality.Toolkit.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-504">Microsoft.MixedReality.Toolkit.Gltf.asmdef</span></span> |
| <span data-ttu-id="fb52b-505">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-505">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span></span> | <span data-ttu-id="fb52b-506">Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-506">Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef</span></span> |

<span data-ttu-id="fb52b-507">**MixedRealityToolkit.Providers**</span><span class="sxs-lookup"><span data-stu-id="fb52b-507">**MixedRealityToolkit.Providers**</span></span>

| <span data-ttu-id="fb52b-508">RC2</span><span class="sxs-lookup"><span data-stu-id="fb52b-508">RC2</span></span> | <span data-ttu-id="fb52b-509">2.0.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-509">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="fb52b-510">MixedRealityToolkit.Providers.OpenVR.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-510">MixedRealityToolkit.Providers.OpenVR.asmdef</span></span> | <span data-ttu-id="fb52b-511">Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-511">Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef</span></span> |
| <span data-ttu-id="fb52b-512">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-512">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span></span> | <span data-ttu-id="fb52b-513">Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-513">Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef</span></span> |
| <span data-ttu-id="fb52b-514">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-514">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span></span> | <span data-ttu-id="fb52b-515">Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-515">Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef</span></span> |

<span data-ttu-id="fb52b-516">**MixedRealityToolkit.Services**</span><span class="sxs-lookup"><span data-stu-id="fb52b-516">**MixedRealityToolkit.Services**</span></span>

| <span data-ttu-id="fb52b-517">RC2</span><span class="sxs-lookup"><span data-stu-id="fb52b-517">RC2</span></span> | <span data-ttu-id="fb52b-518">2.0.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-518">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="fb52b-519">MixedRealityToolkit.Services.BoundarySystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-519">MixedRealityToolkit.Services.BoundarySystem.asmdef</span></span> | <span data-ttu-id="fb52b-520">Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-520">Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef</span></span> |
| <span data-ttu-id="fb52b-521">MixedRealityToolkit.Services.CameraSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-521">MixedRealityToolkit.Services.CameraSystem.asmdef</span></span> | <span data-ttu-id="fb52b-522">Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-522">Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef</span></span> |
| <span data-ttu-id="fb52b-523">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-523">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span></span> | <span data-ttu-id="fb52b-524">Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-524">Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef</span></span> |
| <span data-ttu-id="fb52b-525">MixedRealityToolkit.Services.InputSimulation.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-525">MixedRealityToolkit.Services.InputSimulation.asmdef</span></span> | <span data-ttu-id="fb52b-526">Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-526">Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef</span></span> |
| <span data-ttu-id="fb52b-527">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-527">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span></span> | <span data-ttu-id="fb52b-528">Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-528">Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef</span></span> |
| <span data-ttu-id="fb52b-529">MixedRealityToolkit.Services.InputSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-529">MixedRealityToolkit.Services.InputSystem.asmdef</span></span> | <span data-ttu-id="fb52b-530">Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-530">Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef</span></span> |
| <span data-ttu-id="fb52b-531">MixedRealityToolkit.Services.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-531">MixedRealityToolkit.Services.Inspectors.asmdef</span></span> | <span data-ttu-id="fb52b-532">Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-532">Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef</span></span> |
| <span data-ttu-id="fb52b-533">MixedRealityToolkit.Services.SceneSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-533">MixedRealityToolkit.Services.SceneSystem.asmdef</span></span> | <span data-ttu-id="fb52b-534">Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-534">Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef</span></span> |
| <span data-ttu-id="fb52b-535">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-535">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span></span> | <span data-ttu-id="fb52b-536">Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-536">Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef</span></span> |
| <span data-ttu-id="fb52b-537">MixedRealityToolkit.Services.TeleportSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-537">MixedRealityToolkit.Services.TeleportSystem.asmdef</span></span> | <span data-ttu-id="fb52b-538">Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-538">Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef</span></span> |

<span data-ttu-id="fb52b-539">**MixedRealityToolkit.SDK**</span><span class="sxs-lookup"><span data-stu-id="fb52b-539">**MixedRealityToolkit.SDK**</span></span>

| <span data-ttu-id="fb52b-540">RC2</span><span class="sxs-lookup"><span data-stu-id="fb52b-540">RC2</span></span> | <span data-ttu-id="fb52b-541">2.0.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-541">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="fb52b-542">MixedRealityToolkit.SDK.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-542">MixedRealityToolkit.SDK.asmdef</span></span> | <span data-ttu-id="fb52b-543">Microsoft.MixedReality.Toolkit.SDK.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-543">Microsoft.MixedReality.Toolkit.SDK.asmdef</span></span> |
| <span data-ttu-id="fb52b-544">MixedRealityToolkit.SDK.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-544">MixedRealityToolkit.SDK.Inspectors.asmdef</span></span> | <span data-ttu-id="fb52b-545">Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-545">Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef</span></span> |

<span data-ttu-id="fb52b-546">**MixedRealityToolkit.Examples**</span><span class="sxs-lookup"><span data-stu-id="fb52b-546">**MixedRealityToolkit.Examples**</span></span>

| <span data-ttu-id="fb52b-547">RC2</span><span class="sxs-lookup"><span data-stu-id="fb52b-547">RC2</span></span> | <span data-ttu-id="fb52b-548">2.0.0</span><span class="sxs-lookup"><span data-stu-id="fb52b-548">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="fb52b-549">MixedRealityToolkit.Examples.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-549">MixedRealityToolkit.Examples.asmdef</span></span> | <span data-ttu-id="fb52b-550">Microsoft.MixedReality.Toolkit.Examples.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-550">Microsoft.MixedReality.Toolkit.Examples.asmdef</span></span> |
| <span data-ttu-id="fb52b-551">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-551">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span></span> | <span data-ttu-id="fb52b-552">Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-552">Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef</span></span> |
| <span data-ttu-id="fb52b-553">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-553">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span></span> | <span data-ttu-id="fb52b-554">Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-554">Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef</span></span> |
| <span data-ttu-id="fb52b-555">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-555">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span></span> | <span data-ttu-id="fb52b-556">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-556">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef</span></span> |
| <span data-ttu-id="fb52b-557">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-557">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span></span> | <span data-ttu-id="fb52b-558">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-558">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef</span></span> |
| <span data-ttu-id="fb52b-559">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-559">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span></span> | <span data-ttu-id="fb52b-560">Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef</span><span class="sxs-lookup"><span data-stu-id="fb52b-560">Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef</span></span> |