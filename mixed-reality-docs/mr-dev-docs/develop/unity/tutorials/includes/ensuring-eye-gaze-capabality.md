---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097644"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Plug-in Unity 2019/2020 + Windows XR](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a>Verifica della capacità di input degli occhi e aggiunta degli occhi provider di dati

Nel menu di Unity selezionare Mixed Reality Toolkit > Utilities > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) e quindi, nella sezione **UWP Capabilities** (Funzionalità UWP), verificare che l'opzione **Enable Eye Gaze Input Capability** (Abilita la funzionalità di input mediante sguardo fisso) sia disattivata:

![Finestra MRTK Project Configurator di Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> La funzionalità di input mediante sguardo fisso dovrebbe essere stata abilitata durante la configurazione delle istruzioni riportate in [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) (Applicare le impostazioni del Configuratore del progetto MRTK) quando è stato configurato il progetto Unity all'inizio di questa serie di esercitazioni. Se, tuttavia, non è abilitata, assicurarsi di farlo ora.

Nella finestra gerarchia selezionare l'oggetto MixedRealityToolkit, quindi nella finestra di controllo passare alla scheda input:

* Espandere i **provider di dati di input** e fare clic sul pulsante **+ Aggiungi provider di dati** per aggiungere una nuova provider di dati

![Aggiunta del provider di dati oculisti 1](../images/mr-learning-base/base-08-section1-step1-2.png)

Assegnare **Microsoft. MixedReality. Toolkit. WindowsMixedReality. input**  >  **WindowsMixedRealityEyeGazeProvider** al campo **Type** del nuovo provider di dati.

![Aggiunta del provider di dati oculisti 2](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a>Verifica della capacità di input degli occhi e aggiunta degli occhi provider di dati

Nella finestra gerarchia selezionare l'oggetto MixedRealityToolkit, quindi nella finestra di controllo passare alla scheda input:

* Espandere i **provider di dati di input** e fare clic sul pulsante **+ Aggiungi provider di dati** per aggiungere una nuova provider di dati

![Aggiunta del provider di dati oculisti 1](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

Assegnare **Microsoft. MixedReality. Toolkit. XRSDK. OpenXR. input**  >  **WindowsMixedRealityEyeGazeProvider** al campo **Type** del nuovo provider di dati.

![Aggiunta del provider di dati oculisti 2](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[WSA legacy](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>Verifica dell'abilitazione della funzionalità di input mediante sguardo fisso

Nel menu di Unity selezionare Mixed Reality Toolkit > Utilities > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) e quindi, nella sezione **UWP Capabilities** (Funzionalità UWP), verificare che l'opzione **Enable Eye Gaze Input Capability** (Abilita la funzionalità di input mediante sguardo fisso) sia disattivata:

![Finestra MRTK Project Configurator di Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> La funzionalità di input mediante sguardo fisso dovrebbe essere stata abilitata durante la configurazione delle istruzioni riportate in [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) (Applicare le impostazioni del Configuratore del progetto MRTK) quando è stato configurato il progetto Unity all'inizio di questa serie di esercitazioni. Se, tuttavia, non è abilitata, assicurarsi di farlo ora.
