---
ms.openlocfilehash: 2420e68a0753739111fc2c5eecfbd1da563f52c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175909"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="1862b-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="1862b-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="1862b-102">Dopo **aver aperto MixedRealityFeatureTool,** fare clic su **Start** per iniziare a usare Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="1862b-102">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="1862b-103">Il primo passaggio consiste nell'puntare Mixed Reality Feature Tool  al percorso **del Project** usando il pulsante con i puntini di sospensione, fare clic sul pulsante con i tre puntini di sospensione accanto al percorso del Project e passare alla cartella del progetto nello strumento di esplorazione, ad esempio _D:\MixedRealityLearning\MRTK Tutorials._</span><span class="sxs-lookup"><span data-stu-id="1862b-103">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="1862b-104">Dopo aver individuato la cartella del progetto, fai clic sul pulsante Apri per tornare a Mixed Reality Feature Tool (Strumento per le funzionalità di realtà mista).</span><span class="sxs-lookup"><span data-stu-id="1862b-104">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="1862b-105">Fare quindi clic **su Individua funzionalità**.</span><span class="sxs-lookup"><span data-stu-id="1862b-105">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="1862b-106">La finestra di dialogo visualizzata quando si esplora la cartella del progetto Unity contiene "_" come nome del file.</span><span class="sxs-lookup"><span data-stu-id="1862b-106">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="1862b-107">Per consentire la selezione della cartella, è necessario che sia presente un valore per il nome del file.</span><span class="sxs-lookup"><span data-stu-id="1862b-107">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="1862b-108">Lo strumento di funzionalità di realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="1862b-108">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="1862b-109">La cartella deve contenere asset, pacchetti e Project Impostazioni cartelle.</span><span class="sxs-lookup"><span data-stu-id="1862b-109">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="1862b-110">Le funzionalità sono raggruppate per categoria per semplificare l'individuazione, fare clic sull'elenco a discesa mixed reality Toolkit (Realtà **mista)** per trovare i pacchetti relativi a Mixed Reality Toolkit e fare clic sull'elenco a discesa **Platform Support** (Supporto piattaforma) per trovare i pacchetti relativi alle varie piattaforme di supporto.</span><span class="sxs-lookup"><span data-stu-id="1862b-110">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit and click on **Platform Support** dropdown to find packages relating various supporting platforms.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="1862b-111">Controllare **Mixed Reality Toolkit Foundation** e fare clic sull'elenco a discesa accanto per selezionare **MRTK 2.7.2,** controllare anche **Mixed Reality OpenXR Plugin 1.0.0** e fare clic sull'elenco a discesa accanto per selezionare la versione più recente disponibile, quindi fare clic sul pulsante Get **features** (Ottieni funzionalità) per scaricare i pacchetti selezionati.</span><span class="sxs-lookup"><span data-stu-id="1862b-111">Check the **Mixed Reality Toolkit Foundation** and click on the dropdown next to it to select **MRTK 2.7.2**, also check the **Mixed Reality OpenXR Plugin 1.0.0** and click on the dropdown next to it to select most recent version available, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

<span data-ttu-id="1862b-112">Fare quindi  clic sul pulsante Convalida per convalidare il  pacchetto selezionato. Verrà visualizzata una finestra popup con il messaggio Non sono stati rilevati problemi di convalida fare clic su **OK** per chiudere il popup e fare clic sul **pulsante** Importa.</span><span class="sxs-lookup"><span data-stu-id="1862b-112">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="1862b-113">Fare clic **sul pulsante** Approva per aggiungere **la** Toolkit realtà mista al progetto.</span><span class="sxs-lookup"><span data-stu-id="1862b-113">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a><span data-ttu-id="1862b-114">Configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="1862b-114">Configuring the Unity project</span></span>

<span data-ttu-id="1862b-115">Dopo che Unity ha terminato l'importazione del pacchetto dalla sezione precedente, viene visualizzato un messaggio di avviso per riavviare l'editor di Unity per abilitare i back-end per il nuovo sistema plug-in, fare clic su **Yes (Sì)**</span><span class="sxs-lookup"><span data-stu-id="1862b-115">After Unity has finished importing the package from the previous section, a warning message appears to restart the unity editor to enable to backends for new plugin system, click on **Yes**</span></span>

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

