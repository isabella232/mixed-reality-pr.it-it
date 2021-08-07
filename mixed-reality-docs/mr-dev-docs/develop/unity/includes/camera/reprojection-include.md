---
ms.openlocfilehash: d30bf4b5c382ca953314996dd51087427224e872158b607fd1c5f4c85c62a124
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212305"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK non dispone attualmente di helper per la modalità di nuovaproiezione. Per altre informazioni, vedere una delle altre schede.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

La modalità diproiezione è configurabile impostando [XRDisplaySubsystem.reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) sul valore appropriato.

Ad esempio, se si [](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) sta creando un'esperienza di solo orientamento con contenuto rigidamente bloccato dal corpo (ad esempio, contenuto video a 360 gradi), è possibile impostare in modo esplicito la modalità di nuovaproiezione sull'orientamento solo impostandola su [ReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

La modalità di progetto è configurabile impostando [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) sul valore appropriato.

Ad esempio, se si [](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) sta creando un'esperienza di solo orientamento con contenuto rigidamente bloccato dal corpo (ad esempio, contenuto video a 360 gradi), è possibile impostare in modo esplicito la modalità di riproiezione sull'orientamento solo impostandola su [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).