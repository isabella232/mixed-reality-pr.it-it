---
title: BuildAndDeploy
description: Documentazione per compilare e distribuire app in vari dispositivi.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Visual Studio, Android, IOS
ms.openlocfilehash: a1ee13b083d980896dc5f6d531dc3602f10687825e7013b0b68051eab37b5734
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223957"
---
# <a name="building-and-deploying-mrtk"></a>Compilazione e distribuzione di MRTK

Per eseguire un'app nel dispositivo come app autonoma (per HoloLens, Android, iOS e così via), il passaggio di compilazione e distribuzione deve essere eseguito nel progetto unity. La compilazione e la distribuzione di un'app che usa MRTK è esattamente come la compilazione e la distribuzione di qualsiasi altra app Unity. Non sono disponibili istruzioni specifiche di MRTK. Leggere di seguito per informazioni dettagliate su come compilare e distribuire un'app Unity per HoloLens.  Per altre informazioni sulla compilazione per altre piattaforme, vedere [Pubblicazione di compilazioni](https://docs.unity3d.com/Manual/PublishingBuilds.html).

## <a name="building-and-deploying-mrtk-to-hololens-1-and-hololens-2-uwp"></a>Compilazione e distribuzione di MRTK HoloLens 1 e HoloLens 2 (UWP)

Le istruzioni su come compilare e distribuire per HoloLens 1 e HoloLens 2 (UWP) sono disponibili nella compilazione [dell'applicazione nel dispositivo](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).

**Suggerimento:** Quando si compila per WMR, HoloLens 1 o HoloLens 2, è consigliabile che le impostazioni di compilazione "Versione SDK di destinazione" e "Versione minima della piattaforma" siano simili all'immagine seguente:

![Finestra Di compilazione](../features/images/getting-started/BuildWindow.png)

Le altre impostazioni possono essere diverse,ad esempio Configurazione compilazione/Architettura/Tipo di compilazione e altre possono sempre essere modificate all'interno della Visual Studio soluzione.

Assicurarsi che l'elenco a discesa "Versione SDK di destinazione" includa l'opzione "10.0.18362.0". Se non è presente, è necessario installare [l'SDK di Windows](https://developer.microsoft.com/windows/downloads/windows-10-sdk) più recente.

### <a name="unity-20193-and-hololens"></a>Unity 2019.3 e HoloLens

Se un'app HoloLens viene visualizzata come pannello 2D nel dispositivo, assicurarsi che le impostazioni seguenti siano state configurate in Unity 2019.3.x prima di distribuire l'app UWP:

Se si usa la versione XR legacy:

1. Passare a Modifica > Project Impostazioni, Lettore
1. In **XR Impostazioni** nella scheda UWP verificare che Virtual **Reality Supported** (Realtà virtuale supportata) sia abilitato e che **Windows Mixed Reality** SDK sia stato aggiunto agli SDK.
1. Compilare e distribuire in Visual Studio

Se si usa XR-Plugin:

1. Seguire la procedura descritta in Attività iniziali [con XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)
1. Assicurarsi che il profilo di configurazione sia **DefaultXRSDKConfigurationProfile**
1. Passare a **Modifica > Project Impostazioni, XR-Plugin gestione** e assicurarsi **che** Windows Mixed Reality abilitata.
1. Compilare e distribuire in Visual Studio

>[!IMPORTANT]
> Se si usa Unity 2019.3.x, selezionare **ARM64** e non **ARM** come architettura di compilazione in Visual Studio. Con le impostazioni predefinite di Unity in Unity 2019.3.x, un'app Unity non verrà distribuita in un HoloLens se ARM è selezionato a causa di un bug di Unity. Questa operazione può essere rilevata nel rilevamento [dei problemi di Unity.](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)
>
> Se è necessaria l'architettura arm, passare a Modifica **> Project Impostazioni, Lettore** e nel **menu** Altro Impostazioni disabilitare **Processi grafici**. La **disabilitazione dei processi** di grafica consentirà all'app di eseguire la distribuzione usando l'architettura di compilazione ARM per Unity 2019.3.x, ma è consigliabile usare ARM64.

## <a name="building-and-deploying-mrtk-to-a-windows-mixed-reality-headset"></a>Compilazione e distribuzione di MRTK in un visore Windows Mixed Reality visore

Il visore Windows Mixed Reality (WMR) può essere usato per la piattaforma UWP (Universal Windows Platform) e le build autonome.  Una build autonoma per un visore WMR richiede i passaggi aggiuntivi seguenti:

> [!NOTE]
> L'SDK XR di Unity supporta anche WMR nativo nelle build autonome, ma non richiede il plug-in SteamVR o WMR. Questi passaggi sono necessari per la versione XR legacy di Unity.

1. Installare [Steam](https://store.steampowered.com/about/)
1. Installare [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)
1. Installare il [plug-in WMR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

### <a name="how-to-use-wmr-plugin"></a>Come usare il plug-in WMR

1. Aprire Steam e cercare il plug-in Windows Mixed Reality
    - Prima di avviare il plug-in WMR, assicurarsi che Sia chiuso. L'avvio del plug-in WMR avvia anche SteamVR.
    - Assicurarsi che il visore WMR sia collegato.

    ![Ricerca plug-in WMR](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. Selezionare **Avvia** per l'Windows Mixed Reality plug-in di SteamVR.

    ![Plug-in WMR](../features/images/build-deploy/WMR/WMRPlugin.png)

    - Verrà avviato SteamVR e il plug-in WMR e verrà visualizzata una nuova finestra di stato di rilevamento per il visore WMR.
    - Per altre informazioni, vedere la documentazione [Windows Mixed Reality di Steam](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)

        ![Aspetto di avvio WMR](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. In Unity, con la scena MRTK aperta, passare a **File > Build Impostazioni**

1. Creare la scena
    - Selezionare **Aggiungi scena aperta**
    - Assicurarsi che la piattaforma sia **autonoma**
    - Selezionare **Compila**
    - Scegliere il percorso per la nuova compilazione in Esplora file

    ![Build Impostazioni for Standalone (Build Impostazioni for Standalone)](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. Verrà creato un nuovo file eseguibile di Unity, per avviare l'app selezionare il file eseguibile unity in Esplora file.

    ![Esplora file Unity](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a>Vedi anche

- [Supporto per Android e iOS](../features/cross-platform/using-ar-foundation.md)
- [Supporto del movimento leap](../features/cross-platform/leap-motion-mrtk.md)
- [Rilevamento delle funzionalità della piattaforma](../features/cross-platform/detecting-platform-capabilities.md)
