---
title: BuildAndDeploy
description: Documentazione per la creazione e la distribuzione di app in diversi dispositivi.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Visual Studio, Android, IOS
ms.openlocfilehash: 43ce812a7da01ae99e4005856bade6ab291664b5
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782509"
---
# <a name="building-and-deploying-mrtk"></a><span data-ttu-id="f6e1e-104">Compilazione e distribuzione di MRTK</span><span class="sxs-lookup"><span data-stu-id="f6e1e-104">Building and deploying MRTK</span></span>

<span data-ttu-id="f6e1e-105">Per eseguire un'app nel dispositivo come app autonoma (per HoloLens, Android, iOS e così via), è necessario eseguire il passaggio di compilazione e distribuzione nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-105">To run an app on device as a standalone app (for HoloLens, Android, iOS, etc.), the build and deploy step needs to be executed in the unity project.</span></span> <span data-ttu-id="f6e1e-106">La compilazione e la distribuzione di un'app che usa MRTK è proprio come la compilazione e la distribuzione di qualsiasi altra app Unity.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-106">Building and deploying an app that uses MRTK is just like building and deploying any other Unity app.</span></span> <span data-ttu-id="f6e1e-107">Non sono disponibili istruzioni specifiche per MRTK.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-107">There are no MRTK-specific instructions.</span></span> <span data-ttu-id="f6e1e-108">Leggere di seguito per i passaggi dettagliati su come compilare e distribuire un'app Unity per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-108">Read below for detailed steps on how to build and deploy a Unity app for HoloLens.</span></span>  <span data-ttu-id="f6e1e-109">Altre informazioni sulla compilazione per altre piattaforme in [Build di pubblicazione](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span><span class="sxs-lookup"><span data-stu-id="f6e1e-109">Learn more about building for other platforms at [Publishing Builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-and-hololens-2-uwp"></a><span data-ttu-id="f6e1e-110">Compilazione e distribuzione di MRTK in HoloLens 1 e HoloLens 2 (UWP)</span><span class="sxs-lookup"><span data-stu-id="f6e1e-110">Building and deploying MRTK to HoloLens 1 and HoloLens 2 (UWP)</span></span>