<span data-ttu-id="1862b-116">Dopo il riavvio di Unity, Project visualizzata la finestra configuratore MRTK.</span><span class="sxs-lookup"><span data-stu-id="1862b-116">Once the Unity restarts MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="1862b-117">In caso contrario, è possibile aprirlo manualmente selezionando **Mixed Reality** Toolkit Utilities Configure Project for MRTK (Configura Project  >    >    >  **per MRTK):**</span><span class="sxs-lookup"><span data-stu-id="1862b-117">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Aprire la finestra di configurazione del progetto MRTK](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

<span data-ttu-id="1862b-119">Fare clic **su Unity OpenXR Plugin (Plug-in OpenXR Unity)** per abilitare la gestione dei plug-in XR e aggiungere i pacchetti necessari al progetto.</span><span class="sxs-lookup"><span data-stu-id="1862b-119">Click on **Unity OpenXR Plugin** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![<span data-ttu-id="1862b-120">Aggiungere il plug-in OpenXR di Unity</span><span class="sxs-lookup"><span data-stu-id="1862b-120">Add Unity OpenXR Plugin</span></span> ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

<span data-ttu-id="1862b-121">Verranno importati i pacchetti Unity necessari per XR Plugin Management. Al termine, fare clic su **Show XR Plug-In Management Impostazioni** in MRTK project Configurator (Mostra XR Plug-In Management Impostazioni configurator del progetto MRTK).</span><span class="sxs-lookup"><span data-stu-id="1862b-121">This will import required unity packages for XR Plugin Management, once done click on **Show XR Plug-In Management Settings** in MRTK project Configurator.</span></span>

![<span data-ttu-id="1862b-122">Visualizzare il Plug-In di gestione Impostazioni XR</span><span class="sxs-lookup"><span data-stu-id="1862b-122">Show XR Plug-In Management Settings</span></span> ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

<span data-ttu-id="1862b-123">Verrà visualizzata **Project Impostazioni finestra**.</span><span class="sxs-lookup"><span data-stu-id="1862b-123">This opens **Project Settings window**.</span></span> <span data-ttu-id="1862b-124">Nella finestra Project Impostazioni in **XR Plug-in Management (Gestione plug-in XR)** assicurarsi di essere nelle impostazioni di Universal Windows Platform (Windows logo).</span><span class="sxs-lookup"><span data-stu-id="1862b-124">In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings (Windows logo tab).</span></span> <span data-ttu-id="1862b-125">Assicurarsi anche che **l'opzione Initialize XR on Startup** (Inizializza XR all'avvio) sia selezionata, quindi fare clic sulla casella di controllo **OpenXR** e Microsoft HoloLens **set di funzionalità** per abilitarle.</span><span class="sxs-lookup"><span data-stu-id="1862b-125">Also Ensure **Initialize XR on Startup** is checked, then click **OpenXR** checkbox and **Microsoft HoloLens feature set** checkbox to enable them.</span></span>

![Abilitare Open XR](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

<span data-ttu-id="1862b-127">Dopo aver selezionato la casella di controllo OpenXR, nella finestra MRTK Project Configurator verrà visualizzato un messaggio aggiornato con il pulsante **Impostazioni** applica.</span><span class="sxs-lookup"><span data-stu-id="1862b-127">Once you check OpenXR checkbox, MRTK Project Configurator window will show updated message with **Apply Settings** button.</span></span> <span data-ttu-id="1862b-128">Fare **clic sul Impostazioni** applica.</span><span class="sxs-lookup"><span data-stu-id="1862b-128">Click **Apply Settings** button.</span></span> 

![Project Impostazioni finestra 1](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

<span data-ttu-id="1862b-130">Quando si fa clic su Impostazioni, è possibile che venga visualizzato questo messaggio di errore nella console.</span><span class="sxs-lookup"><span data-stu-id="1862b-130">When you click Apply Settings, you might see this error message in the Console.</span></span> <span data-ttu-id="1862b-131">È possibile procedere se si tratta dell'unico errore o se non si verifica alcun errore.</span><span class="sxs-lookup"><span data-stu-id="1862b-131">You can proceed if this is the only error or there is no error.</span></span>

![Messaggio di errore di OpenXR Remoting](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

<span data-ttu-id="1862b-133">Per convalidare la configurazione di OpenXR, fare clic **su OpenXR** **in XR Plug-in Management (Gestione plug-in XR)** e controllare questi elementi:</span><span class="sxs-lookup"><span data-stu-id="1862b-133">To validate OpenXR configuration, click **OpenXR** under **XR Plug-in Management** and check these items:</span></span>
* <span data-ttu-id="1862b-134">Modalità di invio profondità: **profondità a 16 bit**</span><span class="sxs-lookup"><span data-stu-id="1862b-134">Depth Submission Mode: **Depth 16 Bit**</span></span>
* <span data-ttu-id="1862b-135">Profili di interazione: **Profilo di interazione con la mano Microsoft**</span><span class="sxs-lookup"><span data-stu-id="1862b-135">Interaction Profiles: **Microsoft Hand Interaction Profile**</span></span>

![Project Impostazioni 2](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> <span data-ttu-id="1862b-137">La riduzione del formato profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto.</span><span class="sxs-lookup"><span data-stu-id="1862b-137">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="1862b-138">Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">condivisione del buffer di intensità (HoloLens)</a> della documentazione di MRTK relativa alle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="1862b-138">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>


<span data-ttu-id="1862b-139">Nella finestra **MRTK Project Configurator** fare clic su **Avanti** e quindi sul **pulsante** Applica per applicare le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="1862b-139">In the **MRTK Project Configurator** window, click on **Next**, then click the **Apply** button to apply the settings.</span></span> <span data-ttu-id="1862b-140">Se è stata chiusa, è possibile aprirla manualmente selezionando **Realtà mista**  >  **Toolkit**  >  **Utilità**  >  **Configurare Project per MRTK**)</span><span class="sxs-lookup"><span data-stu-id="1862b-140">(If you closed it, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**)</span></span>

![Project Impostazioni Finestra 3](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![Project Impostazioni 4](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

<span data-ttu-id="1862b-143">Dopo aver fatto clic su Apply (Applica), Unity tenterà di riavviare per applicare il sistema di input, quindi fare clic su **Apply (Applica)** per riavviare l'editor di Unity</span><span class="sxs-lookup"><span data-stu-id="1862b-143">Once you click on Apply, Unity will try to restart for the input system to take into effect, click on **Apply** to restart the Unity editor</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="1862b-144">Configurare impostazioni di progetto aggiuntive</span><span class="sxs-lookup"><span data-stu-id="1862b-144">Configure additional project settings</span></span>

<span data-ttu-id="1862b-145">Nel menu di Unity selezionare **Edit** > **Project Settings** (Modifica > Impostazioni progetto) per aprire la finestra Project Settings (Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="1862b-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window.</span></span>

<span data-ttu-id="1862b-146">Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="1862b-146">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Pubblicazione unity Impostazioni.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="1862b-149">Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app.</span><span class="sxs-lookup"><span data-stu-id="1862b-149">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="1862b-150">Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.</span><span class="sxs-lookup"><span data-stu-id="1862b-150">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="1862b-151">Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1862b-151">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="1862b-152">Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="1862b-152">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="1862b-153">Unity 2019/2020 + Windows plug-in XR</span><span class="sxs-lookup"><span data-stu-id="1862b-153">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="1862b-154">Dopo **aver aperto MixedRealityFeatureTool,** fare clic su **Start** per iniziare a usare Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="1862b-154">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="1862b-155">Il primo passaggio consiste nell'puntare Mixed Reality Feature Tool  al percorso **del Project** usando il pulsante con i puntini di sospensione, fare clic sul pulsante con i tre puntini di sospensione accanto al percorso del Project e passare alla cartella del progetto nello strumento di esplorazione, ad esempio _D:\MixedRealityLearning\MRTK Tutorials._</span><span class="sxs-lookup"><span data-stu-id="1862b-155">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


<span data-ttu-id="1862b-156">Dopo aver individuato la cartella del progetto, fai clic sul pulsante Apri per tornare a Mixed Reality Feature Tool (Strumento per le funzionalità di realtà mista).</span><span class="sxs-lookup"><span data-stu-id="1862b-156">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="1862b-157">Fare quindi clic **su Individua funzionalità**.</span><span class="sxs-lookup"><span data-stu-id="1862b-157">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="1862b-158">La finestra di dialogo visualizzata quando si esplora la cartella del progetto Unity contiene "_" come nome del file.</span><span class="sxs-lookup"><span data-stu-id="1862b-158">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="1862b-159">Per consentire la selezione della cartella, è necessario che sia presente un valore per il nome del file.</span><span class="sxs-lookup"><span data-stu-id="1862b-159">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="1862b-160">Lo strumento di funzionalità di realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="1862b-160">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="1862b-161">La cartella deve contenere asset, pacchetti e Project Impostazioni cartelle.</span><span class="sxs-lookup"><span data-stu-id="1862b-161">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="1862b-162">Le funzionalità sono raggruppate per categoria per semplificare l'individuazione, fare clic sull'elenco a discesa Toolkit mixed **reality (Realtà** mista) per trovare i pacchetti relativi al Toolkit.</span><span class="sxs-lookup"><span data-stu-id="1862b-162">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="1862b-163">Selezionare la casella **mixed reality Toolkit Foundation** e fare clic sull'elenco a discesa accanto per selezionare **MRTK 2.7.0** e quindi fare clic sul pulsante Get **features** (Ottieni funzionalità) per scaricare i pacchetti selezionati.</span><span class="sxs-lookup"><span data-stu-id="1862b-163">Check the box for **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="1862b-164">Fare quindi  clic sul pulsante Convalida per convalidare il  pacchetto selezionato. Verrà visualizzata una finestra popup con il messaggio Non sono stati rilevati problemi di convalida fare clic su **OK** per chiudere il popup e fare clic sul **pulsante** Importa.</span><span class="sxs-lookup"><span data-stu-id="1862b-164">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="1862b-165">Fare clic **sul pulsante** Approva per aggiungere **la** Toolkit realtà mista al progetto.</span><span class="sxs-lookup"><span data-stu-id="1862b-165">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="1862b-166">Configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="1862b-166">Configuring the Unity project</span></span>

<span data-ttu-id="1862b-167">Al termine dell'importazione del pacchetto dalla sezione precedente, viene visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK).</span><span class="sxs-lookup"><span data-stu-id="1862b-167">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="1862b-168">In caso contrario, è possibile aprirlo manualmente selezionando **Mixed Reality** Toolkit Utilities Configure Project for MRTK (Configura Project  >    >    >  **per MRTK):**</span><span class="sxs-lookup"><span data-stu-id="1862b-168">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![apertura dello strumento di configurazione MRTK](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

<span data-ttu-id="1862b-170">Fare clic **su Built-in Unity Plugin (non-OpenXR) (Plug-in Unity** incorporato ( non OpenXR) per abilitare la gestione dei plug-in XR e aggiungere i pacchetti necessari al progetto.</span><span class="sxs-lookup"><span data-stu-id="1862b-170">Click on **Built-in Unity Plugin(non-OpenXR)** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![ <span data-ttu-id="1862b-171">Strumento di configurazione MRTK</span><span class="sxs-lookup"><span data-stu-id="1862b-171">MRTK configurator tool</span></span>](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> <span data-ttu-id="1862b-172">Lo screenshot precedente è di Unity 2020. Se si usa Unity 2019, selezionare **XR SDK/XR Management**</span><span class="sxs-lookup"><span data-stu-id="1862b-172">The above screenshot is from Unity 2020, if you using Unity 2019 please select **XR SDK/XR Management**</span></span>

<span data-ttu-id="1862b-173">Verranno importati i pacchetti Unity necessari per XR Plugin Management. Al termine, fare clic su **Show Impostazioni** in MRTK project Configurator (Mostra Impostazioni nel progetto MRTK Configurator).</span><span class="sxs-lookup"><span data-stu-id="1862b-173">This will import required unity packages for XR Plugin Management, once done click on **Show Settings** in MRTK project Configurator.</span></span>

![Finestra Delle impostazioni del lettore](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

<span data-ttu-id="1862b-175">Verrà visualizzata Project Impostazioni finestra **,** nella finestra Project Impostazioni in **Gestione plug-in XR** Assicurarsi di essere nelle impostazioni della piattaforma Universal Windows Assicurarsi anche che l'opzione Inizializza **XR** all'avvio sia selezionata e selezionare Windows Mixed Reality **casella** di controllo.</span><span class="sxs-lookup"><span data-stu-id="1862b-175">This opens **Project Settings window**, In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings also Ensure **Initialize XR on Startup** is checked, and check **Windows Mixed Reality** checkbox.</span></span>

![Finestra delle impostazioni del lettore Abilita Realtà mista-xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

<span data-ttu-id="1862b-177">Al termine dell'importazione di Windows Mixed Reality SDK, dovrebbe visualizzarsi di nuovo la finestra MRTK Project Configurator (Configuratore del progetto MRTK).</span><span class="sxs-lookup"><span data-stu-id="1862b-177">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="1862b-178">In caso contrario, usa il menu di Unity per aprirla.</span><span class="sxs-lookup"><span data-stu-id="1862b-178">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="1862b-179">Nella finestra MRTK Project Configurator fare  clic su Next (Avanti), quindi usare l'elenco a discesa Audio spatializer (Spazializzatore audio) per selezionare **ms HRTF Spatializer (Spazializzatore MS HRTF),** quindi fare clic sul pulsante **Apply** (Applica) per applicare l'impostazione:</span><span class="sxs-lookup"><span data-stu-id="1862b-179">In the MRTK Project Configurator window, click on **next** then use the Audio spatializer dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Configurator-xrsdk del progetto MRTK](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="1862b-181">L'applicazione delle impostazioni predefinite di MRTK è facoltativa ma fortemente consigliata, poiché consente di configurare alcune impostazioni consigliate di Unity:</span><span class="sxs-lookup"><span data-stu-id="1862b-181">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="1862b-182">Set Single Pass Instanced rendering path (Imposta il percorso di rendering con istanze a singolo passaggio): migliora le prestazioni grafiche eseguendo la pipeline di rendering per entrambi gli occhi nella stessa chiamata di disegno.</span><span class="sxs-lookup"><span data-stu-id="1862b-182">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="1862b-183">Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sul [rendering con istanze a singolo passaggio](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) della documentazione di MRTK relativa alle [prestazioni](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).</span><span class="sxs-lookup"><span data-stu-id="1862b-183">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="1862b-184">Set default Spatial Awareness layer (Imposta livello di consapevolezza spaziale predefinito): crea un livello di Unity denominato Spatial Awareness e configura MRTK per l'uso di questo livello per la mesh di consapevolezza spaziale.</span><span class="sxs-lookup"><span data-stu-id="1862b-184">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="1862b-185">Per altre informazioni sui livelli di Unity, vedere la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="1862b-185">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="1862b-186">L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto.</span><span class="sxs-lookup"><span data-stu-id="1862b-186">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="1862b-187">Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata.</span><span class="sxs-lookup"><span data-stu-id="1862b-187">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="1862b-188">Per altre informazioni su questo argomento, è possibile fare riferimento alle  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> esercitazioni sull'audio spaziale</a>.</span><span class="sxs-lookup"><span data-stu-id="1862b-188">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="1862b-189">Fare clic **su Avanti** e quindi su **Fine** nella finestra MRTK Project Configurator per completare la configurazione del progetto Unity per XRSDK.</span><span class="sxs-lookup"><span data-stu-id="1862b-189">Click on **Next** then click on **Done** in the MRTK Project Configurator window to finish the Unity project configuration for XRSDK.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="1862b-190">Configurare impostazioni di progetto aggiuntive</span><span class="sxs-lookup"><span data-stu-id="1862b-190">Configure additional project settings</span></span>

<span data-ttu-id="1862b-191">Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:</span><span class="sxs-lookup"><span data-stu-id="1862b-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="1862b-192">Nella finestra Project Impostazioni selezionare **XR Plug-in Management** Windows Mixed Reality Runtime Impostazioni (Gestione plug-in XR Impostazioni Runtime) e quindi usare l'elenco a discesa Depth Buffer Format (Formato buffer di profondità) per selezionare la profondità  >    >   **a 16 bit:** </span><span class="sxs-lookup"><span data-stu-id="1862b-192">In the Project Settings window, select **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, then use the **Depth Buffer Format** dropdown to select **16-bit depth**:</span></span>

![Abilitazione di Unity a 16 profondità](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="1862b-194">La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto.</span><span class="sxs-lookup"><span data-stu-id="1862b-194">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="1862b-195">Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">condivisione del buffer di intensità (HoloLens)</a> della documentazione di MRTK relativa alle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="1862b-195">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="1862b-196">Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="1862b-196">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Pubblicazione unity Impostazioni.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="1862b-199">Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app.</span><span class="sxs-lookup"><span data-stu-id="1862b-199">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="1862b-200">Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.</span><span class="sxs-lookup"><span data-stu-id="1862b-200">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="1862b-201">Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1862b-201">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="1862b-202">Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="1862b-202">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="1862b-203">Legacy WSA</span><span class="sxs-lookup"><span data-stu-id="1862b-203">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="1862b-204">Dopo **aver aperto MixedRealityFeatureTool,** fare clic su **Start** per iniziare a usare Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="1862b-204">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="1862b-205">Il primo passaggio consiste nell'puntare Mixed Reality Feature Tool  al percorso **del Project** usando il pulsante con i puntini di sospensione, fare clic sul pulsante con i tre puntini di sospensione accanto al percorso del Project e passare alla cartella del progetto nello strumento di esplorazione, ad esempio _D:\MixedRealityLearning\MRTK Tutorials._</span><span class="sxs-lookup"><span data-stu-id="1862b-205">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="1862b-206">Dopo aver individuato la cartella del progetto, fai clic sul pulsante Apri per tornare a Mixed Reality Feature Tool (Strumento per le funzionalità di realtà mista).</span><span class="sxs-lookup"><span data-stu-id="1862b-206">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="1862b-207">Fare quindi clic **su Individua funzionalità**.</span><span class="sxs-lookup"><span data-stu-id="1862b-207">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="1862b-208">La finestra di dialogo visualizzata quando si esplora la cartella del progetto Unity contiene "_" come nome del file.</span><span class="sxs-lookup"><span data-stu-id="1862b-208">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="1862b-209">Per consentire la selezione della cartella, è necessario che sia presente un valore per il nome del file.</span><span class="sxs-lookup"><span data-stu-id="1862b-209">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="1862b-210">Lo strumento di funzionalità di realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="1862b-210">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="1862b-211">La cartella deve contenere asset, pacchetti e Project Impostazioni cartelle.</span><span class="sxs-lookup"><span data-stu-id="1862b-211">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="1862b-212">Le funzionalità sono raggruppate per categoria per semplificare l'individuazione, fare clic sull'elenco a discesa Toolkit mixed **reality (Realtà** mista) per trovare i pacchetti relativi al Toolkit.</span><span class="sxs-lookup"><span data-stu-id="1862b-212">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="1862b-213">Selezionare **Mixed Reality Toolkit Foundation** e fare clic sull'elenco a discesa accanto a esso per selezionare **MRTK 2.7.0** e quindi fare clic sul pulsante **Get features** (Ottieni funzionalità) per scaricare i pacchetti selezionati.</span><span class="sxs-lookup"><span data-stu-id="1862b-213">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="1862b-214">Fare quindi  clic sul pulsante Convalida per convalidare il  pacchetto selezionato. Verrà visualizzata una finestra popup con il messaggio Non sono stati rilevati problemi di convalida fare clic su **OK** per chiudere il popup e fare clic sul **pulsante** Importa.</span><span class="sxs-lookup"><span data-stu-id="1862b-214">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

<span data-ttu-id="1862b-215">Fare clic **sul pulsante** Approva per aggiungere **la** Toolkit realtà mista al progetto.</span><span class="sxs-lookup"><span data-stu-id="1862b-215">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="1862b-216">Configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="1862b-216">Configuring the Unity project</span></span>

<span data-ttu-id="1862b-217">Al termine dell'importazione del pacchetto dalla sezione precedente, viene visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK).</span><span class="sxs-lookup"><span data-stu-id="1862b-217">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="1862b-218">In caso contrario, è possibile aprirlo manualmente selezionando **Mixed Reality** Toolkit Utilities Configure Project for MRTK (Configura Project  >    >    >  **per MRTK):**</span><span class="sxs-lookup"><span data-stu-id="1862b-218">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Percorso del menu Configure Unity Project di Unity](../images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="1862b-220">Fare clic **su Legacy XR (XR** legacy) per abilitare Legacy XR (XR legacy) e aggiungere i pacchetti necessari al progetto.</span><span class="sxs-lookup"><span data-stu-id="1862b-220">Click on **Legacy XR** to enable Legacy XR and to add its required packages  into your project.</span></span>

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

<span data-ttu-id="1862b-222">Fare clic sul pulsante Avanti per abilitare le impostazioni della pipeline XR per XR legacy.</span><span class="sxs-lookup"><span data-stu-id="1862b-222">Click on next button to enable XR pipeline settings for Legacy XR.</span></span>

![Finestra di configurazione di Unity MRTK](../images/mr-learning-base/base-02-section5-step1-3.PNG)

<span data-ttu-id="1862b-224">Nella finestra MRTK Project Configurator verificare che tutte le opzioni siano selezionate e usare anche l'elenco a  discesa **Spazializzatore** audio per selezionare l'spazializzatore **MS HRTF** e quindi fare clic sul pulsante Applica per applicare l'impostazione:</span><span class="sxs-lookup"><span data-stu-id="1862b-224">In the MRTK Project Configurator window, ensure all options are checked and also use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Finestra di configurazione di MRTK](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> <span data-ttu-id="1862b-226">L'applicazione delle impostazioni predefinite di MRTK è facoltativa ma fortemente consigliata, poiché consente di configurare alcune impostazioni consigliate di Unity:</span><span class="sxs-lookup"><span data-stu-id="1862b-226">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="1862b-227">Set Single Pass Instanced rendering path (Imposta il percorso di rendering con istanze a singolo passaggio): migliora le prestazioni grafiche eseguendo la pipeline di rendering per entrambi gli occhi nella stessa chiamata di disegno.</span><span class="sxs-lookup"><span data-stu-id="1862b-227">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="1862b-228">Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sul [rendering con istanze a singolo passaggio](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) della documentazione di MRTK relativa alle [prestazioni](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).</span><span class="sxs-lookup"><span data-stu-id="1862b-228">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="1862b-229">Set default Spatial Awareness layer (Imposta livello di consapevolezza spaziale predefinito): crea un livello di Unity denominato Spatial Awareness e configura MRTK per l'uso di questo livello per la mesh di consapevolezza spaziale.</span><span class="sxs-lookup"><span data-stu-id="1862b-229">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="1862b-230">Per altre informazioni sui livelli di Unity, vedere la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="1862b-230">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="1862b-231">L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto.</span><span class="sxs-lookup"><span data-stu-id="1862b-231">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="1862b-232">Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata.</span><span class="sxs-lookup"><span data-stu-id="1862b-232">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="1862b-233">Per altre informazioni su questo argomento, è possibile fare riferimento alle  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> esercitazioni sull'audio spaziale</a>.</span><span class="sxs-lookup"><span data-stu-id="1862b-233">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="1862b-234">Fare clic **su Avanti** e quindi sul pulsante **Done** (Fine) nella finestra MRTK Project Configurator per completare la configurazione del progetto Unity per Legacy XR.</span><span class="sxs-lookup"><span data-stu-id="1862b-234">Click on **Next** then click on **Done** button in MRTK Project Configurator window to finish the Unity project configuration for Legacy XR.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="1862b-235">Configurare impostazioni di progetto aggiuntive</span><span class="sxs-lookup"><span data-stu-id="1862b-235">Configure additional project settings</span></span>

<span data-ttu-id="1862b-236">Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:</span><span class="sxs-lookup"><span data-stu-id="1862b-236">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="1862b-237">Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **XR Settings** (Impostazioni XR) e quindi usa l'elenco a discesa **Depth Format** (Formato profondità) per selezionare **16-bit depth** (Profondità a 16 bit):</span><span class="sxs-lookup"><span data-stu-id="1862b-237">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Abilitazione di Unity a 16 profondità](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> <span data-ttu-id="1862b-239">La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto.</span><span class="sxs-lookup"><span data-stu-id="1862b-239">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="1862b-240">Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">condivisione del buffer di intensità (HoloLens)</a> della documentazione di MRTK relativa alle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="1862b-240">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="1862b-241">Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="1862b-241">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Pubblicazione unity Impostazioni.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="1862b-244">Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app.</span><span class="sxs-lookup"><span data-stu-id="1862b-244">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="1862b-245">Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.</span><span class="sxs-lookup"><span data-stu-id="1862b-245">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="1862b-246">Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1862b-246">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="1862b-247">Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="1862b-247">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>
