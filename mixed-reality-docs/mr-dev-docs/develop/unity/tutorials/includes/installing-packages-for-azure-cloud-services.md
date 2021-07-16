---
ms.openlocfilehash: 7cd9400ddb83b95f145a9b962be51aaed30df47b
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224464"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="b6c81-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="b6c81-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="b6c81-102">Nel menu Unity selezionare **Finestra** Gestione pacchetti per aprire la finestra Gestione pacchetti, quindi verificare che sia installata la versione  >   di **AR Foundation**  >  **4.1.7.**</span><span class="sxs-lookup"><span data-stu-id="b6c81-102">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then verify that **AR Foundation** > **4.1.7** version is installed.</span></span>

![Package Manager di Unity con AR Foundation selezionato](../images/mr-learning-asa/asa-02-section3-step1-1-OpenXR.png)

> [!NOTE]
> <span data-ttu-id="b6c81-104">Stai installando il pacchetto AR Foundation perché è richiesto da Azure Spatial Anchors SDK, che verrà importato nella sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="b6c81-104">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="b6c81-105">Importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="b6c81-105">Importing the tutorial assets</span></span>

<span data-ttu-id="b6c81-106">Aggiungere AzurespatialAnchors SDK V2.10 al progetto. Per aggiungere i pacchetti, seguire questa [esercitazione](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span><span class="sxs-lookup"><span data-stu-id="b6c81-106">Add AzurespatialAnchors SDK V2.10 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="b6c81-107">Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:</span><span class="sxs-lookup"><span data-stu-id="b6c81-107">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="b6c81-108">AzureStorageForUnity.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b6c81-108">AzureStorageForUnity.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [<span data-ttu-id="b6c81-109">MRTK. Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b6c81-109">MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage)

<span data-ttu-id="b6c81-110">Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="b6c81-110">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Finestre Hierarchy, Scene e Project di Unity dopo l'importazione degli asset dell'esercitazione](../images/mr-learning-azure/tutorial1-section4-step1-1-OpenXR.png)

> [!TIP]
> <span data-ttu-id="b6c81-112">Per un promemoria su come importare un pacchetto personalizzato unity, è possibile fare riferimento alle istruzioni sull'importazione della realtà [mista Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets)   istruzioni.</span><span class="sxs-lookup"><span data-stu-id="b6c81-112">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

# <a name="unity-2020--windows-xr-plugin"></a>[<span data-ttu-id="b6c81-113">Unity 2020 + Windows plug-in XR</span><span class="sxs-lookup"><span data-stu-id="b6c81-113">Unity 2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="b6c81-114">Nel menu Unity selezionare **Window** Gestione pacchetti per aprire la finestra Gestione pacchetti, quindi  >   selezionare AR Foundation > **versione 4.0.12** e fare clic sul pulsante **Installa** per installare il pacchetto:</span><span class="sxs-lookup"><span data-stu-id="b6c81-114">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation > 4.0.12** version and click the **Install** button to install the package:</span></span>

![Package Manager di Unity con AR Foundation selezionato](../images/mr-learning-asa/asa-02-section3-step1-1-XRSDK.png)

> [!NOTE]
> <span data-ttu-id="b6c81-116">Stai installando il pacchetto AR Foundation perché è richiesto da Azure Spatial Anchors SDK, che verrà importato nella sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="b6c81-116">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="b6c81-117">Importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="b6c81-117">Importing the tutorial assets</span></span>

<span data-ttu-id="b6c81-118">Aggiungere AzurespatialAnchors SDK V2.10 al progetto. Per aggiungere i pacchetti, seguire questa [esercitazione](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span><span class="sxs-lookup"><span data-stu-id="b6c81-118">Add AzurespatialAnchors SDK V2.10 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="b6c81-119">Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:</span><span class="sxs-lookup"><span data-stu-id="b6c81-119">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="b6c81-120">AzureStorageForUnity.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b6c81-120">AzureStorageForUnity.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [<span data-ttu-id="b6c81-121">MRTK. Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b6c81-121">MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage)

<span data-ttu-id="b6c81-122">Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="b6c81-122">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Finestre Hierarchy, Scene e Project di Unity dopo l'importazione degli asset dell'esercitazione](../images/mr-learning-azure/tutorial1-section4-step1-1-XRSDK.png)

> [!TIP]
> <span data-ttu-id="b6c81-124">Per un promemoria su come importare un pacchetto personalizzato unity, è possibile fare riferimento alle istruzioni sull'importazione della realtà [mista Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets)   istruzioni.</span><span class="sxs-lookup"><span data-stu-id="b6c81-124">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="b6c81-125">Legacy WSA</span><span class="sxs-lookup"><span data-stu-id="b6c81-125">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="b6c81-126">Nel menu Unity selezionare **Window** Gestione pacchetti per aprire la finestra Gestione pacchetti, quindi  >   selezionare AR Foundation > **versione 3.1.3** e fare clic sul pulsante **Installa** per installare il pacchetto:</span><span class="sxs-lookup"><span data-stu-id="b6c81-126">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation > 3.1.3** version and click the **Install** button to install the package:</span></span>

![Package Manager di Unity con AR Foundation selezionato](../images/mr-learning-asa/asa-02-section3-step1-1-Legacy.png)

> [!NOTE]
> <span data-ttu-id="b6c81-128">Stai installando il pacchetto AR Foundation perché è richiesto da Azure Spatial Anchors SDK, che verrà importato nella sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="b6c81-128">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="b6c81-129">Importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="b6c81-129">Importing the tutorial assets</span></span>

<span data-ttu-id="b6c81-130">Aggiungere AzurespatialAnchors SDK V2.7.2 al progetto. Per aggiungere i pacchetti, seguire questa [esercitazione](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span><span class="sxs-lookup"><span data-stu-id="b6c81-130">Add AzurespatialAnchors SDK V2.7.2 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="b6c81-131">Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:</span><span class="sxs-lookup"><span data-stu-id="b6c81-131">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="b6c81-132">AzureStorageForUnity.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b6c81-132">AzureStorageForUnity.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [<span data-ttu-id="b6c81-133">MRTK. Tutorials.AzureCloudServices.LegacyWSA.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b6c81-133">MRTK.Tutorials.AzureCloudServices.LegacyWSA.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.LegacyWSA.unitypackage)

<span data-ttu-id="b6c81-134">Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="b6c81-134">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Finestre Hierarchy, Scene e Project di Unity dopo l'importazione degli asset dell'esercitazione](../images/mr-learning-azure/tutorial1-section4-step1-1-Legacy.png)

> [!NOTE]
> <span data-ttu-id="b6c81-136">Se vengono visualizzati avvisi CS0618 che indicano che 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' e 'WorldAnchor.GetNativeSpatialAnchorPtr()' sono obsoleti, è possibile ignorare tali avvisi.</span><span class="sxs-lookup"><span data-stu-id="b6c81-136">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' and 'WorldAnchor.GetNativeSpatialAnchorPtr()' being obsolete, you can ignore these warnings.</span></span>

> [!TIP]
> <span data-ttu-id="b6c81-137">Per un promemoria su come importare un pacchetto personalizzato unity, è possibile fare riferimento alle istruzioni sull'importazione della realtà [mista Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets)   istruzioni.</span><span class="sxs-lookup"><span data-stu-id="b6c81-137">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>
