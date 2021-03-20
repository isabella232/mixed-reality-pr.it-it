---
title: Configurazione dello strumento funzionalità per la realtà mista
description: Informazioni su come scaricare e installare i pacchetti Unity per la realtà mista dallo strumento per la funzionalità MR per lo sviluppo di HoloLens e VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 4201f96ac87a6e9ab33607072c0d8f5f50df38a1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "99244597"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="cc910-104">Configurazione dello strumento funzionalità per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="cc910-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="cc910-105">Quando si usa lo strumento per la funzionalità di realtà mista, è possibile accedere a tre diverse categorie di impostazioni che è possibile personalizzare in:</span><span class="sxs-lookup"><span data-stu-id="cc910-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* [<span data-ttu-id="cc910-106">Impostazioni di download</span><span class="sxs-lookup"><span data-stu-id="cc910-106">Download settings</span></span>](#download-settings)
* [<span data-ttu-id="cc910-107">Impostazioni delle funzionalità</span><span class="sxs-lookup"><span data-stu-id="cc910-107">Feature settings</span></span>](#feature-settings)
* [<span data-ttu-id="cc910-108">Importare impostazioni</span><span class="sxs-lookup"><span data-stu-id="cc910-108">Import settings</span></span>](#import-settings)

![Impostazioni](images/FeatureToolSettings.png)

## <a name="download-settings"></a><span data-ttu-id="cc910-110">Impostazioni di download</span><span class="sxs-lookup"><span data-stu-id="cc910-110">Download settings</span></span>

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="cc910-111">Sovrascrivi file di pacchetto esistenti</span><span class="sxs-lookup"><span data-stu-id="cc910-111">Overwrite existing package files</span></span>

<span data-ttu-id="cc910-112">L'abilitazione di questa impostazione causa il download dei file del pacchetto ogni volta che vengono acquisiti.</span><span class="sxs-lookup"><span data-stu-id="cc910-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 
* <span data-ttu-id="cc910-113">**È consigliabile lasciare questa opzione disabilitata per ridurre l'utilizzo della larghezza di banda di rete**</span><span class="sxs-lookup"><span data-stu-id="cc910-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="cc910-114">Per impostazione predefinita, i file dei pacchetti acquisiti in precedenza non vengono scaricati di nuovo</span><span class="sxs-lookup"><span data-stu-id="cc910-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="cc910-115">Cache pacchetti</span><span class="sxs-lookup"><span data-stu-id="cc910-115">Package cache</span></span>

<span data-ttu-id="cc910-116">Modificare questa impostazione per aggiornare il percorso in cui vengono scaricati i pacchetti di funzionalità.</span><span class="sxs-lookup"><span data-stu-id="cc910-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="cc910-117">Questa impostazione è di sola **lettura** in questa versione.</span><span class="sxs-lookup"><span data-stu-id="cc910-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="cc910-118">Le versioni future possono rendere questa impostazione configurabile.</span><span class="sxs-lookup"><span data-stu-id="cc910-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="cc910-119">Impostazioni delle funzionalità</span><span class="sxs-lookup"><span data-stu-id="cc910-119">Feature settings</span></span>

### <a name="include-preview-releases"></a><span data-ttu-id="cc910-120">Includi versioni di anteprima</span><span class="sxs-lookup"><span data-stu-id="cc910-120">Include preview releases</span></span>

<span data-ttu-id="cc910-121">Abilitare questa impostazione per acquisire le versioni di anteprima.</span><span class="sxs-lookup"><span data-stu-id="cc910-121">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="cc910-122">Per impostazione predefinita, le versioni di anteprima non vengono visualizzate nello strumento funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="cc910-122">By default, preview releases aren't shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="cc910-123">Una versione di anteprima è definita come contenente la designazione **"-Preview"** nella versione del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="cc910-123">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

## <a name="import-settings"></a><span data-ttu-id="cc910-124">Importare impostazioni</span><span class="sxs-lookup"><span data-stu-id="cc910-124">Import settings</span></span>

### <a name="replace-existing-package-files"></a><span data-ttu-id="cc910-125">Sostituisci file di pacchetto esistenti</span><span class="sxs-lookup"><span data-stu-id="cc910-125">Replace existing package files</span></span>

<span data-ttu-id="cc910-126">Per impostazione predefinita, lo strumento della funzionalità di realtà mista rimuove le copie precedenti dei pacchetti importati per ridurre le dimensioni del file e i calcoli non necessari.</span><span class="sxs-lookup"><span data-stu-id="cc910-126">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 
* <span data-ttu-id="cc910-127">Deselezionare questa impostazione per salvare tutte le versioni</span><span class="sxs-lookup"><span data-stu-id="cc910-127">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="cc910-128">Percorso importazione relativa progetto</span><span class="sxs-lookup"><span data-stu-id="cc910-128">Project relative import path</span></span>

<span data-ttu-id="cc910-129">Modificare questa impostazione in Aggiorna percorso cartella di progetto in cui vengono copiati i pacchetti di funzionalità durante l'importazione.</span><span class="sxs-lookup"><span data-stu-id="cc910-129">Change this setting to update project folder path where feature packages are copied on import.</span></span> 
* <span data-ttu-id="cc910-130">Ad esempio, se la cartella del progetto è **C:\GalaxyExplorer**, il percorso di importazione completo sarà **C:\GalaxyExplorer\Packages\MixedReality**.</span><span class="sxs-lookup"><span data-stu-id="cc910-130">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="cc910-131">Questa impostazione è di sola **lettura** in questa versione.</span><span class="sxs-lookup"><span data-stu-id="cc910-131">This setting is **read-only** in this release.</span></span> <span data-ttu-id="cc910-132">Le versioni future possono rendere questa impostazione configurabile.</span><span class="sxs-lookup"><span data-stu-id="cc910-132">Future releases may make this setting configurable.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc910-133">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="cc910-133">See also</span></span>

- [<span data-ttu-id="cc910-134">Strumento per la funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="cc910-134">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)