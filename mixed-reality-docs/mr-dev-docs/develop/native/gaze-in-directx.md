---
title: Puntamento con la testa e sguardo fisso in DirectX
description: Informazioni su come richiedere, usare e decomprimere i dati di Raycasting da sguardi e rilevamento degli occhi nelle app DirectX native.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: occhi, sguardi, Head-sguardi, tracking, tracking, Eye Tracking, DirectX, input, ologrammi, cuffie per realtà mista, cuffie per la realtà mista di Windows, cuffie per realtà virtuale
ms.openlocfilehash: 8b3c63ac7a7edba0ce3173e024139e29d49757ab
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810171"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a>Input occhi e sguardi in DirectX

> [!NOTE]
> Questo articolo si riferisce alle API native di WinRT legacy.  Per i nuovi progetti di app native, è consigliabile usare l' **[API OpenXR](openxr-getting-started.md)**.

Per quanto riguarda la realtà mista di Windows, viene usato l'input occhi e occhio per determinare l'aspetto dell'utente. È possibile usare i dati per guidare i modelli di input primari come [Head-sguardi e commit](../../design/gaze-and-commit.md)e fornire il contesto per diversi tipi di interazione. Esistono due tipi di vettori di sguardi disponibili tramite l'API, ovvero Head-sguardi e sguardo.  Entrambi sono forniti come un raggio tridimensionale con un'origine e una direzione. Le applicazioni possono quindi Raycast nelle proprie scene, o nel mondo reale, e determinare le operazioni di destinazione dell'utente.

**Head-sguardi** rappresenta la direzione a cui è puntata la testa dell'utente. Si pensi a un punto di fronte come la posizione e la direzione di avanzamento del dispositivo stesso, con la posizione come punto centrale tra le due visualizzazioni. Head-sguardi è disponibile in tutti i dispositivi a realtà mista.

**Eye-sguardi** rappresenta la direzione verso la quale gli occhi dell'utente stanno cercando. L'origine si trova tra gli occhi dell'utente.  È disponibile nei dispositivi a realtà mista che includono un sistema di rilevamento degli occhi.

I raggi Head e sguardi sono accessibili tramite l'API  [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) . Chiamare [SpatialPointerPose:: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) per ricevere un nuovo oggetto SpatialPointerPose in corrispondenza del timestamp e del [sistema di coordinate](coordinate-systems-in-directx.md)specificati. Questo SpatialPointerPose contiene un'origine e una direzione per lo sguardo del capo. Contiene anche un'origine e una direzione degli sguardi se è disponibile la verifica degli occhi.

### <a name="device-support"></a>Supporto di dispositivi

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Funzionalità</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
</tr>
<tr>
     <td>Puntamento con la testa</td>
     <td>✔️</td>
     <td>✔️</td>
     <td>✔️</td>
</tr>
<tr>
     <td>Sguardo attento</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a>Uso di Head-sguardi

