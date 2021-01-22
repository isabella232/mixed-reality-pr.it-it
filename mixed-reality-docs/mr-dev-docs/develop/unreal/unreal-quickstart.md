---
title: Creazione di un progetto HoloLens
description: Informazioni su come configurare correttamente un progetto irreale con gli oggetti scena e le interazioni di input per lo sviluppo di realtà mista HoloLens.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal Engine 4, Unreal Editor, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, documentazione, guide, funzionalità, cuffie per la realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale, porting, aggiornamento
ms.openlocfilehash: cd490c47479ba34bec942667afc8f34292bbb53c
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584800"
---
# <a name="creating-a-hololens-project"></a><span data-ttu-id="db475-104">Creazione di un progetto HoloLens</span><span class="sxs-lookup"><span data-stu-id="db475-104">Creating a HoloLens project</span></span>

<span data-ttu-id="db475-105">Prima di tutto, è necessario un progetto su cui lavorare.</span><span class="sxs-lookup"><span data-stu-id="db475-105">The first thing you need is a project to work with.</span></span> <span data-ttu-id="db475-106">Se si sviluppa in Unreal per la prima volta, è necessario [scaricare i file di supporto](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) dal launcher Epic.</span><span class="sxs-lookup"><span data-stu-id="db475-106">If you're a first-time Unreal developer, you'll need to [download supporting files](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="db475-107">Avvia Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="db475-107">Launch Unreal Engine</span></span>
2. <span data-ttu-id="db475-108">Nelle **categorie nuovo progetto** selezionare **giochi** e fare clic su **Avanti**:</span><span class="sxs-lookup"><span data-stu-id="db475-108">In the **New Project Categories**, select **Games** and click **Next**:</span></span>

![Finestra progetti recenti aperta con giochi evidenziati](images/unreal-quickstart-img-01.png)

3. <span data-ttu-id="db475-110">Selezionare il modello **vuoto** e fare clic su **Avanti**:</span><span class="sxs-lookup"><span data-stu-id="db475-110">Select the **Blank** template and click **Next**:</span></span>

![Finestra del browser del progetto non reale con modello vuoto evidenziato](images/unreal-quickstart-img-02.png)

4. <span data-ttu-id="db475-112">Nelle **impostazioni del progetto** impostare **C++, Scalable 3D o 2D, mobile/tablet** e **nessun contenuto iniziale**, quindi scegliere un percorso di salvataggio e fare clic su **Crea progetto**</span><span class="sxs-lookup"><span data-stu-id="db475-112">In the **Project Settings**, set **C++, Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content**, then choose a save location and click **Create Project**</span></span>

> <span data-ttu-id="db475-113">Si sta usando un progetto C++ anziché un progetto per creare il plug-in degli strumenti UX, che verrà configurato in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="db475-113">You're using a C++ rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later.</span></span>

![Finestra Impostazioni progetto con opzioni di progetto, prestazioni, piattaforma di destinazione e contenuto iniziale evidenziato](images/unreal-quickstart-img-03.png)

<span data-ttu-id="db475-115">Il nuovo progetto dovrebbe aprirsi automaticamente nell'editor Unreal, il che significa che si è pronti per la sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="db475-115">Your new project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="db475-116">Abilitazione dei plug-in necessari</span><span class="sxs-lookup"><span data-stu-id="db475-116">Enabling required plugins</span></span>

<span data-ttu-id="db475-117">Prima di iniziare ad aggiungere oggetti alla scena, è necessario abilitare due plug-in.</span><span class="sxs-lookup"><span data-stu-id="db475-117">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="db475-118">Apri **Edit > Plugins** (Modifica > Plug-in) e seleziona **Augmented Reality** (Realtà aumentata) nell'elenco di opzioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="db475-118">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span>
* <span data-ttu-id="db475-119">Scorrere fino a **HoloLens** e selezionare **abilitato**</span><span class="sxs-lookup"><span data-stu-id="db475-119">Scroll down to **HoloLens** and check **Enabled**</span></span>

![Finestra plug-in con la sezione della realtà aumentata aperta e HoloLens evidenziata](images/unreal-quickstart-img-04.png)

2. <span data-ttu-id="db475-121">Digitare **OpenXR** nella casella di ricerca in alto a destra e abilitare i plug-in **OpenXR** e **OpenXRMsftHandInteraction** :</span><span class="sxs-lookup"><span data-stu-id="db475-121">Type **OpenXR** in the search box at the top right and enable the **OpenXR** and **OpenXRMsftHandInteraction** plugins:</span></span>

![Finestra plug-in con OpenXR abilitato](images/unreal-quickstart-img-05.jpg)

![Finestra plug-in con l'interazione della mano Open XR MSFT abilitata](images/unreal-quickstart-img-06.jpg)

3. <span data-ttu-id="db475-124">Riavviare l'editor</span><span class="sxs-lookup"><span data-stu-id="db475-124">Restart your editor</span></span>

> [!NOTE]
> <span data-ttu-id="db475-125">Questa esercitazione USA OpenXR, ma i due plug-in installati in precedenza non forniscono attualmente il set completo di funzionalità per lo sviluppo di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="db475-125">This tutorial uses OpenXR, but the two plugins you've installed above don't currently provide the full feature set for HoloLens development.</span></span> <span data-ttu-id="db475-126">Il plug-in HandInteraction sarà sufficiente per il gesto "pizzico" che verrà usato in un secondo momento, ma se si vogliono superare le nozioni di base, è necessario [scaricare il plug](https://github.com/microsoft/Microsoft-OpenXR-Unreal)-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="db475-126">The HandInteraction plugin will suffice for the "Pinch" gesture you'll use later, but if you want to go beyond the basics you'll need to [download the OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

<span data-ttu-id="db475-127">Con i plug-in abilitati, è possibile concentrarsi sulla compilazione con contenuto.</span><span class="sxs-lookup"><span data-stu-id="db475-127">With the plugins enabled, you can focus on filling it with content.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="db475-128">Creazione di un livello</span><span class="sxs-lookup"><span data-stu-id="db475-128">Creating a level</span></span>

<span data-ttu-id="db475-129">L'attività successiva consiste nel creare una configurazione di gioco con un punto iniziale e un cubo per riferimento e scala.</span><span class="sxs-lookup"><span data-stu-id="db475-129">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="db475-130">Seleziona **File > New Level** (File > Nuovo livello) e scegli **Empty Level** (Livello vuoto).</span><span class="sxs-lookup"><span data-stu-id="db475-130">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="db475-131">La scena predefinita nel viewport ora è vuota</span><span class="sxs-lookup"><span data-stu-id="db475-131">The default scene in the viewport should now be empty</span></span>
2. <span data-ttu-id="db475-132">Dalla scheda **modalità** selezionare **Basic** e trascinare **PlayerStart** nella scena</span><span class="sxs-lookup"><span data-stu-id="db475-132">From the **Modes** tab, select **Basic** and drag **PlayerStart** into the scene</span></span>
* <span data-ttu-id="db475-133">Nella scheda **Dettagli** impostare **percorso** su **X = 0, Y = 0** e **Z = 0** per inserire l'utente al centro della scena all'avvio dell'app</span><span class="sxs-lookup"><span data-stu-id="db475-133">In the **Details** tab, set **Location** to **X = 0, Y = 0,** and **Z = 0** to place the user at the center of the scene when the app starts</span></span>

![Scena dell'editor non reale con la posizione e l'avvio del giocatore aggiunti](images/unreal-quickstart-img-07.png)

3. <span data-ttu-id="db475-135">Dalla scheda di **base** trascinare un **cubo** nella scena</span><span class="sxs-lookup"><span data-stu-id="db475-135">From the **Basic** tab, drag a **Cube** into the scene</span></span>
* <span data-ttu-id="db475-136">Imposta la **posizione** del cubo su **X = 50, Y = 0** e **Z = 0** per posizionare il cubo 50 cm dal lettore all'inizio</span><span class="sxs-lookup"><span data-stu-id="db475-136">Set the cube's **Location** to **X = 50, Y = 0**, and **Z = 0** to position the cube 50 cm away from the player at start</span></span>
* <span data-ttu-id="db475-137">Modificare la **scala** del cubo in **X = 0,2, Y = 0,2** e **Z = 0,2**</span><span class="sxs-lookup"><span data-stu-id="db475-137">Change  the cube's **Scale** to **X = 0.2, Y = 0.2**, and **Z = 0.2**</span></span> 

<span data-ttu-id="db475-138">Il cubo non sarà visibile finché non viene aggiunta una luce alla scena, che è l'ultima attività da eseguire prima del test.</span><span class="sxs-lookup"><span data-stu-id="db475-138">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="db475-139">Nel pannello **modalità** passare alla scheda **luci** e trascinare una **luce direzionale** nella scena</span><span class="sxs-lookup"><span data-stu-id="db475-139">In the **Modes** panel, switch to the **Lights** tab and drag a **Directional Light** into the scene</span></span>
* <span data-ttu-id="db475-140">Posizionare la luce sopra **PlayerStart** in modo che sia possibile visualizzarla</span><span class="sxs-lookup"><span data-stu-id="db475-140">Position the light above **PlayerStart** so you can see it</span></span>

![Scena dell'editor non reale con aggiunta di cubo e luce direzionale](images/unreal-quickstart-img-08.png)

5. <span data-ttu-id="db475-142">Passare a **File > Salva corrente**, assegnare un nome al livello **principale** e selezionare **Salva** .</span><span class="sxs-lookup"><span data-stu-id="db475-142">Go to **File > Save Current**, name your level **Main**, and select **Save**</span></span>

<span data-ttu-id="db475-143">Una volta impostata la scena, seleziona **Play** (Riproduci) sulla barra degli strumenti per vedere il cubo in azione.</span><span class="sxs-lookup"><span data-stu-id="db475-143">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="db475-144">Quando avrai terminato di ammirare il tuo lavoro, premi ESC per arrestare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="db475-144">When you're finished admiring your work, press Esc to stop the application.</span></span>

![Scena in modalità di riproduzione con il cubo al centro della schermata](images/unreal-quickstart-img-09.png)

<span data-ttu-id="db475-146">Ora che la scena è configurata, consente di prepararsi per alcune interazioni di base in AR.</span><span class="sxs-lookup"><span data-stu-id="db475-146">Now that the scene is set up, lets get it ready for some basic interactions in AR.</span></span> <span data-ttu-id="db475-147">Prima di tutto, è necessario creare una sessione AR ed è possibile aggiungere progetti per abilitare l'interazione manuale.</span><span class="sxs-lookup"><span data-stu-id="db475-147">First, you need to create an AR Session and can add blueprints to enable hand interaction.</span></span>

## <a name="adding-a-session-asset"></a><span data-ttu-id="db475-148">Aggiunta di un asset della sessione</span><span class="sxs-lookup"><span data-stu-id="db475-148">Adding a session asset</span></span>

<span data-ttu-id="db475-149">Le sessioni AR in Unreal non funzionano da sole.</span><span class="sxs-lookup"><span data-stu-id="db475-149">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="db475-150">Per usare una sessione, è necessario un asset di dati ARSessionConfig con cui interagire, che costituisce l'attività successiva:</span><span class="sxs-lookup"><span data-stu-id="db475-150">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="db475-151">Nel **browser del contenuto** selezionare **Aggiungi nuovo > varie > asset di dati** e verificare di essere al livello della cartella del contenuto radice</span><span class="sxs-lookup"><span data-stu-id="db475-151">In the **Content Browser**, select **Add New > Miscellaneous > Data Asset** and make sure you're at the root Content folder level</span></span>
2. <span data-ttu-id="db475-152">Selezionare **ARSessionConfig**, fare clic su **Seleziona** e denominare l'asset **ARSessionConfig**:</span><span class="sxs-lookup"><span data-stu-id="db475-152">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**:</span></span>

![Selezionare la finestra classe di asset di dati aperta con l'asset di configurazione della sessione AR evidenziato](images/unreal-quickstart-img-10.png)

2. <span data-ttu-id="db475-154">Fare doppio clic su **ARSessionConfig** per aprirlo, **salvare** con tutte le impostazioni predefinite e tornare alla finestra principale:</span><span class="sxs-lookup"><span data-stu-id="db475-154">Double-click **ARSessionConfig** to open it, **Save** with all default settings, and return to the Main window:</span></span>

![Finestra Dettagli asset di configurazione della sessione AR](images/unreal-quickstart-img-11.png)

<span data-ttu-id="db475-156">Al termine, il passaggio successivo consiste nell'assicurarsi che la sessione AR venga avviata e arrestata quando il livello si carica e termina.</span><span class="sxs-lookup"><span data-stu-id="db475-156">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="db475-157">In Unreal è disponibile un particolare progetto denominato **Level Blueprint** (Progetto livello) che svolge la funzione di grafico eventi globale che prende come riferimento il livello.</span><span class="sxs-lookup"><span data-stu-id="db475-157">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="db475-158">La connessione dell'asset ARSessionConfig in Level Blueprint (Progetto livello) garantisce l'avvio della sessione nel momento in cui viene avviato il gioco.</span><span class="sxs-lookup"><span data-stu-id="db475-158">Connecting the ARSessionConfig asset in the Level Blueprint guarantees the AR session will fire right when the game starts playing.</span></span>

3. <span data-ttu-id="db475-159">Dalla barra degli strumenti dell'editor selezionare Blueprints **> progetto Open level**:</span><span class="sxs-lookup"><span data-stu-id="db475-159">From the editor toolbar, select **Blueprints > Open Level Blueprint**:</span></span>

![Menu progetto aperto con l'opzione progetto Open level evidenziato](images/unreal-quickstart-img-12.png)

4. <span data-ttu-id="db475-161">Trascinare il nodo di esecuzione (icona a sinistra) dell' **evento BeginPlay** e Release</span><span class="sxs-lookup"><span data-stu-id="db475-161">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release</span></span>
* <span data-ttu-id="db475-162">Cercare il **nodo di avvio della sessione AR** e premere INVIO</span><span class="sxs-lookup"><span data-stu-id="db475-162">Search for the **Start AR Session node** and hit enter</span></span>
* <span data-ttu-id="db475-163">Fare clic sull'elenco a discesa **Seleziona asset** in **configurazione della sessione** e scegliere l'asset **ARSessionConfig**</span><span class="sxs-lookup"><span data-stu-id="db475-163">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset</span></span>

![Grafico del progetto con inizio riproduzione evento connesso alla funzione Avvia sessione AR](images/unreal-quickstart-img-13.png)

5. <span data-ttu-id="db475-165">Fai clic con il pulsante destro del mouse in un punto qualsiasi di EventGraph e crea un nuovo nodo **Event EndPlay**.</span><span class="sxs-lookup"><span data-stu-id="db475-165">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> 
* <span data-ttu-id="db475-166">Trascinare il pin di esecuzione e il rilascio, quindi cercare un nodo di **sessione stop AR** e premere INVIO</span><span class="sxs-lookup"><span data-stu-id="db475-166">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter</span></span> 
* <span data-ttu-id="db475-167">Premere **Compila**, quindi **salvare** e tornare alla finestra principale</span><span class="sxs-lookup"><span data-stu-id="db475-167">Hit **Compile**, then **Save** and return to the Main window</span></span>

> [!IMPORTANT]
> <span data-ttu-id="db475-168">Se la sessione AR è ancora in esecuzione al termine del livello, alcune funzionalità potrebbero smettere di funzionare se l'app viene riavviata durante lo streaming a un visore VR.</span><span class="sxs-lookup"><span data-stu-id="db475-168">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>

![Nodo evento finale associato alla funzione di sessione stop AR](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a><span data-ttu-id="db475-170">Impostazione degli input</span><span class="sxs-lookup"><span data-stu-id="db475-170">Setting up inputs</span></span>

1. <span data-ttu-id="db475-171">Selezionare **Modifica impostazioni progetto >** e passare al **motore > input**</span><span class="sxs-lookup"><span data-stu-id="db475-171">Select **Edit > Project Settings** and go to the **Engine > Input**</span></span>
2. <span data-ttu-id="db475-172">Selezionare l' **+** icona accanto a **mapping azioni** e creare azioni **RightPinch** e **LeftPinch** :</span><span class="sxs-lookup"><span data-stu-id="db475-172">Select the **+** icon next to **Action Mappings** and create **RightPinch** and **LeftPinch** actions:</span></span>

![Associazione delle impostazioni di input con i mapping delle azioni di tocco a destra e a sinistra evidenziati](images/unreal-quickstart-img-15.jpg)

3. <span data-ttu-id="db475-174">Eseguire il mapping delle azioni **RightPinch** e **LeftPinch** alla rispettiva azione di **interazione della mano OpenXR MSFT** :</span><span class="sxs-lookup"><span data-stu-id="db475-174">Map the **RightPinch** and **LeftPinch** actions the to the respective **OpenXR Msft Hand Interaction** actions:</span></span>

![Mapping delle azioni con opzioni di interazione della mano Open XR MSFT evidenziate](images/unreal-quickstart-img-16.jpg)

4. <span data-ttu-id="db475-176">Aprire il **progetto Level** e aggiungere un **InputAction RightPinch** e **InputAction LeftPinch**</span><span class="sxs-lookup"><span data-stu-id="db475-176">Open the **Level Blueprint** and add an **InputAction RightPinch** and **InputAction LeftPinch**</span></span>
* <span data-ttu-id="db475-177">Connettere l'evento Pinch a destra a un **AddActorLocalRotation** con il **cubo** come destinazione e **rotazione delta** impostati su **X = 0, Y = 0** e **Z = 20**.</span><span class="sxs-lookup"><span data-stu-id="db475-177">Connect the right pinch event to an **AddActorLocalRotation** with your **Cube** as the target and **Delta Rotation** set to **X = 0, Y = 0**, and **Z = 20**.</span></span> <span data-ttu-id="db475-178">Il cubo verrà ora ruotato di 20 gradi ogni volta che si pizzica</span><span class="sxs-lookup"><span data-stu-id="db475-178">The cube will now rotate by 20 degrees every time you pinch</span></span>
* <span data-ttu-id="db475-179">Connetti l'evento di tocco a sinistra per **chiudere il gioco**</span><span class="sxs-lookup"><span data-stu-id="db475-179">Connect the left pinch event to **Quit Game**</span></span>

![Livello Bluprint aperto con azioni di input per gli eventi di pizzico a destra e a sinistra](images/unreal-quickstart-img-17.jpg)

5. <span data-ttu-id="db475-181">Nelle impostazioni di **trasformazione** del cubo impostare **mobilità** su **mobile** in modo che possa essere spostata dinamicamente:</span><span class="sxs-lookup"><span data-stu-id="db475-181">In the cube's **Transform** settings, set **Mobility** to **Movable** so it can move dynamically:</span></span>

![Impostazioni trasformare con proprietà Mobility evidenziate](images/unreal-quickstart-img-18.jpg)

<span data-ttu-id="db475-183">A questo punto, si è pronti per deply ci ed eseguire il test dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="db475-183">At this point, you're ready to deply and test the application!</span></span>