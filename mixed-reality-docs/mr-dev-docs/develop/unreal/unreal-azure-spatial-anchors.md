---
title: Ancoraggi nello spazio di Azure in Unreal
description: Panoramica della creazione di Ancoraggi nello spazio di Azure nel motore Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 07/01/2020
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, azure, sviluppo di azure, ancoraggi nello spazio, realtà mista, sviluppo, funzionalità, nuovo progetto, emulatore, documentazione, guide, ologrammi, sviluppo di giochi, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: b464292b606f6c375fe84a50867cac770cd8f001
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354549"
---
# <a name="azure-spatial-anchors-in-unreal"></a><span data-ttu-id="81d39-104">Ancoraggi nello spazio di Azure in Unreal</span><span class="sxs-lookup"><span data-stu-id="81d39-104">Azure Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="81d39-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="81d39-105">Overview</span></span>

<span data-ttu-id="81d39-106">Ancoraggi nello spazio di Azure è un servizio di Realtà mista di Microsoft che consente ai dispositivi di realtà aumentata di individuare, condividere e salvare in modo permanente i punti di ancoraggio nel mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="81d39-106">Azure Spatial Anchors is a Microsoft Mixed Reality service, allowing augmented reality devices to discover, share, and persist anchor points in the physical world.</span></span> <span data-ttu-id="81d39-107">La documentazione seguente fornisce istruzioni utili per l'integrazione del servizio Ancoraggi nello spazio di Azure in un progetto Unreal.</span><span class="sxs-lookup"><span data-stu-id="81d39-107">Documentation below provides instructions for integrating the Azure Spatial Anchors service into an Unreal project.</span></span> <span data-ttu-id="81d39-108">Per altre informazioni, vedere il [servizio Ancoraggi nello spazio di Azure](https://azure.microsoft.com/services/spatial-anchors/).</span><span class="sxs-lookup"><span data-stu-id="81d39-108">If you're looking for more information, check out the [Azure Spatial Anchors service](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

> [!NOTE]
> <span data-ttu-id="81d39-109">Unreal Engine 4.26 è ora dotato di plug-in per il supporto di ARKit e ARCore nel caso in cui la destinazione sia un dispositivo iOS o Android.</span><span class="sxs-lookup"><span data-stu-id="81d39-109">Unreal Engine 4.26 now has plugins for ARKit and ARCore support if you're targeting iOS or Android.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="81d39-110">Gli ancoraggi locali vengono archiviati nel dispositivo, mentre i dati relativi ad Ancoraggi nello spazio di Azure vengono archiviati nel cloud.</span><span class="sxs-lookup"><span data-stu-id="81d39-110">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="81d39-111">Se si vuole archiviare gli ancoraggi in locale in un dispositivo, è disponibile il documento [Ancoraggi nello spazio locali](unreal-spatial-anchors.md) che fornisce informazioni dettagliate per l'esecuzione del processo.</span><span class="sxs-lookup"><span data-stu-id="81d39-111">If you're looking to store your anchors locally on a device, we have a [Local Spatial Anchors](unreal-spatial-anchors.md) document that can walk you through the process.</span></span> <span data-ttu-id="81d39-112">Si noti che è possibile includere ancoraggi locali e ancoraggi di Azure nello stesso progetto senza che si verifichino conflitti.</span><span class="sxs-lookup"><span data-stu-id="81d39-112">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="81d39-113">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="81d39-113">Prerequisites</span></span>

<span data-ttu-id="81d39-114">Per completare le procedure contenute in questa guida, verificare che siano soddisfatti i requisti seguenti:</span><span class="sxs-lookup"><span data-stu-id="81d39-114">To complete this guide, make sure you have:</span></span>

- <span data-ttu-id="81d39-115">Installato [Unreal versione 4.25](https://www.unrealengine.com/get-now) o successiva</span><span class="sxs-lookup"><span data-stu-id="81d39-115">Installed [Unreal version 4.25](https://www.unrealengine.com/get-now) or later</span></span>
- <span data-ttu-id="81d39-116">[Progetto HoloLens 2](tutorials/unreal-uxt-ch1.md) configurato in Unreal</span><span class="sxs-lookup"><span data-stu-id="81d39-116">A [HoloLens 2 project](tutorials/unreal-uxt-ch1.md) setup in Unreal</span></span> 
- <span data-ttu-id="81d39-117">Leggere la sezione [Panoramica di Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors/overview)</span><span class="sxs-lookup"><span data-stu-id="81d39-117">Read through the [Azure Spatial Anchors overview](https://docs.microsoft.com/azure/spatial-anchors/overview)</span></span>
- <span data-ttu-id="81d39-118">Nozioni di base su C++ e Unreal</span><span class="sxs-lookup"><span data-stu-id="81d39-118">Basic knowledge on C++ and Unreal</span></span>

## <a name="getting-azure-spatial-anchors-account-info"></a><span data-ttu-id="81d39-119">Recupero delle informazioni sull'account di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="81d39-119">Getting Azure Spatial Anchors account info</span></span>

<span data-ttu-id="81d39-120">Prima di usare Ancoraggi nello spazio di Azure nel progetto, è necessario:</span><span class="sxs-lookup"><span data-stu-id="81d39-120">Before using Azure Spatial Anchors in your project, you need to:</span></span>
* <span data-ttu-id="81d39-121">[Creare una risorsa di Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) e copiare i campi dell'account elencati di seguito.</span><span class="sxs-lookup"><span data-stu-id="81d39-121">[Create a spatial anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) and copy the account fields listed below.</span></span> <span data-ttu-id="81d39-122">Questi valori vengono usati per autenticare gli utenti con l'account dell'applicazione:</span><span class="sxs-lookup"><span data-stu-id="81d39-122">These values are used to authenticate users with your application's account:</span></span>
    * <span data-ttu-id="81d39-123">**ID account**</span><span class="sxs-lookup"><span data-stu-id="81d39-123">**Account ID**</span></span>
    * <span data-ttu-id="81d39-124">**Chiave dell'account**</span><span class="sxs-lookup"><span data-stu-id="81d39-124">**Account Key**</span></span>

<span data-ttu-id="81d39-125">Per altre informazioni, vedere la documentazione relativa all'[autenticazione di Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp).</span><span class="sxs-lookup"><span data-stu-id="81d39-125">Check out the [Azure Spatial Anchors authentication](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp) docs for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="81d39-126">Ancoraggi nello spazio di Azure in Unreal 4.25 non supporta i token di autenticazione di Azure AD. Il supporto per questa funzionalità, tuttavia, sarà disponibile in una versione successiva.</span><span class="sxs-lookup"><span data-stu-id="81d39-126">Azure Spatial Anchors in Unreal 4.25 does not support Azure AD authentication tokens, but support for this functionality will be coming in a later release.</span></span>

## <a name="adding-azure-spatial-anchors-plugins"></a><span data-ttu-id="81d39-127">Aggiunta di plug-in di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="81d39-127">Adding Azure Spatial Anchors plugins</span></span>

<span data-ttu-id="81d39-128">Abilitare i plug-in di Ancoraggi nello spazio di Azure nell'editor Unreal nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="81d39-128">Enable the Azure Spatial Anchors plugins in the Unreal editor by:</span></span>
1. <span data-ttu-id="81d39-129">Fare clic su **Edit > Plugins** (Modifica > Plug-in) e cercare **AzureSpatialAnchors** e **AzureSpatialAnchorsForWMR**.</span><span class="sxs-lookup"><span data-stu-id="81d39-129">Clicking **Edit > Plugins** and searching for **AzureSpatialAnchors** and **AzureSpatialAnchorsForWMR**.</span></span>
2. <span data-ttu-id="81d39-130">Selezionare la casella di controllo **Enabled** (Abilitato) di entrambi i plug-in per consentire l'accesso alle librerie del progetto di Ancoraggi nello spazio di Azure nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="81d39-130">Select the **Enabled** checkbox in both plugins to allow access to the Azure Spatial Anchors blueprint libraries in your application.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-01.png)

<span data-ttu-id="81d39-132">Al termine, riavviare l'editor Unreal per rendere effettive le modifiche apportate ai plug-in.</span><span class="sxs-lookup"><span data-stu-id="81d39-132">Once that's done, restart the Unreal Editor for the plugin changes to take effect.</span></span> <span data-ttu-id="81d39-133">Il progetto è ora pronto per l'uso di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-133">The project is now ready to use Azure Spatial Anchors.</span></span>

## <a name="starting-a-spatial-anchors-session"></a><span data-ttu-id="81d39-134">Avvio di una sessione di Ancoraggi nello spazio</span><span class="sxs-lookup"><span data-stu-id="81d39-134">Starting a Spatial Anchors session</span></span>
<span data-ttu-id="81d39-135">Una sessione di Ancoraggi nello spazio di Azure consente alle applicazioni client di comunicare con il servizio Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-135">An Azure Spatial Anchors session allows client applications to communicate with the Azure Spatial Anchors service.</span></span> <span data-ttu-id="81d39-136">È necessario creare e avviare una sessione di Ancoraggi nello spazio di Azure per creare, salvare in modo permanente e condividere Ancoraggi nello spazio di Azure:</span><span class="sxs-lookup"><span data-stu-id="81d39-136">You'll need to create and start an Azure Spatial Anchors session to create, persist, and share Azure Spatial Anchors:</span></span>

1. <span data-ttu-id="81d39-137">Aprire il progetto per il pedone che si sta usando nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="81d39-137">Open the blueprint for the Pawn you're using in the application.</span></span>
2. <span data-ttu-id="81d39-138">Aggiungere due variabili di stringa per **ID account** e **Chiave dell'account** e quindi assegnare i valori corrispondenti dell'account di Ancoraggi nello spazio di Azure per eseguire l'autenticazione della sessione.</span><span class="sxs-lookup"><span data-stu-id="81d39-138">Add two string variables for the **Account ID** and **Account Key**, then assign the corresponding values from your Azure Spatial Anchors account to authenticate the session.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-02.png)

<span data-ttu-id="81d39-140">Avviare una sessione di Ancoraggi nello spazio di Azure nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="81d39-140">Start an Azure Spatial Anchors session by:</span></span>
1. <span data-ttu-id="81d39-141">Verificare che nell'applicazione HoloLens sia in esecuzione un'istanza di **AR Session** (Sessione AR) poiché la sessione di Ancoraggi nello spazio di Azure non può essere avviata fino a quando non è in esecuzione una sessione AR.</span><span class="sxs-lookup"><span data-stu-id="81d39-141">Checking that an **AR Session** is running in the HoloLens application, as the Azure Spatial Anchors session can't start until an AR Session is running.</span></span> <span data-ttu-id="81d39-142">[Creare un asset di sessione AR](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset) se non ne è stato configurato nessuno.</span><span class="sxs-lookup"><span data-stu-id="81d39-142">If you don't have one setup, [create an AR Session asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>
2. <span data-ttu-id="81d39-143">Aggiungere l'evento personalizzato **Start Azure Spatial Anchors Session** (Avvia sessione di Ancoraggi nello spazio di Azure) e configurarlo nel modo illustrato nello screenshot seguente.</span><span class="sxs-lookup"><span data-stu-id="81d39-143">Adding the **Start Azure Spatial Anchors Session** custom event and configure it as shown in the screenshot below.</span></span>
    * <span data-ttu-id="81d39-144">La creazione di una sessione non determina l'avvio della sessione per impostazione predefinita, che consente allo sviluppatore di configurare la sessione per l'autenticazione con il servizio Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-144">Creating a session doesn't start the session by default, which allows the developer to configure the session for authentication with the Azure Spatial Anchors service.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. <span data-ttu-id="81d39-146">Configurare la sessione di Ancoraggi nello spazio di Azure per specificare **ID account** e **Chiave dell'account**.</span><span class="sxs-lookup"><span data-stu-id="81d39-146">Configure the Azure Spatial Anchors session to provide the **Account ID** and **Account Key**.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. <span data-ttu-id="81d39-148">Avviare la sessione di Ancoraggi nello spazio di Azure, consentendo all'applicazione di creare e individuare Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-148">Start the Azure Spatial Anchors session, allowing the application to create and locate Azure Spatial Anchors.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-05.png)

<span data-ttu-id="81d39-150">Quando non si usa più il servizio, è consigliabile pulire le risorse di Ancoraggi nello spazio di Azure presenti nel progetto Event Graph (Grafico eventi):</span><span class="sxs-lookup"><span data-stu-id="81d39-150">It's good practice to clean up Azure Spatial Anchors resources in your Event Graph blueprint when you're no longer using the service:</span></span>

1. <span data-ttu-id="81d39-151">Arrestare la sessione di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-151">Stop the Azure Spatial Anchors session.</span></span> <span data-ttu-id="81d39-152">La sessione non sarà più in esecuzione, ma le risorse associate saranno ancora presenti nel plug-in di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-152">The session will no longer be running, but its associated resources will still exist in the Azure Spatial Anchors plugin.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. <span data-ttu-id="81d39-154">Eliminare la sessione di Ancoraggi nello spazio di Azure per eseguire la pulizia di tutte le risorse della sessione ancora note al plug-in di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-154">Destroy the Azure Spatial Anchors session to clean up any Azure Spatial Anchors session resources still known to the Azure Spatial Anchors plugin.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-07.png)

<span data-ttu-id="81d39-156">Il progetto Event Graph (Grafico eventi) dovrebbe avere un aspetto simile allo screenshot seguente:</span><span class="sxs-lookup"><span data-stu-id="81d39-156">Your Event Graph blueprint should look like the screenshot below:</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-08.png)


## <a name="creating-an-anchor"></a><span data-ttu-id="81d39-158">Creazione di un ancoraggio</span><span class="sxs-lookup"><span data-stu-id="81d39-158">Creating an anchor</span></span>
<span data-ttu-id="81d39-159">Un ancoraggio nello spazio di Azure rappresenta una posa del mondo fisico nello spazio della applicazione di realtà aumentata, che blocca il contenuto della realtà aumentata nelle posizioni del mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="81d39-159">An Azure Spatial Anchor represents a physical world pose in the augmented reality application space, which locks augmented reality content to locations in the physical world.</span></span> <span data-ttu-id="81d39-160">È anche possibile condividere Ancoraggi nello spazio di Azure tra diversi utenti.</span><span class="sxs-lookup"><span data-stu-id="81d39-160">Azure Spatial Anchors can also be shared among different users.</span></span> <span data-ttu-id="81d39-161">Questa condivisione consente al contenuto della realtà aumentata progettato su dispositivi diversi di essere posizionato come nel mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="81d39-161">This sharing allows augmented reality content drawn on different devices to be positioned in the same location in the physical world.</span></span> 

<span data-ttu-id="81d39-162">Per creare un nuovo ancoraggio nello spazio di Azure:</span><span class="sxs-lookup"><span data-stu-id="81d39-162">To create a new Azure Spatial Anchor:</span></span>
1. <span data-ttu-id="81d39-163">Verificare che sia in esecuzione una sessione di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-163">Check that an Azure Spatial Anchors session is running.</span></span> <span data-ttu-id="81d39-164">L'applicazione non può creare o salvare in modo permanente un ancoraggio nello spazio di Azure quando non è in esecuzione alcuna sessione di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-164">The application can't create or persist an Azure Spatial Anchor when no Azure Spatial Anchors session is running.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. <span data-ttu-id="81d39-166">Creare oppure ottenere un **[componente scena](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** di Unreal di cui deve essere salvata la posizione in modo permanente.</span><span class="sxs-lookup"><span data-stu-id="81d39-166">Create or obtain an Unreal **[Scene Component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** that should have its location persisted.</span></span> 
    * <span data-ttu-id="81d39-167">Nell'immagine seguente il componente **Scene Component Needing Anchor** (Componente scena con necessità di ancoraggio) viene usato come variabile.</span><span class="sxs-lookup"><span data-stu-id="81d39-167">In the below image, the **Scene Component Needing Anchor** component is used as a variable.</span></span> <span data-ttu-id="81d39-168">È necessario un componente scena Unreal per stabilire una trasformazione globale dell'applicazione per un [segnaposto AR](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) e un ancoraggio nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-168">An Unreal Scene Component is needed to establish an application world transform for an [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) and Azure Spatial Anchor.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-10.png)

<span data-ttu-id="81d39-170">Per costruire e salvare un ancoraggio nello spazio di Azure per un componente scena Unreal:</span><span class="sxs-lookup"><span data-stu-id="81d39-170">To construct and save an Azure Spatial Anchor for an Unreal Scene Component:</span></span>
1. <span data-ttu-id="81d39-171">Chiamare [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) (Componente segnaposto) per il componente scena Unreal e specificare **World Transform** (Trasformazione globale) come trasformazione globale usata per il segnaposto AR.</span><span class="sxs-lookup"><span data-stu-id="81d39-171">Call the [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) for the Unreal Scene Component and specify the Scene Component's **World Transform** as the World Transform used for the AR Pin.</span></span>
    * <span data-ttu-id="81d39-172">Unreal tiene traccia dei punti AR nello spazio dell'applicazione con i segnaposto AR, usati per creare un ancoraggio nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-172">Unreal tracks AR points in the application space using AR Pins, which are used to create an Azure Spatial Anchor.</span></span> <span data-ttu-id="81d39-173">In Unreal un segnaposto AR è analogo a un ancoraggio nello spazio di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="81d39-173">In Unreal, an AR Pin is analogous to a SpatialAnchor on HoloLens.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. <span data-ttu-id="81d39-175">Chiamare **Create Cloud Anchor** (Crea ancoraggio cloud) usando il segnaposto AR appena creato.</span><span class="sxs-lookup"><span data-stu-id="81d39-175">Call **Create Cloud Anchor** using the newly created AR Pin.</span></span>
    * <span data-ttu-id="81d39-176">La chiamata a Create Cloud Anchor (Crea ancoraggio cloud) consente di creare un ancoraggio nello spazio di Azure in locale, ma non nel servizio Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-176">Create Cloud Anchor creates an Azure Spatial Anchor locally but not in the Azure Spatial Anchor service.</span></span> <span data-ttu-id="81d39-177">È possibile impostare i parametri relativi all'ancoraggio nello spazio di Azure, ad esempio una data di scadenza, prima di creare l'ancoraggio nello spazio di Azure con il servizio.</span><span class="sxs-lookup"><span data-stu-id="81d39-177">Parameters for the Azure Spatial Anchor, such as an expiration date, can be set before creating the Azure Spatial Anchor with the service.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. <span data-ttu-id="81d39-179">Impostare la scadenza dell'ancoraggio nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-179">Set the Azure Spatial Anchor expiration.</span></span> <span data-ttu-id="81d39-180">Il parametro Lifetime (Durata) di questa funzione consente allo sviluppatore di specificare l'intervallo di tempo in secondi durante il quale l'ancoraggio deve essere mantenuto dal servizio.</span><span class="sxs-lookup"><span data-stu-id="81d39-180">This function's Lifetime parameter allows the developer to specify in seconds how long the anchor should be maintained by the service.</span></span>
    * <span data-ttu-id="81d39-181">Ad esempio, per una durata di una settimana è richiesto un valore di 60 secondi x 60 minuti x 24 ore x sette giorni = 604.800 secondi.</span><span class="sxs-lookup"><span data-stu-id="81d39-181">For example, a week long expiration would take a value of 60 seconds x 60 minutes x 24 hours x seven days = 604,800 seconds.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-13.png)

<span data-ttu-id="81d39-183">Dopo aver impostato i parametri di ancoraggio, dichiarare l'ancoraggio come pronto per il salvataggio.</span><span class="sxs-lookup"><span data-stu-id="81d39-183">After setting anchor parameters, declare the anchor as ready to save.</span></span> <span data-ttu-id="81d39-184">Nell'esempio seguente, l'ancoraggio nello spazio di Azure appena creato viene aggiunto a un set di ancoraggi nello spazio di Azure per i quali è necessario eseguire il salvataggio.</span><span class="sxs-lookup"><span data-stu-id="81d39-184">In the example below, the newly created Azure Spatial Anchor is added to a set of Azure Spatial Anchors needing saving.</span></span> <span data-ttu-id="81d39-185">Questo set viene dichiarato come variabile per il progetto Pawn.</span><span class="sxs-lookup"><span data-stu-id="81d39-185">This set is declared as a variable for the Pawn blueprint.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a><span data-ttu-id="81d39-187">Salvataggio di un ancoraggio</span><span class="sxs-lookup"><span data-stu-id="81d39-187">Saving an Anchor</span></span>

<span data-ttu-id="81d39-188">Dopo aver configurato l'ancoraggio nello spazio di Azure con i parametri, chiamare **Save Cloud Anchor** (Salva ancoraggio cloud).</span><span class="sxs-lookup"><span data-stu-id="81d39-188">After configuring the Azure Spatial Anchor with your parameters, call **Save Cloud Anchor**.</span></span> <span data-ttu-id="81d39-189">La chiamata a Save Cloud Anchor (Salva ancoraggio cloud) dichiara l'ancoraggio al servizio Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-189">Save Cloud Anchor declares the anchor to the Azure Spatial Anchors service.</span></span> <span data-ttu-id="81d39-190">Se la chiamata a Save Cloud Anchor (Salva ancoraggio cloud) ha esito positivo, l'ancoraggio nello spazio di Azure sarà disponibile per altri utenti del servizio Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-190">When the call to Save Cloud Anchor succeeds, the Azure Spatial Anchor is available to other users of the Azure Spatial Anchor service.</span></span>  

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> <span data-ttu-id="81d39-192">Save Cloud Anchor (Salva ancoraggio cloud) è una funzione asincrona e può essere chiamata solo in un evento thread di gioco, ad esempio **EventTick**.</span><span class="sxs-lookup"><span data-stu-id="81d39-192">Save Cloud Anchor is an asynchronous function and can only be called on a game thread event such as **EventTick**.</span></span> <span data-ttu-id="81d39-193">È possibile che Save Cloud Anchor (Salva ancoraggio cloud) non venga visualizzata come funzione disponibile tra le funzioni di progetto personalizzate.</span><span class="sxs-lookup"><span data-stu-id="81d39-193">Save Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="81d39-194">Dovrebbe essere disponibile, tuttavia, nell'editor del progetto Pawn Event Graph (Grafico eventi Pawn).</span><span class="sxs-lookup"><span data-stu-id="81d39-194">However, it should be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="81d39-195">Nell'esempio seguente l'ancoraggio nello spazio di Azure viene archiviato in un set durante un callback dell'evento di input.</span><span class="sxs-lookup"><span data-stu-id="81d39-195">In the example below, the Azure Spatial Anchor is stored in a set during an input event callback.</span></span> <span data-ttu-id="81d39-196">L'ancoraggio viene quindi salvato in EventTick.</span><span class="sxs-lookup"><span data-stu-id="81d39-196">The anchor is then saved on the EventTick.</span></span> <span data-ttu-id="81d39-197">Per salvare un ancoraggio nello spazio di Azure, possono essere necessari più tentativi a seconda della quantità di dati spaziali creati dalla sessione di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-197">Saving an Azure Spatial Anchor may take multiple attempts depending on the amount of spatial data that your Azure Spatial Anchors session has created.</span></span> <span data-ttu-id="81d39-198">Per questo motivo è consigliabile controllare se la chiamata di salvataggio ha avuto esito positivo.</span><span class="sxs-lookup"><span data-stu-id="81d39-198">That's why it's a good idea to check whether the save call succeeded.</span></span>

<span data-ttu-id="81d39-199">Se l'ancoraggio non viene salvato, aggiungerlo nuovamente al set di ancoraggi ancora da salvare.</span><span class="sxs-lookup"><span data-stu-id="81d39-199">If the anchor doesn't save, re-add it to the set of anchors still needing to be saved.</span></span> <span data-ttu-id="81d39-200">EventTick futuri tenteranno di salvare l'ancoraggio fino a quando non viene archiviato nel servizio Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-200">Future EventTicks will try to save the anchor until it's successfully stored in the Azure Spatial Anchor service.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-16.png)

