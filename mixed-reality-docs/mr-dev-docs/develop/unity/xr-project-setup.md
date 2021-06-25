---
title: Configurazione di XR
description: Rimanere aggiornati sulle raccomandazioni di configurazione di Unity XR più recenti per lo sviluppo di applicazioni HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, unity
ms.openlocfilehash: d265725caf95379dfa01baa6dad1b7927fbeca5c
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906942"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="1bae5-104">Configurazione di XR</span><span class="sxs-lookup"><span data-stu-id="1bae5-104">Setting up your XR configuration</span></span>

<span data-ttu-id="1bae5-105">Quando si avvia un nuovo progetto Unity, sono disponibili tre diverse opzioni per la gestione delle esigenze XR:</span><span class="sxs-lookup"><span data-stu-id="1bae5-105">When you start a new Unity project, you have three different options for handling your XR needs:</span></span> 
* <span data-ttu-id="1bae5-106">Plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="1bae5-106">OpenXR plugin</span></span>
* <span data-ttu-id="1bae5-107">Plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="1bae5-107">Windows XR plugin</span></span>
* <span data-ttu-id="1bae5-108">Plug-in XR legacy</span><span class="sxs-lookup"><span data-stu-id="1bae5-108">Legacy XR plugin</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="1bae5-109">Configurazione del progetto con MRTK</span><span class="sxs-lookup"><span data-stu-id="1bae5-109">Setting up your project with MRTK</span></span>

<span data-ttu-id="1bae5-110">MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali.</span><span class="sxs-lookup"><span data-stu-id="1bae5-110">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="1bae5-111">MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="1bae5-111">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="1bae5-112">Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.</span><span class="sxs-lookup"><span data-stu-id="1bae5-112">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1bae5-113">Provare le esercitazioni su MRTK</span><span class="sxs-lookup"><span data-stu-id="1bae5-113">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=winxr)

<span data-ttu-id="1bae5-114">Per altri dettagli sulle funzionalità, vedere la documentazione di [MRTK.](/windows/mixed-reality/mrtk-unity)</span><span class="sxs-lookup"><span data-stu-id="1bae5-114">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

### <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="1bae5-115">Uso di MRTK con il supporto di OpenXR</span><span class="sxs-lookup"><span data-stu-id="1bae5-115">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="1bae5-116">MRTK-Unity versione 2.7 offre un supporto migliore per il plug-in OpenXR di Realtà mista.</span><span class="sxs-lookup"><span data-stu-id="1bae5-116">MRTK-Unity 2.7 release provides better supports for the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="1bae5-117">Aprire di [nuovo Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) per installare Mixed Reality Toolkit, se non è già stato fatto.</span><span class="sxs-lookup"><span data-stu-id="1bae5-117">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="1bae5-118">Il supporto di OpenXR è in pacchetto **Foundation.**</span><span class="sxs-lookup"><span data-stu-id="1bae5-118">OpenXR support is in the **Foundation** package.</span></span>

<span data-ttu-id="1bae5-119">Per informazioni più dettagliate sulla [migrazione a OpenXR,](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)vedere la documentazione di MRTK.</span><span class="sxs-lookup"><span data-stu-id="1bae5-119">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="1bae5-120">Quando si esegue l'aggiornamento da una versione precedente di MRTK precedente alla **2.5.3,** verificare che la riga seguente si trova nel file **Assets/MixedRealityToolkit.Generated/link.xml:**</span><span class="sxs-lookup"><span data-stu-id="1bae5-120">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="1bae5-121">Questa riga verrà aggiunta per impostazione predefinita se si è iniziato con MRTK 2.5.4 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="1bae5-121">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="1bae5-122">Configurazione manuale senza MRTK</span><span class="sxs-lookup"><span data-stu-id="1bae5-122">Manual setup without MRTK</span></span>

<span data-ttu-id="1bae5-123">Anche se Microsoft e la community hanno creato strumenti opensource come [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) che configurano automaticamente l'ambiente WMR, molti sviluppatori vogliono creare le proprie esperienze da zero.</span><span class="sxs-lookup"><span data-stu-id="1bae5-123">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]