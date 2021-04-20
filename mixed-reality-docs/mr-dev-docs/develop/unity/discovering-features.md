---
title: Individuazione e acquisizione di funzionalità
description: Scoprire e scaricare le funzionalità di realtà mista.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 9f12a1eba0c28b89000f1541ba62747a03e3564b
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2021
ms.locfileid: "107732009"
---
# <a name="discovering-and-acquiring-features"></a><span data-ttu-id="74bd6-104">Individuazione e acquisizione di funzionalità</span><span class="sxs-lookup"><span data-stu-id="74bd6-104">Discovering and acquiring features</span></span>

<span data-ttu-id="74bd6-105">Le sezioni di questo articolo descrivono come trovare i pacchetti di funzionalità nello strumento di funzionalità di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="74bd6-105">The sections in this article outline how to find feature packages in the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="74bd6-106">Fare riferimento alla schermata seguente se è necessario un riferimento per una determinata sezione:</span><span class="sxs-lookup"><span data-stu-id="74bd6-106">Refer to the screenshot below if you need a reference for a given section:</span></span>

![Individuazione delle funzionalità](images/FeatureToolDiscovery.png)

## <a name="available-features"></a><span data-ttu-id="74bd6-108">Funzionalità disponibili</span><span class="sxs-lookup"><span data-stu-id="74bd6-108">Available features</span></span>

### <a name="category"></a><span data-ttu-id="74bd6-109">Categoria</span><span class="sxs-lookup"><span data-stu-id="74bd6-109">Category</span></span>

<span data-ttu-id="74bd6-110">Lo strumento funzionalità realtà mista visualizza una raccolta di categorie di funzionalità per semplificare l'individuazione di ciò che si vuole.</span><span class="sxs-lookup"><span data-stu-id="74bd6-110">The Mixed Reality Feature Tool displays a collection of feature categories to make it easy to find what you want.</span></span> <span data-ttu-id="74bd6-111">Espandere una delle categorie per visualizzare la raccolta di funzionalità disponibili.</span><span class="sxs-lookup"><span data-stu-id="74bd6-111">Expand any of the categories to display its collection of available features.</span></span>

> [!NOTE]
> <span data-ttu-id="74bd6-112">Se non è possibile trovare la funzionalità che si sta cercando, selezionare **Altre funzionalità**.</span><span class="sxs-lookup"><span data-stu-id="74bd6-112">If you can't find the functionality you're looking for, check **Other features**.</span></span>

![Categoria funzionalità](images/FeatureCategory.png)

<span data-ttu-id="74bd6-114">L'intestazione della categoria nello screenshot precedente contiene le proprietà seguenti, da sinistra a destra:</span><span class="sxs-lookup"><span data-stu-id="74bd6-114">The category header in the above screenshot contains the following properties, from left to right:</span></span>

- <span data-ttu-id="74bd6-115">Pulsante Espandi e comprimi</span><span class="sxs-lookup"><span data-stu-id="74bd6-115">Expand and collapse button</span></span>
- <span data-ttu-id="74bd6-116">Nome della categoria (ad esempio: Mixed Reality Toolkit)</span><span class="sxs-lookup"><span data-stu-id="74bd6-116">Category name (ex: Mixed Reality Toolkit)</span></span>
- <span data-ttu-id="74bd6-117">Conteggio delle funzionalità selezionate</span><span class="sxs-lookup"><span data-stu-id="74bd6-117">Count of selected features</span></span>
- <span data-ttu-id="74bd6-118">Conteggio delle funzionalità disponibili</span><span class="sxs-lookup"><span data-stu-id="74bd6-118">Count of available features</span></span>
- <span data-ttu-id="74bd6-119">Pulsanti di sezione</span><span class="sxs-lookup"><span data-stu-id="74bd6-119">Section buttons</span></span>

