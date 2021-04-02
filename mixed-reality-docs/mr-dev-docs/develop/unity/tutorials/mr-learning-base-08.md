---
title: Uso del tracciamento oculare
description: Questa esercitazione illustra come usare il tracciamento oculare nelle app di realtà mista con Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, tracciamento oculare
ms.localizationpriority: high
ms.openlocfilehash: bf7bd266eb471193979c588d97d14dd37aed175e
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982889"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="0d3db-104">8. Uso del tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="0d3db-104">8. Using eye-tracking</span></span>

<span data-ttu-id="0d3db-105">In questa esercitazione si apprenderà come abilitare il tracciamento oculare per HoloLens 2 e aggiungere questa funzionalità agli oggetti, in modo da attivare le azioni quando l'utente rivolge loro lo sguardo.</span><span class="sxs-lookup"><span data-stu-id="0d3db-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="0d3db-106">Se si distribuisce questo progetto anche in HoloLens (prima generazione), tenere presente che il tracciamento oculare è supportato solo in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0d3db-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="0d3db-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="0d3db-107">Objectives</span></span>

* <span data-ttu-id="0d3db-108">Imparare ad abilitare il tracciamento oculare per HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="0d3db-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="0d3db-109">Imparare a usare il tracciamento oculare per attivare un'azione</span><span class="sxs-lookup"><span data-stu-id="0d3db-109">Learn how to use eye-tracking to trigger action</span></span>

