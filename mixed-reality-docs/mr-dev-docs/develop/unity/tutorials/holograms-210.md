---
title: 'MR Input 210: Sguardo fisso'
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per informazioni dettagliate sui concetti relativi a sguardi.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, esercitazione, sguardo, HoloLens, realtà mista Academy, Unity, auricolare realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale, Windows 10
ms.openlocfilehash: 2cbbdba0a74ab94c6a291cbe6af1cd1ae9020fe4
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677250"
---
# <a name="mr-input-210-gaze"></a><span data-ttu-id="03381-104">Input MR 210: Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="03381-104">MR Input 210: Gaze</span></span>

>[!NOTE]
><span data-ttu-id="03381-105">Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="03381-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="03381-106">Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="03381-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="03381-107">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="03381-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="03381-108">Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="03381-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="03381-109">Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](../../../mr-learning-base-01.md).</span><span class="sxs-lookup"><span data-stu-id="03381-109">[A new series of tutorials](../../../mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="03381-110">Lo [sguardo](../../../design/gaze-and-commit.md) è la prima forma di input e rivela le finalità e la consapevolezza dell'utente.</span><span class="sxs-lookup"><span data-stu-id="03381-110">[Gaze](../../../design/gaze-and-commit.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="03381-111">MR input 210 (noto anche come Project Explorer) è un approfondimento dei concetti correlati a sguardi per la realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="03381-111">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="03381-112">Verrà aggiunta la consapevolezza contestuale al cursore e agli ologrammi, sfruttando appieno i vantaggi offerti dall'app per quanto riguarda lo sguardo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="03381-112">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="03381-113">Qui è disponibile un astronauta che consente di apprendere i concetti di sguardi.</span><span class="sxs-lookup"><span data-stu-id="03381-113">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="03381-114">In [Mr nozioni di base 101](../../../develop/unity/tutorials/holograms-101.md), abbiamo un semplice cursore che ha subito seguito lo sguardo.</span><span class="sxs-lookup"><span data-stu-id="03381-114">In [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="03381-115">Oggi stiamo muovendo un passaggio oltre il semplice cursore:</span><span class="sxs-lookup"><span data-stu-id="03381-115">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="03381-116">Il cursore e i nostri ologrammi sono consapevoli del fatto che entrambi cambieranno in base alla posizione dell'utente o alla posizione in cui l'utente *non* è in Cerca.</span><span class="sxs-lookup"><span data-stu-id="03381-116">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="03381-117">Che li rende compatibili con il contesto.</span><span class="sxs-lookup"><span data-stu-id="03381-117">This makes them context-aware.</span></span>
* <span data-ttu-id="03381-118">Si aggiungeranno commenti e suggerimenti al cursore e agli ologrammi per fornire all'utente un maggior contesto sugli elementi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="03381-118">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="03381-119">Questo feedback può essere costituito da audio e oggetti visivi.</span><span class="sxs-lookup"><span data-stu-id="03381-119">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="03381-120">Verranno illustrate le tecniche di destinazione per aiutare gli utenti a raggiungere obiettivi più piccoli.</span><span class="sxs-lookup"><span data-stu-id="03381-120">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="03381-121">Verrà illustrato come attirare l'attenzione dell'utente sugli ologrammi con un indicatore direzionale.</span><span class="sxs-lookup"><span data-stu-id="03381-121">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="03381-122">Ti insegneremo le tecniche per portare gli ologrammi all'utente mentre si sposta in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="03381-122">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="03381-123">I video incorporati in ognuno dei capitoli seguenti sono stati registrati usando una versione precedente di Unity e il Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="03381-123">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="03381-124">Sebbene le istruzioni dettagliate siano accurate e aggiornate, è possibile visualizzare gli script e gli oggetti visivi nei video corrispondenti non aggiornati.</span><span class="sxs-lookup"><span data-stu-id="03381-124">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="03381-125">I video rimangono inclusi per i posteri e perché i concetti trattati sono ancora validi.</span><span class="sxs-lookup"><span data-stu-id="03381-125">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="03381-126">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="03381-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="03381-127">Corso</span><span class="sxs-lookup"><span data-stu-id="03381-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="03381-128"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="03381-128"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="03381-129"><a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="03381-129"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="03381-130">Input MR 210: Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="03381-130">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="03381-131">✔️</span><span class="sxs-lookup"><span data-stu-id="03381-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="03381-132">✔️</span><span class="sxs-lookup"><span data-stu-id="03381-132">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="03381-133">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="03381-133">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="03381-134">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="03381-134">Prerequisites</span></span>

* <span data-ttu-id="03381-135">Un PC Windows 10 configurato con gli [strumenti corretti installati](../../../develop/install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="03381-135">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md).</span></span>
* <span data-ttu-id="03381-136">Alcune funzionalità di programmazione C# di base.</span><span class="sxs-lookup"><span data-stu-id="03381-136">Some basic C# programming ability.</span></span>
* <span data-ttu-id="03381-137">Sono state completate le [nozioni di base 101](../../../develop/unity/tutorials/holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="03381-137">You should have completed [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).</span></span>
* <span data-ttu-id="03381-138">Un dispositivo HoloLens [configurato per lo sviluppo](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="03381-138">A HoloLens device [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="03381-139">File di progetto</span><span class="sxs-lookup"><span data-stu-id="03381-139">Project files</span></span>

* <span data-ttu-id="03381-140">Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) richiesti dal progetto.</span><span class="sxs-lookup"><span data-stu-id="03381-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span> <span data-ttu-id="03381-141">Richiede Unity 2017,2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="03381-141">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="03381-142">Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere.</span><span class="sxs-lookup"><span data-stu-id="03381-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="03381-143">Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span><span class="sxs-lookup"><span data-stu-id="03381-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="03381-144">Errori e note</span><span class="sxs-lookup"><span data-stu-id="03381-144">Errata and Notes</span></span>

* <span data-ttu-id="03381-145">In Visual Studio, "Just My Code" deve essere disabilitato (deselezionato) in strumenti-opzioni >->debug per raggiungere i punti di interruzione nel codice.</span><span class="sxs-lookup"><span data-stu-id="03381-145">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="03381-146">Capitolo 1-installazione di Unity</span><span class="sxs-lookup"><span data-stu-id="03381-146">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="03381-147">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="03381-147">Objectives</span></span>

* <span data-ttu-id="03381-148">Ottimizzare Unity per lo sviluppo di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="03381-148">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="03381-149">Importare gli asset e configurare la scena.</span><span class="sxs-lookup"><span data-stu-id="03381-149">Import assets and setup the scene.</span></span>
* <span data-ttu-id="03381-150">Visualizzare l'astronauta nella HoloLens.</span><span class="sxs-lookup"><span data-stu-id="03381-150">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="03381-151">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="03381-151">Instructions</span></span>

1. <span data-ttu-id="03381-152">Riavviare Unity.</span><span class="sxs-lookup"><span data-stu-id="03381-152">Start Unity.</span></span>
2. <span data-ttu-id="03381-153">Selezionare **Nuovo progetto**.</span><span class="sxs-lookup"><span data-stu-id="03381-153">Select **New Project**.</span></span>
3. <span data-ttu-id="03381-154">Denominare il progetto **ModelExplorer**.</span><span class="sxs-lookup"><span data-stu-id="03381-154">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="03381-155">Immettere location come cartella degli **sguardi** precedentemente non archiviata.</span><span class="sxs-lookup"><span data-stu-id="03381-155">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="03381-156">Assicurati che il progetto sia impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="03381-156">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="03381-157">Fare clic su **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="03381-157">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="03381-158">Impostazioni Unity per HoloLens</span><span class="sxs-lookup"><span data-stu-id="03381-158">Unity settings for HoloLens</span></span>

<span data-ttu-id="03381-159">È necessario informare Unity che l'app che si sta tentando di esportare deve creare una [visualizzazione immersiva](../../../design/app-views.md) anziché una visualizzazione 2D.</span><span class="sxs-lookup"><span data-stu-id="03381-159">We need to let Unity know that the app we are trying to export should create an [immersive view](../../../design/app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="03381-160">Questa operazione viene eseguita aggiungendo HoloLens come dispositivo di realtà virtuale.</span><span class="sxs-lookup"><span data-stu-id="03381-160">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="03381-161">Passare a **Edit > Settings Project > Player**.</span><span class="sxs-lookup"><span data-stu-id="03381-161">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="03381-162">Nel **pannello Inspector** per le impostazioni del lettore selezionare l'icona di **Windows Store** .</span><span class="sxs-lookup"><span data-stu-id="03381-162">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="03381-163">Espandere il gruppo **Impostazioni XR**.</span><span class="sxs-lookup"><span data-stu-id="03381-163">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="03381-164">Nella sezione **Rendering** selezionare la casella di controllo **Virtual Reality Supported** (Realtà virtuale supportata) per aggiungere un nuovo elenco di **SDK per la realtà virtuale**.</span><span class="sxs-lookup"><span data-stu-id="03381-164">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="03381-165">Verificare che **Realtà mista di Windows** sia visualizzato nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="03381-165">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="03381-166">In caso contrario, selezionare il **+** pulsante nella parte inferiore dell'elenco e scegliere **Windows olografico**.</span><span class="sxs-lookup"><span data-stu-id="03381-166">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="03381-167">Successivamente, è necessario impostare il back-end di scripting su .NET.</span><span class="sxs-lookup"><span data-stu-id="03381-167">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="03381-168">Passare a **Edit > Settings (Impostazioni progetto) > Player** (è possibile continuare a eseguire questa operazione dal passaggio precedente).</span><span class="sxs-lookup"><span data-stu-id="03381-168">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="03381-169">Nel **pannello Inspector** per le impostazioni del lettore selezionare l'icona di **Windows Store** .</span><span class="sxs-lookup"><span data-stu-id="03381-169">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="03381-170">Nella sezione **altre impostazioni** di configurazione, assicurarsi che **lo scripting backend** sia impostato su **.NET** .</span><span class="sxs-lookup"><span data-stu-id="03381-170">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="03381-171">Infine, verranno aggiornate le impostazioni di qualità per ottenere prestazioni rapide su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="03381-171">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="03381-172">Passare a **modifica > impostazioni progetto > qualità**.</span><span class="sxs-lookup"><span data-stu-id="03381-172">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="03381-173">Fare clic sulla freccia rivolta verso il basso nella riga **predefinita** sotto l'icona di Windows Store.</span><span class="sxs-lookup"><span data-stu-id="03381-173">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="03381-174">Selezionare **molto basso** per le **app di Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="03381-174">Select **Very Low** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="03381-175">Importa asset progetto</span><span class="sxs-lookup"><span data-stu-id="03381-175">Import project assets</span></span>

1. <span data-ttu-id="03381-176">Fare clic con il pulsante destro del mouse sulla cartella **assets** nel pannello **Project** .</span><span class="sxs-lookup"><span data-stu-id="03381-176">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="03381-177">Fare clic su **Importa pacchetto > pacchetto personalizzato**.</span><span class="sxs-lookup"><span data-stu-id="03381-177">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="03381-178">Individuare i file di progetto scaricati e fare clic su **ModelExplorer. file unitypackage Tools**.</span><span class="sxs-lookup"><span data-stu-id="03381-178">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="03381-179">Fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="03381-179">Click **Open**.</span></span>
5. <span data-ttu-id="03381-180">Al termine del caricamento del pacchetto, fare clic sul pulsante **Importa** .</span><span class="sxs-lookup"><span data-stu-id="03381-180">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="03381-181">Configurare la scena</span><span class="sxs-lookup"><span data-stu-id="03381-181">Setup the scene</span></span>

1. <span data-ttu-id="03381-182">Nella gerarchia eliminare la **fotocamera principale**.</span><span class="sxs-lookup"><span data-stu-id="03381-182">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="03381-183">Nella cartella **HoloToolkit** aprire la cartella di **input** , quindi aprire la cartella **prefabbricates** .</span><span class="sxs-lookup"><span data-stu-id="03381-183">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="03381-184">Trascinare il prefabbricato **MixedRealityCameraParent** dalla cartella **prefabbricates** alla **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="03381-184">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="03381-185">Fare clic con il pulsante destro del mouse sulla **luce direzionale** nella gerarchia e scegliere **Elimina**.</span><span class="sxs-lookup"><span data-stu-id="03381-185">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="03381-186">Nella cartella **ologrammi** trascinare e rilasciare gli asset seguenti nella radice della **gerarchia**:</span><span class="sxs-lookup"><span data-stu-id="03381-186">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="03381-187">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="03381-187">**AstroMan**</span></span>
    * <span data-ttu-id="03381-188">**Luci**</span><span class="sxs-lookup"><span data-stu-id="03381-188">**Lights**</span></span>
    * <span data-ttu-id="03381-189">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="03381-189">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="03381-190">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="03381-190">**SpaceBackground**</span></span>
6. <span data-ttu-id="03381-191">Avviare la **modalità di riproduzione** ▶ per visualizzare l'astronauta.</span><span class="sxs-lookup"><span data-stu-id="03381-191">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="03381-192">Fare clic su **modalità Riproduci** ▶ per **arrestare**.</span><span class="sxs-lookup"><span data-stu-id="03381-192">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="03381-193">Nella cartella **ologrammi** individuare l'asset **fitbox** e trascinarlo nella radice della **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="03381-193">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="03381-194">Selezionare **fitbox** nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="03381-194">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="03381-195">Trascinare la raccolta **astror** dalla **gerarchia** alla proprietà della **raccolta ologramma** di fitbox nel pannello **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="03381-195">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="03381-196">Salvare il progetto</span><span class="sxs-lookup"><span data-stu-id="03381-196">Save the project</span></span>

1. <span data-ttu-id="03381-197">Salvare la nuova scena: **File > Salva scena con nome**.</span><span class="sxs-lookup"><span data-stu-id="03381-197">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="03381-198">Fare clic su **nuova cartella** e denominare la cartella **Scenes**.</span><span class="sxs-lookup"><span data-stu-id="03381-198">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="03381-199">Denominare il file "**ModelExplorer**" e salvarlo nella cartella **Scenes** .</span><span class="sxs-lookup"><span data-stu-id="03381-199">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="03381-200">Compilare il progetto</span><span class="sxs-lookup"><span data-stu-id="03381-200">Build the project</span></span>

1. <span data-ttu-id="03381-201">In Unity selezionare **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="03381-201">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="03381-202">Fare clic su **Aggiungi scene aperte** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="03381-202">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="03381-203">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco **piattaforma** e fare clic su **Cambia piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="03381-203">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="03381-204">Se si sta sviluppando in modo specifico per HoloLens, impostare **dispositivo di destinazione** su **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="03381-204">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="03381-205">In caso contrario, lasciarlo in **qualsiasi dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="03381-205">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="03381-206">Verificare che **tipo di compilazione** sia impostato su **D3D** e che l' **SDK** sia impostato su **installato più recente** (che deve essere SDK 16299 o versione successiva).</span><span class="sxs-lookup"><span data-stu-id="03381-206">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="03381-207">Fare clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="03381-207">Click **Build**.</span></span>
7. <span data-ttu-id="03381-208">Creare una **nuova cartella** denominata "app".</span><span class="sxs-lookup"><span data-stu-id="03381-208">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="03381-209">Fare clic sulla cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="03381-209">Single click the **App** folder.</span></span>
9. <span data-ttu-id="03381-210">Premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="03381-210">Press **Select Folder**.</span></span>

<span data-ttu-id="03381-211">Quando si esegue Unity, viene visualizzata una finestra Esplora file.</span><span class="sxs-lookup"><span data-stu-id="03381-211">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="03381-212">Aprire la cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="03381-212">Open the **App** folder.</span></span>
2. <span data-ttu-id="03381-213">Aprire la **soluzione ModelExplorer di Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="03381-213">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="03381-214">Se si esegue la distribuzione in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="03381-214">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="03381-215">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="03381-215">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="03381-216">Fare clic sulla freccia a discesa accanto al pulsante computer locale e selezionare **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="03381-216">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="03381-217">Immettere **l'indirizzo IP del dispositivo HoloLens** e impostare la modalità di autenticazione su **universale (protocollo non crittografato)**.</span><span class="sxs-lookup"><span data-stu-id="03381-217">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="03381-218">Fare clic su **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="03381-218">Click **Select**.</span></span> <span data-ttu-id="03381-219">Se non si conosce l'indirizzo IP del dispositivo, vedere **impostazioni > rete & Internet > opzioni avanzate**.</span><span class="sxs-lookup"><span data-stu-id="03381-219">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="03381-220">Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="03381-220">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="03381-221">Se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario [associarla a Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="03381-221">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="03381-222">Quando l'app è stata distribuita, chiudere il **fitbox** con un **movimento di selezione**.</span><span class="sxs-lookup"><span data-stu-id="03381-222">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="03381-223">Se si esegue la distribuzione in un auricolare immersivo:</span><span class="sxs-lookup"><span data-stu-id="03381-223">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="03381-224">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="03381-224">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="03381-225">Verificare che la destinazione di distribuzione sia impostata su **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="03381-225">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="03381-226">Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="03381-226">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="03381-227">Quando l'app è stata distribuita, chiudere il **fitbox** estraendo il trigger in un controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="03381-227">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="03381-228">Capitolo 2-feedback del cursore e della destinazione</span><span class="sxs-lookup"><span data-stu-id="03381-228">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="03381-229">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="03381-229">Objectives</span></span>

* <span data-ttu-id="03381-230">Comportamento e progettazione visivi del cursore.</span><span class="sxs-lookup"><span data-stu-id="03381-230">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="03381-231">Feedback del cursore basato su sguardi.</span><span class="sxs-lookup"><span data-stu-id="03381-231">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="03381-232">Feedback dell'ologramma basato su sguardi.</span><span class="sxs-lookup"><span data-stu-id="03381-232">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="03381-233">Il nostro lavoro verrà basato sui principi di progettazione dei cursori, vale a dire:</span><span class="sxs-lookup"><span data-stu-id="03381-233">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="03381-234">Il cursore è sempre presente.</span><span class="sxs-lookup"><span data-stu-id="03381-234">The cursor is always present.</span></span>
* <span data-ttu-id="03381-235">Non lasciare il cursore troppo piccolo o grande.</span><span class="sxs-lookup"><span data-stu-id="03381-235">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="03381-236">Evitare di ostacolare il contenuto.</span><span class="sxs-lookup"><span data-stu-id="03381-236">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="03381-237">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="03381-237">Instructions</span></span>

1. <span data-ttu-id="03381-238">Nella cartella **HoloToolkit\Input\Prefabs** trovare l'asset **InputManager** .</span><span class="sxs-lookup"><span data-stu-id="03381-238">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="03381-239">Trascinare e rilasciare **InputManager** nella **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="03381-239">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="03381-240">Nella cartella **HoloToolkit\Input\Prefabs** trovare il **cursore** asset.</span><span class="sxs-lookup"><span data-stu-id="03381-240">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="03381-241">Trascinare e rilasciare il **cursore** nella **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="03381-241">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="03381-242">Consente di selezionare l'oggetto **InputManager** nella **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="03381-242">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="03381-243">Trascinare l'oggetto **cursore** dalla **gerarchia** nel campo **cursore** di **SimpleSinglePointerSelector** di InputManager, nella parte inferiore del **controllo**.</span><span class="sxs-lookup"><span data-stu-id="03381-243">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![Configurazione semplice del selettore con puntatore singolo](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="03381-245">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="03381-245">Build and Deploy</span></span>

1. <span data-ttu-id="03381-246">Ricompilare l'app da **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="03381-246">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="03381-247">Aprire la **cartella dell'app**.</span><span class="sxs-lookup"><span data-stu-id="03381-247">Open the **App folder**.</span></span>
3. <span data-ttu-id="03381-248">Aprire la **soluzione ModelExplorer di Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="03381-248">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="03381-249">Fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="03381-249">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="03381-250">Osservare il modo in cui viene disegnato il cursore e il modo in cui cambia aspetto se tocca un ologramma.</span><span class="sxs-lookup"><span data-stu-id="03381-250">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="03381-251">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="03381-251">Instructions</span></span>

1. <span data-ttu-id="03381-252">Nel pannello **gerarchia** espandere l'oggetto **astror** -> **GEO_G** -> **Back_Center** .</span><span class="sxs-lookup"><span data-stu-id="03381-252">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="03381-253">Fare doppio clic su **Interactible.cs** per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="03381-253">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="03381-254">Rimuovere il commento dalle righe nei callback **IFocusable. OnFocusEnter ()** e **IFocusable. OnFocusExit ()** in **Interactible.cs**.</span><span class="sxs-lookup"><span data-stu-id="03381-254">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="03381-255">Questi vengono chiamati dal InputManager del Toolkit di realtà mista quando lo stato attivo (tramite sguardo o con il puntatore del controller) entra e esce dall'oggetto Collider di GameObject specifico.</span><span class="sxs-lookup"><span data-stu-id="03381-255">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
><span data-ttu-id="03381-256">Usiamo `EnableKeyword` e `DisableKeyword` versioni successive.</span><span class="sxs-lookup"><span data-stu-id="03381-256">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="03381-257">Per usarle nella propria app con lo shader standard del Toolkit, è necessario seguire le [linee guida di Unity per accedere ai materiali tramite script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span><span class="sxs-lookup"><span data-stu-id="03381-257">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="03381-258">In questo caso sono già state incluse le [tre varianti del materiale evidenziato](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) necessario nella cartella Resources (ricerca dei tre materiali con evidenziazione nel nome).</span><span class="sxs-lookup"><span data-stu-id="03381-258">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="03381-259">Compilazione e distribuzione</span><span class="sxs-lookup"><span data-stu-id="03381-259">Build and Deploy</span></span>

1. <span data-ttu-id="03381-260">Come in precedenza, compilare il progetto e distribuirlo in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="03381-260">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="03381-261">Osservare cosa accade quando lo sguardo è mirato a un oggetto e in caso contrario.</span><span class="sxs-lookup"><span data-stu-id="03381-261">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="03381-262">Capitolo 3-tecniche di targeting</span><span class="sxs-lookup"><span data-stu-id="03381-262">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="03381-263">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="03381-263">Objectives</span></span>

* <span data-ttu-id="03381-264">Semplificare la destinazione degli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="03381-264">Make it easier to target holograms.</span></span>
* <span data-ttu-id="03381-265">Stabilizzare i movimenti della testa naturale.</span><span class="sxs-lookup"><span data-stu-id="03381-265">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="03381-266">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="03381-266">Instructions</span></span>

1. <span data-ttu-id="03381-267">Nel pannello **gerarchia** selezionare l'oggetto **InputManager** .</span><span class="sxs-lookup"><span data-stu-id="03381-267">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="03381-268">Nel pannello **Inspector** trovare lo script **stabilizzatore dello sguardo** .</span><span class="sxs-lookup"><span data-stu-id="03381-268">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="03381-269">Fare clic su di esso per aprirlo in Visual Studio, se si vuole dare un'occhiata.</span><span class="sxs-lookup"><span data-stu-id="03381-269">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="03381-270">Questo script scorre gli esempi di dati di Raycast e consente di stabilizzare lo sguardo dell'utente per la destinazione della precisione.</span><span class="sxs-lookup"><span data-stu-id="03381-270">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="03381-271">Nel **controllo** è possibile modificare il valore dei **campioni di stabilità archiviati** .</span><span class="sxs-lookup"><span data-stu-id="03381-271">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="03381-272">Questo valore rappresenta il numero di campioni di cui lo stabilizzatore esegue l'iterazione per calcolare il valore stabilizzato.</span><span class="sxs-lookup"><span data-stu-id="03381-272">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="03381-273">Capitolo 4-indicatore direzionale</span><span class="sxs-lookup"><span data-stu-id="03381-273">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="03381-274">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="03381-274">Objectives</span></span>

* <span data-ttu-id="03381-275">Aggiungere un indicatore direzionale sul cursore per individuare gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="03381-275">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="03381-276">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="03381-276">Instructions</span></span>

<span data-ttu-id="03381-277">Verrà usato il file **DirectionIndicator.cs** che:</span><span class="sxs-lookup"><span data-stu-id="03381-277">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="03381-278">Mostra l'indicatore direzionale se l'utente non sta guardando gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="03381-278">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="03381-279">Nascondere l'indicatore direzionale se l'utente sta guardando gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="03381-279">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="03381-280">Aggiornare l'indicatore direzionale in modo che punti agli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="03381-280">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="03381-281">È possibile iniziare subito.</span><span class="sxs-lookup"><span data-stu-id="03381-281">Let's get started.</span></span>

1. <span data-ttu-id="03381-282">Fare clic sull'oggetto **astror** nel pannello **gerarchia** e **fare clic sulla freccia** per espanderlo.</span><span class="sxs-lookup"><span data-stu-id="03381-282">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="03381-283">Nel pannello **gerarchia** selezionare l'oggetto **DirectionalIndicator** in **Astron**.</span><span class="sxs-lookup"><span data-stu-id="03381-283">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="03381-284">Nel pannello **Inspector** fare clic sul pulsante **Add Component** .</span><span class="sxs-lookup"><span data-stu-id="03381-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="03381-285">Nel menu digitare nell' **indicatore di direzione** della casella di ricerca.</span><span class="sxs-lookup"><span data-stu-id="03381-285">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="03381-286">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="03381-286">Select the search result.</span></span>
5. <span data-ttu-id="03381-287">Nel pannello **gerarchia** trascinare e rilasciare l'oggetto **cursore** sulla proprietà **Cursor** del **controllo**.</span><span class="sxs-lookup"><span data-stu-id="03381-287">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="03381-288">Nel pannello **progetto** , nella cartella **ologrammi** , trascinare l'asset **DirectionalIndicator** sulla proprietà **indicatore direzionale** nel **controllo**.</span><span class="sxs-lookup"><span data-stu-id="03381-288">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="03381-289">Compilare e distribuire l'app.</span><span class="sxs-lookup"><span data-stu-id="03381-289">Build and deploy the app.</span></span>
8. <span data-ttu-id="03381-290">Osservare come l'oggetto indicatore direzionale aiuta a trovare l'astronauta.</span><span class="sxs-lookup"><span data-stu-id="03381-290">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="03381-291">Capitolo 5-Billboard</span><span class="sxs-lookup"><span data-stu-id="03381-291">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="03381-292">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="03381-292">Objectives</span></span>

* <span data-ttu-id="03381-293">Usare il tabellone per fare in modo che gli ologrammi siano sempre volti verso l'utente.</span><span class="sxs-lookup"><span data-stu-id="03381-293">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="03381-294">Verrà usato il file **Billboard.cs** per tenere un GameObject orientato in modo che sia sempre attivo per l'utente.</span><span class="sxs-lookup"><span data-stu-id="03381-294">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="03381-295">Nel pannello **gerarchia** selezionare l'oggetto **Astron** .</span><span class="sxs-lookup"><span data-stu-id="03381-295">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="03381-296">Nel pannello **Inspector** fare clic sul pulsante **Add Component** .</span><span class="sxs-lookup"><span data-stu-id="03381-296">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="03381-297">Nel menu digitare nella casella di ricerca **Billboard**.</span><span class="sxs-lookup"><span data-stu-id="03381-297">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="03381-298">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="03381-298">Select the search result.</span></span>
4. <span data-ttu-id="03381-299">Nel **controllo** impostare l' **asse pivot** su **Y**.</span><span class="sxs-lookup"><span data-stu-id="03381-299">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="03381-300">Prova</span><span class="sxs-lookup"><span data-stu-id="03381-300">Try it!</span></span> <span data-ttu-id="03381-301">Compilare e distribuire l'app come prima.</span><span class="sxs-lookup"><span data-stu-id="03381-301">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="03381-302">Scopri in che modo l'oggetto Billboard si presenta indipendentemente dalla modalità di modifica del punto di vista.</span><span class="sxs-lookup"><span data-stu-id="03381-302">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="03381-303">Eliminare lo script da **astroname** per il momento.</span><span class="sxs-lookup"><span data-stu-id="03381-303">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="03381-304">Capitolo 6-Tag-Along</span><span class="sxs-lookup"><span data-stu-id="03381-304">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="03381-305">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="03381-305">Objectives</span></span>

* <span data-ttu-id="03381-306">Usare Tag-Along per fare in modo che gli ologrammi vengano seguiti dalla stanza.</span><span class="sxs-lookup"><span data-stu-id="03381-306">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="03381-307">Quando si lavora su questo problema, verranno illustrati i vincoli di progettazione seguenti:</span><span class="sxs-lookup"><span data-stu-id="03381-307">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="03381-308">Il contenuto deve essere sempre un'occhiata.</span><span class="sxs-lookup"><span data-stu-id="03381-308">Content should always be a glance away.</span></span>
* <span data-ttu-id="03381-309">Il contenuto non deve essere nel modo previsto.</span><span class="sxs-lookup"><span data-stu-id="03381-309">Content should not be in the way.</span></span>
* <span data-ttu-id="03381-310">Il contenuto del blocco Head è scomodo.</span><span class="sxs-lookup"><span data-stu-id="03381-310">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="03381-311">La soluzione usata in questo articolo prevede l'uso di un approccio "tag-along".</span><span class="sxs-lookup"><span data-stu-id="03381-311">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="03381-312">Un oggetto tag-along non lascia completamente la visualizzazione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="03381-312">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="03381-313">È possibile considerare un tag come un oggetto collegato alla testa dell'utente tramite bande di gomma.</span><span class="sxs-lookup"><span data-stu-id="03381-313">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="03381-314">Quando l'utente si sposta, il contenuto rimarrà in una semplice occhiata scorrendo verso il bordo della visualizzazione senza uscire completamente.</span><span class="sxs-lookup"><span data-stu-id="03381-314">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="03381-315">Quando l'utente guarda l'oggetto tag-along, viene visualizzato in modo più completo.</span><span class="sxs-lookup"><span data-stu-id="03381-315">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="03381-316">Verrà usato il file **SimpleTagalong.cs** che:</span><span class="sxs-lookup"><span data-stu-id="03381-316">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="03381-317">Determinare se l'oggetto Tag-Along si trova all'interno dei limiti della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="03381-317">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="03381-318">Se non è presente nella vista tronco, posizionare il Tag-Along su parzialmente all'interno della vista tronco.</span><span class="sxs-lookup"><span data-stu-id="03381-318">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="03381-319">In caso contrario, posizionare il Tag-Along su una distanza predefinita dall'utente.</span><span class="sxs-lookup"><span data-stu-id="03381-319">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="03381-320">Per eseguire questa operazione, è necessario prima di tutto modificare lo script **Interactible.cs** per chiamare **TagalongAction**.</span><span class="sxs-lookup"><span data-stu-id="03381-320">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="03381-321">Modificare **Interactible.cs** completando il codice esercizio 6. a (rimuovendo il commento dalle righe da 84 a 87).</span><span class="sxs-lookup"><span data-stu-id="03381-321">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="03381-322">Lo script **InteractibleAction.cs** , associato a **Interactible.cs** , esegue azioni personalizzate quando si toccano gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="03381-322">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="03381-323">In questo caso, verrà usato uno specifico per il tag-along.</span><span class="sxs-lookup"><span data-stu-id="03381-323">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="03381-324">Nella cartella **Scripts** fare clic su **TagalongAction.cs** asset per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="03381-324">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="03381-325">Completare l'esercizio di codifica o sostituirlo con il seguente:</span><span class="sxs-lookup"><span data-stu-id="03381-325">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="03381-326">Nella parte superiore della **gerarchia**, nella barra di ricerca digitare **ChestButton_Center** e selezionare il risultato.</span><span class="sxs-lookup"><span data-stu-id="03381-326">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="03381-327">Nel pannello **Inspector** fare clic sul pulsante **Add Component** .</span><span class="sxs-lookup"><span data-stu-id="03381-327">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="03381-328">Nel menu digitare nella casella di ricerca **azione Tagalong**.</span><span class="sxs-lookup"><span data-stu-id="03381-328">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="03381-329">Selezionare il risultato della ricerca.</span><span class="sxs-lookup"><span data-stu-id="03381-329">Select the search result.</span></span>
  * <span data-ttu-id="03381-330">Nella cartella **ologrammi** trovare l'asset **Tagalong** .</span><span class="sxs-lookup"><span data-stu-id="03381-330">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="03381-331">Consente di selezionare l'oggetto **ChestButton_Center** nella **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="03381-331">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="03381-332">Trascinare e rilasciare l'oggetto **TagAlong** dal pannello del **progetto** nel **controllo** nella proprietà **oggetto in TagAlong** .</span><span class="sxs-lookup"><span data-stu-id="03381-332">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="03381-333">Trascinare l'oggetto **azione Tagalong** da **Inspector** nel campo **azione Interactible** nello script **Interactible** .</span><span class="sxs-lookup"><span data-stu-id="03381-333">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="03381-334">Fare doppio clic sullo script **TagalongAction** per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="03381-334">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Configurazione di Interactible](images/holograms210-interactible.png)

<span data-ttu-id="03381-336">È necessario aggiungere quanto segue:</span><span class="sxs-lookup"><span data-stu-id="03381-336">We need to add the following:</span></span>

* <span data-ttu-id="03381-337">Aggiungere funzionalità alla funzione PerformAction nello script TagalongAction (Ereditato da InteractibleAction).</span><span class="sxs-lookup"><span data-stu-id="03381-337">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="03381-338">Aggiungere il tabellone all'oggetto guardato su e impostare l'asse pivot su XY.</span><span class="sxs-lookup"><span data-stu-id="03381-338">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="03381-339">Aggiungere quindi Tag-Along semplici all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="03381-339">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="03381-340">Ecco la nostra soluzione, di **TagalongAction.cs**:</span><span class="sxs-lookup"><span data-stu-id="03381-340">Here's our solution, from **TagalongAction.cs**:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* <span data-ttu-id="03381-341">Prova</span><span class="sxs-lookup"><span data-stu-id="03381-341">Try it!</span></span> <span data-ttu-id="03381-342">Compilare e distribuire l'app.</span><span class="sxs-lookup"><span data-stu-id="03381-342">Build and deploy the app.</span></span>
* <span data-ttu-id="03381-343">Osservare il modo in cui il contenuto segue il centro del punto di controllo, ma non continuamente e senza bloccarlo.</span><span class="sxs-lookup"><span data-stu-id="03381-343">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>