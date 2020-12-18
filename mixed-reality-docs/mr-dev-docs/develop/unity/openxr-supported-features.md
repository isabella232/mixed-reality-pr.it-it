---
title: Funzionalità supportate per il plug-in OpenXR in Unity
description: Scopri le funzionalità supportate da OpenXR per lo sviluppo di realtà miste in Unity.
author: hferrone
ms.author: alexturn
ms.date: 12/15/2020
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realtà mista, MRTK, Toolkit per realtà mista, realtà aumentata, realtà virtuale, cuffie con realtà mista, informazioni, esercitazione, introduzione
ms.openlocfilehash: 1cbe9dd1ffb493bcc9da76e70dec9720f2d10340
ms.sourcegitcommit: 4bbf2f802117a9a3788b2b0e3b0a2f58e187f6ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/18/2020
ms.locfileid: "97665361"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="5eccc-104">Realtà mista OpenXR le funzionalità supportate in Unity</span><span class="sxs-lookup"><span data-stu-id="5eccc-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="5eccc-105">Il pacchetto di plug-in OpenXR per la **realtà mista** è un'estensione del plug-in **OpenXR** di Unity e supporta una suite di funzionalità per gli auricolari per la realtà mista HoloLens 2 e Windows.</span><span class="sxs-lookup"><span data-stu-id="5eccc-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="5eccc-106">Prima di continuare, assicurarsi di avere installato **unity 2020,2** o versione successiva, la versione del plug-in **OpenXR 0.1.1 o versione** successiva e che il progetto Unity sia [configurato per OpenXR](openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="5eccc-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.1** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="5eccc-107">Attività supportate</span><span class="sxs-lookup"><span data-stu-id="5eccc-107">What's supported</span></span>

<span data-ttu-id="5eccc-108">Attualmente sono supportate le funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="5eccc-108">The following features are currently supported:</span></span>

* <span data-ttu-id="5eccc-109">Supporta entrambe le applicazioni UWP per le applicazioni HoloLens 2 e Win32 VR per le cuffie di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="5eccc-109">Supports both UWP applications for HoloLens 2 and Win32 VR applications for Windows Mixed Reality headsets.</span></span>
* <span data-ttu-id="5eccc-110">Ottimizza il pacchetto UWP e l'interazione CoreWindow per le applicazioni HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5eccc-110">Optimizes UWP package and CoreWindow interaction for HoloLens 2 applications.</span></span>
* <span data-ttu-id="5eccc-111">Rilevamento della scalabilità globale tramite ancoraggi e spazio non vincolato.</span><span class="sxs-lookup"><span data-stu-id="5eccc-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="5eccc-112">[API di archiviazione di ancoraggio per salvare](#anchors-and-anchor-persistence) in modo permanente gli ancoraggi nell'archivio locale HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5eccc-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="5eccc-113">[Motion controller e Hand Interactions](#motion-controller-and-hand-interactions), incluso il nuovo controller HP Reverb G2.</span><span class="sxs-lookup"><span data-stu-id="5eccc-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="5eccc-114">Tracciatura manuale articolata con 26 giunzioni e input RADIUS Uniti.</span><span class="sxs-lookup"><span data-stu-id="5eccc-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="5eccc-115">Interazione con gli occhi su HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5eccc-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="5eccc-116">Individuazione della fotocamera Photo/video (PV) in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5eccc-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="5eccc-117">Acquisizione di realtà mista tramite il rendering di 3 occhi attraverso la fotocamera FV.</span><span class="sxs-lookup"><span data-stu-id="5eccc-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="5eccc-118">Supporta ["Play" in HoloLens 2 con l'app di comunicazione remota olografica](#holographic-remoting-in-unity-editor-play-mode), consentendo agli sviluppatori di eseguire il debug degli script senza compilare e distribuire nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5eccc-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="5eccc-119">Compatibile con MRTK Unity 2.5.2 tramite il pacchetto MRTK OpenXR adapter.</span><span class="sxs-lookup"><span data-stu-id="5eccc-119">Compatible with MRTK Unity 2.5.2 through MRTK OpenXR adapter package.</span></span> <missing link>
* <span data-ttu-id="5eccc-120">Compatibile con Unity [ARFoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) o versione successiva</span><span class="sxs-lookup"><span data-stu-id="5eccc-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later</span></span>

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="5eccc-121">Comunicazione remota olografica in modalità di riproduzione dell'editor Unity</span><span class="sxs-lookup"><span data-stu-id="5eccc-121">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="5eccc-122">La creazione di un progetto Unity UWP nel progetto di Visual Studio e quindi la creazione del pacchetto e la distribuzione in un dispositivo HoloLens 2 possono richiedere del tempo.</span><span class="sxs-lookup"><span data-stu-id="5eccc-122">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="5eccc-123">Una soluzione consiste nell'abilitare la comunicazione remota dell'editor olografica, che consente di eseguire il debug dello script C# usando la modalità "Play" direttamente in un dispositivo HoloLens 2 sulla rete.</span><span class="sxs-lookup"><span data-stu-id="5eccc-123">One solution is to enable the Holographic Editor Remoting, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="5eccc-124">Questo scenario consente di evitare il sovraccarico dovuto alla creazione e alla distribuzione di un pacchetto UWP nel dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="5eccc-124">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="5eccc-125">Per prima cosa, è necessario [installare l'app del lettore di comunicazione remota olografica](https://www.microsoft.com/store/productId/9NBLGGH4SV40) dallo Store nel HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5eccc-125">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from Store on your HoloLens 2</span></span>  
2. <span data-ttu-id="5eccc-126">Eseguire l'app del lettore di comunicazione remota olografica in HoloLens 2 per visualizzare il numero di versione e l'indirizzo IP per la connessione</span><span class="sxs-lookup"><span data-stu-id="5eccc-126">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="5eccc-127">Per usare il plug-in OpenXR, è necessario usare la versione 2.4 o successiva.</span><span class="sxs-lookup"><span data-stu-id="5eccc-127">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

![Screenshot del lettore di comunicazione remota olografico in esecuzione in HoloLens](images/openxr-features-img-01.png)

3. <span data-ttu-id="5eccc-129">Aprire la finestra di dialogo **modifica-> impostazioni progetto**, passare alla **Gestione plug-in XR** e selezionare la casella **set di funzionalità di realtà mista di Windows** :</span><span class="sxs-lookup"><span data-stu-id="5eccc-129">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con la gestione dei plug-in di XR evidenziata](images/openxr-features-img-02.png)

4. <span data-ttu-id="5eccc-131">Espandere la sezione **funzionalità** in **OpenXR** e selezionare **Mostra tutto**</span><span class="sxs-lookup"><span data-stu-id="5eccc-131">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
5. <span data-ttu-id="5eccc-132">Controllare la casella di controllo **Remote editor olografico** e immettere l'indirizzo IP ottenuto dall'app di comunicazione remota olografica:</span><span class="sxs-lookup"><span data-stu-id="5eccc-132">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con le funzionalità evidenziate](images/openxr-features-img-03.png)

