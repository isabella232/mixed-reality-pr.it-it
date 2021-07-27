---
title: Cronologia delle versioni di Holographic Remoting
description: Rimanere aggiornati sulla cronologia delle versioni della funzionalità Holographic Remoting per HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 07/20/2021
ms.topic: article
keywords: HoloLens, Comunicazione remota, Holographic Remoting, cronologia delle versioni, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale
ms.openlocfilehash: ec810683a556bebfe92615e9085d26bf33cf7f2c
ms.sourcegitcommit: ebc22c5adee0e785e45fb25fade83191e920f92b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2021
ms.locfileid: "114585724"
---
# <a name="holographic-remoting-version-history"></a>Cronologia delle versioni di Holographic Remoting

> [!IMPORTANT]
> Queste linee guida sono specifiche per Holographic Remoting HoloLens 2.

## <a name="version-261-july-20-2021"></a>Versione 2.6.1 (20 luglio 2021) <a name="v2.6.1"></a>
* L XR_MSFT_holographic_remoting_speech'estensione consente ora la nuova inizializzazione del riconoscimento vocale con nuovi parametri durante una sessione in esecuzione.
* Risolto un problema per cui l'affidabilità del riconoscimento vocale diminuisce su più connessioni.
* Varie correzioni di bug e miglioramenti della stabilità.

## <a name="version-260-june-10-2021"></a>Versione 2.6.0 (10 giugno 2021) <a name="v2.6.0"></a>
* Holographic Remoting con l'API OpenXR supporta ora:
  * Nuova estensione XR_MSFT_holographic_remoting_speech, che consente alle applicazioni di restare in ascolto di comandi vocali personalizzati in varie lingue.
  * Estensione XR_MSFT_scene_understanding, che fornisce alle applicazioni una rappresentazione strutturata di alto livello dei piani, delle mesh e degli oggetti nell'ambiente dell'utente, consentendo lo sviluppo di applicazioni con supporto spaziale. Tuttavia, con l'avvertenza che XR_SCENE_COMPUTE_CONSISTENCY_OCCLUSION_OPTIMIZED_MSFT è l'unica coerenza supportata da xrComputeNewSceneMSFT.
  * Estensione XR_MSFT_spatial_graph_bridge, che consente alle applicazioni di creare handle XrSpace per tenere traccia dei nodi spatial Graph di altre API o librerie della piattaforma del dispositivo Windows Mixed Reality. Tuttavia, con l'avvertenza che XR_SPATIAL_GRAPH_NODE_TYPE_STATIC_MSFT è l'unico tipo di nodo supportato da xrCreateSpatialGraphNodeSpaceMSFT. 
* Holographic Remoting che usa l'API realtà mista supporta ora:
  * Gli overload SpatialGraphInteropPreview.CreateCoordinateSystemForNode, che consentono alle applicazioni di tenere traccia dei nodi Graph spaziali statici in modo che gli utenti possano pensare a luoghi e cose nel proprio ambiente.
* Holographic Remoting che usa le API OpenXR e Mixed Reality ora supporta:
  * Microsoft.MixedReality.SceneUnderstanding SDK, che consente alle applicazioni di calcolare una descrizione della scena che circonda l'utente (ad esempio pareti, piani e superfici) fornendo quad, mesh e segnali di posizionamento del contenuto.
  * Microsoft.MixedReality.QR SDK, che consente alle applicazioni di tenere traccia della posizione, delle dimensioni e del contenuto dei codici a barre rilevati.
* L'esempio remoto OpenXR è stato aggiornato per includere: 
  * Esempio di uso dell'estensione XR_MSFT_holographic_remoting_speech.
* L'esempio remoto di realtà mista è stato aggiornato per includere:  
  * Esempio di uso dell'SDK Microsoft.MixedReality.SceneUnderstanding.
  * Esempio di uso di Microsoft.MixedReality.QR SDK (che sostituisce il meccanismo di rilevamento del codice a matrice precedente).
* Il lettore Holographic Remoting ora mostra un'animazione di caricamento mentre viene stabilita la connessione.
* Sono stati risolti i problemi di compatibilità di RenderDoc sia nel runtime dell'API OpenXR che nell'esempio di API di realtà mista.
* Varie correzioni di bug e miglioramenti della stabilità.

## <a name="version-250-february-12-2021"></a>Versione 2.5.0 (12 febbraio 2021) <a name="v2.5.0"></a>
* Holographic Remoting con [l'API OpenXR](../native/openxr.md) supporta ora:
  * XR_MSFT_spatial_anchor'estensione. Questa estensione consente a un'applicazione di creare ancoraggi nello spazio, ovvero punti di spazio libero arbitrari nell'ambiente fisico dell'utente che verranno monitorati dal runtime.
  * XR_MSFT_controller_model'estensione. Questa estensione fornisce un meccanismo per caricare i modelli GLTF per i controller.
  * Canali di dati personalizzati come parte dell'XR_MSFT_holographic_remoting personalizzata. Un esempio per è illustrato [nell'esempio remoto OpenXR](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).
