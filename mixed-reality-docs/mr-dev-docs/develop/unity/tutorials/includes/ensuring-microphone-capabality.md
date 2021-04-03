---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097802"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Plug-in Unity 2019/2020 + Windows XR](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a>Garanzia della capacità del microfono e aggiunta del provider di dati di input vocale

Nel menu di Unity selezionare Mixed Reality Toolkit > Utilities > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) e quindi, nella sezione **UWP Capabilities** (Funzionalità UWP), verificare che l'opzione **Enable Microphone Capability** (Abilita la funzionalità Microfono) sia disattivata:

![Abilitare la funzionalità microfono](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> La funzionalità Microfono dovrebbe essere stata abilitata durante la procedura illustrata in [Applicare le impostazioni di MRTK Project Configurator (Configuratore del progetto MRTK)](../mr-learning-base-02.md#configuring-the-unity-project) quando è stato configurato il progetto Unity all'inizio di questa serie di esercitazioni. Se, tuttavia, non è abilitata, assicurarsi di farlo ora.

Nella finestra gerarchia selezionare l'oggetto MixedRealityToolkit, quindi nella finestra di controllo passare alla scheda input:

* Espandere i **provider di dati di input** e fare clic sul pulsante **+ Aggiungi provider di dati** per aggiungere una nuova provider di dati

![Provider di dati per l'aggiunta di nuovi comandi vocali](../images/mr-learning-base/base-09-section1-step1-2.png)

Assegnare **Microsoft. MixedReality. Toolkit. Windows. input**  >  **WindowsSpeechInputProvider** al campo **Type** del nuovo provider di dati.

![Aggiunta di nuove impostazioni per i comandi vocali](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a>Garanzia della capacità del microfono e aggiunta del provider di dati di input vocale

Nel menu di Unity selezionare Mixed Reality Toolkit > Utilities > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) e quindi, nella sezione **UWP Capabilities** (Funzionalità UWP), verificare che l'opzione **Enable Microphone Capability** (Abilita la funzionalità Microfono) sia disattivata:

![Abilitare la funzionalità microfono per OpenXR](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> La funzionalità Microfono dovrebbe essere stata abilitata durante la procedura illustrata in [Applicare le impostazioni di MRTK Project Configurator (Configuratore del progetto MRTK)](../mr-learning-base-02.md#configuring-the-unity-project) quando è stato configurato il progetto Unity all'inizio di questa serie di esercitazioni. Se, tuttavia, non è abilitata, assicurarsi di farlo ora.

Nella finestra gerarchia selezionare l'oggetto MixedRealityToolkit, quindi nella finestra di controllo passare alla scheda input:

* Espandere i **provider di dati di input** e fare clic sul pulsante **+ Aggiungi provider di dati** per aggiungere una nuova provider di dati

![Aggiunta di nuovi comandi di riconoscimento vocale per OpenXR](../images/mr-learning-base/base-09-section1-step1-2.png)

Assegnare **Microsoft. MixedReality. Toolkit. Windows. input**  >  **WindowsSpeechInputProvider** al campo **Type** del nuovo provider di dati.

![Aggiunta di nuovi comandi di riconoscimento vocale per le impostazioni OpenXR](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[WSA legacy](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a>Verificare che la funzionalità Microfono sia abilitata

Nel menu di Unity selezionare Mixed Reality Toolkit > Utilities > **Configure Unity Project** (Mixed Reality Toolkit > Utilità > Configura progetto Unity) per aprire la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) e quindi, nella sezione **UWP Capabilities** (Funzionalità UWP), verificare che l'opzione **Enable Microphone Capability** (Abilita la funzionalità Microfono) sia disattivata:

![Abilitare la funzionalità microfono](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> La funzionalità Microfono dovrebbe essere stata abilitata durante la procedura illustrata in [Applicare le impostazioni di MRTK Project Configurator (Configuratore del progetto MRTK)](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) quando è stato configurato il progetto Unity all'inizio di questa serie di esercitazioni. Se, tuttavia, non è abilitata, assicurarsi di farlo ora.
