---
title: Esercitazioni sulle funzionalità multiutente - 5. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa
description: In questo corso viene illustrato come usare Ancoraggi nello spazio di Azure per ancorare oggetti in un'applicazione per HoloLens 2 condivisa da più utenti.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 65672bad9a967e11e7feb7efc45759608e9c9e76
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353429"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="024e5-105">5. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa</span><span class="sxs-lookup"><span data-stu-id="024e5-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="024e5-106">In questa esercitazione apprenderai come integrare Ancoraggi nello spazio di Azure nell'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="024e5-106">In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience.</span></span> <span data-ttu-id="024e5-107">Ancoraggi nello spazio di Azure consente a più dispositivi di avere un riferimento comune al mondo fisico, in modo che gli utenti possano vedersi reciprocamente nella rispettiva posizione fisica effettiva e vedere l'esperienza condivisa nella medesima posizione.</span><span class="sxs-lookup"><span data-stu-id="024e5-107">ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.</span></span>

## <a name="objectives"></a><span data-ttu-id="024e5-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="024e5-108">Objectives</span></span>

* <span data-ttu-id="024e5-109">Integrare Ancoraggi nello spazio di Azure in un'esperienza condivisa per l'allineamento di più dispositivi</span><span class="sxs-lookup"><span data-stu-id="024e5-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
* <span data-ttu-id="024e5-110">Apprendere le nozioni di base sul funzionamento di Ancoraggi nello spazio di Azure nel contesto di un'esperienza condivisa locale</span><span class="sxs-lookup"><span data-stu-id="024e5-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="024e5-111">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="024e5-111">Preparing the scene</span></span>

<span data-ttu-id="024e5-112">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **SharedPlayground** e quindi l'oggetto **TableAnchor** per esporre i relativi oggetti figlio:</span><span class="sxs-lookup"><span data-stu-id="024e5-112">In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:</span></span>

![Unity con gli oggetti SharedPlayground e TableAnchor espansi](images/mr-learning-sharing/sharing-05-section1-step1-1.png)

<span data-ttu-id="024e5-114">Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset)  > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Prefab) e trascinare il prefab **Buttons** nell'oggetto figlio **TableAnchor** , per aggiungerlo alla scena come elemento figlio dell'oggetto TableAnchor:</span><span class="sxs-lookup"><span data-stu-id="024e5-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab onto the **TableAnchor** child object to add it to your scene as a child of the TableAnchor object:</span></span>

