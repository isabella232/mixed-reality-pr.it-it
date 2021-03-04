---
title: Configurare il progetto senza MRTK
description: Informazioni su come configurare un nuovo progetto Unity per la realtà mista di Windows senza il Toolkit di realtà mista.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, realtà mista, sviluppo, Guida introduttiva, nuovo progetto, realtà mista di Windows, UWP, XR, prestazioni
ms.openlocfilehash: bd25c56947007f90c0310ea9802bba91a81b0914
ms.sourcegitcommit: fd19bf57607c7ed94a849d4cf606bba2bb93e668
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2021
ms.locfileid: "102117625"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="cf96a-104">Configurazione del progetto senza MRTK</span><span class="sxs-lookup"><span data-stu-id="cf96a-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="cf96a-105">La realtà mista di Windows (WMR) è una piattaforma Microsoft introdotta come parte del sistema operativo Windows 10.</span><span class="sxs-lookup"><span data-stu-id="cf96a-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="cf96a-106">La piattaforma WMR consente di creare applicazioni che eseguono il rendering di contenuto digitale su dispositivi di visualizzazione olografici e VR.</span><span class="sxs-lookup"><span data-stu-id="cf96a-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="cf96a-107">Microsoft e la community hanno creato strumenti opensource come il Toolkit di [realtà mista (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) che configurerà automaticamente l'ambiente WMR, molti sviluppatori desiderano creare le proprie esperienze da zero.</span><span class="sxs-lookup"><span data-stu-id="cf96a-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="cf96a-108">Nella documentazione seguente viene illustrato come configurare correttamente un progetto per lo sviluppo di realtà mista se si utilizza MRTK o no.</span><span class="sxs-lookup"><span data-stu-id="cf96a-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="cf96a-109">Le impostazioni che è necessario modificare sono suddivise in due categorie: impostazioni per progetto e impostazioni per scena.</span><span class="sxs-lookup"><span data-stu-id="cf96a-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="cf96a-110">È sempre possibile importare MRTK in un secondo momento, quindi non è necessario prima di tutto procedere con la route manuale.</span><span class="sxs-lookup"><span data-stu-id="cf96a-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="cf96a-111">Se si sceglie l'installazione manuale di WMR, le impostazioni che è necessario modificare sono suddivise in due categorie: per progetto e per scena.</span><span class="sxs-lookup"><span data-stu-id="cf96a-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="cf96a-112">Impostazioni per progetto</span><span class="sxs-lookup"><span data-stu-id="cf96a-112">Per-project settings</span></span>

<span data-ttu-id="cf96a-113">Se la destinazione è Desktop VR, è consigliabile usare la piattaforma autonoma per PC selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="cf96a-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra impostazioni di compilazione aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

<span data-ttu-id="cf96a-115">Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="cf96a-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="cf96a-116">Seleziona **File > impostazioni di compilazione...**</span><span class="sxs-lookup"><span data-stu-id="cf96a-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="cf96a-117">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco piattaforma e selezionare **Switch Platform (Cambia piattaforma** )</span><span class="sxs-lookup"><span data-stu-id="cf96a-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="cf96a-118">Impostare l' **architettura** su **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="cf96a-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="cf96a-119">Impostare il **dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="cf96a-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="cf96a-120">Imposta **tipo di compilazione** su **D3D**</span><span class="sxs-lookup"><span data-stu-id="cf96a-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="cf96a-121">Impostare **UWP SDK** sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="cf96a-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="cf96a-122">Impostare la **configurazione della compilazione** su **Release** a causa di problemi noti relativi alle prestazioni con debug</span><span class="sxs-lookup"><span data-stu-id="cf96a-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot della finestra impostazioni di compilazione aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](images/wmr-config-img-4.png)

<span data-ttu-id="cf96a-124">Dopo aver impostato la piattaforma, è necessario consentire a Unity di creare una [visualizzazione immersiva](../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.</span><span class="sxs-lookup"><span data-stu-id="cf96a-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="cf96a-125">Per XRSDK</span><span class="sxs-lookup"><span data-stu-id="cf96a-125">For XRSDK</span></span> 

1. <span data-ttu-id="cf96a-126">Nell'editor di Unity passare a **Edit > Settings Project** e selezionare **XR plugin Management**</span><span class="sxs-lookup"><span data-stu-id="cf96a-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="cf96a-127">Selezionare **Install XR plugin Management**</span><span class="sxs-lookup"><span data-stu-id="cf96a-127">Select **Install XR Plugin Management**</span></span>

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la gestione dei plug-in XR evidenziata](images/wmr-config-img-5.png)

