---
ms.openlocfilehash: 0a4f6f1262bcaa69a8755223d738bbd88bd7a6a8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748480"
---
# <a name="mrtk"></a>[<span data-ttu-id="5ea72-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="5ea72-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="5ea72-102">MRTK offre un sistema di [teletrasporto](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) in box che funziona automaticamente su mani e controller articolati.</span><span class="sxs-lookup"><span data-stu-id="5ea72-102">MRTK provides an in-box [teleport system](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) which automatically works across articulated hands and controllers.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="5ea72-103">XR SDK</span><span class="sxs-lookup"><span data-stu-id="5ea72-103">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="5ea72-104">È consigliabile usare l'implementazione del teletrasporto di MRTK.</span><span class="sxs-lookup"><span data-stu-id="5ea72-104">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="5ea72-105">Se si sceglie di non usare MRTK, Unity fornisce un'implementazione del teletrasporto in [XR Interaction Toolkit.](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)</span><span class="sxs-lookup"><span data-stu-id="5ea72-105">If you choose not to use MRTK, Unity provides a teleportation implementation in the [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span></span>
<span data-ttu-id="5ea72-106">Se si sceglie di implementare il proprio, è bene tenere presente che non è possibile spostare direttamente la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="5ea72-106">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="5ea72-107">A causa del controllo della fotocamera di Unity per il tracciamento della testa, dovrai assegnare alla fotocamera un elemento padre nella gerarchia e spostare invece il GameObject.</span><span class="sxs-lookup"><span data-stu-id="5ea72-107">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="5ea72-108">Equivale a Playspace di MRTK.</span><span class="sxs-lookup"><span data-stu-id="5ea72-108">This is the equivalent of MRTK's Playspace.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="5ea72-109">Legacy WSA</span><span class="sxs-lookup"><span data-stu-id="5ea72-109">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="5ea72-110">È consigliabile usare l'implementazione del teletrasporto di MRTK.</span><span class="sxs-lookup"><span data-stu-id="5ea72-110">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="5ea72-111">Se si sceglie di implementare il proprio, è bene tenere presente che non è possibile spostare direttamente la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="5ea72-111">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="5ea72-112">A causa del controllo della fotocamera di Unity per il tracciamento della testa, dovrai assegnare alla fotocamera un elemento padre nella gerarchia e spostare invece il GameObject.</span><span class="sxs-lookup"><span data-stu-id="5ea72-112">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="5ea72-113">Equivale a Playspace di MRTK.</span><span class="sxs-lookup"><span data-stu-id="5ea72-113">This is the equivalent of MRTK's Playspace.</span></span>