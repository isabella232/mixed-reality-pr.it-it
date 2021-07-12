---
ms.openlocfilehash: 639a96785e666cc3f5da3577ec3166f364753ed5
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603736"
---
# <a name="openxr"></a>[<span data-ttu-id="5d570-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="5d570-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="5d570-102">Installare il plug-in OpenXR con la nuova applicazione Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="5d570-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="5d570-103">Seguire le [istruzioni di installazione e utilizzo](../../welcome-to-mr-feature-tool.md) e selezionare il pacchetto Mixed Reality **OpenXR Plugin** nella categoria Platform Support **(Supporto** piattaforma):</span><span class="sxs-lookup"><span data-stu-id="5d570-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the **Platform Support** category:</span></span>

![Finestra dei pacchetti degli strumenti di funzionalità di realtà mista con il plug-in xr aperto evidenziato](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="5d570-105">Impostazione della destinazione di compilazione</span><span class="sxs-lookup"><span data-stu-id="5d570-105">Setting your build target</span></span>

<span data-ttu-id="5d570-106">Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="5d570-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra build Impostazioni aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

<span data-ttu-id="5d570-108">Se la destinazione è HoloLens 2, è necessario passare alla piattaforma Windows universali:</span><span class="sxs-lookup"><span data-stu-id="5d570-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="5d570-109">Selezionare **File > Compilazione Impostazioni...**</span><span class="sxs-lookup"><span data-stu-id="5d570-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="5d570-110">Selezionare **Universal Windows Platform nell'elenco** Platform (Piattaforma) e selezionare Switch Platform **(Cambia piattaforma)**</span><span class="sxs-lookup"><span data-stu-id="5d570-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="5d570-111">Impostare **Architecture** (Architettura) su **ARM64**</span><span class="sxs-lookup"><span data-stu-id="5d570-111">Set **Architecture** to **ARM64**</span></span>
4. <span data-ttu-id="5d570-112">Impostare **Dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="5d570-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="5d570-113">Impostare **Build Type** (Tipo di compilazione) su **D3D Project**</span><span class="sxs-lookup"><span data-stu-id="5d570-113">Set **Build Type** to **D3D Project**</span></span>
6. <span data-ttu-id="5d570-114">Impostare **Versione SDK di destinazione** su Più recente **installato**</span><span class="sxs-lookup"><span data-stu-id="5d570-114">Set **Target SDK Version** to **Latest installed**</span></span>

![Screenshot della finestra Build Impostazioni aperta nell'editor di Unity con universal Windows Platform evidenziato](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="5d570-116">Configurazione della gestione dei plug-in XR per OpenXR</span><span class="sxs-lookup"><span data-stu-id="5d570-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="5d570-117">Per impostare OpenXR come runtime in Unity:</span><span class="sxs-lookup"><span data-stu-id="5d570-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="5d570-118">Nell'editor di Unity passare a **Edit > Project Impostazioni (Modifica > Project Impostazioni**</span><span class="sxs-lookup"><span data-stu-id="5d570-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="5d570-119">Nell'elenco di Impostazioni selezionare XR Plugin Management (Gestione **plug-in XR)** (dovrebbe essere già installato se è stato installato il plug-in Mixed Reality OpenXR usando MRFT)</span><span class="sxs-lookup"><span data-stu-id="5d570-119">In the list of Settings, select **XR Plugin Management** (should already be installed if you installed the Mixed Reality OpenXR plugin using MRFT)</span></span>
3. <span data-ttu-id="5d570-120">Selezionare la **casella Initialize XR on Startup (Inizializza XR all'avvio)**</span><span class="sxs-lookup"><span data-stu-id="5d570-120">Check the **Initialize XR on Startup** box</span></span>
4. <span data-ttu-id="5d570-121">Se la destinazione è Desktop VR, rimanere nella scheda PC autonomo (monitor) e selezionare le caselle **OpenXR** e **Windows Mixed Reality set di funzionalità**</span><span class="sxs-lookup"><span data-stu-id="5d570-121">If targeting Desktop VR, stay on the PC Standalone tab (the monitor) and check the **OpenXR** and **Windows Mixed Reality feature set** boxes</span></span>
5. <span data-ttu-id="5d570-122">Se la destinazione HoloLens 2, passare alla scheda Universal Windows Platform (logo Windows) e selezionare le caselle **OpenXR** e **Microsoft HoloLens set di funzionalità**</span><span class="sxs-lookup"><span data-stu-id="5d570-122">If targeting HoloLens 2, switch to the Universal Windows Platform tab (the Windows logo) and select the **OpenXR** and **Microsoft HoloLens feature set** boxes</span></span>

![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con gestione plug-in XR evidenziata](../../images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="5d570-124">Se viene visualizzata un'icona di avviso gialla accanto a **Plug-in OpenXR,** fare clic sull'icona e **selezionare Correggi tutto** prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="5d570-124">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix All** before continuing.</span></span> <span data-ttu-id="5d570-125">Per l'applicazione delle modifiche potrebbe essere necessario riavviare l'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="5d570-125">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot della finestra di convalida del progetto OpenXR](../../images/openxr-img-06.png)

### <a name="optimization"></a><span data-ttu-id="5d570-127">Optimization</span><span class="sxs-lookup"><span data-stu-id="5d570-127">Optimization</span></span>

<span data-ttu-id="5d570-128">Se stai sviluppando per HoloLens 2, seleziona la voce di menu **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** (Applica impostazioni di progetto consigliate per HoloLens 2 app) per ottenere prestazioni migliori dell'app.</span><span class="sxs-lookup"><span data-stu-id="5d570-128">If you're developing for HoloLens 2, select the **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** menu item to get better app performance.</span></span>

![Screenshot della voce di menu di realtà mista aperta con OpenXR selezionato](../../images/openxr-img-08.png)

<span data-ttu-id="5d570-130">A questo punto è possibile iniziare a sviluppare con OpenXR in Unity.</span><span class="sxs-lookup"><span data-stu-id="5d570-130">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="5d570-131">Continuare con la sezione successiva per informazioni su come usare gli esempi di OpenXR.</span><span class="sxs-lookup"><span data-stu-id="5d570-131">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="5d570-132">Progetti di esempio Unity per OpenXR e HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5d570-132">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="5d570-133">Consulta il repo di esempi di [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) per progetti Unity di esempio che illustrano come compilare applicazioni Unity per HoloLens 2 o visori VR di realtà mista usando il plug-in OpenXR di Realtà mista.</span><span class="sxs-lookup"><span data-stu-id="5d570-133">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="5d570-134">In caso contrario, se si è pronti per iniziare da un progetto vuoto, passare all'articolo [Configurazione della fotocamera.](../../camera-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="5d570-134">Or, if you're ready to get started on your own from a blank project, proceed to the [Camera setup](../../camera-in-unity.md) article.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="5d570-135">Windows Xr</span><span class="sxs-lookup"><span data-stu-id="5d570-135">Windows XR</span></span>](#tab/windowsxr)

> [!CAUTION]
> <span data-ttu-id="5d570-136">Il Windows plug-in XR è deprecato in Unity 2021.1 e verrà rimosso in Unity 2021.2.</span><span class="sxs-lookup"><span data-stu-id="5d570-136">The Windows XR plugin is deprecated in Unity 2021.1 and will be removed in Unity 2021.2.</span></span>  <span data-ttu-id="5d570-137">Per lo sviluppo di Unity 2020, Microsoft consiglia invece il plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="5d570-137">For Unity 2020 development, Microsoft recommends the OpenXR plugin instead.</span></span>

<span data-ttu-id="5d570-138">Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="5d570-138">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra build Impostazioni aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

<span data-ttu-id="5d570-140">Se la destinazione è HoloLens 2, è necessario passare alla piattaforma Windows universali:</span><span class="sxs-lookup"><span data-stu-id="5d570-140">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="5d570-141">Selezionare **File > Compilazione Impostazioni...**</span><span class="sxs-lookup"><span data-stu-id="5d570-141">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="5d570-142">Selezionare **Universal Windows Platform nell'elenco** Platform (Piattaforma) e selezionare Switch Platform **(Cambia piattaforma)**</span><span class="sxs-lookup"><span data-stu-id="5d570-142">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="5d570-143">Impostare **Architecture** (Architettura) su **ARM64**</span><span class="sxs-lookup"><span data-stu-id="5d570-143">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="5d570-144">Impostare **Dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="5d570-144">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="5d570-145">Impostare **Build Type** (Tipo di compilazione) su **D3D Project**</span><span class="sxs-lookup"><span data-stu-id="5d570-145">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="5d570-146">Impostare **Versione SDK di destinazione** su Più recente **installato**</span><span class="sxs-lookup"><span data-stu-id="5d570-146">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="5d570-147">Impostare **Build configuration (Configurazione build)** **su Release (Versione)** perché sono presenti problemi di prestazioni noti con Debug</span><span class="sxs-lookup"><span data-stu-id="5d570-147">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot della finestra Build Impostazioni aperta nell'editor di Unity con universal Windows Platform evidenziato](../../images/wmr-config-img-4.png)

<span data-ttu-id="5d570-149">Dopo aver impostato la piattaforma, è necessario invii a Unity una visualizzazione [immersiva](../../../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata:</span><span class="sxs-lookup"><span data-stu-id="5d570-149">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="5d570-150">Nell'editor di Unity passare a **Edit > Project settings (> Project impostazioni)** e selezionare **XR Plugin Management (Gestione plug-in XR).**</span><span class="sxs-lookup"><span data-stu-id="5d570-150">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="5d570-151">Selezionare **Install XR Plugin Management (Installa gestione plug-in XR),** se visualizzato</span><span class="sxs-lookup"><span data-stu-id="5d570-151">Select **Install XR Plugin Management** if it appears</span></span>

![Screenshot della finestra Project Impostazioni aperta nell'editor unity con gestione plug-in XR evidenziata](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="5d570-153">Selezionare **Initialize XR on Startup (Inizializza XR all'avvio)** **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="5d570-153">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Screenshot della finestra Project impostazioni aperta nell'editor di Unity con la gestione del plug-in XR evidenziata](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="5d570-155">Selezionare la **sezione XR Plug-in Management (Gestione plug-in XR)** Windows Mixed Reality, selezionare tutte le caselle e impostare Depth Buffer Format (Formato buffer profondità) su  >   Depth Buffer **16 Bit (Buffer profondità a 16 bit)** </span><span class="sxs-lookup"><span data-stu-id="5d570-155">Select the **XR Plug-in Management** > **Windows Mixed Reality** section, check all boxes and set **Depth Buffer Format** to **Depth Buffer 16 Bit**</span></span>

![Screenshot della finestra Project impostazioni aperta nell'editor di Unity con Windows Mixed Reality sezione evidenziata](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="5d570-157">XR legacy</span><span class="sxs-lookup"><span data-stu-id="5d570-157">Legacy XR</span></span>](#tab/legacy)

> [!CAUTION]
> <span data-ttu-id="5d570-158">XR legacy è deprecato in Unity 2019 e rimosso in Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="5d570-158">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

<span data-ttu-id="5d570-159">Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="5d570-159">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra build Impostazioni aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](../../images/wmr-config-img-3.png)

<span data-ttu-id="5d570-161">Se la destinazione è HoloLens 2, è necessario passare alla piattaforma Windows universali:</span><span class="sxs-lookup"><span data-stu-id="5d570-161">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="5d570-162">Selezionare **File > Compilazione Impostazioni...**</span><span class="sxs-lookup"><span data-stu-id="5d570-162">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="5d570-163">Selezionare **Universal Windows Platform nell'elenco** Platform (Piattaforma) e selezionare Switch Platform **(Cambia piattaforma)**</span><span class="sxs-lookup"><span data-stu-id="5d570-163">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="5d570-164">Impostare **Architecture** (Architettura) su **ARM64**</span><span class="sxs-lookup"><span data-stu-id="5d570-164">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="5d570-165">Impostare **Dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="5d570-165">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="5d570-166">Impostare **Build Type** (Tipo di compilazione) su **D3D Project**</span><span class="sxs-lookup"><span data-stu-id="5d570-166">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="5d570-167">Impostare **Versione SDK di destinazione** su Più recente **installato**</span><span class="sxs-lookup"><span data-stu-id="5d570-167">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="5d570-168">Impostare **Build configuration (Configurazione build)** **su Release (Versione)** perché sono presenti problemi di prestazioni noti con Debug</span><span class="sxs-lookup"><span data-stu-id="5d570-168">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot della finestra Build Impostazioni aperta nell'editor di Unity con universal Windows Platform evidenziato](../../images/wmr-config-img-4.png)

<span data-ttu-id="5d570-170">Dopo aver impostato la piattaforma, è necessario invii a Unity una visualizzazione [immersiva](../../../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.</span><span class="sxs-lookup"><span data-stu-id="5d570-170">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

1. <span data-ttu-id="5d570-171">Aprire **Player Impostazioni...** dalla finestra **di Impostazioni... ed** espandere il **gruppo di Impostazioni XR**</span><span class="sxs-lookup"><span data-stu-id="5d570-171">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="5d570-172">Nella sezione **XR Impostazioni** selezionare **Virtual Reality Supported** (Realtà virtuale supportata) per aggiungere l'elenco Virtual Reality Devices (Dispositivi di realtà virtuale)</span><span class="sxs-lookup"><span data-stu-id="5d570-172">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="5d570-173">Impostare **Depth Format (Formato profondità)** su **16 bit depth (Profondità 16 bit)** e **selezionare Enable Depth Buffer Sharing (Abilita condivisione buffer di profondità)**</span><span class="sxs-lookup"><span data-stu-id="5d570-173">Set **Depth Format** to **16-bit depth** and check **Enable Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="5d570-174">Impostare **Stereo Rendering Mode** (Modalità di rendering stereo) su **Single Pass Instanced** (Istanze a singolo passaggio)</span><span class="sxs-lookup"><span data-stu-id="5d570-174">Set **Stereo Rendering Mode** to **Single Pass Instanced**</span></span>
5. <span data-ttu-id="5d570-175">Selezionare **WSA Holographic Remoting Supported se** si desidera usare la comunicazione remota in modalità di riproduzione olografica</span><span class="sxs-lookup"><span data-stu-id="5d570-175">Select **WSA Holographic Remoting Supported** if you'd like to use holographic play mode remoting</span></span>

![Screenshot della finestra Project impostazioni aperta nell'editor di Unity con la sezione Player settings evidenziata](../../images/wmr-config-img-9.png)
