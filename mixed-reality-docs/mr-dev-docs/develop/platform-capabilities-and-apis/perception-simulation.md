---
title: Simulazione della percezione
description: Guida all'uso della libreria Perception Simulation per automatizzare l'input simulato per applicazioni immersive
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens, simulazione, test
ms.openlocfilehash: 8d2999868bfdcf67c1174209566e67fe937005946ef82dd50337d9098c1e1971
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193777"
---
# <a name="perception-simulation"></a>Simulazione della percezione

Si vuole compilare un test automatizzato per l'app? Si vuole che i test superino gli unit test a livello di componente e esercitino realmente l'app end-to-end? Perception Simulation è ciò che si sta cercando. La libreria Perception Simulation invia dati di input umani e mondiali all'app per automatizzare i test. Ad esempio, è possibile simulare l'input di un essere umano che cerca una posizione ripetibile specifica e quindi usare un movimento o un controller di movimento.

Perception Simulation può inviare input simulati come questo a un HoloLens fisico, all'emulatore HoloLens (prima generazione), al HoloLens 2 Emulator o a un PC con Portale realtà mista installato. Perception Simulation ignora i sensori in tempo reale in un dispositivo di realtà mista e invia input simulato alle applicazioni in esecuzione nel dispositivo. Le applicazioni ricevono questi eventi di input tramite le stesse API che usano sempre e non possono distinguere tra l'esecuzione con sensori reali e la simulazione della percezione. Perception Simulation è la stessa tecnologia usata dagli emulatori HoloLens per inviare input simulato alla macchina HoloLens virtuale.

Per iniziare a usare la simulazione nel codice, iniziare creando un oggetto IPerceptionSimulationManager. Da tale oggetto è possibile eseguire comandi per controllare le proprietà di un "umano" simulato, tra cui la posizione della testa, la posizione della mano e i movimenti. È anche possibile abilitare e modificare i controller di movimento.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Configurazione di un Visual Studio Project per Perception Simulation
1. [Installare l HoloLens emulatore](../install-the-tools.md) nel PC di sviluppo. L'emulatore include le librerie usate per Perception Simulation.
2. Creare un nuovo Visual Studio desktop C# (una console Project ideale per iniziare).
3. Aggiungere i file binari seguenti al progetto come riferimenti (Project->Add->Reference...). È possibile trovarli in %ProgramFiles(x86)%\Microsoft XDE (versione), ad esempio \\ **%ProgramFiles(x86)%\Microsoft XDE \\ 10.0.18362.0** per il HoloLens 2 Emulator.  Nota: anche se i file binari fanno parte del HoloLens 2 Emulator, funzionano anche per Windows Mixed Reality sul desktop. Un. PerceptionSimulationManager.Interop.dll - Wrapper C# gestito per Perception Simulation.
    b. PerceptionSimulationRest.dll: libreria per la configurazione di un canale di comunicazione web-socket HoloLens o dell'emulatore.
    c. SimulationStream.Interop.dll: tipi condivisi per la simulazione.
4. Aggiungere il file binario di PerceptionSimulationManager.dll di implementazione al progetto a. Prima di tutto aggiungerlo come file binario al progetto (Project->Add->Existing Item...). Salvarlo come collegamento in modo che non lo copia nella cartella di origine del progetto. ![Aggiungere PerceptionSimulationManager.dll progetto come collegamento ](images/saveaslink.png) b. Assicurarsi quindi che venga copiato nella cartella di output durante la compilazione. Si trova nella finestra delle proprietà per il file binario. ![Contrassegnare PerceptionSimulationManager.dll da copiare nella directory di output](images/copyalways.png)
5. Impostare la piattaforma della soluzione attiva su x64.  Usare il Gestione configurazione per creare una voce platform per x64, se non ne esiste già una.

## <a name="creating-an-iperceptionsimulation-manager-object"></a>Creazione di un oggetto IPerceptionSimulation Manager

