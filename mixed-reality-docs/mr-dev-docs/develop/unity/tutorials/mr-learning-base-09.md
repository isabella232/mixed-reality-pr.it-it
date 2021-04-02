---
title: Uso dei comandi vocali
description: Questa esercitazione illustra come configurare, creare e usare i comandi vocali nelle app di realtà mista con Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, comandi vocali, input vocale
ms.localizationpriority: high
ms.openlocfilehash: 3aea23d5a259e555f47ca9ea41d77f345c977aeb
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982939"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="0e1c3-104">9. Uso dei comandi vocali</span><span class="sxs-lookup"><span data-stu-id="0e1c3-104">9. Using speech commands</span></span>

<span data-ttu-id="0e1c3-105">In questa esercitazione verrà spiegato come creare comandi vocali e come controllarli a livello globale.</span><span class="sxs-lookup"><span data-stu-id="0e1c3-105">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="0e1c3-106">Si imparerà anche a controllare i comandi vocali locali che richiedono che l'utente guardi l'oggetto che controlla il comando vocale.</span><span class="sxs-lookup"><span data-stu-id="0e1c3-106">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="0e1c3-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="0e1c3-107">Objectives</span></span>

* <span data-ttu-id="0e1c3-108">Imparare a creare comandi vocali</span><span class="sxs-lookup"><span data-stu-id="0e1c3-108">Learn how to create speech commands</span></span>
* <span data-ttu-id="0e1c3-109">Imparare a controllare i comandi vocali a livello globale e locale</span><span class="sxs-lookup"><span data-stu-id="0e1c3-109">Learn how to control speech commands globally and locally</span></span>

[!INCLUDE[](includes/ensuring-microphone-capabality.md)]

## <a name="creating-speech-commands"></a><span data-ttu-id="0e1c3-110">Creazione di comandi vocali</span><span class="sxs-lookup"><span data-stu-id="0e1c3-110">Creating speech commands</span></span>