<span data-ttu-id="81d39-202">Dopo il salvataggio dell'ancoraggio, è possibile usare la trasformazione dei segnaposto AR come trasformazione di riferimento per inserire contenuto nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="81d39-202">Once the anchor saves, you can use the AR Pins' transform as a reference transform for placing content in the application.</span></span> <span data-ttu-id="81d39-203">Altri utenti possono rilevare questo ancoraggio e allineare il contenuto AR per dispositivi diversi nel mondo fisico.</span><span class="sxs-lookup"><span data-stu-id="81d39-203">Other users can detect this anchor and align AR content for different devices in the physical world.</span></span>

## <a name="deleting-an-anchor"></a><span data-ttu-id="81d39-204">Eliminazione di un ancoraggio</span><span class="sxs-lookup"><span data-stu-id="81d39-204">Deleting an Anchor</span></span>

<span data-ttu-id="81d39-205">È possibile eliminare gli ancoraggi dal servizio Ancoraggi nello spazio di Azure chiamando **Delete Cloud Anchor** (Elimina ancoraggio cloud).</span><span class="sxs-lookup"><span data-stu-id="81d39-205">You can delete anchors from the Azure Spatial Anchor service by calling **Delete Cloud Anchor**.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> <span data-ttu-id="81d39-207">Delete Cloud Anchor (Elimina ancoraggio cloud) è una funzione latente e può essere chiamata solo nel caso di un evento thread di gioco, ad esempio EventTick.</span><span class="sxs-lookup"><span data-stu-id="81d39-207">Delete Cloud Anchor is a latent function and can only be called on a game thread event, such as EventTick.</span></span> <span data-ttu-id="81d39-208">È possibile che Delete Cloud Anchor (Elimina ancoraggio cloud) non venga visualizzata come funzione disponibile tra le funzioni di progetto personalizzate.</span><span class="sxs-lookup"><span data-stu-id="81d39-208">Delete Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="81d39-209">Dovrebbe essere disponibile, tuttavia, nell'editor del progetto Pawn Event Graph (Grafico eventi Pawn).</span><span class="sxs-lookup"><span data-stu-id="81d39-209">It should however be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="81d39-210">Nell'esempio seguente l'ancoraggio viene contrassegnato per l'eliminazione in un evento di input personalizzato.</span><span class="sxs-lookup"><span data-stu-id="81d39-210">In the example below, the anchor is flagged for deletion on a custom input event.</span></span> <span data-ttu-id="81d39-211">L'eliminazione viene quindi tentata in EventTick.</span><span class="sxs-lookup"><span data-stu-id="81d39-211">The deletion is then attempted on the EventTick.</span></span> <span data-ttu-id="81d39-212">Se l'eliminazione dell'ancoraggio non riesce, aggiungere l'ancoraggio nello spazio di Azure al set di ancoraggi contrassegnati per l'eliminazione e riprovare in EventTick successivi.</span><span class="sxs-lookup"><span data-stu-id="81d39-212">If the anchor deletion fails, add the Azure Spatial Anchor to the set of anchors flagged for deletion and tries again on later EventTicks.</span></span>