Per controllare la simulazione, si emettere aggiornamenti agli oggetti recuperati da un oggetto IPerceptionSimulationManager. Il primo passaggio consiste nel ottenere l'oggetto e connetterlo al dispositivo o all'emulatore di destinazione. È possibile ottenere l'indirizzo IP dell'emulatore facendo clic sul pulsante Portale di dispositivi sulla barra degli [strumenti](using-the-hololens-emulator.md)

![Aprire Portale di dispositivi'icona Apri Portale di dispositivi : aprire il Windows Portale di dispositivi per il HoloLens ](images/emulator-deviceportal.png) sistema operativo nell'emulatore.  Ad Windows Mixed Reality, è possibile recuperarla nell'app Impostazioni in "Update & Security", quindi "For developers" nella sezione "Connessione using:" in "Enable Portale di dispositivi".  Assicurarsi di prendere nota sia dell'indirizzo IP che della porta.

In primo luogo, si chiamerà RestSimulationStreamSink.Create per ottenere un oggetto RestSimulationStreamSink. Si tratta del dispositivo o dell'emulatore di destinazione che sarà possibile controllare su una connessione HTTP. I comandi verranno passati e gestiti dal Windows Portale di dispositivi [in](using-the-windows-device-portal.md) esecuzione nel dispositivo o nell'emulatore. I quattro parametri necessari per creare un oggetto sono:
* URI URI : indirizzo IP del dispositivo di destinazione (ad esempio, " https://123.123.123.123 " o " https://123.123.123.123:50080 ")
* Credenziali system.Net.NetworkCredential: nome utente/password per la connessione [al Windows Portale di dispositivi](using-the-windows-device-portal.md) nel dispositivo o nell'emulatore di destinazione. Se ci si connette all'emulatore tramite il relativo indirizzo locale (ad esempio, 168.*.* *) nello stesso PC, tutte le credenziali verranno accettate.
* bool normal: true per la priorità normale, false per la priorità bassa. In genere si vuole impostare questo valore su *true per* gli scenari di test, che consente al test di assumere il controllo.  L'emulatore e Windows Mixed Reality simulazione usano connessioni con priorità bassa.  Se il test usa anche una connessione con priorità bassa, la connessione stabilita più di recente avrà il controllo.
* Token System.Threading.CancellationToken: token per annullare l'operazione asincrona.

In secondo momento, si creerà IPerceptionSimulationManager. Questo è l'oggetto che si usa per controllare la simulazione. Questa operazione deve essere eseguita anche in un metodo asincrono.

## <a name="control-the-simulated-human"></a>Controllare l'umano simulato

Un oggetto IPerceptionSimulationManager ha una proprietà Human che restituisce un oggetto ISimulatedHuman. Per controllare l'umano simulato, eseguire operazioni su questo oggetto. Ad esempio:

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>Applicazione console C# di esempio di base

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a>Applicazione console C# di esempio estesa

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a>Nota sui controller 6-DOF

Prima di chiamare le proprietà sui metodi in un controller simulato a 6 DOF, è necessario attivare il controller.  Se non si fa questo, verrà generata un'eccezione.  A partire dal Aggiornamento di Windows 10 (maggio 2019), i controller 6-DOF simulati possono essere installati e attivati impostando la proprietà Status dell'oggetto ISimulatedSixDofController su SimulatedSixDofControllerStatus.Active.
Nel Aggiornamento di Windows 10 (ottobre 2018) e versioni precedenti è necessario installare separatamente un controller simulato a 6 DOF chiamando prima lo strumento PerceptionSimulationDevice disponibile nella cartella \Windows\System32.  L'utilizzo di questo strumento è il seguente:


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

Ad esempio:

```
    PerceptionSimulationDevice.exe i 6dof 1
```

Le azioni supportate sono:
* i = installazione
* q = query
* r = remove

Le istanze supportate sono:
* 1 = controller a 6 DOF sinistro
* 2 = il controller a 6 DOF destro

Il codice di uscita del processo indicherà l'esito positivo (un valore restituito zero) o un errore (un valore restituito diverso da zero).  Quando si usa l'azione "q" per verificare se è installato un controller, il valore restituito sarà zero (0) se il controller non è già installato o uno (1) se il controller è installato.

Quando si rimuove un controller nel Aggiornamento di Windows 10 (ottobre 2018) o versioni precedenti, impostarne lo stato su Disattivato prima tramite l'API, quindi chiamare lo strumento PerceptionSimulationDevice.

Questo strumento deve essere eseguito come amministratore.




## <a name="api-reference"></a>Informazioni di riferimento sulle API

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>Microsoft.PerceptionSimulation.SimulatedDeviceType

Descrive un tipo di dispositivo simulato

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**

Un dispositivo di riferimento fittizio, il valore predefinito per PerceptionSimulationManager

### <a name="microsoftperceptionsimulationheadtrackermode"></a>Microsoft.PerceptionSimulation.HeadTrackerMode

Descrive la modalità di rilevamento della testa

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**

Rilevamento head predefinito. Ciò significa che il sistema può selezionare la migliore modalità di rilevamento della testa in base alle condizioni di runtime.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**

Tracciamento solo della testa dell'orientamento. Ciò significa che la posizione rilevata potrebbe non essere affidabile e alcune funzionalità dipendenti dalla posizione head potrebbero non essere disponibili.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**

Rilevamento della testa posizionale. Ciò significa che la posizione della testa tracciata e l'orientamento sono entrambi affidabili

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>Microsoft.PerceptionSimulation.SimulatedGesture

Descrive un movimento simulato

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

**Microsoft.PerceptionSimulation.SimulatedGesture.None**

Valore sentinel usato per indicare l'assenza di movimenti.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**

Movimento premuto con un dito.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**

Movimento rilasciato da un dito.

**Microsoft.PerceptionSimulation.SimulatedGesture.Home**

Movimento di casa/sistema.

**Microsoft.PerceptionSimulation.SimulatedGesture.Max**

Movimento massimo valido.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus

I possibili stati di un controller 6-DOF simulato.

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**

Il controller 6-DOF è disattivato.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**

Il controller 6-DOF è attivato e monitorato.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**

Il controller 6-DOF è attivato, ma non può essere monitorato.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton

Pulsanti supportati in un controller simulato a 6 DOF.

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**

Valore sentinel utilizzato per indicare l'assenza di pulsanti.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**

Viene premuto il pulsante Home.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**

Viene premuto il pulsante Menu.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**

Viene premuto il pulsante Grip.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**

Il TouchPad viene premuto.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**

Viene premuto il pulsante Seleziona.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**

Il TouchPad viene toccato.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**

La levetta è premuta.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**

Pulsante valido massimo.


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState

Stato di calibrazione degli occhi simulati

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**

La calibrazione degli occhi non è disponibile.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**

Gli occhi sono stati calibrati.  Si tratta del valore predefinito.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**

Gli occhi vengono calibrati.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**

Gli occhi devono essere calibrati.

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy

Accuratezza di rilevamento di un giunto della mano.

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**

Il giunto non viene monitorato.

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**

La posizione del giunto viene dedotto.

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**

Il giunto viene tracciato completamente.

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>Microsoft.PerceptionSimulation.SimulatedHandPose

Accuratezza di rilevamento di un giunto della mano.

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**

Le giunzioni delle dita della mano sono configurate per riflettere una posizione chiusa.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**

Le giunzioni delle dita della mano sono configurate per riflettere una posizione aperta.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**

Le giunzioni delle dita della mano sono configurate per riflettere una posizione di puntamento.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**

Le giunzioni delle dita della mano sono configurate per riflettere una posizione di avvicinamento delle dita.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**

Valore massimo valido per SimulatedHandPose.


### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft.PerceptionSimulation.PlaybackState

Descrive lo stato di una riproduzione.

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**Microsoft.PerceptionSimulation.PlaybackState.Stopped**

La registrazione è attualmente arrestata e pronta per la riproduzione.

**Microsoft.PerceptionSimulation.PlaybackState.Playing**

La registrazione è attualmente in riproduzione.

**Microsoft.PerceptionSimulation.PlaybackState.Paused**

La registrazione è attualmente sospesa.

**Microsoft.PerceptionSimulation.PlaybackState.End**

La registrazione ha raggiunto la fine.

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft.PerceptionSimulation.Vector3

Descrive un vettore a tre componenti, che potrebbe descrivere un punto o un vettore nello spazio 3D.

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**Microsoft.PerceptionSimulation.Vector3.X**

Componente X del vettore.

**Microsoft.PerceptionSimulation.Vector3.Y**

Componente Y del vettore.

**Microsoft.PerceptionSimulation.Vector3.Z**

Componente Z del vettore.

**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single))**

