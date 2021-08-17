---
title: Risoluzione dei problemi e limitazioni di Holographic Remoting
description: Trovare le risorse per la risoluzione dei problemi e le istruzioni per la funzionalità Holographic Remoting HoloLens 2 dispositivi.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, ologrammi, comunicazione remota olografica, rendering remoto, rendering di rete, HoloLens, ologrammi remoti, risoluzione dei problemi, guida, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale
ms.openlocfilehash: d49f73f4cbe205e71cb2f76ab02769ddad5f3ed2
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184612"
---
# <a name="holographic-remoting-troubleshooting"></a>Risoluzione dei problemi di Holographic Remoting

> [!IMPORTANT]
> Queste linee guida sono specifiche per Holographic Remoting in HoloLens 2.

## <a name="spectre-mitigated-libraries-not-found"></a>Librerie con mitigazione Spectre non trovate.

Le app di esempio holographic Remoting hanno la mitigazione Spectre (/Qspectre) abilitata nella configurazione della versione.

Se viene visualizzato *l'errore irreversibile vccorlib.lib,* assicurarsi che il carico di lavoro Visual Studio includa le librerie con mitigazione [Spectre](/cpp/build/reference/qspectre)

## <a name="speech"></a>Voce

Holographic Remoting Player supporta una sovrimpressione diagnostica, che può essere abilitata ```Enable Diagnostics``` pronunciando e disabilitando pronunciando ```Disable Diagnostics``` . Se si verificano problemi con questi comandi vocali, è anche possibile avviare il lettore Holographic Remoting tramite un Web browser usando ```ms-holographic-remoting:?stats``` come URL.

## <a name="h265-video-codec-not-available"></a>Codec video H265 non disponibile

Installare il [estensioni video HEVC](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) quando si usa il codec video H265 nell'app remota. Se si verificano problemi in cui il codec è installato ma non può essere usato, vedere la guida alla [risoluzione dei](/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) problemi.

## <a name="limitations"></a>Limitazioni

Le API seguenti non  sono attualmente supportate quando si usa Holographic Remoting per HoloLens 2 e genereranno un errore se non ```ERROR_NOT_SUPPORTED``` diversamente specificato:

[Windows.Graphics.Holographic](/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - Supportato a partire dalla [versione 2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - Nelle versioni precedenti viene sempre generato un errore.
* [HolographicCamera.IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - Supportato a partire dalla [versione 2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - Nelle versioni precedenti non hanno esito negativo, ma le dimensioni della destinazione di rendering non verranno modificate.
* [HolographicCameraPose.OverrideProjectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose.OverrideViewport](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose.OverrideViewTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - Supportato a partire dalla [versione 2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - Doe.
  - Supportato a partire dalla [versione 2.1.0](holographic-remoting-version-history.md#v2.1.0)
* [HolographicDisplay.TryGetViewConfiguration](/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - L'esecuzione di query su HolographicViewConfigurationKind.PhotoVideoCamera restituirà sempre ```nullptr``` .
  - Supportato a partire dalla [versione 2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - Nelle versioni precedenti viene sempre generato un errore.
* [HolographicSpace.CreateFramePresentationMonitor](/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [HolographicDisplay.GetDefault](/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - Segnala un errore se viene chiamato prima che venga stabilita una connessione.


[Windows.Perception.Spatial](/uwp/api/windows.perception.spatial)

* [SpatialLocation.AbsoluteAngularAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation.AbsoluteAngularVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation.AbsoluteLinearAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation.AbsoluteLinearVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference.Current](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - Supportato a partire dalla [versione 2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - Nelle versioni precedenti restituisce sempre ```nullptr``` .
* [SpatialStageFrameOfReference.RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - Supportato a partire dalla [versione 2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [SpatialAnchor.RemovedByUser](/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - Supportato a partire dalla [versione 2.0.9.](holographic-remoting-version-history.md#v2.0.9) 
  - Nelle versioni precedenti restituisce sempre ```nullptr``` . 
* [SpatialAnchorExporter.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - Supportato a partire dalla [versione 2.0.9.](holographic-remoting-version-history.md#v2.0.9) 
  - Nelle versioni precedenti l'operazione asincrona viene sempre completata con ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [SpatialAnchorTransferManager.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - L'operazione asincrona viene sempre completata con ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [SpatialAnchorTransferManager.TryExportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - L'operazione asincrona viene sempre completata con ```false``` .
* [SpatialAnchorTransferManager.TryImportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - L'operazione asincrona viene sempre completata con ```nullptr``` .

[Windows.UI.Input.Spatial](/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [SpatialInteractionSource.Controller](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - Supportato a partire dalla [versione 2.2.0](holographic-remoting-version-history.md#v2.2.0)

[Windows.Perception.Spatial.Preview](/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>Vedere anche
* [Panoramica di Holographic Remoting](holographic-remoting-overview.md)
* [Cronologia delle versioni di Holographic Remoting](holographic-remoting-version-history.md)
* [Scrittura di un'app remota Holographic Remoting Windows Mixed Reality API](holographic-remoting-create-remote-wmr.md)
* [Scrittura di un'app remota Holographic Remoting con le API OpenXR](holographic-remoting-create-remote-openxr.md)
* [Scrivere un'app lettore Holographic Remoting personalizzata](holographic-remoting-create-player.md)
* [Condizioni di licenza software per Holographic Remoting](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)