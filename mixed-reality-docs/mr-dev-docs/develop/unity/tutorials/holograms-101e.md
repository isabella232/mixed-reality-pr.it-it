---
title: HoloLens (prima generazione) Nozioni di base 101E - Progetto completo con emulatore
description: Seguire questa procedura dettagliata di scrittura del codice usando Unity, Visual Studio e HoloLens Emulator per apprendere le nozioni di base di un'applicazione olografica.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realtà mista, Windows Mixed Reality, ologramma, academy, esercitazione, emulatore, HoloLens, Mixed Reality Academy, unity, visore VR di realtà mista, visore VR di realtà mista di Windows, visore VR di realtà virtuale, Windows 10, sguardo, movimenti, input vocale, audio spaziale, mapping spaziale
ms.openlocfilehash: 3cbd1fbba8d4dac4a1d3d0ac1b78a38ed7c8bfa5a7f0b5b3b8d61e9a87f924dd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200841"
---
# <a name="hololens-1st-gen-basics-101e-complete-project-with-emulator"></a>HoloLens (prima generazione) Nozioni di base 101E: Progetto completo con emulatore

>[!IMPORTANT]
>Le esercitazioni di Mixed Reality Academy sono state progettate per HoloLens (prima generazione), Unity 2017 e visori VR immersive di Realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi. Queste esercitazioni non **_verranno_** aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2 e potrebbero non essere compatibili con le versioni più recenti di Unity.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md).

<br>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

Questa esercitazione illustra un progetto completo, compilato in Unity, che illustra le funzionalità principali di Windows Mixed Reality in [](../../../design/spatial-sound.md) HoloLens tra cui sguardo [fisso,](../../../design/gaze-and-commit.md) [](../../../design/gaze-and-commit.md#composite-gestures)movimenti, input [vocale,](../../../design/voice-input.md)audio spaziale e mapping [spaziale.](../../../design/spatial-mapping.md) Il completamento dell'esercitazione richiederà circa un'ora.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>Nozioni di base MR 101E: Progetto completo con emulatore</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un Windows 10 pc configurato con gli strumenti [corretti installati.](../../install-the-tools.md)

### <a name="project-files"></a>File di progetto

* Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) richiesti dal progetto. Richiede Unity 2017.2 o versione successiva.
  * Se è ancora necessario il supporto di Unity 5.6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).
  * Se è ancora necessario il supporto di Unity 5.5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Se è ancora necessario il supporto di Unity 5.4, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).
