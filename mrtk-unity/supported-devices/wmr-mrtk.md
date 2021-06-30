---
title: Distribuzione in HoloLens e visori VR WMR
description: Documentazione per compilare e distribuire app in vari dispositivi.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Visual Studio
ms.openlocfilehash: 12384c3d3c0c2208d86a9a946580d0311f8a8955
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042302"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a>Distribuzione in HoloLens e visori VR WMR

Esistono due modi per distribuire le applicazioni compilate con MRTK nel dispositivo Windows, la piattaforma UWP (Univeral Windows Platform) e la piattaforma autonoma. Le applicazioni compilate per HoloLens 1 o HoloLens 2 devono avere come destinazione la piattaforma UWP, mentre le applicazioni create per visori VR WMR possono avere come destinazione UWP o Standalone.

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a>Compilazione e distribuzione di MRTK in HoloLens 1, HoloLens 2 visori VR WMR (UWP)

Le istruzioni su come compilare e distribuire **per HoloLens 1** **e HoloLens 2** (UWP) sono disponibili nella compilazione dell'applicazione nel [dispositivo](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device). Questi passaggi consentono anche di distribuire nei **visori VR WMR.**

> [!NOTE]
> Quando si distribuisce l'applicazione nel dispositivo in Visual Studio, è necessario configurare Visual Studio in modo leggermente diverso a seconda del dispositivo. Le configurazioni sono le seguenti:
>
>| Piattaforma | Configurazione | Architecture | Destinazione |
|---|---|---|---|
| HoloLens 2 | Versione o master | ARM64 | Dispositivo |
| HoloLens 1 | Versione o master | x86 | Dispositivo |
| Visori VR WMR | Versione o master | x64 | Computer locale |

**Suggerimento:** Quando si compila per HoloLens 1, HoloLens 2 o WMR, è consigliabile che le impostazioni di compilazione "Versione SDK di destinazione" e "Versione minima della piattaforma" siano simili a quanto illustrato nell'immagine seguente:

![Finestra Di compilazione](../features/images/getting-started/BuildWindow.png)

Le altre impostazioni possono essere diverse,ad esempio Configurazione della compilazione/Architettura/Tipo di compilazione e altre possono sempre essere modificate all'interno della Visual Studio soluzione.

Assicurarsi che l'elenco a discesa "Versione SDK di destinazione" includa l'opzione "10.0.18362.0". Se questa versione non è presente, è necessario installare [l'Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) più recente.

### <a name="unity-20192020-and-hololens"></a>Unity 2019/2020 e HoloLens

Se un'app HoloLens viene visualizzata come pannello 2D nel dispositivo, verifica che le impostazioni seguenti siano state configurate in Unity prima di distribuire l'app UWP:

Se si usa il supporto XR incorporato legacy (solo Unity 2019):

1. Passare a Edit > Project Settings( Modifica impostazioni progetto), Player (Lettore)
1. In XR Settings (Impostazioni **XR)** nella scheda UWP verifica che **Virtual Reality Supported** (Realtà virtuale supportata) sia abilitato e che **Windows Mixed Reality** SDK sia stato aggiunto agli SDK.
1. Compilare e distribuire in Visual Studio

Se si usano i plug-in OpenXR o Windows XR:

1. Seguire la procedura descritta in [Attività iniziali con XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)
1. Assicurarsi che il profilo di configurazione sia **DefaultXRSDKConfigurationProfile**
1. Passare a **Edit > Project Settings (> Impostazioni progetto), XR-Plugin Management (Gestione progetti)** e verificare **Windows Mixed Reality** sia abilitato.
1. Compilare e distribuire in Visual Studio

>[!IMPORTANT]
> Se si usa Unity 2019.3.x, selezionare **ARM64** e non **ARM** come architettura di compilazione in Visual Studio. Con le impostazioni unity predefinite in Unity 2019.3.x, un'app Unity non verrà distribuita in HoloLens se arm è selezionato a causa di un bug di Unity.
>
> Se è necessaria l'architettura ARM, passare a Edit **> Project Settings (Modifica** impostazioni progetto), Player (Lettore) e nel menu Other Settings **(Altre impostazioni)** **disabilitare Graphics Jobs (Processi grafici).** La disabilitazione **dei processi di** grafica consentirà all'app di eseguire la distribuzione usando l'architettura di compilazione ARM per Unity 2019.3.x, ma è consigliabile usare ARM64.
>
> Questo problema è stato risolto in Unity 2019.4 e Unity 2020.3.

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a>Compilazione e distribuzione di MRTK in visori VR WMR (Standalone)

Le build autonome di MRTK possono essere usate nei visori VR WMR. Una build autonoma per un visore VR WMR richiede i passaggi aggiuntivi seguenti:

> [!NOTE]
> XR SDK di Unity supporta anche WMR nativo nelle build autonome, ma non richiede plugin WmR o WmR. Questi passaggi sono necessari per la versione XR legacy di Unity.

1. Installare [Steam](https://store.steampowered.com/about/)
1. Installare [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)
1. Installare il [plug-in WMR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

### <a name="how-to-use-wmr-plugin"></a>Come usare il plug-in WMR

1. Aprire Steam e cercare il plug-in Windows Mixed Reality
    - Prima di avviare il plug-in WMR, assicurarsi che Il plug-in WmR sia chiuso. L'avvio del plug-in WMR avvia anche SteamVR.
    - Assicurarsi che il visore VR WMR sia collegato.

    ![Ricerca plug-in WMR](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. Selezionare **Launch (Avvia)** per Windows Mixed Reality per Plugin DirVr.

    ![Plug-in WMR](../features/images/build-deploy/WMR/WMRPlugin.png)

    - Verrà avviato SteamVR e il plug-in WMR e verrà visualizzata una nuova finestra di stato di rilevamento per il visore VR WMR.
    - Per altre informazioni, vedere la [documentazione Windows Mixed Reality Surrey.](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)

        ![Aspetto di avvio di WMR](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. In Unity, con la scena MRTK aperta, passare a File > Build Settings (Impostazioni **compilazione file)**

1. Creare la scena
    - Selezionare **Add Open Scene (Aggiungi scena aperta)**
    - Assicurarsi che la piattaforma sia **autonoma**
    - Selezionare **Build (Compila)**
    - Scegliere il percorso per la nuova compilazione in Esplora file

    ![Impostazioni di compilazione per la versione autonoma](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. Verrà creato un nuovo eseguibile Unity. Per avviare l'app, selezionare l'eseguibile Unity in Esplora file.

    ![Esplora file Unity](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a>Vedere anche

- [Supporto per Android e iOS](using-ar-foundation.md)
- [Supporto del movimento Leap](leap-motion-mrtk.md)
- [Rilevamento delle funzionalità della piattaforma](detecting-platform-capabilities.md)