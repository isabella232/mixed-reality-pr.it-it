---
title: Esercitazioni introduttive - 3. Configurazione dei profili di Mixed Reality Toolkit
description: Questa esercitazione illustra come configurare i profili di Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, consapevolezza spaziale
ms.localizationpriority: high
ms.openlocfilehash: 7ac81c21e1658798b7f512c4afa2eea9f509d827
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679320"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="4013c-105">3. Configurazione dei profili di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="4013c-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="4013c-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="4013c-106">Overview</span></span>

<span data-ttu-id="4013c-107">In questa esercitazione si apprenderà come personalizzare e configurare i profili di MRTK.</span><span class="sxs-lookup"><span data-stu-id="4013c-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="4013c-108">I <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html" target="_blank">profili di MRTK</a> sono profili annidati in una struttura ad albero che costituiscono le informazioni di configurazione per la modalità di inizializzazione dei sistemi e delle funzionalità di MRTK.</span><span class="sxs-lookup"><span data-stu-id="4013c-108">The <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="4013c-109">Il profilo di primo livello, quello di configurazione, contiene profili annidati per ognuno dei sistemi core principali.</span><span class="sxs-lookup"><span data-stu-id="4013c-109">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="4013c-110">Ogni profilo annidato è progettato per la configurazione del comportamento del sistema corrispondente.</span><span class="sxs-lookup"><span data-stu-id="4013c-110">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="4013c-111">Questo particolare esempio mostrerà come nascondere la mesh di consapevolezza spaziale cambiando le impostazioni dell'osservatore della mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="4013c-111">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="4013c-112">Puoi comunque adottare gli stessi principi per personalizzare le impostazioni o i valori nei profili di MRTK.</span><span class="sxs-lookup"><span data-stu-id="4013c-112">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="4013c-113">Come rilevato quando è stato distribuito il progetto in HoloLens 2 nell'[esercitazione precedente](mr-learning-base-02.md#congratulations), la mesh <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness</a> è una raccolta di mesh che rappresentano la geometria dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="4013c-113">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="4013c-114">Si tratta di una visualizzazione utile nella fase iniziale, ma che in genere è disabilitata per evitare distrazioni a livello visivo e l'impatto aggiuntivo che produrrebbe sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="4013c-114">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="4013c-115">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="4013c-115">Objectives</span></span>

* <span data-ttu-id="4013c-116">Imparare a personalizzare e configurare i profili di MRTK</span><span class="sxs-lookup"><span data-stu-id="4013c-116">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="4013c-117">Nascondere il mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="4013c-117">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="4013c-118">Modifica delle opzioni di visualizzazione di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="4013c-118">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="4013c-119">Di seguito sono elencati i passaggi principali da eseguire per nascondere la mesh di consapevolezza spaziale:</span><span class="sxs-lookup"><span data-stu-id="4013c-119">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="4013c-120">Clonare il profilo di configurazione predefinito</span><span class="sxs-lookup"><span data-stu-id="4013c-120">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="4013c-121">Abilitare il sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="4013c-121">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="4013c-122">Clonare il profilo predefinito del sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="4013c-122">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="4013c-123">Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="4013c-123">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="4013c-124">Modificare la visibilità della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="4013c-124">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="4013c-125">per impostazione predefinita, i profili di MRTK non sono modificabili.</span><span class="sxs-lookup"><span data-stu-id="4013c-125">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="4013c-126">Si tratta di modelli di profilo predefiniti che devono essere clonati prima di poter essere modificati.</span><span class="sxs-lookup"><span data-stu-id="4013c-126">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="4013c-127">Sono disponibili diversi livelli annidati di profili.</span><span class="sxs-lookup"><span data-stu-id="4013c-127">There are several nested layers of profiles.</span></span> <span data-ttu-id="4013c-128">È quindi normale clonare e modificare diversi profili quando una o più impostazioni vengono configurate.</span><span class="sxs-lookup"><span data-stu-id="4013c-128">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="4013c-129">1. Clonare il profilo di configurazione predefinito</span><span class="sxs-lookup"><span data-stu-id="4013c-129">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="4013c-130">Il profilo di configurazione è il profilo di primo livello.</span><span class="sxs-lookup"><span data-stu-id="4013c-130">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="4013c-131">Di conseguenza, prima di modificare altri profili, devi clonare il profilo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="4013c-131">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="4013c-132">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) impostare **Configuration Profile** (Profilo di configurazione) di Mixed Reality Toolkit su **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="4013c-132">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit di Unity con DefaultHoloLens2ConfigurationProfile selezionato](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="4013c-134">Con l'oggetto **MixedRealityToolkit** ancora selezionato, nella finestra Inspector (Controllo) fai clic sul pulsante **Copy & Customize** (Copia e personalizza) per aprire la finestra Clone Profile (Clona profilo):</span><span class="sxs-lookup"><span data-stu-id="4013c-134">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Pulsante Copy & Customize del componente MixedRealityToolkit di Unity](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="4013c-136">Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_HoloLens2ConfigurationProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="4013c-136">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![Finestra popup per clonare il profilo di configurazione di MixedRealityToolkit di Unity](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="4013c-138">Il profilo di configurazione appena creato viene ora assegnato come profilo di configurazione per la scena:</span><span class="sxs-lookup"><span data-stu-id="4013c-138">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Componente MixedRealityToolkit di Unity con l'elemento HoloLens2ConfigurationProfile personalizzato appena creato applicato](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="4013c-140">Nel menu di Unity scegli **File** > **Save** (Salva) per salvare la scena.</span><span class="sxs-lookup"><span data-stu-id="4013c-140">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="4013c-141">Ricordarsi di salvare il lavoro durante l'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="4013c-141">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="4013c-142">2. Abilitare il sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="4013c-142">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="4013c-143">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda **Spatial Awareness** (Consapevolezza spaziale), infine la casella di controllo **Enable Spatial Awareness System** (Abilita sistema di consapevolezza spaziale):</span><span class="sxs-lookup"><span data-stu-id="4013c-143">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Componente MixedRealityToolkit di Unity con il sistema Spatial Awareness abilitato](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="4013c-145">Per i progetti futuri, se non è necessario che l'app risponda o interagisca con l'ambiente, è consigliabile che il sistema Spatial Awareness rimanga disabilitato per ridurre l'impatto in termini di prestazioni.</span><span class="sxs-lookup"><span data-stu-id="4013c-145">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="4013c-146">3. Clonare il profilo predefinito del sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="4013c-146">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="4013c-147">Nella scheda **Spatial Awareness** (Consapevolezza spaziale) fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):</span><span class="sxs-lookup"><span data-stu-id="4013c-147">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit di Unity con la scheda Spatial Awareness selezionata](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="4013c-149">Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="4013c-149">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![Finestra popup per clonare il profilo del sistema Spatial Awareness di MixedRealityToolkit di Unity](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="4013c-151">Il profilo del sistema di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo di configurazione:</span><span class="sxs-lookup"><span data-stu-id="4013c-151">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Componente MixedRealityToolkit di Unity con l'elemento MixedRealitySpatialAwarenessSystemProfile personalizzato appena creato applicato](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="4013c-153">4. Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="4013c-153">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="4013c-154">Con la scheda **Spatial Awareness** (Consapevolezza spaziale) ancora selezionata, espandi la sezione **Windows Mixed Reality Spatial Mesh Observer** (Osservatore mesh spaziale Windows Mixed Reality) e quindi fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):</span><span class="sxs-lookup"><span data-stu-id="4013c-154">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit di Unity con la sezione Windows Mixed Reality Spatial Mesh Observer espansa](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="4013c-156">Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="4013c-156">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Finestra popup per clonare il profilo di Spatial Mesh Observer di MixedRealityToolkit di Unity](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="4013c-158">Il profilo dell'osservatore della mesh di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo del sistema di consapevolezza spaziale:</span><span class="sxs-lookup"><span data-stu-id="4013c-158">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Componente MixedRealityToolkit di Unity con l'elemento MixedRealitySpatialAwarenessMeshObserverProfile personalizzato appena creato applicato](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="4013c-160">5. Modificare la visibilità della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="4013c-160">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="4013c-161">In **Spatial Mesh Observer Settings** (Impostazioni osservatore della mesh spaziale) impostare **Display Option** (Opzione di visualizzazione) su **Occlusion** (Occlusione) per rendere invisibile la mesh di mapping spaziale mentre è ancora funzionante:</span><span class="sxs-lookup"><span data-stu-id="4013c-161">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Componente MixedRealityToolkit di Unity con l'opzione Display Option di Spatial Mesh Observer impostata su Occlusion](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="4013c-163">Anche se non è visibile, la mesh di mapping spaziale è comunque presente e funzionante.</span><span class="sxs-lookup"><span data-stu-id="4013c-163">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="4013c-164">Ad esempio, gli ologrammi dietro la mesh di mapping spaziale, come nel caso di un ologramma dietro a un muro fisico, non saranno visibili.</span><span class="sxs-lookup"><span data-stu-id="4013c-164">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="4013c-165">hai appreso come modificare un'impostazione nel profilo di MRTK.</span><span class="sxs-lookup"><span data-stu-id="4013c-165">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="4013c-166">Come si può notare, per personalizzare le impostazioni di MRTK, è necessario prima creare copie dei profili predefiniti.</span><span class="sxs-lookup"><span data-stu-id="4013c-166">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="4013c-167">Poiché i profili predefiniti non sono modificabili, saranno sempre presenti come riferimento in caso di ripristino delle impostazioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="4013c-167">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="4013c-168">Per altre informazioni sui profili di MRTK e sulla loro architettura, consultare la [guida alla configurazione dei profili di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="4013c-168">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="4013c-169">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="4013c-169">Congratulations</span></span>

<span data-ttu-id="4013c-170">In questa esercitazione si è appreso come clonare, personalizzare e configurare i profili e le impostazioni di MRTK.</span><span class="sxs-lookup"><span data-stu-id="4013c-170">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4013c-171">Esercitazione successiva: 4. Posizionamento degli oggetti nella scena</span><span class="sxs-lookup"><span data-stu-id="4013c-171">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)
