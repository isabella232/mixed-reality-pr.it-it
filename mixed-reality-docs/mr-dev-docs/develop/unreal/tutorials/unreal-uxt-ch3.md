---
title: 3. Configurazione del progetto per la realtà mista
description: Parte 3 di 6 in una serie di esercitazioni per la creazione di un'app per gli scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 26bb874578e56b21d319741b8b1c1ff6decebe4b
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "96609702"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="0ea21-104">3. Configurazione del progetto per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="0ea21-104">3. Setting up your project for mixed reality</span></span>

<span data-ttu-id="0ea21-105">Nell'esercitazione precedente ti sei dedicato alla configurazione del progetto dell'app di scacchi.</span><span class="sxs-lookup"><span data-stu-id="0ea21-105">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="0ea21-106">In questa sezione viene illustrato come configurare l'app per lo sviluppo in realtà mista, ovvero aggiungendo una sessione AR.</span><span class="sxs-lookup"><span data-stu-id="0ea21-106">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="0ea21-107">Per questa attività si userà un asset di dati ARSessionConfig che include impostazioni AR utili come il mapping spaziale e l'occlusione.</span><span class="sxs-lookup"><span data-stu-id="0ea21-107">You'll be using an ARSessionConfig data asset for this task, which has useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="0ea21-108">Nella documentazione di Unreal sono disponibili altre informazioni dettagliate sull'asset [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) e la classe [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).</span><span class="sxs-lookup"><span data-stu-id="0ea21-108">You can find more details about the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class in Unreal's documentation.</span></span>

## <a name="objectives"></a><span data-ttu-id="0ea21-109">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="0ea21-109">Objectives</span></span>

* <span data-ttu-id="0ea21-110">Uso delle impostazioni AR di Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="0ea21-110">Working with Unreal Engine's AR settings</span></span>
* <span data-ttu-id="0ea21-111">Uso di un asset di dati ARSessionConfig</span><span class="sxs-lookup"><span data-stu-id="0ea21-111">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="0ea21-112">Configurazione di un pedone e modalità di gioco</span><span class="sxs-lookup"><span data-stu-id="0ea21-112">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="0ea21-113">Aggiunta dell'asset della sessione</span><span class="sxs-lookup"><span data-stu-id="0ea21-113">Adding the session asset</span></span>

