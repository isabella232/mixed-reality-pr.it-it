---
title: 5. Aggiunta di un pulsante e ripristino delle posizioni dei pezzi
description: Parte 5 di 6 in una serie di esercitazioni per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 08/14/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: f7b57cf8a023874aa14118ff5cd50076bbf344e0
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91702348"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="6b6e4-104">5. Aggiunta di un pulsante e ripristino delle posizioni dei pezzi</span><span class="sxs-lookup"><span data-stu-id="6b6e4-104">5. Adding a button & resetting piece locations</span></span>


## <a name="overview"></a><span data-ttu-id="6b6e4-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="6b6e4-105">Overview</span></span>

<span data-ttu-id="6b6e4-106">Nell'esercitazione precedente hai aggiunto attori di interazione manuale al pedone e componenti manipolatore alla scacchiera per renderli entrambi interattivi.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-106">In the previous tutorial, you added Hand Interaction Actors to the Pawn and Manipulator components to the chess board to make them both interactive.</span></span> <span data-ttu-id="6b6e4-107">In questa sezione continuerai a usare il plug-in UX Tools di Mixed Reality Toolkit costruendo le funzionalità dell'app di scacchi.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-107">In this section, you'll continue working with the Mixed Reality Toolkit UX Tools plugin by building out the features of your chess app.</span></span> <span data-ttu-id="6b6e4-108">Durante il processo creerai una nuova funzione e scoprirai come ottenere riferimenti agli attori in un progetto.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-108">This includes creating a new function and learning how to get references to Actors in a Blueprint.</span></span> <span data-ttu-id="6b6e4-109">Al termine di questa sezione sarai in grado di creare un pacchetto dell'app di realtà mista e distribuirla in un dispositivo o emulatore.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-109">By the end of this section, you'll be ready to package and deploy the mixed reality app on a device or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="6b6e4-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="6b6e4-110">Objectives</span></span>

* <span data-ttu-id="6b6e4-111">Aggiunta di un pulsante interattivo</span><span class="sxs-lookup"><span data-stu-id="6b6e4-111">Adding an interactive button</span></span>
* <span data-ttu-id="6b6e4-112">Creazione di una funzione per la riportare un pezzo nella posizione iniziale</span><span class="sxs-lookup"><span data-stu-id="6b6e4-112">Creating a function to reset a pieces' location</span></span>
* <span data-ttu-id="6b6e4-113">Associazione del pulsante in modo che attivi la funzione quando viene premuto</span><span class="sxs-lookup"><span data-stu-id="6b6e4-113">Hooking the button up to trigger the function when pressed</span></span>

## <a name="creating-a-reset-function"></a><span data-ttu-id="6b6e4-114">Creazione di una funzione di reimpostazione</span><span class="sxs-lookup"><span data-stu-id="6b6e4-114">Creating a reset function</span></span>
<span data-ttu-id="6b6e4-115">La prima attività consiste nel creare un progetto di funzione che riporta un pezzo degli scacchi nella sua posizione originale nella scena.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-115">Your first task is to create a function blueprint that resets a chess piece to its original position in the scene.</span></span> 

1.  <span data-ttu-id="6b6e4-116">Apri **WhiteKing** (Re bianco), fai clic sull'icona **+** accanto alla sezione **Functions** (Funzioni) in **My Blueprint** (Progetto personale) e assegna alla funzione il nome **Reset Location** (Ripristina posizione).</span><span class="sxs-lookup"><span data-stu-id="6b6e4-116">Open **WhiteKing** , click the **+** icon next to the **Functions** section in the **My Blueprint** and name it **Reset Location** .</span></span> 

2.  <span data-ttu-id="6b6e4-117">Trascina e rilascia l'esecuzione da **Reset Location** (Ripristina posizione) nella griglia del progetto per creare un nodo **SetActorRelativeTransform** .</span><span class="sxs-lookup"><span data-stu-id="6b6e4-117">Drag and release the execution from **Reset Location** on the Blueprint grid to create a **SetActorRelativeTransform** node.</span></span> 
    * <span data-ttu-id="6b6e4-118">Questa funzione imposta la trasformazione (posizione, rotazione e scala) di un attore rispetto al relativo elemento padre.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-118">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="6b6e4-119">Questa funzione verrà usata per ripristinare la posizione del Re sulla scacchiera, anche se è stata spostata dalla posizione originale.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-119">You’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span> 
    
