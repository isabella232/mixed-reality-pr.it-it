---
title: Acquisizione di realtà mista per gli sviluppatori
description: Informazioni sulle procedure consigliate per l'abilitazione, l'uso e il rendering dell'acquisizione di realtà mista per gli sviluppatori.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc, foto, video, acquisizione, fotocamera
ms.openlocfilehash: af585cd212ba8f2ddc3ea812c1fff2a5da8603bff0e77d8fc2ad794486821685
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192102"
---
# <a name="mixed-reality-capture-for-developers"></a>Acquisizione di realtà mista per gli sviluppatori

> [!NOTE]
> Per indicazioni su una nuova funzionalità MRC per [HoloLens 2,](#render-from-the-pv-camera-opt-in) vedere Eseguire il rendering dalla fotocamera fotovolta HoloLens 2.

È possibile acquisire una foto o un video mrc [(Mixed Reality Capture)](/hololens/holographic-photos-and-videos) in qualsiasi momento, ma quando si sviluppa l'applicazione è necessario tenere presenti alcuni aspetti. Sono incluse le procedure consigliate per la qualità visiva mrc e la capacità di rispondere alle modifiche del sistema durante l'acquisizione di mrc.

Gli sviluppatori possono anche integrare facilmente l'acquisizione e l'inserimento di realtà mista nelle proprie app.

MRC in HoloLens (prima generazione) supporta video e foto fino a 720p, mentre MRC su HoloLens 2 supporta video fino a 1080p e foto con risoluzione fino a 4K.

## <a name="the-importance-of-quality-mrc"></a>L'importanza di MRC di qualità

Che si tratta di screenshot di realtà mista nella pagina Microsoft Store o di altri utenti che condividono contenuti di acquisizione sui social network, i contenuti multimediali Acquisizione realtà mista spesso sono una prima esposizione degli utenti all'app. È possibile usare MRC per eseguire la demo dell'app, informare gli utenti, invitare gli utenti a condividere le interazioni con il mondo misto e per la ricerca degli utenti e la risoluzione dei problemi.

## <a name="how-mrc-impacts-your-app"></a>Impatto di MRC sull'app

### <a name="enabling-mrc-in-your-app"></a>Abilitazione di MRC nell'app

Per impostazione predefinita, un'app non deve eseguire alcun tipo di operazione per consentire agli utenti di acquisire la realtà mista.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>Abilitazione di un allineamento migliorato per MRC nell'app

Per impostazione predefinita, l'acquisizione di realtà mista combina l'output olografico dell'occhio destro con la fotocamera foto/video (PV). Queste due origini vengono combinate usando il punto di attivazione impostato dall'app immersiva attualmente in esecuzione.

Ciò significa che gli ologrammi all'esterno del piano di messa a fuoco non verranno allineati a causa della distanza fisica tra la fotocamera fotovoltaico e lo schermo destro.

#### <a name="set-the-focus-point"></a>Impostare il punto di attivazione

Le app immersive (HoloLens) devono [](../unity/focus-point-in-unity.md) impostare il punto di interesse in cui si vuole posizionare il piano di stabilizzazione. In questo modo si garantisce l'allineamento ottimale sia nel visore sia nell'acquisizione di realtà mista.

Se non è impostato un punto di messa a fuoco, il piano di stabilizzazione avrà un valore predefinito di 2 metri.

#### <a name="render-from-the-pv-camera-opt-in"></a>Eseguire il rendering dalla fotocamera PV (consenso esplicito)

HoloLens 2 aggiunge la possibilità per un'app immersiva di eseguire il **rendering** dalla fotocamera fotovoltaico mentre è in esecuzione l'acquisizione di realtà mista. Per garantire che l'app supporti correttamente il rendering aggiuntivo, l'app deve acconsentire esplicitamente a questa funzionalità.

Il rendering dalla fotocamera PV offre i miglioramenti seguenti rispetto all'esperienza MRC predefinita:
* L'allineamento dell'ologramma all'ambiente fisico e le mani per le interazioni vicine devono essere accurate a tutte le distanze. Evitare di avere un offset a distanze diverse dal punto di messa a fuoco, come si potrebbe vedere nel codice MRC predefinito.
* L'occhio destro nel visore non verrà compromesso, perché non verrà usato per eseguire il rendering degli ologrammi per l'output MRC.

Per abilitare il rendering dalla fotocamera fotovoltaico, è necessario eseguire tre passaggi:
1. Abilitare PhotoVideoCamera HolographicViewConfiguration
2. Gestire il rendering di HolographicCamera aggiuntivo
3. Verificare che il rendering degli shader e del codice venga eseguito correttamente da questa holographicCamera aggiuntiva

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a>Abilitare PhotoVideoCamera HolographicViewConfiguration in DirectX

Per acconsentire esplicitamente al rendering dalla fotocamera fotovoltaico, un'app abilita semplicemente [HolographicViewConfiguration](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)di PhotoVideoCamera:
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfigurationKind.PhotoVideoCamera);
if (view != null)
{
    view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>Gestire il rendering di HolographicCamera aggiuntivo in DirectX

Quando l'app ha acconsentito esplicitamente per il rendering dalla fotocamera PV e dall'acquisizione di realtà mista, viene avviato:
1. Verrà generato l'evento CameraAdded di HolographicSpace. Questo evento può essere posticipato se l'app non è in grado di gestire la fotocamera in questo momento.
2. Al termine dell'evento senza rinvii in sospeso, HolographicCamera verrà visualizzato nell'elenco AddedCameras di HolographicFrame successivo.

Quando l'acquisizione di realtà mista si arresta (o se l'app disabilita la configurazione della visualizzazione mentre è in esecuzione l'acquisizione di realtà mista): HolographicCamera verrà visualizzato nell'elenco RemovedCameras di HolographicFrame successivo e l'evento CameraRemoved di HolographicSpace verrà generato.

È stata aggiunta una proprietà [ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) a HolographicCamera per identificare la configurazione a cui appartiene una fotocamera.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a>Abilitare PhotoVideoCamera HolographicViewConfiguration in Unity

> [!NOTE]
> Se si usa Unity 2018, è necessario **Unity 2018.4.13f1** o versione più recente. Se si usa Unity 2019, è necessario **Unity 2019.4** o versione più recente.

Per acconsentire esplicitamente al rendering dalla fotocamera [PV](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)quando si usa il Toolkit di realtà mista, abilitare il provider Windows Mixed Reality [Camera Impostazioni](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings) e selezionare Rendering **dalla fotocamera PV.**

Se non si usa l'Toolkit realtà mista, è [](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) possibile usare un componente per acconsentire manualmente come descritto in precedenza per DirectX.

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Gestire il rendering di HolographicCamera aggiuntivo in Unity

Questa operazione viene eseguita automaticamente da Unity.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a>Abilitare PhotoVideoCamera HolographicViewConfiguration in Unreal

> [!NOTE]
> Questa operazione richiede **Unreal Engine 4.25** o versioni successive.

Per acconsentire esplicitamente al rendering dalla fotocamera/videocamera:

1. Chiama **SetEnabledMixedRealityCamera** e **ResizeMixedRealityCamera**.
    * Usa i valori **Size X** (Dimensione X) e **Size Y** (Dimensione Y) per impostare le dimensioni video.

![Terza fotocamera](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a>Gestire il rendering di HolographicCamera aggiuntivo in Unreal

Questa operazione viene eseguita automaticamente da Unreal.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>Verificare che shader e codice supportino fotocamere aggiuntive

Eseguire un'acquisizione di realtà mista e verificare l'allineamento insolito, il contenuto mancante o i problemi di prestazioni. Aggiornare shader e codice in base alle esigenze.

Se alcune scene non supportano il rendering in una fotocamera aggiuntiva, è possibile disabilitare HolographicViewConfiguration di PhotoVideoCamera.

### <a name="disabling-mrc-in-your-app"></a>Disabilitazione di MRC nell'app

#### <a name="2d-app"></a>App 2D

Le app 2D possono scegliere di nascondere il contenuto visivo quando l'acquisizione di realtà mista viene eseguita da:
* Presenta con il flag [DXGI_PRESENT_RESTRICT_TO_OUTPUT](/windows/desktop/direct3ddxgi/dxgi-present)
* Creare la catena di scambio dell'app con il flag [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) app
* Con il Aggiornamento di Windows 10 (maggio 2019), l'impostazione di [IsScreenCaptureEnabled](/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled) di ApplicationView

#### <a name="immersive-app"></a>App immersiva

Le app immersive possono scegliere di escludere il contenuto visivo dall'acquisizione di realtà mista tramite:
* Impostazione di [IsContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) di HolographicCameraRenderingParameter per disabilitare l'acquisizione di realtà mista per il frame associato
* Impostazione di [IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) di HolographicCamera per disabilitare l'acquisizione di realtà mista per la fotocamera olografica associata

#### <a name="password-keyboard"></a>Tastiera password

Con il Aggiornamento di Windows 10 (maggio 2019), il contenuto visivo viene automaticamente escluso dall'acquisizione di realtà mista quando è visibile una password o una tastiera del pin.

### <a name="knowing-when-mrc-is-active"></a>Sapere quando MRC è attivo

La [classe AppCapture](/uwp/api/Windows.Media.Capture.AppCapture) può essere usata da un'app per sapere quando è in esecuzione l'acquisizione di realtà mista di sistema (per audio o video).

>[!NOTE]
>L'API [GetForCurrentView](/uwp/api/windows.media.capture.appcapture.getforcurrentview) di AppCapture può restituire Null se l'acquisizione di realtà mista non è disponibile nel dispositivo. È anche importante deregistrare l'evento CapturingChanged quando l'app viene sospesa, in caso contrario MRC può entrare in uno stato bloccato.

### <a name="best-practices-hololens-specific"></a>Procedure consigliate (HoloLens specifiche)

MrC dovrebbe funzionare senza ulteriori attività di sviluppo, ma è necessario tenere presenti alcuni aspetti quando si offre la migliore esperienza di acquisizione di realtà mista.

**MRC usa il canale alfa dell'ologramma per la fusione con le immagini [della](locatable-camera.md) fotocamera**

Il passaggio più importante consiste nel verificare che l'app sia trasparente anziché in nero opaco. In Unity questa operazione viene eseguita per impostazione predefinita con MixedRealityToolkit. Se si sviluppa in non Unity, potrebbe essere necessario apportare una modifica a una riga.

Di seguito sono riportati alcuni elementi che potrebbero essere visualizzati in MRC se l'app non sta cancellando il colore nero trasparente:

**Errori di esempio:** bordi neri intorno al contenuto (non riesce a cancellare il colore nero trasparente)

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failure to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

**Errori di esempio:** l'intera scena di sfondo dell'ologramma viene visualizzata in nero. L'impostazione di un valore alfa di sfondo pari a uno determina uno sfondo nero

![L'impostazione di un valore alfa di sfondo pari a 1 determina uno sfondo nero](images/clearopaqueblack-300px.png)

**Risultato previsto:** Ologrammi visualizzati correttamente con il mondo reale (risultato previsto se si cancella il nero trasparente)

![Risultato previsto in caso di cancellazione in nero trasparente](images/cleartransparentblack-300px.png)

**Soluzione**:
* Modificare il contenuto visualizzato come nero opaco in modo che abbia un valore alfa pari a 0.
* Assicurarsi che l'app sia trasparente in nero.
* Unity usa per impostazione predefinita la cancellazione automatica con MixedRealityToolkit, ma se si tratta di un'app non Unity è necessario modificare il colore usato con ID3D11DeiceContext::ClearRenderTargetView(). Si vuole assicurarsi di usare il colore nero trasparente (0,0,0,0) anziché il nero opaco (0,0,0,1).

È ora possibile ottimizzare i valori alfa degli asset se si vuole, ma in genere non è necessario. Nella maggior parte dei casi, i mrc saranno sempre all'erta. MRC presuppone un valore alfa pre-moltiplicato. I valori alfa influiranno solo sull'acquisizione MRC.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>Cosa aspettarsi quando MRC è abilitato HoloLens

Quanto segue si applica a HoloLens (prima generazione) e HoloLens 2, se non diversamente specificato:

* Il sistema limitaterà l'applicazione al rendering a 30 Hz. Questo crea un po' di spazio per l'esecuzione di MRC in modo che l'app non deve mantenere una riserva di budget costante e corrisponda anche al framerate di record video MRC di 30 fps
* Il contenuto dell'ologramma nell'occhio destro del dispositivo può apparire "sparkle" durante la registrazione/streaming di MRC: il testo potrebbe diventare più difficile da leggere e i bordi dell'ologramma potrebbero apparire più incisivi (acconsentendo esplicitamente al rendering della terza fotocamera su HoloLens 2 evita questo **compromesso)**
* Le foto e i video MRC rispetteranno il punto di interesse dell'applicazione se l'applicazione l'ha abilitata, in modo da garantire un posizionamento accurato degli ologrammi. [](../unity/focus-point-in-unity.md) Per i video, il punto di messa a fuoco viene smussato in modo che gli ologrammi appaiano lentamente in posizione se la profondità del punto di messa a fuoco cambia in modo significativo. Ologrammi a profondità diverse dal punto di messa a fuoco possono apparire offset rispetto al mondo reale (vedere l'esempio seguente in cui il punto di messa a fuoco è impostato a 2 metri ma l'ologramma è posizionato a 1 metro).

![Ologrammi a 2 metri apparirà perfettamente registrato nel mondo. Ologrammi a distanze vicine o molto lunghe può essere leggermente compensato.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>Integrazione della funzionalità MRC dall'interno dell'app

L'app di realtà mista può avviare l'acquisizione di foto o video MRC dall'interno dell'app e il contenuto acquisito viene reso disponibile per l'app senza essere archiviato nel "rullino della fotocamera" del dispositivo. È possibile creare un registratore MRC personalizzato o sfruttare l'interfaccia utente incorporata per l'acquisizione della fotocamera. 

### <a name="mrc-with-built-in-camera-ui"></a>MRC con interfaccia utente della fotocamera incorporata

Gli sviluppatori possono usare *[l'API dell'interfaccia](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* utente acquisizione fotocamera per ottenere una foto o un video di realtà mista acquisita dall'utente con poche righe di codice.

Questa API avvia l'interfaccia utente della fotocamera MRC incorporata in cui gli utenti possono scattare una foto o un video e restituisce l'acquisizione risultante all'app. È possibile creare un registratore Acquisizione realtà mista personalizzato se è necessario aggiungere la propria interfaccia utente della fotocamera o l'accesso di livello inferiore per acquisire i flussi.

### <a name="creating-a-custom-mrc-recorder"></a>Creazione di un registratore MRC personalizzato

Anche se l'utente può sempre attivare una foto o un video usando il servizio di acquisizione MRC di sistema, un'applicazione potrebbe voler creare un'app fotocamera personalizzata che includa ologrammi nel flusso della fotocamera proprio come MRC. In questo modo l'applicazione può avviare le acquisizioni dall'input dell'utente, creare un'interfaccia utente di registrazione personalizzata o personalizzare le impostazioni MRC per citarne alcuni esempi.

**HoloStudio aggiunge una fotocamera MRC personalizzata usando gli effetti MRC**

![HoloStudio aggiunge una fotocamera MRC personalizzata usando gli effetti MRC](images/cameraiconholostudio-300px.jpg)

Unity Applications [dovrebbe](../unity/locatable-camera-in-unity.md) visualizzare Locatable_camera_in_Unity per la proprietà per abilitare gli ologrammi.

Altre applicazioni possono eseguire questa operazione usando le API di acquisizione multimediale [di Windows](/uwp/api/Windows.Media.Capture.MediaCapture) per controllare la fotocamera e aggiungere un effetto mrc video e audio per includere ologrammi virtuali e audio dell'applicazione in immagini e video.

Le applicazioni hanno due opzioni per aggiungere l'effetto:
* L'API precedente: [Windows. Media.Capture.MediaCapture.AddEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* La nuova API consigliata da Microsoft (restituisce un oggetto , che consente di modificare le proprietà dinamiche): [Windows. Media.Capture.MediaCapture.AddVideoEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [Windows. Media.Capture.MediaCapture.AddAudioEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) che richiedono all'app di creare la propria implementazione di [IVideoEffectDefinition](/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) e [IAudioEffectDefinition.](/uwp/api/windows.media.effects.iaudioeffectdefinition) Per [esempi, vedere l'app di esempio MRC.](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture)

>[!NOTE]
> Oggetto Windows. Lo spazio dei nomi Media.MixedRealityCapture non verrà riconosciuto Visual Studio, ma le stringhe sono ancora valide.

Effetto video MRC **(Windows. Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  Nome della proprietà  |  Tipo  |  Valore predefinito  |  Descrizione |
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  Descrivere il flusso di acquisizione per cui viene usato questo effetto. L'audio non è disponibile. |
|  HologramCompositionEnabled  |  boolean  |  true  |  Contrassegnare per abilitare o disabilitare gli ologrammi nell'acquisizione video. |
|  RecordingIndicatorEnabled  |  boolean  |  true  |  Flag per abilitare o disabilitare l'indicatore di registrazione sullo schermo durante l'acquisizione di ologrammi. |
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  Contrassegnare per abilitare o disabilitare la stabilizzazione video basata HoloLens tracker. |
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Impostare il numero di fotogrammi cronologici usati per la stabilizzazione video. 0 è 0-latenza e quasi "gratuito" dal punto di vista della potenza e delle prestazioni. 15 è consigliato per la massima qualità (al costo di 15 fotogrammi di latenza e memoria). |
|  GlobalOpacityCoefficient  |  float  |  0.9 (HoloLens) 1.0 (visore vr immersivo)  |  Impostare il coefficiente di opacità globale dell'ologramma compreso tra 0,0 (completamente trasparente) e 1,0 (completamente opaco). |
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  Flag per abilitare o disabilitare la restituzione di un frame vuoto se è presente un'app UWP 2d che mostra contenuto protetto. Se questo flag è false e un'app UWP 2d mostra contenuto protetto, l'app UWP 2d verrà sostituita da una trama di contenuto protetta sia nel visore che nell'acquisizione di realtà mista. |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  Contrassegna per abilitare o disabilitare la visualizzazione della mesh dell'area nascosta della fotocamera olografica e del contenuto adiacente. |
| OutputSize | Dimensione | 0, 0 | Impostare le dimensioni di output desiderate dopo il ritaglio per la stabilizzazione video. Se viene specificata una dimensione di output non valida o 0, viene scelta una dimensione di ritaglio predefinita. |
| PreferredHologramPerspective | UINT32 | **Eseguire il rendering dall'impostazione** fotocamera nel Windows Portale di dispositivi | Enumerazione usata per indicare la configurazione della visualizzazione olografica della fotocamera da acquisire: 0 (Display) indica che all'app non verrà richiesto di eseguire il rendering dalla fotocamera foto/video, 1 (PhotoVideoCamera) chiederà all'app di eseguire il rendering dalla fotocamera foto/video (se l'app la supporta). Supportato solo in HoloLens 2 |

>[!NOTE]
> È possibile modificare il valore predefinito **preferredHologramPerspective** nel Windows Portale di dispositivi [](using-the-windows-device-portal.md#mixed-reality-capture) selezionando la pagina Acquisizione realtà mista e deselezionando Rendering **dalla fotocamera**. L'impostazione predefinita **è 1 (PhotoVideoCamera),** ma può essere deselezionata per impostarla su **0 (Visualizzazione).**
>
> Il valore predefinito di **PreferredHologramPerspective** era **0 (Display)** prima dell'aggiornamento di giugno 2020 (Windows Holographic, versione 2004 build 19041.1106 e Windows Holographic, versione 1903 build 18362.1064).

Effetto audio MRC **(Windows. Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

| Nome della proprietà | Tipo | Valore predefinito | Descrizione |
|----------|----------|----------|----------|
| MixerMode | UINT32 | 2 (microfono e audio di sistema) | Enumerazione utilizzata per indicare le origini audio da usare: 0 (solo audio microfono), 1 (solo audio di sistema), 2 (microfono e audio di sistema) |
| LoopbackGain | float | **Impostazione di Guadagno audio** dell'app nel Windows Portale di dispositivi | Guadagno da applicare al volume audio di sistema. È compreso tra 0,0 e 5,0. Supportato solo in HoloLens 2 |
| MicrophoneGain | float | **Impostazione Mic Audio Gain** (Guadagno audio microfono) nel Windows Portale di dispositivi | Guadagno da applicare al volume del microfono. È compreso tra 0,0 e 5,0. Supportato solo in HoloLens 2 |

>[!NOTE]
> È possibile modificare il valore predefinito **di LoopbackGain** o **MicrophoneGain** nel Windows Portale di dispositivi selezionando la pagina [Acquisizione realtà mista](using-the-windows-device-portal.md#mixed-reality-capture) e regolando il dispositivo di scorrimento accanto alle rispettive impostazioni. Entrambe le impostazioni sono **impostate su 1.0,** ma possono essere impostate su qualsiasi valore compreso tra **0,0** **e 5,0.**
>
> L'uso di Windows Portale di dispositivi per configurare i valori di guadagno predefiniti è stato aggiunto con l'aggiornamento di giugno 2020 (Windows Holographic, versione 2004 build 19041.1106 e Windows Holographic, versione 1903 build 18362.1064).

### <a name="simultaneous-mrc-limitations"></a>Limitazioni simultanee di MRC

È necessario essere a conoscenza di alcune limitazioni quando più app accedono contemporaneamente a MRC.

#### <a name="photovideo-camera-access"></a>Accesso a foto/videocamera

Nella HoloLens 1, MRC non riuscirà ad acquisire una foto o acquisire video mentre un processo sta registrando un video o scattare una foto. È anche vero il contrario: se MRC è in esecuzione, l'applicazione non riuscirà ad accedere alla fotocamera. 

Con HoloLens 2, è possibile condividere l'accesso alla fotocamera. Se non è necessario il controllo diretto della risoluzione o della frequenza dei fotogrammi, puoi inizializzare MediaCapture usando la [proprietà SharedMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) con SharedReadOnly.  

##### <a name="built-in-mrc-photovideo-camera-access"></a>Accesso a foto/videocamera MRC incorporato

Funzionalità MRC integrate in Windows 10 (tramite Cortana, menu Start, collegamenti hardware, Miracast, Windows Portale di dispositivi):

* Verrà eseguito con ExclusiveControl per impostazione predefinita

È stato tuttavia aggiunto il supporto al sottosistema MRC per operare in modalità condivisa: 

* Se un'app richiede l'accesso ExclusiveControl alla fotocamera/videocamera, mrC incorporato smetterà automaticamente di usare la fotocamera/videocamera in modo che la richiesta dell'app avrà esito positivo 
* Se mrC incorporato viene avviato mentre un'app ha ExclusiveControl, mrC incorporato verrà eseguito in modalità SharedReadOnly 

Questa funzionalità in modalità condivisa presenta alcune restrizioni:

* Foto tramite Cortana, collegamenti hardware o menu Start: richiede l'aggiornamento Windows 10 aprile 2018 (o versione successiva)
* Video tramite Cortana, collegamenti hardware o menu Start: richiede l'aggiornamento Windows 10 aprile 2018 (o versione successiva)
* Streaming di MRC Miracast: richiede il Aggiornamento di Windows 10 (ottobre 2018) (o versione successiva)
* Streaming di MRC Windows Portale di dispositivi o tramite l'app complementare HoloLens: richiede HoloLens 2

>[!NOTE]
> La risoluzione e la frequenza dei fotogrammi dell'interfaccia utente della fotocamera MRC incorporata potrebbero essere ridotte dai valori normali quando un'altra app usa la fotocamera/videocamera.

#### <a name="mrc-access-for-developers"></a>Accesso mrc per sviluppatori

È consigliabile richiedere sempre il controllo esclusivo per la fotocamera quando si usa MRC. In questo modo l'applicazione avrà il controllo completo delle impostazioni per la fotocamera, purché si siano a conoscenza delle limitazioni elencate in precedenza. 

* Creare un oggetto Media Capture usando le impostazioni [di inizializzazione](/uwp/api/windows.media.capture.mediacaptureinitializationsettings?view=winrt-19041)
* Impostare la [proprietà SharingMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#Windows_Media_Capture_MediaCaptureInitializationSettings_SharingMode) su **exclusive**

> [!CAUTION]
> Prima di continuare, leggere attentamente [le osservazioni di SharingMode.](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#remarks)

* Configurare la fotocamera nel modo desiderato
* Avviare l'app, acquisire fotogrammi video con l'API start e quindi abilitare MRC

> [!CAUTION]
> Se si avvia MRC prima di avviare l'app, non è possibile garantire che la funzionalità funzioni come previsto.

È possibile trovare un esempio completo del processo precedente nell'esempio di rilevamento [viso olografico](/samples/microsoft/windows-universal-samples/holographicfacetracking).

> [!NOTE]
> Prima dell'aggiornamento Windows 10 aprile 2018, il registratore MRC personalizzato di un'app si escludono a vicenda con mrC di sistema (acquisizione di foto, acquisizione di video o streaming dal Windows Portale di dispositivi).

## <a name="see-also"></a>Vedere anche

* [Acquisizione in realtà mista (MRC, Mixed Reality Capture)](/hololens/holographic-photos-and-videos)
* [Visualizzazione spettatore](spectator-view.md)
* [Panoramica dello sviluppo in Unity](../unity/unity-development-overview.md)
* [Panoramica dello sviluppo con Unreal](../unreal/unreal-development-overview.md)
