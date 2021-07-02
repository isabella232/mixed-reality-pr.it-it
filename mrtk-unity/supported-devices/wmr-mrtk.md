---
title: Distribuzione in visori HoloLens e WMR
description: Documentazione per compilare e distribuire app in vari dispositivi.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Visual Studio
ms.openlocfilehash: 137e1b699e9a0cda1e8a454a6c3219b581fa71b4
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176375"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a><span data-ttu-id="d2559-104">Distribuzione in visori HoloLens e WMR</span><span class="sxs-lookup"><span data-stu-id="d2559-104">Deploying to HoloLens and WMR headsets</span></span>

<span data-ttu-id="d2559-105">Esistono due modi per distribuire le applicazioni compilate con MRTK nel dispositivo Windows, univeral Windows Platform (UWP) e la piattaforma autonoma.</span><span class="sxs-lookup"><span data-stu-id="d2559-105">There are two ways to deploy applications built with MRTK to your windows device, the Univeral Windows Platform (UWP) and the Standalone Platform.</span></span> <span data-ttu-id="d2559-106">Le applicazioni create per HoloLens 1 o HoloLens 2 devono avere come destinazione la piattaforma UWP, mentre le applicazioni create per i visori WMR possono avere come destinazione UWP o Standalone.</span><span class="sxs-lookup"><span data-stu-id="d2559-106">Applications built for HoloLens 1 or HoloLens 2 must target UWP, while applications built for WMR headsets may target either UWP or Standalone.</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a><span data-ttu-id="d2559-107">Compilazione e distribuzione di MRTK HoloLens 1, HoloLens 2 e WMR visori (UWP)</span><span class="sxs-lookup"><span data-stu-id="d2559-107">Building and deploying MRTK to HoloLens 1, HoloLens 2 and WMR headsets (UWP)</span></span>

<span data-ttu-id="d2559-108">Le istruzioni su come compilare e distribuire per **HoloLens 1** **e HoloLens 2** (UWP) sono disponibili nella compilazione dell'applicazione [nel dispositivo](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="d2559-108">Instructions on how to build and deploy for **HoloLens 1** and **HoloLens 2** (UWP) can be found at [building your application to device](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span> <span data-ttu-id="d2559-109">Questi passaggi consentono anche di distribuire in **visori WMR**.</span><span class="sxs-lookup"><span data-stu-id="d2559-109">These steps also allow you to deploy to **WMR headsets**.</span></span>

> [!NOTE]
> <span data-ttu-id="d2559-110">Quando si distribuisce l'applicazione nel dispositivo Visual Studio, è necessario configurare Visual Studio in modo leggermente diverso a seconda del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d2559-110">When deploying your application to your device in Visual Studio, you need to configure Visual Studio slightly differently depending on the device.</span></span> <span data-ttu-id="d2559-111">Le configurazioni sono le seguenti</span><span class="sxs-lookup"><span data-stu-id="d2559-111">The configurations are as follows</span></span>
>
>| <span data-ttu-id="d2559-112">Piattaforma</span><span class="sxs-lookup"><span data-stu-id="d2559-112">Platform</span></span> | <span data-ttu-id="d2559-113">Configurazione</span><span class="sxs-lookup"><span data-stu-id="d2559-113">Configuration</span></span> | <span data-ttu-id="d2559-114">Architecture</span><span class="sxs-lookup"><span data-stu-id="d2559-114">Architecture</span></span> | <span data-ttu-id="d2559-115">Destinazione</span><span class="sxs-lookup"><span data-stu-id="d2559-115">Target</span></span> |
|---|---|---|---|
| <span data-ttu-id="d2559-116">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d2559-116">HoloLens 2</span></span> | <span data-ttu-id="d2559-117">Versione o master</span><span class="sxs-lookup"><span data-stu-id="d2559-117">Release or Master</span></span> | <span data-ttu-id="d2559-118">ARM64</span><span class="sxs-lookup"><span data-stu-id="d2559-118">ARM64</span></span> | <span data-ttu-id="d2559-119">Dispositivo</span><span class="sxs-lookup"><span data-stu-id="d2559-119">Device</span></span> |
| <span data-ttu-id="d2559-120">HoloLens 1</span><span class="sxs-lookup"><span data-stu-id="d2559-120">HoloLens 1</span></span> | <span data-ttu-id="d2559-121">Versione o master</span><span class="sxs-lookup"><span data-stu-id="d2559-121">Release or Master</span></span> | <span data-ttu-id="d2559-122">x86</span><span class="sxs-lookup"><span data-stu-id="d2559-122">x86</span></span> | <span data-ttu-id="d2559-123">Dispositivo</span><span class="sxs-lookup"><span data-stu-id="d2559-123">Device</span></span> |
| <span data-ttu-id="d2559-124">Visori WMR</span><span class="sxs-lookup"><span data-stu-id="d2559-124">WMR Headsets</span></span> | <span data-ttu-id="d2559-125">Versione o master</span><span class="sxs-lookup"><span data-stu-id="d2559-125">Release or Master</span></span> | <span data-ttu-id="d2559-126">x64</span><span class="sxs-lookup"><span data-stu-id="d2559-126">x64</span></span> | <span data-ttu-id="d2559-127">Computer locale</span><span class="sxs-lookup"><span data-stu-id="d2559-127">Local Machine</span></span> |