> [!NOTE]
> <span data-ttu-id="74bd6-120">I pulsanti di selezione sono sensibili al contesto.</span><span class="sxs-lookup"><span data-stu-id="74bd6-120">The selection buttons are context sensitive.</span></span> <span data-ttu-id="74bd6-121">In base allo stato di selezione delle funzionalità all'interno della categoria, verranno visualizzati uno o più pulsanti `Select All` `Select None` e .</span><span class="sxs-lookup"><span data-stu-id="74bd6-121">Based on the state of feature selection within the category, one or more of the `Select All` and `Select None` buttons will be displayed.</span></span>

### <a name="feature"></a><span data-ttu-id="74bd6-122">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="74bd6-122">Feature</span></span>

![Voce di funzionalità](images/FeatureEntry.png)

<span data-ttu-id="74bd6-124">Le funzionalità sono elencate nella categoria appropriata.</span><span class="sxs-lookup"><span data-stu-id="74bd6-124">Features are listed in their appropriate category.</span></span> <span data-ttu-id="74bd6-125">Da sinistra a destra nello screenshot precedente, le voci di funzionalità contengono:</span><span class="sxs-lookup"><span data-stu-id="74bd6-125">From left to right in the above screenshot, feature entries contain:</span></span>

- <span data-ttu-id="74bd6-126">Casella di controllo Di selezione</span><span class="sxs-lookup"><span data-stu-id="74bd6-126">Selection check box</span></span>
- <span data-ttu-id="74bd6-127">Nome della funzionalità (ad esempio Mixed Reality Toolkit Foundation)</span><span class="sxs-lookup"><span data-stu-id="74bd6-127">Feature name (ex: Mixed Reality Toolkit Foundation)</span></span>
- <span data-ttu-id="74bd6-128">Elenco delle versioni disponibili</span><span class="sxs-lookup"><span data-stu-id="74bd6-128">List of available versions</span></span>
- <span data-ttu-id="74bd6-129">Collegamento ai dettagli [del pacchetto di funzionalità](viewing-package-details.md)</span><span class="sxs-lookup"><span data-stu-id="74bd6-129">Link to the [feature package details](viewing-package-details.md)</span></span>

> [!NOTE]
> <span data-ttu-id="74bd6-130">Se una funzionalità viene fornita da un programma di accesso anticipato (detto anche anteprima privata), verrà visualizzata un'icona indicatore di ![ ](images/EarlyAccess.png) accesso anticipato.</span><span class="sxs-lookup"><span data-stu-id="74bd6-130">If a feature is provided by an Early Access (also called private preview) program, an indicator icon ![early access](images/EarlyAccess.png) will be displayed.</span></span>

## <a name="refresh-the-feature-catalog"></a><span data-ttu-id="74bd6-131">Aggiornare il catalogo delle funzionalità</span><span class="sxs-lookup"><span data-stu-id="74bd6-131">Refresh the feature catalog</span></span>

<span data-ttu-id="74bd6-132">Per verificare la presenza di funzionalità nuove e aggiornate, fare clic sull'aggiornamento</span><span class="sxs-lookup"><span data-stu-id="74bd6-132">To check for new and updated features, click the refresh</span></span> ![pulsante di aggiornamento](images/RefreshButton.png) <span data-ttu-id="74bd6-134">.</span><span class="sxs-lookup"><span data-stu-id="74bd6-134">button.</span></span> <span data-ttu-id="74bd6-135">Questa operazione si connetterà al sito del catalogo e recupererà le informazioni più recenti.</span><span class="sxs-lookup"><span data-stu-id="74bd6-135">This will connect to the catalog site and retrieve the latest information.</span></span> <span data-ttu-id="74bd6-136">Dopo aver letto il catalogo, verranno visualizzate la data e l'ora dell'ultimo aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="74bd6-136">Once the catalog has been read, the date and time of the last update will be displayed.</span></span>

## <a name="select-features"></a><span data-ttu-id="74bd6-137">Selezione delle funzionalità</span><span class="sxs-lookup"><span data-stu-id="74bd6-137">Select features</span></span>