3. <span data-ttu-id="cf96a-129">Selezionare **Inizializza XR all'avvio** e **realtà mista di Windows**</span><span class="sxs-lookup"><span data-stu-id="cf96a-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la gestione dei plug-in XR evidenziata](images/wmr-config-img-7.png)

4. <span data-ttu-id="cf96a-131">Espandere la sezione **Gestione plug-in XR** e selezionare la scheda **impostazioni della piattaforma Windows Univeral**</span><span class="sxs-lookup"><span data-stu-id="cf96a-131">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="cf96a-132">Se si usa Unity 2020 o versioni successive, verranno visualizzate le opzioni per controllare **OpenXR (anteprima)** o la **realtà mista di Windows**</span><span class="sxs-lookup"><span data-stu-id="cf96a-132">If you are using Unity 2020 or later, you will see the options to check **OpenXR (preview)** or **Windows Mixed Reality**</span></span>
6. <span data-ttu-id="cf96a-133">È possibile scegliere Runtime.</span><span class="sxs-lookup"><span data-stu-id="cf96a-133">You can choose either runtime.</span></span>  <span data-ttu-id="cf96a-134">Se si sta sviluppando in modo specifico per HoloLens 2 o HP Reverb G2 e si decide di provare **OpenXR (anteprima)**, selezionare la casella OpenXR (Preview) ed esaminare la Guida all' [uso del plug-in realtà mista OpenXR per Unity](openxr-getting-started.md) per configurare correttamente questi dispositivi prima di tornare a questa esercitazione</span><span class="sxs-lookup"><span data-stu-id="cf96a-134">If you are specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR (preview)**, select the OpenXR (preview) box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>
7. <span data-ttu-id="cf96a-135">Se si decide di scegliere il plug-in per la **realtà mista di Windows** , selezionare tutte le caselle e impostare la **modalità di invio profondità** su **profondità a 16 bit**</span><span class="sxs-lookup"><span data-stu-id="cf96a-135">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la sezione realtà mista di Windows evidenziata](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="cf96a-137">Per la versione precedente di XR</span><span class="sxs-lookup"><span data-stu-id="cf96a-137">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="cf96a-138">La versione precedente di XR è deprecata in Unity 2019 ed è stata rimossa in Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="cf96a-138">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="cf96a-139">Apri **Impostazioni lettore...** dalle **impostazioni di compilazione... ed espandere il gruppo di** **impostazioni di XR**</span><span class="sxs-lookup"><span data-stu-id="cf96a-139">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="cf96a-140">Nella sezione **impostazioni di XR** selezionare **realtà virtuale supportata** per aggiungere l'elenco dispositivi della realtà virtuale</span><span class="sxs-lookup"><span data-stu-id="cf96a-140">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="cf96a-141">Imposta la profondità del **formato** a **16 bit** e Abilita la **condivisione del buffer di profondità**</span><span class="sxs-lookup"><span data-stu-id="cf96a-141">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="cf96a-142">Impostare la **modalità di rendering stereo** su **istanza Single Pass**</span><span class="sxs-lookup"><span data-stu-id="cf96a-142">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="cf96a-143">Selezionare la **comunicazione remota per WSA olografica supportata** se si vuole usare la comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="cf96a-143">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la sezione delle impostazioni del lettore evidenziata](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="cf96a-145">Aggiornamento del manifesto</span><span class="sxs-lookup"><span data-stu-id="cf96a-145">Updating the manifest</span></span>

<span data-ttu-id="cf96a-146">L'app ora può gestire il rendering olografico e l'input spaziale.</span><span class="sxs-lookup"><span data-stu-id="cf96a-146">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="cf96a-147">Tuttavia, l'app deve dichiarare le funzionalità appropriate nel manifesto per sfruttare le funzionalità specifiche.</span><span class="sxs-lookup"><span data-stu-id="cf96a-147">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="cf96a-148">È possibile trovare le funzionalità di progetto passando a **Impostazioni lettore > impostazioni per piattaforma UWP (Universal Windows Platform) > impostazioni di pubblicazione > funzionalità**.</span><span class="sxs-lookup"><span data-stu-id="cf96a-148">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="cf96a-149">È consigliabile fare in modo che le dichiarazioni di manifesto in Unity vengano incluse in tutti i progetti futuri esportati.</span><span class="sxs-lookup"><span data-stu-id="cf96a-149">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="cf96a-150">Le funzionalità applicabili per l'abilitazione di API Unity comunemente usate per la realtà mista sono:</span><span class="sxs-lookup"><span data-stu-id="cf96a-150">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="cf96a-151">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="cf96a-151">Capability</span></span>  |  <span data-ttu-id="cf96a-152">API che richiedono funzionalità</span><span class="sxs-lookup"><span data-stu-id="cf96a-152">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="cf96a-153">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="cf96a-153">SpatialPerception</span></span>  |  <span data-ttu-id="cf96a-154">SurfaceObserver (accesso ai mesh di [mapping spaziale](../../design/spatial-mapping.md) in HoloLens) &mdash; *Nessuna funzionalità necessaria per il rilevamento spaziale generale dell'auricolare*</span><span class="sxs-lookup"><span data-stu-id="cf96a-154">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="cf96a-155">WebCam</span><span class="sxs-lookup"><span data-stu-id="cf96a-155">WebCam</span></span>  |  <span data-ttu-id="cf96a-156">Acquisizione e VideoCapture</span><span class="sxs-lookup"><span data-stu-id="cf96a-156">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="cf96a-157">PicturesLibrary/VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="cf96a-157">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="cf96a-158">Fotocapture o VideoCapture, rispettivamente (quando si archivia il contenuto acquisito)</span><span class="sxs-lookup"><span data-stu-id="cf96a-158">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="cf96a-159">Microfono</span><span class="sxs-lookup"><span data-stu-id="cf96a-159">Microphone</span></span>  |  <span data-ttu-id="cf96a-160">VideoCapture (durante l'acquisizione dell'audio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="cf96a-160">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="cf96a-161">InternetClient</span><span class="sxs-lookup"><span data-stu-id="cf96a-161">InternetClient</span></span>  |  <span data-ttu-id="cf96a-162">DictationRecognizer (e per usare Unity Profiler)</span><span class="sxs-lookup"><span data-stu-id="cf96a-162">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="cf96a-163">Impostazioni qualità</span><span class="sxs-lookup"><span data-stu-id="cf96a-163">Quality settings</span></span>

<span data-ttu-id="cf96a-164">HoloLens dispone di una GPU di classe mobile.</span><span class="sxs-lookup"><span data-stu-id="cf96a-164">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="cf96a-165">Se l'app è destinata a HoloLens, è opportuno iniziare con le impostazioni di qualità nell'app ottimizzate per ottenere prestazioni più rapide per garantire la massima frequenza dei fotogrammi.</span><span class="sxs-lookup"><span data-stu-id="cf96a-165">If your app is targeting HoloLens, you'll want to start off with the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate.</span></span>  <span data-ttu-id="cf96a-166">Una volta completata la fase di sviluppo, è possibile prendere in considerazione la possibilità di eseguire il ping delle impostazioni di qualità per individuare il giusto equilibrio tra qualità e prestazioni:</span><span class="sxs-lookup"><span data-stu-id="cf96a-166">Once you have your are further along in your development you may consider upping the quality settings to find the right balance of quality and performance:</span></span> 

1. <span data-ttu-id="cf96a-167">Selezionare **modifica > impostazioni progetto > qualità**</span><span class="sxs-lookup"><span data-stu-id="cf96a-167">Select **Edit > Project Settings > Quality**</span></span> 
2. <span data-ttu-id="cf96a-168">Selezionare l' **elenco a discesa** sotto il logo di  **Windows Store**   e selezionare  **molto basso**.</span><span class="sxs-lookup"><span data-stu-id="cf96a-168">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="cf96a-169">Si saprà che l'impostazione viene applicata correttamente quando la casella nella colonna Windows Store e con una riga molto bassa è verde</span><span class="sxs-lookup"><span data-stu-id="cf96a-169">You'll know the setting is applied correctly when the box in the Windows Store column and Very Low row is green</span></span> 
3. <span data-ttu-id="cf96a-170">Nella sezione **Shadows**   selezionare **Disabilita ombreggiatura** .</span><span class="sxs-lookup"><span data-stu-id="cf96a-170">In the **Shadows** section, select **Disable Shadows**</span></span> 

<span data-ttu-id="cf96a-171">![Screenshot della finestra delle impostazioni del progetto aperta nell'editor di Unity con la sezione delle impostazioni di qualità evidenziata](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="cf96a-171">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="cf96a-172">*Impostazioni qualità Unity*</span><span class="sxs-lookup"><span data-stu-id="cf96a-172">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="cf96a-173">Impostazioni per scena</span><span class="sxs-lookup"><span data-stu-id="cf96a-173">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="cf96a-174">Impostazioni della fotocamera Unity</span><span class="sxs-lookup"><span data-stu-id="cf96a-174">Unity camera settings</span></span>

<span data-ttu-id="cf96a-175">Con la **realtà virtuale supportata** selezionata, il componente della [fotocamera Unity](camera-in-unity.md) gestisce il [rilevamento Head e il rendering stereoscopico](../platform-capabilities-and-apis/rendering.md).</span><span class="sxs-lookup"><span data-stu-id="cf96a-175">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="cf96a-176">Ciò significa che non è necessario sostituire l'oggetto fotocamera principale con una fotocamera personalizzata.</span><span class="sxs-lookup"><span data-stu-id="cf96a-176">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="cf96a-177">Se l'app è destinata a HoloLens in modo specifico, è necessario modificare alcune impostazioni per ottimizzare la visualizzazione trasparente del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cf96a-177">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="cf96a-178">Queste impostazioni consentono di visualizzare il contenuto olografico nel mondo fisico:</span><span class="sxs-lookup"><span data-stu-id="cf96a-178">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="cf96a-179">Nella **gerarchia** selezionare la **fotocamera principale**</span><span class="sxs-lookup"><span data-stu-id="cf96a-179">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="cf96a-180">Nel pannello **Inspector** impostare la **posizione** di trasformazione su 0, 0 **, 0,** in modo che la posizione della testa dell'utente inizi in corrispondenza dell'origine mondiale di Unity.</span><span class="sxs-lookup"><span data-stu-id="cf96a-180">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="cf96a-181">Modificare i **flag cancellati** in **colore a tinta unita**.</span><span class="sxs-lookup"><span data-stu-id="cf96a-181">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="cf96a-182">Modificare il colore di **sfondo** in **RGBA 0**, 0, 0, 0.</span><span class="sxs-lookup"><span data-stu-id="cf96a-182">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="cf96a-183">Il nero viene visualizzato come trasparente in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cf96a-183">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="cf96a-184">Modificare i **piani di ritaglio in prossimità** del [HoloLens consigliato](camera-in-unity.md#clip-planes) 0,85 (contatori).</span><span class="sxs-lookup"><span data-stu-id="cf96a-184">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="cf96a-185">![Screenshot della scheda di controllo aperta nell'editor di Unity](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="cf96a-185">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="cf96a-186">*Impostazioni della fotocamera Unity*</span><span class="sxs-lookup"><span data-stu-id="cf96a-186">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf96a-187">Se si elimina e si crea una nuova fotocamera, assicurarsi che la nuova fotocamera sia contrassegnata come **MainCamera**.</span><span class="sxs-lookup"><span data-stu-id="cf96a-187">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cf96a-188">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="cf96a-188">Next steps</span></span>

<span data-ttu-id="cf96a-189">Ora che il progetto è pronto, è possibile iniziare a sviluppare l'esperienza di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="cf96a-189">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="cf96a-190">Aggiungi [blocchi predefiniti principali](unity-development-overview.md#2-core-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="cf96a-190">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="cf96a-191">Scopri le [funzionalità della piattaforma disponibili e le API](unity-development-overview.md#3-advanced-features)</span><span class="sxs-lookup"><span data-stu-id="cf96a-191">Check out available [platform capabilities and APIs](unity-development-overview.md#3-advanced-features)</span></span>
* <span data-ttu-id="cf96a-192">Informazioni su come [distribuire l'app](../platform-capabilities-and-apis/using-visual-studio.md#)</span><span class="sxs-lookup"><span data-stu-id="cf96a-192">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#)</span></span>
* <span data-ttu-id="cf96a-193">Usare il [simulatore di realtà mista](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="cf96a-193">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="cf96a-194">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cf96a-194">See also</span></span>
* [<span data-ttu-id="cf96a-195">Installare gli strumenti</span><span class="sxs-lookup"><span data-stu-id="cf96a-195">Install the tools</span></span>](../install-the-tools.md)