<span data-ttu-id="d2559-128">**Suggerimento:** Quando si compila per HoloLens 1, HoloLens 2 o WMR, è consigliabile che le impostazioni di compilazione "Versione SDK di destinazione" e "Versione minima della piattaforma" siano simili all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="d2559-128">**Tip:** When building for HoloLens 1, HoloLens 2, or WMR, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![Finestra Di compilazione](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="d2559-130">Le altre impostazioni possono essere diverse,ad esempio Configurazione compilazione/Architettura/Tipo di compilazione e altre possono sempre essere modificate all'interno della Visual Studio soluzione.</span><span class="sxs-lookup"><span data-stu-id="d2559-130">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="d2559-131">Assicurarsi che l'elenco a discesa "Versione SDK di destinazione" includa l'opzione "10.0.18362.0". Se non è presente, è necessario installare [l'SDK di Windows](https://developer.microsoft.com/windows/downloads/windows-10-sdk) più recente.</span><span class="sxs-lookup"><span data-stu-id="d2559-131">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20192020-and-hololens"></a><span data-ttu-id="d2559-132">Unity 2019/2020 e HoloLens</span><span class="sxs-lookup"><span data-stu-id="d2559-132">Unity 2019/2020 and HoloLens</span></span>

<span data-ttu-id="d2559-133">Se un HoloLens app viene visualizzato come pannello 2D nel dispositivo, assicurarsi che le impostazioni seguenti siano state configurate in Unity prima di distribuire l'app UWP:</span><span class="sxs-lookup"><span data-stu-id="d2559-133">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity before deploying your UWP app:</span></span>

<span data-ttu-id="d2559-134">Se si usa il supporto XR incorporato legacy (solo Unity 2019):</span><span class="sxs-lookup"><span data-stu-id="d2559-134">If using the legacy built-in XR support (Unity 2019 only):</span></span>

1. <span data-ttu-id="d2559-135">Passare a Modifica > Project Impostazioni, Lettore</span><span class="sxs-lookup"><span data-stu-id="d2559-135">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="d2559-136">In **XR Impostazioni** nella scheda UWP verificare che Virtual **Reality Supported** (Realtà virtuale supportata) sia abilitato e che **Windows Mixed Reality** SDK sia stato aggiunto agli SDK.</span><span class="sxs-lookup"><span data-stu-id="d2559-136">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="d2559-137">Compilare e distribuire in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d2559-137">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="d2559-138">Se si usano i plug-in OpenXR o Windows XR:</span><span class="sxs-lookup"><span data-stu-id="d2559-138">If using the OpenXR or Windows XR plugins:</span></span>

1. <span data-ttu-id="d2559-139">Seguire la procedura descritta in Attività iniziali [con XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span><span class="sxs-lookup"><span data-stu-id="d2559-139">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="d2559-140">Assicurarsi che il profilo di configurazione sia **DefaultXRSDKConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="d2559-140">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="d2559-141">Passare a **Modifica > Project Impostazioni, XR-Plugin gestione** e assicurarsi **che** Windows Mixed Reality abilitata.</span><span class="sxs-lookup"><span data-stu-id="d2559-141">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="d2559-142">Compilare e distribuire in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d2559-142">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="d2559-143">Se si usa Unity 2019.3.x, selezionare **ARM64** e non **ARM** come architettura di compilazione in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d2559-143">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="d2559-144">Con le impostazioni predefinite di Unity in Unity 2019.3.x, un'app Unity non verrà distribuita in un HoloLens se ARM è selezionato a causa di un bug di Unity.</span><span class="sxs-lookup"><span data-stu-id="d2559-144">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span>
>
> <span data-ttu-id="d2559-145">Se è necessaria l'architettura arm, passare a Modifica **> Project Impostazioni, Lettore** e nel **menu** Altro Impostazioni disabilitare **Processi grafici**.</span><span class="sxs-lookup"><span data-stu-id="d2559-145">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="d2559-146">La **disabilitazione dei processi** di grafica consentirà all'app di eseguire la distribuzione usando l'architettura di compilazione ARM per Unity 2019.3.x, ma è consigliabile usare ARM64.</span><span class="sxs-lookup"><span data-stu-id="d2559-146">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>
>
> <span data-ttu-id="d2559-147">Questo problema è stato risolto in Unity 2019.4 e Unity 2020.3.</span><span class="sxs-lookup"><span data-stu-id="d2559-147">This issue was fixed in Unity 2019.4 and Unity 2020.3.</span></span>

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a><span data-ttu-id="d2559-148">Compilazione e distribuzione di MRTK in visori WMR (autonomi)</span><span class="sxs-lookup"><span data-stu-id="d2559-148">Building and deploying MRTK to WMR Headsets (Standalone)</span></span>

<span data-ttu-id="d2559-149">Le build autonome di MRTK possono essere usate nei visori WMR.</span><span class="sxs-lookup"><span data-stu-id="d2559-149">Standalone builds of MRTK can be used on WMR headsets.</span></span> <span data-ttu-id="d2559-150">Una build autonoma per un visore WMR richiede i passaggi aggiuntivi seguenti:</span><span class="sxs-lookup"><span data-stu-id="d2559-150">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="d2559-151">L'SDK XR di Unity supporta anche WMR nativo nelle build autonome, ma non richiede il plug-in SteamVR o WMR.</span><span class="sxs-lookup"><span data-stu-id="d2559-151">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="d2559-152">Questi passaggi sono necessari per la versione XR legacy di Unity.</span><span class="sxs-lookup"><span data-stu-id="d2559-152">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="d2559-153">Installare [Steam](https://store.steampowered.com/about/)</span><span class="sxs-lookup"><span data-stu-id="d2559-153">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="d2559-154">Installare [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="d2559-154">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="d2559-155">Installare il [plug-in WMR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="d2559-155">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="d2559-156">Come usare il plug-in WMR</span><span class="sxs-lookup"><span data-stu-id="d2559-156">How to use WMR plugin</span></span>

1. <span data-ttu-id="d2559-157">Aprire Steam e cercare il plug-in Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d2559-157">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="d2559-158">Prima di avviare il plug-in WMR, assicurarsi che Sia chiuso.</span><span class="sxs-lookup"><span data-stu-id="d2559-158">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="d2559-159">L'avvio del plug-in WMR avvia anche SteamVR.</span><span class="sxs-lookup"><span data-stu-id="d2559-159">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="d2559-160">Assicurarsi che il visore WMR sia collegato.</span><span class="sxs-lookup"><span data-stu-id="d2559-160">Make sure the WMR headset is plugged in.</span></span>

    ![Ricerca plug-in WMR](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="d2559-162">Selezionare **Avvia** per l'Windows Mixed Reality plug-in di SteamVR.</span><span class="sxs-lookup"><span data-stu-id="d2559-162">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![Plug-in WMR](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="d2559-164">Verrà avviato SteamVR e il plug-in WMR e verrà visualizzata una nuova finestra di stato di rilevamento per il visore WMR.</span><span class="sxs-lookup"><span data-stu-id="d2559-164">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="d2559-165">Per altre informazioni, vedere la documentazione [Windows Mixed Reality di Steam](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span><span class="sxs-lookup"><span data-stu-id="d2559-165">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![Aspetto di avvio WMR](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="d2559-167">In Unity, con la scena MRTK aperta, passare a **File > Build Impostazioni**</span><span class="sxs-lookup"><span data-stu-id="d2559-167">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="d2559-168">Creare la scena</span><span class="sxs-lookup"><span data-stu-id="d2559-168">Build the scene</span></span>
    - <span data-ttu-id="d2559-169">Selezionare **Aggiungi scena aperta**</span><span class="sxs-lookup"><span data-stu-id="d2559-169">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="d2559-170">Assicurarsi che la piattaforma sia **autonoma**</span><span class="sxs-lookup"><span data-stu-id="d2559-170">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="d2559-171">Selezionare **Compila**</span><span class="sxs-lookup"><span data-stu-id="d2559-171">Select **Build**</span></span>
    - <span data-ttu-id="d2559-172">Scegliere il percorso per la nuova compilazione in Esplora file</span><span class="sxs-lookup"><span data-stu-id="d2559-172">Choose the location for the new build in File Explorer</span></span>

    ![Build Impostazioni for Standalone (Build Impostazioni for Standalone)](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="d2559-174">Verrà creato un nuovo file eseguibile di Unity, per avviare l'app selezionare il file eseguibile unity in Esplora file.</span><span class="sxs-lookup"><span data-stu-id="d2559-174">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![Esplora file Unity](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="d2559-176">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d2559-176">See also</span></span>

- [<span data-ttu-id="d2559-177">Supporto per Android e iOS</span><span class="sxs-lookup"><span data-stu-id="d2559-177">Android and iOS Support</span></span>](using-ar-foundation.md)
- [<span data-ttu-id="d2559-178">Supporto del movimento leap</span><span class="sxs-lookup"><span data-stu-id="d2559-178">Leap Motion Support</span></span>](leap-motion-mrtk.md)
- [<span data-ttu-id="d2559-179">Rilevamento delle funzionalità della piattaforma</span><span class="sxs-lookup"><span data-stu-id="d2559-179">Detecting Platform Capabilities</span></span>](detecting-platform-capabilities.md)
