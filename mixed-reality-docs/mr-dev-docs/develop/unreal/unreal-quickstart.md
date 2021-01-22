---
title: Creazione di un progetto HoloLens
description: Informazioni su come configurare correttamente un progetto irreale con gli oggetti scena e le interazioni di input per lo sviluppo di realtà mista HoloLens.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal Engine 4, Unreal Editor, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, documentazione, guide, funzionalità, cuffie per la realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale, porting, aggiornamento
ms.openlocfilehash: 3b2b88ac897a8791fec1ca2942d0db34efcee598
ms.sourcegitcommit: be33fcda10d1cb98df90b428a923289933d42c77
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2021
ms.locfileid: "98672738"
---
# <a name="creating-a-hololens-project"></a><span data-ttu-id="8153c-104">Creazione di un progetto HoloLens</span><span class="sxs-lookup"><span data-stu-id="8153c-104">Creating a HoloLens project</span></span>

<span data-ttu-id="8153c-105">Prima di tutto, è necessario un progetto su cui lavorare.</span><span class="sxs-lookup"><span data-stu-id="8153c-105">The first thing you need is a project to work with.</span></span> <span data-ttu-id="8153c-106">Se si sviluppa in Unreal per la prima volta, è necessario [scaricare i file di supporto](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) dal launcher Epic.</span><span class="sxs-lookup"><span data-stu-id="8153c-106">If you're a first-time Unreal developer, you'll need to [download supporting files](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="8153c-107">Avvia Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="8153c-107">Launch Unreal Engine</span></span>
2. <span data-ttu-id="8153c-108">Nelle **categorie nuovo progetto** selezionare **giochi** e fare clic su **Avanti**:</span><span class="sxs-lookup"><span data-stu-id="8153c-108">In the **New Project Categories**, select **Games** and click **Next**:</span></span>

![Finestra progetti recenti aperta con giochi evidenziati](images/unreal-quickstart-img-01.png)

3. <span data-ttu-id="8153c-110">Selezionare il modello **vuoto** e fare clic su **Avanti**:</span><span class="sxs-lookup"><span data-stu-id="8153c-110">Select the **Blank** template and click **Next**:</span></span>

![Finestra del browser del progetto non reale con modello vuoto evidenziato](images/unreal-quickstart-img-02.png)

4. <span data-ttu-id="8153c-112">Nelle **impostazioni del progetto** impostare **C++, Scalable 3D o 2D, mobile/tablet** e **nessun contenuto iniziale**, quindi scegliere un percorso di salvataggio e fare clic su **Crea progetto**</span><span class="sxs-lookup"><span data-stu-id="8153c-112">In the **Project Settings**, set **C++, Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content**, then choose a save location and click **Create Project**</span></span>

> [!NOTE] <span data-ttu-id="8153c-113">Per essere pronti a usare il plug-in OpenXR in un secondo momento, si usa un progetto C++ anziché un progetto di progetto.</span><span class="sxs-lookup"><span data-stu-id="8153c-113">You're using a C++ rather than a Blueprint project in order to be ready to use the OpenXR plugin later.</span></span> <span data-ttu-id="8153c-114">Questa Guida introduttiva usa il plug-in OpenXR predefinito incluso in Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="8153c-114">This QuickStart uses the default OpenXR plugin that comes with Unreal Engine.</span></span> <span data-ttu-id="8153c-115">È tuttavia consigliabile scaricare e usare il plug-in Microsoft OpenXR ufficiale.</span><span class="sxs-lookup"><span data-stu-id="8153c-115">However, downloading and using the official Microsoft OpenXR plugin is recommended.</span></span> <span data-ttu-id="8153c-116">Per questo è necessario che il progetto sia un progetto C++.</span><span class="sxs-lookup"><span data-stu-id="8153c-116">That requires the project to be a C++ project.</span></span>

![Finestra Impostazioni progetto con opzioni di progetto, prestazioni, piattaforma di destinazione e contenuto iniziale evidenziato](images/unreal-quickstart-img-03.png)

<span data-ttu-id="8153c-118">Il nuovo progetto dovrebbe aprirsi automaticamente nell'editor Unreal, il che significa che si è pronti per la sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="8153c-118">Your new project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="8153c-119">Abilitazione dei plug-in necessari</span><span class="sxs-lookup"><span data-stu-id="8153c-119">Enabling required plugins</span></span>

<span data-ttu-id="8153c-120">Prima di iniziare ad aggiungere oggetti alla scena, è necessario abilitare due plug-in.</span><span class="sxs-lookup"><span data-stu-id="8153c-120">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="8153c-121">Apri **Edit > Plugins** (Modifica > Plug-in) e seleziona **Augmented Reality** (Realtà aumentata) nell'elenco di opzioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="8153c-121">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span>
* <span data-ttu-id="8153c-122">Scorrere fino a **HoloLens** e selezionare **abilitato**</span><span class="sxs-lookup"><span data-stu-id="8153c-122">Scroll down to **HoloLens** and check **Enabled**</span></span>

![Finestra plug-in con la sezione della realtà aumentata aperta e HoloLens evidenziata](images/unreal-quickstart-img-04.png)

2. <span data-ttu-id="8153c-124">Digitare **OpenXR** nella casella di ricerca in alto a destra e abilitare i plug-in **OpenXR** e **OpenXRMsftHandInteraction** :</span><span class="sxs-lookup"><span data-stu-id="8153c-124">Type **OpenXR** in the search box at the top right and enable the **OpenXR** and **OpenXRMsftHandInteraction** plugins:</span></span>

![Finestra plug-in con OpenXR abilitato](images/unreal-quickstart-img-05.jpg)

![Finestra plug-in con l'interazione della mano Open XR MSFT abilitata](images/unreal-quickstart-img-06.jpg)

3. <span data-ttu-id="8153c-127">Riavviare l'editor</span><span class="sxs-lookup"><span data-stu-id="8153c-127">Restart your editor</span></span>

> [!NOTE]
> <span data-ttu-id="8153c-128">Questa esercitazione USA OpenXR, ma i due plug-in installati in precedenza non forniscono attualmente il set completo di funzionalità per lo sviluppo di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8153c-128">This tutorial uses OpenXR, but the two plugins you've installed above don't currently provide the full feature set for HoloLens development.</span></span> <span data-ttu-id="8153c-129">Il plug-in HandInteraction sarà sufficiente per il gesto "pizzico" che verrà usato in un secondo momento, ma se si vogliono superare le nozioni di base, è necessario [scaricare il plug](https://github.com/microsoft/Microsoft-OpenXR-Unreal)-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="8153c-129">The HandInteraction plugin will suffice for the "Pinch" gesture you'll use later, but if you want to go beyond the basics you'll need to [download the OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

<span data-ttu-id="8153c-130">Con i plug-in abilitati, è possibile concentrarsi sulla compilazione con contenuto.</span><span class="sxs-lookup"><span data-stu-id="8153c-130">With the plugins enabled, you can focus on filling it with content.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="8153c-131">Creazione di un livello</span><span class="sxs-lookup"><span data-stu-id="8153c-131">Creating a level</span></span>

<span data-ttu-id="8153c-132">L'attività successiva consiste nel creare una configurazione di gioco con un punto iniziale e un cubo per riferimento e scala.</span><span class="sxs-lookup"><span data-stu-id="8153c-132">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="8153c-133">Seleziona **File > New Level** (File > Nuovo livello) e scegli **Empty Level** (Livello vuoto).</span><span class="sxs-lookup"><span data-stu-id="8153c-133">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="8153c-134">La scena predefinita nel viewport ora è vuota</span><span class="sxs-lookup"><span data-stu-id="8153c-134">The default scene in the viewport should now be empty</span></span>
2. <span data-ttu-id="8153c-135">Dalla scheda **modalità** selezionare **Basic** e trascinare **PlayerStart** nella scena</span><span class="sxs-lookup"><span data-stu-id="8153c-135">From the **Modes** tab, select **Basic** and drag **PlayerStart** into the scene</span></span>
* <span data-ttu-id="8153c-136">Nella scheda **Dettagli** impostare **percorso** su **X = 0, Y = 0** e **Z = 0** per inserire l'utente al centro della scena all'avvio dell'app</span><span class="sxs-lookup"><span data-stu-id="8153c-136">In the **Details** tab, set **Location** to **X = 0, Y = 0,** and **Z = 0** to place the user at the center of the scene when the app starts</span></span>

![Scena dell'editor non reale con la posizione e l'avvio del giocatore aggiunti](images/unreal-quickstart-img-07.png)

3. <span data-ttu-id="8153c-138">Dalla scheda di **base** trascinare un **cubo** nella scena</span><span class="sxs-lookup"><span data-stu-id="8153c-138">From the **Basic** tab, drag a **Cube** into the scene</span></span>
* <span data-ttu-id="8153c-139">Imposta la **posizione** del cubo su **X = 50, Y = 0** e **Z = 0** per posizionare il cubo 50 cm dal lettore all'inizio</span><span class="sxs-lookup"><span data-stu-id="8153c-139">Set the cube's **Location** to **X = 50, Y = 0**, and **Z = 0** to position the cube 50 cm away from the player at start</span></span>
* <span data-ttu-id="8153c-140">Modificare la **scala** del cubo in **X = 0,2, Y = 0,2** e **Z = 0,2**</span><span class="sxs-lookup"><span data-stu-id="8153c-140">Change  the cube's **Scale** to **X = 0.2, Y = 0.2**, and **Z = 0.2**</span></span> 

<span data-ttu-id="8153c-141">Il cubo non sarà visibile finché non viene aggiunta una luce alla scena, che è l'ultima attività da eseguire prima del test.</span><span class="sxs-lookup"><span data-stu-id="8153c-141">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="8153c-142">Nel pannello **modalità** passare alla scheda **luci** e trascinare una **luce direzionale** nella scena</span><span class="sxs-lookup"><span data-stu-id="8153c-142">In the **Modes** panel, switch to the **Lights** tab and drag a **Directional Light** into the scene</span></span>
* <span data-ttu-id="8153c-143">Posizionare la luce sopra **PlayerStart** in modo che sia possibile visualizzarla</span><span class="sxs-lookup"><span data-stu-id="8153c-143">Position the light above **PlayerStart** so you can see it</span></span>

![Scena dell'editor non reale con aggiunta di cubo e luce direzionale](images/unreal-quickstart-img-08.png)

5. <span data-ttu-id="8153c-145">Passare a **File > Salva corrente**, assegnare un nome al livello **principale** e selezionare **Salva** .</span><span class="sxs-lookup"><span data-stu-id="8153c-145">Go to **File > Save Current**, name your level **Main**, and select **Save**</span></span>

<span data-ttu-id="8153c-146">Una volta impostata la scena, seleziona **Play** (Riproduci) sulla barra degli strumenti per vedere il cubo in azione.</span><span class="sxs-lookup"><span data-stu-id="8153c-146">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="8153c-147">Quando avrai terminato di ammirare il tuo lavoro, premi ESC per arrestare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="8153c-147">When you're finished admiring your work, press Esc to stop the application.</span></span>

![Scena in modalità di riproduzione con il cubo al centro della schermata](images/unreal-quickstart-img-09.png)

<span data-ttu-id="8153c-149">Ora che la scena è configurata, consente di prepararsi per alcune interazioni di base in AR.</span><span class="sxs-lookup"><span data-stu-id="8153c-149">Now that the scene is set up, lets get it ready for some basic interactions in AR.</span></span> <span data-ttu-id="8153c-150">Prima di tutto, è necessario creare una sessione AR ed è possibile aggiungere progetti per abilitare l'interazione manuale.</span><span class="sxs-lookup"><span data-stu-id="8153c-150">First, you need to create an AR Session and can add blueprints to enable hand interaction.</span></span>

## <a name="adding-a-session-asset"></a><span data-ttu-id="8153c-151">Aggiunta di un asset della sessione</span><span class="sxs-lookup"><span data-stu-id="8153c-151">Adding a session asset</span></span>

<span data-ttu-id="8153c-152">Le sessioni AR in Unreal non funzionano da sole.</span><span class="sxs-lookup"><span data-stu-id="8153c-152">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="8153c-153">Per usare una sessione, è necessario un asset di dati ARSessionConfig con cui interagire, che costituisce l'attività successiva:</span><span class="sxs-lookup"><span data-stu-id="8153c-153">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="8153c-154">Nel **browser del contenuto** selezionare **Aggiungi nuovo > varie > asset di dati** e verificare di essere al livello della cartella del contenuto radice</span><span class="sxs-lookup"><span data-stu-id="8153c-154">In the **Content Browser**, select **Add New > Miscellaneous > Data Asset** and make sure you're at the root Content folder level</span></span>
2. <span data-ttu-id="8153c-155">Selezionare **ARSessionConfig**, fare clic su **Seleziona** e denominare l'asset **ARSessionConfig**:</span><span class="sxs-lookup"><span data-stu-id="8153c-155">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**:</span></span>

![Selezionare la finestra classe di asset di dati aperta con l'asset di configurazione della sessione AR evidenziato](images/unreal-quickstart-img-10.png)

2. <span data-ttu-id="8153c-157">Fare doppio clic su **ARSessionConfig** per aprirlo, **salvare** con tutte le impostazioni predefinite e tornare alla finestra principale:</span><span class="sxs-lookup"><span data-stu-id="8153c-157">Double-click **ARSessionConfig** to open it, **Save** with all default settings, and return to the Main window:</span></span>

![Finestra Dettagli asset di configurazione della sessione AR](images/unreal-quickstart-img-11.png)

<span data-ttu-id="8153c-159">Al termine, il passaggio successivo consiste nell'assicurarsi che la sessione AR venga avviata e arrestata quando il livello si carica e termina.</span><span class="sxs-lookup"><span data-stu-id="8153c-159">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="8153c-160">In Unreal è disponibile un particolare progetto denominato **Level Blueprint** (Progetto livello) che svolge la funzione di grafico eventi globale che prende come riferimento il livello.</span><span class="sxs-lookup"><span data-stu-id="8153c-160">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="8153c-161">La connessione dell'asset ARSessionConfig in Level Blueprint (Progetto livello) garantisce l'avvio della sessione nel momento in cui viene avviato il gioco.</span><span class="sxs-lookup"><span data-stu-id="8153c-161">Connecting the ARSessionConfig asset in the Level Blueprint guarantees the AR session will fire right when the game starts playing.</span></span>

3. <span data-ttu-id="8153c-162">Dalla barra degli strumenti dell'editor selezionare Blueprints **> progetto Open level**:</span><span class="sxs-lookup"><span data-stu-id="8153c-162">From the editor toolbar, select **Blueprints > Open Level Blueprint**:</span></span>

![Menu progetto aperto con l'opzione progetto Open level evidenziato](images/unreal-quickstart-img-12.png)

4. <span data-ttu-id="8153c-164">Trascinare il nodo di esecuzione (icona a sinistra) dell' **evento BeginPlay** e Release</span><span class="sxs-lookup"><span data-stu-id="8153c-164">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release</span></span>
* <span data-ttu-id="8153c-165">Cercare il **nodo di avvio della sessione AR** e premere INVIO</span><span class="sxs-lookup"><span data-stu-id="8153c-165">Search for the **Start AR Session node** and hit enter</span></span>
* <span data-ttu-id="8153c-166">Fare clic sull'elenco a discesa **Seleziona asset** in **configurazione della sessione** e scegliere l'asset **ARSessionConfig**</span><span class="sxs-lookup"><span data-stu-id="8153c-166">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset</span></span>

![Grafico del progetto con inizio riproduzione evento connesso alla funzione Avvia sessione AR](images/unreal-quickstart-img-13.png)

5. <span data-ttu-id="8153c-168">Fai clic con il pulsante destro del mouse in un punto qualsiasi di EventGraph e crea un nuovo nodo **Event EndPlay**.</span><span class="sxs-lookup"><span data-stu-id="8153c-168">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> 
* <span data-ttu-id="8153c-169">Trascinare il pin di esecuzione e il rilascio, quindi cercare un nodo di **sessione stop AR** e premere INVIO</span><span class="sxs-lookup"><span data-stu-id="8153c-169">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter</span></span> 
* <span data-ttu-id="8153c-170">Premere **Compila**, quindi **salvare** e tornare alla finestra principale</span><span class="sxs-lookup"><span data-stu-id="8153c-170">Hit **Compile**, then **Save** and return to the Main window</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8153c-171">Se la sessione AR è ancora in esecuzione al termine del livello, alcune funzionalità potrebbero smettere di funzionare se l'app viene riavviata durante lo streaming a un visore VR.</span><span class="sxs-lookup"><span data-stu-id="8153c-171">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>

![Nodo evento finale associato alla funzione di sessione stop AR](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a><span data-ttu-id="8153c-173">Impostazione degli input</span><span class="sxs-lookup"><span data-stu-id="8153c-173">Setting up inputs</span></span>

1. <span data-ttu-id="8153c-174">Selezionare **Modifica impostazioni progetto >** e passare al **motore > input**</span><span class="sxs-lookup"><span data-stu-id="8153c-174">Select **Edit > Project Settings** and go to the **Engine > Input**</span></span>
2. <span data-ttu-id="8153c-175">Selezionare l' **+** icona accanto a **mapping azioni** e creare azioni **RightPinch** e **LeftPinch** :</span><span class="sxs-lookup"><span data-stu-id="8153c-175">Select the **+** icon next to **Action Mappings** and create **RightPinch** and **LeftPinch** actions:</span></span>

![Associazione delle impostazioni di input con i mapping delle azioni di tocco a destra e a sinistra evidenziati](images/unreal-quickstart-img-15.jpg)

3. <span data-ttu-id="8153c-177">Eseguire il mapping delle azioni **RightPinch** e **LeftPinch** alla rispettiva azione di **interazione della mano OpenXR MSFT** :</span><span class="sxs-lookup"><span data-stu-id="8153c-177">Map the **RightPinch** and **LeftPinch** actions the to the respective **OpenXR Msft Hand Interaction** actions:</span></span>

![Mapping delle azioni con opzioni di interazione della mano Open XR MSFT evidenziate](images/unreal-quickstart-img-16.jpg)

4. <span data-ttu-id="8153c-179">Aprire il **progetto Level** e aggiungere un **InputAction RightPinch** e **InputAction LeftPinch**</span><span class="sxs-lookup"><span data-stu-id="8153c-179">Open the **Level Blueprint** and add an **InputAction RightPinch** and **InputAction LeftPinch**</span></span>
* <span data-ttu-id="8153c-180">Connettere l'evento Pinch a destra a un **AddActorLocalRotation** con il **cubo** come destinazione e **rotazione delta** impostati su **X = 0, Y = 0** e **Z = 20**.</span><span class="sxs-lookup"><span data-stu-id="8153c-180">Connect the right pinch event to an **AddActorLocalRotation** with your **Cube** as the target and **Delta Rotation** set to **X = 0, Y = 0**, and **Z = 20**.</span></span> <span data-ttu-id="8153c-181">Il cubo verrà ora ruotato di 20 gradi ogni volta che si pizzica</span><span class="sxs-lookup"><span data-stu-id="8153c-181">The cube will now rotate by 20 degrees every time you pinch</span></span>
* <span data-ttu-id="8153c-182">Connetti l'evento di tocco a sinistra per **chiudere il gioco**</span><span class="sxs-lookup"><span data-stu-id="8153c-182">Connect the left pinch event to **Quit Game**</span></span>

![Livello Bluprint aperto con azioni di input per gli eventi di pizzico a destra e a sinistra](images/unreal-quickstart-img-17.jpg)

5. <span data-ttu-id="8153c-184">Nelle impostazioni di **trasformazione** del cubo impostare **mobilità** su **mobile** in modo che possa essere spostata dinamicamente:</span><span class="sxs-lookup"><span data-stu-id="8153c-184">In the cube's **Transform** settings, set **Mobility** to **Movable** so it can move dynamically:</span></span>

![Impostazioni trasformare con proprietà Mobility evidenziate](images/unreal-quickstart-img-18.jpg)

<span data-ttu-id="8153c-186">A questo punto, si è pronti per deply ci ed eseguire il test dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="8153c-186">At this point, you're ready to deply and test the application!</span></span>