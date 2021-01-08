---
title: Esercitazioni di MRTK - 6. Creazione delle interfacce utente
description: In questo corso viene illustrato come usare Mixed Reality Toolkit (MRTK) per creare interfacce utente.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, prefab, ologrammi, descrizioni comandi
ms.localizationpriority: high
ms.openlocfilehash: 90b794dc6e88b724d16c339e428c4d2ed9cdac07
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613515"
---
# <a name="6-creating-user-interfaces"></a><span data-ttu-id="f8a10-105">6. Creazione delle interfacce utente</span><span class="sxs-lookup"><span data-stu-id="f8a10-105">6. Creating user interfaces</span></span>

## <a name="overview"></a><span data-ttu-id="f8a10-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="f8a10-106">Overview</span></span>

<span data-ttu-id="f8a10-107">In questa esercitazione apprenderai come creare un'interfaccia utente semplice usando i prefab di pulsanti e menu di MRTK insieme al componente TextMeshPro di Unity.</span><span class="sxs-lookup"><span data-stu-id="f8a10-107">In this tutorial, you will learn how to create a simple user interface using MRTK's button and menu prefabs alongside Unity's TextMeshPro component.</span></span> <span data-ttu-id="f8a10-108">Apprenderai anche come configurare i pulsanti per attivare gli eventi e aggiungere descrizioni comandi dinamiche come elementi dell'interfaccia utente per fornire all'utente informazioni aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="f8a10-108">You will also learn how to configure the buttons to trigger events and add dynamic tooltip UI elements to provide the user with additional information.</span></span>

## <a name="objectives"></a><span data-ttu-id="f8a10-109">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f8a10-109">Objectives</span></span>

* <span data-ttu-id="f8a10-110">Apprendere come organizzare i pulsanti in una raccolta</span><span class="sxs-lookup"><span data-stu-id="f8a10-110">Learn how to organize buttons in a collection</span></span>
* <span data-ttu-id="f8a10-111">Apprendere come usare i prefab di menu di MRTK</span><span class="sxs-lookup"><span data-stu-id="f8a10-111">Learn how to use MRTK's menu prefabs</span></span>
* <span data-ttu-id="f8a10-112">Apprendere come interagire con gli ologrammi usando menu e pulsanti dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="f8a10-112">Learn how to interact with holograms using UI menus and buttons</span></span>
* <span data-ttu-id="f8a10-113">Apprendere come aggiungere elementi di testo</span><span class="sxs-lookup"><span data-stu-id="f8a10-113">Learn how to add text elements</span></span>
* <span data-ttu-id="f8a10-114">Apprendere come generare le descrizioni comandi per gli oggetti in modo dinamico</span><span class="sxs-lookup"><span data-stu-id="f8a10-114">Learn how to spawn tooltips on objects dynamically</span></span>

## <a name="creating-a-static-panel-of-buttons"></a><span data-ttu-id="f8a10-115">Creazione di un pannello statico di pulsanti</span><span class="sxs-lookup"><span data-stu-id="f8a10-115">Creating a static panel of buttons</span></span>

<span data-ttu-id="f8a10-116">Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse sull'oggetto **RoverExplorer** e scegli **Create Empty** (Crea vuoto) per aggiungere un oggetto vuoto come figlio di RoverExplorer, quindi assegna all'oggetto il nome **Buttons** e configura il componente **Transform** (Trasformazione) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f8a10-116">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **Buttons**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="f8a10-117">**Position** (Posizione): X = -0.6, Y = 0.036, Z = -0.5</span><span class="sxs-lookup"><span data-stu-id="f8a10-117">**Position**: X = -0.6, Y = 0.036, Z = -0.5</span></span>
* <span data-ttu-id="f8a10-118">**Rotation** (Rotazione): X = 90, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="f8a10-118">**Rotation**: X = 90, Y = 0, Z = 0</span></span>
* <span data-ttu-id="f8a10-119">**Scale** (Scala): X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="f8a10-119">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity con l'oggetto Buttons appena creato selezionato e posizionato](images/mr-learning-base/base-06-section1-step1-1.png)

