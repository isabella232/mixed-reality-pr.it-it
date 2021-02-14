---
title: Cronologia delle versioni remota olografica
description: Rimanere sempre aggiornati sulla cronologia delle versioni della funzionalità di comunicazione remota olografica per HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica, cronologia delle versioni, auricolare in realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 8fa1671657a7cb057f88da24fe4cfe68b0401397
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496039"
---
# <a name="holographic-remoting-version-history"></a>Cronologia delle versioni remota olografica

> [!IMPORTANT]
> Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.

## <a name="version-250-february-12-2021"></a>Versione 2.5.0 (12 febbraio 2021) <a name="v2.5.0"></a>
* La comunicazione remota olografica con l' [API OpenXR](../native/openxr.md) supporta ora:
  * Estensione XR_MSFT_spatial_anchor. Questa estensione consente a un'applicazione di creare ancoraggi spaziali, ovvero punti FreeSpace arbitrari nell'ambiente fisico dell'utente che verranno rilevati dal runtime.
  * Estensione XR_MSFT_controller_model. Questa estensione fornisce un meccanismo per caricare i modelli GLTF per i controller.
  * Canali di dati personalizzati come parte dell'estensione XR_MSFT_holographic_remoting. Un esempio per è illustrato nell' [esempio remoto OpenXR](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).
* Sincronizzazione migliorata tra il lettore e il lato remoto. In questo modo è possibile modificare dinamicamente la posizione e il buffering dei frame, per garantire che il contenuto sottoposto a rendering remoto raggiunga correttamente gli schermi nella frequenza dei fotogrammi di destinazione prevista
* Miglioramento delle prestazioni del lettore di comunicazione remota olografico disponibile tramite il Microsoft Store. In HoloLens 2 il giocatore esegue ora il solido su 60 fotogrammi al secondo.
* Trasmissione ottimizzata di mesh di superficie spaziale su cui è possibile eseguire query tramite [SpatialSurfaceObserver](https://docs.microsoft.com/uwp/api/windows.perception.spatial.surfaces.spatialsurfaceobserver) da un'app remota.
* È stato risolto un problema per cui la chiamata di metodi SpatialAnchorManager o il rilascio di ancoraggi causava eccezioni alla disconnessione.
* Correzione del problema di threading che causava arresti anomali durante la chiusura di istanze di PlayerContext o RemoteContext.
* Molte altre correzioni di bug e miglioramenti alla stabilità.

## <a name="version-241-january-22-2021"></a>Versione 2.4.1 (22 gennaio 2021) <a name="v2.4.1"></a>

* Correzione del problema relativo a SpatialAnchorManager:: RequestStoreAsync non funziona in modo affidabile quando viene chiamato durante la connessione.
* Correzione del problema relativo a SpatialAnchorManager:: TrySave non è stato corretto il salvataggio di un ancoraggio se Anchor in question non è locatable.

## <a name="version-240-december-1-2020"></a>Versione 2.4.0 (1 dicembre 2020) <a name="v2.4.0"></a>

* La comunicazione remota olografica supporta ora la scrittura di app Remote con l' [API OpenXR](../native/openxr.md). Per iniziare, vedere la pagina relativa alla [scrittura di un'app remota di comunicazione remota olografica usando le API OpenXR](holographic-remoting-create-remote-openxr.md) .
* Correzioni di bug e miglioramenti alla stabilità.

## <a name="version-231-october-10-2020"></a>Versione 2.3.1 (10 ottobre 2020) <a name="v2.3.1"></a>

* Correzione della regressione con la stima di posa remota, che ha causato l'instabilità visiva.
* Implementato PerceptionDeviceSetCreateFactoryOverride, che garantisce che PerceptionDevice.dll fornito con la comunicazione remota olografica non interferisca con la versione fornita con Windows 10.

## <a name="version-230-october-2-2020"></a>Versione 2.3.0 (2 ottobre 2020) <a name="v2.3.0"></a>

* Correzione di arresti anomali, che può verificarsi quando il lettore di comunicazione remota olografica è sospeso.
* Miglioramenti della stabilità.

## <a name="version-223-august-28-2020"></a>Versione 2.2.3 (28 agosto 2020) <a name="v2.2.3"></a>

* Correzioni di bug e miglioramenti alla stabilità.

