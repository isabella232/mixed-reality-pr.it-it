---
title: Introduzione a MRTK e XR SDK
description: Pagina di destinazione per MRTK con XR SDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, XRSDK, XR SDK
ms.openlocfilehash: d3ff4306205cc6548bc5617d727f32a780855439
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647202"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Introduzione a MRTK e XR SDK

XR SDK è la nuova pipeline XR di [Unity in Unity 2019.3 e oltre.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) In Unity 2019 offre un'alternativa alla pipeline XR esistente. In Unity 2020 diventerà l'unica pipeline XR in Unity.

## <a name="prerequisites"></a>Prerequisiti

Per iniziare a usare Mixed Reality Toolkit, seguire [la procedura fornita](../install-the-tools.md#importing-the-mixed-reality-toolkit) per aggiungere MRTK a un progetto.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Configurazione di Unity per la pipeline di XR SDK

La pipeline XR SDK supporta attualmente 3 piattaforme: Windows Mixed Reality, Oculus e OpenXR. Le sezioni seguenti illustrano i passaggi necessari per configurare XR SDK per ogni piattaforma.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Passare alla **versione di Unity Gestione pacchetti** installare il pacchetto plug-in Windows XR, che aggiunge il supporto per Windows Mixed Reality in XR SDK. Verrà visualizzato anche alcuni pacchetti di dipendenze. 

1. Assicurarsi che tutti gli elementi seguenti siano stati installati correttamente:
   * Gestione plug-in XR
   * Plug-in XR di Windows
   * Helper di input legacy XR

2. Passa a **Edit > Project Settings** (Modifica > Impostazioni progetto).
3. Fare clic sulla scheda Gestione plug-in XR nella finestra Impostazioni progetto.
4. Passare alle impostazioni piattaforma UWP (Universal Windows Platform) e verificare che Windows Mixed Reality sia selezionato in Provider di plug-in.
5. Assicurarsi che l'opzione Inizializza XR all'avvio sia selezionata.
6. (**_Obbligatorio per holoLens Remoting nell'editor, in caso contrario facoltativo_**) Passare alle impostazioni autonome e verificare che Windows Mixed Reality sia selezionata in Provider di plug-in. Assicurarsi inoltre che l'opzione Inizializza XR all'avvio sia selezionata.

![Gestione del plug-in XR con la scheda Autonomo selezionata](images/xr-management-img-02.png)

7. (**_Facoltativo_**) Fare clic sulla Windows Mixed Reality in Gestione plug-in XR e creare un profilo di impostazioni personalizzato per modificare le impostazioni predefinite. Se l'elenco di impostazioni è già presente, non è necessario creare alcun profilo.

![Gestione del plug-in XR con la scheda Windows selezionata](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. Seguire la guida alla pipeline di XR SDK per configurare [Oculus Quest in MRTK](../supported-devices/oculus-quest-mrtk.md) fino alla fine. La guida illustra i passaggi necessari per configurare Unity e MRTK per usare la pipeline XR SDK per Oculus Quest.

### <a name="openxr-preview"></a>OpenXR (anteprima)

> [!IMPORTANT]
> OpenXR in Unity è supportato solo in Unity 2020.2 e versioni successive.
>
> Attualmente supporta solo compilazioni x64 e ARM64.

1. Seguire la [guida Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) (Uso del plug-in OpenXR di realtà mista per Unity), inclusa la procedura per configurare la gestione e l'ottimizzazione dei plug-in XR per installare il plug-in OpenXR nel progetto. Assicurarsi che gli elementi seguenti siano stati installati correttamente:
   1. Gestione plug-in XR
   1. Plug-in OpenXR
   1. Plug-in OpenXR di realtà mista
1. Passare a Modifica impostazioni > progetto.
1. Fare clic sulla scheda Gestione plug-in XR nella finestra Impostazioni progetto.
1. Assicurarsi che l'opzione Inizializza XR all'avvio sia selezionata.
1. (**_Facoltativo_**) Se la destinazione HoloLens 2, assicurarsi di essere nella piattaforma UWP e selezionare Microsoft HoloLens set di funzionalità

![Gestione dei plug-in Open XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Se si dispone di un progetto preesistibile che usa MRTK da UPM, assicurarsi che la riga seguente si trovi nel file **link.xml** che si trova nella cartella MixedRealityToolkit.Generated.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> Per la versione iniziale di MRTK e OpenXR, sono supportati in modo nativo HoloLens 2 mani articolate e Windows Mixed Reality di movimento. Nelle prossime versioni verrà aggiunto il supporto per hardware aggiuntivo.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Configurazione di MRTK per la pipeline di XR SDK
::: moniker range=">= mrtkunity-2021-05" 
Se si usa OpenXR, scegliere "DefaultOpenXRConfigurationProfile" come profilo attivo o clonarlo per apportare personalizzazioni.

Se si usano altri runtime XR nella configurazione di Gestione plug-in XR, ad esempio Windows Mixed Reality o Oculus, scegliere "DefaultXRSDKConfigurationProfile" come profilo attivo o clonarlo per apportare personalizzazioni.

Questi profili vengono impostati con i sistemi e i provider corretti, se necessario. Per [altre informazioni sul profilo e](../features/profiles/profiles.md#xr-sdk) sul supporto di esempio con XR SDK, vedere la documentazione sui profili.

Per eseguire la migrazione di un profilo esistente a XR SDK, è necessario aggiungere i servizi e i provider di dati seguenti. Sarà possibile visualizzare i nuovi provider di dati nella scheda XR SDK

![Scheda XR SDK](../features/images/xrsdk/XrsdkTabView.png)

### <a name="camera"></a>Fotocamera

Aggiungere i provider di dati seguenti 

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**e**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |

![Impostazioni della fotocamera di XR SDK](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Input

Aggiungere i provider di dati seguenti 

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR__:

![Impostazioni di input OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![Impostazioni di input di XR SDK](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Limite

Aggiungere i provider di dati seguenti 

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Impostazioni dei limiti di XR SDK](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Consapevolezza spaziale

Aggiungere i provider di dati seguenti 

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| In corso | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Impostazioni di riconoscimento spaziale di XR SDK](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Mapping dei controller

Se si usano profili di mapping del controller personalizzati, aprirne uno ed eseguire la voce di menu Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles per assicurarsi che siano definiti i nuovi tipi di controller XR SDK.

## <a name="see-also"></a>Vedi anche

* [Introduzione allo sviluppo di ar in Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Introduzione allo sviluppo vr in Unity](https://docs.unity3d.com/Manual/VROverview.html)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Se si usa OpenXR, scegliere "DefaultOpenXRConfigurationProfile" come profilo attivo o clonarlo per apportare personalizzazioni.

Se si usano altri runtime XR nella configurazione di Gestione plug-in XR, ad esempio Windows Mixed Reality o Oculus, scegliere "DefaultXRSDKConfigurationProfile" come profilo attivo o clonarlo per apportare personalizzazioni.

Questi profili vengono impostati con i sistemi e i provider corretti, se necessario. Per [altre informazioni sul profilo e](../features/profiles/profiles.md#xr-sdk) sul supporto di esempio con XR SDK, vedere la documentazione sui profili.

Per eseguire la migrazione di un profilo esistente a XR SDK, è necessario aggiornare i servizi e i provider di dati seguenti:

### <a name="camera"></a>Fotocamera

Da [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Impostazioni della fotocamera legacy](../features/images/xrsdk/CameraSystemLegacy.png)

in

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**e**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |

![Impostazioni della fotocamera di XR SDK](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Input

Da [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Impostazioni di input legacy](../features/images/xrsdk/InputSystemWMRLegacy.png)

in

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR:__

![Impostazioni di input OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![Impostazioni di input di XR SDK](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Limite

Da [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Impostazioni dei limiti legacy](../features/images/xrsdk/BoundarySystemLegacy.png)

in

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Impostazioni dei limiti di XR SDK](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Consapevolezza spaziale

Da [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Impostazioni di consapevolezza spaziale legacy](../features/images/xrsdk/SpatialAwarenessLegacy.png)

in

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| In corso | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Impostazioni di consapevolezza spaziale di XR SDK](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Mapping dei controller

Se si usano profili di mapping del controller personalizzati, aprirne uno ed eseguire la voce di menu Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles (Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles) per assicurarsi che siano definiti i nuovi tipi di controller XR SDK.

## <a name="see-also"></a>Vedi anche

* [Introduzione allo sviluppo ar in Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Introduzione allo sviluppo della realtà virtuale in Unity](https://docs.unity3d.com/Manual/VROverview.html)
::: moniker-end