---
ms.openlocfilehash: 550ad2b9fa92894cdf4dad86def4cd3a9b450fb1
ms.sourcegitcommit: e9a1510984d00dc40ffd39239349e500f5737a0d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113103901"
---
# <a name="openxr"></a>[<span data-ttu-id="ebf2d-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ebf2d-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="ebf2d-102">Il plug-in OpenXR di realtà mista **è la** raccomandazione di Microsoft per Unity 2020 LTS o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ebf2d-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for Unity 2020 LTS or later.</span></span> <span data-ttu-id="ebf2d-103">Poiché le nuove funzionalità verranno sviluppate in futuro, verranno incluse solo nel plug-in OpenXR di realtà mista in futuro.</span><span class="sxs-lookup"><span data-stu-id="ebf2d-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="ebf2d-104">Il plug-in OpenXR di realtà mista supporta completamente AR Foundation 4.0, fornendo implementazioni arPlaneManager e ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="ebf2d-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="ebf2d-105">In questo modo è possibile scrivere codice di raycasting una volta che si estende su HoloLens 2 telefoni e tablet ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="ebf2d-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="ebf2d-106">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="ebf2d-106">Prerequisites</span></span> 

* <span data-ttu-id="ebf2d-107">Strumenti [più recenti per lo HoloLens 2 di sviluppo](../../../install-the-tools.md?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="ebf2d-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="ebf2d-108">Versione più recente di Unity 2020.3 LTS (è consigliabile 2020.3.8f1 o versione precedente)</span><span class="sxs-lookup"><span data-stu-id="ebf2d-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>

### <a name="minimum-versions"></a><span data-ttu-id="ebf2d-109">Versioni minime</span><span class="sxs-lookup"><span data-stu-id="ebf2d-109">Minimum versions</span></span>

<span data-ttu-id="ebf2d-110">Le istruzioni in questa pagina configurano i requisiti più recenti e più recenti di Unity e OpenXR elencati di seguito:</span><span class="sxs-lookup"><span data-stu-id="ebf2d-110">The instructions in this page will set you up with the latest and greatest Unity and OpenXR requirements listed below:</span></span>

* <span data-ttu-id="ebf2d-111">Plug-in Unity OpenXR più recente (è consigliabile usare la versione 1.2 o successiva)</span><span class="sxs-lookup"><span data-stu-id="ebf2d-111">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="ebf2d-112">Plug-in OpenXR di realtà mista più recente (è consigliabile la versione 1.0.0 o successiva)</span><span class="sxs-lookup"><span data-stu-id="ebf2d-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0 or later)</span></span>
* <span data-ttu-id="ebf2d-113">Se il progetto usa MRTK, è consigliabile usare la versione 2.7.2 o successiva</span><span class="sxs-lookup"><span data-stu-id="ebf2d-113">If your project uses MRTK, we recommend version 2.7.2 or later</span></span>
* <span data-ttu-id="ebf2d-114">Se il progetto usa un pacchetto URP (Universal Render Pipeline), è consigliabile usare la versione 10.5.1 o successiva</span><span class="sxs-lookup"><span data-stu-id="ebf2d-114">If your project uses Universal Render Pipeline (URP) package, we recommend version 10.5.1 or later</span></span>

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> <span data-ttu-id="ebf2d-115">Se si compilano applicazioni VR su PC Windows, il plug-in OpenXR di realtà mista non è necessariamente necessario.</span><span class="sxs-lookup"><span data-stu-id="ebf2d-115">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="ebf2d-116">Tuttavia, è necessario installare il plug-in se si personalizza il mapping del controller per i controller HP Reverb G2 o si compilano app che funzionano sia su visori HoloLens 2 che vr.</span><span class="sxs-lookup"><span data-stu-id="ebf2d-116">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="ebf2d-117">Windows XR</span><span class="sxs-lookup"><span data-stu-id="ebf2d-117">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="ebf2d-118">Microsoft non consiglia di usare il plug-in Windows XR per i nuovi progetti in Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="ebf2d-118">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>

<span data-ttu-id="ebf2d-119">Tuttavia, se si usa Unity 2019 ed è necessario AR Foundation 2.0 per la compatibilità con i dispositivi ARCore/ARKit, questo plug-in abilita tale supporto.</span><span class="sxs-lookup"><span data-stu-id="ebf2d-119">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ebf2d-120">L'uso di questo plug-in in Unity 2019 non supporta Ancoraggi nello stato di Azure.</span><span class="sxs-lookup"><span data-stu-id="ebf2d-120">Using this plugin in Unity 2019 doesn't support Azure Spatial Anchors.</span></span> 

# <a name="legacy-xr"></a>[<span data-ttu-id="ebf2d-121">XR legacy</span><span class="sxs-lookup"><span data-stu-id="ebf2d-121">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="ebf2d-122">Se si usa ancora Unity 2019 o versioni precedenti, Microsoft consiglia di usare il supporto XR incorporato legacy.</span><span class="sxs-lookup"><span data-stu-id="ebf2d-122">If you're still on Unity 2019 or earlier, Microsoft recommends using the Legacy Built-in XR support.</span></span> <span data-ttu-id="ebf2d-123">Anche se il plug-in Windows XR è funzionante in Unity 2019, non è consigliabile perché Ancoraggi nello spaziali di Azure non è supportato.</span><span class="sxs-lookup"><span data-stu-id="ebf2d-123">While the Windows XR plugin is functional on Unity 2019, it's not recommended because Azure Spatial Anchors isn't supported.</span></span>