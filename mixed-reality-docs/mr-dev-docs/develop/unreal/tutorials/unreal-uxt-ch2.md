---
title: 2. Inizializzazione del progetto e prima applicazione
description: Parte 2 di 6 in una serie di esercitazioni per la creazione di un'app per gli scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 464df846d0fc6e1bd22ee3862adcdf110c377728
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609652"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="65a06-104">2. Inizializzazione del progetto e prima applicazione</span><span class="sxs-lookup"><span data-stu-id="65a06-104">2. Initializing your project and first application</span></span>

<span data-ttu-id="65a06-105">Nella prima esercitazione si inizia con un nuovo progetto Unreal e si abilita il plug-in HoloLens, si crea e si illumina un livello e si aggiungono pezzi degli scacchi.</span><span class="sxs-lookup"><span data-stu-id="65a06-105">In the first tutorial, you'll start out with a new Unreal project and enable the HoloLens plugin, create and light a level, and add chess pieces.</span></span> <span data-ttu-id="65a06-106">Poiché per tutti i materiali e gli oggetti 3D verranno usati gli asset predefiniti, non occorre preoccuparsi di modellare alcunché.</span><span class="sxs-lookup"><span data-stu-id="65a06-106">You'll be using our pre-made assets for all 3D objects and materials, so don't worry about modeling anything yourself.</span></span> <span data-ttu-id="65a06-107">Al termine di questa esercitazione, sarà disponibile un'area di disegno vuota, pronta per lo sviluppo in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="65a06-107">By the end of this tutorial, you'll have a blank canvas that's ready for mixed reality.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="65a06-108">Verificare di soddisfare tutti i prerequisiti indicati nella [Guida introduttiva](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1).</span><span class="sxs-lookup"><span data-stu-id="65a06-108">Make sure you have all the prerequisites from the [Getting Started](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="65a06-109">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="65a06-109">Objectives</span></span>

* <span data-ttu-id="65a06-110">Configurazione di un progetto Unreal per lo sviluppo con HoloLens</span><span class="sxs-lookup"><span data-stu-id="65a06-110">Configuring an Unreal project for HoloLens development</span></span>
* <span data-ttu-id="65a06-111">Importazione di asset e configurazione di una scena</span><span class="sxs-lookup"><span data-stu-id="65a06-111">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="65a06-112">Creazione di attori ed eventi a livello di script con progetti</span><span class="sxs-lookup"><span data-stu-id="65a06-112">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="65a06-113">Creazione di un nuovo progetto Unreal</span><span class="sxs-lookup"><span data-stu-id="65a06-113">Creating a new Unreal project</span></span>

<span data-ttu-id="65a06-114">Prima di tutto, è necessario un progetto su cui lavorare.</span><span class="sxs-lookup"><span data-stu-id="65a06-114">The first thing you need is a project to work with.</span></span> <span data-ttu-id="65a06-115">Se si sviluppa in Unreal per la prima volta, è necessario [scaricare i file di supporto](https://docs.microsoft.com/windows/mixed-reality/develop/unreal/tutorials/unreal-uxt-ch6#packaging-and-deploying-the-app-via-device-portal) dal launcher Epic.</span><span class="sxs-lookup"><span data-stu-id="65a06-115">If you're a first-time Unreal developer, you'll need to [download supporting files](https://docs.microsoft.com/windows/mixed-reality/develop/unreal/tutorials/unreal-uxt-ch6#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="65a06-116">Avvia Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="65a06-116">Launch Unreal Engine</span></span>

2. <span data-ttu-id="65a06-117">Seleziona **Games** (Giochi) in **New Project Categories** (Categorie nuovo progetto) e fai clic su **Next** (Avanti).</span><span class="sxs-lookup"><span data-stu-id="65a06-117">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![Selezionare il modello di progetto Games (Giochi)](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="65a06-119">Seleziona il modello **Blank** (Vuoto) e fai clic su **Next** (Avanti).</span><span class="sxs-lookup"><span data-stu-id="65a06-119">Select the **Blank** Template and click **Next**.</span></span> 

![Selezionare il modello vuoto](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="65a06-121">Impostare **C++** , **Scalable 3D or 2D, Mobile/Tablet** (3D o 2D scalabile, Cellulare/Tablet) e **No Starter Content** (Nessun contenuto iniziale) come **Project Settings** (Impostazioni progetto) e quindi scegliere un percorso di salvataggio e fare clic su **Create Project** (Crea progetto).</span><span class="sxs-lookup"><span data-stu-id="65a06-121">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**, then choose a save location and click **Create Project**.</span></span> 

> [!NOTE]
> <span data-ttu-id="65a06-122">Devi selezionare un progetto C++ anziché un progetto Blueprint per compilare il plug-in UX Tools, che verrà configurato più avanti nella sezione 4.</span><span class="sxs-lookup"><span data-stu-id="65a06-122">You must select a C++ project rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later on in section 4.</span></span>

![Impostazioni iniziali del progetto](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="65a06-124">Il progetto dovrebbe aprirsi automaticamente nell'editor Unreal e a quel punto puoi passare alla sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="65a06-124">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="65a06-125">Abilitazione dei plug-in necessari</span><span class="sxs-lookup"><span data-stu-id="65a06-125">Enabling required plugins</span></span>

<span data-ttu-id="65a06-126">Prima di iniziare ad aggiungere oggetti alla scena, è necessario abilitare due plug-in.</span><span class="sxs-lookup"><span data-stu-id="65a06-126">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="65a06-127">Apri **Edit > Plugins** (Modifica > Plug-in) e seleziona **Augmented Reality** (Realtà aumentata) nell'elenco di opzioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="65a06-127">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="65a06-128">Scorri verso il basso fino a **HoloLens** e seleziona **Enabled** (Abilitato).</span><span class="sxs-lookup"><span data-stu-id="65a06-128">Scroll down to **HoloLens** and check **Enabled**.</span></span> 

![Abilitazione dei plug-in HoloLens](images/unreal-uxt/2-plugins.PNG)

2. <span data-ttu-id="65a06-130">Seleziona **Virtual Reality** (Realtà virtuale) nell'elenco di opzioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="65a06-130">Select **Virtual Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="65a06-131">Scorri verso il basso fino a **Microsoft Windows Mixed Reality**, seleziona **Enabled** (Abilitato) e riavvia l'editor.</span><span class="sxs-lookup"><span data-stu-id="65a06-131">Scroll down to **Microsoft Windows Mixed Reality**, check **Enabled**, and restart your editor.</span></span> 

![Abilitazione del plug-in Windows Mixed Reality](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> <span data-ttu-id="65a06-133">Per lo sviluppo di HoloLens 2 sono necessari entrambi i plug-in.</span><span class="sxs-lookup"><span data-stu-id="65a06-133">Both plugins are required for HoloLens 2 development.</span></span>

<span data-ttu-id="65a06-134">Con i plug-in abilitati, il livello vuoto è pronto per l'uso da parte dell'azienda.</span><span class="sxs-lookup"><span data-stu-id="65a06-134">With the plugins enabled, your empty level is ready for company.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="65a06-135">Creazione di un livello</span><span class="sxs-lookup"><span data-stu-id="65a06-135">Creating a level</span></span>
<span data-ttu-id="65a06-136">L'attività successiva consiste nel creare una configurazione di gioco con un punto iniziale e un cubo per riferimento e scala.</span><span class="sxs-lookup"><span data-stu-id="65a06-136">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="65a06-137">Seleziona **File > New Level** (File > Nuovo livello) e scegli **Empty Level** (Livello vuoto).</span><span class="sxs-lookup"><span data-stu-id="65a06-137">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="65a06-138">In questa fase, la scena predefinita nel riquadro di visualizzazione dovrebbe essere vuota.</span><span class="sxs-lookup"><span data-stu-id="65a06-138">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="65a06-139">Seleziona **Basic** (Base) nella scheda **Modes** (Modalità) e trascina **PlayerStart** nella scena.</span><span class="sxs-lookup"><span data-stu-id="65a06-139">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="65a06-140">Impostare **Location** (Posizione) su **X = 0**, **Y = 0** e **Z = 0** nella scheda **Details** (Dettagli) per collocare l'utente al centro della scena all'avvio dell'app.</span><span class="sxs-lookup"><span data-stu-id="65a06-140">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab to set the user at the center of the scene when the app starts up.</span></span>

![Riquadro di visualizzazione con PlayerStart](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="65a06-142">Trascina un oggetto **Cube** (Cubo) dalla scheda **Basic** (Base) nella scena.</span><span class="sxs-lookup"><span data-stu-id="65a06-142">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="65a06-143">Imposta **Location** (Posizione) su **X = 50**, **Y = 0** e **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="65a06-143">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="65a06-144">In questo modo, il cubo viene posizionato a 50 cm di distanza dal giocatore al momento dell'avvio.</span><span class="sxs-lookup"><span data-stu-id="65a06-144">to position the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="65a06-145">Imposta **Scale** (Scala) su **X = 0.2**, **Y = 0.2** e **Z = 0.2** per ridurre le dimensioni del cubo.</span><span class="sxs-lookup"><span data-stu-id="65a06-145">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="65a06-146">Il cubo non sarà visibile finché non viene aggiunta una luce alla scena, che è l'ultima attività da eseguire prima del test.</span><span class="sxs-lookup"><span data-stu-id="65a06-146">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="65a06-147">Passa alla scheda **Lights** (Luci) nel pannello **Modes** (Modalità) e trascina un oggetto **Directional Light** (Luce direzionale) nella scena.</span><span class="sxs-lookup"><span data-stu-id="65a06-147">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="65a06-148">Posiziona la luce al di sopra di **PlayerStart** perché sia visibile.</span><span class="sxs-lookup"><span data-stu-id="65a06-148">Position the light above **PlayerStart** so you can see it.</span></span>

![Riquadro di visualizzazione con aggiunta di luce](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="65a06-150">Passare a **File > Save Current** (File > Salva corrente), assegnare al livello il nome **Main** e selezionare **Save** (Salva).</span><span class="sxs-lookup"><span data-stu-id="65a06-150">Go to **File > Save Current**, name your level **Main**, and select **Save**.</span></span> 

<span data-ttu-id="65a06-151">Una volta impostata la scena, seleziona **Play** (Riproduci) sulla barra degli strumenti per vedere il cubo in azione.</span><span class="sxs-lookup"><span data-stu-id="65a06-151">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="65a06-152">Quando avrai terminato di ammirare il tuo lavoro, premi **ESC** per arrestare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="65a06-152">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![Un cubo nel riquadro di visualizzazione](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="65a06-154">Ora che la scena è configurata, è possibile iniziare ad aggiungere la scacchiera e i pezzi per completare l'ambiente dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="65a06-154">Now that the scene is set up, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="65a06-155">Importazione di asset</span><span class="sxs-lookup"><span data-stu-id="65a06-155">Importing assets</span></span>
<span data-ttu-id="65a06-156">Al momento la scena è un po' spoglia, ma puoi arricchirla importando asset predefiniti nel progetto.</span><span class="sxs-lookup"><span data-stu-id="65a06-156">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="65a06-157">Scaricare e decomprimere la cartella di asset [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) con [7-zip](https://www.7-zip.org/).</span><span class="sxs-lookup"><span data-stu-id="65a06-157">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder using [7-zip](https://www.7-zip.org/).</span></span>

2. <span data-ttu-id="65a06-158">Selezionare **Add New > New Folder** (Aggiungi nuovo > Nuova cartella) in **Content Browser** (Browser contenuto) e assegnare alla cartella il nome **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="65a06-158">Select **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="65a06-159">Fare doppio clic sulla nuova cartella in cui verranno importati gli asset 3D.</span><span class="sxs-lookup"><span data-stu-id="65a06-159">Double-click the new folder where you'll import the 3D assets.</span></span>

![Visualizzare o nascondere il pannello delle origini](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="65a06-161">Fare clic su **Import** (Importa) in **Content Browser** (Browser contenuto), selezionare tutti gli elementi inclusi nella cartella degli asset decompressa e fare clic su **Open** (Apri).</span><span class="sxs-lookup"><span data-stu-id="65a06-161">Select **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="65a06-162">Gli asset includono le mesh degli oggetti 3D per la scacchiera e i pezzi in formato FBX e le mappe di texture in formato TGA che verranno usate per i materiali.</span><span class="sxs-lookup"><span data-stu-id="65a06-162">Assets include the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="65a06-163">Quando viene visualizzata la finestra FBX Import Options (Opzioni di importazione FBX), espandi la sezione **Material** (Materiale) e modifica **Material Import Method** (Metodo importazione materiale) in **Do Not Create Material** (Non creare materiale).</span><span class="sxs-lookup"><span data-stu-id="65a06-163">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="65a06-164">Selezionare **Import All** (Importa tutto).</span><span class="sxs-lookup"><span data-stu-id="65a06-164">Select **Import All**.</span></span>

![Opzioni importazione FBX](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="65a06-166">Non serve fare altro per gli asset.</span><span class="sxs-lookup"><span data-stu-id="65a06-166">That's all you need to do for the assets.</span></span> <span data-ttu-id="65a06-167">Il prossimo set di attività consiste nel creare i blocchi predefiniti dell'applicazione con i progetti.</span><span class="sxs-lookup"><span data-stu-id="65a06-167">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="65a06-168">Aggiunta di progetti</span><span class="sxs-lookup"><span data-stu-id="65a06-168">Adding blueprints</span></span>

1. <span data-ttu-id="65a06-169">Selezionare **Add New > New Folder** (Aggiungi nuovo > Nuova cartella) in **Content Browser** (Browser contenuto) e assegnare alla cartella il nome **Blueprints**.</span><span class="sxs-lookup"><span data-stu-id="65a06-169">Select **Add New > New Folder** in the **Content Browser** and name it **Blueprints**.</span></span> 

> [!NOTE]
> <span data-ttu-id="65a06-170">I [progetti](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html) sono asset speciali che forniscono un'interfaccia basata su nodi per la creazione di nuovi tipi di attori ed eventi a livello di script.</span><span class="sxs-lookup"><span data-stu-id="65a06-170">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="65a06-171">Fai doppio clic nella cartella **Blueprints** (Progetti), quindi fai clic con il pulsante destro del mouse e scegli **Blueprint Class** (Classe progetto).</span><span class="sxs-lookup"><span data-stu-id="65a06-171">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="65a06-172">Seleziona **Actor** (Attore) e assegna al nuovo progetto il nome **Board** (Tavola).</span><span class="sxs-lookup"><span data-stu-id="65a06-172">Select **Actor** and name the blueprint **Board**.</span></span> 

![Selezionare una classe padre per il progetto](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="65a06-174">Il nuovo progetto **Board** (Tavola) verrà incluso nella cartella **Blueprints** (Progetti) mostrata nello screenshot seguente.</span><span class="sxs-lookup"><span data-stu-id="65a06-174">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![Nuovo progetto Board (Tavola)](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="65a06-176">È tutto pronto per iniziare ad aggiungere materiali agli oggetti creati.</span><span class="sxs-lookup"><span data-stu-id="65a06-176">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="65a06-177">Uso dei materiali</span><span class="sxs-lookup"><span data-stu-id="65a06-177">Working with materials</span></span>
<span data-ttu-id="65a06-178">Gli oggetti che hai creato sono grigi per impostazione predefinita e questo non li rende particolarmente gradevoli dal punto di vista estetico.</span><span class="sxs-lookup"><span data-stu-id="65a06-178">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="65a06-179">L'ultima serie di attività di questa esercitazione consiste appunto nell'aggiungere materiali e mesh agli oggetti.</span><span class="sxs-lookup"><span data-stu-id="65a06-179">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="65a06-180">Fai doppio clic su **Board** (Tavola) per aprire l'editor dei progetti.</span><span class="sxs-lookup"><span data-stu-id="65a06-180">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="65a06-181">Selezionare **Add Component > Scene** (Aggiungi componente > Scena) nel pannello **Components** (Componenti) e assegnare alla scena il nome **Root**.</span><span class="sxs-lookup"><span data-stu-id="65a06-181">Select **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="65a06-182">Nota che **Root** (Radice) viene visualizzato come elemento figlio di **DefaultSceneRoot** nello screenshot seguente:</span><span class="sxs-lookup"><span data-stu-id="65a06-182">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![Sostituzione della radice nel progetto](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="65a06-184">Trascina **Root** (Radice) su **DefaultSceneRoot** per sostituire la radice ed eliminare la sfera nel viewport.</span><span class="sxs-lookup"><span data-stu-id="65a06-184">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![Sostituzione della radice](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="65a06-186">Selezionare **Add Component > Static Mesh** (Aggiungi componente > Mesh statica) nel pannello **Components** (Componenti) e assegnare alla mesh il nome **SM_Board**.</span><span class="sxs-lookup"><span data-stu-id="65a06-186">Select **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="65a06-187">Verrà visualizzata come oggetto figlio in **Root** (Radice).</span><span class="sxs-lookup"><span data-stu-id="65a06-187">It will appear as a child object under **Root**.</span></span>

![Aggiunta di una mesh statica](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="65a06-189">Selezionare **SM_Board**, scorrere verso il basso fino alla sezione **Static Mesh** (Mesh statica) del pannello **Details** (Dettagli) e selezionare **ChessBoard** nell'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="65a06-189">Select **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![Mesh Tavola nel riquadro di visualizzazione](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="65a06-191">Sempre nel pannello **Details** (Dettagli) espandere la sezione **Materials** (Materiali) e selezionare **Create New Asset > Material** (Crea nuovo asset > Materiale) nell'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="65a06-191">Still in the **Details** panel, expand the **Materials** section and select **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="65a06-192">Assegna a questo materiale il nome **M_ChessBoard** (M_Scacchiera) e salvalo nella cartella **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="65a06-192">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![Creare un nuovo materiale](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="65a06-194">Fai doppio clic sull'immagine del materiale **M_ChessBoard** (M_Scacchiera) per aprire l'editor dei materiali.</span><span class="sxs-lookup"><span data-stu-id="65a06-194">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![Aprire l'editor dei materiali](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="65a06-196">Nell'editor dei materiali fai clic con il pulsante destro del mouse e cerca **Texture Sample** (Esempio di texture).</span><span class="sxs-lookup"><span data-stu-id="65a06-196">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="65a06-197">Espandi la sezione **Material Expression Texture Base** (Espressione materiale - Base texture) nel pannello **Details** (Dettagli) e imposta **Texture** su **ChessBoard_Albedo** (Scacchiera_Albedo).</span><span class="sxs-lookup"><span data-stu-id="65a06-197">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="65a06-198">Trascina il segnaposto di output **RGB** sul segnaposto Base Color (Colore di base) di **M_ChessBoard** (M_Scacchiera).</span><span class="sxs-lookup"><span data-stu-id="65a06-198">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![Impostare il colore di base](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="65a06-200">Ripetere altre quattro volte il passaggio precedente per creare altri quattro nodi **Texture Sample** (Esempio di texture) con le impostazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="65a06-200">Repeat the previous step 4 more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="65a06-201">Imposta **Texture** su **ChessBoard_AO** (Scacchiera_OA) e collega **RGB** al segnaposto **Ambient Occlusion** (Occlusione ambiente).</span><span class="sxs-lookup"><span data-stu-id="65a06-201">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="65a06-202">Imposta **Texture** su **ChessBoard_Metal**(Scacchiera_Metallo) e collega **RGB** al segnaposto **Metallic** (Metallico).</span><span class="sxs-lookup"><span data-stu-id="65a06-202">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="65a06-203">Imposta **Texture** su **ChessBoard_Normal** (Scacchiera_Normale) e collega **RGB** al segnaposto **Normal** (Normale).</span><span class="sxs-lookup"><span data-stu-id="65a06-203">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="65a06-204">Imposta **Texture** su **ChessBoard_Rough**(Scacchiera_Ruvido) e collega **RGB** al segnaposto **Roughness** (Ruvidezza).</span><span class="sxs-lookup"><span data-stu-id="65a06-204">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="65a06-205">Fare clic su **Save**.</span><span class="sxs-lookup"><span data-stu-id="65a06-205">Click **Save**.</span></span> 

![Associare le texture rimanenti](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="65a06-207">Prima di continuare, verificare che la configurazione del materiale corrisponda allo screenshot riportato sopra.</span><span class="sxs-lookup"><span data-stu-id="65a06-207">Make sure your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="65a06-208">Popolamento della scena</span><span class="sxs-lookup"><span data-stu-id="65a06-208">Populating the scene</span></span>
<span data-ttu-id="65a06-209">Se torni al progetto **Board** (Tavola), noterai che il materiale appena creato è stato applicato.</span><span class="sxs-lookup"><span data-stu-id="65a06-209">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="65a06-210">A questo punto devi solo configurare la scena.</span><span class="sxs-lookup"><span data-stu-id="65a06-210">All that's left is setting up the scene!</span></span> <span data-ttu-id="65a06-211">Prima di tutto, modifica le proprietà seguenti per assicurarti che la scacchiera sia di dimensioni ragionevoli e disposta nella corretta angolazione quando viene inserita nella scena:</span><span class="sxs-lookup"><span data-stu-id="65a06-211">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="65a06-212">Imposta **Scale** (Scala) su **(0.05, 0.05, 0.05)** e **Z Rotation** (Rotazione Z) su **90**.</span><span class="sxs-lookup"><span data-stu-id="65a06-212">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="65a06-213">Fai clic su **Compile** (Compila) sulla barra degli strumenti in alto, quindi su **Save** (Salva) e torna alla finestra principale.</span><span class="sxs-lookup"><span data-stu-id="65a06-213">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![Scacchiera con materiale applicato](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="65a06-215">Fai clic con il pulsante destro del mouse su **Cube > Edit > Delete** (Cubo > Modifica > Elimina) e trascina **Board** (Tavola) da **Content Browser** (Browser contenuto) nel viewport.</span><span class="sxs-lookup"><span data-stu-id="65a06-215">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="65a06-216">Imposta **Location** (Posizione) su **X = 80**, **Y = 0** e **Z = 20**.</span><span class="sxs-lookup"><span data-stu-id="65a06-216">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="65a06-217">Selezionare il pulsante **Play** per visualizzare la nuova scacchiera nel livello.</span><span class="sxs-lookup"><span data-stu-id="65a06-217">Select the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="65a06-218">Premi **ESC** per tornare all'editor.</span><span class="sxs-lookup"><span data-stu-id="65a06-218">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="65a06-219">A questo punto creerai un pezzo degli scacchi seguendo la stessa procedura usata per la scacchiera:</span><span class="sxs-lookup"><span data-stu-id="65a06-219">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="65a06-220">Passare alla cartella **Blueprints** (Progetti), fare clic con il pulsante destro del mouse e scegliere **Blueprint Class** (Classe progetto) e **Actor** (Attore).</span><span class="sxs-lookup"><span data-stu-id="65a06-220">Go to the **Blueprints** folder, right-click, and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="65a06-221">Assegna a questo attore il nome **WhiteKing** (Re bianco).</span><span class="sxs-lookup"><span data-stu-id="65a06-221">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="65a06-222">Fare doppio clic su **WhiteKing** per aprirlo nell'editor progetti, selezionare **Add Component > Scene** (Aggiungi componente > Scena) e assegnare alla scena il nome **Root**.</span><span class="sxs-lookup"><span data-stu-id="65a06-222">Double-click **WhiteKing** to open it in the Blueprint Editor, select **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="65a06-223">Trascina **Root** (Radice) su **DefaultSceneRoot** per sostituirla.</span><span class="sxs-lookup"><span data-stu-id="65a06-223">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="65a06-224">Fai clic su **Add Component > Static Mesh** (Aggiungi componente > Mesh statica) e assegna il nome **SM_King** (MS_Re) alla mesh.</span><span class="sxs-lookup"><span data-stu-id="65a06-224">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="65a06-225">Nel pannello Details (Dettagli) imposta **Static Mesh** (Mesh statica) su **Chess_King** (Scacchi_Re) e **Material** (Materiale) su un nuovo materiale denominato **M_ChessWhite** (M_ScacchiBianco).</span><span class="sxs-lookup"><span data-stu-id="65a06-225">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="65a06-226">Apri **M_ChessWhite** (M_ScacchiBianco) nell'editor dei materiali e associa i seguenti nodi **Texture Sample** (Esempio di texture) a quanto segue:</span><span class="sxs-lookup"><span data-stu-id="65a06-226">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
   * <span data-ttu-id="65a06-227">Impostare **Texture** su **ChessWhite_Albedo** (ScacchiBianco_Albedo) e collegare **RGB** al segnaposto **Base Color** (Colore di base).</span><span class="sxs-lookup"><span data-stu-id="65a06-227">Set **Texture** to **ChessWhite_Albedo** and link the **RGB** to the **Base Color** pin.</span></span>
    * <span data-ttu-id="65a06-228">Imposta **Texture** su **ChessWhite_AO** (ScacchiBianco_OA) e collega **RGB** al segnaposto **Ambient Occlusion** (Occlusione ambiente).</span><span class="sxs-lookup"><span data-stu-id="65a06-228">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="65a06-229">Imposta **Texture** su **ChessWhite_Metal**(ScacchiBianco_Metallo) e collega **RGB** al segnaposto **Metallic** (Metallico).</span><span class="sxs-lookup"><span data-stu-id="65a06-229">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="65a06-230">Imposta **Texture** su **ChessWhite_Normal** (ScacchiBianco_Normale) e collega **RGB** al segnaposto **Normal** (Normale).</span><span class="sxs-lookup"><span data-stu-id="65a06-230">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="65a06-231">Imposta **Texture** su **ChessWhite_Rough**(ScacchiBianco_Ruvido) e collega **RGB** al segnaposto **Roughness** (Ruvidezza).</span><span class="sxs-lookup"><span data-stu-id="65a06-231">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="65a06-232">Fare clic su **Save**.</span><span class="sxs-lookup"><span data-stu-id="65a06-232">Click **Save**.</span></span> 

<span data-ttu-id="65a06-233">Prima di continuare, il materiale **M_ChessKing** (M_ScacchiRe) deve essere simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="65a06-233">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![Creare il materiale per il re degli scacchi](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="65a06-235">Hai quasi finito: ora basta aggiungere il nuovo pezzo degli scacchi alla scena:</span><span class="sxs-lookup"><span data-stu-id="65a06-235">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="65a06-236">Apri il progetto **WhiteKing** (ReBianco) e imposta **Scale** (Scala) su **(0.05, 0.05, 0.05)** e **Z Rotation** (Rotazione Z) su **90**.</span><span class="sxs-lookup"><span data-stu-id="65a06-236">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="65a06-237">Compila e salva il progetto e quindi torna alla finestra principale.</span><span class="sxs-lookup"><span data-stu-id="65a06-237">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="65a06-238">Trascina **WhiteKing** (ReBianco) nel viewport, passa al pannello **World Outliner** (Delinatore mondo reale) e trascina **WhiteKing** (ReBianco) su **Board** (Tavola) per renderlo un oggetto figlio.</span><span class="sxs-lookup"><span data-stu-id="65a06-238">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![Delineatore mondo reale](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="65a06-240">Nel pannello **Details** (Dettagli) in **Transform** (Trasformazione) imposta **Location** (Posizione) di **WhiteKing** (ReBianco) su **X = -26**, **Y = 4** e **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="65a06-240">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="65a06-241">Ecco fatto!</span><span class="sxs-lookup"><span data-stu-id="65a06-241">That's a wrap!</span></span> <span data-ttu-id="65a06-242">Selezionare **Play** per vedere in azione il livello popolato e premere **ESC** per uscire.</span><span class="sxs-lookup"><span data-stu-id="65a06-242">Select **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="65a06-243">Con la creazione di un progetto semplice sono già stati illustrati molti aspetti. Ora, tuttavia, è possibile passare alla parte successiva della serie, dedicata alla configurazione per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="65a06-243">You covered a lot of ground just creating a simple project, but now you're ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="65a06-244">Sezione successiva: 3. Configurare il progetto per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="65a06-244">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)
