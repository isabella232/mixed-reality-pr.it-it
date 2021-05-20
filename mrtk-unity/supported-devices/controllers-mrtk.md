---
title: Controller in MRTK
description: Documentazione sull'uso di vari controller con MRTK
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, controller, HP Reverb, Oculus, HTC Vive, Mani
ms.openlocfilehash: 953b1cd56dbf7d7a548a3aba8da07ce5875fec74
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145471"
---
# <a name="controllers-in-mrtk"></a><span data-ttu-id="0d2a4-104">Controller in MRTK</span><span class="sxs-lookup"><span data-stu-id="0d2a4-104">Controllers in MRTK</span></span>

<span data-ttu-id="0d2a4-105">MRTK supporta molti controller diversi.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-105">MRTK has support for many different controllers.</span></span> <span data-ttu-id="0d2a4-106">Molti controller, ad esempio i wands DI VIVE e i wands DI VIVE, funzioneranno in modo nativo dopo l'avvio di un'applicazione compilata con MRTK nel dispositivo compatibile.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-106">Many controllers, such as HTC Vive Knuckles and HTC Vive Wands, will work natively once an application built with MRTK is launched on the compatible device.</span></span> <span data-ttu-id="0d2a4-107">Altri controller, ad esempio le mani articolate su Oculus Quest e i controller HP Reverb G2, richiedono pacchetti aggiuntivi prima che siano riconosciuti da MRTK.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-107">Other controllers, such as articulated hands on the Oculus Quest and the HP Reverb G2 Controllers, require additional packages before they are recognized by MRTK.</span></span>

<span data-ttu-id="0d2a4-108">Questo documento descrive gli scenari comuni in cui è necessario installare pacchetti aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-108">This document will describe the common scenarios where extra packages need to be installed.</span></span> <span data-ttu-id="0d2a4-109">Per altre informazioni sui controller, visitare la [**pagina delle funzionalità**](../features/input/controllers.md).</span><span class="sxs-lookup"><span data-stu-id="0d2a4-109">For additional information about controllers, visit the [**features page**](../features/input/controllers.md).</span></span> <span data-ttu-id="0d2a4-110">Per eseguire il debug dei problemi con i controller, vedere lo [ **strumento di mapping dei controller**](../features/tools/controller-mapping-tool.md)</span><span class="sxs-lookup"><span data-stu-id="0d2a4-110">To debug issues with controllers, see the [**Controller mapping tool**](../features/tools/controller-mapping-tool.md)</span></span>

## <a name="hp-reverb-g2-controllers"></a><span data-ttu-id="0d2a4-111">Controller HP Reverb G2</span><span class="sxs-lookup"><span data-stu-id="0d2a4-111">HP Reverb G2 Controllers</span></span>

<span data-ttu-id="0d2a4-112">Per rilevare e visualizzare i controller HP Reverb G2 quando si usa MRTK, seguire questa procedura per installare il pacchetto [**Microsoft.MixedReality.Input.**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="0d2a4-112">To detect and show the HP Reverb G2 controllers when using MRTK, follow these steps to install the [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) package.</span></span> <span data-ttu-id="0d2a4-113">Dopo aver installato questo pacchetto, non è necessario apportare altre modifiche ai profili predefiniti per visualizzare i controller in HP Reverb.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-113">Once this package is installed, no other changes to the default profiles need to be made to have the controllers show up on the HP Reverb.</span></span> 

<span data-ttu-id="0d2a4-114">Per visualizzare i controller nell'editor, è necessario assicurarsi di usare il plug-in [**OpenXR**](/windows/mixed-reality/develop/unity/openxr-getting-started).</span><span class="sxs-lookup"><span data-stu-id="0d2a4-114">In order to display the controllers in editor, you need to ensure that you are using the using the [**OpenXR Plugin**](/windows/mixed-reality/develop/unity/openxr-getting-started).</span></span>

## <a name="oculus-controllers"></a><span data-ttu-id="0d2a4-115">Controller Oculus</span><span class="sxs-lookup"><span data-stu-id="0d2a4-115">Oculus Controllers</span></span> 

<span data-ttu-id="0d2a4-116">Per visualizzare i modelli di controller Oculus, seguire le istruzioni per la distribuzione di Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-116">To visualize Oculus controller models, follow the Oculus Quest deployment instructions.</span></span> <span data-ttu-id="0d2a4-117">Se si desidera visualizzare le mani virtuali quando si usano i controller, assicurarsi che l'opzione **Render Avatar Hands Instead Of Controllers** sia selezionata in XR SDK Oculus Device Manager.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-117">If you wish to show virtual hands when using the controllers, make sure that **Render Avatar Hands Instead Of Controllers** is checked under the XR SDK Oculus Device Manager.</span></span> <span data-ttu-id="0d2a4-118">In caso contrario, deselezionare questa opzione.</span><span class="sxs-lookup"><span data-stu-id="0d2a4-118">Otherwise, uncheck this option.</span></span>

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
