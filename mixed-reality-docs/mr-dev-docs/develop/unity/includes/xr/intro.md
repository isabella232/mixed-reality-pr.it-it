---
ms.openlocfilehash: eaa2651a22fd5b2b601493845d507aeda6745f1a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603717"
---
# <a name="openxr"></a>[<span data-ttu-id="130db-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="130db-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="130db-102">Il plug-in OpenXR di Realtà mista è una raccomandazione **di Microsoft** per **Unity 2020 LTS** o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="130db-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for **Unity 2020 LTS** or later.</span></span> <span data-ttu-id="130db-103">Le nuove funzionalità sviluppate in futuro verranno incluse solo nel plug-in OpenXR di Realtà mista in futuro.</span><span class="sxs-lookup"><span data-stu-id="130db-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="130db-104">Il plug-in OpenXR di realtà mista supporta completamente AR Foundation 4.0, fornendo implementazioni ARPlaneManager e ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="130db-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="130db-105">In questo modo è possibile scrivere codice di raycasting una volta che si estende su HoloLens 2 telefoni e tablet ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="130db-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="130db-106">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="130db-106">Prerequisites</span></span> 

* <span data-ttu-id="130db-107">Strumenti [più recenti per HoloLens 2 sviluppo](../../../install-the-tools.md?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="130db-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="130db-108">Versione più recente di Unity 2020.3 LTS: versione 2020.3.8f1 o successiva</span><span class="sxs-lookup"><span data-stu-id="130db-108">Latest Unity 2020.3 LTS: version 2020.3.8f1 or later</span></span>

### <a name="recommended-package-versions"></a><span data-ttu-id="130db-109">Versioni dei pacchetti consigliate</span><span class="sxs-lookup"><span data-stu-id="130db-109">Recommended package versions</span></span>

<span data-ttu-id="130db-110">Le istruzioni in questa pagina configurano i pacchetti OpenXR Unity di base necessari per distribuire HoloLens 2 o Windows Mixed Reality app:</span><span class="sxs-lookup"><span data-stu-id="130db-110">The instructions in this page will set you up with the core Unity OpenXR packages required to deploy HoloLens 2 or Windows Mixed Reality apps:</span></span>

* <span data-ttu-id="130db-111">Plug-in Unity OpenXR: versione 1.2 o successiva</span><span class="sxs-lookup"><span data-stu-id="130db-111">Unity OpenXR plugin: version 1.2 or later</span></span>
* <span data-ttu-id="130db-112">Plug-in OpenXR di Realtà mista: versione 1.0.0 o successiva</span><span class="sxs-lookup"><span data-stu-id="130db-112">Mixed Reality OpenXR plugin: version 1.0.0 or later</span></span>

<span data-ttu-id="130db-113">Se si usano i pacchetti seguenti nel progetto, è necessario assicurarsi di usare almeno le versioni minime elencate di seguito:</span><span class="sxs-lookup"><span data-stu-id="130db-113">If you use the following packages in your project, you will need to ensure that you use at least the minimum versions listed below:</span></span>

* <span data-ttu-id="130db-114">MRTK: versione 2.7.2 o successiva</span><span class="sxs-lookup"><span data-stu-id="130db-114">MRTK: version 2.7.2 or later</span></span>
* <span data-ttu-id="130db-115">AR Foundation: versione 4.1.1 o successiva</span><span class="sxs-lookup"><span data-stu-id="130db-115">AR Foundation: version 4.1.1 or later</span></span>
* <span data-ttu-id="130db-116">Universal Render Pipeline (URP): versione 10.5.1 o successiva</span><span class="sxs-lookup"><span data-stu-id="130db-116">Universal Render Pipeline (URP): version 10.5.1 or later</span></span>
* <span data-ttu-id="130db-117">Ancoraggi nello stato di Azure: versione 2.10 o successiva</span><span class="sxs-lookup"><span data-stu-id="130db-117">Azure Spatial Anchors: version 2.10 or later</span></span>
* <span data-ttu-id="130db-118">Rendering remoto di Azure: versione 1.0.15 o successiva</span><span class="sxs-lookup"><span data-stu-id="130db-118">Azure Remote Rendering: version 1.0.15 or later</span></span>

> [!NOTE]
> <span data-ttu-id="130db-119">Se si compilano applicazioni di realtà virtuale Windows PC, il plug-in OpenXR di realtà mista non è strettamente necessario.</span><span class="sxs-lookup"><span data-stu-id="130db-119">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not strictly required.</span></span> <span data-ttu-id="130db-120">Tuttavia, è necessario installare il plug-in se si configurano associazioni di input per i controller HP Reverb G2 o si compilano app che funzionano sia su visori VR HoloLens 2 che su visori VR.</span><span class="sxs-lookup"><span data-stu-id="130db-120">However, you'll want to install the plugin if you're setting up input bindings for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="130db-121">Windows Xr</span><span class="sxs-lookup"><span data-stu-id="130db-121">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="130db-122">Microsoft non consiglia di usare il plug-Windows XR per i nuovi progetti in Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="130db-122">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>  <span data-ttu-id="130db-123">È invece consigliabile usare il plug-in OpenXR di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="130db-123">Instead, you should use the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="130db-124">Tuttavia, se si usa Unity 2019 ed è necessario AR Foundation 2.0 per la compatibilità con i dispositivi ARCore/ARKit, questo plug-in abilita tale supporto.</span><span class="sxs-lookup"><span data-stu-id="130db-124">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="130db-125">L'uso di questo plug-in in Unity 2019 non è compatibile con Ancoraggi nello stato di Azure.</span><span class="sxs-lookup"><span data-stu-id="130db-125">Using this plugin in Unity 2019 is not compatible with Azure Spatial Anchors.</span></span>

# <a name="legacy-xr"></a>[<span data-ttu-id="130db-126">XR legacy</span><span class="sxs-lookup"><span data-stu-id="130db-126">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="130db-127">Se si usa ancora **Unity 2019** o versioni precedenti, Microsoft consiglia di usare il supporto **XR legacy incorporato.**</span><span class="sxs-lookup"><span data-stu-id="130db-127">If you're still on **Unity 2019** or earlier, Microsoft recommends using the **Legacy Built-in XR support**.</span></span>

<span data-ttu-id="130db-128">Anche se Windows plug-in XR è funzionante in Unity 2019, non è consigliabile perché questo plug-in non è compatibile con Ancoraggi nello stato di Azure in Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="130db-128">While the Windows XR plugin is functional on Unity 2019, it's not recommended because this plugin is not compatible with Azure Spatial Anchors on Unity 2019.</span></span>

<span data-ttu-id="130db-129">Se si sta avviando un nuovo progetto, è consigliabile installare [Unity 2020](../../choosing-unity-version.md) e usare il plug-in OpenXR di Realtà mista.</span><span class="sxs-lookup"><span data-stu-id="130db-129">If you're starting a new project, we recommend [installing Unity 2020 instead](../../choosing-unity-version.md) and using the Mixed Reality OpenXR plugin.</span></span>