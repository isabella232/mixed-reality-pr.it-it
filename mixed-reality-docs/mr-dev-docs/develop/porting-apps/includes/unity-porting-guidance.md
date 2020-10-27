---
ms.openlocfilehash: bcc899a178917a8ef184b4c11bd724df71f7b5c0
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638543"
---
# <a name="project-settings"></a>[Impostazioni del progetto](#tab/project)

### <a name="1-review-the-common-porting-steps-listed-above"></a>1. esaminare i passaggi di porting comuni elencati sopra

Esaminare i passaggi comuni elencati sopra per assicurarsi che l'ambiente di sviluppo sia configurato correttamente. Nel passaggio #3, se si usa Visual Studio, è necessario selezionare il carico di lavoro **sviluppo di giochi con Unity** . È possibile deselezionare il componente "Unity editor optional" poiché verrà installata una versione più recente di Unity nel passaggio successivo.

### <a name="2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>2. eseguire l'aggiornamento alla build pubblica più recente di Unity con il supporto di Windows MR
1. Scarica l'ultima [Build pubblica consigliata di Unity](../../install-the-tools.md) con il supporto della realtà mista.
2. Salva una copia del progetto prima di iniziare
3. Esaminare la [documentazione](https://docs.unity3d.com/Manual/UpgradeGuides.html) disponibile in Unity per l'aggiornamento se il progetto è stato creato con una versione precedente di Unity.
4. Seguire le [istruzioni](https://docs.unity3d.com/Manual/APIUpdater.html) nel sito di Unity per usare il relativo aggiornamento automatico delle API
5. Controllare e verificare se sono presenti ulteriori modifiche che è necessario apportare per eseguire il progetto e risolvere gli eventuali errori e avvisi rimanenti. 

> [!Note] 
> Se è presente un middleware da cui si dipende, verificare che sia in uso la versione più recente. per altre informazioni, vedere il passaggio 3 riportato di seguito.

### <a name="3-upgrade-your-middleware-to-the-latest-versions"></a>3. aggiornare il middleware alle versioni più recenti

Con qualsiasi aggiornamento di Unity, è possibile che sia necessario aggiornare uno o più pacchetti middleware da cui dipende il gioco o l'applicazione. Inoltre, l'aggiornamento con il middleware più recente aumenta la probabilità di successo durante il resto del processo di porting.

### <a name="4-target-your-application-to-run-on-win32"></a>4. indirizzare l'applicazione per l'esecuzione in Win32

Dall'interno dell'applicazione Unity:

* Passare a file-> impostazioni di compilazione
* Selezionare "PC, Mac, Linux autonomo"
* Imposta la piattaforma di destinazione su "Windows"
* Imposta architettura su "x86" selezionare "Cambia piattaforma"

> [!NOTE] 
> Se l'applicazione dispone di dipendenze da servizi specifici del dispositivo, ad esempio la corrispondenza da Steam, sarà necessario disabilitarli in questo passaggio. È possibile associare i servizi equivalenti forniti da Windows in un secondo momento.

### <a name="5-setup-your-windows-mixed-reality-hardware"></a>5. configurare l'hardware della realtà mista di Windows
1. Esaminare i passaggi nella [configurazione dell'auricolare immersiva](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. Scopri come [usare il simulatore di realtà mista di Windows](../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) e passare [alla Home realtà mista di Windows](../../../discover/navigating-the-windows-mixed-reality-home.md)

### <a name="6-target-your-application-to-run-on-windows-mixed-reality"></a>6. indirizzare l'applicazione per l'esecuzione in realtà mista di Windows
1. In primo luogo, è necessario rimuovere o compilare in modo condizionale qualsiasi altro supporto di libreria specifico di un determinato VR SDK. Tali asset cambiano spesso le impostazioni e le proprietà del progetto in modi non compatibili con altri SDK di VR, ad esempio la realtà mista di Windows.
    * Ad esempio, se il progetto fa riferimento a SteamVR SDK, sarà necessario aggiornare il progetto per usare invece le API VR comuni di Unity che supportano sia la realtà mista di Windows che la SteamVR.
    * I passaggi specifici per escludere gli altri SDK di VR saranno presto disponibili.
2. Nel progetto Unity, fare [riferimento a Windows 10 SDK](../../unity/tutorials/holograms-100.md#target-windows-10-sdk)
3. Per ogni scena, [configurare la fotocamera](../../unity/tutorials/holograms-100.md#chapter-2---setup-the-camera)

### <a name="7-use-the-stage-to-place-content-on-the-floor"></a>7. utilizzare la fase per collocare il contenuto al piano

È possibile creare esperienze di realtà miste in un'ampia gamma di [scale di esperienza](../../../design/coordinate-systems.md).

Se si esegue il porting di un' **esperienza con scalabilità verticale** , è necessario assicurarsi che Unity sia impostato sul tipo di spazio di rilevamento **stazionario** :

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

Questo codice precedente imposta il sistema di Coordinate internazionali di Unity per tenere traccia del [frame di riferimento fisso](../../../design/coordinate-systems.md#spatial-coordinate-systems). Nella modalità di rilevamento fisso, il contenuto inserito nell'editor immediatamente davanti alla posizione predefinita della fotocamera (avanti è-Z) viene visualizzato davanti all'utente all'avvio dell'app. Per ricentrare l'origine di seduta dell'utente, è possibile chiamare XR di Unity [. Metodo InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) .

Se si sta effettuando il porting di un'esperienza di **scalabilità permanente** o di **scalabilità** in modalità locale, il contenuto verrà inserito in relazione al pavimento. Si ragiona sul pavimento dell'utente usando la **[fase spaziale](../../../design/coordinate-systems.md#spatial-coordinate-systems)** , che rappresenta l'origine di livello del piano definita dall'utente e il limite di spazio facoltativo, configurato durante la prima esecuzione. Per queste esperienze è necessario assicurarsi che Unity sia impostato sul tipo di spazio di rilevamento **RoomScale** . Anche se RoomScale è il valore predefinito, è consigliabile impostarlo in modo esplicito e assicurarsi di tornare a true per individuare le situazioni in cui l'utente ha spostato il computer dalla stanza in cui è stato calibrato:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

Quando l'app imposta correttamente il tipo di spazio di rilevamento RoomScale, il contenuto inserito sul piano y = 0 verrà visualizzato sul pavimento. L'origine in (0, 0, 0) sarà la posizione specifica del piano in cui l'utente si trovava durante l'installazione della chat room, con-Z che rappresenta la direzione in avanti durante l'installazione.

Nel codice di script è quindi possibile chiamare il metodo TryGetGeometry sul tipo UnityEngine. Experimental. XR. Boundary per ottenere un poligono di limiti, specificando un tipo di limite di TrackedArea. Se l'utente ha definito un limite (si ottiene un elenco di vertici), è possibile fornire all'utente un' **esperienza di scalabilità della stanza** , in cui è possibile aggirare la scena creata.

Il sistema eseguirà automaticamente il rendering del limite quando l'utente si avvicina. L'app non deve usare questo poligono per eseguire il rendering del limite.

Per altre informazioni, vedere la pagina [sistemi di coordinate in Unity](../../unity/coordinate-systems-in-unity.md) .

<!-- Some applications use a rectangle to constrain their interaction. Retrieving the largest inscribed rectangle is not directly supported in the UWP API or Unity. The example code linked to below shows how to find a rectangle within the traced bounds. It's heuristic-based so may not find the optimal solution, however, results are consistent with expectations. Parameters in the algorithm can be tuned to find more precise results at the cost of processing time. The algorithm is in a fork of the Mixed Reality Toolkit that uses the 5.6 preview MRTP version of Unity. This isn't publicly available. The code should be directly usable in 2017.2 and higher versions of Unity. The code will be ported to the current MRTK in the near future. -->

Esempio di risultati:

![Esempio di risultati](../../porting-apps/images/largestrectangle-400px.jpg)

L'algoritmo si basa su un Blog di Daniel smilkov: [rettangolo più grande in un poligono](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="8-work-through-your-input-model"></a>8. utilizzare il modello di input

Ogni gioco o applicazione destinata a un HMD esistente avrà un set di input che gestisce, i tipi di input necessari per l'esperienza e le API specifiche che chiama per ottenere tali input. Abbiamo investito nel tentativo di renderlo il più semplice e semplice possibile per sfruttare i vantaggi degli input disponibili nella realtà mista di Windows.
1. Per informazioni dettagliate sul modo in cui la realtà mista di Windows espone l'input e su come eseguire questa operazione, vedere la **Guida al porting di input per Unity** nella scheda adiacente.
2. Scegliere se utilizzare l'API di input cross-VR-SDK di Unity o l'API di input specifica del sig. Le API di input. GetButton/input. getaxis generale vengono usate attualmente dalle app di Unity VR per l'input [Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) e l' [input OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html). Se le app usano già queste API per i controller di movimento, questo è il percorso più semplice: è necessario solo modificare il mapping di pulsanti e assi nel gestore di input.
    * È possibile accedere ai dati di motion controller in Unity usando le API General Cross-VR-SDK input. GetButton/input. getaxis o le API UnityEngine. XR. WSA. input specifiche di MR. (in precedenza nello spazio dei nomi UnityEngine. XR. WSA. input in Unity 5,6)
    * Vedere l' [esempio nel Toolkit](https://github.com/Microsoft/HoloToolkit-Unity/pull/572) che combina gamepad e controller di movimento.

### <a name="9-performance-testing-and-tuning"></a>9. test delle prestazioni e ottimizzazione

La realtà mista di Windows sarà disponibile in un'ampia gamma di dispositivi, a partire da PC con giochi di fascia alta, fino a PC mainstream di mercato più ampi. A seconda del mercato di destinazione, esiste una differenza significativa nei budget di calcolo e grafica disponibili per l'applicazione. Durante questo esercizio di porting, è probabile che si usi un PC Premium e che siano disponibili budget di calcolo e grafica significativi per l'app. Se si vuole rendere l'app disponibile a un pubblico più ampio, è consigliabile eseguire il test e la profilatura dell'app sull' [hardware rappresentativo a cui si vuole fare riferimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

[Unity](https://docs.unity3d.com/Manual/Profiler.html) e [Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index) includono i profiler delle prestazioni e le linee guida per la pubblicazione di [Microsoft](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) e [Intel](https://software.intel.com/articles/vr-content-developer-guide) per la profilatura e l'ottimizzazione delle prestazioni. È disponibile una descrizione approfondita delle prestazioni disponibili [per comprendere le prestazioni della realtà mista](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md). Sono inoltre disponibili dettagli specifici per Unity in [raccomandazioni sulle prestazioni per Unity](../../unity/performance-recommendations-for-unity.md).

# <a name="input-mapping"></a>[Mapping dell'input](#tab/input)

È possibile trasferire la logica di input in una realtà mista di Windows usando uno dei due approcci, le API input. GetButton/getaxis di Unity che si estendono su più piattaforme o la XR specifica di Windows. WSA. API di input che offrono dati più ricchi in modo specifico per i controller di movimento e le HoloLens.

> [!IMPORTANT]
> Se si usano i controller di HP Reverb G2, fare riferimento a [questo articolo](../../unity/unity-reverb-g2-controllers.md) per istruzioni aggiuntive sul mapping degli input.

## <a name="general-inputgetbuttongetaxis-apis"></a>Input generale. GetButton/API getaxis

Unity usa attualmente le API input. GetButton/input. getasse generale per esporre l'input per [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) e [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html). Se le app usano già queste API per l'input, questo è il percorso più semplice per supportare i controller di movimento in realtà mista di Windows: è necessario solo modificare il mapping di pulsanti e assi nel gestore di input.

Per altre informazioni, vedere la [tabella di mapping degli assi e dei pulsanti di Unity](../../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) e la [Panoramica delle API comuni di Unity](../../unity/gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).

## <a name="windows-specific-xrwsainput-apis"></a>XR specifico di Windows. WSA. API di input

Se l'app crea già una logica di input personalizzata per ogni piattaforma, è possibile scegliere di usare le API di input spaziali specifiche di Windows nello spazio dei nomi **UnityEngine. XR. WSA. input** . In questo modo è possibile accedere a informazioni aggiuntive, ad esempio l'accuratezza della posizione o il tipo di origine, consentendo di comunicare le mani e i controller a HoloLens.

> [!NOTE]
> Se si usano i controller di HP Reverb G2, tutte le API di input continueranno a funzionare ad eccezione di **InteractionSource. supportsTouchpad** , che restituirà false senza dati del touchpad.

Per altre informazioni, vedere la [Panoramica delle API UnityEngine. XR. WSA. input](../../unity/gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Posa del grip e puntamento

La realtà mista di Windows supporta i controller di movimento in diversi fattori di forma, con la progettazione di ogni controller diversa nella relazione tra la posizione della mano dell'utente e la direzione naturale "Avanti" che le app devono usare per puntare durante il rendering del controller.

Per rappresentare meglio questi controller, esistono due tipi di pose che è possibile esaminare per ogni origine interazione:

* La posizione del **grip** , che rappresenta la posizione della Palma di una mano rilevata da un HoloLens o della palma che contiene un controller di movimento.
    * Negli auricolari immersivi è consigliabile usare questa soluzione per eseguire **il rendering della mano dell'utente** o di **un oggetto contenuto nella mano** , ad esempio una spada o una pistola.
    * **Posizione del grip** : il centro della palma quando si tiene il controller in modo naturale, regolato a sinistra o a destra per centrare la posizione all'interno del grip.
    * L' **asse destro dell'orientamento del grip** : quando si apre completamente la mano per formare una formula a 5 dita piatta, il raggio normale per la Palma (in avanti dal palmo sinistro e viceversa)
    * **Asse di avanzamento dell'orientamento del grip** : quando si chiude parzialmente la mano (come se si utilizzasse il controller), il raggio che punta "in poi" attraverso il tubo formato dalle dita non Thumb.
    * **Asse verticale dell'orientamento del grip** : l'asse verso l'alto implicato dalle definizioni di destra e di avanzamento.
    * È possibile accedere al grip con l'API di input tra fornitori di Unity ( **[XR). InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation** ) o tramite l'API specifica di Windows ( **SourceState. SourcePose. TryGetPosition/Rotation** , che richiede la richiesta della forma del grip).
* Il **puntatore** che rappresenta il suggerimento del controller che punta in poi.
    * Questa posizione è particolarmente utilizzata per Raycast quando si **punta all'interfaccia utente** quando si esegue il rendering del modello di controller.
    * Attualmente, la posa del puntatore è disponibile solo tramite l'API specifica di Windows ( **sourceState. sourcePose. TryGetPosition/Rotation** , che richiede la posa del puntatore).

Queste coordinate di pose sono tutte espresse in coordinate internazionali di Unity.