<span data-ttu-id="f8a10-121">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset)  > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Prefab), fai clic e trascina il prefab **PressableRoundButton** sull'oggetto **Buttons**, quindi fai clic con il pulsante destro del mouse su PressableRoundButton e scegli **Duplicate** (Duplica) per creare una copia. Ripeti queste operazioni fino a ottenere un totale di tre oggetti PressableRoundButton:</span><span class="sxs-lookup"><span data-stu-id="f8a10-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **PressableRoundButton** prefab on to the **Buttons** object, then right-click on the PressableRoundButton and select **Duplicate** to create a copy, repeat until you have a total of three PressableRoundButton objects:</span></span>

![Unity con i prefab PressableRoundButton appena aggiunti](images/mr-learning-base/base-06-section1-step1-2.png)

<span data-ttu-id="f8a10-123">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Buttons**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **GridObjectCollection** e configuralo come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f8a10-123">In the Hierarchy window, select the **Buttons** object, then in the Inspector window, use the **Add Component** button to add the **GridObjectCollection** component and configure it as follows:</span></span>

* <span data-ttu-id="f8a10-124">**Sort Type** (Tipo ordinamento): Child Order (Ordine elementi figlio)</span><span class="sxs-lookup"><span data-stu-id="f8a10-124">**Sort Type**: Child Order</span></span>
* <span data-ttu-id="f8a10-125">**Layout**: Orizzontale</span><span class="sxs-lookup"><span data-stu-id="f8a10-125">**Layout**: Horizontal</span></span>
* <span data-ttu-id="f8a10-126">**Cell Width** (Larghezza cella): 0.2</span><span class="sxs-lookup"><span data-stu-id="f8a10-126">**Cell Width**: 0.2</span></span>
* <span data-ttu-id="f8a10-127">**Anchor** (Ancoraggio): Middle Left (In mezzo a sinistra)</span><span class="sxs-lookup"><span data-stu-id="f8a10-127">**Anchor**: Middle Left</span></span>

<span data-ttu-id="f8a10-128">Fai quindi clic sul pulsante **Update Collection** (Aggiorna raccolta) per aggiornare la posizione degli oggetti figlio dell'oggetto Buttons:</span><span class="sxs-lookup"><span data-stu-id="f8a10-128">Then click the **Update Collection** button to update the position of the Buttons object's child objects:</span></span>

![Oggetto Buttons di Unity con il componente GridObjectCollection aggiunto, configurato e applicato](images/mr-learning-base/base-06-section1-step1-3.png)

<span data-ttu-id="f8a10-130">Nella finestra Hierarchy (Gerarchia) assegna ai pulsanti i nomi **Hints**, **Explode** e **Reset**.</span><span class="sxs-lookup"><span data-stu-id="f8a10-130">In the Hierarchy window, name the buttons **Hints**, **Explode**, and **Reset**.</span></span>

<span data-ttu-id="f8a10-131">Per ogni pulsante, seleziona l'oggetto figlio **SeeItSayItLabel** > **TextMeshPro**, quindi nella finestra Inspector (Controllo) modifica il rispettivo testo componente **TextMeshPro - Text** (TextMeshPro - Testo) in modo che corrisponda ai nomi dei pulsanti:</span><span class="sxs-lookup"><span data-stu-id="f8a10-131">For each button, select the **SeeItSayItLabel** > **TextMeshPro** child object, then in the Inspector window, change the respective **TextMeshPro - Text** component text to match the button names:</span></span>

![Unity con le etichette di testo dei pulsanti configurate](images/mr-learning-base/base-06-section1-step1-4.png)

<span data-ttu-id="f8a10-133">Al termine, comprimi gli oggetti figlio dell'oggetto Buttons.</span><span class="sxs-lookup"><span data-stu-id="f8a10-133">Once done, collapse the Buttons object's child objects.</span></span>

<span data-ttu-id="f8a10-134">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto pulsante **Hints**, quindi nella finestra Inspector (Controllo) configurare l'evento **Interactable.OnClick ()** come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f8a10-134">In the Hierarchy window, select the **Hints** button object, then in the Inspector window, configure the **Interactable.OnClick ()** event as follows:</span></span>

