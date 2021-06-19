---
ms.openlocfilehash: ca3589364fb27c3f8087572113f09e48d30e087e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394575"
---
# <a name="openxr"></a>[<span data-ttu-id="2e958-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="2e958-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="2e958-102">Il plug-in OpenXR di Realtà mista è una raccomandazione **di Microsoft** per Unity 2020 LTS o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="2e958-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for Unity 2020 LTS or later.</span></span> <span data-ttu-id="2e958-103">Le nuove funzionalità sviluppate in futuro verranno incluse solo nel plug-in OpenXR di Realtà mista in futuro.</span><span class="sxs-lookup"><span data-stu-id="2e958-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="2e958-104">Il plug-in OpenXR di realtà mista supporta completamente AR Foundation 4.0, fornendo implementazioni ARPlaneManager e ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="2e958-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="2e958-105">In questo modo è possibile scrivere codice di raycasting una volta che si estende su HoloLens 2 telefoni e tablet ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="2e958-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="2e958-106">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="2e958-106">Prerequisites</span></span> 

* <span data-ttu-id="2e958-107">Strumenti [più recenti per HoloLens 2 sviluppo](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="2e958-107">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="2e958-108">Versione più recente di Unity 2020.3 LTS (è consigliabile usare 2020.3.8f1 o versione superiore)</span><span class="sxs-lookup"><span data-stu-id="2e958-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>

### <a name="minimum-versions"></a><span data-ttu-id="2e958-109">Versioni minime</span><span class="sxs-lookup"><span data-stu-id="2e958-109">Minimum versions</span></span>

<span data-ttu-id="2e958-110">Le istruzioni in questa pagina illustrano i requisiti più recenti e più recenti di Unity e OpenXR elencati di seguito:</span><span class="sxs-lookup"><span data-stu-id="2e958-110">The instructions in this page will set you up with the latest and greatest Unity and OpenXR requirements listed below:</span></span>

* <span data-ttu-id="2e958-111">Plug-in Unity OpenXR più recente (è consigliabile usare la versione 1.2 o successiva)</span><span class="sxs-lookup"><span data-stu-id="2e958-111">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="2e958-112">Plug-in OpenXR di realtà mista più recente (è consigliabile usare la versione 1.0.0 o successiva)</span><span class="sxs-lookup"><span data-stu-id="2e958-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0 or later)</span></span>
* <span data-ttu-id="2e958-113">**(Facoltativo)** Ultima versione di MRTK (è consigliabile la versione 2.7 o successiva)</span><span class="sxs-lookup"><span data-stu-id="2e958-113">**(Optional)** Latest MRTK, (we recommend version 2.7 or later)</span></span>
* <span data-ttu-id="2e958-114">**(Facoltativo)** Pacchetto della pipeline di rendering universale più recente (è consigliabile la versione 10.5.1 o successiva)</span><span class="sxs-lookup"><span data-stu-id="2e958-114">**(Optional)** Latest Universal Render Pipeline package, (we recommend version 10.5.1 or later)</span></span>

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> <span data-ttu-id="2e958-115">Se si compilano applicazioni di realtà virtuale in PC Windows, il plug-in OpenXR di Realtà mista non è necessariamente necessario.</span><span class="sxs-lookup"><span data-stu-id="2e958-115">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="2e958-116">Tuttavia, è necessario installare il plug-in se si personalizza il mapping del controller per i controller HP Reverb G2 o si compilano app che funzionano sia su visori VR HoloLens 2 che su visori VR.</span><span class="sxs-lookup"><span data-stu-id="2e958-116">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="2e958-117">Windows XR</span><span class="sxs-lookup"><span data-stu-id="2e958-117">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="2e958-118">Microsoft non consiglia di usare il plug-in Windows XR per i nuovi progetti in Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="2e958-118">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>

<span data-ttu-id="2e958-119">Tuttavia, se si usa Unity 2019 ed è necessario AR Foundation 2.0 per la compatibilità con i dispositivi ARCore/ARKit, questo plug-in abilita tale supporto.</span><span class="sxs-lookup"><span data-stu-id="2e958-119">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2e958-120">L'uso di questo plug-in in Unity 2019 non supporta Ancoraggi nello stato di Azure.</span><span class="sxs-lookup"><span data-stu-id="2e958-120">Using this plugin in Unity 2019 doesn't support Azure Spatial Anchors.</span></span> 

# <a name="legacy-xr"></a>[<span data-ttu-id="2e958-121">XR legacy</span><span class="sxs-lookup"><span data-stu-id="2e958-121">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="2e958-122">Se si usa ancora Unity 2019 o versioni precedenti, Microsoft consiglia di usare il supporto XR legacy incorporato.</span><span class="sxs-lookup"><span data-stu-id="2e958-122">If you're still on Unity 2019 or earlier, Microsoft recommends using the Legacy Built-in XR support.</span></span> <span data-ttu-id="2e958-123">Anche se il plug-in Windows XR è funzionale in Unity 2019, non è consigliabile perché Ancoraggi nello stato di Azure non è supportato.</span><span class="sxs-lookup"><span data-stu-id="2e958-123">While the Windows XR plugin is functional on Unity 2019, it's not recommended because Azure Spatial Anchors isn't supported.</span></span>