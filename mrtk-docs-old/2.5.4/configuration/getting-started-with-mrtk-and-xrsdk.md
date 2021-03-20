---
title: GettingStartedWithMRTKAndXRSDK
description: Pagina di destinazione per MRTK con XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, XRSDK,
ms.openlocfilehash: 825641616047c920b677cb93662438389f1f3506
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682204"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Introduzione a MRTK e XR SDK

XR SDK è la [nuova pipeline XR di Unity in unity 2019,3 e versioni successive](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/). In Unity 2019, fornisce un'alternativa alla pipeline XR esistente. In Unity 2020, diventerà l'unica pipeline XR in Unity.

## <a name="prerequisites"></a>Prerequisiti

Per iniziare a usare il Toolkit di realtà mista, seguire [i passaggi forniti](../../2.5.4/welcome-to-mrtk.md) per aggiungere MRTK a un progetto.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Configurazione di Unity per la pipeline di XR SDK

La pipeline dell'SDK XR supporta attualmente 3 piattaforme: realtà mista di Windows, Oculus e OpenXR. Le sezioni seguenti illustrano i passaggi necessari per configurare XR SDK per ogni piattaforma.

#### <a name="windows-mixed-reality"></a>Windows Mixed Reality

1. Passare a gestione pacchetti di Unity e installare il pacchetto di plug-in di Windows XR, che aggiunge il supporto per la realtà mista di Windows in XR SDK. Verrà anche effettuato il pull di alcuni pacchetti di dipendenze. Verificare che tutti gli elementi seguenti siano stati installati correttamente:
   1. Gestione dei plug-in XR
   1. Plug-in Windows XR
   1. Helper di input legacy XR
1. Passare a modifica > impostazioni progetto.
1. Fare clic sulla scheda Gestione plug-in XR nella finestra Impostazioni progetto.
1. Passare alle impostazioni piattaforma UWP (Universal Windows Platform) e verificare che la realtà mista di Windows sia selezionata in provider plug-in.
1. Assicurarsi che l'opzione Inizializza XR all'avvio sia selezionata.
1. (**_Obbligatorio per la comunicazione remota HoloLens nell'editor, in caso contrario facoltativo_**) Passare alle impostazioni autonome e verificare che la realtà mista di Windows sia selezionata in provider plug-in. Assicurarsi anche che Initialize XR all'avvio sia selezionato.
1. (**_Facoltativo_**) Fare clic sulla scheda realtà mista di Windows in Gestione plug-in XR e creare un profilo delle impostazioni personalizzate per modificare le impostazioni predefinite. Se l'elenco delle impostazioni è già presente, non è necessario creare alcun profilo.

![Gestione dei plug-in](../features/images/xrsdk/PluginManagement.png)

#### <a name="oculus"></a>Oculus

1. Seguire la [procedura come configurare Oculus quest in MRTK usando la guida alla pipeline dell'SDK XR](../features/cross-platform/oculus-quest-mrtk.md) alla fine. La guida descrive i passaggi necessari per configurare Unity e MRTK per l'uso della pipeline di XR SDK per l'Oculus quest.

#### <a name="openxr-preview"></a>OpenXR (anteprima)

> [!IMPORTANT]
> OpenXR in Unity è supportato solo in Unity 2020,2 e versioni successive.
>
> Attualmente, supporta anche solo le compilazioni x64 e ARM64.

1. Per installare il plug-in di OpenXR nel progetto, seguire la guida per l'uso del plug-in [reality OpenXR per Unity](https://aka.ms/openxr-unity-install) , inclusi i passaggi per la configurazione della gestione dei plug-in XR e dell'ottimizzazione. Verificare che siano stati installati i seguenti elementi:
   1. Gestione dei plug-in XR
   1. Plug-in OpenXR
   1. Plug-in OpenXR realtà mista
1. Passare a modifica > impostazioni progetto.
1. Fare clic sulla scheda Gestione plug-in XR nella finestra Impostazioni progetto.
1. Assicurarsi che l'opzione Inizializza XR all'avvio sia selezionata.
1. (**_Facoltativo_**) Se la destinazione è HoloLens 2, assicurarsi di trovarsi nella piattaforma UWP e selezionare il set di funzionalità di Microsoft HoloLens

![Gestione plug-in aperto XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Se si dispone di un progetto preesistente che usa MRTK da UPM, assicurarsi che la riga seguente si trovi nel file **link.xml** che si trova nella cartella MixedRealityToolkit. generated.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> Per la versione iniziale di MRTK e OpenXR, sono supportati in modo nativo solo i controller di movimento per la realtà mista HoloLens 2 e Windows. Il supporto per hardware aggiuntivo verrà aggiunto nelle prossime versioni.

### <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Configurazione di MRTK per la pipeline di XR SDK

Se si usa OpenXR, scegliere "DefaultOpenXRConfigurationProfile" come profilo attivo o clonarlo per apportare le personalizzazioni.

Se si usano altri runtime XR nella configurazione di gestione plug-in XR, ad esempio realtà mista di Windows o Oculus, scegliere "DefaultXRSDKConfigurationProfile" come profilo attivo o clonarlo per apportare le personalizzazioni.

Questi profili sono configurati con i sistemi e i provider corretti, ove necessario.

Per eseguire la migrazione di un profilo esistente a XR SDK, è necessario aggiornare i servizi e i provider di dati seguenti:

#### <a name="camera"></a>Fotocamera

Da [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Impostazioni della fotocamera legacy](../features/images/xrsdk/CameraSystemLegacy.png)

in

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**e**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |

![Impostazioni della fotocamera di XR SDK](../features/images/xrsdk/CameraSystemXRSDK.png)

#### <a name="input"></a>Input

Da [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Impostazioni di input legacy](../features/images/xrsdk/InputSystemWMRLegacy.png)

in

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR__:

![Impostazioni di input di OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

__Realtà mista di Windows__:

![Impostazioni di input di XR SDK](../features/images/xrsdk/InputSystemWMRXRSDK.png)

#### <a name="boundary"></a>Limite

Da [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Impostazioni limite legacy](../features/images/xrsdk/BoundarySystemLegacy.png)

in

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Impostazioni limite SDK XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

#### <a name="spatial-awareness"></a>Consapevolezza spaziale

Da [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Impostazioni di consapevolezza spaziale legacy](../features/images/xrsdk/SpatialAwarenessLegacy.png)

in

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| In corso | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Impostazioni di sensibilizzazione spaziale di XR SDK](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

#### <a name="controller-mappings"></a>Mapping dei controller

Se si usano profili di mapping del controller personalizzato, aprire uno di essi ed eseguire la voce di menu Mixed Reality Toolkit-> Utilities-> Update-> controller mapping del controller per assicurarsi che siano definiti i nuovi tipi di controller di XR SDK.

## <a name="see-also"></a>Vedi anche

* [Introduzione allo sviluppo AR in Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Introduzione allo sviluppo per VR in Unity](https://docs.unity3d.com/Manual/VROverview.html)
