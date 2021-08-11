---
title: Puntamento con la testa e sguardo fisso in DirectX
description: Informazioni su come richiedere, usare e decomprimere i dati di raycasting dallo sguardo fisso con la testa e dal tracciamento oculare nelle app DirectX native.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: sguardo fisso, sguardo con la testa, tracciamento della testa, tracciamento oculare, directx, input, ologrammi, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale
ms.openlocfilehash: 0e32c9f24b56d938b5c6f9cbdf28e9959b190abc22591a26d1dfcfa0af2f5f4d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193208"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a>Input con sguardo fisso e sguardo fisso in DirectX

> [!NOTE]
> Questo articolo è correlato alle API native WinRT legacy.  Per i nuovi progetti di app native, è consigliabile usare **[l'API OpenXR](openxr-getting-started.md)**.

In Windows Mixed Reality l'input dello sguardo fisso e della testa viene usato per determinare ciò che l'utente sta guardando. È possibile usare i dati per guidare i modelli di input principali, ad esempio il sguardo con la testa e [il commit,](../../design/gaze-and-commit.md)e fornire il contesto per tipi di interazione diversi. Esistono due tipi di vettori di sguardo fisso disponibili tramite l'API: sguardo con la testa e sguardo fisso.  Entrambi vengono forniti come raggio tridimensionale con un'origine e una direzione. Le applicazioni possono quindi eseguire il raycast nelle scene o nel mondo reale e determinare la destinazione dell'utente.

**Il puntato con** la testa rappresenta la direzione in cui punta la testa dell'utente. Si pensi al puntamento con la testa come alla posizione e alla direzione in avanti del dispositivo stesso, con la posizione come punto centrale tra i due schermi. Il sguardo con la testa è disponibile in tutti i dispositivi di realtà mista.

**Lo sguardo fisso** rappresenta la direzione verso cui gli occhi dell'utente guardano. L'origine si trova tra gli occhi dell'utente.  È disponibile nei dispositivi di realtà mista che includono un sistema di tracciamento oculare.

I raggi della testa e dello sguardo fisso sono accessibili tramite l'API [SpatialPointerPose.](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) Chiamare [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) per ricevere un nuovo oggetto SpatialPointerPose in corrispondenza del timestamp e del sistema [di coordinate specificati.](coordinate-systems-in-directx.md) Questo SpatialPointerPose contiene un'origine e una direzione di sguardo con la testa. Contiene anche un'origine e una direzione dello sguardo fisso se è disponibile il tracciamento oculare.

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
     <td>Sguardo fisso</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a>Uso dello sguardo fisso con la testa

Per accedere al sguardo fisso, iniziare chiamando  [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) per ricevere un nuovo oggetto SpatialPointerPose. Passare i parametri seguenti.
 - [SpatialCoordinateSystem che](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) rappresenta il sistema di coordinate desiderato per lo sguardo con la testa. È rappresentato dalla variabile *coordinateSystem* nel codice seguente. Per altre informazioni, vedere la guida per gli [sviluppatori dei sistemi](coordinate-systems-in-directx.md) di coordinate.
 - Timestamp [che](/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) rappresenta l'ora esatta della posizione della testa richiesta.  In genere, si usa un timestamp che corrisponde all'ora in cui verrà visualizzato il frame corrente. È possibile ottenere questo timestamp di visualizzazione previsto da un [oggetto HolographicFramePrediction,](/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) accessibile tramite l'oggetto [HolographicFrame corrente.](/uwp/api/windows.graphics.holographic.holographicframe)  Questo oggetto HolographicFramePrediction è rappresentato dalla variabile *di* stima nel codice seguente.

 Dopo aver creato un spatialPointerPose valido, la posizione della testa e la direzione in avanti sono accessibili come proprietà.  Il codice seguente illustra come accedervi.

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

## <a name="using-eye-gaze"></a>Uso dello sguardo fisso

Per consentire agli utenti di usare l'input dello [](/hololens/hololens-calibration) sguardo fisso, ogni utente deve eseguire una calibrazione dell'utente di tracciamento oculare la prima volta che usa il dispositivo. L'API sguardo fisso è simile al sguardo fisso con la testa.
Usa la stessa API [SpatialPointerPose,](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) che fornisce un'origine e una direzione del raggio che è possibile eseguire il raycast sulla scena.  L'unica differenza è che è necessario abilitare in modo esplicito il tracciamento oculare prima di usarlo:
1. Richiedere all'utente l'autorizzazione per usare il tracciamento oculare nell'app.
2. Abilitare la funzionalità "Input sguardo fisso" nel manifesto del pacchetto.

### <a name="requesting-access-to-eye-gaze-input"></a>Richiesta di accesso all'input dello sguardo fisso

Quando l'app si avvia, chiama [EyePose::RequestAccessAsync](/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) per richiedere l'accesso al tracciamento oculare. Il sistema chiederà all'utente se necessario e restituirà [GazeInputAccessStatus::Allowed](/uwp/api/windows.ui.input.gazeinputaccessstatus) dopo che l'accesso è stato concesso. Si tratta di una chiamata asincrona, quindi richiede un po' di gestione aggiuntiva. Nell'esempio seguente viene creato un std::thread scollegato per attendere il risultato, archiviato in una variabile membro *denominata m_isEyeTrackingEnabled*.

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
L'avvio di un thread disconnesso è solo un'opzione per la gestione delle chiamate asincrone. Puoi anche usare la [nuova](/windows/uwp/cpp-and-winrt-apis/concurrency) co_await funzionalità supportata da C++/WinRT.
Ecco un altro esempio di richiesta dell'autorizzazione utente:
-   EyePose::IsSupported() consente all'applicazione di attivare la finestra di dialogo di autorizzazione solo se è presente un tracciatore oculare.
-   GazeInputAccessStatus m_gazeInputAccessStatus; In questo modo si evita di visualizzare più volte la richiesta di autorizzazione.

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

### <a name="declaring-the-gaze-input-capability"></a>Dichiarazione della funzionalità *Di input sguardo* fisso

Fare doppio clic sul file appxmanifest in *Esplora soluzioni*.  Passare quindi alla sezione *Capabilities (Funzionalità)* e controllare la *funzionalità Gaze Input (Input* sguardo fisso). 

![Funzionalità di input sguardo fisso](images/gaze-input-capability.png)

Le righe seguenti vengono aggiunte *alla sezione Package* del file appxmanifest:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>Ottenere il raggio dello sguardo fisso

Dopo aver ricevuto l'accesso a ET, è possibile afferrare il raggio dello sguardo fisso per ogni fotogramma.
Come con lo sguardo fisso con la testa, ottenere [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) chiamando [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con un timestamp e un sistema di coordinate desiderati. SpatialPointerPose contiene un [oggetto EyesPose](/uwp/api/windows.perception.people.eyespose) tramite la [proprietà Eyes.](/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) Non è Null solo se è abilitato il tracciamento oculare. Da qui è possibile controllare se l'utente nel dispositivo ha una calibrazione del tracciamento oculare chiamando [EyePose::IsCalibrationValid.](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)  Usare quindi la proprietà [Gaze](/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) per ottenere [spatialRay](/uwp/api/windows.perception.spatial.spatialray) contenente la posizione e la direzione dello sguardo fisso. A volte la proprietà Sguardo fisso può essere null, quindi assicurarsi di verificare la presenza di questo valore. Ciò può verificarsi se un utente calibrato chiude temporaneamente gli occhi.

Il codice seguente illustra come accedere al raggio dello sguardo fisso.

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

## <a name="fallback-when-eye-tracking-isnt-available"></a>Fallback quando il tracciamento oculare non è disponibile

Come accennato nella [documentazione sulla](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available)progettazione del tracciamento oculare, sia i progettisti che gli sviluppatori devono essere a conoscenza delle istanze in cui i dati di tracciamento oculare potrebbero non essere disponibili.

Esistono diversi motivi per cui i dati non sono disponibili:
* Un utente non calibrato
* Un utente ha negato all'app l'accesso ai dati di tracciamento oculare
* Interferenze temporanee, ad esempio sbavature HoloLens visore o capello che oscludono gli occhi dell'utente. 

Anche se alcune DELLE API sono già state citate in questo documento, di seguito viene fornito un riepilogo di come rilevare che il tracciamento oculare è disponibile come riferimento rapido: 

* Verificare che il sistema supporti il tracciamento oculare. Chiamare il metodo *seguente:* [Windows. Perception.People.EyesPose.IsSupported()](/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* Verificare che l'utente sia calibrato. Chiamare la proprietà *seguente:* [Windows. Perception.People.EyesPose.IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)   

* Verificare che l'utente abbia assegnato all'app l'autorizzazione per usare i dati di tracciamento oculare: recuperare l'oggetto _'GazeInputAccessStatus' corrente._ Un esempio su come eseguire questa operazione è illustrato in Richiedere [l'accesso all'input dello sguardo fisso.](/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input) 

È anche possibile verificare che i dati di tracciamento oculare non sono obsoleti aggiungendo un timeout tra gli aggiornamenti dei dati di tracciamento oculare ricevuti e in caso contrario il fallback al sguardo con la testa, come illustrato di seguito.   
Per altre informazioni, vedere le considerazioni sulla progettazione del [fallback.](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available)

<br>

## <a name="correlating-gaze-with-other-inputs"></a>Correlazione dello sguardo fisso con altri input

In alcuni casi può essere necessario un [spatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) che corrisponde a un evento nel passato. Ad esempio, se l'utente esegue un'operazione Air Tap, l'app potrebbe voler sapere cosa stava guardando. A questo scopo, il semplice uso di [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con il tempo di frame previsto non sarebbe accurato a causa della latenza tra l'elaborazione dell'input di sistema e l'ora di visualizzazione. Inoltre, se si usa lo sguardo fisso per la destinazione, gli occhi tendono a procedere anche prima di completare un'azione di commit. Questo è meno un problema per un semplice tocco d'aria, ma diventa più importante quando si combinano comandi vocali lunghi con movimenti oculari rapidi. Un modo per gestire questo scenario consiste nell'effettuare una chiamata aggiuntiva a  [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)usando un timestamp cronologico corrispondente all'evento di input.  

Tuttavia, per l'input che viene instradato tramite SpatialInteractionManager, esiste un metodo più semplice. [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) ha la propria [funzione TryGetAtTimestamp.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) Chiamata di che fornirà un [spatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) perfettamente correlato senza indovinare. Per altre informazioni sull'uso di SpatialInteractionSourceStates, vedere mani e controller del movimento [nella documentazione di DirectX.](hands-and-motion-controllers-in-directx.md)

<br>

## <a name="calibration"></a>Calibrazione

Per un corretto funzionamento del tracciamento oculare, ogni utente deve eseguire una calibrazione [dell'utente di tracciamento oculare.](/hololens/hololens-calibration) In questo modo il dispositivo può regolare il sistema per un'esperienza di visualizzazione più comoda e di qualità superiore per l'utente e per garantire contemporaneamente un tracciamento oculare accurato. Gli sviluppatori non devono eseguire alcun'operazione per gestire la calibrazione dell'utente. Il sistema garantisce che all'utente venga richiesto di calibrare il dispositivo nelle circostanze seguenti:
* L'utente usa il dispositivo per la prima volta
* L'utente ha precedentemente rifiutato esplicitamente il processo di calibrazione
* Il processo di calibrazione non è riuscito l'ultima volta che l'utente ha usato il dispositivo

Gli sviluppatori devono assicurarsi di fornire un supporto adeguato agli utenti in cui i dati di tracciamento oculare potrebbero non essere disponibili. Per altre informazioni sulle considerazioni per le soluzioni di fallback, vedere [Tracciamento oculare HoloLens 2](../../design/eye-tracking.md).

<br>

## <a name="see-also"></a>Vedi anche

* [Calibrazione](/hololens/hololens-calibration)
* [Sistemi di coordinate in DirectX](coordinate-systems-in-directx.md)
* [Sguardo fisso su HoloLens 2](../../design/eye-tracking.md)
* [Modello di input sguardo fisso e commit](../../design/gaze-and-commit.md)
* [Mani e controller del movimento in DirectX](hands-and-motion-controllers-in-directx.md)
* [Input vocale in DirectX](voice-input-in-directx.md)