Per accedere all'Head-sguardi, iniziare chiamando  [SpatialPointerPose:: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) per ricevere un nuovo oggetto SpatialPointerPose. Passare i parametri seguenti.
 - Oggetto [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) che rappresenta il sistema di coordinate desiderato per lo sguardo inverso. Questa operazione è rappresentata dalla variabile *coordinateSystem* nel codice riportato di seguito. Per ulteriori informazioni, visitare la guida per gli sviluppatori di [sistemi di coordinate](coordinate-systems-in-directx.md) .
 - [Timestamp](/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) che rappresenta l'ora esatta della richiesta Head.  In genere, verrà utilizzato un timestamp corrispondente all'ora di visualizzazione del frame corrente. È possibile ottenere questo timestamp di visualizzazione stimato da un oggetto  [HolographicFramePrediction](/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , accessibile tramite il [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe)corrente.  Questo oggetto HolographicFramePrediction è rappresentato dalla variabile di *stima* nel codice riportato di seguito.

 Quando si dispone di un SpatialPointerPose valido, la posizione della testa e la direzione di avanzamento sono accessibili come proprietà.  Nel codice seguente viene illustrato come accedervi.

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a>Uso degli sguardi

Per consentire agli utenti di usare l'input con sguardo oculare, ogni utente deve esaminare la [calibrazione degli utenti](/hololens/hololens-calibration) per la prima volta che usano il dispositivo. L'API Eye-sguardi è simile a Head-sguardi.
Usa la stessa API [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , che fornisce un'origine e una direzione del raggio che è possibile Raycast per la scena.  L'unica differenza è che è necessario abilitare in modo esplicito la verifica degli occhi prima di usarla:
1. Richiedere all'utente l'autorizzazione per usare il rilevamento degli occhi nell'app.
2. Abilitare la funzionalità di "input dello sguardo" nel manifesto del pacchetto.

### <a name="requesting-access-to-eye-gaze-input"></a>Richiesta di accesso a Eye-sguardi input

All'avvio dell'app, chiamare [EyesPose:: RequestAccessAsync](/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) per richiedere l'accesso al rilevamento degli occhi. Se necessario, il sistema richiede all'utente e restituisce [GazeInputAccessStatus:: allowed](/uwp/api/windows.ui.input.gazeinputaccessstatus) dopo che è stato concesso l'accesso. Si tratta di una chiamata asincrona, quindi richiede un po' di gestione aggiuntiva. Nell'esempio seguente viene avviata un'operazione std:: thread scollegata per attendere il risultato, che viene archiviato in una variabile membro denominata *m_isEyeTrackingEnabled*.

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
L'avvio di un thread scollegato è solo un'opzione per la gestione delle chiamate asincrone. È anche possibile usare la nuova funzionalità di [co_await](/windows/uwp/cpp-and-winrt-apis/concurrency) supportata da C++/WinRT.
Ecco un altro esempio per richiedere l'autorizzazione utente:
-   EyesPose:: supporto () consente all'applicazione di attivare la finestra di dialogo di autorizzazione solo se è presente uno strumento di rilevamento.
-   GazeInputAccessStatus m_gazeInputAccessStatus; In questo modo si evita di riscattare il prompt delle autorizzazioni più volte.

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```

### <a name="declaring-the-gaze-input-capability"></a>Dichiarazione della funzionalità di *input di sguardi*

Fare doppio clic sul file appxmanifest in *Esplora soluzioni*.  Passare quindi alla sezione *funzionalità* e controllare la funzionalità di *input di sguardi* . 

![Funzionalità di input di sguardi](images/gaze-input-capability.png)

Vengono aggiunte le righe seguenti alla sezione del *pacchetto* nel file appxmanifest:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>Ottenere il raggio d'occhio

Dopo aver ricevuto l'accesso a ET, è possibile cogliere il raggio d'occhio per ogni fotogramma.
Come per l'Head-sguardi, ottenere il [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) chiamando [SpatialPointerPose:: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con un timestamp e un sistema di coordinate desiderati. SpatialPointerPose contiene un oggetto [EyesPose](/uwp/api/windows.perception.people.eyespose) tramite la proprietà [Eyes](/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) . Questo valore non è null solo se è abilitata la funzionalità Eye Tracking. Da qui è possibile verificare se l'utente nel dispositivo ha una calibrazione per il rilevamento degli occhi chiamando [EyesPose:: IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).  Usare quindi la proprietà [sguardi](/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) per ottenere [SpatialRay](/uwp/api/windows.perception.spatial.spatialray) che contiene la posizione e la direzione degli sguardi. La proprietà sguardi può talvolta essere null, quindi assicurarsi di controllarla. Questo problema può verificarsi se un utente calibrato chiude temporaneamente gli occhi.

Il codice seguente illustra come accedere al raggio d'occhio.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-isnt-available"></a>Fallback quando il rilevamento degli occhi non è disponibile

Come indicato nella documentazione di progettazione per il [monitoraggio degli occhi](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available), sia le finestre di progettazione che gli sviluppatori devono tenere presenti le istanze in cui i dati di rilevamento degli occhi potrebbero non essere disponibili.

I dati non sono disponibili per diversi motivi:
* Un utente che non è stato calibrato
* Un utente ha negato l'accesso dell'app ai dati di rilevamento degli occhi
* Interferenze temporanee, ad esempio le sbavature sulla visiera HoloLens o sui capelli occlusione gli occhi dell'utente. 

Sebbene alcune API siano già state citate in questo documento, di seguito viene fornito un riepilogo su come rilevare che il rilevamento degli occhi è disponibile come riferimento rapido: 

* Verificare che il sistema supporti la verifica degli occhi. Chiamare il *Metodo* seguente: [Windows. Perception. people. EyesPose. IsValid ()](/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* Verificare che l'utente sia calibrato. Chiamare la *Proprietà* seguente: [Windows. Perception. people. EyesPose. IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)   

* Verificare che l'utente abbia specificato l'autorizzazione dell'app per usare i dati di rilevamento degli occhi: recuperare il _' GazeInputAccessStatus '_ corrente. Un esempio di come eseguire questa operazione è illustrato nella pagina relativa alla [richiesta di accesso a sguardi input](/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input). 

È anche possibile verificare che i dati di rilevamento degli occhi non siano obsoleti aggiungendo un timeout tra gli aggiornamenti dei dati di rilevamento degli occhi ricevuti e altrimenti il fallback a Head-sguardi, come descritto di seguito.   
Per ulteriori informazioni, vedere le [considerazioni sulla progettazione di fallback](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available) .

<br>

## <a name="correlating-gaze-with-other-inputs"></a>Correlazione di sguardi con altri input

In alcuni casi potrebbe essere necessario un [SpatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) che corrisponda a un evento nel passato. Ad esempio, se l'utente esegue una scelta aerea, l'app potrebbe voler sapere cosa stavano cercando. A questo scopo, l'uso di [SpatialPointerPose:: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con il tempo previsto per i frame potrebbe non essere accurato a causa della latenza tra l'elaborazione dell'input di sistema e l'ora di visualizzazione. Inoltre, se si usa il controllo degli sguardi per la destinazione, gli occhi tendono a proseguire anche prima di terminare un'azione di commit. Si tratta di un problema minore per un semplice tocco, ma diventa più importante quando si combinano i comandi Long Voice con rapidi movimenti oculari. Un modo per gestire questo scenario è eseguire un'ulteriore chiamata a  [SpatialPointerPose:: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), usando un timestamp cronologico corrispondente all'evento di input.  

Tuttavia, per l'input che viene indirizzato attraverso SpatialInteractionManager, è disponibile un metodo più semplice. [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) dispone di una propria funzione [TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) . Chiamando che fornirà un [SpatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) perfettamente correlato senza le congetture. Per altre informazioni sull'uso di SpatialInteractionSourceStates, vedere la documentazione su [hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) .

<br>

## <a name="calibration"></a>Calibrazione

Per il corretto funzionamento dell'analisi degli occhi, è necessario che ogni utente debba esaminare la [calibrazione degli utenti](/hololens/hololens-calibration). In questo modo, il dispositivo può modificare il sistema per un'esperienza di visualizzazione più comoda e di qualità superiore per l'utente e garantire il rilevamento accurato degli occhi allo stesso tempo. Gli sviluppatori non devono eseguire alcuna operazione al termine della gestione della calibrazione degli utenti. Il sistema garantisce che all'utente venga richiesto di calibrare il dispositivo nei casi seguenti:
* L'utente sta usando il dispositivo per la prima volta
* L'utente ha rifiutato in precedenza il processo di calibrazione
* Il processo di calibrazione non ha avuto esito positivo l'ultima volta in cui l'utente ha usato il dispositivo

Gli sviluppatori devono garantire un supporto adeguato per gli utenti in cui i dati di rilevamento degli occhi potrebbero non essere disponibili. Per altre informazioni sulle soluzioni di fallback, vedere [Eye tracking on HoloLens 2](../../design/eye-tracking.md).

<br>

## <a name="see-also"></a>Vedi anche

* [Calibrazione](/hololens/hololens-calibration)
* [Sistemi di coordinate in DirectX](coordinate-systems-in-directx.md)
* [Eye-sguardi su HoloLens 2](../../design/eye-tracking.md)
* [Modello di input sguardo e commit](../../design/gaze-and-commit.md)
* [Mani e controller del movimento in DirectX](hands-and-motion-controllers-in-directx.md)
* [Input vocale in DirectX](voice-input-in-directx.md)