* Annullare l'archiviazione dei file sul desktop o in un'altra posizione facilmente raggiungibile. Mantenere il nome della cartella **Origami**.

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è disponibile [in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Capitolo 1 : mondo "Holo"

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

In questo capitolo si configura il primo progetto Unity e si esegue il processo di compilazione e distribuzione.

### <a name="objectives"></a>Obiettivi

* Configurare Unity per lo sviluppo olografico.
* Creare un ologramma.
* Vedere un ologramma creato.

### <a name="instructions"></a>Istruzioni

* Riavviare Unity.
* Selezionare **Open** (Apri).
* Immettere percorso come cartella **Origami** non archiviata in precedenza.
* Selezionare **Origami e** fare clic **su Seleziona cartella.**
* Salvare la nuova scena: **Salva scena**  /  **con nome**.
* Assegnare alla scena **il nome Origami** e premere **il pulsante** Salva.

#### <a name="setup-the-main-camera"></a>Configurare la fotocamera principale

* Nel **Pannello di gerarchia**, selezionare **Fotocamera principale**.
* In Inspector **impostarne** la posizione di trasformazione su **0,0,0.**
* Trovare la **proprietà Clear Flags (Cancella** flag) e modificare l'elenco a discesa **da Skybox** a **Solid color (Colore a tinta unita).**
* Fare clic sul campo **Sfondo** per aprire un editor dei colori.
* Impostare **R, G, B e A** su **0**.

#### <a name="setup-the-scene"></a>Configurare la scena

* Nel pannello **Hierarchy (Gerarchia)** fare clic **su Create** and Create **Empty (Crea e crea vuoto).**
* Fare clic con il pulsante destro del mouse **sul nuovo GameObject** e scegliere Rinomina. Rinominare il GameObject in **OrigamiCollection.**
* Dalla cartella **Ologrammi** nel pannello **Project :**
  * Trascinare **Stage** nella gerarchia in modo che sia un elemento figlio **di OrigamiCollection.**
  * Trascinare **Sphere1** nella gerarchia per essere un elemento figlio di **OrigamiCollection.**
  * Trascinare **Sphere2** nella gerarchia per essere un elemento figlio di **OrigamiCollection.**
* Fare clic con il pulsante **destro del mouse sull'oggetto Directional Light (Luce** direzionale) nel **pannello Hierarchy (Gerarchia)** e **scegliere Delete (Elimina).**
* Dalla cartella **Ologrammi** trascinare **Lights** nella radice di **Hierarchy Panel**.
* In **Hierarchy (Gerarchia)** selezionare **OrigamiCollection.**
* In **Inspector impostare** la posizione della trasformazione su **0, -0.5, 2.0.**
* Premere il **pulsante Play** (Riproduci) in Unity per visualizzare in anteprima gli ologrammi.
* Gli oggetti Origami dovrebbero essere visualizzati nella finestra di anteprima.
* Premere **Riproduci** una seconda volta per arrestare la modalità di anteprima.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Esportare il progetto da Unity in Visual Studio

* In Unity selezionare **File > Build Impostazioni**.
* Selezionare **Windows Store nell'elenco** **Piattaforma e** fare clic su **Cambia piattaforma.**
* Impostare **SDK** su **Universal 10 e** Tipo di **compilazione** su **D3D.**
* Controllare **i progetti C# di Unity.**
* Fare **clic su Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena.
* Fare **clic su Player Impostazioni...**.
* Nel pannello Inspector (Controllo) seleziona **il logo Windows Store**. Selezionare quindi **Pubblicazione Impostazioni**.
* Nella sezione **Funzionalità** selezionare le funzionalità **Microfono** **e SpatialPerception.**
* Nella finestra Compila Impostazioni fare clic su **Compila**.
* Creare una **nuova cartella** denominata "App".
* Fare clic su **Cartella app**.
* Fare clic **su Seleziona cartella**.
* Al termine dell'operazione, verrà Esplora file finestra di dialogo.
* Aprire la **cartella App.**
* Aprire la **soluzione Visual Studio Origami**.
* Usando la barra degli strumenti superiore Visual Studio, modificare la destinazione da Debug a **Release** e da ARM a **X86.**
  * Fare clic sulla freccia accanto al pulsante Dispositivo e selezionare **HoloLens Emulator**.
  * Fare **clic su Debug -> Avvia senza eseguire** debug o premere **CTRL+F5.**
  * Dopo un certo periodo di tempo l'emulatore verrà avviato con il progetto Origami. Quando si avvia [l'emulatore](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)per la prima volta, l'avvio dell'emulatore può richiedere fino a 15 minuti. Dopo l'avvio, non chiuderlo.

## <a name="chapter-2---gaze"></a>Capitolo 2 - Sguardo fisso

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

In questo capitolo verranno presentati i primi tre modi per interagire con gli ologrammi, lo [sguardo fisso](../../../design/gaze-and-commit.md).

### <a name="objectives"></a>Obiettivi

* Visualizzare lo sguardo fisso usando un cursore bloccato a livello mondiale.

### <a name="instructions"></a>Istruzioni

* Tornare al progetto Unity e chiudere la finestra build Impostazioni se è ancora aperta.
* Selezionare la **Ologrammi** nel pannello **Project .**
* Trascinare **l'oggetto Cursor** nel **pannello Hierarchy (Gerarchia)** a livello di radice.
* Fare doppio clic **sull'oggetto Cursor** per osservarlo più da vicino.
* Fare clic con il pulsante destro **del mouse sulla** cartella Scripts Project pannello.
* Fare clic **sul sottomenu** Crea.
* Selezionare **Script C#.**
* Assegnare allo script **il nome WorldCursor**. Nota: il nome fa distinzione tra maiuscole e minuscole. Non è necessario aggiungere l'estensione cs.
* Selezionare **l'oggetto** Cursor nel **pannello Gerarchia**.
* Trascinare e rilasciare lo script **WorldCursor** nel **pannello Inspector**.
* Fare doppio clic nello script **WorldCursor** per aprirlo in Visual Studio.
* Copiare e incollare questo codice in **WorldCursor.cs** e **Salva tutto**.

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move thecursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* Ricompilare l'app **da File > Build Impostazioni**.
* Tornare alla soluzione Visual Studio usata in precedenza per la distribuzione nell'emulatore.
* Quando richiesto, selezionare 'Ricarica tutto'.
* Fare **clic su Debug -> Avvia senza eseguire debug** o premere **CTRL+F5.**
* Usare il controller Xbox per osservare la scena. Si noti come il cursore interagisce con la forma degli oggetti.