![Unity con il prefab Buttons appena aggiunto selezionato](images/mr-learning-sharing/sharing-05-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="024e5-116">Configurazione dei pulsanti per il funzionamento della scena</span><span class="sxs-lookup"><span data-stu-id="024e5-116">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="024e5-117">In questa sezione verrà configurata una serie di eventi Button che illustrano le nozioni di base per poter usare Ancoraggi nello spazio di Azure e ottenere l'allineamento spaziale in un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="024e5-117">In this section, you will configure a series of button events demonstrating the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.</span></span>

<span data-ttu-id="024e5-118">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **Button** e seleziona il primo oggetto pulsante figlio denominato **StartAzureSession** :</span><span class="sxs-lookup"><span data-stu-id="024e5-118">In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession** :</span></span>

![Unity con l'oggetto pulsante StartAzureSession selezionato](images/mr-learning-sharing/sharing-05-section2-step1-1.png)

<span data-ttu-id="024e5-120">Nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e configura l'evento **OnClick ()** nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="024e5-120">In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="024e5-121">Al campo **None (Object)** (Nessuno - Oggetto) assegnare l'oggetto **TableAnchor**</span><span class="sxs-lookup"><span data-stu-id="024e5-121">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="024e5-122">Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare la funzione **AnchorModuleScript** > **StartAzureSession ()**</span><span class="sxs-lookup"><span data-stu-id="024e5-122">From the **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function</span></span>

![Unity con l'evento OnClick del pulsante StartAzureSession configurato](images/mr-learning-sharing/sharing-05-section2-step1-2.png)

<span data-ttu-id="024e5-124">Nella finestra Hierarchy (Gerarchia) seleziona il secondo oggetto pulsante figlio denominato **CreateAzureAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e configura l'evento **OnClick ()** nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="024e5-124">In the Hierarchy window, select the second child button object named **CreateAzureAnchor** , then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="024e5-125">Al campo **None (Object)** (Nessuno - Oggetto) assegnare l'oggetto **TableAnchor**</span><span class="sxs-lookup"><span data-stu-id="024e5-125">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="024e5-126">Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare la funzione **AnchorModuleScript** > **CreateAzureAnchor ()**</span><span class="sxs-lookup"><span data-stu-id="024e5-126">From the **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function</span></span>
* <span data-ttu-id="024e5-127">Al nuovo campo **None (Game Object)** (Nessuno - Oggetto gioco) che viene visualizzato assegna l'oggetto **TableAnchor**</span><span class="sxs-lookup"><span data-stu-id="024e5-127">To the new **None (Game Object)** field that appears, assign the **TableAnchor** object</span></span>

![Unity con l'evento OnClick del pulsante CreateAzureAnchor configurato](images/mr-learning-sharing/sharing-05-section2-step1-3.png)

<span data-ttu-id="024e5-129">Nella finestra Hierarchy (Gerarchia) seleziona il terzo oggetto pulsante figlio denominato **ShareAzureAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e configura l'evento **OnClick ()** nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="024e5-129">In the Hierarchy window, select the third child button object named **ShareAzureAnchor** , then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="024e5-130">Al campo **None (Object)** (Nessuno - Oggetto) assegnare l'oggetto **TableAnchor**</span><span class="sxs-lookup"><span data-stu-id="024e5-130">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="024e5-131">Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare la funzione **SharingModuleScript** > **ShareAzureAnchor ()**</span><span class="sxs-lookup"><span data-stu-id="024e5-131">From the **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function</span></span>

![Unity con l'evento OnClick del pulsante ShareAzureAnchor configurato](images/mr-learning-sharing/sharing-05-section2-step1-4.png)

<span data-ttu-id="024e5-133">Nella finestra Hierarchy (Gerarchia) selezionare il quarto oggetto pulsante figlio denominato **GetAzureAnchor** e quindi nella finestra Inspector (Controllo) individuare il componente **Interactable (Script)** (Con supporto per interazioni - Script) e configurare l'evento **OnClick ()** nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="024e5-133">In the Hierarchy window, select the fourth child button object named **GetAzureAnchor** , then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="024e5-134">Al campo **None (Object)** (Nessuno - Oggetto) assegnare l'oggetto **TableAnchor**</span><span class="sxs-lookup"><span data-stu-id="024e5-134">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="024e5-135">Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare la funzione **SharingModuleScript** > **GetAzureAnchor ()**</span><span class="sxs-lookup"><span data-stu-id="024e5-135">From the **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function</span></span>

![Unity con l'evento OnClick del pulsante GetAzureAnchor configurato](images/mr-learning-sharing/sharing-05-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="024e5-137">Connessione della scena alla risorsa di Azure</span><span class="sxs-lookup"><span data-stu-id="024e5-137">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="024e5-138">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **SharedPlayground** e seleziona l'oggetto **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="024e5-138">In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object.</span></span>

<span data-ttu-id="024e5-139">Nella finestra Inspector (Controllo) individuare il componente **Spatial Anchor Manager (Script)** (Gestione ancoraggi nello spazio - Script) e configurare la sezione **Credentials** (Credenziali) con le credenziali dell'account di Ancoraggi nello spazio di Azure creato in fase di definizione dei [Prerequisiti](mr-learning-sharing-01.md#prerequisites) per questa serie di esercitazioni:</span><span class="sxs-lookup"><span data-stu-id="024e5-139">In the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-sharing-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="024e5-140">Nel campo **Spatial Anchors Account ID** (ID account Ancoraggi nello spazio) incolla il valore di **Account ID** (ID account) del tuo account di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="024e5-140">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="024e5-141">Nel campo **Spatial Anchors Account Key** (Chiave account Ancoraggi nello spazio) incolla il valore di **Access Key** (Chiave di accesso) primario o secondario del tuo account di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="024e5-141">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![Unity con Spatial Anchor Manager configurato](images/mr-learning-sharing/sharing-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="024e5-143">Anziché impostare nella scena l'ID e la chiave dell'account di Ancoraggi nello spazio, è possibile impostarla per l'intero progetto. Questa soluzione può risultare vantaggiosa se sono disponibili più scene con ASA.</span><span class="sxs-lookup"><span data-stu-id="024e5-143">Instead of setting the Spatial Anchors Account ID and Key in the scene, you can set it for your entire project, this can be advantageous if you have multiple scenes using ASA.</span></span> <span data-ttu-id="024e5-144">A tale scopo, nella finestra Project (Progetto) passare all'asset Assets (Asset) > AzureSpatialAnchors.SDK > Resources (Risorse) > **SpatialAnchorConfig** e quindi impostare i valori nella finestra Inspector (Controllo).</span><span class="sxs-lookup"><span data-stu-id="024e5-144">To do this, in the Project window, navigate to the Assets > AzureSpatialAnchors.SDK > Resources > **SpatialAnchorConfig** asset, then set the values in the Inspector window.</span></span>

<span data-ttu-id="024e5-145">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **TableAnchor** e quindi nella finestra Inspector (Controllo) individuare il componente **Anchor Module (Script)** (Modulo di ancoraggio - Script) e configuralo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="024e5-145">In the Hierarchy window, select the **TableAnchor** object, then in the Inspector window, locate the **Anchor Module (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="024e5-146">Nel campo **Public Sharing Pin** (PIN di condivisione pubblico) modificare alcune cifre, in modo che il PIN diventi univoco per il progetto</span><span class="sxs-lookup"><span data-stu-id="024e5-146">In the **Public Sharing Pin** field, change a few digits, so the pin becomes unique to your project</span></span>

![Unity con Anchor Module Script configurato](images/mr-learning-sharing/sharing-05-section3-step1-2.png)

<span data-ttu-id="024e5-148">Con l'oggetto **TableAnchor** ancora selezionato, nella finestra Inspector (Controllo) verificare che tutti i componenti dello script siano **abilitati** :</span><span class="sxs-lookup"><span data-stu-id="024e5-148">With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are **enabled** :</span></span>

* <span data-ttu-id="024e5-149">Seleziona la casella di controllo accanto a **Spatial Anchor Manager (Script)** (Gestione ancoraggi nello spazio - Script) per abilitarlo</span><span class="sxs-lookup"><span data-stu-id="024e5-149">Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it</span></span>
* <span data-ttu-id="024e5-150">Seleziona la casella di controllo accanto a **Anchor Module Script (Script)** (Script modulo di ancoraggio - Script) per abilitarlo</span><span class="sxs-lookup"><span data-stu-id="024e5-150">Check the checkbox next to the **Anchor Module Script (Script)** components to enable it</span></span>
* <span data-ttu-id="024e5-151">Seleziona la casella di controllo accanto a **Sharing Module Script (Script)** (Script modulo di condivisione - Script) per abilitarlo</span><span class="sxs-lookup"><span data-stu-id="024e5-151">Check the checkbox next to the **Sharing Module Script (Script)** components to enable it</span></span>

![Unity con tutti i componenti script TableAnchor abilitati](images/mr-learning-sharing/sharing-05-section3-step1-3.png)

## <a name="trying-the-experience-with-spatial-alignment"></a><span data-ttu-id="024e5-153">Prova dell'esperienza con l'allineamento spaziale</span><span class="sxs-lookup"><span data-stu-id="024e5-153">Trying the experience with spatial alignment</span></span>

> [!NOTE]
> <span data-ttu-id="024e5-154">Non è possibile eseguire Ancoraggi nello spazio di Azure in Unity.</span><span class="sxs-lookup"><span data-stu-id="024e5-154">Azure Spatial Anchors can not run in Unity.</span></span> <span data-ttu-id="024e5-155">Di conseguenza, per testare la funzionalità di questo servizio, è necessario distribuire il progetto in almeno due dispositivi.</span><span class="sxs-lookup"><span data-stu-id="024e5-155">Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two devices.</span></span>

<span data-ttu-id="024e5-156">Se si compila e distribuisce il progetto Unity in due dispositivi, è possibile ottenere l'allineamento spaziale tra i dispositivi condividendo l'ID ancoraggio di Azure.</span><span class="sxs-lookup"><span data-stu-id="024e5-156">If you now build and deploy the Unity project to two devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="024e5-157">Per provare, puoi seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="024e5-157">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="024e5-158">Nel dispositivo 1: **Avviare l'app** (un'istanza di Rover Explorer è stata creata e posizionata sulla tabella)</span><span class="sxs-lookup"><span data-stu-id="024e5-158">On device 1: **Start the app** (the Rover Explorer is instantiated and placed on the table)</span></span>
2. <span data-ttu-id="024e5-159">Nel dispositivo 2: **Avviare l'app** (entrambi gli utenti visualizzano la tabella con Rover Explorer, ma la tabella non è visualizzata nella stessa posizione e gli avatar degli utenti non compaiono nella posizione reale degli utenti)</span><span class="sxs-lookup"><span data-stu-id="024e5-159">On device 2: **Start the app** (both users see the table with the Rover Explorer, but the table does not appear in the same place, and the user avatars do not appear where the users are)</span></span>
3. <span data-ttu-id="024e5-160">Nel dispositivo 1: Premi il pulsante **Start Azure Session** (Avvia sessione di Azure)</span><span class="sxs-lookup"><span data-stu-id="024e5-160">On device 1: Press the **Start Azure Session** button</span></span>
4. <span data-ttu-id="024e5-161">Nel dispositivo 1: Premi il pulsante **Create Azure Anchor** (Crea ancoraggio di Azure) (crea l'ancoraggio nella posizione dell'oggetto TableAnchor e archivia le informazioni relative all'ancoraggio nella risorsa di Azure).</span><span class="sxs-lookup"><span data-stu-id="024e5-161">On device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).</span></span>
5. <span data-ttu-id="024e5-162">Nel dispositivo 1: Premi il pulsante **Share Azure Anchor** (Condividi ancoraggio di Azure) (condivide l'ID ancoraggio con altri utenti in tempo reale)</span><span class="sxs-lookup"><span data-stu-id="024e5-162">On device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)</span></span>
6. <span data-ttu-id="024e5-163">Nel dispositivo 2: Premi il pulsante **Start Azure Session** (Avvia sessione di Azure)</span><span class="sxs-lookup"><span data-stu-id="024e5-163">On device 2: Press the **Start Azure Session** button</span></span>
7. <span data-ttu-id="024e5-164">Nel dispositivo 2: Premere il pulsante **Get Azure Anchor** (Ottieni ancoraggio di Azure) (si connette alla risorsa di Azure per recuperare le informazioni relative all'ancoraggio per l'ID ancoraggio condiviso e quindi sposta l'oggetto TableAnchor nella posizione in cui è stato creato l'ancoraggio con il dispositivo 1)</span><span class="sxs-lookup"><span data-stu-id="024e5-164">On device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the device 1)</span></span>

> [!TIP]
> <span data-ttu-id="024e5-165">Se non si ha accesso a due dispositivi HoloLens, è possibile seguire la procedura per la [creazione di Ancoraggi nello spazio di Azure per dispositivi mobili](mr-learning-asa-05.md) per distribuire il progetto nel dispositivo mobile.</span><span class="sxs-lookup"><span data-stu-id="024e5-165">If you don't have access to two HoloLens devices, you may follow the [Building Azure Spatial Anchors for mobile devices](mr-learning-asa-05.md) to deploy the project to your mobile device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="024e5-166">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="024e5-166">Congratulations</span></span>

<span data-ttu-id="024e5-167">In questa esercitazione hai appreso come integrare il potente servizio Ancoraggi nello spazio di Azure per allineare i dispositivi in un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="024e5-167">In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience.</span></span>

<span data-ttu-id="024e5-168">Si conclude così la serie di esercitazioni in cui sono state fornite istruzioni per impostare un account Photon, creare un'app PUN, integrare PUN nel progetto Unity, configurare gli avatar degli utenti e gli oggetti condivisi e infine allineare più partecipanti tramite Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="024e5-168">This also concludes this tutorial series where you learned how to set up a Photon account, create a PUN app, integrate PUN into the Unity project, configure user avatars and shared objects, and finally align multiple participants using Azure Spatial Anchors.</span></span>
