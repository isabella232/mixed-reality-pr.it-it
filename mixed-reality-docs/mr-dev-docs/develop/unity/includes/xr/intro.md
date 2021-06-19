---
ms.openlocfilehash: ca3589364fb27c3f8087572113f09e48d30e087e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394575"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Il plug-in OpenXR di Realtà mista è una raccomandazione **di Microsoft** per Unity 2020 LTS o versioni successive. Le nuove funzionalità sviluppate in futuro verranno incluse solo nel plug-in OpenXR di Realtà mista in futuro.

Il plug-in OpenXR di realtà mista supporta completamente AR Foundation 4.0, fornendo implementazioni ARPlaneManager e ARRaycastManager. In questo modo è possibile scrivere codice di raycasting una volta che si estende su HoloLens 2 telefoni e tablet ARCore/ARKit.

### <a name="prerequisites"></a>Prerequisiti 

* Strumenti [più recenti per HoloLens 2 sviluppo](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)
* Versione più recente di Unity 2020.3 LTS (è consigliabile usare 2020.3.8f1 o versione superiore)

### <a name="minimum-versions"></a>Versioni minime

Le istruzioni in questa pagina illustrano i requisiti più recenti e più recenti di Unity e OpenXR elencati di seguito:

* Plug-in Unity OpenXR più recente (è consigliabile usare la versione 1.2 o successiva)
* Plug-in OpenXR di realtà mista più recente (è consigliabile usare la versione 1.0.0 o successiva)
* **(Facoltativo)** Ultima versione di MRTK (è consigliabile la versione 2.7 o successiva)
* **(Facoltativo)** Pacchetto della pipeline di rendering universale più recente (è consigliabile la versione 10.5.1 o successiva)

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> Se si compilano applicazioni di realtà virtuale in PC Windows, il plug-in OpenXR di Realtà mista non è necessariamente necessario. Tuttavia, è necessario installare il plug-in se si personalizza il mapping del controller per i controller HP Reverb G2 o si compilano app che funzionano sia su visori VR HoloLens 2 che su visori VR.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Microsoft non consiglia di usare il plug-in Windows XR per i nuovi progetti in Unity 2020.

Tuttavia, se si usa Unity 2019 ed è necessario AR Foundation 2.0 per la compatibilità con i dispositivi ARCore/ARKit, questo plug-in abilita tale supporto.

> [!IMPORTANT]
> L'uso di questo plug-in in Unity 2019 non supporta Ancoraggi nello stato di Azure. 

# <a name="legacy-xr"></a>[XR legacy](#tab/legacy)

Se si usa ancora Unity 2019 o versioni precedenti, Microsoft consiglia di usare il supporto XR legacy incorporato. Anche se il plug-in Windows XR è funzionale in Unity 2019, non è consigliabile perché Ancoraggi nello stato di Azure non è supportato.