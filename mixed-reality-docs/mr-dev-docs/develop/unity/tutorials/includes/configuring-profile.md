---
ms.openlocfilehash: 5d3f5b1dd0600404e534023e3bf7b6fcaf7fe8f6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097790"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="19af3-101">Plug-in Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="19af3-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="19af3-102">1. Clonare il profilo di configurazione predefinito</span><span class="sxs-lookup"><span data-stu-id="19af3-102">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="19af3-103">Il profilo di configurazione è il profilo di primo livello.</span><span class="sxs-lookup"><span data-stu-id="19af3-103">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="19af3-104">Di conseguenza, prima di modificare altri profili, devi clonare il profilo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="19af3-104">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="19af3-105">Nella finestra gerarchia selezionare l'oggetto **MixedRealityToolkit** , quindi nella finestra di controllo verificare che il profilo di configurazione **MixedRealityToolkit** sia impostato su **DefaultXRSDKConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="19af3-105">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultXRSDKConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit di Unity con DefaultHoloLens2ConfigurationProfile selezionato](../images/mr-learning-base/base-03-section1-step1-1xrsdk.png)

<span data-ttu-id="19af3-107">Con l'oggetto **MixedRealityToolkit** ancora selezionato, nella finestra Inspector (Controllo) fai clic sul pulsante **Copy & Customize** (Copia e personalizza) per aprire la finestra Clone Profile (Clona profilo):</span><span class="sxs-lookup"><span data-stu-id="19af3-107">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Pulsante Copy & Customize del componente MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step1-2xrsdk.png)

<span data-ttu-id="19af3-109">Nella finestra profilo clone immettere un **nome di profilo** adatto, ad esempio _GettingStarted_XRSDKConfigurationProfile_, quindi fare clic sul pulsante **clona** per creare una copia modificabile del **DefaultXRSDKConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="19af3-109">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKConfigurationProfile**:</span></span>

![Finestra popup per clonare il profilo di configurazione di MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step1-3xrsdk.png)

<span data-ttu-id="19af3-111">Il profilo di configurazione appena creato viene ora assegnato come profilo di configurazione per la scena:</span><span class="sxs-lookup"><span data-stu-id="19af3-111">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Componente MixedRealityToolkit di Unity con l'elemento HoloLens2ConfigurationProfile personalizzato appena creato applicato](../images/mr-learning-base/base-03-section1-step1-4xrsdk.png)