* Miglioramento della sincronizzazione tra il lettore e il lato remoto. In questo modo è possibile modificare dinamicamente la posizione e il buffer dei frame, in modo da garantire che il contenuto sottoposto a rendering remoto raggiunga senza problemi gli schermi alla frequenza dei fotogrammi di destinazione prevista.
* Miglioramento delle prestazioni del lettore Holographic Remoting disponibile tramite il Microsoft Store. In HoloLens 2 il lettore viene ora eseguito in tinta unita su 60 fotogrammi al secondo.
* Trasmissione ottimizzata di mesh di superficie spaziale su cui è possibile eseguire query tramite [SpatialSurfaceObserver](/uwp/api/windows.perception.spatial.surfaces.spatialsurfaceobserver) da un'app remota.
* Risolto un problema per cui la chiamata dei metodi SpatialAnchorManager o il rilascio di ancoraggi causava eccezioni alla disconnessione.
* Correzione di un problema di threading che causava arresti anomali durante la chiusura di istanze PlayerContext o RemoteContext.
* Holographic Remoting Player sul desktop: visualizza un messaggio di errore quando Windows Mixed Reality non è installato invece di chiudersi automaticamente.
* Sono stati apportati numerosi altri miglioramenti alla stabilità e alle correzioni di bug.

## <a name="version-241-january-22-2021"></a>Versione 2.4.1 (22 gennaio 2021) <a name="v2.4.1"></a>

* Correzione del problema relativo al fatto che SpatialAnchorManager::RequestStoreAsync non funziona in modo affidabile quando viene chiamato durante la connessione.
* Correzione del problema relativo a SpatialAnchorManager::TrySave che non salva correttamente un ancoraggio se l'ancoraggio in questione non è localizzato.

## <a name="version-240-december-1-2020"></a>Versione 2.4.0 (1 dicembre 2020) <a name="v2.4.0"></a>

* Holographic Remoting supporta ora la scrittura di app remote tramite [l'API OpenXR.](../native/openxr.md) Per [iniziare, vedere Writing a Holographic Remoting remote app using OpenXR APIs](holographic-remoting-create-remote-openxr.md) (Scrittura di un'app remota Holographic Remoting con le API OpenXR).
* Correzioni di bug e miglioramenti della stabilità.

## <a name="version-231-october-10-2020"></a>Versione 2.3.1 (10 ottobre 2020) <a name="v2.3.1"></a>

* Correzione della regressione con stima della posizione remota, che causava instabilità visiva.
* Implementazione di PerceptionDeviceSetCreateFactoryOverride, che garantisce che PerceptionDevice.dll fornito con Holographic Remoting non interferisca con la versione fornita con Windows 10.

## <a name="version-230-october-2-2020"></a>Versione 2.3.0 (2 ottobre 2020) <a name="v2.3.0"></a>

* Correzione degli arresti anomali, che possono verificarsi quando Holographic Remoting Player viene sospeso.
* Miglioramenti della stabilità.

## <a name="version-223-august-28-2020"></a>Versione 2.2.3 (28 agosto 2020) <a name="v2.2.3"></a>

* Correzioni di bug e miglioramenti della stabilità.

## <a name="version-222-july-10-2020"></a>Versione 2.2.2 (10 luglio 2020) <a name="v2.2.2"></a>

* Correzione del problema con [HolographicCamera.LeftViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) e [HolographicCamera.RightViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) che non restituisce vertici della mesh di area nascosta durante lo streaming da un visore VR Windows Mixed Reality dispositivo.
* Correzione dell'arresto anomalo del sistema, che può verificarsi con una connessione di rete non corretta.

## <a name="version-221-july-6-2020"></a>Versione 2.2.1 (6 luglio 2020) <a name="v2.2.1"></a>

