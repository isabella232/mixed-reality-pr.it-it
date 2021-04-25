---
title: Cronologia delle versioni di Holographic Remoting
description: Rimanere aggiornati sulla cronologia delle versioni della funzionalità Holographic Remoting per HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Comunicazione remota, Holographic Remoting, cronologia delle versioni, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale
ms.openlocfilehash: 93ab38108d5ad557d61ad366ebb7aebd8cb65ab7
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2021
ms.locfileid: "107944703"
---
# <a name="holographic-remoting-version-history"></a>Cronologia delle versioni di Holographic Remoting

> [!IMPORTANT]
> Queste linee guida sono specifiche per Holographic Remoting in HoloLens 2.

## <a name="version-250-february-12-2021"></a>Versione 2.5.0 (12 febbraio 2021) <a name="v2.5.0"></a>
* Holographic Remoting con [l'API OpenXR](../native/openxr.md) supporta ora:
  * XR_MSFT_spatial_anchor'estensione. Questa estensione consente a un'applicazione di creare ancoraggi nello spazio, ovvero punti di spazio libero arbitrari nell'ambiente fisico dell'utente che verranno monitorati dal runtime.
  * XR_MSFT_controller_model'estensione. Questa estensione fornisce un meccanismo per caricare i modelli GLTF per i controller.
  * Canali di dati personalizzati come parte dell'XR_MSFT_holographic_remoting personalizzata. Un esempio per è illustrato [nell'esempio remoto OpenXR.](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)
* Sincronizzazione migliorata tra il lettore e il lato remoto. In questo modo è possibile modificare dinamicamente la posizione e il buffer dei frame, in modo da garantire che il contenuto sottoposto a rendering remoto raggiunga senza problemi gli schermi alla frequenza dei fotogrammi di destinazione prevista.
* Miglioramento delle prestazioni del lettore Holographic Remoting disponibile tramite il Microsoft Store. In HoloLens 2 il lettore viene ora eseguito in tinta unita su 60 fotogrammi al secondo.
* Trasmissione ottimizzata di mesh di superficie spaziale su cui è possibile eseguire query tramite [SpatialSurfaceObserver](/uwp/api/windows.perception.spatial.surfaces.spatialsurfaceobserver) da un'app remota.
* Risolto un problema per cui la chiamata dei metodi SpatialAnchorManager o il rilascio di ancoraggi causava eccezioni alla disconnessione.
* Correzione di un problema di threading che causava arresti anomali durante la chiusura di istanze PlayerContext o RemoteContext.
* Holographic Remoting Player sul desktop: visualizza un messaggio di errore Windows Mixed Reality non è installato invece di chiudersi automaticamente.
* Molte altre correzioni di bug e miglioramenti alla stabilità.

## <a name="version-241-january-22-2021"></a>Versione 2.4.1 (22 gennaio 2021) <a name="v2.4.1"></a>

* Correzione del problema relativo a SpatialAnchorManager::RequestStoreAsync non funziona in modo affidabile quando viene chiamato durante la connessione.
* È stato risolto un problema con SpatialAnchorManager::TrySave non salvando correttamente un ancoraggio se l'ancoraggio in questione non è localizzato.

## <a name="version-240-december-1-2020"></a>Versione 2.4.0 (1 dicembre 2020) <a name="v2.4.0"></a>

* Holographic Remoting supporta ora la scrittura di app remote usando [l'API OpenXR](../native/openxr.md). Per [iniziare, vedere Writing a Holographic Remoting remote app using OpenXR APIs (Scrittura di un'app remota Holographic Remoting con le API OpenXR).](holographic-remoting-create-remote-openxr.md)
* Correzioni di bug e miglioramenti della stabilità.

## <a name="version-231-october-10-2020"></a>Versione 2.3.1 (10 ottobre 2020) <a name="v2.3.1"></a>

* Correzione della regressione con la stima della posizione remota, che ha causato jitter visivo.
* Implementato PerceptionDeviceSetCreateFactoryOverride, che assicura che PerceptionDevice.dll forniti con Holographic Remoting non interferisca con la versione fornita con Windows 10.

## <a name="version-230-october-2-2020"></a>Versione 2.3.0 (2 ottobre 2020) <a name="v2.3.0"></a>

* Correzione di arresti anomali, che possono verificarsi quando Holographic Remoting Player viene sospeso.
* Miglioramenti della stabilità.

