---
title: Configurare il progetto senza MRTK
description: Informazioni su come configurare un nuovo progetto Unity per la realtà mista di Windows senza il Toolkit di realtà mista.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, realtà mista, sviluppo, Guida introduttiva, nuovo progetto, realtà mista di Windows, UWP, XR, prestazioni
ms.openlocfilehash: 47ca4041e997d623d08fa1732f7039c655810bfc
ms.sourcegitcommit: b0fb5497bf9f280ba5610c30e4b9e5aa1cda52c9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/23/2021
ms.locfileid: "104837418"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="b52e0-104">Configurazione del progetto senza MRTK</span><span class="sxs-lookup"><span data-stu-id="b52e0-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="b52e0-105">La realtà mista di Windows (WMR) è una piattaforma Microsoft introdotta come parte del sistema operativo Windows 10.</span><span class="sxs-lookup"><span data-stu-id="b52e0-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="b52e0-106">La piattaforma WMR consente di creare applicazioni che eseguono il rendering di contenuto digitale su dispositivi di visualizzazione olografici e VR.</span><span class="sxs-lookup"><span data-stu-id="b52e0-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="b52e0-107">Microsoft e la community hanno creato strumenti opensource come il Toolkit di [realtà mista (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) che configurerà automaticamente l'ambiente WMR, molti sviluppatori desiderano creare le proprie esperienze da zero.</span><span class="sxs-lookup"><span data-stu-id="b52e0-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="b52e0-108">Nella documentazione seguente viene illustrato come configurare correttamente un progetto per lo sviluppo di realtà mista se si utilizza MRTK o no.</span><span class="sxs-lookup"><span data-stu-id="b52e0-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="b52e0-109">Le impostazioni che è necessario modificare sono suddivise in due categorie: impostazioni per progetto e impostazioni per scena.</span><span class="sxs-lookup"><span data-stu-id="b52e0-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="b52e0-110">È sempre possibile importare MRTK in un secondo momento, quindi non è necessario prima di tutto procedere con la route manuale.</span><span class="sxs-lookup"><span data-stu-id="b52e0-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="b52e0-111">Se si sceglie l'installazione manuale di WMR, le impostazioni che è necessario modificare sono suddivise in due categorie: per progetto e per scena.</span><span class="sxs-lookup"><span data-stu-id="b52e0-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="b52e0-112">Impostazioni per progetto</span><span class="sxs-lookup"><span data-stu-id="b52e0-112">Per-project settings</span></span>

<span data-ttu-id="b52e0-113">Se la destinazione è Desktop VR, è consigliabile usare la piattaforma autonoma per PC selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="b52e0-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra impostazioni di compilazione aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

<span data-ttu-id="b52e0-115">Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="b52e0-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="b52e0-116">Seleziona **File > impostazioni di compilazione...**</span><span class="sxs-lookup"><span data-stu-id="b52e0-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="b52e0-117">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco piattaforma e selezionare **Switch Platform (Cambia piattaforma** )</span><span class="sxs-lookup"><span data-stu-id="b52e0-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="b52e0-118">Impostare l' **architettura** su **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="b52e0-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="b52e0-119">Impostare il **dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="b52e0-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="b52e0-120">Imposta **tipo di compilazione** su **D3D**</span><span class="sxs-lookup"><span data-stu-id="b52e0-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="b52e0-121">Impostare **UWP SDK** sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="b52e0-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="b52e0-122">Impostare la **configurazione della compilazione** su **Release** a causa di problemi noti relativi alle prestazioni con debug</span><span class="sxs-lookup"><span data-stu-id="b52e0-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot della finestra impostazioni di compilazione aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](images/wmr-config-img-4.png)

<span data-ttu-id="b52e0-124">Dopo aver impostato la piattaforma, è necessario consentire a Unity di creare una [visualizzazione immersiva](../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.</span><span class="sxs-lookup"><span data-stu-id="b52e0-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="b52e0-125">Per XRSDK</span><span class="sxs-lookup"><span data-stu-id="b52e0-125">For XRSDK</span></span> 

1. <span data-ttu-id="b52e0-126">Nell'editor di Unity passare a **Edit > Settings Project** e selezionare **XR plugin Management**</span><span class="sxs-lookup"><span data-stu-id="b52e0-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="b52e0-127">Selezionare **Install XR plugin Management**</span><span class="sxs-lookup"><span data-stu-id="b52e0-127">Select **Install XR Plugin Management**</span></span>

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la gestione dei plug-in XR evidenziata](images/wmr-config-img-5.png)