<span data-ttu-id="5eccc-134">A questo punto è possibile fare clic sul pulsante "Riproduci" per riprodurre l'app Unity nell'app per la comunicazione remota olografica nella HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5eccc-134">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="5eccc-135">È anche possibile [aggiungere Visual Studio a Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) per eseguire il debug degli script C# in modalità Play.</span><span class="sxs-lookup"><span data-stu-id="5eccc-135">You can also [attach Visual Studio to Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="5eccc-136">A partire dalla versione 0.1.0 la comunicazione remota olografica, il runtime non supporta la funzionalità di ancoraggio e le funzionalità di ARAnchorManager non funzioneranno tramite la comunicazione remota.</span><span class="sxs-lookup"><span data-stu-id="5eccc-136">As of version 0.1.0 the Holographic Remoting, runtime doesn’t support Anchor feature, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="5eccc-137">Questa funzionalità è disponibile nelle versioni future.</span><span class="sxs-lookup"><span data-stu-id="5eccc-137">This feature is coming in future releases.</span></span>

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="5eccc-138">Ancoraggi e persistenza di ancoraggio</span><span class="sxs-lookup"><span data-stu-id="5eccc-138">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="5eccc-139">Il plug-in di OpenXR realtà mista fornisce la funzionalità di ancoraggio di base tramite un'implementazione di ARFoundation **ARAnchorManager** di Unity.</span><span class="sxs-lookup"><span data-stu-id="5eccc-139">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="5eccc-140">Per apprendere le nozioni di base su **ARAnchor** in ARFoundation, vedere il [Manuale di ARFoundation per AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="5eccc-140">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="5eccc-141">A partire dalla versione 0.1.0, questo plug-in supporta tutte le funzionalità di ARAnchorManager, ad eccezione della creazione di ancoraggi collegati a un piano, che sarà disponibile in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="5eccc-141">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="5eccc-142">Persistenza di ancoraggio e XRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="5eccc-142">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="5eccc-143">Un'API aggiuntiva denominata **XRAnchorStore** consente di salvare in modo permanente gli ancoraggi tra le sessioni.</span><span class="sxs-lookup"><span data-stu-id="5eccc-143">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="5eccc-144">XRAnchorStore è una rappresentazione degli ancoraggi salvati nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5eccc-144">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="5eccc-145">Gli ancoraggi possono essere salvati in permanenza da **ARAnchors** nella scena Unity, caricati dall'archiviazione in nuovi **ARAnchors** o eliminati dall'archivio.</span><span class="sxs-lookup"><span data-stu-id="5eccc-145">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="5eccc-146">Questi ancoraggi devono essere salvati e caricati nello stesso dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5eccc-146">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="5eccc-147">L'archiviazione di ancoraggio tra dispositivi verrà supportata tramite ancoraggi spaziali di Azure in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="5eccc-147">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the 
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if 
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="5eccc-148">Per caricare XRAnchorStore, il plug-in fornisce un metodo di estensione in XRAnchorSubsystem, il sottosistema di un ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="5eccc-148">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="5eccc-149">Per usare questo metodo di estensione, accedervi dal sottosistema di ARAnchorManager come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="5eccc-149">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>
 
