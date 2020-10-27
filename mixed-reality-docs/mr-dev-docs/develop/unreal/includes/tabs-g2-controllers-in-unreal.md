---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638733"
---
# <a name="all-platforms"></a>[Tutte le piattaforme](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a>Abilitazione del plug-in HP Motion controller 

Il profilo di interazione e i mapping del controller si trovano nel plug-in HP Motion controller, che deve essere abilitato per esporre i mapping del controller al sistema di input Unreal.

![Abilitazione del plug-in OpenXRHPController](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a>Configurazione di startup e HMDPluginPriority

L'input in Unreal con SteamVR presenta alcune differenze.  Quando si configura il progetto, assicurarsi prima di tutto di usare il nuovo sistema di input di SteamVR aggiungendo **VR. SteamVR. EnableVRInput = 1** alla sezione **Startup** nel **motore/config/ConsoleVariables.ini** .  Questo ini si trova nella directory di installazione del motore, non nella directory del progetto.

![Aggiornamento della configurazione di avvio](../images/reverb-g2-img-07.png)

Il plug-in HP Motion controller consentirà OpenXR.  Se non si usa OpenXR, sarà necessario modificare il HMDPluginPriority di SteamVR in BaseEngine.ini nella stessa directory ConsoleVariables.ini.  Modificare il valore di SteamVR in modo che sia maggiore del valore di OpenXRHMD.

![Aggiornamento della configurazione di HMDPluginPriority](../images/reverb-g2-img-08.png)


