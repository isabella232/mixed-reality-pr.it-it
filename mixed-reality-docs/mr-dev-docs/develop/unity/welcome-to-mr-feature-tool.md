---
title: Strumento per la funzionalità di realtà mista
description: Informazioni sulle nozioni di base dello strumento per la funzionalità MR per lo sviluppo di HoloLens e VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 990119b25aeffcb4ce786120659af8f290a6fde2
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550201"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="1a64e-104">Strumento per la funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="1a64e-104">Welcome to the Mixed Reality Feature Tool</span></span>

![Immagine del banner dello strumento della funzionalità di realtà mista](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="1a64e-106">Lo strumento per la funzionalità di realtà mista è disponibile solo per Unity al momento.</span><span class="sxs-lookup"><span data-stu-id="1a64e-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="1a64e-107">Se si sta sviluppando in Unreal, fare riferimento alla documentazione di [installazione degli strumenti](../install-the-tools.md) .</span><span class="sxs-lookup"><span data-stu-id="1a64e-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="1a64e-108">Lo strumento per la funzionalità di realtà mista è un nuovo modo per gli sviluppatori di individuare, aggiornare e aggiungere pacchetti di funzionalità di realtà mista in progetti Unity.</span><span class="sxs-lookup"><span data-stu-id="1a64e-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="1a64e-109">È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="1a64e-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="1a64e-110">Se non si è mai usato un file manifesto prima, si tratta di un file JSON contenente tutti i pacchetti di progetti.</span><span class="sxs-lookup"><span data-stu-id="1a64e-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="1a64e-111">Dopo aver convalidato i pacchetti desiderati, lo strumento per la funzionalità di realtà mista li scaricherà nel progetto di propria scelta.</span><span class="sxs-lookup"><span data-stu-id="1a64e-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="1a64e-112">Requisiti di sistema</span><span class="sxs-lookup"><span data-stu-id="1a64e-112">System requirements</span></span>

<span data-ttu-id="1a64e-113">Prima di poter eseguire lo strumento per la funzionalità di realtà mista, è necessario:</span><span class="sxs-lookup"><span data-stu-id="1a64e-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="1a64e-114">Runtime .NET 5,0</span><span class="sxs-lookup"><span data-stu-id="1a64e-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="1a64e-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="1a64e-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="1a64e-116">Lo strumento per le funzionalità di realtà mista attualmente viene eseguito solo in Windows, ma il supporto MacOS sarà presto disponibile.</span><span class="sxs-lookup"><span data-stu-id="1a64e-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

## <a name="download"></a><span data-ttu-id="1a64e-117">Scarica</span><span class="sxs-lookup"><span data-stu-id="1a64e-117">Download</span></span>

<span data-ttu-id="1a64e-118">Dopo aver configurato l'ambiente:</span><span class="sxs-lookup"><span data-stu-id="1a64e-118">Once you have your environment set up:</span></span>

* <span data-ttu-id="1a64e-119">[Scaricare la versione più recente dello strumento per le funzionalità di realtà mista](https://aka.ms/MRFeatureTool) dall'area download Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1a64e-119">[Download the latest version of the Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) from the Microsoft Download Center.</span></span>
* <span data-ttu-id="1a64e-120">Al termine del download, decomprimere il file e salvarlo sul desktop</span><span class="sxs-lookup"><span data-stu-id="1a64e-120">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="1a64e-121">Si consiglia di creare un collegamento al file eseguibile per un accesso più rapido</span><span class="sxs-lookup"><span data-stu-id="1a64e-121">We recommend creating a shortcut to the executable file for faster access</span></span>

> [!NOTE]
> <span data-ttu-id="1a64e-122">Se non si ha familiarità con l'uso di gestione pacchetti Unity, seguire le [istruzioni di UPM](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).</span><span class="sxs-lookup"><span data-stu-id="1a64e-122">If you're new to using the Unity Package Manager, follow our [UPM instructions](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).</span></span>

## <a name="changes-in-this-release"></a><span data-ttu-id="1a64e-123">Modifiche in questa versione</span><span class="sxs-lookup"><span data-stu-id="1a64e-123">Changes in this release</span></span>

<span data-ttu-id="1a64e-124">La versione beta di 1.0.2103 include le correzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="1a64e-124">Version 1.0.2103 Beta includes the following fixes:</span></span>

* <span data-ttu-id="1a64e-125">Miglioramenti per il download del rilevamento degli errori.</span><span class="sxs-lookup"><span data-stu-id="1a64e-125">Improvements to download error detection.</span></span>
* <span data-ttu-id="1a64e-126">Aggiornamenti sulla modalità di scrittura dei manifesti per evitare errori di aggiornamento corretti.</span><span class="sxs-lookup"><span data-stu-id="1a64e-126">Updates on how manifests are written to avoid failure to update correctly.</span></span>
* <span data-ttu-id="1a64e-127">Escpaing è stato rimosso da percorsi di file nel manifesto del progetto.</span><span class="sxs-lookup"><span data-stu-id="1a64e-127">Escpaing has been removed from file paths in the project manifest.</span></span>

<span data-ttu-id="1a64e-128">In questa versione sono state aggiunte le funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="1a64e-128">The following features have been added in this release:</span></span>

* <span data-ttu-id="1a64e-129">Il catalogo delle funzionalità è ora memorizzato nella cache.</span><span class="sxs-lookup"><span data-stu-id="1a64e-129">The feature catalog is now cached.</span></span> <span data-ttu-id="1a64e-130">Per verificare la disponibilità di nuove funzionalità e aggiornamenti, usare il pulsante Aggiorna nell'individuazione.</span><span class="sxs-lookup"><span data-stu-id="1a64e-130">To check for new features and updates, please use the refresh button in Discovery.</span></span>
* <span data-ttu-id="1a64e-131">Spostare la selezione del progetto dal passaggio importa a prima dell'individuazione.</span><span class="sxs-lookup"><span data-stu-id="1a64e-131">Move project selection from the Import step to before Discovery.</span></span>
* <span data-ttu-id="1a64e-132">I pacchetti disponibili vengono filtrati in base alla versione di Unity specificata dal progetto.</span><span class="sxs-lookup"><span data-stu-id="1a64e-132">Available packages are filtered by the project's specified Unity version.</span></span>
* <span data-ttu-id="1a64e-133">Nella visualizzazione individuazione sono ora visualizzati i pacchetti attualmente installati.</span><span class="sxs-lookup"><span data-stu-id="1a64e-133">The discovery view now displays currently installed packages.</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="1a64e-134">1. Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="1a64e-134">1. Getting started</span></span>

<span data-ttu-id="1a64e-135">Avviare lo strumento della funzionalità di realtà mista dal file eseguibile, che visualizza la pagina iniziale al primo avvio:</span><span class="sxs-lookup"><span data-stu-id="1a64e-135">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![Introduzione](images/FeatureToolStart.png)

<span data-ttu-id="1a64e-137">Dalla pagina iniziale è possibile:</span><span class="sxs-lookup"><span data-stu-id="1a64e-137">From the start page, you can:</span></span>

* <span data-ttu-id="1a64e-138">[Configurare](configuring-feature-tool.md) le impostazioni dello strumento usando il pulsante dell' **icona dell'ingranaggio**</span><span class="sxs-lookup"><span data-stu-id="1a64e-138">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="1a64e-139">Usare il pulsante **punto interrogativo** per avviare il Web browser predefinito e visualizzare la documentazione</span><span class="sxs-lookup"><span data-stu-id="1a64e-139">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="1a64e-140">Selezionare **inizia** per iniziare a individuare i pacchetti di funzionalità</span><span class="sxs-lookup"><span data-stu-id="1a64e-140">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-selecting-your-unity-project"></a><span data-ttu-id="1a64e-141">2. selezione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="1a64e-141">2. Selecting your Unity project</span></span>

<span data-ttu-id="1a64e-142">Per assicurarsi che tutte le funzionalità individuate siano supportate nella versione di Unity del progetto, il primo passaggio consiste nel puntare lo strumento della funzionalità di realtà mista al progetto usando il pulsante con i **puntini** di sospensione (a sinistra del campo percorso progetto).</span><span class="sxs-lookup"><span data-stu-id="1a64e-142">To ensure that all discovered features are supported on your project's version of Unity, the fist step is to point the Mixed Reality Feature Tool to your project using the **ellipsis** button (to the left of the project path field).</span></span>

![Selezionare il progetto Unity](images/FeatureToolSelectUnityProject.png)

> [!NOTE]
> <span data-ttu-id="1a64e-144">La finestra di dialogo visualizzata quando si Esplora la cartella del progetto Unity contiene ' _' come nome file.</span><span class="sxs-lookup"><span data-stu-id="1a64e-144">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="1a64e-145">Per abilitare la selezione della cartella, è necessario specificare un valore per il nome del file.</span><span class="sxs-lookup"><span data-stu-id="1a64e-145">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="1a64e-146">Dopo aver individuato la cartella del progetto, fare clic sul pulsante Apri per tornare allo strumento funzionalità per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="1a64e-146">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1a64e-147">Lo strumento per la funzionalità di realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="1a64e-147">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="1a64e-148">La cartella deve contenere `Assets` le `Packages` cartelle, e `Project Settings` .</span><span class="sxs-lookup"><span data-stu-id="1a64e-148">The folder must contain `Assets`, `Packages` and `Project Settings` folders.</span></span>

## <a name="3-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="1a64e-149">3. individuazione e acquisizione dei pacchetti di funzionalità</span><span class="sxs-lookup"><span data-stu-id="1a64e-149">3. Discovering and acquiring feature packages</span></span>

> [!NOTE]
> <span data-ttu-id="1a64e-150">La versione beta di 1.0.2103 ora memorizza nella cache il contenuto del catalogo funzionalità ogni volta che viene eseguito l'accesso al server.</span><span class="sxs-lookup"><span data-stu-id="1a64e-150">Version 1.0.2103 Beta now caches the feature catalog contents whenever the server is accessed.</span></span> <span data-ttu-id="1a64e-151">Questa modifica consente di accedere rapidamente alle funzionalità disponibili, a scapito della visualizzazione dei dati più recenti assoluti.</span><span class="sxs-lookup"><span data-stu-id="1a64e-151">This change enables fast access to available features, at the expense of displaying the absolute latest data.</span></span> <span data-ttu-id="1a64e-152">Per aggiornare il catalogo, usare il pulsante **Aggiorna** .</span><span class="sxs-lookup"><span data-stu-id="1a64e-152">To update the catalog, please use the **Refresh** button.</span></span>

<span data-ttu-id="1a64e-153">Le funzionalità sono raggruppate per categoria per semplificare la ricerca.</span><span class="sxs-lookup"><span data-stu-id="1a64e-153">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="1a64e-154">Ad esempio, la categoria del **Toolkit di realtà mista** offre diverse funzionalità per scegliere:</span><span class="sxs-lookup"><span data-stu-id="1a64e-154">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![Individuazione e acquisizione](images/FeatureToolDiscovery.png)

<span data-ttu-id="1a64e-156">Quando lo strumento della funzionalità di realtà mista riconosce le funzionalità importate in precedenza, Visualizza un messaggio di notifica per ogni.</span><span class="sxs-lookup"><span data-stu-id="1a64e-156">When the Mixed Reality Feature Tool recognizes previously imported feature(s), it displays a notification message by each.</span></span>

![Notifica della funzionalità importata](images/feature-tool-imported-note.png)


<span data-ttu-id="1a64e-158">Una volta effettuate le scelte, selezionare **Recupera funzionalità** per recuperare tutti i pacchetti necessari dal catalogo.</span><span class="sxs-lookup"><span data-stu-id="1a64e-158">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="1a64e-159">Per ulteriori informazioni, vedere [individuazione e acquisizione di funzionalità](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="1a64e-159">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="4-importing-feature-packages"></a><span data-ttu-id="1a64e-160">4. importazione di pacchetti di funzionalità</span><span class="sxs-lookup"><span data-stu-id="1a64e-160">4. Importing feature packages</span></span>

<span data-ttu-id="1a64e-161">Dopo l'acquisizione viene presentato il set completo di pacchetti, insieme a un elenco di dipendenze obbligatorie.</span><span class="sxs-lookup"><span data-stu-id="1a64e-161">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="1a64e-162">Se è necessario modificare le selezioni delle funzionalità o dei pacchetti, questo è il momento:</span><span class="sxs-lookup"><span data-stu-id="1a64e-162">If you need to change any feature or package selections, this is the time:</span></span>

![Importazione di pacchetti](images/FeatureToolImport.png)

<span data-ttu-id="1a64e-164">Si consiglia vivamente di usare il pulsante **Validate** per assicurarsi che il progetto Unity possa importare correttamente le funzionalità selezionate.</span><span class="sxs-lookup"><span data-stu-id="1a64e-164">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="1a64e-165">Dopo la convalida, verrà visualizzata una finestra di dialogo popup con un messaggio di operazione completata o un elenco di problemi identificati.</span><span class="sxs-lookup"><span data-stu-id="1a64e-165">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="1a64e-166">Selezionare **Importa** per continuare.</span><span class="sxs-lookup"><span data-stu-id="1a64e-166">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="1a64e-167">Dopo aver fatto clic sul pulsante **Importa** , se eventuali problemi rimangono, verrà visualizzato un messaggio semplice.</span><span class="sxs-lookup"><span data-stu-id="1a64e-167">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="1a64e-168">È consigliabile fare clic su No e utilizzare il pulsante **Validate** per visualizzare e risolvere i problemi.</span><span class="sxs-lookup"><span data-stu-id="1a64e-168">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="1a64e-169">Per ulteriori informazioni, vedere [importazione di funzionalità](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="1a64e-169">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="5-reviewing-and-approving-project-changes"></a><span data-ttu-id="1a64e-170">5. Revisione e approvazione delle modifiche del progetto</span><span class="sxs-lookup"><span data-stu-id="1a64e-170">5. Reviewing and approving project changes</span></span>

<span data-ttu-id="1a64e-171">Il passaggio finale consiste nell'esaminare e approvare le modifiche proposte al manifesto e ai file di progetto:</span><span class="sxs-lookup"><span data-stu-id="1a64e-171">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="1a64e-172">Le modifiche proposte al manifesto vengono visualizzate a sinistra</span><span class="sxs-lookup"><span data-stu-id="1a64e-172">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="1a64e-173">I file da aggiungere al progetto sono elencati a destra</span><span class="sxs-lookup"><span data-stu-id="1a64e-173">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="1a64e-174">Il pulsante **Confronta** consente di visualizzare side-by-side del manifesto corrente e delle modifiche proposte</span><span class="sxs-lookup"><span data-stu-id="1a64e-174">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![Autorizzazione](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="1a64e-176">Per ulteriori informazioni, vedere [revisione e approvazione delle modifiche del progetto](reviewing-changes.md).</span><span class="sxs-lookup"><span data-stu-id="1a64e-176">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="6-project-updated"></a><span data-ttu-id="1a64e-177">6. progetto aggiornato</span><span class="sxs-lookup"><span data-stu-id="1a64e-177">6. Project updated</span></span>

<span data-ttu-id="1a64e-178">Quando vengono approvate le modifiche proposte, il progetto Unity di destinazione viene aggiornato in modo da fare riferimento alle funzionalità della realtà mista selezionate.</span><span class="sxs-lookup"><span data-stu-id="1a64e-178">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features.</span></span>

![Progetto aggiornato](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="1a64e-180">La cartella **packages** del progetto Unity dispone ora di una sottocartella **MixedReality** con i file del pacchetto di funzionalità e il manifesto conterrà i riferimenti appropriati.</span><span class="sxs-lookup"><span data-stu-id="1a64e-180">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="1a64e-181">Tornare a Unity, attendere il caricamento delle nuove funzionalità selezionate e iniziare la compilazione.</span><span class="sxs-lookup"><span data-stu-id="1a64e-181">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="1a64e-182">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="1a64e-182">See also</span></span>

- [<span data-ttu-id="1a64e-183">Configurazione dello strumento funzionalità</span><span class="sxs-lookup"><span data-stu-id="1a64e-183">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="1a64e-184">Individuazione e acquisizione</span><span class="sxs-lookup"><span data-stu-id="1a64e-184">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="1a64e-185">Visualizzazione dei dettagli del pacchetto di funzionalità</span><span class="sxs-lookup"><span data-stu-id="1a64e-185">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="1a64e-186">Importazione dei pacchetti selezionati</span><span class="sxs-lookup"><span data-stu-id="1a64e-186">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="1a64e-187">Revisione e approvazione delle modifiche del progetto</span><span class="sxs-lookup"><span data-stu-id="1a64e-187">Reviewing and approving project modifications</span></span>](reviewing-changes.md)