Costruire un nuovo vector3.

Parametri
* x : componente x del vettore.
* y : componente y del vettore.
* z : componente z del vettore.

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft.PerceptionSimulation.Rotation3

Descrive una rotazione di tre componenti.

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**Microsoft.PerceptionSimulation.Rotation3.Pitch**

Componente Pitch della rotazione, verso il basso intorno all'asse X.

**Microsoft.PerceptionSimulation.Rotation3.Yaw**

Componente Yaw della rotazione, proprio intorno all'asse Y.

**Microsoft.PerceptionSimulation.Rotation3.Roll**

Componente Roll della rotazione, proprio intorno all'asse Z.

**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single))**

Costruire un nuovo oggetto Rotation3.

Parametri
* pitch : componente pitch della rotazione.
* yaw: componente yaw della rotazione.
* roll: componente di roll della rotazione.

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration

Descrive la configurazione di un giunto su una mano simulata.

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**

Posizione del giunto.

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**

Rotazione del giunto.

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**

Accuratezza del rilevamento del giunto.


### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft.PerceptionSimulation.Frustum

Descrive un frusto di visualizzazione, come in genere usato da una fotocamera.

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft.PerceptionSimulation.Frustum.Near**

Distanza minima contenuta nel frustum.

**Microsoft.PerceptionSimulation.Frustum.Far**

