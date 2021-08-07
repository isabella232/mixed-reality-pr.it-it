---
ms.openlocfilehash: e7f298b9d587df2243601670e187c109bb674a278deb67862b517568ca5198d7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213516"
---
# <a name="project-settings"></a>[Impostazioni del progetto](#tab/project)

### <a name="1-review-the-common-porting-steps-listed-above"></a>1. Esaminare i passaggi comuni di porting elencati in precedenza

Esaminare i passaggi comuni elencati in precedenza per assicurarsi che l'ambiente di sviluppo sia configurato correttamente. Nel passaggio #3, se si usa Visual Studio è necessario selezionare il carico di lavoro Sviluppo di giochi **con Unity.** È possibile deselezionare il componente "Editor unity facoltativo" perché nel passaggio successivo si installerà una versione più recente di Unity.

### <a name="2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>2. Eseguire l'aggiornamento alla build pubblica più recente di Unity con Windows MR Support
1. Scaricare la build [pubblica più recente consigliata di Unity con](../../install-the-tools.md) supporto per la realtà mista.
2. Salvare una copia del progetto prima di iniziare
3. Esaminare la [documentazione](https://docs.unity3d.com/Manual/UpgradeGuides.html) disponibile in Unity per l'aggiornamento se il progetto è stato compilato in una versione precedente di Unity.
4. Seguire le [istruzioni nel](https://docs.unity3d.com/Manual/APIUpdater.html) sito di Unity per l'uso dell'aggiornamento automatico delle API
5. Controllare e verificare se sono necessarie modifiche aggiuntive per eseguire il progetto e risolvere eventuali errori e avvisi rimanenti. 

> [!Note] 
> Se si dispone di middleware da cui si dipende, verificare di usare la versione più recente (altri dettagli nel passaggio 3 di seguito).

### <a name="3-upgrade-your-middleware-to-the-latest-versions"></a>3. Aggiornare il middleware alle versioni più recenti

Con qualsiasi aggiornamento di Unity, è probabile che sia necessario aggiornare uno o più pacchetti middleware da cui dipende il gioco o l'applicazione. Inoltre, l'aggiornamento del middleware più recente aumenta la probabilità di successo durante il resto del processo di porting.

### <a name="4-target-your-application-to-run-on-win32"></a>4. Impostare come destinazione l'esecuzione dell'applicazione in Win32

Dall'interno dell'applicazione Unity:

* Passare a File -> Build Impostazioni
* Selezionare "PC, Mac, Linux autonomo"
* Impostare la piattaforma di destinazione su "Windows"
* Impostare architettura su "x86" Selezionare "Cambia piattaforma"

> [!NOTE] 
> Se l'applicazione ha dipendenze da servizi specifici del dispositivo, ad esempio la creazione di corrispondenze da Steam, è necessario disabilitarle in questo passaggio. È possibile collegarsi ai servizi equivalenti che Windows in un secondo momento.

### <a name="5-setup-your-windows-mixed-reality-hardware"></a>5. Configurare l'hardware Windows Mixed Reality hardware
1. Esaminare i passaggi in [Configurazione visore immersivo](/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. Informazioni [sull'uso del simulatore Windows Mixed Reality](../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) [e sulla navigazione nella Windows Mixed Reality home page](../../../discover/navigating-the-windows-mixed-reality-home.md)

### <a name="6-target-your-application-to-run-on-windows-mixed-reality"></a>6. Impostare come destinazione l'esecuzione dell'applicazione Windows Mixed Reality
1. In primo luogo, è necessario rimuovere o compilare in modo condizionale qualsiasi altro supporto di libreria specifico per un sdk VR specifico. Tali asset modificano spesso le impostazioni e le proprietà del progetto in modi incompatibili con altri SDK vr, ad esempio Windows Mixed Reality.
    * Ad esempio, se il progetto fa riferimento a SteamVR SDK, è necessario aggiornare il progetto per usare invece le API VR comuni di Unity che supportano sia Windows Mixed Reality che SteamVR.
    * Saranno presto disponibili passaggi specifici per escludere in modo condizionale altri SDK vr.
2. Nel progetto Unity fare riferimento [all'SDK Windows 10](../../unity/tutorials/holograms-100.md#target-windows-10-sdk)
3. Per ogni scena, [configurare la fotocamera](../../unity/tutorials/holograms-100.md#chapter-2---setup-the-camera)

### <a name="7-use-the-stage-to-place-content-on-the-floor"></a>7. Usare la fase per posizionare il contenuto sul pavimento

È possibile creare esperienze di realtà mista in un'ampia gamma di [scalabilità di esperienze.](../../../design/coordinate-systems.md)

Se si sta trasando **un'esperienza di** ridimensionamento, è necessario assicurarsi che Unity sia impostato sul **tipo di** spazio di rilevamento stazionario:

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

Questo codice precedente imposta il sistema di coordinate del mondo di Unity per tenere traccia [del fotogramma zionario di riferimento.](../../../design/coordinate-systems.md#spatial-coordinate-systems) Nella modalità di rilevamento stazionario, il contenuto posizionato nell'editor proprio davanti alla posizione predefinita della fotocamera (forward è -Z) viene visualizzato davanti all'utente all'avvio dell'app. Per visualizzare più recente l'origine dell'utente, è possibile chiamare la XR di [Unity. Metodo InputTracking.Recenter.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)

Se si sta effettuando il porting di un'esperienza su larga scala o su scala **locale,** il contenuto verrà posizionato rispetto al piano.  Il piano dell'utente viene ragione usando la fase spaziale **[,](../../../design/coordinate-systems.md#spatial-coordinate-systems)** che rappresenta l'origine definita a livello di piano dell'utente e il limite facoltativo della stanza, configurato durante la prima esecuzione. Per queste esperienze, è necessario assicurarsi che Unity sia impostato sul tipo di spazio di rilevamento **RoomScale.** Anche se RoomScale è l'impostazione predefinita, è necessario impostarla in modo esplicito e assicurarsi di tornare true per rilevare le situazioni in cui l'utente ha spostato il computer dalla stanza calibrata:

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

Dopo che l'app ha impostato correttamente il tipo di spazio di rilevamento RoomScale, sul piano y=0 verrà visualizzato il contenuto posizionato sul piano y=0. L'origine in (0, 0, 0) sarà la posizione specifica sul piano in cui l'utente si trovava durante la configurazione della stanza, con -Z che rappresenta la direzione in avanti che stava affrontando durante la configurazione.

Nel codice di script è quindi possibile chiamare il metodo TryGetGeometry sul tipo UnityEngine.Experimental.XR.Boundary per ottenere un poligono limite, specificando un tipo di limite TrackedArea. Se l'utente ha definito un limite (si ottiene un elenco di  vertici), è possibile offrire un'esperienza su larga scala all'utente, in cui può aggirare la scena creata.

Il sistema eseguirà automaticamente il rendering del limite quando l'utente vi si avvicina. L'app non deve usare questo poligono per eseguire il rendering del limite stesso.

Per altre informazioni, vedere la [pagina Sistemi di coordinate in Unity.](../../unity/coordinate-systems-in-unity.md)

<!-- Some applications use a rectangle to constrain their interaction. Retrieving the largest inscribed rectangle is not directly supported in the UWP API or Unity. The example code linked to below shows how to find a rectangle within the traced bounds. It's heuristic-based so may not find the optimal solution, however, results are consistent with expectations. Parameters in the algorithm can be tuned to find more precise results at the cost of processing time. The algorithm is in a fork of the Mixed Reality Toolkit that uses the 5.6 preview MRTP version of Unity. This isn't publicly available. The code should be directly usable in 2017.2 and higher versions of Unity. The code will be ported to the current MRTK in the near future. -->

Esempio di risultati:

![Esempio di risultati](../../porting-apps/images/largestrectangle-400px.jpg)

L'algoritmo è basato su un blog di Daniel Smilkov: [Rettangolo più grande in un poligono](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="8-work-through-your-input-model"></a>8. Usare il modello di input

Ogni gioco o applicazione che ha come destinazione un HMD esistente avrà un set di input gestiti, tipi di input di cui ha bisogno per l'esperienza e API specifiche che chiama per ottenere tali input. Abbiamo investito nel tentativo di rendere il più semplice e semplice possibile sfruttare gli input disponibili in Windows Mixed Reality.

Leggere la guida [alla portabilità dell'input](../porting-guides.md?tabs=input) per Unity nella scheda adiacente per informazioni dettagliate su come Windows Mixed Reality espone l'input e su come viene eseguito il mapping a ciò che l'applicazione può eseguire attualmente.

### <a name="9-performance-testing-and-tuning"></a>9. Test e ottimizzazione delle prestazioni

Windows Mixed Reality sarà disponibile su un'ampia classe di dispositivi, che vanno dai PC di gioco di fascia alta, fino ai PC mainstream di ampio mercato. A seconda del mercato di destinazione, esiste una differenza significativa nei budget di calcolo e grafica disponibili per l'applicazione. Durante questo esercizio di porting, probabilmente si sta sfruttando un PC Premium e sono stati disponibili budget di calcolo e grafica significativi per l'app. Se si vuole rendere disponibile l'app a un pubblico più ampio, è consigliabile testare e profilare l'app nell'hardware rappresentativo che si [vuole impostare come destinazione.](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)

[Unity e Visual Studio](https://docs.unity3d.com/Manual/Profiler.html) includono [profiler](/visualstudio/profiling/index) delle prestazioni e [microsoft](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) e [Intel](https://software.intel.com/articles/vr-content-developer-guide) pubblicano linee guida sulla profilatura e l'ottimizzazione delle prestazioni. È disponibile un'ampia discussione sulle prestazioni in [Informazioni sulle prestazioni per la realtà mista.](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) Sono inoltre disponibili dettagli specifici per Unity in [Prestazioni Consigli per Unity](../../unity/performance-recommendations-for-unity.md).

# <a name="input-mapping"></a>[Mapping dell'input](#tab/input)

È possibile convertire la logica di input Windows Mixed Reality usando uno dei due approcci seguenti, le API Input.GetButton/GetAxis generali di Unity che si estendono su più piattaforme o il Windows XR specifico di Windows. Wsa. API di input che offrono dati più ricchi in particolare per i controller di movimento e HoloLens mani.

> [!IMPORTANT]
> Se si usano controller HP Reverb G2, fare riferimento a [questo articolo](../../unity/unity-reverb-g2-controllers.md) per istruzioni aggiuntive sul mapping dell'input.

## <a name="unity-xr-input-apis"></a>API di input XR di Unity

Per i nuovi progetti, è consigliabile usare le nuove API di input XR dall'inizio. 

Altre informazioni sulle [API XR sono](https://docs.unity3d.com/Manual/xr_input.html)disponibili qui.

## <a name="inputgetbuttongetaxis-apis"></a>API Input.GetButton/GetAxis

Unity attualmente usa le API Input.GetButton/Input.GetAxis generali per esporre l'input per [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) e [OpenVR SDK.](https://docs.unity3d.com/Manual/OpenVRControllers.html) Se le app usano già queste API per l'input, questo è il percorso più semplice per supportare i controller di movimento in Windows Mixed Reality: è sufficiente modificare il mapping di pulsanti e assi in Gestione input.

Per altre informazioni, vedere la tabella [di mapping di pulsanti/assi unity](../../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) e la panoramica delle API comuni di [Unity.](../../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)

## <a name="windows-specific-xrwsainput-apis"></a>Windows XR specifico. Wsa. API di input

> [!CAUTION]
> Se il progetto usa una delle versioni XR. API WSA, che verranno gradualmente sfasati a favore di XR SDK nelle versioni future di Unity. Per i nuovi progetti, è consigliabile usare XR SDK fin dall'inizio. Altre informazioni sul sistema [di input XR e sulle API](https://docs.unity3d.com/Manual/xr_input.html)sono disponibili qui.

Se l'app crea già logica di input personalizzata per ogni piattaforma, è possibile scegliere di usare le API di input spaziale specifiche di Windows nello spazio dei nomi **UnityEngine.XR.WSA.Input.** In questo modo è possibile accedere a informazioni aggiuntive, ad esempio l'accuratezza della posizione o il tipo di origine, consentendo di distogliere mani e controller HoloLens.

> [!NOTE]
> Se si usano controller HP Reverb G2, tutte le API di input continueranno a funzionare ad eccezione di **InteractionSource.supportsTouchpad**, che restituirà false senza dati touchpad.

Per altre informazioni, vedere [la panoramica delle API UnityEngine.XR.WSA.Input](../../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Posizione di aderenza rispetto alla posizione di puntamento

Windows Mixed Reality supporta i controller di movimento in un'ampia gamma di fattori di forma, con la progettazione di ogni controller diversa nella relazione tra la posizione della mano dell'utente e la direzione naturale "in avanti" che le app devono usare per puntare durante il rendering del controller.

Per rappresentare meglio questi controller, è possibile analizzare due tipi di pose per ogni origine di interazione:

* La **posizione del grip**, che rappresenta la posizione del palmo di una mano rilevata da un HoloLens o del palmo che tiene un controller di movimento.
    * Nei visori immersivi, questa posizione è più adatta per eseguire il rendering della mano **dell'utente** o di un oggetto in mano **dell'utente,** ad esempio un colpo di mano o una mitragliatrice.
    * Posizione **del grip:** centroide del palmo quando si tiene il controller naturalmente, regolato a sinistra o a destra per centrare la posizione all'interno del grip.
    * Asse destro dell'orientamento del grip: quando si apre completamente la mano per formare una posizione a 5 dita piana, il raggio normale al palmo (in avanti dal palmo sinistro, **all'indietro** dal palmo destro)
    * Asse avanti **dell'orientamento** del grip: quando si chiude parzialmente la mano (come se si tiene il controller), il raggio che punta in avanti attraverso il canale formato dalle dita non del pollice.
    * Asse **su dell'orientamento del** grip: asse Su implicito dalle definizioni Right e Forward.
    * È possibile accedere alla posizione del grip tramite l'API di input tra fornitori di Unity **[(XR). InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) o tramite l'API Windows specifica (**sourceState.sourcePose.TryGetPosition/Rotation,** che richiede la posizione del grip).
* Puntatore **che rappresenta** la punta del controller che punta in avanti.
    * Questa posizione è più adatta per eseguire il raycast quando **si punta all'interfaccia** utente quando si esegue il rendering del modello del controller stesso.
    * Attualmente, la posizione del puntatore è disponibile solo tramite l'API specifica Windows (**sourceState.sourcePose.TryGetPosition/Rotation,** che richiede la posizione del puntatore).

Queste coordinate di posizione sono tutte espresse in coordinate del mondo unity.