<span data-ttu-id="81d39-213">Il progetto Event Graph (Grafico eventi) dovrebbe ora avere un aspetto simile allo screenshot seguente:</span><span class="sxs-lookup"><span data-stu-id="81d39-213">Your Event Graph blueprint should now look like the screenshot below:</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a><span data-ttu-id="81d39-215">Individuazione di ancoraggi preesistenti</span><span class="sxs-lookup"><span data-stu-id="81d39-215">Locating pre-existing anchors</span></span>

<span data-ttu-id="81d39-216">Oltre a creare ancoraggi nello spazio di Azure, è possibile rilevare ancoraggi creati da peer con il servizio Ancoraggi nello spazio di Azure:</span><span class="sxs-lookup"><span data-stu-id="81d39-216">In addition to creating Azure Spatial Anchors, you can detect anchors created by peers with the Azure Spatial Anchors service:</span></span>

1. <span data-ttu-id="81d39-217">Ottenere un identificatore di ancoraggio nello spazio di Azure per l'ancoraggio da rilevare.</span><span class="sxs-lookup"><span data-stu-id="81d39-217">Obtain an Azure Spatial Anchor identifier for the anchor that you would like to detect.</span></span>
    * <span data-ttu-id="81d39-218">È possibile ottenere un identificatore per un ancoraggio creato dallo stesso dispositivo in una precedente sessione di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-218">An anchor identifier can be obtained for an anchor created by the same device in a previous Azure Spatial Anchors session.</span></span> <span data-ttu-id="81d39-219">Può anche essere creato e condiviso da dispositivi peer che interagiscono con il servizio Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-219">It can also be created and shared by peer devices interacting with the Azure Spatial Anchors service.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. <span data-ttu-id="81d39-221">Aggiungere un componente **AzureSpatialAnchorsEvent** al progetto Pawn.</span><span class="sxs-lookup"><span data-stu-id="81d39-221">Add an **AzureSpatialAnchorsEvent** component to your Pawn blueprint.</span></span>
    * <span data-ttu-id="81d39-222">Questo componente consente di effettuare la sottoscrizione a diversi eventi di Ancoraggi nello spazio di Azure, ad esempio eventi chiamati quando vengono individuati gli ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-222">This component allows you to subscribe to various Azure Spatial Anchors events, such as events called when Azure Spatial Anchors are located.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. <span data-ttu-id="81d39-224">Effettuare la sottoscrizione ad **ASAAnchor Located Delegate** per il componente **AzureSpatialAnchorsEvent**.</span><span class="sxs-lookup"><span data-stu-id="81d39-224">Subscribe to the **ASAAnchor Located Delegate** for the **AzureSpatialAnchorsEvent** component.</span></span>
    * <span data-ttu-id="81d39-225">Il delegato consente all'applicazione di stabilire quando sono stati individuati nuovi ancoraggi associati all'account di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-225">The delegate lets the application know when new anchors associated with the Azure Spatial Anchors account have been located.</span></span>
    * <span data-ttu-id="81d39-226">Con il callback dell'evento, gli ancoraggi nello spazio di Azure creati dai peer con la sessione di Ancoraggi nello spazio di Azure non avranno segnaposto AR creati per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="81d39-226">With the event callback, Azure Spatial Anchors created by peers using the Azure Spatial Anchors session won't have AR Pins created by default.</span></span> <span data-ttu-id="81d39-227">Per creare un segnaposto AR per l'ancoraggio nello spazio di Azure rilevato, gli sviluppatori possono chiamare la funzione **Create ARPin Around Azure Cloud Spatial Anchor** (Crea segnaposto AR attorno all'ancoraggio nello spazio cloud di Azure).</span><span class="sxs-lookup"><span data-stu-id="81d39-227">To create an AR Pin for the detected Azure Spatial Anchor, developers can call **Create ARPin Around Azure Cloud Spatial Anchor**.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-20.png)