Distanza massima contenuta nel frustum.

**Microsoft.PerceptionSimulation.Frustum.FieldOfView**

Campo di visualizzazione orizzontale del frusto, espresso in radianti (minore di PI).

**Microsoft.PerceptionSimulation.Frustum.AspectRatio**

Rapporto tra il campo di visualizzazione orizzontale e il campo di visualizzazione verticale.

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a>Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration

Descrive la configurazione dello schermo del visore simulato.

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**

Trasformazione dal centro della testa all'occhio sinistro ai fini del rendering stereo.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**

Rotazione dell'occhio sinistro ai fini del rendering stereo.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**

Trasformazione dal centro della testa all'occhio destro ai fini del rendering stereo.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**

Rotazione dell'occhio destro ai fini del rendering stereo.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**

Valore Ipd segnalato dal sistema ai fini del rendering stereo.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**

Indica se i valori specificati per le trasformazioni dell'occhio sinistro e destro devono essere considerati validi e applicati al sistema in esecuzione.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**

Indica se il valore fornito per Ipd deve essere considerato valido e applicato al sistema in esecuzione.


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.IPerceptionSimulationManager

Radice per la generazione dei pacchetti usati per controllare un dispositivo.

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**

Recuperare l'oggetto dispositivo simulato che interpreta l'essere umano simulato e il mondo simulato.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**

Recuperare l'oggetto che controlla l'oggetto umano simulato.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**

Reimposta lo stato predefinito della simulazione.

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft.PerceptionSimulation.ISimulatedDevice

Interfaccia che descrive il dispositivo, che interpreta il mondo simulato e l'umano simulato

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**

Recuperare head tracker dal dispositivo simulato.

**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**

Recuperare il tracciatore manuale dal dispositivo simulato.

**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**

Impostare le proprietà del dispositivo simulato in modo che corrispondano al tipo di dispositivo specificato.

Parametri
* type : nuovo tipo di dispositivo simulato

### <a name="microsoftperceptionsimulationisimulateddevice2"></a>Microsoft.PerceptionSimulation.ISimulatedDevice2

Sono disponibili proprietà aggiuntive eseguendo il cast di ISimulatedDevice a ISimulatedDevice2

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**

Recuperare o impostare se l'umano simulato indossa attivamente il visore.

**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**