3. <span data-ttu-id="b52e0-129">Selezionare **Inizializza XR all'avvio** e **realtà mista di Windows**</span><span class="sxs-lookup"><span data-stu-id="b52e0-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la gestione dei plug-in XR evidenziata](images/wmr-config-img-7.png)

4. <span data-ttu-id="b52e0-131">Espandere la sezione **Gestione plug-in XR** e selezionare la scheda **impostazioni della piattaforma Windows Univeral**</span><span class="sxs-lookup"><span data-stu-id="b52e0-131">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="b52e0-132">Se si usa Unity 2020 o versioni successive, verranno visualizzate le opzioni per controllare **OpenXR** o la **realtà mista di Windows**.</span><span class="sxs-lookup"><span data-stu-id="b52e0-132">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="b52e0-133">È possibile scegliere Runtime.</span><span class="sxs-lookup"><span data-stu-id="b52e0-133">You can choose either runtime.</span></span>  <span data-ttu-id="b52e0-134">Se si sta sviluppando in modo specifico per HoloLens 2 o HP Reverb G2 e si decide di provare il **OpenXR**, selezionare la casella OpenXR ed esaminare la Guida all' [uso del plug-in realtà mista OpenXR per Unity](openxr-getting-started.md) per configurarlo correttamente per questi dispositivi prima di tornare a questa esercitazione</span><span class="sxs-lookup"><span data-stu-id="b52e0-134">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="b52e0-135">A partire da Unity 2020 LTS, Microsoft abbraccia lo sviluppo con OpenXR.</span><span class="sxs-lookup"><span data-stu-id="b52e0-135">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="b52e0-136">Quando si esegue la migrazione a questo percorso, in Unity 2021,1 il plug-in Windows XR verrà deprecato e rimosso in 2021,2 rendendo OpenXR l'unico percorso supportato.</span><span class="sxs-lookup"><span data-stu-id="b52e0-136">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="b52e0-137">Altre informazioni sono disponibili in [uso del plug-in OpenXR per la realtà mista](openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="b52e0-137">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="b52e0-138">Se si decide di scegliere il plug-in per la **realtà mista di Windows** , selezionare tutte le caselle e impostare la **modalità di invio profondità** su **profondità a 16 bit**</span><span class="sxs-lookup"><span data-stu-id="b52e0-138">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la sezione realtà mista di Windows evidenziata](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="b52e0-140">Per la versione precedente di XR</span><span class="sxs-lookup"><span data-stu-id="b52e0-140">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="b52e0-141">La versione precedente di XR è deprecata in Unity 2019 ed è stata rimossa in Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="b52e0-141">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="b52e0-142">Apri **Impostazioni lettore...** dalle **impostazioni di compilazione... ed espandere il gruppo di** **impostazioni di XR**</span><span class="sxs-lookup"><span data-stu-id="b52e0-142">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="b52e0-143">Nella sezione **impostazioni di XR** selezionare **realtà virtuale supportata** per aggiungere l'elenco dispositivi della realtà virtuale</span><span class="sxs-lookup"><span data-stu-id="b52e0-143">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="b52e0-144">Imposta la profondità del **formato** a **16 bit** e Abilita la **condivisione del buffer di profondità**</span><span class="sxs-lookup"><span data-stu-id="b52e0-144">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="b52e0-145">Impostare la **modalità di rendering stereo** su **istanza Single Pass**</span><span class="sxs-lookup"><span data-stu-id="b52e0-145">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="b52e0-146">Selezionare la **comunicazione remota per WSA olografica supportata** se si vuole usare la comunicazione remota olografica</span><span class="sxs-lookup"><span data-stu-id="b52e0-146">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Screenshot della finestra Impostazioni progetto aperta nell'editor di Unity con la sezione delle impostazioni del lettore evidenziata](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="b52e0-148">Aggiornamento del manifesto</span><span class="sxs-lookup"><span data-stu-id="b52e0-148">Updating the manifest</span></span>

<span data-ttu-id="b52e0-149">L'app ora può gestire il rendering olografico e l'input spaziale.</span><span class="sxs-lookup"><span data-stu-id="b52e0-149">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="b52e0-150">Tuttavia, l'app deve dichiarare le funzionalità appropriate nel manifesto per sfruttare le funzionalità specifiche.</span><span class="sxs-lookup"><span data-stu-id="b52e0-150">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="b52e0-151">È possibile trovare le funzionalità di progetto passando a **Impostazioni lettore > impostazioni per piattaforma UWP (Universal Windows Platform) > impostazioni di pubblicazione > funzionalità**.</span><span class="sxs-lookup"><span data-stu-id="b52e0-151">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="b52e0-152">È consigliabile fare in modo che le dichiarazioni di manifesto in Unity vengano incluse in tutti i progetti futuri esportati.</span><span class="sxs-lookup"><span data-stu-id="b52e0-152">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="b52e0-153">Le funzionalità applicabili per l'abilitazione di API Unity comunemente usate per la realtà mista sono:</span><span class="sxs-lookup"><span data-stu-id="b52e0-153">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="b52e0-154">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="b52e0-154">Capability</span></span>  |  <span data-ttu-id="b52e0-155">API che richiedono funzionalità</span><span class="sxs-lookup"><span data-stu-id="b52e0-155">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="b52e0-156">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="b52e0-156">SpatialPerception</span></span>  |  <span data-ttu-id="b52e0-157">SurfaceObserver (accesso ai mesh di [mapping spaziale](../../design/spatial-mapping.md) in HoloLens) &mdash; *Nessuna funzionalità necessaria per il rilevamento spaziale generale dell'auricolare*</span><span class="sxs-lookup"><span data-stu-id="b52e0-157">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="b52e0-158">WebCam</span><span class="sxs-lookup"><span data-stu-id="b52e0-158">WebCam</span></span>  |  <span data-ttu-id="b52e0-159">Acquisizione e VideoCapture</span><span class="sxs-lookup"><span data-stu-id="b52e0-159">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="b52e0-160">PicturesLibrary/VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="b52e0-160">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="b52e0-161">Fotocapture o VideoCapture, rispettivamente (quando si archivia il contenuto acquisito)</span><span class="sxs-lookup"><span data-stu-id="b52e0-161">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="b52e0-162">Microfono</span><span class="sxs-lookup"><span data-stu-id="b52e0-162">Microphone</span></span>  |  <span data-ttu-id="b52e0-163">VideoCapture (durante l'acquisizione dell'audio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="b52e0-163">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="b52e0-164">InternetClient</span><span class="sxs-lookup"><span data-stu-id="b52e0-164">InternetClient</span></span>  |  <span data-ttu-id="b52e0-165">DictationRecognizer (e per usare Unity Profiler)</span><span class="sxs-lookup"><span data-stu-id="b52e0-165">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="b52e0-166">Impostazioni qualità</span><span class="sxs-lookup"><span data-stu-id="b52e0-166">Quality settings</span></span>

<span data-ttu-id="b52e0-167">HoloLens dispone di una GPU di classe mobile.</span><span class="sxs-lookup"><span data-stu-id="b52e0-167">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="b52e0-168">Se l'app è destinata a HoloLens, è opportuno iniziare con le impostazioni di qualità nell'app ottimizzate per ottenere prestazioni più rapide per garantire la massima frequenza dei fotogrammi.</span><span class="sxs-lookup"><span data-stu-id="b52e0-168">If your app is targeting HoloLens, you'll want to start off with the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate.</span></span>  <span data-ttu-id="b52e0-169">Una volta completata la fase di sviluppo, è possibile prendere in considerazione la possibilità di eseguire il ping delle impostazioni di qualità per individuare il giusto equilibrio tra qualità e prestazioni:</span><span class="sxs-lookup"><span data-stu-id="b52e0-169">Once you have your are further along in your development you may consider upping the quality settings to find the right balance of quality and performance:</span></span> 

1. <span data-ttu-id="b52e0-170">Selezionare **modifica > impostazioni progetto > qualità**</span><span class="sxs-lookup"><span data-stu-id="b52e0-170">Select **Edit > Project Settings > Quality**</span></span> 
2. <span data-ttu-id="b52e0-171">Selezionare l' **elenco a discesa** sotto il logo di  **Windows Store**   e selezionare  **molto basso**.</span><span class="sxs-lookup"><span data-stu-id="b52e0-171">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="b52e0-172">Si saprà che l'impostazione viene applicata correttamente quando la casella nella colonna Windows Store e con una riga molto bassa è verde</span><span class="sxs-lookup"><span data-stu-id="b52e0-172">You'll know the setting is applied correctly when the box in the Windows Store column and Very Low row is green</span></span> 
3. <span data-ttu-id="b52e0-173">Nella sezione **Shadows**   selezionare **Disabilita ombreggiatura** .</span><span class="sxs-lookup"><span data-stu-id="b52e0-173">In the **Shadows** section, select **Disable Shadows**</span></span> 

<span data-ttu-id="b52e0-174">![Screenshot della finestra delle impostazioni del progetto aperta nell'editor di Unity con la sezione delle impostazioni di qualità evidenziata](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="b52e0-174">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="b52e0-175">*Impostazioni qualità Unity*</span><span class="sxs-lookup"><span data-stu-id="b52e0-175">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="b52e0-176">Impostazioni per scena</span><span class="sxs-lookup"><span data-stu-id="b52e0-176">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="b52e0-177">Impostazioni della fotocamera Unity</span><span class="sxs-lookup"><span data-stu-id="b52e0-177">Unity camera settings</span></span>

<span data-ttu-id="b52e0-178">Con la **realtà virtuale supportata** selezionata, il componente della [fotocamera Unity](camera-in-unity.md) gestisce il [rilevamento Head e il rendering stereoscopico](../platform-capabilities-and-apis/rendering.md).</span><span class="sxs-lookup"><span data-stu-id="b52e0-178">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="b52e0-179">Ciò significa che non è necessario sostituire l'oggetto fotocamera principale con una fotocamera personalizzata.</span><span class="sxs-lookup"><span data-stu-id="b52e0-179">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="b52e0-180">Se l'app è destinata a HoloLens in modo specifico, è necessario modificare alcune impostazioni per ottimizzare la visualizzazione trasparente del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b52e0-180">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="b52e0-181">Queste impostazioni consentono di visualizzare il contenuto olografico nel mondo fisico:</span><span class="sxs-lookup"><span data-stu-id="b52e0-181">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="b52e0-182">Nella **gerarchia** selezionare la **fotocamera principale**</span><span class="sxs-lookup"><span data-stu-id="b52e0-182">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="b52e0-183">Nel pannello **Inspector** impostare la **posizione** di trasformazione su 0, 0 **, 0,** in modo che la posizione della testa dell'utente inizi in corrispondenza dell'origine mondiale di Unity.</span><span class="sxs-lookup"><span data-stu-id="b52e0-183">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="b52e0-184">Modificare i **flag cancellati** in **colore a tinta unita**.</span><span class="sxs-lookup"><span data-stu-id="b52e0-184">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="b52e0-185">Modificare il colore di **sfondo** in **RGBA 0**, 0, 0, 0.</span><span class="sxs-lookup"><span data-stu-id="b52e0-185">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="b52e0-186">Il nero viene visualizzato come trasparente in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b52e0-186">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="b52e0-187">Modificare i **piani di ritaglio in prossimità** del [HoloLens consigliato](camera-in-unity.md#clip-planes) 0,85 (contatori).</span><span class="sxs-lookup"><span data-stu-id="b52e0-187">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="b52e0-188">![Screenshot della scheda di controllo aperta nell'editor di Unity](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="b52e0-188">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="b52e0-189">*Impostazioni della fotocamera Unity*</span><span class="sxs-lookup"><span data-stu-id="b52e0-189">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b52e0-190">Se si elimina e si crea una nuova fotocamera, assicurarsi che la nuova fotocamera sia contrassegnata come **MainCamera**.</span><span class="sxs-lookup"><span data-stu-id="b52e0-190">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b52e0-191">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="b52e0-191">Next steps</span></span>

<span data-ttu-id="b52e0-192">Ora che il progetto è pronto, è possibile iniziare a sviluppare l'esperienza di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="b52e0-192">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="b52e0-193">Aggiungi [blocchi predefiniti principali](unity-development-overview.md#2-core-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="b52e0-193">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="b52e0-194">Scopri le [funzionalità della piattaforma disponibili e le API](unity-development-overview.md#3-advanced-features)</span><span class="sxs-lookup"><span data-stu-id="b52e0-194">Check out available [platform capabilities and APIs](unity-development-overview.md#3-advanced-features)</span></span>
* <span data-ttu-id="b52e0-195">Informazioni su come [distribuire l'app](../platform-capabilities-and-apis/using-visual-studio.md#)</span><span class="sxs-lookup"><span data-stu-id="b52e0-195">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#)</span></span>
* <span data-ttu-id="b52e0-196">Usare il [simulatore di realtà mista](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="b52e0-196">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="b52e0-197">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b52e0-197">See also</span></span>
* [<span data-ttu-id="b52e0-198">Installare gli strumenti</span><span class="sxs-lookup"><span data-stu-id="b52e0-198">Install the tools</span></span>](../install-the-tools.md)