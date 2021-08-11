---
ms.openlocfilehash: ce1f02bd2846cadc4e970fef738fb4b46bc3a09f10742b820a0998491c590c80
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204284"
---
# <a name="all-platforms"></a>[Tutte le piattaforme](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a>Abilitazione del plug-in HP Motion Controller 

I mapping del profilo di interazione e del controller sono nel plug-in HP Motion Controller, che deve essere abilitato per esporre i mapping del controller al sistema di input di Unreal.

![Abilitazione del plug-in OpenXRHPController](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a>Configurazione di Startup e HMDPluginPriority

L'input in Unreal con SteamVR presenta alcune differenze.  Quando si configura il progetto, assicurarsi prima di tutto che sia in uso il nuovo sistema di input di SteamVR aggiungendo **vr. EngineVR.EnableVRInput=1** nella **sezione Startup** in **Engine/Config/ConsoleVariables.ini**.  Questo ini si trova nella directory di installazione del motore, non nella directory del progetto.

![Aggiornamento della configurazione di avvio](../images/reverb-g2-img-07.png)

Il plug-in HP Motion Controller abiliterà OpenXR.  Se non si usa OpenXR, sarà necessario modificare HMDPluginPriority di SteamVR in BaseEngine.ini nella stessa directory di ConsoleVariables.ini.  Modificare il valore di SteamVR in modo che sia maggiore del valore OpenXRHMD.

![Aggiornamento della configurazione HMDPluginPriority](../images/reverb-g2-img-08.png)


