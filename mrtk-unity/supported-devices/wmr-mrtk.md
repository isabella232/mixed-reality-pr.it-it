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
# <a name="building-and-deploying-mrtk-uwp"></a>Compilazione e distribuzione di MRTK (UWP)

Per eseguire un'app nel dispositivo come app autonoma (per HoloLens, Android, iOS e così via), il passaggio di compilazione e distribuzione deve essere eseguito nel progetto unity. La compilazione e la distribuzione di un'app che usa MRTK è esattamente come la compilazione e la distribuzione di qualsiasi altra app Unity. Non sono disponibili istruzioni specifiche di MRTK. Leggere di seguito per la procedura dettagliata su come compilare e distribuire un'app Unity per HoloLens. Per altre informazioni sulla compilazione per altre piattaforme, vedere [Pubblicazione di compilazioni](https://docs.unity3d.com/Manual/PublishingBuilds.html).

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a>Compilazione e distribuzione di MRTK in visori HoloLens 1, HoloLens 2 e WMR (UWP)

Le istruzioni su come compilare e distribuire **per HoloLens 1** **e HoloLens 2** (UWP) sono disponibili nella compilazione dell'applicazione [nel dispositivo](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device). Questi passaggi consentono anche di distribuire in **visori WMR**.

**Suggerimento:** Quando si compila per HoloLens 1, HoloLens 2 o WMR, è consigliabile che le impostazioni di compilazione "Versione SDK di destinazione" e "Versione minima della piattaforma" siano simili all'immagine seguente:

![Finestra Di compilazione](../features/images/getting-started/BuildWindow.png)

Le altre impostazioni possono essere diverse,ad esempio Configurazione compilazione/Architettura/Tipo di compilazione e altre possono sempre essere modificate all'interno della Visual Studio soluzione.

Assicurarsi che l'elenco a discesa "Versione SDK di destinazione" includa l'opzione "10.0.18362.0". Se non è [presente,](https://developer.microsoft.com/windows/downloads/windows-10-sdk) è necessario installare l'Windows SDK più recente.

### <a name="unity-20193-and-hololens"></a>Unity 2019.3 e HoloLens

Se un'app HoloLens viene visualizzata come pannello 2D nel dispositivo, assicurarsi che le impostazioni seguenti siano state configurate in Unity 2019.3.x prima di distribuire l'app UWP:

Se si usa la versione XR legacy:

1. Passare a Modifica impostazioni > progetto, Player
1. In XR Settings (Impostazioni **XR)** nella scheda UWP verifica che **Virtual Reality Supported** (Realtà virtuale supportata) sia abilitato e che **Windows Mixed Reality** SDK sia stato aggiunto agli SDK.
1. Compilare e distribuire in Visual Studio

Se si usa XR-Plugin:

1. Seguire la procedura descritta in [Attività iniziali con XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)
1. Assicurarsi che il profilo di configurazione sia **DefaultXRSDKConfigurationProfile**
1. Passare a **Edit > Project Settings (> Impostazioni progetto), XR-Plugin Management (Gestione progetti)** e verificare **Windows Mixed Reality** sia abilitato.
1. Compilare e distribuire in Visual Studio

>[!IMPORTANT]
> Se si usa Unity 2019.3.x, selezionare **ARM64** e non **ARM** come architettura di compilazione in Visual Studio. Con le impostazioni predefinite di Unity in Unity 2019.3.x, un'app Unity non verrà distribuita in HoloLens se arm è selezionato a causa di un bug di Unity. Questa operazione può essere rilevata nel file [di rilevamento dei problemi di Unity.](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)
>
> Se è necessaria l'architettura ARM, passare a Edit **> Project Settings (Modifica** impostazioni progetto), Player (Lettore) e nel menu Other Settings **(Altre impostazioni)** **disabilitare Graphics Jobs (Processi grafici).** La disabilitazione **dei processi di** grafica consentirà all'app di eseguire la distribuzione usando l'architettura di compilazione ARM per Unity 2019.3.x, ma è consigliabile usare ARM64.

## <a name="building-and-deploying-mrtk-standalone"></a>Compilazione e distribuzione di MRTK (Standalone)

Le build autonome di MRTK possono essere usate nei visori VR WMR. Una build autonoma per un visore VR WMR richiede i passaggi aggiuntivi seguenti:

> [!NOTE]
> XR SDK di Unity supporta anche WMR nativo nelle build autonome, ma non richiede plugin WmR o WmR. Questi passaggi sono necessari per la versione XR legacy di Unity.

1. Installare [Steam](https://store.steampowered.com/about/)
1. Installare [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)
1. Installare il [plug-in WMR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

### <a name="how-to-use-wmr-plugin"></a>Come usare il plug-in WMR

1. Aprire Steam e cercare il plug-Windows Mixed Reality plug-in
    - Prima di avviare il plug-in WMR, assicurarsi che Sia chiuso. L'avvio del plug-in WMR avvia anche SteamVR.
    - Assicurarsi che il visore WMR sia collegato.

    ![Ricerca plug-in WMR](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. Selezionare **Avvia** per l'Windows Mixed Reality plug-in di SteamVR.

    ![Plug-in WMR](../features/images/build-deploy/WMR/WMRPlugin.png)

    - Verrà avviato SteamVR e il plug-in WMR e verrà visualizzata una nuova finestra di stato di rilevamento per il visore WMR.
    - Per altre informazioni, vedere la documentazione [Windows Mixed Reality di Steam](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)

        ![Aspetto di avvio WMR](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. In Unity, con la scena MRTK aperta, passare a **File > Build Settings**

1. Creare la scena
    - Selezionare **Aggiungi scena aperta**
    - Assicurarsi che la piattaforma sia **autonoma**
    - Selezionare **Compila**
    - Scegliere il percorso per la nuova compilazione in Esplora file

    ![Impostazioni di compilazione per la versione autonoma](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. Verrà creato un nuovo file eseguibile di Unity, per avviare l'app selezionare il file eseguibile unity in Esplora file.

    ![Esplora file Unity](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a>Vedi anche

- [Supporto per Android e iOS](using-ar-foundation.md)
- [Supporto del movimento Leap](leap-motion-mrtk.md)
- [Rilevamento delle funzionalità della piattaforma](detecting-platform-capabilities.md)