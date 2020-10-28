---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638733"
---
# <a name="all-platforms"></a>[<span data-ttu-id="67673-101">Tutte le piattaforme</span><span class="sxs-lookup"><span data-stu-id="67673-101">All platforms</span></span>](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a><span data-ttu-id="67673-102">Abilitazione del plug-in HP Motion controller</span><span class="sxs-lookup"><span data-stu-id="67673-102">Enabling HP Motion Controller Plugin</span></span> 

<span data-ttu-id="67673-103">Il profilo di interazione e i mapping del controller si trovano nel plug-in HP Motion controller, che deve essere abilitato per esporre i mapping del controller al sistema di input Unreal.</span><span class="sxs-lookup"><span data-stu-id="67673-103">The interaction profile and controller mappings are in the HP Motion Controller plugin, which must be enabled to expose the controller mappings to Unreal’s input system.</span></span>

![Abilitazione del plug-in OpenXRHPController](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[<span data-ttu-id="67673-105">SteamVR</span><span class="sxs-lookup"><span data-stu-id="67673-105">SteamVR</span></span>](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a><span data-ttu-id="67673-106">Configurazione di startup e HMDPluginPriority</span><span class="sxs-lookup"><span data-stu-id="67673-106">Configuring Startup and HMDPluginPriority</span></span>

<span data-ttu-id="67673-107">L'input in Unreal con SteamVR presenta alcune differenze.</span><span class="sxs-lookup"><span data-stu-id="67673-107">Input in Unreal using SteamVR has a few differences.</span></span>  <span data-ttu-id="67673-108">Quando si configura il progetto, assicurarsi prima di tutto di usare il nuovo sistema di input di SteamVR aggiungendo **VR. SteamVR. EnableVRInput = 1** alla sezione **Startup** nel **motore/config/ConsoleVariables.ini** .</span><span class="sxs-lookup"><span data-stu-id="67673-108">When setting up the project, first ensure it is using SteamVR’s new input system by adding **vr.SteamVR.EnableVRInput=1** to the **Startup** section in **Engine/Config/ConsoleVariables.ini** .</span></span>  <span data-ttu-id="67673-109">Questo ini si trova nella directory di installazione del motore, non nella directory del progetto.</span><span class="sxs-lookup"><span data-stu-id="67673-109">This ini is found in the engine install directory, not the project directory.</span></span>

![Aggiornamento della configurazione di avvio](../images/reverb-g2-img-07.png)

<span data-ttu-id="67673-111">Il plug-in HP Motion controller consentirà OpenXR.</span><span class="sxs-lookup"><span data-stu-id="67673-111">The HP Motion Controller plugin will enable OpenXR.</span></span>  <span data-ttu-id="67673-112">Se non si usa OpenXR, sarà necessario modificare il HMDPluginPriority di SteamVR in BaseEngine.ini nella stessa directory ConsoleVariables.ini.</span><span class="sxs-lookup"><span data-stu-id="67673-112">If you're not using OpenXR, you will need to edit the HMDPluginPriority of SteamVR in BaseEngine.ini in the same directory as ConsoleVariables.ini.</span></span>  <span data-ttu-id="67673-113">Modificare il valore di SteamVR in modo che sia maggiore del valore di OpenXRHMD.</span><span class="sxs-lookup"><span data-stu-id="67673-113">Change the SteamVR value to be greater than the OpenXRHMD value.</span></span>

![Aggiornamento della configurazione di HMDPluginPriority](../images/reverb-g2-img-08.png)