* <span data-ttu-id="f8a10-135">Assegna l'oggetto **RoverAssembly** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="f8a10-135">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="f8a10-136">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **PlacementHintsController** > **TogglePlacementHints ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="f8a10-136">From the **No Function** dropdown, select **PlacementHintsController** > **TogglePlacementHints ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con l'evento OnClick dell'oggetto pulsante Hints configurato](images/mr-learning-base/base-06-section1-step1-5.png)

> [!TIP]
> <span data-ttu-id="f8a10-138">Il componente Interactable è un contenitore all-in-one che consente a tutti gli oggetti di interagire con facilità e rispondere all'input.</span><span class="sxs-lookup"><span data-stu-id="f8a10-138">The Interactable component is an all-in-one container to make any object easily interactable and responsive to input.</span></span> <span data-ttu-id="f8a10-139">Interactable agisce come un catch-all per tutti i tipi di input, tra cui il tocco, i raggi della mano, il riconoscimento vocale e così via e incanala tali interazioni in eventi e risposte con temi visivi.</span><span class="sxs-lookup"><span data-stu-id="f8a10-139">Interactable acts as a catch-all for all types of input including touch, hand rays, speech, etc. and funnels these interactions into events and visual theme responses.</span></span> <span data-ttu-id="f8a10-140">Per informazioni su come configurarlo per diversi tipi di input e personalizzarne il tema visivo, è possibile fare riferimento all'argomento [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="f8a10-140">To learn how to configure it for different input types and customize it's visual theme, you can refer to the [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="f8a10-141">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto pulsante **Explode**, quindi nella finestra Inspector (Controllo) configurare l'evento **Interactable.OnClick ()** come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f8a10-141">In the Hierarchy window, select the **Explode** button object, then in the Inspector window, configure the **Interactable.OnClick ()** event as follows:</span></span>

* <span data-ttu-id="f8a10-142">Assegna l'oggetto **RoverAssembly** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="f8a10-142">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="f8a10-143">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **ExplodedViewController** > **ToggleExplodedView ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="f8a10-143">From the **No Function** dropdown, select **ExplodedViewController** > **ToggleExplodedView ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con l'evento OnClick dell'oggetto pulsante Explode configurato](images/mr-learning-base/base-06-section1-step1-6.png)

<span data-ttu-id="f8a10-145">Premi il pulsante Play (Riproduci) per attivare la modalità di gioco, quindi tieni premuto il pulsante della barra spaziatrice per attivare la mano e usa il mouse per premere il pulsante **Hints** per attivare/disattivare la visibilità degli oggetti relativi ai suggerimenti per il posizionamento:</span><span class="sxs-lookup"><span data-stu-id="f8a10-145">Press the Play button to enter Game mode, then press-and-hold the space bar button to activate the hand and use the mouse to press the **Hints** button to toggle the visibility of the placement hint objects:</span></span>

![Visualizzazione suddivisa della modalità di riproduzione in Unity con il pulsante Hints selezionato](images/mr-learning-base/base-06-section1-step1-7.png)

<span data-ttu-id="f8a10-147">e il pulsante **Explode** per attivare e disattivare la visualizzazione esplosa:</span><span class="sxs-lookup"><span data-stu-id="f8a10-147">and the **Explode** button to toggle the exploded view on and off:</span></span>

![Visualizzazione suddivisa della modalità di riproduzione in Unity con il pulsante Explode selezionato](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a><span data-ttu-id="f8a10-149">Creazione di un menu dinamico che segue l'utente</span><span class="sxs-lookup"><span data-stu-id="f8a10-149">Creating a dynamic menu that follows the user</span></span>

<span data-ttu-id="f8a10-150">Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset)  > **MRTK** > **SDK** > **Features** (Funzionalità)  > **UX** > **Prefabs** (Prefab)  > **Menus** (Menu), fare clic e trascinare il prefab **NearMenu4x1** nella finestra Hierarchy (Gerarchia), impostare il campo **Position** (Posizione) della trasformazione su X = 0, Y = -0.4, Z = 0 e configurare il prefab come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f8a10-150">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **Menus** folder, click-and-drag the **NearMenu4x1** prefab into the Hierarchy window, set its Transform **Position** to X = 0, Y = -0.4, Z = 0 and configure it as follows:</span></span>

* <span data-ttu-id="f8a10-151">Verifica che per **Tracked Target Type** (Tipo destinazione tracciata) del componente **SolverHandler** sia impostato il valore **Head** (Testa)</span><span class="sxs-lookup"><span data-stu-id="f8a10-151">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="f8a10-152">Seleziona la casella di controllo accanto al componente **RadialView** in modo che sia abilitato per impostazione predefinita</span><span class="sxs-lookup"><span data-stu-id="f8a10-152">Check the checkbox next to the **RadialView** Solver component so it is enabled by default</span></span>

![Unity con il prefab NearMenu appena aggiunto selezionato](images/mr-learning-base/base-06-section2-step1-1.png)

<span data-ttu-id="f8a10-154">Nella finestra Hierarchy (Gerarchia) rinomina l'oggetto come **Menu**, quindi espandi il relativo oggetto figlio **ButtonCollection** per visualizzare i quattro pulsanti:</span><span class="sxs-lookup"><span data-stu-id="f8a10-154">In the Hierarchy window, rename the object to **Menu**, then expand its **ButtonCollection** child object to reveal the four buttons:</span></span>

![Unity con l'oggetto Menu selezionato e l'oggetto ButtonCollection espanso](images/mr-learning-base/base-06-section2-step1-2.png)

<span data-ttu-id="f8a10-156">Rinomina il primo pulsante come **Indicator**, quindi nella finestra Inspector (Controllo) configura il componente **Button Config Helper (Script)** (Helper configurazione pulsanti - Script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f8a10-156">Rename the first button to **Indicator**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="f8a10-157">Modifica il contenuto di **Main Label Text** (Testo etichetta principale) in modo che corrisponda al nome del pulsante</span><span class="sxs-lookup"><span data-stu-id="f8a10-157">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="f8a10-158">Assegna l'oggetto **Indicator** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="f8a10-158">Assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="f8a10-159">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **GameObject** > **SetActive (bool)** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="f8a10-159">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="f8a10-160">Verifica che la casella di controllo dell'argomento sia **selezionata**</span><span class="sxs-lookup"><span data-stu-id="f8a10-160">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="f8a10-161">Imposta **Icon** (Icona) sull'icona di ricerca</span><span class="sxs-lookup"><span data-stu-id="f8a10-161">Change the **Icon** to the 'search' icon</span></span>

![Unity con il componente Button Config Helper dell'oggetto pulsante Indicator configurato](images/mr-learning-base/base-06-section2-step1-3.png)

<span data-ttu-id="f8a10-163">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **Indicator** (Indicatore), quindi nella finestra di controllo:</span><span class="sxs-lookup"><span data-stu-id="f8a10-163">In the Hierarchy window, select the **Indicator** object, then in the Inspector window:</span></span>

* <span data-ttu-id="f8a10-164">Deseleziona la casella di controllo accanto al nome per rendere inattivo il componente per impostazione predefinita</span><span class="sxs-lookup"><span data-stu-id="f8a10-164">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="f8a10-165">Usare il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Directional Indicator Controller (Script)** (Controller destinazione direzionale - Script)</span><span class="sxs-lookup"><span data-stu-id="f8a10-165">Use the **Add Component** button to add the **Directional Indicator Controller (Script)** component</span></span>

![Unity con l'oggetto Indicator selezionato e disabilitato e il componente DirectionalIndicatorController aggiunto](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="f8a10-167">A questo punto, all'avvio dell'app, l'indicatore è disabilitato per impostazione predefinita e può essere abilitato premendo il pulsante Indicator.</span><span class="sxs-lookup"><span data-stu-id="f8a10-167">Now, when the app starts, the Indicator is disabled by default and can be enabled by pressing the Indicator button.</span></span>

<span data-ttu-id="f8a10-168">Rinomina il secondo pulsante come **TapToPlace**, quindi nella finestra Inspector (Controllo) configura il componente **Button Config Helper (Script)** (Helper configurazione pulsanti - Script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f8a10-168">Rename the second button to **TapToPlace**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="f8a10-169">Modifica il contenuto di **Main Label Text** (Testo etichetta principale) in modo che corrisponda al nome del pulsante</span><span class="sxs-lookup"><span data-stu-id="f8a10-169">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="f8a10-170">Assegna l'oggetto RoverExplorer > **RoverAssembly** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="f8a10-170">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="f8a10-171">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **TapToPlace** > **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="f8a10-171">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="f8a10-172">Verifica che la casella di controllo dell'argomento sia **selezionata**</span><span class="sxs-lookup"><span data-stu-id="f8a10-172">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="f8a10-173">Imposta **Icon** (Icona) sull'icona della mano con raggio</span><span class="sxs-lookup"><span data-stu-id="f8a10-173">Change the **Icon** to the 'hand with ray' icon</span></span>

![Unity con il componente Button Config Helper dell'oggetto pulsante TapToPlace configurato](images/mr-learning-base/base-06-section2-step1-5.png)

<span data-ttu-id="f8a10-175">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **RoverAssembly**, quindi nella finestra Inspector (Controllo) configura il componente **Tap To Place (Script)** (Tocco per posizionamento - Script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f8a10-175">In the Hierarchy window, select the **RoverAssembly** object, then in the Inspector window, configure the **Tap To Place (Script)** component as follows:</span></span>

* <span data-ttu-id="f8a10-176">Deseleziona la casella di controllo accanto al nome per rendere inattivo il componente per impostazione predefinita</span><span class="sxs-lookup"><span data-stu-id="f8a10-176">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="f8a10-177">Nella sezione dell'evento **On Placing Stopped ()** (All'arresto del posizionamento) fare clic sull'icona **+** per aggiungere un nuovo evento:</span><span class="sxs-lookup"><span data-stu-id="f8a10-177">In the **On Placing Stopped ()** event section, click the **+** icon to add a new event:</span></span>
* <span data-ttu-id="f8a10-178">Assegna l'oggetto RoverExplorer > **RoverAssembly** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="f8a10-178">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="f8a10-179">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **TapToPlace** > **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="f8a10-179">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="f8a10-180">Verifica che la casella di controllo dell'argomento sia **deselezionata**</span><span class="sxs-lookup"><span data-stu-id="f8a10-180">Verify that the argument checkbox is **unchecked**</span></span>

![Unity con il componente TapToPlace riconfigurato](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> <span data-ttu-id="f8a10-182">A questo punto, all'avvio dell'app, la funzionalità di tocco per posizionamento è disabilitata per impostazione predefinita e può essere abilitata premendo il pulsante TaptoPlace.</span><span class="sxs-lookup"><span data-stu-id="f8a10-182">Now, when the app starts, the Tap to Place functionality is disabled by default and can be enabled by pressing the Tap to Place button.</span></span> <span data-ttu-id="f8a10-183">Inoltre, quando il tocco per posizionamento viene completato, si disabilita automaticamente.</span><span class="sxs-lookup"><span data-stu-id="f8a10-183">Additionally, when the tap to place is completed, it will disable itself.</span></span>

## <a name="adding-text-to-the-scene"></a><span data-ttu-id="f8a10-184">Aggiunta di testo alla scena</span><span class="sxs-lookup"><span data-stu-id="f8a10-184">Adding text to the scene</span></span>

<span data-ttu-id="f8a10-185">Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse sull'oggetto **Table** (Tabella) e scegli **3D Object** (Oggetto 3D)  > **Text - TextMeshPro** (Testo - TextMeshPro) per aggiungere un oggetto di testo come figlio dell'oggetto Table (Tabella), quindi nella finestra Inspector (Controllo) configura il componente **Rect Transform** (Trasformazione rettangolare) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f8a10-185">In the Hierarchy window, right-click on the **Table** object and select **3D Object** > **Text - TextMeshPro** to add a text object as a child of the Table object, then in the Inspector window, configure the **Rect Transform** component as follows:</span></span>

* <span data-ttu-id="f8a10-186">Imposta **Pos Y** (Posizione Y) su 1</span><span class="sxs-lookup"><span data-stu-id="f8a10-186">Change **Pos Y** to 1</span></span>
* <span data-ttu-id="f8a10-187">Imposta **Width** (Larghezza) su 1</span><span class="sxs-lookup"><span data-stu-id="f8a10-187">Change **Width** to 1</span></span>
* <span data-ttu-id="f8a10-188">Imposta **Height** (Altezza) su 1</span><span class="sxs-lookup"><span data-stu-id="f8a10-188">Change **Height** to 1</span></span>
* <span data-ttu-id="f8a10-189">Imposta **Rotation X** (Rotazione X) su 90</span><span class="sxs-lookup"><span data-stu-id="f8a10-189">Change **Rotation X** to 90</span></span>

![Unity con l'oggetto TextMeshPro appena creato selezionato](images/mr-learning-base/base-06-section3-step1-1.png)

<span data-ttu-id="f8a10-191">Quindi configura il componente **TextMeshPro - Text** (TextMeshPro - Testo) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f8a10-191">Then configure the **TextMeshPro - Text** component as follows::</span></span>

* <span data-ttu-id="f8a10-192">Imposta **Text** (Testo) su Rover Explorer</span><span class="sxs-lookup"><span data-stu-id="f8a10-192">Change **Text** to Rover Explorer</span></span>
* <span data-ttu-id="f8a10-193">Imposta **Font Style** (Stile carattere) su Bold (Grassetto)</span><span class="sxs-lookup"><span data-stu-id="f8a10-193">Change **Font Style** to Bold</span></span>
* <span data-ttu-id="f8a10-194">Imposta **Font Size** (Dimensione carattere) su 1</span><span class="sxs-lookup"><span data-stu-id="f8a10-194">Change **Font Size** to 1</span></span>
* <span data-ttu-id="f8a10-195">Imposta Extra Settings (Impostazioni aggiuntive) > **Margins** (Margini) su 0.03</span><span class="sxs-lookup"><span data-stu-id="f8a10-195">Change Extra Settings > **Margins** to 0.03</span></span>

![Unity con il componente TextMeshPro configurato](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a><span data-ttu-id="f8a10-197">Aggiunta di descrizioni comandi</span><span class="sxs-lookup"><span data-stu-id="f8a10-197">Adding tooltips</span></span>

<span data-ttu-id="f8a10-198">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset)  > **MRTK** > **SDK** > **Features** (Funzionalità)  > **UX** > **Prefabs** (Prefab)  > **ToolTip** (Descrizione comando) per individuare i prefab relativi alle descrizioni comandi:</span><span class="sxs-lookup"><span data-stu-id="f8a10-198">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![Finestra Project di Unity con la cartella ToolTips selezionata](images/mr-learning-base/base-06-section4-step1-1.png)

<span data-ttu-id="f8a10-200">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto RoverExplorer > **RoverParts** e seleziona tutti i relativi oggetti parte rover figlio, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **ToolTipSpawner** e configuralo come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f8a10-200">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects, then in the Inspector window, use the **Add Component** button to add the **ToolTipSpawner** component and configure it as follows:</span></span>

* <span data-ttu-id="f8a10-201">Verifica che la casella di controllo **Focus Enabled** (Stato attivo abilitato) sia selezionata per richiedere all'utente di guardare la parte per visualizzare la descrizione comando</span><span class="sxs-lookup"><span data-stu-id="f8a10-201">Ensure the **Focus Enabled** checkbox is checked to require the user to look at the part for the tooltip to appear</span></span>
* <span data-ttu-id="f8a10-202">Assegna il prefab **Simple Line ToolTip** (Descrizione comando linee semplice) dalla finestra Project (Progetto) al campo **Tool Tip Prefab** (Prefab descrizione comando)</span><span class="sxs-lookup"><span data-stu-id="f8a10-202">Assign the **Simple Line ToolTip** prefab from the Project window to the **Tool Tip Prefab** field</span></span>
* <span data-ttu-id="f8a10-203">Imposta ToolTip Override Settings (Impostazioni di override descrizione comando) > **Settings Mode** (Modalità impostazioni) su **Override**</span><span class="sxs-lookup"><span data-stu-id="f8a10-203">Change the ToolTip Override Settings > **Settings Mode** to **Override**</span></span>
* <span data-ttu-id="f8a10-204">Imposta ToolTip Override Settings (Impostazioni di override descrizione comando) > **Manual Pivot Local Position Y** (Posizione Y locale pivot manuale) su **1.5**</span><span class="sxs-lookup"><span data-stu-id="f8a10-204">Change the ToolTip Override Settings > **Manual Pivot Local Position Y** to **1.5**</span></span>

![Unity con tutti gli oggetti parte rover selezionati e il componente ToolTipSpawner aggiunto e configurato](images/mr-learning-base/base-06-section4-step1-2.png)

<span data-ttu-id="f8a10-206">Nella finestra Hierarchy (Gerarchia) seleziona la prima parte rover, RoverParts > **Camera_Part**, e configura il componente **ToolTipSpawner** come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f8a10-206">In the Hierarchy window, select the first rover part, RoverParts > **Camera_Part**, and configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="f8a10-207">Modifica **Tool Tip Text** (Testo descrizione comando) in modo che rifletta il nome della parte, ovvero **Camera**</span><span class="sxs-lookup"><span data-stu-id="f8a10-207">Change **Tool Tip Text** to reflect the name of the part, i.e., **Camera**</span></span>

![Unity con l'opzione Tool Tip Text della fotocamera configurata](images/mr-learning-base/base-06-section4-step1-3.png)

<span data-ttu-id="f8a10-209">**Ripeti** questo passaggio per ogni oggetto parte rover per configurare il componente **ToolTipSpawner** come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f8a10-209">**Repeat** this step for each of the rover part objects to configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="f8a10-210">Per **Generator_Part**, imposta **Tool Tip Text** (Testo descrizione comando) su **Generator**</span><span class="sxs-lookup"><span data-stu-id="f8a10-210">For the **Generator_Part**, change the **Tool Tip Text** to **Generator**</span></span>
* <span data-ttu-id="f8a10-211">Per **Lights_Part**, imposta **Tool Tip Text** (Testo descrizione comando) su **Lights**</span><span class="sxs-lookup"><span data-stu-id="f8a10-211">For the **Lights_Part**, change the **Tool Tip Text** to **Lights**</span></span>
* <span data-ttu-id="f8a10-212">Per **UHFAntenna_Part**, imposta **Tool Tip Text** (Testo descrizione comando) su **UHF Antenna**</span><span class="sxs-lookup"><span data-stu-id="f8a10-212">For the **UHFAntenna_Part**, change the **Tool Tip Text** to **UHF Antenna** field</span></span>
* <span data-ttu-id="f8a10-213">Per **Spectrometer_Part**, imposta **Tool Tip Text** (Testo descrizione comando) su **Spectrometer**</span><span class="sxs-lookup"><span data-stu-id="f8a10-213">For the **Spectrometer_Part**, change the **Tool Tip Text** to **Spectrometer**</span></span>

<span data-ttu-id="f8a10-214">Seleziona il pulsante Play (Riproduci) per attivare la modalità di gioco, quindi tieni premuto il pulsante destro del mouse mentre muovi il mouse finché lo sguardo non incontra una delle parti. Verrà così visualizzata la descrizione comando relativa a tale parte:</span><span class="sxs-lookup"><span data-stu-id="f8a10-214">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the parts and the tooltip for that part will be displayed:</span></span>

![Visualizzazione suddivisa della modalità di riproduzione in Unity con descrizione comando attivata dallo sguardo fisso](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="f8a10-216">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="f8a10-216">Congratulations</span></span>

<span data-ttu-id="f8a10-217">In questa esercitazione hai appreso come creare un'interfaccia utente semplice usando i prefab per pulsanti e menu forniti da MRTK insieme al componente TextMeshPro di Unity e come configurare i pulsanti per attivare eventi quando vengono premuti.</span><span class="sxs-lookup"><span data-stu-id="f8a10-217">In this tutorial, you learned how to create a simple user interface using MRTK's provided button and menu prefabs alongside Unity's TextMeshPro component and how to configure the buttons to trigger events when they are pressed.</span></span> <span data-ttu-id="f8a10-218">Hai inoltre appreso come aggiungere elementi descrizione comando dinamici per l'interfaccia utente per fornire all'utente informazioni aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="f8a10-218">You also learned how to add dynamic tooltip UI elements to provide the user with additional information.</span></span>

[<span data-ttu-id="f8a10-219">Esercitazione successiva: 7. Interazione con oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="f8a10-219">Next Tutorial: 7. Interacting with 3D objects</span></span>](mr-learning-base-07.md)