Recuperare o impostare le proprietà della visualizzazione simulata.

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHeadTracker

Interfaccia che descrive la parte del dispositivo simulato che tiene traccia della testa dell'umano simulato.

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**

Recupera e imposta la modalità di rilevamento della testa corrente.

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHandTracker

Interfaccia che descrive la parte del dispositivo simulato che tiene traccia delle mani dell'umano simulato

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**

Recuperare la posizione del nodo in relazione al mondo, in metri.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**

Recuperare e impostare la posizione del tracciatore manuale simulato, rispetto al centro della testa.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**

Recuperare e impostare il passo verso il basso del tracciatore manuale simulato.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**

Recuperare e impostare se il frusto del tracciatore manuale simulato viene ignorato. Se ignorate, entrambe le mani sono sempre visibili. Quando non vengono ignorate (impostazione predefinita), le mani sono visibili solo quando si trova all'interno del frustum del tracciatore della mano.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**

Recuperare e impostare le proprietà frustum usate per determinare se le mani sono visibili al tracciatore della mano simulato.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft.PerceptionSimulation.ISimulatedHuman

Interfaccia di primo livello per il controllo dell'essere umano simulato.

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }s
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**

Recuperare e impostare la posizione del nodo in relazione al mondo, in metri. La posizione corrisponde a un punto al centro dei piedi dell'umano.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**

Recuperare e impostare la direzione dei visi umani simulati nel mondo. 0 radianti verso il basso sull'asse Z negativo. I radianti positivi ruotano in senso orario sull'asse Y.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**

Recuperare e impostare l'altezza dell'oggetto umano simulato, in metri.

**Microsoft.PerceptionSimulation.ISimulatedHand.LeftHand**

Recuperare la mano sinistra dell'umano simulato.

**Microsoft.PerceptionSimulation.ISimulatedHand.RightHand**

Recuperare la mano destra dell'umano simulato.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**

Recuperare la testa dell'oggetto umano simulato.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**

Spostare l'oggetto umano simulato rispetto alla posizione corrente, in metri.

Parametri
* translation: traduzione da spostare rispetto alla posizione corrente.

**Microsoft.PerceptionSimulation.ISimulated Rotate(System.Single)**

Ruotare l'oggetto umano simulato rispetto alla direzione corrente, in senso orario rispetto all'asse Y

Parametri
* radianti: quantità di rotazione intorno all'asse Y.

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>Microsoft.PerceptionSimulation.ISimulatedUlation2

Sono disponibili proprietà aggiuntive eseguendo il cast di ISimulatedReplica a ISimulated 2

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedController2.LeftController**

Recuperare il controller 6-DOF sinistro.

**Microsoft.PerceptionSimulation.ISimulatedController2.RightController**

Recuperare il controller 6-DOF giusto.


### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft.PerceptionSimulation.ISimulatedHand

Interfaccia che descrive una mano dell'essere umano simulato

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**

Recuperare la posizione del nodo in relazione al mondo, in metri.

**Microsoft.PerceptionSimulation.ISimulatedHand.Position**

Recuperare e impostare la posizione della mano simulata rispetto all'essere umano, in metri.

**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**

Recuperare e impostare se la mano è attualmente attivata.

**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**

Recupera un valore che indica se la mano è attualmente visibile a SimulatedDevice, ovvero se è in una posizione rilevata da HandTracker.

**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**

Spostare la mano in modo che sia visibile a SimulatedDevice.

**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**

Spostare la posizione della mano simulata rispetto alla posizione corrente, in metri.

Parametri
* translation: quantità di traslazione della mano simulata.

**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**

Eseguire un movimento usando la mano simulata.  Verrà rilevato dal sistema solo se la mano è abilitata.

Parametri
* gesture: movimento da eseguire.

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>Microsoft.PerceptionSimulation.ISimulatedHand2

Le proprietà aggiuntive sono disponibili eseguendo il cast di un oggetto ISimulatedHand a ISimulatedHand2.
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**

Recupera o imposta la rotazione della mano simulata.  I radianti positivi ruotano in senso orario quando si guarda lungo l'asse.

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>Microsoft.PerceptionSimulation.ISimulatedHand3

