---
ms.openlocfilehash: eaa2651a22fd5b2b601493845d507aeda6745f1a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603717"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Il plug-in OpenXR di Realtà mista è una raccomandazione **di Microsoft** per **Unity 2020 LTS** o versioni successive. Le nuove funzionalità sviluppate in futuro verranno incluse solo nel plug-in OpenXR di Realtà mista in futuro.

Il plug-in OpenXR di realtà mista supporta completamente AR Foundation 4.0, fornendo implementazioni ARPlaneManager e ARRaycastManager. In questo modo è possibile scrivere codice di raycasting una volta che si estende su HoloLens 2 telefoni e tablet ARCore/ARKit.

### <a name="prerequisites"></a>Prerequisiti 

* Strumenti [più recenti per HoloLens 2 sviluppo](../../../install-the-tools.md?tabs=unity#installation-checklist)
* Versione più recente di Unity 2020.3 LTS: versione 2020.3.8f1 o successiva

### <a name="recommended-package-versions"></a>Versioni dei pacchetti consigliate

Le istruzioni in questa pagina configurano i pacchetti OpenXR Unity di base necessari per distribuire HoloLens 2 o Windows Mixed Reality app:

* Plug-in Unity OpenXR: versione 1.2 o successiva
* Plug-in OpenXR di Realtà mista: versione 1.0.0 o successiva

Se si usano i pacchetti seguenti nel progetto, è necessario assicurarsi di usare almeno le versioni minime elencate di seguito:

* MRTK: versione 2.7.2 o successiva
* AR Foundation: versione 4.1.1 o successiva
* Universal Render Pipeline (URP): versione 10.5.1 o successiva
* Ancoraggi nello stato di Azure: versione 2.10 o successiva
* Rendering remoto di Azure: versione 1.0.15 o successiva

> [!NOTE]
> Se si compilano applicazioni di realtà virtuale Windows PC, il plug-in OpenXR di realtà mista non è strettamente necessario. Tuttavia, è necessario installare il plug-in se si configurano associazioni di input per i controller HP Reverb G2 o si compilano app che funzionano sia su visori VR HoloLens 2 che su visori VR.

# <a name="windows-xr"></a>[Windows Xr](#tab/windowsxr)

Microsoft non consiglia di usare il plug-Windows XR per i nuovi progetti in Unity 2020.  È invece consigliabile usare il plug-in OpenXR di realtà mista.

Tuttavia, se si usa Unity 2019 ed è necessario AR Foundation 2.0 per la compatibilità con i dispositivi ARCore/ARKit, questo plug-in abilita tale supporto.

> [!IMPORTANT]
> L'uso di questo plug-in in Unity 2019 non è compatibile con Ancoraggi nello stato di Azure.

# <a name="legacy-xr"></a>[XR legacy](#tab/legacy)

Se si usa ancora **Unity 2019** o versioni precedenti, Microsoft consiglia di usare il supporto **XR legacy incorporato.**

Anche se Windows plug-in XR è funzionante in Unity 2019, non è consigliabile perché questo plug-in non è compatibile con Ancoraggi nello stato di Azure in Unity 2019.

Se si sta avviando un nuovo progetto, è consigliabile installare [Unity 2020](../../choosing-unity-version.md) e usare il plug-in OpenXR di Realtà mista.