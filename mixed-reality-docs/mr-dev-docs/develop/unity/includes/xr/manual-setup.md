---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394585"
---
# <a name="openxr"></a>[<span data-ttu-id="eea1d-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="eea1d-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="eea1d-102">Installare il plug-in OpenXR con la nuova applicazione Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="eea1d-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="eea1d-103">Seguire le [istruzioni di installazione e utilizzo](../../welcome-to-mr-feature-tool.md) e selezionare il pacchetto Mixed Reality **OpenXR Plugin** nella categoria Mixed Reality Toolkit:</span><span class="sxs-lookup"><span data-stu-id="eea1d-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Finestra dei pacchetti dello strumento di funzionalità di realtà mista con il plug-in xr aperto evidenziato](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="eea1d-105">Impostazione della destinazione di compilazione</span><span class="sxs-lookup"><span data-stu-id="eea1d-105">Setting your build target</span></span>

<span data-ttu-id="eea1d-106">Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma PC autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="eea1d-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

<span data-ttu-id="eea1d-108">Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="eea1d-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="eea1d-109">Selezionare **Impostazioni > file...**</span><span class="sxs-lookup"><span data-stu-id="eea1d-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="eea1d-110">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**</span><span class="sxs-lookup"><span data-stu-id="eea1d-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="eea1d-111">Impostare **Architettura** su **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="eea1d-111">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="eea1d-112">Impostare **Dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="eea1d-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="eea1d-113">Impostare **Tipo di compilazione** su **D3D**</span><span class="sxs-lookup"><span data-stu-id="eea1d-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="eea1d-114">Impostare **UWP SDK su** Latest installed **(Versione più recente installata)**</span><span class="sxs-lookup"><span data-stu-id="eea1d-114">Set **UWP SDK** to **Latest installed**</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="eea1d-116">Configurazione della gestione dei plug-in XR per OpenXR</span><span class="sxs-lookup"><span data-stu-id="eea1d-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="eea1d-117">Per impostare OpenXR come runtime in Unity:</span><span class="sxs-lookup"><span data-stu-id="eea1d-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="eea1d-118">Nell'editor di Unity passare a **Edit > Project Settings (Modifica impostazioni progetto)**</span><span class="sxs-lookup"><span data-stu-id="eea1d-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="eea1d-119">Nell'elenco delle impostazioni selezionare **XR Plugin Management (Gestione plug-in XR)**</span><span class="sxs-lookup"><span data-stu-id="eea1d-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="eea1d-120">Selezionare le **caselle Inizializza XR all'avvio** **e OpenXR**</span><span class="sxs-lookup"><span data-stu-id="eea1d-120">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="eea1d-121">Se la destinazione HoloLens 2, assicurarsi di essere nella piattaforma UWP e selezionare Microsoft HoloLens **set di funzionalità**</span><span class="sxs-lookup"><span data-stu-id="eea1d-121">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con gestione plug-in XR evidenziata](../../images/openxr-img-05.png)

### <a name="optimization"></a><span data-ttu-id="eea1d-123">Optimization</span><span class="sxs-lookup"><span data-stu-id="eea1d-123">Optimization</span></span>

<span data-ttu-id="eea1d-124">Se stai sviluppando per HoloLens 2, passa a **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** (Applica le impostazioni di progetto consigliate per HoloLens 2 per ottenere prestazioni migliori per le app).</span><span class="sxs-lookup"><span data-stu-id="eea1d-124">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Screenshot della voce di menu di realtà mista aperta con OpenXR selezionato](../../images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="eea1d-126">Se viene visualizzata un'icona di avviso gialla accanto a **Plug-in OpenXR,** fare clic sull'icona e **selezionare Correggi tutto** prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="eea1d-126">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="eea1d-127">Per l'applicazione delle modifiche, potrebbe essere necessario riavviare l'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="eea1d-127">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot della finestra di convalida del progetto OpenXR](../../images/openxr-img-06.png)

