---
ms.openlocfilehash: 8a7253f4d151911fa0de3e60ccec1712df0956df
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2021
ms.locfileid: "105983457"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Plug-in Unity 2019/2020 + Windows XR](#tab/winxr)

### <a name="1-clone-the-default-configuration-profile"></a>1. Clonare il profilo di configurazione predefinito

> [!NOTE]
> Il profilo di configurazione è il profilo di primo livello. Di conseguenza, prima di modificare altri profili, devi clonare il profilo di configurazione.

Nella finestra gerarchia selezionare l'oggetto **MixedRealityToolkit** , quindi nella finestra di controllo verificare che il profilo di configurazione **MixedRealityToolkit** sia impostato su **DefaultXRSDKConfigurationProfile**:

![Componente MixedRealityToolkit di Unity con DefaultHoloLens2ConfigurationProfile selezionato](../images/mr-learning-base/base-03-section1-step1-1xrsdk.png)

Con l'oggetto **MixedRealityToolkit** ancora selezionato, nella finestra Inspector (Controllo) fai clic sul pulsante **Copy & Customize** (Copia e personalizza) per aprire la finestra Clone Profile (Clona profilo):

![Pulsante Copy & Customize del componente MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step1-2xrsdk.png)

Nella finestra profilo clone immettere un **nome di profilo** adatto, ad esempio _GettingStarted_XRSDKConfigurationProfile_, quindi fare clic sul pulsante **clona** per creare una copia modificabile del **DefaultXRSDKConfigurationProfile**:

![Finestra popup per clonare il profilo di configurazione di MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step1-3xrsdk.png)

Il profilo di configurazione appena creato viene ora assegnato come profilo di configurazione per la scena:

![Componente MixedRealityToolkit di Unity con l'elemento HoloLens2ConfigurationProfile personalizzato appena creato applicato](../images/mr-learning-base/base-03-section1-step1-4xrsdk.png)

Nel menu di Unity scegli **File** > **Save** (Salva) per salvare la scena.

> [!TIP]
> Ricordarsi di salvare il lavoro durante l'esercitazione.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Abilitare il sistema di consapevolezza spaziale

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda **Spatial Awareness** (Consapevolezza spaziale), infine la casella di controllo **Enable Spatial Awareness System** (Abilita sistema di consapevolezza spaziale):

![Componente MixedRealityToolkit di Unity con il sistema Spatial Awareness abilitato](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> Per i progetti futuri, se non è necessario che l'app risponda o interagisca con l'ambiente, è consigliabile che il sistema Spatial Awareness rimanga disabilitato per ridurre l'impatto in termini di prestazioni.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Clonare il profilo predefinito del sistema di consapevolezza spaziale

Nella scheda **Spatial Awareness** (Consapevolezza spaziale) fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):

![Componente MixedRealityToolkit di Unity con la scheda Spatial Awareness selezionata](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

Nella finestra profilo clone immettere un **nome di profilo** adatto, ad esempio _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, quindi fare clic sul pulsante **clona** per creare una copia modificabile del **DefaultXRSDKSpatialAwarenessSystemProfile**:

![Finestra popup per clonare il profilo del sistema Spatial Awareness di MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

Il profilo del sistema di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo di configurazione:

![Componente MixedRealityToolkit di Unity con l'elemento MixedRealitySpatialAwarenessSystemProfile personalizzato appena creato applicato](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale

Con la scheda **consapevolezza spaziale** ancora selezionata, espandere la sezione **Observer SDK Windows Mixed Reality Spatial mesh** , quindi fare clic sul pulsante **clona** per aprire la finestra profilo Clone:

![Componente MixedRealityToolkit di Unity con la sezione Windows Mixed Reality Spatial Mesh Observer espansa](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![Finestra popup per clonare il profilo di Spatial Mesh Observer di MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

Il profilo dell'osservatore della mesh di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo del sistema di consapevolezza spaziale:

![Componente MixedRealityToolkit di Unity con l'elemento MixedRealitySpatialAwarenessMeshObserverProfile personalizzato appena creato applicato](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Modificare la visibilità della mesh di consapevolezza spaziale

In **Spatial Mesh Observer Settings** (Impostazioni osservatore della mesh spaziale) impostare **Display Option** (Opzione di visualizzazione) su **Occlusion** (Occlusione) per rendere invisibile la mesh di mapping spaziale mentre è ancora funzionante:

![Componente MixedRealityToolkit di Unity con l'opzione Display Option di Spatial Mesh Observer impostata su Occlusion](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> Anche se non è visibile, la mesh di mapping spaziale è comunque presente e funzionante. Ad esempio, gli ologrammi dietro la mesh di mapping spaziale, come nel caso di un ologramma dietro a un muro fisico, non saranno visibili.

hai appreso come modificare un'impostazione nel profilo di MRTK. Come si può notare, per personalizzare le impostazioni di MRTK, è necessario prima creare copie dei profili predefiniti. Poiché i profili predefiniti non sono modificabili, saranno sempre presenti come riferimento in caso di ripristino delle impostazioni predefinite. Per altre informazioni sui profili di MRTK e sulla loro architettura, consultare la [guida alla configurazione dei profili di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).


# <a name="legacy-wsa"></a>[WSA legacy](#tab/wsa)

### <a name="1-clone-the-default-configuration-profile"></a>1. Clonare il profilo di configurazione predefinito

> [!NOTE]
> Il profilo di configurazione è il profilo di primo livello. Di conseguenza, prima di modificare altri profili, devi clonare il profilo di configurazione.

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) impostare **Configuration Profile** (Profilo di configurazione) di Mixed Reality Toolkit su **DefaultHoloLens2ConfigurationProfile**:

![Componente MixedRealityToolkit di Unity con DefaultHoloLens2ConfigurationProfile selezionato](../images/mr-learning-base/base-03-section1-step1-1.png)

Con l'oggetto **MixedRealityToolkit** ancora selezionato, nella finestra Inspector (Controllo) fai clic sul pulsante **Copy & Customize** (Copia e personalizza) per aprire la finestra Clone Profile (Clona profilo):

![Pulsante Copy & Customize del componente MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step1-2.png)

Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_HoloLens2ConfigurationProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultHololens2ConfigurationProfile**:

![Finestra popup per clonare il profilo di configurazione di MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step1-3.png)

Il profilo di configurazione appena creato viene ora assegnato come profilo di configurazione per la scena:

![Componente MixedRealityToolkit di Unity con l'elemento HoloLens2ConfigurationProfile personalizzato appena creato applicato](../images/mr-learning-base/base-03-section1-step1-4.png)

Nel menu di Unity scegli **File** > **Save** (Salva) per salvare la scena.

> [!TIP]
> Ricordarsi di salvare il lavoro durante l'esercitazione.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Abilitare il sistema di consapevolezza spaziale

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda **Spatial Awareness** (Consapevolezza spaziale), infine la casella di controllo **Enable Spatial Awareness System** (Abilita sistema di consapevolezza spaziale):

![Componente MixedRealityToolkit di Unity con il sistema Spatial Awareness abilitato](../images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> Per i progetti futuri, se non è necessario che l'app risponda o interagisca con l'ambiente, è consigliabile che il sistema Spatial Awareness rimanga disabilitato per ridurre l'impatto in termini di prestazioni.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Clonare il profilo predefinito del sistema di consapevolezza spaziale

Nella scheda **Spatial Awareness** (Consapevolezza spaziale) fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):

![Componente MixedRealityToolkit di Unity con la scheda Spatial Awareness selezionata](../images/mr-learning-base/base-03-section1-step3-1.png)

Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessSystemProfile**:

![Finestra popup per clonare il profilo del sistema Spatial Awareness di MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step3-2.png)

Il profilo del sistema di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo di configurazione:

![Componente MixedRealityToolkit di Unity con l'elemento MixedRealitySpatialAwarenessSystemProfile personalizzato appena creato applicato](../images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale

Con la scheda **Spatial Awareness** (Consapevolezza spaziale) ancora selezionata, espandi la sezione **Windows Mixed Reality Spatial Mesh Observer** (Osservatore mesh spaziale Windows Mixed Reality) e quindi fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):

![Componente MixedRealityToolkit di Unity con la sezione Windows Mixed Reality Spatial Mesh Observer espansa](../images/mr-learning-base/base-03-section1-step4-1.png)

Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![Finestra popup per clonare il profilo di Spatial Mesh Observer di MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step4-2.png)

Il profilo dell'osservatore della mesh di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo del sistema di consapevolezza spaziale:

![Componente MixedRealityToolkit di Unity con l'elemento MixedRealitySpatialAwarenessMeshObserverProfile personalizzato appena creato applicato](../images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Modificare la visibilità della mesh di consapevolezza spaziale

In **Spatial Mesh Observer Settings** (Impostazioni osservatore della mesh spaziale) impostare **Display Option** (Opzione di visualizzazione) su **Occlusion** (Occlusione) per rendere invisibile la mesh di mapping spaziale mentre è ancora funzionante:

![Componente MixedRealityToolkit di Unity con l'opzione Display Option di Spatial Mesh Observer impostata su Occlusion](../images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> Anche se non è visibile, la mesh di mapping spaziale è comunque presente e funzionante. Ad esempio, gli ologrammi dietro la mesh di mapping spaziale, come nel caso di un ologramma dietro a un muro fisico, non saranno visibili.

hai appreso come modificare un'impostazione nel profilo di MRTK. Come si può notare, per personalizzare le impostazioni di MRTK, è necessario prima creare copie dei profili predefiniti. Poiché i profili predefiniti non sono modificabili, saranno sempre presenti come riferimento in caso di ripristino delle impostazioni predefinite. Per altre informazioni sui profili di MRTK e sulla loro architettura, consultare la [guida alla configurazione dei profili di MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md) nel [portale della documentazione di MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs).
