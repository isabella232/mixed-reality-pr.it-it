---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097802"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="8b290-101">Plug-in Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="8b290-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="8b290-102">Garanzia della capacità del microfono e aggiunta del provider di dati di input vocale</span><span class="sxs-lookup"><span data-stu-id="8b290-102">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="8b290-103">Nel menu di Unity selezionare Mixed Reality Toolkit > Utilities > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) e quindi, nella sezione **UWP Capabilities** (Funzionalità UWP), verificare che l'opzione **Enable Microphone Capability** (Abilita la funzionalità Microfono) sia disattivata:</span><span class="sxs-lookup"><span data-stu-id="8b290-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Abilitare la funzionalità microfono](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="8b290-105">La funzionalità Microfono dovrebbe essere stata abilitata durante la procedura illustrata in [Applicare le impostazioni di MRTK Project Configurator (Configuratore del progetto MRTK)](../mr-learning-base-02.md#configuring-the-unity-project) quando è stato configurato il progetto Unity all'inizio di questa serie di esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="8b290-105">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="8b290-106">Se, tuttavia, non è abilitata, assicurarsi di farlo ora.</span><span class="sxs-lookup"><span data-stu-id="8b290-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="8b290-107">Nella finestra gerarchia selezionare l'oggetto MixedRealityToolkit, quindi nella finestra di controllo passare alla scheda input:</span><span class="sxs-lookup"><span data-stu-id="8b290-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="8b290-108">Espandere i **provider di dati di input** e fare clic sul pulsante **+ Aggiungi provider di dati** per aggiungere una nuova provider di dati</span><span class="sxs-lookup"><span data-stu-id="8b290-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Provider di dati per l'aggiunta di nuovi comandi vocali](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="8b290-110">Assegnare **Microsoft. MixedReality. Toolkit. Windows. input**  >  **WindowsSpeechInputProvider** al campo **Type** del nuovo provider di dati.</span><span class="sxs-lookup"><span data-stu-id="8b290-110">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![Aggiunta di nuove impostazioni per i comandi vocali](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="8b290-112">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="8b290-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="8b290-113">Garanzia della capacità del microfono e aggiunta del provider di dati di input vocale</span><span class="sxs-lookup"><span data-stu-id="8b290-113">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="8b290-114">Nel menu di Unity selezionare Mixed Reality Toolkit > Utilities > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) e quindi, nella sezione **UWP Capabilities** (Funzionalità UWP), verificare che l'opzione **Enable Microphone Capability** (Abilita la funzionalità Microfono) sia disattivata:</span><span class="sxs-lookup"><span data-stu-id="8b290-114">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Abilitare la funzionalità microfono per OpenXR](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="8b290-116">La funzionalità Microfono dovrebbe essere stata abilitata durante la procedura illustrata in [Applicare le impostazioni di MRTK Project Configurator (Configuratore del progetto MRTK)](../mr-learning-base-02.md#configuring-the-unity-project) quando è stato configurato il progetto Unity all'inizio di questa serie di esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="8b290-116">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="8b290-117">Se, tuttavia, non è abilitata, assicurarsi di farlo ora.</span><span class="sxs-lookup"><span data-stu-id="8b290-117">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="8b290-118">Nella finestra gerarchia selezionare l'oggetto MixedRealityToolkit, quindi nella finestra di controllo passare alla scheda input:</span><span class="sxs-lookup"><span data-stu-id="8b290-118">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="8b290-119">Espandere i **provider di dati di input** e fare clic sul pulsante **+ Aggiungi provider di dati** per aggiungere una nuova provider di dati</span><span class="sxs-lookup"><span data-stu-id="8b290-119">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Aggiunta di nuovi comandi di riconoscimento vocale per OpenXR](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="8b290-121">Assegnare **Microsoft. MixedReality. Toolkit. Windows. input**  >  **WindowsSpeechInputProvider** al campo **Type** del nuovo provider di dati.</span><span class="sxs-lookup"><span data-stu-id="8b290-121">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![Aggiunta di nuovi comandi di riconoscimento vocale per le impostazioni OpenXR](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="8b290-123">WSA legacy</span><span class="sxs-lookup"><span data-stu-id="8b290-123">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="8b290-124">Verificare che la funzionalità Microfono sia abilitata</span><span class="sxs-lookup"><span data-stu-id="8b290-124">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="8b290-125">Nel menu di Unity selezionare Mixed Reality Toolkit > Utilities > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) e quindi, nella sezione **UWP Capabilities** (Funzionalità UWP), verificare che l'opzione **Enable Microphone Capability** (Abilita la funzionalità Microfono) sia disattivata:</span><span class="sxs-lookup"><span data-stu-id="8b290-125">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Abilitare la funzionalità microfono](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="8b290-127">La funzionalità Microfono dovrebbe essere stata abilitata durante la procedura illustrata in [Applicare le impostazioni di MRTK Project Configurator (Configuratore del progetto MRTK)](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) quando è stato configurato il progetto Unity all'inizio di questa serie di esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="8b290-127">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="8b290-128">Se, tuttavia, non è abilitata, assicurarsi di farlo ora.</span><span class="sxs-lookup"><span data-stu-id="8b290-128">However, if it is not enabled, make sure you enable it now.</span></span>
