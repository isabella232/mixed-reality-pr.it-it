---
title: Connessione di più utenti
description: In questo corso viene illustrato come connettere più utenti in un'applicazione di realtà mista per HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, funzionalità multiutente, Photon, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure
ms.localizationpriority: high
ms.openlocfilehash: 0c6bf0871836ad7aae9c3906b2042f97ae003ebf
ms.sourcegitcommit: 3dad2adfdb5bdb8100d8d864f7845e34a3ef912d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2021
ms.locfileid: "98699065"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="69647-104">3. Connessione di più utenti</span><span class="sxs-lookup"><span data-stu-id="69647-104">3. Connecting multiple users</span></span>

<span data-ttu-id="69647-105">In questa esercitazione imparerai a connettere più utenti all'interno di un'esperienza live condivisa.</span><span class="sxs-lookup"><span data-stu-id="69647-105">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="69647-106">Al termine dell'esercitazione sarà possibile eseguire l'app in più dispositivi e fare in modo che ogni utente visualizzi l'avatar degli altri utenti muoversi in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="69647-106">By the end of the tutorial, you will be able to run the app on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="69647-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="69647-107">Objectives</span></span>

* <span data-ttu-id="69647-108">Imparare a connettere più utenti in un'esperienza condivisa</span><span class="sxs-lookup"><span data-stu-id="69647-108">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="69647-109">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="69647-109">Preparing the scene</span></span>

<span data-ttu-id="69647-110">In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="69647-110">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="69647-111">Nella finestra Project (Progetto) passare alla cartella **Assets**  (Asset)  > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Prefab) e quindi fare clic e trascinare i prefab seguenti sulla finestra Hierarchy (Gerarchia) per aggiungerli alla scena:</span><span class="sxs-lookup"><span data-stu-id="69647-111">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="69647-112">Prefab **NetworkLobby**</span><span class="sxs-lookup"><span data-stu-id="69647-112">**NetworkLobby** prefab</span></span>
* <span data-ttu-id="69647-113">Prefab **SharedPlayground**</span><span class="sxs-lookup"><span data-stu-id="69647-113">**SharedPlayground** prefab</span></span>

![Unity con i prefab NetworkLobby e SharedPlayground appena aggiunti selezionati](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

<span data-ttu-id="69647-115">Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset)  > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** (Prefab) e quindi fare clic e trascinare il prefab seguente sulla finestra Hierarchy (Gerarchia) per aggiungerlo alla scena:</span><span class="sxs-lookup"><span data-stu-id="69647-115">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefab into the Hierarchy window to add it to your scene:</span></span>

* <span data-ttu-id="69647-116">Prefab **DebugWindow**</span><span class="sxs-lookup"><span data-stu-id="69647-116">**DebugWindow** prefab</span></span>

