---
title: Configurazione della configurazione XR
description: Rimanere aggiornati sulle raccomandazioni di configurazione più recenti di Unity XR per lo HoloLens di applicazioni.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale, unity
ms.openlocfilehash: d2904b9ea4771286b7091a8d5b7c599fcbd1244a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603727"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="dc314-104">Configurazione della configurazione XR</span><span class="sxs-lookup"><span data-stu-id="dc314-104">Setting up your XR configuration</span></span>

<span data-ttu-id="dc314-105">Dopo aver scelto una [versione di Unity,](choosing-unity-version.md)il passaggio successivo consiste nel selezionare la configurazione XR che verrà utilizzata per creare l'app di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="dc314-105">Once you've [chosen a Unity version](choosing-unity-version.md), the next step is to select the XR configuration you'll use to build your mixed reality app:</span></span>

## <a name="choosing-an-xr-configuration"></a><span data-ttu-id="dc314-106">Scelta di una configurazione XR</span><span class="sxs-lookup"><span data-stu-id="dc314-106">Choosing an XR configuration</span></span>

<span data-ttu-id="dc314-107">Quando si avvia un nuovo progetto Unity, è possibile selezionare diverse configurazioni XR: plug-in **OpenXR** di realtà mista, plug-in **XR Windows** e **XR legacy incorporato.**</span><span class="sxs-lookup"><span data-stu-id="dc314-107">When you start a new Unity project, you have various XR configurations you can select from: the **Mixed Reality OpenXR plugin**, the **Windows XR plugin** and **Legacy Built-in XR**.</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="dc314-108">Configurazione del progetto con MRTK</span><span class="sxs-lookup"><span data-stu-id="dc314-108">Setting up your project with MRTK</span></span>

<span data-ttu-id="dc314-109">Il modo più semplice per configurare il progetto Unity per la realtà mista è con l'Toolkit (MRTK).</span><span class="sxs-lookup"><span data-stu-id="dc314-109">The easiest way to get your Unity project set up for mixed reality is with the Mixed Reality Toolkit (MRTK).</span></span>  <span data-ttu-id="dc314-110">MRTK per Unity è un kit di sviluppo multipiattaforma open source progettato per semplificare la creazione di straordinarie applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="dc314-110">MRTK for Unity is an open-source, cross-platform development kit designed to make it easy to build amazing mixed reality applications.</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="dc314-112">MRTK offre un sistema di input multipiattaforma, componenti di base e blocchi predefiniti comuni per le interazioni spaziali.</span><span class="sxs-lookup"><span data-stu-id="dc314-112">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span>  <span data-ttu-id="dc314-113">Con MRTK versione 2, è possibile velocizzare lo sviluppo di applicazioni per Microsoft HoloLens, visori vr immersivi Windows Mixed Reality e molti altri dispositivi VR/AR.</span><span class="sxs-lookup"><span data-stu-id="dc314-113">With MRTK version 2, you can speed up your application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and many other VR/AR devices.</span></span> <span data-ttu-id="dc314-114">Il progetto ha lo scopo di ridurre le barriere all'ingresso, consentendo a tutti di creare applicazioni di realtà mista e contribuire alla community con la crescita di tutti.</span><span class="sxs-lookup"><span data-stu-id="dc314-114">The project is aimed at reducing barriers to entry, enabling everyone to build mixed reality applications and contribute back to the community as we all grow.</span></span>

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

<span data-ttu-id="dc314-115">Per altre informazioni sul modello di realtà Toolkit, vedere la [documentazione di MRTK.](/windows/mixed-reality/mrtk-unity)</span><span class="sxs-lookup"><span data-stu-id="dc314-115">To learn more about the Mixed Reality Toolkit, check out the [MRTK documentation](/windows/mixed-reality/mrtk-unity).</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="dc314-116">Configurazione manuale senza MRTK</span><span class="sxs-lookup"><span data-stu-id="dc314-116">Manual setup without MRTK</span></span>

<span data-ttu-id="dc314-117">Anche se Microsoft e la community hanno creato open source strumenti come Il Toolkit di realtà mista [(MRTK)](/windows/mixed-reality/mrtk-unity) che configura automaticamente l'ambiente per la realtà mista, alcuni sviluppatori potrebbero voler creare le proprie esperienze da zero.</span><span class="sxs-lookup"><span data-stu-id="dc314-117">While Microsoft and the community have created open source tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity) that will automatically set up your environment for mixed reality, some developers may wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]