<span data-ttu-id="eea1d-129">A questo punto è possibile iniziare a sviluppare con OpenXR in Unity.</span><span class="sxs-lookup"><span data-stu-id="eea1d-129">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="eea1d-130">Continuare con la sezione successiva per informazioni su come usare gli esempi di OpenXR.</span><span class="sxs-lookup"><span data-stu-id="eea1d-130">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="eea1d-131">Progetti di esempio Unity per OpenXR e HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="eea1d-131">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="eea1d-132">Consulta il repo di esempi di [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) per progetti Unity di esempio che illustrano come compilare applicazioni Unity per HoloLens 2 o visori VR di realtà mista usando il plug-in OpenXR di Realtà mista.</span><span class="sxs-lookup"><span data-stu-id="eea1d-132">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="eea1d-133">Windows XR</span><span class="sxs-lookup"><span data-stu-id="eea1d-133">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="eea1d-134">Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma PC autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="eea1d-134">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

<span data-ttu-id="eea1d-136">Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="eea1d-136">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="eea1d-137">Selezionare **Impostazioni > file...**</span><span class="sxs-lookup"><span data-stu-id="eea1d-137">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="eea1d-138">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**</span><span class="sxs-lookup"><span data-stu-id="eea1d-138">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="eea1d-139">Impostare **Architettura** su **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="eea1d-139">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="eea1d-140">Impostare **Dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="eea1d-140">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="eea1d-141">Impostare **Tipo di compilazione** su **D3D**</span><span class="sxs-lookup"><span data-stu-id="eea1d-141">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="eea1d-142">Impostare **UWP SDK su** Latest installed **(Versione più recente installata)**</span><span class="sxs-lookup"><span data-stu-id="eea1d-142">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="eea1d-143">Impostare **Build configuration (Configurazione build)** **su Release (Versione)** perché sono presenti problemi di prestazioni noti con Debug</span><span class="sxs-lookup"><span data-stu-id="eea1d-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](../../images/wmr-config-img-4.png)