<span data-ttu-id="19af3-113">Nel menu di Unity scegli **File** > **Save** (Salva) per salvare la scena.</span><span class="sxs-lookup"><span data-stu-id="19af3-113">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="19af3-114">Ricordarsi di salvare il lavoro durante l'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="19af3-114">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="19af3-115">2. Abilitare il sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="19af3-115">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="19af3-116">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda **Spatial Awareness** (Consapevolezza spaziale), infine la casella di controllo **Enable Spatial Awareness System** (Abilita sistema di consapevolezza spaziale):</span><span class="sxs-lookup"><span data-stu-id="19af3-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Componente MixedRealityToolkit di Unity con il sistema Spatial Awareness abilitato](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="19af3-118">Per i progetti futuri, se non è necessario che l'app risponda o interagisca con l'ambiente, è consigliabile che il sistema Spatial Awareness rimanga disabilitato per ridurre l'impatto in termini di prestazioni.</span><span class="sxs-lookup"><span data-stu-id="19af3-118">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="19af3-119">3. Clonare il profilo predefinito del sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="19af3-119">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="19af3-120">Nella scheda **Spatial Awareness** (Consapevolezza spaziale) fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):</span><span class="sxs-lookup"><span data-stu-id="19af3-120">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit di Unity con la scheda Spatial Awareness selezionata](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="19af3-122">Nella finestra profilo clone immettere un **nome di profilo** adatto, ad esempio _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, quindi fare clic sul pulsante **clona** per creare una copia modificabile del **DefaultXRSDKSpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="19af3-122">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![Finestra popup per clonare il profilo del sistema Spatial Awareness di MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="19af3-124">Il profilo del sistema di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo di configurazione:</span><span class="sxs-lookup"><span data-stu-id="19af3-124">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Componente MixedRealityToolkit di Unity con l'elemento MixedRealitySpatialAwarenessSystemProfile personalizzato appena creato applicato](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="19af3-126">4. Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="19af3-126">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="19af3-127">Con la scheda **consapevolezza spaziale** ancora selezionata, espandere la sezione **Observer SDK Windows Mixed Reality Spatial mesh** , quindi fare clic sul pulsante **clona** per aprire la finestra profilo Clone:</span><span class="sxs-lookup"><span data-stu-id="19af3-127">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit di Unity con la sezione Windows Mixed Reality Spatial Mesh Observer espansa](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="19af3-129">Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="19af3-129">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Finestra popup per clonare il profilo di Spatial Mesh Observer di MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="19af3-131">Il profilo dell'osservatore della mesh di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo del sistema di consapevolezza spaziale:</span><span class="sxs-lookup"><span data-stu-id="19af3-131">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Componente MixedRealityToolkit di Unity con l'elemento MixedRealitySpatialAwarenessMeshObserverProfile personalizzato appena creato applicato](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="19af3-133">5. Modificare la visibilità della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="19af3-133">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="19af3-134">In **Spatial Mesh Observer Settings** (Impostazioni osservatore della mesh spaziale) impostare **Display Option** (Opzione di visualizzazione) su **Occlusion** (Occlusione) per rendere invisibile la mesh di mapping spaziale mentre è ancora funzionante:</span><span class="sxs-lookup"><span data-stu-id="19af3-134">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Componente MixedRealityToolkit di Unity con l'opzione Display Option di Spatial Mesh Observer impostata su Occlusion](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="19af3-136">Anche se non è visibile, la mesh di mapping spaziale è comunque presente e funzionante.</span><span class="sxs-lookup"><span data-stu-id="19af3-136">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="19af3-137">Ad esempio, gli ologrammi dietro la mesh di mapping spaziale, come nel caso di un ologramma dietro a un muro fisico, non saranno visibili.</span><span class="sxs-lookup"><span data-stu-id="19af3-137">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="19af3-138">hai appreso come modificare un'impostazione nel profilo di MRTK.</span><span class="sxs-lookup"><span data-stu-id="19af3-138">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="19af3-139">Come si può notare, per personalizzare le impostazioni di MRTK, è necessario prima creare copie dei profili predefiniti.</span><span class="sxs-lookup"><span data-stu-id="19af3-139">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="19af3-140">Poiché i profili predefiniti non sono modificabili, saranno sempre presenti come riferimento in caso di ripristino delle impostazioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="19af3-140">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="19af3-141">Per altre informazioni sui profili di MRTK e sulla loro architettura, consultare la [guida alla configurazione dei profili di MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) nel [portale della documentazione di MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="19af3-141">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="19af3-142">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="19af3-142">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="19af3-143">1. Clonare il profilo di configurazione predefinito</span><span class="sxs-lookup"><span data-stu-id="19af3-143">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="19af3-144">Il profilo di configurazione è il profilo di primo livello.</span><span class="sxs-lookup"><span data-stu-id="19af3-144">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="19af3-145">Di conseguenza, prima di modificare altri profili, devi clonare il profilo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="19af3-145">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="19af3-146">Nella finestra gerarchia selezionare l'oggetto **MixedRealityToolkit** , quindi nella finestra di controllo verificare che il profilo di configurazione **MixedRealityToolkit** sia impostato su **DefaultOpenXRConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="19af3-146">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultOpenXRConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit Unity con profilo openXR predefinito selezionato](../images/mr-learning-base/base-03-section1-step1-1openxr.png)

<span data-ttu-id="19af3-148">Con l'oggetto **MixedRealityToolkit** ancora selezionato, nella finestra Inspector (Controllo) fai clic sul pulsante **Copy & Customize** (Copia e personalizza) per aprire la finestra Clone Profile (Clona profilo):</span><span class="sxs-lookup"><span data-stu-id="19af3-148">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Copia del componente MixedRealityToolkit di Unity & pulsante Personalizza per il profilo openxr](../images/mr-learning-base/base-03-section1-step1-2openxr.png)

<span data-ttu-id="19af3-150">Nella finestra profilo clone immettere un **nome di profilo** adatto, ad esempio _GettingStarted_OpenXRConfigurationProfile_, quindi fare clic sul pulsante **clona** per creare una copia modificabile del **DefaultOpenXRConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="19af3-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_OpenXRConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultOpenXRConfigurationProfile**:</span></span>

![Finestra popup del profilo di configurazione di Unity MixedRealityToolkit Clone per profilo openxr](../images/mr-learning-base/base-03-section1-step1-3openxr.png)

<span data-ttu-id="19af3-152">Il profilo di configurazione appena creato viene ora assegnato come profilo di configurazione per la scena:</span><span class="sxs-lookup"><span data-stu-id="19af3-152">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Componente MixedRealityToolkit Unity con OpenXR personalizzato appena creato applicato](../images/mr-learning-base/base-03-section1-step1-4openxr.png)