3. <span data-ttu-id="6b6e4-120">Fai clic con il pulsante destro del mouse all'interno di Event Graph (Grafico eventi), scegli **Make Transform** (Crea trasformazione) e imposta **Location** (Posizione) su **X = -26** , **Y = 4** , **Z = 0** .</span><span class="sxs-lookup"><span data-stu-id="6b6e4-120">Right-click inside the Event Graph, select **Make Transform** , and change its **Location** to **X = -26** , **Y = 4** , **Z = 0** .</span></span>
    * <span data-ttu-id="6b6e4-121">Connetti il relativo **Return Value** (Valore restituito) al segnaposto **New Relative Transform** (Nuova trasformazione relativa) in **SetActorRelativeTransform** .</span><span class="sxs-lookup"><span data-stu-id="6b6e4-121">Connect its **Return Value** to the **New Relative Transform** pin in **SetActorRelativeTransform** .</span></span> 

![Funzione di ripristino della posizione](images/unreal-uxt/5-function.PNG)

<span data-ttu-id="6b6e4-123">Scegli **Compile** (Compila) e **Save** (Salva) per compilare e salvare il progetto prima di tornare alla finestra princpale.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-123">**Compile** and **Save** the project before returning to the Main window.</span></span> 


## <a name="adding-a-button"></a><span data-ttu-id="6b6e4-124">Aggiunta di un pulsante</span><span class="sxs-lookup"><span data-stu-id="6b6e4-124">Adding a button</span></span>
<span data-ttu-id="6b6e4-125">Ora che la funzione è stata configurata correttamente, l'attività successiva consiste nel creare un pulsante che la attiva quando viene toccato.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-125">Now that the function is setup correctly, your next task is to create a button that fires it off when touched.</span></span> 


1.  <span data-ttu-id="6b6e4-126">Fare clic su **Add New > Blueprint Class** (Aggiungi nuovo > Classe progetto), espandere la sezione **All Classes** (Tutte le classi) e cercare **BP_ButtonHoloLens2** .</span><span class="sxs-lookup"><span data-stu-id="6b6e4-126">Click **Add New > Blueprint Class** , expand the **All Classes** section, and search for **BP_ButtonHoloLens2** .</span></span> 
    * <span data-ttu-id="6b6e4-127">Assegna il nome **ResetButton** e fai doppio clic per aprire il progetto.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-127">Name it **ResetButton** and double click to open the Blueprint</span></span>

> [!NOTE]
> <span data-ttu-id="6b6e4-128">**BP_ButtonHoloLens2** è un attore di progetto di un pulsante 3D incluso nel plug-in UX Tools.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-128">**BP_ButtonHoloLens2** is a 3D button Blueprint Actor that's part of the UX Tools plugin.</span></span>

![Creare il nuovo progetto come sottoclasse del pulsante di stile HoloLens 2](images/unreal-uxt/5-subclass.PNG)

2. <span data-ttu-id="6b6e4-130">Verificare che sia selezionata l'opzione **ResetButton(self)** nel pannello **Components** (Componenti).</span><span class="sxs-lookup"><span data-stu-id="6b6e4-130">Ensure **ResetButton(self)** is selected in the **Components** panel.</span></span> <span data-ttu-id="6b6e4-131">Nel pannello **Details** (Dettagli) passare alla sezione **Button** (Pulsante).</span><span class="sxs-lookup"><span data-stu-id="6b6e4-131">In the **Details** panel, navigate to the **Button** section.</span></span> <span data-ttu-id="6b6e4-132">Cambiare il valore predefinito di **Button Label** (Etichetta pulsante) in "Reset".</span><span class="sxs-lookup"><span data-stu-id="6b6e4-132">Change the default **Button Label** to "Reset".</span></span> <span data-ttu-id="6b6e4-133">Espandere la sezione **Button Icon Brush** (Pennello icona pulsante) e selezionare il pulsante **Open Icon Brush Editor** (Apri Icon Brush Editor).</span><span class="sxs-lookup"><span data-stu-id="6b6e4-133">Expand the **Button Icon Brush** section and press the **Open Icon Brush Editor** button.</span></span> 

![Impostare l'etichetta e l'icona sul pulsante](images/unreal-uxt/5-buttonconfig.PNG)