[!INCLUDE[](includes/ensuring-eye-gaze-capabality.md)]

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="0d3db-110">Abilitazione dello sguardo fisso nel provider di dati per lo sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="0d3db-110">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="0d3db-111">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda MixedRealityToolkit > **Input** e seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="0d3db-111">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="0d3db-112">Clonare il profilo **DefaultHoloLens2InputSystemProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_HoloLens2InputSystemProfile_</span><span class="sxs-lookup"><span data-stu-id="0d3db-112">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="0d3db-113">Espandere la sezione **Pointers** (Puntatori)</span><span class="sxs-lookup"><span data-stu-id="0d3db-113">Expand the **Pointers** section</span></span>
* <span data-ttu-id="0d3db-114">Clonare il profilo **DefaultMixedRealityPointerProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_MixedRealityPointerProfile_</span><span class="sxs-lookup"><span data-stu-id="0d3db-114">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="0d3db-115">Individuare la sezione **Gaze Settings** (Impostazioni sguardo) e selezionare la casella di controllo **Is Eye Tracking Enabled** (Tracciamento oculare abilitato)</span><span class="sxs-lookup"><span data-stu-id="0d3db-115">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![Componente MixedRealityToolkit di Unity con i profili appena creati applicati e il tracciamento oculare abilitato](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="0d3db-117">Per rivedere la procedura di clonazione dei profili di MRTK, fare riferimento alle istruzioni riportate in [Configurazione dei profili di Mixed Reality Toolkit](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="0d3db-117">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="0d3db-118">Abilitazione del tracciamento oculare simulato per l'editor di Unity</span><span class="sxs-lookup"><span data-stu-id="0d3db-118">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="0d3db-119">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit**, nella finestra Inspector (Controllo) passare alla scheda **Input** e quindi:</span><span class="sxs-lookup"><span data-stu-id="0d3db-119">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="0d3db-120">Espandere la sezione **Input Data Providers** > **Input Simulation Service** (Provider di dati di input > Servizio di simulazione input)</span><span class="sxs-lookup"><span data-stu-id="0d3db-120">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="0d3db-121">Clonare il profilo **DefaultMixedRealityInputSimulationProfile** e assegnargli un nome appropriato, ad esempio _GettingStarted_MixedRealityInputSimulationProfile_</span><span class="sxs-lookup"><span data-stu-id="0d3db-121">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="0d3db-122">Individuare la **simulazione degli** sguardi a occhio e impostare la **modalità di simulazione degli sguardi** con occhi predefiniti sull' **asse di avanzamento della fotocamera**</span><span class="sxs-lookup"><span data-stu-id="0d3db-122">Locate **Eye Gaze Simulation** and set the **Default Eye Gaze Simulation Mode** to **Camera Forward Axis**</span></span>

![Unity con l'oggetto TextMeshPro selezionato](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="0d3db-124">Aggiunta del tracciamento oculare agli oggetti</span><span class="sxs-lookup"><span data-stu-id="0d3db-124">Adding eye-tracking to objects</span></span>

<span data-ttu-id="0d3db-125">Nella finestra gerarchia espandere i   >  **pulsanti** RoverExplorer, quindi selezionare tutti e tre gli oggetti Button figlio:</span><span class="sxs-lookup"><span data-stu-id="0d3db-125">In the Hierarchy window, expand the **RoverExplorer** > **Buttons**, then select all three of the child button objects:</span></span>

![Unity con oggetto Button selezionato](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="0d3db-127">Con tutti e tre gli oggetti pulsante ancora selezionati, nella finestra di controllo usare il pulsante **Aggiungi componente** per aggiungere il componente **EyeTrackingTarget** a tutti gli oggetti selezionati:</span><span class="sxs-lookup"><span data-stu-id="0d3db-127">With all three Button objects still selected, in the Inspector window use the **Add Component** button to add the **EyeTrackingTarget** component to all the selected objects:</span></span>

![Unity con l'oggetto TextMeshPro selezionato e componenti aggiunti](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="0d3db-129">Nella finestra gerarchia espandere **RoverExplorer**  >  **Buttons**  >  **hints**  >  **SeeItSayItLabel**  >  **TextMeshPro**</span><span class="sxs-lookup"><span data-stu-id="0d3db-129">In the Hierarchy window, expand **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel** > **TextMeshPro**</span></span>

<span data-ttu-id="0d3db-130">Nella finestra gerarchia selezionare quindi l'oggetto pulsante **hints** e configurare il componente **EyeTrackingTarget** nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="0d3db-130">Then in the Hierarchy window, select the **Hints** button object , and configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="0d3db-131">Nella sezione dell'evento **On Look At Start ()** (Quando viene rivolto lo sguardo all'inizio)</span><span class="sxs-lookup"><span data-stu-id="0d3db-131">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="0d3db-132">Fare clic sull'icona **+** piccola per aggiungere un altro evento</span><span class="sxs-lookup"><span data-stu-id="0d3db-132">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="0d3db-133">Assegnare l'oggetto  **TextMeshPro** dal pulsante **hints** al campo **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="0d3db-133">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="0d3db-134">Dall'elenco a discesa **No Function** (Nessuna funzione) selezionare **TextMeshPro** > **float fontSize** (fontSize mobile) per aggiornare il valore della proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="0d3db-134">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="0d3db-135">Impostare l'argomento su **0,06** per aumentare del 50% le dimensioni correnti del carattere 0,04</span><span class="sxs-lookup"><span data-stu-id="0d3db-135">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="0d3db-136">Nella sezione dell'evento **On Look Away ()** (Quando viene distolto lo sguardo)</span><span class="sxs-lookup"><span data-stu-id="0d3db-136">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="0d3db-137">Fare clic sull'icona **+** piccola per aggiungere un altro evento</span><span class="sxs-lookup"><span data-stu-id="0d3db-137">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="0d3db-138">Assegnare l'oggetto  **TextMeshPro** dal pulsante **hints** al campo **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="0d3db-138">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="0d3db-139">Dall'elenco a discesa **No Function** (Nessuna funzione) selezionare **TextMeshPro** > **float fontSize** (fontSize mobile) per aggiornare il valore della proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="0d3db-139">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="0d3db-140">Impostare l'argomento su **0,04** per ripristinare le dimensioni del carattere a 0,04</span><span class="sxs-lookup"><span data-stu-id="0d3db-140">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![Unity con l'oggetto TextMeshPro di Hints selezionato e il componente EyeTrackingTarget configurato](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="0d3db-142">**Ripetere** questo passaggio per l'oggetto pulsante **Esplodi** e **Reimposta** per configurare la verifica degli occhi per i pulsanti rimanenti.</span><span class="sxs-lookup"><span data-stu-id="0d3db-142">**Repeat** this step for **Explode** and **Reset** button object to configure eye tracking for remaining buttons.</span></span>

<span data-ttu-id="0d3db-143">Se si immette la modalità di gioco e si preme il pulsante destro del mouse mentre si sposta il mouse fino a quando lo sguardo raggiunge uno dei pulsanti, si noterà che le dimensioni del carattere del testo aumentano del 50% e vengono reimpostate sulle dimensioni originali quando si è interessati:</span><span class="sxs-lookup"><span data-stu-id="0d3db-143">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the buttons, you will see the text font size increase by 50% and reset back to its original size when looking away:</span></span>

![Doppia visualizzazione della modalità Play di Unity con lo sguardo che incontra l'obiettivo del tracciamento oculare costituito dall'etichetta del pulsante Explode](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="0d3db-145">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="0d3db-145">Congratulations</span></span>

<span data-ttu-id="0d3db-146">In questa esercitazione si è appreso come abilitare il tracciamento oculare per HoloLens 2 e come aggiungere questa funzionalità agli oggetti per attivare le azioni quando l'utente rivolge loro lo sguardo.</span><span class="sxs-lookup"><span data-stu-id="0d3db-146">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0d3db-147">Esercitazione successiva: 9. Uso dei comandi vocali</span><span class="sxs-lookup"><span data-stu-id="0d3db-147">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
