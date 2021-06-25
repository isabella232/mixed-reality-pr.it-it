---
ms.openlocfilehash: d39f6032eaf9a59ca52a6e7ae9b8e4d227175738
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906943"
---
# <a name="openxr"></a>[<span data-ttu-id="459d8-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="459d8-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="459d8-102">Il plug-in OpenXR di realtà mista **è la** raccomandazione di Microsoft per Unity 2020 LTS o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="459d8-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for Unity 2020 LTS or later.</span></span> <span data-ttu-id="459d8-103">Poiché le nuove funzionalità verranno sviluppate in futuro, verranno incluse solo nel plug-in OpenXR di realtà mista in futuro.</span><span class="sxs-lookup"><span data-stu-id="459d8-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="459d8-104">Il plug-in OpenXR di realtà mista supporta completamente AR Foundation 4.0, fornendo implementazioni arPlaneManager e ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="459d8-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="459d8-105">In questo modo è possibile scrivere codice di raycasting una volta che si estende su HoloLens 2 telefoni e tablet ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="459d8-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="459d8-106">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="459d8-106">Prerequisites</span></span> 

* <span data-ttu-id="459d8-107">Strumenti [più recenti per lo HoloLens 2 di sviluppo](../../../install-the-tools.md?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="459d8-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="459d8-108">Versione più recente di Unity 2020.3 LTS (è consigliabile 2020.3.8f1 o versione precedente)</span><span class="sxs-lookup"><span data-stu-id="459d8-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>

### <a name="minimum-versions"></a><span data-ttu-id="459d8-109">Versioni minime</span><span class="sxs-lookup"><span data-stu-id="459d8-109">Minimum versions</span></span>

<span data-ttu-id="459d8-110">Le istruzioni in questa pagina configurano i requisiti più recenti e più recenti di Unity e OpenXR elencati di seguito:</span><span class="sxs-lookup"><span data-stu-id="459d8-110">The instructions in this page will set you up with the latest and greatest Unity and OpenXR requirements listed below:</span></span>

* <span data-ttu-id="459d8-111">Plug-in Unity OpenXR più recente (è consigliabile usare la versione 1.2 o successiva)</span><span class="sxs-lookup"><span data-stu-id="459d8-111">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="459d8-112">Plug-in OpenXR di realtà mista più recente (è consigliabile la versione 1.0.0 o successiva)</span><span class="sxs-lookup"><span data-stu-id="459d8-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0 or later)</span></span>
* <span data-ttu-id="459d8-113">**(Facoltativo)** MRTK più recente (è consigliabile la versione 2.7 o successiva)</span><span class="sxs-lookup"><span data-stu-id="459d8-113">**(Optional)** Latest MRTK, (we recommend version 2.7 or later)</span></span>
* <span data-ttu-id="459d8-114">**(Facoltativo)** Pacchetto universal render pipeline più recente (è consigliabile la versione 10.5.1 o successiva)</span><span class="sxs-lookup"><span data-stu-id="459d8-114">**(Optional)** Latest Universal Render Pipeline package, (we recommend version 10.5.1 or later)</span></span>

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> <span data-ttu-id="459d8-115">Se si compilano applicazioni VR su PC Windows, il plug-in OpenXR di realtà mista non è necessariamente necessario.</span><span class="sxs-lookup"><span data-stu-id="459d8-115">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="459d8-116">Tuttavia, è necessario installare il plug-in se si personalizza il mapping del controller per i controller HP Reverb G2 o si compilano app che funzionano sia su visori HoloLens 2 che vr.</span><span class="sxs-lookup"><span data-stu-id="459d8-116">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="459d8-117">Windows XR</span><span class="sxs-lookup"><span data-stu-id="459d8-117">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="459d8-118">Microsoft non consiglia di usare il plug-in Windows XR per i nuovi progetti in Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="459d8-118">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>

<span data-ttu-id="459d8-119">Tuttavia, se si usa Unity 2019 ed è necessario AR Foundation 2.0 per la compatibilità con i dispositivi ARCore/ARKit, questo plug-in abilita tale supporto.</span><span class="sxs-lookup"><span data-stu-id="459d8-119">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="459d8-120">L'uso di questo plug-in in Unity 2019 non supporta Ancoraggi nello stato di Azure.</span><span class="sxs-lookup"><span data-stu-id="459d8-120">Using this plugin in Unity 2019 doesn't support Azure Spatial Anchors.</span></span> 

# <a name="legacy-xr"></a>[<span data-ttu-id="459d8-121">XR legacy</span><span class="sxs-lookup"><span data-stu-id="459d8-121">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="459d8-122">Se si è ancora in Unity 2019 o versioni precedenti, Microsoft consiglia di usare il supporto XR incorporato legacy.</span><span class="sxs-lookup"><span data-stu-id="459d8-122">If you're still on Unity 2019 or earlier, Microsoft recommends using the Legacy Built-in XR support.</span></span> <span data-ttu-id="459d8-123">Anche se il plug-in Windows XR è funzionante in Unity 2019, non è consigliabile perché Ancoraggi nello stato di Azure non è supportato.</span><span class="sxs-lookup"><span data-stu-id="459d8-123">While the Windows XR plugin is functional on Unity 2019, it's not recommended because Azure Spatial Anchors isn't supported.</span></span>