<span data-ttu-id="81d39-229">Per individuare gli ancoraggi nello spazio di Azure creati dai peer con il servizio Ancoraggi nello spazio di Azure, l'applicazione dovrà creare un elemento **Azure Spatial Anchors Watcher** (Watcher ancoraggi nello spazio di Azure):</span><span class="sxs-lookup"><span data-stu-id="81d39-229">In order to locate Azure Spatial Anchors created by peers using the Azure Spatial Anchor service, the application will have to create an **Azure Spatial Anchors Watcher**:</span></span>
1. <span data-ttu-id="81d39-230">Verificare che sia in esecuzione una sessione di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="81d39-230">Check that an Azure Spatial Anchors session is running.</span></span>
2. <span data-ttu-id="81d39-231">Creare **AzureSpatialAnchorsLocateCriteria**.</span><span class="sxs-lookup"><span data-stu-id="81d39-231">Create an **AzureSpatialAnchorsLocateCriteria**.</span></span>
    * <span data-ttu-id="81d39-232">È possibile specificare diversi parametri di posizione, ad esempio la distanza dall'utente o la distanza da un altro ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="81d39-232">You can specify various location parameters like distance from the user or distance from another anchor.</span></span>
3. <span data-ttu-id="81d39-233">Dichiarare in **AzureSpatialAnchorsLocateCritieria** l'identificatore di ancoraggio nello spazio di Azure desiderato.</span><span class="sxs-lookup"><span data-stu-id="81d39-233">Declare your desired Azure Spatial Anchor identifier in the **AzureSpatialAnchorsLocateCritieria**.</span></span>
4. <span data-ttu-id="81d39-234">Chiamare **Create Watcher** (Crea Watcher).</span><span class="sxs-lookup"><span data-stu-id="81d39-234">Call **Create Watcher**.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-21.png)

