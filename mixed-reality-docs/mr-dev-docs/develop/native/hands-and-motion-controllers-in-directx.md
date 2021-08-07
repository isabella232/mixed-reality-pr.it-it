---
title: Mani e controller del movimento in DirectX
description: Introduzione alla guida per gli sviluppatori per l'uso del tracciamento delle mani e dei controller del movimento nelle app DirectX native.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: mani, controller del movimento, directx, input, ologrammi, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale
ms.openlocfilehash: 13988df80052ef85662dcf9834406baa91d48f7c0b70242d1c904548c2707105
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210958"
---
# <a name="hands-and-motion-controllers-in-directx"></a>Mani e controller del movimento in DirectX

> [!NOTE]
> Questo articolo è correlato alle API native WinRT legacy.  Per i nuovi progetti di app native, è consigliabile usare **[l'API OpenXR](openxr-getting-started.md)**.

In Windows Mixed Reality l'input della mano e del [controller](../../design/motion-controllers.md) del movimento viene gestito tramite le API di input spaziale, disponibili nella [Windows. Ui. Spazio dei nomi Input.Spatial.](/uwp/api/windows.ui.input.spatial) In questo modo è possibile gestire facilmente azioni comuni come le presse **Select** nello stesso modo in entrambe le mani e nei controller del movimento.

## <a name="getting-started"></a>Guida introduttiva

Per accedere all'input spaziale Windows Mixed Reality, iniziare con l'interfaccia SpatialInteractionManager.  È possibile accedere a questa interfaccia chiamando  [SpatialInteractionManager::GetForCurrentView,](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview)in genere durante l'avvio dell'app.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

Il compito di SpatialInteractionManager è fornire l'accesso a [SpatialInteractionSources,](/uwp/api/windows.ui.input.spatial.spatialinteractionsource)che rappresentano un'origine di input.  Nel sistema sono disponibili tre tipi di SpatialInteractionSources.
* **Hand** rappresenta la mano rilevata di un utente. Le origini delle mani offrono diverse funzionalità in base al dispositivo, dai movimenti di base HoloLens al tracciamento della mano completamente articolato HoloLens 2. 
* **Il controller** rappresenta un controller del movimento associato. I controller del movimento possono offrire diverse funzionalità, ad esempio Seleziona trigger, Pulsanti di menu, Pulsanti di afferramento, touchpad e levette.
* **La** voce rappresenta le parole chiave rilevate dal sistema per la voce dell'utente. Ad esempio, questa origine inserirà una press and release Select ogni volta che l'utente dice "Seleziona".

I dati per frame per un'origine sono rappresentati [dall'interfaccia SpatialInteractionSourceState.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) Esistono due modi diversi per accedere a questi dati, a seconda che si voglia usare un modello basato su eventi o basato sul polling nell'applicazione.

### <a name="event-driven-input"></a>Input basato su eventi
SpatialInteractionManager fornisce una serie di eventi che l'app può ascoltare.  Alcuni esempi includono   [SourcePressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased e [SourceUpdated](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated).

Ad esempio, il codice seguente collega un gestore eventi denominato MyApp::OnSourcePressed all'evento SourcePressed.  Ciò consente all'app di rilevare le presse su qualsiasi tipo di origine di interazione.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

Questo evento premuto viene inviato all'app in modo asincrono, insieme all'oggetto SpatialInteractionSourceState corrispondente al momento della pressione. È possibile che l'app o il motore di gioco voglia avviare immediatamente l'elaborazione o accodare i dati dell'evento nella routine di elaborazione dell'input. Ecco una funzione del gestore eventi per l'evento SourcePressed, che controlla se il pulsante di selezione è stato premuto.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

Il codice precedente controlla solo la pressione "Seleziona", che corrisponde all'azione principale nel dispositivo. Gli esempi includono l'esecuzione di un AirTap HoloLens o il pull del trigger in un controller del movimento.  Le presse "Seleziona" rappresentano l'intenzione dell'utente di attivare l'ologramma di destinazione.  L'evento SourcePressed verrà generato per diversi pulsanti e movimenti ed è possibile esaminare altre proprietà in SpatialInteractionSource per testare tali casi.

