---
title: Importazione di funzionalità
description: Informazioni su come importare e installare le funzionalità dallo strumento di funzionalità di MR per lo sviluppo di HoloLens e VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: a82eea93a07b662314f3a718eef0c1bd18a4ca4e
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244589"
---
# <a name="importing-features"></a><span data-ttu-id="3d60c-104">Importazione di funzionalità</span><span class="sxs-lookup"><span data-stu-id="3d60c-104">Importing features</span></span>

<span data-ttu-id="3d60c-105">Una volta scaricate, le funzionalità possono essere esaminate e importate nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="3d60c-105">Once your features have been downloaded, they can be reviewed and imported into the Unity project.</span></span> <span data-ttu-id="3d60c-106">In questo passaggio la finestra dell'applicazione dovrebbe essere simile all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="3d60c-106">At this step, your application window should look like the following image:</span></span>

![Importazione di funzionalità](images/FeatureToolImport.png)

## <a name="features-list"></a><span data-ttu-id="3d60c-108">Elenco di funzionalità</span><span class="sxs-lookup"><span data-stu-id="3d60c-108">Features list</span></span>

<span data-ttu-id="3d60c-109">L'elenco delle **funzionalità** contiene la raccolta di pacchetti selezionati durante l'individuazione.</span><span class="sxs-lookup"><span data-stu-id="3d60c-109">The **Features** list contains the collection of packages selected during discovery.</span></span> 
* <span data-ttu-id="3d60c-110">È possibile selezionare o deselezionare ogni funzionalità prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="3d60c-110">Each feature can be selected or deselected before importing.</span></span> <span data-ttu-id="3d60c-111">I dettagli del pacchetto possono essere visualizzati usando il collegamento **Dettagli** riportato di seguito</span><span class="sxs-lookup"><span data-stu-id="3d60c-111">Package details can be viewed using the **Details** link shown below</span></span>

![Elenco di funzionalità](images/FeaturesList.png)

## <a name="required-dependencies-list"></a><span data-ttu-id="3d60c-113">Elenco dipendenze obbligatorie</span><span class="sxs-lookup"><span data-stu-id="3d60c-113">Required dependencies list</span></span>

<span data-ttu-id="3d60c-114">L'elenco **dipendenze necessarie** contiene i pacchetti necessari per il funzionamento di una o più delle funzionalità selezionate.</span><span class="sxs-lookup"><span data-stu-id="3d60c-114">The **Required dependencies** list contains the packages that one or more of the selected features requires to function.</span></span> <span data-ttu-id="3d60c-115">Questo elenco conterrà anche le dipendenze delle dipendenze.</span><span class="sxs-lookup"><span data-stu-id="3d60c-115">This list will also contain dependencies of dependencies.</span></span>
* <span data-ttu-id="3d60c-116">Ogni dipendenza può essere selezionata o deselezionata prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="3d60c-116">Each dependency can be selected or deselected before importing.</span></span> <span data-ttu-id="3d60c-117">I dettagli del pacchetto possono essere visualizzati usando il collegamento **Dettagli** riportato di seguito</span><span class="sxs-lookup"><span data-stu-id="3d60c-117">Package details can be viewed using the **Details** link shown below</span></span>

![Elenco dipendenze](images/RequiredDependencyList.png)

> [!NOTE]
> <span data-ttu-id="3d60c-119">La deselezione delle dipendenze richieste genererà uno o più errori di dipendenza mancanti durante il caricamento del progetto in Unity.</span><span class="sxs-lookup"><span data-stu-id="3d60c-119">Deselecting required dependencies will result in one or more missing dependency errors when loading the project in Unity.</span></span> <span data-ttu-id="3d60c-120">Queste funzionalità non saranno utilizzabili nel progetto.</span><span class="sxs-lookup"><span data-stu-id="3d60c-120">These features won't be usable in the project.</span></span>

## <a name="specifying-the-unity-project-path"></a><span data-ttu-id="3d60c-121">Specifica del percorso del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="3d60c-121">Specifying the Unity project path</span></span>

<span data-ttu-id="3d60c-122">Prima che le funzionalità possano essere importate nel progetto, è necessario registrare il percorso con lo strumento della funzionalità di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="3d60c-122">Before features can be imported into the project, you need to register the path with the Mixed Reality Feature Tool.</span></span>

![Impostazione del percorso del progetto](images/ProjectPath.png)

## <a name="validating-selections"></a><span data-ttu-id="3d60c-124">Convalida di selezioni</span><span class="sxs-lookup"><span data-stu-id="3d60c-124">Validating selections</span></span>

<span data-ttu-id="3d60c-125">Si consiglia vivamente di convalidare le selezioni delle funzionalità prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="3d60c-125">We highly recommend validating feature selections before importing.</span></span> <span data-ttu-id="3d60c-126">Questo passaggio solleverà eventuali problemi che potrebbero impedire la riuscita dello sviluppo del progetto.</span><span class="sxs-lookup"><span data-stu-id="3d60c-126">This step will raise any issues that are likely to impede successful project development.</span></span>

![Problemi di convalida](images/ValidationIssues.png)