<span data-ttu-id="81d39-236">L'applicazione ora inizia a cercare gli ancoraggi nello spazio di Azure noti al servizio Ancoraggi nello spazio di Azure. In altre parole, gli utenti possono individuare gli ancoraggi nello spazio di Azure creati dai relativi peer.</span><span class="sxs-lookup"><span data-stu-id="81d39-236">The application now begins looking for Azure Spatial Anchors known to the Azure Spatial Anchors service, meaning that users can locate Azure Spatial Anchors created by their peers.</span></span>

<span data-ttu-id="81d39-237">Dopo aver individuato l'ancoraggio nello spazio di Azure, chiamare **Stop Watcher** (Arresta Watcher) per arrestare Azure Spatial Anchors Watcher (Watcher ancoraggi nello spazio di Azure) e pulire le risorse Watcher.</span><span class="sxs-lookup"><span data-stu-id="81d39-237">After locating the Azure Spatial Anchor, call **Stop Watcher** to stop the Azure Spatial Anchors Watcher and clean up watcher resources.</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-22.png)

<span data-ttu-id="81d39-239">Il progetto Event Graph (Grafico eventi) finale dovrebbe ora avere un aspetto simile allo screenshot seguente:</span><span class="sxs-lookup"><span data-stu-id="81d39-239">Your final Event Graph blueprint should now look like the screenshot below:</span></span>

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-23.png)

