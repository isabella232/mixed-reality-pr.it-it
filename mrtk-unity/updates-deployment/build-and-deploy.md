---
title: BuildAndDeploy
description: Documentazione per la creazione e la distribuzione di app in diversi dispositivi.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Visual Studio, Android, IOS
ms.openlocfilehash: f86e70fb80e854111c62391d706a8d33fcd67c90
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782877"
---
# <a name="building-and-deploying-mrtk"></a>Compilazione e distribuzione di MRTK

Per eseguire un'app nel dispositivo come app autonoma (per HoloLens, Android, iOS e così via), è necessario eseguire il passaggio di compilazione e distribuzione nel progetto Unity. La compilazione e la distribuzione di un'app che usa MRTK è proprio come la compilazione e la distribuzione di qualsiasi altra app Unity. Non sono disponibili istruzioni specifiche per MRTK. Leggere di seguito per i passaggi dettagliati su come compilare e distribuire un'app Unity per HoloLens.  Altre informazioni sulla compilazione per altre piattaforme in [Build di pubblicazione](https://docs.unity3d.com/Manual/PublishingBuilds.html).

## <a name="building-and-deploying-mrtk-to-hololens-1-and-hololens-2-uwp"></a>Compilazione e distribuzione di MRTK in HoloLens 1 e HoloLens 2 (UWP)

Le istruzioni su come compilare e distribuire per HoloLens 1 e HoloLens 2 (UWP) sono disponibili nella pagina relativa alla [creazione dell'applicazione nel dispositivo](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).

**Suggerimento:** Quando si compila per WMR, HoloLens 1 o HoloLens 2, è consigliabile che le impostazioni di compilazione "versione SDK di destinazione" e "versione minima piattaforma" abbiano un aspetto analogo a quello illustrato nell'immagine seguente:

![Finestra di compilazione](../features/images/getting-started/BuildWindow.png)

Le altre impostazioni possono essere diverse, ad esempio configurazione di compilazione/architettura/tipo di compilazione e altre possono sempre essere modificate all'interno della soluzione di Visual Studio.

Verificare che l'elenco a discesa "versione SDK di destinazione" includa l'opzione "10.0.18362.0". se non è presente, è necessario installare [la Windows SDK più recente](https://developer.microsoft.com/windows/downloads/windows-10-sdk) .

### <a name="unity-20193-and-hololens"></a>Unity 2019,3 e HoloLens

Se un'app HoloLens viene visualizzata come pannello 2D nel dispositivo, verificare che siano state configurate le impostazioni seguenti in Unity 2019.3. x prima di distribuire l'app UWP:

Se si usa la versione precedente di XR:

1. Passare a modifica > impostazioni progetto, lettore
1. In **Impostazioni XR** nella scheda UWP verificare che **Virtual Reality supported** sia abilitato e che **Windows Mixed Reality** SDK sia stato aggiunto agli SDK.
1. Compilazione e distribuzione in Visual Studio

Se si usa il plug-in XR:

1. Seguire i passaggi disponibili in [Introduzione con XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)
1. Verificare che il profilo di configurazione sia **DefaultXRSDKConfigurationProfile**
1. Passare a **modifica > impostazioni progetto, gestione XR-Plugin** e assicurarsi che la **realtà mista di Windows** sia abilitata.
1. Compilazione e distribuzione in Visual Studio

>[!IMPORTANT]
> Se si usa Unity 2019.3. x, selezionare **arm64** e non **ARM** come architettura di compilazione in Visual Studio. Con le impostazioni di Unity predefinite in Unity 2019.3. x, un'app Unity non verrà distribuita in un HoloLens se ARM è selezionato a causa di un bug di Unity. Questa operazione può essere rilevata nello strumento [di rilevamento dei problemi di Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).
>
> Se è richiesta l'architettura ARM, passare a **modifica > impostazioni progetto, lettore** e nel menu **altre impostazioni** disabilitare i **processi grafici**. La disabilitazione dei **processi grafici** consentirà all'app di eseguire la distribuzione usando l'architettura di compilazione ARM per Unity 2019.3. x, ma è consigliabile arm64.

## <a name="building-and-deploying-mrtk-to-a-windows-mixed-reality-headset"></a>Compilazione e distribuzione di MRTK in un auricolare di realtà mista di Windows

È possibile usare l'auricolare della realtà mista di Windows (WMR) per piattaforma UWP (Universal Windows Platform) (UWP) e le compilazioni autonome.  Una compilazione autonoma per un auricolare WMR richiede i seguenti passaggi aggiuntivi:

> [!NOTE]
> XR SDK di Unity supporta anche WMR nativi nelle build autonome, ma non richiede il plug-in SteamVR o WMR. Questi passaggi sono necessari per la versione precedente di XR di Unity.

1. Installare [Steam](https://store.steampowered.com/about/)
1. Installare [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)
1. Installare il [plug](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) -in WMR

### <a name="how-to-use-wmr-plugin"></a>Come usare il plug-in WMR

1. Apri Steam e cerca il plug-in per la realtà mista di Windows
    - Assicurarsi che SteamVR sia chiuso prima di avviare il plug-in WMR. L'avvio del plug-in WMR avvia anche SteamVR.
    - Verificare che l'auricolare WMR sia collegato.

    ![Ricerca plug-in WMR](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. Selezionare **Launch** per la realtà mista di Windows per il plug-in SteamVR.

    ![Plug-in WMR](../features/images/build-deploy/WMR/WMRPlugin.png)

    - Verranno avviati SteamVR e il plug-in WMR e verrà visualizzata una nuova finestra di stato di rilevamento per l'auricolare WMR.
    - Per ulteriori informazioni, visitare la [documentazione di Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)

        ![Aspetto di avvio di WMR](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. In Unity, con la scena MRTK aperta, passare a **File > impostazioni di compilazione**

1. Creazione della scena
    - Selezionare **Aggiungi scena aperta**
    - Verificare che la piattaforma sia **autonoma**
    - Selezione **compilazione**
    - Scegliere il percorso per la nuova compilazione in Esplora file

    ![Impostazioni di compilazione per autonome](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. Verrà creato un nuovo file eseguibile Unity per avviare l'app. Selezionare il file eseguibile Unity in Esplora file.

    ![Unity Esplora file](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a>Vedi anche

- [Supporto per Android e iOS](../features/cross-platform/using-ar-foundation.md)
- [Supporto del movimento Leap](../features/cross-platform/leap-motion-mrtk.md)
- [Rilevamento delle funzionalità della piattaforma](../features/cross-platform/detecting-platform-capabilities.md)
