---
title: Strumento per la funzionalità di realtà mista
description: Informazioni sulle nozioni di base dello strumento per la funzionalità MR per lo sviluppo di HoloLens e VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 0aad81ddd625467dd9159232d590b1a4bf68d06b
ms.sourcegitcommit: d9f87635c87627adba7db37834e4627c149f9a28
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/05/2021
ms.locfileid: "99570254"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="1f8ff-104">Strumento per la funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="1f8ff-104">Welcome to the Mixed Reality Feature Tool</span></span>

![Immagine del banner dello strumento della funzionalità di realtà mista](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="1f8ff-106">Lo strumento per la funzionalità di realtà mista è disponibile solo per Unity al momento.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="1f8ff-107">Se si sta sviluppando in Unreal, fare riferimento alla documentazione di [installazione degli strumenti](../install-the-tools.md) .</span><span class="sxs-lookup"><span data-stu-id="1f8ff-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="1f8ff-108">Lo strumento per la funzionalità di realtà mista è un nuovo modo per gli sviluppatori di individuare, aggiornare e aggiungere pacchetti di funzionalità di realtà mista in progetti Unity.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="1f8ff-109">È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="1f8ff-110">Se non si è mai usato un file manifesto prima, si tratta di un file JSON contenente tutti i pacchetti di progetti.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="1f8ff-111">Dopo aver convalidato i pacchetti desiderati, lo strumento per la funzionalità di realtà mista li scaricherà nel progetto di propria scelta.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="1f8ff-112">Requisiti di sistema</span><span class="sxs-lookup"><span data-stu-id="1f8ff-112">System requirements</span></span>

<span data-ttu-id="1f8ff-113">Prima di poter eseguire lo strumento per la funzionalità di realtà mista, è necessario:</span><span class="sxs-lookup"><span data-stu-id="1f8ff-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="1f8ff-114">Runtime .NET 5,0</span><span class="sxs-lookup"><span data-stu-id="1f8ff-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="1f8ff-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="1f8ff-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="1f8ff-116">Lo strumento per le funzionalità di realtà mista attualmente viene eseguito solo in Windows, ma il supporto MacOS sarà presto disponibile.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

## <a name="download"></a><span data-ttu-id="1f8ff-117">Scarica</span><span class="sxs-lookup"><span data-stu-id="1f8ff-117">Download</span></span> 

<span data-ttu-id="1f8ff-118">Dopo aver configurato l'ambiente:</span><span class="sxs-lookup"><span data-stu-id="1f8ff-118">Once you have your environment set up:</span></span>

* <span data-ttu-id="1f8ff-119">[Scaricare la versione più recente dello strumento per le funzionalità di realtà mista](https://aka.ms/MRFeatureTool) dall'area download Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-119">[Download the latest version of the Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) from the Microsoft Download Center.</span></span>
* <span data-ttu-id="1f8ff-120">Al termine del download, decomprimere il file e salvarlo sul desktop</span><span class="sxs-lookup"><span data-stu-id="1f8ff-120">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="1f8ff-121">Si consiglia di creare un collegamento al file eseguibile per un accesso più rapido</span><span class="sxs-lookup"><span data-stu-id="1f8ff-121">We recommend creating a shortcut to the executable file for faster access</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="1f8ff-122">1. Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="1f8ff-122">1. Getting started</span></span>

<span data-ttu-id="1f8ff-123">Avviare lo strumento della funzionalità di realtà mista dal file eseguibile, che visualizza la pagina iniziale al primo avvio:</span><span class="sxs-lookup"><span data-stu-id="1f8ff-123">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![Guida introduttiva](images/FeatureToolStart.png)

<span data-ttu-id="1f8ff-125">Dalla pagina iniziale è possibile:</span><span class="sxs-lookup"><span data-stu-id="1f8ff-125">From the start page, you can:</span></span>

* <span data-ttu-id="1f8ff-126">[Configurare](configuring-feature-tool.md) le impostazioni dello strumento usando il pulsante dell' **icona dell'ingranaggio**</span><span class="sxs-lookup"><span data-stu-id="1f8ff-126">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="1f8ff-127">Usare il pulsante **punto interrogativo** per avviare il Web browser predefinito e visualizzare la documentazione</span><span class="sxs-lookup"><span data-stu-id="1f8ff-127">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="1f8ff-128">Selezionare **inizia** per iniziare a individuare i pacchetti di funzionalità</span><span class="sxs-lookup"><span data-stu-id="1f8ff-128">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="1f8ff-129">2. individuazione e acquisizione dei pacchetti di funzionalità</span><span class="sxs-lookup"><span data-stu-id="1f8ff-129">2. Discovering and acquiring feature packages</span></span>

<span data-ttu-id="1f8ff-130">Il catalogo dei pacchetti di funzionalità viene recuperato non appena si preme Avvia.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-130">The feature package catalog is retrieved as soon as you press Start.</span></span> <span data-ttu-id="1f8ff-131">Le funzionalità sono raggruppate per categoria per semplificare la ricerca.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-131">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="1f8ff-132">Ad esempio, la categoria del **Toolkit di realtà mista** offre diverse funzionalità per scegliere:</span><span class="sxs-lookup"><span data-stu-id="1f8ff-132">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![Individuazione e acquisizione](images/FeatureToolDiscovery.png)

<span data-ttu-id="1f8ff-134">Una volta effettuate le scelte, selezionare **Recupera funzionalità** per recuperare tutti i pacchetti necessari dal catalogo.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-134">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="1f8ff-135">Per ulteriori informazioni, vedere [individuazione e acquisizione di funzionalità](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="1f8ff-135">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="3-importing-feature-packages"></a><span data-ttu-id="1f8ff-136">3. importazione di pacchetti di funzionalità</span><span class="sxs-lookup"><span data-stu-id="1f8ff-136">3. Importing feature packages</span></span>

<span data-ttu-id="1f8ff-137">Dopo l'acquisizione viene presentato il set completo di pacchetti, insieme a un elenco di dipendenze obbligatorie.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-137">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="1f8ff-138">Se è necessario modificare le selezioni delle funzionalità o dei pacchetti, questo è il momento:</span><span class="sxs-lookup"><span data-stu-id="1f8ff-138">If you need to change any feature or package selections, this is the time:</span></span>

![Importazione di pacchetti](images/FeatureToolImport.png)

<span data-ttu-id="1f8ff-140">Si consiglia vivamente di usare il pulsante **Validate** per assicurarsi che il progetto Unity possa importare correttamente le funzionalità selezionate.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-140">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="1f8ff-141">Dopo la convalida, verrà visualizzata una finestra di dialogo popup con un messaggio di operazione completata o un elenco di problemi identificati.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-141">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="1f8ff-142">Prima di importare, è anche necessario impostare il percorso del progetto Unity di destinazione.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-142">You also need to set the location of the target Unity project before you import.</span></span> <span data-ttu-id="1f8ff-143">Utilizzare il pulsante con i **puntini** di sospensione a sinistra del campo percorso progetto per sfogliare.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-143">Use the **ellipsis** button to the left of the project path field to browse.</span></span> <span data-ttu-id="1f8ff-144">Al termine dell'esplorazione della file system, aprire la cartella che contiene il progetto Unity di destinazione.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-144">When you're done navigating your file system, open the folder containing your target Unity project.</span></span>

> [!NOTE]
> <span data-ttu-id="1f8ff-145">La finestra di dialogo visualizzata quando si Esplora la cartella del progetto Unity contiene ' _' come nome file.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-145">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="1f8ff-146">Per abilitare la selezione della cartella, è necessario specificare un valore per il nome del file.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-146">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="1f8ff-147">Selezionare **Importa** per continuare.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-147">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="1f8ff-148">Dopo aver fatto clic sul pulsante **Importa** , se eventuali problemi rimangono, verrà visualizzato un messaggio semplice.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-148">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="1f8ff-149">È consigliabile fare clic su No e utilizzare il pulsante **Validate** per visualizzare e risolvere i problemi.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-149">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="1f8ff-150">Per ulteriori informazioni, vedere [importazione di funzionalità](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="1f8ff-150">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="4-reviewing-and-approving-project-changes"></a><span data-ttu-id="1f8ff-151">4. Revisione e approvazione delle modifiche del progetto</span><span class="sxs-lookup"><span data-stu-id="1f8ff-151">4. Reviewing and approving project changes</span></span>

<span data-ttu-id="1f8ff-152">Il passaggio finale consiste nell'esaminare e approvare le modifiche proposte al manifesto e ai file di progetto:</span><span class="sxs-lookup"><span data-stu-id="1f8ff-152">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="1f8ff-153">Le modifiche proposte al manifesto vengono visualizzate a sinistra</span><span class="sxs-lookup"><span data-stu-id="1f8ff-153">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="1f8ff-154">I file da aggiungere al progetto sono elencati a destra</span><span class="sxs-lookup"><span data-stu-id="1f8ff-154">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="1f8ff-155">Il pulsante **Confronta** consente di visualizzare side-by-side del manifesto corrente e delle modifiche proposte</span><span class="sxs-lookup"><span data-stu-id="1f8ff-155">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![Autorizzazione](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="1f8ff-157">Per ulteriori informazioni, vedere [revisione e approvazione delle modifiche del progetto](reviewing-changes.md).</span><span class="sxs-lookup"><span data-stu-id="1f8ff-157">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="5-project-updated"></a><span data-ttu-id="1f8ff-158">5. progetto aggiornato</span><span class="sxs-lookup"><span data-stu-id="1f8ff-158">5. Project updated</span></span>

<span data-ttu-id="1f8ff-159">Quando vengono approvate le modifiche proposte, il progetto Unity di destinazione viene aggiornato in modo da fare riferimento alle funzionalità di realtà mista selezionate:</span><span class="sxs-lookup"><span data-stu-id="1f8ff-159">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features:</span></span>

![Progetto aggiornato](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="1f8ff-161">La cartella **packages** del progetto Unity dispone ora di una sottocartella **MixedReality** con i file del pacchetto di funzionalità e il manifesto conterrà i riferimenti appropriati.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-161">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="1f8ff-162">Tornare a Unity, attendere il caricamento delle nuove funzionalità selezionate e iniziare la compilazione.</span><span class="sxs-lookup"><span data-stu-id="1f8ff-162">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="1f8ff-163">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="1f8ff-163">See also</span></span>

- [<span data-ttu-id="1f8ff-164">Configurazione dello strumento funzionalità</span><span class="sxs-lookup"><span data-stu-id="1f8ff-164">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="1f8ff-165">Individuazione e acquisizione</span><span class="sxs-lookup"><span data-stu-id="1f8ff-165">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="1f8ff-166">Visualizzazione dei dettagli del pacchetto di funzionalità</span><span class="sxs-lookup"><span data-stu-id="1f8ff-166">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="1f8ff-167">Importazione dei pacchetti selezionati</span><span class="sxs-lookup"><span data-stu-id="1f8ff-167">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="1f8ff-168">Revisione e approvazione delle modifiche del progetto</span><span class="sxs-lookup"><span data-stu-id="1f8ff-168">Reviewing and approving project modifications</span></span>](reviewing-changes.md)