<span data-ttu-id="0ea21-114">Le sessioni AR in Unreal non funzionano da sole.</span><span class="sxs-lookup"><span data-stu-id="0ea21-114">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="0ea21-115">Per usare una sessione, è necessario un asset di dati ARSessionConfig con cui interagire, che costituisce l'attività successiva:</span><span class="sxs-lookup"><span data-stu-id="0ea21-115">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="0ea21-116">Fai clic su **Add New > Miscellaneous > Data Asset** (Aggiungi nuovo > Varie > Asset dati) in **Content Browser** (Browser contenuto).</span><span class="sxs-lookup"><span data-stu-id="0ea21-116">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="0ea21-117">Assicurati di essere nella cartella **Content** radice.</span><span class="sxs-lookup"><span data-stu-id="0ea21-117">Make sure you're at the root **Content** folder level.</span></span>
    * <span data-ttu-id="0ea21-118">Seleziona **ARSessionConfig**, fai clic su **Select** (Seleziona) e assegna all'asset il nome **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="0ea21-118">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![Creazione di un'origine dati](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="0ea21-120">Fai doppio clic su **ARSessionConfig** per aprirlo, lascia tutte le impostazioni predefinite e premi **Save** (Salva).</span><span class="sxs-lookup"><span data-stu-id="0ea21-120">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="0ea21-121">Torna alla finestra principale.</span><span class="sxs-lookup"><span data-stu-id="0ea21-121">Return to the Main window.</span></span>

![ARSessionConfig](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="0ea21-123">Al termine, il passaggio successivo consiste nell'assicurarsi che la sessione AR venga avviata e arrestata quando il livello si carica e termina.</span><span class="sxs-lookup"><span data-stu-id="0ea21-123">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="0ea21-124">In Unreal è disponibile un particolare progetto denominato **Level Blueprint** (Progetto livello) che svolge la funzione di grafico eventi globale che prende come riferimento il livello.</span><span class="sxs-lookup"><span data-stu-id="0ea21-124">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="0ea21-125">La connessione dell'asset ARSessionConfig in **Level Blueprint** (Progetto livello) garantisce l'avvio della sessione nel momento in cui viene avviato il gioco.</span><span class="sxs-lookup"><span data-stu-id="0ea21-125">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="0ea21-126">Fai clic su **Blueprints > Open Level Blueprint** (Progetti > Apri progetto livello) sulla barra degli strumenti dell'editor:</span><span class="sxs-lookup"><span data-stu-id="0ea21-126">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span>

![Open Level Blueprint (Apri progetto livello)](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="0ea21-128">Trascinare il nodo esecuzione (icona a forma di freccia rivolta verso sinistra) da **evento BeginPlay** e rilasciare, quindi cercare il nodo **Start AR Session** (Avvia sessione AR) e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="0ea21-128">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release, then search for the **Start AR Session** node and hit enter.</span></span>  
    * <span data-ttu-id="0ea21-129">Fai clic sull'elenco a discesa **Select Asset** (Seleziona asset) in **Session Config** (Configurazione sessione) e scegli l'asset **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="0ea21-129">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span>

![Start AR Session (Avvia sessione AR)](images/unreal-uxt/3-start-ar-session.PNG)

6. <span data-ttu-id="0ea21-131">Fai clic con il pulsante destro del mouse in un punto qualsiasi di EventGraph e crea un nuovo nodo **Event EndPlay**.</span><span class="sxs-lookup"><span data-stu-id="0ea21-131">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> <span data-ttu-id="0ea21-132">Trascinare il pin di esecuzione e rilasciare, quindi cercare un nodo **Stop AR Session** (Arresta sessione AR) e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="0ea21-132">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter.</span></span> <span data-ttu-id="0ea21-133">Se la sessione AR è ancora in esecuzione al termine del livello, alcune funzionalità potrebbero smettere di funzionare se l'app viene riavviata durante lo streaming a un visore VR.</span><span class="sxs-lookup"><span data-stu-id="0ea21-133">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>
    * <span data-ttu-id="0ea21-134">Seleziona **Compile** (Compila) e **Save** (Salva) e torna alla finestra principale.</span><span class="sxs-lookup"><span data-stu-id="0ea21-134">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![Stop AR Session (Arresta sessione AR)](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="0ea21-136">Creare un pedone</span><span class="sxs-lookup"><span data-stu-id="0ea21-136">Create a Pawn</span></span>

<span data-ttu-id="0ea21-137">A questo punto, il progetto necessita ancora di un oggetto Player.</span><span class="sxs-lookup"><span data-stu-id="0ea21-137">At this point, the project still needs a player object.</span></span> <span data-ttu-id="0ea21-138">In Unreal, l'oggetto **Pawn** (Pedone) rappresenta l'utente del gioco, ma in questo caso sarà l'esperienza HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0ea21-138">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="0ea21-139">Fai clic su **Add New > Blueprint Class** (Aggiungi nuovo > Classe progetto) nella cartella **Content** ed espandi la sezione **All Classes** (Tutte le classi) in fondo.</span><span class="sxs-lookup"><span data-stu-id="0ea21-139">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span>
    * <span data-ttu-id="0ea21-140">Cercare **DefaultPawn**, fare clic su **Select** (Seleziona), assegnare il nome **MRPawn** e fare doppio clic sull'asset per aprirlo.</span><span class="sxs-lookup"><span data-stu-id="0ea21-140">Search for **DefaultPawn**, click **Select**, name it **MRPawn**, and double-click the asset to open.</span></span>

![Creare un nuovo pedone basato su DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

2. <span data-ttu-id="0ea21-142">Fare clic su **Add Component > Camera** (Aggiungi componente > Fotocamera) nel pannello **Components** (Componenti) e assegnare all'elemento il nome **Camera** (Fotocamera).</span><span class="sxs-lookup"><span data-stu-id="0ea21-142">Click **Add Component > Camera** from the **Components** panel and name it **Camera**.</span></span> <span data-ttu-id="0ea21-143">Verificare che il componente **Camera** sia un figlio diretto della radice (**CollisionComponent**).</span><span class="sxs-lookup"><span data-stu-id="0ea21-143">Make sure that the **Camera** component is a direct child of the root (**CollisionComponent**).</span></span> <span data-ttu-id="0ea21-144">In tal modo, la fotocamera del giocatore si muoverà insieme al dispositivo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0ea21-144">This allows the player camera to move with the HoloLens 2 device.</span></span>

> [!NOTE]
> <span data-ttu-id="0ea21-145">Per impostazione predefinita, i pedoni hanno componenti mesh e collisione.</span><span class="sxs-lookup"><span data-stu-id="0ea21-145">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="0ea21-146">Nella maggior parte dei progetti Unreal, i pedoni sono oggetti solidi che possono collidere con altri componenti.</span><span class="sxs-lookup"><span data-stu-id="0ea21-146">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="0ea21-147">Dato che il pedone e l'utente coincidono nella realtà mista, è necessario poter passare attraverso gli ologrammi senza collisioni.</span><span class="sxs-lookup"><span data-stu-id="0ea21-147">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span>

3. <span data-ttu-id="0ea21-148">Seleziona **CollisionComponent** nel pannello **Components** (Componenti) e scorri fino alla sezione **Collision** (Collisione) del pannello **Details** (Dettagli).</span><span class="sxs-lookup"><span data-stu-id="0ea21-148">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span>
    * <span data-ttu-id="0ea21-149">Fai clic sull'elenco a discesa **Collision Presets** (Set di impostazioni di collisione) e cambia il valore in **NoCollision**.</span><span class="sxs-lookup"><span data-stu-id="0ea21-149">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span>
    * <span data-ttu-id="0ea21-150">Eseguire la stessa operazione per **MeshComponent**.</span><span class="sxs-lookup"><span data-stu-id="0ea21-150">Do the same for the **MeshComponent**</span></span>

![Modifica dei set di impostazioni di collisione del pedone](images/unreal-uxt/3-nocollision.PNG)

4. <span data-ttu-id="0ea21-152">Fare clic su **Compile** (Compila) e quindi su **Save** (Salva) per salvare il progetto.</span><span class="sxs-lookup"><span data-stu-id="0ea21-152">**Compile** and **Save** the Blueprint.</span></span>

<span data-ttu-id="0ea21-153">Al termine, torna alla finestra principale.</span><span class="sxs-lookup"><span data-stu-id="0ea21-153">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="0ea21-154">Crea una modalità di gioco</span><span class="sxs-lookup"><span data-stu-id="0ea21-154">Create a Game Mode</span></span>

<span data-ttu-id="0ea21-155">Per completare la configurazione della realtà mista manca solo la modalità di gioco.</span><span class="sxs-lookup"><span data-stu-id="0ea21-155">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="0ea21-156">La modalità di gioco determina una serie di impostazioni relative al gioco o all'esperienza, incluso il pedone predefinito da usare.</span><span class="sxs-lookup"><span data-stu-id="0ea21-156">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="0ea21-157">Fare clic su **Add New > Blueprint Class** (Aggiungi nuovo > Classe progetto) nella cartella **Content** (Contenuto) e selezionare **Game Mode Base** (Base modalità gioco) come classe padre.</span><span class="sxs-lookup"><span data-stu-id="0ea21-157">Click **Add New > Blueprint Class** in the **Content** folder and select **Game Mode Base** as the parent class.</span></span> <span data-ttu-id="0ea21-158">Denominarla **MRGameMode** e fare doppio clic per aprirla.</span><span class="sxs-lookup"><span data-stu-id="0ea21-158">Name it **MRGameMode** and double-click to open.</span></span>

![MRGameMode nel browser dei contenuti](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="0ea21-160">Passa alla sezione **Classes** (Classi) nel pannello **Details** (Dettagli) e modifica **Default Pawn Class** (Classe pedone predefinito) in **MRPawn**.</span><span class="sxs-lookup"><span data-stu-id="0ea21-160">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span>
    * <span data-ttu-id="0ea21-161">Seleziona **Compile** (Compila) e **Save** (Salva) e torna alla finestra principale.</span><span class="sxs-lookup"><span data-stu-id="0ea21-161">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![Impostazione della classe di pedone predefinita](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="0ea21-163">Seleziona **Edit > Projects Settings** (Modifica > Impostazioni progetti) e fai clic su **Maps & Modes** (Mappe e modalità) nell'elenco a sinistra.</span><span class="sxs-lookup"><span data-stu-id="0ea21-163">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span>
    * <span data-ttu-id="0ea21-164">Espandi **Default Modes** (Modalità predefinite) e cambia **Default Game Mode** (Modalità gioco predefinita) in **MRGameMode**.</span><span class="sxs-lookup"><span data-stu-id="0ea21-164">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span>
    * <span data-ttu-id="0ea21-165">Espandi **Default Maps** (Mappe predefinite) e imposta sia **EditorStartupMap** sia **GameDefaultMap** su **Main** (Principale).</span><span class="sxs-lookup"><span data-stu-id="0ea21-165">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="0ea21-166">Quando si chiude e si riapre l'editor o si usa il gioco, per impostazione predefinita viene selezionata la mappa principale.</span><span class="sxs-lookup"><span data-stu-id="0ea21-166">When you close and reopen the editor or play the game, the Main map will now be selected by default.</span></span>

![Project Settings - Maps & Modes (Impostazioni progetto - Mappe e modalità)](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="0ea21-168">Dopo aver completato la configurazione del progetto per la realtà mista, è possibile passare all'esercitazione successiva e iniziare ad aggiungere input utente alla scena.</span><span class="sxs-lookup"><span data-stu-id="0ea21-168">With the project fully set up for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span>

[<span data-ttu-id="0ea21-169">Sezione successiva: 4. Rendere la scena interattiva</span><span class="sxs-lookup"><span data-stu-id="0ea21-169">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)
