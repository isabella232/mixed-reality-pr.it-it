---
title: Uso del tracciamento oculare
description: Questa esercitazione illustra come usare il tracciamento oculare nelle app di realtà mista con Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, tracciamento oculare
ms.localizationpriority: high
ms.openlocfilehash: f464ba4e08f1446f1d50eda577aedf9d070630ee
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007891"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="1e86c-104">8. Uso del tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="1e86c-104">8. Using eye-tracking</span></span>

<span data-ttu-id="1e86c-105">In questa esercitazione si apprenderà come abilitare il tracciamento oculare per HoloLens 2 e aggiungere questa funzionalità agli oggetti, in modo da attivare le azioni quando l'utente rivolge loro lo sguardo.</span><span class="sxs-lookup"><span data-stu-id="1e86c-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="1e86c-106">Se si distribuisce questo progetto anche in HoloLens (prima generazione), tenere presente che il tracciamento oculare è supportato solo in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1e86c-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="1e86c-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="1e86c-107">Objectives</span></span>

* <span data-ttu-id="1e86c-108">Imparare ad abilitare il tracciamento oculare per HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1e86c-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="1e86c-109">Imparare a usare il tracciamento oculare per attivare un'azione</span><span class="sxs-lookup"><span data-stu-id="1e86c-109">Learn how to use eye-tracking to trigger action</span></span>

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="1e86c-110">Verifica dell'abilitazione della funzionalità di input mediante sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="1e86c-110">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="1e86c-111">Nel menu di Unity selezionare Mixed Reality Toolkit > Utilities > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) e quindi, nella sezione **UWP Capabilities** (Funzionalità UWP), verificare che l'opzione **Enable Eye Gaze Input Capability** (Abilita la funzionalità di input mediante sguardo fisso) sia disattivata:</span><span class="sxs-lookup"><span data-stu-id="1e86c-111">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Finestra MRTK Project Configurator di Unity](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="1e86c-113">La funzionalità di input mediante sguardo fisso dovrebbe essere stata abilitata durante la configurazione delle istruzioni riportate in [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#selecting-mrtk-and-project-settings) (Applicare le impostazioni del Configuratore del progetto MRTK) quando è stato configurato il progetto Unity all'inizio di questa serie di esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="1e86c-113">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#selecting-mrtk-and-project-settings) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="1e86c-114">Se, tuttavia, non è abilitata, assicurarsi di farlo ora.</span><span class="sxs-lookup"><span data-stu-id="1e86c-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="1e86c-115">Abilitazione dello sguardo fisso nel provider di dati per lo sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="1e86c-115">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="1e86c-116">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda MixedRealityToolkit > **Input** e seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="1e86c-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="1e86c-117">Clonare il profilo **DefaultHoloLens2InputSystemProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_HoloLens2InputSystemProfile_</span><span class="sxs-lookup"><span data-stu-id="1e86c-117">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="1e86c-118">Espandere la sezione **Pointers** (Puntatori)</span><span class="sxs-lookup"><span data-stu-id="1e86c-118">Expand the **Pointers** section</span></span>
* <span data-ttu-id="1e86c-119">Clonare il profilo **DefaultMixedRealityPointerProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_MixedRealityPointerProfile_</span><span class="sxs-lookup"><span data-stu-id="1e86c-119">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="1e86c-120">Individuare la sezione **Gaze Settings** (Impostazioni sguardo) e selezionare la casella di controllo **Is Eye Tracking Enabled** (Tracciamento oculare abilitato)</span><span class="sxs-lookup"><span data-stu-id="1e86c-120">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![Componente MixedRealityToolkit di Unity con i profili appena creati applicati e il tracciamento oculare abilitato](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="1e86c-122">Per rivedere la procedura di clonazione dei profili di MRTK, fare riferimento alle istruzioni riportate in [Configurazione dei profili di Mixed Reality Toolkit](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="1e86c-122">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="1e86c-123">Abilitazione del tracciamento oculare simulato per l'editor di Unity</span><span class="sxs-lookup"><span data-stu-id="1e86c-123">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="1e86c-124">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit**, nella finestra Inspector (Controllo) passare alla scheda **Input** e quindi:</span><span class="sxs-lookup"><span data-stu-id="1e86c-124">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="1e86c-125">Espandere la sezione **Input Data Providers** > **Input Simulation Service** (Provider di dati di input > Servizio di simulazione input)</span><span class="sxs-lookup"><span data-stu-id="1e86c-125">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="1e86c-126">Clonare il profilo **DefaultMixedRealityInputSimulationProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_MixedRealityInputSimulationProfile_</span><span class="sxs-lookup"><span data-stu-id="1e86c-126">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="1e86c-127">Individuare la sezione **Eye Simulation** (Simulazione oculare) e selezionare la casella di controllo **Simulate Eye Position** (Simula posizione oculare)</span><span class="sxs-lookup"><span data-stu-id="1e86c-127">Locate the **Eye Simulation** section and check the **Simulate Eye Position** checkbox</span></span>

![Componente MixedRealityToolkit di Unity con il profilo appena creato applicato e la simulazione oculare abilitata](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="1e86c-129">Aggiunta del tracciamento oculare agli oggetti</span><span class="sxs-lookup"><span data-stu-id="1e86c-129">Adding eye-tracking to objects</span></span>

<span data-ttu-id="1e86c-130">Nella finestra Hierarchy (Gerarchia) espandere l'oggetto RoverExplorer > **Buttons** (Pulsanti) e quindi, per ognuno dei tre oggetti pulsante figlio, espandere e selezionare l'oggetto SeeItSayItLabel > **TextMeshPro**:</span><span class="sxs-lookup"><span data-stu-id="1e86c-130">In the Hierarchy window, expand the RoverExplorer > **Buttons** object, then for each of the three child button objects, expand and select the SeeItSayItLabel > **TextMeshPro** object:</span></span>

![Unity con l'oggetto TextMeshPro selezionato](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="1e86c-132">Con i tre oggetti TextMeshPro ancora selezionati, nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente) per aggiungere i componenti seguenti a tutti gli oggetti selezionati:</span><span class="sxs-lookup"><span data-stu-id="1e86c-132">With the three TextMeshPro objects still selected, in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="1e86c-133">Componente **Box Collider** (Collisore cubico)</span><span class="sxs-lookup"><span data-stu-id="1e86c-133">**Box Collider** component</span></span>
* <span data-ttu-id="1e86c-134">Componente **EyeTrackingTarget**</span><span class="sxs-lookup"><span data-stu-id="1e86c-134">**EyeTrackingTarget** component</span></span>

![Unity con l'oggetto TextMeshPro selezionato e componenti aggiunti](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="1e86c-136">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **Hints** (Suggerimenti) > SeeItSayItLabel > **TextMeshPro** e quindi configurare il componente **EyeTrackingTarget** come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="1e86c-136">In the Hierarchy window, select the **Hints** > SeeItSayItLabel > **TextMeshPro** object, then configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="1e86c-137">Nella sezione dell'evento **On Look At Start ()** (Quando viene rivolto lo sguardo all'inizio)</span><span class="sxs-lookup"><span data-stu-id="1e86c-137">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="1e86c-138">Fare clic sull'icona **+** piccola per aggiungere un altro evento</span><span class="sxs-lookup"><span data-stu-id="1e86c-138">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="1e86c-139">Assegnare l'oggetto, ad esempio lo stesso oggetto **TextMeshPro**, al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="1e86c-139">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="1e86c-140">Dall'elenco a discesa **No Function** (Nessuna funzione) selezionare **TextMeshPro** > **float fontSize** (fontSize mobile) per aggiornare il valore della proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="1e86c-140">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="1e86c-141">Impostare l'argomento su **0,06** per aumentare del 50% le dimensioni correnti del carattere 0,04</span><span class="sxs-lookup"><span data-stu-id="1e86c-141">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="1e86c-142">Nella sezione dell'evento **On Look Away ()** (Quando viene distolto lo sguardo)</span><span class="sxs-lookup"><span data-stu-id="1e86c-142">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="1e86c-143">Fare clic sull'icona **+** piccola per aggiungere un altro evento</span><span class="sxs-lookup"><span data-stu-id="1e86c-143">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="1e86c-144">Assegnare l'oggetto, ad esempio lo stesso oggetto **TextMeshPro**, al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="1e86c-144">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="1e86c-145">Dall'elenco a discesa **No Function** (Nessuna funzione) selezionare **TextMeshPro** > **float fontSize** (fontSize mobile) per aggiornare il valore della proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="1e86c-145">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="1e86c-146">Impostare l'argomento su **0,04** per ripristinare le dimensioni del carattere a 0,04</span><span class="sxs-lookup"><span data-stu-id="1e86c-146">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![Unity con l'oggetto TextMeshPro di Hints selezionato e il componente EyeTrackingTarget configurato](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="1e86c-148">**Ripetere** questo passaggio per l'oggetto **Explode** (Espandi) > SeeItSayItLabel > **TextMeshPro** e l'oggetto **Reset** (Ripristina) > SeeItSayItLabel > **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="1e86c-148">**Repeat** this step for the **Explode** > SeeItSayItLabel > **TextMeshPro** object and the **Reset** > SeeItSayItLabel > **TextMeshPro** object.</span></span>

<span data-ttu-id="1e86c-149">Se si immette la modalità di gioco e quindi si tiene premuto il pulsante destro del mouse mentre si sposta il puntatore del mouse fino a quando lo sguardo fisso raggiunge una delle etichette, si noterà che le dimensioni del carattere aumentano del 50% e vengono ripristinate le dimensioni originali quando si distoglie lo sguardo:</span><span class="sxs-lookup"><span data-stu-id="1e86c-149">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the labels, you will see the font size increase by 50% and reset back to its original size when looking away:</span></span>

![Doppia visualizzazione della modalità Play di Unity con lo sguardo che incontra l'obiettivo del tracciamento oculare costituito dall'etichetta del pulsante Explode](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="1e86c-151">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="1e86c-151">Congratulations</span></span>

<span data-ttu-id="1e86c-152">In questa esercitazione si è appreso come abilitare il tracciamento oculare per HoloLens 2 e come aggiungere questa funzionalità agli oggetti per attivare le azioni quando l'utente rivolge loro lo sguardo.</span><span class="sxs-lookup"><span data-stu-id="1e86c-152">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1e86c-153">Esercitazione successiva: 9. Uso dei comandi vocali</span><span class="sxs-lookup"><span data-stu-id="1e86c-153">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)