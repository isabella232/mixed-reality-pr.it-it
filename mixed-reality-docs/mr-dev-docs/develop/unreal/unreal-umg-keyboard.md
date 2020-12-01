---
title: UMG e tastiera in Unreal
description: Informazioni su come usare i grafici di movimento di Unreal per creare un sistema di interfaccia utente all'esterno dei widget.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, HoloLens 2, rilevamento degli occhi, input di sguardi, visualizzazione montata su schermo, Unreal Engine, auricolare realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, widget, interfaccia utente, UMG, grafica di movimento non reale, Unreal Engine, UE, UE4
ms.openlocfilehash: 9f22a5f7a13732727b6b122d385aad7e708a1343
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355409"
---
# <a name="umg-and-keyboard-in-unreal"></a><span data-ttu-id="160e5-104">UMG e tastiera in Unreal</span><span class="sxs-lookup"><span data-stu-id="160e5-104">UMG and keyboard in Unreal</span></span>

<span data-ttu-id="160e5-105">Unreal Motion Graphics (UMG) è il sistema di interfaccia utente incorporato del motore di Unreal, usato per creare interfacce quali menu e caselle di testo.</span><span class="sxs-lookup"><span data-stu-id="160e5-105">Unreal Motion Graphics (UMG) is Unreal Engine’s built-in UI system, used to create interfaces such as menus and text boxes.</span></span> <span data-ttu-id="160e5-106">Le interfacce utente compilate con UMG sono costituite da widget.</span><span class="sxs-lookup"><span data-stu-id="160e5-106">User interfaces built with UMG consist of widgets.</span></span> <span data-ttu-id="160e5-107">In questa guida viene illustrato come creare un nuovo widget, aggiungerlo allo spazio globale e abilitare l'interazione con tale widget in realtà mista, usando la tastiera di sistema come esempio.</span><span class="sxs-lookup"><span data-stu-id="160e5-107">This guide will show you how to create a new widget, add it to world space, and enable interaction with that widget in mixed reality, using the system keyboard as an example.</span></span> <span data-ttu-id="160e5-108">Per altre informazioni su UMG, vedere la [documentazione](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)ufficiale di Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="160e5-108">You can learn more about UMG in the official Unreal Engine [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span></span> 

## <a name="create-a-new-widget"></a><span data-ttu-id="160e5-109">Creare un nuovo widget</span><span class="sxs-lookup"><span data-stu-id="160e5-109">Create a new widget</span></span>

- <span data-ttu-id="160e5-110">Creare un progetto widget per il layout dell'interfaccia utente del gioco:</span><span class="sxs-lookup"><span data-stu-id="160e5-110">Create a Widget Blueprint to lay out the game’s UI:</span></span>