## <a name="version-222-july-10-2020"></a>Versione 2.2.2 (10 luglio 2020) <a name="v2.2.2"></a>

* Correzione di un problema relativo a [HolographicCamera. LeftViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) e [HolographicCamera. RightViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) che non restituisce alcun vertice di mesh di area nascosta durante il flusso da un auricolare a realtà mista di Windows.
* Correzione di un arresto anomalo, che può verificarsi con una connessione di rete insufficiente.

## <a name="version-221-july-6-2020"></a>Versione 2.2.1 (6 luglio 2020) <a name="v2.2.1"></a>

> [!IMPORTANT]
> La convalida del [Kit di certificazione app Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) con versione [2.2.0](holographic-remoting-version-history.md#v2.2.0) avrà esito negativo. Se si usa la versione [2.2.0](holographic-remoting-version-history.md#v2.2.0) e si vuole inviare l'applicazione al lease di Microsoft Store p aggiornato almeno alla versione 2.2.1.
* Correzione dei problemi di conformità del [Kit di certificazione app Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) .

## <a name="version-220-july-1-2020"></a>Versione 2.2.0 (1 luglio 2020) <a name="v2.2.0"></a>

* È ora possibile installare il lettore di comunicazione remota olografica nei PC che eseguono la [realtà mista di Windows](../../discover/navigating-the-windows-mixed-reality-home.md), rendendo possibile lo streaming di auricolari immersivi.
* I [controller di movimento](../../design/motion-controllers.md) sono ora supportati dalla comunicazione remota olografica e i dati specifici del controller possono essere recuperati tramite [SpatialInteractionSource. controller](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller).
* [SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference) è ora supportato e la fase corrente può essere recuperata tramite [SpatialStageFrameOfReference. Current](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current). Inoltre, è possibile richiedere una nuova fase tramite [SpatialStageFrameOfReference. RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync).
* Nelle versioni precedenti, la stima di pose veniva gestita sul lato Player dal lettore di comunicazione remota olografica. A partire dalla versione 2.2.0, la comunicazione remota olografica ha la sincronizzazione dell'ora e la stima viene eseguita completamente dall'applicazione remota. Gli utenti devono inoltre prevedere una maggiore stabilità degli ologrammi in situazioni di rete complesse.

## <a name="version-213-may-25-2020"></a>Versione 2.1.3 (25 maggio 2020) <a name="v2.1.3"></a>

* Comportamento modificato dell'evento [HolographicSpace. CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) . Nelle versioni precedenti, **non** era garantito che un [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera) aggiunto abbia anche un [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) valido durante la creazione del frame successivo tramite [HolographicSpace. CreateNextFrame](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe). A partire dalla versione 2.1.3, [HolographicSpace. CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) viene sincronizzato con i dati di post provenienti dal lettore di comunicazione remota olografica. Gli utenti possono prevedere che, quando viene aggiunta una fotocamera, nel frame successivo è disponibile anche un [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) valido.
* Aggiunto **disabilitato** a DepthBufferStreamResolution, che può essere usato per disabilitare il flusso del buffer di profondità tramite RemoteContext.ConfigureDepthVideoStream. Si noti che se si usa [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) avrà esito negativo con *E_ILLEGAL_METHOD_CALL*.
* La schermata iniziale del lettore di comunicazione remota olografica è stata riprogettata e ora non blocca la visualizzazione degli utenti.
* Miglioramenti alla stabilità e correzioni di bug.

## <a name="version-212-april-5-2020"></a>Versione 2.1.2 (5 aprile 2020) <a name="v2.1.2"></a>

* Correzione del problema di compatibilità con le versioni precedenti dell'audio tra la versione più recente di Remote Remoting Player e le app Remote con una versione inferiore a 2.1.0.
* Problema di ancoraggio spaziale fisso, che ha chiuso in modo imprevisto il lettore di comunicazione remota olografica. Questo problema interessa anche i giocatori personalizzati.

## <a name="version-211-march-20-2020"></a>Versione 2.1.1 (20 marzo 2020) <a name="v2.1.1"></a>

* Correzione del problema di codifica video con le app remote quando si usano GPU AMD.
* Miglioramenti delle prestazioni del lettore di comunicazione remota olografico.

## <a name="version-210-march-11-2020"></a>Versione 2.1.0 (11 marzo 2020) <a name="v2.1.0"></a>

* Commutazione del trasporto di rete per l'uso di [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) tramite UDP. Le connessioni sicure usano [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) Now. Si noti che il [lettore di comunicazione remota olografico](holographic-remoting-player.md) è ancora compatibile con tutte le versioni di comunicazione remota olografica precedentemente disponibili. Per trarre vantaggio dal nuovo trasporto di rete, il lettore di comunicazione remota olografica e l'app remota in questione devono usare la versione 2.1.0.
* Aggiunta del supporto per [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_). 

## <a name="version-2020-february-2-2020"></a>Versione 2.0.20 (2 febbraio 2020) <a name="v2.0.20"></a>

* Corretti vari bug che causavano arresti anomali.

## <a name="version-2018-december-17-2019"></a>Versione 2.0.18 (17 dicembre 2019) <a name="v2.0.18"></a>

* Aggiunta del supporto per [HolographicViewConfiguration](/uwp/api/windows.graphics.holographic.holographicviewconfiguration)
* Corretti vari bug che causavano arresti anomali.
* Correzione del bug in cui è necessario un callback HolographicSpace. CameraAdded per l'accettazione di un HolographicCamera e la visualizzazione come fotocamera aggiuntiva in HolographicFrame.

## <a name="version-2016-november-11-2019"></a>Versione 2.0.16 (11 novembre 2019) <a name="2.0.16"></a>

* Correzione di un deadlock nel rilevamento del codice QR.
* Correzione dell'eccezione unhandeled a causa di un'attesa di blocco nel thread principale.

## <a name="version-2014-october-26-2019"></a>Versione 2.0.14 (26 ottobre 2019) <a name="v2.0.14"></a>

* Supporto per le nuove API PerceptionDevice (aggiornamento di Windows 10 di novembre 2019).
* Correzione del problema, che impedisce l'attivazione degli eventi di movimento da SpatialGestureRecognizer.
* Correzione del problema di threading quando si utilizza SpatialSurfaceObserver. SetBoundingVolume.

## <a name="version-2012-october-18-2019"></a>Versione 2.0.12 (18 ottobre 2019) <a name="v2.0.12"></a>

* Correzione di un arresto anomalo in SpatialGestureRecognizer quando si utilizza NavigationRail (X/Y/Z).

## <a name="version-2010-october-10-2019"></a>Versione 2.0.10 (10 ottobre 2019) <a name="v2.0.10"></a>

* Correzione di un arresto anomalo quando si usa il pulsante trigger dei controller VR. La comunicazione remota olografica non supporta completamente i controller, ma solo il pulsante trigger e il pulsante Windows funzionano se abbinati a HoloLens 2.

## <a name="version-209-september-19-2019"></a>Versione 2.0.9 (19 settembre 2019) <a name="v2.0.9"></a>

* Aggiunta del supporto per [SpatialAnchorExporter](/uwp/api/windows.perception.spatial.spatialanchorexporter)
* Aggiunta ```IPlayerContext2``` di una nuova interfaccia (implementata da ```PlayerContext``` ) che fornisce i membri seguenti:
  - Proprietà [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .
* Aggiunto ```Failed_RemoteFrameTooOld``` valore a ```BlitResult```
* Miglioramenti alla stabilità e all'affidabilità

## <a name="version-208-august-20-2019"></a>Versione 2.0.8 (20 agosto 2019) <a name="v2.0.8"></a>

* Correzione di un arresto anomalo quando si chiama [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) con un [IDXGISurface2](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) come parametro.
* Miglioramenti alla stabilità e all'affidabilità

## <a name="version-207-july-26-2019"></a>Versione 2.0.7 (26 luglio 2019) <a name="v2.0.7"></a>

* Prima versione pubblica della comunicazione remota olografica per HoloLens 2.

## <a name="see-also"></a>Vedere anche

* [Scrittura di un'app remota olografica remota usando le API di realtà mista di Windows](holographic-remoting-create-remote-wmr.md)
* [Scrittura di un'app remota di comunicazione remota olografica usando le API di OpenXR](holographic-remoting-create-remote-openxr.md)
* [Scrivere un'app lettore Holographic Remoting personalizzata](holographic-remoting-create-player.md)
* [Limitazioni e risoluzione dei problemi di comunicazione remota olografica](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)