<span data-ttu-id="3d60c-128">Lo strumento per la funzionalità di realtà mista fornisce due risoluzioni automatiche di problemi, descritte nelle sezioni seguenti, e l'opzione per annullare e risolvere i problemi manualmente.</span><span class="sxs-lookup"><span data-stu-id="3d60c-128">The Mixed Reality Feature Tool provides two automatic issue resolutions, described in the following sections), and the option to cancel and resolve issues manually.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d60c-129">Lo strumento di funzionalità della realtà mista non può risolvere automaticamente i problemi correlati alle versioni di Unity richieste.</span><span class="sxs-lookup"><span data-stu-id="3d60c-129">The Mixed Reality Feature Tool cannot automatically resolve issues related to required versions of Unity.</span></span> <span data-ttu-id="3d60c-130">Questi problemi devono essere gestiti manualmente aggiornando la versione di Unity usata dal progetto o disabilitando le funzionalità che richiedono una versione più recente.</span><span class="sxs-lookup"><span data-stu-id="3d60c-130">These issues must be handled manually by upgrading the version of Unity used by the project or disabling the feature(s) requiring a newer version.</span></span>
>
> <span data-ttu-id="3d60c-131">Una versione futura dello strumento per la funzionalità di realtà mista fornirà un filtro migliore per le funzionalità basate sulla versione di Unity usata dal progetto.</span><span class="sxs-lookup"><span data-stu-id="3d60c-131">A future release of the Mixed Reality Feature Tool will provide better filtering of features based upon the version of Unity being used by the project.</span></span>

### <a name="enable-dependencies"></a><span data-ttu-id="3d60c-132">Abilita dipendenze</span><span class="sxs-lookup"><span data-stu-id="3d60c-132">Enable dependencies</span></span>

<span data-ttu-id="3d60c-133">Il pulsante **Abilita dipendenze** selezionerà automaticamente le dipendenze mancanti.</span><span class="sxs-lookup"><span data-stu-id="3d60c-133">The **Enable dependencies** button will automatically re-select the missing dependencies.</span></span> <span data-ttu-id="3d60c-134">Questo vale per le dipendenze che sono state selezionate in modo esplicito (visualizzate nell'elenco delle **funzionalità** ) e quelle che sono state selezionate in modo implicito in base ai requisiti delle funzionalità selezionate.</span><span class="sxs-lookup"><span data-stu-id="3d60c-134">This is true for dependencies that were explicitly selected (appear in the **Features** list) and those that were implicitly selected based on the requirements of the selected features.</span></span>

### <a name="disable-features"></a><span data-ttu-id="3d60c-135">Disabilitare le funzionalità</span><span class="sxs-lookup"><span data-stu-id="3d60c-135">Disable features</span></span>

<span data-ttu-id="3d60c-136">Selezionando **Disabilita funzionalità** verrà automaticamente deselezionata una funzionalità che dipende da una o più dipendenze deselezionate.</span><span class="sxs-lookup"><span data-stu-id="3d60c-136">Selecting **Disable features** will automatically deselect any feature that depends on one or more of the dependencies that have been unchecked.</span></span> <span data-ttu-id="3d60c-137">Questo vale per i pacchetti di dipendenza selezionati in modo implicito e le funzionalità selezionate in modo esplicito.</span><span class="sxs-lookup"><span data-stu-id="3d60c-137">This is true for implicitly selected dependency packages and explicitly selected features.</span></span>

## <a name="importing"></a><span data-ttu-id="3d60c-138">Importazione</span><span class="sxs-lookup"><span data-stu-id="3d60c-138">Importing</span></span>

<span data-ttu-id="3d60c-139">Selezionare **Importa** per aggiungere le funzionalità selezionate e fornire l' [approvazione finale](reviewing-changes.md) prima di aggiornare il progetto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="3d60c-139">Select **Import** to add your selected features and give [final approval](reviewing-changes.md) before updating your target project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d60c-140">Se si verifica un problema di convalida durante l'importazione, verrà visualizzato un messaggio di avviso.</span><span class="sxs-lookup"><span data-stu-id="3d60c-140">If a validation issue remains when importing, a warning message will be displayed.</span></span> <span data-ttu-id="3d60c-141">È consigliabile selezionare No, fare clic su **convalida** e risolvere i problemi presentati.</span><span class="sxs-lookup"><span data-stu-id="3d60c-141">It is recommended to select No, click **Validate** and resolve any issues presented.</span></span>
>
> ![Continua con i problemi di convalida](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="3d60c-143">Tornando al passaggio precedente</span><span class="sxs-lookup"><span data-stu-id="3d60c-143">Going back to the previous step</span></span>

<span data-ttu-id="3d60c-144">Dalle **funzionalità di importazione**, lo strumento della funzionalità di realtà mista consente di tornare all' [individuazione](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="3d60c-144">From **Import features**, the Mixed Reality Feature Tool allows for navigating back to [discovery](discovering-features.md).</span></span> <span data-ttu-id="3d60c-145">Selezionare **Torna indietro** per scaricare altri pacchetti di funzionalità.</span><span class="sxs-lookup"><span data-stu-id="3d60c-145">Select **Go back** to download other feature packages.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d60c-146">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="3d60c-146">See also</span></span>

- [<span data-ttu-id="3d60c-147">Strumento per la funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="3d60c-147">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="3d60c-148">Individuazione e acquisizione</span><span class="sxs-lookup"><span data-stu-id="3d60c-148">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="3d60c-149">Visualizzazione dei dettagli del pacchetto di funzionalità</span><span class="sxs-lookup"><span data-stu-id="3d60c-149">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="3d60c-150">Revisione e approvazione delle modifiche del progetto</span><span class="sxs-lookup"><span data-stu-id="3d60c-150">Reviewing and approving project modifications</span></span>](reviewing-changes.md)