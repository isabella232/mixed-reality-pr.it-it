---
title: GettingStartedWithMRTKAndXRSDK
description: Pagina di destinazione per MRTK con XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, XRSDK,
ms.openlocfilehash: c1f4baec1927fd97948245f31c40788473c457d0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681274"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Introduzione a MRTK e XR SDK

XR SDK è la [nuova pipeline XR di Unity in unity 2019,3 e versioni successive](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/). In Unity 2019, fornisce un'alternativa alla pipeline XR esistente. In Unity 2020, diventerà l'unica pipeline XR in Unity.

## <a name="prerequisites"></a>Prerequisiti

Per iniziare a usare il Toolkit di realtà mista, seguire [i passaggi forniti](../WelcomeToMRTK.md) per aggiungere MRTK a un progetto.

## <a name="add-xr-sdk-to-a-unity-project"></a>Aggiungere XR SDK a un progetto Unity

Per MRTK 2,3, la realtà mista di Windows è supportata in XR SDK.

### <a name="required-in-unity"></a>Obbligatorio in Unity

1. Passare a gestione pacchetti di Unity e installare il pacchetto di plug-in di Windows XR, che aggiunge il supporto per la realtà mista di Windows in XR SDK. Verrà anche effettuato il pull di alcuni pacchetti di dipendenze. Verificare che tutti gli elementi seguenti siano stati installati correttamente:
   1. Gestione dei plug-in XR
   1. Plug-in Windows XR
   1. Helper di input legacy XR
1. Passare a modifica > impostazioni progetto.
1. Fare clic sulla scheda Gestione plug-in XR nella finestra Impostazioni progetto.
1. Passare alle impostazioni piattaforma UWP (Universal Windows Platform) e verificare che la realtà mista di Windows sia selezionata in provider plug-in.
1. Assicurarsi che l'opzione Inizializza XR all'avvio sia selezionata.
1. (**_Facoltativo_**) Fare clic sulla scheda realtà mista di Windows in Gestione plug-in XR e creare un profilo delle impostazioni personalizzate per modificare le impostazioni predefinite. Se l'elenco delle impostazioni è già presente, non è necessario creare alcun profilo.

![Gestione dei plug-in](../features/Images/XRSDK/PluginManagement.png)

### <a name="required-in-mrtk"></a>Obbligatorio in MRTK

Scegliere "DefaultXRSDKConfigurationProfile" come profilo attivo o clonarlo per apportare le personalizzazioni. Questo profilo è configurato con i sistemi e i provider di MRTK XR SDK, ove necessario.

Per eseguire la migrazione di un profilo esistente a XR SDK, è necessario aggiornare i servizi e i provider di dati seguenti:

#### <a name="camera"></a>Fotocamera

Da [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Impostazioni della fotocamera legacy](../features/Images/XRSDK/CameraSystemLegacy.png)

a [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **e**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)

![Impostazioni della fotocamera di XR SDK](../features/Images/XRSDK/CameraSystemXRSDK.png)

#### <a name="input"></a>Input

Da [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Impostazioni di input legacy](../features/Images/XRSDK/InputSystemWMRLegacy.png)

A [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager)

![Impostazioni di input di XR SDK](../features/Images/XRSDK/InputSystemWMRXRSDK.png)

#### <a name="boundary"></a>Limite

Da [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Impostazioni limite legacy](../features/Images/XRSDK/BoundarySystemLegacy.png)

A  [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem)

![Impostazioni limite SDK XR](../features/Images/XRSDK/BoundarySystemXRSDK.png)

#### <a name="spatial-awareness"></a>Consapevolezza spaziale

Da [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Impostazioni di consapevolezza spaziale legacy](../features/Images/XRSDK/SpatialAwarenessLegacy.png)

A [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver)

![Impostazioni di sensibilizzazione spaziale di XR SDK](../features/Images/XRSDK/SpatialAwarenessXRSDK.png)

#### <a name="controller-mappings"></a>Mapping dei controller

Se si usano profili di mapping del controller personalizzato, aprire uno di essi ed eseguire la voce di menu Mixed Reality Toolkit-> Utilities-> Update-> controller mapping del controller per assicurarsi che siano definiti i nuovi tipi di controller di XR SDK.

## <a name="see-also"></a>Vedi anche

* [Introduzione allo sviluppo AR in Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Introduzione allo sviluppo per VR in Unity](https://docs.unity3d.com/Manual/VROverview.html)