Sono disponibili proprietà aggiuntive eseguendo il cast di un oggetto ISimulatedHand a ISimulatedHand3
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**

Ottiene la configurazione congiunta per il giunzione specificato.

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**

Imposta la configurazione congiunta per il giunzione specificato.

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**

Impostare la mano su una posizione nota con un flag facoltativo da animare.  Nota: l'animazione non comporta giunzioni che riflettono immediatamente le configurazioni congiunte finali.


### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft.PerceptionSimulation.ISimulatedHead

Interfaccia che descrive la testa dell'essere umano simulato.

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**

Recuperare la posizione del nodo in relazione al mondo, in metri.

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**

Recuperare la rotazione della testa simulata. I radianti positivi ruotano in senso orario quando si guarda lungo l'asse.

**Microsoft.PerceptionSimulation.ISimulatedHead.Diametro**

Recuperare il diametro della testa simulata. Questo valore viene usato per determinare il centro della testa (punto di rotazione).

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Ruotare la testa simulata rispetto alla rotazione corrente. I radianti positivi ruotano in senso orario quando si guarda lungo l'asse.

Parametri
* rotation: quantità di rotazione.

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>Microsoft.PerceptionSimulation.ISimulatedHead2

Sono disponibili proprietà aggiuntive eseguendo il cast di un elemento ISimulatedHead a ISimulatedHead2

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**

Recuperare gli occhi dell'essere umano simulato.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController

Interfaccia che descrive un controller 6-DOF associato all'essere umano simulato.

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**

Recuperare la posizione del nodo in relazione al mondo, in metri.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**

Recupera o imposta lo stato corrente del controller.  Lo stato del controller deve essere impostato su un valore diverso da Disattivato prima che le chiamate ai pulsanti di spostamento, rotazione o pressione riescano.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**

Recuperare o impostare la posizione del controller simulato rispetto all'essere umano, in metri.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**

Recupera o imposta l'orientamento del controller simulato.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**

Spostare la posizione del controller simulato rispetto alla posizione corrente, in metri.

Parametri
* translation: quantità di traslazione del controller simulato.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**

Premere un pulsante sul controller simulato.  Verrà rilevato dal sistema solo se il controller è abilitato.

Parametri
* button : pulsante da premere.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**

Rilasciare un pulsante nel controller simulato.  Verrà rilevato dal sistema solo se il controller è abilitato.

Parametri
* button : pulsante da rilasciare.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**

Ottenere la posizione di un dito simulato sul touchpad del controller simulato.

Parametri
* x : posizione orizzontale del dito.
* y: posizione verticale del dito.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**

Impostare la posizione di un dito simulato sul touchpad del controller simulato.

Parametri
* x : posizione orizzontale del dito.
* y: posizione verticale del dito.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController2

Proprietà e metodi aggiuntivi sono disponibili eseguendo il cast di ISimulatedSixDofController a ISimulatedSixDofController2

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**

Ottenere la posizione della levetta simulata sul controller simulato.

Parametri
* x : posizione orizzontale della levetta.
* y: posizione verticale della levetta.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**

Impostare la posizione della levetta simulata sul controller simulato.

Parametri
* x : posizione orizzontale della levetta.
* y: posizione verticale della levetta.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**

Recuperare o impostare il livello della batteria del controller simulato.  Il valore deve essere maggiore di 0,0 e minore o uguale a 100,0.


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>Microsoft.PerceptionSimulation.ISimulatedEyes

Interfaccia che descrive gli occhi dell'essere umano simulato.

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**

Recuperare la rotazione degli occhi simulati. I radianti positivi ruotano in senso orario quando si guarda lungo l'asse.

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Ruotare gli occhi simulati rispetto alla rotazione corrente. I radianti positivi ruotano in senso orario quando si guarda lungo l'asse.

Parametri
* rotation: quantità di rotazione.

**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**

Recupera o imposta lo stato di calibrazione degli occhi simulati.

**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**

Recuperare la posizione del nodo in relazione al mondo, in metri.


### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft.PerceptionSimulation.ISimulationRecording

Interfaccia per l'interazione con una singola registrazione caricata per la riproduzione.

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**

Recupera l'elenco dei tipi di dati nella registrazione.

**Microsoft.PerceptionSimulation.ISimulationRecording.State**

Recupera lo stato corrente della registrazione.

**Microsoft.PerceptionSimulation.ISimulationRecording.Play**

Avviare la riproduzione. Se la registrazione è sospesa, la riproduzione riprenderà dalla posizione sospesa. Se viene arrestata, la riproduzione verrà avviata all'inizio. Se è già in riproduzione, questa chiamata viene ignorata.

**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**

Sospende la riproduzione nella posizione corrente. Se la registrazione viene arrestata, la chiamata viene ignorata.

**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**

Cerca la registrazione nell'ora specificata (a intervalli di 100 nanosecondi dall'inizio) e viene sospesa in tale posizione. Se l'ora supera la fine della registrazione, viene sospesa in corrispondenza dell'ultimo fotogramma.

Parametri
* ticks: ora in cui eseguire la ricerca.

**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**

Arresta la riproduzione e reimposta la posizione all'inizio.

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft.PerceptionSimulation.ISimulationRecordingCallback

Interfaccia per la ricezione delle modifiche di stato durante la riproduzione.

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**

Chiamato quando lo stato di riproduzione di un oggetto ISimulationRecording viene modificato.

Parametri
* newState: nuovo stato della registrazione.

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.PerceptionSimulationManager

Oggetto radice per la creazione di oggetti perception simulation.

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**

Creare sull'oggetto per generare pacchetti simulati e recapitarli al sink fornito.

Parametri
* sink: sink che riceverà tutti i pacchetti generati.

Valore restituito

Manager creato.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**

Creare un sink che archivia tutti i pacchetti ricevuti in un file nel percorso specificato.

Parametri
* path: percorso del file da creare.

Valore restituito

Sink creato.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**

Caricare una registrazione dal file specificato.

Parametri
* path: percorso del file da caricare.
* factory: factory usata dalla registrazione per la creazione di un ISimulationStreamSink quando necessario.

Valore restituito

Registrazione caricata.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**

Caricare una registrazione dal file specificato.

Parametri
* path: percorso del file da caricare.
* factory: factory usata dalla registrazione per la creazione di un ISimulationStreamSink quando necessario.
* callback: callback, che riceve gli aggiornamenti per il nuovo aggiornamento dello stato della registrazione.

Valore restituito

Registrazione caricata.

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft.PerceptionSimulation.StreamDataTypes

Descrive i diversi tipi di dati del flusso.

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

**Microsoft.PerceptionSimulation.StreamDataTypes.None**

Valore sentinel utilizzato per indicare l'assenza di tipi di dati del flusso.

**Microsoft.PerceptionSimulation.StreamDataTypes.Head**

Flusso di dati per la posizione e l'orientamento della testa.

**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**

Flusso di dati per la posizione e i movimenti delle mani.

**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**

Flusso di dati per il mapping spaziale dell'ambiente.

**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**

Flusso di dati per la calibrazione del dispositivo. I pacchetti di calibrazione vengono accettati solo da un sistema in modalità remota.

**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**

Flusso di dati per l'ambiente del dispositivo.

**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**

Flusso di dati per i controller del movimento.

**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**

Flusso di dati con gli occhi dell'essere umano simulato.

**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**

Flusso di dati con la configurazione dello schermo del dispositivo.

**Microsoft.PerceptionSimulation.StreamDataTypes.All**

Valore sentinel usato per indicare tutti i tipi di dati registrati.

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft.PerceptionSimulation.ISimulationStreamSink

Oggetto che riceve pacchetti di dati da un flusso di simulazione.

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**

Riceve un singolo pacchetto, che è tipiato internamente e con controllo delle versioni.

Parametri
* length: lunghezza del pacchetto.
* packet: dati del pacchetto.

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory

Oggetto che crea ISimulationStreamSink.

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**

Crea una singola istanza di ISimulationStreamSink.

Valore restituito

Sink creato.
