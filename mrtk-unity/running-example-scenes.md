---
title: Esecuzione delle scene di esempio
description: Informazioni su come acquisire e usare le scene di esempio di MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/07/2021
ms.topic: article
keywords: mixed reality toolkit, MRTK, esempi, HoloLens, HoloLens 2, shader, descrizioni comando, interazione con la mano, ritaglio, rettande di selezione, pulsanti, menu a mano, slate, dispositivo di scorrimento
ms.openlocfilehash: 8ba4df237189f0de3bd869bc05bdf7e3c5451490
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111911869"
---
# <a name="example-scenes"></a><span data-ttu-id="22262-104">Scene di esempio</span><span class="sxs-lookup"><span data-stu-id="22262-104">Example scenes</span></span>

<span data-ttu-id="22262-105">MRTK offre diversi tipi di scene di esempio che illustrano le funzionalità e i blocchi predefiniti di MRTK per l'esperienza utente spaziale.</span><span class="sxs-lookup"><span data-stu-id="22262-105">MRTK provides various types of example scenes that demonstrate MRTK's features and building blocks for spatial user experience.</span></span> <span data-ttu-id="22262-106">Sperimentare e analizzare scene di esempio può essere utile per comprendere le funzionalità e applicarle ai progetti.</span><span class="sxs-lookup"><span data-stu-id="22262-106">Experiencing and dissecting example scenes could be helpful to understand the features and apply them to your projects.</span></span> 

## <a name="how-to-acquire-example-scenes"></a><span data-ttu-id="22262-107">Come acquisire scene di esempio</span><span class="sxs-lookup"><span data-stu-id="22262-107">How to acquire example scenes</span></span>

### <a name="using-mixed-reality-feature-tool-and-unity-package-manager"></a><span data-ttu-id="22262-108">Uso di Mixed Reality Feature Tool e gestione pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="22262-108">Using Mixed Reality Feature Tool and Unity package manager</span></span>

<span data-ttu-id="22262-109">È possibile scaricare e importare il **pacchetto di esempi di Mixed Reality Toolkit** tramite mixed reality feature [tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="22262-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="22262-110">In Unity usare il menu **Window > Gestione pacchetti > In Project > Custom (Esempi** di Mixed Reality **Toolkit).**</span><span class="sxs-lookup"><span data-stu-id="22262-110">In Unity, use the menu **Window > Package Manager > In Project > Custom** and select **Mixed Reality Toolkit Examples**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<span data-ttu-id="22262-111">Nell'elenco sul lato destro del pannello fare clic sul pulsante **Import into Project** (Importa nel progetto) accanto ai nomi delle scene di esempio.</span><span class="sxs-lookup"><span data-stu-id="22262-111">From the list on the right side of the panel, click **Import into Project** button next to the example scene names.</span></span>  <span data-ttu-id="22262-112">Ad esempio, è possibile fare **clic sul pulsante** Import into Project (Importa nel progetto) accanto a **Demos - HandTracking (Demo - HandTracking).**</span><span class="sxs-lookup"><span data-stu-id="22262-112">For example, you can click **Import into Project** button next to **Demos - HandTracking**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<span data-ttu-id="22262-113">Dopo l'importazione, sarà possibile trovarli nella **cartella Assets > Samples** ( Esempi).</span><span class="sxs-lookup"><span data-stu-id="22262-113">Once imported, you will be able to find them under **Assets > Samples** folder.</span></span>
<span data-ttu-id="22262-114">**La scena HandInteractionExamples** è un ottimo punto di partenza per iniziare a sperimentare le interazioni spaziali e i blocchi predefiniti dell'interfaccia utente di MRTK.</span><span class="sxs-lookup"><span data-stu-id="22262-114">**HandInteractionExamples** scene is a great place to start experiencing MRTK's spatial interactions and UI building blocks.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

### <a name="directly-downloading-and-importing-packages-from-github"></a><span data-ttu-id="22262-115">Download diretto e importazione di pacchetti da GitHub</span><span class="sxs-lookup"><span data-stu-id="22262-115">Directly downloading and importing packages from GitHub</span></span>

<span data-ttu-id="22262-116">Se non si usa Mixed Reality Feature Tool, è possibile scaricare e importare **direttamente Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** dalla pagina di rilascio di [MRTK in GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span><span class="sxs-lookup"><span data-stu-id="22262-116">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

<span data-ttu-id="22262-117">Usare **Assets > Importa pacchetto > menu Pacchetto personalizzato per** importare il file unitypackage scaricato.</span><span class="sxs-lookup"><span data-stu-id="22262-117">Use **Assets > Import Package > Custom Package** menu to import downloaded .unitypackage.</span></span> <span data-ttu-id="22262-118">Dopo l'importazione, sarà possibile trovare scene di esempio in **Assets > MRTK > Examples > Demos (Esempi > MRTK).**</span><span class="sxs-lookup"><span data-stu-id="22262-118">Once it is imported, you will be able to find example scenes under **Assets > MRTK > Examples > Demos**.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual1.png" width="650" alt="Example Manual 1"><br/>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual2.png" width="650" alt="Example Manual 2"><br/>