> [!IMPORTANT]
> [Windows convalida del kit di certificazione](https://developer.microsoft.com/windows/downloads/app-certification-kit/) app con la versione [2.2.0](holographic-remoting-version-history.md#v2.2.0) avrà esito negativo. Se si è nella versione [2.2.0](holographic-remoting-version-history.md#v2.2.0) e si vuole inviare l'applicazione al lease p di Microsoft Store aggiornato almeno alla versione 2.2.1.
* Correzione dei [Windows di conformità del kit di certificazione](https://developer.microsoft.com/windows/downloads/app-certification-kit/) app.

## <a name="version-220-july-1-2020"></a>Versione 2.2.0 (1 luglio 2020) <a name="v2.2.0"></a>

* Il lettore Holographic Remoting può ora essere installato nei PC che eseguono Windows Mixed Reality [,](../../discover/navigating-the-windows-mixed-reality-home.md)rendendo possibile lo streaming in visori VR immersive.
* [I controller del](../../design/motion-controllers.md) movimento sono ora supportati da Holographic Remoting e i dati specifici del controller possono essere recuperati tramite [SpatialInteractionSource.Controller.](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
* [SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference) è ora supportato e la fase corrente può essere recuperata tramite [SpatialStageFrameOfReference.Current.](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current) È anche possibile richiedere una nuova fase tramite [SpatialStageFrameOfReference.RequestNewStageAsync.](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* Nelle versioni precedenti la stima della posizione è stata gestita sul lato lettore dal lettore Holographic Remoting. A partire dalla versione 2.2.0, Holographic Remoting dispone della sincronizzazione dell'ora e la stima viene eseguita completamente dall'applicazione remota. Gli utenti devono anche aspettarsi una maggiore stabilità degli ologrammi in situazioni di rete difficili.

## <a name="version-213-may-25-2020"></a>Versione 2.1.3 (25 maggio 2020) <a name="v2.1.3"></a>

* Modifica del comportamento [dell'evento HolographicSpace.CameraAdded.](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) Nelle versioni precedenti  non era garantito che un elemento [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera) aggiunto abbia anche un [oggetto HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) valido durante la creazione del frame successivo tramite [HolographicSpace.CreateNextFrame.](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe) A partire dalla versione 2.1.3, [HolographicSpace.CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) è sincronizzato con i dati di posizione provenienti da Holographic Remoting Player. Gli utenti possono aspettarsi che quando viene aggiunta una fotocamera sia disponibile anche un oggetto [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) valido per la fotocamera nel fotogramma successivo.
* Aggiunta **di Disabled** a DepthBufferStreamResolution, che può essere usata per disabilitare lo streaming del buffer di profondità tramite RemoteContext.ConfigureDepthVideoStream. Si noti che se viene [usato HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) avrà esito *negativo con E_ILLEGAL_METHOD_CALL*.
* La schermata di avvio di Holographic Remoting Player è stata riprogettata e ora non blocca la visualizzazione degli utenti.
* Miglioramenti della stabilità e correzioni di bug.

## <a name="version-212-april-5-2020"></a>Versione 2.1.2 (5 aprile 2020) <a name="v2.1.2"></a>

* Correzione del problema di compatibilità audio con le versioni precedenti tra il lettore Holographic Remoting più recente e le app remote che usano una versione precedente alla 2.1.0.
* Risolto un problema di ancoraggio nello spaziale, che chiudeva in modo imprevisto il lettore Holographic Remoting. Questo problema interessa anche i lettori personalizzati.

## <a name="version-211-march-20-2020"></a>Versione 2.1.1 (20 marzo 2020) <a name="v2.1.1"></a>

* Correzione del problema di codifica video con le app remote quando si usano GPU AMD.
* Miglioramenti delle prestazioni del lettore holographic Remoting.

## <a name="version-210-march-11-2020"></a>Versione 2.1.0 (11 marzo 2020) <a name="v2.1.0"></a>

* Trasporto di rete commutato per [l'uso di RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) tramite UDP. Le connessioni sicure usano [ora SRTP.](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) Si noti che [Holographic Remoting Player è](holographic-remoting-player.md) ancora compatibile con tutte le versioni precedenti di Holographic Remoting. Per trarre vantaggio dal nuovo trasporto di rete, holographic Remoting Player e l'app remota in questione devono usare la versione 2.1.0.
* Aggiunta del supporto [per HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_). 

## <a name="version-2020-february-2-2020"></a>Versione 2.0.20 (2 febbraio 2020) <a name="v2.0.20"></a>

* Correzione di vari bug che causano arresti anomali.

## <a name="version-2018-december-17-2019"></a>Versione 2.0.18 (17 dicembre 2019) <a name="v2.0.18"></a>

* Aggiunta del supporto [per HolographicViewConfiguration](/uwp/api/windows.graphics.holographic.holographicviewconfiguration)
* Correzione di vari bug che causano arresti anomali.
* Correzione del bug per cui era necessario un callback HolographicSpace.CameraAdded per accettare holographicCamera e presentarlo come fotocamera aggiunta in HolographicFrame.

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
* Miglioramenti di stabilità e affidabilità

## <a name="version-208-august-20-2019"></a>Versione 2.0.8 (20 agosto 2019) <a name="v2.0.8"></a>

* Correzione dell'arresto anomalo quando si chiama [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) con [IDXGISurface2](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) come parametro.
* Miglioramenti di stabilità e affidabilità

## <a name="version-207-july-26-2019"></a>Versione 2.0.7 (26 luglio 2019) <a name="v2.0.7"></a>

* Prima versione pubblica di Holographic Remoting per HoloLens 2.

## <a name="see-also"></a>Vedere anche

* [Scrittura di un'app remota Holographic Remoting Windows Mixed Reality API](holographic-remoting-create-remote-wmr.md)
* [Scrittura di un'app remota Holographic Remoting con le API OpenXR](holographic-remoting-create-remote-openxr.md)
* [Scrivere un'app lettore Holographic Remoting personalizzata](holographic-remoting-create-player.md)
* [Risoluzione dei problemi e limitazioni di Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)