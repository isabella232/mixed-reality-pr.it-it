---
ms.openlocfilehash: 879d8083f832e716389e4b4598aa0fffe6930ff1c06d7a07fe9e4dacc98e7937
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212312"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK offre un sistema di [teletrasporto](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) in box che funziona automaticamente su mani e controller articolati.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

È consigliabile usare l'implementazione del teletrasporto di MRTK.
Se si sceglie di non usare MRTK, Unity fornisce un'implementazione del teletrasporto nel Toolkit [XR.](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)
Se si sceglie di implementare il proprio, è bene tenere presente che non è possibile spostare direttamente la fotocamera. A causa del controllo della fotocamera di Unity per il rilevamento della testa, è necessario assegnare alla fotocamera un elemento padre nella gerarchia e spostare il GameObject. Questo è l'equivalente di Playspace di MRTK.

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

È consigliabile usare l'implementazione del teletrasporto di MRTK.
Se si sceglie di implementare il proprio, è bene tenere presente che non è possibile spostare direttamente la fotocamera. A causa del controllo della fotocamera di Unity per il rilevamento della testa, è necessario assegnare alla fotocamera un elemento padre nella gerarchia e spostare il GameObject. Questo è l'equivalente di Playspace di MRTK.