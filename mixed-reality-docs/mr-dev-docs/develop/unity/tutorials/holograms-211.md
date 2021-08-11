---
title: HoloLens (prima generazione) Input 211 - Movimento
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per informazioni dettagliate sui concetti relativi ai movimenti.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, gesture, HoloLens, Mixed Reality Academy, unity, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale, Windows 10
ms.openlocfilehash: 75cfb836e5a9702c1d949ed57450984081db0c5d6ec14c76cae5148edf637e7e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206427"
---
# <a name="hololens-1st-gen-input-211-gesture"></a>HoloLens (prima generazione) Input 211: Movimento

>[!IMPORTANT]
>Le esercitazioni di Mixed Reality Academy sono state progettate con HoloLens (prima generazione), Unity 2017 e Visori immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi. Queste esercitazioni **_non verranno_** aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2 e potrebbero non essere compatibili con le versioni più recenti di Unity.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md).

[I movimenti trasformano](../../../design/gaze-and-commit.md#composite-gestures) l'intenzione dell'utente in azione. Grazie ai movimenti, gli utenti possono interagire con gli ologrammi. In questo corso si apprenderà come tenere traccia delle mani dell'utente, rispondere all'input dell'utente e inviare commenti e suggerimenti all'utente in base allo stato e alla posizione della mano.

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

In [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md)è stato usato un semplice movimento di tocco dell'aria per interagire con gli ologrammi. A questo punto, si andrà oltre il movimento di tocco dell'aria ed esploreremo i nuovi concetti per:

* Rilevare quando viene rilevata la mano dell'utente e inviare commenti e suggerimenti all'utente.
* Usare un movimento di navigazione per ruotare gli ologrammi.
* Inviare commenti e suggerimenti quando la mano dell'utente sta per uscire dalla visualizzazione.
* Usare gli eventi di manipolazione per consentire agli utenti di spostare gli ologrammi con le mani.

In questo corso verrà rivisto esplora modelli del progetto **Unity,** compilato in [MR Input 210.](holograms-210.md) Il nostro amico astronauta è tornato ad assisterci nell'esplorazione di questi nuovi concetti di movimento.

>[!IMPORTANT]
>I video incorporati in ognuno dei capitoli seguenti sono stati registrati usando una versione precedente di Unity e della realtà mista Toolkit. Anche se le istruzioni dettagliate sono accurate e aggiornate, è possibile che nei video corrispondenti siano visualizzati script e oggetti visivi non aggiornati. I video rimangono inclusi per i poster e perché i concetti trattati sono ancora applicabili.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>Input MR 211: Movimento</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un Windows 10 pc configurato con gli strumenti [corretti installati.](../../../develop/install-the-tools.md)
* Alcune funzionalità di programmazione C# di base.
* È necessario aver completato [MR Basics 101.](../../../develop/unity/tutorials/holograms-101.md)
* L'input [MR 210](holograms-210.md)dovrebbe essere stato completato.
* Un HoloLens configurato [per lo sviluppo.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>File di progetto

* Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) richiesti dal progetto. Richiede Unity 2017.2 o versione successiva.
* Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere.

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è disponibile in GitHub [.](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)

### <a name="errata-and-notes"></a>Errata e note

* "Abilita Just My Code" deve essere disabilitato *(* deselezionato ) in Visual Studio in Strumenti->Opzioni->Debug per poter terminare con i punti di interruzione nel codice.

## <a name="chapter-0---unity-setup"></a>Capitolo 0 - Installazione di Unity

### <a name="instructions"></a>Istruzioni

1. Riavviare Unity.
2. Selezionare **Open** (Apri).
3. Passare alla **cartella Gesture** precedentemente non archiviata.
4. Trovare e selezionare la **cartella Starting** Model Explorer / **(Avvio di Esplora** modelli).
5. Fare clic **sul pulsante Seleziona** cartella.
6. Nel pannello **Project** espandere la **cartella Scene.**
7. Fare doppio clic **sulla scena ModelExplorer** per caricarla in Unity.

### <a name="building"></a>Compilazione

1. In Unity selezionare **File > build Impostazioni**.
2. Se **Scenes/ModelExplorer** non è elencato in Scenes In Build (Scene **in compilazione),** fare clic **su Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena.
3. Se si sviluppa in modo specifico per HoloLens, impostare **Dispositivo di destinazione** su **HoloLens**. In caso contrario, lasciarlo in **Qualsiasi dispositivo**.
4. Assicurarsi **che Tipo di** compilazione sia impostato su **D3D** e **che SDK** sia impostato su **Più** recente installato (che deve essere SDK 16299 o versione successiva).
5. Fare clic su **Compila**.
6. Creare una **nuova cartella** denominata "App".
7. Fare clic sulla **cartella App.**
8. Premere **Seleziona cartella e** Unity inizierà a compilare il progetto per Visual Studio.

Al termine di Unity, viene visualizzata Esplora file finestra di dialogo.

1. Aprire la **cartella App.**
2. Aprire **modelExplorer Visual Studio Soluzione**.

Se si esegue la distribuzione in HoloLens:

1. Usando la barra degli strumenti superiore Visual Studio, modificare la destinazione da Debug a **Versione** e da ARM a **x86**.
2. Fare clic sulla freccia a discesa accanto al pulsante Computer locale e selezionare **Computer remoto**.
3. Immettere **l HoloLens IP del dispositivo** e impostare Modalità di autenticazione su Universale **(protocollo non crittografato).** Fare clic su **Seleziona**. Se non si conosce l'indirizzo IP del dispositivo, cercare Impostazioni > **rete & Internet > opzioni avanzate**.
4. Nella barra dei menu superiore fare clic su **Debug -> Avvia** senza eseguire debug o premere **CTRL+F5.** Se questa è la prima volta che si esegue la distribuzione nel dispositivo, è necessario [associarlo](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)a Visual Studio .
5. Dopo la distribuzione dell'app, chiudere **Fitbox** con un **movimento di selezione.**

Se si esegue la distribuzione in un visore vr immersivo:

1. Usando la barra degli strumenti superiore Visual Studio, modificare la destinazione da Debug a **Versione** e da ARM a **x64.**
2. Assicurarsi che la destinazione della distribuzione sia impostata su **Computer locale**.
3. Nella barra dei menu superiore fare clic su **Debug -> Avvia** senza eseguire debug o premere **CTRL+F5.**
4. Dopo la distribuzione dell'app, chiudere **Fitbox** estraendo il trigger in un controller di movimento.

>[!NOTE]
>È possibile notare alcuni errori di colore rosso nel pannello Visual Studio errori. È sicuro ignorarli. Passare al pannello Output per visualizzare lo stato effettivo della compilazione. Gli errori nel pannello Output richiederanno di apportare una correzione(nella maggior parte dei casi sono causati da un errore in uno script).

## <a name="chapter-1---hand-detected-feedback"></a>Capitolo 1 - Feedback rilevato dalla mano

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>Obiettivi

* Sottoscrivere eventi di rilevamento manuale.
* Usare il feedback del cursore per mostrare agli utenti quando viene rilevata una mano.

>[!NOTE]
>In HoloLens 2 , le mani rilevate si incendino ogni volta che le mani sono visibili (non solo quando un dito è puntato verso l'alto).

### <a name="instructions"></a>Istruzioni

* Nel pannello **Gerarchia** espandere **l'oggetto InputManager.**
* Cercare e selezionare **l'oggetto GesturesInput.**

Lo script **InteractionInputSource.cs** esegue questi passaggi:

1. Sottoscrive gli eventi InteractionSourceDetected e InteractionSourceLost.
2. Imposta lo stato HandDetected.
3. Annulla la sottoscrizione dagli eventi InteractionSourceDetected e InteractionSourceLost.

Successivamente, il cursore verrà aggiornato da [MR Input 210](holograms-210.md) a uno che mostra i commenti e suggerimenti in base alle azioni dell'utente.

1. Nel pannello **Gerarchia** selezionare **l'oggetto Cursore** ed eliminarlo.
2. Nel pannello **Project,** cercare **CursorWithFeedback** e trascinarlo nel **pannello Gerarchia.**
3. Fare clic su **InputManager** nel pannello **Gerarchia,** quindi trascinare l'oggetto **CursorWithFeedback** dalla **gerarchia** nel campo **Cursore** di InputManager **SimpleSinglePointerSelector,** nella parte inferiore del controllo **.**
4. Fare clic su **CursorWithFeedback** nella **gerarchia**.
5. Nel pannello **Inspector** (Controllo) espandere Cursor State Data (Dati stato **cursore)** nello script **Object Cursor (Cursore** oggetto).

I **dati relativi allo stato del** cursore funzionano nel modo seguente:

* Qualsiasi **stato Osserva** indica che non viene rilevata alcuna mano e che l'utente si limita a guardarsi intorno.
* Qualsiasi **stato interact** indica che viene rilevata una mano o un controller.
* Qualsiasi **stato hover** indica che l'utente sta esaminando un ologramma.

### <a name="build-and-deploy"></a>Compilazione e distribuzione

* In Unity usare File > **Build Impostazioni** ricompilare l'applicazione.
* Aprire la **cartella App.**
* Se non è già aperto, aprire **modelExplorer Visual Studio Soluzione**.
  * Se il progetto è già stato compilato/distribuito in Visual Studio durante la configurazione, è possibile aprire l'istanza di Visual Studio e fare clic su 'Ricarica tutto' quando richiesto.
* In Visual Studio fare clic su **Debug -> Avvia** senza eseguire debug o premere **CTRL+F5.**
* Dopo la distribuzione dell'applicazione nel HoloLens, chiudere il riquadro di adattamento usando il movimento di tocco dell'aria.
* Spostare la mano nella visualizzazione e puntare il dito indice verso il cielo per iniziare a tracciare la mano.
* Spostare la mano a sinistra, a destra, verso l'alto e verso il basso.
* Osservare come cambia il cursore quando la mano viene rilevata e quindi persa dalla visualizzazione.
* Se si ha un visore vr immersivo, è necessario connettersi e disconnettere il controller. Questo feedback diventa meno interessante in un dispositivo immersivo, perché un controller connesso sarà sempre "disponibile".

## <a name="chapter-2---navigation"></a>Capitolo 2 - Navigazione

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>Obiettivi

* Usare gli eventi dei movimenti di navigazione per ruotare l'astronauta.

### <a name="instructions"></a>Istruzioni

Per usare i movimenti di navigazione nell'app, si modificherà **GestureAction.cs** per ruotare gli oggetti quando si verifica il movimento di navigazione. Inoltre, si aggiungeranno commenti e suggerimenti al cursore da visualizzare quando è disponibile l'esplorazione.

1. Nel pannello **Gerarchia** espandere **CursorWithFeedback**.
2. Nella cartella **Ologrammi** trovare l'asset **ScrollFeedback.**
3. Trascinare e rilasciare il prefab **ScrollFeedback** in **CursorWithFeedback** GameObject nella **gerarchia**.
4. Fare clic **su CursorWithFeedback**.
5. Nel pannello **Inspector** (Controllo) fare clic **sul pulsante Add Component (Aggiungi** componente).
6. Nel menu digitare nella casella di ricerca **CursorFeedback**. Selezionare il risultato della ricerca.
7. Trascinare e rilasciare **l'oggetto ScrollFeedback** dalla **gerarchia** alla proprietà **Scroll Detected Game Object** nel componente **Feedback** cursore in **Inspector**.
8. Nel pannello **Gerarchia** selezionare **l'oggetto AstroMan.**
9. Nel pannello **Inspector** (Controllo) fare clic **sul pulsante Add Component (Aggiungi** componente).
10. Nel menu digitare nella casella di ricerca **Azione movimento**. Selezionare il risultato della ricerca.

Aprire quindi **GestureAction.cs** in Visual Studio. Nell'esercizio di codifica 2.c modificare lo script per eseguire le operazioni seguenti:

1. **Ruotare l'oggetto AstroMan** ogni volta che viene eseguito un movimento di navigazione.
2. Calcolare **rotationFactor** per controllare la quantità di rotazione applicata all'oggetto.
3. **Ruotare l'oggetto** intorno all'asse y quando l'utente sposta la mano a sinistra o a destra.

Completare gli esercizi di codifica 2.c nello script o sostituire il codice con la soluzione completata seguente:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

Si noterà che gli altri eventi di navigazione sono già compilati con alcune informazioni. Il GameObject viene inserito nello stack modale di InputSystem del Toolkit, quindi l'utente non deve mantenere lo stato attivo sull'astronauta dopo l'inizio della rotazione. Di conseguenza, l'oggetto GameObject viene espulso dallo stack al termine del movimento.

### <a name="build-and-deploy"></a>Compilazione e distribuzione

1. Ricompilare l'applicazione in Unity e quindi compilare e distribuire da Visual Studio per eseguirla nel HoloLens.
2. Guarda l'astronauta, due frecce dovrebbero essere visualizzate su entrambi i lati del cursore. Questo nuovo oggetto visivo indica che l'astronauta può essere ruotato.
3. Posizionare la mano nella posizione pronta (indice puntato verso il cielo) in modo che il HoloLens inizi a tracciare la mano.
4. Per ruotare l'astronauta, abbassare il dito dell'indice in una posizione di avvicinamento delle dita e quindi spostare la mano verso sinistra o verso destra per attivare il movimento NavigationX.

## <a name="chapter-3---hand-guidance"></a>Capitolo 3 - Guida manuale

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>Obiettivi

* Usare **il punteggio di guida manuale** per prevedere quando il rilevamento della mano andrà perso.
* Fornire **commenti e suggerimenti sul cursore** per visualizzare quando la mano dell'utente si avvicina al bordo visivo della fotocamera.

### <a name="instructions"></a>Istruzioni

1. Nel pannello **Gerarchia** selezionare **l'oggetto CursorWithFeedback.**
2. Nel pannello **Inspector** (Controllo) fare clic **sul pulsante Add Component (Aggiungi** componente).
3. Nel menu digitare nella casella di ricerca **Hand Guidance**. Selezionare il risultato della ricerca.
4. Nella cartella **Project** pannello **Ologrammi** trovare **l'asset HandGuidanceFeedback.**
5. Trascinare e rilasciare **l'asset HandGuidanceFeedback** nella **proprietà Indicatore** di guida manuale nel **pannello Controllo.**

### <a name="build-and-deploy"></a>Compilazione e distribuzione

* Ricompilare l'applicazione in Unity e quindi compilare e distribuire da Visual Studio per sperimentare l'app HoloLens.
* Visualizzare la mano e alzare il dito indice per essere monitorati.
* Iniziare a ruotare l'astronauta con il movimento Navigation (avvicinare le dita dell'indice e il pollice).
* Spostare la mano a sinistra, a destra, verso l'alto e verso il basso.
* Quando la mano si avvicina al bordo della cornice del movimento, accanto al cursore dovrebbe essere visualizzata una freccia per avvisare che il rilevamento della mano andrà perso. La freccia indica la direzione in cui spostare la mano per evitare la perdita del rilevamento.

## <a name="chapter-4---manipulation"></a>Capitolo 4 - Manipolazione

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>Obiettivi

* Usare gli eventi di manipolazione per spostare l'astronauta con le mani.
* Fornire commenti e suggerimenti sul cursore per inserire l'utente quando è possibile usare la manipolazione.

### <a name="instructions"></a>Istruzioni

GestureManager.cs e AstronautManager.cs consentono di eseguire le operazioni seguenti:

1. Usare la parola chiave vocale "**Move Astronaut**" per abilitare i movimenti **di** manipolazione e "**Rotate Astronaut**" per disabilitarli.
2. Passare alla risposta al **riconoscimento del movimento di manipolazione.**

A questo punto, procedere con l'esercitazione.

1. Nel pannello **Hierarchy** (Gerarchia) creare un nuovo GameObject vuoto. Assegnare il nome "**AstronautManager**".
2. Nel pannello **Inspector** (Controllo) fare clic **sul pulsante Add Component (Aggiungi** componente).
3. Nel menu digitare nella casella di ricerca **Astronaut Manager**. Selezionare il risultato della ricerca.
4. Nel pannello **Inspector** (Controllo) fare clic **sul pulsante Add Component (Aggiungi** componente).
5. Nel menu digitare nella casella di ricerca **Origine input vocale**. Selezionare il risultato della ricerca.

Verranno ora aggiunti i comandi vocali necessari per controllare lo stato di interazione dell'astronauta.

1. Espandere la **sezione Parole** chiave in **Inspector**.
2. Fare clic **+** sul lato destro per aggiungere una nuova parola chiave.
3. Digitare la parola chiave come **Move Astronaut**. Se lo si desidera, è possibile aggiungere un tasto di scelta rapida.
4. Fare clic **+** sul lato destro per aggiungere una nuova parola chiave.
5. Digitare la parola chiave rotate **astronaut**. Se lo si desidera, è possibile aggiungere un tasto di scelta rapida.
6. Il codice del gestore corrispondente è disponibile in **GestureAction.cs** nel gestore **ISpeechHandler.OnSpeechKeywordRecognized.**

![Come configurare l'origine input vocale per il capitolo 4](images/holograms211-speech.png)

Successivamente, si configura il feedback sulla manipolazione sul cursore.

1. Nella cartella **Project** pannello **Ologrammi** trovare **l'asset PathingFeedback.**
2. Trascinare e rilasciare il prefab **PathingFeedback** **nell'oggetto CursorWithFeedback** nella **gerarchia**.
3. Nel pannello **Gerarchia** fare clic su **CursorWithFeedback**.
4. Trascinare e rilasciare **l'oggetto PathingFeedback** dalla **gerarchia** alla proprietà **Pathing Detected Game Object** (Oggetto gioco rilevato tracciato) del componente **Cursor Feedback (Feedback** cursore) in Inspector ( **Controllo**).

A questo punto è necessario aggiungere codice **a GestureAction.cs** per abilitare quanto segue:

1. Aggiungere il codice alla **funzione IManipulationHandler.OnManipulationUpdated,** che sposterà l'astronauta quando viene rilevato **un movimento di** manipolazione.
2. Calcolare il **vettore di** spostamento per determinare dove deve essere spostato l'astronauta in base alla posizione della mano.
3. **Spostare** l'astronauta nella nuova posizione.

Completare l'esercizio di scrittura del codice 4.a in **GestureAction.cs** oppure usare la soluzione completata seguente:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>Compilazione e distribuzione

* Ricompilare in Unity e quindi compilare e distribuire da Visual Studio per eseguire l'app in HoloLens.
* Spostare la mano davanti al HoloLens e alzare il dito indice in modo che possa essere monitorato.
* Spostare il cursore sull'astronauta.
* Pronunciare "Move Astronaut" (Sposta astronauta) per spostare l'astronauta con un movimento di manipolazione.
* Intorno al cursore dovrebbero essere visualizzate quattro frecce per indicare che il programma risponderà agli eventi di manipolazione.
* Abbassare il dito indice verso il basso fino al pollice e mantenerli avvicinati.
* Quando si sposta la mano, si sposta anche l'astronauta (si tratta di Manipulation).
* Alzare il dito indice per arrestare la manipolazione dell'astronauta.
* Nota: se non si pronuncia "Move Astronaut" (Sposta astronauta) prima di spostare la mano, verrà usato il movimento Navigation (Navigazione).
* Pronunciare "Rotate Astronaut" (Ruota astronauta) per tornare allo stato rotabile.

## <a name="chapter-5---model-expansion"></a>Capitolo 5 - Espansione del modello

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>Obiettivi

* Espandere il modello Astronaut in più parti più piccole con cui l'utente può interagire.
* Spostare ogni parte singolarmente usando i movimenti di navigazione e manipolazione.

### <a name="instructions"></a>Istruzioni

In questa sezione verranno eseguite le attività seguenti:

1. Aggiungere una nuova parola chiave "**Expand Model**" per espandere il modello astronauta.
2. Aggiungere una nuova parola chiave "**Reset Model**" (Reimposta modello) per ripristinare il formato originale del modello.

A tale scopo, si aggiungeranno altre due parole chiave all'origine input vocale del capitolo precedente. Verrà anche illustrato un altro modo per gestire gli eventi di riconoscimento.

1. Fare di nuovo clic **su AstronautManager** in **Inspector (Controllo)** ed espandere **la sezione Keywords (Parole** chiave) in **Inspector (Controllo).**
2. Fare clic **+** su sul lato destro per aggiungere una nuova parola chiave.
3. Digitare la parola chiave **come Espandi modello**. Se lo si desidera, è possibile aggiungere un tasto di scelta rapida.
4. Fare clic **+** su sul lato destro per aggiungere una nuova parola chiave.
5. Digitare La parola chiave come **Reimposta modello**. Se lo si desidera, è possibile aggiungere un tasto di scelta rapida.
6. Nel pannello **Inspector (Controllo)** fai clic **sul pulsante Add Component (Aggiungi** componente).
7. Nel menu digitare nella casella di ricerca **Speech Input Handler**. Selezionare il risultato della ricerca.
8. Selezionare **Is Global Listener (Listener** globale) perché si vuole che questi comandi funzionino indipendentemente dal GameObject che si sta concentrando.
9. Fare clic sul **+** pulsante e selezionare Espandi modello **dall'elenco** a discesa Parola chiave.
10. Fare clic **+** su in Response (Risposta) e **trascinare AstronautManager** da **Hierarchy (Gerarchia)** **nel campo None (Object) (Nessuno -** Oggetto).
11. A questo punto, fare **clic sull'elenco a** discesa No Function (Nessuna funzione), **selezionare AstronautManager** e **quindi ExpandModelCommand**.
12. Fare clic sul pulsante Speech Input Handler (Gestore input **+** vocale) e selezionare **Reset Model (Reimposta modello)** nell'elenco a discesa Keyword (Parola chiave).
13. Fare clic **+** su in Response (Risposta) e **trascinare AstronautManager** da **Hierarchy (Gerarchia)** **nel campo None (Object) (Nessuno -** Oggetto).
14. A questo punto, fare **clic sull'elenco a** discesa No Function (Nessuna funzione), **selezionare AstronautManager** e **quindi ResetModelCommand**.

![Come configurare l'origine e il gestore dell'input vocale per il capitolo 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>Compilazione e distribuzione

* Prova Compilare e distribuire l'app nel HoloLens.
* Pronunciare **Espandi modello** per visualizzare il modello astronauta espanso.
* Usare **La navigazione** per ruotare singoli elementi della tuta astronauta.
* Pronunciare **Move Astronaut (Sposta astronauta)** **e quindi usare Manipulation (Manipolazione)** per spostare singoli elementi della tuta astronauta.
* Pronunciare **Rotate Astronaut (Ruota astronauta)** per ruotare di nuovo i componenti.
* Pronunciare **Reset Model (Reimposta** modello) per ripristinare la forma originale dell'astronauta.

## <a name="the-end"></a>La fine

Congratulazioni! L'input **MR 211: Gesture** è stato completato.

* Si sa come rilevare e rispondere agli eventi di tracciamento delle mani, navigazione e manipolazione.
* Si comprende la differenza tra i movimenti di navigazione e di manipolazione.
* Si sa come modificare il cursore per fornire feedback visivo quando viene rilevata una mano, quando una mano sta per andare persa e per quando un oggetto supporta interazioni diverse (navigazione e manipolazione).