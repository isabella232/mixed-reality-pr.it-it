---
ms.openlocfilehash: 0c25f726c391c1485efab26828d2bfe4a6468f8b
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112397045"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="d7564-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="d7564-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="d7564-102">Dopo **aver aperto MixedRealityFeatureTool,** per  accedere alle  versioni di  anteprima fare clic su Impostazioni e abilitare Mostra versioni di anteprima nella scheda Funzionalità, quindi fare clic su **OK** per salvare le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="d7564-102">Once **MixedRealityFeatureTool** is opened, to access preview releases click on **Settings** and enable **Show preview releases** under **Feature** tab, then click on **ok** to save the settings.</span></span>

![MixedRealityFeatureTool (anteprima)](../images/mr-learning-base/base-02-section4-step1-2-preview.PNG)

<span data-ttu-id="d7564-104">Fare clic su **Start (Avvia)** per iniziare a usare mixed reality feature tool (Strumento per le funzionalità di realtà mista).</span><span class="sxs-lookup"><span data-stu-id="d7564-104">next click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

![MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="d7564-106">Il primo passaggio consiste nel puntare Lo  strumento per  le funzionalità di realtà mista al percorso del progetto usando il pulsante con i puntini di sospensione, fare clic sul pulsante con i tre puntini di sospensione accanto al percorso del progetto e passare alla cartella del progetto nello strumento di esplorazione, ad esempio _D:\MixedRealityLearning\MRTK Tutorials._</span><span class="sxs-lookup"><span data-stu-id="d7564-106">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

![Aggiunta di un percorso Unity per MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="d7564-108">Dopo aver individuato la cartella del progetto, fai clic sul pulsante Apri per tornare a Mixed Reality Feature Tool (Strumento per le funzionalità di realtà mista).</span><span class="sxs-lookup"><span data-stu-id="d7564-108">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="d7564-109">Fare quindi clic **su Individua funzionalità**.</span><span class="sxs-lookup"><span data-stu-id="d7564-109">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="d7564-110">La finestra di dialogo visualizzata quando si esplora la cartella del progetto Unity contiene "_" come nome del file.</span><span class="sxs-lookup"><span data-stu-id="d7564-110">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="d7564-111">Per consentire la selezione della cartella, è necessario che sia presente un valore per il nome del file.</span><span class="sxs-lookup"><span data-stu-id="d7564-111">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="d7564-112">Lo strumento di funzionalità di realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="d7564-112">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="d7564-113">La cartella deve contenere le cartelle Assets, Packages e Project Settings.</span><span class="sxs-lookup"><span data-stu-id="d7564-113">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="d7564-114">Le funzionalità sono raggruppate per categoria per semplificare l'individuazione, fai clic sull'elenco a discesa **Mixed Reality Toolkit** per trovare i pacchetti relativi a Mixed Reality Toolkit e fai clic sull'elenco a discesa Platform **Support** (Supporto piattaforma) per trovare i pacchetti relativi alle varie piattaforme di supporto.</span><span class="sxs-lookup"><span data-stu-id="d7564-114">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit and click on **Platform Support** dropdown to find packages relating various supporting platforms.</span></span>

![Funzionalità di individuazione di MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-4-openxr.png)

<span data-ttu-id="d7564-116">Controlla **Mixed Reality Toolkit Foundation** e fai clic sull'elenco a discesa accanto a esso per selezionare **MRTK 2.7.0,** controlla anche **Mixed Reality OpenXR Plugin (Plug-in OpenXR** realtà mista) e fai clic sull'elenco a discesa accanto per selezionare la versione più recente disponibile, quindi fai clic sul pulsante **Get features** (Ottieni funzionalità) per scaricare i pacchetti selezionati.</span><span class="sxs-lookup"><span data-stu-id="d7564-116">check the **Mixed Reality Toolkit Foundation** and click on the dropdown next to it to select **MRTK 2.7.0**, also check the **Mixed Reality OpenXR Plugin** and click on the dropdown next to it to select most recent version available, then click on **Get features** button to download the selected packages.</span></span>

![MixedRealityFeatureTool Open MixedReality](../images/mr-learning-base/base-02-section4-step1-5-openxr.PNG)

<span data-ttu-id="d7564-118">Fare quindi  clic sul pulsante Convalida per convalidare il  pacchetto selezionato. Verrà visualizzata una finestra popup con il messaggio Non sono stati rilevati problemi di convalida fare clic su **OK** per chiudere il popup e fare clic sul **pulsante** Importa.</span><span class="sxs-lookup"><span data-stu-id="d7564-118">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![MixedRealityFeatureTool Selezionare il pacchetto richiesto](../images/mr-learning-base/base-02-section4-step1-6-OpenXR.PNG)

<span data-ttu-id="d7564-120">Fare clic **sul pulsante** Approva per aggiungere Mixed **Reality Toolkit** al progetto.</span><span class="sxs-lookup"><span data-stu-id="d7564-120">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![Pacchetto MixedRealityFeatureTool Validate](../images/mr-learning-base/base-02-section4-step1-7-openxr.PNG)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="d7564-122">Configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="d7564-122">Configuring the Unity project</span></span>

<span data-ttu-id="d7564-123">Dopo che Unity ha terminato l'importazione del pacchetto dalla sezione precedente, viene visualizzato un messaggio di avviso per riavviare l'editor di Unity per abilitare i back-end per il nuovo sistema plug-in, fare clic su **Yes (Sì)**</span><span class="sxs-lookup"><span data-stu-id="d7564-123">After Unity has finished importing the package from the previous section, a warning message appears to restart the unity editor to enable to backends for new plugin system, click on **Yes**</span></span>

![Opzione di riavvio di Unity](../images/mr-learning-base/base-02-section5-step1-1-openxr.PNG)

<span data-ttu-id="d7564-125">Dopo il riavvio di Unity verrà visualizzata la finestra MRTK Project Configurator (Configuratore progetto MRTK).</span><span class="sxs-lookup"><span data-stu-id="d7564-125">Once the Unity restarts MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="d7564-126">In caso contrario, è possibile aprirlo manualmente selezionando **Mixed Reality** Toolkit Utilities Configure Project for MRTK (Mixed Reality  >  **Toolkit**  >  **Utilities**  >  **Configure Project for MRTK:**</span><span class="sxs-lookup"><span data-stu-id="d7564-126">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Aprire la finestra di configurazione del progetto MRTK](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

<span data-ttu-id="d7564-128">Fare clic **su Unity OpenXR Plugin (Plug-in OpenXR Unity)** per abilitare la gestione dei plug-in XR e aggiungere i pacchetti necessari al progetto.</span><span class="sxs-lookup"><span data-stu-id="d7564-128">Click on **Unity OpenXR Plugin** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![<span data-ttu-id="d7564-129">Aggiungere il plug-in OpenXR di Unity</span><span class="sxs-lookup"><span data-stu-id="d7564-129">Add Unity OpenXR Plugin</span></span> ](../images/mr-learning-base/base-02-section5-step1-3-openxr.PNG)

<span data-ttu-id="d7564-130">Verranno importati i pacchetti Unity necessari per XR Plugin Management. Al termine, fare clic su **Show XR Plug-In Management Settings** in MRTK project Configurator (Mostra impostazioni di gestione Plug-In XR nel progetto MRTK Configurator).</span><span class="sxs-lookup"><span data-stu-id="d7564-130">This will import required unity packages for XR Plugin Management, once done click on **Show XR Plug-In Management Settings** in MRTK project Configurator.</span></span>

![<span data-ttu-id="d7564-131">Mostra impostazioni di Plug-In XR</span><span class="sxs-lookup"><span data-stu-id="d7564-131">Show XR Plug-In Management Settings</span></span> ](../images/mr-learning-base/base-02-section5-step1-4-openxr.PNG)

<span data-ttu-id="d7564-132">Verrà visualizzata la **finestra Impostazioni progetto**,</span><span class="sxs-lookup"><span data-stu-id="d7564-132">This opens **Project Settings window**,</span></span>

![Abilitare Open XR](../images/mr-learning-base/base-02-section5-step1-5-openxr.PNG)

<span data-ttu-id="d7564-134">Nella finestra Project Settings (Impostazioni progetto) in **XR Plug-in Management (Gestione plug-in XR)** assicurarsi che sia selezionata anche l'opzione piattaforma UWP (Universal Windows Platform) Initialize **XR on Startup** (Inizializza XR all'avvio), quindi selezionare la casella di controllo Open XR (Apri **XR)** e la casella di controllo Microsoft HoloLens **feature set (Set** di funzionalità) per abilitarle.</span><span class="sxs-lookup"><span data-stu-id="d7564-134">In the Project Settings window  under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings also Ensure **Initialize XR on Startup** is checked, then check **Open XR** checkbox and **Microsoft HoloLens feature set** checkbox to enable them.</span></span>

![Finestra Impostazioni progetto 1](../images/mr-learning-base/base-02-section5-step1-6-openxr.PNG)

<span data-ttu-id="d7564-136">Se viene visualizzata un'icona di avviso rossa accanto a **Plug-in OpenXR,** fare clic sull'icona e **selezionare Correggi tutto** prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="d7564-136">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="d7564-137">Per l'applicazione delle modifiche, potrebbe essere necessario riavviare l'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="d7564-137">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Finestra Impostazioni progetto 2](../images/mr-learning-base/base-02-section5-step1-7-openxr.PNG)

<span data-ttu-id="d7564-139">Dopo aver risolto tutti i problemi, chiudere la **finestra Impostazioni** progetto.</span><span class="sxs-lookup"><span data-stu-id="d7564-139">Once all issues are fixed, close the **Project Settings** window.</span></span>

<span data-ttu-id="d7564-140">Nella barra dei menu passare a **Mixed Reality** >  **OpenXR Apply** recommended project settings for HoloLens 2 to get better app performance (Applica le impostazioni di progetto consigliate per la realtà mista per ottenere prestazioni migliori  >   dell'app).</span><span class="sxs-lookup"><span data-stu-id="d7564-140">In the menu bar, navigate to **Mixed Reality**> **OpenXR** > **Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Finestra Impostazioni progetto 3](../images/mr-learning-base/base-02-section5-step1-8-openxr.PNG)

<span data-ttu-id="d7564-142">Usare il menu Unity per aprire MRTK Project Configurator. Nella finestra MRTK Project Configurator (Configuratore progetto MRTK) fare clic su **Next**(Avanti) e quindi sul pulsante **Apply (Applica)** per applicare le impostazioni:</span><span class="sxs-lookup"><span data-stu-id="d7564-142">Use the Unity menu to open MRTK Project Configurator, In the MRTK Project Configurator window, click on **next**, then click the **Apply** button to apply the settings:</span></span>

![Finestra Impostazioni progetto 4](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

<span data-ttu-id="d7564-144">Dopo aver fatto clic su Applica, Unity tenterà di riavviare per applicare il sistema di input, fare clic su **Applica** per riavviare l'editor di Unity</span><span class="sxs-lookup"><span data-stu-id="d7564-144">Once you click on Apply, Unity will try to restart for the input system to take into effect, click on **Apply** to restart the Unity editor</span></span>

![Finestra Impostazioni progetto 5](../images/mr-learning-base/base-02-section5-step1-10-openxr.PNG)

<span data-ttu-id="d7564-146">Dopo il riavvio di Unity, aprire MRTK Project Configurator dal menu di Unity e fare clic su **Next** (Avanti), quindi fare clic su **Done** (Fine) per completare la configurazione del progetto Unity per OpenXR.</span><span class="sxs-lookup"><span data-stu-id="d7564-146">Once the Unity restarts open MRTK Project Configurator from the unity menu and Click on **Next** then click on **Done** finish the Unity project configuration for OpenXR.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="d7564-147">Configurare impostazioni di progetto aggiuntive</span><span class="sxs-lookup"><span data-stu-id="d7564-147">Configure additional project settings</span></span>

<span data-ttu-id="d7564-148">Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:</span><span class="sxs-lookup"><span data-stu-id="d7564-148">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="d7564-149">Nella finestra Project Settings (Impostazioni progetto) selezionare XR Plug-in Management OpenXR (OpenXR gestione **plug-in XR),** quindi usare l'elenco a discesa Depth Submission Mode (Modalità di invio profondità) per selezionare  >   **Depth 16-bit (Profondità a 16 bit):** </span><span class="sxs-lookup"><span data-stu-id="d7564-149">In the Project Settings window, select **XR Plug-in Management** > **OpenXR**, then use the **Depth Submission Mode** dropdown to select **Depth 16-bit**:</span></span>

![Abilitazione di Unity a 16 profondità](../images/mr-learning-base/base-02-section5-step2-1-openxr.PNG)

> [!TIP]
> <span data-ttu-id="d7564-151">La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto.</span><span class="sxs-lookup"><span data-stu-id="d7564-151">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="d7564-152">Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">condivisione del buffer di intensità (HoloLens)</a> della documentazione di MRTK relativa alle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="d7564-152">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="d7564-153">Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="d7564-153">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Impostazioni di pubblicazione di Unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="d7564-156">Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app.</span><span class="sxs-lookup"><span data-stu-id="d7564-156">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="d7564-157">Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.</span><span class="sxs-lookup"><span data-stu-id="d7564-157">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="d7564-158">Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d7564-158">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="d7564-159">Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="d7564-159">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="d7564-160">Unity 2019/2020 + Plug-in Windows XR</span><span class="sxs-lookup"><span data-stu-id="d7564-160">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="d7564-161">Dopo **aver aperto MixedRealityFeatureTool,** per  accedere alle  versioni di  anteprima fare clic su Impostazioni e abilitare Mostra versioni di anteprima nella scheda Funzionalità, quindi fare clic su **OK** per salvare le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="d7564-161">Once **MixedRealityFeatureTool** is opened, to access preview releases click on **Settings** and enable **Show preview releases** under **Feature** tab, then click on **ok** to save the settings.</span></span>

![MixedRealityFeatureTool per l'anteprima](../images/mr-learning-base/base-02-section4-step1-2-preview.PNG)

<span data-ttu-id="d7564-163">Fare quindi clic su **Start (Avvia)** per iniziare a usare mixed reality feature tool (Strumento per le funzionalità di realtà mista).</span><span class="sxs-lookup"><span data-stu-id="d7564-163">Next, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

![<span data-ttu-id="d7564-164">MixedRealityFeatureTool</span><span class="sxs-lookup"><span data-stu-id="d7564-164">MixedRealityFeatureTool</span></span> ](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="d7564-165">Il primo passaggio consiste nel puntare Lo  strumento per  le funzionalità di realtà mista al percorso del progetto usando il pulsante con i puntini di sospensione, fare clic sul pulsante con i tre puntini di sospensione accanto al percorso del progetto e passare alla cartella del progetto nello strumento di esplorazione, ad esempio _D:\MixedRealityLearning\MRTK Tutorials._</span><span class="sxs-lookup"><span data-stu-id="d7564-165">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

![Aggiunta di un percorso Unity per MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="d7564-167">Dopo aver individuato la cartella del progetto, fai clic sul pulsante Apri per tornare a Mixed Reality Feature Tool (Strumento per le funzionalità di realtà mista).</span><span class="sxs-lookup"><span data-stu-id="d7564-167">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="d7564-168">Fare quindi clic **su Individua funzionalità**.</span><span class="sxs-lookup"><span data-stu-id="d7564-168">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="d7564-169">La finestra di dialogo visualizzata quando si esplora la cartella del progetto Unity contiene "_" come nome del file.</span><span class="sxs-lookup"><span data-stu-id="d7564-169">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="d7564-170">Per consentire la selezione della cartella, è necessario che sia presente un valore per il nome del file.</span><span class="sxs-lookup"><span data-stu-id="d7564-170">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="d7564-171">Lo strumento di funzionalità di realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="d7564-171">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="d7564-172">La cartella deve contenere le cartelle Assets, Packages e Project Settings.</span><span class="sxs-lookup"><span data-stu-id="d7564-172">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="d7564-173">Le funzionalità sono raggruppate per categoria per semplificare l'individuazione. Fare clic sull'elenco a discesa **mixed reality toolkit** per trovare i pacchetti relativi a Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="d7564-173">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

![Funzionalità di individuazione di MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-4.PNG)

<span data-ttu-id="d7564-175">Seleziona la casella **per Mixed Reality Toolkit Foundation** e fai clic sull'elenco a discesa accanto per selezionare **MRTK 2.7.0** e quindi fai clic sul pulsante **Get features** (Ottieni funzionalità) per scaricare i pacchetti selezionati.</span><span class="sxs-lookup"><span data-stu-id="d7564-175">Check the box for **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

![MixedRealityFeatureTool Open MixedReality](../images/mr-learning-base/base-02-section4-step1-5.PNG)

<span data-ttu-id="d7564-177">Fare quindi  clic sul pulsante Convalida per convalidare il  pacchetto selezionato. Verrà visualizzata una finestra popup con il messaggio Non sono stati rilevati problemi di convalida fare clic su **OK** per chiudere il popup e fare clic sul **pulsante** Importa.</span><span class="sxs-lookup"><span data-stu-id="d7564-177">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![MixedRealityFeatureTool Selezionare il pacchetto richiesto](../images/mr-learning-base/base-02-section4-step1-6.PNG)

<span data-ttu-id="d7564-179">Fare clic **sul pulsante** Approva per aggiungere Mixed **Reality Toolkit** al progetto.</span><span class="sxs-lookup"><span data-stu-id="d7564-179">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![Pacchetto MixedRealityFeatureTool Validate](../images/mr-learning-base/base-02-section4-step1-7.PNG)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="d7564-181">Configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="d7564-181">Configuring the Unity project</span></span>

<span data-ttu-id="d7564-182">Al termine dell'importazione del pacchetto dalla sezione precedente, viene visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK).</span><span class="sxs-lookup"><span data-stu-id="d7564-182">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="d7564-183">In caso contrario, è possibile aprirlo manualmente selezionando **Mixed Reality** Toolkit Utilities Configure Project for MRTK (Mixed Reality  >  **Toolkit**  >  **Utilities**  >  **Configure Project for MRTK:**</span><span class="sxs-lookup"><span data-stu-id="d7564-183">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![apertura dello strumento di configurazione MRTK](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

<span data-ttu-id="d7564-185">Fare clic **su Built-in Unity Plugin (non-OpenXR) (Plug-in Unity** incorporato ( non OpenXR) per abilitare la gestione dei plug-in XR e aggiungere i pacchetti necessari al progetto.</span><span class="sxs-lookup"><span data-stu-id="d7564-185">Click on **Built-in Unity Plugin(non-OpenXR)** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![ <span data-ttu-id="d7564-186">Strumento di configurazione MRTK</span><span class="sxs-lookup"><span data-stu-id="d7564-186">MRTK configurator tool</span></span>](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> <span data-ttu-id="d7564-187">Lo screenshot precedente è di Unity 2020. Se si usa Unity 2019, selezionare **XR SDK/XR Management**</span><span class="sxs-lookup"><span data-stu-id="d7564-187">The above screenshot is from Unity 2020, if you using Unity 2019 please select **XR SDK/XR Management**</span></span>

<span data-ttu-id="d7564-188">Verranno importati i pacchetti Unity necessari per XR Plugin Management. Al termine, fare clic **su Show Settings** in MRTK project Configurator (Mostra impostazioni nel progetto MRTK Configurator).</span><span class="sxs-lookup"><span data-stu-id="d7564-188">This will import required unity packages for XR Plugin Management, once done click on **Show Settings** in MRTK project Configurator.</span></span>

![Finestra Player settings (Impostazioni lettore)](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

<span data-ttu-id="d7564-190">Verrà visualizzata la finestra Project **Settings**(Impostazioni progetto), nella finestra Project Settings (Impostazioni progetto) in XR Plug-in piattaforma UWP (Universal Windows Platform) Management (Gestione **plug-in XR)** Assicurarsi che sia selezionata anche la casella di controllo Initialize **XR on Startup** (Inizializza XR **all'avvio)** e selezionare la casella di controllo Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="d7564-190">This opens **Project Settings window**, In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings also Ensure **Initialize XR on Startup** is checked, and check **Windows Mixed Reality** checkbox.</span></span>

![Finestra delle impostazioni del lettore Abilita Realtà mista-xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

<span data-ttu-id="d7564-192">Al termine dell'importazione di Windows Mixed Reality SDK, dovrebbe visualizzarsi di nuovo la finestra MRTK Project Configurator (Configuratore del progetto MRTK).</span><span class="sxs-lookup"><span data-stu-id="d7564-192">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="d7564-193">In caso contrario, usa il menu di Unity per aprirla.</span><span class="sxs-lookup"><span data-stu-id="d7564-193">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="d7564-194">Nella finestra MRTK Project Configurator  (Configuratore progetto MRTK) fare clic su Next (Avanti), quindi usare l'elenco a discesa Audio spatializer (Spazializzatore audio) per selezionare **MS HRTF Spatializer (Spazializzatore MS HRTF),** quindi fare clic sul pulsante **Apply (Applica)** per applicare l'impostazione:</span><span class="sxs-lookup"><span data-stu-id="d7564-194">In the MRTK Project Configurator window, click on **next** then use the Audio spatializer dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Configurator-xrsdk del progetto MRTK](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="d7564-196">L'applicazione delle impostazioni predefinite di MRTK è facoltativa ma fortemente consigliata, poiché consente di configurare alcune impostazioni consigliate di Unity:</span><span class="sxs-lookup"><span data-stu-id="d7564-196">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="d7564-197">Set Single Pass Instanced rendering path (Imposta il percorso di rendering con istanze a singolo passaggio): migliora le prestazioni grafiche eseguendo la pipeline di rendering per entrambi gli occhi nella stessa chiamata di disegno.</span><span class="sxs-lookup"><span data-stu-id="d7564-197">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="d7564-198">Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sul [rendering con istanze a singolo passaggio](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) della documentazione di MRTK relativa alle [prestazioni](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).</span><span class="sxs-lookup"><span data-stu-id="d7564-198">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="d7564-199">Set default Spatial Awareness layer (Imposta livello di consapevolezza spaziale predefinito): crea un livello di Unity denominato Spatial Awareness e configura MRTK per l'uso di questo livello per la mesh di consapevolezza spaziale.</span><span class="sxs-lookup"><span data-stu-id="d7564-199">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="d7564-200">Per altre informazioni sui livelli di Unity, vedere la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="d7564-200">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="d7564-201">L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto.</span><span class="sxs-lookup"><span data-stu-id="d7564-201">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="d7564-202">Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata.</span><span class="sxs-lookup"><span data-stu-id="d7564-202">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="d7564-203">Per altre informazioni su questo argomento, è possibile fare riferimento alle esercitazioni  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> sull'audio spaziale</a>.</span><span class="sxs-lookup"><span data-stu-id="d7564-203">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="d7564-204">Fare clic **su Avanti** e quindi **fare** clic su Fine nella finestra MRTK Project Configurator per completare la configurazione del progetto Unity per XRSDK.</span><span class="sxs-lookup"><span data-stu-id="d7564-204">Click on **Next** then click on **Done** in the MRTK Project Configurator window to finish the Unity project configuration for XRSDK.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="d7564-205">Configurare impostazioni di progetto aggiuntive</span><span class="sxs-lookup"><span data-stu-id="d7564-205">Configure additional project settings</span></span>

<span data-ttu-id="d7564-206">Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:</span><span class="sxs-lookup"><span data-stu-id="d7564-206">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="d7564-207">Nella finestra Project Settings (Impostazioni progetto) selezionare XR Plug-in Management Windows Mixed Reality Runtime Settings (Impostazioni runtime **plug-in XR)** e quindi usare l'elenco a discesa Depth Buffer Format (Formato buffer di profondità) per selezionare la profondità  >    >   **a 16 bit:** </span><span class="sxs-lookup"><span data-stu-id="d7564-207">In the Project Settings window, select **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, then use the **Depth Buffer Format** dropdown to select **16-bit depth**:</span></span>

![Unity Abilita 16 profondità](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="d7564-209">La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto.</span><span class="sxs-lookup"><span data-stu-id="d7564-209">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="d7564-210">Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">condivisione del buffer di intensità (HoloLens)</a> della documentazione di MRTK relativa alle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="d7564-210">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="d7564-211">Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="d7564-211">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Impostazioni di pubblicazione unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="d7564-214">Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app.</span><span class="sxs-lookup"><span data-stu-id="d7564-214">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="d7564-215">Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.</span><span class="sxs-lookup"><span data-stu-id="d7564-215">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="d7564-216">Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d7564-216">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="d7564-217">Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="d7564-217">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="d7564-218">Legacy WSA</span><span class="sxs-lookup"><span data-stu-id="d7564-218">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="d7564-219">Dopo **aver aperto MixedRealityFeatureTool,** per accedere alle versioni di anteprima fare clic su **Impostazioni** e abilitare **Mostra** versioni di anteprima nella scheda **Funzionalità,** quindi fare clic su **OK** per salvare le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="d7564-219">Once **MixedRealityFeatureTool** is opened, to access preview releases click on **Settings** and enable **Show preview releases** under **Feature** tab, then click on **ok** to save the settings.</span></span>

![MixedRealityFeatureTool preview](../images/mr-learning-base/base-02-section4-step1-2-preview.PNG)

<span data-ttu-id="d7564-221">Fare clic su **Start per** iniziare a usare Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="d7564-221">next click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

![MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="d7564-223">Il primo passaggio consiste nel puntare lo  strumento di  funzionalità di realtà mista al percorso del progetto usando il pulsante con i puntini di sospensione, fare clic sul pulsante con i puntini di sospensione tre puntini accanto al percorso del progetto e passare alla cartella del progetto in Esplora risorse, ad esempio _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="d7564-223">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

![Aggiunta del percorso Unity per MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="d7564-225">Dopo aver individuato la cartella del progetto, fare clic sul pulsante Apri per tornare a Strumento di funzionalità di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="d7564-225">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="d7564-226">Fare quindi clic su **Individua funzionalità**.</span><span class="sxs-lookup"><span data-stu-id="d7564-226">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="d7564-227">La finestra di dialogo visualizzata quando si esplora la cartella del progetto Unity contiene '_' come nome file.</span><span class="sxs-lookup"><span data-stu-id="d7564-227">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="d7564-228">Per consentire la selezione della cartella, deve essere presente un valore per il nome file.</span><span class="sxs-lookup"><span data-stu-id="d7564-228">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="d7564-229">Lo strumento funzionalità realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella del progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="d7564-229">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="d7564-230">La cartella deve contenere le cartelle Asset, Pacchetti e Impostazioni progetto.</span><span class="sxs-lookup"><span data-stu-id="d7564-230">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="d7564-231">Le funzionalità sono raggruppate per categoria per semplificare l'individuazione, fare clic sull'elenco a discesa **mixed reality toolkit** per trovare i pacchetti relativi a Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="d7564-231">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

![Funzionalità di individuazione degli strumenti MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-4.PNG)

<span data-ttu-id="d7564-233">Selezionare **Mixed Reality Toolkit Foundation** e fare clic sull'elenco a discesa accanto a esso per  selezionare **MRTK 2.7.0,** quindi fare clic sul pulsante Ottieni funzionalità per scaricare i pacchetti selezionati.</span><span class="sxs-lookup"><span data-stu-id="d7564-233">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

![MixedRealityFeatureTool Open MixedReality](../images/mr-learning-base/base-02-section4-step1-5.PNG)

<span data-ttu-id="d7564-235">Fare quindi clic **sul** pulsante Convalida per convalidare il pacchetto selezionato. Verrà visualizzata una finestra popup con il messaggio Nessun problema di convalida rilevato **fare** clic su **OK** per chiudere il popup e fare clic sul **pulsante** Importa.</span><span class="sxs-lookup"><span data-stu-id="d7564-235">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![MixedRealityFeatureTool Selezionare il pacchetto richiesto](../images/mr-learning-base/base-02-section4-step1-6.PNG)

<span data-ttu-id="d7564-237">Fare clic **sul pulsante** Approva per aggiungere Mixed **Reality Toolkit** al progetto.</span><span class="sxs-lookup"><span data-stu-id="d7564-237">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![Pacchetto MixedRealityFeatureTool Validate](../images/mr-learning-base/base-02-section4-step1-7.PNG)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="d7564-239">Configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="d7564-239">Configuring the Unity project</span></span>

<span data-ttu-id="d7564-240">Al termine dell'importazione del pacchetto dalla sezione precedente, viene visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK).</span><span class="sxs-lookup"><span data-stu-id="d7564-240">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="d7564-241">In caso contrario, è possibile aprirlo manualmente in **Mixed Reality**  >  **Toolkit**  >  **Utilities**  >  **Configure Project for MRTK**:</span><span class="sxs-lookup"><span data-stu-id="d7564-241">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Percorso del menu Configure Unity Project di Unity](../images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="d7564-243">Fare clic **su Legacy XR (XR** legacy) per abilitare Legacy XR e aggiungere i pacchetti necessari al progetto.</span><span class="sxs-lookup"><span data-stu-id="d7564-243">Click on **Legacy XR** to enable Legacy XR and to add its required packages  into your project.</span></span>

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

<span data-ttu-id="d7564-245">Fare clic sul pulsante Avanti per abilitare le impostazioni della pipeline XR per Legacy XR.</span><span class="sxs-lookup"><span data-stu-id="d7564-245">Click on next button to enable XR pipeline settings for Legacy XR.</span></span>

![Finestra di configurazione di Unity MRTK](../images/mr-learning-base/base-02-section5-step1-3.PNG)

<span data-ttu-id="d7564-247">Nella finestra MRTK Project Configurator verificare che tutte le opzioni siano selezionate e usare anche l'elenco a discesa **Spazializzatore** audio per selezionare lo spazializzatore **MS HRTF,** quindi fare clic sul pulsante Applica per applicare l'impostazione: </span><span class="sxs-lookup"><span data-stu-id="d7564-247">In the MRTK Project Configurator window, ensure all options are checked and also use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Finestra di configurazione di MRTK](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> <span data-ttu-id="d7564-249">L'applicazione delle impostazioni predefinite di MRTK è facoltativa ma fortemente consigliata, poiché consente di configurare alcune impostazioni consigliate di Unity:</span><span class="sxs-lookup"><span data-stu-id="d7564-249">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="d7564-250">Set Single Pass Instanced rendering path (Imposta il percorso di rendering con istanze a singolo passaggio): migliora le prestazioni grafiche eseguendo la pipeline di rendering per entrambi gli occhi nella stessa chiamata di disegno.</span><span class="sxs-lookup"><span data-stu-id="d7564-250">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="d7564-251">Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sul [rendering con istanze a singolo passaggio](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) della documentazione di MRTK relativa alle [prestazioni](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).</span><span class="sxs-lookup"><span data-stu-id="d7564-251">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="d7564-252">Set default Spatial Awareness layer (Imposta livello di consapevolezza spaziale predefinito): crea un livello di Unity denominato Spatial Awareness e configura MRTK per l'uso di questo livello per la mesh di consapevolezza spaziale.</span><span class="sxs-lookup"><span data-stu-id="d7564-252">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="d7564-253">Per altre informazioni sui livelli di Unity, vedere la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="d7564-253">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="d7564-254">L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto.</span><span class="sxs-lookup"><span data-stu-id="d7564-254">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="d7564-255">Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata.</span><span class="sxs-lookup"><span data-stu-id="d7564-255">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="d7564-256">Per altre informazioni su questo argomento, è possibile fare riferimento alle esercitazioni  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> sull'audio spaziale</a>.</span><span class="sxs-lookup"><span data-stu-id="d7564-256">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="d7564-257">Fare clic **su Avanti** e quindi **fare** clic sul pulsante Fine nella finestra di MRTK Project Configurator per completare la configurazione del progetto Unity per Legacy XR.</span><span class="sxs-lookup"><span data-stu-id="d7564-257">Click on **Next** then click on **Done** button in MRTK Project Configurator window to finish the Unity project configuration for Legacy XR.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="d7564-258">Configurare impostazioni di progetto aggiuntive</span><span class="sxs-lookup"><span data-stu-id="d7564-258">Configure additional project settings</span></span>

<span data-ttu-id="d7564-259">Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:</span><span class="sxs-lookup"><span data-stu-id="d7564-259">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="d7564-260">Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **XR Settings** (Impostazioni XR) e quindi usa l'elenco a discesa **Depth Format** (Formato profondità) per selezionare **16-bit depth** (Profondità a 16 bit):</span><span class="sxs-lookup"><span data-stu-id="d7564-260">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity Abilita 16 profondità](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> <span data-ttu-id="d7564-262">La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto.</span><span class="sxs-lookup"><span data-stu-id="d7564-262">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="d7564-263">Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">condivisione del buffer di intensità (HoloLens)</a> della documentazione di MRTK relativa alle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="d7564-263">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="d7564-264">Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="d7564-264">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Impostazioni di pubblicazione unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="d7564-267">Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app.</span><span class="sxs-lookup"><span data-stu-id="d7564-267">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="d7564-268">Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.</span><span class="sxs-lookup"><span data-stu-id="d7564-268">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="d7564-269">Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d7564-269">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="d7564-270">Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="d7564-270">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>
