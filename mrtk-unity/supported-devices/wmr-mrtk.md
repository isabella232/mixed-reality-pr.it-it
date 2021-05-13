---
title: Distribuzione in dispositivi Hololens e WMR
description: Documentazione per compilare e distribuire app in vari dispositivi.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, Visual Studio
ms.openlocfilehash: ec66c6ccb8cf1c702fed804230f5cf3ca0526139
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852444"
---
# <a name="building-and-deploying-mrtk-uwp"></a><span data-ttu-id="570e9-104">Compilazione e distribuzione di MRTK (UWP)</span><span class="sxs-lookup"><span data-stu-id="570e9-104">Building and deploying MRTK (UWP)</span></span>

<span data-ttu-id="570e9-105">Per eseguire un'app nel dispositivo come app autonoma (per HoloLens, Android, iOS e così via), il passaggio di compilazione e distribuzione deve essere eseguito nel progetto unity.</span><span class="sxs-lookup"><span data-stu-id="570e9-105">To run an app on device as a standalone app (for HoloLens, Android, iOS, etc.), the build and deploy step needs to be executed in the unity project.</span></span> <span data-ttu-id="570e9-106">La compilazione e la distribuzione di un'app che usa MRTK è esattamente come la compilazione e la distribuzione di qualsiasi altra app Unity.</span><span class="sxs-lookup"><span data-stu-id="570e9-106">Building and deploying an app that uses MRTK is just like building and deploying any other Unity app.</span></span> <span data-ttu-id="570e9-107">Non sono disponibili istruzioni specifiche di MRTK.</span><span class="sxs-lookup"><span data-stu-id="570e9-107">There are no MRTK-specific instructions.</span></span> <span data-ttu-id="570e9-108">Leggere di seguito per la procedura dettagliata su come compilare e distribuire un'app Unity per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="570e9-108">Read below for detailed steps on how to build and deploy a Unity app for HoloLens.</span></span> <span data-ttu-id="570e9-109">Per altre informazioni sulla compilazione per altre piattaforme, vedere [Pubblicazione di compilazioni](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span><span class="sxs-lookup"><span data-stu-id="570e9-109">Learn more about building for other platforms at [Publishing Builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a><span data-ttu-id="570e9-110">Compilazione e distribuzione di MRTK in visori HoloLens 1, HoloLens 2 e WMR (UWP)</span><span class="sxs-lookup"><span data-stu-id="570e9-110">Building and deploying MRTK to HoloLens 1, HoloLens 2 and WMR headsets (UWP)</span></span>

<span data-ttu-id="570e9-111">Le istruzioni su come compilare e distribuire **per HoloLens 1** **e HoloLens 2** (UWP) sono disponibili nella compilazione dell'applicazione [nel dispositivo](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="570e9-111">Instructions on how to build and deploy for **HoloLens 1** and **HoloLens 2** (UWP) can be found at [building your application to device](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span> <span data-ttu-id="570e9-112">Questi passaggi consentono anche di distribuire in **visori WMR**.</span><span class="sxs-lookup"><span data-stu-id="570e9-112">These steps also allow you to deploy to **WMR headsets**.</span></span>

