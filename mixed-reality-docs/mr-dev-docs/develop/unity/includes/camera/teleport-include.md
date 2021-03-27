---
ms.openlocfilehash: daf81bcd6ce215d908ce6b4028effcdc2ed38328
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636370"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK fornisce un [sistema di teletrasporto integrato](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) che funziona automaticamente tra le mani e i controller articolati.

# <a name="xr-sdk"></a>[SDK XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Si consiglia di usare l'implementazione di Teleporting di MRTK.
Se si sceglie di non usare MRTK, Unity fornisce un'implementazione di Teleporting in [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).
Se si sceglie di implementare il proprio, è opportuno tenere presente che non è possibile spostare direttamente la fotocamera. A causa del controllo di Unity della fotocamera per il rilevamento delle intestazioni, è necessario assegnare alla fotocamera un elemento padre nella gerarchia e spostare invece tale GameObject. Equivale a playspace di MRTK.

# <a name="legacy-wsa"></a>[WSA legacy](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Si consiglia di usare l'implementazione di Teleporting di MRTK.
Se si sceglie di implementare il proprio, è opportuno tenere presente che non è possibile spostare direttamente la fotocamera. A causa del controllo di Unity della fotocamera per il rilevamento delle intestazioni, è necessario assegnare alla fotocamera un elemento padre nella gerarchia e spostare invece tale GameObject. Equivale a playspace di MRTK.