![Unity con il prefab DebugWindow appena aggiunto selezionato](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="69647-118">Creazione del prefab dell'utente</span><span class="sxs-lookup"><span data-stu-id="69647-118">Creating the user prefab</span></span>

<span data-ttu-id="69647-119">In questa sezione creerai un prefab che verrà usato per rappresentare gli utenti nell'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="69647-119">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="69647-120">1. Creare e configurare l'utente</span><span class="sxs-lookup"><span data-stu-id="69647-120">1. Create and configure the user</span></span>

<span data-ttu-id="69647-121">Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse su un'area vuota e seleziona **Create Empty** (Crea vuoto) per aggiungere alla scena un oggetto vuoto, assegna all'oggetto il nome **PhotonUser** e configuralo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="69647-121">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="69647-122">Verifica che il campo **Position** (Posizione) della trasformazione sia impostato su X = 0, Y = 0, Z = 0:</span><span class="sxs-lookup"><span data-stu-id="69647-122">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![Unity con l'oggetto PhotonUser appena creato selezionato](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

<span data-ttu-id="69647-124">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **PhotonUser** e quindi nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Photon User (Script)** (Utente Photon - Script) all'oggetto PhotonUser:</span><span class="sxs-lookup"><span data-stu-id="69647-124">In the Hierarchy window, select the **PhotonUser** object, then in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![Unity con il componente Photon User aggiunto](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

<span data-ttu-id="69647-126">Nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Generic Net Sync (Script)** (Sincronizzazione rete generica - Script) all'oggetto PhotonUser e configura l'oggetto nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="69647-126">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="69647-127">Seleziona la casella di controllo **Is User** (È utente)</span><span class="sxs-lookup"><span data-stu-id="69647-127">Check the **Is User** checkbox</span></span>

![Unity con il componente Generic Net Sync aggiunto e configurato](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

<span data-ttu-id="69647-129">Nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Photon View (Script)** (Visualizzazione Photon - Script) all'oggetto PhotonUser e configura l'oggetto nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="69647-129">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="69647-130">Verificare che il campo **componenti osservati** sia assegnato con il componente **generico di sincronizzazione rete (script)**</span><span class="sxs-lookup"><span data-stu-id="69647-130">Ensure that the **Observed Components** field is assigned with the **Generic Net Sync (Script)** component</span></span>

![Unity con il componente Photon View aggiunto e configurato](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="69647-132">2. Creare l'avatar</span><span class="sxs-lookup"><span data-stu-id="69647-132">2. Create the avatar</span></span>

<span data-ttu-id="69647-133">Nella finestra del progetto passare alla cartella **assets**  >  **MRTK**  >  **StandardAssets**  >  **Materials** per individuare i materiali MRTK.</span><span class="sxs-lookup"><span data-stu-id="69647-133">In the Project window, navigate to the **Assets** > **MRTK** > **StandardAssets** > **Materials** folder to locate the MRTK materials.</span></span>

<span data-ttu-id="69647-134">Nella finestra Hierarchy (Gerarchia) fare quindi clic con il pulsante destro del mouse sull'oggetto **PhotonUser** e selezionare **3D Object** > **Sphere** (Oggetto 3D > Sfera) per creare un oggetto sfera come elemento figlio dell'oggetto PhotonUser e configuralo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="69647-134">Then, in the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="69647-135">Verifica che il campo **Position** (Posizione) della trasformazione sia impostato su X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="69647-135">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="69647-136">Imposta il campo **Scale** (Ridimensiona) della trasformazione su una dimensione appropriata, ad esempio X = 0.15, Y = 0.15, Z = 0.15</span><span class="sxs-lookup"><span data-stu-id="69647-136">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>
* <span data-ttu-id="69647-137">Al campo MeshRenderer > Materials > **Element 0** (Materiali > Elemento 0) assegnare il materiale **MRTK_Standard_White**</span><span class="sxs-lookup"><span data-stu-id="69647-137">To the MeshRenderer > Materials > **Element 0** field, assign the **MRTK_Standard_White** material</span></span>

![Unity con la sfera avatar appena creata e configurata](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="69647-139">3. Creare il prefab</span><span class="sxs-lookup"><span data-stu-id="69647-139">3. Create the prefab</span></span>

<span data-ttu-id="69647-140">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Risorse):</span><span class="sxs-lookup"><span data-stu-id="69647-140">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![Finestra Project di Unity con la cartella Resource selezionata](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

<span data-ttu-id="69647-142">Con la cartella Resources (Risorse) ancora selezionata, **fai clic e trascina** l'oggetto **PhotonUser** dalla finestra Hierarchy (Gerarchia) nella cartella **Resources** (Risorse) per convertire l'oggetto PhotonUser in un prefab:</span><span class="sxs-lookup"><span data-stu-id="69647-142">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![Unity con il prefab PhotonUser appena creato selezionato](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

<span data-ttu-id="69647-144">Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse sull'oggetto **PhotonUser** e seleziona **Delete** (Elimina) per rimuovere l'oggetto dalla scena:</span><span class="sxs-lookup"><span data-stu-id="69647-144">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![Unity con l'oggetto prefab PhotonUser appena creato rimosso dalla scena](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="69647-146">Configurazione di PUN per creare un'istanza del prefab dell'utente</span><span class="sxs-lookup"><span data-stu-id="69647-146">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="69647-147">In questa sezione configurerai il progetto per l'uso del prefab PhotonUser creato nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="69647-147">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="69647-148">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Risorse).</span><span class="sxs-lookup"><span data-stu-id="69647-148">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="69647-149">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **NetworkLobby** e seleziona l'oggetto figlio **NetworkRoom** e quindi nella finestra Inspector (Controllo) individua il componente **Photon Room (Script)** (Stanza Photon - Script) e configuralo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="69647-149">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="69647-150">Al campo **Photon User Prefab** (Prefab utente Photon) assegna il prefab **PhotonUser** dalla cartella Resources (Risorse)</span><span class="sxs-lookup"><span data-stu-id="69647-150">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![Unity con il componente Photon Room parzialmente configurato](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="69647-152">Prova dell'esperienza con più utenti</span><span class="sxs-lookup"><span data-stu-id="69647-152">Trying the experience with multiple users</span></span>

<span data-ttu-id="69647-153">Se si compila e distribuisce il progetto Unity in HoloLens e quindi, tornando in Unity, si attiva la modalità di gioco mentre l'app è in esecuzione in HoloLens, si visualizzerà l'avatar dell'utente HoloLens muoversi quando si muove la testa (HoloLens):</span><span class="sxs-lookup"><span data-stu-id="69647-153">If you now build and deploy the Unity project to your HoloLens, then, back in Unity, enter Game mode while the app is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![Animazione che mostra Unity con utenti collegati in rete](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="69647-155">Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="69647-155">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="69647-156">Poiché l'app deve connettersi a Photon, assicurarsi che il computer o il dispositivo sia connesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="69647-156">The app needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="69647-157">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="69647-157">Congratulations</span></span>

<span data-ttu-id="69647-158">Hai configurato il progetto per consentire a più utenti di connettersi alla stessa esperienza e vedere i movimenti gli uni degli altri.</span><span class="sxs-lookup"><span data-stu-id="69647-158">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="69647-159">Nella prossima esercitazione implementerai le funzionalità in modo che anche i movimenti degli oggetti vengano condivisi tra più dispositivi.</span><span class="sxs-lookup"><span data-stu-id="69647-159">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="69647-160">Esercitazione successiva: 4. Condivisione dei movimenti di oggetti con più utenti</span><span class="sxs-lookup"><span data-stu-id="69647-160">Next Tutorial: 4. Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
