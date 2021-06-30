---
ms.openlocfilehash: 550ad2b9fa92894cdf4dad86def4cd3a9b450fb1
ms.sourcegitcommit: e9a1510984d00dc40ffd39239349e500f5737a0d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113103901"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Il plug-in OpenXR di realtà mista **è la** raccomandazione di Microsoft per Unity 2020 LTS o versioni successive. Poiché le nuove funzionalità verranno sviluppate in futuro, verranno incluse solo nel plug-in OpenXR di realtà mista in futuro.

Il plug-in OpenXR di realtà mista supporta completamente AR Foundation 4.0, fornendo implementazioni arPlaneManager e ARRaycastManager. In questo modo è possibile scrivere codice di raycasting una volta che si estende su HoloLens 2 telefoni e tablet ARCore/ARKit.

### <a name="prerequisites"></a>Prerequisiti 

* Strumenti [più recenti per lo HoloLens 2 di sviluppo](../../../install-the-tools.md?tabs=unity#installation-checklist)
* Versione più recente di Unity 2020.3 LTS (è consigliabile 2020.3.8f1 o versione precedente)

### <a name="minimum-versions"></a>Versioni minime

Le istruzioni in questa pagina configurano i requisiti più recenti e più recenti di Unity e OpenXR elencati di seguito:

* Plug-in Unity OpenXR più recente (è consigliabile usare la versione 1.2 o successiva)
* Plug-in OpenXR di realtà mista più recente (è consigliabile la versione 1.0.0 o successiva)
* Se il progetto usa MRTK, è consigliabile usare la versione 2.7.2 o successiva
* Se il progetto usa un pacchetto URP (Universal Render Pipeline), è consigliabile usare la versione 10.5.1 o successiva

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> Se si compilano applicazioni VR su PC Windows, il plug-in OpenXR di realtà mista non è necessariamente necessario. Tuttavia, è necessario installare il plug-in se si personalizza il mapping del controller per i controller HP Reverb G2 o si compilano app che funzionano sia su visori HoloLens 2 che vr.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Microsoft non consiglia di usare il plug-in Windows XR per i nuovi progetti in Unity 2020.

Tuttavia, se si usa Unity 2019 ed è necessario AR Foundation 2.0 per la compatibilità con i dispositivi ARCore/ARKit, questo plug-in abilita tale supporto.

> [!IMPORTANT]
> L'uso di questo plug-in in Unity 2019 non supporta Ancoraggi nello stato di Azure. 

# <a name="legacy-xr"></a>[XR legacy](#tab/legacy)

Se si usa ancora Unity 2019 o versioni precedenti, Microsoft consiglia di usare il supporto XR incorporato legacy. Anche se il plug-in Windows XR è funzionante in Unity 2019, non è consigliabile perché Ancoraggi nello spaziali di Azure non è supportato.