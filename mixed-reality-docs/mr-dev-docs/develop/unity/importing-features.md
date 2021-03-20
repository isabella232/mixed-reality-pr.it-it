---
title: Importazione di funzionalità
description: Informazioni su come importare e installare le funzionalità dallo strumento di funzionalità di MR per lo sviluppo di HoloLens e VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 0d9139835b9eb4e3e5ce3d1f378c56a4724bfa55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "102230819"
---
# <a name="importing-features"></a><span data-ttu-id="31dac-104">Importazione di funzionalità</span><span class="sxs-lookup"><span data-stu-id="31dac-104">Importing features</span></span>

<span data-ttu-id="31dac-105">Una volta scaricate, le funzionalità possono essere esaminate e importate nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="31dac-105">Once your features have been downloaded, they can be reviewed and imported into the Unity project.</span></span> <span data-ttu-id="31dac-106">In questo passaggio la finestra dell'applicazione dovrebbe essere simile all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="31dac-106">At this step, your application window should look like the following image:</span></span>

![Importazione di funzionalità](images/FeatureToolImport.png)

## <a name="features-list"></a><span data-ttu-id="31dac-108">Elenco di funzionalità</span><span class="sxs-lookup"><span data-stu-id="31dac-108">Features list</span></span>

<span data-ttu-id="31dac-109">L'elenco delle **funzionalità** contiene la raccolta di pacchetti selezionati durante l'individuazione.</span><span class="sxs-lookup"><span data-stu-id="31dac-109">The **Features** list contains the collection of packages selected during discovery.</span></span> <span data-ttu-id="31dac-110">È possibile selezionare o deselezionare ogni funzionalità prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="31dac-110">Each feature can be selected or deselected before importing.</span></span> <span data-ttu-id="31dac-111">I dettagli del pacchetto possono essere visualizzati usando il collegamento **Dettagli** riportato di seguito</span><span class="sxs-lookup"><span data-stu-id="31dac-111">Package details can be viewed using the **Details** link shown below</span></span>

![Elenco di funzionalità](images/FeaturesList.png)

## <a name="required-dependencies-list"></a><span data-ttu-id="31dac-113">Elenco dipendenze obbligatorie</span><span class="sxs-lookup"><span data-stu-id="31dac-113">Required dependencies list</span></span>

<span data-ttu-id="31dac-114">L'elenco **dipendenze necessarie** contiene i pacchetti necessari per il funzionamento di una o più delle funzionalità selezionate.</span><span class="sxs-lookup"><span data-stu-id="31dac-114">The **Required dependencies** list contains the packages that one or more of the selected features requires to function.</span></span> <span data-ttu-id="31dac-115">Questo elenco conterrà anche le dipendenze delle dipendenze.</span><span class="sxs-lookup"><span data-stu-id="31dac-115">This list will also contain dependencies of dependencies.</span></span> <span data-ttu-id="31dac-116">Ogni dipendenza può essere selezionata o deselezionata prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="31dac-116">Each dependency can be selected or deselected before importing.</span></span> <span data-ttu-id="31dac-117">I dettagli del pacchetto possono essere visualizzati usando il collegamento **Dettagli** riportato di seguito</span><span class="sxs-lookup"><span data-stu-id="31dac-117">Package details can be viewed using the **Details** link shown below</span></span>

![Elenco dipendenze](images/RequiredDependencyList.png)

> [!NOTE]
> <span data-ttu-id="31dac-119">La deselezione delle dipendenze richieste genererà uno o più errori di dipendenza mancanti durante il caricamento del progetto in Unity.</span><span class="sxs-lookup"><span data-stu-id="31dac-119">Deselecting required dependencies will result in one or more missing dependency errors when loading the project in Unity.</span></span> <span data-ttu-id="31dac-120">Queste funzionalità non saranno utilizzabili nel progetto.</span><span class="sxs-lookup"><span data-stu-id="31dac-120">These features won't be usable in the project.</span></span>

## <a name="validating-selections"></a><span data-ttu-id="31dac-121">Convalida di selezioni</span><span class="sxs-lookup"><span data-stu-id="31dac-121">Validating selections</span></span>

<span data-ttu-id="31dac-122">Si consiglia vivamente di convalidare le selezioni delle funzionalità prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="31dac-122">We highly recommend validating feature selections before importing.</span></span> <span data-ttu-id="31dac-123">Questo passaggio solleverà eventuali problemi che potrebbero impedire la riuscita dello sviluppo del progetto.</span><span class="sxs-lookup"><span data-stu-id="31dac-123">This step will raise any issues that are likely to impede successful project development.</span></span>

![Problemi di convalida](images/ValidationIssues.png)

