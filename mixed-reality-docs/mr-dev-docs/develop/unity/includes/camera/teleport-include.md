---
ms.openlocfilehash: 0a4f6f1262bcaa69a8755223d738bbd88bd7a6a8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748480"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK offre un sistema di [teletrasporto](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) in box che funziona automaticamente su mani e controller articolati.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

È consigliabile usare l'implementazione del teletrasporto di MRTK.
Se si sceglie di non usare MRTK, Unity fornisce un'implementazione del teletrasporto in [XR Interaction Toolkit.](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)
Se si sceglie di implementare il proprio, è bene tenere presente che non è possibile spostare direttamente la fotocamera. A causa del controllo della fotocamera di Unity per il tracciamento della testa, dovrai assegnare alla fotocamera un elemento padre nella gerarchia e spostare invece il GameObject. Equivale a Playspace di MRTK.

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

È consigliabile usare l'implementazione del teletrasporto di MRTK.
Se si sceglie di implementare il proprio, è bene tenere presente che non è possibile spostare direttamente la fotocamera. A causa del controllo della fotocamera di Unity per il tracciamento della testa, dovrai assegnare alla fotocamera un elemento padre nella gerarchia e spostare invece il GameObject. Equivale a Playspace di MRTK.