``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>(); 
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync(); 
```

<span data-ttu-id="5eccc-150">Per un esempio completo di come salvare in modo permanente/non permanente gli ancoraggi, vedere gli script di ancoraggio-> di esempio GameObject e AnchorsSample.cs nella scena di [esempio di plug-in realtà mista OpenXR](openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="5eccc-150">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![Screenshot del pannello gerarchia aperto nell'editor di Unity con l'esempio Anchors evidenziato](images/openxr-features-img-04.png)

![Screenshot del pannello Inspector aperto nell'editor di Unity con lo script di esempio Anchors evidenziato](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="5eccc-153">Interazioni tra controller di movimento e mano</span><span class="sxs-lookup"><span data-stu-id="5eccc-153">Motion controller and hand interactions</span></span>

<span data-ttu-id="5eccc-154">Per apprendere le nozioni di base sulle interazioni tra realtà mista in Unity, vedere il [Manuale di Unity per Unity XR input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span><span class="sxs-lookup"><span data-stu-id="5eccc-154">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="5eccc-155">Questa documentazione di Unity riguarda i mapping da input specifici del controller a **InputFeatureUsage** più generalizzabili, il modo in cui possono essere identificati e categorizzati gli input XR disponibili, come leggere i dati da questi input e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="5eccc-155">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span> 
 
<span data-ttu-id="5eccc-156">Il plug-in OpenXR per la realtà mista fornisce profili di interazione di input aggiuntivi, mappati a **InputFeatureUsage** standard, come descritto di seguito:</span><span class="sxs-lookup"><span data-stu-id="5eccc-156">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span> 
 
| <span data-ttu-id="5eccc-157">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="5eccc-157">InputFeatureUsage</span></span> | <span data-ttu-id="5eccc-158">Controller HP Reverb G2 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="5eccc-158">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="5eccc-159">Mano HoloLens (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="5eccc-159">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="5eccc-160">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="5eccc-160">primary2DAxis</span></span> | <span data-ttu-id="5eccc-161">Joystick</span><span class="sxs-lookup"><span data-stu-id="5eccc-161">Joystick</span></span> | |
| <span data-ttu-id="5eccc-162">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="5eccc-162">primary2DAxisClick</span></span> | <span data-ttu-id="5eccc-163">Joystick-fare clic</span><span class="sxs-lookup"><span data-stu-id="5eccc-163">Joystick - Click</span></span> | |
| <span data-ttu-id="5eccc-164">trigger</span><span class="sxs-lookup"><span data-stu-id="5eccc-164">trigger</span></span> | <span data-ttu-id="5eccc-165">Trigger</span><span class="sxs-lookup"><span data-stu-id="5eccc-165">Trigger</span></span>  | |
| <span data-ttu-id="5eccc-166">ridimensionamento</span><span class="sxs-lookup"><span data-stu-id="5eccc-166">grip</span></span> | <span data-ttu-id="5eccc-167">Ridimensionamento</span><span class="sxs-lookup"><span data-stu-id="5eccc-167">Grip</span></span> | <span data-ttu-id="5eccc-168">Toccare o fare pressione</span><span class="sxs-lookup"><span data-stu-id="5eccc-168">Air tap or squeeze</span></span> |
| <span data-ttu-id="5eccc-169">primaryButton</span><span class="sxs-lookup"><span data-stu-id="5eccc-169">primaryButton</span></span> | <span data-ttu-id="5eccc-170">[X/A]-premere</span><span class="sxs-lookup"><span data-stu-id="5eccc-170">[X/A] - Press</span></span> | <span data-ttu-id="5eccc-171">Simulazione del tocco</span><span class="sxs-lookup"><span data-stu-id="5eccc-171">Air tap</span></span> |
| <span data-ttu-id="5eccc-172">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="5eccc-172">secondaryButton</span></span> | <span data-ttu-id="5eccc-173">[S/B]-premere</span><span class="sxs-lookup"><span data-stu-id="5eccc-173">[Y/B] - Press</span></span> | |
| <span data-ttu-id="5eccc-174">gripButton</span><span class="sxs-lookup"><span data-stu-id="5eccc-174">gripButton</span></span> | <span data-ttu-id="5eccc-175">Pressione del pulsante</span><span class="sxs-lookup"><span data-stu-id="5eccc-175">Grip - Press</span></span> | |
| <span data-ttu-id="5eccc-176">triggerButton</span><span class="sxs-lookup"><span data-stu-id="5eccc-176">triggerButton</span></span> | <span data-ttu-id="5eccc-177">Trigger-premere</span><span class="sxs-lookup"><span data-stu-id="5eccc-177">Trigger - Press</span></span> | |
| <span data-ttu-id="5eccc-178">menuButton</span><span class="sxs-lookup"><span data-stu-id="5eccc-178">menuButton</span></span> | <span data-ttu-id="5eccc-179">Menu</span><span class="sxs-lookup"><span data-stu-id="5eccc-179">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="5eccc-180">Pose AIM e grip</span><span class="sxs-lookup"><span data-stu-id="5eccc-180">Aim and Grip Poses</span></span>

<span data-ttu-id="5eccc-181">È possibile accedere a due set di pose tramite interazioni di input OpenXR:</span><span class="sxs-lookup"><span data-stu-id="5eccc-181">You have access to two sets of poses through OpenXR input interactions:</span></span> 
* <span data-ttu-id="5eccc-182">Il grip si pone per il rendering degli oggetti a mano</span><span class="sxs-lookup"><span data-stu-id="5eccc-182">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="5eccc-183">L'obiettivo si pone per puntare al mondo.</span><span class="sxs-lookup"><span data-stu-id="5eccc-183">The aim poses for pointing into the world.</span></span> 

<span data-ttu-id="5eccc-184">Altre informazioni su questa progettazione e sulle differenze tra le due pose sono reperibili nella [specifica OpenXR-sottopercorsi di input](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span><span class="sxs-lookup"><span data-stu-id="5eccc-184">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="5eccc-185">Le pose fornite da InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity** e **DeviceAngularVelocity** rappresentano tutti la postura del **grip** OpenXR.</span><span class="sxs-lookup"><span data-stu-id="5eccc-185">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="5eccc-186">InputFeatureUsages correlate alle pose del grip sono definite in [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)di Unity.</span><span class="sxs-lookup"><span data-stu-id="5eccc-186">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="5eccc-187">Le pose fornite da InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity** e **PointerAngularVelocity** rappresentano tutti il OpenXR **AIM** pose.</span><span class="sxs-lookup"><span data-stu-id="5eccc-187">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="5eccc-188">Questi InputFeatureUsages non sono definiti in alcun file C# incluso, quindi è necessario definire il proprio InputFeatureUsages come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="5eccc-188">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="5eccc-189">Haptics</span><span class="sxs-lookup"><span data-stu-id="5eccc-189">Haptics</span></span>

<span data-ttu-id="5eccc-190">Per informazioni sull'uso di haptics nel sistema di input XR di Unity, è possibile trovare la documentazione nel [Manuale di Unity per Unity XR input-haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span><span class="sxs-lookup"><span data-stu-id="5eccc-190">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span> 

## <a name="whats-coming-soon"></a><span data-ttu-id="5eccc-191">Presto disponibile</span><span class="sxs-lookup"><span data-stu-id="5eccc-191">What's coming soon</span></span>

<span data-ttu-id="5eccc-192">I problemi e le funzionalità mancanti seguenti sono noti con la versione del plug-in OpenXR della realtà mista **0.1.0**.</span><span class="sxs-lookup"><span data-stu-id="5eccc-192">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="5eccc-193">Stiamo lavorando a questi e verranno rilasciate correzioni e nuove funzionalità nelle prossime versioni.</span><span class="sxs-lookup"><span data-stu-id="5eccc-193">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="5eccc-194">**ARPlaneSubsystem** non è ancora supportato.</span><span class="sxs-lookup"><span data-stu-id="5eccc-194">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="5eccc-195">Le API **ARPlaneManager**, **ARRaycastManager** e related, ad esempio **ARAnchorManager. AttachAnchor** , non sono supportate in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5eccc-195">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="5eccc-196">L' **ancoraggio** non è ancora supportato dalla comunicazione remota olografica, ma sarà disponibile a breve in futuro.</span><span class="sxs-lookup"><span data-stu-id="5eccc-196">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="5eccc-197">Il rilevamento della **mesh manuale** , i **codici QR** e **XRMeshSubsystem** non sono ancora supportati.</span><span class="sxs-lookup"><span data-stu-id="5eccc-197">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="5eccc-198">Il supporto di **ancoraggi spaziali di Azure** è disponibile in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="5eccc-198">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="5eccc-199">**Arm64** è l'unica piattaforma supportata per le app HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5eccc-199">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="5eccc-200">La piattaforma **ARM** sarà disponibile in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="5eccc-200">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="5eccc-201">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="5eccc-201">Troubleshooting</span></span> 

<span data-ttu-id="5eccc-202">Quando si sospende e si riprende un'app Unity in HoloLens 2, l'app non può essere ripresa correttamente, il che comporta 4 puntini di rotazione nella visualizzazione HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5eccc-202">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span> 
* <span data-ttu-id="5eccc-203">Impostare la **modalità di invio di profondità** su **None** nelle impostazioni del progetto OpenXR come soluzione alternativa</span><span class="sxs-lookup"><span data-stu-id="5eccc-203">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