## <a name="chapter-3---gestures"></a>Capitolo 3 - Movimenti

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

In questo capitolo verrà aggiunto il supporto per [i movimenti](../../../design/gaze-and-commit.md#composite-gestures). Quando l'utente seleziona una sfera di carta, la sfera cadrà attivando la gravità usando il motore fisico di Unity.

### <a name="objectives"></a>Obiettivi

* Controllare gli ologrammi con il movimento Seleziona.

### <a name="instructions"></a>Istruzioni

Si inizierà creando uno script che può rilevare il movimento Seleziona.

* Nella cartella **Scripts** creare uno script denominato **GazeGestureManager**.
* Trascinare lo script **GazeGestureManager** **nell'oggetto OrigamiCollection** nella gerarchia.
* Aprire lo script **GazeGestureManager** in Visual Studio e aggiungere il codice seguente:

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Start()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* Creare un altro script nella cartella Scripts, questa volta **denominata SphereCommands**.
* Espandere **l'oggetto OrigamiCollection** nella visualizzazione Gerarchia.
* Trascinare lo script **SphereCommands** **nell'oggetto Sphere1** nel pannello Gerarchia.
* Trascinare lo script **SphereCommands** nell'oggetto **Sphere2** nel pannello Gerarchia.
* Aprire lo script in Visual Studio per la modifica e sostituire il codice predefinito con il codice seguente:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* Esportare, compilare e distribuire l'app nell HoloLens emulatore.
* Guardarsi intorno alla scena e centrare su una delle sphere.
* Premere il **pulsante A** nel controller Xbox o premere la BARRA SPAZIATRICE per simulare il movimento Seleziona.

## <a name="chapter-4---voice"></a>Capitolo 4 - Voce

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

In questo capitolo si aggiungerà il supporto per due comandi [vocali:](../../../design/voice-input.md)"Reset world" (Reimposta mondo) per ripristinare la posizione originale delle sfera rilasciate e "Drop sphere" per far diminuire la sfera.

### <a name="objectives"></a>Obiettivi

* Aggiungere comandi vocali che sono sempre in ascolto in background.
* Creare un ologramma che reagisce a un comando vocale.

### <a name="instructions"></a>Istruzioni

* Nella cartella **Scripts** creare uno script denominato **SpeechManager**.
* Trascinare lo script **SpeechManager** **nell'oggetto OrigamiCollection** nella gerarchia
* Aprire lo script **SpeechManager** in Visual Studio.
* Copiare e incollare questo codice in **SpeechManager.cs** e **Salva tutto**:

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* Aprire lo script **SphereCommands** in Visual Studio.
* Aggiornare lo script in modo che sia letto come segue:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* Esportare, compilare e distribuire l'app nell HoloLens emulatore.
* L'emulatore supporterà il microfono del PC e risponderà alla voce: regolare la visualizzazione in modo che il cursore si trova su una delle sfera e pronunciare "Drop Sphere".
* Pronunciare "**Reset World**" per riportarli alle posizioni iniziali.

## <a name="chapter-5---spatial-sound"></a>Capitolo 5 - Suono spaziale

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

In questo capitolo si aggiungerà musica all'app e quindi si attiveranno effetti sonori su determinate azioni. Si usa il suono [spaziale](../../../design/spatial-sound.md) per assegnare ai suoni una posizione specifica nello spazio 3D.

### <a name="objectives"></a>Obiettivi

* Ascoltare gli ologrammi nel mondo.

### <a name="instructions"></a>Istruzioni

* In Unity selezionare dal menu in alto Modifica > Project Impostazioni > **audio**
* Trovare **l'impostazione Plug-in spazializzatore** e selezionare **MS HRTF Spatializer**.
* Dalla cartella **Ologrammi** trascinare l'oggetto **Ambiente** nell'oggetto **OrigamiCollection** nel pannello Gerarchia.
* Selezionare **OrigamiCollection e** trovare il **componente Origine** audio. Modificare queste proprietà:
  * Controllare la **proprietà Spatialize.**
  * Controllare play **on awake**.
  * Impostare **Fusione spaziale** su **3D** trascinando il dispositivo di scorrimento fino a destra.
  * Controllare la **proprietà Loop.**
  * Espandere **3D Sound Impostazioni** e immettere **0.1** per **Livello Doppler**.
  * Impostare **Rolloff volume** su **Rolloff logaritmico**.
  * Impostare **Distanza massima** su **20.**
* Nella cartella **Scripts** creare uno script denominato **SphereSounds**.
* Trascinare **SphereSounds** negli **oggetti Sphere1** e **Sphere2** nella gerarchia.
* Aprire **SphereSounds** in Visual Studio, aggiornare il codice seguente e **salvare tutti**.

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* Salvare lo script e tornare a Unity.
* Esportare, compilare e distribuire l'app nell HoloLens emulatore.
* Indossa le cuffia per ottenere l'effetto completo e passa sempre più da stage per ascoltare il cambiamento dei suoni.

## <a name="chapter-6---spatial-mapping"></a>Capitolo 6 - Mapping spaziale

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

Ora si userà il [mapping spaziale](../../../design/spatial-mapping.md) per posizionare la tavola da gioco su un oggetto reale nel mondo reale.

### <a name="objectives"></a>Obiettivi

* Portare il mondo reale nel mondo virtuale.
* Posizionare gli ologrammi dove sono più importanti per l'utente.

### <a name="instructions"></a>Istruzioni

* Fare clic sulla **cartella Ologrammi** nel pannello Project dati.
* Trascinare **l'asset Mapping** spaziale nella radice della **gerarchia**.
* Fare clic **sull'oggetto Mapping** spaziale nella gerarchia.
* Nel pannello **Controllo** modificare le proprietà seguenti:
  * Selezionare la **casella Disegna mesh visive.**
  * Individuare **Disegna materiale e** fare clic sul cerchio a destra. Digitare "**wireframe**" nel campo di ricerca nella parte superiore. Fare clic sul risultato e quindi chiudere la finestra.
* Esportare, compilare e distribuire l'app nell HoloLens emulatore.
* Quando l'app viene eseguita, il rendering di una mesh di un living reale analizzato in precedenza verrà eseguito in wireframe.
* Guarda come una sfera in sequenza cadrà dal livello e sul pavimento.

A questo punto verrà illustrato come spostare OrigamiCollection in una nuova posizione:

* Nella cartella **Script** creare uno script denominato **TapToPlaceParent**.
* In **Gerarchia** espandere **OrigamiCollection** e selezionare l'oggetto **Stage.**
* Trascinare lo script **TapToPlaceParent** nell'oggetto Stage.
* Aprire lo script **TapToPlaceParent** Visual Studio e aggiornarlo come segue:

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* Esportare, compilare e distribuire l'app.
* A questo punto si dovrebbe essere in grado di posizionare il gioco in una posizione specifica guardandolo, usando il movimento Seleziona **(A** o BARRA SPAZIATRICE) e quindi spostandosi in una nuova posizione e usando di nuovo il movimento Seleziona.

## <a name="the-end"></a>La fine

Questa è la fine di questa esercitazione.

Sono stati appresi i concetti seguenti:

* Come creare un'app olografica in Unity.
* Come usare lo sguardo, il movimento, la voce, i suoni e il mapping spaziale.
* Come compilare e distribuire un'app usando Visual Studio.

A questo punto è possibile iniziare a creare app olografiche personalizzate.

## <a name="see-also"></a>Vedi anche

* [Nozioni di base MR 101: Progetto completo con dispositivo](holograms-101.md)
* [Sguardo fisso](../../../design/gaze-and-commit.md)
* [Puntamento con la testa e commit](../../../design/gaze-and-commit.md)
* [Input vocale](../../../design/voice-input.md)
* [Audio spaziale](../../../design/spatial-sound.md)
* [Mapping spaziale](../../../design/spatial-mapping.md)