<span data-ttu-id="f6e1e-111">Le istruzioni su come compilare e distribuire per HoloLens 1 e HoloLens 2 (UWP) sono disponibili nella pagina relativa alla [creazione dell'applicazione nel dispositivo](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="f6e1e-111">Instructions on how to build and deploy for HoloLens 1 and HoloLens 2 (UWP) can be found at [building your application to device](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span>

<span data-ttu-id="f6e1e-112">**Suggerimento:** Quando si compila per WMR, HoloLens 1 o HoloLens 2, è consigliabile che le impostazioni di compilazione "versione SDK di destinazione" e "versione minima piattaforma" abbiano un aspetto analogo a quello illustrato nell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="f6e1e-112">**Tip:** When building for WMR, HoloLens 1, or HoloLens 2, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![Finestra di compilazione](../features/Images/getting_started/BuildWindow.png)

<span data-ttu-id="f6e1e-114">Le altre impostazioni possono essere diverse, ad esempio configurazione di compilazione/architettura/tipo di compilazione e altre possono sempre essere modificate all'interno della soluzione di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-114">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="f6e1e-115">Verificare che l'elenco a discesa "versione SDK di destinazione" includa l'opzione "10.0.18362.0". se non è presente, è necessario installare [la Windows SDK più recente](https://developer.microsoft.com/windows/downloads/windows-10-sdk) .</span><span class="sxs-lookup"><span data-stu-id="f6e1e-115">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="f6e1e-116">Unity 2019,3 e HoloLens</span><span class="sxs-lookup"><span data-stu-id="f6e1e-116">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="f6e1e-117">Se un'app HoloLens viene visualizzata come pannello 2D nel dispositivo, verificare che siano state configurate le impostazioni seguenti in Unity 2019.3. x prima di distribuire l'app UWP:</span><span class="sxs-lookup"><span data-stu-id="f6e1e-117">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="f6e1e-118">Se si usa la versione precedente di XR:</span><span class="sxs-lookup"><span data-stu-id="f6e1e-118">If using the legacy XR:</span></span>

1. <span data-ttu-id="f6e1e-119">Passare a modifica > impostazioni progetto, lettore</span><span class="sxs-lookup"><span data-stu-id="f6e1e-119">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="f6e1e-120">In **Impostazioni XR** nella scheda UWP verificare che **Virtual Reality supported** sia abilitato e che **Windows Mixed Reality** SDK sia stato aggiunto agli SDK.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-120">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="f6e1e-121">Compilazione e distribuzione in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f6e1e-121">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="f6e1e-122">Se si usa il plug-in XR:</span><span class="sxs-lookup"><span data-stu-id="f6e1e-122">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="f6e1e-123">Seguire i passaggi disponibili in [Introduzione con XRSDK](../configuration/GettingStartedWithMRTKAndXRSDK.md)</span><span class="sxs-lookup"><span data-stu-id="f6e1e-123">Follow the steps found in [Getting Started with XRSDK](../configuration/GettingStartedWithMRTKAndXRSDK.md)</span></span>
1. <span data-ttu-id="f6e1e-124">Verificare che il profilo di configurazione sia **DefaultXRSDKConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="f6e1e-124">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="f6e1e-125">Passare a **modifica > impostazioni progetto, gestione XR-Plugin** e assicurarsi che la **realtà mista di Windows** sia abilitata.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-125">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="f6e1e-126">Compilazione e distribuzione in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f6e1e-126">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="f6e1e-127">Se si usa Unity 2019.3. x, selezionare **arm64** e non **ARM** come architettura di compilazione in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-127">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="f6e1e-128">Con le impostazioni di Unity predefinite in Unity 2019.3. x, un'app Unity non verrà distribuita in un HoloLens se ARM è selezionato a causa di un bug di Unity.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-128">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="f6e1e-129">Questa operazione può essere rilevata nello strumento [di rilevamento dei problemi di Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="f6e1e-129">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="f6e1e-130">Se è richiesta l'architettura ARM, passare a **modifica > impostazioni progetto, lettore** e nel menu **altre impostazioni** disabilitare i **processi grafici**.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-130">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="f6e1e-131">La disabilitazione dei **processi grafici** consentirà all'app di eseguire la distribuzione usando l'architettura di compilazione ARM per Unity 2019.3. x, ma è consigliabile arm64.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-131">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-to-a-windows-mixed-reality-headset"></a><span data-ttu-id="f6e1e-132">Compilazione e distribuzione di MRTK in un auricolare di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="f6e1e-132">Building and deploying MRTK to a Windows Mixed Reality Headset</span></span>

<span data-ttu-id="f6e1e-133">È possibile usare l'auricolare della realtà mista di Windows (WMR) per piattaforma UWP (Universal Windows Platform) (UWP) e le compilazioni autonome.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-133">The Windows Mixed Reality (WMR) headset can be used for Universal Windows Platform (UWP) and Standalone builds.</span></span>  <span data-ttu-id="f6e1e-134">Una compilazione autonoma per un auricolare WMR richiede i seguenti passaggi aggiuntivi:</span><span class="sxs-lookup"><span data-stu-id="f6e1e-134">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="f6e1e-135">XR SDK di Unity supporta anche WMR nativi nelle build autonome, ma non richiede il plug-in SteamVR o WMR.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-135">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="f6e1e-136">Questi passaggi sono necessari per la versione precedente di XR di Unity.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-136">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="f6e1e-137">Installare [Steam](https://store.steampowered.com/about/)</span><span class="sxs-lookup"><span data-stu-id="f6e1e-137">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="f6e1e-138">Installare [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="f6e1e-138">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="f6e1e-139">Installare il [plug](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) -in WMR</span><span class="sxs-lookup"><span data-stu-id="f6e1e-139">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="f6e1e-140">Come usare il plug-in WMR</span><span class="sxs-lookup"><span data-stu-id="f6e1e-140">How to use WMR plugin</span></span>

1. <span data-ttu-id="f6e1e-141">Apri Steam e cerca il plug-in per la realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="f6e1e-141">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="f6e1e-142">Assicurarsi che SteamVR sia chiuso prima di avviare il plug-in WMR.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-142">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="f6e1e-143">L'avvio del plug-in WMR avvia anche SteamVR.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-143">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="f6e1e-144">Verificare che l'auricolare WMR sia collegato.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-144">Make sure the WMR headset is plugged in.</span></span>

    ![Ricerca plug-in WMR](../features/Images/BuildDeploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="f6e1e-146">Selezionare **Launch** per la realtà mista di Windows per il plug-in SteamVR.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-146">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![Plug-in WMR](../features/Images/BuildDeploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="f6e1e-148">Verranno avviati SteamVR e il plug-in WMR e verrà visualizzata una nuova finestra di stato di rilevamento per l'auricolare WMR.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-148">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="f6e1e-149">Per ulteriori informazioni, visitare la [documentazione di Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span><span class="sxs-lookup"><span data-stu-id="f6e1e-149">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![Aspetto di avvio di WMR](../features/Images/BuildDeploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="f6e1e-151">In Unity, con la scena MRTK aperta, passare a **File > impostazioni di compilazione**</span><span class="sxs-lookup"><span data-stu-id="f6e1e-151">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="f6e1e-152">Creazione della scena</span><span class="sxs-lookup"><span data-stu-id="f6e1e-152">Build the scene</span></span>
    - <span data-ttu-id="f6e1e-153">Selezionare **Aggiungi scena aperta**</span><span class="sxs-lookup"><span data-stu-id="f6e1e-153">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="f6e1e-154">Verificare che la piattaforma sia **autonoma**</span><span class="sxs-lookup"><span data-stu-id="f6e1e-154">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="f6e1e-155">Selezione **compilazione**</span><span class="sxs-lookup"><span data-stu-id="f6e1e-155">Select **Build**</span></span>
    - <span data-ttu-id="f6e1e-156">Scegliere il percorso per la nuova compilazione in Esplora file</span><span class="sxs-lookup"><span data-stu-id="f6e1e-156">Choose the location for the new build in File Explorer</span></span>

    ![Impostazioni di compilazione per autonome](../features/Images/BuildDeploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="f6e1e-158">Verrà creato un nuovo file eseguibile Unity per avviare l'app. Selezionare il file eseguibile Unity in Esplora file.</span><span class="sxs-lookup"><span data-stu-id="f6e1e-158">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![Unity Esplora file](../features/Images/BuildDeploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="f6e1e-160">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="f6e1e-160">See also</span></span>

- [<span data-ttu-id="f6e1e-161">Supporto per Android e iOS</span><span class="sxs-lookup"><span data-stu-id="f6e1e-161">Android and iOS Support</span></span>](../features/CrossPlatform/UsingARFoundation.md)
- [<span data-ttu-id="f6e1e-162">Supporto del movimento Leap</span><span class="sxs-lookup"><span data-stu-id="f6e1e-162">Leap Motion Support</span></span>](../features/CrossPlatform/LeapMotionMRTK.md)
- [<span data-ttu-id="f6e1e-163">Rilevamento delle funzionalità della piattaforma</span><span class="sxs-lookup"><span data-stu-id="f6e1e-163">Detecting Platform Capabilities</span></span>](../features/DetectingPlatformCapabilities.md)