<span data-ttu-id="570e9-113">**Suggerimento:** Quando si compila per HoloLens 1, HoloLens 2 o WMR, è consigliabile che le impostazioni di compilazione "Versione SDK di destinazione" e "Versione minima della piattaforma" siano simili all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="570e9-113">**Tip:** When building for HoloLens 1, HoloLens 2, or WMR, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![Finestra Di compilazione](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="570e9-115">Le altre impostazioni possono essere diverse,ad esempio Configurazione compilazione/Architettura/Tipo di compilazione e altre possono sempre essere modificate all'interno della Visual Studio soluzione.</span><span class="sxs-lookup"><span data-stu-id="570e9-115">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="570e9-116">Assicurarsi che l'elenco a discesa "Versione SDK di destinazione" includa l'opzione "10.0.18362.0". Se non è [presente,](https://developer.microsoft.com/windows/downloads/windows-10-sdk) è necessario installare l'Windows SDK più recente.</span><span class="sxs-lookup"><span data-stu-id="570e9-116">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="570e9-117">Unity 2019.3 e HoloLens</span><span class="sxs-lookup"><span data-stu-id="570e9-117">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="570e9-118">Se un'app HoloLens viene visualizzata come pannello 2D nel dispositivo, assicurarsi che le impostazioni seguenti siano state configurate in Unity 2019.3.x prima di distribuire l'app UWP:</span><span class="sxs-lookup"><span data-stu-id="570e9-118">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="570e9-119">Se si usa la versione XR legacy:</span><span class="sxs-lookup"><span data-stu-id="570e9-119">If using the legacy XR:</span></span>

1. <span data-ttu-id="570e9-120">Passare a Modifica impostazioni > progetto, Player</span><span class="sxs-lookup"><span data-stu-id="570e9-120">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="570e9-121">In XR Settings (Impostazioni **XR)** nella scheda UWP verifica che **Virtual Reality Supported** (Realtà virtuale supportata) sia abilitato e che **Windows Mixed Reality** SDK sia stato aggiunto agli SDK.</span><span class="sxs-lookup"><span data-stu-id="570e9-121">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="570e9-122">Compilare e distribuire in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="570e9-122">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="570e9-123">Se si usa XR-Plugin:</span><span class="sxs-lookup"><span data-stu-id="570e9-123">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="570e9-124">Seguire la procedura descritta in [Attività iniziali con XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span><span class="sxs-lookup"><span data-stu-id="570e9-124">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="570e9-125">Assicurarsi che il profilo di configurazione sia **DefaultXRSDKConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="570e9-125">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="570e9-126">Passare a **Edit > Project Settings (> Impostazioni progetto), XR-Plugin Management (Gestione progetti)** e verificare **Windows Mixed Reality** sia abilitato.</span><span class="sxs-lookup"><span data-stu-id="570e9-126">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="570e9-127">Compilare e distribuire in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="570e9-127">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="570e9-128">Se si usa Unity 2019.3.x, selezionare **ARM64** e non **ARM** come architettura di compilazione in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="570e9-128">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="570e9-129">Con le impostazioni predefinite di Unity in Unity 2019.3.x, un'app Unity non verrà distribuita in HoloLens se arm è selezionato a causa di un bug di Unity.</span><span class="sxs-lookup"><span data-stu-id="570e9-129">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="570e9-130">Questa operazione può essere rilevata nel file [di rilevamento dei problemi di Unity.](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)</span><span class="sxs-lookup"><span data-stu-id="570e9-130">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="570e9-131">Se è necessaria l'architettura ARM, passare a Edit **> Project Settings (Modifica** impostazioni progetto), Player (Lettore) e nel menu Other Settings **(Altre impostazioni)** **disabilitare Graphics Jobs (Processi grafici).**</span><span class="sxs-lookup"><span data-stu-id="570e9-131">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="570e9-132">La disabilitazione **dei processi di** grafica consentirà all'app di eseguire la distribuzione usando l'architettura di compilazione ARM per Unity 2019.3.x, ma è consigliabile usare ARM64.</span><span class="sxs-lookup"><span data-stu-id="570e9-132">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-standalone"></a><span data-ttu-id="570e9-133">Compilazione e distribuzione di MRTK (Standalone)</span><span class="sxs-lookup"><span data-stu-id="570e9-133">Building and deploying MRTK (Standalone)</span></span>

<span data-ttu-id="570e9-134">Le build autonome di MRTK possono essere usate nei visori VR WMR.</span><span class="sxs-lookup"><span data-stu-id="570e9-134">Standalone builds of MRTK can be used on WMR headsets.</span></span> <span data-ttu-id="570e9-135">Una build autonoma per un visore VR WMR richiede i passaggi aggiuntivi seguenti:</span><span class="sxs-lookup"><span data-stu-id="570e9-135">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="570e9-136">XR SDK di Unity supporta anche WMR nativo nelle build autonome, ma non richiede plugin WmR o WmR.</span><span class="sxs-lookup"><span data-stu-id="570e9-136">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="570e9-137">Questi passaggi sono necessari per la versione XR legacy di Unity.</span><span class="sxs-lookup"><span data-stu-id="570e9-137">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="570e9-138">Installare [Steam](https://store.steampowered.com/about/)</span><span class="sxs-lookup"><span data-stu-id="570e9-138">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="570e9-139">Installare [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="570e9-139">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="570e9-140">Installare il [plug-in WMR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="570e9-140">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="570e9-141">Come usare il plug-in WMR</span><span class="sxs-lookup"><span data-stu-id="570e9-141">How to use WMR plugin</span></span>

1. <span data-ttu-id="570e9-142">Aprire Steam e cercare il plug-Windows Mixed Reality plug-in</span><span class="sxs-lookup"><span data-stu-id="570e9-142">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="570e9-143">Prima di avviare il plug-in WMR, assicurarsi che Sia chiuso.</span><span class="sxs-lookup"><span data-stu-id="570e9-143">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="570e9-144">L'avvio del plug-in WMR avvia anche SteamVR.</span><span class="sxs-lookup"><span data-stu-id="570e9-144">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="570e9-145">Assicurarsi che il visore WMR sia collegato.</span><span class="sxs-lookup"><span data-stu-id="570e9-145">Make sure the WMR headset is plugged in.</span></span>

    ![Ricerca plug-in WMR](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="570e9-147">Selezionare **Avvia** per l'Windows Mixed Reality plug-in di SteamVR.</span><span class="sxs-lookup"><span data-stu-id="570e9-147">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![Plug-in WMR](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="570e9-149">Verrà avviato SteamVR e il plug-in WMR e verrà visualizzata una nuova finestra di stato di rilevamento per il visore WMR.</span><span class="sxs-lookup"><span data-stu-id="570e9-149">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="570e9-150">Per altre informazioni, vedere la documentazione [Windows Mixed Reality di Steam](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span><span class="sxs-lookup"><span data-stu-id="570e9-150">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![Aspetto di avvio WMR](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="570e9-152">In Unity, con la scena MRTK aperta, passare a **File > Build Settings**</span><span class="sxs-lookup"><span data-stu-id="570e9-152">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="570e9-153">Creare la scena</span><span class="sxs-lookup"><span data-stu-id="570e9-153">Build the scene</span></span>
    - <span data-ttu-id="570e9-154">Selezionare **Aggiungi scena aperta**</span><span class="sxs-lookup"><span data-stu-id="570e9-154">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="570e9-155">Assicurarsi che la piattaforma sia **autonoma**</span><span class="sxs-lookup"><span data-stu-id="570e9-155">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="570e9-156">Selezionare **Compila**</span><span class="sxs-lookup"><span data-stu-id="570e9-156">Select **Build**</span></span>
    - <span data-ttu-id="570e9-157">Scegliere il percorso per la nuova compilazione in Esplora file</span><span class="sxs-lookup"><span data-stu-id="570e9-157">Choose the location for the new build in File Explorer</span></span>

    ![Impostazioni di compilazione per la versione autonoma](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="570e9-159">Verrà creato un nuovo file eseguibile di Unity, per avviare l'app selezionare il file eseguibile unity in Esplora file.</span><span class="sxs-lookup"><span data-stu-id="570e9-159">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![Esplora file Unity](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="570e9-161">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="570e9-161">See also</span></span>

- [<span data-ttu-id="570e9-162">Supporto per Android e iOS</span><span class="sxs-lookup"><span data-stu-id="570e9-162">Android and iOS Support</span></span>](using-ar-foundation.md)
- [<span data-ttu-id="570e9-163">Supporto del movimento Leap</span><span class="sxs-lookup"><span data-stu-id="570e9-163">Leap Motion Support</span></span>](leap-motion-mrtk.md)
- [<span data-ttu-id="570e9-164">Rilevamento delle funzionalità della piattaforma</span><span class="sxs-lookup"><span data-stu-id="570e9-164">Detecting Platform Capabilities</span></span>](detecting-platform-capabilities.md)