### <a name="polling-based-input"></a>Input basato sul polling
È anche possibile usare SpatialInteractionManager per eseguire il polling dello stato corrente di input per ogni frame.  A tale scopo, chiamare [GetDetectedSourcesAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) ogni frame.  Questa funzione restituisce una matrice contenente [un oggetto SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) per ogni [spatialInteractionSource attivo.](/uwp/api/windows.ui.input.spatial.spatialinteractionsource) Ciò significa che uno per ogni controller del movimento attivo, uno per ogni mano tracciata e uno per il parlato se di recente è stato pronunciato un comando "select". È quindi possibile esaminare le proprietà in ogni SpatialInteractionSourceState per guidare l'input nell'applicazione. 

Di seguito è riportato un esempio di come verificare l'azione 'select' usando il metodo di polling. La *variabile* di stima rappresenta [un oggetto HolographicFramePrediction,](/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) che può essere ottenuto da [HolographicFrame.](/uwp/api/windows.graphics.holographic.holographicframe)

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

Ogni SpatialInteractionSource ha un ID, che è possibile usare per identificare nuove origini e correlare le origini esistenti da un frame all'altro.  Le mani ottengono un nuovo ID ogni volta che lasciano l'applicazione e entrano nella fov, ma gli ID controller rimangono statici per la durata della sessione.  È possibile usare gli eventi in SpatialInteractionManager, ad esempio [SourceDetected](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) e [SourceLost,](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost)per reagire quando le mani entrano o lasciano la visualizzazione del dispositivo o quando i controller del movimento sono attivati/disattivati o associati/non abbinati.

### <a name="predicted-vs-historical-poses"></a>Posizione stimata e cronologica
GetDetectedSourcesAtTimestamp ha un parametro timestamp. In questo modo è possibile richiedere lo stato e inserire dati stimati o cronologici, consentendo di correlare le interazioni spaziali con altre origini di input. Ad esempio, quando si esegue il rendering della posizione della mano nel frame corrente, è possibile passare il timestamp previsto fornito da [HolographicFrame.](/uwp/api/windows.graphics.holographic.holographicframe) In questo modo il sistema può prevedere in avanti la posizione della mano per allinearsi con l'output del frame sottoposto a rendering, riducendo al minimo la latenza percepita.

Tuttavia, tale posizione stimata non produce un raggio di puntamento ideale per la destinazione con un'origine di interazione. Ad esempio, quando viene premuto un pulsante del controller del movimento, possono essere necessario fino a 20 ms prima che l'evento si invii attraverso Bluetooth al sistema operativo. Analogamente, dopo che un utente ha eseguito un movimento della mano, può passare un certo periodo di tempo prima che il sistema rilevi il movimento e che l'app ne esezioni il polling. Quando l'app esegue il polling per una modifica dello stato, le posizioni della testa e della mano usate per impostare come destinazione l'interazione si è effettivamente verificato in passato. Se la destinazione è passare il timestamp di HolographicFrame corrente a GetDetectedSourcesAtTimestamp, la posizione verrà invece stimata in avanti al raggio di destinazione nel momento in cui verrà visualizzato il fotogramma, che potrebbe essere superiore a 20 ms in futuro. Questa posizione futura è buona per il *rendering* dell'origine di interazione, ma costituisce un problema di tempo per l'interazione come destinazione, perché la destinazione dell'utente si è verificata in passato. 

