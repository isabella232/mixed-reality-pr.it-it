---
title: Configurazione dello strumento funzionalità realtà mista
description: Informazioni su come scaricare e installare pacchetti Unity di Realtà mista dallo strumento di funzionalità MR per lo sviluppo di HoloLens e VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 5b61924ccf4d3eb5f5433c9042582ff2a850bb04
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2021
ms.locfileid: "107731950"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="174a9-104">Configurazione dello strumento funzionalità realtà mista</span><span class="sxs-lookup"><span data-stu-id="174a9-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="174a9-105">Quando si usa lo strumento funzionalità realtà mista, è possibile accedere a tre diverse categorie di impostazioni che è possibile personalizzare a p pmento:</span><span class="sxs-lookup"><span data-stu-id="174a9-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* [<span data-ttu-id="174a9-106">Scaricare le impostazioni</span><span class="sxs-lookup"><span data-stu-id="174a9-106">Download settings</span></span>](#download-settings)
* [<span data-ttu-id="174a9-107">Impostazioni delle funzionalità</span><span class="sxs-lookup"><span data-stu-id="174a9-107">Feature settings</span></span>](#feature-settings)
* [<span data-ttu-id="174a9-108">Importare impostazioni</span><span class="sxs-lookup"><span data-stu-id="174a9-108">Import settings</span></span>](#import-settings)

## <a name="download-settings"></a><span data-ttu-id="174a9-109">Scaricare le impostazioni</span><span class="sxs-lookup"><span data-stu-id="174a9-109">Download settings</span></span>

![Scaricare le impostazioni](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="174a9-111">Sovrascrivi file di pacchetto esistenti</span><span class="sxs-lookup"><span data-stu-id="174a9-111">Overwrite existing package files</span></span>

<span data-ttu-id="174a9-112">Se si abilita questa impostazione, i file del pacchetto vengono scaricati ogni volta che vengono acquisiti.</span><span class="sxs-lookup"><span data-stu-id="174a9-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 

* <span data-ttu-id="174a9-113">**È consigliabile lasciare disabilitata questa opzione per ridurre l'utilizzo della larghezza di banda di rete**</span><span class="sxs-lookup"><span data-stu-id="174a9-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="174a9-114">Per impostazione predefinita, i file di pacchetto acquisiti in precedenza non vengono scaricati di nuovo</span><span class="sxs-lookup"><span data-stu-id="174a9-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="174a9-115">Cache dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="174a9-115">Package cache</span></span>

<span data-ttu-id="174a9-116">Modificare questa impostazione per aggiornare il percorso in cui vengono scaricati i pacchetti di funzionalità.</span><span class="sxs-lookup"><span data-stu-id="174a9-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="174a9-117">Questa impostazione è **di sola lettura** in questa versione.</span><span class="sxs-lookup"><span data-stu-id="174a9-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="174a9-118">Le versioni future possono rendere configurabile questa impostazione.</span><span class="sxs-lookup"><span data-stu-id="174a9-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="174a9-119">Impostazioni delle funzionalità</span><span class="sxs-lookup"><span data-stu-id="174a9-119">Feature settings</span></span>

![Impostazioni delle funzionalità](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a><span data-ttu-id="174a9-121">Mostra versioni di anteprima</span><span class="sxs-lookup"><span data-stu-id="174a9-121">Show preview releases</span></span>

<span data-ttu-id="174a9-122">Abilitare questa impostazione per acquisire le versioni di anteprima.</span><span class="sxs-lookup"><span data-stu-id="174a9-122">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="174a9-123">Per impostazione predefinita, le versioni di anteprima non vengono visualizzate nello strumento di funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="174a9-123">By default, preview releases are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="174a9-124">Una versione di anteprima è definita come contenente la designazione **"-preview"** nella versione del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="174a9-124">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

### <a name="show-early-access-program-features"></a><span data-ttu-id="174a9-125">Visualizzare le funzionalità del programma ad accesso anticipato</span><span class="sxs-lookup"><span data-stu-id="174a9-125">Show early access program features</span></span>

<span data-ttu-id="174a9-126">Abilitare questa impostazione per acquisire funzionalità dalle versioni dei programmi registrati ad accesso anticipato.</span><span class="sxs-lookup"><span data-stu-id="174a9-126">Enable this setting to acquire features from registered early access programs releases.</span></span>

* <span data-ttu-id="174a9-127">Per impostazione predefinita, le funzionalità di accesso anticipato non vengono visualizzate nello strumento di funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="174a9-127">By default, early access features are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="174a9-128">L'abilitazione di senza può comportare la visualizzazione dei pacchetti di accesso `Show early access program features` `Show preview releases` eary nell'individuazione.</span><span class="sxs-lookup"><span data-stu-id="174a9-128">Enabling `Show early access program features` without `Show preview releases` may result in eary access packages not appearing in Discovery.</span></span>

## <a name="import-settings"></a><span data-ttu-id="174a9-129">Importare impostazioni</span><span class="sxs-lookup"><span data-stu-id="174a9-129">Import settings</span></span>

![Importare impostazioni](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a><span data-ttu-id="174a9-131">Sostituire i file di pacchetto esistenti</span><span class="sxs-lookup"><span data-stu-id="174a9-131">Replace existing package files</span></span>

<span data-ttu-id="174a9-132">Per impostazione predefinita, lo strumento per le funzionalità di realtà mista rimuove le copie precedenti dei pacchetti importati per ridurre le dimensioni del file e i calcoli non necessari.</span><span class="sxs-lookup"><span data-stu-id="174a9-132">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 

* <span data-ttu-id="174a9-133">Deselezionare questa impostazione per mantenere tutte le versioni</span><span class="sxs-lookup"><span data-stu-id="174a9-133">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="174a9-134">Percorso di importazione relativo del progetto</span><span class="sxs-lookup"><span data-stu-id="174a9-134">Project relative import path</span></span>

<span data-ttu-id="174a9-135">Modificare questa impostazione per aggiornare il percorso della cartella del progetto in cui vengono copiati i pacchetti di funzionalità durante l'importazione.</span><span class="sxs-lookup"><span data-stu-id="174a9-135">Change this setting to update project folder path where feature packages are copied on import.</span></span> 

* <span data-ttu-id="174a9-136">Ad esempio, se la cartella del progetto è **C:\GalaxyExplorer**, il percorso di importazione completo sarà **C:\GalaxyExplorer\Packages\MixedReality**.</span><span class="sxs-lookup"><span data-stu-id="174a9-136">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="174a9-137">Questa impostazione è **di sola lettura** in questa versione.</span><span class="sxs-lookup"><span data-stu-id="174a9-137">This setting is **read-only** in this release.</span></span> <span data-ttu-id="174a9-138">Le versioni future possono rendere configurabile questa impostazione.</span><span class="sxs-lookup"><span data-stu-id="174a9-138">Future releases may make this setting configurable.</span></span>

## <a name="early-access-settings"></a><span data-ttu-id="174a9-139">Impostazioni di accesso anticipato</span><span class="sxs-lookup"><span data-stu-id="174a9-139">Early Access settings</span></span>

![Impostazioni di accesso anticipato](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a><span data-ttu-id="174a9-141">Chiedere conferma prima di rimuovere un programma ad accesso anticipato</span><span class="sxs-lookup"><span data-stu-id="174a9-141">Ask for confirmation before removing an early access program</span></span>

<span data-ttu-id="174a9-142">Questa impostazione determina se verrà visualizzata una richiesta ogni volta che viene rimosso un programma ad accesso anticipato.</span><span class="sxs-lookup"><span data-stu-id="174a9-142">This setting determines if a prompt will be displayed each time an early access program is removed.</span></span>

### <a name="my-previews"></a><span data-ttu-id="174a9-143">Anteprime</span><span class="sxs-lookup"><span data-stu-id="174a9-143">My previews</span></span>

<span data-ttu-id="174a9-144">Elenco di programmi registrati ad accesso anticipato.</span><span class="sxs-lookup"><span data-stu-id="174a9-144">The list of registered early access programs.</span></span> <span data-ttu-id="174a9-145">Usare `Add` e `Edit` per gestire la raccolta di `Remove` programmi registrati.</span><span class="sxs-lookup"><span data-stu-id="174a9-145">Use the `Add`, `Edit` and `Remove` to manage the collection of registered programs.</span></span>

## <a name="diagnostic-settings"></a><span data-ttu-id="174a9-146">Impostazioni di diagnostica</span><span class="sxs-lookup"><span data-stu-id="174a9-146">Diagnostic settings</span></span>

![Impostazioni di diagnostica](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a><span data-ttu-id="174a9-148">File di registro</span><span class="sxs-lookup"><span data-stu-id="174a9-148">Log file</span></span>

<span data-ttu-id="174a9-149">Visualizza il percorso del file di log di diagnostica.</span><span class="sxs-lookup"><span data-stu-id="174a9-149">Displays the path to the diagnostic log file.</span></span>

## <a name="see-also"></a><span data-ttu-id="174a9-150">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="174a9-150">See also</span></span>

- [<span data-ttu-id="174a9-151">Introduzione a Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="174a9-151">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)