## <a name="version-223-august-28-2020"></a>Versione 2.2.3 (28 agosto 2020) <a name="v2.2.3"></a>

* Correzioni di bug e miglioramenti della stabilità.

## <a name="version-222-july-10-2020"></a>Versione 2.2.2 (10 luglio 2020) <a name="v2.2.2"></a>

* È stato risolto un problema con [HolographicCamera.LeftViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) e [HolographicCamera.RightViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) che non restituiscono vertici della mesh di area nascosta durante lo streaming da un visore Windows Mixed Reality visore.
* Correzione dell'arresto anomalo del sistema, che può verificarsi con una connessione di rete non corretta.

## <a name="version-221-july-6-2020"></a>Versione 2.2.1 (6 luglio 2020) <a name="v2.2.1"></a>

> [!IMPORTANT]
> [Kit di certificazione app Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) convalida con la [versione 2.2.0](holographic-remoting-version-history.md#v2.2.0) avrà esito negativo. Se si è nella versione [2.2.0](holographic-remoting-version-history.md#v2.2.0) e si vuole inviare l'applicazione al lease p di Microsoft Store aggiornato almeno alla versione 2.2.1.
* Correzione dei [Kit di certificazione app Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) di conformità.

## <a name="version-220-july-1-2020"></a>Versione 2.2.0 (1 luglio 2020) <a name="v2.2.0"></a>

* Il lettore Holographic Remoting può ora essere installato nei PC che eseguono Windows Mixed Reality [,](../../discover/navigating-the-windows-mixed-reality-home.md)rendendo possibile lo streaming in visori VR immersive.
* [I controller del](../../design/motion-controllers.md) movimento sono ora supportati da Holographic Remoting e i dati specifici del controller possono essere recuperati tramite [SpatialInteractionSource.Controller.](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
* [SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference) è ora supportato e la fase corrente può essere recuperata tramite [SpatialStageFrameOfReference.Current.](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current) È anche possibile richiedere una nuova fase tramite [SpatialStageFrameOfReference.RequestNewStageAsync.](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* Nelle versioni precedenti la stima della posizione è stata gestita sul lato lettore dal lettore Holographic Remoting. A partire dalla versione 2.2.0, Holographic Remoting dispone della sincronizzazione dell'ora e la stima viene eseguita completamente dall'applicazione remota. Gli utenti devono anche aspettarsi una maggiore stabilità degli ologrammi in situazioni di rete difficili.

## <a name="version-213-may-25-2020"></a>Versione 2.1.3 (25 maggio 2020) <a name="v2.1.3"></a>

* Modifica del comportamento [dell'evento HolographicSpace.CameraAdded.](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) Nelle versioni precedenti  non era garantito che un elemento [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera) aggiunto abbia anche un [oggetto HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) valido durante la creazione del frame successivo tramite [HolographicSpace.CreateNextFrame.](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe) A partire dalla versione 2.1.3, [HolographicSpace.CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) è sincronizzato con i dati di posizione provenienti da Holographic Remoting Player. Gli utenti possono aspettarsi che quando viene aggiunta una fotocamera sia disponibile anche un oggetto [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) valido per la fotocamera nel fotogramma successivo.
* Aggiunta **di Disabled** a DepthBufferStreamResolution, che può essere usata per disabilitare lo streaming del buffer di profondità tramite RemoteContext.ConfigureDepthVideoStream. Si noti che se viene [usato HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) avrà esito negativo *E_ILLEGAL_METHOD_CALL*.
* La schermata di avvio di Holographic Remoting Player è stata riprogettata e ora non blocca la visualizzazione degli utenti.
* Miglioramenti della stabilità e correzioni di bug.

## <a name="version-212-april-5-2020"></a>Versione 2.1.2 (5 aprile 2020) <a name="v2.1.2"></a>

* Risolto il problema di compatibilità con le versioni precedenti dell'audio tra il lettore Holographic Remoting più recente e le app remote usando una versione inferiore alla 2.1.0.
* Risolto un problema di ancoraggio spaziale, che chiudeva in modo imprevisto il lettore Holographic Remoting. Questo problema interessa anche i lettori personalizzati.

## <a name="version-211-march-20-2020"></a>Versione 2.1.1 (20 marzo 2020) <a name="v2.1.1"></a>

* È stato risolto un problema di codifica video con le app remote quando si usano GPU AMD.
* Miglioramenti delle prestazioni di Holographic Remoting Player.

## <a name="version-210-march-11-2020"></a>Versione 2.1.0 (11 marzo 2020) <a name="v2.1.0"></a>

* Trasporto di rete commutato per [l'uso di RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) tramite UDP. Le connessioni protette [usano ora SRTP.](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) Si noti che [Holographic Remoting Player](holographic-remoting-player.md) è ancora compatibile con tutte le versioni precedenti di Holographic Remoting. Per trarre vantaggio dal nuovo trasporto di rete, sia Holographic Remoting Player che l'app remota in questione devono usare la versione 2.1.0.
* Aggiunta del supporto [per HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_). 

## <a name="version-2020-february-2-2020"></a>Versione 2.0.20 (2 febbraio 2020) <a name="v2.0.20"></a>

* Correzione di vari bug che causano arresti anomali.

## <a name="version-2018-december-17-2019"></a>Versione 2.0.18 (17 dicembre 2019) <a name="v2.0.18"></a>

* Aggiunta del supporto [per HolographicViewConfiguration](/uwp/api/windows.graphics.holographic.holographicviewconfiguration)
* Correzione di vari bug che causano arresti anomali.
* Correzione del bug per cui era necessario un callback HolographicSpace.CameraAdded per l'accettazione di holographicCamera e la visualizzazione come fotocamera aggiunta in HolographicFrame.

## <a name="version-2016-november-11-2019"></a>Versione 2.0.16 (11 novembre 2019) <a name="2.0.16"></a>

* Correzione del deadlock nel rilevamento del codice a qr.
* Correzione dell'eccezione non gestita a causa di un'attesa di blocco nel thread principale.

## <a name="version-2014-october-26-2019"></a>Versione 2.0.14 (26 ottobre 2019) <a name="v2.0.14"></a>

* Supporto per le nuove API PerceptionDevice (Windows 10 aggiornamento di novembre 2019).
* È stato risolto un problema che impediva l'attivazione di eventi di movimento di blocco da parte di SpatialGestureRecognizer.
* Correzione di un problema di threading quando si usa SpatialSurfaceObserver.SetBoundingVolume.

## <a name="version-2012-october-18-2019"></a>Versione 2.0.12 (18 ottobre 2019) <a name="v2.0.12"></a>

* Correzione dell'arresto anomalo in SpatialGestureRecognizer quando si usa NavigationRail(X/Y/Z).

## <a name="version-2010-october-10-2019"></a>Versione 2.0.10 (10 ottobre 2019) <a name="v2.0.10"></a>

* Correzione dell'arresto anomalo quando si usa il pulsante di attivazione dei controller VR. Holographic Remoting non supporta completamente i controller, solo il pulsante trigger e il pulsante Windows funzionano se associati a HoloLens 2.

## <a name="version-209-september-19-2019"></a>Versione 2.0.9 (19 settembre 2019) <a name="v2.0.9"></a>

* Aggiunta del supporto [per SpatialAnchorExporter](/uwp/api/windows.perception.spatial.spatialanchorexporter)
* Aggiunta di una nuova ```IPlayerContext2``` interfaccia ```PlayerContext``` (implementata da ) che fornisce i membri seguenti:
  - [Proprietà BlitRemoteFrameTimeout.](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)
* Valore ```Failed_RemoteFrameTooOld``` aggiunto a ```BlitResult```
* Miglioramenti alla stabilità e all'affidabilità

## <a name="version-208-august-20-2019"></a>Versione 2.0.8 (20 agosto 2019) <a name="v2.0.8"></a>

* Correzione dell'arresto anomalo del sistema quando si chiama [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) con [IDXGISurface2](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) come parametro.
* Miglioramenti della stabilità e dell'affidabilità

## <a name="version-207-july-26-2019"></a>Versione 2.0.7 (26 luglio 2019) <a name="v2.0.7"></a>

* Prima versione pubblica di Holographic Remoting per HoloLens 2.

## <a name="see-also"></a>Vedere anche

* [Scrittura di un'app remota Holographic Remoting usando Windows Mixed Reality API](holographic-remoting-create-remote-wmr.md)
* [Scrittura di un'app remota Holographic Remoting con API OpenXR](holographic-remoting-create-remote-openxr.md)
* [Scrivere un'app lettore Holographic Remoting personalizzata](holographic-remoting-create-player.md)
* [Risoluzione dei problemi e limitazioni di Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)