<span data-ttu-id="31dac-125">Lo strumento per la funzionalità di realtà mista fornisce due risoluzioni automatiche di problemi, descritte nelle sezioni seguenti, e l'opzione per annullare e risolvere i problemi manualmente.</span><span class="sxs-lookup"><span data-stu-id="31dac-125">The Mixed Reality Feature Tool provides two automatic issue resolutions, described in the following sections), and the option to cancel and resolve issues manually.</span></span>

### <a name="enable-dependencies"></a><span data-ttu-id="31dac-126">Abilita dipendenze</span><span class="sxs-lookup"><span data-stu-id="31dac-126">Enable dependencies</span></span>

<span data-ttu-id="31dac-127">Il pulsante **Abilita dipendenze** selezionerà automaticamente le dipendenze mancanti.</span><span class="sxs-lookup"><span data-stu-id="31dac-127">The **Enable dependencies** button will automatically re-select the missing dependencies.</span></span> <span data-ttu-id="31dac-128">Questo vale per le dipendenze che sono state selezionate in modo esplicito (visualizzate nell'elenco delle **funzionalità** ) e quelle che sono state selezionate in modo implicito in base ai requisiti delle funzionalità selezionate.</span><span class="sxs-lookup"><span data-stu-id="31dac-128">This is true for dependencies that were explicitly selected (appear in the **Features** list) and those that were implicitly selected based on the requirements of the selected features.</span></span>

### <a name="disable-features"></a><span data-ttu-id="31dac-129">Disabilitare le funzionalità</span><span class="sxs-lookup"><span data-stu-id="31dac-129">Disable features</span></span>

<span data-ttu-id="31dac-130">Selezionando **Disabilita funzionalità** verrà automaticamente deselezionata una funzionalità che dipende da una o più dipendenze deselezionate.</span><span class="sxs-lookup"><span data-stu-id="31dac-130">Selecting **Disable features** will automatically deselect any feature that depends on one or more of the dependencies that have been unchecked.</span></span> <span data-ttu-id="31dac-131">Questo vale per i pacchetti di dipendenza selezionati in modo implicito e le funzionalità selezionate in modo esplicito.</span><span class="sxs-lookup"><span data-stu-id="31dac-131">This is true for implicitly selected dependency packages and explicitly selected features.</span></span>

## <a name="importing"></a><span data-ttu-id="31dac-132">Importazione</span><span class="sxs-lookup"><span data-stu-id="31dac-132">Importing</span></span>

<span data-ttu-id="31dac-133">Selezionare **Importa** per aggiungere le funzionalità selezionate e fornire l' [approvazione finale](reviewing-changes.md) prima di aggiornare il progetto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="31dac-133">Select **Import** to add your selected features and give [final approval](reviewing-changes.md) before updating your target project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="31dac-134">Se si verifica un problema di convalida durante l'importazione, verrà visualizzato un messaggio di avviso.</span><span class="sxs-lookup"><span data-stu-id="31dac-134">If a validation issue remains when importing, a warning message will be displayed.</span></span> <span data-ttu-id="31dac-135">È consigliabile selezionare No, fare clic su **convalida** e risolvere i problemi presentati.</span><span class="sxs-lookup"><span data-stu-id="31dac-135">It is recommended to select No, click **Validate** and resolve any issues presented.</span></span>
>
> ![Continua con i problemi di convalida](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="31dac-137">Tornando al passaggio precedente</span><span class="sxs-lookup"><span data-stu-id="31dac-137">Going back to the previous step</span></span>

<span data-ttu-id="31dac-138">Dalle **funzionalità di importazione**, lo strumento della funzionalità di realtà mista consente di tornare all' [individuazione](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="31dac-138">From **Import features**, the Mixed Reality Feature Tool allows for navigating back to [discovery](discovering-features.md).</span></span> <span data-ttu-id="31dac-139">Selezionare **Torna indietro** per scaricare altri pacchetti di funzionalità.</span><span class="sxs-lookup"><span data-stu-id="31dac-139">Select **Go back** to download other feature packages.</span></span>

## <a name="see-also"></a><span data-ttu-id="31dac-140">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="31dac-140">See also</span></span>

- [<span data-ttu-id="31dac-141">Strumento per la funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="31dac-141">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="31dac-142">Individuazione e acquisizione</span><span class="sxs-lookup"><span data-stu-id="31dac-142">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="31dac-143">Visualizzazione dei dettagli del pacchetto di funzionalità</span><span class="sxs-lookup"><span data-stu-id="31dac-143">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="31dac-144">Revisione e approvazione delle modifiche del progetto</span><span class="sxs-lookup"><span data-stu-id="31dac-144">Reviewing and approving project modifications</span></span>](reviewing-changes.md)