Fortunatamente, gli [eventi SourcePressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased e [SourceUpdated](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) forniscono lo stato cronologico [associato](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) a ogni evento di input.  Include direttamente le posizioni cronologiche della testa e della mano disponibili tramite [TryGetPointerPose,](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)insieme a un [timestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) cronologico che è possibile passare ad altre API per la correlazione con questo evento.

Ciò comporta le procedure consigliate seguenti quando si esegue il rendering e la destinazione con mani e controller per ogni fotogramma:
* Per **il rendering manuale/controller** di ogni fotogramma, l'app deve eseguire il **polling** della **posizione** stimata in avanti di ogni origine di interazione al momento della foto del fotogramma corrente.  È possibile eseguire il polling di tutte le origini di interazione chiamando [GetDetectedSourcesAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) per ogni frame, passando il timestamp previsto fornito da [HolographicFrame::CurrentPrediction.](/uwp/api/windows.graphics.holographic.holographicframe.currentprediction)
* Per la selezione della mano **o del controller** in base a una pressione o  a un rilascio, l'app deve gestire gli eventi premuti/rilasciati, il raycasting in base alla posizione cronologica della testa o della mano per l'evento.  Per ottenere questo raggio di destinazione, puoi gestire l'evento [SourcePressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) o [SourceReleased,](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) ottenere la proprietà [State](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) dagli argomenti dell'evento e quindi chiamare il relativo metodo [TryGetPointerPose.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)

## <a name="cross-device-input-properties"></a>Proprietà di input tra dispositivi
L'API SpatialInteractionSource supporta controller e sistemi di tracciamento delle mani con un'ampia gamma di funzionalità. Alcune di queste funzionalità sono comuni tra i tipi di dispositivo. Ad esempio, il tracciamento delle mani e i controller del movimento forniscono un'azione di selezione e una posizione 3D. Laddove possibile, l'API esegue il mapping di queste funzionalità comuni alle stesse proprietà in SpatialInteractionSource.  In questo modo le applicazioni possono supportare più facilmente un'ampia gamma di tipi di input. Nella tabella seguente vengono descritte le proprietà supportate e il modo in cui vengono confrontate tra i tipi di input.

| Proprietà | Descrizione | HoloLens (prima generazione) | Controller del movimento | Mani articolate|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**Handedness**](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | Mano destra o sinistra/controller. | Non supportato | Supportato | Supportato |
| [SpatialInteractionSourceState::**IsSelectPressed**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | Stato corrente del pulsante primario. | Air Tap | Trigger | Tocco d'aria relaxed (dita verso l'alto) |
| [SpatialInteractionSourceState::**IsGrasped**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | Stato corrente del pulsante di cattura. | Non supportato | Pulsante Afferra | Avvicinamento delle dita o mano chiusa |
| [SpatialInteractionSourceState::**IsMenuPressed**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | Stato corrente del pulsante di menu.    | Non supportato | Pulsante di menu | Non supportato |
| [SpatialInteractionSourceLocation::**Position**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | Posizione XYZ della mano o della posizione del controllo sul controller. | Posizione palmo | Posizione della posizione del controllo | Posizione palmo |
| [SpatialInteractionSourceLocation::**Orientation**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | Quaternione che rappresenta l'orientamento della mano o della posizione del controllo sul controller. | Non supportato | Orientamento della posizione del controllo | Orientamento del palmo |
| [SpatialPointerInteractionSourcePose::**Position**](/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | Origine del raggio di puntamento. | Non supportato | Supportato | Supportato |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | Direzione del raggio di puntamento. | Non supportato | Supportato | Supportato |

Alcune delle proprietà precedenti non sono disponibili in tutti i dispositivi e l'API fornisce un modo per eseguire il test. Ad esempio, è possibile esaminare la [proprietà SpatialInteractionSource::IsGraspSupported](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) per determinare se l'origine fornisce un'azione di controllo.

### <a name="grip-pose-vs-pointing-pose"></a>Posizione del mantenimento e posizione di puntamento

Windows Mixed Reality supporta i controller del movimento in fattori di forma diversi.  Supporta anche sistemi di tracciamento delle mani articolati.  Tutti questi sistemi hanno relazioni diverse tra la posizione della mano e la direzione "in avanti" naturale che le app devono usare per puntare o eseguire il rendering degli oggetti nella mano dell'utente.  Per supportare tutto questo, sono disponibili due tipi di posizioni 3D per il tracciamento delle mani e i controller del movimento.  Il primo è la posizione del controllo, che rappresenta la posizione della mano dell'utente.  Il secondo è la posizione di puntamento, che rappresenta un raggio di puntamento proveniente dalla mano o dal controller dell'utente. Pertanto, se si vuole eseguire il rendering della mano **dell'utente** o di un oggetto mantenuto nella mano **dell'utente,** ad esempio una mano, usare la posizione del perno. Se si vuole eseguire il raycast dal controller o dalla mano, ad esempio quando l'utente punta **verso l'interfaccia utente, usare la posizione di puntamento.

È possibile accedere alla **posizione del controllo** tramite [SpatialInteractionSourceState::P roperties::TryGetLocation(...)](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_). Viene definito come segue:
* Posizione **del riquadro:** centroide del palmo quando si tiene il controller in modo naturale, regolato a sinistra o a destra per centrare la posizione all'interno del riquadro.
* Asse destro **dell'orientamento** del riquadro: quando si apre completamente la mano per formare una posizione piana a 5 dita, il raggio normale al palmo (in avanti dal palmo sinistro, all'indietro dal palmo destro)
* Asse avanti **dell'orientamento** del controllo: quando si chiude parzialmente la mano (come se si tiene il controller), il raggio che punta "in avanti" attraverso il raggio formato dalle dita non del pollice.
* Asse **su dell'orientamento del** riquadro: asse verso l'alto implicito dalle definizioni Right e Forward.

È possibile accedere alla **posizione** del puntatore tramite [SpatialInteractionSourceState::P roperties::TryGetLocation(...)::SourcePointerPose](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) o [SpatialInteractionSourceState::TryGetPointerPose(...)::TryGetInteractionSourcePose.](/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)

## <a name="controller-specific-input-properties"></a>Proprietà di input specifiche del controller
Per i controller, SpatialInteractionSource ha una proprietà Controller con funzionalità aggiuntive.
* **HasThumbstick:** Se true, il controller ha una levetta. Esaminare la proprietà [ControllerProperties](/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) di SpatialInteractionSourceState per acquisire i valori x e y della levetta (ThumbstickX e ThumbstickY), nonché lo stato premuto (IsThumbstickPressed).
* **HasTouchpad:** Se true, il controller ha un touchpad. Esaminare la proprietà ControllerProperties di SpatialInteractionSourceState per acquisire i valori x e y del touchpad (TouchpadX e TouchpadY) e per sapere se l'utente tocca il pad (IsTouchpadTouched) e se preme il touchpad verso il basso (IsTouchpadPressed).
* **SimpleHapticsController:** L'API SimpleHapticsController per il controller consente di controllare le funzionalità aptiche del controller e di controllare il feedback attico.

L'intervallo per il touchpad e la levetta è compreso tra -1 e 1 per entrambi gli assi (dal basso verso l'alto e da sinistra a destra). L'intervallo per il trigger analogo, a cui si accede tramite la proprietà SpatialInteractionSourceState::SelectPressedValue, è compreso tra 0 e 1. Il valore 1 è correlato al fatto che IsSelectPressed è uguale a true; qualsiasi altro valore è correlato al fatto che IsSelectPressed è uguale a false.

## <a name="articulated-hand-tracking"></a>Tracciamento delle mani articolato
L Windows Mixed Reality API offre supporto completo per il tracciamento delle mani articolato, ad esempio in HoloLens 2. Il tracciamento delle mani articolato può essere usato per implementare modelli di input di manipolazione diretta e point-and-commit nelle applicazioni. Può essere usato anche per creare interazioni completamente personalizzate.

### <a name="hand-skeleton"></a>Scheletro della mano
Il tracciamento delle mani articolato fornisce uno scheletro di 25 giunzioni che consente molti tipi diversi di interazioni.  Lo scheletro fornisce cinque giunzioni per l'indice/centrale/anello/piccole dita, quattro giunzioni per il pollice e una giunzione del pollice.  Il giunzione di giunzione funge da base della gerarchia. L'immagine seguente illustra il layout dello scheletro.

![Scheletro della mano](images/hand-skeleton.png)

Nella maggior parte dei casi, ogni giunzione viene denominata in base all'elemento rappresentato.  Poiché sono presenti due animali in ogni giunzione, viene utilizzata una convenzione per denominare ogni giunzione in base al figlio in quella posizione.  L'elemento figlio è definito come l'elemento più lontano dal collo.  Ad esempio, il giunzione "Index Proximal" contiene la posizione iniziale dell'indice proximal e l'orientamento di tale vertice.  Non contiene la posizione finale dell'oggetto .  Se necessario, è possibile ottenerlo dal successivo giunzione della gerarchia, il congiunto "Index Intermediate".

Oltre ai 25 giunzioni gerarchiche, il sistema fornisce un giunzione di palmo.  Il palmo non è in genere considerato parte della struttura dello scheletro. Viene fornito solo come un modo pratico per ottenere la posizione e l'orientamento complessivi della mano.

Per ogni giunzione vengono fornite le informazioni seguenti:

| Nome | Descrizione |
|--- |--- |
|Posizione | Posizione 3D del giunzione, disponibile in qualsiasi sistema di coordinate richiesto. |
|Orientamento | Orientamento 3D dell'oggetto , disponibile in qualsiasi sistema di coordinate richiesto. |
|Radius | Distanza dalla superficie dell'interfaccia in corrispondenza della posizione congiunta. Utile per l'ottimizzazione di interazioni dirette o visualizzazioni che si basano sulla larghezza del dito. |
|Accuratezza | Fornisce un suggerimento sul modo in cui il sistema è sicuro delle informazioni di questo comune. |

È possibile accedere alla struttura della mano tramite una funzione in [SpatialInteractionSourceState.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)  La funzione è denominata [TryGetHandPose](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)e restituisce un oggetto [denominato HandPose.](/uwp/api/windows.perception.people.handpose)  Se l'origine non supporta le mani articolate, questa funzione restituirà Null.  Dopo aver creato un handPose, è possibile ottenere i dati congiunti correnti chiamando [TryGetJoint](/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__), con il nome del congiunto a cui si è interessati.  I dati vengono restituiti come [struttura JointPose.](/uwp/api/windows.perception.people.jointpose)  Il codice seguente ottiene la posizione della punta del dito indice. La variabile *currentState* rappresenta un'istanza [di SpatialInteractionSourceState.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>Mesh mano

L'API di tracciamento delle mani articolata consente una mesh a forma di mano triangolare completamente triangolare.  Questa mesh può essere in tempo reale insieme alla struttura della mano ed è utile per la visualizzazione e le tecniche di fisica avanzata.  Per accedere alla mesh manuale, è prima necessario creare un oggetto [HandMeshObserver](/uwp/api/windows.perception.people.handmeshobserver) chiamando [TryCreateHandMeshObserverAsync](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) in [SpatialInteractionSource.](/uwp/api/windows.ui.input.spatial.spatialinteractionsource)  Questa operazione deve essere eseguita una sola volta per ogni origine, in genere la prima volta che viene visualizzata.  Ciò significa che questa funzione verrà chiamata per creare un oggetto HandMeshObserver ogni volta che una mano entra nella fov.  Si tratta di una funzione asincrona, quindi in questo caso è necessario gestire un po' di concorrenza.  Una volta disponibile, è possibile chiedere all'oggetto HandMeshObserver l'index buffer triangolo chiamando [GetTriangleIndices.](/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___)  Gli indici non cambiano frame nel frame, quindi è possibile ottenerli una sola volta e memorizzarli nella cache per la durata dell'origine.  Gli indici vengono forniti in ordine di vento in senso orario.

Il codice seguente crea un oggetto std::thread scollegato per creare l'osservatore mesh ed estrae il index buffer quando l'osservatore mesh è disponibile.  Inizia da una variabile denominata *currentState*, che è un'istanza di [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) che rappresenta una mano rilevata.

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
L'avvio di un thread disconnesso è solo un'opzione per la gestione delle chiamate asincrone.  In alternativa, è possibile usare la nuova [co_await](/windows/uwp/cpp-and-winrt-apis/concurrency) supportata da C++/WinRT.

Dopo aver creato un oggetto HandMeshObserver, è necessario mantenere attivo l'oggetto SpatialInteractionSource corrispondente per la durata.  A questo punto, è possibile richiedere il buffer dei vertici più recente che rappresenta la mano chiamando [GetVertexStateForPose e](/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) passando un'istanza [handPose](/uwp/api/windows.perception.people.handpose) che rappresenta la posizione per cui si vogliono ottenere i vertici.  Ogni vertice nel buffer ha una posizione e una normale.  Ecco un esempio di come ottenere il set corrente di vertici per una mesh mano.  Come in precedenza, *la variabile currentState* rappresenta un'istanza [di SpatialInteractionSourceState.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

A differenza degli scheletri delle giunzioni, l'API hand mesh non consente di specificare un sistema di coordinate per i vertici.  [HandMeshVertexState](/uwp/api/windows.perception.people.handmeshvertexstate) specifica invece il sistema di coordinate in cui vengono forniti i vertici.  È quindi possibile ottenere una trasformazione mesh chiamando [TryGetTransformTo](/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) e specificando il sistema di coordinate desiderato.  È necessario usare questa trasformazione mesh ogni volta che si lavora con i vertici.  Questo approccio riduce il sovraccarico della CPU, soprattutto se si usa la mesh solo a scopo di rendering.

## <a name="gaze-and-commit-composite-gestures"></a>Movimenti compositi sguardo fisso e commit
Per le applicazioni che usano il modello di input con sguardo fisso e commit, in particolare in HoloLens (prima generazione), l'API Di input spaziale fornisce un [spatialGestureRecognizer](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer) facoltativo che può essere usato per abilitare movimenti compositi creati in base all'evento "select".  Instradando le interazioni da SpatialInteractionManager a SpatialGestureRecognizer di un ologramma, le app possono rilevare gli eventi di tocco, attesa, manipolazione e navigazione in modo uniforme tra le mani, la voce e i dispositivi di input spaziale, senza dover gestire manualmente le presse e i rilasci.

SpatialGestureRecognizer esegue solo la disambiguazione minima tra il set di movimenti richiesto. Ad esempio, se si richiede solo il tocco, l'utente può tenere premuto il dito fino a quando lo desidera e un tocco continuerà a verificarsi. Se si richiedono sia tocco che hold, dopo circa un secondo di tenere premuto il dito, il movimento verrà alzato di livello a hold e non si verificherà più un tocco.

Per usare SpatialGestureRecognizer, gestisci l'evento [InteractionDetected](/uwp/api/Windows.UI.Input.Spatial.SpatialInteractionManager) di SpatialInteractionManager e afferra l'oggetto SpatialPointerPose esposto. Usare il raggio dello sguardo fisso della testa dell'utente da questa posizione per intersecarsi con gli ologrammi e le mesh di superficie nell'ambiente circostante dell'utente per determinare con quali elementi l'utente intende interagire. Instradare quindi SpatialInteraction negli argomenti dell'evento all'oggetto SpatialGestureRecognizer dell'ologramma di destinazione, usando il [relativo metodo CaptureInteraction.](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer) Viene avviata l'interpretazione dell'interazione in base all'oggetto [SpatialGestureSettings](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureSettings) impostato su tale sistema di riconoscimento al momento della creazione oppure tramite [TrySetGestureSettings.](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer)

In HoloLens (prima generazione), le interazioni e i movimenti devono derivare la destinazione dallo sguardo con la testa dell'utente, anziché eseguire il rendering o interagire con la posizione della mano. Dopo l'avvio di un'interazione, è possibile usare i movimenti relativi della mano per controllare il movimento, come con il movimento di manipolazione o navigazione.

## <a name="see-also"></a>Vedi anche
* [Puntamento con la testa e sguardo fisso in DirectX](gaze-in-directx.md)
* [Modello di input di manipolazione diretta](../../design/direct-manipulation.md)
* [Modello di input point-and-commit](../../design/point-and-commit.md)
* [Modello di input sguardo fisso e commit](../../design/gaze-and-commit.md)
* [Controller del movimento](../../design/motion-controllers.md)