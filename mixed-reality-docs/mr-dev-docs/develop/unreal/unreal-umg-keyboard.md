---
title: UMG e tastiera in Unreal
description: Informazioni su come usare i grafici di movimento di Unreal per creare un sistema di interfaccia utente all'esterno dei widget.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Realtà mista di Windows, ologrammi, HoloLens 2, rilevamento degli occhi, input di sguardi, visualizzazione montata su schermo, Unreal Engine, auricolare realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, widget, interfaccia utente, UMG, grafica di movimento non reale, Unreal Engine, UE, UE4
ms.openlocfilehash: 59ad108a0e27298256f4f0d1661381a4f1748777
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609762"
---
# <a name="umg-and-keyboard-in-unreal"></a><span data-ttu-id="5be77-104">UMG e tastiera in Unreal</span><span class="sxs-lookup"><span data-stu-id="5be77-104">UMG and keyboard in Unreal</span></span>

<span data-ttu-id="5be77-105">Unreal Motion Graphics (UMG) è il sistema di interfaccia utente incorporato del motore di Unreal, usato per creare interfacce quali menu e caselle di testo.</span><span class="sxs-lookup"><span data-stu-id="5be77-105">Unreal Motion Graphics (UMG) is Unreal Engine’s built-in UI system, used to create interfaces such as menus and text boxes.</span></span> <span data-ttu-id="5be77-106">Le interfacce utente compilate con UMG sono costituite da widget.</span><span class="sxs-lookup"><span data-stu-id="5be77-106">User interfaces built with UMG consist of widgets.</span></span> <span data-ttu-id="5be77-107">Verranno fornite istruzioni per la creazione di un nuovo widget, per aggiungerlo allo spazio globale e per abilitare l'interazione utilizzando la tastiera di sistema come esempio.</span><span class="sxs-lookup"><span data-stu-id="5be77-107">We'll guide you through creating a new widget, adding it to world space, and enabling interaction using the system keyboard as an example.</span></span> <span data-ttu-id="5be77-108">Per altre informazioni su UMG, vedere la [documentazione](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)ufficiale di Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="5be77-108">You can learn more about UMG in the official Unreal Engine [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span></span> 

## <a name="create-a-new-widget"></a><span data-ttu-id="5be77-109">Creare un nuovo widget</span><span class="sxs-lookup"><span data-stu-id="5be77-109">Create a new widget</span></span>

- <span data-ttu-id="5be77-110">Creare un progetto widget per il layout dell'interfaccia utente del gioco:</span><span class="sxs-lookup"><span data-stu-id="5be77-110">Create a Widget Blueprint to lay out the game’s UI:</span></span>

![Screenshot dell'aggiunta di un progetto widget dal menu Unreal](images/unreal-umg-img-01.png)

- <span data-ttu-id="5be77-112">Aprire il nuovo progetto e aggiungere componenti dalla tavolozza all'area di disegno.</span><span class="sxs-lookup"><span data-stu-id="5be77-112">Open the new blueprint and add components from the Palette to the canvas.</span></span>  <span data-ttu-id="5be77-113">In questo caso sono stati aggiunti due componenti della casella di testo dalla sezione "input":</span><span class="sxs-lookup"><span data-stu-id="5be77-113">In this case, we've added two Text Box components from the “Input” section:</span></span>

![Screenshot della finestra della gerarchia con componente del widget di testo evidenziato ed espanso](images/unreal-umg-img-02.png)

- <span data-ttu-id="5be77-115">Selezionare un widget nella gerarchia o nella finestra di progettazione e modificare i parametri nel pannello dei dettagli.</span><span class="sxs-lookup"><span data-stu-id="5be77-115">Select a widget in the Hierarchy or Designer window and modify parameters in the details panel.</span></span>  <span data-ttu-id="5be77-116">In questo caso, è stato aggiunto un "testo suggerimento" predefinito e un colore tinta visualizzato quando si passa il mouse sulla casella di testo.</span><span class="sxs-lookup"><span data-stu-id="5be77-116">In this case, we’ve added some default “Hint Text” and a tint color that appears when you hover over the text box.</span></span>  <span data-ttu-id="5be77-117">In una casella di testo viene visualizzata una tastiera virtuale in HoloLens quando viene interagito con:</span><span class="sxs-lookup"><span data-stu-id="5be77-117">A text box will pop up a virtual keyboard on HoloLens when it's interacted with:</span></span>

![Screenshot dei parametri modificati nella finestra gerarchia](images/unreal-umg-img-03.png)

- <span data-ttu-id="5be77-119">È anche possibile sottoscrivere gli eventi nel pannello dei dettagli:</span><span class="sxs-lookup"><span data-stu-id="5be77-119">Events can also be subscribed to in the details panel:</span></span>

![Screenshot degli eventi nel pannello dei dettagli](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a><span data-ttu-id="5be77-121">Aggiungere un widget allo spazio globale</span><span class="sxs-lookup"><span data-stu-id="5be77-121">Add a Widget to World Space</span></span>

- <span data-ttu-id="5be77-122">Creare un nuovo attore, aggiungere un componente widget e aggiungere l'attore alla scena:</span><span class="sxs-lookup"><span data-stu-id="5be77-122">Create a new Actor, add a Widget component, and add the actor to the scene:</span></span>

![Screenshot di un attore con un widget collegato](images/unreal-umg-img-05.png)

- <span data-ttu-id="5be77-124">Nel pannello dei dettagli per il widget impostare la **classe Widget** sul progetto widget creato in precedenza:</span><span class="sxs-lookup"><span data-stu-id="5be77-124">In the details panel for the Widget, set the **Widget Class** to the Widget Blueprint created earlier:</span></span>

![Screenshot del pannello Dettagli progetto con la classe Widget impostata](images/unreal-umg-img-06.png)

- <span data-ttu-id="5be77-126">Per un widget di testo, verificare che la **ricezione dell'input hardware** sia deselezionata, in modo da aggiornare solo il testo dalla tastiera virtuale:</span><span class="sxs-lookup"><span data-stu-id="5be77-126">For a text Widget, ensure **Receive Hardware Input** is unchecked so we only update its text from the virtual keyboard:</span></span>

![Screenshot della sezione interazione con l'input hardware di ricezione non selezionata](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a><span data-ttu-id="5be77-128">Interazione widget</span><span class="sxs-lookup"><span data-stu-id="5be77-128">Widget Interaction</span></span>

<span data-ttu-id="5be77-129">I widget UMG ricevono in genere l'input da un mouse.</span><span class="sxs-lookup"><span data-stu-id="5be77-129">UMG Widgets typically receive input from a mouse.</span></span>  <span data-ttu-id="5be77-130">In HoloLens o VR è necessario simulare un mouse con un componente di interazione widget per ottenere gli stessi eventi.</span><span class="sxs-lookup"><span data-stu-id="5be77-130">On HoloLens or VR, we need to simulate a mouse with a Widget Interaction component to get the same events.</span></span>

- <span data-ttu-id="5be77-131">Creare un nuovo attore, aggiungere un componente di **interazione widget** e aggiungere l'attore alla scena:</span><span class="sxs-lookup"><span data-stu-id="5be77-131">Create a new Actor, add a **Widget Interaction** component, and add the actor to your scene:</span></span>

![Screenshot di un nuovo attore con un componente di interazione widget evidenziato](images/unreal-umg-img-08.png)

- <span data-ttu-id="5be77-133">Nel pannello dei dettagli per il componente interazione widget:</span><span class="sxs-lookup"><span data-stu-id="5be77-133">In the details panel for the Widget Interaction component:</span></span>
    - <span data-ttu-id="5be77-134">Impostare la distanza di interazione sul valore della distanza desiderato</span><span class="sxs-lookup"><span data-stu-id="5be77-134">Set the interaction distance to the distance value you want</span></span>
    - <span data-ttu-id="5be77-135">Impostare l' **origine interazione** su **personalizzata**</span><span class="sxs-lookup"><span data-stu-id="5be77-135">Set the **Interaction Source** to **custom**</span></span>
    - <span data-ttu-id="5be77-136">Per lo sviluppo, impostare **Mostra debug** su **true**:</span><span class="sxs-lookup"><span data-stu-id="5be77-136">For development, set **Show Debug** to **true**:</span></span>

![Screenshot delle proprietà del componente interazione e debug del widget](images/unreal-umg-img-09.png)

<span data-ttu-id="5be77-138">Il valore predefinito per l'origine interazione è "World", che deve inviare raycasts in base alla posizione globale del componente di interazione del widget.</span><span class="sxs-lookup"><span data-stu-id="5be77-138">The default for Interaction Source is “World”, which should send raycasts based on the world position of the Widget Interaction component.</span></span> <span data-ttu-id="5be77-139">In AR e VR, questo non è il caso.</span><span class="sxs-lookup"><span data-stu-id="5be77-139">In AR and VR, that's not the case.</span></span>  <span data-ttu-id="5be77-140">L'abilitazione di "Mostra debug" e l'aggiunta di una tinta al passaggio del mouse ai widget è importante per verificare che il componente interazione widget stia eseguendo le operazioni desiderate.</span><span class="sxs-lookup"><span data-stu-id="5be77-140">Enabling “Show Debug” and adding a hover tint to widgets is important to check the widget interaction component is doing what you expect.</span></span>  <span data-ttu-id="5be77-141">La soluzione alternativa consiste nell'usare un'origine personalizzata e impostare Raycast nel grafico eventi dal raggio della mano.</span><span class="sxs-lookup"><span data-stu-id="5be77-141">The workaround is to use a custom source and set the raycast in the event graph from the hand ray.</span></span>  

<span data-ttu-id="5be77-142">Questa operazione viene chiamata dal segno di evento:</span><span class="sxs-lookup"><span data-stu-id="5be77-142">Here we're calling this from Event Tick:</span></span>

![Progetto del segno di evento](images/unreal-umg-img-10.png)

<span data-ttu-id="5be77-144">Aggiungere quindi gli eventi del puntatore del mouse virtuale al componente di interazione del widget che reagisce all'input HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5be77-144">Then add virtual mouse pointer events to the widget interaction component reacting to HoloLens input.</span></span>  <span data-ttu-id="5be77-145">In questo caso, inviare un evento di pressione del mouse sinistro quando la mano viene afferrata e un evento di rilascio del mouse a sinistra quando non viene afferrato:</span><span class="sxs-lookup"><span data-stu-id="5be77-145">In this case, send a Left Mouse press event when the hand is grasped, and a Left Mouse release event when not grasped:</span></span>

![Progetto con eventi di puntatore del mouse virtuale aggiunti](images/unreal-umg-img-13.png)

<span data-ttu-id="5be77-147">A questo punto, quando si distribuisce l'app in HoloLens 2, verrà visualizzato un raggio a mano che si estende da destra.</span><span class="sxs-lookup"><span data-stu-id="5be77-147">Now, when you deploy the app to the HoloLens 2, you’ll see a hand ray extending from your right hand.</span></span> <span data-ttu-id="5be77-148">Se viene indirizzato a una delle caselle di testo modificabili e al tocco aereo, la tastiera di sistema viene visualizzata davanti all'utente e consente di immettere il testo.</span><span class="sxs-lookup"><span data-stu-id="5be77-148">If you direct it at one of the editable text boxes and air tap, the system keyboard will appear in front of you and allow you to enter text.</span></span> 
 
> [!NOTE]
> <span data-ttu-id="5be77-149">La tastiera di sistema HoloLens richiede Unreal Engine 4,26 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="5be77-149">The HoloLens system keyboard requires Unreal Engine 4.26 or later.</span></span> <span data-ttu-id="5be77-150">Inoltre, la tastiera non verrà visualizzata quando l'app viene trasmessa da un editor non reale all'auricolare, solo quando l'app è in esecuzione nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5be77-150">Additionally, the keyboard will not appear when your app is being streamed from the Unreal editor to the headset, only when the app is running on device.</span></span>

## <a name="see-also"></a><span data-ttu-id="5be77-151">Vedere anche:</span><span class="sxs-lookup"><span data-stu-id="5be77-151">See Also:</span></span>
* [<span data-ttu-id="5be77-152">Documentazione di UMG di Unreal</span><span class="sxs-lookup"><span data-stu-id="5be77-152">Unreal's UMG documentation</span></span>](https://docs.unrealengine.com/Engine/UMG/index.html)
* [<span data-ttu-id="5be77-153">Esercitazioni di UMG di Unreal</span><span class="sxs-lookup"><span data-stu-id="5be77-153">Unreal's UMG tutorials</span></span>](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
