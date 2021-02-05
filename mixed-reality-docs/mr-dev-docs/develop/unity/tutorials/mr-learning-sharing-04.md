---
title: Condivisione dei movimenti di oggetti con più utenti
description: In questo corso viene illustrato come condividere i movimenti di oggetti con più utente in un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, funzionalità multiutente, Photon, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure
ms.localizationpriority: high
ms.openlocfilehash: d4dc943c8ca57331b4916e40db67df3cd3d6d2e6
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590063"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="0c86b-104">4. Condivisione dei movimenti di oggetti con più utenti</span><span class="sxs-lookup"><span data-stu-id="0c86b-104">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="0c86b-105">In questa esercitazione si apprenderà come condividere i movimenti degli oggetti in modo che tutti i partecipanti di un'esperienza condivisa possano collaborare e visualizzare le interazioni reciproche.</span><span class="sxs-lookup"><span data-stu-id="0c86b-105">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each other's interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="0c86b-106">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="0c86b-106">Objectives</span></span>

* <span data-ttu-id="0c86b-107">Configurare il progetto per condividere i movimenti degli oggetti</span><span class="sxs-lookup"><span data-stu-id="0c86b-107">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="0c86b-108">Imparare a creare un'app collaborativa multiutente di base</span><span class="sxs-lookup"><span data-stu-id="0c86b-108">Learn how to build a basic multi-user collaborative app</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="0c86b-109">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="0c86b-109">Preparing the scene</span></span>

<span data-ttu-id="0c86b-110">In questa sezione preparerai la scena aggiungendo il prefab dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="0c86b-110">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="0c86b-111">Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Prefab) e trascinare il prefab **TableAnchor** nell'oggetto **SharedPlayground** nella finestra Hierarchy (Gerarchia) per aggiungerlo alla scena come elemento figlio dell'oggetto SharedPlayground:</span><span class="sxs-lookup"><span data-stu-id="0c86b-111">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab onto the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![Unity con il prefab TableAnchor appena aggiunto selezionato](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="0c86b-113">Configurazione di PUN per creare un'istanza degli oggetti</span><span class="sxs-lookup"><span data-stu-id="0c86b-113">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="0c86b-114">In questa sezione si configurerà il progetto in modo da usare l'esperienza di Rover Explorer creata durante le [esercitazioni introduttive](mr-learning-base-01.md) e definire il punto in cui verrà creata un'istanza.</span><span class="sxs-lookup"><span data-stu-id="0c86b-114">In this section, you will configure the project to use the Rover Explorer experience created during the [Getting started tutorials](mr-learning-base-01.md) and define where it will be instantiated.</span></span>

<span data-ttu-id="0c86b-115">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Risorse).</span><span class="sxs-lookup"><span data-stu-id="0c86b-115">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="0c86b-116">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **NetworkLobby** e seleziona l'oggetto figlio **NetworkRoom** e quindi nella finestra Inspector (Controllo) individua il componente **Photon Room (Script)** (Stanza Photon - Script) e configuralo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="0c86b-116">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="0c86b-117">Al campo **Rover Explorer Prefab** (Prefab Rover Explorer) assegnare il prefab **RoverExplorer_Complete_Variant** dalla cartella Resources (Risorse)</span><span class="sxs-lookup"><span data-stu-id="0c86b-117">To the **Rover Explorer Prefab** field, assign the **RoverExplorer_Complete_Variant** prefab from the Resources folder</span></span>

![Unity con il componente Photon Room parzialmente configurato](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

<span data-ttu-id="0c86b-119">Con l'oggetto figlio **NetworkRoom** ancora selezionato, nella finestra Hierarchy (Gerarchia) espandi l'oggetto **TableAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Photon Room (Script)** (Stanza Photon - Script) e configuralo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="0c86b-119">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="0c86b-120">Al campo **Rover Explorer Location** (Posizione Rover Explorer) assegnare l'oggetto figlio TableAnchor > **Table** (Tabella) dalla finestra Hierarchy (Gerarchia)</span><span class="sxs-lookup"><span data-stu-id="0c86b-120">To the **Rover Explorer Location** field, assign the TableAnchor > **Table** child object from the Hierarchy window</span></span>

![Unity con il componente Photon Room configurato](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="0c86b-122">Prova dell'esperienza con il movimento di un oggetto condiviso</span><span class="sxs-lookup"><span data-stu-id="0c86b-122">Trying the experience with shared object movement</span></span>

<span data-ttu-id="0c86b-123">Se si compila e distribuisce il progetto Unity in HoloLens e quindi, tornando in Unity, si preme il pulsante Play per attivare la modalità di gioco mentre l'app è in esecuzione in HoloLens, si osserverà l'oggetto muoversi in Unity quando viene spostato in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="0c86b-123">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the app is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![Animazione che mostra Unity con oggetti collegati in rete](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="0c86b-125">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="0c86b-125">Congratulations</span></span>

<span data-ttu-id="0c86b-126">Il progetto è stato configurato in modo che i movimenti degli oggetti siano sincronizzati e gli utenti possano vedere gli oggetti muoversi quando vengono mossi da altri utenti.</span><span class="sxs-lookup"><span data-stu-id="0c86b-126">You have successfully configured your project to synchronize object movements so users can see the objects move when other users move them.</span></span> <span data-ttu-id="0c86b-127">Nell'esercitazione successiva verrà implementata la funzionalità per allineare l'esperienza nel mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="0c86b-127">In the next tutorial, you will implement functionality to align the experience in the physical world.</span></span> <span data-ttu-id="0c86b-128">In questo modo, gli utenti si vedranno reciprocamente nella posizione fisica effettiva e gli oggetti verranno visualizzati nella stessa rotazione e posizione fisica per tutti gli utenti.</span><span class="sxs-lookup"><span data-stu-id="0c86b-128">This will ensure the users see each other in their actual physical location, and so the objects appear in the same physical position and rotation for all users.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0c86b-129">Esercitazione successiva: 5. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa</span><span class="sxs-lookup"><span data-stu-id="0c86b-129">Next Tutorial: 5. Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)
