---
title: Simulazione della percezione
description: Guida all'uso della libreria di simulazione della percezione per automatizzare l'input simulato per le applicazioni immersive
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens, simulazione, test
ms.openlocfilehash: 64028c3a1ad58cecfebc93aee325b73c3a6a649a
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530397"
---
# <a name="perception-simulation"></a><span data-ttu-id="b7609-104">Simulazione della percezione</span><span class="sxs-lookup"><span data-stu-id="b7609-104">Perception simulation</span></span>

<span data-ttu-id="b7609-105">Si vuole compilare un test automatizzato per l'app?</span><span class="sxs-lookup"><span data-stu-id="b7609-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="b7609-106">Si desidera che i test vadano oltre il testing unità a livello di componente e che l'app venga effettivamente eseguita end-to-end?</span><span class="sxs-lookup"><span data-stu-id="b7609-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="b7609-107">La simulazione della percezione è ciò che si sta cercando.</span><span class="sxs-lookup"><span data-stu-id="b7609-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="b7609-108">La libreria di simulazione della percezione invia dati di input umani e internazionali all'app in modo che sia possibile automatizzare i test.</span><span class="sxs-lookup"><span data-stu-id="b7609-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="b7609-109">Ad esempio, è possibile simulare l'input di un utente che cerca una posizione specifica e ripetibile e quindi usare un movimento o un controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="b7609-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then use a gesture or motion controller.</span></span>

