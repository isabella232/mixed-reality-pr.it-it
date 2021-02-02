---
title: Strumento per la funzionalità di realtà mista
description: Informazioni sulle nozioni di base dello strumento per la funzionalità MR per lo sviluppo di HoloLens e VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: b9d54edb251cfe22d4f5fbea6fa8c923f6ff2d69
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244610"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="ccfe6-104">Strumento per la funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="ccfe6-104">Welcome to the Mixed Reality Feature Tool</span></span>

![Immagine del banner dello strumento della funzionalità di realtà mista](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="ccfe6-106">Lo strumento per la funzionalità di realtà mista è disponibile solo per Unity al momento.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="ccfe6-107">Se si sta sviluppando in Unreal, fare riferimento alla documentazione di [installazione degli strumenti](../install-the-tools.md) .</span><span class="sxs-lookup"><span data-stu-id="ccfe6-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="ccfe6-108">Lo strumento per la funzionalità di realtà mista è un nuovo modo per gli sviluppatori di individuare, aggiornare e aggiungere pacchetti di funzionalità di realtà mista in progetti Unity.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="ccfe6-109">È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="ccfe6-110">Se non si è mai usato un file manifesto prima, si tratta di un file JSON contenente tutti i pacchetti di progetti.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="ccfe6-111">Dopo aver convalidato i pacchetti desiderati, lo strumento per la funzionalità di realtà mista li scaricherà nel progetto di propria scelta.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="ccfe6-112">Requisiti di sistema</span><span class="sxs-lookup"><span data-stu-id="ccfe6-112">System requirements</span></span>

<span data-ttu-id="ccfe6-113">Prima di poter eseguire lo strumento per la funzionalità di realtà mista, è necessario:</span><span class="sxs-lookup"><span data-stu-id="ccfe6-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="ccfe6-114">Runtime .NET 5,0</span><span class="sxs-lookup"><span data-stu-id="ccfe6-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="ccfe6-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="ccfe6-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="ccfe6-116">Lo strumento per le funzionalità di realtà mista attualmente viene eseguito solo in Windows, ma il supporto MacOS sarà presto disponibile.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

<span data-ttu-id="ccfe6-117">Dopo aver configurato l'ambiente:</span><span class="sxs-lookup"><span data-stu-id="ccfe6-117">Once you have your environment set up:</span></span>

* <span data-ttu-id="ccfe6-118">Scaricare la versione più recente dello strumento per le funzionalità di realtà mista dall' [area download Microsoft](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="ccfe6-118">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool).</span></span>
* <span data-ttu-id="ccfe6-119">Al termine del download, decomprimere il file e salvarlo sul desktop</span><span class="sxs-lookup"><span data-stu-id="ccfe6-119">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="ccfe6-120">Si consiglia di creare un collegamento al file eseguibile per un accesso più rapido</span><span class="sxs-lookup"><span data-stu-id="ccfe6-120">We recommend creating a shortcut to the executable file for faster access</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="ccfe6-121">1. Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="ccfe6-121">1. Getting started</span></span>

<span data-ttu-id="ccfe6-122">Avviare lo strumento della funzionalità di realtà mista dal file eseguibile, che visualizza la pagina iniziale al primo avvio:</span><span class="sxs-lookup"><span data-stu-id="ccfe6-122">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![Guida introduttiva](images/FeatureToolStart.png)

<span data-ttu-id="ccfe6-124">Dalla pagina iniziale è possibile:</span><span class="sxs-lookup"><span data-stu-id="ccfe6-124">From the start page, you can:</span></span>

* <span data-ttu-id="ccfe6-125">[Configurare](configuring-feature-tool.md) le impostazioni dello strumento usando il pulsante dell' **icona dell'ingranaggio**</span><span class="sxs-lookup"><span data-stu-id="ccfe6-125">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="ccfe6-126">Usare il pulsante **punto interrogativo** per avviare il Web browser predefinito e visualizzare la documentazione</span><span class="sxs-lookup"><span data-stu-id="ccfe6-126">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="ccfe6-127">Selezionare **inizia** per iniziare a individuare i pacchetti di funzionalità</span><span class="sxs-lookup"><span data-stu-id="ccfe6-127">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="ccfe6-128">2. individuazione e acquisizione dei pacchetti di funzionalità</span><span class="sxs-lookup"><span data-stu-id="ccfe6-128">2. Discovering and acquiring feature packages</span></span>

<span data-ttu-id="ccfe6-129">Il catalogo dei pacchetti di funzionalità viene recuperato non appena si preme Avvia.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-129">The feature package catalog is retrieved as soon as you press Start.</span></span> <span data-ttu-id="ccfe6-130">Le funzionalità sono raggruppate per categoria per semplificare la ricerca.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-130">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="ccfe6-131">Ad esempio, la categoria del **Toolkit di realtà mista** offre diverse funzionalità per scegliere:</span><span class="sxs-lookup"><span data-stu-id="ccfe6-131">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![Individuazione e acquisizione](images/FeatureToolDiscovery.png)

<span data-ttu-id="ccfe6-133">Una volta effettuate le scelte, selezionare **Recupera funzionalità** per recuperare tutti i pacchetti necessari dal catalogo.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-133">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="ccfe6-134">Per ulteriori informazioni, vedere [individuazione e acquisizione di funzionalità](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="ccfe6-134">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="3-importing-feature-packages"></a><span data-ttu-id="ccfe6-135">3. importazione di pacchetti di funzionalità</span><span class="sxs-lookup"><span data-stu-id="ccfe6-135">3. Importing feature packages</span></span>

<span data-ttu-id="ccfe6-136">Dopo l'acquisizione viene presentato il set completo di pacchetti, insieme a un elenco di dipendenze obbligatorie.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-136">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="ccfe6-137">Se è necessario modificare le selezioni delle funzionalità o dei pacchetti, questo è il momento:</span><span class="sxs-lookup"><span data-stu-id="ccfe6-137">If you need to change any feature or package selections, this is the time:</span></span>

![Importazione di pacchetti](images/FeatureToolImport.png)

<span data-ttu-id="ccfe6-139">Si consiglia vivamente di usare il pulsante **Validate** per assicurarsi che il progetto Unity possa importare correttamente le funzionalità selezionate.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-139">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="ccfe6-140">Dopo la convalida, verrà visualizzata una finestra di dialogo popup con un messaggio di operazione completata o un elenco di problemi identificati.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-140">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="ccfe6-141">Prima di importare, è anche necessario impostare il percorso del progetto Unity di destinazione.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-141">You also need to set the location of the target Unity project before you import.</span></span> <span data-ttu-id="ccfe6-142">Utilizzare il pulsante con i **puntini** di sospensione a sinistra del campo percorso progetto per sfogliare.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-142">Use the **ellipsis** button to the left of the project path field to browse.</span></span> <span data-ttu-id="ccfe6-143">Al termine dell'esplorazione della file system, aprire la cartella che contiene il progetto Unity di destinazione.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-143">When you're done navigating your file system, open the folder containing your target Unity project.</span></span>

> [!NOTE]
> <span data-ttu-id="ccfe6-144">La finestra di dialogo visualizzata quando si Esplora la cartella del progetto Unity contiene ' _' come nome file.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-144">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="ccfe6-145">Per abilitare la selezione della cartella, è necessario specificare un valore per il nome del file.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-145">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="ccfe6-146">Selezionare **Importa** per continuare.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-146">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="ccfe6-147">Dopo aver fatto clic sul pulsante **Importa** , se eventuali problemi rimangono, verrà visualizzato un messaggio semplice.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-147">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="ccfe6-148">È consigliabile fare clic su No e utilizzare il pulsante **Validate** per visualizzare e risolvere i problemi.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-148">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="ccfe6-149">Per ulteriori informazioni, vedere [importazione di funzionalità](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="ccfe6-149">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="4-reviewing-and-approving-project-changes"></a><span data-ttu-id="ccfe6-150">4. Revisione e approvazione delle modifiche del progetto</span><span class="sxs-lookup"><span data-stu-id="ccfe6-150">4. Reviewing and approving project changes</span></span>

<span data-ttu-id="ccfe6-151">Il passaggio finale consiste nell'esaminare e approvare le modifiche proposte al manifesto e ai file di progetto:</span><span class="sxs-lookup"><span data-stu-id="ccfe6-151">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="ccfe6-152">Le modifiche proposte al manifesto vengono visualizzate a sinistra</span><span class="sxs-lookup"><span data-stu-id="ccfe6-152">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="ccfe6-153">I file da aggiungere al progetto sono elencati a destra</span><span class="sxs-lookup"><span data-stu-id="ccfe6-153">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="ccfe6-154">Il pulsante **Confronta** consente di visualizzare side-by-side del manifesto corrente e delle modifiche proposte</span><span class="sxs-lookup"><span data-stu-id="ccfe6-154">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![Autorizzazione](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="ccfe6-156">Per ulteriori informazioni, vedere [revisione e approvazione delle modifiche del progetto](reviewing-changes.md).</span><span class="sxs-lookup"><span data-stu-id="ccfe6-156">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="5-project-updated"></a><span data-ttu-id="ccfe6-157">5. progetto aggiornato</span><span class="sxs-lookup"><span data-stu-id="ccfe6-157">5. Project updated</span></span>

<span data-ttu-id="ccfe6-158">Quando vengono approvate le modifiche proposte, il progetto Unity di destinazione viene aggiornato in modo da fare riferimento alle funzionalità di realtà mista selezionate:</span><span class="sxs-lookup"><span data-stu-id="ccfe6-158">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features:</span></span>

![Progetto aggiornato](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="ccfe6-160">La cartella **packages** del progetto Unity dispone ora di una sottocartella **MixedReality** con i file del pacchetto di funzionalità e il manifesto conterrà i riferimenti appropriati.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-160">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="ccfe6-161">Tornare a Unity, attendere il caricamento delle nuove funzionalità selezionate e iniziare la compilazione.</span><span class="sxs-lookup"><span data-stu-id="ccfe6-161">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="ccfe6-162">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="ccfe6-162">See also</span></span>

- [<span data-ttu-id="ccfe6-163">Configurazione dello strumento funzionalità</span><span class="sxs-lookup"><span data-stu-id="ccfe6-163">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="ccfe6-164">Individuazione e acquisizione</span><span class="sxs-lookup"><span data-stu-id="ccfe6-164">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="ccfe6-165">Visualizzazione dei dettagli del pacchetto di funzionalità</span><span class="sxs-lookup"><span data-stu-id="ccfe6-165">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="ccfe6-166">Importazione dei pacchetti selezionati</span><span class="sxs-lookup"><span data-stu-id="ccfe6-166">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="ccfe6-167">Revisione e approvazione delle modifiche del progetto</span><span class="sxs-lookup"><span data-stu-id="ccfe6-167">Reviewing and approving project modifications</span></span>](reviewing-changes.md)