<span data-ttu-id="eea1d-145">Dopo aver impostato la piattaforma, è necessario invii a Unity una visualizzazione [immersiva](../../../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata:</span><span class="sxs-lookup"><span data-stu-id="eea1d-145">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="eea1d-146">Nell'editor di Unity passare a **Edit > Project settings (Modifica impostazioni progetto)** e selezionare **XR Plugin Management (Gestione plug-in XR)**</span><span class="sxs-lookup"><span data-stu-id="eea1d-146">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="eea1d-147">Selezionare **Install XR Plugin Management (Installa gestione plug-in XR)**</span><span class="sxs-lookup"><span data-stu-id="eea1d-147">Select **Install XR Plugin Management**</span></span>

![Screenshot della finestra Project Settings (Impostazioni progetto) aperta nell'editor di Unity con la gestione del plug-in XR evidenziata](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="eea1d-149">Selezionare Initialize XR on Startup (Inizializza **XR all'avvio)** **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="eea1d-149">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Screenshot della finestra Delle impostazioni del progetto aperta nell'editor di Unity con la gestione del plug-in XR evidenziata](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="eea1d-151">Espandere la **sezione XR Plug-in Management (Gestione plug-in XR)** e selezionare **la scheda Univeral Windows Platform Settings (Impostazioni piattaforma Windows univeral)**</span><span class="sxs-lookup"><span data-stu-id="eea1d-151">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="eea1d-152">Se si usa Unity 2020 o versione successiva, verranno visualizzati i controlli **OpenXR** **o Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="eea1d-152">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="eea1d-153">È possibile scegliere uno dei due runtime.</span><span class="sxs-lookup"><span data-stu-id="eea1d-153">You can choose either runtime.</span></span>  <span data-ttu-id="eea1d-154">Se si sviluppa specificamente per il HoloLens 2 o HP Reverb G2 e si decide di provare **OpenXR,** selezionare la casella OpenXR ed esaminare la guida Uso del plug-in [OpenXR](../../openxr-getting-started.md) di Realtà mista per Unity per configurare correttamente questi dispositivi prima di tornare a questa esercitazione</span><span class="sxs-lookup"><span data-stu-id="eea1d-154">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](../../openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="eea1d-155">A partire da Unity 2020 LTS, Microsoft sta iniziando lo sviluppo con OpenXR.</span><span class="sxs-lookup"><span data-stu-id="eea1d-155">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="eea1d-156">Durante la migrazione a questo percorso, in Unity 2021.1 il plug-in Windows XR verrà deprecato e rimosso nella versione 2021.2 rendendo OpenXR l'unico percorso supportato.</span><span class="sxs-lookup"><span data-stu-id="eea1d-156">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="eea1d-157">Per altre informazioni, vedere [Using the Mixed Reality OpenXR plugin (Uso del plug-in OpenXR di Realtà mista).](../../openxr-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="eea1d-157">You can find more information in [Using the Mixed Reality OpenXR plugin](../../openxr-getting-started.md).</span></span>

6. <span data-ttu-id="eea1d-158">Se si decide di scegliere il **plug-Windows Mixed Reality,** selezionare tutte le caselle e impostare Modalità di invio **profondità** **su Depth 16 Bit (Profondità 16 bit)**</span><span class="sxs-lookup"><span data-stu-id="eea1d-158">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Screenshot della finestra Project settings (Impostazioni progetto) aperta nell'editor di Unity con Windows Mixed Reality sezione evidenziata](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="eea1d-160">XR legacy</span><span class="sxs-lookup"><span data-stu-id="eea1d-160">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="eea1d-161">Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma PC autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="eea1d-161">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

<span data-ttu-id="eea1d-163">Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="eea1d-163">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="eea1d-164">Selezionare **Impostazioni > file...**</span><span class="sxs-lookup"><span data-stu-id="eea1d-164">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="eea1d-165">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**</span><span class="sxs-lookup"><span data-stu-id="eea1d-165">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="eea1d-166">Impostare **Architettura** su **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="eea1d-166">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="eea1d-167">Impostare **Dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="eea1d-167">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="eea1d-168">Impostare **Tipo di compilazione** su **D3D**</span><span class="sxs-lookup"><span data-stu-id="eea1d-168">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="eea1d-169">Impostare **UWP SDK su** Latest installed **(Versione più recente installata)**</span><span class="sxs-lookup"><span data-stu-id="eea1d-169">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="eea1d-170">Impostare **Build configuration (Configurazione build)** **su Release (Versione)** perché sono presenti problemi di prestazioni noti con Debug</span><span class="sxs-lookup"><span data-stu-id="eea1d-170">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](../../images/wmr-config-img-4.png)

<span data-ttu-id="eea1d-172">Dopo aver impostato la piattaforma, è necessario invii a Unity una visualizzazione [immersiva](../../../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.</span><span class="sxs-lookup"><span data-stu-id="eea1d-172">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="eea1d-173">XR legacy è deprecato in Unity 2019 e rimosso in Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="eea1d-173">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="eea1d-174">Aprire **Player Settings (Impostazioni lettore)** da Build Settings **(Impostazioni di compilazione) ed** espandere il **gruppo XR Settings (Impostazioni XR)**</span><span class="sxs-lookup"><span data-stu-id="eea1d-174">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="eea1d-175">Nella sezione **XR Settings (Impostazioni XR)** selezionare **Virtual Reality Supported (Realtà virtuale supportata)** per aggiungere l'elenco Virtual Reality Devices (Dispositivi di realtà virtuale)</span><span class="sxs-lookup"><span data-stu-id="eea1d-175">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="eea1d-176">Impostare **Depth Format (Formato profondità)** su **Depth (Profondità) a 16 bit** e abilitare Depth Buffer Sharing **(Condivisione buffer di profondità)**</span><span class="sxs-lookup"><span data-stu-id="eea1d-176">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="eea1d-177">Impostare **La modalità di rendering stereo** su Istanza a passaggio **singolo**</span><span class="sxs-lookup"><span data-stu-id="eea1d-177">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="eea1d-178">Selezionare **WSA Holographic Remoting Supported** se si desidera usare holographic remoting</span><span class="sxs-lookup"><span data-stu-id="eea1d-178">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Screenshot della finestra Project settings (Impostazioni progetto) aperta nell'editor di Unity con la sezione Player settings (Impostazioni lettore) evidenziata](../../images/wmr-config-img-9.png)