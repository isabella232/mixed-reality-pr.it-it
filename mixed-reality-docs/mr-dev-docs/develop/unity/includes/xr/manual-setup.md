---
ms.openlocfilehash: c965eb1b4edc91421e0b8b2e96893a04431aef6e
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2021
ms.locfileid: "112535933"
---
# <a name="openxr"></a>[<span data-ttu-id="7021a-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="7021a-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="7021a-102">Installare il plug-in OpenXR con la nuova applicazione Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="7021a-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="7021a-103">Seguire le [istruzioni di installazione e utilizzo](../../welcome-to-mr-feature-tool.md) e selezionare il pacchetto Mixed Reality **OpenXR Plugin** nella categoria Platform Support **(Supporto** piattaforma):</span><span class="sxs-lookup"><span data-stu-id="7021a-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the **Platform Support** category:</span></span>

![Finestra dei pacchetti degli strumenti di funzionalità di realtà mista con il plug-in xr aperto evidenziato](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="7021a-105">Impostazione della destinazione di compilazione</span><span class="sxs-lookup"><span data-stu-id="7021a-105">Setting your build target</span></span>

<span data-ttu-id="7021a-106">Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="7021a-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

<span data-ttu-id="7021a-108">Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="7021a-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="7021a-109">Selezionare **Impostazioni > file...**</span><span class="sxs-lookup"><span data-stu-id="7021a-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="7021a-110">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**</span><span class="sxs-lookup"><span data-stu-id="7021a-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="7021a-111">Impostare **Architecture** (Architettura) su **ARM64**</span><span class="sxs-lookup"><span data-stu-id="7021a-111">Set **Architecture** to **ARM64**</span></span>
4. <span data-ttu-id="7021a-112">Impostare **Dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="7021a-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="7021a-113">Impostare **Build Type** (Tipo di compilazione) su **D3D Project**</span><span class="sxs-lookup"><span data-stu-id="7021a-113">Set **Build Type** to **D3D Project**</span></span>
6. <span data-ttu-id="7021a-114">Impostare **Versione SDK di destinazione** su Più recente **installato**</span><span class="sxs-lookup"><span data-stu-id="7021a-114">Set **Target SDK Version** to **Latest installed**</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="7021a-116">Configurazione della gestione dei plug-in XR per OpenXR</span><span class="sxs-lookup"><span data-stu-id="7021a-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="7021a-117">Per impostare OpenXR come runtime in Unity:</span><span class="sxs-lookup"><span data-stu-id="7021a-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="7021a-118">Nell'editor di Unity passare a **Edit > Project Settings (Modifica impostazioni progetto)**</span><span class="sxs-lookup"><span data-stu-id="7021a-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="7021a-119">Nell'elenco delle impostazioni selezionare **XR Plugin Management (Gestione plug-in XR)**</span><span class="sxs-lookup"><span data-stu-id="7021a-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="7021a-120">Selezionare **Install XR Plugin Management (Installa gestione plug-in XR)** se viene visualizzata ![ la schermata della finestra Project Settings (Impostazioni progetto) aperta nell'editor unity con XR Plugin management (Gestione plug-in XR) evidenziato](../../images/wmr-config-img-5.png)</span><span class="sxs-lookup"><span data-stu-id="7021a-120">Select **Install XR Plugin Management** if it appears ![Screenshot of Project Settings window open in unity editor with XR Plugin management highlighted](../../images/wmr-config-img-5.png)</span></span>
4. <span data-ttu-id="7021a-121">Selezionare la **casella Initialize XR on Startup (Inizializza XR all'avvio)**</span><span class="sxs-lookup"><span data-stu-id="7021a-121">Check the **Initialize XR on Startup** box</span></span>
5. <span data-ttu-id="7021a-122">Se la destinazione è Desktop VR, rimanere nella scheda PC autonomo (monitor) e selezionare le caselle **OpenXR** e **Windows Mixed Reality set di funzionalità**</span><span class="sxs-lookup"><span data-stu-id="7021a-122">If targeting Desktop VR, stay on the PC Standalone tab (the monitor) and check the **OpenXR** and **Windows Mixed Reality feature set** boxes</span></span>
6. <span data-ttu-id="7021a-123">Se la destinazione HoloLens 2, passare alla scheda piattaforma UWP (Universal Windows Platform) (logo Windows) e selezionare le caselle **OpenXR** e **Microsoft HoloLens set di funzionalità**</span><span class="sxs-lookup"><span data-stu-id="7021a-123">If targeting HoloLens 2, switch to the Universal Windows Platform tab (the Windows logo) and select the **OpenXR** and **Microsoft HoloLens feature set** boxes</span></span>

![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con gestione plug-in XR evidenziata](../../images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="7021a-125">Se viene visualizzata un'icona di avviso gialla accanto a **Plug-in OpenXR,** fare clic sull'icona e **selezionare Correggi tutto** prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="7021a-125">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix All** before continuing.</span></span> <span data-ttu-id="7021a-126">Per l'applicazione delle modifiche potrebbe essere necessario riavviare l'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="7021a-126">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot della finestra di convalida del progetto OpenXR](../../images/openxr-img-06.png)

### <a name="optimization"></a><span data-ttu-id="7021a-128">Optimization</span><span class="sxs-lookup"><span data-stu-id="7021a-128">Optimization</span></span>

<span data-ttu-id="7021a-129">Se stai sviluppando per HoloLens 2, seleziona la voce di menu **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** (Applica le impostazioni di progetto consigliate per HoloLens 2 per ottenere prestazioni migliori dell'app).</span><span class="sxs-lookup"><span data-stu-id="7021a-129">If you're developing for HoloLens 2, select the **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** menu item to get better app performance.</span></span>

![Screenshot della voce di menu di realtà mista aperta con OpenXR selezionato](../../images/openxr-img-08.png)

<span data-ttu-id="7021a-131">A questo punto è possibile iniziare a sviluppare con OpenXR in Unity.</span><span class="sxs-lookup"><span data-stu-id="7021a-131">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="7021a-132">Continuare con la sezione successiva per informazioni su come usare gli esempi di OpenXR.</span><span class="sxs-lookup"><span data-stu-id="7021a-132">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="7021a-133">Progetti di esempio Unity per OpenXR e HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7021a-133">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="7021a-134">Consulta il repo di esempi di [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) per progetti Unity di esempio che illustrano come compilare applicazioni Unity per HoloLens 2 o visori VR di realtà mista usando il plug-in OpenXR di Realtà mista.</span><span class="sxs-lookup"><span data-stu-id="7021a-134">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="7021a-135">In caso contrario, se si è pronti per iniziare da un progetto vuoto, passare all'articolo [Configurazione della fotocamera.](../../camera-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="7021a-135">Or, if you're ready to get started on your own from a blank project, proceed to the [Camera setup](../../camera-in-unity.md) article.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="7021a-136">Windows XR</span><span class="sxs-lookup"><span data-stu-id="7021a-136">Windows XR</span></span>](#tab/windowsxr)

> [!CAUTION]
> <span data-ttu-id="7021a-137">Il plug-in Windows XR è deprecato in Unity 2021.1 e verrà rimosso in Unity 2021.2.</span><span class="sxs-lookup"><span data-stu-id="7021a-137">The Windows XR plugin is deprecated in Unity 2021.1 and will be removed in Unity 2021.2.</span></span>  <span data-ttu-id="7021a-138">Per lo sviluppo di Unity 2020, Microsoft consiglia invece il plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="7021a-138">For Unity 2020 development, Microsoft recommends the OpenXR plugin instead.</span></span>

<span data-ttu-id="7021a-139">Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="7021a-139">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

<span data-ttu-id="7021a-141">Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="7021a-141">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="7021a-142">Selezionare **Impostazioni > file...**</span><span class="sxs-lookup"><span data-stu-id="7021a-142">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="7021a-143">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**</span><span class="sxs-lookup"><span data-stu-id="7021a-143">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="7021a-144">Impostare **Architecture** (Architettura) su **ARM64**</span><span class="sxs-lookup"><span data-stu-id="7021a-144">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="7021a-145">Impostare **Dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="7021a-145">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="7021a-146">Impostare **Build Type** (Tipo di compilazione) su **D3D Project**</span><span class="sxs-lookup"><span data-stu-id="7021a-146">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="7021a-147">Impostare **Versione SDK di destinazione** su Più recente **installato**</span><span class="sxs-lookup"><span data-stu-id="7021a-147">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="7021a-148">Impostare **Build configuration (Configurazione build)** **su Release (Versione)** perché sono presenti problemi di prestazioni noti con Debug</span><span class="sxs-lookup"><span data-stu-id="7021a-148">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](../../images/wmr-config-img-4.png)

<span data-ttu-id="7021a-150">Dopo aver impostato la piattaforma, è necessario invii a Unity una visualizzazione [immersiva](../../../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata:</span><span class="sxs-lookup"><span data-stu-id="7021a-150">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="7021a-151">Nell'editor di Unity passare a **Edit > Project settings (Modifica impostazioni progetto)** e selezionare **XR Plugin Management (Gestione plug-in XR)**</span><span class="sxs-lookup"><span data-stu-id="7021a-151">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="7021a-152">Selezionare **Install XR Plugin Management (Installa gestione plug-in XR),** se visualizzato</span><span class="sxs-lookup"><span data-stu-id="7021a-152">Select **Install XR Plugin Management** if it appears</span></span>

![Screenshot della finestra Project Settings (Impostazioni progetto) aperta nell'editor di Unity con la gestione del plug-in XR evidenziata](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="7021a-154">Selezionare Initialize XR on Startup (Inizializza **XR all'avvio)** **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="7021a-154">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Screenshot della finestra Delle impostazioni del progetto aperta nell'editor di Unity con la gestione del plug-in XR evidenziata](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="7021a-156">Selezionare la **sezione Gestione plug-in XR Windows Mixed Reality,** selezionare tutte le caselle e impostare Depth Buffer Format (Formato buffer profondità) su  >   Depth Buffer **16 Bit (Buffer profondità a 16 bit)** </span><span class="sxs-lookup"><span data-stu-id="7021a-156">Select the **XR Plug-in Management** > **Windows Mixed Reality** section, check all boxes and set **Depth Buffer Format** to **Depth Buffer 16 Bit**</span></span>

![Screenshot della finestra Project settings (Impostazioni progetto) aperta nell'editor di Unity con Windows Mixed Reality sezione evidenziata](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="7021a-158">XR legacy</span><span class="sxs-lookup"><span data-stu-id="7021a-158">Legacy XR</span></span>](#tab/legacy)

> [!CAUTION]
> <span data-ttu-id="7021a-159">XR legacy è deprecato in Unity 2019 e rimosso in Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="7021a-159">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

<span data-ttu-id="7021a-160">Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="7021a-160">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

<span data-ttu-id="7021a-162">Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="7021a-162">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="7021a-163">Selezionare **Impostazioni > file...**</span><span class="sxs-lookup"><span data-stu-id="7021a-163">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="7021a-164">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**</span><span class="sxs-lookup"><span data-stu-id="7021a-164">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="7021a-165">Impostare **Architecture** (Architettura) su **ARM64**</span><span class="sxs-lookup"><span data-stu-id="7021a-165">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="7021a-166">Impostare **Dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="7021a-166">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="7021a-167">Impostare **Build Type** (Tipo di compilazione) su **D3D Project**</span><span class="sxs-lookup"><span data-stu-id="7021a-167">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="7021a-168">Impostare **Versione SDK di destinazione** su Più recente **installato**</span><span class="sxs-lookup"><span data-stu-id="7021a-168">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="7021a-169">Impostare **Build configuration (Configurazione build)** **su Release (Versione)** perché sono presenti problemi di prestazioni noti con Debug</span><span class="sxs-lookup"><span data-stu-id="7021a-169">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](../../images/wmr-config-img-4.png)

<span data-ttu-id="7021a-171">Dopo aver impostato la piattaforma, è necessario invii a Unity una visualizzazione [immersiva](../../../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.</span><span class="sxs-lookup"><span data-stu-id="7021a-171">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

1. <span data-ttu-id="7021a-172">Aprire **Player Settings (Impostazioni lettore)** da Build Settings **(Impostazioni compilazione) ed** espandere il **gruppo XR Settings (Impostazioni XR)**</span><span class="sxs-lookup"><span data-stu-id="7021a-172">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="7021a-173">Nella sezione **XR Settings (Impostazioni XR)** selezionare **Virtual Reality Supported (Realtà virtuale supportata)** per aggiungere l'elenco Virtual Reality Devices (Dispositivi di realtà virtuale)</span><span class="sxs-lookup"><span data-stu-id="7021a-173">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="7021a-174">Impostare **Depth Format (Formato profondità)** su **16 bit depth (Profondità 16 bit)** e **selezionare Enable Depth Buffer Sharing (Abilita condivisione buffer di profondità)**</span><span class="sxs-lookup"><span data-stu-id="7021a-174">Set **Depth Format** to **16-bit depth** and check **Enable Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="7021a-175">Impostare **Stereo Rendering Mode** (Modalità di rendering stereo) su **Single Pass Instanced** (Istanze a singolo passaggio)</span><span class="sxs-lookup"><span data-stu-id="7021a-175">Set **Stereo Rendering Mode** to **Single Pass Instanced**</span></span>
5. <span data-ttu-id="7021a-176">Selezionare **WSA Holographic Remoting Supported se** si desidera usare la comunicazione remota in modalità di riproduzione olografica</span><span class="sxs-lookup"><span data-stu-id="7021a-176">Select **WSA Holographic Remoting Supported** if you'd like to use holographic play mode remoting</span></span>

![Screenshot della finestra Project settings (Impostazioni progetto) aperta nell'editor di Unity con la sezione Player settings (Impostazioni lettore) evidenziata](../../images/wmr-config-img-9.png)