<span data-ttu-id="19af3-154">Nel menu di Unity scegli **File** > **Save** (Salva) per salvare la scena.</span><span class="sxs-lookup"><span data-stu-id="19af3-154">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="19af3-155">Ricordarsi di salvare il lavoro durante l'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="19af3-155">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="19af3-156">2. Abilitare il sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="19af3-156">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="19af3-157">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda **Spatial Awareness** (Consapevolezza spaziale), infine la casella di controllo **Enable Spatial Awareness System** (Abilita sistema di consapevolezza spaziale):</span><span class="sxs-lookup"><span data-stu-id="19af3-157">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Componente MixedRealityToolkit di Unity con il sistema Spatial Awareness abilitato](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="19af3-159">Per i progetti futuri, se non è necessario che l'app risponda o interagisca con l'ambiente, è consigliabile che il sistema Spatial Awareness rimanga disabilitato per ridurre l'impatto in termini di prestazioni.</span><span class="sxs-lookup"><span data-stu-id="19af3-159">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="19af3-160">3. Clonare il profilo predefinito del sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="19af3-160">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="19af3-161">Nella scheda **Spatial Awareness** (Consapevolezza spaziale) fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):</span><span class="sxs-lookup"><span data-stu-id="19af3-161">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit di Unity con la scheda Spatial Awareness selezionata](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="19af3-163">Nella finestra profilo clone immettere un **nome di profilo** adatto, ad esempio GettingStarted_OpenXRSpatialAwarenessSystemProfile, quindi fare clic sul pulsante **clona** per creare una copia modificabile del **DefaultXRSDKSpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="19af3-163">In the Clone Profile window, enter a suitable **Profile Name**, for example, GettingStarted_OpenXRSpatialAwarenessSystemProfile, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![Finestra popup per clonare il profilo del sistema Spatial Awareness di MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="19af3-165">Il profilo del sistema di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo di configurazione:</span><span class="sxs-lookup"><span data-stu-id="19af3-165">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Componente MixedRealityToolkit di Unity con l'elemento MixedRealitySpatialAwarenessSystemProfile personalizzato appena creato applicato](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="19af3-167">4. Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="19af3-167">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="19af3-168">Con la scheda **consapevolezza spaziale** ancora selezionata, espandere la sezione **Observer SDK Windows Mixed Reality Spatial mesh** , quindi fare clic sul pulsante **clona** per aprire la finestra profilo Clone:</span><span class="sxs-lookup"><span data-stu-id="19af3-168">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit di Unity con la sezione Windows Mixed Reality Spatial Mesh Observer espansa](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="19af3-170">Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="19af3-170">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Finestra popup per clonare il profilo di Spatial Mesh Observer di MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="19af3-172">Il profilo dell'osservatore della mesh di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo del sistema di consapevolezza spaziale:</span><span class="sxs-lookup"><span data-stu-id="19af3-172">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Componente MixedRealityToolkit di Unity con l'elemento MixedRealitySpatialAwarenessMeshObserverProfile personalizzato appena creato applicato](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="19af3-174">5. Modificare la visibilità della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="19af3-174">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="19af3-175">In **Spatial Mesh Observer Settings** (Impostazioni osservatore della mesh spaziale) impostare **Display Option** (Opzione di visualizzazione) su **Occlusion** (Occlusione) per rendere invisibile la mesh di mapping spaziale mentre è ancora funzionante:</span><span class="sxs-lookup"><span data-stu-id="19af3-175">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Componente MixedRealityToolkit di Unity con l'opzione Display Option di Spatial Mesh Observer impostata su Occlusion](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="19af3-177">Anche se non è visibile, la mesh di mapping spaziale è comunque presente e funzionante.</span><span class="sxs-lookup"><span data-stu-id="19af3-177">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="19af3-178">Ad esempio, gli ologrammi dietro la mesh di mapping spaziale, come nel caso di un ologramma dietro a un muro fisico, non saranno visibili.</span><span class="sxs-lookup"><span data-stu-id="19af3-178">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="19af3-179">hai appreso come modificare un'impostazione nel profilo di MRTK.</span><span class="sxs-lookup"><span data-stu-id="19af3-179">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="19af3-180">Come si può notare, per personalizzare le impostazioni di MRTK, è necessario prima creare copie dei profili predefiniti.</span><span class="sxs-lookup"><span data-stu-id="19af3-180">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="19af3-181">Poiché i profili predefiniti non sono modificabili, saranno sempre presenti come riferimento in caso di ripristino delle impostazioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="19af3-181">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="19af3-182">Per altre informazioni sui profili di MRTK e sulla loro architettura, consultare la [guida alla configurazione dei profili di MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) nel [portale della documentazione di MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="19af3-182">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="19af3-183">WSA legacy</span><span class="sxs-lookup"><span data-stu-id="19af3-183">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="19af3-184">1. Clonare il profilo di configurazione predefinito</span><span class="sxs-lookup"><span data-stu-id="19af3-184">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="19af3-185">Il profilo di configurazione è il profilo di primo livello.</span><span class="sxs-lookup"><span data-stu-id="19af3-185">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="19af3-186">Di conseguenza, prima di modificare altri profili, devi clonare il profilo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="19af3-186">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="19af3-187">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) impostare **Configuration Profile** (Profilo di configurazione) di Mixed Reality Toolkit su **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="19af3-187">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit di Unity con DefaultHoloLens2ConfigurationProfile selezionato](../images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="19af3-189">Con l'oggetto **MixedRealityToolkit** ancora selezionato, nella finestra Inspector (Controllo) fai clic sul pulsante **Copy & Customize** (Copia e personalizza) per aprire la finestra Clone Profile (Clona profilo):</span><span class="sxs-lookup"><span data-stu-id="19af3-189">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Pulsante Copy & Customize del componente MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="19af3-191">Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_HoloLens2ConfigurationProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="19af3-191">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![Finestra popup per clonare il profilo di configurazione di MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="19af3-193">Il profilo di configurazione appena creato viene ora assegnato come profilo di configurazione per la scena:</span><span class="sxs-lookup"><span data-stu-id="19af3-193">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Componente MixedRealityToolkit di Unity con l'elemento HoloLens2ConfigurationProfile personalizzato appena creato applicato](../images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="19af3-195">Nel menu di Unity scegli **File** > **Save** (Salva) per salvare la scena.</span><span class="sxs-lookup"><span data-stu-id="19af3-195">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="19af3-196">Ricordarsi di salvare il lavoro durante l'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="19af3-196">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="19af3-197">2. Abilitare il sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="19af3-197">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="19af3-198">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda **Spatial Awareness** (Consapevolezza spaziale), infine la casella di controllo **Enable Spatial Awareness System** (Abilita sistema di consapevolezza spaziale):</span><span class="sxs-lookup"><span data-stu-id="19af3-198">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Componente MixedRealityToolkit di Unity con il sistema Spatial Awareness abilitato](../images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="19af3-200">Per i progetti futuri, se non è necessario che l'app risponda o interagisca con l'ambiente, è consigliabile che il sistema Spatial Awareness rimanga disabilitato per ridurre l'impatto in termini di prestazioni.</span><span class="sxs-lookup"><span data-stu-id="19af3-200">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="19af3-201">3. Clonare il profilo predefinito del sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="19af3-201">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="19af3-202">Nella scheda **Spatial Awareness** (Consapevolezza spaziale) fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):</span><span class="sxs-lookup"><span data-stu-id="19af3-202">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit di Unity con la scheda Spatial Awareness selezionata](../images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="19af3-204">Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="19af3-204">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![Finestra popup per clonare il profilo del sistema Spatial Awareness di MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="19af3-206">Il profilo del sistema di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo di configurazione:</span><span class="sxs-lookup"><span data-stu-id="19af3-206">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Componente MixedRealityToolkit di Unity con l'elemento MixedRealitySpatialAwarenessSystemProfile personalizzato appena creato applicato](../images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="19af3-208">4. Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="19af3-208">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="19af3-209">Con la scheda **Spatial Awareness** (Consapevolezza spaziale) ancora selezionata, espandi la sezione **Windows Mixed Reality Spatial Mesh Observer** (Osservatore mesh spaziale Windows Mixed Reality) e quindi fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):</span><span class="sxs-lookup"><span data-stu-id="19af3-209">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit di Unity con la sezione Windows Mixed Reality Spatial Mesh Observer espansa](../images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="19af3-211">Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="19af3-211">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Finestra popup per clonare il profilo di Spatial Mesh Observer di MixedRealityToolkit di Unity](../images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="19af3-213">Il profilo dell'osservatore della mesh di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo del sistema di consapevolezza spaziale:</span><span class="sxs-lookup"><span data-stu-id="19af3-213">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Componente MixedRealityToolkit di Unity con l'elemento MixedRealitySpatialAwarenessMeshObserverProfile personalizzato appena creato applicato](../images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="19af3-215">5. Modificare la visibilità della mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="19af3-215">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="19af3-216">In **Spatial Mesh Observer Settings** (Impostazioni osservatore della mesh spaziale) impostare **Display Option** (Opzione di visualizzazione) su **Occlusion** (Occlusione) per rendere invisibile la mesh di mapping spaziale mentre è ancora funzionante:</span><span class="sxs-lookup"><span data-stu-id="19af3-216">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Componente MixedRealityToolkit di Unity con l'opzione Display Option di Spatial Mesh Observer impostata su Occlusion](../images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="19af3-218">Anche se non è visibile, la mesh di mapping spaziale è comunque presente e funzionante.</span><span class="sxs-lookup"><span data-stu-id="19af3-218">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="19af3-219">Ad esempio, gli ologrammi dietro la mesh di mapping spaziale, come nel caso di un ologramma dietro a un muro fisico, non saranno visibili.</span><span class="sxs-lookup"><span data-stu-id="19af3-219">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="19af3-220">hai appreso come modificare un'impostazione nel profilo di MRTK.</span><span class="sxs-lookup"><span data-stu-id="19af3-220">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="19af3-221">Come si può notare, per personalizzare le impostazioni di MRTK, è necessario prima creare copie dei profili predefiniti.</span><span class="sxs-lookup"><span data-stu-id="19af3-221">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="19af3-222">Poiché i profili predefiniti non sono modificabili, saranno sempre presenti come riferimento in caso di ripristino delle impostazioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="19af3-222">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="19af3-223">Per altre informazioni sui profili di MRTK e sulla loro architettura, consultare la [guida alla configurazione dei profili di MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) nel [portale della documentazione di MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="19af3-223">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>