<span data-ttu-id="b7609-110">La simulazione della percezione può inviare input simulati come questo a un HoloLens fisico, l'emulatore di HoloLens (prima generazione), l'emulatore HoloLens 2 o un PC con portale di realtà mista installato.</span><span class="sxs-lookup"><span data-stu-id="b7609-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (first gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="b7609-111">La simulazione della percezione ignora i sensori dinamici in un dispositivo di realtà mista e invia un input simulato alle applicazioni in esecuzione sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b7609-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="b7609-112">Le applicazioni ricevono questi eventi di input tramite le stesse API che usano sempre e non riescono a capire la differenza tra l'esecuzione con sensori reali e la simulazione della percezione.</span><span class="sxs-lookup"><span data-stu-id="b7609-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus Perception Simulation.</span></span> <span data-ttu-id="b7609-113">La simulazione della percezione è la stessa tecnologia usata dagli emulatori di HoloLens per inviare input simulato alla macchina virtuale HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b7609-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="b7609-114">Per iniziare a usare la simulazione nel codice, iniziare creando un oggetto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="b7609-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="b7609-115">Da tale oggetto, è possibile eseguire comandi per controllare le proprietà di un elemento "Human" simulato, inclusi posizione della testa, posizione della mano e movimenti.</span><span class="sxs-lookup"><span data-stu-id="b7609-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span> <span data-ttu-id="b7609-116">È anche possibile abilitare e modificare i controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="b7609-116">You can also enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="b7609-117">Configurazione di un progetto di Visual Studio per la simulazione della percezione</span><span class="sxs-lookup"><span data-stu-id="b7609-117">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="b7609-118">[Installare l'emulatore di HoloLens](../install-the-tools.md) nel PC di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="b7609-118">[Install the HoloLens emulator](../install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="b7609-119">L'emulatore include le librerie usate per la simulazione della percezione.</span><span class="sxs-lookup"><span data-stu-id="b7609-119">The emulator includes the libraries you' use for Perception Simulation.</span></span>
2. <span data-ttu-id="b7609-120">Creare un nuovo progetto desktop di Visual Studio C# (un progetto console è molto interessante per iniziare).</span><span class="sxs-lookup"><span data-stu-id="b7609-120">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="b7609-121">Aggiungere i file binari seguenti al progetto come riferimenti (informazioni di riferimento sul >di aggiunta di Project->...). È possibile trovarli in% ProgramFiles (x86)% \ Microsoft XDE \\ (Version), ad esempio **% ProgramFiles (x86)% \ Microsoft XDE \\ 10.0.18362.0** per l'emulatore HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b7609-121">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="b7609-122">Nota: anche se i file binari fanno parte dell'emulatore HoloLens 2, funzionano anche per la realtà mista di Windows sul desktop. un.</span><span class="sxs-lookup"><span data-stu-id="b7609-122">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="b7609-123">Wrapper C# gestito da PerceptionSimulationManager.Interop.dll per la simulazione della percezione.</span><span class="sxs-lookup"><span data-stu-id="b7609-123">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="b7609-124">b.</span><span class="sxs-lookup"><span data-stu-id="b7609-124">b.</span></span> <span data-ttu-id="b7609-125">PerceptionSimulationRest.dll-Library per la configurazione di un canale di comunicazione del socket Web per HoloLens o emulatore.</span><span class="sxs-lookup"><span data-stu-id="b7609-125">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="b7609-126">c.</span><span class="sxs-lookup"><span data-stu-id="b7609-126">c.</span></span> <span data-ttu-id="b7609-127">Tipi condivisi SimulationStream.Interop.dll per la simulazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-127">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="b7609-128">Aggiungere il PerceptionSimulationManager.dll binario di implementazione al progetto a.</span><span class="sxs-lookup"><span data-stu-id="b7609-128">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="b7609-129">Per prima cosa, aggiungere il file come binario al progetto (>elemento esistente del >di progetto...). Salvarlo come collegamento in modo che non venga copiato nella cartella di origine del progetto.</span><span class="sxs-lookup"><span data-stu-id="b7609-129">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="b7609-130">![Aggiungere PerceptionSimulationManager.dll al progetto come collegamento ](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="b7609-130">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="b7609-131">Assicurarsi quindi che venga copiato nella cartella di output durante la compilazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-131">Then make sure that it gets copied to your output folder on build.</span></span> <span data-ttu-id="b7609-132">Si trova nella finestra delle proprietà per il file binario.</span><span class="sxs-lookup"><span data-stu-id="b7609-132">This is in the property sheet for the binary.</span></span> <span data-ttu-id="b7609-133">![Contrassegna PerceptionSimulationManager.dll per la copia nella directory di output](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="b7609-133">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="b7609-134">Impostare la piattaforma della soluzione attiva su x64.</span><span class="sxs-lookup"><span data-stu-id="b7609-134">Set your active solution platform to x64.</span></span>  <span data-ttu-id="b7609-135">Usare il Configuration Manager per creare una voce della piattaforma per x64, se non ne esiste già una.</span><span class="sxs-lookup"><span data-stu-id="b7609-135">(Use the Configuration Manager to create a Platform entry for x64 if one doesn't already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="b7609-136">Creazione di un oggetto IPerceptionSimulation Manager</span><span class="sxs-lookup"><span data-stu-id="b7609-136">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="b7609-137">Per controllare la simulazione, è possibile eseguire aggiornamenti agli oggetti recuperati da un oggetto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="b7609-137">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="b7609-138">Il primo passaggio consiste nell'ottenere l'oggetto e connetterlo al dispositivo o all'emulatore di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-138">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="b7609-139">È possibile ottenere l'indirizzo IP dell'emulatore facendo clic sul pulsante portale del dispositivo sulla [barra degli strumenti](using-the-hololens-emulator.md) .</span><span class="sxs-lookup"><span data-stu-id="b7609-139">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="b7609-140">![Aprire l'icona del portale del dispositivo ](images/emulator-deviceportal.png) **aprire il portale** del dispositivo: aprire il portale del dispositivo Windows per il sistema operativo HoloLens nell'emulatore.</span><span class="sxs-lookup"><span data-stu-id="b7609-140">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="b7609-141">Per la realtà mista di Windows, questo può essere recuperato nell'app impostazioni in "Aggiorna & sicurezza", quindi "per sviluppatori" nella sezione "Connetti tramite:" in "abilitare il portale del dispositivo".</span><span class="sxs-lookup"><span data-stu-id="b7609-141">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="b7609-142">Assicurarsi di annotare l'indirizzo IP e la porta.</span><span class="sxs-lookup"><span data-stu-id="b7609-142">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="b7609-143">In primo luogo, si chiamerà RestSimulationStreamSink. create per ottenere un oggetto RestSimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="b7609-143">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="b7609-144">Si tratta del dispositivo o dell'emulatore di destinazione che si controllerà su una connessione HTTP.</span><span class="sxs-lookup"><span data-stu-id="b7609-144">This is the target device or emulator that you'll control over an http connection.</span></span> <span data-ttu-id="b7609-145">I comandi verranno passati e gestiti dal [portale del dispositivo Windows](using-the-windows-device-portal.md) in esecuzione nel dispositivo o nell'emulatore.</span><span class="sxs-lookup"><span data-stu-id="b7609-145">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="b7609-146">I quattro parametri necessari per creare un oggetto sono:</span><span class="sxs-lookup"><span data-stu-id="b7609-146">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="b7609-147">Uri URI-indirizzo IP del dispositivo di destinazione (ad esempio, " https://123.123.123.123 " o " https://123.123.123.123:50080 ")</span><span class="sxs-lookup"><span data-stu-id="b7609-147">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="b7609-148">System .NET. NetworkCredential credentials: nome utente/password per la connessione al [portale per dispositivi Windows](using-the-windows-device-portal.md) sul dispositivo o sull'emulatore di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-148">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="b7609-149">Se ci si connette all'emulatore tramite l'indirizzo locale (ad esempio,*168...* \*) nello stesso computer verranno accettate le credenziali.</span><span class="sxs-lookup"><span data-stu-id="b7609-149">If you're connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="b7609-150">bool Normal-true per la priorità normale, false per priorità bassa.</span><span class="sxs-lookup"><span data-stu-id="b7609-150">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="b7609-151">In genere è consigliabile impostare questo valore su *true* per gli scenari di test, che consente al test di assumere il controllo.</span><span class="sxs-lookup"><span data-stu-id="b7609-151">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="b7609-152">L'emulatore e la simulazione di realtà mista di Windows usano connessioni con priorità bassa.</span><span class="sxs-lookup"><span data-stu-id="b7609-152">The emulator and Windows Mixed Reality simulation use low-priority connections.</span></span>  <span data-ttu-id="b7609-153">Se il test USA anche una connessione con priorità bassa, la connessione stabilita più di recente sarà controllata.</span><span class="sxs-lookup"><span data-stu-id="b7609-153">If your test also uses a low-priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="b7609-154">System. Threading. CancellationToken token-token per annullare l'operazione asincrona.</span><span class="sxs-lookup"><span data-stu-id="b7609-154">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="b7609-155">In secondo luogo, verrà creato il IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="b7609-155">Second, you'll create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="b7609-156">Si tratta dell'oggetto usato per controllare la simulazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-156">This is the object you use to control simulation.</span></span> <span data-ttu-id="b7609-157">Questa operazione deve essere eseguita anche in un metodo asincrono.</span><span class="sxs-lookup"><span data-stu-id="b7609-157">This must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="b7609-158">Controllare la persona simulata</span><span class="sxs-lookup"><span data-stu-id="b7609-158">Control the simulated Human</span></span>

<span data-ttu-id="b7609-159">Un IPerceptionSimulationManager ha una proprietà umana che restituisce un oggetto ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="b7609-159">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="b7609-160">Per controllare l'uomo simulato, eseguire operazioni su questo oggetto.</span><span class="sxs-lookup"><span data-stu-id="b7609-160">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="b7609-161">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="b7609-161">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="b7609-162">Applicazione console C# di esempio di base</span><span class="sxs-lookup"><span data-stu-id="b7609-162">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="b7609-163">Applicazione console C# di esempio estesa</span><span class="sxs-lookup"><span data-stu-id="b7609-163">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="b7609-164">Nota sui controller da 6 a DOF</span><span class="sxs-lookup"><span data-stu-id="b7609-164">Note on 6-DOF controllers</span></span>

<span data-ttu-id="b7609-165">Prima di chiamare qualsiasi proprietà nei metodi in un controller 6-DOF simulato, è necessario attivare il controller.</span><span class="sxs-lookup"><span data-stu-id="b7609-165">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="b7609-166">In caso contrario, viene generata un'eccezione.</span><span class="sxs-lookup"><span data-stu-id="b7609-166">Not doing so will result in an exception.</span></span>  <span data-ttu-id="b7609-167">A partire dall'aggiornamento 2019 di Windows 10, è possibile installare e attivare i controller 6-DOF simulati impostando la proprietà Status dell'oggetto ISimulatedSixDofController su SimulatedSixDofControllerStatus. Active.</span><span class="sxs-lookup"><span data-stu-id="b7609-167">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="b7609-168">Nell'aggiornamento di Windows 10 ottobre 2018 e versioni precedenti, è necessario installare prima di tutto un controller 6-DOF simulato chiamando lo strumento PerceptionSimulationDevice disponibile nella cartella \Windows\System32..</span><span class="sxs-lookup"><span data-stu-id="b7609-168">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="b7609-169">L'utilizzo di questo strumento è il seguente:</span><span class="sxs-lookup"><span data-stu-id="b7609-169">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="b7609-170">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="b7609-170">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="b7609-171">Le azioni supportate sono:</span><span class="sxs-lookup"><span data-stu-id="b7609-171">Supported actions are:</span></span>
* <span data-ttu-id="b7609-172">i = install</span><span class="sxs-lookup"><span data-stu-id="b7609-172">i = install</span></span>
* <span data-ttu-id="b7609-173">q = query</span><span class="sxs-lookup"><span data-stu-id="b7609-173">q = query</span></span>
* <span data-ttu-id="b7609-174">r = Rimuovi</span><span class="sxs-lookup"><span data-stu-id="b7609-174">r = remove</span></span>

<span data-ttu-id="b7609-175">Le istanze supportate sono:</span><span class="sxs-lookup"><span data-stu-id="b7609-175">Supported instances are:</span></span>
* <span data-ttu-id="b7609-176">1 = il controller 6-DOF a sinistra</span><span class="sxs-lookup"><span data-stu-id="b7609-176">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="b7609-177">2 = il controller 6-DOF a destra</span><span class="sxs-lookup"><span data-stu-id="b7609-177">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="b7609-178">Il codice di uscita del processo indicherà l'esito positivo (un valore restituito pari a zero) o un errore (un valore restituito diverso da zero).</span><span class="sxs-lookup"><span data-stu-id="b7609-178">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="b7609-179">Quando si usa l'azione "q" per eseguire una query su se è installato un controller, il valore restituito sarà zero (0) se il controller non è già installato o uno (1) se il controller è installato.</span><span class="sxs-lookup"><span data-stu-id="b7609-179">When using the 'q' action to query whether a controller is installed, the return value will be zero (0) if the controller isn't already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="b7609-180">Quando si rimuove un controller nell'aggiornamento di Windows 10 ottobre 2018 o versioni precedenti, impostare lo stato su disattivato tramite l'API, quindi chiamare lo strumento PerceptionSimulationDevice.</span><span class="sxs-lookup"><span data-stu-id="b7609-180">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="b7609-181">Questo strumento deve essere eseguito come amministratore.</span><span class="sxs-lookup"><span data-stu-id="b7609-181">This tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="b7609-182">Riferimento API</span><span class="sxs-lookup"><span data-stu-id="b7609-182">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="b7609-183">Microsoft. PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="b7609-183">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="b7609-184">Descrive un tipo di dispositivo simulato</span><span class="sxs-lookup"><span data-stu-id="b7609-184">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="b7609-185">**Microsoft. PerceptionSimulation. SimulatedDeviceType. Reference**</span><span class="sxs-lookup"><span data-stu-id="b7609-185">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="b7609-186">Un dispositivo di riferimento fittizio, il valore predefinito per PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="b7609-186">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="b7609-187">Microsoft. PerceptionSimulation. HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="b7609-187">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="b7609-188">Descrive la modalità Head Tracker</span><span class="sxs-lookup"><span data-stu-id="b7609-188">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="b7609-189">**Microsoft. PerceptionSimulation. HeadTrackerMode. default**</span><span class="sxs-lookup"><span data-stu-id="b7609-189">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="b7609-190">Rilevamento Head predefinito.</span><span class="sxs-lookup"><span data-stu-id="b7609-190">Default Head Tracking.</span></span> <span data-ttu-id="b7609-191">Ciò significa che il sistema può selezionare la modalità di rilevamento Head migliore in base alle condizioni di Runtime.</span><span class="sxs-lookup"><span data-stu-id="b7609-191">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="b7609-192">**Microsoft. PerceptionSimulation. HeadTrackerMode. Orientation**</span><span class="sxs-lookup"><span data-stu-id="b7609-192">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="b7609-193">Solo orientamento Head Tracking.</span><span class="sxs-lookup"><span data-stu-id="b7609-193">Orientation Only Head Tracking.</span></span> <span data-ttu-id="b7609-194">Ciò significa che la posizione rilevata potrebbe non essere affidabile e che alcune funzionalità che dipendono dalla posizione Head potrebbero non essere disponibili.</span><span class="sxs-lookup"><span data-stu-id="b7609-194">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="b7609-195">**Microsoft. PerceptionSimulation. HeadTrackerMode. Position**</span><span class="sxs-lookup"><span data-stu-id="b7609-195">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="b7609-196">Rilevamento Head posizionale.</span><span class="sxs-lookup"><span data-stu-id="b7609-196">Positional Head Tracking.</span></span> <span data-ttu-id="b7609-197">Ciò significa che la posizione e l'orientamento della testa rilevati sono entrambi affidabili</span><span class="sxs-lookup"><span data-stu-id="b7609-197">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="b7609-198">Microsoft. PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="b7609-198">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="b7609-199">Descrive un movimento simulato</span><span class="sxs-lookup"><span data-stu-id="b7609-199">Describes a simulated gesture</span></span>

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

<span data-ttu-id="b7609-200">**Microsoft. PerceptionSimulation. SimulatedGesture. None**</span><span class="sxs-lookup"><span data-stu-id="b7609-200">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="b7609-201">Valore sentinella utilizzato per indicare nessun movimento.</span><span class="sxs-lookup"><span data-stu-id="b7609-201">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="b7609-202">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="b7609-202">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="b7609-203">Gesto premuto con un dito.</span><span class="sxs-lookup"><span data-stu-id="b7609-203">A finger pressed gesture.</span></span>

<span data-ttu-id="b7609-204">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="b7609-204">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="b7609-205">Gesto rilasciato da un dito.</span><span class="sxs-lookup"><span data-stu-id="b7609-205">A finger released gesture.</span></span>

<span data-ttu-id="b7609-206">**Microsoft. PerceptionSimulation. SimulatedGesture. Home**</span><span class="sxs-lookup"><span data-stu-id="b7609-206">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="b7609-207">Movimento Home/sistema.</span><span class="sxs-lookup"><span data-stu-id="b7609-207">The home/system gesture.</span></span>

<span data-ttu-id="b7609-208">**Microsoft. PerceptionSimulation. SimulatedGesture. max**</span><span class="sxs-lookup"><span data-stu-id="b7609-208">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="b7609-209">Il gesto massimo valido.</span><span class="sxs-lookup"><span data-stu-id="b7609-209">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="b7609-210">Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="b7609-210">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="b7609-211">Gli stati possibili di un controller 6-DOF simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-211">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="b7609-212">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. off**</span><span class="sxs-lookup"><span data-stu-id="b7609-212">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="b7609-213">Il controller 6-DOF è disattivato.</span><span class="sxs-lookup"><span data-stu-id="b7609-213">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="b7609-214">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. Active**</span><span class="sxs-lookup"><span data-stu-id="b7609-214">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="b7609-215">Il controller 6-DOF è acceso e rilevato.</span><span class="sxs-lookup"><span data-stu-id="b7609-215">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="b7609-216">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="b7609-216">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="b7609-217">Il controller 6-DOF è acceso, ma non è possibile monitorarlo.</span><span class="sxs-lookup"><span data-stu-id="b7609-217">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="b7609-218">Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="b7609-218">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="b7609-219">Pulsanti supportati in un controller 6-DOF simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-219">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="b7609-220">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. None**</span><span class="sxs-lookup"><span data-stu-id="b7609-220">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="b7609-221">Valore sentinella utilizzato per indicare l'assenza di pulsanti.</span><span class="sxs-lookup"><span data-stu-id="b7609-221">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="b7609-222">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Home**</span><span class="sxs-lookup"><span data-stu-id="b7609-222">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="b7609-223">Viene premuto il pulsante Home.</span><span class="sxs-lookup"><span data-stu-id="b7609-223">The Home button is pressed.</span></span>

<span data-ttu-id="b7609-224">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. menu**</span><span class="sxs-lookup"><span data-stu-id="b7609-224">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="b7609-225">Viene premuto il pulsante di menu.</span><span class="sxs-lookup"><span data-stu-id="b7609-225">The Menu button is pressed.</span></span>

<span data-ttu-id="b7609-226">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Grip**</span><span class="sxs-lookup"><span data-stu-id="b7609-226">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="b7609-227">Viene premuto il pulsante del grip.</span><span class="sxs-lookup"><span data-stu-id="b7609-227">The Grip button is pressed.</span></span>

<span data-ttu-id="b7609-228">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="b7609-228">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="b7609-229">Il TouchPad è premuto.</span><span class="sxs-lookup"><span data-stu-id="b7609-229">The TouchPad is pressed.</span></span>

<span data-ttu-id="b7609-230">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Select**</span><span class="sxs-lookup"><span data-stu-id="b7609-230">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="b7609-231">Viene premuto il pulsante Seleziona.</span><span class="sxs-lookup"><span data-stu-id="b7609-231">The Select button is pressed.</span></span>

<span data-ttu-id="b7609-232">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="b7609-232">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="b7609-233">Il TouchPad viene toccato.</span><span class="sxs-lookup"><span data-stu-id="b7609-233">The TouchPad is touched.</span></span>

<span data-ttu-id="b7609-234">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. levetta**</span><span class="sxs-lookup"><span data-stu-id="b7609-234">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="b7609-235">Viene premuto levetta.</span><span class="sxs-lookup"><span data-stu-id="b7609-235">The Thumbstick is pressed.</span></span>

<span data-ttu-id="b7609-236">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. max**</span><span class="sxs-lookup"><span data-stu-id="b7609-236">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="b7609-237">Pulsante massimo valido.</span><span class="sxs-lookup"><span data-stu-id="b7609-237">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="b7609-238">Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="b7609-238">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="b7609-239">Stato di calibrazione degli occhi simulati</span><span class="sxs-lookup"><span data-stu-id="b7609-239">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="b7609-240">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. non disponibile**</span><span class="sxs-lookup"><span data-stu-id="b7609-240">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="b7609-241">La calibrazione degli occhi non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="b7609-241">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="b7609-242">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Ready**</span><span class="sxs-lookup"><span data-stu-id="b7609-242">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="b7609-243">Gli occhi sono stati calibrati.</span><span class="sxs-lookup"><span data-stu-id="b7609-243">The eyes have been calibrated.</span></span>  <span data-ttu-id="b7609-244">Si tratta del valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="b7609-244">This is the default value.</span></span>

<span data-ttu-id="b7609-245">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configusando**</span><span class="sxs-lookup"><span data-stu-id="b7609-245">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="b7609-246">Gli occhi vengono calibrati.</span><span class="sxs-lookup"><span data-stu-id="b7609-246">The eyes are being calibrated.</span></span>

<span data-ttu-id="b7609-247">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="b7609-247">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="b7609-248">È necessario calibrare gli occhi.</span><span class="sxs-lookup"><span data-stu-id="b7609-248">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="b7609-249">Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="b7609-249">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="b7609-250">Accuratezza del rilevamento di una giunzione della mano.</span><span class="sxs-lookup"><span data-stu-id="b7609-250">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="b7609-251">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. non disponibile**</span><span class="sxs-lookup"><span data-stu-id="b7609-251">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="b7609-252">Il giunto non viene rilevato.</span><span class="sxs-lookup"><span data-stu-id="b7609-252">The joint isn't tracked.</span></span>

<span data-ttu-id="b7609-253">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. approssimate**</span><span class="sxs-lookup"><span data-stu-id="b7609-253">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="b7609-254">La posizione congiunta viene dedotta.</span><span class="sxs-lookup"><span data-stu-id="b7609-254">The joint position is inferred.</span></span>

<span data-ttu-id="b7609-255">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. Visible**</span><span class="sxs-lookup"><span data-stu-id="b7609-255">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="b7609-256">Il giunto è completamente monitorato.</span><span class="sxs-lookup"><span data-stu-id="b7609-256">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="b7609-257">Microsoft. PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="b7609-257">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="b7609-258">Accuratezza del rilevamento di una giunzione della mano.</span><span class="sxs-lookup"><span data-stu-id="b7609-258">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="b7609-259">**Microsoft. PerceptionSimulation. SimulatedHandPose. Closed**</span><span class="sxs-lookup"><span data-stu-id="b7609-259">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="b7609-260">Le giunzioni del dito della mano sono configurate in modo da riflettere una posa chiusa.</span><span class="sxs-lookup"><span data-stu-id="b7609-260">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="b7609-261">**Microsoft. PerceptionSimulation. SimulatedHandPose. Open**</span><span class="sxs-lookup"><span data-stu-id="b7609-261">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="b7609-262">Le giunzioni del dito della mano sono configurate in modo da riflettere una posa aperta.</span><span class="sxs-lookup"><span data-stu-id="b7609-262">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="b7609-263">**Microsoft. PerceptionSimulation. SimulatedHandPose. Point**</span><span class="sxs-lookup"><span data-stu-id="b7609-263">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="b7609-264">Le giunzioni del dito della mano sono configurate in modo da riflettere una posa di puntamento.</span><span class="sxs-lookup"><span data-stu-id="b7609-264">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="b7609-265">**Microsoft. PerceptionSimulation. SimulatedHandPose. Pinch**</span><span class="sxs-lookup"><span data-stu-id="b7609-265">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="b7609-266">Le giunzioni del dito della mano sono configurate in modo da riflettere una puntura.</span><span class="sxs-lookup"><span data-stu-id="b7609-266">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="b7609-267">**Microsoft. PerceptionSimulation. SimulatedHandPose. max**</span><span class="sxs-lookup"><span data-stu-id="b7609-267">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="b7609-268">Valore massimo valido per SimulatedHandPose.</span><span class="sxs-lookup"><span data-stu-id="b7609-268">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="b7609-269">Microsoft. PerceptionSimulation. PlaybackState</span><span class="sxs-lookup"><span data-stu-id="b7609-269">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="b7609-270">Descrive lo stato di una riproduzione.</span><span class="sxs-lookup"><span data-stu-id="b7609-270">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="b7609-271">**Microsoft. PerceptionSimulation. PlaybackState. Stopped**</span><span class="sxs-lookup"><span data-stu-id="b7609-271">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="b7609-272">La registrazione è attualmente arrestata e pronta per la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="b7609-272">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="b7609-273">**Microsoft. PerceptionSimulation. PlaybackState. playing**</span><span class="sxs-lookup"><span data-stu-id="b7609-273">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="b7609-274">La registrazione è attualmente in riproduzione.</span><span class="sxs-lookup"><span data-stu-id="b7609-274">The recording is currently playing.</span></span>

<span data-ttu-id="b7609-275">**Microsoft. PerceptionSimulation. PlaybackState. Paused**</span><span class="sxs-lookup"><span data-stu-id="b7609-275">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="b7609-276">La registrazione è attualmente sospesa.</span><span class="sxs-lookup"><span data-stu-id="b7609-276">The recording is currently paused.</span></span>

<span data-ttu-id="b7609-277">**Microsoft. PerceptionSimulation. PlaybackState. end**</span><span class="sxs-lookup"><span data-stu-id="b7609-277">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="b7609-278">La registrazione ha raggiunto la fine.</span><span class="sxs-lookup"><span data-stu-id="b7609-278">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="b7609-279">Microsoft. PerceptionSimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="b7609-279">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="b7609-280">Descrive un vettore a tre componenti, che può descrivere un punto o un vettore nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="b7609-280">Describes a three components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="b7609-281">**Microsoft. PerceptionSimulation. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="b7609-281">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="b7609-282">Componente X del vettore.</span><span class="sxs-lookup"><span data-stu-id="b7609-282">The X component of the vector.</span></span>

<span data-ttu-id="b7609-283">**Microsoft. PerceptionSimulation. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="b7609-283">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="b7609-284">Componente Y del vettore.</span><span class="sxs-lookup"><span data-stu-id="b7609-284">The Y component of the vector.</span></span>

<span data-ttu-id="b7609-285">**Microsoft. PerceptionSimulation. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="b7609-285">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="b7609-286">Componente Z del vettore.</span><span class="sxs-lookup"><span data-stu-id="b7609-286">The Z component of the vector.</span></span>

<span data-ttu-id="b7609-287">**Microsoft. PerceptionSimulation. Vector3. #ctor (System. Single, System. Single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="b7609-287">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="b7609-288">Costruire un nuovo Vector3.</span><span class="sxs-lookup"><span data-stu-id="b7609-288">Construct a new Vector3.</span></span>

<span data-ttu-id="b7609-289">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-289">Parameters</span></span>
* <span data-ttu-id="b7609-290">x: componente x del vettore.</span><span class="sxs-lookup"><span data-stu-id="b7609-290">x - The x component of the vector.</span></span>
* <span data-ttu-id="b7609-291">y: componente y del vettore.</span><span class="sxs-lookup"><span data-stu-id="b7609-291">y - The y component of the vector.</span></span>
* <span data-ttu-id="b7609-292">z: componente z del vettore.</span><span class="sxs-lookup"><span data-stu-id="b7609-292">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="b7609-293">Microsoft. PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="b7609-293">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="b7609-294">Descrive una rotazione di tre componenti.</span><span class="sxs-lookup"><span data-stu-id="b7609-294">Describes a three components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="b7609-295">**Microsoft. PerceptionSimulation. Rotation3. Pitch**</span><span class="sxs-lookup"><span data-stu-id="b7609-295">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="b7609-296">Componente pitch della rotazione, verso il basso attorno all'asse X.</span><span class="sxs-lookup"><span data-stu-id="b7609-296">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="b7609-297">**Microsoft. PerceptionSimulation. Rotation3. imbardata**</span><span class="sxs-lookup"><span data-stu-id="b7609-297">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="b7609-298">Componente di imbardata della rotazione, immediatamente intorno all'asse Y.</span><span class="sxs-lookup"><span data-stu-id="b7609-298">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="b7609-299">**Microsoft. PerceptionSimulation. Rotation3. roll**</span><span class="sxs-lookup"><span data-stu-id="b7609-299">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="b7609-300">Componente di roll della rotazione, immediatamente intorno all'asse Z.</span><span class="sxs-lookup"><span data-stu-id="b7609-300">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="b7609-301">**Microsoft. PerceptionSimulation. Rotation3. #ctor (System. Single, System. Single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="b7609-301">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="b7609-302">Costruire un nuovo Rotation3.</span><span class="sxs-lookup"><span data-stu-id="b7609-302">Construct a new Rotation3.</span></span>

<span data-ttu-id="b7609-303">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-303">Parameters</span></span>
* <span data-ttu-id="b7609-304">Pitch: componente pitch della rotazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-304">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="b7609-305">imbardata: componente imbardata della rotazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-305">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="b7609-306">Roll-il componente roll della rotazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-306">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="b7609-307">Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="b7609-307">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="b7609-308">Descrive la configurazione di un insieme in una mano simulata.</span><span class="sxs-lookup"><span data-stu-id="b7609-308">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="b7609-309">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Position**</span><span class="sxs-lookup"><span data-stu-id="b7609-309">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="b7609-310">Posizione della giunzione.</span><span class="sxs-lookup"><span data-stu-id="b7609-310">The position of the joint.</span></span>

<span data-ttu-id="b7609-311">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Rotation**</span><span class="sxs-lookup"><span data-stu-id="b7609-311">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="b7609-312">Rotazione della giunzione.</span><span class="sxs-lookup"><span data-stu-id="b7609-312">The rotation of the joint.</span></span>

<span data-ttu-id="b7609-313">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="b7609-313">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="b7609-314">Accuratezza del rilevamento della giunzione.</span><span class="sxs-lookup"><span data-stu-id="b7609-314">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="b7609-315">Microsoft. PerceptionSimulation. tronco</span><span class="sxs-lookup"><span data-stu-id="b7609-315">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="b7609-316">Descrive una vista tronco, usata in genere da una fotocamera.</span><span class="sxs-lookup"><span data-stu-id="b7609-316">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="b7609-317">**Microsoft. PerceptionSimulation. tronco. near**</span><span class="sxs-lookup"><span data-stu-id="b7609-317">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="b7609-318">Distanza minima contenuta in tronco.</span><span class="sxs-lookup"><span data-stu-id="b7609-318">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="b7609-319">**Microsoft. PerceptionSimulation. tronco. lontano**</span><span class="sxs-lookup"><span data-stu-id="b7609-319">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="b7609-320">Distanza massima contenuta in tronco.</span><span class="sxs-lookup"><span data-stu-id="b7609-320">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="b7609-321">**Microsoft. PerceptionSimulation. tronco. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="b7609-321">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="b7609-322">Campo orizzontale della visualizzazione di tronco, in radianti (minore di PI).</span><span class="sxs-lookup"><span data-stu-id="b7609-322">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="b7609-323">**Microsoft. PerceptionSimulation. tronco. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="b7609-323">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="b7609-324">Rapporto tra il campo orizzontale e la visualizzazione e il campo verticale della visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-324">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="b7609-325">Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration</span><span class="sxs-lookup"><span data-stu-id="b7609-325">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="b7609-326">Descrive la configurazione del display simulato dell'auricolare.</span><span class="sxs-lookup"><span data-stu-id="b7609-326">Describes the configuration of the simulated headset's display.</span></span>

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

<span data-ttu-id="b7609-327">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**</span><span class="sxs-lookup"><span data-stu-id="b7609-327">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="b7609-328">Trasformazione dal centro della parte centrale all'occhio sinistro per il rendering stereo.</span><span class="sxs-lookup"><span data-stu-id="b7609-328">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="b7609-329">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="b7609-329">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="b7609-330">Rotazione dell'occhio sinistro a scopo di rendering stereo.</span><span class="sxs-lookup"><span data-stu-id="b7609-330">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="b7609-331">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**</span><span class="sxs-lookup"><span data-stu-id="b7609-331">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="b7609-332">Trasformazione dal centro dell'inizio all'occhio destro per il rendering stereo.</span><span class="sxs-lookup"><span data-stu-id="b7609-332">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="b7609-333">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="b7609-333">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="b7609-334">Rotazione dell'occhio destro per il rendering stereo.</span><span class="sxs-lookup"><span data-stu-id="b7609-334">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="b7609-335">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. dpi**</span><span class="sxs-lookup"><span data-stu-id="b7609-335">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="b7609-336">Valore di dpi segnalato dal sistema per il rendering stereo.</span><span class="sxs-lookup"><span data-stu-id="b7609-336">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="b7609-337">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. ApplyEyeTransforms**</span><span class="sxs-lookup"><span data-stu-id="b7609-337">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="b7609-338">Indica se i valori specificati per le trasformazioni a sinistra e a destra devono essere considerati validi e applicati al sistema in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="b7609-338">Whether the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="b7609-339">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**</span><span class="sxs-lookup"><span data-stu-id="b7609-339">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="b7609-340">Indica se il valore specificato per la funzione DPI deve essere considerato valido e applicato al sistema in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="b7609-340">Whether the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="b7609-341">Microsoft. PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="b7609-341">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="b7609-342">Radice per la generazione dei pacchetti usati per controllare un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b7609-342">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="b7609-343">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Device**</span><span class="sxs-lookup"><span data-stu-id="b7609-343">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="b7609-344">Recuperare l'oggetto dispositivo simulato che interpreta l'uomo simulato e il mondo simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-344">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="b7609-345">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Human**</span><span class="sxs-lookup"><span data-stu-id="b7609-345">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="b7609-346">Recuperare l'oggetto che controlla l'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-346">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="b7609-347">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Reset**</span><span class="sxs-lookup"><span data-stu-id="b7609-347">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="b7609-348">Reimposta lo stato predefinito della simulazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-348">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="b7609-349">Microsoft. PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="b7609-349">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="b7609-350">Interfaccia che descrive il dispositivo, che interpreta il mondo simulato e l'uomo simulato</span><span class="sxs-lookup"><span data-stu-id="b7609-350">Interface describing the device, which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="b7609-351">**Microsoft. PerceptionSimulation. ISimulatedDevice. HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="b7609-351">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="b7609-352">Recuperare l'Head Tracker dal dispositivo simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-352">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="b7609-353">**Microsoft. PerceptionSimulation. ISimulatedDevice. HandTracker**</span><span class="sxs-lookup"><span data-stu-id="b7609-353">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="b7609-354">Recuperare il Tracker mano dal dispositivo simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-354">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="b7609-355">**Microsoft. PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (Microsoft. PerceptionSimulation. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="b7609-355">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="b7609-356">Impostare le proprietà del dispositivo simulato in modo che corrispondano al tipo di dispositivo specificato.</span><span class="sxs-lookup"><span data-stu-id="b7609-356">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="b7609-357">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-357">Parameters</span></span>
* <span data-ttu-id="b7609-358">Tipo: nuovo tipo di dispositivo simulato</span><span class="sxs-lookup"><span data-stu-id="b7609-358">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="b7609-359">Microsoft. PerceptionSimulation. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="b7609-359">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="b7609-360">Sono disponibili proprietà aggiuntive eseguendo il cast di ISimulatedDevice a ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="b7609-360">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="b7609-361">**Microsoft. PerceptionSimulation. ISimulatedDevice2. IsUserPresent**</span><span class="sxs-lookup"><span data-stu-id="b7609-361">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="b7609-362">Recuperare o impostare un valore che indica se l'uomo simulato sta attivamente indossando l'auricolare.</span><span class="sxs-lookup"><span data-stu-id="b7609-362">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="b7609-363">**Microsoft. PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="b7609-363">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="b7609-364">Recuperare o impostare le proprietà della visualizzazione simulata.</span><span class="sxs-lookup"><span data-stu-id="b7609-364">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="b7609-365">Microsoft. PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="b7609-365">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="b7609-366">Interfaccia che descrive la parte del dispositivo simulato che tiene traccia del titolo dell'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-366">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="b7609-367">**Microsoft. PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="b7609-367">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="b7609-368">Recupera e imposta la modalità di rilevamento Head corrente.</span><span class="sxs-lookup"><span data-stu-id="b7609-368">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="b7609-369">Microsoft. PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="b7609-369">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="b7609-370">Interfaccia che descrive la parte del dispositivo simulato che tiene traccia delle mani dell'uomo simulato</span><span class="sxs-lookup"><span data-stu-id="b7609-370">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="b7609-371">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="b7609-371">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="b7609-372">Recuperare la posizione del nodo con la relazione con il mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="b7609-372">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="b7609-373">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Position**</span><span class="sxs-lookup"><span data-stu-id="b7609-373">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="b7609-374">Recuperare e impostare la posizione della traccia a mano simulata, relativa al centro della testa.</span><span class="sxs-lookup"><span data-stu-id="b7609-374">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="b7609-375">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Pitch**</span><span class="sxs-lookup"><span data-stu-id="b7609-375">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="b7609-376">Recuperare e impostare il passo verso il basso della traccia a mano simulata.</span><span class="sxs-lookup"><span data-stu-id="b7609-376">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="b7609-377">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="b7609-377">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="b7609-378">Recuperare e impostare se il tronco della traccia a mano simulata viene ignorato.</span><span class="sxs-lookup"><span data-stu-id="b7609-378">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="b7609-379">Quando viene ignorato, entrambe le mani sono sempre visibili.</span><span class="sxs-lookup"><span data-stu-id="b7609-379">When ignored, both hands are always visible.</span></span> <span data-ttu-id="b7609-380">Quando non vengono ignorate (impostazione predefinita), le mani sono visibili solo quando si trovano all'interno del tronco della traccia a mano.</span><span class="sxs-lookup"><span data-stu-id="b7609-380">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="b7609-381">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. tronco**</span><span class="sxs-lookup"><span data-stu-id="b7609-381">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="b7609-382">Recuperare e impostare le proprietà tronco usate per determinare se le mani sono visibili per la traccia a mano simulata.</span><span class="sxs-lookup"><span data-stu-id="b7609-382">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="b7609-383">Microsoft. PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="b7609-383">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="b7609-384">Interfaccia di primo livello per il controllo dell'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-384">Top-level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="b7609-385">**Microsoft. PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="b7609-385">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="b7609-386">Recuperare e impostare la posizione del nodo con la relazione con il mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="b7609-386">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="b7609-387">La posizione corrisponde a un punto al centro dei piedi dell'uomo.</span><span class="sxs-lookup"><span data-stu-id="b7609-387">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="b7609-388">**Microsoft. PerceptionSimulation. ISimulatedHuman. Direction**</span><span class="sxs-lookup"><span data-stu-id="b7609-388">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="b7609-389">Recuperare e impostare la direzione dei visi umani simulati nel mondo.</span><span class="sxs-lookup"><span data-stu-id="b7609-389">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="b7609-390">0 radianti si affacciano sull'asse Z negativo.</span><span class="sxs-lookup"><span data-stu-id="b7609-390">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="b7609-391">Radianti positivi ruotano in senso orario sull'asse Y.</span><span class="sxs-lookup"><span data-stu-id="b7609-391">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="b7609-392">**Microsoft. PerceptionSimulation. ISimulatedHuman. Height**</span><span class="sxs-lookup"><span data-stu-id="b7609-392">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="b7609-393">Recuperare e impostare l'altezza dell'oggetto umano simulato, in metri.</span><span class="sxs-lookup"><span data-stu-id="b7609-393">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="b7609-394">**Microsoft. PerceptionSimulation. ISimulatedHuman. Mancini**</span><span class="sxs-lookup"><span data-stu-id="b7609-394">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="b7609-395">Recuperare il lato sinistro dell'oggetto umano simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-395">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="b7609-396">**Microsoft. PerceptionSimulation. ISimulatedHuman. destra**</span><span class="sxs-lookup"><span data-stu-id="b7609-396">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="b7609-397">Recuperare la mano giusta dell'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-397">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="b7609-398">**Microsoft. PerceptionSimulation. ISimulatedHuman. Head**</span><span class="sxs-lookup"><span data-stu-id="b7609-398">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="b7609-399">Recuperare l'intestazione dell'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-399">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="b7609-400">**Microsoft. PerceptionSimulation. ISimulatedHuman. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="b7609-400">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="b7609-401">Spostare l'oggetto umano simulato rispetto alla posizione corrente, in metri.</span><span class="sxs-lookup"><span data-stu-id="b7609-401">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="b7609-402">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-402">Parameters</span></span>
* <span data-ttu-id="b7609-403">Translation: la traduzione da spostare rispetto alla posizione corrente.</span><span class="sxs-lookup"><span data-stu-id="b7609-403">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="b7609-404">**Microsoft. PerceptionSimulation. ISimulatedHuman. Rotate (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="b7609-404">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="b7609-405">Ruotare l'oggetto umano simulato rispetto alla direzione corrente, in senso orario sull'asse Y</span><span class="sxs-lookup"><span data-stu-id="b7609-405">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="b7609-406">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-406">Parameters</span></span>
* <span data-ttu-id="b7609-407">radianti: la quantità da ruotare intorno all'asse Y.</span><span class="sxs-lookup"><span data-stu-id="b7609-407">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="b7609-408">Microsoft. PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="b7609-408">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="b7609-409">Sono disponibili proprietà aggiuntive eseguendo il cast di ISimulatedHuman a ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="b7609-409">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="b7609-410">**Microsoft. PerceptionSimulation. ISimulatedHuman2. LeftController**</span><span class="sxs-lookup"><span data-stu-id="b7609-410">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="b7609-411">Recuperare il controller 6-DOF a sinistra.</span><span class="sxs-lookup"><span data-stu-id="b7609-411">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="b7609-412">**Microsoft. PerceptionSimulation. ISimulatedHuman2. RightController**</span><span class="sxs-lookup"><span data-stu-id="b7609-412">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="b7609-413">Recuperare il controller 6-DOF a destra.</span><span class="sxs-lookup"><span data-stu-id="b7609-413">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="b7609-414">Microsoft. PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="b7609-414">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="b7609-415">Interfaccia che descrive una mano dell'uomo simulato</span><span class="sxs-lookup"><span data-stu-id="b7609-415">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="b7609-416">**Microsoft. PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="b7609-416">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="b7609-417">Recuperare la posizione del nodo con la relazione con il mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="b7609-417">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="b7609-418">**Microsoft. PerceptionSimulation. ISimulatedHand. Position**</span><span class="sxs-lookup"><span data-stu-id="b7609-418">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="b7609-419">Recuperare e impostare la posizione della mano simulata rispetto all'oggetto umano, in metri.</span><span class="sxs-lookup"><span data-stu-id="b7609-419">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="b7609-420">**Microsoft. PerceptionSimulation. ISimulatedHand. Activated**</span><span class="sxs-lookup"><span data-stu-id="b7609-420">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="b7609-421">Recuperare e impostare se la mano è attualmente attivata.</span><span class="sxs-lookup"><span data-stu-id="b7609-421">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="b7609-422">**Microsoft. PerceptionSimulation. ISimulatedHand. Visible**</span><span class="sxs-lookup"><span data-stu-id="b7609-422">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="b7609-423">Recuperare se la mano è attualmente visibile a SimulatedDevice (ovvero se si trova in una posizione che deve essere rilevata da HandTracker).</span><span class="sxs-lookup"><span data-stu-id="b7609-423">Retrieve whether the hand is currently visible to the SimulatedDevice (that is, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="b7609-424">**Microsoft. PerceptionSimulation. ISimulatedHand. EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="b7609-424">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="b7609-425">Spostare la mano in modo che sia visibile a SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="b7609-425">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="b7609-426">**Microsoft. PerceptionSimulation. ISimulatedHand. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="b7609-426">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="b7609-427">Spostare la posizione della mano simulata rispetto alla posizione corrente, in metri.</span><span class="sxs-lookup"><span data-stu-id="b7609-427">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="b7609-428">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-428">Parameters</span></span>
* <span data-ttu-id="b7609-429">Translation: la quantità per tradurre la mano simulata.</span><span class="sxs-lookup"><span data-stu-id="b7609-429">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="b7609-430">**Microsoft. PerceptionSimulation. ISimulatedHand. PerformGesture (Microsoft. PerceptionSimulation. SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="b7609-430">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="b7609-431">Eseguire un movimento usando la mano simulata.</span><span class="sxs-lookup"><span data-stu-id="b7609-431">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="b7609-432">Verrà rilevato solo dal sistema se la mano è abilitata.</span><span class="sxs-lookup"><span data-stu-id="b7609-432">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="b7609-433">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-433">Parameters</span></span>
* <span data-ttu-id="b7609-434">Gesture: movimento da eseguire.</span><span class="sxs-lookup"><span data-stu-id="b7609-434">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="b7609-435">Microsoft. PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="b7609-435">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="b7609-436">Sono disponibili proprietà aggiuntive eseguendo il cast di un ISimulatedHand a ISimulatedHand2.</span><span class="sxs-lookup"><span data-stu-id="b7609-436">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="b7609-437">**Microsoft. PerceptionSimulation. ISimulatedHand2. Orientation**</span><span class="sxs-lookup"><span data-stu-id="b7609-437">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="b7609-438">Recuperare o impostare la rotazione della mano simulata.</span><span class="sxs-lookup"><span data-stu-id="b7609-438">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="b7609-439">Radianti positivi ruotano in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="b7609-439">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="b7609-440">Microsoft. PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="b7609-440">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="b7609-441">Sono disponibili proprietà aggiuntive eseguendo il cast di un ISimulatedHand in ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="b7609-441">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="b7609-442">**Microsoft. PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="b7609-442">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="b7609-443">Ottiene la configurazione congiunta per il giunto specificato.</span><span class="sxs-lookup"><span data-stu-id="b7609-443">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="b7609-444">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="b7609-444">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="b7609-445">Imposta la configurazione congiunta per il giunto specificato.</span><span class="sxs-lookup"><span data-stu-id="b7609-445">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="b7609-446">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="b7609-446">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="b7609-447">Impostare la mano su una forma nota con un flag facoltativo a cui aggiungere un'animazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-447">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="b7609-448">Nota: l'animazione non comporterà l'aggiunta immediata di giunzioni che riflettono le configurazioni finali.</span><span class="sxs-lookup"><span data-stu-id="b7609-448">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="b7609-449">Microsoft. PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="b7609-449">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="b7609-450">Interfaccia che descrive l'intestazione dell'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-450">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="b7609-451">**Microsoft. PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="b7609-451">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="b7609-452">Recuperare la posizione del nodo con la relazione con il mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="b7609-452">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="b7609-453">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotation**</span><span class="sxs-lookup"><span data-stu-id="b7609-453">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="b7609-454">Recuperare la rotazione della testa simulata.</span><span class="sxs-lookup"><span data-stu-id="b7609-454">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="b7609-455">Radianti positivi ruotano in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="b7609-455">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="b7609-456">**Microsoft. PerceptionSimulation. ISimulatedHead. Diametr**</span><span class="sxs-lookup"><span data-stu-id="b7609-456">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="b7609-457">Recuperare il diametro della testa simulata.</span><span class="sxs-lookup"><span data-stu-id="b7609-457">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="b7609-458">Questo valore viene usato per determinare il centro della testa (punto di rotazione).</span><span class="sxs-lookup"><span data-stu-id="b7609-458">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="b7609-459">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="b7609-459">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="b7609-460">Ruota la testa simulata rispetto alla rotazione corrente.</span><span class="sxs-lookup"><span data-stu-id="b7609-460">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="b7609-461">Radianti positivi ruotano in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="b7609-461">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="b7609-462">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-462">Parameters</span></span>
* <span data-ttu-id="b7609-463">Rotation: quantità da ruotare.</span><span class="sxs-lookup"><span data-stu-id="b7609-463">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="b7609-464">Microsoft. PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="b7609-464">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="b7609-465">Sono disponibili proprietà aggiuntive eseguendo il cast di un ISimulatedHead in ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="b7609-465">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="b7609-466">**Microsoft. PerceptionSimulation. ISimulatedHead2. Eyes**</span><span class="sxs-lookup"><span data-stu-id="b7609-466">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="b7609-467">Recuperare gli occhi dell'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-467">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="b7609-468">Microsoft. PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="b7609-468">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="b7609-469">Interfaccia che descrive un controller 6-DOF associato all'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-469">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="b7609-470">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="b7609-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="b7609-471">Recuperare la posizione del nodo con la relazione con il mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="b7609-471">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="b7609-472">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. status**</span><span class="sxs-lookup"><span data-stu-id="b7609-472">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="b7609-473">Recuperare o impostare lo stato corrente del controller.</span><span class="sxs-lookup"><span data-stu-id="b7609-473">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="b7609-474">Lo stato del controller deve essere impostato su un valore diverso da off prima che tutte le chiamate per lo spostamento, la rotazione o la pressione dei pulsanti abbiano esito positivo.</span><span class="sxs-lookup"><span data-stu-id="b7609-474">The controller status must be set to a value other than Off before any calls to move, rotate, or press buttons will succeed.</span></span>

<span data-ttu-id="b7609-475">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Position**</span><span class="sxs-lookup"><span data-stu-id="b7609-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="b7609-476">Recuperare o impostare la posizione del controller simulato rispetto all'oggetto umano, in metri.</span><span class="sxs-lookup"><span data-stu-id="b7609-476">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="b7609-477">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Orientation**</span><span class="sxs-lookup"><span data-stu-id="b7609-477">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="b7609-478">Recupera o imposta l'orientamento del controller simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-478">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="b7609-479">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="b7609-479">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="b7609-480">Spostare la posizione del controller simulato rispetto alla posizione corrente, in metri.</span><span class="sxs-lookup"><span data-stu-id="b7609-480">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="b7609-481">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-481">Parameters</span></span>
* <span data-ttu-id="b7609-482">Translation: quantità di conversione del controller simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-482">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="b7609-483">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. PressButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="b7609-483">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="b7609-484">Premere un pulsante sul controller simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-484">Press a button on the simulated controller.</span></span>  <span data-ttu-id="b7609-485">Verrà rilevato solo dal sistema se il controller è abilitato.</span><span class="sxs-lookup"><span data-stu-id="b7609-485">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="b7609-486">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-486">Parameters</span></span>
* <span data-ttu-id="b7609-487">Button-pulsante da premere.</span><span class="sxs-lookup"><span data-stu-id="b7609-487">button - The button to press.</span></span>

<span data-ttu-id="b7609-488">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. ReleaseButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="b7609-488">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="b7609-489">Rilasciare un pulsante sul controller simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-489">Release a button on the simulated controller.</span></span>  <span data-ttu-id="b7609-490">Verrà rilevato solo dal sistema se il controller è abilitato.</span><span class="sxs-lookup"><span data-stu-id="b7609-490">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="b7609-491">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-491">Parameters</span></span>
* <span data-ttu-id="b7609-492">Button-pulsante da rilasciare.</span><span class="sxs-lookup"><span data-stu-id="b7609-492">button - The button to release.</span></span>

<span data-ttu-id="b7609-493">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="b7609-493">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="b7609-494">Ottiene la posizione di un dito simulato nel touchpad del controller simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-494">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="b7609-495">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-495">Parameters</span></span>
* <span data-ttu-id="b7609-496">x: posizione orizzontale del dito.</span><span class="sxs-lookup"><span data-stu-id="b7609-496">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="b7609-497">y: posizione verticale del dito.</span><span class="sxs-lookup"><span data-stu-id="b7609-497">y - The vertical position of the finger.</span></span>

<span data-ttu-id="b7609-498">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="b7609-498">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="b7609-499">Imposta la posizione di un dito simulato nel touchpad del controller simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-499">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="b7609-500">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-500">Parameters</span></span>
* <span data-ttu-id="b7609-501">x: posizione orizzontale del dito.</span><span class="sxs-lookup"><span data-stu-id="b7609-501">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="b7609-502">y: posizione verticale del dito.</span><span class="sxs-lookup"><span data-stu-id="b7609-502">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="b7609-503">Microsoft. PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="b7609-503">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="b7609-504">Sono disponibili proprietà e metodi aggiuntivi eseguendo il cast di un ISimulatedSixDofController in ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="b7609-504">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="b7609-505">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="b7609-505">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="b7609-506">Ottiene la posizione della levetta simulata sul controller simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-506">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="b7609-507">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-507">Parameters</span></span>
* <span data-ttu-id="b7609-508">x: posizione orizzontale di levetta.</span><span class="sxs-lookup"><span data-stu-id="b7609-508">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="b7609-509">y: posizione verticale del levetta.</span><span class="sxs-lookup"><span data-stu-id="b7609-509">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="b7609-510">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="b7609-510">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="b7609-511">Impostare la posizione della levetta simulata sul controller simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-511">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="b7609-512">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-512">Parameters</span></span>
* <span data-ttu-id="b7609-513">x: posizione orizzontale di levetta.</span><span class="sxs-lookup"><span data-stu-id="b7609-513">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="b7609-514">y: posizione verticale del levetta.</span><span class="sxs-lookup"><span data-stu-id="b7609-514">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="b7609-515">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="b7609-515">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="b7609-516">Recuperare o impostare il livello di batteria del controller simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-516">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="b7609-517">Il valore deve essere maggiore di 0,0 e minore o uguale a 100,0.</span><span class="sxs-lookup"><span data-stu-id="b7609-517">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="b7609-518">Microsoft. PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="b7609-518">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="b7609-519">Interfaccia che descrive gli occhi dell'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-519">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="b7609-520">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotation**</span><span class="sxs-lookup"><span data-stu-id="b7609-520">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="b7609-521">Recuperare la rotazione degli occhi simulati.</span><span class="sxs-lookup"><span data-stu-id="b7609-521">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="b7609-522">Radianti positivi ruotano in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="b7609-522">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="b7609-523">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="b7609-523">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="b7609-524">Ruotare gli occhi simulati rispetto alla rotazione corrente.</span><span class="sxs-lookup"><span data-stu-id="b7609-524">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="b7609-525">Radianti positivi ruotano in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="b7609-525">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="b7609-526">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-526">Parameters</span></span>
* <span data-ttu-id="b7609-527">Rotation: quantità da ruotare.</span><span class="sxs-lookup"><span data-stu-id="b7609-527">rotation - The amount to rotate.</span></span>

<span data-ttu-id="b7609-528">**Microsoft. PerceptionSimulation. ISimulatedEyes. CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="b7609-528">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="b7609-529">Recupera o imposta lo stato di calibrazione degli occhi simulati.</span><span class="sxs-lookup"><span data-stu-id="b7609-529">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="b7609-530">**Microsoft. PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="b7609-530">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="b7609-531">Recuperare la posizione del nodo con la relazione con il mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="b7609-531">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="b7609-532">Microsoft. PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="b7609-532">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="b7609-533">Interfaccia per l'interazione con una singola registrazione caricata per la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="b7609-533">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="b7609-534">**Microsoft. PerceptionSimulation. ISimulationRecording. DataTypes**</span><span class="sxs-lookup"><span data-stu-id="b7609-534">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="b7609-535">Recupera l'elenco dei tipi di dati nella registrazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-535">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="b7609-536">**Microsoft. PerceptionSimulation. ISimulationRecording. state**</span><span class="sxs-lookup"><span data-stu-id="b7609-536">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="b7609-537">Recupera lo stato corrente della registrazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-537">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="b7609-538">**Microsoft. PerceptionSimulation. ISimulationRecording. Play**</span><span class="sxs-lookup"><span data-stu-id="b7609-538">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="b7609-539">Avviare la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="b7609-539">Start the playback.</span></span> <span data-ttu-id="b7609-540">Se la registrazione viene sospesa, la riproduzione riprenderà dal percorso sospeso; Se arrestata, la riproduzione inizierà dall'inizio.</span><span class="sxs-lookup"><span data-stu-id="b7609-540">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="b7609-541">Se è già in esecuzione, questa chiamata viene ignorata.</span><span class="sxs-lookup"><span data-stu-id="b7609-541">If already playing, this call is ignored.</span></span>

<span data-ttu-id="b7609-542">**Microsoft. PerceptionSimulation. ISimulationRecording. pause**</span><span class="sxs-lookup"><span data-stu-id="b7609-542">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="b7609-543">Sospende la riproduzione nella posizione corrente.</span><span class="sxs-lookup"><span data-stu-id="b7609-543">Pauses the playback at its current location.</span></span> <span data-ttu-id="b7609-544">Se la registrazione viene arrestata, la chiamata viene ignorata.</span><span class="sxs-lookup"><span data-stu-id="b7609-544">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="b7609-545">**Microsoft. PerceptionSimulation. ISimulationRecording. Seek (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="b7609-545">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="b7609-546">Cerca la registrazione per l'ora specificata, in intervalli di 100 nanosecondi dall'inizio, e viene sospesa in corrispondenza di tale posizione.</span><span class="sxs-lookup"><span data-stu-id="b7609-546">Seeks the recording to the specified time (in 100-nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="b7609-547">Se l'ora supera la fine della registrazione, viene sospesa in corrispondenza dell'ultimo frame.</span><span class="sxs-lookup"><span data-stu-id="b7609-547">If the time is beyond the end of the recording, it's paused at the last frame.</span></span>

<span data-ttu-id="b7609-548">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-548">Parameters</span></span>
* <span data-ttu-id="b7609-549">cicli: il tempo in cui eseguire la ricerca.</span><span class="sxs-lookup"><span data-stu-id="b7609-549">ticks - The time to which to seek.</span></span>

<span data-ttu-id="b7609-550">**Microsoft. PerceptionSimulation. ISimulationRecording. Stop**</span><span class="sxs-lookup"><span data-stu-id="b7609-550">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="b7609-551">Arresta la riproduzione e reimposta la posizione iniziale.</span><span class="sxs-lookup"><span data-stu-id="b7609-551">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="b7609-552">Microsoft. PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="b7609-552">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="b7609-553">Interfaccia per la ricezione delle modifiche di stato durante la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="b7609-553">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="b7609-554">**Microsoft. PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (Microsoft. PerceptionSimulation. PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="b7609-554">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="b7609-555">Chiamato quando viene modificato lo stato di riproduzione di un ISimulationRecording.</span><span class="sxs-lookup"><span data-stu-id="b7609-555">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="b7609-556">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-556">Parameters</span></span>
* <span data-ttu-id="b7609-557">newState: nuovo stato della registrazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-557">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="b7609-558">Microsoft. PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="b7609-558">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="b7609-559">Oggetto radice per la creazione di oggetti di simulazione della percezione.</span><span class="sxs-lookup"><span data-stu-id="b7609-559">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="b7609-560">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (Microsoft. PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="b7609-560">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="b7609-561">Creare sull'oggetto per generare pacchetti simulati e distribuirli al sink fornito.</span><span class="sxs-lookup"><span data-stu-id="b7609-561">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="b7609-562">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-562">Parameters</span></span>
* <span data-ttu-id="b7609-563">sink: sink che riceverà tutti i pacchetti generati.</span><span class="sxs-lookup"><span data-stu-id="b7609-563">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="b7609-564">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="b7609-564">Return value</span></span>

<span data-ttu-id="b7609-565">Gestore creato.</span><span class="sxs-lookup"><span data-stu-id="b7609-565">The created Manager.</span></span>

<span data-ttu-id="b7609-566">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System. String)**</span><span class="sxs-lookup"><span data-stu-id="b7609-566">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="b7609-567">Creare un sink che archivia tutti i pacchetti ricevuti in un file nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="b7609-567">Create a sink, which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="b7609-568">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-568">Parameters</span></span>
* <span data-ttu-id="b7609-569">Path: percorso del file da creare.</span><span class="sxs-lookup"><span data-stu-id="b7609-569">path - The path of the file to create.</span></span>

<span data-ttu-id="b7609-570">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="b7609-570">Return value</span></span>

<span data-ttu-id="b7609-571">Sink creato.</span><span class="sxs-lookup"><span data-stu-id="b7609-571">The created sink.</span></span>

<span data-ttu-id="b7609-572">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="b7609-572">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="b7609-573">Carica una registrazione dal file specificato.</span><span class="sxs-lookup"><span data-stu-id="b7609-573">Load a recording from the specified file.</span></span>

<span data-ttu-id="b7609-574">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-574">Parameters</span></span>
* <span data-ttu-id="b7609-575">Path: percorso del file da caricare.</span><span class="sxs-lookup"><span data-stu-id="b7609-575">path - The path of the file to load.</span></span>
* <span data-ttu-id="b7609-576">Factory: Factory usata dalla registrazione per la creazione di un ISimulationStreamSink quando richiesto.</span><span class="sxs-lookup"><span data-stu-id="b7609-576">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="b7609-577">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="b7609-577">Return value</span></span>

<span data-ttu-id="b7609-578">Registrazione caricata.</span><span class="sxs-lookup"><span data-stu-id="b7609-578">The loaded recording.</span></span>

<span data-ttu-id="b7609-579">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory, Microsoft. PerceptionSimulation. ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="b7609-579">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="b7609-580">Carica una registrazione dal file specificato.</span><span class="sxs-lookup"><span data-stu-id="b7609-580">Load a recording from the specified file.</span></span>

<span data-ttu-id="b7609-581">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-581">Parameters</span></span>
* <span data-ttu-id="b7609-582">Path: percorso del file da caricare.</span><span class="sxs-lookup"><span data-stu-id="b7609-582">path - The path of the file to load.</span></span>
* <span data-ttu-id="b7609-583">Factory: Factory usata dalla registrazione per la creazione di un ISimulationStreamSink quando richiesto.</span><span class="sxs-lookup"><span data-stu-id="b7609-583">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="b7609-584">callback: callback che riceve gli aggiornamenti che rigradano lo stato della registrazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-584">callback - A callback, which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="b7609-585">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="b7609-585">Return value</span></span>

<span data-ttu-id="b7609-586">Registrazione caricata.</span><span class="sxs-lookup"><span data-stu-id="b7609-586">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="b7609-587">Microsoft. PerceptionSimulation. StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="b7609-587">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="b7609-588">Vengono descritti i diversi tipi di dati di flusso.</span><span class="sxs-lookup"><span data-stu-id="b7609-588">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="b7609-589">**Microsoft. PerceptionSimulation. StreamDataTypes. None**</span><span class="sxs-lookup"><span data-stu-id="b7609-589">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="b7609-590">Valore sentinella utilizzato per indicare nessun tipo di dati di flusso.</span><span class="sxs-lookup"><span data-stu-id="b7609-590">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="b7609-591">**Microsoft. PerceptionSimulation. StreamDataTypes. Head**</span><span class="sxs-lookup"><span data-stu-id="b7609-591">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="b7609-592">Flusso di dati per la posizione e l'orientamento dell'intestazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-592">Stream of data for the position and orientation of the head.</span></span>

<span data-ttu-id="b7609-593">**Microsoft. PerceptionSimulation. StreamDataTypes. Hands**</span><span class="sxs-lookup"><span data-stu-id="b7609-593">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="b7609-594">Flusso di dati per la posizione e i movimenti delle mani.</span><span class="sxs-lookup"><span data-stu-id="b7609-594">Stream of data for the position and gestures of hands.</span></span>

<span data-ttu-id="b7609-595">**Microsoft. PerceptionSimulation. StreamDataTypes. SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="b7609-595">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="b7609-596">Flusso di dati per il mapping spaziale dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="b7609-596">Stream of data for spatial mapping of the environment.</span></span>

<span data-ttu-id="b7609-597">**Microsoft. PerceptionSimulation. StreamDataTypes. Calibration**</span><span class="sxs-lookup"><span data-stu-id="b7609-597">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="b7609-598">Flusso di dati per la taratura del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b7609-598">Stream of data for calibration of the device.</span></span> <span data-ttu-id="b7609-599">I pacchetti di calibrazione sono accettati solo da un sistema in modalità remota.</span><span class="sxs-lookup"><span data-stu-id="b7609-599">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="b7609-600">**Microsoft. PerceptionSimulation. StreamDataTypes. Environment**</span><span class="sxs-lookup"><span data-stu-id="b7609-600">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="b7609-601">Flusso di dati per l'ambiente del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b7609-601">Stream of data for the environment of the device.</span></span>

<span data-ttu-id="b7609-602">**Microsoft. PerceptionSimulation. StreamDataTypes. SixDofControllers**</span><span class="sxs-lookup"><span data-stu-id="b7609-602">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="b7609-603">Flusso di dati per i controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="b7609-603">Stream of data for motion controllers.</span></span>

<span data-ttu-id="b7609-604">**Microsoft. PerceptionSimulation. StreamDataTypes. Eyes**</span><span class="sxs-lookup"><span data-stu-id="b7609-604">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="b7609-605">Flusso di dati con gli occhi dell'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="b7609-605">Stream of data with the eyes of the simulated human.</span></span>

<span data-ttu-id="b7609-606">**Microsoft. PerceptionSimulation. StreamDataTypes. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="b7609-606">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="b7609-607">Flusso di dati con la configurazione di visualizzazione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b7609-607">Stream of data with the display configuration of the device.</span></span>

<span data-ttu-id="b7609-608">**Microsoft. PerceptionSimulation. StreamDataTypes. All**</span><span class="sxs-lookup"><span data-stu-id="b7609-608">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="b7609-609">Valore sentinella utilizzato per indicare tutti i tipi di dati registrati.</span><span class="sxs-lookup"><span data-stu-id="b7609-609">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="b7609-610">Microsoft. PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="b7609-610">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="b7609-611">Oggetto che riceve pacchetti di dati da un flusso di simulazione.</span><span class="sxs-lookup"><span data-stu-id="b7609-611">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="b7609-612">**Microsoft. PerceptionSimulation. ISimulationStreamSink. OnPacketReceived (uint length, byte [] Packet)**</span><span class="sxs-lookup"><span data-stu-id="b7609-612">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="b7609-613">Riceve un singolo pacchetto, che è tipizzato internamente e con controllo delle versioni.</span><span class="sxs-lookup"><span data-stu-id="b7609-613">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="b7609-614">Parametri</span><span class="sxs-lookup"><span data-stu-id="b7609-614">Parameters</span></span>
* <span data-ttu-id="b7609-615">length: lunghezza del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="b7609-615">length - The length of the packet.</span></span>
* <span data-ttu-id="b7609-616">Packet: dati del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="b7609-616">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="b7609-617">Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="b7609-617">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="b7609-618">Oggetto che crea ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="b7609-618">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="b7609-619">**Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink ()**</span><span class="sxs-lookup"><span data-stu-id="b7609-619">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="b7609-620">Crea una singola istanza di ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="b7609-620">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="b7609-621">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="b7609-621">Return value</span></span>

<span data-ttu-id="b7609-622">Sink creato.</span><span class="sxs-lookup"><span data-stu-id="b7609-622">The created sink.</span></span>