<span data-ttu-id="74bd6-138">Le funzionalità vengono selezionate espandendo una categoria, selezionando una versione e facendo clic sulla casella di controllo:</span><span class="sxs-lookup"><span data-stu-id="74bd6-138">Features are selected by expanding a category, selecting a version, and clicking the check box:</span></span>

![Funzionalità selezionate](images/SelectedFeatures.png)

<span data-ttu-id="74bd6-140">Per selezionare ogni pacchetto all'interno di una categoria, viene `Select All` fornito un pulsante.</span><span class="sxs-lookup"><span data-stu-id="74bd6-140">To select every package within a category, a `Select All` button is provided.</span></span> <span data-ttu-id="74bd6-141">`Select None` deseleziona tutti i pacchetti selezionati.</span><span class="sxs-lookup"><span data-stu-id="74bd6-141">`Select None` will deselect all selected packages.</span></span> 

<span data-ttu-id="74bd6-142">Ogni categoria con una o più funzionalità selezionate verrà aggiornato per visualizzare il conteggio.</span><span class="sxs-lookup"><span data-stu-id="74bd6-142">Each category with one or more selected features will update to display the count.</span></span>

## <a name="acquiring-features"></a><span data-ttu-id="74bd6-143">Acquisizione di funzionalità</span><span class="sxs-lookup"><span data-stu-id="74bd6-143">Acquiring features</span></span>

<span data-ttu-id="74bd6-144">Dopo aver scelto le funzionalità, selezionare **Ottieni** funzionalità per avviare il download dei file del pacchetto di funzionalità selezionato.</span><span class="sxs-lookup"><span data-stu-id="74bd6-144">Once you've chosen your features, select **Get features** to start downloading the selected feature package files.</span></span>

> [!NOTE]
> <span data-ttu-id="74bd6-145">Per impostazione predefinita, i file dei pacchetti di funzionalità acquisiti in precedenza non verranno scaricati nuovamente.</span><span class="sxs-lookup"><span data-stu-id="74bd6-145">By default, previously acquired feature package files won't be re-downloaded.</span></span> <span data-ttu-id="74bd6-146">Per modificare questo comportamento, vedere configurazione [dello strumento di funzionalità](configuring-feature-tool.md).</span><span class="sxs-lookup"><span data-stu-id="74bd6-146">To change this behavior please see [configuring the feature tool](configuring-feature-tool.md).</span></span>

<span data-ttu-id="74bd6-147">Al termine del download, lo strumento per le funzionalità di realtà mista passa al passaggio [di importazione delle](importing-features.md) funzionalità.</span><span class="sxs-lookup"><span data-stu-id="74bd6-147">Once downloading is complete, the Mixed Reality Feature Tool will move to the [importing features](importing-features.md) step.</span></span>

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="74bd6-148">Tornare al passaggio precedente</span><span class="sxs-lookup"><span data-stu-id="74bd6-148">Going back to the previous step</span></span>

<span data-ttu-id="74bd6-149">Da **Individua funzionalità,** lo strumento funzionalità realtà mista consente di tornare alla selezione del progetto.</span><span class="sxs-lookup"><span data-stu-id="74bd6-149">From **Discover features**, the Mixed Reality Feature Tool allows for navigating back to project selection.</span></span> <span data-ttu-id="74bd6-150">Selezionare **Torna indietro** per iniziare di nuovo.</span><span class="sxs-lookup"><span data-stu-id="74bd6-150">Select **Go back** to start again.</span></span>

## <a name="see-also"></a><span data-ttu-id="74bd6-151">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="74bd6-151">See also</span></span>

- [<span data-ttu-id="74bd6-152">Introduzione a Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="74bd6-152">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="74bd6-153">Configurazione dello strumento di funzionalità</span><span class="sxs-lookup"><span data-stu-id="74bd6-153">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="74bd6-154">Visualizzazione dei dettagli del pacchetto di funzionalità</span><span class="sxs-lookup"><span data-stu-id="74bd6-154">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="74bd6-155">Importazione di pacchetti selezionati</span><span class="sxs-lookup"><span data-stu-id="74bd6-155">Importing selected packages</span></span>](importing-features.md)
