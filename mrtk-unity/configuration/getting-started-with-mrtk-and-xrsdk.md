---
title: Introduzione a MRTK e XR SDK
description: Pagina di destinazione per MRTK con XR SDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, XRSDK, XR SDK
ms.openlocfilehash: 1560188d1a69f0083940a37da8c378691ee75a9d569c2c5088e0e3f614a44858
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188272"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Introduzione a MRTK e XR SDK

XR SDK è la nuova pipeline XR di [Unity in Unity 2019.3 e versioni ancora.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) In Unity 2019 offre un'alternativa alla pipeline XR esistente. In Unity 2020 è l'unica pipeline XR in Unity.

## <a name="prerequisites"></a>Prerequisiti

Per iniziare a usare mixed reality Toolkit, segui la procedura fornita [per](../install-the-tools.md#importing-the-mixed-reality-toolkit) aggiungere MRTK a un progetto.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Configurazione di Unity per la pipeline di XR SDK

La pipeline XR SDK supporta attualmente 3 piattaforme: Windows Mixed Reality, Oculus e OpenXR. Le sezioni seguenti illustrano i passaggi necessari per configurare XR SDK per ogni piattaforma.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Passare al Gestione pacchetti di **Unity e** installare il pacchetto Windows plug-in XR, che aggiunge il supporto per Windows Mixed Reality in XR SDK. In questo modo verranno trascinati anche alcuni pacchetti di dipendenze.

1. Verificare che tutti gli elementi seguenti siano stati installati correttamente:
   * Gestione dei plug-in XR
   * Windows Plug-in XR
   * Helper di input legacy XR

2. Passa a **Edit > Project Settings** (Modifica > Impostazioni progetto).
3. Fare clic sulla scheda XR Plug-in Management (Gestione plug-in XR) Project Impostazioni finestra.
4. Passare alle impostazioni di Universal Windows Platform e verificare Windows Mixed Reality'opzione sia selezionata in Plug-in Providers (Provider plug-in).
5. Assicurarsi che l'opzione Initialize XR on Startup (Inizializza XR all'avvio) sia selezionata.
6. ( Obbligatorio per la comunicazione remota nell HoloLens **_nell'editor; in caso contrario, facoltativo_**) Passare alle impostazioni autonome e verificare che Windows Mixed Reality sia selezionata in Provider di plug-in. Assicurarsi inoltre che l'opzione Initialize XR on Startup (Inizializza XR all'avvio) sia selezionata.

    ![Gestione del plug-in XR con la scheda Autonomo selezionata](images/xr-management-img-02.png)

7. (**_Facoltativo_**) Fare clic sulla Windows Mixed Reality in XR Plug-in Management (Gestione plug-in XR) e creare un profilo di impostazioni personalizzate per modificare le impostazioni predefinite. Se l'elenco delle impostazioni è già presente, non è necessario creare alcun profilo.

    ![Gestione del plug-in XR Windows scheda selezionata](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. Seguire la guida alla fine [come configurare Oculus Quest in MRTK usando la pipeline XR SDK.](../supported-devices/oculus-quest-mrtk.md) La guida illustra i passaggi necessari per configurare Unity e MRTK per l'uso della pipeline XR SDK per Oculus Quest.

### <a name="openxr"></a>OpenXR

> [!IMPORTANT]
> OpenXR in Unity è supportato solo in Unity 2020.2 e versioni successive.
> Supporta anche solo build x64, ARM e ARM64.

1. Seguire la guida [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) (Uso del plug-in OpenXR di Realtà mista per Unity), inclusi i passaggi per configurare la gestione e l'ottimizzazione dei plug-in XR per installare il plug-in OpenXR nel progetto. Verificare che gli elementi seguenti siano stati installati correttamente:
   1. Gestione dei plug-in XR
   1. Plug-in OpenXR
   1. Plug-in OpenXR per realtà mista
1. Passare a Modifica > Project Impostazioni.
1. Fare clic sulla scheda XR Plug-in Management (Gestione plug-in XR) Project Impostazioni finestra.
1. Assicurarsi che l'opzione Initialize XR on Startup (Inizializza XR all'avvio) sia selezionata.
1. (**_Facoltativo_**) Se la destinazione HoloLens 2, assicurarsi di essere nella piattaforma UWP e selezionare Microsoft HoloLens set di funzionalità

![OpenXR per la gestione dei plug-in](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Se si dispone di un progetto preesistibile che usa MRTK da UPM, assicurarsi che la riga seguente si trovi nel file **link.xml** che si trova nella cartella MixedRealityToolkit.Generated.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> Per il rilascio iniziale di MRTK e OpenXR, sono supportati in modo nativo HoloLens 2 mani articolate Windows Mixed Reality controller del movimento. Il supporto per hardware aggiuntivo verrà aggiunto nelle versioni future.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Configurazione di MRTK per la pipeline XR SDK

::: moniker range=">= mrtkunity-2021-05"
Usare uno dei profili MRTK predefiniti, che sono tutti configurati nelle pipeline XR di Unity. I precedenti "DefaultOpenXRConfigurationProfile" e "DefaultXRSDKConfigurationProfile" sono ora etichettati come obsoleti.
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Se si usa OpenXR, scegliere "DefaultOpenXRConfigurationProfile" come profilo attivo o clonarlo per apportare personalizzazioni.

Se si usano altri runtime XR nella configurazione di Gestione plug-in XR, ad esempio Windows Mixed Reality o Oculus, scegliere "DefaultXRSDKConfigurationProfile" come profilo attivo o clonarlo per apportare personalizzazioni.

Questi profili vengono impostati con i sistemi e i provider corretti, se necessario. Per [altre informazioni sul profilo](../features/profiles/profiles.md#xr-sdk) e sul supporto di esempio con XR SDK, vedere la documentazione sui profili.
::: moniker-end

Per eseguire la migrazione di un profilo esistente a XR SDK, è necessario aggiornare i servizi e i provider di dati seguenti.
::: moniker range=">= mrtkunity-2021-05"
Sarà possibile visualizzare i nuovi provider di dati nella scheda XR SDK in Unity 2019 o nella visualizzazione principale/solo in Unity 2020+, dove XR legacy non esiste.

![Scheda XR SDK](../features/images/xrsdk/XrsdkTabView.png)
::: moniker-end

### <a name="camera"></a>Fotocamera

::: moniker range=">= mrtkunity-2021-05"
Aggiungere i provider di dati seguenti
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Da [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Impostazioni della fotocamera legacy](../features/images/xrsdk/CameraSystemLegacy.png)

in
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end

![Impostazioni della fotocamera di XR SDK](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Input

::: moniker range=">= mrtkunity-2021-05"
Aggiungere i provider di dati seguenti
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Da [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Impostazioni di input legacy](../features/images/xrsdk/InputSystemWMRLegacy.png)

in
::: moniker-end

| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR:__

![Impostazioni di input OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![Impostazioni di input di XR SDK](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Limite

::: moniker range=">= mrtkunity-2021-05"
Aggiungere i provider di dati seguenti
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Da [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Impostazioni dei limiti legacy](../features/images/xrsdk/BoundarySystemLegacy.png)

in
::: moniker-end

| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Impostazioni dei limiti di XR SDK](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Consapevolezza spaziale

::: moniker range=">= mrtkunity-2021-05"
Aggiungere i provider di dati seguenti
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Da [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Impostazioni di consapevolezza spaziale legacy](../features/images/xrsdk/SpatialAwarenessLegacy.png)

in
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (per UWP) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (per UWP) |
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (per la rete non UWP) | |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| Plug-in OpenXR | Windows Plug-in XR |
|---------------|-------------------|
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |
::: moniker-end

![Impostazioni di consapevolezza spaziale di XR SDK](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Mapping dei controller

Se si usano profili di mapping del controller personalizzati, aprirne uno ed eseguire la voce di menu Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles per assicurarsi che siano definiti i nuovi tipi di controller XR SDK.

## <a name="see-also"></a>Vedi anche

* [Introduzione allo sviluppo di ar in Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Introduzione allo sviluppo vr in Unity](https://docs.unity3d.com/Manual/VROverview.html)