<span data-ttu-id="0e1c3-111">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda MixedRealityToolkit > **Input** e seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="0e1c3-111">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="0e1c3-112">Espandere la **Speech** (Voce)</span><span class="sxs-lookup"><span data-stu-id="0e1c3-112">Expand the **Speech** section</span></span>
* <span data-ttu-id="0e1c3-113">Clonare il profilo **DefaultMixedRealitySpeechCommandsProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_MixedRealitySpeechCommandsProfile_</span><span class="sxs-lookup"><span data-stu-id="0e1c3-113">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="0e1c3-114">Verificare che **Start Behaviour** (Comportamento di avvio) sia impostato su **Auto Start** (Avvio automatico)</span><span class="sxs-lookup"><span data-stu-id="0e1c3-114">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![Creazione di comandi vocali](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="0e1c3-116">Per rivedere la procedura di clonazione dei profili MRTK, fare riferimento alle istruzioni contenute in [Configurazione dei profili di Mixed Reality Toolkit](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="0e1c3-116">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="0e1c3-117">Nella sezione **Speech Commands** (Comandi vocali) fare clic sul pulsante **+ Add a New Speech Command** (+ Aggiungi un nuovo comando vocale) per aggiungere quattro nuovi comandi vocali all'elenco dei comandi vocali esistenti e quindi nei campi **Keyword** (Parola chiave) immettere quanto segue:</span><span class="sxs-lookup"><span data-stu-id="0e1c3-117">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="0e1c3-118">Abilita indicatore</span><span class="sxs-lookup"><span data-stu-id="0e1c3-118">Enable Indicator</span></span>
* <span data-ttu-id="0e1c3-119">Abilita tocco per posizionare</span><span class="sxs-lookup"><span data-stu-id="0e1c3-119">Enable Tap to Place</span></span>
* <span data-ttu-id="0e1c3-120">Abilita controllo limiti</span><span class="sxs-lookup"><span data-stu-id="0e1c3-120">Enable Bounds Control</span></span>
* <span data-ttu-id="0e1c3-121">Disabilitare il controllo dei limiti</span><span class="sxs-lookup"><span data-stu-id="0e1c3-121">Disable Bounds Control</span></span>

![Aggiunta di nuovi comandi vocali](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="0e1c3-123">Se il computer non dispone di un microfono, è possibile assegnare un KeyCode ai comandi vocali, che consente di attivarli quando viene premuto il tasto corrispondente.</span><span class="sxs-lookup"><span data-stu-id="0e1c3-123">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="0e1c3-124">Controllo dei comandi vocali</span><span class="sxs-lookup"><span data-stu-id="0e1c3-124">Controlling speech commands</span></span>

<span data-ttu-id="0e1c3-125">Nella finestra del progetto passare alla cartella **Package**  >  **mixed reality Toolkit Foundation**  >  **SDK**  >  **features**  >    >    >   per individuare le prefabbricate ToolTip:</span><span class="sxs-lookup"><span data-stu-id="0e1c3-125">In the Project window, navigate to the **Package** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![Apertura della cartella delle descrizioni comando](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="0e1c3-127">Nella finestra Hierarchy (Gerarchia) fare clic con il pulsante destro del mouse su un'area vuota e scegliere **Create Empty** (Crea vuoto) per aggiungere un oggetto vuoto alla scena.</span><span class="sxs-lookup"><span data-stu-id="0e1c3-127">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="0e1c3-128">Denominare l'oggetto **SpeechInputHandler_Global**, quindi nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **SpeechInputHandler** e configurarlo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="0e1c3-128">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="0e1c3-129">**Deselezionare** la casella di controllo **Is Focus Required** (È necessario lo stato attivo) in modo che l'utente non debba guardare l'oggetto con il componente SpeechInputHandler per attivare il comando vocale</span><span class="sxs-lookup"><span data-stu-id="0e1c3-129">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="0e1c3-130">Dalla finestra Project (Progetto) assegnare il prefeb **SpeechConfirmation Tooltip** al campo **Speech Confirmation Tooltip Prefab**, in modo che venga visualizzato questo prefab quando viene riconosciuto un comando vocale</span><span class="sxs-lookup"><span data-stu-id="0e1c3-130">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Configurazione del componente di gestione dell'input vocale](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="0e1c3-132">Nel componente SpeechInputHandler component fare clic tre volte sulla piccola icona **+** per aggiungere tre elementi di parola chiave:</span><span class="sxs-lookup"><span data-stu-id="0e1c3-132">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![Aggiunta di elementi parola chiave al gestore di input vocale](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="0e1c3-134">Espandere **Element 0** e configurarlo come segue:</span><span class="sxs-lookup"><span data-stu-id="0e1c3-134">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="0e1c3-135">Nel campo **Keyword** (Parola chiave) immettere **Abilita indicatore** per fare riferimento al comando vocale Abilita indicatore creato nella sezione precedente</span><span class="sxs-lookup"><span data-stu-id="0e1c3-135">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="0e1c3-136">Fare clic sulla piccola icona **+** per aggiungere un evento</span><span class="sxs-lookup"><span data-stu-id="0e1c3-136">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="0e1c3-137">Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto **Indicator** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="0e1c3-137">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="0e1c3-138">Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare **GameObject** > **SetActive (bool)** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="0e1c3-138">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="0e1c3-139">Assicurarsi che la casella di controllo dell'argomento sia **selezionata**</span><span class="sxs-lookup"><span data-stu-id="0e1c3-139">Check the argument checkbox, so it is **checked**</span></span>

![Configurare l'elemento parola chiave 0](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="0e1c3-141">Espandere **Element 1** e configurarlo come segue:</span><span class="sxs-lookup"><span data-stu-id="0e1c3-141">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="0e1c3-142">Nel campo della **parola chiave** immettere **Enable Bounds Control** per fare riferimento al comando Enable Bounds Control creato nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="0e1c3-142">In the **Keyword** field, enter **Enable Bounds Control**, to reference the Enable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="0e1c3-143">Fare clic sulla piccola icona **+** per aggiungere un evento</span><span class="sxs-lookup"><span data-stu-id="0e1c3-143">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="0e1c3-144">Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="0e1c3-144">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="0e1c3-145">Nell'elenco a discesa **Nessuna funzione** selezionare **BoundsControl**  >  **bool Enabled** per aggiornare il valore della proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="0e1c3-145">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="0e1c3-146">Assicurarsi che la casella di controllo dell'argomento sia **selezionata**</span><span class="sxs-lookup"><span data-stu-id="0e1c3-146">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="0e1c3-147">Fai clic sulla piccola icona **+** per aggiungere un altro evento</span><span class="sxs-lookup"><span data-stu-id="0e1c3-147">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="0e1c3-148">Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="0e1c3-148">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="0e1c3-149">Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare **ObjectManipulator** > **bool enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="0e1c3-149">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="0e1c3-150">Assicurarsi che la casella di controllo dell'argomento sia **selezionata**</span><span class="sxs-lookup"><span data-stu-id="0e1c3-150">Check the argument checkbox, so it is **checked**</span></span>

![Configurare l'elemento parola chiave 1](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="0e1c3-152">Espandere **Element 2** e configurarlo come segue:</span><span class="sxs-lookup"><span data-stu-id="0e1c3-152">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="0e1c3-153">Nel campo **parola chiave** immettere **Disable Bounds Control** per fare riferimento al comando Disable Bounds Control creato nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="0e1c3-153">In the **Keyword** field, enter **Disable Bounds Control**, to reference the Disable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="0e1c3-154">Fare clic sulla piccola icona **+** per aggiungere un evento</span><span class="sxs-lookup"><span data-stu-id="0e1c3-154">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="0e1c3-155">Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="0e1c3-155">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="0e1c3-156">Nell'elenco a discesa **Nessuna funzione** selezionare **BoundsControl**  >  **bool Enabled** per aggiornare il valore della proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="0e1c3-156">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="0e1c3-157">Verificare che la casella di controllo dell'argomento sia **deselezionata**</span><span class="sxs-lookup"><span data-stu-id="0e1c3-157">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="0e1c3-158">Fai clic sulla piccola icona **+** per aggiungere un altro evento</span><span class="sxs-lookup"><span data-stu-id="0e1c3-158">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="0e1c3-159">Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="0e1c3-159">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="0e1c3-160">Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare **ObjectManipulator** > **bool enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="0e1c3-160">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="0e1c3-161">Verificare che la casella di controllo dell'argomento sia **deselezionata**</span><span class="sxs-lookup"><span data-stu-id="0e1c3-161">Verify that the argument checkbox is **unchecked**</span></span>

![Configurare l'elemento parola chiave 2](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="0e1c3-163">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto RoverExplorer > **RoverAssembly** e quindi nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **SpeechInputHandler** e configuralo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="0e1c3-163">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="0e1c3-164">Verificare che la casella di controllo **Is Focus Required** (È necessario lo stato attivo) sia **selezionata**, in modo che l'utente debba guardare l'oggetto con il componente SpeechInputHandler, ovvero RoverAssembly, per attivare il comando vocale</span><span class="sxs-lookup"><span data-stu-id="0e1c3-164">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="0e1c3-165">Dalla finestra Project (Progetto) assegnare il prefeb **SpeechConfirmation Tooltip** al campo **Speech Confirmation Tooltip Prefab**, in modo che venga visualizzato questo prefab quando viene riconosciuto un comando vocale</span><span class="sxs-lookup"><span data-stu-id="0e1c3-165">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Aggiungere un gestore di input vocale all'assembly Rover](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="0e1c3-167">Nel componente SpeechInputHandler fare clic sulla piccola icona **+** per aggiungere un elemento parola chiave, espandere l'elemento appena creato, quindi configurarlo come segue:</span><span class="sxs-lookup"><span data-stu-id="0e1c3-167">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="0e1c3-168">Nel campo **Keyword** (Parola chiave) immettere **Abilita tocco per posizionare** per fare riferimento al comando vocale Abilita tocco per posizionare creato nella sezione precedente</span><span class="sxs-lookup"><span data-stu-id="0e1c3-168">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="0e1c3-169">Fare clic sulla piccola icona **+** per aggiungere un evento</span><span class="sxs-lookup"><span data-stu-id="0e1c3-169">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="0e1c3-170">Nella finestra Hierarchy (Gerarchia) assegnare l'oggetto stesso, ovvero lo stesso oggetto **RoverAssembly**, al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="0e1c3-170">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="0e1c3-171">Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare **TapToPlace** > **bool enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="0e1c3-171">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="0e1c3-172">Assicurarsi che la casella di controllo dell'argomento sia **selezionata**</span><span class="sxs-lookup"><span data-stu-id="0e1c3-172">Check the argument checkbox, so it is **checked**</span></span>

![Configurare il gestore di input vocale nell'assembly Rover](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="0e1c3-174">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="0e1c3-174">Congratulations</span></span>

<span data-ttu-id="0e1c3-175">In questa esercitazione è stato spiegato come creare comandi vocali e come controllarli a livello globale.</span><span class="sxs-lookup"><span data-stu-id="0e1c3-175">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="0e1c3-176">Si è anche imparato a controllare i comandi vocali locali che richiedono che l'utente guardi l'oggetto che controlla il comando vocale.</span><span class="sxs-lookup"><span data-stu-id="0e1c3-176">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="0e1c3-177">A questo punto si conclude la serie [Esercitazioni introduttive](mr-learning-base-01.md).</span><span class="sxs-lookup"><span data-stu-id="0e1c3-177">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="0e1c3-178">In queste esercitazioni è stata creata da zero un'esperienza di realtà mista completa tramite MRTK.</span><span class="sxs-lookup"><span data-stu-id="0e1c3-178">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="0e1c3-179">Nelle prossime due serie di esercitazioni, [Esercitazioni su Ancoraggi nello spazio di Azure](mr-learning-asa-01.md) e [Esercitazioni sulle funzionalità multiutente](mr-learning-sharing-01.md), verrà spiegato prima di tutto come integrare Ancoraggi nello spazio di Azure in un progetto per ancorare l'esperienza Rover Explorer creata nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="0e1c3-179">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="0e1c3-180">Quindi, verrà illustrato come aggiungere funzionalità multiutente al progetto per condividere i movimenti di utenti e oggetti in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="0e1c3-180">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="0e1c3-181">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="0e1c3-181">Next Development Checkpoint</span></span>

<span data-ttu-id="0e1c3-182">Se si sta seguendo il percorso di checkpoint per lo sviluppo con Unity che abbiamo delineato, il passaggio successivo consiste nell'acquisire familiarità con i blocchi predefiniti fondamentali delle app di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="0e1c3-182">If you're following the Unity development checkpoint journey we've laid out, your next task is to familiarize yourself with core building blocks of Mixed Reality apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e1c3-183">Interazioni di base</span><span class="sxs-lookup"><span data-stu-id="0e1c3-183">Basic interactions</span></span>](../../../out-of-scope/mrtk-101.md)

<span data-ttu-id="0e1c3-184">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](../unity-development-overview.md#1-getting-started) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="0e1c3-184">You can always go back to the [Unity development checkpoints](../unity-development-overview.md#1-getting-started) at any time.</span></span>