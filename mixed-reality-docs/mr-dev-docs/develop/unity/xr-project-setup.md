---
title: Configurazione di XR
description: Rimanere aggiornati sulle raccomandazioni di configurazione di Unity XR più recenti per lo sviluppo di applicazioni HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, unity
ms.openlocfilehash: d265725caf95379dfa01baa6dad1b7927fbeca5c
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906942"
---
# <a name="setting-up-your-xr-configuration"></a>Configurazione di XR

Quando si avvia un nuovo progetto Unity, sono disponibili tre diverse opzioni per la gestione delle esigenze XR: 
* Plug-in OpenXR
* Plug-in Windows XR
* Plug-in XR legacy

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>Configurazione del progetto con MRTK

MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali. MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR. Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.

> [!div class="nextstepaction"]
> [Provare le esercitazioni su MRTK](./tutorials/mr-learning-base-02.md?tabs=winxr)

Per altri dettagli sulle funzionalità, vedere la documentazione di [MRTK.](/windows/mixed-reality/mrtk-unity)

### <a name="using-mrtk-with-openxr-support"></a>Uso di MRTK con il supporto di OpenXR

MRTK-Unity versione 2.7 offre un supporto migliore per il plug-in OpenXR di Realtà mista.

Aprire di [nuovo Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) per installare Mixed Reality Toolkit, se non è già stato fatto. Il supporto di OpenXR è in pacchetto **Foundation.**

Per informazioni più dettagliate sulla [migrazione a OpenXR,](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)vedere la documentazione di MRTK.

> [!NOTE]
> Quando si esegue l'aggiornamento da una versione precedente di MRTK precedente alla **2.5.3,** verificare che la riga seguente si trova nel file **Assets/MixedRealityToolkit.Generated/link.xml:**
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Questa riga verrà aggiunta per impostazione predefinita se si è iniziato con MRTK 2.5.4 o versione successiva.

## <a name="manual-setup-without-mrtk"></a>Configurazione manuale senza MRTK

Anche se Microsoft e la community hanno creato strumenti opensource come [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) che configurano automaticamente l'ambiente WMR, molti sviluppatori vogliono creare le proprie esperienze da zero.

[!INCLUDE[](includes/xr/manual-setup.md)]