## <a name="next-development-checkpoint"></a><span data-ttu-id="81d39-241">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="81d39-241">Next Development Checkpoint</span></span>

<span data-ttu-id="81d39-242">Se si segue il percorso di checkpoint per lo sviluppo con Unreal che è stato delineato, si stanno esplorando i blocchi predefiniti fondamentali di MRTK.</span><span class="sxs-lookup"><span data-stu-id="81d39-242">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="81d39-243">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="81d39-243">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="81d39-244">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="81d39-244">Spatial mapping</span></span>](unreal-spatial-mapping.md)

<span data-ttu-id="81d39-245">In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="81d39-245">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="81d39-246">Fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="81d39-246">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="81d39-247">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="81d39-247">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="next-steps"></a><span data-ttu-id="81d39-248">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="81d39-248">Next steps</span></span>
* [<span data-ttu-id="81d39-249">Ancoraggi nello spazio locali</span><span class="sxs-lookup"><span data-stu-id="81d39-249">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="81d39-250">Documentazione di Ancoraggi nello spazio</span><span class="sxs-lookup"><span data-stu-id="81d39-250">Spatial Anchors documentation</span></span>](https://docs.microsoft.com/azure/spatial-anchors/)
* [<span data-ttu-id="81d39-251">Funzionalità di Ancoraggi nello spazio</span><span class="sxs-lookup"><span data-stu-id="81d39-251">Spatial Anchor features</span></span>](https://azure.microsoft.com/services/spatial-anchors/#features)
* [<span data-ttu-id="81d39-252">Linee guida per un'esperienza efficace di gestione degli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="81d39-252">Effective anchor experience guidelines</span></span>](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)