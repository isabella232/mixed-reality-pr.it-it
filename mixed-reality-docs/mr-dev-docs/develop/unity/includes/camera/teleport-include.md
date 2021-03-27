---
ms.openlocfilehash: daf81bcd6ce215d908ce6b4028effcdc2ed38328
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636370"
---
# <a name="mrtk"></a>[<span data-ttu-id="b4fe9-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="b4fe9-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="b4fe9-102">MRTK fornisce un [sistema di teletrasporto integrato](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) che funziona automaticamente tra le mani e i controller articolati.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-102">MRTK provides an in-box [teleport system](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) which automatically works across articulated hands and controllers.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="b4fe9-103">SDK XR</span><span class="sxs-lookup"><span data-stu-id="b4fe9-103">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="b4fe9-104">Si consiglia di usare l'implementazione di Teleporting di MRTK.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-104">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="b4fe9-105">Se si sceglie di non usare MRTK, Unity fornisce un'implementazione di Teleporting in [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span><span class="sxs-lookup"><span data-stu-id="b4fe9-105">If you choose not to use MRTK, Unity provides a teleportation implementation in the [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span></span>
<span data-ttu-id="b4fe9-106">Se si sceglie di implementare il proprio, è opportuno tenere presente che non è possibile spostare direttamente la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-106">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="b4fe9-107">A causa del controllo di Unity della fotocamera per il rilevamento delle intestazioni, è necessario assegnare alla fotocamera un elemento padre nella gerarchia e spostare invece tale GameObject.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-107">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="b4fe9-108">Equivale a playspace di MRTK.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-108">This is the equivalent of MRTK's Playspace.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="b4fe9-109">WSA legacy</span><span class="sxs-lookup"><span data-stu-id="b4fe9-109">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="b4fe9-110">Si consiglia di usare l'implementazione di Teleporting di MRTK.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-110">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="b4fe9-111">Se si sceglie di implementare il proprio, è opportuno tenere presente che non è possibile spostare direttamente la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-111">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="b4fe9-112">A causa del controllo di Unity della fotocamera per il rilevamento delle intestazioni, è necessario assegnare alla fotocamera un elemento padre nella gerarchia e spostare invece tale GameObject.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-112">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="b4fe9-113">Equivale a playspace di MRTK.</span><span class="sxs-lookup"><span data-stu-id="b4fe9-113">This is the equivalent of MRTK's Playspace.</span></span>