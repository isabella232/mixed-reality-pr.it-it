---
ms.openlocfilehash: 923f7eda8b40e88aa69006896bd478f7aedcbcafccd449b75f144231d02b0d56
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202725"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Il plug-in OpenXR di realtà mista **è la** raccomandazione di Microsoft per **Unity 2020 LTS** o versioni successive. Poiché le nuove funzionalità verranno sviluppate in futuro, verranno incluse solo nel plug-in OpenXR di realtà mista in futuro.

Il plug-in OpenXR di realtà mista supporta completamente AR Foundation 4.0, fornendo implementazioni arPlaneManager e ARRaycastManager. In questo modo è possibile scrivere codice di raycasting una volta che si estende su HoloLens 2 telefoni e tablet ARCore/ARKit.

### <a name="prerequisites"></a>Prerequisiti 

* Strumenti [più recenti per HoloLens 2 sviluppo](../../../install-the-tools.md?tabs=unity#installation-checklist)
* Versione più recente di Unity 2020.3 LTS: versione 2020.3.8f1 o successiva

### <a name="recommended-package-versions"></a>Versioni consigliate dei pacchetti

Le istruzioni in questa pagina configurano i pacchetti OpenXR di Unity di base necessari per distribuire HoloLens 2 o Windows Mixed Reality app:

* Plug-in Unity OpenXR: versione 1.2 o successiva
* Plug-in OpenXR di realtà mista: versione 1.0.0 o successiva

Se si usano i pacchetti seguenti nel progetto, è necessario assicurarsi di usare almeno le versioni minime elencate di seguito:

* MRTK: versione 2.7.2 o successiva
* AR Foundation: versione 4.1.1 o successiva
* Universal Render Pipeline (URP): versione 10.5.1 o successiva
* Ancoraggi nello spaziale di Azure: versione 2.10 o successiva
* Rendering remoto di Azure: versione 1.0.15 o successiva

> [!NOTE]
> Se si compilano applicazioni VR Windows PC, il plug-in OpenXR di realtà mista non è strettamente necessario. Tuttavia, è necessario installare il plug-in se si configurano associazioni di input per controller HP Reverb G2 o si compilano app che funzionano sia su visori HoloLens 2 che vr.

# <a name="windows-xr"></a>[Windows Xr](#tab/windowsxr)

Microsoft non consiglia di usare il plug-Windows XR per i nuovi progetti in Unity 2020.  È invece consigliabile usare il plug-in OpenXR di realtà mista.

Tuttavia, se si usa Unity 2019 ed è necessario AR Foundation 2.0 per la compatibilità con i dispositivi ARCore/ARKit, questo plug-in abilita tale supporto.

> [!IMPORTANT]
> L'uso di questo plug-in in Unity 2019 non è compatibile con Ancoraggi nello spaziale di Azure.

# <a name="legacy-xr"></a>[XR legacy](#tab/legacy)

Se si usa ancora **Unity 2019** o versioni precedenti, Microsoft consiglia di usare il supporto **XR incorporato legacy.**

Anche se Windows plug-in XR è funzionante in Unity 2019, non è consigliabile perché questo plug-in non è compatibile con Ancoraggi nello spaziale di Azure in Unity 2019.

Se si avvia un nuovo progetto, è consigliabile installare [Unity 2020](../../choosing-unity-version.md) e usare il plug-in OpenXR di realtà mista.