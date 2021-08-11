---
title: HoloLens (prima generazione) Input 212 - Voce
description: Seguire questa procedura dettagliata per la scrittura di codice usando Unity, Visual Studio e HoloLens informazioni dettagliate sui concetti vocali.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, voice, HoloLens, Mixed Reality Academy, unity, visore VR di realtà mista, visore VR windows mixed reality, visore VR di realtà virtuale, Windows 10
ms.openlocfilehash: 75a1d32ae72a07b68fc65c40035109c468adb1080070240827eeb253eb4a03f4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207367"
---
# <a name="hololens-1st-gen-input-212-voice"></a>HoloLens (prima generazione) Input 212: Voce

>[!IMPORTANT]
>Le esercitazioni di Mixed Reality Academy sono state progettate per HoloLens (prima generazione), Unity 2017 e visori VR immersive di Realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi. Queste esercitazioni non **_verranno_** aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2 e potrebbero non essere compatibili con le versioni più recenti di Unity.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md).

[L'input](../../../design/voice-input.md) vocale offre un altro modo per interagire con gli ologrammi. I comandi vocali funzionano in modo molto naturale e semplice. Progettare i comandi vocali in modo che siano:

* Natural
* Facile da ricordare
* Contesto appropriato
* Sufficientemente distinta dalle altre opzioni all'interno dello stesso contesto

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

In [Nozioni di base MR 101](../../../develop/unity/tutorials/holograms-101.md)è stato usato KeywordRecognizer per creare due semplici comandi vocali. In MR Input 212 verranno approfondite le informazioni su come:

* Progettare comandi vocali ottimizzati per il motore HoloLens voce.
* Rendere l'utente a conoscenza dei comandi vocali disponibili.
* Confermare di aver sentito il comando vocale dell'utente.
* Comprendere cosa dice l'utente usando un riconoscimento dettatura.
* Usare un sistema di riconoscimento grammaticale per ascoltare i comandi basati su un file SRGS, o Speech Recognition Grammar Specification.

In questo corso si rivedrà Model Explorer, che è stato compilato in [MR Input 210](holograms-210.md) e [MR Input 211.](holograms-211.md)

>[!IMPORTANT]
>I video incorporati in ognuno dei capitoli seguenti sono stati registrati usando una versione precedente di Unity e mixed reality Toolkit. Anche se le istruzioni dettagliate sono accurate e aggiornate, è possibile che nei video corrispondenti siano visualizzati script e oggetti visivi non aggiornati. I video rimangono inclusi per i poster e perché i concetti trattati sono ancora applicabili.


## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>Input MR 212: Voce</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un Windows 10 pc configurato con gli strumenti [corretti installati.](../../../develop/install-the-tools.md)
* Alcune funzionalità di programmazione C# di base.
* È necessario aver completato [Mr Basics 101](../../../develop/unity/tutorials/holograms-101.md).
* L'input [MR 210](holograms-210.md)dovrebbe essere stato completato.
* L'input [MR 211](holograms-211.md)dovrebbe essere stato completato.
* Un HoloLens configurato [per lo sviluppo.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>File di progetto

* Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) richiesti dal progetto. Richiede Unity 2017.2 o versione successiva.
* Annullare l'archiviazione dei file sul desktop o in un'altra posizione facilmente raggiungibile.

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è disponibile [in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).

### <a name="errata-and-notes"></a>Errata e note

* "Abilita Just My Code" deve essere disabilitato *(* deselezionato ) in Visual Studio in Strumenti->Opzioni -debug >per poter terminare con i punti di interruzione nel codice.

## <a name="unity-setup"></a>Installazione di Unity

### <a name="instructions"></a>Istruzioni

1. Riavviare Unity.
2. Selezionare **Open** (Apri).
3. Passare alla **cartella HolographicAcademy-Ologrammi-212-Voice** precedentemente non archiviata.
4. Trovare e selezionare la **cartella Starting** Model / **Explorer (Avvio di Esplora** modelli).
5. Fare clic **sul pulsante Seleziona** cartella.
6. Nel pannello **Project** espandere la **cartella Scene.**
7. Fare doppio clic **sulla scena ModelExplorer** per caricarla in Unity.

### <a name="building"></a>Compilazione

1. In Unity selezionare **File > Build Impostazioni**.
2. Se **Scenes/ModelExplorer** non è elencato in **Scenes In Build (Scene in compilazione),** fare clic su Add Open Scenes (Aggiungi **scene** aperte) per aggiungere la scena.
3. Se si sviluppa in modo specifico per HoloLens, impostare **Dispositivo di destinazione** su **HoloLens**. In caso contrario, lasciarlo in **Qualsiasi dispositivo.**
4. Assicurarsi **che Build Type (Tipo** di compilazione) sia impostato su **D3D** e **che SDK** sia impostato su Latest **installed** (Versione più recente installata), che deve essere SDK 16299 o versione successiva.
5. Fare clic su **Compila**.
6. Creare una **nuova cartella** denominata "App".
7. Fare clic sulla **cartella App.**
8. Premere **Seleziona cartella** e Unity inizierà a compilare il progetto per Visual Studio.

Al termine dell'operazione, verrà Esplora file finestra di dialogo.

1. Aprire la **cartella App.**
2. Aprire la **soluzione Visual Studio ModelExplorer**.

Se si esegue la distribuzione HoloLens:

1. Usando la barra degli strumenti superiore Visual Studio, modificare la destinazione da Debug a **Release** e da ARM a **x86.**
2. Fare clic sulla freccia a discesa accanto al pulsante Computer locale e selezionare **Computer remoto.**
3. Immettere **l'HoloLens IP del dispositivo** e impostare Modalità di autenticazione su Universale **(protocollo non crittografato).** Fare clic su **Seleziona**. Se non si conosce l'indirizzo IP del dispositivo, Impostazioni > rete & **Internet > Opzioni avanzate**.
4. Nella barra dei menu superiore fare clic **su Debug -> Avvia** senza eseguire debug oppure premere **CTRL+F5.** Se è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario [associarlo a Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).
5. Dopo la distribuzione dell'app, chiudere **fitbox** con un **movimento di selezione.**

Se si esegue la distribuzione in un visore VR immersive:

1. Usando la barra degli strumenti superiore Visual Studio, modificare la destinazione da Debug a **Release** e da ARM a **x64.**
2. Assicurarsi che la destinazione di distribuzione sia impostata **su Computer locale.**
3. Nella barra dei menu superiore fare clic **su Debug -> Avvia** senza eseguire debug oppure premere **CTRL+F5.**
4. Dopo che l'app è stata distribuita, chiudere **Fitbox** estraendo il trigger in un controller del movimento.

>[!NOTE]
>È possibile notare alcuni errori rossi nel pannello Visual Studio errori. È possibile ignorarli. Passare al pannello Output per visualizzare lo stato di avanzamento effettivo della compilazione. Gli errori nel pannello Output richiederanno una correzione( nella maggior parte dei casi sono causati da un errore in uno script).

## <a name="chapter-1---awareness"></a>Capitolo 1 - Consapevolezza

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>Obiettivi

* Informazioni sulla progettazione dei comandi vocali Dos e **Don'ts.**
* Usare **KeywordRecognizer per** aggiungere comandi vocali basati su sguardo fisso.
* Fare in modo che gli utenti siano a conoscenza dei comandi vocali usando il **feedback del cursore.**

### <a name="voice-command-design"></a>Progettazione dei comandi vocali

In questo capitolo si apprenderà come progettare i comandi vocali. Quando si creano comandi vocali:

#### <a name="do"></a>DO

* Creare comandi concisi. Non si vuole usare "Riproduci il video attualmente *selezionato",* perché il comando non è conciso e verrebbe facilmente dimenticato dall'utente. È invece consigliabile usare: *"Riproduci video",* perché è conciso e ha più sillabe.
* Usare un vocabolario semplice. Provare sempre a usare parole e frasi comuni facili da individuare e ricordare per l'utente. Ad esempio, se l'applicazione dispone di un oggetto nota che può essere visualizzato o nascosto dalla visualizzazione, non si userà il comando *"Show Placard"*, perché "placard" è un termine usato raramente. Usare invece il comando *"Mostra nota"* per visualizzare la nota nell'applicazione.
* Mantenere la coerenza. I comandi vocali devono essere mantenuti coerenti nell'applicazione. Imagine che nell'applicazione sono presenti due scene ed entrambe contengono un pulsante per la chiusura dell'applicazione. Se la prima scena ha usato il comando *"Exit"* per attivare il pulsante, ma la seconda scena ha usato il comando *"Chiudi app",* l'utente si confonderà molto. Se la stessa funzionalità persiste in più scene, per attivarla è necessario usare lo stesso comando vocale.

#### <a name="dont"></a>Non

* Usare singoli comandi della sillaba. Ad esempio, se si crea un comando vocale per riprodurre un video, è consigliabile evitare di usare il semplice comando *"Play",* perché è solo una singola sillaba e può essere facilmente persa dal sistema. È invece consigliabile usare: *"Riproduci video",* perché è conciso e ha più sillabe.
* Usare i comandi di sistema. Il *comando "Seleziona"* è riservato dal sistema per attivare un evento Tap per l'oggetto attualmente attivo. Non usare di nuovo il *comando "Select"* in una parola chiave o in una frase, perché potrebbe non funzionare come previsto. Ad esempio, se il comando vocale per la selezione di un cubo nell'applicazione è *"Seleziona cubo",* ma l'utente stava osservando una sfera quando ha pronunciato il comando, la sfera verrà invece selezionata. Analogamente, i comandi della barra dell'app sono abilitati per la voce. Non usare i comandi vocali seguenti nella visualizzazione CoreWindow:
    1. Indietro
    2. Strumento di scorrimento
    3. Strumento zoom
    4. Strumento di trascinamento
    5. Regolare
    6. Rimuovi
* Usare suoni simili. Provare a evitare di usare comandi vocali che rima. Se si ha un'applicazione di acquisto che supporta *"Show Store"* e *"Show More"* come comandi vocali, è necessario disabilitare uno dei comandi mentre l'altro era in uso. Ad esempio, è possibile usare il pulsante *"Mostra archivio"* per aprire lo Store e quindi disabilitare tale comando quando lo store è stato visualizzato in modo che il *comando "Mostra altro"* possa essere usato per l'esplorazione.

### <a name="instructions"></a>Istruzioni

* Nel pannello Hierarchy **(Gerarchia)** di Unity usare lo strumento di ricerca per trovare **l'holoComm_screen_mesh** object.
* Fare doppio clic **sull'holoComm_screen_mesh** per visualizzarlo nella **scena**. Questo è l'orologio dell'astronauta, che risponderà ai comandi vocali.
* Nel pannello **Controllo** individuare il **componente Origine input vocale (script).**
* Espandere la **sezione Parole** chiave per visualizzare il comando vocale supportato: **Apri Communicator**.
* Fare clic sull'ingranaggio a destra, quindi **selezionare Modifica script**.
* Esplorare **SpeechInputSource.cs per** comprendere come usa **KeywordRecognizer** per aggiungere comandi vocali.

### <a name="build-and-deploy"></a>Compilazione e distribuzione

* In Unity usare File > **Build Impostazioni** per ricompilare l'applicazione.
* Aprire la **cartella App.**
* Aprire **modelExplorer Visual Studio Soluzione**.

Se il progetto è già stato compilato/distribuito in Visual Studio durante la configurazione, è possibile aprire l'istanza di Visual Studio e fare clic su 'Ricarica tutto' quando richiesto.

* In Visual Studio fare clic su **Debug -> Avvia** senza eseguire debug o premere **CTRL+F5.**
* Dopo la distribuzione dell'applicazione nel HoloLens, chiudere la casella di adattamento usando il [movimento di tocco dell'aria.](../../../design/gaze-and-commit.md#composite-gestures)
* Guarda l'orologio dell'astronauta.
* Quando l'orologio ha lo stato attivo, verificare che il cursore cambi in un microfono. Ciò fornisce un feedback che indica che l'applicazione è in ascolto di comandi vocali.
* Verificare che nell'orologio sia visualizzata una descrizione comando. Ciò consente agli utenti di individuare il comando *"Apri Communicator".*
* Mentre si guarda l'orologio, *pronunciare "Open Communicator" (Apri Communicator)* per aprire il pannello del comunicatore.

## <a name="chapter-2---acknowledgement"></a>Capitolo 2 - Riconoscimento

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>Obiettivi

* Registrare un messaggio usando l'input microfono.
* Inviare un feedback all'utente che l'applicazione sta ascoltando la voce.

>[!NOTE]
>La **funzionalità Microfono** deve essere dichiarata per poter registrare un'app dal microfono. Questa operazione viene eseguita per l'utente già in MR Input 212, ma tenere presente questa operazione per i propri progetti.
>
>1. Nell'editor di Unity passare alle impostazioni del lettore passando a "Modifica > Project Impostazioni > lettore"
>2. Fare clic sulla scheda "Universal Windows Platform"
>3. Nella sezione "Funzionalità Impostazioni > pubblicazione" controllare la **funzionalità Microfono**

### <a name="instructions"></a>Istruzioni

* Nel pannello **Gerarchia di** Unity verificare che **l'oggetto** holoComm_screen_mesh selezionato.
* Nel pannello **Inspector** (Controllo) trovare il **componente Astronaut Watch (Script).**
* Fare clic sul piccolo cubo blu impostato come valore della proprietà **Communicator Prefab.**
* Nel pannello **Project,** il **prefab** Communicator dovrebbe ora avere lo stato attivo.
* Fare clic sul **Communicator** prefab nel pannello Project **per** visualizzare i relativi componenti nel **controllo**.
* Esaminare il **componente Gestione microfoni (script)** per registrare la voce dell'utente.
* Si noti che **l Communicator o** object include un **componente Speech Input Handler (Script)** per rispondere al comando Send **Message.**
* Esaminare il componente **Communicator (script)** e fare doppio clic sullo script per aprirlo in Visual Studio.

Communicator.cs è responsabile dell'impostazione degli stati dei pulsanti nel dispositivo del comunicatore. In questo modo gli utenti potranno registrare un messaggio, riprodurlo e inviarlo all'astronauta. Verrà anche avviata e interrotta una forma di onda animata per confermare all'utente che la voce è stata udita.

* In **Communicator.cs** eliminare le righe seguenti (81 e 82) dal **metodo Start.** In questo modo verrà abilitato il pulsante "Record" nel comunicatore.

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>Compilazione e distribuzione

* In Visual Studio ricompilare l'applicazione e distribuire nel dispositivo.
* Osservare l'orologio dell'astronauta e *pronunciare "Open Communicator"* per mostrare il comunicatore.
* Premere il **pulsante Registra** (microfono) per avviare la registrazione di un messaggio verbale per l'astronauta.
* Iniziare a parlare e verificare che l'animazione ondulata sia riprodotta nel comunicatore, che fornisce all'utente feedback che la voce viene udita.
* Premere il **pulsante Arresta** (quadrato sinistro) e verificare che l'animazione ondata smetta di essere eseguita.
* Premere il **pulsante Riproduci** (triangolo destro) per riprodurre il messaggio registrato e ascoltarlo nel dispositivo.
* Premere il **pulsante Arresta** (quadrato destro) per arrestare la riproduzione del messaggio registrato.
* Pronunciare *"Invia messaggio"* per chiudere il comunicatore e ricevere una risposta "Messaggio ricevuto" dall'astronauta.

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>Capitolo 3 - Comprensione e riconoscimento dettatura

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>Obiettivi

* Usare Riconoscimento dettatura per convertire il riconoscimento vocale dell'utente in testo.
* Mostra i risultati ipotezzati e finali del riconoscimento dettatura nel comunicatore.

In questo capitolo si userà Riconoscimento dettatura per creare un messaggio per l'astronauta. Quando si usa Riconoscimento dettatura, tenere presente che:

* Per il funzionamento di Riconoscimento dettatura, è necessario essere connessi al Wi-Fi.
* I timeout si verificano dopo un periodo di tempo impostato. È necessario tenere presenti due timeout:
  * Se il riconoscitore viene avviato e non riceve audio per i primi cinque secondi, si verifica il timeout.
  * Se il riconoscitore ha dato un risultato, ma quindi riceve il silenzio per venti secondi, il timeout.
* È possibile eseguire un solo tipo di riconoscimento (parola chiave o dettatura) alla volta.

>[!NOTE]
>La **funzionalità Microfono** deve essere dichiarata per poter registrare un'app dal microfono. Questa operazione viene eseguita per l'utente già in MR Input 212, ma tenere presente questa operazione per i propri progetti.
>
>1. Nell'editor di Unity passare alle impostazioni del lettore passando a "Modifica > Project Impostazioni > lettore"
>2. Fare clic sulla scheda "Universal Windows Platform"
>3. Nella sezione "Funzionalità Impostazioni > pubblicazione" controllare la **funzionalità Microfono**

### <a name="instructions"></a>Istruzioni

Si modificherà **MicrophoneManager.cs** per usare Riconoscimento dettatura. Questo è ciò che verrà aggiunto:

1. Quando si **preme il** pulsante Record, si avvia **DictationRecognizer.**
2. Mostra **l'ipotesi** di ciò che dictationRecognizer ha compreso.
3. Bloccare i **risultati di** ciò che dictationRecognizer ha compreso.
4. Controllare la presenza di timeout da DictationRecognizer.
5. Quando si **preme il pulsante Arresta** o si verifica il timeout della sessione del microfono, **arrestare DictationRecognizer**.
6. Riavviare **KeywordRecognizer**, che sarà in ascolto del **comando Send Message.**

A questo punto, procedere con l'esercitazione. Completare tutti gli esercizi di codifica per la versione 3.a in **MicrophoneManager.cs** oppure copiare e incollare il codice completo riportato di seguito:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone.
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a>Compilazione e distribuzione

* Ricompilare Visual Studio e distribuire nel dispositivo.
* Chiudere la casella di adattamento con un movimento di tocco dell'aria.
* Osservare l'orologio dell'astronauta e *pronunciare "Open Communicator".*
* Selezionare il **pulsante Registra** (microfono) per registrare il messaggio.
* Iniziare a parlare. Riconoscimento **dettatura** interpreterà il parlato e mostrerà il testo ipotetico nel comunicatore.
* Provare a *pronunciare "Invia messaggio"* durante la registrazione di un messaggio. Si noti che **Riconoscimento parole chiave** non risponde perché **riconoscimento** dettatura è ancora attivo.
* Smettere di parlare per alcuni secondi. Osservare come Riconoscimento dettatura completa l'ipotesi e mostra il risultato finale.
* Iniziare a parlare e quindi sospendere per 20 secondi. Ciò causerà il timeout **di Riconoscimento** dettatura.
* Si noti che **riconoscimento parole chiave** viene riattivato dopo il timeout precedente. Il comunicatore ora risponderà ai comandi vocali.
* Pronunciare *"Send Message" (Invia messaggio)* per inviare il messaggio all'astronauta.

## <a name="chapter-4---grammar-recognizer"></a>Capitolo 4 - Riconoscimento grammaticale

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>Obiettivi

* Usare riconoscimento grammaticale per riconoscere il riconoscimento vocale dell'utente in base a un file SRGS o Speech Recognition Grammar Specification.

>[!NOTE]
>La **funzionalità Microfono** deve essere dichiarata per poter registrare un'app dal microfono. Questa operazione viene eseguita per l'utente già in MR Input 212, ma tenere presente questa operazione per i propri progetti.
>
>1. Nell'editor di Unity passare alle impostazioni del lettore passando a "Modifica > Project Impostazioni > lettore"
>2. Fare clic sulla scheda "Universal Windows Platform"
>3. Nella sezione "Funzionalità Impostazioni > pubblicazione" controllare la **funzionalità Microfono**

### <a name="instructions"></a>Istruzioni

1. Nel pannello **Gerarchia** cercare **Jetpack_Center** e selezionarlo.
2. Cercare lo script **Tagalong Action** nel **pannello Inspector (Controllo).**
3. Fare clic sul piccolo cerchio a destra del **campo Oggetto da contrassegnare.**
4. Nella finestra visualizzata cercare **SRGSToolbox** e selezionarlo dall'elenco.
5. Esaminare il file **SRGSColor.xml** nella cartella **StreamingAssets.**
    1. La specifica di progettazione SRGS è disponibile nel sito Web W3C [qui.](https://www.w3.org/TR/speech-grammar/)

Nel file SRGS sono disponibili tre tipi di regole:

* Regola che consente di pronunciare un colore da un elenco di dodici colori.
* Tre regole che sono in ascolto di una combinazione della regola del colore e di una delle tre forme.
* Regola radice, colorChooser, che rimane in ascolto di qualsiasi combinazione delle tre regole "color + shape". Le forme possono essere di tipo detto in qualsiasi ordine e in qualsiasi quantità, da una a tutte e tre. Questa è l'unica regola che viene attesa perché viene specificata come regola radice all'inizio del file nel &lt; &gt; tag grammaticale iniziale.

### <a name="build-and-deploy"></a>Compilazione e distribuzione

* Ricompilare l'applicazione in Unity, quindi compilare e distribuire da Visual Studio per sperimentare l'app HoloLens.
* Chiudere la casella di adattamento con un movimento di tocco dell'aria.
* Osservare il jetpack dell'astronauta ed eseguire un movimento di tocco dell'aria.
* Iniziare a parlare. Riconoscimento **grammaticale** interpreterà il riconoscimento vocale e modificherà i colori delle forme in base al riconoscimento. Un comando di esempio è "cerchio blu, quadrato giallo".
* Eseguire un altro movimento di tocco dell'aria per chiudere la casella degli strumenti.

## <a name="the-end"></a>La fine

Congratulazioni! L'input **MR 212: Voice** è stato completato.

* Si conoscono i comandi Dos e Don'ts dei comandi vocali.
* Si è visto come sono state utilizzate le descrizioni comando per rendere gli utenti consapevoli dei comandi vocali.
* Sono stati visti diversi tipi di feedback usati per confermare che la voce dell'utente è stata udita.
* Si sa come passare da Riconoscimento parole chiave a Riconoscimento dettatura e da come queste due funzionalità comprendono e interpretano la voce.
* Si è appreso come usare un file SRGS e riconoscimento grammaticale per il riconoscimento vocale nell'applicazione.