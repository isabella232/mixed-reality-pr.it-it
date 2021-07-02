---
title: Scene di esempio
description: Informazioni su come acquisire e usare le scene di esempio di MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/07/2021
ms.topic: article
keywords: mixed reality toolkit, MRTK, examples, HoloLens, HoloLens 2, shaders, tooltips, hand interaction, clipping, bounding boxes, buttons, hand menus, slate, slider
ms.openlocfilehash: d8d2bb40ff1c95e01cb051f36de04beb93829ba1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177470"
---
# <a name="example-scenes"></a><span data-ttu-id="695c8-104">Scene di esempio</span><span class="sxs-lookup"><span data-stu-id="695c8-104">Example scenes</span></span>

<span data-ttu-id="695c8-105">MRTK offre vari tipi di scene di esempio che illustrano le funzionalità di MRTK e i blocchi predefiniti per l'esperienza utente spaziale.</span><span class="sxs-lookup"><span data-stu-id="695c8-105">MRTK provides various types of example scenes that demonstrate MRTK's features and building blocks for spatial user experience.</span></span> <span data-ttu-id="695c8-106">L'esperienza e la sezione di scene di esempio possono essere utili per comprendere le funzionalità e applicarle ai progetti.</span><span class="sxs-lookup"><span data-stu-id="695c8-106">Experiencing and dissecting example scenes could be helpful to understand the features and apply them to your projects.</span></span> 

## <a name="how-to-acquire-example-scenes"></a><span data-ttu-id="695c8-107">Come acquisire scene di esempio</span><span class="sxs-lookup"><span data-stu-id="695c8-107">How to acquire example scenes</span></span>

### <a name="using-mixed-reality-feature-tool-and-unity-package-manager"></a><span data-ttu-id="695c8-108">Uso dello strumento di funzionalità di realtà mista e di Gestione pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="695c8-108">Using Mixed Reality Feature Tool and Unity package manager</span></span>

<span data-ttu-id="695c8-109">È possibile scaricare e importare il pacchetto **Mixed Reality Toolkit Examples** tramite Mixed Reality Feature [Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="695c8-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="695c8-110">In Unity usare il menu **Window > Gestione pacchetti > In Project > e** selezionare Mixed Reality Toolkit **Examples**.</span><span class="sxs-lookup"><span data-stu-id="695c8-110">In Unity, use the menu **Window > Package Manager > In Project > Custom** and select **Mixed Reality Toolkit Examples**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<span data-ttu-id="695c8-111">Nell'elenco a destra del pannello fare clic sul pulsante Importa **in** Project accanto ai nomi delle scene di esempio.</span><span class="sxs-lookup"><span data-stu-id="695c8-111">From the list on the right side of the panel, click **Import into Project** button next to the example scene names.</span></span>  <span data-ttu-id="695c8-112">Ad esempio, è possibile fare **clic sul** pulsante Importa Project accanto a Demo **- HandTracking**.</span><span class="sxs-lookup"><span data-stu-id="695c8-112">For example, you can click **Import into Project** button next to **Demos - HandTracking**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<span data-ttu-id="695c8-113">Dopo l'importazione, sarà possibile trovarli nella cartella **Asset > Samples.**</span><span class="sxs-lookup"><span data-stu-id="695c8-113">Once imported, you will be able to find them under **Assets > Samples** folder.</span></span>
<span data-ttu-id="695c8-114">**La scena HandInteractionExamples** è un ottimo punto per iniziare a sperimentare le interazioni spaziali di MRTK e i blocchi predefiniti dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="695c8-114">**HandInteractionExamples** scene is a great place to start experiencing MRTK's spatial interactions and UI building blocks.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

### <a name="directly-downloading-and-importing-packages-from-github"></a><span data-ttu-id="695c8-115">Download e importazione diretta di pacchetti da GitHub</span><span class="sxs-lookup"><span data-stu-id="695c8-115">Directly downloading and importing packages from GitHub</span></span>

<span data-ttu-id="695c8-116">Se non si usa Mixed Reality Feature Tool, è possibile scaricare e importare **direttamente Microsoft.MixedReality.Toolkit. Unity.Examples.unitypackage** [dalla pagina di GitHub di MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span><span class="sxs-lookup"><span data-stu-id="695c8-116">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

<span data-ttu-id="695c8-117">Usare **Asset > Importa pacchetto >** menu Pacchetto personalizzato per importare il pacchetto unitypackage scaricato.</span><span class="sxs-lookup"><span data-stu-id="695c8-117">Use **Assets > Import Package > Custom Package** menu to import downloaded .unitypackage.</span></span> <span data-ttu-id="695c8-118">Dopo l'importazione, sarà possibile trovare scene di esempio in **Asset > MRTK > Examples > Demos**.</span><span class="sxs-lookup"><span data-stu-id="695c8-118">Once it is imported, you will be able to find example scenes under **Assets > MRTK > Examples > Demos**.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual1.png" width="650" alt="Example Manual 1"><br/>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual2.png" width="650" alt="Example Manual 2"><br/>