![Screenshot dell'aggiunta di un progetto widget dal menu Unreal](images/unreal-umg-img-01.png)

- <span data-ttu-id="160e5-112">Aprire il nuovo progetto e aggiungere componenti dalla tavolozza all'area di disegno.</span><span class="sxs-lookup"><span data-stu-id="160e5-112">Open the new blueprint and add components from the Palette to the canvas.</span></span>  <span data-ttu-id="160e5-113">In questo caso sono stati aggiunti due componenti della casella di testo dalla sezione "input":</span><span class="sxs-lookup"><span data-stu-id="160e5-113">In this case we have added two Text Box components from the “Input” section:</span></span>

![Screenshot della finestra della gerarchia con componente del widget di testo evidenziato ed espanso](images/unreal-umg-img-02.png)

- <span data-ttu-id="160e5-115">Selezionare un widget nella gerarchia o nella finestra di progettazione e modificare i parametri nel pannello dei dettagli.</span><span class="sxs-lookup"><span data-stu-id="160e5-115">Select a widget in the Hierarchy or Designer window and modify parameters in the details panel.</span></span>  <span data-ttu-id="160e5-116">In questo caso, è stato aggiunto un "testo suggerimento" predefinito e un colore tinta quando il cursore è posizionato sulla casella di testo per fornire commenti e suggerimenti su cui il widget è pronto per l'interazione.</span><span class="sxs-lookup"><span data-stu-id="160e5-116">In this case, we’ve added some default “Hint Text” and a tint color when the cursor is hovering over the text box to give feedback that the widget is ready to be interacted with.</span></span>  <span data-ttu-id="160e5-117">In una casella di testo viene visualizzata una tastiera virtuale in HoloLens quando viene interagito con:</span><span class="sxs-lookup"><span data-stu-id="160e5-117">A text box will pop up a virtual keyboard on HoloLens when it is interacted with:</span></span>

![Screenshot dei parametri modificati nella finestra gerarchia](images/unreal-umg-img-03.png)

- <span data-ttu-id="160e5-119">È anche possibile sottoscrivere gli eventi nel pannello dei dettagli:</span><span class="sxs-lookup"><span data-stu-id="160e5-119">Events can also be subscribed to in the details panel:</span></span>

![Screenshot degli eventi nel pannello dei dettagli](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a><span data-ttu-id="160e5-121">Aggiungere un widget allo spazio globale</span><span class="sxs-lookup"><span data-stu-id="160e5-121">Add a Widget to World Space</span></span>

- <span data-ttu-id="160e5-122">Creare un nuovo attore, aggiungere un componente widget e aggiungere l'attore alla scena:</span><span class="sxs-lookup"><span data-stu-id="160e5-122">Create a new Actor, add a Widget component, and add the actor to the scene:</span></span>

![Screenshot di un attore con un widget collegato](images/unreal-umg-img-05.png)

- <span data-ttu-id="160e5-124">Nel pannello dei dettagli per il widget impostare la **classe Widget** sul progetto widget creato in precedenza:</span><span class="sxs-lookup"><span data-stu-id="160e5-124">In the details panel for the Widget, set the **Widget Class** to the Widget Blueprint created earlier:</span></span>

![Screenshot del pannello Dettagli progetto con la classe Widget impostata](images/unreal-umg-img-06.png)

- <span data-ttu-id="160e5-126">Per un widget di testo, verificare che la **ricezione dell'input hardware** sia deselezionata, in modo da aggiornare solo il testo dalla tastiera virtuale:</span><span class="sxs-lookup"><span data-stu-id="160e5-126">For a text Widget, ensure **Receive Hardware Input** is unchecked so we only update its text from the virtual keyboard:</span></span>

![Screenshot della sezione interazione con l'input hardware di ricezione non selezionata](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a><span data-ttu-id="160e5-128">Interazione widget</span><span class="sxs-lookup"><span data-stu-id="160e5-128">Widget Interaction</span></span>

<span data-ttu-id="160e5-129">I widget UMG ricevono in genere l'input da un mouse.</span><span class="sxs-lookup"><span data-stu-id="160e5-129">UMG Widgets typically receive input from a mouse.</span></span>  <span data-ttu-id="160e5-130">In HoloLens o VR è necessario simulare un mouse con un componente di interazione widget per ottenere gli stessi eventi.</span><span class="sxs-lookup"><span data-stu-id="160e5-130">On HoloLens or VR, we need to simulate a mouse with a Widget Interaction component to get the same events.</span></span>

- <span data-ttu-id="160e5-131">Creare un nuovo attore, aggiungere un componente di **interazione widget** e aggiungere l'attore alla scena:</span><span class="sxs-lookup"><span data-stu-id="160e5-131">Create a new Actor, add a **Widget Interaction** component, and add the actor to your scene:</span></span>

![Screenshot di un nuovo attore con un componente di interazione widget evidenziato](images/unreal-umg-img-08.png)

- <span data-ttu-id="160e5-133">Nel pannello dei dettagli per il componente interazione widget impostare la distanza di interazione sulla distanza desiderata, impostare l' **origine interazione** su **personalizzata** e per lo sviluppo impostare **Mostra debug** su **true**:</span><span class="sxs-lookup"><span data-stu-id="160e5-133">In the details panel for the Widget Interaction component, set the interaction distance to the desired distance, set the **Interaction Source** to **custom**, and for development, set **Show Debug** to **true**:</span></span>

![Screenshot delle proprietà del componente interazione e debug del widget](images/unreal-umg-img-09.png)

<span data-ttu-id="160e5-135">Il valore predefinito per l'origine interazione è "World", che deve inviare raycasts in base alla posizione globale del componente di interazione del widget, ma in AR e VR questa situazione non sembra essere la stessa.</span><span class="sxs-lookup"><span data-stu-id="160e5-135">The default for Interaction Source is “World”, which should send raycasts based on the world position of the Widget Interaction component, but in AR and VR this does not appear to be the case.</span></span>  <span data-ttu-id="160e5-136">L'abilitazione di "Mostra debug" e l'aggiunta di una tinta del passaggio del mouse ai widget durante lo sviluppo è importante per verificare la correttezza del componente interazione widget.</span><span class="sxs-lookup"><span data-stu-id="160e5-136">Enabling “Show Debug” and adding a hover tint to widgets while developing is important to sanity check the widget interaction component is doing what you expect.</span></span>  <span data-ttu-id="160e5-137">La soluzione alternativa consiste nell'usare un'origine personalizzata e impostare Raycast nel grafico eventi dal raggio della mano.</span><span class="sxs-lookup"><span data-stu-id="160e5-137">The workaround is to use a custom source and set the raycast in the event graph from the hand ray.</span></span>  

<span data-ttu-id="160e5-138">Qui viene chiamato il simbolo di evento:</span><span class="sxs-lookup"><span data-stu-id="160e5-138">Here we are calling this from Event Tick:</span></span>

![Progetto del segno di evento](images/unreal-umg-img-10.png)

<span data-ttu-id="160e5-140">Aggiungere quindi gli eventi del puntatore del mouse virtuale al componente di interazione del widget che reagisce all'input HoloLens.</span><span class="sxs-lookup"><span data-stu-id="160e5-140">Then add virtual mouse pointer events to the widget interaction component reacting to HoloLens input.</span></span>  <span data-ttu-id="160e5-141">In questo caso, inviare un evento di pressione del mouse sinistro quando la mano viene afferrata e un evento di rilascio del mouse a sinistra quando non viene afferrato:</span><span class="sxs-lookup"><span data-stu-id="160e5-141">In this case, send a Left Mouse press event when the hand is grasped, and a Left Mouse release event when not grasped:</span></span>

![Progetto con eventi di puntatore del mouse virtuale aggiunti](images/unreal-umg-img-13.png)

<span data-ttu-id="160e5-143">A questo punto, quando si distribuisce l'app in HoloLens 2, verrà visualizzato un raggio a mano che si estende da destra.</span><span class="sxs-lookup"><span data-stu-id="160e5-143">Now, when you deploy the app to the HoloLens 2, you’ll see a hand ray extending from your right hand.</span></span> <span data-ttu-id="160e5-144">Se viene indirizzato a una delle caselle di testo modificabili e al tocco aereo, la tastiera di sistema viene visualizzata davanti all'utente e consente di immettere il testo.</span><span class="sxs-lookup"><span data-stu-id="160e5-144">If you direct it at one of the editable text boxes and air tap, the system keyboard will appear in front of you and allow you to enter text.</span></span> 
 
> [!NOTE]
> <span data-ttu-id="160e5-145">La tastiera di sistema HoloLens richiede Unreal Engine 4,26 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="160e5-145">The HoloLens system keyboard requires Unreal Engine 4.26 or later.</span></span> <span data-ttu-id="160e5-146">Inoltre, la tastiera non verrà visualizzata quando l'app viene trasmessa da un editor non reale all'auricolare, solo quando l'app è in esecuzione nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="160e5-146">Additionally, the keyboard will not appear when your app is being streamed from the Unreal editor to the headset, only when the app is running on device.</span></span>

## <a name="see-also"></a><span data-ttu-id="160e5-147">Vedere anche:</span><span class="sxs-lookup"><span data-stu-id="160e5-147">See Also:</span></span>
* [<span data-ttu-id="160e5-148">Documentazione di UMG di Unreal</span><span class="sxs-lookup"><span data-stu-id="160e5-148">Unreal's UMG documentation</span></span>](https://docs.unrealengine.com/Engine/UMG/index.html)
* [<span data-ttu-id="160e5-149">Esercitazioni di UMG di Unreal</span><span class="sxs-lookup"><span data-stu-id="160e5-149">Unreal's UMG tutorials</span></span>](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
