---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097644"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="5e89e-101">Plug-in Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="5e89e-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="5e89e-102">Verifica della capacità di input degli occhi e aggiunta degli occhi provider di dati</span><span class="sxs-lookup"><span data-stu-id="5e89e-102">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="5e89e-103">Nel menu di Unity selezionare Mixed Reality Toolkit > Utilities > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) e quindi, nella sezione **UWP Capabilities** (Funzionalità UWP), verificare che l'opzione **Enable Eye Gaze Input Capability** (Abilita la funzionalità di input mediante sguardo fisso) sia disattivata:</span><span class="sxs-lookup"><span data-stu-id="5e89e-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Finestra MRTK Project Configurator di Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="5e89e-105">La funzionalità di input mediante sguardo fisso dovrebbe essere stata abilitata durante la configurazione delle istruzioni riportate in [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) (Applicare le impostazioni del Configuratore del progetto MRTK) quando è stato configurato il progetto Unity all'inizio di questa serie di esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="5e89e-105">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="5e89e-106">Se, tuttavia, non è abilitata, assicurarsi di farlo ora.</span><span class="sxs-lookup"><span data-stu-id="5e89e-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="5e89e-107">Nella finestra gerarchia selezionare l'oggetto MixedRealityToolkit, quindi nella finestra di controllo passare alla scheda input:</span><span class="sxs-lookup"><span data-stu-id="5e89e-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="5e89e-108">Espandere i **provider di dati di input** e fare clic sul pulsante **+ Aggiungi provider di dati** per aggiungere una nuova provider di dati</span><span class="sxs-lookup"><span data-stu-id="5e89e-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Aggiunta del provider di dati oculisti 1](../images/mr-learning-base/base-08-section1-step1-2.png)

<span data-ttu-id="5e89e-110">Assegnare **Microsoft. MixedReality. Toolkit. WindowsMixedReality. input**  >  **WindowsMixedRealityEyeGazeProvider** al campo **Type** del nuovo provider di dati.</span><span class="sxs-lookup"><span data-stu-id="5e89e-110">Assign **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![Aggiunta del provider di dati oculisti 2](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="5e89e-112">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="5e89e-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="5e89e-113">Verifica della capacità di input degli occhi e aggiunta degli occhi provider di dati</span><span class="sxs-lookup"><span data-stu-id="5e89e-113">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="5e89e-114">Nella finestra gerarchia selezionare l'oggetto MixedRealityToolkit, quindi nella finestra di controllo passare alla scheda input:</span><span class="sxs-lookup"><span data-stu-id="5e89e-114">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="5e89e-115">Espandere i **provider di dati di input** e fare clic sul pulsante **+ Aggiungi provider di dati** per aggiungere una nuova provider di dati</span><span class="sxs-lookup"><span data-stu-id="5e89e-115">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Aggiunta del provider di dati oculisti 1](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

<span data-ttu-id="5e89e-117">Assegnare **Microsoft. MixedReality. Toolkit. XRSDK. OpenXR. input**  >  **WindowsMixedRealityEyeGazeProvider** al campo **Type** del nuovo provider di dati.</span><span class="sxs-lookup"><span data-stu-id="5e89e-117">Assign **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![Aggiunta del provider di dati oculisti 2](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="5e89e-119">WSA legacy</span><span class="sxs-lookup"><span data-stu-id="5e89e-119">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="5e89e-120">Verifica dell'abilitazione della funzionalità di input mediante sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="5e89e-120">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="5e89e-121">Nel menu di Unity selezionare Mixed Reality Toolkit > Utilities > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) e quindi, nella sezione **UWP Capabilities** (Funzionalità UWP), verificare che l'opzione **Enable Eye Gaze Input Capability** (Abilita la funzionalità di input mediante sguardo fisso) sia disattivata:</span><span class="sxs-lookup"><span data-stu-id="5e89e-121">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Finestra MRTK Project Configurator di Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="5e89e-123">La funzionalità di input mediante sguardo fisso dovrebbe essere stata abilitata durante la configurazione delle istruzioni riportate in [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) (Applicare le impostazioni del Configuratore del progetto MRTK) quando è stato configurato il progetto Unity all'inizio di questa serie di esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="5e89e-123">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="5e89e-124">Se, tuttavia, non è abilitata, assicurarsi di farlo ora.</span><span class="sxs-lookup"><span data-stu-id="5e89e-124">However, if it is not enabled, make sure you enable it now.</span></span>