<span data-ttu-id="6b6e4-135">Verrà aperta l'utilità Icon Brush Editor fornita dal plug-in UX Tools, che consente di selezionare una nuova icona per il pulsante.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-135">This will open up the Icon Brush Editor, which is a utility provided by the UX Tools plugin which you can use to select a new icon for your button.</span></span> 

![Selezionare un'icona per il pulsante](images/unreal-uxt/5-iconbrusheditor.PNG)

<span data-ttu-id="6b6e4-137">È possibile modificare molte altre impostazioni per configurare il pulsante.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-137">There are plenty of other settings you can adjust to configure your button.</span></span> <span data-ttu-id="6b6e4-138">Per altre informazioni sul componente UXT Pressable Button, vedere la [documentazione](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html).</span><span class="sxs-lookup"><span data-stu-id="6b6e4-138">To learn more about the UXT Pressable Button component, check out the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html).</span></span>

3. <span data-ttu-id="6b6e4-139">Fare clic su **UxtPressableButton (Inherited)** (UxtPressableButton - Ereditato) nel pannello **Components** (Componenti) e scorrere verso il basso nel pannello **Details** (Dettagli) fino alla sezione **Events** (Eventi).</span><span class="sxs-lookup"><span data-stu-id="6b6e4-139">Click **UxtPressableButton (Inherited)** in the **Components** panel and scroll down the **Details** panel to the **Events** section.</span></span> 
    * <span data-ttu-id="6b6e4-140">Fai clic sul pulsante **+** verde accanto a **On Button Pressed** (Alla pressione del pulsante) per aggiungere un evento al grafico degli eventi, che verrà chiamato ogni volta che viene premuto il pulsante.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-140">Click the green **+** button next to **On Button Pressed** to add an event to the Event Graph, which will be called when the button is pressed.</span></span> 
    
<span data-ttu-id="6b6e4-141">A questo punto puoi chiamare la funzione **Reset Location** (Ripristina posizione) di **WhiteKing** (Re bianco), che necessita un riferimento all'attore **WhiteKing** (Re bianco) nel livello.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-141">From here, you’ll want to call **WhiteKing** ’s **Reset Location** function, which needs a reference to the **WhiteKing** Actor in the Level.</span></span> 

4.  <span data-ttu-id="6b6e4-142">Nel pannello **My Blueprint** (Progetto personale) passare alla sezione **Variables** (Variabili), fare clic sul pulsante **+** e assegnare alla variabile il nome **WhiteKing** .</span><span class="sxs-lookup"><span data-stu-id="6b6e4-142">In the **My Blueprint** panel, navigate to the **Variables** section , click the **+** button and name the variable **WhiteKing** .</span></span> 
    * <span data-ttu-id="6b6e4-143">Nel pannello **Details** (Dettagli) selezionare l'elenco a discesa accanto a **Variable Type** (Tipo di variabile), cercare **WhiteKing** e selezionare **Object Reference** (Riferimento oggetto).</span><span class="sxs-lookup"><span data-stu-id="6b6e4-143">In the **Details** panel, select the dropdown next to **Variable Type** , search for **WhiteKing** , and select the **Object Reference** .</span></span> 
    * <span data-ttu-id="6b6e4-144">Seleziona la casella accanto a **Instance Editable** (Istanza modificabile).</span><span class="sxs-lookup"><span data-stu-id="6b6e4-144">Check the box next to **Instance Editable** .</span></span> <span data-ttu-id="6b6e4-145">In questo modo la variabile potrà essere impostata dal livello principale.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-145">This will allow the variable to be set from the Main Level.</span></span> 

![Creazione di una variabile](images/unreal-uxt/5-var.PNG)

5.  <span data-ttu-id="6b6e4-147">Trascina la variabile WhiteKing da **My Blueprint > Variables** (Progetto personale > Variabili) in Reset Button Event Graph (Grafico eventi ResetButton) e scegli **Get WhiteKing** (Ottieni WhiteKing).</span><span class="sxs-lookup"><span data-stu-id="6b6e4-147">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Reset Button Event Graph and choose **Get WhiteKing** .</span></span> 

## <a name="firing-the-function"></a><span data-ttu-id="6b6e4-148">Attivazione della funzione</span><span class="sxs-lookup"><span data-stu-id="6b6e4-148">Firing the function</span></span>
<span data-ttu-id="6b6e4-149">A questo punto non resta che attivare la funzione di reimpostazione alla pressione del pulsante.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-149">All that's left is to officially fire off the reset function when the button is pressed.</span></span>

1.  <span data-ttu-id="6b6e4-150">Trascina il pin di output di WhiteKing e rilascialo per inserire un nuovo nodo.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-150">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="6b6e4-151">Seleziona la funzione **Reset Location** (Ripristina posizione).</span><span class="sxs-lookup"><span data-stu-id="6b6e4-151">Select the **Reset Location** function.</span></span> <span data-ttu-id="6b6e4-152">Trascina infine il pin di esecuzione in uscita da **On Button Pressed** (Alla pressione del pulsante) al pin di esecuzione in ingresso in **Reset Location** (Ripristina posizione).</span><span class="sxs-lookup"><span data-stu-id="6b6e4-152">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location** .</span></span> <span data-ttu-id="6b6e4-153">Fai clic su **Compile** (Compila) e quindi su **Save** (Salva) per salvare il progetto ResetButton e quindi torna alla finestra principale.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-153">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span> 

![Chiamata della funzione di ripristino della posizione alla pressione del pulsante](images/unreal-uxt/5-callresetloc.PNG)

2.  <span data-ttu-id="6b6e4-155">Trascina **ResetButton** nel viewport e impostane la posizione su **X = 50** , **Y = -25** e **Z = 10** .</span><span class="sxs-lookup"><span data-stu-id="6b6e4-155">Drag **ResetButton** into the viewport and set its location to **X = 50** , **Y = -25** , and **Z = 10** .</span></span> <span data-ttu-id="6b6e4-156">Impostarne la rotazione su **Z = 180** .</span><span class="sxs-lookup"><span data-stu-id="6b6e4-156">Set its rotation to **Z = 180** .</span></span> <span data-ttu-id="6b6e4-157">In **Default** (Valore predefinito) imposta il valore della variabile **WhiteKing** su **WhiteKing** .</span><span class="sxs-lookup"><span data-stu-id="6b6e4-157">Under **Default** , set the value of the **WhiteKing** variable to **WhiteKing** .</span></span>

![Impostazione della variabile](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="6b6e4-159">Eseguire l'app, spostare il pezzo in una nuova posizione e premere il pulsante di stile HoloLens 2 per vedere in azione la logica di reimpostazione.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-159">Run the app, move the chess piece to a new location, and press your HoloLens 2-style button to see the reset logic in action!</span></span>

<span data-ttu-id="6b6e4-160">Ora hai un'app di realtà mista con un pezzo degli scacchi e una scacchiera con cui puoi interagire, nonché un pulsante completamente funzionante che, quando viene premuto, ripristina la posizione del pezzo.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-160">You now have a mixed reality app with a chess piece and board that you can interact with, as well as a fully functioning button that will reset the piece’s location.</span></span> <span data-ttu-id="6b6e4-161">L'app completata fino a questo punto è disponibile nel repository di [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) corrispondente.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-161">You can find the completed app up to this point in its [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) repo.</span></span> <span data-ttu-id="6b6e4-162">Al termine di questa esercitazione puoi proseguire configurando gli altri pezzi degli scacchi, in modo che venga ripristinata l'intera scacchiera quando viene premuto il pulsante.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-162">Feel free to go beyond this tutorial and set up the remainder of the chess pieces so that the entire board is reset when the button is pressed.</span></span>

![Schermata finale in viewport](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="6b6e4-164">Ora puoi passare alla sezione finale di questa esercitazione, in cui viene illustrato come creare un pacchetto dell'app e distribuirla in un dispositivo o emulatore.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-164">You're ready to move on to the final section of this tutorial where you'll learn how to correctly package and deploy the app to a device or emulator.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6b6e4-165">A questo punto è consigliabile aggiornare il progetto con le **[Impostazioni per le prestazioni di Unreal](../performance-recommendations-for-unreal.md)** consigliate prima di distribuire l'applicazione in un dispositivo o emulatore.</span><span class="sxs-lookup"><span data-stu-id="6b6e4-165">At this point, you should update your project with the recommended **[Unreal performance settings](../performance-recommendations-for-unreal.md)** before deploying your application to a device or emulator.</span></span>

[<span data-ttu-id="6b6e4-166">Sezione successiva: 6. Creazione di pacchetti e distribuzione nel dispositivo o nell'emulatore</span><span class="sxs-lookup"><span data-stu-id="6b6e4-166">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)
